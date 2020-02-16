# Git Guide

I forked a [popular list of git-commands](https://github.com/joshnh/Git-Commands) and added my own notes to serve as a general Git Guide

<!-- 
====================  Contribution Guide ====================
1. Add the section header in the ## Sections
2. Create the header and start typing.
-->

## TLDR

```bash
# Clone the Repo
git clone <repolink.git>
# Get Status (whether files were modified or remote was updated)
git status
# Pull changes to local
git pull # alternatively: git pull origin <branchName> (no '-u')
# Stage your changes
git add <filename> # alternatively: git add . to add all files
# Commit your changes
git commit -m "[#XX] Add Git guide's TLDR"
# Push your changes
git push # alternatively: git push -u origin <branchName> (note the '-u')

# Create a branch
git checkout -b <branchName>
# Update the list of branches from the remote
git fetch -a
# Change branch
git checkout <branchName>
# Go back to master
git checkout master

# See the list of commits
git log
```

More Details:

For `git clone` see [Using Existing Folder](#existing-folder)

For `git status`, `git add` and `git commit` see [Basic Snapshotting](#basic-snapshotting)

For `git pull` and `git push` see [Sharing & Updating Projects](#sharing--updating-projects)

For `git checkout` see [Branching & Merging](#branching--merging)

For `git log` see [Inspection & Comparison](#inspection--comparison)

## Git Basics

### Accessing a repo

Two ways of accessing a repo, one by cloning, and the other one by `git init`.

#### Cloning

While your terminal is at the folder where you want to clone the repo, execute `git clone <repolink.git>`. When you `cd` into the repo folder, your git should now be at `master`

#### Existing Folder

If you have an existing folder where you want to place the files of the repo, you should use the `git init` workflow instead.

Navigate to your folder using the terminal. Execute `git init`. This will create the `.git` files that Git needs to function. Your terminal might now indicate that you are in a Git folder.

Then, enter `git remote add origin <repolink.git>`. This tells Git that the remote repo (aka upstream) is at `<repolink.git>`.

Now, pull the remote files using `git pull`. Your folder should now fill with the repo files and you are ready to work on `master`.

### Branches

#### Update your branch cache

When there are new branches created, Git does not automatically update your cache. Use the command `git fetch -a` to receive a list of all the branches available at the remote. Then use `git branch -a` to see a list of all the branches (including those at the remote).

#### Creating a new branch

While you don't always need to, you should do `git pull` and `git fetch -a` to ensure that you have the latest version locally. This is especially true for if you're trying to create a branch off `master`.

First `git checkout <branch>` you want to start your new branch from.

Then, execute `git checkout -b <nameOfnewBranch>` to create a branch.

Alternatively, you can just do `git checkout -b <nameOfnewBranch> origin/<branch>`.

### Typical workflow

While you are contributing to a repo, there is a typical workflow you will be doing all the time.

#### Staging, Commiting, Pushing

After you've done some modifications, you use `git add <fileName>` to stage them (add them to your commit). Alternatively, you can use `git add .` or `git add *` to stage all modified files.

Then you commit the changes by giving them a [Good commit message](#writing-good-git-commit-messages) using `git commit -m "[#issueNumber] PresentTenseVerb + detail"`. Alternatively, you could do the `add` and `commit` in one step using `git commit -am "<commit message>"`. Note that this `-am` command only stages and commit files already tracked by Git (if you created any new files, they will be ignored, so you'll have to use `git add <file>`.

Before you push the commit, ensure that your branch has been updated with any new commits from the remote by executing `git pull`.

Finally, push the commit with `git push`.

#### Reverting some changes

If you've tried something, it's not working and you would like to go back to a previous edition of the file you have modified, you can use `git checkout <nameOfFile>`. There is also `git reset` that will reset all changes to the nearest commit and `git revert` that can revert the changes of files you have committed. Check the commands help page for more usage information. This is why _frequent commits_ and _frequent pushes_ are important, as you risk losing all your work if you do not do it often enough.

## Git Commands

### Getting & Creating Projects

| Command | Description |
| ------- | ----------- |
| `git init` | Initialize a local Git repository |
| `git clone ssh://git@github.com/[username]/[repository-name].git` | Create a local copy of a remote repository |

### Basic Snapshotting

| Command | Description |
| ------- | ----------- |
| `git status` | Check status (also -s for short, --porcelain for pretty)|
| `git add [file-name.txt]` | Add a file to the staging area |
| `git add -A` | Add all new and changed files to the staging area |
| `git commit -m "[commit message]"` | Commit changes |
| `git rm -r [file-name.txt]` | Remove a file (or folder) |

### Branching & Merging

| Command | Description |
| ------- | ----------- |
| `git branch` | List branches (the asterisk denotes the current branch) |
| `git branch -a` | List all branches (local and remote) |
| `git branch [branch name]` | Create a new branch |
| `git branch -d [branch name]` | Delete a branch |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git checkout -b [branch name]` | Create a new branch and switch to it |
| `git checkout -b [branch name] origin/[branch name]` | Clone a remote branch and switch to it |
| `git branch -m [old branch name] [new branch name]` | Rename a local branch |
| `git checkout [branch name]` | Switch to a branch |
| `git checkout -` | Switch to the branch last checked out |
| `git checkout -- [file-name.txt]` | Discard changes to a file |
| `git merge [branch name]` | Merge a branch into the active branch |
| `git merge [source branch] [target branch]` | Merge a branch into a target branch |
| `git stash` | Stash changes in a dirty working directory [see Stash section](#stashing) |
| `git stash clear` | Remove all stashed entries |

### Sharing & Updating Projects

| Command | Description |
| ------- | ----------- |
| `git push origin [branch name]` | Push a branch to your remote repository |
| `git push -u origin [branch name]` | Push changes to remote repository (and remember the branch) |
| `git push` | Push changes to remote repository (remembered branch) |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git pull` | Update local repository to the newest commit |
| `git pull origin [branch name]` | Pull changes from remote repository |
| `git remote add origin ssh://git@github.com/[user]/[repo].git` | Add a remote repository |
| `git remote set-url origin ssh://git@github.com/[user]/[repo].git` | Set a repository's origin branch to SSH |

### Inspection & Comparison

| Command | Description |
| ------- | ----------- |
| `git log` | View changes |
| `git log --summary` | View changes (detailed) |
| `git log --oneline` | View changes (briefly) |
| `git diff [source branch] [target branch]` | Preview changes before merging |

### Stashing

Git only stashes staged and tracked files by default.

Use `git stash -u` to also stash untracked files.
Use `git stash -a` to also stash ignored files.

| Command | Description |
| ------- | ----------- |
| `git stash pop`| Reapply saved stash (can use stash@{id} for specific stashes and delete the stash|
| `git stash apply`| Reapply saved stash and keep it stashed|
| `git stash list`| List all saved stashes|
| `git stash show` `-p`| List changes between current and stash with `-p` for full diff|

More information can be found [here](https://www.atlassian.com/git/tutorials/saving-changes/git-stash)

## Advanced Git Guides

### Changing a commit

`git rebase -i HEAD~n` use a commit before the one you want to change

Use VIM to pick/reword/... (actually rewrite pick into "reword" or whatever other command)

`git push` (sometimes need `--force`)

### Archiving Branches

[Source](https://stackoverflow.com/questions/35738790/how-to-close-a-branch-in-git)

`git tag archive/<branchname> <branchname>`

`git branch -d <branchname>`

`git checkout master`

Retrieving the archived branch

`git checkout -b new_branch_name archive/<branchname>`

My solution (from remote)

`git tag archive/<branchname> remotes/origin/<branchname>`

`git push origin --delete <branchname>`

Then, update remote

`git push --tags`

### Overwrite Local Branch

[Source](https://www.freecodecamp.org/forum/t/git-pull-how-to-override-local-files-with-git-pull/13216)

`git fetch (--all)`

`git reset (--hard <remote>/<branch_name>)` i.e. `git reset --hard origin/master`

### Overwrite Remote Branch

`git push --force-with-lease` (better way, won't push if unknown state)

`git push --force` (unsafe way)

### Delete Sensitive Files from Git

[Source](https://help.github.com/en/github/authenticating-to-github/removing-sensitive-data-from-a-repository)

See [BFG guide](https://rtyley.github.io/bfg-repo-cleaner/) use `bfg` instead of the java commands (make sure to mirror)

Can also use `git filter-branch` (more details in source)

### Forking Workflow

[Source](https://docs.qmk.fm/#/newbs_git_using_your_master_branch)

For some development projects, you might want to fork an existing repository and keep the master branch updated with the fork, and only work off in a development branch in the fork.

### Keeping the master branch updated

* Add the source repo as your as a remote alias `git remote add upstream <repolink.git>`

  * Here we used `upstream` by convention, but you can name it anything you want

* Verify that the repository has been added by running `git remote -v` (the `<repolink.git>` should be displayed right next to the alias you chose (`upstream` in this case))

* Now you can check for updates in the source repo by using `git fetch <alias>` (`git fetch upstream`).

To update your fork's master branch, run the following (with `Enter` key after each line):

```bash
git checkout master
git fetch upstream
git pull upstream master
git push origin master
```

## Good Practices

### Writing good Git Commit Messages

From [How to write a Git Commit Message](https://chris.beams.io/posts/git-commit/)

1. Separate subject from body with a blank line
2. Limit the subject line to 50 characters
3. Capitalize the subject line
4. Do not end the subject line with a period
5. Use the imperative mood in the subject line
6. Wrap the body at 72 characters
7. Use the body to explain what and why vs. how

```Fix typo in README.md``` instead of ```Fixed typo in READMEmd.```

### Being a good Code Reviewer

[Google's Enginnering Practices documentation](https://google.github.io/eng-practices/review/) is a good reference for writing a good Code Review.
