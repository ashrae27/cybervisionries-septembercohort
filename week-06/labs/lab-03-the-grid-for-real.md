# Week 6 Lab 03 — The Grid, For Real

**Student Name:** Ashley Raether

**Date Completed:** 10/22/2026

**Module:** 2 — Networking & Cloud Foundations | **Week:** 6  
**Submission Path:** `week-06/labs/lab-03-the-grid-for-real.md`

---

> ### 🔒 Cloud Heights Security Rule
> Your Bastion link and Cloud Heights password are **private access credentials**. Never paste either into a worksheet, screenshot, GitHub repository, Circle post, or chat message. When taking screenshots, crop out the browser address bar and all login information.

---

## Overview

In Week 5 you ran `ip addr`, `ip route`, `ping`, and `traceroute` in a simulator that always behaved. Today you run the same toolkit against real cloud infrastructure that does **not** always behave the way the textbook implies — and you learn to tell "broken" apart from "normal."

This is an **independent** lab. It tells you what to accomplish; you choose the commands. Expect about 40 minutes.

---

## Lab Environment / Pre-Lab Check

| Component | Details |
|---|---|
| Environment | Cloud Heights — live Ubuntu 22.04 VM, reached through Azure Bastion |
| Commands used | `ip addr`, `ip route`, `ping`, `traceroute`, `curl` |
| Known-good target | **Grid Beacon — `10.60.6.4`** |
| Prerequisite | Week 6 Labs 01–02 |

---

## Part A — Where You Actually Are

### Step 1 — Read Your Own Address

Run the command that lists your interfaces and addresses.

Command and output:

```
ip addr

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
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
3: enP16341s1: <BROADCAST,MULTICAST,SLAVE,UP,LOWER_UP> mtu 1500 qdisc mq master eth0 state UP group default qlen 1000
    link/ether 7c:1e:52:41:ad:04 brd ff:ff:ff:ff:ff:ff
    altname enP16341p0s2
```

Your private IPv4 address and prefix length:

```
169.254.169.254 via 10.60.6.1 dev eth0 proto dhcp src 10.60.6.25 metric 100
```

### Step 2 — Read Your Route

Run the command that shows the routing table.

Command and output:

```
iproute

default via 10.60.6.1 dev eth0 proto dhcp src 10.60.6.25 metric 100 
10.60.6.0/26 dev eth0 proto kernel scope link src 10.60.6.25 metric 100 
10.60.6.1 dev eth0 proto dhcp scope link src 10.60.6.25 metric 100 
168.63.129.16 via 10.60.6.1 dev eth0 proto dhcp src 10.60.6.25 metric 100 
169.254.169.254 via 10.60.6.1 dev eth0 proto dhcp src 10.60.6.25 metric 100 
```

Your default gateway:

```
default via 10.60.6.1 dev eth0 proto dhcp src 10.60.6.25 metric 100 
```

### Step 3 — Compare to Week 5

Compare this live Ubuntu output to what the CLI Simulator produced in Week 5. What looks the same, what looks different, and what surprised you:

```
What looks the same is the commands, ip addr, ip route, and ping, and traceroute. What looks different is that Azure Bastion has a different IP address, Subnet Mask, and IPv4. What surprised me is Linux IPv4 is eth0 and default gateway is called default in the Linux machine.
```

---

## Part B — The Gateway That Does Not Answer

### Step 1 — Ping the Gateway

Ping the default gateway address you recorded. Let it run a few seconds, then stop it.

Command and output:

```
ping 10.60.6.1
```

### Step 2 — Interpret It Correctly

You almost certainly got **no replies**. In Azure, the platform gateway commonly does not answer ICMP. This is **expected platform behaviour** and by itself proves nothing about whether your machine or network is broken.

Explain why "the gateway did not answer ping" is weak evidence:

```
The gateway didn't answer ping because the ping command is responding to the gateway address, but the gateway address is not responding back. The Azure Bastion default gateway IP address doesn't have another VM machine connected to others. The Azure Bastion VM is a private VM, it doesn't communicate with any routers and VMs.
```

---

## Part C — The Known-Good Target

The **Grid Beacon** at `10.60.6.4` is a machine that is known to be up and known to answer. When your first probe fails, you test against something known-good before you conclude anything.

### Step 1 — Ping the Beacon

```
ping 10.60.6.4
```
Output:

```
64 bytes from 10.60.6.4: icmp_seq=1 ttl=64 time=2.09 ms
64 bytes from 10.60.6.4: icmp_seq=2 ttl=64 time=1.10 ms
64 bytes from 10.60.6.4: icmp_seq=3 ttl=64 time=1.14 ms
64 bytes from 10.60.6.4: icmp_seq=4 ttl=64 time=1.23 ms
64 bytes from 10.60.6.4: icmp_seq=5 ttl=64 time=1.25 ms
64 bytes from 10.60.6.4: icmp_seq=6 ttl=64 time=1.15 ms
64 bytes from 10.60.6.4: icmp_seq=7 ttl=64 time=1.20 ms
64 bytes from 10.60.6.4: icmp_seq=8 ttl=64 time=1.18 ms
64 bytes from 10.60.6.4: icmp_seq=9 ttl=64 time=1.25 ms
64 bytes from 10.60.6.4: icmp_seq=10 ttl=64 time=1.20 ms
64 bytes from 10.60.6.4: icmp_seq=11 ttl=64 time=1.13 ms
64 bytes from 10.60.6.4: icmp_seq=12 ttl=64 time=1.83 ms
64 bytes from 10.60.6.4: icmp_seq=13 ttl=64 time=1.37 ms
64 bytes from 10.60.6.4: icmp_seq=14 ttl=64 time=1.14 ms
64 bytes from 10.60.6.4: icmp_seq=15 ttl=64 time=1.21 ms
64 bytes from 10.60.6.4: icmp_seq=16 ttl=64 time=1.16 ms
64 bytes from 10.60.6.4: icmp_seq=17 ttl=64 time=1.17 ms
64 bytes from 10.60.6.4: icmp_seq=18 ttl=64 time=1.15 ms
64 bytes from 10.60.6.4: icmp_seq=19 ttl=64 time=1.22 ms
```

### Step 2 — Trace the Path

```
traceroute 10.60.6.4
```
Output:

```
grid-beacon.internal.cloudapp.net (10.60.6.4)  1.394 ms  1.351 ms  1.334 ms
```

### Step 3 — Ask the Application

```
curl http://10.60.6.4
```
Output:

```
 <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GRID BEACON | CVI CyberFoundations</title>
    <style>
        body {
            background: #071426;
            color: #d9f7ef;
            font-family: monospace;
            max-width: 850px;
            margin: 80px auto;
            padding: 30px;
        }
        .beacon {
            border: 1px solid #31d6a6;
            padding: 35px;
        }
        h1 { color: #31d6a6; }
        .label { color: #8ca8ff; }
        .status { color: #31d6a6; }
        .classified {
            margin-top: 30px;
            border-top: 1px solid #31445e;
            padding-top: 20px;
     }
    </style>
</head>
<body>
<div class="beacon">

    <h1>GRID BEACON</h1>

    <p><span class="label">NODE:</span> grid-beacon</p>
    <p><span class="label">NETWORK:</span> CVI Training Grid</p>
    <p><span class="label">STATUS:</span>
       <span class="status">ONLINE</span></p>

    <p>
        Network beacon established.<br>
        If you reached this node, your route is operational.
    </p>

    <div class="classified">
        <p>INVESTIGATION CHECKPOINT</p>

        <p>
            Observe the path that brought you here.
            The destination is only part of the story.
        </p>

        <p>TRACE ID: CF-NET-0604</p>
    </div>

</div>
</body>
</html>
```

> ### ⚠️ Grid Beacon not responding?
> The Grid Beacon is shared course infrastructure and should normally be available. First, confirm your Cloud Heights VM shows **Running** and that you completed the preceding network checks. Then retry the command once after a minute or two.
>
> If the Grid Beacon still does not respond, **stop this part of the lab and contact your instructor.** Record that the shared service was unavailable; do not treat the result as evidence that your VM or your work is incorrect.
>
> Do not change networking, NSGs, firewall rules, routes, DNS, or any Azure settings to try to reach the beacon.
>
> *Instructor note: a confirmed Grid Beacon outage is an environment issue, not a student error. Affected students may complete this portion of Lab 03 after the service is restored, with no penalty.*

### Step 4 — Record the Application Evidence

The beacon returns a banner and a trace ID. Record exactly what you received:

```
 <title>GRID BEACON | CVI CyberFoundations</title>
    <style>
        body {
            background: #071426;
            color: #d9f7ef;
            font-family: monospace;
            max-width: 850px;
            margin: 80px auto;
            padding: 30px;
        }
        .beacon {
            border: 1px solid #31d6a6;
            padding: 35px;
        }
        h1 { color: #31d6a6; }
        .label { color: #8ca8ff; }
        .status { color: #31d6a6; }
        .classified {
            margin-top: 30px;
            border-top: 1px solid #31445e;
            padding-top: 20px;
TRACE ID: CF-NET-0604
```

Explain the difference between what the `ping` proved and what the `curl` proved:

```
The ping command is making sure the IP address is connecting to a router or a server. Once a ping starts, it sends a message back to the router saying, "Hello, can you send me a couple of packets?" The curl command is a tool used by developers to transfer data to and from another server using the URL syntax.
```

### Step 5 — Capture Your Evidence

Two screenshots, both cropped to the terminal only:

**Required filename:** `vm-toolkit-live.png` — your `ip addr` and `ip route` output

![Live VM toolkit — ip addr and ip route](https://raw.githubusercontent.com/ashrae27/cybervisionries-septembercohort/refs/heads/main/assets/screenshots/week-06/vm-toolkit-live.png)

**Required filename:** `beacon-reply.png` — your beacon ping/traceroute/curl evidence

![Grid Beacon reply](https://raw.githubusercontent.com/ashrae27/cybervisionries-septembercohort/refs/heads/main/assets/screenshots/week-06/beacon-reply.png)

---

## Part D — Rewrite the Ladder Rule

Week 5 taught the Ladder Rule: test the near thing before the far thing. Real infrastructure adds a wrinkle — a silent rung is not automatically a broken rung.

Rewrite the Ladder Rule in your own words so that it survives real cloud infrastructure. Your version must include both **route/path evidence** and **a known-good target**:

```
Start with running the IP address, ping the default gateway to make sure it sends back any packets, if the ping working, use the dig command to use the default gateway IP address to look up what kind of IP address belongs to, it mostly belongs to an operating system or in public. Finally, use the traceroute command to see if the VM or the operating system is connected to any hops(routers).
```

---

## Analysis Questions

**Analysis Question 1.** Your ping to the gateway failed and your ping to the beacon succeeded. What does that pair of results, taken together, prove about your machine's networking? *(Minimum 3 sentences.)*

```
My ping gateway failed because my default gateway is personal and kept private. The ping to the beacon succeeded because the beacon's default gateway is different, and the beacon's IP address is on a different operating machine. You can not ping your own default gateway.
```

**Analysis Question 2.** Why is `traceroute` useful even when `ping` already answered? What extra thing does it show you? *(Minimum 2 sentences.)*

```
Traceroute is useful when ping is already answered, because if the ping answer the default gateway by sending an infinite amount of packets, you can use the traceroute command to see how many hops(routers) are connected to the default gateway. If it's connected to any hops, it shows how many hops to get to the server. If it doesn't have any hops, it is not connected to a server. 
```

**Analysis Question 3.** A service is unreachable and ping to it succeeds. Where would you look next, and why is "the network is fine" an incomplete answer? *(Minimum 3 sentences.)*

```
A service is unreachable and pinging it to succeeds because the service's private IP address is not registered and not a hostname. The network is fine, because it receives back packets from the ping command and the network is now registered. The service is not reachable because the instructor registered the private IP address.
```

**Analysis Question 4.** Something already controls what is allowed to reach your machine in Cloud Heights. If you could decide those rules, what would you want to allow, what would you want to block, and who in an organization should get to make that decision? *(Minimum 3 sentences.)*

```
I would allow trusted IP addresses from my colleagues, instructors, and people I can trust. I would block defenders and people I don't trust who are trying to find my private IP address. The organization should make a smart decision to secure the private IP addresses from those who try to find them.
```

---

## Submission Checklist

- [x] `ip addr` output recorded and own private IP/prefix identified (Part A)

- [x] `ip route` output recorded and default gateway identified (Part A)

- [x] Live output compared to the Week 5 simulator (Part A, Step 3)

- [x] Gateway pinged and the silent result interpreted correctly (Part B)

- [x] Beacon `ping`, `traceroute`, and `curl` all run and recorded (Part C)

- [x] Beacon banner and TRACE ID recorded (Part C, Step 4)

- [x] `vm-toolkit-live.png` and `beacon-reply.png` captured, cropped, uploaded to `assets/screenshots/week-06/` (Part C, Step 5)

- [x] Ladder Rule rewritten with route evidence + known-good target (Part D)

- [x] All four Analysis Questions answered (minimum sentence counts met)

- [x] This file is committed to your portfolio repo at `week-06/labs/lab-03-the-grid-for-real.md`

---

## GitHub Commit Subsection

1. Open **Week 6 → Lab 03: The Grid, For Real** in the Lab Portal.
2. Fill in the worksheet fields and upload both screenshots to `assets/screenshots/week-06/`.
3. Click **Submit to GitHub** — the Portal commits to `week-06/labs/lab-03-the-grid-for-real.md`.

---

*CyberVisionaries Institute · Cyber Foundations · Tier I*
