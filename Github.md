# How to add user name and user email in github
   git config --global user.name "Your Name"
   git config --global user.email "Your Email"

# Three ways to add new line in markdown files:  
   a) Add two spaces at the end of first line, this will move to next line in same paragraph
   
   b) Add `<br>` tag as markdown files support html syntax<br>
   
   c) Press enter twice i.e. leave a line in between, this will move to next paragraph

# What all I can do when someone shares a git repo link with me ? : 
a) If he is the owner of the repo then he can add me as a collaborator. Then I will be able to see the repo in my github account and also able to clone it in my local repo and can push directly to main or to the branch on which I am working. But I will have to periodically do git pull in order to get the latest state of the repo. If we both try to push directly to main then it may create conflict as one would overwrite other's contribution. Here I will have to make pull request for the commits that I have done on my branch.  

b) If I can't be added as a collaborator then I will have to fork that repo so that a copy of that repo will be visible in my github account and then I can clone it and work upon it. Here I will have to make Pull request for the commits that I have done in my fork. Common in open-source contributions. Here I will have to sync my fork with the original repo periodically just as I need to do git pull in the above case. 

# What if I directly clone a repo available on github without doing fork ? :
In such a case I will get the local copy of remote repo in which I can make changes and also commit them but I will not be able to push them to the remote repo because I dont have access for that but I will be able to do git pull because only write permisson is denied and not read permission. In such case either I should fork the repo and then I will be able to push changes to the forked repo.

# How to clone a repo ?  
git clone https://github.com/friendusername/reponame.git -> (after this a remote repo named origin pointing to this URL is automatically created so anytime we want to push or pull we can just do, git push origin main or git pull origin main)

# How to change the origin remote of my local repo ?
git remote set-url origin https://github.com/yourusername/reponame.git -> (Here we used set-url instead of add because we are not adding a new remote URL but changing the URL for an existing remote which is named as origin)

# How to create a new branch and push changes to it ?
git checkout -b sam-feature  
git push origin sam-feature

# How to add a repo to do pull or push ?
git remote add upstream https://github.com/friendusername/reponame.git -> (Here upstream is the name given to this remote repo, we can have more than one remote repo for our local repo, one to pull from and one to push to. So after adding this repo we can pull changes so that our local forked repo remains synced with the remote repo.)  

git pull upstream main -> (git pull = git fetch + get merge)

# When I am trying to do git pull but there are divergent branches, then  
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


# Virtual environment is not pushed to github unless explicitly added

# To check the remote repo:  
   git remote -v

# To check the git config username and email  
   git config user.name  
   git config user.email

# To reset a particular commit but preserve the changes and then push this to github
   git reset --soft <commit_id of last commit before the commit we want to reset>
   git push --force

# To set tracking information for current branch of local repo
   git branch --set-upstream-to=origin/<branch> main

# How to add a local repo to github
   1) create a new repo on github
   2) initialise empty git repo in local repo
   3) run, "git remote add origin (HTTPS URL of remote repo on github)"
   4) now we can commit the changes and push them to github repo

# Check total repo size (including .git)
   du -sh .

# To initialize git in a local repo
   1) create a new repository in GitHub
   2) copy its URL
   3) initialize git in the local repo by running the command, `git init`

