# Day 4

## ⛹️ Lab - Git soft reset

```
cd ~/git-demo
rm -rf .git
rm *

touch file1.txt
git init
git status
git add file1.txt
git commit -m "Initial commit."

echo "Line 1" > file1.txt
git commit -am "Added Line 1"

echo "Line 2" >> file1.txt
git commit -am "Added Line 2"

echo "Line 3" >> file1.txt
git commit -am "Added Line 3"

echo "Line 4" >> file1.txt
git commit -am "Added Line 4"

echo "Line 5" >> file1.txt
git commit -am "Added Line 5"
git status
git log --oneline
```

Expected output
<pre>
file1.txt
jegan@tektutor.org:~/git-demo$ git init
Initialized empty Git repository in /home/jegan/git-demo/.git/
jegan@tektutor.org:~/git-demo$ git status
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	file1.txt

nothing added to commit but untracked files present (use "git add" to track)
jegan@tektutor.org:~/git-demo$ git add .
jegan@tektutor.org:~/git-demo$ git status
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   file1.txt

jegan@tektutor.org:~/git-demo$ git commit -m "Initial commit."
[main (root-commit) 52acebe] Initial commit.
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 file1.txt
    
jegan@tektutor.org:~/git-demo$ echo "Line 1" > file1.txt 
jegan@tektutor.org:~/git-demo$ git commit -am "Added Line 1"
warning: LF will be replaced by CRLF in file1.txt.
The file will have its original line endings in your working directory
[main 6d0091c] Added Line 1
 1 file changed, 1 insertion(+)
    
jegan@tektutor.org:~/git-demo$ echo "Line 2" >> file1.txt 
jegan@tektutor.org:~/git-demo$ git commit -am "Added Line 2"
warning: LF will be replaced by CRLF in file1.txt.
The file will have its original line endings in your working directory
[main 368eef9] Added Line 2
 1 file changed, 1 insertion(+)
    
jegan@tektutor.org:~/git-demo$ echo "Line 3" >> file1.txt 
jegan@tektutor.org:~/git-demo$ git commit -am "Added Line 3"
warning: LF will be replaced by CRLF in file1.txt.
The file will have its original line endings in your working directory
[main 6b2f043] Added Line 3
 1 file changed, 1 insertion(+)
    
jegan@tektutor.org:~/git-demo$ echo "Line 4" >> file1.txt 
jegan@tektutor.org:~/git-demo$ git commit -am "Added Line 4"
    
warning: LF will be replaced by CRLF in file1.txt.
The file will have its original line endings in your working directory
[main 1e95a95] Added Line 4
 1 file changed, 1 insertion(+)
    
jegan@tektutor.org:~/git-demo$ echo "Line 5" >> file1.txt 
jegan@tektutor.org:~/git-demo$ git commit -am "Added Line 5"
warning: LF will be replaced by CRLF in file1.txt.
The file will have its original line endings in your working directory
[main 5093009] Added Line 5
 1 file changed, 1 insertion(+)
    
jegan@tektutor.org:~/git-demo$ git log --oneline
5093009 (HEAD -> main) Added Line 5
1e95a95 Added Line 4
6b2f043 Added Line 3
368eef9 Added Line 2
6d0091c Added Line 1
52acebe Initial commit.
</pre>

Now, let's do a soft reset. We would like to revert the code changes done in the commit id 5093009.
```
git reset --soft 1e95a95
git status
git diff --staged # This will show the difference between the file1.txt within the repository and what is in the staging area
```
The above command will update the HEAD to point to the commit id 1e95a95 and discard the commid id 5093009 from the local repo.

Expected output
<pre>
jegan@tektutor.org:~/git-demo$ git reset --soft 1e95a95
jegan@tektutor.org:~/git-demo$ git status
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   file1.txt

jegan@tektutor.org:~/git-demo$ cat file1.txt 
Line 1
Line 2
Line 3
Line 4
Line 5
jegan@tektutor.org:~/git-demo$ git diff
jegan@tektutor.org:~/git-demo$ git diff --staged
diff --git a/file1.txt b/file1.txt
index e579141..572d5d9 100644
--- a/file1.txt
+++ b/file1.txt
@@ -2,3 +2,4 @@ Line 1
 Line 2
 Line 3
 Line 4
+Line 5
</pre>

Now, let's take a backup of this code in the working directory before we can complete discard it
<pre>

jegan@tektutor.org:~/git-demo$ git restore --staged file1.txt # This will discard the code from staging area
jegan@tektutor.org:~/git-demo$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   file1.txt

no changes added to commit (use "git add" and/or "git commit -a")
  
jegan@tektutor.org:~/git-demo$ mkdir -p ../ENH12345_NextSprint
jegan@tektutor.org:~/git-demo$ cp file1.txt ../ENH12345_NextSprint/
jegan@tektutor.org:~/git-demo$ cat file1.txt 
Line 1
Line 2
Line 3
Line 4
Line 5
jegan@tektutor.org:~/git-demo$ git restore file1.txt  #This will discard the code changes from working directory also
jegan@tektutor.org:~/git-demo$ ls
file1.txt
jegan@tektutor.org:~/git-demo$ git status
On branch main
nothing to commit, working tree clean
</pre>

## ⛹️ Lab - Git hard reset
```
cd ~/git-demo
rm -rf .git
rm *

git init
touch file1.txt
git status
git add file1.txt 
git commit -m "Initial commit."
git status
cat file1.txt


echo "Line 1" > file1.txt
git commit -am "Added Line 1"

echo "Line 2" >> file1.txt
git commit -am "Added Line 2"

echo "Line 2" >> file1.txt
git commit -am "Added Line 3"

echo "Line 3" >> file1.txt
git commit -am "Added Line 3"

echo "Line 4" >> file1.txt
git commit -am "Added Line 4"

echo "Line 5" >> file1.txt
git commit -am "Added Line 5"

cat file1.txt
git status
git log --oneline

git reset --hard eb93559
git status
git log --oneline
cat file1.txt
```

Expected output
<pre>
jegan@tektutor.org:~/git-demo$ git init
Initialized empty Git repository in /home/jegan/git-demo/.git/
jegan@tektutor.org:~/git-demo$ touch file1.txt
jegan@tektutor.org:~/git-demo$ git status
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
	file1.txt

nothing added to commit but untracked files present (use "git add" to track)
jegan@tektutor.org:~/git-demo$ git add file1.txt 
jegan@tektutor.org:~/git-demo$ git commit -m "Initial commit."
[main (root-commit) 20583cb] Initial commit.
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 file1.txt
jegan@tektutor.org:~/git-demo$ git status
On branch main
nothing to commit, working tree clean
	  
jegan@tektutor.org:~/git-demo$ cat file1.txt 
jegan@tektutor.org:~/git-demo$ echo "Line 1" > file1.txt 
jegan@tektutor.org:~/git-demo$ git commit -am "Added Line 1"
warning: LF will be replaced by CRLF in file1.txt.
The file will have its original line endings in your working directory
[main 7dc438e] Added Line 1
 1 file changed, 1 insertion(+)
	  
jegan@tektutor.org:~/git-demo$ echo "Line 2" >> file1.txt 
jegan@tektutor.org:~/git-demo$ git commit -am "Added Line 2"
warning: LF will be replaced by CRLF in file1.txt.
The file will have its original line endings in your working directory
[main 9c7b898] Added Line 2
 1 file changed, 1 insertion(+)
	  
jegan@tektutor.org:~/git-demo$ echo "Line 3" >> file1.txt 
jegan@tektutor.org:~/git-demo$ git commit -am "Added Line 3"
warning: LF will be replaced by CRLF in file1.txt.
The file will have its original line endings in your working directory
[main b9ea26d] Added Line 3
 1 file changed, 1 insertion(+)
	  
jegan@tektutor.org:~/git-demo$ echo "Line 4" >> file1.txt 
jegan@tektutor.org:~/git-demo$ git commit -am "Added Line 4"
warning: LF will be replaced by CRLF in file1.txt.
The file will have its original line endings in your working directory
[main eb93559] Added Line 4
 1 file changed, 1 insertion(+)
	  
jegan@tektutor.org:~/git-demo$ echo "Line 5" >> file1.txt 
jegan@tektutor.org:~/git-demo$ git commit -am "Added Line 5"
warning: LF will be replaced by CRLF in file1.txt.
The file will have its original line endings in your working directory
[main 7a6fe75] Added Line 5
 1 file changed, 1 insertion(+)
	  
jegan@tektutor.org:~/git-demo$ cat file1.txt 
Line 1
Line 2
Line 3
Line 4
Line 5
	  
jegan@tektutor.org:~/git-demo$ git status
On branch main
nothing to commit, working tree clean
	  
jegan@tektutor.org:~/git-demo$ git log --oneline
7a6fe75 (HEAD -> main) Added Line 5
eb93559 Added Line 4
b9ea26d Added Line 3
9c7b898 Added Line 2
7dc438e Added Line 1
20583cb Initial commit.
	  
jegan@tektutor.org:~/git-demo$ git reset --hard eb93559
HEAD is now at eb93559 Added Line 4
jegan@tektutor.org:~/git-demo$ git status
On branch main
nothing to commit, working tree clean
	  
jegan@tektutor.org:~/git-demo$ git log --oneline
eb93559 (HEAD -> main) Added Line 4
b9ea26d Added Line 3
9c7b898 Added Line 2
7dc438e Added Line 1
20583cb Initial commit.
	  
jegan@tektutor.org:~/git-demo$ cat file1.txt 
Line 1
Line 2
Line 3
Line 4
</pre>


## ⛹️ Lab - Git merge - Fast Forward

Let's cleanup any existing repo 
```
cd ~/git-demo
rm -rf .git
rm *
```

Let's create a new main repo
```
git config --global init.defaultbranch main
git init
touch file1.txt
git add file1.txt
git commit -m "Initial commit."

echo "Line 1" > file1.txt
git commit -am "Added Line 1"

echo "Line 2" > file1.txt
git commit -am "Added Line 2"

echo "Line 3" > file1.txt
git commit -am "Added Line 3"

git status
git log --oneline
```

We can create the dev-1.0 branch from main branch
```
git branch
git checkout main  # This will switch to main branch
git checkout -b dev-1.0 # This will create a new branch dev-1.0
git log --oneline
```

We can make some changes in the dev-1.0
```
echo "Line 4" >> file1.txt
git commit -am "Added Line 4"

echo "Line 5" >> file1.txt
git commit -am "Added Line 5"

git status
git log --oneline
```

Let's switch to main branch and see the content of file1.txt
```
git checkout main
cat file1.txt
git log --oneline
```

Let's merge the changes done in dev-1.0 branch to the main branch
```
git merge dev-1.0
git log --oneline
cat file1.txt
```

