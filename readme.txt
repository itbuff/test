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
		
			
		
	
		
	
	