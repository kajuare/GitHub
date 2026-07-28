## Git hub Login: 

**Via WSL:**
- sudo apt update
- sudo apt install gh -y
- gh auth login
Note: Here if the aut not possible via WSL, you wiull get a code in the WSL session and a Github Portal address so you can auth with that code. 

# Diagram:
![GitHub Login WSL Flow](/GitHub/ImagesGit/github_login_flow.png)

## Modify a Repository or add inforamtion:

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

# Diagram:
![GitHub Modify Repo](/GitHub/ImagesGit/modify_repo_add_content_final.png)

## To Update a file: 

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

# Diagram:
![GitHub Update Repo](/GitHub/ImagesGit/update_existing_file.png)

## To upload images: 

If there is no specific folder for images, crete it: 
- mkdir /gitprojects/Repository/ImageFolder
- cp /mnt/c/Users/YOUR_WINDOWS_USERNAME/Downloads/screenshot.png ~/gitprojects/gitprojects/Repository/ImageFolder/ImageName.png

Commit and push like normal:
- git add Repo-Folder/Image-Folder/IMAGE.png Repo-Folder/File-name.md
or
- git add GitHub/   -- this informs abput multiple changes on the specific repo.
- git commit -m "Add SSPR config screenshot to Entra ID notes"
- git push

# Diagram:
![GitHub Update Images](/GitHub/ImagesGit/upload_images_flow.png)



