# GIT COMMANDS HANDBOOK
## This Repository contains about git commands and the explanation for each command along with the different flags each command takes


## Initial Setup of Username and Email for the terminal
    > git config --global user.name "username"
    > git config --global user.email "emailId"
    > git config --global core.editor "code --wait"       waits for window
    > git config --global core.autocrlf input   // Use true on Windows
        > Read about this more

    To Check settings: git config --global -e
## To Setup shortcuts for git commands
    git config --global alias.<shortcut> <command>
    Example : alias.st status
## To Store the token auth key, use the git `credential helper`
    git config --global credential.helper store
## Terminology
1. Staging Area/Index
    - Temporary space b/w working directory and the project history
    - The file *to be committed* are put here.
    - This allows to group files going into **next commit(snapshot)**

## Git commands
### CLONE
- Creates a copy of the Remote *Existing* Repository
- usage: git clone `URL`
- A new folder with the same name as Repo is Created 

### ADD
- Moves files into staging Area
- This makes git to start tracking the file
- Use this command as soon as (part of) work on file is DONE
- Usage: git add *filename1*
- Flags available
    - **Tracks all files:** --all / -A:

### RESTORE
- to **UNSTAGE** files 
- git restore --staged **filename1** ... 
### PULL
- Update the local repo with the Remote Repository
- helps stay in the latest version of the Repo
### git commit
- Save a snapshot of the files **staged**
git diff
git status
git branch
git checkout
git stash
git fetch
git push
git merge
git rebase
git cherry-pick
git log
git reset
git tag

git config  
    The different flags are
        - --system : For all the users in the system
        - --global : For all the repositories of THAT user
        - --local  : For a single repository

## GIT WORKING
- Each commit create a **complete snapshot** of the project
    - Uses compression to save space
    - Doesn't allow duplicates
- Note that it doesnt store the **delta change**
- It also stores ID, Author, Date/time, Message

## Modifying a file that is already staged
- When a file is already added (v1), then modified(v2), Git shows it as untracked
- But the prev version added is still tracked
- now if we commit and push, v1 is pushed. v2 is still untracked!
- only in the next commit can we push v2