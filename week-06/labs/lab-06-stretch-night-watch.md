# Week 6 Stretch Lab — Night Watch (Optional)

**Student Name:** Ashley Raether

**Date Completed:** 10/23/2026

**Module:** 2 — Networking & Cloud Foundations | **Week:** 6  
**Submission Path:** `week-06/labs/lab-06-stretch-night-watch.md`

---

## Overview

**This lab is optional.** Skipping it costs you nothing. Your Week 6 submission is complete and full-credit with Labs 01–05 alone, and choosing not to do this does not make your week's work lesser in any way. It is here for students who want to connect Cloud Heights to the network they actually live on. Expect about 30 minutes if you take it on.

**Built-in tools only.** Use commands that already ship with your own computer. **Do not install any software** for this lab.

---

## Lab Environment / Pre-Lab Check

| Component | Details |
|---|---|
| Environment | Your own personal computer — not Cloud Heights |
| Tools | Built-in only: `ipconfig` / `Get-NetIPConfiguration` (Windows) or `ifconfig` / `ip addr` / `netstat -rn` (macOS/Linux), plus `ping` |
| Installs | None. If it needs installing, it is out of scope. |
| Screenshot | Required **only if you submit**: `stretch-real-network.png`, redacted |

> ### 🔒 Redaction Rule
> If you submit this lab, you must redact before uploading. Never publish your home network identity.

---

## Part A — Your Own Address

### Step 1 — Read Your Machine's Network Configuration

Use the built-in command for your operating system to show your address, subnet mask/prefix, and default gateway.

Command you ran:

```
ipconfig
```

Your private IP and prefix/mask (this is a private address — safe to record):

```
 IPv4 Address. . . . . . . . . . . : 192.168.0.90
 Subnet Mask . . . . . . . . . . . : 255.255.255.0
 Default Gateway . . . . . . . . . : fe80::12a7:93ff:fef3:40c9%31
                                     
```

Your default gateway (private address — safe to record):

```
Default gateway: 192.168.0.1
```

**Do not record your public IP address anywhere in this file.**

### Step 2 — Compare to Cloud Heights

Compare your home addressing to your Cloud Heights addressing — address range, prefix size, and how many machines each network could hold:

```
 The network can hold 3 Ethernet machines connected to each other using cables. 
```

---

## Part B — Two Gateways, Two Behaviours

### Step 1 — Ping Your Home Gateway

Ping your own default gateway.

Output:

```
ping 192.168.0.1
```

### Step 2 — Compare to Azure's Silent Gateway

Your home router almost certainly answered. The Azure gateway in Lab 03 did not.

Explain why both behaviours are normal, and what that teaches you about assuming a non-answer means failure:

```
Both behaviors are normal because using the ping command for the default gateway, the server responds back 4 packets 0% packet loss. What teaches me about assuming a non-answer means the ping command can not fail.
```

---

## Part C — Redaction (Required Only If You Submit)

**Required filename:** `stretch-real-network.png`

Redact **before** uploading. Redaction targets:

- your **public IP address**
- your computer's **hostname**
- your **shell username**
- any **ISP-identifying names** (router model strings, provider names, SSIDs)

**Method:** crop the image, or cover the text with **solid opaque boxes**. **Do not use blur or pixelation** — both can be reversed.

![Home network configuration — redacted](https://raw.githubusercontent.com/ashrae27/cybervisionries-septembercohort/refs/heads/main/assets/screenshots/week-06/stretch-real-network.png)

List what you redacted and the method you used:

```
I covered up the sensitive data by using the paint app on my laptop. 
```

---

## Analysis Questions

**Analysis Question 1.** What is genuinely different between the network you sit on at home and the one Cloud Heights sits on, and what is essentially the same? *(Minimum 3 sentences.)*

```
The difference between the network at my home and one at Cloud Heights is that the network at my home is my personal network, and the network at Cloud Heights is the business/companies network. Both of their networks are private, and only trusted people can access the networks. What is the same both have a private IP address and private default gateway's.
```

**Analysis Question 2.** Why is publishing your public IP, hostname, and username together riskier than publishing any one of them alone? *(Minimum 3 sentences.)*

```
Publishing my public IP address, hostname, and username is risky, because they can not be publish in public so untrusted individuals can not see my private information, and it will lose its confidentiality. The public IP address, hostname, and username should be private and will be available for trusted individuals. Professionals who work on my laptop if it has any issues can only see my  public IP address, hostname, and username.
```

---

## Submission Checklist (Only If You Choose to Submit)

- [x] Home address, mask, and gateway recorded — **public IP not recorded**

- [x] Home network compared to Cloud Heights (Part A, Step 2)

- [x] Home gateway pinged and compared to Azure's silent gateway (Part B)

- [x] `stretch-real-network.png` redacted with crop or solid boxes (no blur), uploaded to `assets/screenshots/week-06/`

- [x] Redaction list recorded (Part C)

- [x] Both Analysis Questions answered

- [x] This file is committed to your portfolio repo at `week-06/labs/lab-06-stretch-night-watch.md`

---

## GitHub Commit Subsection

1. Open **Week 6 → Stretch Lab: Night Watch** in the Lab Portal.
2. Fill in the worksheet fields and upload your redacted screenshot to `assets/screenshots/week-06/`.
3. Click **Submit to GitHub** — the Portal commits to `week-06/labs/lab-06-stretch-night-watch.md`.

---

*CyberVisionaries Institute · Cyber Foundations · Tier I*
