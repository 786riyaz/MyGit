###########################################
#               1. SETUP
###########################################
git config --global user.name "Your Name"
    → Sets your Git username.

git config --global user.email "email@example.com"
    → Sets your Git email address.

git config --global color.ui auto
    → Enables colored Git output.
###########################################
#        2. REPOSITORY INITIALIZATION
###########################################
git init
    → Create a new Git repository.

git clone <url>
    → Clone an existing repository from a URL.
###########################################
#       3. STAGING & SNAPSHOTS
###########################################
git status
    → Shows working directory status.

git add <file>
    → Stage a specific file.

git add .
    → Stage all modified/created files.

git reset <file>
    → Unstage a file (keeps changes).

git diff
    → Show unstaged changes.

git diff --staged
    → Show staged changes.

git commit -m "message"
    → Commit staged changes.
###########################################
#        4. BRANCHING & MERGING
###########################################
git branch
    → List all branches.

git branch <name>
    → Create a new branch.

git checkout <branch>
    → Switch to a branch.

git merge <branch>
    → Merge a branch into current branch.

git log
    → View commit history.
###########################################
#       5. REMOTE REPOSITORIES
###########################################
git remote add origin <url>
    → Add a remote repository.

git fetch
    → Download latest changes without merging.

git merge origin/main
    → Merge fetched changes.

git pull
    → Fetch + merge in one step.

git push
    → Push commits to remote.
###########################################
#       6. FILE CHANGES & RENAME
###########################################
git rm <file>
    → Remove a tracked file.

git mv old new
    → Rename or move a file.
###########################################
#              7. STASH COMMANDS
###########################################
git stash
    → Save uncommitted work temporarily.

git stash list
    → View stashes.

git stash pop
    → Restore + remove last stash.

git stash drop
    → Delete last stash.
###########################################
#        8. HISTORY & COMPARISON
###########################################
git show <SHA>
    → Show commit details.

git log --follow <file>
    → Track file history across renames.

git diff branchA..branchB
    → Compare differences between branches.
###########################################
#        9. ADVANCED HISTORY CONTROL
###########################################
git rebase <branch>
    → Rewrite commit history on top of another branch.

git reset --hard <commit>
    → Reset branch to an earlier commit and remove all changes.
###########################################
#         10. COMMON .gitignore
###########################################
Example `.gitignore`:

node_modules/
.env
logs/
*.log
===========================================
        END OF MERGED GIT CHEAT SHEET
===========================================