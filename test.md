# 🧩 DevOps Git Hooks Setup Guide

This repository includes shared **Git pre-commit hooks** to help maintain code quality, security, and consistency across the team.  
The hooks automatically run checks (e.g., secrets scanning, Dockerfile validation, YAML syntax) before allowing commits.

---

## ⚙️ Hook Folder Structure

All hook scripts are stored under:

pre_commit_hooks/
    ├── pre-commit
    ├── pre-commit-secrets-scan.sample
    ├── pre-commit-dcofile.sample
    └── pre-commit-yaml-syntax.sample


These scripts are **version-controlled** and shared with everyone in the team.

---

## 🔧 One-Time Setup

To enable the hooks locally, run the setup script once after cloning the repository:

```bash
bash setup-hooks.sh
This script configures Git to use the shared hooks folder:

🧩 Configuring Git hooks path...
✅ Done! Hooks path set to devops/hooks
After this setup, Git will automatically run hooks from devops/hooks/ instead of .git/hooks/.

📘 Manual Setup (if needed)
If you prefer to configure manually, run:

git config core.hooksPath devops/hooks
This writes the following setting to your local .git/config:

[core]
    hooksPath = devops/hooks
⚠️ This setting is local — it’s not version-controlled.
Each new clone must either run the setup script or re-run the command above.

🔁 Keeping Hooks Updated
Whenever new hook scripts are added or modified:

Pull the latest changes:

git pull
Verify hooks path (should show devops/hooks):

git config core.hooksPath
No further setup is required — the hooks update automatically.

🚫 Bypassing Hooks (for emergencies only)
If you need to skip hooks temporarily (e.g., emergency fix), use:

git commit -m "message" --no-verify
Use this carefully — hooks are there to enforce code quality and security checks.

🧠 Why This Setup
✅ Hooks are version-controlled (devops/hooks/)

✅ No need to copy to .git/hooks/ manually

✅ All developers share the same pre-commit checks

✅ Easy one-time setup via setup-hooks.sh

💡 Example: setup-hooks.sh
#!/usr/bin/env bash
# setup-hooks.sh - one-time setup for Git hooks

echo "🧩 Configuring Git hooks path..."
git config core.hooksPath devops/hooks
echo "✅ Done! Hooks path set to devops/hooks"
🧪 Verification
After setup, you can confirm the hooks are active by running:

git config core.hooksPath
Output:

devops/hooks
Now your hooks will automatically run before every commit. 🚀

👩‍💻 Maintainer Notes
Hook updates should be tested locally before pushing.

If adding new hooks, make sure they are executable:

chmod +x devops/hooks/*
Hooks should exit with a non-zero status to block commits when validation fails.

Enjoy automated DevOps quality checks! 🧩



