# Quick Command Reference

## First Time Setup (One-time commands)

```bash
# 1. Navigate to your project folder
cd ~/Documents/compas-calibration-analysis

# 2. Initialize Git
git init

# 3. Add all files
git add .

# 4. Make first commit
git commit -m "Initial commit: COMPAS calibration analysis"

# 5. Connect to GitHub (replace YOUR_USERNAME)
git remote add origin https://github.com/YOUR_USERNAME/compas-calibration-analysis.git

# 6. Push to GitHub
git branch -M main
git push -u origin main
```

## Regular Updates (Use these when making changes)

```bash
# 1. Check what changed
git status

# 2. Add changes
git add .

# 3. Commit with message
git commit -m "Your descriptive message here"

# 4. Push to GitHub
git push
```

## Useful Commands

```bash
# See commit history
git log --oneline

# See what changed in files
git diff

# Undo changes to a file (before staging)
git checkout -- filename

# Unstage a file (after git add)
git reset HEAD filename

# See remote URL
git remote -v

# Pull latest changes from GitHub
git pull

# Clone an existing repository
git clone https://github.com/USERNAME/REPO_NAME.git
```

## Common Workflows

### Starting a new feature
```bash
git checkout -b feature-name
# ... make changes ...
git add .
git commit -m "Add new feature"
git push -u origin feature-name
```

### Fixing a typo in last commit message
```bash
git commit --amend -m "Corrected commit message"
git push --force
```

### Reverting to previous commit
```bash
git log  # find commit hash
git revert COMMIT_HASH
git push
```
