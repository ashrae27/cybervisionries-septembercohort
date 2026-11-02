# Week 7 Notes — Cloud Heights: The Guard Post

**Student Name:** Ashley Raether

**Week:** 7

## Firewall and Security Group

```text
A firewall is a security tool that decides whether traffic is allowed or denied.
A security group monitors the incoming traffic coming towards the firewall, the security group decides the traffic is allow or deny.
```

## Rule Anatomy

```text
(priority, direction, source, destination, protocol, port, action)
```

## First Match Wins

```text
Priority 100 is the highest priority; priority 200 is lower than priority 100. Priority 200 wins the match. Priority 100 -deny Ivy, priority 200 allow all staff.
Ivy is staff but she is rule 100. She is denied. The guard finds a match at 100 and stops.

```

## Least Privilege

```text
Least Privilege grants only the access necessary to perform an authorized task.
Least privilege does not block everything.
Positive and negative testing: A positive test means Ivy can enter. Negative test: send an unauthorized visitor; prove they're blocked.

```

## Testing and Evidence

```text
Evidence needs context -observe first, interpret second, and conclude when the evidence supports it.
Denied traffic doesn't mean it's under attack. It can be a simple mistake, a colleague using the wrong path, or a route test.

```

## Troubleshooting and Remediation

```text
Troubleshooting: address an error, routing problem, or the firewall dropping the traffic?
If a connection fails, you can change the source to any to see if its works. Great way to isolate the problem.

```

## Questions I Still Have

```text
What should I do, the computer or the VM, if I start having a troubleshooting issue?
What kind of authorized traffic does the firewall allow?

```
