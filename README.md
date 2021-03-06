# SimpleGit

Safely play with Git and GitHub via command line, and several useful shell combos.

## Installing Git

- See <https://git-scm.com/downloads>

## Basic Git setup

If you are using macOS, like me, I recommend several settings.

```sh
# See https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
git config --global core.editor "nano"  # You can also use Visual Studio Code or Gedit by setting nano to code or gedit
git config --list  # or git config --global --edit
```

## Local Git and remote Git

- Local Git can be created after navigating to the folder via command line, inside the terminal.

```sh
git init
git add .
git commit -m 'Commit message'  # Or simple `git commit`, and it will open your default text editor
```

- You can also create a local Git via cloning from a remote (online) Git. The folder to use Git might not be existed yet, though.

```sh
git clone https://github.com/foo/bar.git
```

- Remote Git on GitHub can be easily created as a repository on [GitHub website](https://github.com). Better make it empty, or you will run into problems later.
- Then, set the remote branch on your computer,

```sh
git remote add origin https://github.com/foo/bar.git
```

- Or, if you put in a wrong URL, and you want to change, (Source: <https://stackoverflow.com/questions/13509293/git-fatal-could-not-read-from-remote-repository>)

```sh
git remote set-url origin https://github.com/foo/bar.git
```

## Syncing local and remote Git

- Merging and solving conflicts can be a little complex. Easier actions are pushing and pulling. (Push: local->remote, Pull: remote->local).

```sh
git push -u origin master
git pull origin master
```

## `.gitignore`

Put the filenames you want to ignore in `.gitignore`.

## Update Git based on Gitignore

See <https://stackoverflow.com/questions/1143796/remove-a-file-from-a-git-repository-without-deleting-it-from-the-local-filesyste>

```sh
git rm --cached `git ls-files -i -X .gitignore`
```

## What I recently googled for

- [How to prune local tracking branches that do not exist on remote anymore](https://stackoverflow.com/questions/13064613/how-to-prune-local-tracking-branches-that-do-not-exist-on-remote-anymore)

```sh
git branch -D <branchname>
```

- [How to replace master branch in Git, entirely, from another branch?](https://stackoverflow.com/questions/2862590/how-to-replace-master-branch-in-git-entirely-from-another-branch)

```sh
git branch -m master old-master
git branch -m seotweaks master
git push -f origin master
# git branch -D old-master
```

- [How can I determine the URL that a local Git repository was originally cloned from?](https://stackoverflow.com/questions/4089430/how-can-i-determine-the-url-that-a-local-git-repository-was-originally-cloned-fr)

```sh
git config --get remote.origin.url
```

Can also be done and retrieved in JavaScript

```js
const { execSync } = require('child_process')
const repoName = execSync('git config --get remote.origin.url').toString()
console.log(repoName)
```

- [Git submodule](https://git-scm.com/book/en/v2/Git-Tools-Submodules)

```sh
git submodule add https://github.com/foo/bar.git packages/bar
```

- [Force “git push” to overwrite remote files](https://stackoverflow.com/questions/10510462/force-git-push-to-overwrite-remote-files) -- Apparently, it works as same as deleting the repo on GitHub, and recreate the repo again, I recommend [renaming Git-branch](https://multiplestates.wordpress.com/2015/02/05/rename-a-local-and-remote-branch-in-git/) instead. `git branch -m old-name new-name`

```sh
git push -f <remote> <branch>
```

- [Git reset all files with particular extension](https://stackoverflow.com/questions/58409532/git-reset-all-files-with-particular-extension)

```sh
git ls-files master -- *.scss.d.ts
git checkout master -- $(git ls-files master -- *.scss.d.ts)
```

## Git commands I use often

- [git clone](https://git-scm.com/docs/git-clone)
- [git submodule](https://git-scm.com/docs/git-submodule)

## How VSCode helps me a little with Git

If I recommend any GUI tools at all, that would be Visual Studio Code. Not sure how to work this in PyCharm, IntelliJ, Android Studio, or WebStorm...

- It helps me mainly with [git checkout](https://git-scm.com/docs/git-checkout)

## Historical notes

- Year 2019's writing can be seen here -- [/blog/2019/](/blog/2019/)
