# Fixing Wrong Author in Git Commits (Interactive Rebase)

If some of your commits were made with the wrong Git user (e.g., `anonymous_user`) and you want to change them to your own account (e.g., `mohamd7ali`), you can rewrite the commit history with **interactive rebase**.

⚠️ **Warning:** This rewrites Git history. Only do this if you understand the impact and are okay with force-pushing.  
Make a backup branch first:
```bash
git branch backup-my-branch
