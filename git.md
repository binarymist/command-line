## Contents

* [Assumptions, Prerequisites](#assumptions-prerequisites)
* [Working with Remotes using SSH](#working-with-remotes-using-ssh)
* [Most Commonly Used](#most-commonly-used)
* [Github](#github)
  * [Compare View](#compare-view)
* [Fetching and Merging](fetching-and-merging)
* [Pushing](#pushing)
* [Less Used Commands](#less-used-commands)

## Assumptions, Prerequisites

Your git configs are [set-up](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup):

* `~/.gitconfig`

Install the cross platform diff tool "diffuse". It's free and open:

* Linux (Debian based): `apt-get install diffuse`
* Windows: http://diffuse.sourceforge.net/

On Linux use zsh, oh-my-zsh, and the oh-my-zsh git plugin

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
Or just `diffuse -m`

[`git add`](https://git-scm.com/docs/git-add)  
`git add -A`

If you want to revert all changes in your working directory to the last commit:  
`git reset --hard`

`git checkout -- name/of/file/to/unstage.txt`

`git commit -v` Will run the text editor you set-up in your config  
or  
`git commit -m '<my commit message>'`

[`git show`](https://git-scm.com/docs/git-show)`--name-only {commit}`. Replace the `{commit}` with the SHA1 you want to retrieve, or things like `HEAD` or `HEAD^^`  
As a shortcut, Git uses the `^` notation to mean "one commit prior.", so `HEAD^^` means 2 commits prior to `HEAD`

Show Remotes  
`git remote -v`

## Github

### Compare View

To get to the compare view, just append `/compare` to your github repository  
https://github.com/binarymist/command-line/compare

## Fetching and Merging

`fetch` gives you a chance to examine the changes you just fetched.

[`git fetch origin`](https://git-scm.com/docs/git-fetch#_examples)  
fetches all branches from origin and stores them as remote branches locally.

`git fetch --all`  
fetches all branches from all remotes and stores them as remote branches locally.

`git fetch origin develop`  
fetches the `develop` branch from origin and stores it as a remote branch locally: `remotes/origin/develop`


Merge: Todo







## Pushing

[`git push`](https://git-scm.com/docs/git-push)`origin master`  
Pushes your local `master` branch to the origin's `master` branch.

Push with dry run  
`git push --dry-run --porcelain`

Push a new branch to origin and add upstream tracking  
`git push -u origin <myNewBranchThatOriginDoesn'tKnowAbout>`

Push tags and branches  
`git push --all origin`


## Less Used Commands

Show all files in the index  
[`git ls-files`](https://git-scm.com/docs/git-ls-files)






