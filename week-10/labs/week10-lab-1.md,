# Week 10 — Lab 1: Investigate What Needs Protection

Learner: Ashley Raether
Case: Cloud Heights Family Clinic — Risk & Threat Investigation
Scenario date: Friday 13 March 2026, 09:00 (clinic local time)
Report generated: 2026-11-19T19:09:44.758Z
Study mode: Guided (hints available)

Completion checklist: all required work for Lab 1 is present.

## Evidence added to my findings
- EV-REC-01 — Email received at the reception mailbox
- EV-REC-02 — Sender address comparison card
- EV-REC-03 — Reception desk log note
- EV-REC-OFF-01 — Records application account list
- EV-REC-OFF-02 — Records access log extract
- EV-REC-OFF-03 — Practice manager statement — leavers
- EV-WKS-01 — Update status report (IT contractor, 13 March 2026)
- EV-WKS-02 — IT contractor statement
- EV-WKS-03 — Desk photo — signed-in laptop
- EV-WEB-01 — Website certificate details (captured 13 March 2026)
- EV-WEB-02 — Renewal process note
- EV-WEB-03 — What the public website actually holds
- EV-BAK-03 — Backup drive photo
- EV-BAK-02 — Restore testing statement
- EV-BAK-01 — Backup job history

## My investigation notebook
Room 1: Reception
The front office received a message saying our scheduling account closes in two hours unless  confirm the password.
The front office received a phishing email from an unknown sender trying to pretend to be IT support.
The front desk emailed the office IT team, telling them they received a suspicious email from an unknown sender and that they do not know who it is from.
The office  IT team responded, Third message like this in three weeks. Everyone at the front desk gets them. We just delete them.

Room 2: Records Office
All four people share the login to make it quicker to access the records. When someone quits the front office job, the front office takes the badge from them.
Four employees can only get access to the badge,  clinician/nurse accounts \(named\), 1 billing account \(named\), 1 account named \`frontdesk.
The password written inside the desk is not secure enough to keep the password confidential; The password needs to be kept secret.
The records office has a weak password written on a card inside the desk.
The records office has to change the weak password to a stronger password.
An unauthorized person found the password inside the desk written on the card, and read the patients' records.

Room 3: Staff Workspace
Two laptops have not received an update in 90 days.
9 clinic laptops are updated.
7 laptops have been updated in the last 14 days.
2 laptops \(CHC-04, CHC-07\) do not have security updates for 90 days
No one is using the two laptops.
A photo was taken in the staff workspace at 9:00, a laptop is signed in to the records application, screen unlocked, no one seated.

Room 4: Website Station
The attacker sends an email; the certificate for the website is valid. It expires in 7 days.
The two Cloud Heights IT  signed the real Cloud Heights website certificate for renewal.
Real Cloud Heights public website: address and map, opening hours, list of services, a phone number, and a 'how to register' page.
Fake website: the website has no sign-in, no patient portal, and no connection to the records application.

Room 5: Backup Room
The original Backup drive is plugged in; last clean was two weeks ago
There are no copies anywhere else: no second drive, no offsite copy, no cloud copy.
The drive sits on the desk
Anything that can write to the reception workstation's files can also write to this drive while it is attached. Beside the reception workstation, plugged in by USB, powered on.

## Risk scenarios

| ID | Asset | Evidence | Threat / event | Vulnerability | Consequence | CIA | Unknown / question |
| --- | --- | --- | --- | --- | --- | --- | --- |
| SC-01 | Appointment scheduling account | EV\-REC\-01 \(Email received at the reception mailbox\); EV\-REC\-02 \(Sender address comparison card\); EV\-REC\-03 \(Reception desk log note\) | The Cloud Heights front desk receives a phishing email with an unknown name. | The cloud heights software is outdated; the software needs to be upgraded. | The patients' and the employees' personal information will be stolen. | Confidentiality, Integrity, Availability | How can you tell that the email is a phishing email? |
| SC-02 | Patient records application | EV\-REC\-OFF\-01 \(Records application account list\); EV\-REC\-OFF\-02 \(Records access log extract\); EV\-REC\-OFF\-03 \(Practice manager statement — leavers\) | Unauthorized individuals can find the card inside the desk, gain access to the computer, and read the medical records. | The password is written down on a card inside the unlocked desk. | The patients' records will be misplaced. | Confidentiality, Integrity, Availability | How do you change the front desk password from weak to strong? |
| SC-03 | Staff laptops | EV\-WKS\-02 \(IT contractor statement\); EV\-WKS\-03 \(Desk photo — signed\-in laptop\); EV\-WKS\-01 \(Update status report \(IT contractor, 13 March 2026\)\) | An unauthorized person enters the office, gains access to the laptop logs in, and reads the medical records. | The office door is opened and unlocked, allowing an unauthorized individual to enter and utilize the laptop. | Unauthorized individuals will get access, view, or steal the patients records. | Confidentiality, Integrity | How can you prevent the laptops from being unattended? |
| SC-04 | Public information website | EV\-WEB\-01 \(Website certificate details \(captured 13 March 2026\)\); EV\-WEB\-02 \(Renewal process note\); EV\-WEB\-03 \(What the public website actually holds\) | An unknown individual created a fraudulent website that looks similar to the legitimate Cloud Heights website. | The employees cannot recognize the fraudulent Cloud Heights Website. | Employees may enter their credentials into the fraudulent website, allowing the attackers to steal the passwords and patient's records. | Confidentiality, Integrity | How do you remove a fraudulent website the attacker created?<br> |
| SC-05 | Backup archive | EV\-BAK\-01 \(Backup job history\); EV\-BAK\-02 \(Restore testing statement\); EV\-BAK\-03 \(Backup drive photo\) | An unauthorized person accessing the computer and the backup drive. | Computer is left logged in and unattended with backup drive connected. | An unauthorized individual will destroy or tamper the data; the patients' and employees information will be exposed. | Confidentiality, Integrity, Availability | How do you protect the backup drive from being stolen? |

## Email analysis
1. From: Clinic IT Support <appointments@clinic-support.example>
2. Subject: URGENT — scheduling account will be closed today
3. Body: "Our records show your scheduling password has expired. Confirm your username and current password within 2 hours at https://account-verify.clinic-support.example/reset or the appointment system will be locked for your whole clinic today."

**Safe response / reporting step:** I would email back the cloudheights-clinic. example telling them I received a suspicious email from  support@appointments-vendor.example. The email does not name the person who sent it.  I will tell the part-time IT contractor I received a suspicious email  from an social engineer who is pretending to be the IT  contractor.

**Suspicious vs proven:** The message is telling the employee that their account will be closed today unless they reschedule an appointment to reset their expired passwords.  If the employee did not reset their password, their account will be locked. I would check which email address is from the attacker and which is from Cloud Heights.
