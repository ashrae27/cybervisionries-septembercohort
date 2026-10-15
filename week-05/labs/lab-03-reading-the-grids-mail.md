# Week 5 Lab 03 — Reading the Grid's Mail (Packet Inspector)

**Student Name:** Ashley Raether

**Date Completed:** 10/15/2026

**Module:** 2 — Networking & Cloud Foundations | **Week:** 5  
**Submission Path:** `week-05/labs/lab-03-reading-the-grids-mail.md`

---

## Overview

Lesson 4 showed you the three panes of a packet analyzer — the packet list, the detail pane, and the filter bar — and told you that professionals live in this tool. This lab is where you stop watching and start driving. You'll open a recorded minute of traffic on The Grid and read it packet by packet: a name lookup (Part B), a handshake and the message that followed it (Part C), and one conversation that refuses to be read at all.

**The capture is the same for every student.** It's a simplified teaching capture, not a live network — fifteen packets, built to show one idea at a time and replayed identically for everyone. Real captures contain far more, and a real HTTPS conversation contains more TLS packets than the one shown here. That means your numbers should match your classmates' exactly. If yours don't, you've filtered something out; clear the filter and look again.

**Nothing here can break anything.** You are reading a recording. There is no traffic to disturb and nothing to configure.

---

## Lab Environment / Pre-Lab Check

| Component | Details |
|---|---|
| Environment | CyberFoundations **Packet Inspector** — browser-based, inside the Lab Portal. Nothing to install. You will never install Wireshark for this course |
| Where to find it | Lab Portal main navigation, alongside the **CLI Simulator** |
| Capture | "The Grid — Workstation Capture." Canned and identical for every student |
| Prerequisite | Week 5, Lesson 3 (ports, the handshake) and Lesson 4 (the three panes) completed. Lab 01 recommended first — Part B builds directly on it |
| Filters available | `dns` · `icmp` · `tcp` · `udp` · `http` · `tls` · `ip.addr == x.x.x.x` · `tcp.port == N` · `udp.port == N`. A filter the inspector doesn't understand shows a red message instead of a list — fix the spelling and try again |
| Time | Plan for 30–40 minutes, including this worksheet |

**Before you start:** log into the Lab Portal, open **Week 5 → Packet Inspector**, and load the capture named **"The Grid — Workstation Capture."** You should see a list of packets across the top, an empty detail pane below it, and a filter bar above everything. **Two-tab workflow:** keep this worksheet open in a second browser tab — look in the Inspector tab, record here, and Save Progress as you go.

**Get your screenshot tool ready now.** **Windows:** `Win + Shift + S` · **Mac:** `Cmd + Shift + 4`, then drag to capture. You'll need it twice in this lab, and both screenshots are required.

**A note on filters:** a filter never deletes packets. It hides the ones that don't match so you can concentrate. Clearing the filter box brings everything back. This matters in Part A — count *before* you filter anything.

---

## Part A — Orientation

### Step 1 — Count the Whole Capture

With the filter bar **empty**, look at the packet list and count how many packets the capture contains. Every packet has a number in the first column, so the last row tells you the answer without counting by hand.

The total number of packets in the capture:

```
15 packets
```

### Step 2 — Inventory the Protocols

Scan the **Protocol** column from top to bottom and write down every distinct protocol name you see. There are five. You met all five in Lessons 2, 3 and 4 — this is the first time you're seeing them as labelled traffic rather than as ideas.

The protocols that appear in this capture:

```
DNS, ICMP, TCP, TLS, and HTTP
```

### Step 3 — Read the Columns

Four columns do most of the work in a packet analyzer. In your own words — not the Lesson 4 wording — write one plain sentence for each: what does it tell you, and what question does it answer?

What the Source column tells you:

```
The source column shows the original address of the captured packet.
```

What the Destination column tells you:

```
The destination column shows the target IP address of the host.
```

What the Protocol column tells you:

```
List of protocols for each IP addresses
```

What the Info column tells you:

```
The information column is communicating with the IP addresses by sending a message. 
```

### Step 4 — Spot Your Own Machine

One address appears more often than any other, and it's the one sending most of the requests. That's the workstation the capture was taken from — the same address you recorded in Lab 01.

The workstation's IP address, and how you worked out it was the workstation:

```
The workstation IP address is 10.20.5.42. I worked out the IP address by navigating the workstation.
```

---

## Part B — Follow a DNS Lookup

In Lab 01 you ran `dig foundry-archive.grid.local` and read a tidy answer: a name went in, an IP address came out. You saw the *result*. Now you're going to see the actual conversation that produced it — the question travelling across the wire and the answer coming back.

### Step 1 — Filter for DNS

Type `dns` into the filter bar and apply it. The packet list shrinks to the name-lookup traffic only.

The packet numbers that remain after the `dns` filter:

```
1	0.000	10.20.5.42	10.20.5.10	DNS	Standard query A foundry-archive.grid.local
2	0.014	10.20.5.10	10.20.5.42	DNS	Standard query response A 10.20.5.20
```

### Step 2 — Read the Question

Click the first of your two DNS packets and read its Info column and detail pane. This is the query — your workstation asking the Directory Board a question.

The packet number of the query, and the name being asked about:

```
1	0.000	10.20.5.42	10.20.5.10	DNS	Standard query A foundry-archive.grid.local
```

The source and destination addresses of the query — who asked, and who was asked:

```
Source address is 10.20.5.42, and the destination address is	10.20.5.1.
```

### Step 3 — Read the Answer

Now click the second DNS packet. This is the response coming back the other way.

The packet number of the response, and the IP address it returned:

```
2	0.014	10.20.5.10	10.20.5.42	DNS	Standard query response A 10.20.5.20
```

### Step 4 — Find the Door

DNS doesn't just travel to an address — it travels to a specific **port** on that address, the way Lesson 3 described a numbered door on a building. Open the detail pane on either DNS packet and find the port number the lookup used.

The port number DNS used here:

```
Port 53
```

### Step 5 — Tie It Back to Lab 01

This is the same lookup you ran with `dig` in Lab 01 — same name, same answer, same DNS server. The difference is the altitude you're viewing it from. `dig` handed you the conclusion; the Packet Inspector shows you the two messages that produced it.

In two or three sentences: what did the packet view show you that `dig` did not?

```
The Dig command didn't show me the protocol. The dig command showed me the source, port and the destination.
```

### Step 6 — Capture Screenshot 1 (REQUIRED)

With the `dns` filter still applied and one of the two DNS packets selected, take a screenshot showing the filter bar, the filtered packet list, and the detail pane. Name it exactly **`packet-dns-query.png`**. Upload instructions are in the GitHub Commit section.

---

## Part C — Doors and the Handshake

Lesson 3 told the TCP handshake as a knock at a door: **SYN** ("knock"), **SYN-ACK** ("who's there — come in"), **ACK** ("thanks"). You're about to watch one happen.

### Step 1 — Filter for Port 443

Clear the `dns` filter and enter `tcp.port == 443` instead. Port 443 is HTTPS — one of the well-known doors from Lesson 3.

The packet numbers that remain after the `tcp.port == 443` filter:

```
7	2.100	10.20.5.42	10.20.5.20	TCP	51514 → 443 [SYN] Seq=0 Win=64240
8	2.102	10.20.5.20	10.20.5.42	TCP	443 → 51514 [SYN, ACK] Seq=0 Ack=1
9	2.103	10.20.5.42	10.20.5.20	TCP	51514 → 443 [ACK] Seq=1 Ack=1
10	2.140	10.20.5.42	10.20.5.20	TLS	Client Hello (TLS handshake, SNI=foundry-archive.grid.local)
```

### Step 2 — Identify the Three-Step Handshake

Three of those packets are the handshake itself. Find each one by reading the flags in the Info column, and record its number, its direction (which address sent it to which), and which step of the handshake it is.

The SYN — packet number and direction:

```
7	2.100	10.20.5.42	10.20.5.20	TCP	51514 → 443 [SYN] Seq=0 Win=64240
```

The SYN-ACK — packet number and direction:

```
8	2.102	10.20.5.20	10.20.5.42	TCP	443 → 51514 [SYN, ACK] Seq=0 Ack=1
```

The ACK — packet number and direction:

```
9	2.103	10.20.5.42	10.20.5.20	TCP	51514 → 443 [ACK] Seq=1 Ack=1
```

### Step 3 — Notice the Two Port Numbers

Look at the Info column on the SYN packet. Two port numbers appear: a high, odd-looking one on your workstation's side, and 443 on the server's side. Only one of them is a "well-known door" — the other is a temporary one your machine picked for this conversation.

The two port numbers, and which belongs to the server:

```
9	2.103	10.20.5.42	10.20.5.20	TCP	51514 → 443 [ACK] Seq=1 Ack=1
10	2.140	10.20.5.42	10.20.5.20	TLS	Client Hello (TLS handshake, SNI=foundry-archive.grid.local)

```

### Step 4 — Switch to the Plain Conversation

Clear the filter and enter `http` instead. This is a different conversation to a different machine on The Grid — the notice board — on port 80.

The packet numbers that remain after the `http` filter:

```
14	3.240	10.20.5.42	10.20.5.25	HTTP	GET /shift-notice.html HTTP/1.1
15	3.301	10.20.5.25	10.20.5.42	HTTP	HTTP/1.1 200 OK (text/html)
```

### Step 5 — Open the Request and Read It

Click **packet 14** and expand its detail pane all the way. Unlike everything you've read so far, this packet's contents are ordinary text — you can simply read them, the way you'd read a note left on a desk.

The request line at the top of packet 14 (the method, the page, and the version):

```
GET /shift-notice.html HTTP/1.1

```

The Host line — which machine the request was addressed to:

```
Host: grid-notice.grid.local
```

Every other readable line in packet 14's detail pane:

```
User-Agent: GridBrowser/2.4
X-Staff-Code: FOUNDRY-2026-STOREROOM
```

### Step 6 — Notice What You Just Read

One of those lines is not like the others. It carries a value that looks like an internal code rather than a technical setting.

The name of that header and the exact value it carries:

```
HTTP
14	3.240	10.20.5.42	10.20.5.25	HTTP	GET /shift-notice.html HTTP/1.1
15	3.301	10.20.5.25	10.20.5.42	HTTP	HTTP/1.1 200 OK (text/html)
```

In one or two sentences: if you were sitting on this network with a packet analyzer open, what would you now know that you were never meant to know?

```
I know how to use the packet analyzer by learning how to use the packet analyzer by using the commands I am learning to navigate the packet analyzer. 
```

### Step 7 — Capture Screenshot 2 (REQUIRED)

With the `http` filter applied and **packet 14** selected and expanded so the readable lines are visible, take a screenshot. Name it exactly **`packet-http-plaintext.png`**.

### Step 8 — Now Try to Read the Other One

Clear the filter and click **packet 10** — the TLS **Client Hello** from the port 443 conversation you examined in Steps 1–3. Expand its detail pane and compare it with packet 14.

> **Run →** clear the filter, click packet 10 · **Look for →** the *Transport Layer Security* layers and the raw bytes at the bottom · **Record →** what you see, in your own words

Here's what's really going on. The Client Hello is the browser's opening "hello" in the TLS handshake — it offers which TLS versions and ciphers it supports and names the site it wants (`foundry-archive.grid.local`). It is **binary**, so the bottom pane shows bytes (`16` = a handshake record, `01` = Client Hello) instead of words like packet 14. But it is **not secret**: the inspector has already decoded those bytes into the fields above. **Not being plain text is not the same thing as being encrypted.**

What TLS protects comes *after* the handshake finishes: the actual page request and response travel as encrypted **application data**. If packet 14's request had been sent over HTTPS, an eavesdropper would see that encrypted application data — the address, ports and size — but not the `X-Staff-Code` line. This simplified capture leaves those later TLS packets out.

What packet 10's detail pane shows you, described in your own words:

```
Packet 10 shows a message back saying Client Hello crypted instead of being encrypted scrambled bunch of words. The message is not-so secret anymore; it has been shown to everyone.
```

Compare it to packet 14 — what can you tell about packet 10 from the packet list and its decoded fields, and what would an eavesdropper *not* be able to read once the HTTPS conversation moved on to encrypted application data?

```
The eavesdropper won't be able to read the "Client Hello" message the HTTPS conversation is moved on to the encrypted application data.
```

**You'll go deeper later in the course** (Week 9 covers certificates and TLS). For now, hold onto the distinction: the handshake is visible and decodable; the conversation it protects is not. Analysis Question 4 asks what you make of it.

---

## Analysis Questions

**Analysis Question 1.** In Part A you counted the packets before applying any filter. Explain why a filter is a *view* rather than a deletion, and describe a situation where forgetting that could lead an analyst to a wrong conclusion. *(Minimum 3 sentences.)*

```
A filter is a view rather than a deletion because it is important to count how many packets are there in the packet filter. In the professional field, there are thousands to millions of packets. An analyst could lead to a wrong conclusion is forgetting to look how much packets are there in the filter before using the filter.
```

**Analysis Question 2.** You have now seen the same DNS lookup twice — once as `dig` output in Lab 01, once as two packets here. Describe what each view is good for, and name one investigation where you would specifically want the packet view. *(Minimum 3 sentences.)*

```
The Dig command is good for viewing the source IP address and ports of the destination IP address. The packet view is good for viewing the protocol, destination, source, time, and information. The dig and the packet view are kind of similar, but different answers.
```

**Analysis Question 3.** The handshake took three packets and about three milliseconds before a single byte of real content moved. Using the knock-at-the-door analogy from Lesson 3, explain what those three packets accomplish and why a connection would be less reliable without them. *(Minimum 3 sentences.)*

```
The three packets are communicating with each other by using the TCP handshake protocol. The three packets communicate with each other by sending a message to the client telling the client "hello. The connection would be less reliable without them it would be hard to communicate without using the ports, in order to communicate, you need to use ports.
```

**Analysis Question 4.** You read packet 14 word for word as plain text, while packet 10 was a decoded TLS handshake with no readable page content — same capture, same network, same workstation. What do you think explains the difference between plain HTTP and HTTPS here, and what would TLS have protected once the handshake finished? And why does it matter that the one you *could* read contained a staff code? Give us your best reasoning from what you observed. *(Minimum 4 sentences.)*

```
Plain text HTTP is not secure; it is easier to eavesdrop on the conversation. The conversations are not encrypted. HTTPS is secure; it is harder to eavesdrop on the conversation. The conversation is harder to read when it's encrypted. The TLS should protect the message "Client Hello" once the handshake is finished.
```

---

## Submission Checklist

- [x] Total packet count recorded with the filter bar empty (Part A, Step 1)

- [x] All five protocols listed (Part A, Step 2)

- [x] Source, Destination, Protocol and Info columns each explained in your own words (Part A, Step 3)

- [x] Workstation address identified with reasoning (Part A, Step 4)

- [x] `dns` filter applied; query and response packets identified by number (Part B, Steps 1–3)

- [x] Hostname queried, IP address returned, and port number recorded (Part B, Steps 2–4)

- [x] Lab 01 comparison written (Part B, Step 5)

- [x] **REQUIRED:** `packet-dns-query.png` uploaded to `assets/screenshots/week-05/` and its filename recorded (Part B, Step 6)

- [x] `tcp.port == 443` filter applied; SYN, SYN-ACK and ACK identified by number *and* direction (Part C, Steps 1–2)

- [x] `http` filter applied; the remaining packet numbers recorded (Part C, Step 4)

- [x] Both port numbers recorded, server's port identified (Part C, Step 3)

- [x] Packet 14's readable lines recorded, including the staff-code header and its exact value (Part C, Steps 5–6)

- [x] **REQUIRED:** `packet-http-plaintext.png` uploaded to `assets/screenshots/week-05/` and its filename recorded (Part C, Step 7)

- [x] Packet 10 (TLS Client Hello) opened and its contrast with packet 14's plain HTTP described (Part C, Step 8)

- [x] All four Analysis Questions answered (minimum sentence counts met)

- [x] This file is committed to your portfolio repo at `week-05/labs/lab-03-reading-the-grids-mail.md`

---

## GitHub Commit Subsection

This lab's written answers are submitted through the **CyberFoundations Lab Portal**, the same way as Week 4.

1. Go to the CyberFoundations Lab Portal and sign in.
2. Open **Week 5 → Lab 03: Reading the Grid's Mail**.
3. Fill in the worksheet fields — they match the steps and questions in this file.
4. Connect your GitHub account if you haven't already (one-time setup), and select your portfolio repo.
5. Click **Submit to GitHub**. The Portal commits the completed file to `week-05/labs/lab-03-reading-the-grids-mail.md` for you.

**📸 REQUIRED — both screenshots.** This lab has two, and both are graded:

| Screenshot | From | Filename |
|---|---|---|
| Filtered DNS view with a query packet selected | Part B, Step 6 | `packet-dns-query.png` |
| Packet 14 expanded, readable lines visible | Part C, Step 7 | `packet-http-plaintext.png` |

1. Go to your portfolio repository on GitHub.com and navigate to `assets/screenshots/week-05/` (create the folder if this is your first Week 5 screenshot).
2. Click **Add file → Upload files**, drag both images in, named exactly as above (lowercase, hyphens, no spaces).
3. Scroll down and click **Commit changes**.
4. Click each uploaded image's filename to open it and confirm the packet detail is readable at full size.
5. Record both filenames below so your grader knows to look for them.

The filename of your DNS screenshot:

```
https://private-user-images.githubusercontent.com/88813019/674997919-90fb831f-2170-4641-9d14-681879881c10.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3OTIwODkxODksIm5iZiI6MTc5MjA4ODg4OSwicGF0aCI6Ii84ODgxMzAxOS82NzQ5OTc5MTktOTBmYjgzMWYtMjE3MC00NjQxLTlkMTQtNjgxODc5ODgxYzEwLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjEwMTUlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYxMDE1VDE4MjgwOVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWNlOTIxZmQxNGY4YmQ5Y2ZmNjU0NjhiN2ZjMTkwNjM3N2RlZmE0ZjZhNzE1Y2MyN2I5YTUwODMyZDA1ZDRmNTgmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.Z85iakTf5gNNIU0PwFLrhcP5D2490ux4xlkw0-toLWI
```

The filename of your packet 14 screenshot:

```
https://private-user-images.githubusercontent.com/88813019/674997919-90fb831f-2170-4641-9d14-681879881c10.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3OTIwODkxODksIm5iZiI6MTc5MjA4ODg4OSwicGF0aCI6Ii84ODgxMzAxOS82NzQ5OTc5MTktOTBmYjgzMWYtMjE3MC00NjQxLTlkMTQtNjgxODc5ODgxYzEwLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNjEwMTUlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjYxMDE1VDE4MjgwOVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPWNlOTIxZmQxNGY4YmQ5Y2ZmNjU0NjhiN2ZjMTkwNjM3N2RlZmE0ZjZhNzE1Y2MyN2I5YTUwODMyZDA1ZDRmNTgmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JnJlc3BvbnNlLWNvbnRlbnQtdHlwZT1pbWFnZSUyRnBuZyJ9.Z85iakTf5gNNIU0PwFLrhcP5D2490ux4xlkw0-toLWI
```

Both screenshots live in `assets/screenshots/week-05/` in your repository. They do not need to be linked inside this worksheet.

**Commit message tip:** name the work, not the file type — *"Add Week 5 Lab 03 packet analysis evidence"* reads far better to an employer browsing your repo than "update."

---

*CyberVisionaries Institute · Cyber Foundations · Tier I*
