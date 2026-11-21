# Week 10 — Lab 2: Prioritize Risks and Recommend Controls

Learner: Ashley Raether
Case: Cloud Heights Family Clinic — Risk & Threat Investigation
Scenario date: Friday 13 March 2026, 09:00 (clinic local time)
Report generated: 2026-11-20T21:35:05.224Z
Study mode: Guided (hints available)

> **DRAFT — this report is incomplete.** Still to finish in Lab 2:
> - Two priority risks chosen, with your reasoning
> - Each priority risk has a control, how it helps, and remaining risk described

## Risk ratings

| ID | Asset | Likelihood | Why | Impact | Why | Score (L x I) | Classroom band |
| --- | --- | --- | --- | --- | --- | --- | --- |
| SC-01 | Appointment scheduling account | 1 | The attacker is trying to access the Cloud Heights system by sending the employees a phishing email. | 1 | The cost of Updating the Cloud Heights software and email system is expensive. | 1 | Low (1–2) |
| SC-02 | Patient records application | 2 | An unauthorized person will open the desk's unlocked drawer, find the password written on the card, and access the patient's records. | 2 | The patient's records will be destroyed. | 4 | Medium (3–4) |
| SC-03 | Staff laptops | 1 | The workplace door is open and unlocked, and an unauthorized person can enter the room and access to the patient's records. | 2 | The patients records will be damaged and tampered. | 2 | Low (1–2) |
| SC-04 | Public information website | 3 | The employees can not compare the fraud and the legitimate certificate. | 3 | The employees and the patient's  credentials will be stolen from the attacker. | 9 | High (6–9) |
| SC-05 | Backup archive | 1 | The backup room door is opened and unlocked, and an unauthorized person enters the room, accessing the patient's record and the backup drive. | 2 | The employee's and patients data will be modified, lost, damaged or tampered. | 2 | Low (1–2) |

Bands (1–2 low, 3–4 medium, 6–9 high) are a classroom teaching aid, not a compliance standard.

## Priority risks
- SC-04 — Public information website

**Why these:** The patient records application and the public information website have the highest scores because the Public information website has the highest chance of a patient or an employee mistaking the fraudulent  Cloud Heights website for the real Cloud Heights website.  The patient records application is the second highest because the password is simple to guess and is written on a card inside the desk, unsecured.

## Recommended controls
### SC-04
- **Control:** The clinic can email the  IT contractor that the fraud certificate has no sign-in, no patient portal, and no connection to the records application.  The clinic will tell the IT contractor that the certificate has been copied or modified by an unknown individual.
- **How it helps:** The IT contractor will compare the fraudulent and the legitimate certificates by analyzing the fraudulent and the legitimate websites.
- **Risk remaining afterwards:** The Cloud Heights employees will receive training to recognize fake websites by checking the website certificates and addresses.

## Owner briefing
Word count: 226 (guide: 100–150)

At Cloud Heights,  there are several Cybersecurity threats: the patient records are easy to access, the Cloud Heights website is vulnerable to fraud, and the password for the front desk sign-in is weak and easy to guess. Leaving the laptops behind logged in and displaying the patients' records, anyone can read them; the employees forgot to log off and did not encrypt the patients' files. Unauthorized individuals, including the patients in the waiting room, can access the patients' records and view them; they can copy or modify the sensitive information without permission. The original Cloud Heights certificate is copied or modified by an unknown individual who copies or modifies the Cloud Heights certificate to develop a fraudulent Cloud Heights website that looks similar to the legitimate website. The employees can not compare which Cloud Heights website is fraudulent and legitimate.  Lastly, an employee who is working the front desk created a password that is easy to memorize, wrote it on the card, and put it in the unlocked desk drawer.  An unauthorized individual can access to the front desk drawer, log in into the front desk account and read the patient's records. To prevent the problems, the employee's should logged off the computers without using them, use a strong password instead of a weak password, and train the employee's comparing the fraudulent and the legitimate certificate.
