# 🛠️ Infosec Notes

A clean and structured personal knowledge base for cybersecurity learning and practice.  
Built with [Hugo](https://gohugo.io/) and the minimalist [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme.

---

## 📂 Topics Covered

- 🖥️ **Vulnerable Machines** — intentionally insecure systems to practice exploitation  
- 🎮 **CTF-style Games** — war games and challenges to sharpen hacking skills  
- 🔎 **Enumeration** — information gathering techniques and cheat sheets  
- 🧪 **Privilege Escalation** — Linux & Windows privesc methods and tools  
- 🔁 **Reverse Shells** — payloads, one-liners, and techniques  
- 🔐 **Encryption & Decryption** — online tools for encoding, decoding, and crypto analysis  

---

## ⚙️ Project Structure

All content is stored in:

```
content/posts/
├── privesc/
├── enumeration/
├── vulnerable-machines/
├── reverse-shells/
├── encryption-decryption/
└── games/
```

Each folder contains an `index.md` file with organized notes and links in Markdown format.

---

## 🚀 Getting Started

To run this project locally:

```bash
git clone https://github.com/hoverdd/infosec-notes.git
cd infosec-notes

# Add the PaperMod theme
git submodule update --init --recursive

# Start the local dev server
hugo server -D
```

Then open http://localhost:1313 in your browser.

## 💡 Why This Exists
I'm building this site to organize my cybersecurity resources, practice notes, and bookmarks — all in one clean and portable format.
It’s my personal infosec wiki — fast, offline, and version-controlled.

## 📬 Contributions
This is a personal project, but feel free to fork it or suggest cool links or improvements via issues.