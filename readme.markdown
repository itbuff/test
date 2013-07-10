#Git Essentials
==================
*README file for projects.*

![It Buff](http://www.itbuff.com.au/images/logo.png)

Settings 
========
Location of .gitconfig C:\Users\[UserName]

###Login Credentials

>_First set the option to Global level - ( Global means for the current user. All users would be system_)
  
__Type the following to set Name and Email__
	
    git config --global user.name "My Name"
	
    git config --global user.email "email@itbuff.com.au"
	
**To display output in colour type:**

    git config --global color.ui = true

>*note: To display a setting type the setting without a value*

    git config --global user.email

Projects
========
###Create new reposotory

>_First move to the Project folder and open command prompt_

**Type:**

    git init
	
>1. _Create a README file_
>2. _populate it with text_
>3. _Save it in the projects root folder_
>_This root folder should contain a folder called .git_

**To view project status type:**

    git status
	
>You'll notice readme.txt is a Untracked file

**Add a file to the unstage area**

    git add readme.txt
    git status

>You'll notice readme.txt is now flagged as a new file
>Moditify readme.txt
>Create another file todo.txt and type:

    git status
	
>Notice that readme.txt is now modified totodo is new.
>To add all files to the staging area use a dot .

    git add .

###Commit the files
**To commit type:**

    git commit

>In the editor all lines starting with # will be ignored
>On the first line just type a description for the commit.
>Example: Initial commit: created readme.txt and todo.txt files.
>*PRESS ESC* to make sure you're out of the editor mode

    :wq

>:wq this will write (save) then quit the editor

    git status

>should display: nothing to commit ...
>create another file called license.txt
>Moditfy todo add 2) ignoring files.
>Only commit files that have been previously commited.

    git commit -a

>only readme and todo should be commited, license should be ignored.

**A quick commit without using editor, pass the message string.**

    git commit -m "now license is commited"

Exclusions
==========
>There are files and folders that do not need tracking for exmaple.

>JQuery Librabries and framework libraries don't need to be tracked.

>Usually only code sections need tracking.

1. Create a folder called exclude

2. Create folder called include

3. Create a textfile called .gitignore

4. Add these lines to .gitignore file:

    1. exclude
    2. libs/*.*
    3. *.swp~
    4. *.tmp
    5. !libs/mycustomlib.php
	
>So all the ones above will be excluded from your project.
>!libs... line means NOT excluded
>where ! = NOT
###DIFF
// finding out the differences between changes
git diff readme.txt
// This will display (if any) changes before staging (compared to the index)
git diff --staged readme.txt
// find out the difference between stage and commited
git diff HEAD readme.txt
// find out the difference between working folder and commited, skips staging area
LOGS
// Show a log off all commits (commit comments will also be shown)
git log
// Show graph (don't get ecited its text base)
git log --graph
// Show one liner graph. Will display one line per commit.
git log --oneline --graph
// Make it pretty
//               hash name when
git log --pretty="%h, %cn, %cr"
****
// Graphical git UI displaying logs
gitk  
****
BRANCH
------
// the branch command allows you to branch off new revisions without affecting 
// the original or HEAD branch.

// List the branch
git branch
// create new branch
git branch newlibs
// Switch to the branch (note: you must switch to a branch before you can use it)
git checkout newlibs
git commit -am "new branch newlibs readme and todo moditfied"
Output:
[newlibs d0bc20e] new branch newlibs readme and todo moditfied
2 files changed, 32 insertions(+), 8 deletions(-)
// when you checkout bakc to master.. It will be an older verion in the working directory.
git checkout master
// to delete a branch
git branch --delete branchName
// CREATE AND CHECKOUT in one line
// notice the -b after chekcout (means create branch and then switch)
git checkout -b bug-fix-1
Output:
Switched to a new branch 'bug-fix-1'
// back to log... show commits on all branches (Decorate puts colour back into dos life)
git log --oneline --graph --all --decorate
// ** TIP
// IN DOS PROMPT you can create an alias or doskey macro which you cna re-use:...
> doskey gl=git log --oneline --all --graph --decorate
> gl
// Now the above gl will type the long line above :)
// To merge one branch into another:
git merge bug-fix-1
// now we can delete the bug-fix-1 branch
git branch -d bug-fix-1
// Using rebase to revert changes to the master branch from another branch
git rebase newlibs
GITHUB
------
// Create SSH key
-> Open git Bash
 > ssh-keygen -t rsa -C 'simon@itbuff.com.au'
> filename
> passphrase
-> You'll find the file in c:\users\simon\.ssh
-> use the .pub file for github
-> paste the contents into githug website shh keys
 > ssh -T git@github.com
 // Add your local "existing" repository to github online.
 > git remote add origin git@github.com:itbuff/test.git
 // Now push your local repository to github online
 > git push -u origin master
-> If you go to github.com you should now see your files.
// Now lets look at ALL /a branches
 > git branch -a
// Rename the readme file using git command 
 > git mv readme.txt readme.markdown
// Commit
 > git commit -m "changed reame.txt to readme.markdown"
Output:
[master d1576c6] changed reame.txt to readme.markdown
1 file changed, 0 insertions(+), 0 deletions(-)
rename readme.txt => readme.markdown (100%)
 > git push origin master
