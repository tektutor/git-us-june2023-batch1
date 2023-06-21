# Day 2

## Lab - Renaming a branch

By default git creates master branch when we create new repository locally.

You may configure the default preferred branch as shown below
```
git config --global init.defaultbranch main
```

In case, you have already created the local repo, then you may try renaming the master branch to main as shown below
```
git branch --move master main
```

Expected output
<pre>
jegan@tektutor.org:~/git-demo$ git branch --move master main
jegan@tektutor.org:~/git-demo$ git status
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)
jegan@tektutor.org:~/git-demo$ git status
On branch main

No commits yet

nothing to commit (create/copy files and use "git add" to track)
 
</pre>
