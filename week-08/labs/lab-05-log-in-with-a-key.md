# Week 8 Lab 05 — Log In with a Key

**Student Name:** Ashley Raether

**Date Completed:** 11/6/2026

**Module:** 3 — Practical Cryptography  
**Submission Path:** `week-08/labs/lab-05-log-in-with-a-key.md`

> ## STOP — Protect secrets
> Never paste, upload, commit, or screenshot a password, passphrase, or private key. Do not run `cat` on any private-key file. Submit only the worksheet and the named screenshots. Keep all cryptographic files on the VM.

## How to Use This Lab

- **[TERMINAL]** means type or paste the command into the Cloud Heights terminal.
- **[WORKSHEET]** means type your response in this lab worksheet.
- Run commands in the order shown. Do not type the sample output.
- If your result does not match the stated success check, stop at the Troubleshooting box. Do not improvise with `sudo`, package installation, Azure settings, or SSH server configuration.

## Mission

Authorize the public key created in Lab 03 and prove that `analyst@localhost` authenticates with that key without falling back to the account password.

## What You Already Know

In Week 6, SSH used the `analyst` account password. Here, the server stores the public key in `authorized_keys`, while the private key stays in the client account. The same user, protocol, and destination remain; only the authentication method changes.

## Lab Environment / Pre-Lab Check

**Required prerequisite:** Complete Lab 03 first.

**[TERMINAL] Run:** test -f ~/.ssh/week8_analyst_ed25519 &&   test -f ~/.ssh/week8_analyst_ed25519.pub &&   echo "READY: Lab 03 key pair exists" ||   echo "STOP: complete Lab 03 before continuing"

```bash
whoami
cf-week8-check
test -f ~/.ssh/week8_analyst_ed25519 &&   test -f ~/.ssh/week8_analyst_ed25519.pub &&   echo "READY: Lab 03 key pair exists" ||   echo "STOP: complete Lab 03 before continuing"
```

**Continue only if:** `whoami` prints `analyst`, all checks report `PASS`, and the final line begins with `READY`.

### If the VM Stops

Return to **My Lab Environment** in the Lab Portal and start your assigned VM. A stopped or deallocated VM is not deleted; saved disk files remain.

## Predict First

**[WORKSHEET]** Does the private key need to be copied into `authorized_keys`? Explain.

```text
The private key does not need to be copied into the authorized keys directory. The private key is for the analyst who can own the private key for encrypting and decrypting their own files.
```

## Guided Steps

### Step 1 — Prepare `authorized_keys`

**[TERMINAL] Run:** mkdir -p ~/.ssh, chmod 700 ~/.ssh ,touch ~/.ssh/authorized_keys ,chmod 600 ~/.ssh/authorized_keys

```bash
mkdir -p ~/.ssh
chmod 700 ~/.ssh
touch ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
```

### Step 2 — Add the Week 8 Public Key Once

**[TERMINAL] Run:** grep -qxF "$(cat ~/.ssh/week8_analyst_ed25519.pub)" ~/.ssh/authorized_keys   || cat ~/.ssh/week8_analyst_ed25519.pub >> ~/.ssh/authorized_keys

```bash
grep -qxF "$(cat ~/.ssh/week8_analyst_ed25519.pub)" ~/.ssh/authorized_keys   || cat ~/.ssh/week8_analyst_ed25519.pub >> ~/.ssh/authorized_keys
```

This command adds the key only if an identical line is not already present.

### Step 3 — Confirm the Entry and Safe Permissions

**[TERMINAL] Run:** grep -c 'week8-analyst-key$' ~/.ssh/authorized_keys, stat -c '%a %n' ~/.ssh ~/.ssh/authorized_keys

```bash
grep -c 'week8-analyst-key$' ~/.ssh/authorized_keys
stat -c '%a %n' ~/.ssh ~/.ssh/authorized_keys
```

**Required result:** The count is `1`; permissions show `700` for `.ssh` and `600` for `authorized_keys`.

**Evidence moment:** Capture this result as `week08-lab05-authorized-key-permissions.png`.

### Step 4 — Run the Public-Key-Only Proof

**[TERMINAL] Run:** ssh   -o PreferredAuthentications=publickey   -o PasswordAuthentication=no   -i ~/.ssh/week8_analyst_ed25519   analyst@localhost   'echo "AUTH_TEST=PUBLICKEY_SUCCESS"; whoami; hostname'

```bash
ssh   -o PreferredAuthentications=publickey   -o PasswordAuthentication=no   -i ~/.ssh/week8_analyst_ed25519   analyst@localhost   'echo "AUTH_TEST=PUBLICKEY_SUCCESS"; whoami; hostname'
```

If SSH asks whether to trust the host fingerprint, type `yes` and press Enter. If no fingerprint question appears, continue; `localhost` was already known. Do not delete `known_hosts` to force the question.

At `Enter passphrase for key`, enter the **Lab 03 key passphrase**. Do not enter the `analyst` account password.

**Required result:** AUTH_TEST=PUBLICKEY_SUCCESS ,analyst ,cf-student-06

```text
AUTH_TEST=PUBLICKEY_SUCCESS
analyst
cf-student-XX
```

The final hostname will contain your assigned VM number instead of `XX`.

**Evidence moment:** Capture the three result lines as `week08-lab05-publickey-auth-success.png`.

## Stop & Check

If the command asks for the `analyst` account password, reports `Permission denied`, or does not print `AUTH_TEST=PUBLICKEY_SUCCESS`, do not submit. The options in the proof command disable account-password fallback for this one test only; they do not change the VM server.

### Troubleshooting

1. Run `grep -c 'week8-analyst-key$' ~/.ssh/authorized_keys`; required value is `1`.
2. Run `stat -c '%a %n' ~/.ssh ~/.ssh/authorized_keys`; required values are `700` and `600`.
3. Run `ssh-keygen -lf ~/.ssh/week8_analyst_ed25519.pub`; it must show the Lab 03 key.
4. If any check fails, stop and contact the instructor. Do not edit `/etc/ssh/sshd_config`, use `sudo`, disable password authentication, or delete `known_hosts`.

## Explain

**[WORKSHEET]** In 4–5 sentences, compare Week 6 password authentication with this key-based test. State what changed and what stayed the same.

```text
The permissions stayed the same: read, write, execute for SSH and read and write for the authorized keys. The directory for the public and private keys did not change. The passphrase stayed the same; the passphrase can not be modified. The user 'analyst' for the Azure Bastion VM stayed the same and can not be modified. The original file, incident report, stayed the same, but the modified file incident report did not stayed the same.
```

## Analysis Questions

1. What changed between the Week 6 and Week 8 SSH logins?

```text
What changed between the Wee8 and Week 8 SSH logins is the permissions. The permissions changed for the user only for read, write, and execute the SSH and read and write only for the authorized keys. The user can get access to the keys in Week 8. In Week 6, the user did not have permission to get access to the SSH, because the user can not log in the SSH until Week 8. On Week 8, the user can finally get access to SSH logins by changing the files permissions using the chmod command.
```

2. What stayed the same?

```text
The private and the public keys stayed the same; they cannot be modified. The passphrase remains the same; it can not be changed. The passphrase is scrambled in gibberish, and it's on ciphertext so no one can see it. The file incident report stays the same; it can not be copied or modified. 
```

3. Why does `authorized_keys` contain the public key rather than the private key?

```text
The authorized keys contain a public key rather than the private key, because the authorized key are for authorized people who can only access to the public key. They can encrypt and decrypt the incident report file. They can not get access to the private key because the the private key is only for the analyst to use.
```

4. Why is the forced proof stronger evidence than a normal successful SSH login?

```text
Forced proof is stronger evidence than a normal successful SSH login, because the private and public keys are stronger than the SSH login, the private and public keys have better protection than the SSH.
```

5. How is the key passphrase different from the `analyst` account password?

```text
The key passphrase has different characters than the analyst account password. The analyst password is stronger than the passphrase for the private and public keys.
```

## Required Evidence

- `assets/screenshots/week-08/week08-lab05-authorized-key-permissions.png`
- `assets/screenshots/week-08/week08-lab05-publickey-auth-success.png`

## Submission Checklist

- [x] Lab 03 was completed first.

- [x] The authorized-key count is exactly `1`.

- [x] Permissions are `700` and `600`.

- [x] The public-key-only proof printed all three required lines.

- [x] Both screenshots use the exact filenames.

- [x] No password, passphrase, private key, or Bastion URL appears.

- [x] Every worksheet response is complete.

## GitHub / Lab Portal Submission

1. In the Lab Portal, open the matching Week 8 lab.
2. Complete every **[WORKSHEET]** response.
3. Upload only the required screenshots to `assets/screenshots/week-08/`.
4. Select **Submit to GitHub**.
5. Open the committed worksheet and screenshots on GitHub. Confirm they are readable and contain no secrets.

**Never submit:** `.pem` files, files from `~/.ssh/`, passwords, passphrases, private-key contents, or a Bastion shareable URL.
