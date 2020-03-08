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
