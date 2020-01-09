# What I recently googled and more

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
