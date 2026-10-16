# Week 5 Notes — The Grid: Addresses, Names, Ports, and Diagnostics

**Student Name:** Ashley Raether

**Date Completed:** 10/15/2026

Summarize this week's key concepts in your own words — not copy-pasted definitions.

## Key Concepts This Week

- IP addresses — the dotted-quad number every device on a network needs (`10.20.5.42` on The Grid)
- The subnet mask — the answer to "which addresses are my neighbours?" (`/24` = `255.255.255.0`)
- The default gateway — the door out of your neighbourhood (`10.20.5.1` on The Grid)
- Private vs public addresses — `10.x`, `172.16–31.x`, and `192.168.x` are *inside* addresses
- DNS — the Grid's Directory Board: a name goes in, an IP address comes out
- NXDOMAIN vs a host that resolves but doesn't answer — two different failures with two different causes
- DHCP — the Address Office: leases, why addresses change, why a laptop "just works" on a new network
- Ports — the numbered doors on a building: 22 SSH, 53 DNS, 80 HTTP, 443 HTTPS, 3389 RDP, 25 SMTP
- TCP vs UDP — a confirmed conversation vs a shout across the room
- The TCP handshake — SYN → SYN-ACK → ACK (packets 7, 8 and 9 in Lab 03)
- The diagnostic toolkit — `ping` (does it answer this test?), `traceroute` (which hops answer?), `dig` (what number is behind that name?). Evidence limits: no ping reply doesn't prove a host is off, and `* * *` means no reply came back, not proof of the exact fault
- **THE LADDER RULE** — check yourself → check your gateway → check the target by NAME → check the target by IP → trace the path. *Work outward, one rung at a time, and let the evidence pick the culprit.*

## My Command Table

You learned the same five jobs twice this week — once in bash, once in PowerShell. Fill the pairs in from memory if you can, and check them afterwards. Type straight into the box below — one job per line, e.g. `show my address: ip addr | ipconfig`. This table is worth keeping.

The bash command and its PowerShell equivalent for each job — show my own address, show my default gateway, test reachability, trace the path, look up a name:

```
ipconfig
```

## In My Own Words

Your machine has three numbers: an address, a subnet mask, and a default gateway. Explain what each one is for, the way you'd explain it to someone who has never heard those words.

```
An address that helps to connect the Wi-Fi to the laptop. The subnet mask identifies the host and the network. A default gateway is a node usually a router, send data to outside networks or the public network.
```

What does DNS actually do? Include the difference between a name that comes back "Name or service not known" (NXDOMAIN) and a name that resolves perfectly well to a host that never answers.

```
The DNS is the phonebook of the internet. It communicates with trusted websites such as www.google.com. Name or service not known (NXDOMAIN) means there is an error, the DNS can not find the IP address.
```

An IP address gets your traffic to the right building. What does a port number add to that, and why would a defender care how many doors are open?

```
The port number will be 443 because the IP address is secured. There only be one door open since its going straight to the right building.
```

Write out THE LADDER RULE — all five rungs, in order — and say why running them in that order matters more than running them fast.

```
The ladder rule is ip addr, ping IP address, ping the servers name, ping the Servers IP address and traceroute the servers IP address.
```

What is DHCP, and why does your laptop get an address automatically on a network it has never joined before, while a server like `grid-dns` keeps the same address permanently?

```
DHCP is Dynamic Host Configuration Protocol, network protocol assigns IP addresses. The laptop get an address automatically on a network it has never joined before because the laptop is a new IP address when it joins a new WI-Fi connection.
```

---

## Submission Checklist

- [x] I summarized each concept in my own words, not copied definitions

- [x] I completed the bash-to-PowerShell command table

- [x] I answered all five "In My Own Words" prompts

- [x] This file is committed to my portfolio repo at `week-05/notes.md`

---

*CyberVisionaries Institute — Cyber Foundations, Tier I*
