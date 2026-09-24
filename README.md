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

- WEEK 3 | PROJECT MODULE 1

## PASSWORD CRACKING WITH JTR

## Background
John the Ripper (JTR) is a popular password cracking tool used by security professionals to test how strong
passwords are. It started as a tool for Unix systems but now works on Windows, Linux, and Mac. It can
check many types of password hashes and also unlock password protected files like PDF, ZIP, and Office
documents.
Johnny is the graphical version of John the Ripper. It gives a simple point and click screen, so beginners can
use JTR without typing long commands. Both tools are widely used in security testing and learning labs to
understand password safety.
In this lab task you will use JTR John and JTR Johnny to recover the password of a protected PDF file. This
exercise helps you learn how password cracking works and why it is important to use strong passwords for
protection.

## Task
Crack the password of attached PDF file (My Locked PDF1.pdf) using JTR
JOHN and JTR JOHNNY tools on your Windows PC.

Related Info:
Note: If you are using Kali Linux then you can open JTR (John The Ripper) directly because it comes pre-installed in Kali Linux

## Solution

## STEP 1
Download John the Ripper from official website on your windows PC:
https://www.openwall.com/john/
or https://distro.ibiblio.org/openwall/projects/john/1.9.0/
or you can download from Google Drive:
https://drive.google.com/drive/u/1/folders/1aHtgOh7U9mQhkN8VHU7ctTyaDg5KbuJx


## STEP 2
Download Johnny GUI from official website:
https://openwall.info/wiki/john/johnny
or you can download from Google Drive:
https://drive.google.com/drive/u/1/folders/1aHtgOh7U9mQhkN8VHU7ctTyaDg5KbuJx



## STEP 3
Follow below steps to crack the password.
Download the encrypted PDF file to your PC:

Open the hash website & upload your pdf file to find its hash:
https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php
<img width="850" height="327" alt="hashcrack" src="https://github.com/user-attachments/assets/a4d674d6-d0c1-4042-8622-0f756fbb5c06" />

Browse the PDF file & click on Upload:

Select & copy the hash value:
<img width="638" height="134" alt="hash1" src="https://github.com/user-attachments/assets/cccde9de-852f-4e64-9615-e11684760bad" />


Open notepad:

Paste the hash value inside notepad:

Save as text file:

Save the file with name hash1.txt:

Open Johnny again:

Click on ‘Open password file’:

Browse to the hash1.txt file that you have just saved & click on Open:
<img width="638" height="134" alt="hash1" src="https://github.com/user-attachments/assets/9bcd8033-35a1-4bef-9afc-c6c1ac55c56e" />

Click on ‘Start new attack’:
<img width="931" height="649" alt="hash-created" src="https://github.com/user-attachments/assets/490f423a-d5c3-4496-a31a-880fb9a11401" />

Your PDF file password will be cracked (it might take some time depending on your computer
speed & password complexity):
<img width="878" height="688" alt="password-cracked" src="https://github.com/user-attachments/assets/b52dd031-741a-48a1-9313-f365315a548f" />
<img width="958" height="642" alt="pdf1-opened" src="https://github.com/user-attachments/assets/68f1c63e-c776-4600-89c4-a2b0c7804e71" />

<img width="964" height="643" alt="flag-captured" src="https://github.com/user-attachments/assets/c76ff8ea-d3ed-4c0b-959e-3df3763722ee" />

Now you can use this password to open your PDF file.
## PASSWORD CRACKING WITH NETWORKWALKS TOOLS

## Background
Password cracking is the process of recovering a password from stored data or a protected file. Security
professionals use it to test how strong a password is and to show why weak passwords are risky. If a
password is short or common, it can be found quickly, which proves the need for strong passwords.
Many files like PDF, ZIP, and Office documents can be locked with a password. When a file is locked, its
password is stored in the form of a hash. A hash is a scrambled value that represents the password. To
recover the password, we first take out this hash from the file, and then run it through a cracking tool that
tries different words until it finds a match.
In this lab you will use two free online tools made by Networkwalks. First you will use the Hash Calculator
to take the hash out of a locked PDF file. Then you will use the Password Cracker to find the real password
from that hash. Both tools run in your web browser, so you do not need to install anything.
This lab helps you understand how password cracking works step by step and why strong passwords are
important for protection.

## Task
Crack the password of the attached PDF file (My Locked PDF1.pdf) using the
Networkwalks Hash Calculator and Password Cracker tools on your Windows
laptop.

Note: You can also do this lab on Kali Linux, as both tools run in any web browser.

Solution

## STEP 1
Download the encrypted PDF file (My Locked PDF1.pdf) to your laptop from the lab page:
https://networkwalks.com/project-task-lab-password-cracking-with-networkwalks-tools/

## STEP 2
Open the Networkwalks Hash Calculator in your web browser:
https://networkwalks.com/hash-calculator/

## STEP 3
Upload the locked PDF file to the Hash Calculator. The tool will read the file and give you the hash
value that starts with $pdf$...

## STEP 4
Copy the full hash value.
Note: Copy the complete hash starting from $pdf$. Do not miss any part of it.

## STEP 5
Open the Networkwalks Password Cracker in your web browser:

https://networkwalks.com/password-cracker/

## STEP 6
Paste the hash value into the Password Cracker and start the attack. The tool will try different
passwords until it finds a match.

## STEP 7
Wait for the tool to finish. The cracked password will be shown on the screen.

Note: The time taken depends on how simple or complex the password is.

## STEP 8
Open the locked PDF file and enter the cracked password.
Enter password1 (which you have just cracked):

## STEP 9
Your PDF file will open. You have completed the lab.
