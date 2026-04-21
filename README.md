![GitHub stars](https://img.shields.io/github/stars/YOUR_USERNAME/YOUR_REPO?style=social)
![GitHub forks](https://img.shields.io/github/forks/YOUR_USERNAME/YOUR_REPO?style=social)
![GitHub issues](https://img.shields.io/github/issues/YOUR_USERNAME/YOUR_REPO)
![GitHub license](https://img.shields.io/github/license/YOUR_USERNAME/YOUR_REPO)
![Made With](https://img.shields.io/badge/Made%20With-SSH%20%7C%20Git-blue)

# 🔥 Use Multiple GitHub Accounts on One System (Windows) Using SSH | Complete Guide

> 🚀 Struggling with multiple GitHub accounts on the same system?  
> This guide solves authentication conflicts, wrong commits, and SSH issues step-by-step.

## ⭐ Features

- Supports multiple GitHub accounts on one system
- Works on Windows (PowerShell)
- No authentication conflicts
- Clean and scalable setup

---
## 📌 Why This Setup is Needed

When using multiple GitHub accounts on the same system, you may face:
- Authentication conflicts
- Wrong account commits
- Push/pull permission issues
  
This setup solves these problems by:
- Using separate SSH keys
- Creating SSH aliases
- Assigning identity per repository

## Accounts Used
|Type|Email|Username|
|---|---|---|
|Personal|[yashbelgahe99@gmail.com](mailto:yashbelgahe99@gmail.com)|ycode99|
|Work|[yashwant@gmail.com](mailto:yashwant@gmail.com)|yashwant|

## 🧠 How It Works

Each GitHub account is mapped to a unique SSH key and alias:

- `github-personal` → Personal account  
- `github-work` → Work account  

This ensures Git uses the correct account automatically.

## ⚙️ Step 1: Generate SSH Keys

### 1.1 🔹Work Account

```bash
ssh-keygen -t ed25519 -C "yashwant@gmail.com"
```
Save as:

```bash
C:\Users\yashq\.ssh\id_ed25519_work
```
![My Image](/images/1.png)

### 1.2 🔹Personal Account

```bash
ssh-keygen -t ed25519 -C "yashbelgahe99@gmail.com"
```
Save as:

```
C:\Users\yashq\.ssh\id_ed25519_personal
```
![My Image](/images/2.png)

## ✅ Resulting Structure

```text
C:\Users\yashq\.ssh\
├── config
├── id_ed25519_work
├── id_ed25519_work.pub
├── id_ed25519_personal
├── id_ed25519_personal.pub
```
![My Image](/images/3.png)

## 🧩 Step 2: Configure SSH

### Create or edit the SSH config file:
Note: The SSH config file is typically located at:

```bash
C:\Users\yashq\.ssh\config
```

### Add the following configuration:

```text
# Work Account
Host github-work
  HostName github.com
  User git
  IdentityFile C:\Users\yashq\.ssh\id_ed25519_work

# Personal Account
Host github-personal
  HostName github.com
  User git
  IdentityFile C:\Users\yashq\.ssh\id_ed25519_personal
```
## 🔗 Step 3: Add SSH Keys to GitHub Accounts

### 3.1 Add SSH Keys to Work GitHub account

Open the terminal and run:

```bash
type C:\Users\yashq\.ssh\id_ed25519_work.pub
```
Enter:
#### Copy the work Key :
![My Image](/images/4.png)

#### Add Keys to GitHub

- Go to GitHub on browser → Settings
- Navigate to **SSH and GPG Keys**
- Click **New SSH Key**
- Paste the copied key
- Save the key

![My Image](/images/6.png)

### 3.2 Add SSH Keys to personal GitHub account 

#### Note:  follow same steps for Add SSH Keys to personal GitHub account:
#### Open the terminal and run:

```bash
type C:\Users\yashq\.ssh\id_ed25519_personal.pub
```
Enter:
#### Copy the Personal Key :
![My Image](/images/5.png)

#### Add Keys to GitHub

- Go to GitHub on browser → Settings
- Navigate to **SSH and GPG Keys**
- Click **New SSH Key**
- Paste the copied key
- Save the key
![My Image](/images/7.png)


## 🧪 Step 4: Test SSH Connection

Note: After adding the SSH keys to both accounts, run the following commands to verify the connection.

Go to Work account:
Type:
```bash
ssh -T git@github-work
```
Output:
```bash
Hi <username>! You've successfully authenticated.
```

Go to Personal account:
Type:
```bash
ssh -T git@github-personal
```
Output
```bash
Hi <username>! You've successfully authenticated.
```

## 📥 Step 5: Clone Repositories

### Format:
```bash
git clone git@<alias>:<username>/<repo>.git
```
### Personal Repository:

```
git clone git@github-personal:ycode99/<repo-name>.git
```
### Work Repository:

```
git clone git@github-work:yashwant/<repo-name>.git
```

## 👤 Step 6: Set Git Identity (Per Repository)

Note: Git identity is required only when creating commits. It determines which account the commit will be attributed to.

Rule:

If no commit is created, Git identity is not required.

If you are committing changes, Git identity must be configured.

### Work Repository:
```bash
git config user.name "Yashwant"
git config user.email "yashwant@gmail.com"
```
### Personal Repository:
```bash
git config user.name "ycode99"
git config user.email "yashbelgahe99@gmail.com"
```
## ⚠️ Important Rules

❌ Do NOT use:
```bash
git@github.com:...
```
✅ Always use:
```bash
github-work
github-personal
```

## 🔍 Quick Debug Commands
```bash
git remote -v
git config user.email
ssh -T git@github-personal
```

## 🚨 Common Mistakes
- Using default GitHub URL instead of SSH alias
- Not setting Git identity before commit
- Adding SSH key to the wrong account

## 🖥️ GitHub Desktop Note

GitHub Desktop:
- Uses the logged-in account
- Does not fully support SSH alias switching

👉 Recommended: Use **VS Code + Terminal**

## 📂 Recommended Folder Structure
```bash
C:\Users\yashq\work\
C:\Users\yashq\personal\
```

## ✅ Summary

This setup provides:

- Secure SSH authentication
- Correct commit attribution
- Smooth multi-account workflow
- Production-ready Git environment
---
## 👨‍💻 Author

**Yashwant Belgahe**  
Full Stack Developer | MERN | Data Science & AI | Embedded Systems  

📧 yashbelgahe99@gmail.com  

## 🔍 Keywords

Multiple github accounts ssh windows, github ssh config multiple accounts, use two github accounts same pc, git ssh multiple users, github work personal setup

---

## ⭐ Support

If this helped you, please ⭐ star this repository — it helps others find it!