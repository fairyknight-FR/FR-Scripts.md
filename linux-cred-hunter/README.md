# 🔐 linux-cred-hunter

A simple bash script to automatically locate files on a Linux system that may contain **usernames**, **passwords**, **SSH keys**, or other **sensitive credentials**.

Useful for:

- ✅ Post-exploitation during red teaming or penetration testing  
- 🧠 CTF (Capture The Flag) and OSCP-style challenges  
- 🛡️ Internal system audits and security hardening  

---

## 📂 What It Does

The script searches for common credential-containing files such as:

- `/etc/shadow`, `/etc/passwd`, `/etc/mysql/my.cnf`
- User bash histories (`.bash_history`)
- SSH private keys (`~/.ssh/id_rsa`)
- Application config files (`wp-config.php`, `*.conf`)
- Saved credentials (`.aws/credentials`, `.git-credentials`)

It will output what it finds and where, helping you quickly identify weak spots or sensitive data.

---

## 🛠️ How to Use

```bash
git clone https://github.com/your-username/linux-cred-hunter.git
cd linux-cred-hunter
chmod +x find_credentials.sh
./find_credentials.sh

```
> 📌 Note: Root access may be required to read certain protected files like `/etc/shadow `or `/root/.bash_history`.

## 📁 Example Output
```
[+] Found: /etc/shadow
    - /etc/shadow

[-] Not Found: /home/user/.git-credentials

[+] Found: /home/user/.ssh/id_rsa
    - /home/user/.ssh/id_rsa
```

## 📚 References & Inspiration

- 🔗 [GTFOBins](https://gtfobins.github.io/)

-  🔗 [PayloadAllTheThings – Credential Dumping](https://github.com/swisskyrepo/PayloadsAllTheThings)
