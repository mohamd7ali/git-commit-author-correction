# Fixing Wrong Author in Git Commits (Interactive Rebase)

If some of your commits were made with the wrong Git user (e.g., `anonymous_user`) and you want to change them to your own account (e.g., `mohamd7ali`), you can rewrite the commit history with **interactive rebase**.

⚠️ **Warning:** This rewrites Git history. Only do this if you understand the impact and are okay with force-pushing.  
Make a backup branch first:
```bash
git branch backup-my-branch
```

## Step 1 – Start Interactive Rebase

Run:
```bash
git rebase -i HEAD~10
```
This will open the last 10 commits in an editor.

## Step 2 – Mark Commits to Edit

In the editor, change `pick` → `edit` for the commits with the wrong author.
Example:
```text
edit 1f63846 modify the gitignore file
edit 408cdb9 Add DMD & AFIS Codes for SD302 Dataset
edit 6014797 Add Evaluation Codes for Police Dataset
edit 0086e66 Add Codes of Combination Scores
edit 53e1bf6 Add Python Script to Check the Combined Scores that are Monotonic or Not
edit dc0e44f Add combination_scripts Folder
edit fb659ca Add Normalization Script
edit c932202 rename the normalization.py to 02_normalization.py
edit f985d85 Add Average Combination Method Script
pick 9d66b49 Max Combination Script   # already correct, leave as pick
```
Save and exit the editor.

## Step 3 – Amend Each Commit

For each commit marked `edit`, Git will pause and let you change it.
Git will stop at that commit. Run:
```bash
git commit --amend --author="Mohammad Ali Etemadi <your.email@example.com>" --no-edit
```
- Replace `your.email@example.com` with the email that is registered in your GitHub account (for example for me it is mohamd7ali).

Then continue the rebase:
```bash
git rebase --continue
```

Git will move to the next commit you marked as edit.
- Repeat the --amend + --continue cycle until all are done.

## Step 4 – Push the Rewritten History
When finished, you’ve rewritten the last 10 commits.
Finally, push your branch to GitHub with:
```bash
git push origin feature/moham... --force-with-lease
```
- `--force-with-lease` is safer than `--force` because it prevents overwriting if someone else pushed new commits in the meantime.

Now all the commits should show your correct name and email (Mohammad Ali Etemadi <your.email@example.com>), and GitHub will attribute them to your account.

# Author
Mohammad Ali Etemadi Naeen


