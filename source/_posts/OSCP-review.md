---
title: Yet another OSCP war story 
date: 2022-08-03 13:43:00
tags:
 - Certificate
cover: /img/OSCP-logo.png
---

I passed my OSCP in my first attempt (70 + 10)! I want to share my experience because I learned so much by reading other's war stories!

## Background

- 2nd year University Student
- start to play with computers since 6 years old
- did 3 years of competitive programming (solving questions like those in leetcode) in high school using CPP
- 4 years Linux user. (began with raspberry Pi)


I grew interest in Cybersecurity because of `liveoverflow`. I I also learned basic computer network, assembly / reverse engineering, basic cryptography right before my univeristy.

## Preparation

I brought 365 days subscription last year. I mainly use two summers during school year to study for OSCP.

I followed the TJnull's list, just like almost everyone else. Here's what I have done:

### StandAlone Machines:

- 40+ HackTheBox machines from the list
- Every (43) Proving Ground Machines from the list
- Every exercises from the pdf, with report
- Every online exercise from the pdf

Become familiar with Enumerations and Privilege Escalations takes time and practice.

`nmap`, `hacktricks` and `burpsuite` are my best friend on enumeration. 
Search every port on `hacktricks`, fuzz every field in your web request on `burpsuite` using <https://github.com/1N3/IntruderPayloads>. Don't forget to try bruteforce if everything failed.

For privilege escalation, usually <https://github.com/carlospolop/PEASS-ng> is good enough. Again, search every suspicious result on `hacktricks` and `google`.

Finally, I suggest to NOT waste more than 6 hours on one machines when you practice. Read writeups if you haven't solved it by then. Try to conclude why you didn't solve it and learn from your mistake on your next practice.

### AD:

- 2 AD online practice from the pdf
- 2 AD network in oscp's lab (XOR and SVcorp)

These are pretty important and are similar to the real exams in my opinion.
If you don't have time to do anything else, I would suggest at least finish these.

- 3 AD machines from Proving Ground (Heist, Hutch, and Vault)

Highly recommend doing them, too

I also did following from TryHackMe:

- Attactive Directory
- Active Directory Basics
- Post-Exploitation Baisc
- Attacking Kerberos

I think these are for understanding basic concept about AD.

Also, about your arsenal on AD:

<https://help.offensive-security.com/hc/en-us/articles/4412170923924-OSCP-Exam-Update-01-11-22-FAQ>

If you click this link, you can see some allowed tools under `Which tools are allowed for the new exam?` section. Many of them are pretty OP, so take them as your advantage. I personally love `Rubeus`, `evil-winrm`, `Responder`, `crackmapexec`, `mimikatz`, `bloodhound`.

### BOF:

- Buffer Overflow Prep from TryHackMe

I think it is pretty good, but I don't know if it's enough for oscp or not since I didn't encounter bof in my exam.

## Exam

After reading other's experience of exam on this subreddit, I scheduled my timetable of the exam day:

- start at when you usually start working
- work for a whole day 
- a few hours' sleep
- get up and continue working till the end

I was hoping that I can finish my AD in 4-5 hours and then spend rest of the time on other machines.
However, I stucked on privilege escalation of the first AD machine for 4 hours.

I thought I was going to fail. Therefore I switched to a stand alone machines to test if I was prepared for OSCP in general. Luckily I successfully solved it in 2 hours. This machine also gives me a hint on the AD set. I went back to AD and solved the whole AD set after 12 hours into the exam.

I took a 5 hours sleep and manage to get another foothold. I then spent the last 2 hours making sure I got all the screenshots I need.

## After Exam

I heard offsec speed up their process on grading. Sometimes you could even get your result in less than 48 hours. However, if you took on early to mid August you might wait longer since many officers are going to Defcon.

If you want to know your result a few hours earlier, you could check offensive security student forum. They will add you to a special subforum for cert holder as soon as they passed you. The email will usually comes a few hours later.

## Thought

OSCP is definitely a hard  and challenging journey for me. I realized that I still have a long way to go in this field because there are so many things in OSCP that I could dig into. 

I also want to thanks the communities that I frequent during my OSCP, specifically offsec discord and `r/oscp`. I made many friends and learned so many new things there! The offsec discord is also a life saver when I stucked on proving ground or lab machines!

## AD as in Advertisement

Looking for 12 months interns/junior opportunities in Canada starting 2023 summer 👀

I'm ok with Pentest/red team, application security, sysadmin, etc.

Please give me a job!!!