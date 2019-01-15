# 用git来记笔记
```
$ git remote -v //用来显示已有的远程仓库，并表示出拥有的权限
origin	https://github.com/schacon/ticgit (fetch)
origin	https://github.com/schacon/ticgit (push)
$ git remote add pb https://github.com/paulboone/ticgit //可以添加新的仓库 并用pb来代替
$ git remote -v 
origin	https://github.com/schacon/ticgit (fetch)
origin 	https://github.com/schacon/ticgit (push)
pb	https://github.com/paulboone/ticgit (fetch)
pb	https://github.com/paulboone/ticgit (push)

$ git fetch origin //会拉取到本地的origin/master分支
$ git pull origin //拉取并直接合并到本地分支中，这个比较方便
// git clone 会自动添加远程仓库为origin
$ git push origin master // 将本地新添加的内容同步到远程仓库，注意是先写仓库名再写分支名

