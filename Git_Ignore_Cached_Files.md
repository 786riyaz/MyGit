If node_modules was already committed before adding .gitignore, Git will still track it.
Remove cached tracking:
git rm -r --cached node_modules
git rm -r --cached **/node_modules
git commit -m "Remove node_modules from git tracking"