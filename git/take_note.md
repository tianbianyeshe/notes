# 用git来记笔记
```bash
$ git add * //将新建的文件add到追踪中，可以用ignore文件进行忽略指定文件
$ git status -s //查看文件变化与状态
$ git commit -a -m "tags" //-a可以快捷的添加add过的文件，省略每次修改
都要add一遍的麻烦，-m可以直接将tag附到命令后面
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

```
