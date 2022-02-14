# Git Tutorial
## Introduction
-  Git is a version control system for tracking changes in computer files. It is a distributed version control system or decentralized control system, which means that multiple developers can work on a single project at the same time, without having to be on the same network. Git coordinates work between multiple developers and it tracks every single version and every single change that is made on the project. It also allows users to revert back to specific versions of any file in the project at any time as long as it was committed to the repository. When using git there will be a repository on your local machine that you work on and make changes and then you push it to a remote repository which is on GitHub. GitHub is the provider of internet hosting for version control using git. An internet connection is not required to work on the local repository because it is local to the machine you are using, but it is required if you want to push it to the remote repository on GitHub. 
- Git will keep track of code with snapshots of the files. These snapshots are made by making a commit with a simple command and you can always go back to see any snapshot of previously written code and you can always revert back to it, which keeps the code secure when working on it.
- The code can be placed in a staging area before making the commit and this is done using a simple add command.
- Once a commit is made to the remote repository on GitHub, other developers will be able to make changes and create branches, which will be discussed in this tutorial.

## Setting up the repository and making the initial commit
- To start, our project should be located on the desktop in a folder called “Project.” This folder will contain all of the files for the project we want to push to git. We can add the first program we are working on, which will be called ForLoop.java.
- With the file in the project folder, we are ready to begin moving the project to git.
- In the terminal we need to first change the working directory to the desktop.
  > cd desktop
- We also need to change the working directory to the project folder.
  > cd Project 
- We next want to initialize the folder as a git repository, so that we may begin using the git commands.
  > git init
- We need to add the ForLoop.java file to the staging area.
  > git add ForLoop.java
- Now we can check what is in our staging area. This will tell us that the ForLoop.java file has changes to be committed and that we have added it to the staging area. This is dine using the status command.
  > git status 
- If we change something in the ForLoop.java file and use the status command again, we will get a message indicating that the ForLoop.java file is no longer in the staging area and that’s because we have updated it. So in order to get it back to the staging area, we must add it back again. using the add command. Now, if we use the status command again, we will find that it is once again in the staging area.
  > git status
  > git add ForLoop.java
  > git status
- Now we want to commit the file to our local repository and add a message to indicate what the changes are to the file. Since this is the first commit, our message can simply be “Initial commit.”
  > git commit -m “Initial commit”
- For the next step, we need to go to GitHub in the browser and create a new repository, give it a name, and give it a description. The name can be “Tutorial” and the description can be “GitHub tutorial.” And then we can select whether we want it to be public (anyone can view it and we select who can commit) or private (we select who can view it and who can commit). We can also choose to initialize with a README file, but for the sake of this tutorial we are not going to do that, as we will learn to add this in later on from the terminal. Finally, click on the green “Create repository” button at the bottom.
- If we use the remote command, we will get nothing in our terminal, because we do not yet have a remote repository added.
  > git remote 
- We will need to locate the url for the repository which will be located at the top on GitHub. Copy this url and go back to terminal and type the following command, with the url pasted. This step will allow us to add the git repository as a remote repository.
  > git remote add origin https://github.com/mmb1214/Tutorial.git
- Now if we type git remote, our output will be “origin”
  > git remote
- Next, we want to push from our local repository, to the remote GitHub repository, on the master branch. And this will make sure that the ForLoop.java file will now be on the remote GitHub repository and other developers will be able to view the project and work on it as well.
  > git push -u origin master

## Adding a README
- Now we might want to add a README file, to provide other developers some information about the project we are working on and this file will be in markdown language, hence the .md extension. Creating the file can be done with the touch command which creates a new file if it does not already exist, but otherwise accesses it.
  > touch README.md
- Now if we go to our project folder called “Project,” the README.md file will show up there and we can edit it. We can type for example, “My project”
- Then we need to add it to the staging area.
  > git add README.md
- Then we need to commit it and add a message such as “Added README"
  > git commit - m “Added README”
- Finally, we need to push it to the remote GitHub repository.
  > git push

## Making updates to the already existing project
- If we are not yet in the directory for the project we need to first change the working directory to the desktop and then change it to the project folder.
  > cd desktop
  > cd Project
- We need to make sure we are making the changes on the correct branch, so if we wanted to make the changes directly onto the master branch we would checkout master.
  > git checkout master 
- Then we need to add the changed files to the staging area. We can add all the files to the staging area using git add . or if we can add the specific files we have made changes to, such as if we have made changes to the ForLoop.java file.
  > git add .           or           git add ForLoop.java
- Then we need to commit the changes to the remote repository and add a message. If we added an if statement for example, then we should add a message like “Added an if statement.”
  > git commit -m “Added an if statement”
- Finally, we need to push the changes to the remote repository. 
  > git push

## Branching

If you are a developer working on a project with multiple individuals and you are assigned a specific task, you may want to make specific changes and push to the repository and have the main code base edited without the functionality being changed, so branches allow you to work in a separate branch and still commit changes without affecting the main branch which is called the master branch.

- To begin creating a branch, make sure the working directory is changed to the project folder and type in the following command with a name for the branch “mybranch.”
  > git branch mybranch
- The last command will not change us to the “mybranch” branch, so in order to do that, we will use the checkout command. This will place is on the new branch, mybranch
  > git checkout mybranch
- Now if we want to make changes on mybranch, let’s begin by first making a java file in the Project folder, called “whileLoop.java.”
  > touch whileLoop.java
- Now we can edit the whileLoop.java file and add in a simple a while loop.
- Once we have edited the whileLoop.java file, we can add it by using the add all command.
  > git add .
- Then we can commit
  > git commit -m “Added while loop file”
- If we want to change the branch between the main and the mybranch branch, simply use either of these commands and if we look at the project folder, we will notice that it will reflect the branch that is currently checked out.
  > git checkout master.    *or*     git checkout mybranch
- Now if we are done with the functionality of the whileLoop.java file in the mybranch branch, we can merge it with the main branch. But we do first need to have the master branch checked out. After checking out the master branch, then we can use the merge command.
  > git checkout master
  > git merge mybranch

## Stashing
The git stash command is useful whenever we have changes that we are not yet ready to commit and maybe we need to switch branches or we may even want to temporarily revert back to where you started and you are unsure of what to do with your changes. The git stash command will save the changes to a temporary location that we can come back to later on.

- To begin, we will begin by branching with a new branch called feature-a.
  > **git branch feature-a**
- Then we want to checkout the branch to make sure we are working on it.
  > git checkout feature-a
- Now, let’s go into a file such as the whileLoop.java file and make a change to the file such as by adding a System.out.println statement.
- If we use a git diff command, it will highlight the changes we made.
  > git diff
- At this point, if we want to switch back to the master branch to check something out or we need to see what our whileLoop.java file looked like before we made any changes to it, we can stash the changes we just made and go back to where we were before. To do this, we can use the stash command and add a message at the end to remind us of the purpose of the stash. The message can be something like “Worked on whileLoop.java file”
  > git stash save “Worked on whileLoop.java file”
- To make sure of this, if we use a git diff command, nothing will show up. 
  > git diff
- And if we do a git status, the terminal will show that there is nothing to commit.
  > git status
- Additionally, if we go to that whileLoop.java file, the changes we made, adding the System.out.println() statement, will be gone. The change however is not gone for good. If we use the git stash list command, it will reveal the message from the stash that we made as well as its id.
  > git stash list
- Now if we are ready to bring back the changes made in the stash, we need to use the pop command, which will take the most recent stash and apply the changes made in it. Since we have only made one stash, it will apply the changes of that stash.
  > git stash pop
- If there were multiple stashes, the pop command may not suffice since it only applies the most recent stash, so in this case, git stash apply command will work best. At the end of this command, the id of the stash should be added, such as stash@{0}
  > git stash apply stash@{0}
- Additionally, if we want to remove a specific stash, we can use the drop command, with the stash’s id
  > git stash drop stash@{0}
- Or if we want to get rid of all of the stashes, we can use the clear command. 
  > git stash clear

## Cloning a Git repository
Cloning is downloading a project from its remote repository on GitHub, onto your own computer. For this example, we will clone the Project repository from GitHub, to get the files on our computer. To begin, we need to delete the already existing files from our computer.

- The first step is to go to the repository on GitHub. We need to locate the green button with the word “Code” on it and copy the HTTPS link, which in this case is https://github.com/mmb1214/Tutorial.git.
- Then, in the terminal, we need to change directory to the desktop, so that the repository’s files can be easily located on our desktop.
  > cd desktop
- Finally, we need to use the clone command and paste the url after it. This will get the project from GitHub and put it on our computer. And this will create a new folder with the name of the repository, on our computer. In this case, the repository was called “Tutorial,” so the folder on our computer will also share that name.