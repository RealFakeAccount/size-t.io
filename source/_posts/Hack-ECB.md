---
title: Hacking the ECB!
date: 2020-09-11 16:01:14
tags:
 - CTF
cover: /images/Hack-ECB.png
---

This article is not about cracking ECB encryption, but how to abuse it. If you are looking for how to bruteforce ECB, this is not what you are looking for.

I recommend you read this <https://zachgrace.com/posts/attacking-ecb/> if you find my article hard to understand.

### What is ECB(Electronic Code Book)?
You actually can get a well understanding in [Wikipedia](https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation)
I want to clarify one picture in wikipedia. 

![](ECBencryption.png)

ECB actually divide the original plain text into a lot of `blocks`. Then it use Block cipher encryption to encrypt each block independently. One advantage of this method is that it can encrypt one plain text in parallel. But the following article will explain its disadvantage. 

 *in the following article, CT stand for Ciphertext, PT stand for Plain text*

----------------------------------

### abuse LV.1

Consider following situation:

```text
ada1ed6764f0e4292c850631aad51009 (Remitter: Alice)
0215a52009de7a0105517b91b3c7e4e8 (Remittee: Bob)
a142fdb3b3eeac6638bce8d6fe4ff343 (Amount: $100,000,000)
```

Just by simply change line 1 and line 2, we can get our new CT:

```text
0215a52009de7a0105517b91b3c7e4e8 (Remittee: Bob)
ada1ed6764f0e4292c850631aad51009 (Remitter: Alice)
a142fdb3b3eeac6638bce8d6fe4ff343 (Amount: $100,000,000)
```

You can also delete or copy CT to control PT in some extent.

### abuse LV.2

Image one naive website admin use ECB encrypted username as cookies.

One day, you are so boring, so you decide to register tons of new account with username:`aaaa....` in this website.
You find something really strange. When you increase your username by 8, your cookies also increase.

```text
1 a, the CT is : 96348b9522f748fe 
9 a, the CT is : 1a4cd2336bca1dd7 96348b9522f748fe 
17 a, the CT is : 1a4cd2336bca1dd7 1a4cd2336bca1dd7 96348b9522f748fe 
```

You realized that this website might use Block cipher.

But when you look closer, you will find a patten occur in CT: `1a4cd2336bca1dd7`. Then you realized this website may use ECB instead of more secure Block cipher algorithm.
Also, you can find that the block size of the ECB encryption is 8 bytes, because when the length of your username increase by 8, the CT increase.

Now, for example, you want to get cookies of user `admin` so you can login as admin, all you need to do is to register an account with username `aaaaaaaaadmin`. The leading 8 a can be any letters.

![](example1.png)

After replace your session cookies with `d6e8b780dc98a7ba`, you should be logged in as `admin`.

### abuse LV.3

You reported this to admin, and he fixed this question by adding a prefix and surfix in the encryption. Now when you register a account with username `hack`, the encyrption would be

```text
PT: FOOLhackLOL
CT: 392ed00be8c3e1cc 0ce3d380e18ba39c

//prefix is FOOL, surfix is LOL
```

after some consideration, you find following conclusion:
 - you can calculate the length of the prefix.
 - The surfix does not matter in this scenario.
 - You can actually calculate what the surfix is.

I will explain how one by one.

#### calculate the length of the prefix

First, you should calculate the block size using the methods metioned above. There, we assume the size is still 8 bytes.
Since the admin still using ECB, if you register a username with tons of `a`, you should see the familiar `1a4cd2336bca1dd7` pattern in the middle of CT.

So in order to find the length of the prefix, you need to add some character before your a's.

![](example2-1.png)
![](example2-2.png)

After you fill in the fifth 'X', you could see the CT of the next block changed. 
![](example2-3.png)
This means, 4 character + prefix = 8 byte. Thus, the length of prefix = 8 - 4 = 4.

#### surfix does not matter in this scenario

If the surfix would not change subject to the username, then you can just use the method in LV.2. 

#### You can actually calculate what the surfix is

[zachgrace](https://zachgrace.com/posts/attacking-ecb/) made an excellent explaintation of this method.

![](example3-1.png)
This is where you should start.

![](example3-2.png)
The first step is to get the target we need. Here, in the former block, the CT of 7 a's with one surfix letter is `6643ec845c44574d`

Then, we need to find our a's plus which letters can form our target. 

You can simply write a python script. Remember to add the prefix.

```python
for i in range(0, 255):
    ciphered = get_ECB(offset + 7 * 'a' + chr(i))
    if ciphered[l:r] == target:
        print("the letter is {}".format(chr(i)))
```

After finding out the first letter, drop one a out, use the CT of `aaaaaaL` as target to find the next letter.

You can continue these steps until you find all the surfix.