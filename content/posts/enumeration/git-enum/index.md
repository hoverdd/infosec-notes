---
title: "Git Enumeration"
description: "Tools and techniques for discovering and exploiting exposed .git directories on web servers."
draft: false
---

## Overview

Sometimes web servers expose the `.git/` folder, which can allow an attacker to reconstruct the entire Git repository — including source code, sensitive files, and even deleted secrets.

This technique is especially useful during CTFs and real-world pentests when a target has poor `.gitignore` hygiene or misconfigured web directories.

---

## 🔧 Tools

### 🛠️ [GitTools – Dumper](https://github.com/internetwache/GitTools)

A well-known toolset for dumping Git repositories from exposed `.git/` folders.

```bash
git clone https://github.com/internetwache/GitTools
cd GitTools/Dumper
./gitdumper.sh http://target/.git/ /tmp/recovered-repo
```

### 🧪 [githack](https://github.com/BugScanTeam/githack)
Fast Python-based tool to clone .git repos via HTTP.

```bash
git clone https://github.com/BugScanTeam/githack
cd githack
python3 githack.py http://target/.git/
```

### 🧰 [DVCS-Ripper](https://github.com/kost/dvcs-ripper)
Extracts repos from Git, SVN, Mercurial. Helpful when `.git` isn't the only exposed DVCS.

```bash
git clone https://github.com/kost/dvcs-ripper
cd dvcs-ripper
perl rip-git.pl -v -u http://target/.git/
```

## 🔍 Post-Extraction Tips
Once you recover the repo, check for:

```bash
git log
git show HEAD
git diff
git checkout <old-commit>
```
Also grep for common keywords:

```bash
grep -i 'pass\|secret\|key\|token' -r .
```
Look for:

- `.env` files

- Database credentials

- Hardcoded API keys

- Deleted but tracked files

## 💡 Notes
- If `.git/index` exists, full history may be recoverable.

- Use `git fsck` to list dangling commits and blobs.

- Check `.gitignore` for hints about what the devs tried to hide.

## 🧷 Related
[gitleaks](https://github.com/gitleaks/gitleaks) – Scan Git repos for secrets

[GitHub Dorks](https://github.com/techgaun/github-dorks)