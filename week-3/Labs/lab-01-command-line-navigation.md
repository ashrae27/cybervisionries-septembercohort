# Week 3 Lab — Navigate Your First File System (CLI Simulator)

**Student Name:**  
**Date Completed:**  
**Module:** 1 — Digital Infrastructure & CLI | **Week:** 3  
**Submission Path:** `week-03/labs/lab-01-command-line-navigation.md`

---

## Overview

Lesson 3 introduced your first five commands — finding where you are, looking around, moving through folders, peeking inside a file, and asking for help — in both bash and PowerShell. This lab has you apply those same five commands to a brand-new practice area inside the CLI Simulator, on your own, then connect what you find back to the file-system tree you learned to read in Lessons 1 and 2.

**Nothing here can break anything real.** The CLI Simulator is a consequence-free practice space — if you type something wrong, the worst outcome is an error message telling you so.

---

## Lab Environment / Pre-Lab Check

| Component | Details |
|---|---|
| Environment | CyberFoundations CLI Simulator (browser-based, inside the Lab Portal) — no install, no VM, no real terminal required |
| Shell | Your choice — bash or PowerShell. Try the same steps in both if you want extra practice; only one is required |
| Prerequisite | Lessons 1, 2, and 3 completed |

**Before you start:** here is how to open this lab's practice area.

1. Sign in to the Lab Portal and open **CLI Simulator** (in the top menu, or the **Open the CLI Simulator** link on the Week 3 page).
2. Scroll down to the heading **Week 3 Labs**.
3. Pick **one** box: **Foundry District Shift Log — Bash** or **Foundry District Shift Log — PowerShell**. Each box is its own terminal. There is no separate shell switch — the box you pick decides the shell.
4. Click inside the terminal and type your commands there.

**How the challenges work.**

- The box shows **Challenge 1 of 6**, **Challenge 2 of 6**, and so on. Each worksheet step below tells you which challenge it matches.
- Read the challenge goal, type commands until it is met, then press **Next** (or press Enter on an empty line). Use **Previous** any time to look back at an earlier challenge.
- **Each challenge loads its own prepared files and its own starting folder.** The terminal still shows your earlier commands, but your location and files reset to that challenge's setup. This is normal — it is not lost work.
- **Good habit:** at the start of every new challenge, run `pwd` (bash) or `Get-Location` (PowerShell), then `ls` (bash) or `dir` (PowerShell), so you know where you are and what is there.
- **Restart challenge** gives you fresh files for the current challenge. It does **not** remove challenges you already completed and saved.
- Only commands that run without an error count toward a challenge. If you see an error, read it and try again.
- The simulator saves your challenge progress. Your worksheet answers are separate — save them on this worksheet page.

**Command reference:** at the top of the CLI Simulator page, click **Command reference** to open it. You can search by command name or by task (for example "list" or "help") and filter to **Bash** or **PowerShell**. Its examples use sample file names that may not exist in your challenge — always check with `ls`/`dir` first.

---

## Part A — Find Your Way

### Step 1 — Check Your Starting Point

**Matches Challenge 1.** Run the command that tells you where you currently are (`pwd` in bash, `Get-Location` in PowerShell).

Command you ran:
```
(paste the command here)
```
Output (your current path):
```
(paste the output here)
```

### Step 2 — Look Around

**Matches Challenge 2.** Run the command that lists what's in your current location (`ls` in bash, `dir` or `Get-ChildItem` in PowerShell).

Command you ran:
```
(paste the command here)
```
Output (files/folders listed):
```
(paste the output here)
```

### Step 3 — Predict Before You Move

**Do this before you press Next into Challenge 3.** Look at the folder names from Step 2 and guess which one might contain a shift log or notes file. Write your guess down first — you'll check it in Part B.

My guess:
```
(type your guess here)
```

---

## Part B — Move and Peek

### Step 1 — Move Into a Folder

**Matches Challenge 3 (first half).** Challenge 3 starts in your home folder. Use `cd` (bash) or `cd`/`Set-Location` (PowerShell) with a folder name from Part A, Step 2 to move into the folder you guessed.

Command you ran:
```
(paste the command here)
```

### Step 2 — Confirm Your New Location

**Matches Challenge 3 (second half).** Right after moving, run `pwd` or `Get-Location` to confirm exactly where you landed. Challenge 3 is complete only when you move **and then** check.

Command you ran:
```
(paste the command here)
```
Output (your new path):
```
(paste the output here)
```

### Step 3 — Look Around Again

**Matches Challenge 4 (searching).** Challenge 4 starts fresh in your home folder again — not in the folder from Challenge 3. Run `pwd`/`Get-Location` to check, then use `cd` and `ls`/`dir` to look inside the folders until you find the file that logs today's activity.

Command you ran:
```
(paste the command here)
```
Output:
```
(paste the output here)
```

### Step 4 — Peek Inside the File

**Matches Challenge 4 (reading).** Once you've found the log file, use `cat` (bash) or `type`/`Get-Content` (PowerShell) to read its contents. Was your guess from Part A, Step 3 right?

Command you ran:
```
(paste the command here)
```
File contents:
```
(paste the file contents here)
```

### Step 5 — Move Back Up

**Matches Challenge 5.** Challenge 5 starts you inside a folder below home (run `pwd`/`Get-Location` to see where). Your goal is to return to your home folder, `/home/morgan`. Use `cd ..` (in bash, plain `cd` also works), then confirm with `pwd`/`Get-Location` that you are in `/home/morgan`.

Command you ran:
```
(paste the command here)
```
Output (confirming your new — higher — location):
```
(paste the output here)
```

---

## Part C — Ask for Help

### Step 1 — Pick an Unfamiliar Command

**Matches Challenge 6.** The challenge names one command you haven't been taught yet: `grep` in the bash box, or `Get-Acl` in the PowerShell box. Instead of guessing what it does, ask the terminal directly.

### Step 2 — Run the Help Command

In bash, use `grep --help` (or `man grep`). In PowerShell, use `Get-Help Get-Acl`. Read the output, then describe it in your own words.

Command you ran:
```
(paste the command here)
```
What the help text told you the command does, in your own words:
```
(describe it in your own words here)
```

---

## Analysis Questions

### Analysis Question 1

Look at the path `pwd` (or `Get-Location`) printed in Part A, Step 1. In this simulator, both the bash and PowerShell boxes use Linux-style paths. Explain what makes this path Linux-style, and describe what a Windows-style path would look like instead. Reference at least one specific detail from Lesson 2 (a drive letter, a slash direction, or the presence of a ~) to support your answer.

```
(your answer here — minimum 3 sentences)
```

### Analysis Question 2

In Part B, you ran `pwd`/`Get-Location` right after moving with `cd`, more than once. Explain why that "move, then check" habit matters, especially while you're still building confidence with the command line.

```
(your answer here — minimum 3 sentences)
```

### Analysis Question 3

In Part C, you looked up a command you'd never used before, instead of guessing or skipping it. Explain why this habit — asking the terminal for help instead of memorizing everything in advance — matters for a real career in IT or cybersecurity.

```
(your answer here — minimum 3 sentences)
```

### Analysis Question 4

Compare this lab to Lesson 1's filing-room analogy (the pile of paper vs. the labeled cabinets). Now that you've actually navigated a file-system tree yourself instead of just reading about one, what — if anything — surprised you or felt different from what you expected?

```
(your answer here — minimum 2 sentences)
```

---

## Submission Checklist

- [ ] Starting location recorded using `pwd`/`Get-Location` (Part A, Step 1)
- [ ] Folder contents listed using `ls`/`dir` (Part A, Step 2)
- [ ] Prediction written down before moving (Part A, Step 3)
- [ ] Moved into a folder using `cd` and confirmed the new location with `pwd`/`Get-Location` **immediately after** the move, not just at the end (Part B, Steps 1–2)
- [ ] Found and read a text file using `cat`/`type` (Part B, Steps 3–4)
- [ ] Moved back up using `cd ..` and confirmed with `pwd`/`Get-Location` (Part B, Step 5)
- [ ] Looked up an unfamiliar command using `--help`, `man`, or `Get-Help` and recorded what it does (Part C)
- [ ] All four Analysis Questions answered (minimum sentence counts met)
- [ ] This file is committed to your portfolio repo at `week-03/labs/lab-01-command-line-navigation.md`

---

## GitHub Commit Subsection

This lab's written answers are submitted the same way as Week 2's: through the **CyberFoundations Lab Portal**, not by typing directly into GitHub.

1. Go to the CyberFoundations Lab Portal and sign in with your student Microsoft account.
2. Open **Week 3 → Lab 01: Navigate Your First File System**.
3. Fill in the worksheet fields — they match the commands, outputs, and questions in this file.
4. Connect your GitHub account if you haven't already (one-time setup), and select your portfolio repo.
5. Click **Submit to GitHub**. The Portal commits the completed file to `week-03/labs/lab-01-command-line-navigation.md` for you — no manual typing or commit needed for this part.

**Three different things — do all that apply:** finishing the simulator challenges saves your challenge progress; **Submit to GitHub** on this worksheet sends your written answers to your repo; logging the lab in the separate lab tracker is its own step (see the Week 3 Submissions Guide).

**📌 Optional — add a screenshot for your portfolio.** This entire step is optional. Skipping it will **not** affect your grade — it's a nice-to-have addition to your portfolio, not a requirement. Only do this if you'd like a visual record of your CLI Simulator session.

If you'd like to add one, take a screenshot showing your commands and their output, then:

1. Go to your portfolio repository on GitHub.com and navigate to `assets/screenshots/week-03/`.
2. Click **Add file → Upload files**, drag in your screenshot, and give it a descriptive name (lowercase, hyphens, no spaces — e.g. `cli-simulator-session.png`).
3. Scroll down and click **Commit changes**.
4. Click on the uploaded image's filename to open it — you'll see the image itself displayed on the page.
5. Right-click directly on the image and choose **Copy image address** (Chrome/Edge) or **Copy Image Link** (Firefox).
6. Come back to this file, open the pencil (edit) icon, and add the embed near the bottom of Part B, pasting your copied link in place of the placeholder:

```markdown
![CLI Simulator session screenshot](paste your copied image link here)
```

**If right-click doesn't show that option** (e.g., on some trackpads or tablets): click the small download-arrow icon in the top-right of the image preview instead, then copy the URL from your browser's address bar.

---

*CyberVisionaries Institute · Cyber Foundations · Tier I*

