start in the directory  and check which folder you want to separate

> ls

go one level up and create a backup of the original

> cd ../ && mv \<name of repo\> \<name of repo\>.orig 

clone repo

> git clone \<name of original url\>

cd in to cloned repo

> git filter-branch --prune-empty --subdirectory-filter \<name of subdirectory\> -- main

remove origin

> git remote remove origin

create new github repo and push to it