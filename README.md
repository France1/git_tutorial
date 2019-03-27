# git_tutorial
Git tutorial based on Atlassian "Getting Started" [guide](https://it.atlassian.com/git/tutorials/setting-up-a-repository)

### Create repository
Create a new Git repository locally
```
mkdir git_tutorial
cd git_tutorial/
git init
```

Create a text file with some content
```
echo "test content for git tutorial" >> CommitTest.txt
```

Add and commit the new file locally
```
git add CommitTest.txt 
git commit -m "added CommitTest.txt to the repo"
```

Add a new remote repository called `origin` to the local Git repository
```
git remote add origin https://github.com/France1/git_tutorial.git
```

Push changes to remote and check that repo is up to date
```
git push -u origin master
git status
```
### Add and remove changes
Modify file and commit changes *locally*:
```
echo "test content to be removed" >> CommitTest.txt
git commit -am 'added changes to be removed'
```

Navigate history of commit and remove last changes by returning to the previous pointer `3730f63` (preferred "undo" method for local commit)
```
git log --oneline
git status
git reset --hard 3730f63
```

Modify file and push changes to *remote*: 
```
echo "test content to be removed" >> CommitTest.txt
git commit -am 'added changes to be removed'
git push
```

Remove last changes (preferred "undo" method for public commit), then verify history of commit:
```
git revert HEAD
git log --oneline
```
### Create and merge branches
Create a branch called `branch-experiment`, list all branches, then switch to the new branch:
```
branch branch-experiment
git branch
git checkout branch-experiment
```
Modify file within branch 
```
echo "test content added in branch" >> CommitTest.txt
git commit -am 'added changes in branch-experiment'
```
Push change to remote, then verify that the new branch exists in [remote](https://github.com/France1/git_tutorial)
```
git push --set-upstream origin branch-experiment
```
Switch to the receiving branch, merge `branch-experiment`, then verify `CommitTest.txt` is modified:
```
git checkout master
git merge branch-experiment
cat CommitTest.txt
```
Delete `branch-experiment`
```
git branch -d branch-experiment
```



