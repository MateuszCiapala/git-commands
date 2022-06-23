# Author: [Mateusz Ciapała](https://github.com/MateuszCiapala)

# Git Commands Guide

## git init
###### Desc: Creating a git repository
## git status
###### Desc: Provide informations about current branch, file status ( tracked / untracked / modified )
## git add
###### Desc: Moves specified "untracked" / "modified" file(s) in working directory to git staging area.
###### Usage Examples:
- git add fileName // adds specified file
- git add -A // adds all untracked & modified files
## git commit
###### Desc: Move files(s) from staging area to local repository ( Commits changes ).
###### Usage Examples:
- git commit -m"Comment here" // commits all files from staging area with specified comment.
- git commit -am"Comment here" // adding all modified files to staging area then commits all files from staging area with specified comment.
###### *Note that git commit -am moves only modified file to staging area, untracked files must be moved manually with git add.
## git log
###### Desc: Lists commits on current branch.
###### Informations provided for listed commits:
- hash
- branch
- Author
- Date
- Name
## git branch
###### Desc: Provide informations about current selected branch and list all available branches. Can be used to configure upstream (remote branch tracking).
###### Usage Examples:
- git branch --set-upstream-to origin/main //sets upstream for remote repository main branch.
- git branch -u origin/main // Does exact same thing as previous - shorter version usage.
## git checkout
###### Desc: Used to select specified branch or commit (current or from history) or create new branch.
###### Usage Example:
- git checkout -b branchName // creates branch with specified name.
- git checkout branchName // navigates (select) to specified branch by name.
- git checkout commitHash // navigates (select) to specified commit from history.
###### *Note that during new branch creation, branch template will be taken from currently selected branch (including upstream)
## git remote add
###### Desc: Set up git remote address for your remote repository.
###### Usage Example:
- git remote add origin https://github.com/userName/repoName.git // set origin to specified repository address on github.
## git push
###### Desc: Pushing out commited changed from local repository to remote repository.
###### Usage Examples:
- git push
