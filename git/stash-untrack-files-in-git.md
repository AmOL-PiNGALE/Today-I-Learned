
# Stash untracked files in Git

Git allows you to stash untracked files with the `--include-untracked` or `-u` option:

```bash
git stash --include-untracked
# or
git stash -u
```

New versions of git now have `git stash --all` which stashes all files, including untracked and ignored files.

git stash removes any untracked or uncommited files from your workspace. And you can revert git stash by using following command

```bash
git stash pop
```

**[Warning, doing this will permanently delete your files if you have any directory/* entries in your gitignore file.](https://web.archive.org/web/20140310215100/http://blog.icefusion.co.uk:80/git-stash-can-delete-ignored-files-git-stash-u/)**

As of version 1.7.7 you can use `git stash --include-untracked` or `git stash save -u` to stash untracked files without staging them.

Add (git add) the file and start tracking it. Then stash. Since the entire contents of the file are new, they will be stashed, and you can manipulate it as necessary.

</br>

### References

1. [https://stackoverflow.com/questions/835501/how-do-you-stash-an-untracked-file](https://stackoverflow.com/questions/835501/how-do-you-stash-an-untracked-file)
