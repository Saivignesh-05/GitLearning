# GIT COMMANDS HANDBOOK
## This Repository contains about git commands and the explanation for each command along with the different flags each command takes


## Initial Setup of Username and Email for the terminal
    > git config --global user.name "user name"
    > git config --global user.email "emailId"
    > git config --global core.editor "code --wait"       waits for window
            
                *** By defualt it uses vim ***

    -Apply the shell command in vscode. This allows Git to know who is code 
            
            *** search ">code" -> Install 'code' command in path ***

    > git config --global init.defaultBranch 'master' (can also be main)

    > git config --global core.autocrlf input   // Use true on Windows

    To Check settings: 
        1. git config --global -e 
        2. In root: .gitconfig File
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
    - **git ls-files**: Shows the files in Staging Area

## Git commands
### git config  
- Used for setting Options
- FLAGS
    - --system : For all the users in the system
    - --global : For all the repositories of THAT user
    - --local  : For a single repository


### CLONE
- Creates a copy of the Remote *Existing* Repository
- usage: git clone `URL`
- A new folder with the same name as Repo is Created 

### ADD
- Moves files into staging Area
- This makes git to start tracking the file
- Use this command as soon as (part of) work on file is DONE
- Usage: git add *filename1*
- To untrack: git rm --cached *filename1*
- FLAGS
    - **Tracks all files:** --all / -A:

### RESTORE
- to **UNSTAGE** files 
- git restore --staged **filename1** ... 

### PULL
- Update the local repo with the Remote Repository
- helps stay in the latest version of the Repo
### COMMIT
- Save a snapshot of the files **staged**
- Opens the COMMIT_EDITMSG file in the **.git Folder** in the preferred Editor
- FLAGS
    - -m: **Commit message directly as cmd argument**
    - -am: **Add all files and commit them**
### STATUS
- Shows the full status of the local directory (working tree information)
- FLAGS
    - -s: **short style status info**
### DIFF
- Shows difference b/w files **Unstaged** and **Last Commit**
- FLAGS
    - --staged/cached: Shows difference b/w files **Staged** and **Last Commit**
    - git diff `branch1..branch2` OR git diff branch1 branch2 (Both produce same results)
    - git diff `commit_id-1..commit_id-2` OR git diff commit_id-1 commit_id-2
### PUSH
- Push the commited code to the remote Repo
- Requests for Username and PAT (Personal Authentication Token)

### LOG
- Shows the previous commited versions of the Repository
- Includes Author,Date, Commit-id
- FLAGS
    - --oneline : Shows a simplified version

## git branch
- Shows where the **HEAD** is pointing
- This HEAD can be seen inside .git folder

    ### git branch `branch-name`
    - Creates a new timeline from the current Branch

    ### git branch `-d` branch-name 
    - Deletes the specified Branch

## git checkout `branch-name`
- Moves the HEAD to branch-name mentioned
- Alias to checkout is `switch`
- FLAGS
    - git switch -c new-branch : **Creates the branch and Switches**
    - git checkout -b new-branch : Same as above
- ** commit before switching a branch

## git merge
- Three types of Merge exists
    1. Fast forward merge
        - This is where the master does no commit
        - The branch has CHANGES
        - Since the Master Didnt move at all, We fast forward Master to the new HEAD
    2. Not a fast forward
        - The master and branch have done some commits of their own
        - But the commits dont conflict (Not of SAME FILE)
    3. Conflict Merge
git stash
git fetch
git rebase
git cherry-pick
git reset
git tag


## GIT WORKING
- Each commit create a **complete snapshot** of the project
    - Uses compression to save space
    - Doesn't allow duplicates
- Note that it doesnt store the **delta change**
- It also stores ID, Author, Date/time, Message

# Case Study
## Modifying a file that is already staged
- When a file is already added (v1), then modified(v2), Git shows it as untracked
- But the prev version added is still tracked
- now if we commit and push, v1 is pushed. v2 is still untracked!
- only in the next commit can we push v2

## Deleting a File
- When doing **rm filename**, This change is not staged
- Thus we need to ADD the file, and commit
- If we want to remove File from **working dir** AND **staging area**
    > **git** rm filenames

## Moving a File
- Like removing a file, use the command
    > **git** mv filenames
- Does the staging of new file and deleting of old file

## Ignoring certain files
- Create a file named **.gitignore**
- File: test.txt
- Directory: dir1/      **remember to use fwd-slash
- Look for gitignore generator. Has templates for different programming languages

## Commit - Behind the scenes
![alt text](image.png)
- First Parent points to NULL
- The Child version's Hash is generated using the Parent's information
