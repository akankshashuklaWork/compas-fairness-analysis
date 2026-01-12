# Step-by-Step Guide: Adding Your Project to GitHub

## Prerequisites
- A GitHub account (create one at https://github.com if you don't have one)
- Git installed on your computer (download from https://git-scm.com/)

## Step 1: Create a New Repository on GitHub

1. Go to https://github.com and log in
2. Click the **"+"** icon in the top-right corner
3. Select **"New repository"**
4. Fill in the repository details:
   - **Repository name**: `compas-calibration-analysis` (or any name you prefer)
   - **Description**: "Analysis of COMPAS recidivism prediction calibration across racial groups"
   - **Visibility**: Choose Public or Private
   - **Do NOT** check "Initialize this repository with a README" (we already have one)
5. Click **"Create repository"**

## Step 2: Prepare Your Local Project

1. Open Terminal (Mac/Linux) or Command Prompt/Git Bash (Windows)

2. Navigate to the folder where you want to store your project:
   ```bash
   cd ~/Documents/GitHub  # or any folder you prefer
   ```

3. Create a new folder for your project:
   ```bash
   mkdir compas-calibration-analysis
   cd compas-calibration-analysis
   ```

4. Copy the following files to this folder:
   - `finalProject.ipynb` (your Jupyter notebook)
   - `README.md` (provided)
   - `requirements.txt` (provided)
   - `.gitignore` (provided)

## Step 3: Initialize Git Repository

1. Initialize a new Git repository:
   ```bash
   git init
   ```

2. Add all files to staging:
   ```bash
   git add .
   ```

3. Commit the files:
   ```bash
   git commit -m "Initial commit: COMPAS calibration analysis"
   ```

## Step 4: Connect to GitHub

1. Link your local repository to GitHub (replace YOUR_USERNAME with your actual GitHub username):
   ```bash
   git remote add origin https://github.com/YOUR_USERNAME/compas-calibration-analysis.git
   ```

2. Verify the remote was added:
   ```bash
   git remote -v
   ```

## Step 5: Push to GitHub

1. Push your code to GitHub:
   ```bash
   git branch -M main
   git push -u origin main
   ```

2. If prompted, enter your GitHub username and password/personal access token

## Step 6: Verify Upload

1. Go to your repository on GitHub: `https://github.com/YOUR_USERNAME/compas-calibration-analysis`
2. You should see all your files listed
3. The README.md will be displayed on the repository homepage

## Important Notes

### About the Data File
- The `.gitignore` file is configured to exclude CSV files
- This prevents accidentally uploading sensitive data to GitHub
- Users will need to provide their own COMPAS dataset
- Consider adding a note in your README about where to obtain the data

### Updating Your Repository Later

When you make changes to your project:

1. Check status of changes:
   ```bash
   git status
   ```

2. Stage the changes:
   ```bash
   git add .
   # or add specific files:
   git add finalProject.ipynb
   ```

3. Commit with a descriptive message:
   ```bash
   git commit -m "Description of what you changed"
   ```

4. Push to GitHub:
   ```bash
   git push
   ```

## Authentication Methods

GitHub requires authentication. You have two options:

### Option 1: HTTPS with Personal Access Token (Recommended)
1. Go to GitHub Settings → Developer settings → Personal access tokens → Tokens (classic)
2. Click "Generate new token (classic)"
3. Give it a name and select scopes (at minimum: `repo`)
4. Copy the token and use it as your password when pushing

### Option 2: SSH Keys
1. Generate SSH key: `ssh-keygen -t ed25519 -C "your_email@example.com"`
2. Add to GitHub: Settings → SSH and GPG keys → New SSH key
3. Use SSH URL instead: `git@github.com:YOUR_USERNAME/compas-calibration-analysis.git`

## Troubleshooting

### "Permission denied" error
- Make sure you're using the correct GitHub username
- Use a personal access token instead of password
- Check if you have write access to the repository

### "Repository not found" error
- Verify the repository exists on GitHub
- Check the remote URL: `git remote -v`
- Update if needed: `git remote set-url origin NEW_URL`

### Files not appearing on GitHub
- Check `.gitignore` - file types might be excluded
- Ensure you committed: `git status`
- Make sure you pushed: `git push`

## Next Steps

After uploading to GitHub, you can:
- Add a LICENSE file
- Create a more detailed documentation
- Add example outputs/visualizations
- Set up GitHub Pages for project website
- Enable GitHub Actions for automated testing
- Add badges to your README (build status, license, etc.)

## Resources

- [GitHub Documentation](https://docs.github.com/)
- [Git Documentation](https://git-scm.com/doc)
- [GitHub Learning Lab](https://lab.github.com/)
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)
