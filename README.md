
# Password Security Auditing Using John the Ripper and NetworkWalks Tools

# Password Cracking Lab: John the Ripper (Johnny) + NetworkWalks Tools

> **Educational Use Only:** This repository documents an authorized password-security lab performed in a controlled training environment. Only test hashes and intentionally vulnerable files are used. No real user credentials or production systems are involved.

## Objective

Demonstrate offline password auditing by recovering a protected file’s password using two independent tools and verifying that both produce the same result.

## Tools Used

- **John the Ripper (Johnny GUI)** on Windows
- **NetworkWalks Hash Calculator** (online)
- **NetworkWalks Password Cracker** (online)
- Intentionally vulnerable lab files (e.g., password-protected PDF)

## Lab Workflow

1. Extract the password hash from the protected file using the lab-provided extractor.
2. Crack the hash with **Johnny** on Windows:
   - Load the hash file
   - Select the correct hash type
   - Choose a wordlist
   - Run the attack
   - Record the recovered password
3. Verify with **NetworkWalks tools**:
   - Paste the same hash into the NetworkWalks Hash Calculator
   - Run the dictionary attack
   - Confirm the same password is recovered
4. Open the protected file using the recovered password to prove success.

NetworkWalks describes this exact pattern: extract the hash, run the attack, then open the file with the recovered password. [18] Their JTR lab task is specifically to recover a locked PDF password using Johnny. [19]

## Why Both Tools Give the Same Result

Password cracking in this lab is **offline hash matching**:

- The target hash is fixed
- The hash algorithm is fixed
- A candidate password is hashed and compared to the target
- The first password that produces a matching hash is the correct one

Because cryptographic hashes are deterministic, any tool that correctly implements the same algorithm and tests the same password space will ultimately find the same password. Differences may appear in speed or attack order, but not in the final correct password when the hash, format, and wordlist are effectively the same. [26]

## Repository Contents

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

**Note:** This repository does **not** include real password hashes, personal data, or production files. Only lab-provided or synthetic examples are used.

## Flags

Flags are included in the `flags/` directory as proof of successful completion:

- `flag_johnny.txt` – flag obtained after cracking with Johnny
- `flag_networkwalks.txt` – flag obtained after cracking with NetworkWalks tools

Both flags correspond to the same recovered password, confirming that the two toolchains produce consistent results.

## Findings

- The same password was recovered using Johnny and NetworkWalks tools
- Opening the protected file with this password succeeded
- The lab confirms that offline password auditing depends on hash matching, not on a specific tool

## Security Takeaways

- Weak or common passwords can be recovered quickly from hashes
- Offline attacks do not require contacting the target system
- Strong, unique passwords and multi-factor authentication significantly reduce risk
- Password managers help generate and store credentials that resist dictionary attacks

## Disclaimer

This project is for educational and training purposes only. All exercises were performed in an authorized lab environment using intentionally vulnerable files. Do not use these techniques on systems or files you do not own or have explicit permission to test.
