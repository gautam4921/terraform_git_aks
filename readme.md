gautam@YG1010056LT:/mnt/d/az_aks_terraform_nginx-app$ git config --global --list
user.name=gautam_terraform
user.email=gautam.prasad@gamil.com
gautam@YG1010056LT:/mnt/d/az_aks_terraform_nginx-app$ 

When you are doing git status on your local computer it says it is on Branch master 
we donot want master as a name ....we have to change 

below is live example 
gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git status
fatal: not a git repository (or any parent up to mount point /mnt)        
Stopping at filesystem boundary (GIT_DISCOVERY_ACROSS_FILESYSTEM not set).
gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git init
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all   
hint: of your new repositories, which will suppress this warning, call:
hint: 
hint:   git config --global init.defaultBranch <name>
hint: 
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint: 
hint:   git branch -m <name>
Initialized empty Git repository in /mnt/d/terraform_nginx-app/.git/
gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git status
On branch master

No commits yet

nothing to commit (create/copy files and use "git add" to track)
gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ 

go to local folder were you have initilized git.
my location for folder is D:\terraform_nginx-app were i see a .git folder 

Delete this .git folder 

Once again go to VS code and type command git status ...which will retur with an error 

gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git status
fatal: not a git repository (or any parent up to mount point /mnt)
Stopping at filesystem boundary (GIT_DISCOVERY_ACROSS_FILESYSTEM not set).

to set the branch name to main put below command 
gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git init -b main
Initialized empty Git repository in /mnt/d/terraform_nginx-app/.git/

**gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git status   : The branch name is been changed 
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)

**Adding a single file to tracking area
gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git status
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        main.tf
        output.tf
        providers.tf
        terraform.tfvars
        varibles.tf

nothing added to commit but untracked files present (use "git add" to track)

**Adding multiple files in one shot 

gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git add .
gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   main.tf
        new file:   output.tf
        new file:   providers.tf
        new file:   terraform.tfvars
        new file:   varibles.tf

**How to delete a file in git which is commited 

A new file Creds.txt is used to store credentials 
username : gautam
Password : pass@123

gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git add .
gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git commit -m "adding readme.md & creds file to local"
[main 7883ec1] adding readme.md & creds file to local
 2 files changed, 103 insertions(+)
 create mode 100644 creds.txt
 create mode 100644 readme.md

gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git status
On branch main
nothing to commit, working tree clean

**The file is commited ...first we need to remove the file from commit 

**gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git rm --cached creds.txt
rm 'creds.txt'
gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git status 
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    creds.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   readme.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        creds.txt

this will bring the file to untracked area ...

Now you can right click on the file in VS code and delete it.


By using the command git status you can check the status of file 

gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git status
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        **deleted:    creds.txt

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   readme.md


why i did git add. .......coz i am adding notes to readme.md

gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git add .
gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git commit -m "removed the creds file and added notes to readme.md"
[main 8ea7146] removed the creds file and added notes to readme.md
 1 file changed, 42 insertions(+), 3 deletions(-)

gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git status
On branch main
nothing to commit, working tree clean

***Remote Repository (Github)***
when you want to push your files to github repo ......below steps needs to be followed .....with errors 

1 you need to create a github repo to (were you want to push your local files)

2 In my case the repo name is gautam4921/terraform_git_aks

3 Create a Personnel access token 

4 Reference Url : https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens

5 When your PAT is ready copy it and keep it in a safe place 

6 Copy the URL of Github repo and paste it in the below command

7 I am using Https 

8 https://github.com/gautam4921/terraform_git_aks.git

9.git remote add origin https://github.com/gautam4921/terraform_git_aks.git

** I was getting error when i pushing the code to remote 
gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git push origin main
Username for 'https://github.com': gautam4921@gmail.com
Password for 'https://gautam4921@gmail.com@github.com':
To https://github.com/gautam4921/terraform_git_aks.git
 ! [rejected]        main -> main (non-fast-forward)
error: failed to push some refs to 'https://github.com/gautam4921/terraform_git_aks.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. If you want to integrate the remote changes,
hint: use 'git pull' before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.

Solution Found on web :
use below command :- 
gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git fetch
##**gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git push -f -u origin main
Username for 'https://github.com': gautam4921@gmail.com
Password for 'https://gautam4921@gmail.com@github.com':
Enumerating objects: 19, done.
Counting objects: 100% (19/19), done.
Delta compression using up to 8 threads
Compressing objects: 100% (19/19), done.
Writing objects: 100% (19/19), 4.11 KiB | 48.00 KiB/s, done.
Total 19 (delta 6), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (6/6), done.
To https://github.com/gautam4921/terraform_git_aks.git
 + eeb37b5...bce147f main -> main (forced update)
branch 'main' set up to track 'origin/main'.

*check in github repo for codes 

