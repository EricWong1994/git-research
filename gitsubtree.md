报错
➜  git-research git:(master) git subtree add --prefix=/child git@github.com:EricWong1994/git-research-child.git master
fatal: 有歧义的参数 'HEAD'：未知的版本或路径不存在于工作区中。
使用 '--' 来分隔版本和路径，例如：
'git <命令> [<版本>...] -- [<文件>...]'
Working tree has modifications.  Cannot add.
原因：没有与远程库建立联系


这条命令看起来没有语法错误，它是将远程仓库 `git@github.com:EricWong1994/git-research-child.git` 的 `master` 分支（默认分支）添加为本地仓库的子树，并指定子树的路径为 `/child`。

如果在执行该命令时出现错误，可能是因为以下原因：

- 没有在本地仓库的根目录下执行该命令。
- 在执行 `git subtree add` 命令之前没有先跑一遍 `git remote add` 这样的命令，提前把远程仓库添加到本地仓库的 remote 列表中。
- 在执行 `git subtree add` 命令之前没有先拉取远程仓库的代码。


### 答
`git remote add` 是 Git 的一个命令，用于将一个远程仓库添加到本地仓库中。

一般情况下，我们在使用 Git 的时候需要与远程仓库进行交互，如从远程仓库获取代码、向远程仓库推送代码等。在这些情况下，我们需要先将远程仓库添加到本地仓库中，然后才能对其进行操作。

比如说，你要将远程仓库的名为 `origin` 的仓库添加到本地仓库中，可以使用如下的 `git remote add` 命令：

```
git remote add origin git@github.com:yourusername/your-repo.git
```

这条命令会将远程仓库的地址 `git@github.com:yourusername/your-repo.git` 添加到本地仓库的 remote 列表中，并将这个远程仓库命名为 `origin`。这样，你就可以使用类似 `git pull origin master`、`git push origin main` 等命令与远程仓库进行交互了。




git subtree pull --prefix=child git@github.com:EricWong1994/git-research-child.git master

git remote add child git@github.com:EricWong1994/git-research-child.git

git subtree pull --prefix=child child master

git subtree pull --prefix=child child master --squash