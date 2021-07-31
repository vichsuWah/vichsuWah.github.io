# Git Commands


<!--more-->
## git init
{{< admonition note "This command creates an empty Git repository." >}}

* 初始化 git
```bash
# cd the target folder
git init
```
* 也可以指定資料夾使用
```bash
git init <directory>
```
{{< /admonition >}}
- - -
- - -
- - -
## git clone
{{< admonition note "Clone a repository into a new directory" >}}

* 複製一個Repository(倉儲)
```bash
# ssh
git clone git@github.com:test/test.git

# https
git clone https://github.com/test/test.git
```

* 加速 (只取最近1筆的history commit)
```bash
git clone git@github.com:test/test.git --depth 1
# equal to
git clone git@github.com:test/test.git --depth 1 --single-branch
# 使用 --depth 相當於是 --single-branch，會無法切換 remote branch

# [solution]: --no-signle-branch
# 每個 branch 的最新一筆 history commit 都會取下來
git clone git@github.com:test/test.git --depth 1 --no-single-branch
```
{{< /admonition >}}
- - -
- - -
- - -
## git add
{{< admonition note "Add file contents to the index" >}}
* 將檔案放到Stage(暫存區)
```bash
git add <filename>

git add .     # stages new files and modifications, without deletions
git add -u    # stages modifications and deletions, without new files (-u == --update)

git add -A    # stages both additions and removals (-A == --all)
# in detail, 'git add -A' is equivalent to 'git add .; git add -u'
```
* 若有需要取消 add
```bash
git reset HEAD <file>
```
* 新增檔案部分的內容
```bash
# Interactively choose hunks of patch between the index and the work tree and add them to the index.
git add -p    # equal to `git add --patch`
Stage this hunk [y,n,q,a,d,/,s,e,?]
```
> y - stage this hunk \
> n - do not stage this hunk\
> q - quit; do not stage this hunk or any of the remaining ones\
> a - stage this hunk and all later hunks in the file\
> d - do not stage this hunk or any of the later hunks in the file\
> g - select a hunk to go to\
> / - search for a hunk matching the given regex\
> j - leave this hunk undecided, see next undecided hunk\
> J - leave this hunk undecided, see next hunk\
> k - leave this hunk undecided, see previous undecided hunk\
> K - leave this hunk undecided, see previous hunk\
> s - split the current hunk into smaller hunks\
> e - manually edit the current hunk\
> ? - print help

#### 通常只會用到s, y, n
* y 就是 yes，要 add 這個 hunk
* n 就是 no，不要 add 這個 hunk
* s 把目前的 hunk 再切成更小的 hunk

[more detail about ```git add -p``` can click this url](https://www.cnblogs.com/zqb-all/p/13020293.html)
{{< /admonition >}}
- - -
- - -
- - -
## git commit
{{< admonition note "Record changes to the repository" >}}
* 記錄Stage(暫存區)的狀態到Repository(倉儲)
```bash
git commit -m "savepoint"
```
* 若需要修改最後一次的 commit 
```bash
git commit --amend
```
{{< /admonition >}}
- - -
- - -
- - -
## git log
{{< admonition note "Show commit logs" >}}
* 顯示版本控制的歷史記錄(commit record)
* 小寫q退出
* 簡化版面 
```bash
git log --pretty=oneline
```
```bash
git log --graph --pretty=format:"%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset" --abbrev-commit --date=relative
```
{{< /admonition >}}
- - -
- - -
- - -
## git reset
{{< admonition note "Reset current HEAD to the specified state" >}}
* 回退版本
* reset 可以理解為 go to
* 三個參數`--mixed`, `--soft`, `--hard`, 預設為`--mixed`
```bash
# 前往兩個 Commit 之前的狀態
git reset HEAD~2
```
[more detail about ```git reset``` can click this url](https://gitbook.tw/chapters/using-git/reset-commit.html)
{{< /admonition >}}
- - -
- - -
- - -
## git checkout
{{< admonition note "Switch branches or restore working tree files" >}}
* 用於切換分支或者恢復工作樹的檔案
```bash
# switch branches
git checkout branchName

# restore working tree files
git checkout  -- <filename>    # 檔案會回到最近一次 git commit 或 git add 時的狀態。
```
{{< /admonition >}}
- - -
- - -
- - -
## git push
{{< admonition note "Update remote refs along with associated objects" >}}
*
```bash

```
{{< /admonition >}}
- - -
- - -
- - -
## git pull
{{< admonition note "Fetch from and integrate with another repository or a local branch" >}}
*
```bash

```
{{< /admonition >}}
- - -
- - -
- - -

