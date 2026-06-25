Below is a **complete, Windows-specific, end-to-end guide** to set up Git with SSH, clone a repository, and perform pull/push operations correctly.

---

# 1) Install Git on Windows

### Step 1 — Download

Download Git for Windows:
👉 [https://git-scm.com/download/win](https://git-scm.com/download/win)

### Step 2 — Install (Important options)

During setup:

* ✔ “Git from the command line and also from 3rd-party software”
* ✔ “Use bundled OpenSSH”
* ✔ “Use Windows’ default console window”

Finish installation.

### Step 3 — Verify

Open **Git Bash** (recommended) or Command Prompt:

```bash
git --version
```

You should see something like:

```
git version 2.xx.x.windows.x
```

---

# 2) Configure Git Identity (Global)

This sets your commit identity (once per machine):

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

Verify:

```bash
git config --global --list
```

---

# 3) Check for Existing SSH Keys (Windows Path)

Open **Git Bash**:

```bash
ls -al ~/.ssh
```

On Windows, this folder is actually:

```
C:\Users\YourUsername\.ssh
```

If you see files like:

```
id_ed25519
id_ed25519.pub
```

You already have a key.

If not → generate one.

---

# 4) Generate SSH Key (Recommended: ED25519)

In **Git Bash**:

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```

Press:

* Enter (for default location)
* Enter (for passphrase, optional)

This creates:

```
C:\Users\YourUsername\.ssh\id_ed25519
C:\Users\YourUsername\.ssh\id_ed25519.pub
```

---

# 5) Start SSH Agent (Windows)

In **Git Bash**:

```bash
eval "$(ssh-agent -s)"
```

Then add key:

```bash
ssh-add ~/.ssh/id_ed25519
```

If successful → no error.

---

# 6) Copy Public Key (Windows)

Run:

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy the entire output (starts with `ssh-ed25519`).

---

# 7) Add SSH Key to Git Provider

## If Using GitHub

Go to:
👉 [https://github.com/settings/keys](https://github.com/settings/keys)
Click **New SSH Key**
Paste the key → Save

## If Using GitLab

Profile → Preferences → SSH Keys

## If Using Bitbucket

Personal Settings → SSH Keys

---

# 8) Test SSH Connection

For GitHub:

```bash
ssh -T git@github.com
```

First time, it may ask:

```
Are you sure you want to continue connecting?
```

Type:

```
yes
```

If successful:

```
Hi username! You've successfully authenticated.
```

---

# 9) Clone Repository Using SSH (Windows)

⚠ Always copy the **SSH URL**, not HTTPS.

It looks like:

```
git@github.com:username/repository.git
```

Clone:

```bash
git clone git@github.com:username/repository.git
```

Move into project:

```bash
cd repository
```

---

# 10) Verify Remote is SSH

```bash
git remote -v
```

Should show:

```
origin  git@github.com:username/repository.git (fetch)
origin  git@github.com:username/repository.git (push)
```

If you see HTTPS instead, change it:

```bash
git remote set-url origin git@github.com:username/repository.git
```

---

# 11) Pull Latest Changes

```bash
git pull origin main
```

If branch is master:

```bash
git pull origin master
```

---

# 12) Make Changes → Push to Repo

### Step 1 — Check status

```bash
git status
```

### Step 2 — Add files

Add all:

```bash
git add .
```

Or specific file:

```bash
git add app.js
```

### Step 3 — Commit

```bash
git commit -m "Added new feature"
```

### Step 4 — Push

```bash
git push origin main
```

---

# 13) Common Windows Issues & Fixes

## ❌ Permission denied (publickey)

Fix:

1. Ensure SSH agent running:

   ```bash
   eval "$(ssh-agent -s)"
   ```
2. Add key again:

   ```bash
   ssh-add ~/.ssh/id_ed25519
   ```
3. Verify:

   ```bash
   ssh -vT git@github.com
   ```

---

## ❌ SSH Agent Not Starting in PowerShell

Use **Git Bash**, not CMD/PowerShell (recommended).

Or start Windows service:

Open PowerShell as Admin:

```powershell
Get-Service ssh-agent | Set-Service -StartupType Automatic
Start-Service ssh-agent
```

---

# 14) Recommended Folder Structure on Windows

Keep projects in:

```
C:\Users\YourUsername\Documents\Projects\
```

Then:

```bash
cd /c/Users/YourUsername/Documents/Projects
git clone git@github.com:username/repo.git
```

---

# Complete Workflow (Windows)

```bash
Install Git
Generate SSH key
Add key to GitHub
Test SSH
Clone repo
cd repo
git pull
Make changes
git add .
git commit -m "message"
git push
```
