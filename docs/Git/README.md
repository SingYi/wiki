# Git
## 批量删除本地分支
- 删除当前分支外的所有分支
```
git branch | xargs git branch -d
```
- 删除分支名包含指定字符的分支
```
git branch | grep 'upstream*' | xargs git branch -d
```