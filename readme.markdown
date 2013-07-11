#Git Essentials
==================
*README file for projects.*

[Live test for Markdown text](http://tmpvar.com/markdown.html)

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
>Only commit files that have been previously committed.  

    git commit -a

>only readme and todo should be commited, license should be ignored.

**A quick commit without using editor, pass the message string.**

    git commit -m "now license is committed"

Exclusions
==========
>There are files and folders that do not need tracking for example.  
>JQuery Librabries and framework libraries don't need to be tracked.  
>Usually only code sections need tracking.  

1. Create a folder called exclude  
2. Create folder called include  
3. Create a text file called .gitignore  
4. Add these lines to .gitignore file:

> 

    exclude  
    libs/*.*  
    *.swp~  
    *.tmp  
    !libs/mycustomlib.php  
	
>So all the ones above will be excluded from your project.
>!libs... line means NOT excluded
>where ! = NOT

DIFF
===

>Finding out the differences between changes

    git diff readme.txt

>This will display (if any) changes before staging (compared to the index)

    git diff --staged readme.txt

>Find out the difference between stage and committed

    git diff HEAD readme.txt

>find out the difference between working folder and committed, skips staging area

LOGS
====
>Show a log off all commits (commit comments will also be shown)

    git log

**Show graph (don't get ecited its text base)**

    git log --graph

**Show one liner graph. Will display one line per commit.**

    git log --oneline --graph

>Make it pretty  
>               hash name when

    git log --pretty="%h, %cn, %cr"

**Graphical git UI displaying logs**

    gitk  


BRANCH
=======
>The branch command allows you to branch off new revisions without affecting  the original or HEAD branch.
**List the branch**

    git branch

**create new branch**

    git branch newlibs

>Switch to the branch (note: you must switch to a branch before you can use it)

    git checkout newlibs
    git commit -am "new branch newlibs readme and todo moditfied"

Output:
>[newlibs d0bc20e] new branch newlibs readme and todo moditfied  
>2 files changed, 32 insertions(+), 8 deletions(-)

>when you checkout back to master.. It will be an older version in the working directory.

    git checkout master

**To delete a branch**

    git branch --delete branchName

>CREATE AND CHECKOUT in one line  
>notice the -b after checkout (means create branch and then switch)

    git checkout -b bug-fix-1

>Output:  
>Switched to a new branch 'bug-fix-1'  

**back to log... show commits on all branches (Decorate puts colour back into dos life)**

    git log --oneline --graph --all --decorate

>*TIP*  
>IN DOS PROMPT you can create an alias or doskey macro which you can re-use:...
> check this link about DOSKEY. [Saving permanently](http://darkforge.blogspot.com.au/2010/08/permanent-windows-command-line-aliases.html).

    doskey gl=git log --oneline --all --graph --decorate  
    gl
>Now the above gl will type the long line above :)
*To merge one branch into another:*

    git merge bug-fix-1

>now we can delete the bug-fix-1 branch

    git branch -d bug-fix-1

__Using rebase to revert changes to the master branch from another branch__

    git rebase newlibs

GITHUB
======
* Create SSH key  
* Open git Bash

> 

    ssh-keygen -t rsa -C 'simon@itbuff.com.au'  
    [ filename ]  
    [ passphrase ]  


* You'll find the file in c:\users\simon\.ssh
* Use the .pub file for github
* paste the contents into githug website shh keys

> 

    ssh -T git@github.com

>Add your local "existing" repository to github online.

    git remote add origin git@github.com:itbuff/test.git
>Now push your local repository to github online

    git push -u origin master

>If you go to github.com you should now see your files.  
>Now lets look at ALL /a branches

    git branch -a

>Rename the readme file using git command

    git mv readme.txt readme.markdown

*Commit*

    git commit -m "changed reame.txt to readme.markdown"

>Output:  
>[master d1576c6] changed reame.txt to readme.markdown  
>1 file changed, 0 insertions(+), 0 deletions(-)  
>rename readme.txt => readme.markdown (100%)  

    git push origin master

###Pull Requests
> When someone uses fork on your project they can modify the code and send you a pull request.  
> If the changes are acceptable you can merge the request into your project.  

> However you will need to update your project on your local computer once you've merged the request.  

__*To do so simply type*__

    git pull

> This will update your local project with the remote changes made by the request forked.

###Cloning
>You can clone another project by obtaining its link available on the github.com project.  
>> *For example cloning Zend Framework 2.*

    git clone https://github.com/zendframework/zf2.git

>> *Use the fetch command to pull the changes down.

    git fetch

>>You can merge origin and master when changes have been made and pulled using:  

    git merge origin/master

Making your own webpage on github
==========================
1. Create a new folder and initialise a new repository on github.com by its webname.  
example: itbuff.github.com

> 

    md itbuff.github.com  
    cd itbuff.github.com 
    git init
    git add .
    git status
    git commit -m "first commit"
    git remote add origin git@github.com:itbuff/itbuff.github.com.git
    git push -u origin master

>Now when you go to itbuff.github.com you have your personal github webpage

>To create a page for a project use:

    git checkout --orphan gh-pages

>Watch video 17 for more details.

git Commands
==========
>Interactive add

    git add -i  

>To split or patch a file before a commit use:

    git add -p

git stash
======
>The git stash allows you to stash content that you don't want to commit until you're ready.  
>Unstaged files currently in the queue will now be staged (ignored in future commits)

    git stash

>You can now make changes to other files and commit them without affecting files before the stash command.  

*__Find out what has been stashed:__*

    git stash list

*__remove content from stage__*

    git stash apply stash@{1}

>stash@{1} would have been shown in the list when using _git  stash list_  
>**NOTE** when using apply the content of stash will still be in stashing and working area.  
>**USE** pop to move the stash back into working folder.

    git stash pop stash@{1}

*__to remove or drop a stash applied use:__*  

    git stash drop


Alias - shorten git commands
=====================
>shorten the status command

    git config --global alias.s status  
    git config --global alias.a add
    git config --global alias.aa "add ."

>You can also create aliases in git bash command prompt

    alias gs='git status'  
    alias gc='git commit'

>Use doskey for dos prompt

    doskey ls=dir

> OR from a file

    doskey /macrofile=doskey.txt

Is there a way to skip password typing when using https:// github
=================================================================
>Read this article

[Cache Password](http://www.stackoverflow.com/questions/5343068/is-there-a-way-to-skip-password-typing-when-using-https-github)  
[git-credentials](http://gitcredentialstore.codeplex.com/releases/view/103679)  



	
