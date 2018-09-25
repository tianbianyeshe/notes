# [笔记Docker--从入门到实践](https://yeasy.gitbooks.io/docker_practice/)
## 基本指令
docker镜像导入导出
```
docker commit container_id image_name:tags

docker save -o path:/backup_name.tar image_name:tags
docker load -i path:/backup_name.tar
```
[获取镜像](https://yeasy.gitbooks.io/docker_practice/image/pull.html)
```
docker pull [选项] [Docker Registry 地址[:端口号]/] 仓库名[:tags]

eg: docker pull ubuntu:16.04
    docker pull python:3.6
```
[列出镜像](https://yeasy.gitbooks.io/docker_practice/image/list.html)
列出镜像、镜像体积、虚悬镜像、中间层镜像、列出部分镜像、特定格式显示
```
docker image ls

docker system df

docker image ls -f dangling=true
docker image prune

docker image ls -a

docker image ls ubuntu
docker image ls ubuntu:16.04
docker image ls -f since=mogo:3.2

docker image ls --format "table {{.ID}}\t{{.Repository}}\t{{.Tag}}"
```
[删除本地镜像](https://yeasy.gitbooks.io/docker_practice/image/rm.html)
```
#删除本地镜像
$ docker image rm [options] image[image...]

#用ID、镜像名、摘要删除镜像
#长短ID都可以，可以区分即可
$ docker image rm id
$ docker image rm centos
$ docker image ls --digests
$ docker image ls --digests
REPOSITORY                  TAG                 DIGEST                                                                    IMAGE ID            CREATED             SIZE
node                        slim                sha256:b4f0e0bdeb578043c1ea6862f0d40cc4afe32a4a582f3be235a3b164422be228   6e0c4c8e3913        3 weeks ago         214 MB

$ docker image rm node@sha256:b4f0e0bdeb578043c1ea6862f0d40cc4afe32a4a582f3be235a3b164422be228
Untagged: node@sha256:b4f0e0bdeb578043c1ea6862f0d40cc4afe32a4a582f3be235a3b164422be228

#用docker image ls命令来配合
$ docker image rm $(docker image ls -1 redis)

$ docker image rm $(docker image ls -q -f before=mogo:3.2)
```
[利用commit理解镜像构成](https://yeasy.gitbooks.io/docker_practice/image/commit.html)
```
$ docker exec -it container_name bash
$ docker commit [选项] <容器ID或容器名> [<仓库名>[:<标签>]]
```
