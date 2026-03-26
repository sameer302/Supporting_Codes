# $ Important notes

## virtual environment is not pushed to github unless explicitly stated

## always do git pull if you are using a repo on different devices.

## Check total repo size (including .git) 
`du -sh`





# $ Made a local repo and now you want to push it on github

## how to initialize a git repo
   
   `git init`

## how to add user name and user email in github
   
   `git config --global user.name "Your Name"`  
   `git config --global user.email "Your Email"`

## how to check user name and user email in github
   
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
   3. origin is the name given to the remote reference branch and we can give any other name also
   4. this command just adds the given repo but does not yet push anything from our local repo to github repo

## add separate repo to push

   `git remote set-url --push origin <push_url>` --> (here it may seem that we are giving same name origin to this repo also and so this might create confusion when we are pushing any commits but that wont happen as git will save two urls for the name origin, one for fetching and one for pushing)

## change the repo to pull from 

   `git remote set-url origin <fetch_url>`

## check the remote repo

   `git remote -v` --> (this will tell us about separate github repo's to push to and pull from)

## set the local current branch name so that we can push this branch to the remote repo branch

   `git branch -M main` --> (by default this branch is named as Master and we need to write -M just to avoid some unnecessary errors)

## push local commits to github

   `git push -u origin main` --> (-u sets this branch push and pull names, origin and main, so next time we just need to do git push)

## when you want to revert all changes made till last commmit 

   `git reset --hard`

## how to remove a directory from git tracking ?

`git rm -r --cached hailo-apps`
`git commit -m "removed hailo-apps from direct tracking"`

# To reset a particular commit but preserve the changes and then push this to github

`git reset --soft <commit_id of last commit before the commit we want to reset>`
`git push --force`


   
# $ When you have a remote repo and you want to use it locally

## What all I can do when someone shares a git repo link with me ? 

a) If he is the owner of the repo then he can add me as a collaborator. Then I will be able to see the repo in my github account and also able to clone it in my local system and can push directly to main or to the branch on which I am working. But I will have to periodically do git pull in order to get the latest state of the repo. If we both try to push directly to main then it may create conflict as one would overwrite other's contribution. Here I will have to make pull request for the commits that I have done on my branch.  

b) If I can't be added as a collaborator then I will have to fork that repo so that a copy of that repo will be visible in my github account and then I can clone it and work upon it. Here I will have to make Pull request for the commits that I have done in my fork if I want them to be added in the repo from which I have forked. Common in open-source contributions. Here I will have to sync my fork with the original repo periodically just as I need to do git pull in the previous case. For this what I do is set the push url as my forked repo url and set the pull repo as the original repo url. So I will push to my forked repo and pull from the original repo by adjusting necessary conflicts. 

## What if I directly clone a repo available on github without doing fork ? :

In such a case I will get the local copy of remote repo in which I can make changes and also commit them but I will not be able to push them to the remote repo because I dont have access for that but I will be able to do git pull because only write permisson is denied and not read permission. In such case either I should fork the repo and then I will be able to push changes to the forked repo.

## How to clone a repo ?  

`git clone https://github.com/friendusername/reponame.git` -> (after this a remote repo named origin (or we can say branch named origin) pointing to this URL is automatically added so anytime we want to push or pull we can just do, git pull origin main and also git push origin main if we have write permission. I don't need to do git init in this local repo, that is already done in the root folder of the cloned repo. So if I change the directory and come inside the root folder of the cloned repo, now I can do git status and verify.)

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

## What happens if I clone a repo in another git repo on which I was working locally ?

In such case, I will be able to see two git tracks being maintained in the source control section. Name of each section will be the name of the root repo in which I have created the git repo or initialized the git repo, i.e. ran `git init`. For example it looks like below,

optimization_of_ai_models/          ← your main git repo
├── hailo-apps/                     ← another git repo cloned inside (nested)
│   └── .git/
├── system_metrics_logger.py
├── detection_simple.py
└── .git/

Now here I have following options to do :-

1) convert to git submodule
- to add this as a submodule we first go to our main root repo and then add this module as sub module by giving information about the repo which we want to add as remote for this repo, `git submodule add <hailo-apps-remote-url> hailo-apps`, then we can also add this change as a commit to our main module git history, `git commit -m "Added hailo-apps as submodule"` and then push this change `git push`
- we can verify if our submodule is added or not by seeing the output of command `cat .gitsubmodules`
- main repo stores pointer to a specific commit of hailo-apps, not the actual files
- if I make any changes in hailo-apps and want to push those changes, I first go to its root folder `cd hailo-apps`, then add, commit and push those changes to its own remote repo (maybe since its cloned so we will have separate repo to push to, maybe the forked repo and a separate repo to pull from, the original repo), then I come out from that repo to the root repo of my main module and again add, commit (with a simple msg like updated hailo-apps) and push this to the remote repo of our main module.
- if I make any changes outside hailo-apps in my main module root repo, in that case I just need to do this process once.
- if I want to pull changes in hailo-apps or update it to the latest then also I need to go to its root repo and then do `git pull` and then come back to our main module root repo and make a commit stating that the hailo-apps repo is updated
- in this case if I want to clone this repo on any new machine then I will have to do, `git clone --recursive-submodules <repo_name>`
- this is best if the cloned repo has its own remote and we want to track it separately.

optimization_of_ai_models/   ← your main repo

├── .git/

├── .gitmodules              ← new file, stores the link to hailo-apps remote repos

├── hailo-apps/              ← looks like a normal folder but is actually a pointer

│   └── (files from hailo-apps repo at a specific commit)

├── system_metrics_logger.py

└── detection_simple.py


2) remove nested .git, track everything in main repo
- first we just simply remove the git folder present in hailo-apps so no tracking is done, `rm -rf hailo-apps/.git` (r for recursive since its a directory and f for force to not get any confirmation msg)
- then we add this repo to our git logs for tracking, `git add hailo-apps/` and maybe commit this as, `git commit -m "Absorbed hailo-apps into main repo"`
- so in this we will have everything in one repo but we will loose hailo-apps original git history and also not able to pull upstream updates from hailo-apps easily.
- this is best if we are cloning any dependency which we modified heavily and dont care to update it later

3) Keep them fully separate
- we just add hailo-apps to .gitignore so our main module git does not track it, `echo "hailo-apps/" >> .gitignore`
- here we manage each repo independently with separate git push/pull and while cloning on a new machine both the repos will have to be cloned separately
- this is best if hailo-apps is a third party repo whcih we didnt modify and used just as it is. 
