# How to Push this Repository to Your GitHub

Follow these simple steps to upload this complete portfolio to your GitHub account:

### Step 1: Create a new repository on GitHub
1. Open your browser and go to [GitHub New Repository](https://github.com/new).
2. Name your repository (e.g., `wireshark-network-analysis-labs` or `packet-analysis-portfolio`).
3. Set visibility to **Public**.
4. **Do NOT** check "Add a README file" (we already have a complete one created).
5. Click **Create repository**.

---

### Step 2: Initialize and Push from your Computer
Open your Terminal (Linux/Mac) or Command Prompt / PowerShell (Windows), navigate inside this unzipped folder, and run:

```bash
# Initialize git repository
git init

# Add all files and make initial commit
git add .
git commit -m "feat: initialize Wireshark security portfolio and lab templates"

# Rename branch to main
git branch -M main

# Link to your newly created GitHub repository (replace with your actual URL)
git remote add origin https://github.com/<YOUR-USERNAME>/<YOUR-REPO-NAME>.git

# Push everything to GitHub
git push -u origin main
```

---

### Step 3: Complete Labs & Add Screenshots
1. Open the project folder you are working on (e.g. `01-http-traffic-analysis`).
2. Follow the lab steps and save your Wireshark screenshots into the `screenshots/` subfolder.
3. Update the `README.md` with your real findings and replace image placeholders.
4. Commit and push your updates:
   ```bash
   git add .
   git commit -m "docs(lab-01): add HTTP analysis findings and evidence"
   git push
   ```
