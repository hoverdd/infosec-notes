---
title: 'Privilege Escalation'
weight: 3
draft: false
---
## 🧠 Overview
This section covers techniques, tools, and references for escalating privileges on compromised systems — both Linux and Windows.

---

## 🛠️ Tools

- [LinPEAS](https://github.com/carlospolop/PEASS-ng/tree/master/linPEAS)
  - Script for Linux privesc enumeration.
- [WinPEAS](https://github.com/carlospolop/PEASS-ng/tree/master/winPEAS)
  - Windows equivalent of LinPEAS.
- [Linux Exploit Suggester](https://github.com/mzet-/linux-exploit-suggester)
  - Suggests local privilege escalation exploits.
- [PowerUp](https://github.com/PowerShellMafia/PowerSploit/tree/master/Privesc)
  - Windows PowerShell privesc tool.

---

## 📘 References & Writeups

- [GTFOBins](https://gtfobins.github.io)
  - List of Unix binaries that can be used to bypass local security.
- [LOLBAS](https://lolbas-project.github.io)
  - Living Off The Land Binaries for Windows.
- [PayloadsAllTheThings - PrivEsc](https://github.com/swisskyrepo/PayloadsAllTheThings#privilege-escalation)

---

## 📂 Useful Files & Paths

- `/etc/passwd`
- `/etc/sudoers`
- `/etc/crontab`
- `~/.bashrc`, `~/.profile`

---

## 📝 Notes

- Always run enumeration scripts like LinPEAS first.
- Check capabilities: `getcap -r / 2>/dev/null`
- Look for SUID/SGID: `find / -type f -perm -04000 2>/dev/null`
- Inspect `sudo -l` output for abuse.

---

## 🐚 SUID Binaries to Exploit

Use GTFOBins to check if the following are present:

- `vim`
- `nmap`
- `less`
- `find`
- `bash`

---

## 🔍 Custom Binaries

Check `/usr/bin` or unusual files with capabilities:

- Example: `/usr/bin/python3.8` with cap_setuid

---

## 🧪 Test Ideas

- Inject cron jobs.
- Abuse writable service configs.
- Exploit kernel vulnerabilities (check kernel version and match with exploit suggester).