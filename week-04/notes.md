# Week 4 Notes — Permissions, Searching, and Virtual Machines

**Student Name:** Ashley Raether

**Date Completed:** 10/8/2026

Summarize this week's key concepts in your own words — not copy-pasted definitions.

## Key Concepts This Week

- File permissions: read/write/execute × owner/group/other, and reading `ls -l`
- Changing permissions with `chmod` (symbolic and numeric) — and THE GATEKEEPER'S RULE
- Windows ACLs, read with `Get-Acl` (the real-world `icacls` tool does the same job, but is not available in the simulator)
- Wildcards (`*`, `?`, `[ ]`) and searching inside files with `grep`/`Select-String`
- Virtual machines: host vs. guest, the hypervisor, Type 1 vs. Type 2, isolation
- The VM lifecycle: create, start, stop (deallocate), snapshot, delete — and what each costs
- Golden snapshots — how your Weeks 6–12 lab machines are made

## In My Own Words

**Decode `-rw-r-----` audience by audience: who can do what to this file?**

```
User can read and write but the group can only read the file, everyone can't access to the file. Read, write and execute is not available for everyone. The user can only read and write the file, the group can only read the file.
```

**What is a hypervisor, and what are its two jobs?**

```
A hypervisor is software and hardware that runs multiple virtual machines on a single host. Two jobs are isolating VMs and allocating physical hardware resources.
```

**A stopped VM still costs a little money. What is it paying for, and what's the only way to reach a true zero?**

```
The company is paying for it; one way to reach zero is to delete the VM.
```

---

## Submission Checklist

- [x] I summarized each concept in my own words, not copied definitions

- [x] I answered all three "In My Own Words" prompts

- [x] This file is committed to my portfolio repo at `week-04/notes.md`
