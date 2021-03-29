Rename a Git Branch
------------------------------------------------------------------------------------------------

1. Rename your local branch:

- If you want to rename the current branch, you can do:
```
  git branch -m <new_name>
```

- If you want to rename a branch while pointed to any branch, do:
```
  git branch -m <old_name> <new_name>
```

2. Delete the old-name remote branch and push the new-name local branch:
```
  git push origin :<old_name> <new_name>
```

3. Reset the upstream branch for the new-name local branch:
Switch to the branch and then:
```
  git push origin -u <new_name>
```


------------------------------------------------------------------------------------------------

1. [How do I rename a local Git branch?](https://stackoverflow.com/questions/6591213/how-do-i-rename-a-local-git-branch)

2. [Rename master branch for both local and remote Git repositories.](https://stackoverflow.com/questions/1526794/rename-master-branch-for-both-local-and-remote-git-repositories)

3. [How do I rename both a Git local and remote branch name?](https://stackoverflow.com/questions/30590083/how-do-i-rename-both-a-git-local-and-remote-branch-name/30590238#30590238)