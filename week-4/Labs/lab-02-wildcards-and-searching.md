# Week 4 Lab — The Archive Investigation (CLI Simulator)

**Student Name:**  
**Date Completed:**  
**Module:** 1 — Digital Infrastructure & CLI | **Week:** 4  
**Submission Path:** `week-04/labs/lab-02-wildcards-and-searching.md`

---

## Overview

Lesson 2 gave you the Archive's two tools: patterns that match many filenames at once, and the magnet — `grep` — that searches *inside* files. This lab hands you an Archive of your own and a request slip with three jobs on it: match a set of files with patterns (Part A), hunt down a suspicious log entry with grep (Part B), and run the full find → check → lock down audit that combines this week's two lessons into one workflow (Part C). This lab is more independent than Lab 01 — the steps tell you *what* to accomplish, and the *how* is mostly on you. One screenshot from this lab becomes part of ★ Deliverable 1.

---

## Lab Environment / Pre-Lab Check

| Component | Details |
|---|---|
| Environment | CyberFoundations CLI Simulator (browser-based, inside the Lab Portal) |
| Shell | **Bash is REQUIRED** for Parts A, B and C (Archive Investigation — Bash, challenges 1–8). The four Archive Investigation — PowerShell challenges are **optional extra practice** — they do not replace any bash step, and there is no PowerShell permission-change step. |
| Paths | Simulated Linux-style paths such as `/home/morgan/archive` — this is not your real Windows or Mac computer |
| Prerequisite | Week 4, Lessons 1 and 2 completed; Lab 01 recommended first |

**Before you start**

1. Sign in to the Lab Portal and open **Week 4 → CLI Simulator**.
2. Open **Foundry District Archive Investigation — Bash**.
3. Check the prompt. Every challenge starts in `/home/morgan/archive`, a folder of **11 files** — invoices, logs and notes. Type `pwd` if you are unsure.
4. Know about fresh starts. **Every challenge gives you a brand-new copy of the Archive.** Folders you made or permissions you changed in an earlier challenge will not carry over. That is expected.
5. Know the two kinds of saving. **Next** in the simulator only moves to the next challenge (simulator progress saves automatically). Your typed answers in **this worksheet** are saved only when you click **Save Progress** here in the Lab Portal.

**Which challenge goes with which step**

| Simulator challenge (Bash) | Worksheet step |
|---|---|
| 1 — Survey | Part A, Step 1 |
| 2 — Every invoice | Part A, Step 2 |
| 3 — March invoices only | Part A, Step 3 |
| 4 — Wildcard copy + list | Part A, Step 4 |
| 5 — Search one log | Part B, Steps 1–2 |
| 6 — Search every log | Part B, Step 3 |
| 7 — Find the badge-code file | Part C, Step 1 |
| 8 — Search again, check, change, check | Part C, Steps 2–4 (and the screenshot) |

---

## Part A — Work the Request Slip

### Step 1 — Survey the Archive

*Simulator: challenge 1.* Before filtering anything, run a plain listing of the Archive folder (`ls`). You don't need to record every filename — just note roughly how many files there are and what naming families you can see (invoices, logs, notes…).

What you observed (rough count + the naming families you spotted):
```
(type your observations here)
```

### Step 2 — Match One Family With a Pattern

*Simulator: challenge 2.* The slip's first request: **every invoice file.** Write a pattern that matches all of them and *only* them, and test it with `ls` — remember the habit: pattern first, look at what it catches, then act.

Command you ran (your ls + pattern):
```
(paste the command here)
```
Output (the matched files):
```
(paste the output here)
```

### Step 3 — Get Precise

*Simulator: challenge 3.* The slip gets pickier: **only the March invoices**. Refine your pattern so it catches exactly those — no other months and no non-invoice files — you may need a second `*`, a `?`, or a `[ ]` set, depending on how the names are built.

Command you ran:
```
(paste the command here)
```
Output (the matched files — and nothing extra):
```
(paste the output here)
```

### Step 4 — Act on a Pattern

*Simulator: challenge 4* (fresh Archive — make the folder again).

1. Create a folder named `evidence`.
2. Copy **both** March invoices into it with **one** `cp` command that uses your Step 3 pattern. Copy — don't move — so the originals stay put.
3. Confirm with `ls evidence`. You should see exactly the two March invoices.

Commands you ran (mkdir, cp with pattern, confirming ls):
```
(paste the commands here)
```

---

## Part B — Run the Magnet

### Step 1 — Search One File

*Simulator: challenge 5.* The slip's second request: `door-access.log` records badge events, and somewhere in it are **denied entries**. Search **that one file** with `grep` for the denied entries — and remember the Strict Teacher: the log writes in CAPS, so decide whether you need the case-insensitive flag or the exact capitals. Showing the whole file with `cat` does not count.

Command you ran:
```
(paste the command here)
```
Output (every matching line):
```
(paste the output here)
```

### Step 2 — Find the Line That Matters

*Same search as Step 1.* Most denied entries are routine — mistyped badges at reasonable hours. One is not. Identify the suspicious line (think: what *time* would worry you?) and record it exactly.

The suspicious line, and why you flagged it:
```
(paste the line and type your reasoning here)
```

### Step 3 — Widen the Sweep

*Simulator: challenge 6.* One log is never the whole story. Re-run your search across **every** `.log` file in one command — a pattern where the filename goes. Note which files your suspicious word appears in.

Command you ran:
```
(paste the command here)
```
Which files contained matches:
```
(type the filenames here)
```

---

## Part C — Find, Check, Lock Down

The slip's last request is the real test: **somewhere in this Archive is a file listing storeroom badge codes.** You don't know its name. You know what's inside it.

### Step 1 — Find It by Its Contents

*Simulator: challenge 7.* Search every `.txt` file for the term `badge-code`, in one command. Record which file comes back.

Command you ran:
```
(paste the command here)
```
The file you found:
```
(type the filename here)
```

### Step 2 — Check Who Can Touch It

*Simulator: challenge 8* (fresh Archive). Do Steps 2–4 in this order in ONE session so your screenshot tells the whole story:

1. Re-run your Step 1 search across every `.txt` file.
2. Run `ls -l` (BEFORE) and read the found file's rings.

Before you walk away — this is the Week 4 reflex now — read the long listing for that file. Record what you find. Is this file as locked down as its contents deserve?

Command you ran and its output:
```
(paste the command and output here)
```
Your read of the situation:
```
(type your assessment here — who can currently touch this file?)
```

### Step 3 — Lock It Down

*Still challenge 8.*

3. Change the file's permissions so only its owner can read and write it.
4. Run `ls -l` again (AFTER). The simulator checks this order: search, BEFORE listing, change, AFTER listing.

Commands you ran (including both ls -l checks):
```
(paste the commands here)
```
The file's permission string BEFORE and AFTER:
```
(paste both permission strings here)
```

### Step 4 — Capture Your Investigation Evidence (REQUIRED screenshot)

*Still challenge 8.*

1. Scroll so one screen shows the search result, the BEFORE `ls -l`, your `chmod`, and the AFTER `ls -l`.
2. Take a screenshot and save it on your computer as `cli-search-investigation.png` (lowercase, hyphens, no spaces).

**This screenshot is REQUIRED — it is part of ★ Deliverable 1.** You will upload and link it in the GitHub Commit section below.

---

## Analysis Questions

**Analysis Question 1.** In Part A you tested every pattern with `ls` before letting `cp` act on it. Explain what could go wrong if you skipped straight to acting — and why the stakes get higher when the command attached to the pattern is `rm`. *(Minimum 2 sentences.)*

```
(your answer here — minimum 2 sentences)
```

**Analysis Question 2.** Your Part B search returned several routine matches and one suspicious one. In a real security job, why is "reducing six hundred lines to three worth reading" often more valuable than any single answer the search returns? *(Minimum 2 sentences.)*

```
(your answer here — minimum 2 sentences)
```

**Analysis Question 3.** Part C found a sensitive file by its *contents*, then audited its *permissions*. Explain why neither skill alone would have been enough — what does each half of the workflow catch that the other misses? *(Minimum 3 sentences.)*

```
(your answer here — minimum 3 sentences)
```

**Analysis Question 4.** The Archive had eleven files; real systems have millions. Which habit from this lab do you think scales up the furthest into professional work, and why? *(Minimum 2 sentences.)*

```
(your answer here — minimum 2 sentences)
```

---

## Submission Checklist

- [ ] Archive surveyed and naming families noted (Part A, Step 1)
- [ ] Full invoice family matched with a tested pattern (Part A, Step 2)
- [ ] Precise single-month pattern built and verified (Part A, Step 3)
- [ ] Matches copied to `evidence/` with one pattern-driven `cp` (Part A, Step 4)
- [ ] Log searched for denied entries with correct case handling (Part B, Step 1)
- [ ] Suspicious line identified with reasoning (Part B, Step 2)
- [ ] Multi-file sweep run in one command (Part B, Step 3)
- [ ] Hidden file found by contents (Part C, Step 1)
- [ ] Its permissions checked and assessed (Part C, Step 2)
- [ ] Locked down to owner-only with before/after checks (Part C, Step 3)
- [ ] **REQUIRED:** `cli-search-investigation.png` (search, BEFORE, change, AFTER) uploaded to `assets/screenshots/week-04/` and its link pasted in the screenshot box below (Part C, Step 4)
- [ ] All four Analysis Questions answered (minimum sentence counts met)
- [ ] This file is committed to your portfolio repo at `week-04/labs/lab-02-wildcards-and-searching.md`

---

## GitHub Commit Subsection

This lab's written answers are submitted through the **CyberFoundations Lab Portal**. Do the screenshot steps first, then submit.

**📸 REQUIRED — upload your Deliverable 1 screenshot to GitHub**

1. Go to your own portfolio repository on GitHub.com and open `assets/screenshots/week-04/` (create it the same way as Lab 01 if it is missing).
2. Click **Add file → Upload files**.
3. Drag in `cli-search-investigation.png` and click **Commit changes**.

**🔗 Link the screenshot in the portal**

4. On GitHub, click the uploaded file name, then click **Raw** (or the download icon). The image opens on its own.
5. Copy the address from your browser's address bar. It should start with `https://raw.githubusercontent.com/`.
6. In the Lab Portal, paste it into the screenshot box labeled **Archive investigation — find, check, lock down** (just below). A green "Looks like an image address" message and a preview should appear.
   - Do not paste a `github.com/.../blob/...` page link or a file path from your computer — the box will reject them.
   - If your repository is private, the preview may not load. That is fine; the link still points to your image.

**✅ Submit**

7. Click **Save Progress** to save your answers and the link.
8. Click **Submit to GitHub**. The Portal commits this worksheet to `week-04/labs/lab-02-wildcards-and-searching.md`. It commits your answers and the image link — not the image file itself.
9. Open the committed file on GitHub and check that the screenshot shows. If you change anything later, click **Save Progress** and **Submit to GitHub** again.

```markdown
![Archive investigation — find, check, lock down](paste your copied image link here)
```

---

*CyberVisionaries Institute · Cyber Foundations · Tier I*
