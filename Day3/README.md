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

touch file1.txt file2.txt file3.txt
git add *
git commit -m "Initial commit."

echo "Line 1" > file1.txt
git commit -am "Added Line 1 in file1.txt"

echo "Line 1" > file2.txt
git commit -am "Added Line 1 in file2.txt"

echo "Line 2" > file2.txt
git commit -am "Added Line 2 in file2.txt"

echo "Line 1" > file3.txt
git commit -am "Added Line 1 in file3.txt"

echo "Line 2" > file3.txt
git commit -am "Added Line 2 in file3.txt"

echo "Line 3" > file3.txt
git commit -am "Added Line 3 in file3.txt"

git log --oneline
```


<pre>
</pre>
