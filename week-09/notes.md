# Week 9 Notes - Vault Exchange Digital Trust

**Student Name:** Ashley Raether

**Week:** 9

Use your own words. Short notes and everyday examples are welcome. You do not need to memorize commands.

## From a Key to an Identity

Ivy has two keys with the same label. Why is the label not enough? How can checking a visitor badge help explain the problem?

```text
My explanation: Ivy checks which key is personal and which key is the visitor's key with the same label by checking both keys by going to the front office, checking which key is Ivy's and which key is the visitor's. The label is not enough because both labels that have the same name need the label the name of the visitors key. Checking the visitors' badges explains the problem by checking the visitors ID to make sure their name is match with visitors key.
```

## Certificate Fields

A certificate is a digital badge. Explain the name list (SAN), signing office (issuer), start/end dates, public key, signature method, and allowed job (purpose). Which field would you check to see whether the badge covers the right website?

```text
Field and its job: The field I check to see whether the badge covers the right website is the name list (SAN).  The name list has the list of issuers who signed the certificate of the file and the website. The field I check whether the badge covers the right website is the public key. The public key allows the public to get access to the website but the public can not decrypt the file.
```

## Issuers and Accepted Trust

Who signed the badge? Who chooses whether to accept the top office? Explain why an office signing its own badge is not enough to make your browser trust it.

```text
My explanation: The signing office and the owner(issuers) signs the badge.  The owner chooses the accepted top office to sign the certificate. Why an office signing its own badge is not enough to make the browser trust it, because the signing the badge requires the current owner to sign the badge to ensure the badge can be accepted or not.
```

## Key CSR and Certificate Roles

The CSR is a badge application. Explain the separate jobs of the service’s private key, application, office’s private key, and finished certificate. Who signs the application? Who signs the finished badge?

```text
My explanation: The signing office signs the application by receiving the office's private key for the CSR badge.  The owner(issuer) signs the finished badge by receiving the private key.
```

## TLS and Verification Evidence

Compare looking at a certificate, checking its saved file, and connecting to a running service. TLS sets up a protected connection. What did you observe in each activity?

```text
I looked at: The TLS baseline for the digital certificate is passed and verified.
I checked: The office's name Cyber Foundation Lab signs the certificate and current name.
I connected to: TLS v1.3
```

## Troubleshooting and Remediation

These words mean finding and fixing a problem. Record an actual message, what it meant, and your next step. Consider a wrong name, expired dates, wrong office, canceled certificate, or service that is not running. Label situations you only discussed; do not claim to have tested them.

```text
Message or situation: The wrong.txt and wrong ca.txt certificate test failed.
What it means: The certificate is modified and copied from both failed cerfitcates, wrong.txt and wrong ca .txt.
What I would check or fix: I will fix it by removing the failed certificates that are modified and copied.
Which check I would repeat: I would check which certificate is the original certificate and the certificate is modified and copied.
```

## Questions I Still Have

```text
A word or step I want explained again: Why can't the original signed certificate be copied and modified?
How can you tell whether the certificate is the original or the certificate is copied/modified?
```
