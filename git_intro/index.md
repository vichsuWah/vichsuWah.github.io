# Introduction Git

<!--more-->

{{< admonition >}}
A ***software system*** that records changes to a file or set of files over time so that you can recall specific versions later.\
Git can track the changes you make to files, so you have a record of what has been done, and you can revert to specific versions should you ever need to.
{{< /admonition >}}

&nbsp;
## 0. Before start

Github, Gitlab ?

***Cloud services*** for remote hosting of git repositories. In addition to hosting your code, the site helps manage software development projects with features like issue tracking, collaborating with other GitHub users, and hosting web pages.
- - -
- - -
- - -
## 1. Installation

* Official website : https://git-scm.com/

### Windows
1. Go to the offical website and download the .exe installation file for windows.\
<center>

![](https://i.imgur.com/9jNhnyK.png=500x)

</center>

2. Using scoop (Windows command line package management tool)
```bash
scoop install git
```
&nbsp;
### Linux (Ubuntu)
```bash
# (recommend) only includes main components with minimal dependencies
sudo apt-get install git 

# contains all sub-packages
sudo apt-get install git-all 
```
- - -
- - -
- - -
## Settings
The first thing you should do when you install Git is to set your user name and email address. This is important because every Git commit uses this information.
```bash
git config --global user.name "Username"
git config --global user.email Username@example.com
```
>若你有傳遞``` --global ```參數，只需要做這工作一次，此後在你安裝使用的系統上，不論 Git 做任何事都會採用此資訊。 若你想指定不同的名字或電子郵件給特定的專案，只需要在該專案目錄內執行此命令，並確定未加上``` --global ```參數。

Check settings
```bash
git config --list

[output]
user.name=vic
user.email=vic@example.com
color.status=auto
color.branch=auto
color.interactive=auto
color.diff=auto
...
[end output]
```
```bash
# or maybe use: git config <key>
git config --global user.name
vic

git config --global user.email
vic@example.com
```

> Git的設定會被記錄在gitconfig檔案中，這些參數被存放在下列三個地方
>> 1. 檔案 `/etc/gitconfig`：裡面包含該系統所有使用者和使用者倉儲的預設設定。 如果你傳遞``` --system ```參數給``` git config ```，它就會明確地從這個檔案讀取或寫入設定。
>
>> 2. 檔案 `~/.gitconfig`、`~/.config/git/config`：你的帳號專用的設定。只要你傳遞``` --global```，就會明確地讓 Git 從這個檔案讀取或寫入設定
>
>> 3. 任何倉儲中 Git 資料夾的 config 檔案（位於 `.git/config`）：這個倉儲的專用設定。
>
> 每個層級的設定皆覆蓋先前的設定，所以在`.git/config `的設定優先權高於在 `/etc/gitconfig`裡的設定。
> * 在 Windows 系統，Git 會在`$HOME`目錄（對大部份使用者來說是 `C:\Users\$USER`）內尋找`.gitconfig`

&nbsp;
### Help
If you ever need help while using Git, there are three equivalent ways to get the comprehensive manual page (manpage) help for any of the Git commands:
```bash
git help <verb>
git <verb> --help
man git-<verb>

# ex.
git help config
```

- - -
- - -
- - -
## Basics
### The lifecycle of the status of your files
Remember that each file in your working directory can be in one of two states: **tracked** or **untracked**. Tracked files are files that were in the last snapshot, as well as any newly staged files; they can be unmodified, modified, or staged. In short, **tracked files are files that Git knows about**.

Untracked files are everything else — any files in your working directory that were not in your last snapshot and are not in your staging area. When you first clone a repository, all of your files will be tracked and unmodified because Git just checked them out and you haven’t edited anything.

As you edit files, Git sees them as modified, because you’ve changed them since your last commit. As you work, you selectively stage these modified files and then commit all those staged changes, and the cycle repeats.

&nbsp;

<center>

![](https://i.imgur.com/lnpqvXX.png=2000x)

</center>

&nbsp;
### Initializing a Repository in an Existing Directory

> you can using the `git status` command to determine which files are in which state 

1.
    If you have a project directory that is currently not under version control and you want to start controlling it with Git, you first need to go to that project’s directory and type:
    ```bash
    git init
    ```
    > This creates a new subdirectory named ```.git``` that contains all of your necessary repository files

2.
    You can accomplish that with a few ` git add `commands that specify the files you want to track, followed by a ` git commit `:
    ```bash
    git add -A             # track all files inside the folder
    git commit -m "msg"    # save a checkpoint with a message "msg"
    ```
- - -
- - -
- - -
## Reference
https://git-scm.com/doc
