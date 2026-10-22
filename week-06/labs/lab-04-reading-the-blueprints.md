# Week 6 Lab 04 — Reading the Blueprints

**Student Name:** Ashley Raether

**Date Completed:** 10/22/2026

**Module:** 2 — Networking & Cloud Foundations | **Week:** 6  
**Submission Path:** `week-06/labs/lab-04-reading-the-blueprints.md`

---

> ### 🔒 Cloud Heights Security Rule
> Your Bastion link and Cloud Heights password are **private access credentials**. Never paste either into a worksheet, screenshot, GitHub repository, Circle post, or chat message. When taking screenshots, crop out the browser address bar and all login information.

---

## Overview

**This is a SHORT lab — 15 to 20 minutes.** It is deliberately small. You already have the commands; this lab is about matching a drawing to reality.

The **Cloud Heights Network Blueprint** is displayed at the top of this lab page in the portal. Everything you write about the network's architecture comes from that blueprint or from your own machine — never from a guess.

---

## Lab Environment / Pre-Lab Check

| Component | Details |
|---|---|
| Environment | Cloud Heights — live Ubuntu 22.04 VM, reached through Azure Bastion |
| Source of truth | The Cloud Heights Network Blueprint shown at the top of this lab page |
| Commands used | `ip addr`, `ip route` |
| Known value | Student subnet: **`10.60.6.0/26`** |

---

## Part A — Read the Drawing

### Step 1 — Record the Architecture Values

From the blueprint at the top of this page, record each value **exactly as drawn**. If a value is not shown on the blueprint, write "not shown on blueprint" — do not guess.

| Item | Value from the blueprint |
| --- | --- |
| VNet name | VNet name: vnet-cf-labs |
| VNet address space | Address space: 10.60.6.0/24 |
| Student subnet range | snet-cf-students: 10.60.6.0/26 |

---

## Part B — Verify Against Your Own Machine

### Step 1 — Confirm Your Address Lives in the Subnet

Run `ip addr` and find your private IPv4 address.

Command and output:

```
ip addr

lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 7c:1e:52:41:ad:04 brd ff:ff:ff:ff:ff:ff
    inet 10.60.6.25/26 metric 100 brd 10.60.6.63 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::7e1e:52ff:fe41:ad04/64 scope link 
       valid_lft forever preferred_lft forever
3: enP23215s1: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc mq master eth0 state UP group default qlen 1000
    link/ether 7c:1e:52:41:ad:04 brd ff:ff:ff:ff:ff:ff
    altname enP23215p0s2
```

Your private IP:

```
10.60.6.25/26
```

Explain how you know your address falls inside `10.60.6.0/26` — what range does that prefix actually cover:

```
My address didn't fail anymore because I used the ping command and I received 16 packets and 0% packet loss. The range the prefix actually cover
```

### Step 2 — Confirm Route Behaviour

Run `ip route`.

Command and output:

```
ip route
default via 10.60.6.1 dev eth0 proto dhcp src 10.60.6.25 metric 100 
10.60.6.0/26 dev eth0 proto kernel scope link src 10.60.6.25 metric 100 
10.60.6.1 dev eth0 proto dhcp scope link src 10.60.6.25 metric 100 
168.63.129.16 via 10.60.6.1 dev eth0 proto dhcp src 10.60.6.25 metric 100 
169.254.169.254 via 10.60.6.1 dev eth0 proto dhcp src 10.60.6.25 metric 100 

```

What the default route tells you about traffic that is not destined for your own subnet:

```
default via 10.60.6.1 dev eth0 proto dhcp src 10.60.6.25 metric 100 
```

### Step 3 — Capture Your Evidence

**Required filename:** `blueprint-verified.png`

This must be **your own `ip addr` and `ip route` output** — not a re-screenshot of the blueprint. Crop out the address bar and any login information.

![Blueprint verified — my address inside the student subnet](https://raw.githubusercontent.com/ashrae27/cybervisionries-septembercohort/refs/heads/main/assets/screenshots/week-06/blueprint-verified.png)

---

## Part C — How Traffic Actually Moves

### Step 1 — No Public IP

Your VM has a private address and **no public IP**. Explain what that means for who can reach it directly from the internet:

```
My VM has a private address no public IP address, because the private IP address is my personal IP address and no one can see my private IP address including my collagues, only the instructors can only see my public IP address. The private IP address can't connected it to the internet, it can only connect to my assigned VM.
```

### Step 2 — Outbound vs. Inbound

Outbound internet traffic from your VM leaves through address **translation (NAT)**. Inbound access for you arrives through **Azure Bastion**, not through a public address on the VM.

Explain both directions in your own words:

```
The NAT traffic doesn't go through a public address because the internet is connected to a trusted device, and it's secured by needing a password. The Wi-fi is for homeowners and people I can trust, not for the public. The Azure bastion only connects to a private Wi-fi router for the user to use for educational purpose only.
```

### Step 3 — The Guard Post You Do Not Touch Yet

Each student machine sits behind its own **network security group** — a per-student guard post that decides what traffic is allowed in.

**In Week 6 you do not configure it.** Week 7 is when you take control of those rules.

Write one sentence naming what the guard post does and one sentence stating what you are *not* doing with it this week:

```
The guard post allows any network traffic to go through using a firewall. I am not doing this week is learning how to defend myself, the guard is doing their job to defend the VMs.
```

---

## Analysis Questions

**Analysis Question 1.** Why would an organization put every student machine in one small subnet instead of giving each machine a public address? *(Minimum 3 sentences.)*

```
An organization puts every student machine in a small subnet instead of giving each machine a public address, because the organization gives each student a subnet IP address so the public can not get access to the students' machines. Every student has their own unique private IP address and the student can not share their private IP address to other students. The public IP address is the address the public can only see when they are connected to the guest Wi-fi by using their own personal devices.
```

**Analysis Question 2.** Segmentation means separating a network into parts that cannot freely reach each other. Give one concrete benefit of segmentation during a security incident. *(Minimum 3 sentences.)*

```
One benefit of segmentation during a security incident is when an attacker can access when they break into a network system. The attacker can send a phishing email pretending to be an employee to see if someone takes the bait. If someone clicks on the link the attacker sent, the device is infected and the device that is connected to the server is also infected. The device is not connected to multiple servers, just one.
```

**Analysis Question 3.** A diagram and a live machine disagree about an address range. Which do you trust, what do you do next, and why? *(Minimum 2 sentences.)*

```
A diagram and a live machine disagree about an address range; I trust the live machine because the live machine has its own private IP addresses, default gateways, and subnets. The diagram doesn't have its own private IP address, default gateways, or subnets. What I do next is use a live machine because a live machine is the only option to use instead of using a diagram
```

---

## Submission Checklist

- [x] VNet name, address space, and subnet range recorded from the blueprint (Part A)

- [x] `ip addr` run and own private IP confirmed inside `10.60.6.0/26` (Part B, Step 1)

- [x] `ip route` run and default route behaviour explained (Part B, Step 2)

- [x] `blueprint-verified.png` captured from your own terminal, cropped, uploaded to `assets/screenshots/week-06/` (Part B, Step 3)

- [x] Private address / NAT / Bastion explained (Part C, Steps 1–2)

- [x] Per-student guard post identified — and explicitly not configured this week (Part C, Step 3)

- [x] All three Analysis Questions answered (minimum sentence counts met)

- [x] This file is committed to your portfolio repo at `week-06/labs/lab-04-reading-the-blueprints.md`

---

## GitHub Commit Subsection

1. Open **Week 6 → Lab 04: Reading the Blueprints** in the Lab Portal.
2. Fill in the worksheet fields and upload `blueprint-verified.png` to `assets/screenshots/week-06/`.
3. Click **Submit to GitHub** — the Portal commits to `week-06/labs/lab-04-reading-the-blueprints.md`.

---

*CyberVisionaries Institute · Cyber Foundations · Tier I*
