
# Checkout Previous Branch

Git makes it easy to checkout the last branch you were on.

```bash
$ git checkout -
```

This is shorthand for `git checkout @{-1}` which is a way of referring to
the previous (or last) branch you were on. You can use this trick to easily
bounce back and forth between `master` and a feature branch.

1. [StackOverfow](http://stackoverflow.com/questions/7206801/is-there-any-way-to-git-checkout-previous-branch)
2. [How To Checkout The Previous Branch In Git](https://marcgg.com/blog/2015/10/18/git-checkout-minus/)