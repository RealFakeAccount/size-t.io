---
title: Jetbrain解谜
date: 2020-03-11 11:29:17
tags:
 - 中文
 - writeups
category:
 - just for fun
cover: /images/JBmainpage.png
---



<https://twitter.com/jetbrains/status/1236986174075482113>

Jetbrain团队在自己的twitter上发了一个解谜. 刚好手上没什么事, 就看了看.

```text
JetBrains Quest begins… #JetBrainsQuest
48 61 76 65 20 79 6f 75 20 73 65 65 6e 20 74 68 65 20 73 6f 75 72 63 65 20 63 6f 64 65 20 6f 66 20 74 68 65 20 4a 65 74 42 72 61 69 6e 73 20 77 65 62 73 69 74 65 3f
```
明显的十六进制. 扔到十六进制转换器里面就好.

```text
Have you seen the source code of the JetBrains website?
```

Jetbrain的官网是 <https://www.jetbrains.com/>

都说的这么直白了,那就在source code里面找找.

找了几个关键词, 最终在`/html/body/div/div[2]`看到了我们要的信息:
```

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
嗯... 这个key要记好`Good luck! == Jrrg#oxfn$`

下一步也很明显了. 但是注意, 这个地方列出来的所有软件都不是"joke"

![](JBproducts.png)

..真正的joke在"find your tool"里面

![](JBreal.png)

JK?

![](JBquest_prime.png)

对了.

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

<https://jb.gg/574>

![](JBfollow.png)

毫无头绪. 看起来是某个网址的一部分. 直接高搜算了.

`"MPS-31816 site:jetbrains.com"`

找到了一个网址:

<https://youtrack.jetbrains.com/issue/MPS-31816>

```text
“The key is to think back to the beginning.” -- The JetBrains Quest team

Qlfh$#Li#|rx#duh#uhdglqj#wklv#|rx#pxvw#kdyh#zrunhg#rxw#krz#wr#ghfu|sw#lw1#Wklv#lv#rxu#lvvxh#wudfnhu#ghvljqhg#iru#djloh#whdpv1#Lw#lv#iuhh#iru#xs#wr#6#xvhuv#lq#Forxg#dqg#iru#43#xvhuv#lq#Vwdqgdorqh/#vr#li#|rx#zdqw#wr#jlyh#lw#d#jr#lq#|rxu#whdp#wkhq#zh#wrwdoo|#uhfrpphqg#lw1#|rx#kdyh#ilqlvkhg#wkh#iluvw#Txhvw/#qrz#lw“v#wlph#wr#uhghhp#|rxu#iluvw#sul}h1#Wkh#frgh#iru#wkh#iluvw#txhvw#lv#‟WkhGulyhWrGhyhors†1#Jr#wr#wkh#Txhvw#Sdjh#dqg#xvh#wkh#frgh#wr#fodlp#|rxu#sul}h1#kwwsv=22zzz1mhweudlqv1frp2surpr2txhvw2
```

结合最开始给的key, 我猜这个是*简单替换密码*

慢慢动手解开:

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


```text
nice! if you are reading this you must have worked out how to decrypt it. this is our issue tracker designed for agile teams. it is free for up to 6 users in cloud and for 43 users in standalone/ so 
if you want to give it a go in your team then we totally recommend it. you have finished the first quest/ now it“s time to redeem your first price. the code for the first quest is ‟thedrivetodevelop†. go to the quest page and use the code to claim your price. https://www.jetbrains.com/promo/quest/
```
注意解的时候我们把所有字母换成小写了,最后输入密钥的时候要换回大写.

![](JBreward.png)

搞定.
