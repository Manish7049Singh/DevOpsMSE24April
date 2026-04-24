# How to Push to GitHub and Trigger CI/CD

## Step 1: Make sure all files are ready
The workflow is now configured to run on **EVERY PUSH** to any branch.

## Step 2: Push to GitHub

### If this is a NEW repository:

```bash
cd testcase5

# Initialize git
git init

# Add all files
git add .

# Commit with the required message
git commit -m "This is the new CI/CD pipeline for CA2"

# Rename branch to main
git branch -M main

# Create repository on GitHub first, then add remote
# Replace YOUR_USERNAME with your GitHub username
git remote add origin https://github.com/YOUR_USERNAME/nodejs-api.git

# Push to GitHub
git push -u origin main
```

### If repository ALREADY EXISTS:

```bash
cd testcase5

# Add all files
git add .

# Commit with the required message
git commit -m "This is the new CI/CD pipeline for CA2"

# Push to GitHub
git push
```

## Step 3: View in GitHub Actions

1. Go to: `https://github.com/YOUR_USERNAME/nodejs-api`
2. Click on the **Actions** tab at the top
3. You should immediately see "Deploy Pipeline" workflow running
4. Click on the workflow run to see all 5 steps

## Step 4: Enable GitHub Actions (if needed)

If you see a message like "Workflows aren't being run on this repository":
1. Click the green button: **"I understand my workflows, go ahead and enable them"**
2. Or go to Settings → Actions → General
3. Select "Allow all actions and reusable workflows"
4. Click Save

## What happens now?

✅ **Every time you push ANY commit to ANY branch**, the workflow will run automatically
✅ The workflow will appear in the Actions tab
✅ You'll see all 5 steps execute:
   1. Check out the repository code
   2. Set up Node.js version 18
   3. Install project dependencies
   4. Build the Docker image tagged as nodejs-api
   5. Print deployment message

## Test it:

After the first push, make a small change and push again:

```bash
# Make a small change
echo "# Test" >> README.md

# Commit and push
git add .
git commit -m "Test CI/CD trigger"
git push
```

Go to Actions tab and you'll see a new workflow run!
