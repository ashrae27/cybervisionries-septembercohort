# Week 6 Notes — Cloud Heights: Cloud VMs, SSH, VNets & Layers

**Student Name:** Ashley Raether

**Date Completed:** 10/24/2026

Summarize this week's key concepts in your own words — not copy-pasted definitions. This week moved from the simulated Grid into a real cloud environment, so focus on what you personally observed as well as what each term means.

> **Cloud Heights Security Rule:** Your Bastion shareable link and Cloud Heights password are private access credentials. Never paste either into this file, a screenshot, your GitHub repository, Circle, or a chat message.

## Key Concepts This Week

- **Cloud** — other people's computers, professionally operated and reached over a network
- **Datacenter** — the physical facility where cloud computing equipment lives
- **Region** — a geographic area where a cloud provider operates datacenters
- **Virtual machine (VM)** — a computer created in software; in Cloud Heights, your VM runs on hardware in a real datacenter
- **IaaS / PaaS / SaaS** — different levels of cloud service: rent the room, rent the workshop, or rent the finished service
- **Shared responsibility model** — the cloud provider secures the building and underlying platform; the customer is still responsible for what belongs to them
- **Provisioning** — creating and preparing a resource so it is ready to use
- **Golden image / snapshot** — a known starting point that can be used to create consistent machines
- **Snapshot vs backup** — a snapshot is a point-in-time copy used for recovery or cloning; a backup is a separate recovery copy with a different purpose
- **Azure Bastion** — the guarded front desk that gives you browser-based SSH access without giving your VM a public IP
- **Bastion shareable link** — sensitive access information that must never be committed to GitHub or exposed in screenshots
- **SSH (Secure Shell)** — remote command-line access to another machine
- **SSH client and server** — the client starts the connection; the server listens and answers
- **Port 22** — the standard numbered door used by SSH
- **Host / fingerprint verification** — the verify-before-approve habit when connecting to a host for the first time
- **Authentication** — proving that you are the account you claim to be
- **Remote session / remote shell** — the live command-line session running on another machine
- **Getting TO vs getting INTO a machine** — network reachability and authentication are different problems
- **`hostname`** — asks which machine you are on
- **`whoami`** — asks which account you are using
- **`pwd`** — asks where you are in the filesystem
- **Private IP address** — an address used inside a private network rather than directly on the public internet
- **Virtual network (VNet)** — the private cloud neighborhood where resources communicate
- **Subnet** — a smaller address range inside a VNet; a floor inside the larger building
- **NAT / outbound translation** — lets a privately addressed machine communicate outward without giving the machine its own public IP
- **Network Security Group (NSG)** — the network guard post that controls what traffic is allowed; you take control of these rules in Week 7
- **Known-good reference point** — a target whose expected behavior gives you something reliable to compare against
- **Grid Beacon** — the known-good Cloud Heights host at `10.60.6.4`
- **The silent Azure gateway** — Azure's default gateway may not answer ICMP ping even when the network is healthy
- **OSI model** — the seven-layer vocabulary used to organize network and application behavior
- **TCP/IP model** — the more compact layer model commonly used by practitioners
- **Layers** — a way to separate different jobs in a communication path so troubleshooting can be systematic
- **Encapsulation** — information travelling inside other information, like a letter inside an envelope inside a mailbag
- **The Ladder Rule in the real cloud** — work outward, prove what works, use the route and a known-good target, and never let one silent tool response choose the culprit by itself

## My Cloud Heights Command Table

You used these commands on a real Ubuntu machine this week. Instead of memorizing syntax, write down the **question each command answers** or the job it performs.

| Command | What question does it answer / what does it do? |
| --- | --- |
| `hostname` | shows the virtual machines's name,  it make sure the name of the VM has not be changed.  |
| `whoami` | shows the user name who owns the VM, it shows the username. |
| `pwd` | the directory is user currently working inside the terminal,  it shows what directory are they are working. |
| `ip addr` | shows the VMs  private  or public IP address and IPv4 address.  IP addresses assigned to the VM. |
| `ip route` | shows the default gateway and subnet mask. It sends the network to a trusted destination. |
| `ping` | test a IP address or website reaching to other device.  Checks any packets are send back from the server or any devices. |
| `traceroute` | shows how many hops (routers) can take to get the packet to the destination(server). It shows how the IP address or a  website takes milliseconds to get to their destination. |
| `dig` | looking up for DNS information. It helps you find which IP address belongs. |
| `curl` | request data from websites, the website send back the data.vcommunicates with the website and the website sends back data. |
| `ssh` | connected to other computer or server. It looks inside of other computer or server. |
| `exit` | closes your shell or terminal.  It exits the shell when the user is finished navigating the shell. |

## In My Own Words

### 1. Getting TO vs Getting INTO

Explain the difference between getting **TO** a machine and getting **INTO** a machine. Use something you personally observed in Cloud Heights as evidence.

```
Getting to a machine is assigned a Virtual Machine. Get into a machine is having access the machine by renting it, the person who is renting the machine receives a username and password kept private.
```

### 2. The Silent Gateway

Your Azure gateway did not answer `ping`, but your VM was still healthy. Explain how you proved the network was working and what this taught you about interpreting tool output.

```
The Azure gateway did not answer ping because the Azure gateway has a hard time communicating the server is connecting to the azure gateway. The VM is healthy because the VM is built correctly. 
```

### 3. Private on the Inside, Connected to the Outside

Explain how your Cloud Heights VM can reach the internet even though it has only a private IP address. Then explain how **you** reach the VM from outside its VNet.

```
The Cloud Heights VM can reach the internet even though it has only a private IP address, the Cloud Heights VM can only connect to someone's personal internet, but it can't get access to the internets private IP address. The internet and the Cloud Height VM connected to separate devices.
```

### 4. VNet vs Subnet

Explain the difference between a VNet and a subnet using the Cloud Heights building/floor analogy. Then explain why separating systems into smaller network ranges can help security.

```
A VNet is a private cloud network where it communicates to other private VMs. A subnet is a small address range connected to a private network. Separating the systems into smaller networks can help with security because separating the systems to different networks by having a backup network in case of the networks fails or gets broken or gets attacks from a hacker, it has an extra network for crisis only.
```

### 5. The Ladder Rule Has a Map Now

The Ladder Rule never used the words OSI or TCP/IP. Explain how the layer models give you a map for the same troubleshooting process you have already been using.

```
The Ladder rule is making sure that any device or VM connected to a network on a server or other devices. It make sure the network is receiving any data from a server or a device communicating back to the VM.
```

---

## Submission Checklist

- [x] I summarized the Week 6 concepts in my own words, not copied definitions

- [x] I completed my Cloud Heights command table

- [x] I explained getting TO vs getting INTO a machine

- [x] I documented what the silent Azure gateway taught me

- [x] I explained the Cloud Heights private-network design

- [x] I connected the Ladder Rule to network layers

- [x] I checked that my Bastion shareable URL does not appear anywhere in this file

- [x] I checked that my Cloud Heights password does not appear anywhere in this file

- [x] This file is committed to my portfolio repo at `week-06/notes.md`

---

*CyberVisionaries Institute — Cyber Foundations, Tier I*
