# SimpleGit

Safely play with Git and GitHub via command line, and several useful shell combos.

## Installing Git

- See <https://git-scm.com/downloads>

## Local Git and remote Git

- Local Git can be created after navigating to the folder via command line, inside the terminal.

```commandline
git init
git add .
git commit -m 'Commit message'
```

- You can also create a local Git via cloning from a remote (online) Git. The folder to use Git might not be existed yet, though.

```commandline
git clone https://github.com/foo/bar.git
```

- Remote Git on GitHub can be easily created as a repository on [GitHub website](https://github.com). Better make it empty, or you will run into problems later.
- Then, set the remote branch on your computer,

```commandline
git remote add origin https://github.com/foo/bar.git
```

- Or, if you put in a wrong URL, and you want to change, (Source: <https://stackoverflow.com/questions/13509293/git-fatal-could-not-read-from-remote-repository>)

```commandline
git remote set-url origin https://github.com/foo/bar.git
```

## Syncing local and remote Git

- Merging and solving conflicts can be a little complex. Easier actions are pushing and pulling. (Push: local->remote, Pull: remote->local).

```commandline
git push -u origin master
git pull origin master
```

- Merging and solving conflicts' commands are,

```commandline
git pull --rebase origin master
git rebase master
git add .
git rebase continue
```

**If you run into Conflicts during the Rebase:**
First, resolve conflict in file. Then:

```commandline
git add .
git rebase --continue
```

Then, you can `push` when you are ready. (Source: <https://stackoverflow.com/a/53076196/9023855>)

## Branching

```commandline
git branch <branch-name>
git checkout <branch-name>
```

## `.gitignore`

Put the filenames you want to ignore in `.gitignore`.

## Some possible serious mistakes

### Mistakenly `commit` large or unwanted files

First of all, add the filename to [`.gitignore`](https://www.gitignore.io).

If you have never really `push` the files, simply (Source: <https://stackoverflow.com/a/38629666/9023855>)

```commandline
git reset --hard HEAD~1
git rm --cached <file_name>
```

Or, if you have a lot of files, (Source: <https://stackoverflow.com/questions/13541615/how-to-remove-files-that-are-listed-in-the-gitignore-but-still-on-the-repositor>)

```commandline
git rm --cached `git ls-files -i --exclude-from=.gitignore`         # Or
git ls-files -i --exclude-from=.gitignore | xargs git rm --cached
```

If you have really `push` the file, it is more complicated (Source: <https://help.github.com/articles/removing-sensitive-data-from-a-repository/>)

```commandline
bfg --delete-files YOUR-FILE-WITH-SENSITIVE-DATA
# Or java -jar bfg.jar
git reflog expire --expire=now --all && git gc --prune=now --aggressive
git push
```

Get `bfg.jar` from <https://rtyley.github.io/bfg-repo-cleaner/>

Or,

```commandline
git filter-branch --force --index-filter \
'git rm --cached --ignore-unmatch PATH-TO-YOUR-FILE-WITH-SENSITIVE-DATA' \
--prune-empty --tag-name-filter cat -- --all
git commit -m "Add YOUR-FILE-WITH-SENSITIVE-DATA to .gitignore"
git push origin --force --all
```
