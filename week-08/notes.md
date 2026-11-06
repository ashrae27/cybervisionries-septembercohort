# Week 8 Notes — Practical Cryptography

**Student Name:** Ashley Raether

**Date:** 11/6/2026

## Vocabulary in My Own Words

```text
Plaintext: A plaintext is a file is unencrypted, readable, sensitive information readable anyone who can see it.
Ciphertext: A ciphertext is a scrambled-up text with gibberish that no one can read without a key.
Encryption: Encryption protects the file or the data while it is transferred from a different server or location
Hash / digest: A hash keeps sensitive information, data, passwords, messages, and documents secure and turns sensitive data into gibberish characters no one can see the message.
Public key: A public key allows only trusted authorized people for sending or verifying the file.
Private key: A private key is secret key is kept only for the owner to use to encrypt the personal files,
Digital signature: A digital signature is an electronic signature that an individual signs a legitimate contract that can not be modified or copied.
`authorized_keys`: The `authorized_keys' file is a server stores public keys allow to login into a users account.
```

## Command-to-Purpose Map

| Command | What it demonstrated |
| --- | --- |
| `openssl enc` | A command tool to encrypt and decrypt data using ciphers. |
| `sha256sum` | A command verifies SHA256 crypto message files.  |
| `ssh-keygen` | A command creating new authentication keys. |
| `openssl dgst` | A command outputs the message of files. |
| `ssh ... -o PasswordAuthentication=no` | Disables password authentication. |

## Safety Rules I Must Remember

```text
Rule 1: Data at rest: use full-disk encryption for laptops, mobile devices,  and desktops to protect files if the physical devices are lost or stolen.
Rule 2: Protect Data in Transit: use a VPN for transferring sensitive data, emailing or sending a message from an unsecure Wi-FI.
Rule 3: Protect encryption keys: never share the keys with unauthorized individuals, and store keys in a different directory.
```

## Question for the Instructor

```text
My question for the instructor: What sensitive files are required for encryption?
```
