# Day 3

## Undo changes using reset

Git reset supports two modes
1. soft
2. hard

Soft reset will undo the changes and the changes are added to the staging. Hence, we get a chance to make further changes before we could commit.  We need to keep in mind that reset command will modify the commit history.

Hard reset will undo the changes and straight will commit the changes by modifying the commit history without any further warning.


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
