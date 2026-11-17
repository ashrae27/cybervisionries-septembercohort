# Week 10 — Lab 1: Investigate What Needs Protection

Learner: Ashley Raether
Case: Cloud Heights Family Clinic — Risk & Threat Investigation
Scenario date: Friday 13 March 2026, 09:00 (clinic local time)
Report generated: 2026-11-17T21:39:54.953Z
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
The front office received a message saying our scheduling account closes in two hours unless I confirm the password.
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
Backup target: One external drive, letter D:, permanently attached to the reception workstation.
Since then: 6 job entries reading 'completed with errors — source in use'.
There are no copies anywhere else: no second drive, no offsite copy, no cloud copy.

## Risk scenarios

| ID | Asset | Evidence | Threat / event | Vulnerability | Consequence | CIA | Unknown / question |
| --- | --- | --- | --- | --- | --- | --- | --- |
| SC-01 | Appointment scheduling account | EV\-REC\-01 \(Email received at the reception mailbox\); EV\-REC\-02 \(Sender address comparison card\); EV\-REC\-03 \(Reception desk log note\) | The attacker sent a phishing email to the employees, claiming the front desk scheduling passwords had expired and providing a link to enter their credentials, waiting for an employee to click the link and enter their credentials, thinking it was a legitimate link from the IT team.  What caused it is that the system has too many vulnerabilities, and the system has not been upgraded. | The vulnerability is outdated software. The software at the front desk is outdated and needs to be upgraded. The outdated software has too many vulnerabilities. The front office has weak email security; their email system needs an upgrade. | If one of the employees does not know it's a phishing email and they click on the link and enter their email and password, the clinic's and patients' credentials will get stolen, and the clinic might have a ransomware attack, paying a ransom amount of money to unlock the stolen credentials. | Confidentiality, Integrity, Availability | How can you tell the email is a phishing email? |
| SC-02 | Patient records application | EV\-REC\-OFF\-01 \(Records application account list\); EV\-REC\-OFF\-02 \(Records access log extract\); EV\-REC\-OFF\-03 \(Practice manager statement — leavers\) | An unauthorized person went to the front desk and logged in to the front desk's account and read the patients' records without modifying the records. The password is written on a card inside the desk by an employee who just left.  The password needs to have stronger characteristics.  One of the employees must have created the password to make it easy to memorize.  What caused the password not to be secure is that it cannot be written on a piece of paper. | The vulnerability is the weak password created by someone who is not tech\-savvy; the password is written on a piece of paper and stored in the desk.  The password should be kept secret and must have stronger characteristics. | If the unauthorized user logs in to the front desk and reads the patient's records, the unauthorized user will probably modify 8  patient records. The clinic will change the password to a stronger password, and the patient's information is changed; the clinic cannot recognize the patient's records. | Confidentiality, Integrity | How do you change the front desk password from weak to strong? |
| SC-03 | Staff laptops | EV\-WKS\-02 \(IT contractor statement\); EV\-WKS\-03 \(Desk photo — signed\-in laptop\); EV\-WKS\-01 \(Update status report \(IT contractor, 13 March 2026\)\) | An unauthorized person enters the office and gains access to the medical records. This happened because two employees forgot to log off their accounts. | The vulnerability is unattended laptops left logged in with the medical records that everyone can read.  An unauthorized person in the waiting room will enter the office and read the medical records. | An unauthorized person can use one of the laptops that is logged in and modify the decrypted medical records. | Confidentiality, Integrity | How can you prevent the laptops from being unattended? |
| SC-04 | Public information website | EV\-WEB\-01 \(Website certificate details \(captured 13 March 2026\)\); EV\-WEB\-02 \(Renewal process note\); EV\-WEB\-03 \(What the public website actually holds\) | An unknown attacker created the fake Cloud Heights website certificate with no name of the owner, no medical records, and no patient portals. | The vulnerability is a spoofed or phishing website that looks similar to the real website. | If the spoofed website is not reported, the patients will enter the spoofed Cloud Heights website, and the patients' personal information will be stolen. | Confidentiality, Integrity | How do you remove a spoofed website the attacker created?<br> |
| SC-05 | Backup archive | EV\-BAK\-01 \(Backup job history\); EV\-BAK\-02 \(Restore testing statement\); EV\-BAK\-03 \(Backup drive photo\) | The backup drive is duplicated and cloned by an attacker.  The attacker brought a backup drive that looks similar to the Cloud Heights drive and uses similar information for the Cloud Heights backup drive; the attacker might put malware on the drive. | The vulnerability is the backup drive duplication or cloning.  The attacker brings a cloned or spoofed backup drive that looks similar to the Cloud Heights backup drive. | If one of the employees found two similar drives and uses the cloned backup drive, the employee will use the cloned backup drive and all the credentials in the employees will get stolen. | Confidentiality, Integrity | How can which backup drive is the original and which one is the spoofed backup drive? |

## Email analysis
1. From: Clinic IT Support <appointments@clinic-support.example>
2. Subject: URGENT — scheduling account will be closed today
3. Body: "Our records show your scheduling password has expired. Confirm your username and current password within 2 hours at https://account-verify.clinic-support.example/reset or the appointment system will be locked for your whole clinic today."

**Safe response / reporting step:** I would email back the cloudheights-clinic. example telling them I received a suspicious email from  support@appointments-vendor.example. The email does not name the person who sent it.  I will tell the part-time IT contractor I received a suspicious email  from an social engineer who is pretending to be the IT  contractor.

**Suspicious vs proven:** The message is telling the employee that their account will be closed today unless they reschedule an appointment to reset their expired passwords.  If the employee did not reset their password, their account will be locked. I would check which email address is from the attacker and which is from Cloud Heights.
