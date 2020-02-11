## Contents

* [Working with Remotes using SSH](#working-with-remotes-using-ssh)
* [Most Commonly Used](#most-commonly-used)
* [Fetching and Merging](fetching-and-merging)
* [Pushing](#pushing)

## Working with Remotes using SSH

Getting you ssh key to stay in the SSH agent, in git bash:

1. Make sure ssh-agent is running:  
  `eval $(ssh-agent)`
2. Add the private key to the `ssh-agent` for the shell you are using with:  
  `ssh-add`

## Most Commonly Used

`git status`

`git diff`

`git diff HEAD -- file/from/working/dir/to/compare/with/tip/of/current/branch`

`git diff --cached` or `--staged`  
Or just `diffuse -m` Providing diffuse is installed

[`git add`](https://git-scm.com/docs/git-add)  
`git add -A`

If you want to revert all changes in your working directory to the last commit:  
`git reset --hard`

`git checkout -- name/of/file/to/unstage.txt`

`git commit -v`  
or  
`git commit -m '<my commit message>'`

[`git show`](https://git-scm.com/docs/git-show)`--name-only {commit}`. Replace the `{commit}` with the SHA1 you want to retrieve, or things like `HEAD` or `HEAD^^`

Show Remotes  
`git remote -v`

## Fetching and Merging

`fetch` gives you a chance to examine the changes you just fetched.

[`git fetch origin`](https://git-scm.com/docs/git-fetch#_examples)  
fetches all branches from origin and stores them as remote branches locally.

`git fetch --all`  
fetches all branches from all remotes and stores them as remote branches locally.

`git fetch origin develop`  
fetches the `develop` branch from origin and stores it as a remote branch locally: `remotes/origin/develop`


## Pushing

[`git push`](https://git-scm.com/docs/git-push)`origin master`  


