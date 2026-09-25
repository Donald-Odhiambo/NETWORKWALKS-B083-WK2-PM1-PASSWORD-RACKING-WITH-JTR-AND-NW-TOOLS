# Password Auditing Lab — Johnny (JtR) + NetworkWalks

> Educational lab: recover a protected file password using two tools and verify both give the same result.

## At a Glance

- **Programme:** NetworkWalks Academy — Cysesecurity Internship, Batch B083  
- **Mentor:** Waqas Karim, CCIC  
- **Author:** Donald Oketch Odhiambo  
- **Tools:** John the Ripper (Johnny GUI) on Windows; NetworkWalks Hash Calculator + Password Cracker (online)  
- **Outcome:** Same password recovered with both tools; file opened successfully; flags captured

## Tools

| Tool | Platform | Role |
|------|----------|------|
| John the Ripper (Johnny GUI) | Windows | Offline hash auditing and password recovery |
| NetworkWalks Hash Calculator | Web | Hash identification/verification |
| NetworkWalks Password Cracker | Web | Dictionary attack and verification |
| Lab Protected File (PDF) | Windows | Intentionally vulnerable target |

## Workflow (4 Steps)

1. Extract hash from the protected file (lab extractor)
2. Crack with Johnny (load hash → select type → wordlist → run → record password)
3. Verify with NetworkWalks (paste same hash → run dictionary attack → confirm same password)
4. Open the protected file using the recovered password

## Why Results Match

Offline cracking is deterministic: same hash + same algorithm + same candidate space → same password. Tools may differ in speed or order, not in the final correct password when configured equivalently. [18][19][26]

## Repo Map

- `flags/flag_johnny.txt` — flag after Johnny crack  
- `flags/flag_networkwalks.txt` — flag after NetworkWalks crack  
- `screenshots/` — evidence images  
- `writeup/report.md` — full lab report  

## Security Takeaways

- Weak/common passwords are recovered quickly via dictionary attacks  
- Offline attacks need only the hash (no live system interaction)  
- Use long unique passwords + a password manager + MFA  

## Author

**Donald Oketch Odhiambo** — Cybersecurity Student | Aspiring Penetration Tester  
- LinkedIn: [Donald Oketch Odhiambo](https://www.linkedin.com/in/oketch-donald-odhiambo-0a6823429)  
- GitHub: [Donald-Odhiambo](https://github.com/Donald-Odhiambo)  

## References

1. NetworkWalks Password Cracker — https://networkwalks.com/password-cracker/ [18]  
2. NetworkWalks JTR Lab Task — https://networkwalks.com/password-cracking-with-jtr-john-the-ripper-project-task-lab/ [19]  
3. Openwall John the Ripper Docs — https://www.openwall.com/john/doc/ [2]  

> Disclaimer: Educational use only. Authorized lab environment. No real credentials or production systems.
