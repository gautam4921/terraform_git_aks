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

How to delete a file in git which is commited 

A new file Creds.txt is used to store credentials 
username : gautam
Password : pass@123

gautam@YG1010056LT:/mnt/d/terraform_nginx-app$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        creds.txt
        readme.md

nothing added to commit but untracked files present (use "git add" to track)