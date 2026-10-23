# Week 6 Lab 05 — Layer Detective

**Student Name:** Ashley Raether

**Date Completed:** 10/22/2026

**Module:** 2 — Networking & Cloud Foundations | **Week:** 6  
**Submission Path:** `week-06/labs/lab-05-layer-detective.md`

---

## Overview

**This is a SHORT lab — 20 to 30 minutes — and it needs no VM.** No Cloud Heights session, no simulator, no screenshot. This is a thinking lab: you take the evidence you have already collected in Weeks 5 and 6 and sort it into layers.

This is an **independent** lab.

---

## Lab Environment / Pre-Lab Check

| Component | Details |
|---|---|
| Environment | This worksheet only — nothing to start, nothing to connect to |
| Prerequisite | Week 5 labs and Week 6 Labs 01–04 |
| Screenshot | None required |

---

## Part A — The Seven-Row Table

Fill in every row. For the last column, name one **real thing you personally saw** in Weeks 5–6 that belongs at that layer.

| # | Layer name | One-line job | Real thing from Weeks 5–6 |
| --- | --- | --- | --- |
| 7 | Application | Access websites and emails | Week 5 |
| 6 | Presentation | Encrypts data | Week 5-6 |
| 5 | Session | HTTP, HTTPS, | Week 5  |
| 4 | Transportation | TCP, UDP | Week 5-6 |
| 3 | Network | IP, ICMP, Packets | Week 6 |
| 2 | Data Link | Ethernet, Wi-Fi, VLAN, NAT | Week 5-6 |
| 1 | Physical  | Hardware, cables, Wi-Fi signals, servers | Week 5 |

---

## Part B — Case Files

For each case, name the layer where the problem lives, and name the evidence proving the layers **below** it were already working.

### Case File 1 — The Name That Went Nowhere

A hostname lookup fails, but pinging the machine's IP address directly succeeds.

Layer:

```
Layer 3
```

Evidence that the layers below were working:

```
Layers 1 and 2 are working, the hardware to run the device and Wi-fi helping to connect the device. The VM doesn't have a hostname; no one owns the VM, but the hardware, data, and network in the machine are working 
```

### Case File 2 — Permission Denied

`ssh` to a host returns `Permission denied` after a password prompt.

Layer:

```
Layer 7
```

Evidence that the layers below were working:

```
Layers 1-5 are working, but layer 7 is not working. After the host types the correct password, the ssh denied the login because the host needs permission to gain access to someone's VM by using the SSH command.
```

### Case File 3 — The Cable Story

A machine reports no link on its interface and has no address at all.

Layer:

```
Layer 1
```

Evidence and reasoning:

```
The machine is not registered for an interface link or an IP address. The machine is built with hardware.
```

### Case File 4 — Ping Works, The Page Does Not

`ping` to a server succeeds, but `curl http://<that server>` returns nothing useful.

Layer:

```
Layer 7
```

Evidence that the layers below were working:

```
The ping command receives the server's packets. The curl http://<that server> is not a website, it wont return, its useful.
```

### Case File 5 — Wrong Neighbourhood

A machine has an address, but its default route points somewhere that cannot forward its traffic.

Layer:

```
Layer 4
```

Evidence and reasoning:

```
The machine has an IP address that is registered but the machines default route can not connect to any ports. The machine's default route has difficulty communicating with other machines. 
```

---

## Part C — The Silent Gateway Case

In Lab 03 the Azure default gateway did not answer your ping. However, your VM had a valid default route configured, and your local communication with the Grid Beacon — the ping replies, the HTTP banner, and `TRACE ID: CF-NET-0604` — succeeded.

A failed gateway ping is one piece of evidence — not automatically proof of a gateway or network failure. But the evidence you weigh against it has to be the right kind of evidence.

The Grid Beacon at `10.60.6.4` sits on the same local subnet as your VM (`10.60.6.0/26`). Reaching it proves **local-subnet connectivity** — that traffic never crosses the default gateway, so beacon success alone cannot prove the gateway forwarded anything. Your `ip route` output proves a **default route is configured** — your VM knows where it intends to send non-local traffic — but it does not prove the gateway forwarded that traffic. The evidence that demonstrates the **default path is functioning** is successful communication with a destination outside `10.60.6.0/26`, such as the outbound internet access through NAT that you examined in Lab 04.

### Step 1 — Rule on the Case

Is the failed gateway ping enough evidence to declare a network-layer failure? Explain your answer using the other evidence you collected. In your response, distinguish between:

- evidence that proves **local-subnet connectivity**
- evidence that proves a **default route is configured**
- evidence that supports **successful off-subnet connectivity**

```
The failed gateway ping doesn't have enough evidence to declare a network-layer failure because the ping command is looking for the gateway's evidence, and the gateway must not be registered in the VM. Another option is to use the dig and traceroute commands to look for evidence. Ping sometimes doesn't cooperate with the default gateway.
```

### Step 2 — Name the Correct Conclusion

For each of these four results, state what it actually proves: the Grid Beacon at `10.60.6.4` answering, the default route shown by `ip route`, a successful connection to a destination outside your local subnet, and the gateway's failed ping. Then state the rule you would give a junior colleague about the difference between an observation ("the gateway did not answer my ICMP probe") and a diagnosis ("the gateway is broken"):

```
The default gateway is not broken; it can not reach the local router. Restart the VM by turn it back off, waiting 30 seconds, and then turning it back on. Mistyping the gateway IP address when using the ping command is not receiving ICMP packets. Typing the gateway IP address the correct way will receive ICMP packet.
```

---

## Part D — Two Models, One Job

The OSI model has seven layers. The practical TCP/IP model most engineers speak day to day has four or five.

### Step 1 — Map Them

Briefly show how the seven OSI layers collapse into the practical model:

```
The seven OSI layers collapse into the TCP/IP model, the TCP/IP model only has 4 layers, the seven OSI model has 7 layers. The OSI model has more layers than the TCP/IP model. 
```

### Step 2 — When Each Is Useful

Explain when the seven-layer vocabulary helps and when the practical model is the better tool:

```
The seven-layer vocabulary helps because the seven-layer analogy, think of the OSI a building, a building has floors, the OSI model has 7 floors, TCP/IP model has 4 floors. The OSI model has more information than the TCP/IP model. OSI model is larger than the TCP/IP model.
```

---

## Analysis Questions

**Analysis Question 1.** Explain the Ladder Rule using layer language. What does "test the near thing first" mean when the rungs are layers? *(Minimum 3 sentences.)*

```
The ladder rule is run the ip addr command to find the private and prefix address, run the ip route to find the default gateway address. Run the ping command to the default gateway address to make sure any packets are received from the default gateway. Run dig to see what the default gateway's address belongs to (usually a VM). Run the traceroute command with the default gateway address to see any hops respond to the address to get to the destination with is the server. 
```

**Analysis Question 2.** Why is "which layer is this?" a faster question than "what is broken?" when you are under pressure? *(Minimum 3 sentences.)*

```
"which layer is this" is a faster question than "what is broken?" because the "which layer is this" is easier to respond than the question "what is broken?" If the user can't not understand the one of the layers of the OSI model, you can try to get them an easy answer to explain the layer they're stuck on. Layers are not broken, they respond back when they are responding the correct way.
```

**Analysis Question 3.** Pick one case file from Part B and describe the very next command you would run to confirm your ruling, and what result would change your mind. *(Minimum 2 sentences.)*

```
I choose case file from Part B because the VM machine doesn't have a owner assigned to. Case file 2 Layer 4 failed because it can not show the hostnames on the VM.
```

---

## Submission Checklist

- [x] All seven rows of the OSI table completed with a real Week 5–6 anchor each (Part A)

- [x] All five case files given a layer and supporting evidence (Part B)

- [x] Silent gateway case ruled on correctly (Part C)

- [x] OSI vs. practical TCP/IP model compared (Part D)

- [x] All three Analysis Questions answered (minimum sentence counts met)

- [x] No screenshot required for this lab

- [x] This file is committed to your portfolio repo at `week-06/labs/lab-05-layer-detective.md`

---

## GitHub Commit Subsection

1. Open **Week 6 → Lab 05: Layer Detective** in the Lab Portal.
2. Fill in the worksheet fields.
3. Click **Submit to GitHub** — the Portal commits to `week-06/labs/lab-05-layer-detective.md`.

---

*CyberVisionaries Institute · Cyber Foundations · Tier I*
