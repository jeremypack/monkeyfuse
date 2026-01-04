# Quick GitHub Repository Setup

## Option 1: Create via GitHub Website (Fastest - 2 minutes)

1. Go to https://github.com/new
2. Repository name: `monkeyfuse`
3. Description: `Monkeyfuse holding website`
4. Make sure it's set to **Public**
5. **DO NOT** initialize with README, .gitignore, or license (we already have files)
6. Click "Create repository"

7. Then run these commands in your terminal:
```bash
cd /Users/jeremypack/Development/GitHub/monkeyfuse
git remote add origin https://github.com/YOUR_USERNAME/monkeyfuse.git
git branch -M main
git push -u origin main
```
(Replace `YOUR_USERNAME` with your actual GitHub username)

## Option 2: Wait for GitHub CLI Installation

If GitHub CLI (gh) finishes installing, you can run:
```bash
cd /Users/jeremypack/Development/GitHub/monkeyfuse
gh auth login
gh repo create monkeyfuse --public --source=. --remote=origin --push
```

This will create the repo and push everything in one command.

