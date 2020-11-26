
# .gitignore

To know which files are ignored (not tracked) by git in your local directory, we can use the following command (there are many commands to do the same):
```
$ git status --ignored
```

Useful resources to learn how to write a `.gitignore`
- https://docs.microsoft.com/en-us/azure/devops/repos/git/ignore-files?view=azure-devops&tabs=visual-studio


# Can't keep an empty folder in git

>There are times when you'd like to track an empty directory within git but there's a problem: git wont allow you to add a directory that doesn't have a file in it.  The easy solution is putting an empty stub file within the directory. [source](https://davidwalsh.name/git-empty-directory)

The name of the stub-file can be anything. However, if we use `.gitignore` as sub-file with the following content, it provides additional advantage.
```txt
# Ignore everything in this directory
*
# Except this file
!.gitignore
```
This `.gitignore` provides the following advantages:
- We can tell git to ignore specific type of files. The `*` is mentioned to ignore everything inside this directory. 
- Using `!.gitignore`, you are telling git to track the `.gitignore`.

For further reading, check these resources:
- [What are the differences between .gitignore and .gitkeep?](https://stackoverflow.com/questions/7229885/what-are-the-differences-between-gitignore-and-gitkeep)
- [Hey git, please .keep those folders](https://medium.com/@kinduff/hey-git-please-keep-those-folders-eb0ed37621c8)
- [How can I add an empty directory to a Git repository?](https://stackoverflow.com/questions/115983/how-can-i-add-an-empty-directory-to-a-git-repository)
- [Does Git delete empty folders?](https://superuser.com/questions/1472515/does-git-delete-empty-folders)

# Git Merge
Please check the following liks:
- [Git Branching - Basic Branching and Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)
- [Git Merge](https://www.atlassian.com/git/tutorials/using-branches/git-merge)

Quick steps to be executed before merging `branch-X` into `branch-Y`:
1. Goto `brnach-Y`
    ```
    git checkout branch-Y
    ```
1. Update `branch-Y` if remote branch is updated in-between by someone else
    ```
    git pull
    ```
1. Merge `branch-X` into `branch-Y`
    ```
    git merge branch-X
    ```

 If you find any conflict during merging, please resolved them first with the help of [link](https://www.atlassian.com/git/tutorials/using-branches/merge-conflicts), and then track those changes using `git add` and eventually use `git commit`.

# Rewriting the most recent commit message
You can change the most recent commit message using the following command:
```
git commit --amend
```

In Git, the text of the commit message is part of the commit. Changing the commit message will change the commit ID--i.e., the SHA1 checksum that names the commit. Effectively, you are creating a new commit that replaces the old one.

## Commit has not been pushed online
If the commit only exists in your local repository and has not been pushed to GitHub, you can amend the commit message with: 
```
git commit --amend
```
On the command line, navigate to the repository that contains the commit you want to amend.

Type `git commit --amend` and press Enter.

In your text editor, edit the commit message, and save the commit. The new commit and message will appear on GitHub the next time you push.

You can change the default text editor for Git by changing the core.editor setting. For more information, see "Basic Client Configuration" in the Git manual.

## Amending older or multiple commit messages
If you have already pushed the commit to GitHub, you will have to force push a commit with an amended message.

We strongly discourage force pushing, since this changes the history of your repository. If you force push, people who have already cloned your repository will have to manually fix their local history. For more information, see "Recovering from upstream rebase" in the Git manual.

## Amending the message of the most recently pushed commit

Follow the steps above to amend the commit message.
Use the push --force command to force push over the old commit.
```
$ git push --force example-branch
```

Links
https://help.github.com/en/github/committing-changes-to-your-project/changing-a-commit-message

# Delete git branch
This section is wrriten based on https://www.git-tower.com/learn/git/faq/delete-remote-branch

> You cannot delete the present branch (say `branch-x`). You need to checkout to another branch (say `master` branch), to delete the `branch-x`. 

# Deleting local branches in Git
```
$ git branch -d LOCAL-BRANCH-NAME
```
Using the "-d" flag, you tell "git branch" which `LOCAL-BRANCH-NAME` you want to delete.

Note that you might also need the "-f" flag if you're trying to delete a branch that contains unmerged changes. Use this option with care because it makes losing data very easy.

## Deleting remote branches in Git
To delete a remote branch, we do not use the "git branch" command - but instead "git push" with the "--delete" flag:
```
$ git push origin --delete REMOTE-BRANCH-NAME
```

## Deleting both a local and a remote branch
Just a side note: please keep in mind that local and remote branches actually have nothing to do with each other. They are completely separate objects in Git.

Even if you've established a tracking connection (which you should for most scenarios), this still does not mean that deleting one would delete the other, too!

If you want any branch item to be deleted, you need to delete it explicitly.

# Git repository preparation for a simple project

For this project, we assume the following three branch:

Step 1: Create a empty git repo (without README.md)

Step 2: Clone the repository, perform the configuration, push the update to remote and apply the branch permission using the following commands:

## Prepare a git repository for a new project

```
git clone REPO
cd REPO
```
Now, create a readme file, and push it in remote branch:     

```
touch README.md
git add --all
git commint -m "Initial Commit"
git push -u origin master
```
Let's assume that `master` branch will contains of the released code, while development will happend in `dev` branch and tested code will be merged into `dev-tested` branch. During release, the `dev-tested` branch needs to be merged with release tag. This git project flow can be achieved using the following commands:
```
git checkout -b dev
git push -u origin dev
git checkout -b dev-tested
git push -u origin dev-tested
```
Note that it is also possible to push all branches together using `git push -u origin --all`.


# Links
- [15 tips to enhance your github flow](https://hackernoon.com/15-tips-to-enhance-your-github-flow-6af7ceb0d8a3)
- [Github git cheat sheet](https://github.github.com/training-kit/downloads/github-git-cheat-sheet.pdf)
