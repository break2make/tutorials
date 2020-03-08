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

# Links
- [15-tips-to-enhance-your-github-flow](https://hackernoon.com/15-tips-to-enhance-your-github-flow-6af7ceb0d8a3)
