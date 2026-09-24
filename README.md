# NETWORKWALKS-EMMANUEL-B083-WK3-PM1-2-CYBERSECURITY-LAB

## Password Cracking with JTR and Other Tools

> ⚠️ Use these techniques only in authorized lab, CTF, or security assessment environments.

### Objective
Practice offline password auditing and hash analysis using:
- **John the Ripper (JTR)**
- **Hashcat**
- **Hydra** (for controlled online login testing)

### Common Workflow
1. **Identify the hash type** with `hashid` or `hash-identifier`.
2. **Prepare a wordlist** (for example, `rockyou.txt`).
3. **Run a dictionary attack** first.
4. **Apply rules/masks** if dictionary-only fails.
5. **Document recovered credentials** and defensive recommendations.

### John the Ripper (JTR)
#### Basic crack
```bash
john --wordlist=/usr/share/wordlists/rockyou.txt hashes.txt
```

#### Show cracked passwords
```bash
john --show hashes.txt
```

#### Force hash format when needed
```bash
john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hashes.txt
```

### Hashcat
#### Dictionary mode
```bash
hashcat -m 0 -a 0 hashes.txt /usr/share/wordlists/rockyou.txt
```

#### Mask attack example
```bash
hashcat -m 0 -a 3 hashes.txt ?l?l?l?l?d?d
```

### Hydra (authorized online testing)
```bash
hydra -l admin -P /usr/share/wordlists/rockyou.txt ssh://TARGET_IP
```

### Reporting Checklist
- Hash type identified
- Tool and attack mode used
- Password(s) recovered
- Time taken
- Account lockout/detection observations
- Mitigation recommendations (MFA, strong password policy, lockout thresholds)
