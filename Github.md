# 0) Three ways to add new line in markdown files:  
   a) Add two spaces at the end of first line, this will move to next line in same paragraph
   
   b) Add `<br>` tag as markdown files support html syntax<br>
   
   c) Press enter twice i.e. leave a line in between, this will move to next paragraph

# 2) When I am trying to do git pull but there are divergent branches, then  
   a) to merge/keep both the histories:  
   git pull --no-rebase
   
   b) to add local commits over remote:  
   git pull --rebase
   
   c) to move the pointer forward if there are no unique local commits:  
   git pull --ff-only
   
   d) to discard local commits and reset to remote:  
   git fetch origin  
   git reset --hard origin/main
   
   e) but before resetting if there are any uncommited changes we should save them by using:  
   git stash


# 3) Virtual environment is not pushed to github unless explicitly added

# 4) To check the remote repo:  
   git remote -v

# 5) To check the git config username and email  
   git config user.name  
   git config user.email

# 6) To reset a particular commit but preserve the changes and then push this to github
   git reset --soft <commit_id of last commit before the commit we want to reset>
   git push --force

# 7) To set tracking information for current branch of local repo
   git branch --set-upstream-to=origin/<branch> main
