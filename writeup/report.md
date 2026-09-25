# Password Cracking Lab Report

## Assessment Information

| Field | Details |
|-------|---------|
| Programme | NetworkWalks Academy – Cyber IT Diploma (Cybersecurity with Ethical Hacking & AI) |
| Batch | B083 |
| Module | Password Cracking & Security Auditing |
| Mentor | Waqas Karim, CCIC |
| Author | Donald Oketch Odhiambo |
| Date | 25 September 2026 |
| Assessment Type | Authorized Educational Lab |
| Repository | https://github.com/Donald-Odhiambo |

---

## 1. Executive Summary

This lab demonstrates offline password auditing by recovering the password of an intentionally vulnerable protected file (PDF) using two independent tools: John the Ripper (Johnny GUI) on Windows and NetworkWalks online password-cracking tools. Both tools successfully recovered the same password, confirming that offline password cracking relies on deterministic hash matching rather than tool-specific behavior. The exercise reinforces the importance of strong, unique passwords and multi-factor authentication in defending against offline attacks.

---

## 2. Objectives

- Extract a password hash from a protected lab file
- Recover the password using John the Ripper (Johnny) on Windows
- Verify the result using NetworkWalks Hash Calculator and Password Cracker
- Document the methodology, findings, and security implications
- Submit flags as proof of successful completion

---

## 3. Scope and Authorization

This activity was performed strictly within an authorized educational lab environment provided by NetworkWalks Academy. The target file was intentionally created for training purposes. No real user credentials, production systems, or unauthorized files were used.

---

## 4. Tools and Environment

### 4.1 Tools Used

| Tool | Platform | Purpose |
|------|----------|---------|
| John the Ripper (Johnny GUI) | Windows | Offline password hash auditing and recovery |
| NetworkWalks Hash Calculator | Web (Online) | Hash identification and verification |
| NetworkWalks Password Cracker | Web (Online) | Dictionary-based password cracking |
| Lab Protected File (PDF) | Windows | Intentionally vulnerable test target |

### 4.2 Lab Environment

- Operating System: Windows  
- Browser: (for NetworkWalks online tools)  
- Network: Personal/Training lab network  
- All activities performed in an isolated, authorized training environment  

---

## 5. Methodology

### 5.1 Hash Extraction

1. Used the lab-provided hash extractor tool to obtain the password hash from the protected PDF file.  
2. Saved the extracted hash to a text file for use in subsequent steps.  

### 5.2 Password Cracking with Johnny (John the Ripper)

1. Launched Johnny (John the Ripper GUI) on Windows.  
2. Loaded the extracted hash file into Johnny.  
3. Selected the appropriate hash type (as identified by the extractor/Johnny).  
4. Chose a wordlist for the dictionary attack.  
5. Started the cracking process.  
6. Recorded the recovered password once Johnny displayed a successful match.  

NetworkWalks describes this workflow as part of their JTR lab task to recover a locked PDF password using Johnny. [19]

### 5.3 Verification with NetworkWalks Tools

1. Opened the NetworkWalks Hash Calculator in a browser.  
2. Pasted the same extracted hash into the calculator.  
3. Confirmed the hash type matched the one used in Johnny.  
4. Opened the NetworkWalks Password Cracker.  
5. Pasted the hash and ran a dictionary attack using a comparable wordlist.  
6. Verified that the recovered password matched the one obtained from Johnny.  

NetworkWalks explicitly outlines this pattern: extract the hash, run the attack, then open the file with the recovered password. [18]

### 5.4 File Access Verification

1. Opened the protected PDF file.  
2. Entered the recovered password.  
3. Confirmed successful access to the file contents.  
4. Captured screenshots as evidence (stored in `screenshots/` folder).  

---

## 6. Results

### 6.1 Password Recovery

- **Johnny (JtR):** Password successfully recovered  
- **NetworkWalks Tools:** Password successfully recovered  
- **Recovered Password:** *(Same for both tools – see flags in repository)*  
- **File Access:** Protected PDF opened successfully using the recovered password  

### 6.2 Flags

- `flags/flag_johnny.txt` – obtained after cracking with Johnny  
- `flags/flag_networkwalks.txt` – obtained after cracking with NetworkWalks tools  

Both flags confirm that the same password was recovered using both toolchains.

---

## 7. Analysis

### 7.1 Why Both Tools Produced the Same Result

Offline password cracking is based on deterministic hash matching:

- The target hash is fixed and does not change  
- The hash algorithm is fixed (e.g., PDF-specific hash)  
- Each candidate password is hashed and compared to the target  
- The first password that produces a matching hash is the correct one  

Because cryptographic hash functions are deterministic, any correctly implemented tool using the same algorithm and searching the same password space will ultimately find the same password. Differences may occur in speed or the order of attempts, but not in the final correct password when the hash, format, and wordlist are effectively the same. [26]

### 7.2 Security Implications

- Weak or common passwords can be recovered quickly from hashes using dictionary attacks  
- Offline attacks do not require interacting with the target system, making them harder to detect  
- Users who reuse passwords across services increase their risk if any single hash is compromised  
- Strong, unique passwords and multi-factor authentication significantly reduce the success rate of such attacks  

---

## 8. Recommendations

Based on this lab, the following defensive measures are recommended:

- Use long, unique passwords for every account (preferably passphrases)  
- Use a reputable password manager to generate and store credentials  
- Enable multi-factor authentication (MFA) wherever available  
- Avoid predictable patterns (e.g., name + year, common substitutions)  
- Organizations should implement password policies that block known weak and compromised passwords  
- Store passwords using modern, slow, salted password-hashing algorithms (e.g., Argon2id, bcrypt, scrypt, or PBKDF2 with appropriate parameters)  

---

## 9. Lessons Learned

- Offline password auditing depends on hash matching, not on a specific tool  
- Both professional tools (John the Ripper) and lightweight online tools can recover weak passwords  
- Proper lab documentation and evidence handling are essential for professional reporting  
- Strong password practices and MFA are critical defenses against offline attacks  

---

## 10. Conclusion

This lab successfully demonstrated offline password cracking using John the Ripper (Johnny) and NetworkWalks tools. Both tools recovered the same password from the same hash, validating the deterministic nature of cryptographic hashing and the effectiveness of dictionary attacks against weak passwords. The exercise highlights the importance of robust password policies and multi-factor authentication in modern cybersecurity defenses.

---

## 11. References

1. NetworkWalks Academy. Password Cracker (Dictionary Attack). https://networkwalks.com/password-cracker/ [18]  
2. NetworkWalks Academy. Password Cracking with JTR John the Ripper (Project Task Lab). https://networkwalks.com/password-cracking-with-jtr-john-the-ripper-project-task-lab/ [19]  
3. Openwall. John the Ripper Documentation. https://www.openwall.com/john/doc/ [2]  
4. Openwall. John the Ripper Usage Examples. https://www.openwall.com/john/doc/EXAMPLES.shtml [3]  
5. TechTarget. How to use the John the Ripper password cracker. https://www.techtarget.com/cybersecurity/tutorial/How-to-use-the-John-the-Ripper-password-cracker [5]  

---

## 12. Appendix

### 12.1 Repository Structure

```text
password-cracking-lab/
├── README.md
├── flags/
│   ├── flag_johnny.txt
│   └── flag_networkwalks.txt
├── lab-files/
│   └── (intentionally vulnerable test files)
├── screenshots/
│   ├── johnny_result.png
│   └── networkwalks_result.png
└── writeup/
    └── report.md
```

### 12.2 Author Information

**Donald Oketch Odhiambo**  
Cybersecurity Student | Aspiring Penetration Tester  

- LinkedIn: [Donald Oketch Odhiambo](https://www.linkedin.com/in/oketch-donald-odhiambo-0a6823429)  
- GitHub: [Donald-Odhiambo](https://github.com/Donald-Odhiambo)  

---

**Disclaimer:** This report is for educational and training purposes only. All exercises were performed in an authorized lab environment using intentionally vulnerable files. Do not use these techniques on systems or files you do not own or have explicit permission to test.
