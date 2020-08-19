
# Git Basics LA

# ------------------------------------------------------------------

# Git Introduction and Architecture

# ------------------------------------------------------------------



Commit: Is siply a state. The git commit command is one of the core primary functions of Git. Prior use of the git add command is required to select the changes that will be staged for the next commit. Then git commit is used to create a snapshot of the staged changes along a timeline of a Git projects history.


How do I commit a file in Git?
Create a new file in a root directory or in a subdirectory, or update an existing file. Add files to the staging area by using the "git add" command and passing necessary options. Commit files to the local repository using the "git commit -m <message>" command.
  
Head: Current commit is called Head. 

Head > Commit > Content.

# ---------------------------------------------------------------

# Git Installation and Configuration

# ------------------------------------------------------------------


Log into your account; here i did; 

cloud_user@...71c:~$ 


This user does not have permission to install git; so use sudo


# (for RedHat/CentOS)

$ sudo yum install git 

[sudo] password for user: ...


Is this ok (yes/no): yes

# (for Ubuntu/)

$ sudo apt-get install git 

[sudo] password for user: ...


Is this ok (yes/no): yes


# See if installed

$ git --version

# Location

$ which git


# For help

$ man git


# To searh manual

$ man git (then inside page /"wordYouWantToSearh" , press "q" to go back to terminal)


# See current configuration

$ git config -l



$ git config --global user.name "Mo So"



$ git config --global user.email "dkfjdfj@gmail.com"




$ sudo git config --system core.editor vim


# Check if configured

$ git config -l

core.editor=vim

user.name=Mo So

user.email=dkfjdfj@gmail.com


# (~) Tilda is home directory in Linux;   (.) for hidden directory;we are looking at the content of /home/cloud_user@...71c/ gitconfig  file


$ cat ~/.gitconfig 


[user]

        name = Mo So
        
        email = dkfjdfj@gmail.com


$ cat /etc/gitconfig 

[core]

        editor = vim
        
# ------------------------------------------------------------------

# Working with Repositories in Git

# ------------------------------------------------------------------


# Present working directory

$ pwd




# Make a directory

$ mkdir mohDirctory


# Go to mohDirctory

$ cd mohDirctory/


# See files inside it; note that, alias ll == ls -l

$ ll -a

      
          
# Create empty repository

$ git init "file/dir name"



# See all files incl. hidden

$ ll -a



# Look inside .git directory

$ ll -a .git/


# Creating New text file named intro

$ vim intro.txt


# Write inside that file

Esc i


# Save and exit

Esc shift + : qw return


# Exit without saving

Esc shift + : q! return



# To see the status of current directory

$ git status



# To start git tracking the file

$ git add "fileName.extension"



# To Save in git

$ git commit -m "yourMessage"


# To see if file modified

$ git status



# To add all files from current directory use (.)

$ git add .


# To see who made changes to what

$ git log



# To (no longer will be tracked by Git); delete file from Git and from Directory 

$ git rm "fileName.extension"
#Don't forget to Commit




# To delete file from Directory Only

$ rm "fileName.extension"




# If we delete file accidentally. To bring that file back

$ git checkout --(space) "fileName.extension"

# ------------------------------------------------------------------

# Managing What is Tracked with gitignore

# ------------------------------------------------------------------



# Create a sample empty jpg file named pic

$ touch pic.jpg


# To ignore the files you don't want to track

$ vim .gitignore



# List all the files you wan to ignore

$ *.jpg 



# Create 1 folder named temp and 2 files in it named moh & sak

$ mkdir temp
$ touch temp/moh
$ touch yemp/sak
$ ls -l


# If you dont want git to track folder temp and files moh & sak; just add temp in .gitignore

$ vim .gitignore
temp/ (write inside editor, save and exit)
$ git status


# It is also possible to exclude certain paths

$ git config --global core.excludesfile <path>

# ------------------------------------------------------------------

# Cloning Repositories

# ------------------------------------------------------------------


# See the files in PWD

$ ls -l


# Go one step back/up

$ cd .. 


# To clone a folder/dir

$ git clone "folder/dir name"/ "just put the name of folder/dir where you want to clone; it will also create that folder/dir"

$ ls -l (check if cloned)


# Go to the folder/dir, where you just cloned

$ cd "folder/dir"/


# Create a file there

$ touch "fileName.Ext"



# Save/commit that file to git

$ git commit -m "yourMessage"

$ git log (check the dtails)


# Go to original folder/dir 

$ cd ../"folder/dir name"/

$ git log (see, it does not have the clone; beccause each repo is unique. We've 2 different records tracking 2 different folder/dir)



# Cloning via SSH 

$ git clone my_username@server:<org-path-relative-to-user-home> ~/<local-repo-path>
  
  
  
# Cloing from Github

$ git clone "https://github.com/..." ~/"local-repo-path"  (if you don't give the name of <local-repo-path>, it will copy to pwd)
  
$ cd ../"local-repo-path"
  
$ ls -l (see the files)

$ git log (se the details of cloning)

(press "q" to go to terminal)




# To work on any files you just cloned

$ vim "existing fileNam"
  
(save and exit)  



# Add that file you just modified to git

$ git add "existing fileName"

$ git status (see the files modified)



# Save modified file

$ git commit -m "yourMessage"

$ git log (see what added)

(press "q" to go to terminal)



# Push it to git origin from our master

$ git push origin master

(put user name and password when prompt)



# ------------------------------------------------------------------

# Understanding Git Logging

# ------------------------------------------------------------------


# Who did what in repo

$ git log



# In short 

$ git log --oneline



# Details of who did what in repo

$ git log -p

(/"what you wan to search here")

(press End to go down. press Shft + End to go up)
  
(press "q" to go to terminal)



# Who did what in file

$ git log -- (space) "fileName"
  
  

# Who did what in file in short

$ git log --oneline "fileName"
  
  
  
# To see graphical representation

$ git log --graph --decorate



# ------------------------------------------------------------------


# Working with Branches in Git

Branching allows you to create an effective copy of the master branch within the repo that can be worked on without interfering with the master.

Branch can be used to fix the bug; create new features. It declutters the master branch.

Branch is similar to cloning except it is in the same repo

Branch can be merged back into master branch when work is complete.



# ------------------------------------------------------------------



  
# Create a branch

$ git branch "newBranchName"
  
  
  
# To change to that branch

$ git cheakout "existingBranchName"

$ git status (see...)



# Create a new directory named website2

$ mkdir website2



# Create a file inside that directory

$ touch website2/index.html

$ touch website2/logo.jpg



# Add everything inside of that dir

$ git add website2/*

$ git status (see..)


# Save to the branch you created 

$ git commit -m "yourMessage"

$ git status (see..)

$ ls -l (see files)

$ ls -l website2/ (see files)



# Switch back to master 

$ git checkout master 

$ ls -l (see website2 is not here)



# Create a branch and switch back to it immediately

$ git checkout -b "newBranchName"

$ git status (see if you are in branch)


# See what you have in this branch

$ vim .git/



# Open one of the file

$ vim "existingFileName"
  
(edit and save, exit)


# Save waht you did

$ git commit -a -m "yourMessage"  (-a will add everything you changed)

$ git status (see what saved)


# See contents of the file

$ cat "existingFileName.extn"



# Switch back to branch


$ git checkout "existingBranchName"


# Switch back to master 

$ git checkout master




# ------------------------------------------------------------------

Merging and Pushing Changes in Git

# ------------------------------------------------------------------



# Clone everything to new dir from pwd

$ git clone "nameOfThepwd"/ (space) "nameOfTheNewDirYouWantToPutClone"
  
  
# Go to that new dir

$ cd "nameOfTheNewDirYouWantToPutClone"/
  
$ git status (see if you are in branch...)  

$ git checkout "branchNameYouWantToGo"

 


# See the git configuration before push

$ git config -l



# Push your new branch (stay in that dir)

$ git push origin "branchName-you-want-to-push"
  
  
  
# Push all the branches to origin

$ git push origin --all


# Merge branch to master 


$ git checkout master (go to master)

$ git merge "branchName-you-want-merge"
  
$ ls -l (see the long list)

# ------------------------------------------------------------------

# Adds the files in the local repository and stages them for commit

  $ git add .
  
  
# Commits the tracked changes and prepares them to be pushed to a remote repository

  $ git commit -m "First commit"
  
  copy the remote repository URL


# Sets the new remote

  $ git remote add origin remote repository URL


# Verifies the new remote URL

  $ git remote -v


# Pushes the changes in your local repository up to the remote repo

  $ git push origin master
  
  $ git push origin master -f (with force)
  
  
# ----------------------------------------------











