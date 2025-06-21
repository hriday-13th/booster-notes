## Initialize a git folder
`git init`

## To clone a remote repository
`git clone <git url>`

## To check the staged and unstaged changes
`git status`

## Save / stage changes
All the changes in question -> `git add .`
Specific changes in question -> `git add <file_name1_> <file_name_2>`

## Commits those changes to memory
`git commit -m "<git commit note>"`

## Sync your local git with the remote
`git pull origin branch-name`

## To check the logs
`git log`

## To open an existing commit
`git checkout <commit code>` 
check git log for the code thingy

## To see the branches
`git branch`

## To add your local git folder to github
`git remote add origin <local-git-path>

## To push the branch for the first time
`git push -u origin main` 
here the name of the connection between the local and remote repo is called 'origin' and '-u' is basically --set-upstream

-- Branches --
## Create a new git branch
`git checkout -b branch-name`

## Push a branch to github
`git push origin branch-name`

-- Delete options --
## delete a branch
`git branch -d branch-name`

## force delete a branch
`git branch -D branch-name`

-- Merging --
## Merge branch-X into your current branch
`git merge branch-X`

-- Rebasing --
Kind of superimposes the commits on feature branch on top of your master branch

## Rebase your branch
```
git checkout main
git pull
git checkout feature-branch
git rebase main
git checkout main
git rebase feature-branch
```