# Day 3

## Undo changes using reset

Git reset supports two modes
1. soft
2. hard

Soft reset will undo the changes, commits the changes and retains your old changes in the staging area.  We need to keep in mind that reset command will modify the commit history.

Hard reset will undo the changes and straight away it will commit the changes by modifying the commit history without any further warning.


#### Performing a soft reset
```
cd ~/git-demo
rm -rf .git
rm *

git config --global init.defaultbranch main
git config --global core.autocrlf true # Recommended especially for windows users
git config --global -l
git init

touch file1.txt file2.txt file3.txt
git add *
git commit -m "Initial commit."

echo "Line 1" > file1.txt
git commit -am "Added Line 1 in file1.txt"

echo "Line 1" > file2.txt
git commit -am "Added Line 1 in file2.txt"

echo "Line 2" >> file2.txt
git commit -am "Added Line 2 in file2.txt"

echo "Line 1" > file3.txt
git commit -am "Added Line 1 in file3.txt"

echo "Line 2" >> file3.txt
git commit -am "Added Line 2 in file3.txt"

echo "Line 3" >> file3.txt
git commit -am "Added Line 3 in file3.txt"

git log --oneline
```

Expected output
<pre>
918df8a (HEAD -> main) Added Line 3 in file3.txt
d3f5fe4 Added Line 2 in file3.txt
5545ed5 Added Line 1 in file3.txt
41b8335 Added Line 2 in file2.txt
7d47706 Added Line 1 in file2.txt
155e471 Added Line 1 in file1.txt
cbdcb8d Initial commit.

jegan@tektutor.org:~/git-demo$ <b>git reset --soft d3f5fe4</b>
jegan@tektutor.org:~/git-demo$ cat file3.txt 
Line 1
Line 2
Line 3
  
jegan@tektutor.org:~/git-demo$ git status
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   file3.txt
</pre>    

#### Performing a hard reset

<pre>
jegan@tektutor.org:~/git-demo$ git status
On branch main
nothing to commit, working tree clean
jegan@tektutor.org:~/git-demo$ git log --oneline
d3f5fe4 (HEAD -> main) Added Line 2 in file3.txt
5545ed5 Added Line 1 in file3.txt
41b8335 Added Line 2 in file2.txt
7d47706 Added Line 1 in file2.txt
155e471 Added Line 1 in file1.txt
cbdcb8d Initial commit.
jegan@tektutor.org:~/git-demo$ cat file3.txt 
Line 1
Line 2
</pre>

Expected output
<pre>
jegan@tektutor.org:~/git-demo$ <b>git reset --hard 5545ed5</b>
HEAD is now at 5545ed5 Added Line 1 in file3.txt
jegan@tektutor.org:~/git-demo$ git status
On branch main
nothing to commit, working tree clean
jegan@tektutor.org:~/git-demo$ git log --oneline
5545ed5 (HEAD -> main) Added Line 1 in file3.txt
41b8335 Added Line 2 in file2.txt
7d47706 Added Line 1 in file2.txt
155e471 Added Line 1 in file1.txt
cbdcb8d Initial commit.
jegan@tektutor.org:~/git-demo$ cat file3.txt 
Line 1
</pre>


## Summary
<pre>
git clone - to download the latest code from remote GitHub repo to local repo
git pull - to download only the delta changes done in remote GitHub repo to your local repo
git init - to create an empty local repository
git status - to check the status of your local repo
git add - to add your changes to the staging area
git commit - to checkin your changes to the local repo
git log - to show the log/commit history
git tag - to add human friendly tags to the commid id
git diff - to observe the diff between two files
git commit --amend - to make small corrections in the recent commit
git restore - to undo changes done in a commit, requires an extra commit 
git reset - to undo changes done in a commit with an extra commit
</pre>

# Git Branches

## ⛹️‍♀️ Lab - Creating a new branch called dev-1.0 from main branch

Let us check the log in the main branch
```
cd ~/git-demo
git log --oneline
ls
cat file1.txt
cat file2.txt
cat file3.txt
```

Expected output
<pre>
jegan@tektutor.org:~/git-demo$ git log --oneline
5545ed5 (HEAD -> main) Added Line 1 in file3.txt
41b8335 Added Line 2 in file2.txt
7d47706 Added Line 1 in file2.txt
155e471 Added Line 1 in file1.txt
cbdcb8d Initial commit.
</pre>

Let us create the dev-1.0 branch from main branch
```
git checkout -b dev-1.0
ls
cat file1.txt
cat file2.txt
cat file3.txt

git log --oneline

touch file4.txt
echo "Enhancement - User Story 123" > file4.txt
git add file4.txt
git commit -m "Added Enhancement - User Story 123" 

echo "BUGFIX 235434" >> file3.txt
git add file3.txt
git commit -m "Fixed BUG - BUG235434"

git log --oneline
```

Switch to main branch

Observe file4.txt doesn't exist in the main branch
```
git checkout main
ls
cat file1.txt
cat file2.txt
cat file3.txt

git log --oneline
```

Finding the currently active branch.  The active branch is shown in green color and the branch name is preceded with "*".
```
git branch
```

Switch back to dev-1.0 branch
```
git checkout dev-1.0
git status
ls
```

## ⛹️‍♀️ Lab - Checking diff between two commits
```
cd ~/git-demo
git branch
git checkout dev-1.0
git log --oneline

git diff cbdcb8d 155e471
git diff cbdcb8d 7d47706
git diff 5545ed5 3076833  #This compares the changes done in dev-1.0 and main branch
``` 

Expected output
<pre>
jegan@tektutor.org:~/git-demo$ git branch
* dev-1.0
  main
jegan@tektutor.org:~/git-demo$ git log --oneline
3076833 (HEAD -> dev-1.0) Added User story - ENC466123
e4b2b6c Added Enhancement - EN345432
f0a6d42 Added Enhancement - EN124234
5545ed5 (main) Added Line 1 in file3.txt
41b8335 Added Line 2 in file2.txt
7d47706 Added Line 1 in file2.txt
155e471 Added Line 1 in file1.txt
cbdcb8d Initial commit.
jegan@tektutor.org:~/git-demo$ git diff cbdcb8d 155e471
diff --git a/file1.txt b/file1.txt
index e69de29..3be9c81 100644
--- a/file1.txt
+++ b/file1.txt
@@ -0,0 +1 @@
+Line 1
jegan@tektutor.org:~/git-demo$ git diff cbdcb8d 7d47706
diff --git a/file1.txt b/file1.txt
index e69de29..3be9c81 100644
--- a/file1.txt
+++ b/file1.txt
@@ -0,0 +1 @@
+Line 1
diff --git a/file2.txt b/file2.txt
index e69de29..3be9c81 100644
--- a/file2.txt
+++ b/file2.txt
@@ -0,0 +1 @@
+Line 1
jegan@tektutor.org:~/git-demo$ git diff 5545ed5 3076833
diff --git a/file1.txt b/file1.txt
index 3be9c81..e1001fd 100644
--- a/file1.txt
+++ b/file1.txt
@@ -1 +1,2 @@
 Line 1
+Enhancement - user story2
diff --git a/file3.txt b/file3.txt
index 3be9c81..8f394db 100644
--- a/file3.txt
+++ b/file3.txt
@@ -1 +1,2 @@
 Line 1
+Enhancement - user story1
diff --git a/file4.txt b/file4.txt
new file mode 100644
index 0000000..e9bc72b
--- /dev/null
+++ b/file4.txt
@@ -0,0 +1 @@
+Added User story - ENC466123
</pre>
