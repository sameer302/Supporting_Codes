# Important notes

## virtual environment is not pushed to github unless explicitly stated

## always do git pull if you are using a repo on different devices.

# Made a local repo and now you want to push it on github

## how to initialize a git repo
   
   `git init`

## how to add user name and user email in github
   
   `git config --global user.name "Your Name"`
   `git config --global user.email "Your Email"`

## how to add user name and user email in github
   
   `git config user.name`
   `git config user.email`

## check repository status (which files are untracked, modified or staged)

   `git status`

## add files to the staging area (so that we can make logically grouped commits at the end rather than commitiing after every one logical set of changes)

   `git add . --> (to add all the unstaged files)`
   `git add filename.py --> (to add a specific file)`

## commit the staged changes 

   `git commit -m "commit message"`

## Make a remote github repo on github website and copy its url

## adding a remote repo for the first time
   
   `git remote add origin <github_repo_url>`

   1. this command will add the given repo for both fetch and push
   2. for the first time we can't separately add repo for fetch and push
   3. origin is the name given to the remote reference and we can give any other name also
   4. this command just adds the given repo but does not yet push anything from our local repo to github repo

## add separate repo to push

   `git remote set-url --push origin <push_url>` --> (here it may seem that we are giving same name origin to this repo also and so this might create confusion when we are pushing any commits but that wont happen as git will save two urls for the name origin, one for fetching and one for pushing)

## change the repo to pull from 

   `git remote set-url origin <fetch_url>`

## check the remote repo

   `git remote -v` --> (this will tell us about separate github repo's to push to and pull from)

## set the local current branch name so that we can push this branch to the remote repo branch

   `git branch -M main` --> (by default this branch is named as Master and we need to -M just to avoid some unnecessary errors)

## push local commits to github

   `git push -u origin main` --> (-u sets this branch push and pull names, origin and main, so next time we just need to do git push)

## when you want to revert all changes made till last commmit 

   `git reset --hard`
   
# When you have a remote repo and you want to use it locally

## What all I can do when someone shares a git repo link with me ? 

a) If he is the owner of the repo then he can add me as a collaborator. Then I will be able to see the repo in my github account and also able to clone it in my local system and can push directly to main or to the branch on which I am working. But I will have to periodically do git pull in order to get the latest state of the repo. If we both try to push directly to main then it may create conflict as one would overwrite other's contribution. Here I will have to make pull request for the commits that I have done on my branch.  

b) If I can't be added as a collaborator then I will have to fork that repo so that a copy of that repo will be visible in my github account and then I can clone it and work upon it. Here I will have to make Pull request for the commits that I have done in my fork if I want them to be added in the repo from which I have forked. Common in open-source contributions. Here I will have to sync my fork with the original repo periodically just as I need to do git pull in the previous case. 

## What if I directly clone a repo available on github without doing fork ? :

In such a case I will get the local copy of remote repo in which I can make changes and also commit them but I will not be able to push them to the remote repo because I dont have access for that but I will be able to do git pull because only write permisson is denied and not read permission. In such case either I should fork the repo and then I will be able to push changes to the forked repo.

## How to clone a repo ?  

`git clone https://github.com/friendusername/reponame.git` -> (after this a remote repo named origin pointing to this URL is automatically added so anytime we want to push or pull we can just do, git pull origin main and also git push origin main if we have write permission)

## When I am trying to do git pull but there are divergent branches, then  

   a) to merge/keep both the histories:  
   `git pull --no-rebase`
   
   b) to add local commits over remote:  
   `git pull --rebase`
   
   c) to move the pointer forward if there are no unique local commits:  
   `git pull --ff-only`
   
   d) to discard local commits and reset to remote:  
   `git fetch origin`  
   `git reset --hard origin/main`
   
   e) but before resetting if there are any uncommited changes we should save them by using:  
   `git stash`






# How to create a new branch and push changes to it ?
`git checkout -b sam-feature`  
`git push origin sam-feature`

# Virtual environment is not pushed to github unless explicitly added

# To reset a particular commit but preserve the changes and then push this to github
   `git reset --soft <commit_id of last commit before the commit we want to reset>`
   `git push --force`

# To set tracking information for current branch of local repo
   `git branch --set-upstream-to=origin/<branch> main`

# Check total repo size (including .git)
   `du -sh`

