# 本地操作

### 提交
```git
git add file
git commit -m 'message'
```
### 分支
```git
git branch <branch>

# delete branch
git branch -d <branch> 

# move HEAD to branch
git checkout <branch>

```

### 远程分支
```git
git fetch origin
git pull/push <remote> <local-branch>:<remote-branch>

# create branch from remote and track it
git checkout -b <branch> [<remote>/<branch>]

# use the same branch name
git checkout --track <remote>/<branch>

# manual set up-stream
git branch -u <remote>/<branch>

# delete remote branch
git push --delete <remote> <branch>
```

# 远程操作
```git
git clone [-b <branch-name>] [-o <remote-name>] repository-address [<directory>]
```

### 历史记录
```git
# reset 1st step, move branch and HEAD
git reset --soft <commit>

# rest 2nd step, move index
git reset --mixed <commit>

# rest 3rd step, clear workspace
git reset --hard <commit>

# tips, action below will not change HEAD, only change index
git reset <commit> -- <file>

# checkout, not change HEAD, only change index?!
git checkout <commit> <file>

# force overwrite the history on the server
git push --force

# revert, m 1 is the first parent node
git revert -m 1 HEAD

```

### 高级命令
```git
# trace file log
git blame -L <start>,<end>  <file>

```