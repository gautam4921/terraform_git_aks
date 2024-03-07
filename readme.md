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
