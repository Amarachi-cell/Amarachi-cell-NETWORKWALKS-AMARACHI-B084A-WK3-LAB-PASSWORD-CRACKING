# Amarachi-cell-NETWORKWALKS-AMARACHI-B084A-WK3-LAB-PASSWORD-CRACKING.
Step-by-step ethical hacking lab on extracting PDF hashes and cracking encrypted documents using John the Ripper and Johnny GUI.
# Password Cracking with John the Ripper (JTR) & Johnny GUI

**Module:** Week 3 | Project Module 1 — Cybersecurity & Ethical Hacking Project Tasks  
**Objective:** Recover the password of an encrypted PDF document (`My Locked PDF1.pdf`) by extracting its cryptographic hash and performing a password recovery attack using John the Ripper (CLI) and Johnny (GUI) on Windows

---

## Project Overview

**John the Ripper (JTR)** is an open-source password security auditing and recovery tool originally built for Unix systems, now available across Windows, Linux, and macOS. It supports hundreds of hash and cipher types—including system passwords, archives (ZIP, RAR, 7z), and encrypted documents (PDF, Microsoft Office).

**Johnny** is the official cross-platform Graphical User Interface (GUI) front-end for John the Rippe. It provides a point-and-click workflow for managing sessions, configuring attack options, and viewing cracked passwords without relying solely on command-line arguments.

### Key Concepts Covered
* **Encryption vs. Hashing:** Understanding the difference between two-way encryption (which requires a key to reverse/decrypt) and one-way cryptographic hashing (which generates a unique message digest used to validate passwords).
* **Hash Extraction:** Converting password-protected file metadata into a JTR-compatible hash string (`pdf...`) using `pdf2john` utilities.
* **Dictionary / Brute-Force Auditing:** Leveraging JTR's jumbo release through Johnny to recover weak passwords and capture the target flag.

---

## 🛠️ Tools & Prerequisites

* **Operating System:** Windows PC (64-bit) *(Note: JTR comes pre-installed on Kali Linux)*
* **John the Ripper (Jumbo Release):** `john-1.9.0-jumbo-1-win64` — [Openwall Official Download](https://www.openwall.com/john/)
* **Johnny GUI:** `johnny_2.2_win.zip` — [Openwall Johnny Wiki](https://openwall.info/wiki/john/johnny)
* **PDF Hash Extractor (`pdf2john`):** [OnlineHashCrack PDF Hash Extractor](https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php) (or local `pdf2john.pl` / `pdf2john.py` script included in the JTR `run` directory)
* **Target File:** `My Locked PDF1.pdf`

---

## 🚀 Step-by-Step Walkthrough

### 1. Environment Setup & Configuration
1. **Download John the Ripper:** Download the 64-bit Windows Jumbo binary archive (`1.9.0-jumbo-1`) from Openwall and extract it to your local drive.
2. **Install Johnny GUI:** Download and run the Windows installer (`johnny_2.2_win.zip` / `johnnyInstaller.exe`).
3. **Link JTR Executable in Johnny:**
   * Launch **Johnny** and navigate to the **Settings** tab on the left panel.
   * Click **Browse** next to *John the Ripper executable*.
   * Navigate to your extracted JTR folder (`.../john-1.9.0-jumbo-1-win64/run/`) and select `john.exe`.
   * Confirm that Johnny detects the Jumbo build (`Detected John the Ripper 1.9.0-jumbo-1 OMP...`).

### 2. Extracting the PDF Hash
1. Open the [OnlineHashCrack PDF Hash Extractor](https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php) in your browser.
2. Click **Browse...**, select `My Locked PDF1.pdf`, and click **Upload**.
3. Copy the generated hash output:
   ```text
   $pdf$4*4*128*-1060*1*16*55d1a5c14175da449753199e44971d32*32*777fd021a7f3c5ae598c0c6495c7f76e00000000000000000000000000000000*32*ceecdac74b19b5a62688d3b3524e1374c955cbb9cc3c45316494d9446ef81af1
4. Open Notepad, paste the clean hash string, and save the file as hash1.txt (UTF-8 encoding).  
3. Cracking the Hash in Johnny
1. Return to Johnny and click Open password file -> Open password file (PASSWD format).  
2. Select hash1.txt and click Open. Verify that the format is recognized as PDF.  
3. Click Start new attack on the top toolbar.  
4. Wait for JTR to audit the hash against its wordlist/rules. Once progress reaches 100% (1/1: 1 cracked, 0 left), the recovered plaintext password will appear in the Password column.  
4. Unlocking the Document & Capturing the Flag
1. Double-click My Locked PDF1.pdf to open it in your PDF reader.  
2. Enter the recovered password when prompted.  
3. Access the unlocked document to view the completion confirmation and capture the lab flags.

## 📊 Results & Artifacts

| Artifact / Field | Value |
| :--- | :--- |
| **Target File** | `My Locked PDF1.pdf` |
| **Hash Format** | `PDF` (`$pdf$4*4*128*...`) |
| **Recovered Password(s)** | `password1` *(primary walkthrough)* / `good-luck` *(alternate lab instance)* |
| **Captured Flag(s)** | `nw{networkwalks_flag1_jtr_270521_1}` / `nw{cybersecurity_flag_captured_2608}` |

🛡️ Security Takeaways & Mitigation
• Avoid Predictable Passwords: Common dictionary words and simple alphanumeric substitutions (password1, good-luck) are cracked within seconds by automated auditing tools.  
• Enforce Length and Entropy: Protect sensitive documents with long, randomly generated passphrases (14+ characters) combining uppercase, lowercase, numbers, and symbols.
• Use Modern Encryption Standards: Ensure PDF documents are encrypted with AES-256 rather than legacy RC4/128-bit revisions ($pdf$4*4*128*).


⚠️ Disclaimer
This project was completed strictly for educational and authorized ethical hacking training . Do not attempt password recovery or unauthorized access against files or systems you do not own or have explicit permission to test.


---

## ✍️ Author

**Amarachi Esther Onwenu**  
*Cybersecurity & Ethical Hacking Project*



