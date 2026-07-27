## Git hub Login: 

**Via WSL:**
- sudo apt update
- sudo apt install gh -y
- gh auth login
Note: Here if the aut not possible via WSL, you wiull get a code in the WSL session and a Github Portal address so you can auth with that code. 

## Modify a Repository or add inforamtion:

Move to the projects folder in your local PC (WSL - ~/gitprojects/)
- cd ~/gitprojects/

Load the repo you need to modify:
- git clone https://github.com/kajuare/<Repo-Name>.git

Create either the .md file you want to add or the folder you need.
- mkdir -p <Folder-Name>
- touch <File-Name>.md -> Add the content via Vi or Nano. 
- nano <Folder-Name>/<File-Name>.md

Step I am trying to understand: 
- git add <Folder>/<File>.md
- git commit -m "Aqui va una descipcion para el folder que se creo anteriormente".
Note: creo que aqui en el commit es que se crea el folder o se actualzia en GitHub y luego ademas agrega una descripcion.
Esta misma descripcion parece se le agrego al folder y al file .mb que esta dentro. 
- git push
Note: o no se si es este el que hace todo en GitHub. 


