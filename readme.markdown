# Git Essentials

README file for projects.

Location of .gitconfig
	C:\Users\[UserName]

Settings 
	Login Credentials
		// First set the option to Global level - Only for the current user.
		// All users would be system
		-> Type the follow to set Name and Email
			git config --global user.name "Simon Assouline"
			git config --global user.email "regos@itbuff.net"
		-> To display output in colour type:
			git config --global color.ui = true
		
		// note: To display a setting 
		-> type the setting without a value:
			git config --global user.email

Projects
	Create new reposotory
		-> First move to the Project folder and open command prompt and type:
			git init
	Create a README file 
		-> populate it with text
		-> Save it in the projects root folder 
		// This root folder should contain a folder called .git
		-> To view project status type:
			git status
		// you'll notice readme.txt is a Untracked file
	Add a file to the unstage area	
			git add readme.txt
			git status
		// you'll notice readme.txt is now flagged as a new file
		-> Moditify readme.txt
		-> Create another file todo.txt and type:
			git status
			// Notice that readme.txt is now modified totodo is new.
			// To add all files to the staging area use a dot .
			git add .
	Commit the files
		-> To commit type:
			git commit
			// In the editor all # will be ignored/
			// On the first line just type a description for the commit.
			// Example: Initial commit: created readme.txt and todo.txt files.
		-> press ESC to make sure you're out of the editor mode
			:wq
			// :wq this will write (save) then quit the editor
			git status
			// should display: nothing to commit ...
		-> create another file called license.txt
		-> Moditfy todo add 2) ignoring files.
		-> Only commit files that have been previously commited.
			git commit -a
			// only readme and todo should be commited, license should be ignored.
			// A quick commit without using editor, pass the message string.
			git commit -m "now license is commited"
	Exclusions
		// There are files and folders that do not need tracking for exmaple.
		// JQuery Librabries and framework libraries don't need to be tracked.
		// Usually only code sections need tracking.
		-> Create a folder called exclude
		-> Create folder called include
		-> Create a textfile called .gitignore
		-> Add these lines to .gitignore file:
			1] exclude
			2] libs/*.*
			3] *.swp~
			4] *.tmp
			5] !libs/mycustomlib.php
			// So all the ones above will be excluded from your project.
			// !libs... line means NOT excluded
			// where ! = NOT
	DIFF
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
	
		
	
	