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

## Git logs
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

## Git tags

Git supports two types of tags
1. Lightweight tag - Git doesn't require creating a separated for lightweight tags
2. Annotated tag - recommended - 


