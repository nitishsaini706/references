### basic comands 
- git config --global user.name name  
- git config --global user.email email
- git init  - to initialise a git repo for a new or existing project
- git add <file-name>  - add one or more files to staging (index) 
- git status - list the files we have changed and those you still need to add or commit
- git commit -m "commit message " - commit changes to the file
	- in first commit we write initial commit as a convention
- git commit -am " commit message " - it add and commit in one command
- git log - tells all the commit we did
- git rm --cached <file-name> - to remove file from staging area 
- git branch <branch-name> - to create new branch with name
- git checkout <branch-name> - to switch from current branch to another
- git merge <branch-name> - to merge a branch into current branch 
- git remote add origin link - to connect local with remote repo
- git push -u origin <branch-name> - to push branch to remote repo
- git pull 
- git diff - tells about the diff in files from staging area with working directory 
	- git diff --stagged - compare with last commit
 