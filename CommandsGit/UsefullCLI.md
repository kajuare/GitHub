# Git hub Login: 

**Via WSL:**
- sudo apt update
- sudo apt install gh -y
- gh auth login
Note: Here if the aut not possible via WSL, you wiull get a code in the WSL session and a Github Portal address so you can auth with that code. 

## Diagram:
![GitHub Login WSL Flow](../ImagesGit/github_login_flow.png)

# Modify a Repository or add inforamtion:

Move to the projects folder in your local PC (WSL - ~/gitprojects/)
- cd ~/gitprojects/

Load the repo you need to modify:
- git clone https://github.com/kajuare/Repo-Name.git

Create either the .md file you want to add or the folder you need.
- mkdir -p Folder-Name
- touch File-Name.md -> Add the content via Vi or Nano. 
- nano Folder-Name/File-Name.md

Prepare the change: 
- git add Folder/File.md

Confirm Change with a message: 
- git commit -m "Message"

Push the change to the file in GitHub Repo:
- git push

## Diagram:
![GitHub Modify Repo](../ImagesGit/modify_repo_add_content_final.png)

# To Update a file: 

Go to the repo fodler:
- cd ~/gitprojects/Repo-Name/Folder-Name/

Review if current dat local is updated with the one in Git Repo:
- git pull

Edit the file you need to update: 
- nano Folder-Name/Fileto-to-modify.md

Review the change:
- git status
- git diff

Prepare the change: 
- git add 01-identity/entra-id-basics.md
 
Confirm Change with a message: 
- git commit -m "Message"

Push the change to the file in GitHub Repo:
- git push

## Diagram:
![GitHub Update Repo](../ImagesGit/update_existing_file.png)


# To upload images: 

If there is no specific folder for images, crete it: 
- mkdir /gitprojects/Repository/ImageFolder
- cp /mnt/c/Users/YOUR_WINDOWS_USERNAME/Downloads/screenshot.png ~/gitprojects/gitprojects/Repository/ImageFolder/ImageName.png

Commit and push like normal:
- git add Repo-Folder/Image-Folder/IMAGE.png Repo-Folder/File-name.md
or
- git add GitHub/   -- this informs abput multiple changes on the specific repo.
- git commit -m "Add SSPR config screenshot to Entra ID notes"
- git push

## Diagram:
![GitHub Update Images](../ImagesGit/upload_images_flow.png)

# Monitoring changes: 

To review modifications and commits: 
- git log

# Manage branches: 

To create a new branch:
- git branch <branch name>

Switch to an existing branch:
- git checkout sarah

To create a new branch and switch to it: 
- git checkout -b <branch name>

To review on which branch are you working on:
- git branch

To make local branch to appear in Github: 
- git push -u origin <branch name>

Delete a branch:
- git branch -d max

# Understanding Git Merge: Fast-Forward vs. No-Fast-Forward (`--no-ff`)

When you merge one branch into another in Git, Git decides how to combine the histories. The two main ways it handles this are **Fast-Forward** and **No-Fast-Forward** merges.

---

## 1. Fast-Forward Merge (`git merge`)

### What is it?
A Fast-Forward merge happens automatically when there are **no new commits on `<main branch name>`** since you created `<own branch name>`. 

Instead of creating a new "merge commit," Git simply moves the tip of `<main branch name>` forward to point at the latest commit of `<own branch name>`.

### Before Merge:
```text
C0 --- C1 ( <main branch name> )
         \
          C2 --- C3 ( <own branch name> )
```

### Commands to execute:
```bash
# Switch to the target branch
git checkout <main branch name>

# Merge your feature branch (defaults to fast-forward if possible)
git merge <own branch name>
```

### After Merge:
```text
C0 --- C1 --- C2 --- C3 ( <main branch name>, <own branch name> )
```

### Key Takeaways:
* **History:** Linear and clean. Looks like all work was done directly on `<main branch name>`.
* **Merge Commit:** None is created.
* **Best for:** Small, quick features or individual bug fixes.

---

## 2. No-Fast-Forward Merge (`git merge --no-ff`)

### What is it?
A No-Fast-Forward merge forces Git to create a **dedicated merge commit**, even if a fast-forward merge is possible. 

This preserves the explicit history that `<own branch name>` existed as a separate group of commits before being combined into `<main branch name>`.

### Before Merge:
```text
C0 --- C1 ( <main branch name> )
         \
          C2 --- C3 ( <own branch name> )
```

### Commands to execute:
```bash
# Switch to the target branch
git checkout <main branch name>

# Force a merge commit
git merge --no-ff <own branch name> -m "Merge branch '<own branch name>' into <main branch name>"
```

### After Merge:
```text
C0 --- C1 ----------- M ( <main branch name> )
         \           /
          C2 --- C3 ( <own branch name> )
```
*(Where `M` is the newly created merge commit)*

### Key Takeaways:
* **History:** Non-linear. Clearly shows the branch topology and when features were integrated.
* **Merge Commit:** Always created (`M`).
* **Best for:** Pull requests, multi-commit feature branches, or shared team branches where keeping context is important.
---

## Summary Comparison

| Feature | Fast-Forward (`git merge`) | No-Fast-Forward (`git merge --no-ff`) |
| :--- | :--- | :--- |
| **Merge Commit Created?** | No | Yes |
| **Git History** | Straight line (Linear) | Branching tree (Non-linear) |
| **Easy to revert full feature?** | Harder (must revert individual commits) | Easier (revert the single merge commit `M`) |
| **Default behavior?** | Yes (if no diverging commits exist) | No (must pass `--no-ff` flag) |
