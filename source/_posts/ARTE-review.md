---
title: AWS Red Team Expert (ARTE) – My SITREP and review
date: 2025-02-01 17:30:00
tags:
 - Certificate
cover: /img/ARTE_CAN.png
---

# **AWS Red Team Expert (ARTE) – My SITREP and review**  

## **Introduction**  

🌟 If you're looking to level up your **cloud security skills**, the **HackTricks AWS Red Team Expert (ARTE) certification** is a fantastic choice. This credential validates your ability to **penetration test AWS environments**, making it a **valuable certification** for both **offensive and defensive security professionals**.  

AWS has been around since **2006**, yet **red teaming resources** for AWS remain relatively scarce compared to traditional penetration testing domains. Even well-known certifications like **OSCP** don’t cover AWS security extensively. However, AWS is something that **every red teamer and security researcher** will encounter sooner or later.  

That’s exactly why I pursued the **ARTE certification**. Another key reason? **HackTricks!** While preparing for **OSCP**, I found **HackTricks** (by Carlospolop) to be an invaluable resource. Since **ARTE is created by the same author**, I knew it was going to be high-quality content, making it a no-brainer for me.  

Some might ask: **"Why go for a red team cert instead of blue team ones like CCSP or AZ-500?"** Simple: **Red teaming is way more fun!** 😆  

---

## **My Background & Motivation**  

Before taking ARTE, I had:  
✅ **OSCP Certification**  
✅ **CTF Experience**  
✅ **Cloud Security Engineer role** (although I primarily focus on endpoint security)  

However, my biggest challenge in **AWS security** was **thinking like a hacker**. I knew many **attack techniques**, but I didn’t really understand how to **chain them together** effectively. I lacked a structured approach to **AWS red teaming**, which made ARTE the perfect learning opportunity.  

---

## **Exam Preparation**  

### **How I Prepared**  
- **HackTricks** was my **#1 resource**.  
- **AWS official documentation** was also **super useful**.  
- Unfortunately, **there aren’t many AWS red teaming resources** online, so if you know any, let me know!  
- **ChatGPT** also played a role—more on that later.  

### **How Long Did It Take?**  
- **A full Christmas holiday (~14 days) + a few weekends** (total ~30 days).  
- My **study tip**: Everyone learns at a different pace. Start with a few modules, find your speed, and adjust your schedule accordingly.  

### **Most Interesting Things I Learned**  
- **Lambda is super versatile** and fun to explore.  
- **EC2 security from a red team perspective is eye-opening**—it makes you realize how many **misconfigurations** exist in real-world environments.  

---

## **The Exam Experience**  

### **Exam Overview**  
The ARTE exam is a **simulated AWS cloud environment** where you must capture **three flags**—similar to an **Active Directory attack chain in OSCP**.  

🔹 **My Experience:**  
- The **first foothold** was the hardest—**I spent 4 hours** stuck due to an argument mistake.  
- After that, the remaining two flags **only took 3 hours**—once you're in, things move quickly!  

### **A Glimpse of a Flag (Without Spoilers!)**  
One of the flags required me to **identify a misconfiguration** in an AWS cloud component and **exploit it** to gain access.  

### **If I Could Do It Again…**  
- **ENUMERATE, ENUMERATE, ENUMERATE!**  
- **Train with ChatGPT before the exam.** The black-box nature of the test means you'll rely on external resources, so learning how to efficiently **cooperate with AI tools** can be a game-changer.  

---

## **How Does ARTE Compare to OSCP?**  

| Feature | ARTE | OSCP |
|---------|------|------|
| **Tool Freedom** | More freedom | More restrictions |
| **Focus** | Cloud (AWS) | Traditional pentest |
| **Difficulty** | Technical but manageable | More endurance-based |
| **Cost** | **Cheaper** than OSCP | More expensive |
| **Recognizability**| Less known | More famous |

---

## **Who Should Take ARTE?**  

🚀 **Best for:**  
✅ Red Teamers  
✅ Cloud Security Engineers (both offensive & defensive)  
✅ Security Researchers interested in AWS security  

🚀 **Prerequisites:**  
- **OSCP-level knowledge is preferable**, but not required.  
- If you don’t have OSCP, at least be able to solve **Hack The Box easy boxes**.  
- Some **web pentesting & CTF experience** helps, as certain footholds involve **traditional attack techniques** (e.g., **SQL injection**).  

---

## **Final Thoughts & Recommendations**  

### **Has this certification changed my approach to cloud security?**  
**Absolutely.**  
- I can now **plan engagements for AWS environments** more effectively.  
- It also helped me improve **XDR configurations for cloud security**.  

### **Would I take more cloud security certs?**  
- Maybe **OSCE3 or CISSP**.  
- If I ever need **Azure or GCP security**, HackTricks also offers courses for those.  

### **Final Advice for ARTE Candidates**  
✔️ While **cheaper than OffSec certs**, ARTE is still an investment—**but totally worth it** for cloud red teaming.  
✔️ There aren’t many **good AWS red team certs** out there, so **I’m super grateful to Carlos** for creating this course.  

**Thinking of taking ARTE? Have questions? Drop them in the comments!** 🚀  

## **Introduction**  

🌟 If you're looking to level up your **cloud security skills**, the **HackTricks AWS Red Team Expert (ARTE) certification** is a fantastic choice. This credential validates your ability to **penetration test AWS environments**, making it a **valuable certification** for both **offensive and defensive security professionals**.  

AWS has been around since **2006**, yet **red teaming resources** for AWS remain relatively scarce compared to traditional penetration testing domains. Even well-known certifications like **OSCP** don’t cover AWS security extensively. However, AWS is something that **every red teamer and security researcher** will encounter sooner or later.  

That’s exactly why I pursued the **ARTE certification**. Another key reason? **HackTricks!** While preparing for **OSCP**, I found **HackTricks** (by Carlospolop) to be an invaluable resource. Since **ARTE is created by the same author**, I knew it was going to be high-quality content, making it a no-brainer for me.  

Some might ask: **"Why go for a red team cert instead of blue team ones like CCSP or AZ-500?"** Simple: **Red teaming is way more fun!** 😆  

---

## **My Background & Motivation**  

Before taking ARTE, I had:  
✅ **OSCP Certification**  
✅ **CTF Experience**  
✅ **Cloud Security Engineer role** (although I primarily focus on endpoint security)  

However, my biggest challenge in **AWS security** was **thinking like a hacker**. I knew many **attack techniques**, but I didn’t really understand how to **chain them together** effectively. I lacked a structured approach to **AWS red teaming**, which made ARTE the perfect learning opportunity.  

---

## **Exam Preparation**  

### **How I Prepared**  
- **HackTricks** was my **#1 resource**.  
- **AWS official documentation** was also **super useful**.  
- Unfortunately, **there aren’t many AWS red teaming resources** online, so if you know any, let me know!  
- **ChatGPT** also played a role—more on that later.  

### **How Long Did It Take?**  
- **A full Christmas holiday (~14 days) + a few weekends** (total ~30 days).  
- My **study tip**: Everyone learns at a different pace. Start with a few modules, find your speed, and adjust your schedule accordingly.  

### **Most Interesting Things I Learned**  
- **Lambda is super versatile** and fun to explore.  
- **EC2 security from a red team perspective is eye-opening**—it makes you realize how many **misconfigurations** exist in real-world environments.  

---

## **The Exam Experience**  

### **Exam Overview**  
The ARTE exam is a **simulated AWS cloud environment** where you must capture **three flags**—similar to an **Active Directory attack chain in OSCP**.  

🔹 **My Experience:**  
- The **first foothold** was the hardest—**I spent 4 hours** stuck due to an argument mistake.  
- After that, the remaining two flags **only took 3 hours**—once you're in, things move quickly!  

### **A Glimpse of a Flag (Without Spoilers!)**  
One of the flags required me to **identify a misconfiguration** in an AWS cloud component and **exploit it** to gain access.  

### **If I Could Do It Again…**  
- **ENUMERATE, ENUMERATE, ENUMERATE!**  
- **Train with ChatGPT before the exam.** The black-box nature of the test means you'll rely on external resources, so learning how to efficiently **cooperate with AI tools** can be a game-changer.  

---

## **How Does ARTE Compare to OSCP?**  

| Feature | ARTE | OSCP |
|---------|------|------|
| **Tool Freedom** | More freedom | More restrictions |
| **Focus** | Cloud (AWS) | Traditional pentest |
| **Difficulty** | Technical but manageable | More endurance-based |
| **Cost** | **Cheaper** than OSCP | More expensive |
| **Recognizability**| Less known | More famous |

---

## **Who Should Take ARTE?**  

🚀 **Best for:**  
✅ Red Teamers  
✅ Cloud Security Engineers (both offensive & defensive)  
✅ Security Researchers interested in AWS security  

🚀 **Prerequisites:**  
- **OSCP-level knowledge is preferable**, but not required.  
- If you don’t have OSCP, at least be able to solve **Hack The Box easy boxes**.  
- Some **web pentesting & CTF experience** helps, as certain footholds involve **traditional attack techniques** (e.g., **SQL injection**).  

---

## **Final Thoughts & Recommendations**  

### **Has this certification changed my approach to cloud security?**  
**Absolutely.**  
- I can now **plan engagements for AWS environments** more effectively.  
- It also helped me improve **XDR configurations for cloud security**.  

### **Would I take more cloud security certs?**  
- Maybe **OSCE3 or CISSP**.  
- If I ever need **Azure or GCP security**, HackTricks also offers courses for those.  

### **Final Advice for ARTE Candidates**  
✔️ While **cheaper than OffSec certs**, ARTE is still an investment—**but totally worth it** for cloud red teaming.  
✔️ There aren’t many **good AWS red team certs** out there, so **I’m super grateful to Carlos** for creating this course.  
