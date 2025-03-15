### **Implementation Document: GitHub Sync Automation Script**

---

## **Overview**  
This document provides a detailed implementation guide for setting up and executing an automated GitHub sync script. The script will push updates from your local machine to pre-configured GitHub repositories. It uses a one-way sync, meaning local files will overwrite remote changes if necessary.

---

## **Directory Structure**  
The following directory structure is expected:  

| Local Directory | GitHub Repo |
|----------------|-------------|
| `~/s/bin/`     | bin         |
| `~/s/bld/`     | bld         |
| `~/s/doc/`     | doc         |
| `~/s/web/`     | web         |

---

## **Prerequisites**  
### **1. Install Git**  
Ensure Git is installed:  
```bash
sudo pacman -S --needed git
```

### **2. Verify SSH Key Configuration**  
Ensure your SSH keys are properly configured for GitHub:  
```bash
ssh -T git@github.com
```

- If you see a success message, SSH is configured correctly.
- If not, create an SSH key and add it to GitHub:  
```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```
Add the key to the SSH agent:  
```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
cat ~/.ssh/id_ed25519.pub
```
Add the public key to GitHub under **Settings → SSH and GPG Keys**.

### **3. Configure Git Author Information**  
Set your global Git username and email:  
```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
```

---

## **Step 1: Prepare Local Directories**  
Ensure the following repositories exist locally and are linked to their respective GitHub repositories.

### **Create Directories**  
Create the necessary directories:  
```bash
mkdir -p ~/s/bin ~/s/bld ~/s/doc ~/s/web
```

### **Initialize Git Repositories**  
Initialize the repositories (if not already initialized):  
```bash
cd ~/s/bin && git init
cd ~/s/bld && git init
cd ~/s/doc && git init
cd ~/s/web && git init
```

### **Set Remote URLs**  
Set the remote origin for each repository:  
```bash
cd ~/s/bin && git remote add origin git@github.com:your-username/bin.git
cd ~/s/bld && git remote add origin git@github.com:your-username/bld.git
cd ~/s/doc && git remote add origin git@github.com:your-username/doc.git
cd ~/s/web && git remote add origin git@github.com:your-username/web.git
```

### **Create `README.md` and `LICENSE` Files**  
Create a basic `README.md` and `LICENSE` file for each repository:  

**README.md**  
```bash
echo "# bin" > ~/s/bin/README.md
echo "# bld" > ~/s/bld/README.md
echo "# doc" > ~/s/doc/README.md
echo "# web" > ~/s/web/README.md
```

**LICENSE** (Use MIT License as an example)  
```bash
cat <<EOF > ~/s/bin/LICENSE
MIT License

Copyright (c) $(date +%Y)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software...
EOF
```

Repeat for all repositories:  
```bash
cp ~/s/bin/LICENSE ~/s/bld/LICENSE
cp ~/s/bin/LICENSE ~/s/doc/LICENSE
cp ~/s/bin/LICENSE ~/s/web/LICENSE
```

### **Create Initial Commit**  
Stage, commit, and push initial changes:  
```bash
cd ~/s/bin && git add . && git commit -m "Initial commit" && git push -u origin main --force
cd ~/s/bld && git add . && git commit -m "Initial commit" && git push -u origin main --force
cd ~/s/doc && git add . && git commit -m "Initial commit" && git push -u origin main --force
cd ~/s/web && git add . && git commit -m "Initial commit" && git push -u origin main --force
```

---

## **Step 2: Create the Sync Script**  
Create the script `~/sync_repos.sh`:

```bash
#!/bin/bash

# Set error handling
set -euo pipefail

# Base directory containing all repos
BASE_DIRS=(~/s/bin ~/s/bld ~/s/doc ~/s/web)
LOG_FILE=~/sync_repos_$(date '+%Y%m%d_%H%M%S').log

# Function to log messages
log_message() {
    local message="$1"
    local timestamp=$(date '+%Y-%m-%d %H:%M:%S')
    echo "[$timestamp] $message" | tee -a "$LOG_FILE"
}

# Initialize log file
log_message "Starting repository sync script"

# Store original directory
ORIGINAL_DIR=$(pwd)

# Process each repository
for repo in "${BASE_DIRS[@]}"; do
    if [[ -d "$repo/.git" ]]; then
        cd "$repo"
        log_message "Processing repository: $repo"

        # Verify branch
        current_branch=$(git rev-parse --abbrev-ref HEAD 2>/dev/null || echo "unknown")
        if [[ "$current_branch" != "main" ]]; then
            log_message "ERROR: Repository not on main branch: $repo (current: $current_branch)"
            continue
        fi

        # Stage changes
        git add --all

        # Commit changes if any
        if ! git diff --cached --quiet; then
            commit_message="Automated sync $(date '+%Y-%m-%d %H:%M:%S')"
            git commit -m "$commit_message"
            log_message "Created commit: $commit_message"

            # Force push changes
            git push origin main --force
            log_message "Successfully FORCE pushed changes to main"
        else
            log_message "No changes to commit in $repo"
        fi
    else
        log_message "WARNING: No git repository found in $repo"
    fi
done

# Return to original directory
cd "$ORIGINAL_DIR"

log_message "Repository sync completed"
log_message "Log file saved to: $LOG_FILE"
```

---

## **Step 3: Set Permissions**  
Make the script executable:  
```bash
chmod +x ~/sync_repos.sh
```

---

## **Step 4: Execute the Script**  
Run the script to sync all repositories:  
```bash
./sync_repos.sh
```

---

## **Log File**  
- A log file will be created in the home directory:  
```
~/sync_repos_YYYYMMDD_HHMMSS.log
```
- Example:  
```
[2025-03-14 12:00:00] Starting repository sync script  
[2025-03-14 12:00:05] Processing repository: ~/s/bin  
[2025-03-14 12:00:06] Successfully FORCE pushed changes to main  
```

---

## **Verification**  
### **1. Confirm the correct repositories are used:**  
```bash
find ~/s -type d -name ".git"
```
### **2. Check GitHub for the latest updates in each repo.**  

---

## **Troubleshooting**  
| Issue | Solution |
|-------|----------|
| Permission denied | Ensure SSH key is added to GitHub |
| `git push` fails | Use `git push --force` |
| Branch mismatch | Ensure repo is on `main` branch |

---

## **Security Considerations**  
✅ The script uses `--force` — be careful of overwriting remote changes.  
✅ Ensure SSH keys are secured.  
✅ Logs provide detailed status for debugging.  

---

## **End of Document**
