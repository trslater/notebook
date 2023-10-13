# Working With Forks

Your forked repo should automatically have a second remote called `upstream` that points to the upstream repo (i.e., the repo your repo was forked from).

To access a branch on the upstream repo, first fetch it:

```
$ git fetch upstream [branch]
```

To make a local working copy, you can check it out (**note**: they should be automatically named prefixed with `upstream`):

```
$ git checkout upstream/[branch]
```

You can also merge the branch into a local branch:

```
$ get checkout [local-branch]
$ git merge upstream [branch]
```
