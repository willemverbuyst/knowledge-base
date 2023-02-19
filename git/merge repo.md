> git clone repo

show remote

> git remote -v

show branches

> git branch -a -vv

add remote from the repo you want to merge into this one

> git remote add \<name of repo to merge\> \<git@github.com:...\>

> git fetch \<name of repo to merge\>

now you should have two remotes

> git remote -v

- origin
- name of repo to merge

checkout to new branch to create a subfolder

> git checkout -b \<name of repo to merge\> \<name of repo to merge\>/main

> mkdir \<name of folder for main repo\>

> git mv -k * ./\<name of folder for main repo\>

CD into folder and remove .gitignore

Copy over .files

Back to root and list out files

> ls

you should have one folder with the name of the folder for the main repo

> status

you should see all the files ready to be commited

> git commit -m "Move files to subfolder"

Checkout to main/master branch

> git checkout main

> git merge \<branch name\> --allow-unrelated-histories

Both repos are in the same place, you should see the subfolder in the root

> git push

Clean up

> git remote rm \<name of repo\>

> git branch -d \<name of branch\>

Confirm banch and remote

> git branch -a -v

Delete repo on github



