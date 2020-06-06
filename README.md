
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


This user does not have permission to install git; so use sudo


(for RedHat/CentOS)

$ sudo yum install git 


(for Ubuntu/)

$ sudo apt-get install git 

[sudo] password for user: ...


Is this ok (yes/no): yes


#see if installed

$ git --version

#see current configuration

$ git config -l



$ git config --global user.name "Mo So"



$ git config --global user.email "dkfjdfj@gmail.com"


#sudo for permission

$ sudo git config --system core.editor vim


#check if configured

$ git config -l

core.editor=vim

user.name=Mo So

user.email=dkfjdfj@gmail.com


#~ tilda is home directory in Linux;   (.) for hidden directory;we are looking at the content of /home/cloud_user@...71c/ gitconfig  file


$ cat ~/.gitconfig 

[user]

        name = Mo So
        
        email = dkfjdfj@gmail.com


$ cat /etc/gitconfig 

[core]

        editor = vim
        
# Working with Repositories in Git


