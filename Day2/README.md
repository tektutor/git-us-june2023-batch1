# Day 2

## ⛹️‍♂️ Lab - For windows participants
```
git config --global core.autocrlf true
```


## ⛹️‍♂️ Lab - Renaming a branch

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

## ⛹️‍♂️ Lab - Git logs
```
cd ~
mkdir git-demo
cd git-demo

git config --global user.name "Jeganathan Swaminathan"
git config --global user.email "jegan@tektutor.org"
git config --global init.defaultbranch main
git config --global core.editor vim

git init
touch cars.txt
git status
git add cars.txt
git commit -m "Initial commit."

echo "BMW X1" > cars.txt
git status
git commit -a -m "Added BMW X1 in cars.txt"

echo "Audi A6" > cars.txt
git status
git commit -a -m "Added Audi A6 in cars.txt"

echo "Audi Q7" > cars.txt
git status
git commit -a -m "Added Audi Q7 in cars.txt"

echo "Skoda Kodiaq" > cars.txt
git status
git commit -a -m "Added Kodiaq in cars.txt"

git log # Listing detailed log - commit history
git log --oneline
```

## ⛹️‍♂️ Lab - Some additional options you may find it interesting in logs
```
git log -p -2
git log --stat
git log --pretty=oneline
git log --pretty=short
git log --pretty=full
git log --pretty=fuller
git log --pretty=format:"%h - %an %ar %s"
git log --pretty=format:"%h %s" --graph
git log --since=2.weeks
git log --oneline --decorate

git log --pretty="%h - %s" --author="Jeganathan Swaminathan" --since="2023-06-18" --before="2023-06-22"
```

The possible specifiers
<pre>
%H - Full lenght of commit id
%h - shorter commit id
%an - author name
%ae - author email
%s - commit message
</pre>

## ⛹️‍♂️ Lab - Git tags

Git supports two types of tags
1. Lightweight tag - Git doesn't require creating a separated for lightweight tags
2. Annotated tag - Git creates an object entry under .git/object folder to store detailed tag details. This is recommended

#### Creating a lightweight tag
```
git log --oneline
git tag v0.1 19bd207 #Creates a lightweight tag
git tag v0.2 f4ea00b 
git tag v0.3 31c912e
git tag v0.4 6e73019
git tag v0.5 5044009

git log --oneline
```

Expected output
<pre>
jegan@tektutor.org:~/git-demo$ git tag v0.1 19bd207
jegan@tektutor.org:~/git-demo$ git tag v0.2 f4ea00b
jegan@tektutor.org:~/git-demo$ git tag v0.3 31c912e
jegan@tektutor.org:~/git-demo$ git tag v0.4 6e73019
jegan@tektutor.org:~/git-demo$ git tag v0.5 5044009
jegan@tektutor.org:~/git-demo$ git log --oneline
5044009 (HEAD -> main, tag: v0.5) Added BMW X4
6e73019 (tag: v0.4) Added BMW X3
31c912e (tag: v0.3) Added BMW X2
f4ea00b (tag: v0.2) Added BMW X1
19bd207 (tag: v0.1) Initial commit.
</pre>

#### Listing tags
```
git log --oneline
git tag
```

Expected output
<pre> 
jegan@tektutor.org:~/git-demo$ git tag
v0.1
v0.2
v0.3
v0.4
v0.5
</pre>

#### Deleting tags
```
git tag -d v0.1
git tag -d v0.2
git tag -d v0.3
git tag -d v0.4
git tag -d v0.5
 
git tag
git log --oneline
```

Expected output
<pre>
jegan@tektutor.org:~/git-demo$ git tag -d v0.1
Deleted tag 'v0.1' (was 19bd207)
jegan@tektutor.org:~/git-demo$ git tag -d v0.2
Deleted tag 'v0.2' (was f4ea00b)
jegan@tektutor.org:~/git-demo$ git tag -d v0.3
Deleted tag 'v0.3' (was 31c912e)
jegan@tektutor.org:~/git-demo$ git tag -d v0.4
Deleted tag 'v0.4' (was 6e73019)
jegan@tektutor.org:~/git-demo$ git tag -d v0.5
Deleted tag 'v0.5' (was 5044009)
 
jegan@tektutor.org:~/git-demo$ git tag
 
jegan@tektutor.org:~/git-demo$ git log --oneline
5044009 (HEAD -> main) Added BMW X4
6e73019 Added BMW X3
31c912e Added BMW X2
f4ea00b Added BMW X1
19bd207 Initial commit. 
</pre>

#### Creating annotated tags and listing them
```
git log --oneline
git tag -a v0.1 19bd207 -m "Dev release v0.1"
git tag -a v0.2 f4ea00b -m "Dev release v0.2"
git tag -a v0.3 31c912e -m "Dev release v0.3"
git tag -a v0.4 6e73019 -m "Dev release v0.4"
git tag -a v0.5 5044009 -m "Dev release v0.5"

git tag # This will list the tags
git log --oneline  # This will list a single line log along with tags(if any)
```

Expected output
<pre>
 
jegan@tektutor.org:~/git-demo$ git tag -a v0.1 19bd207 -m "Dev release v0.1"
jegan@tektutor.org:~/git-demo$ git tag -a v0.2 f4ea00b -m "Dev release v0.2"
jegan@tektutor.org:~/git-demo$ git tag -a v0.3 31c912e -m "Dev release v0.3"
jegan@tektutor.org:~/git-demo$ git tag -a v0.4 6e73019 -m "Dev release v0.4"
jegan@tektutor.org:~/git-demo$ git tag -a v0.5 5044009 -m "Dev release v0.5"
 
jegan@tektutor.org:~/git-demo$ git tag
v0.1
v0.2
v0.3
v0.4
v0.5
 
jegan@tektutor.org:~/git-demo$ git log --oneline
5044009 (HEAD -> main, tag: v0.5) Added BMW X4
6e73019 (tag: v0.4) Added BMW X3
31c912e (tag: v0.3) Added BMW X2
f4ea00b (tag: v0.2) Added BMW X1
19bd207 (tag: v0.1) Initial commit.
</pre>


#### Deleting the tags
```
git tag -d v0.1
git tag -d v0.2 v0.3 v0.4 v0.5

git tag
git log --oneline
```

Expected output
<pre>
jegan@tektutor.org:~/git-demo$ git tag -d v0.1
Deleted tag 'v0.1' (was 952ac8c)
 
jegan@tektutor.org:~/git-demo$ git tag -d v0.2 v0.3 v0.4 v0.5
Deleted tag 'v0.2' (was 291d775)
Deleted tag 'v0.3' (was 5265ba9)
Deleted tag 'v0.4' (was 2002c00)
Deleted tag 'v0.5' (was 7397bdc)
</pre>

## ⛹️‍♂️ Lab - Undo a commit from git repo
```
git log --oneline
git restore --source 6e73019 cars.txt # Any commit that comes after this commit with id 6e73019 will be deleted
git status

git commit -am "Removed the commit 5044009 with tag v0.5"
```

Expected output
<pre>
jegan@tektutor.org:~/git-demo$ git log --oneline
5044009 (HEAD -> main, tag: v0.5) Added BMW X4
6e73019 (tag: v0.4) Added BMW X3
31c912e (tag: v0.3) Added BMW X2
f4ea00b (tag: v0.2) Added BMW X1
19bd207 (tag: v0.1) Initial commit.
jegan@tektutor.org:~/git-demo$ git restore --source 6e73019 cars.txt
jegan@tektutor.org:~/git-demo$ git status
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   cars.txt

no changes added to commit (use "git add" and/or "git commit -a")
jegan@tektutor.org:~/git-demo$ vim cars.txt 
jegan@tektutor.org:~/git-demo$ git commit -am "Undone the commit with tag v0.5 commit id 5044009"
[main 642cc02] Undone the commit with tag v0.5 commit id 5044009
 1 file changed, 1 deletion(-)
   
jegan@tektutor.org:~/git-demo$ git log --oneline
642cc02 (HEAD -> main) Undone the commit with tag v0.5 commit id 5044009
5044009 (tag: v0.5) Added BMW X4
6e73019 (tag: v0.4) Added BMW X3
31c912e (tag: v0.3) Added BMW X2
f4ea00b (tag: v0.2) Added BMW X1
19bd207 (tag: v0.1) Initial commit.
jegan@tektutor.org:~/git-demo$ vim cars.txt  
</pre>
