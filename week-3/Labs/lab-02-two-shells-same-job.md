# Week 3 Lab 02 — Two Shells, Same Job: Incident Response Edition (CLI Simulator)

**Student Name:**  
**Date Completed:**  
**Module:** 1 — Digital Infrastructure & CLI | **Week:** 3  
**Submission Path:** `week-03/labs/lab-02-two-shells-same-job.md`

---

## Overview

Welcome to your first Incident Response (IR) assignment in the **Foundry District Storeroom**. A potential unauthorized file access attempt has been flagged in the storeroom files, and you've been asked to investigate it twice, using two command syntaxes: first with bash commands (Pass A), then with PowerShell commands (Pass B). Both passes use an equivalent simulated practice dataset with the same Linux-style folders and files — it is practice data inside the simulator, not a real remote server or a real Windows computer. Your goal is to do the same job with both command styles and compare what you typed and what you saw — the same translation skill from Lesson 2, now applied to a real-feeling scenario instead of just a comparison slide. You'll also log your own findings along the way, using the create-and-organize commands from Lesson 3C — a real investigator never just looks and remembers, they document.

**Nothing here can break anything real.** Same consequence-free CLI Simulator as Lab 01.

---

## Lab Environment / Pre-Lab Check

| Component | Details |
|---|---|
| Environment | CyberFoundations CLI Simulator (browser-based, inside the Lab Portal) |
| Shells | Both bash **and** PowerShell are required — that's the whole point of this lab |
| Prerequisite | Lab 01 completed |

**Before you start:** here is how to open this lab's practice area.

1. Sign in to the Lab Portal and open **CLI Simulator** (in the top menu, or the **Open the CLI Simulator** link on the Week 3 page).
2. Scroll down to the heading **Week 3 Labs**.
3. For Part A use the box **Foundry District Storeroom — Bash**. For Part B use the box **Foundry District Storeroom — PowerShell**. Each box is its own terminal. There is no separate shell switch — the box decides the shell.
4. Each box has 6 challenges. Worksheet step A1 matches bash Challenge 1, A2 matches Challenge 2, and so on to A6. Steps B1–B6 match PowerShell Challenges 1–6 the same way.

**How the challenges work.**

- Meet the challenge goal, then press **Next** (or Enter on an empty line). Use **Previous** to look back.
- **Each challenge loads its own prepared files and its own starting folder.** The terminal still shows your earlier commands, but your location and files reset to that challenge's setup. This is normal — it is not lost work.
- **Good habit:** at the start of every new challenge, run `pwd`/`Get-Location`, then `ls`/`dir`.
- The bash box and the PowerShell box each have their own copy of the practice files. Files you create in the bash box do not appear in the PowerShell box — you create them again in Part B.
- **Restart challenge** gives fresh files for the current challenge and keeps any challenges you already saved.
- Your worksheet answers are separate from simulator progress — save them on this worksheet page.

**Command reference:** at the top of the CLI Simulator page, click **Command reference**, then search (for example "copy") and filter to **Bash** or **PowerShell**. Its examples use sample names that may not exist in your challenge.

---

## 💡 Pro-Tips for Reducing Keyboard Strain

Before you start typing, remember these three professional efficiency "cheat codes":

- **Tab Completion (the autocomplete helper):** type the first few letters of a file or folder name (e.g., `cd arc`) and press **Tab**. If only one name starts with those letters, the simulator fills in the rest, in both boxes. If several names match, it fills in only the part they share (or nothing) — type a few more letters and press Tab again. Tab does not fully work with names that contain spaces; for those, type the full name inside quotes, like `cd "my folder"`.
- **Up Arrow (the recaller):** if you make a typo, don't retype the whole command — press the **Up Arrow** to recall your last command, use the left/right arrows to fix the typo, and hit **Enter**.
- **PowerShell aliases:** if typing `Get-Location` or `Get-ChildItem` feels too long, PowerShell lets you use `pwd` as a shortcut for location, and `ls` or `dir` for listing files.

---

## 🛠️ Lab Checklist

- [ ] Part A: Complete the Bash Pass (bash commands), including creating and backing up your investigation note
- [ ] Part B: Complete the PowerShell Pass (PowerShell commands), including creating and backing up your investigation note
- [ ] Part C: Side-by-Side Comparison & Reflection
- [ ] Analysis Questions: Final Conceptual Review

---

## Part A — The Bash Pass

Use the **Foundry District Storeroom — Bash** box. Every challenge starts from a prepared setup, so check your location at the start of each one. Record your commands and output exactly as they appear.

### Step A1 — Verify Your Starting Location

**Bash Challenge 1.** Run the command to print your current working directory. You should start in `/home/agent`.

Command you ran:
```
(paste the command here)
```
Output:
```
(paste the output here)
```

### Step A2 — Look Around the Directory

**Bash Challenge 2.** List the contents of your current location to spot any files or folders. You should see an `archive` folder and a `README.txt` file.

Command you ran:
```
(paste the command here)
```
Output:
```
(paste the output here)
```

### Step A3 — Move Deeper into the Storeroom

**Bash Challenge 3.** This challenge starts in `/home/agent`. Move into the flagged incident folder, `/home/agent/archive/incident-42`. From `/home/agent` you can type `cd archive/incident-42`.

Command you ran:
```
(paste the command here)
```

**⚠️ Stop and check:** run your location-check command *immediately* after moving, to confirm you arrived safely.

Command you ran:
```
(paste the command here)
```
Output:
```
(paste the output here)
```

### Step A4 — Inspect the Incident Log File

**Bash Challenge 4.** This challenge starts inside `/home/agent/archive/incident-42`. The incident log is `access-log.txt`. Print its contents to the screen with `cat`.

Command you ran:
```
(paste the command here)
```
Output:
```
(paste the output here)
```

### Step A5 — Create Your Investigation Note

**Bash Challenge 5.** This challenge starts inside `/home/agent/archive/incident-42`. Investigators document as they go. Create a new, empty file right here called `investigation-notes.txt` to hold your findings.

Command you ran:
```
(paste the command here)
```

### Step A6 — Back Up Your Note

**Bash Challenge 6.** This challenge starts inside `/home/agent/archive/incident-42`, and `investigation-notes.txt` is already prepared there for you. Make a backup copy called `investigation-notes-backup.txt` with `cp` (copy, not move), then run `ls` in the same challenge to see both files.

Command you ran:
```
(paste the command here)
```

Confirm both files now exist:
```
(paste the output here)
```

---

## Part B — The PowerShell Pass

Now use the **Foundry District Storeroom — PowerShell** box. It has its own equivalent copy of the same practice files, with the same Linux-style paths. **Target the same folder and file as Part A:** `/home/agent/archive/incident-42` and `access-log.txt`. The notes files you made in Part A are not in this box — you will create them again here.

### Step B1 — Verify Your Starting Location

**PowerShell Challenge 1.** Run the PowerShell command to print your current location (`Get-Location`). You should start in `/home/agent`.

Command you ran:
```
(paste the command here)
```
Output:
```
(paste the output here)
```

### Step B2 — Look Around the Directory

**PowerShell Challenge 2.** List the contents of your current location (`Get-ChildItem` or `dir`).

Command you ran:
```
(paste the command here)
```
Output:
```
(paste the output here)
```

### Step B3 — Move Deeper into the Storeroom

**PowerShell Challenge 3.** This challenge starts in `/home/agent`. Move into the **same folder** as Part A, `/home/agent/archive/incident-42` — for example `Set-Location archive/incident-42`.

Command you ran:
```
(paste the command here)
```

**⚠️ Stop and check:** run your location-check command *immediately* after moving, to confirm you arrived safely.

Command you ran:
```
(paste the command here)
```
Output:
```
(paste the output here)
```

### Step B4 — Inspect the Incident Log File

**PowerShell Challenge 4.** This challenge starts inside `/home/agent/archive/incident-42`. Print the contents of the same file you read in Part A, `access-log.txt`, with `Get-Content` (or `type`).

Command you ran:
```
(paste the command here)
```
Output:
```
(paste the output here)
```

### Step B5 — Create Your Investigation Note

**PowerShell Challenge 5.** This challenge starts inside `/home/agent/archive/incident-42`. Create the **same-named** empty file, `investigation-notes.txt`, right here with `New-Item`.

Command you ran:
```
(paste the command here)
```

### Step B6 — Back Up Your Note

**PowerShell Challenge 6.** `investigation-notes.txt` is already prepared in `/home/agent/archive/incident-42`. Make a backup copy called `investigation-notes-backup.txt` with `Copy-Item`, same as you did in Part A, then run `dir` in the same challenge to see both files.

Command you ran:
```
(paste the command here)
```

Confirm both files now exist:
```
(paste the output here)
```

---

## Part C — Side-by-Side Comparison (Spot the Difference)

### Step C1 — The Command Comparison Table

Fill in the exact commands you typed for each task. Do not use generic names — list what you actually executed.

| Task / Question | Bash Command (Bash Pass) | PowerShell Command (PowerShell Pass) |
|---|---|---|
| 1. Where am I? | | |
| 2. Look around | | |
| 3. Move into a folder | | |
| 4. Peek inside a file | | |
| 5. Create + back up your note | | |

**⚠️ Stop and check:** did both passes use `/home/agent/archive/incident-42` and `access-log.txt`? If not, go back to the matching PowerShell challenge (use **Previous**) and redo it in that folder before continuing.

### Step C2 — Output Differences Reflection

Describe at least one difference in how the two shells presented information to you (e.g., column layout, text colors, file details, folder headers). Minimum 2 sentences.

```
(your answer here)
```

---

## 🧠 Analysis Questions

### Analysis Question 1 — The Identical Tree

Both passes used equivalent practice datasets with the same Linux-style layout, even though you typed different commands. How do you know the folders and files matched? Point to concrete evidence from your terminal outputs (e.g., matching paths, folder names, or file content). Minimum 3 sentences.

```
(your answer here)
```

### Analysis Question 2 — Syntax Preferences

Which command pair (e.g., pwd vs. Get-Location, ls vs. dir, cat vs. type) felt most different to you? Give a specific reason why one felt more comfortable or intuitive than the other. Minimum 3 sentences.

```
(your answer here)
```

### Analysis Question 3 — Applying Lesson 2 Differences

In this simulator, both boxes use the same Linux-style paths (like `/home/agent`) — PowerShell also runs on Linux, so you did not see drive letters such as `C:\`. If the simulator accepted a backslash in a path, that is a typing convenience, not a sign of a Windows file system. First, describe what you actually observed that was different between the bash and PowerShell commands or output. Then explain one Windows-vs-Linux difference from Lesson 2 (such as slash styles, case-sensitivity, or drive letters) and what it would look like on a real Windows computer. Minimum 3 sentences.

```
(your answer here)
```

---

## Submission Checklist

- [ ] Part A completed entirely in bash (Steps A1–A6, all commands and output recorded)
- [ ] Location re-checked immediately after the Part A move (Step A3), not just at the end
- [ ] Investigation note created and backed up in Part A (Steps A5–A6)
- [ ] Part B completed entirely in PowerShell, on the same folder/file as Part A (Steps B1–B6)
- [ ] Location re-checked immediately after the Part B move (Step B3)
- [ ] Investigation note created and backed up in Part B, with the same filenames as Part A (Steps B5–B6)
- [ ] Comparison table filled in with actual commands, not placeholders (Part C, Step C1)
- [ ] Output-differences reflection written (Part C, Step C2 — minimum 2 sentences)
- [ ] All three Analysis Questions answered (minimum sentence counts met)
- [ ] This file is committed to your portfolio repo at `week-03/labs/lab-02-two-shells-same-job.md`

---

## GitHub Commit Subsection

Same mechanism as Lab 01: fill out this lab's worksheet in the **CyberFoundations Lab Portal** (Week 3 → Lab 02) and click **Submit to GitHub** — the Portal commits the completed file to `week-03/labs/lab-02-two-shells-same-job.md` automatically. No manual typing or commit needed.

**📌 Optional:** a CLI Simulator session screenshot can be added the same way as Lab 01 — upload to `assets/screenshots/week-03/`, then right-click the uploaded image and choose **Copy image address**/**Copy Image Link** to embed it — but it isn't required and won't affect your grade.

---

*CyberVisionaries Institute · Cyber Foundations · Tier I*
