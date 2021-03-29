Change Git Commit Message
------------------------------------------------------------------------------------------------
Commits to Git are accompanied with a commit message that explains what changes the commit has made to the code. However, a situation may arise where the commit message will need to be changed after it has been pushed. ​ex Made a typo in your commit message? Or forgot to mention an important detail in the message?


Amending the Last Commit
------------------------------------------------------------------------------------------------
To change the last commit, you can simply commit again, using the --amend flag:

```
  $ git commit --amend -m "New and correct message"
  $ git push --force repository-name branch-name
```

Note that using --force is not recommended unless you are absolutely sure that no one else has cloned your repository after the latest commit.
A safer alternative is to use:

```
  $ git push --force-with-lease repository-name branch-name
```



------------------------------------------------------------------------------------------------

[source](https://www.educative.io/edpresso/how-to-change-a-git-commit-message-after-a-push)
