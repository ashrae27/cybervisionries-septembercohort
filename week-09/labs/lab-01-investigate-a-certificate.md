# Week 9 Lab 01 - Investigate a Certificate

**Student Name:** Ashley Raether

**Date Completed:** 11/11/2026

**Module:** 3 - Practical Cryptography | **Week:** 9  
**Submission Path:** `week-09/labs/lab-01-investigate-a-certificate.md`

> ## Vault Exchange Trust and Key Safety Rule
> Inspect a public website without signing in. Do not click past a browser certificate warning, add a practice issuing office (CA) to your browser’s accepted list, or upload secret private keys. Keep all Week 6-8 VM files, SSH keys, and access settings unchanged. This lab makes no security-rule changes.
>
> **Evidence safety:** Capture the certificate viewer, not your account, bookmarks, browser address bar, passwords, or Bastion access URL. Record the public hostname as text in this worksheet.

---

## Mission

Ivy has two digital keys. Both say “Vault Exchange Support.” How can she tell which one belongs to the support team? A label alone is not enough.

Think of a visitor showing a badge at a front desk. The guard checks the name, the dates, and the office that issued it. In this lab, you will look at a website’s digital badge, called a **certificate**. You will write down what you see and follow the list of offices that signed it. You are looking and recording; you are not changing the website.

A visitor badge has a name, issuing office, validity period, and permitted use. A certificate similarly supplies information to check. A polished badge does not make its issuer trusted, and a certificate does not guarantee that a website's advice or downloads are safe.

## What You Already Know

You do not need to memorize last week’s vocabulary. Use these reminders:

- A **public key** is the shareable part of a pair of digital keys. Its label alone does not prove who owns it.
- A **private key** is the secret part. Keep it private, like a key to a locked room.
- A **digital signature** is a mathematical check made with a private key. It helps detect changes and check which matching key signed something.
- A **browser** is the app you use to visit websites. It checks certificates for you.
- A **hostname** is a website’s name, such as `example.com`. It does not include `https://` or the page name after the slash.

Our question is: “Does this digital badge fit the website I meant to visit, and does my browser accept the office behind it?”

## Lab Environment / Pre-Lab Check

| Component | Details |
|---|---|
| Environment | Your normal desktop browser; assigned VM is not needed for this investigation |
| Public target | Start with `https://example.com`; use an instructor-approved public HTTPS site if unavailable |
| Change level | Read-only inspection; no sign-in, certificate import, or warning bypass |
| Time | 35-50 minutes; pause and resume as needed |
| Evidence | Certificate fields, browser chain view, dated observations, and your explanation |

- [x] I have watched Lessons 1-3 or reviewed their slides.

- [x] I can open the public site without signing in.

- [x] I know that live issuer names and dates may differ from the lesson images.

- [x] I will write “not observed” when the viewer does not expose a field.

### Cloud Heights Idle Stop

This browser investigation can be completed while your VM is stopped. If you also open Cloud Heights, respond to its idle warning only while actively working. Restart a stopped VM from My Lab Environment when you need it; do not rebuild it.

## Predict First

A visitor’s badge has not expired. Is checking the date enough to let that visitor in? What else should the guard check? Connect your prediction to a website’s certificate in 2–3 sentences. A prediction is your best guess before investigating; it does not have to be correct.

```text
Checking the badge's date is not enough to let the visitor inside the building. Both of the digital keys 'Vault Exchange Support ', have the same name but one of them is for the visitor can use. Ivy can ask the guard which key is for the visitors and which key is Ivy's key. 
```

## Guided Steps

### Step 1 - Identify the Destination and Observation

1. Open your browser and visit `https://example.com`. Do not sign in or enter a password.
2. Look at the address after the page loads. Sometimes one address sends you to another; that is a **redirect**. Write the name you ended up visiting in the table.
3. Record today’s date, time, and time zone. A time zone tells us which local clock you used.
4. Open the site-information button beside the address. Look for connection or certificate information. Wording may include “Connection is secure” or “Certificate is valid.”
5. Open the certificate details. Browser menus differ. If you cannot find them, ask your instructor to show you. Do not install anything.

**What you should see:** information about the website’s certificate. Copy the browser’s message exactly. For the browser version, use its Help/About screen if available; ask for help if needed.

| Observation | Your record |
| --- | --- |
| Starting public URL | https://example.com |
| Final expected hostname | example.com |
| Observation date and time | 11/10/2026, 9:56am. |
| Time zone | PST |
| Browser and version | Browser google chrome, Version 157.0.8103.38 / 39 |
| Browser connection/certificate status, exactly as shown | Browser connection: secure, certificate status: verified. |

If a warning appears, stop before proceeding to the site. Record the warning privately and select an approved alternative with your instructor. A warning is not a request to disable verification.

### Step 2 - Read the Leaf Certificate

Select the certificate for the website itself. This is called the **leaf certificate** because it is at the end of the signing chain. Other certificates in the list belong to the offices that issued certificates.

Open Details or Fields. A **field** is one labeled piece of information, like “Name” on a badge. Work down the table one row at a time. Use this guide to understand the labels:

| Label in the viewer | Plain-language meaning |
|---|---|
| Subject | Who or what this certificate describes. |
| Subject Alternative Name (SAN) | The list of website names the certificate covers. Use this list to check the name you visited. |
| Issuer | The office that signed this certificate. Such an office is called a certificate authority, or **CA**. |
| Not Before / Not After | The start and end of the certificate’s allowed date-and-time period. |
| Subject public-key algorithm and size | The kind of public key and its size. An **algorithm** is a set of instructions for doing a calculation. Copy the label and number you see. |
| Certificate signature algorithm | The method the issuing office used to sign the certificate. This is a different job from the website’s own public key. |
| Extended Key Usage (EKU) | The listed jobs for this certificate, such as identifying a web server. |
| Basic Constraints | Whether this certificate may act as an issuing office (CA). |
| Serial number / SHA-256 fingerprint | A tracking number, or a calculated fingerprint, that helps identify the particular certificate you inspected. |

You do not need to explain how the algorithms work. In the last column below, explain the field’s job in your own words. Expand a long list to see its entries. A Subject “Common Name” is not a substitute for checking the SAN list.

| Field | Value you observed | What question does this field help answer? |
| --- | --- | --- |
| Subject | CN = Cloudflare TLS Issuing ECC CA 3 | What is the certificate's name? |
| Subject Alternative Name (SAN) | DNS Name: *.example.com | What is the name of the website the certificate belongs to? |
| Issuer | O = SSL Corporation | Who signed the certificate?  |
| Not Before | 9/26/26, 3:49:11 PM PDT | What is the date and time the certificate start? |
| Not After | 12/25/26, 2:56:35 PM PST | What is the date and time the certificate end? |
| Subject public-key algorithm and size, if shown | Elliptic Curve Public Key | What kind of key does the website uses? |
| Certificate signature algorithm | X9.62 ECDSA Signature with SHA-256 | What method the certificate is signed? |
| Extended Key Usage (EKU), if shown | Not Critical TLS WWW Server Authentication (OID.1.3.6.1.5.5.7.3.1) | What are the jobs for the certificate?  |
| Basic Constraints, if shown | Critical Is a Certification Authority Maximum number of intermediate CAs: 0 | Is the certificate authorized?  |
| Serial number or SHA-256 certificate fingerprint | e38be21734c2fa1fcbfb7387460e11b39bf8f80729cc766f23d4e77b64433469 | What is the tracking number or fingerprint for the certificate?  |

Copy the matching SAN entry fully. If other names are listed, say “additional names listed.” Keep the website’s public-key information separate from the method used to sign its certificate.

**Capture now (Step 2):** With the public leaf certificate fields expanded, save `week09-lab01-certificate-fields.png` on your computer. Keep one readable overview screenshot and exclude accounts and address bars. Required certificate details may be spread between the observation table and this overview screenshot; every field does not need to fit in one image. Copy actual values into the table. Additional numbered images are optional for smaller screens or larger text; do not shrink text.

**If you cannot find a field:** write “not observed” and ask your instructor. If you have confirmed that the full certificate has no EKU field, write “extension not present.” Not seeing a label in a limited viewer does not prove it is missing from the certificate.

### Step 3 - Check the Website Name and Dates

Now do two badge checks yourself: “Right name?” and “Still within its dates?” A wildcard is a `*` that stands in for part of a name.

1. Compare your final expected hostname with the leaf's DNS SAN entries. For a wildcard, `*.example.com` ordinarily matches one label such as `shop.example.com`, not `example.com` or `a.shop.example.com`.
2. Compare the observation time with Not Before and Not After using consistent time zones. Do not change your device clock.
3. Record the browser result separately from the field comparison.

```text
Expected hostname: example.com
Matching SAN entry, or no match: No match, DNS Name: example.com ,DNS Name: *.example.com
Why the entry matches or does not match: The DNS names do not match,  example.com does not have wildcard,  *.example.com has a wildcard.
Observation time and certificate time zone: 11/10/2026, 9:56am PST
Is your observation time between the start and end dates? Explain: Start: 9/26/26, 3:49:11 PM PST, Ends: 12/25/26, 2:56:35 PM PST. The start date for the user can use example.com and the end date the user can not use example.com.
Browser-reported result: Connection is secure
What I checked myself versus what the browser reported: The browser reported the website is a safe.
```

### Step 4 - Map the Observed Chain

Look for a view called **hierarchy**, **certification path**, or **chain**. These are names for the list of certificates linked by signatures.

Think of a badge office approved by a larger office:

- **Leaf:** the website’s badge.
- **Intermediate:** an issuing office between the website and the top office. There can be more than one, or none shown.
- **Root / trust anchor:** the top office your browser is set up to accept. A **client** is the program doing the checking; here, that is your browser.

Record only what your browser shows. The browser may add a root from its own stored list. This screen is not a recording of everything the website sent. Also, reading matching office names is not the same as doing the mathematical signature checks yourself.

| Position / role | Subject | Issuer | Where observed | What remains unknown? |
| --- | --- | --- | --- | --- |
| Leaf / website | CN = example.com | O = SSL Corporation | Google Chrome | The certificate private details have not been released |
| Intermediate, if shown | CN = Cloudflare TLS Issuing ECC CA 3 | O = SSL Corporation | Google Chrome | The certificate private details have not yet been released |
| Additional intermediate, if shown | CN = SSL.com TLS Transit ECC CA R2 | O = SSL Corporation | Google Chrome | The certificate private details have not yet been released |
| Root / trust anchor, if shown | CN = SSL.com TLS ECC Root CA 2022 | O = SSL Corporation | Google Chrome | The certificate private details have not yet been released |

**Capture now (Step 4):** With the observed chain/hierarchy visible, save `week09-lab01-chain-view.png` on your computer. Show the leaf and only issuing offices actually displayed. An additional chain map is optional.

Remove unused intermediate rows or mark them “not shown.” Do not invent a three-certificate chain. If the viewer exposes only the leaf, report that limit and ask the instructor for a supported viewer demonstration.

Make a simple labeled chain sketch, or write the relationship in words:

```text
The website leaf is signed by: CN = Cloudflare TLS Issuing ECC CA 3
That issuer is signed by (if shown): O = SSL Corporation
The top office (root / trust anchor) shown by my browser is (or not observed): The top office (root / trust anchor) shown by my browser is on the top of the certificate hierarchy list.
Why an office signing its own badge is not enough (who must choose to accept that office?): A office signing its own badge is not enough because the owner of the website to sign the badge, not only the office.
This view is the browser's displayed path; I have / have not independently captured what the server sent: I have not captured the server sent because the server does not know example.com is a legitimate website.
```

## Stop & Check

- Is the selected certificate the website leaf, rather than its CA?
- Did you distinguish the subject key from the issuer's signature algorithm?
- Did you record the actual observation date and time zone?
- Did you label a field you could not see as “not observed”?
- Did you explain why an office signing its own badge does not make everyone accept that office?

## Test

Your test is to compare the name and dates, then record the browser’s result. Write “I checked…” for your own work and “The browser reported…” for its result. You have not separately checked every signature yourself. You also have not separately checked whether an issuer canceled the certificate early; that is called **revocation**. Do not claim checks you did not perform.

## Capture Evidence

Capture required images at Steps 2 and 4 while the views are visible. Keep account details and browser address bars outside the crop. The observation table plus one readable certificate overview may document the required fields. Extra field images are optional; the chain-view screenshot remains required.

**Upload to your own GitHub portfolio (not the VM):** Save exact filenames on your computer and open each image to check legibility and privacy. In your connected portfolio repository open `assets/screenshots/week-09/`. If missing, from the repository root use **Add file > Create new file** named `assets/screenshots/week-09/README.md`, add a short description and **Commit changes**. Within the screenshot folder choose **Add file > Upload files**, select reviewed images from your computer and **Commit changes**. Do not upload private material or change your repository visibility.

Open each committed image in GitHub in **Raw** or image view. Right-click it to **Copy image address**. Add the direct `https://` image address and caption in the matching **Screenshot Links and Captions** box. A GitHub file-view webpage (`github.com/.../blob/...`), local path or repository-relative path does not work in these boxes. A private-repository image might not preview in the portal; inspect it in your own repo rather than making it public. Previously saved valid addresses remain valid. A relative link such as `../../assets/screenshots/week-09/week09-lab01-certificate-fields.png` is only for manually edited GitHub Markdown, not a portal box.

**Order:** Capture while visible, save and review, upload and commit images, add direct links and captions, finish answers, **Save Progress**, then **Submit to GitHub**. Save Progress stores portal answers. Submit to GitHub commits the worksheet Markdown and references, **not image bytes**. Inspect committed Markdown and images. If links or answers change later, Save Progress and Submit to GitHub again.

## Explain

Write 3–4 sentences using the visitor-badge example. Explain one field, who signed the website’s certificate, why the browser accepts the top office, and one thing a certificate cannot promise. Sentence starters: “The SAN list is like…”, “The issuing office…”, “My browser accepts…”, and “This does not mean…”.

```text
The browser accepts the top office because the top office signs the website example.com certificate to ensure the top office owns the website, example.com. The browser, Google Chrome, accepts the example.com website to ensure the website example.com is secure, the website is marked secured. This does not mean the website does not own by attackers who put malware on the website, the website is signed by a trust company's office owns the example.com website. 
```

## Required Evidence

Upload and commit the exact filenames in your own GitHub portfolio under `assets/screenshots/week-09/` (not on the VM), then add direct image addresses and captions below:

- `week09-lab01-certificate-fields.png` (add `-02`, `-03` if needed)
- `week09-lab01-chain-view.png`

Complete all observation, field, name/time, and chain records in this worksheet. A chain sketch can be embedded as `week09-lab01-chain-map.png` or written in the provided fields. Browser-specific layouts and live certificate changes are acceptable when the evidence is internally consistent.

### Screenshot Links and Captions - Certificate Fields (required)

![week09-lab01-certificate-fields.png](https://raw.githubusercontent.com/ashrae27/cybervisionries-septembercohort/refs/heads/main/assets/screenshots/week%209/week09-lab01-certificate-fields.png)

**Caption - certificate fields:** Leaf Certificate

### Screenshot Links and Captions - Chain View (required)

![week09-lab01-chain-view.png](https://raw.githubusercontent.com/ashrae27/cybervisionries-septembercohort/refs/heads/main/assets/screenshots/week%209/week09-lab01-chain-view.png)

**Caption - chain view:** Chain of Certificates

### Screenshot Links and Captions - Optional Extra Evidence (leave blank if you do not need it)

![week09-lab01-certificate-fields-02.png](https://raw.githubusercontent.com/ashrae27/cybervisionries-septembercohort/refs/heads/main/assets/screenshots/week%209/week09-lab01-certificate-fields-02.png)

**Caption - extra certificate fields image:** Root Certificate

![week09-lab01-certificate-fields-03.png](https://raw.githubusercontent.com/ashrae27/cybervisionries-septembercohort/refs/heads/main/assets/screenshots/week%209/week09-lab01-certificate-fields-03.png)

**Caption - third certificate fields image:**  Intermediate Certificate

![week09-lab01-chain-map.png](https://raw.githubusercontent.com/ashrae27/cybervisionries-septembercohort/refs/heads/main/assets/screenshots/week%209/week09-lab01-chain-map.png)

**Caption - chain sketch image:** Chains of Certificates and fields

## Analysis Questions

**Analysis Question 1.** Ivy has two working keys with the same label. Why does a working key or a correct signature not, by itself, prove that the key belongs to the support team? Write at least 3 sentences.

```text
The working key is owned by Ivy, who is currently working at the Cloud Heights office building. She uses the key to get access to the building since she is an employee at Cloud Heights. The other key belongs to the guest who is visiting the building for just one day; it can be a visitor's family member, maintenance or someone who works a different company. 
```

**Analysis Question 2.** Anyone could print an office name on a badge. Why must the browser check more than the printed issuer name? Explain how the browser’s settings or accepted list determines which top offices it trusts. Write at least 3 sentences.

```text
The browser checks more than the printed issuer name because the browser checks the information about who owns the badge, besides the name of the issuer who owns the badge. The browser will change the badge's settings by adding a new visitor's information. The office can only accept authorized visitors who are visiting the office building. 
```

**Analysis Question 3.** What did your name, date, and browser checks tell you about this connection? Why do they not promise that everything the website says or offers is safe? Say which checks you did and which you did not do. Write at least 3 sentences.

```text
The name, date, and browser checks the website is safe or not, the name and the date is unknown. The browser, Google Chrome, says the website example.com is secure and safe to use. It checks to make sure there is no malware or viruses on the example.com website. 
```

## Submission Checklist

Before submitting, check both images are committed in your own GitHub portfolio and both direct image addresses and captions are present in the portal. Save Progress, Submit to GitHub, then inspect committed Markdown and images.

- [x] Public hostname, observation time, time zone, and browser recorded

- [x] Certificate fields completed, with unavailable fields labeled honestly

- [x] SAN/name and validity comparisons explained

- [x] Observed chain roles mapped without inventing missing certificates

- [x] Browser-reported result distinguished from my own inspection

- [x] Both required screenshot subjects captured clearly

- [x] Analysis answers completed in my own words

- [x] No credentials, private keys, account details, or Bastion URL included

- [x] Worksheet saved to `week-09/labs/lab-01-investigate-a-certificate.md`

## GitHub / Lab Portal Submission

A **repository** is your project’s folder on GitHub. A **commit** is a saved set of changes. A `.md` file is a text document that uses simple formatting marks. Keep the headings and fill in the blank answers.

1. Capture at Steps 2 and 4 while visible; save exact filenames on your computer and review images for legibility and privacy.
2. In your own connected GitHub portfolio, use **Add file > Upload files** in `assets/screenshots/week-09/` and **Commit changes**. Create the folder first as described above if missing.
3. Open each committed image in Raw/image view; copy the direct image address into the corresponding portal box and add a caption. Complete your answers.
4. Press **Save Progress** to store portal answers, then **Submit to GitHub** to commit Markdown and image references only. Connect and select your own repository if prompted.
5. Open the committed worksheet and every image on GitHub. Confirm that tables render, images are legible, and private information is absent. If answers or links change later, Save Progress and Submit to GitHub again. Keep this investigation for Portfolio Deliverable 3 and Lab 02's comparison.

*CyberVisionaries Institute · CyberFoundations · Tier I*
