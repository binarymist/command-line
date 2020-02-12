## Contents

* [Assumptions, Prerequisites](#assumptions-prerequisites)
* [Working with Remotes using SSH](#working-with-remotes-using-ssh)
* [Most Commonly Used](#most-commonly-used)
* [Github](#github)
  * [Compare View](#compare-view)
* [Fetching and Merging](fetching-and-merging)
  * [Merge Conflicts](#merge-conflicts)
* [Pushing](#pushing)
* [git log](#git-log)
* [Branch Management](#branch-management)
  * [Deleting Branches](#deleting-branches)
* [Diffing](#diffing)
* [Patching](#patching)
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

Show Remotes:  
`git remote -v`

## Github

### Compare View

To get to the [compare view](https://help.github.com/en/github/committing-changes-to-your-project/comparing-commits), just append `/compare` to your github repository:  
https://github.com/binarymist/command-line/compare  
This allows you to compare just about anythng.

## Fetching and Merging

`fetch` gives you a chance to examine the changes you just fetched.

[`git fetch origin`](https://git-scm.com/docs/git-fetch#_examples)  
fetches all branches from origin and stores them as remote branches locally.

`git fetch --all`  
fetches all branches from all remotes and stores them as remote branches locally.  
`git fetch origin develop`  
fetches the `develop` branch from origin and stores it as a remote branch locally: `remotes/origin/develop`

Essentially there are two types of branches, local and remote-tracking (see the "Types of Branches" section [here](https://longair.net/blog/2009/04/16/git-fetch-and-merge/)).

_So what you mostly do with remote-tracking branches is one of the following:_

* _Create new local branches based on them_
* _Update them with `git fetch`_
* _Merge from them into your current branch_

1. Create new local branches based on them:  
  _To create a local branch based on a remote-tracking branch (I.E. in order to actually work on it) you can do so with one of the following two commands:_  
   * `git branch –-track <new_branch_name> [<start_point>]`  
     This creates a new branch head named <`new_branch_name`> which points to the current `HEAD`, or <`start_point`> if given.  
   * `git checkout --track -b refactored origin/refactored`  
   
   The `--track` option is implied in recent versions of git if the last parameter is a remote-tracking branch
2. Update them with `git fetch`:  
  `git fetch origin`  
  This will update your remote-tracking branches. `git fetch` doesn’t touch your working tree at all. To get any remote changes from your updated remote-tracking branches, you now need to do a `git merge`. So if for example you are on the `master` branch, you would do the following:  
  `git merge origin/master`.  
  If you would rather see the differences in the two branches before you merge:  
  `git diff master origin/master`  
  Or  
  `git difftool -t diffuse master origin/master`



&nbsp;&nbsp;

Merge into `master` from your feature branch (`amazing_feature`):

1. `git checkout master`
2. `git merge <amazing_feature>`

### Merge Conflicts

[git-scm Basic Merge Conflicts](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging#_basic_merge_conflicts)

Once conflicts are shown: `git mergetool` will allow you to merge with your configured merge tool. Failing that, just do it manually. Then add the changed file to staging, then `git status` again.



Todo



## Pushing

[`git push`](https://git-scm.com/docs/git-push)`origin master`  
Pushes your local `master` branch to the origin's `master` branch.

Push with dry run:  
`git push --dry-run --porcelain`

Push a new branch to origin and add upstream tracking:  
`git push -u origin <myNewBranchThatOriginDoesn'tKnowAbout>`

Push tags and branches:  
`git push --all origin`

## `git log`

Show unpushed git commits:  
[`git log origin/master..HEAD`](https://stackoverflow.com/questions/2016901/viewing-unpushed-git-commits#answer-2016954)  
Or to show the actual changes:  
`git diff origin/master..HEAD`

Show commits which are pointed to by tags or branches:  
`git log --graph --all --decorate`

`--abbrev-commit` shows a shortend commit hash:  
`git log --abbrev-commit --graph --oneline --all`

`--decorate` shows the branch names:  
`git log --abbrev-commit --graph --oneline --all --decorate`

Show only the `kimsBranch` and all branches leading into it:  
`git log --abbrev-commit --graph --oneline --decorate --branches=kimsBranch`

Single file:  
`git log -- file/I/want/to/see/all/commits/for`

Commits for an author, just add `--author=Kim`

## Branch Management

Show status of local and remote branches:  
`git remote show origin`

Show local branches only:  
`git branch`

Show remote branches  
`git branch -r`

Show both remote and local branches:  
`git branch -av`

Merge [only specific files](http://jasonrudolph.com/blog/2009/02/25/git-tip-how-to-merge-specific-files-from-another-branch/) from a specific branch to the current branch:  
`git checkout [other_branch] <file_paths>...`

Merge [only specific changes from specific files](https://stackoverflow.com/questions/18115411/how-to-merge-specific-files-from-git-branches) from a specific branch to the current branch:  
`git checkout --patch [other_branch] <file_paths>...`

Create new branch from master and switch to it:  
`git checkout -b <myFeature> master`  
Which is short for:  
`git branch <myFeature>`  
`git checkout [myFeature]`

If you are already on a branch (say `feature1`) and I have made some changes on it but want those changes to be on a newBranch:  
`git checkout -b <newBranch>`

Same as above, but `newBranch` already exists:  
`git checkout [newBranch]`

### Deleting Branches

Delete local branch:  
`git branch -d <nameOfMyLocalBranch>`

[Delete local remote-tracking branch and origins remote](https://stackoverflow.com/questions/2003505/how-do-i-delete-a-git-branch-both-locally-and-remotely):  
`git push <remote_name> --delete <branch_name>`  
Ex: `git push origin --delete newFeature`  
`origin` is the remote defined in your repositories `./.git/config` file, or another way to find the remote is with `git branch -va`, the remote is usually `origin`.  

If remote branches have already been removed:  
`git remote prune <remote>`  
Or  
[`git fetch -p`](https://makandracards.com/makandra/621-git-delete-a-branch-local-or-remote)  
Or  
`git remote prune origin`

## Diffing

View history of single file. Often you will have to go into the directory of the file before running the following commands:  
`git log`  
Then use the commit hashes as diffuse arguments:  
[`diffuse -r <commit_hash> <name_of_file>`](http://diffuse.sourceforge.net/manual.html#file-comparison)  
Or two (or any number of) revisions of the same file:  
`diffuse -r <commit_hash_1> -r <commit_hash_2> <name_of_file>`

Diff single file from `HEAD` of current branch to working directory:  
`git diff HEAD -- path/of/file/I/want/to/diff`

[Compare two different files in two different revisions](http://stackoverflow.com/questions/3338126/git-how-to-diff-the-same-file-between-two-different-commits-on-the-same-branch):  
`git diff <revision_1>:<file_1> <revision_2>:<file_2>`

[Compare all files from two revisions](http://blog.binarymist.net/2013/02/02/painless-git-diff/):  
`git difftool -t meld <commit> <commit>`  
Or to open all file comparisons:  
`git difftool <commit_1> <commit_2>` # works across branches  
`git difftool -t diffuse <develop> <anotherBranch>`

List all files that were changed between revisions:  
`git diff --name-only <SHA1> <SHA2>`  
or:  
`git diff --name-only HEAD~10 HEAD~5`

## Patching

Create a patch with all changes from current point to `hash1`:  
`git format-patch <hash1> --stdout > <myPatchFile>`

Apply changes in `myPatchFile` to your current working directory:  
`git apply <myPatchFile>`

[Create two patch files](http://makandracards.com/makandra/2521-git-how-to-create-and-apply-patches), one for each commit since `HEAD~~`:  
`git format-patch HEAD~~`





## Less Used Commands

Show all files in the index  
[`git ls-files`](https://git-scm.com/docs/git-ls-files)






