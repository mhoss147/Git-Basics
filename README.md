# Git Basics LA


# Git Introduction and Architecture

Commit: Is siply a state. The git commit command is one of the core primary functions of Git. Prior use of the git add command is required to select the changes that will be staged for the next commit. Then git commit is used to create a snapshot of the staged changes along a timeline of a Git projects history.


How do I commit a file in Git?
Create a new file in a root directory or in a subdirectory, or update an existing file. Add files to the staging area by using the "git add" command and passing necessary options. Commit files to the local repository using the "git commit -m <message>" command.
  
Head: Current commit is called Head. 

Head > Commit > Content.



# Git Installation and Configuration


Log into your account; here i did; 
cloud_user@...71c:~$ 

This user does not have permission to install git; so sudo

$ sudo yum install git (for RedHat/CentOS)

$ sudo apt-get install git (for Ubuntu/)

[sudo] password for user: ...

Is this ok (yes/no): yes


$ git --version

#see current configuration
$ git config -l























