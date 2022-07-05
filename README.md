# Git Commands Guide

## git init
###### Desc: Creating a git repository
## git status
###### Desc: Provide informations about current branch, file status ( tracked / untracked / modified )
## git config
###### Desc: configuration for git.
###### Usage Examples:
- git config user.email "you@example.com" // set your git email for current repo
- git config user.name "Your Name" // set your git username for current repo
- git config --global user.email "you@example.com" // set your git email globally
- git config --global user.name "Your Name" // set your git username globally
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
- git commit --author="username <email>" // commits changes with specified author described.
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
## git remote
###### Desc: Manage git address of your remote repository.
###### Usage Example:
- git remote show origin // shows detailed info about your currently remote origin status
- git remote prune origin --dry-run // shows which references of local machine branches are no longer exist in remote.
- git remote prune origin // clears references of local machine branches that are no longer exist in remote.
- git remote add origin https://github.com/userName/repoName.git // set origin to specified repository address on github.
- git remote remove origin // removes currently used origin address.
## git push
###### Desc: Pushing out commited changed from local repository to remote repository.
###### Usage Examples:
- git push // default push to remote repository. See notes for restrictions.
- git push origin HEAD // push selected branch to remote repository. Example: You are in branch test and you're pushing new/updating branch test in remote repository.
- git push origin HEAD:main // push your selected branch to specified branch. Example: You are in branch test and you're updating branch main in remote repository.
###### *Note that git push require same branchName as configured upstream branchName. For example if you are using branchTest then u need to configure upstream as follows: git branch -u origin/branchTest
## git pull
###### Desc: Fetch data from remote repository.
###### Usage Examples:
- git pull //pull remote repository data and merge all commits.
- git pull --rebase //pull remote repository data with commits history.
- git pull origin HEAD:main --rebase //pull selected remote repository branch to your current local branch with full commits history. Example: You are in branch test and pull data from remote branch main.
###### *Note that default pull command merge pulled data. If you are willing to keep history of commits use --rebase parameter.
## git clone
###### Desc: Clone remote repository.
###### Usage Example:
- git clone https://github.com/userName/repoName.git // clone repoName remote repository to your working directory locally.
## git reflog
###### Desc: Shows ordered list of all local commits from past 90 days.
## git reset
###### Desc: Used to remove files from staging area or undo commits.
###### Usage Example:
- git reset HEAD //remove all files from staging area.
- git reset HEAD path/to/file //remove selected file from staging area. Example: git reset Head test.txt will remove test.txt from staging area back to working directory.
- git reset --soft HEAD~1 //undo commit only and moves commited files to staging area once again.
- git reset HEAD~1 // undo last commit and pointing to previous HEAD ( changes are kept, commit deleted and commited files are moved back to working directory untracked area).
- git reset --hard HEAD~1 //undo last commit, delete commited data and pointing to previous HEAD ( both, commit and changes are deleted in this case ).
###### *Note that after deleting files with --hard parameter they're removed permamently. If you done this accidentally use git reflog to check your commits and restore it.
## git cherry-pick
###### Desc: Copy just a specified commit(s) to selected branch.
###### Usage Example:
- git cherry-pick commitHash // Copy commit with specified hash to selected branch. Example: You're in branch thisBranch and you're picking commit with specified hash from branch anotherBranch, only this commit will be copied to thisBranch.
- git cherry-pick commitId1 commitId2 //Same as above, with difference of copying 2 commits instead of 1 and by id not by hash.
## git rebase -i
###### Desc: interactive rebase.
###### Usage Example:
- git rebase -i commitHash // rebasing specific commit
- git rebase -i HEAD~1 // rebasing 1 commit ahead.
- git rebase --abort // exit interactive rebase without saving changes.
###### *Selected commit can be edited as description shows. For example if u want to modify author, do as following:
1. git rebase -i HEAD~1 // open interactive rebase for last commit
1. press INSERT and change "pick" to "edit" before commit you want to edit ( in our case there is only 1 commit )
1. press :wq to save
1. type git commit --amend --author="Author <author@mail.com>" // changes author for all files from specified commit.
1. type git rebase --continue // finish interactive rebasing.
