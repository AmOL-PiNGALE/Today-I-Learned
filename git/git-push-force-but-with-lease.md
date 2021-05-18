
# Git Push Force but with lease

If you need to run a `git push --force` to push a fixup or an amended commit you can try the `--force-with-lease` tag first for safety. It will protect you to overwrite a commit made by other dev.

```shell
alias gplease='git push --force-with-lease'
```

Check [Git push documentation](https://git-scm.com/docs/git-push#git-push---force-with-leaseltrefnamegtltexpectgt)

> `--force-with-lease` will protect all remote refs that are going to be updated by requiring their current value to be the same as the remote-tracking branch we have for them.