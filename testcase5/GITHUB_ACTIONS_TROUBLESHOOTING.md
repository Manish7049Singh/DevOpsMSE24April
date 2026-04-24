# GitHub Actions Troubleshooting Guide

## Why GitHub Actions might not be showing up:

### 1. Check if files are pushed to GitHub
```bash
git status
git log --oneline
```
Make sure the `.github/workflows/` folder and files are committed and pushed.

### 2. Verify branch name
The workflow triggers on `main` or `master` branch. Check your current branch:
```bash
git branch
```

If you're on a different branch, either:
- Switch to main/master: `git checkout main` or `git checkout master`
- Or push to main/master: `git push origin your-branch:main`

### 3. Check if workflows are pushed
```bash
git ls-tree -r HEAD --name-only | grep workflows
```
This should show:
- `.github/workflows/deploy.yml`
- `.github/workflows/test.yml`

### 4. Enable GitHub Actions in repository settings
1. Go to your GitHub repository
2. Click on **Settings** tab
3. Click on **Actions** → **General** (left sidebar)
4. Under "Actions permissions", select **"Allow all actions and reusable workflows"**
5. Click **Save**

### 5. Manual trigger (if auto-trigger doesn't work)
1. Go to your GitHub repository
2. Click on **Actions** tab
3. Select **Deploy Pipeline** from the left sidebar
4. Click **Run workflow** button (top right)
5. Select branch and click **Run workflow**

### 6. Check for YAML syntax errors
Run this command to validate YAML:
```bash
cat .github/workflows/deploy.yml
```
Make sure there are no tabs (use spaces only) and indentation is correct.

### 7. Force push to trigger workflow
```bash
git commit --allow-empty -m "Trigger GitHub Actions"
git push origin main
```

### 8. Check GitHub Actions status
Visit: https://www.githubstatus.com/
Make sure GitHub Actions service is operational.

## Quick Fix Commands

### Complete setup from scratch:
```bash
# Make sure you're in testcase5 folder
cd testcase5

# Initialize git if not already done
git init

# Add all files
git add .

# Commit with the required message
git commit -m "This is the new CI/CD pipeline for CA2"

# Rename branch to main
git branch -M main

# Add your remote (replace YOUR_USERNAME and REPO_NAME)
git remote add origin https://github.com/YOUR_USERNAME/nodejs-api.git

# Push to GitHub
git push -u origin main --force
```

### If repository already exists:
```bash
cd testcase5
git add .
git commit -m "This is the new CI/CD pipeline for CA2"
git push origin main
```

## Expected Result

After pushing, you should see:
1. Go to: `https://github.com/YOUR_USERNAME/nodejs-api/actions`
2. You should see workflow runs listed
3. Click on a run to see the 5 steps
4. All steps should have green checkmarks ✅

## Test Workflow

I've added a simple `test.yml` workflow that triggers on ANY push. This will help verify if GitHub Actions is working at all.

After pushing, check if you see "Test Workflow" in the Actions tab.
