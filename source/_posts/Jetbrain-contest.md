---
title: Jetbrain contest
date: 2020-03-10 22:10:36
tags:
 - English
 - writeups
category:
 - just for fun
cover: /images/JBmainpage.png
---

<https://twitter.com/jetbrains/status/1236986174075482113>

the Jetbrain team offered a interesting puzzle. Anyone solve this can get a 3-months activation code for all of the Jetbrain product.

Ok. So let's start with these code:

```text
48 61 76 65 20 79 6f 75 20 73 65 65 6e 20 74 68 65 20 73 6f 75 72 63 65 20 63 6f 64 65 20 6f 66 20 74 68 65 20 4a 65 74 42 72 61 69 6e 73 20 77 65 62 73 69 74 65 3f
```

Obviously, Hex. Use Hex converter:

```text
Have you seen the source code of the JetBrains website?
```

Ok. Jetbrains' website is there <https://www.jetbrains.com/>

Seems nothing interesting on the main page. Not surprising. 

Let's use inspector and try to find some interesting key words.

`Code`? nothing... `Key`? Oh! Here we are on `/html/body/div/div[2]` (xpath)

```text

      O
{o)xxx|===============-
      O

Welcome to the JetBrains Quest.

What awaits ahead is a series of challenges. Each one will require a little initiative, a little thinking, and a whole lot of JetBrains to get to the end. Cheating is allowed and in some places encouraged. You have until the 15th of March at 12:00 CET to finish all the quests.
Getting to the end of each quest will earn you a reward.
Let the quest commence!

JetBrains has a lot of products, but there is one that looks like a joke on our Products page, you should start there... (hint: use Chrome Incognito mode)
It’s dangerous to go alone take this key: Good luck! == Jrrg#oxfn$

                 O
-===============|xxx(o}
                 O
```

What's this hint mean? Incognito mode? This mode have nothing special but creates a temporary session that is isolated from the browser's main session and user data.

Oh, and this key `Good luck! == Jrrg#oxfn$` Let's see when should we use it.

Then we should check the project  "that looks like a joke". However, I looked through all these projects and it seems all these projects are excellent. No joke.

![](JBproducts.png)

I had stucked a little bit until I click the "find your tool".

![](JBreal.png)

wait.. I've never seen this one before.

![](JBquest_prime.png)

Here we are! Here comes a simple math problem. 

```python
def check(num):
    flag = False
    for i in range(2, num):
        if num % i == 0:
            flag = True

    return flag

cnt = 0

for i in range(500, 5000):
    if not check(i) :
        cnt = cnt + 1

print(cnt)
```
solve it and we can step into next stage.
<https://jb.gg/574>

![](JBfollow.png)

A picture with a string `MPS-31816`..
This string seems to be a part of an URL, and YT is Jetbrains' products `youtrack`

After looking through youtrack for a while, I decided to use Google advanced research:
`"MPS-31816 site:jetbrains.com"`
..which give us a website in youtrack:

<https://youtrack.jetbrains.com/issue/MPS-31816>

```
“The key is to think back to the beginning.” -- The JetBrains Quest team

Qlfh$#Li#|rx#duh#uhdglqj#wklv#|rx#pxvw#kdyh#zrunhg#rxw#krz#wr#ghfu|sw#lw1#Wklv#lv#rxu#lvvxh#wudfnhu#ghvljqhg#iru#djloh#whdpv1#Lw#lv#iuhh#iru#xs#wr#6#xvhuv#lq#Forxg#dqg#iru#43#xvhuv#lq#Vwdqgdorqh/#vr#li#|rx#zdqw#wr#jlyh#lw#d#jr#lq#|rxu#whdp#wkhq#zh#wrwdoo|#uhfrpphqg#lw1#|rx#kdyh#ilqlvkhg#wkh#iluvw#Txhvw/#qrz#lw“v#wlph#wr#uhghhp#|rxu#iluvw#sul}h1#Wkh#frgh#iru#wkh#iluvw#txhvw#lv#‟WkhGulyhWrGhyhors†1#Jr#wr#wkh#Txhvw#Sdjh#dqg#xvh#wkh#frgh#wr#fodlp#|rxu#sul}h1#kwwsv=22zzz1mhweudlqv1frp2surpr2txhvw2
```

This is the hardest part in this challenge. Remember the key we get earlier? `Good luck! == Jrrg#oxfn$`. This should be some kind of *substitution cipher*

We can guess all the substitution; This takes some time and some patience.

```python
from colorama import Fore, Style

str = "Qlfh$#Li#|rx#duh#uhdglqj#wklv#|rx#pxvw#kdyh#zrunhg#rxw#krz#wr#ghfu|sw#lw1#Wklv#lv#rxu#lvvxh#wudfnhu#ghvljqhg#iru#djloh#whdpv1#Lw#lv#iuhh#iru#xs#wr#6#xvhuv#lq#Forxg#dqg#iru#43#xvhuv#lq#Vwdqgdorqh/#vr#li#|rx#zdqw#wr#jlyh#lw#d#jr#lq#|rxu#whdp#wkhq#zh#wrwdoo|#uhfrpphqg#lw1#|rx#kdyh#ilqlvkhg#wkh#iluvw#Txhvw/#qrz#lw“v#wlph#wr#uhghhp#|rxu#iluvw#sul}h1#Wkh#frgh#iru#wkh#iluvw#txhvw#lv#‟WkhGulyhWrGhyhors†1#Jr#wr#wkh#Txhvw#Sdjh#dqg#xvh#wkh#frgh#wr#fodlp#|rxu#sul}h1#kwwsv=22zzz1mhweudlqv1frp2surpr2txhvw2
"
str = str.lower()
dic = {
    'j': 'g',
    'r': 'o',
    'g': 'd',
    '#': ' ',
    'o': 'l',
    'x': 'u',
    'f': 'c',
    'n': 'k',
    '$': '!',
    '|': 'y',
    'u': 'r',
    'd': 'a',
    'h': 'e',
    'Q': 'n',
    'q': 'n',
    'v': 's',
    'i': 'f',
    'l': 'i',
    'w': 't',
    'p': 'm',
    'k': 'h',
    'y': 'v',
    'z': 'w',
    's': 'p',
    '1': '.',
    't': 'q',
    '}': 'c',
    '=': ':',
    '2': '/',
    'm': 'j',
    'e': 'b'
}

for i in str:
    if i in dic:
        print(dic[i], end = "")
    else : print(i, end = '')
```

And here is the result:

```text
nice! if you are reading this you must have worked out how to decrypt it. this is our issue tracker designed for agile teams. it is free for up to 6 users in cloud and for 43 users in standalone/ so 
if you want to give it a go in your team then we totally recommend it. you have finished the first quest/ now it“s time to redeem your first price. the code for the first quest is ‟thedrivetodevelop†. go to the quest page and use the code to claim your price. https://www.jetbrains.com/promo/quest/
```

And we are done! Don't forget the uppercase in the original key!

![](JBreward.png)