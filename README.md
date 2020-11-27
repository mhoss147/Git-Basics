# Git Basics LA
# ------------------------------------------------------------------


# Git Introduction and Architecture
# ------------------------------------------------------------------

# By default, every get repositories begins with one branch in that branch is called MASTER

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

  $ git remote add origin remoteRepositoryURL
  
  like, git remote add origin https://github.com/...


# Verifies the new remote URL

  $ git remote -v


# Pushes the changes in your local repository up to the remote repo

  $ git push origin master
  
  $ git push origin master -f (with force)
  
  
# NOTICE: This is never a recommended use of git. This will overwrite changes on the remote. Only do this if you know 100% that your local changes should be pushed to the remote master.

git push -f origin master


# Reset local repository branch to be just like remote repository HEAD


- To remove the git commit which you have added locally do:

	git reset --hard HEAD^

- To remove the remove the uncommitted files, do:

	git clean -fd

check out other git Clean options here:

https://git-scm.com/docs/git-clean

- and then do

	git fetch
	git rebase origin/master

or

   	git pull
	
Ref: https://stackoverflow.com/questions/34888874/delete-all-the-local-files-and-download-a-fresh-copy-from-git

  
- If you want to save your current branch's state before doing this (just in case), you can do:

git commit -a -m "Saving my work, just in case"
git branch my-saved-work



- Setting your branch to exactly match the remote branch can be done in two steps:

git fetch origin
git reset --hard origin/master

Ref: https://stackoverflow.com/questions/1628088/reset-local-repository-branch-to-be-just-like-remote-repository-head


# Quick setup — if you’ve done this kind of thing before
or	
https://github.com/mhoss147/Certified-Jenkins-Engineer-2020-.git
Get started by creating a new file or uploading an existing file. We recommend every repository include a README, LICENSE, and .gitignore.

…or create a new repository on the command line
echo "# Certified-Jenkins-Engineer-2020-" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/mhoss147/Certified-Jenkins-Engineer-2020-.git
git push -u origin main
                
…or push an existing repository from the command line
git remote add origin https://github.com/mhoss147/Certified-Jenkins-Engineer-2020-.git
git branch -M main
git push -u origin main
…or import code from another repository
You can initialize this repository with code from a Subversion, Mercurial, or TFS project.



# For new repository my steps:

1. Create a folder in my local pc with same name of remote repo
Create a remote repo in your github with same name of the local folder
DO NOT ADD readme file

2. open that folder from vs code > file > open folder > browse to the folder and select it > open

3. In vs code use 'ctl + ~' for terminal

4. Create new file in vs code

5. In code terminal:

$ git init 
$ git add .
$ git commit -a -m "abcd..."
$ git remote add origin https://github.com/... 	(https://github.com/... = remote repo link)
$ git push origin master



# Authenticate to your Github from Git (Linux)

- Easy way: Use an ssh ke pair

$ ssh-keygen -t rsa -b 4096

Enter file in which to save the key (/home/cloud_user/.ssh/id_rsa): I am leaving it empty


Enter passphrase (empty for no passphrase): I am leaving it empty


Your identification has been saved in /home/cloud_user/.ssh/id_rsa.
Your public key has been saved in /home/cloud_user/.ssh/id_rsa.pub.


- See the content of the public key

$ cat /home/cloud_user/.ssh/id_rsa.pub


Copy the ssh-key

Goto your Github a/c > settings > SSH and GPG keys (on the left) > New SSH key > put title and paste the ssh-key > Add ssh key

Now the git installation will be able to authenticate with Github.com in order to pull and push changes to source code repository


# Fork: Use it you want to make changes to repo

Forks provide a way for any user to create their own personal copy of a GitHub repository which they can fully control without interfering with other users. 


Copy GitHub repository link > paste in address bar > click "FORK" (in upper  right corner)


# Clone a repository

- After forking the repo to your github you can clone it to your local machine 

	From Code icon on the top right or use 
	
	$ git clone https://github.com/...(repo address)
	
	
- Verify if cloned

$ ls -la

copy the fileName


- Goto that dir

$ cd fileName


- Check the dir here

$ ls -la


- Make sure your location is actual git repositoy

$ pwd


$ git status

$ git add .

$ git commit -m "yourMessage"



# About "git push"

$ git push -u <remoteName, usuallyOrigin> <branchName>


- Editing one of the file - views/index.jade 

vim views/index.jade 

Changing one of the Header here...

$ git status

	# Changes not staged for commit:
>>>	#   (use "git add <file>..." to update what will be committed)
	#   (use "git checkout -- <file>..." to discard changes in working directory)
	#
	#       modified:   views/index.jade


$ git add .


$ git commit -m "Changed header text"


$ git status


	# On branch master
>>>	# Your branch is ahead of 'origin/master' by 1 commit.
	#   (use "git push" to publish your local commits)
	#
	nothing to commit, working directory clean


Here "origin/master" is the remote repository


- Try to push it with 

$ git push

Will prompt for your details

Username for 'https://github.com': Username for your github, for me "mhoss147"

Password for 'https://mhoss147@github.com': Password for your github, for me "boroCheleBond"


$ git status

	# On branch master
	nothing to commit, working directory clean

	
	
# Command "git checkout"

$ git checkout => checks out an existing branch i.e. it puts the contents of the branch into your working tree
			and your working copy of the source code files.
			
			When you commit, whichever branch you have checked out will be the branch that the commit will be added.
			
$ git checkout <branch>
	
	
	
- Create a new branch and check it out immediately with -b flag


$ git checkout -b <newBranch>
	
- Go to your local folder and check the branch name

$ cd folderName

$ git branch

$ git status
#On branch master
nothing to commit, working directory clean

$ git checkout -b newBranchSorowar
Switched to a new branch 'newBranchSorowar'

$ git status
#On branch newBranchSorowar
nothing to commit, working directory clean


- Go back to master branch

$ git checkout master

$ git status
#On branch master
nothing to commit, working directory clean


- Create a Tag (can be used for version of the App)

$ git tag myTagSorowar		(myTagSorowar = tag name)

$ git tag 
myTagSorowar
	

# Pull request

Merges can be handled locally using git, another way is using pull request 

Pull requests is made to merge changes of yourCode into anotherBranch (usually a shared mainline), 
and other team member can approve or deny the changes!

- Make a pull request

	go to your github a/c > go to repo you have made changes > click "branches" tab > will see ALL the branches > click "New pull request" (on the right of yourBranch) >
	
	Click the dropdown of "base repository" and select (this is WHERE youCode going now) from "head repository" > 
	
	you can change title, leave a comment > click "Create pull request" > will see "userName wants to merge 1 commit into master from youBranchName" >
	
	(code are not merged yet) all in the team can click "commits or file changed" tab and see the changes> click "Merge pull request" and > 
	
	"confirm merge" to confirm the Merge


# Create branch from master, work on branch, and merge the branch to master


	cloud@Azure:~$ ls
	clouddrive  scm
	cloud@Azure:~$ mkdir sorowarscm
	cloud@Azure:~$ cd sorowarscm/
	cloud@Azure:~/sorowarscm$ git init
	Initialized empty Git repository in /home/cloud/sorowarscm/.git/
	cloud@Azure:~/sorowarscm$ touch file1.rb
	cloud@Azure:~/sorowarscm$ git status
	On branch master

	Initial commit

	Untracked files:
	  (use "git add <file>..." to include in what will be committed)

		file1.rb

	nothing added to commit but untracked files present (use "git add" to track)

	cloud@Azure:~/sorowarscm$ git add file1.rb
	cloud@Azure:~/sorowarscm$ git status
	On branch master

	Initial commit

	Changes to be committed:
	  (use "git rm --cached <file>..." to unstage)

		new file:   file1.rb

	cloud@Azure:~/sorowarscm$ git commit -a -m "Initial commit to file1"
	[master (root-commit) 0bd0032] Initial commit to file1
	 1 file changed, 0 insertions(+), 0 deletions(-)
	 create mode 100644 file1.rb
	cloud@Azure:~/sorowarscm$ git status
	On branch master
	nothing to commit, working directory clean

- Craete a branch named sorowarBug

	cloud@Azure:~/sorowarscm$ git branch sorowarBug

- Switch to that branch

	cloud@Azure:~/sorowarscm$ git checkout sorowarBug
	Switched to branch 'sorowarBug'




	
----------------------------------------------

