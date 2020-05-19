### Git&Github操作指南：

1.为什么要学git与github

调试

重构

迭代

参考其他同学代码

Git&Github操作：

#### 2.什么是版本控制

分布式版本控制软件

之前版本与现在版本就是版本控制

对各个代码文件进行控制，git是当前最流行的版本控制软件

3.Git安装、初始化仓库并做简单的配置

参考链接：

https://git-scm.com/downloads

安装完成后查看git版本：

git  --version

新建一个目录：

mkdir learn_git

cd  learn_git

ls -al

git init  //会多了一个.git

ls -al    //会多了一个.**git**

git config  --global user.name   "yeweiwei"

git config  --global user.email    "hunanmen@126.com"

git config --global --list

4.完成一个简单的git操作流程

clear

git status   //查看git状态

$ pwd
/c/Users/yeweiwei/learn_git

去C:\Users\yeweiwei\learn_git添加一个文件

learn_git.html文件

git status   //查看

git  add learn_git.html

git status   //查看

git commit -m "create learn_git.html file"

步骤：

工作区（已经修改）       git add         暂存区 （已经暂存）         git commit -a              Git仓库（已经提交）

working directory                               staging area                                                                   repository



=先 去C:\Users\yeweiwei\learn_git添加一个文件，查看变化过程       

![1589889994023](算法学习.assets/1589889994023.png)

#### 在learn_git.html中添加内容

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">     <!--引入bootstrap-->
    <link rel="stylesheet" href="../css/bootstrap.min.css" rel="stylesheet">
    <title>Spring Boot开发入门</title>
</head>
<body>
<#-- FreeMarker注释方式1 -->
<h1>${title!}</h1>
<!-- FreeMarker注释方式2-->
<h3> 时间戳转换成日期格式：${date?number_to_datetime}<br>
    日期格式：${datetime?date}<br> 日期+时间格式：${datetime?datetime}<br></h3> <h5>     <#if user??>     姓名：${user.name!}
        <br>     年龄：${user.age!}<br>     地址：${user.address!}<br>     </#if> <br></h5>
<script src="../js/bootstrap.min.js" rel="stylesheet"></script> <!-- jQuery (Bootstrap 的 JavaScript 插件需要引入 jQuery) -->
<script src="../js/jquery.min.js" rel="stylesheet"></script>
</body>
</html>
```

git status

git add .    //把所有修改的文件放在暂存区

git commit -m  “web1.0”

6.将本地仓库同步到远程GitHub仓库

通过git管理源代码的管理平台

hunanmen@126.com       Kevin168816!     <<https://github.com/>>

新建一个仓库

![1589891393691](算法学习.assets/1589891393691.png)

用ssh协议，不要用https协议，不然每次都要输入用户名密码

![1589891503172](算法学习.assets/1589891503172.png)

执行命令必须要在参考git  init的路径下C:\Users\yeweiwei\learn_git

```
git remote add origin git@github.com:hunanmentest/learn_git.git
git push -u origin master  //要配置好了ssh相关信息才可以执行
```

yeweiwei@AT4341-DLP1 MINGW64 ~/learn_git (master)
$ git remote add origin git@github.com:hunanmentest/learn_git.git

yeweiwei@AT4341-DLP1 MINGW64 ~/learn_git (master)
$ git remote
origin

git push -u origin master  //要配置好了ssh相关信息才可以执行

ssh-keygen -t rsa   -C   “hunanmen@126.com”回车   回车

yeweiwei@AT4341-DLP1 MINGW64 ~/learn_git (master)
$ ssh-keygen -t rsa   -C   “hunanmen@126.com”   
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/yeweiwei/.ssh/id_rsa): //回车
Enter passphrase (empty for no passphrase): //回车
Enter same passphrase again: //回车
Your identification has been saved in /c/Users/yeweiwei/.ssh/id_rsa.
Your public key has been saved in /c/Users/yeweiwei/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:ivZ298b0ao9ZjpcsQIi1iknd8seC6nQSHbpwbdprhTM “hunanmen@126.com”
The key's randomart image is:
+---[RSA 2048]----+
|                 |
|        .        |
|     ..+ o       |
|    .++.+ .      |
|  ..+o+*So       |
|   ooBE.+ + .    |
|    B.++ o + o.. |
|   o.+o.. . =*=  |
|   ..oo. . +*=o  |
+----[SHA256]-----+

去/c/Users/yeweiwei/.ssh/这个路径看看

cd    /c/Users/yeweiwei/.ssh/

ls

yeweiwei@AT4341-DLP1 MINGW64 ~/learn_git (master)
$ cd /c/Users/yeweiwei/.ssh/

yeweiwei@AT4341-DLP1 MINGW64 ~/.ssh
$ ll
total 9
-rw-r--r-- 1 yeweiwei 1049089 1831 5月  19 20:36 id_rsa     //私钥
-rw-r--r-- 1 yeweiwei 1049089  404 5月  19 20:36 id_rsa.pub   //公钥
-rw-r--r-- 1 yeweiwei 1049089  712 8月   6  2019 known_hosts

公钥：

ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCw5WUKA6N9nJJcmO4VrmAnv8lywMOg8E6kUthZXOg/PWLR4i9uHrpyZYDKaQvD5PvKZkLEozOT+qeMJpmhOgbxo9LHJTs/gd1xSsufkIKVAXdegqWNq8/SymXmZy+gX2XPnJEdgkptF6nSoO76JZ6oLEMbgsLSnFHj7QG65zgCLpYMQ8VJzMlbamItZM/SHnSW8UqZ4++GNxoCButxW8YvwoEqruWGFpOzSBPAY28TMkOck02UGJakheOqeadP2z7ZhA4Ja9YDed7TGeYRQnk8me7KxhoGQzL4G1DzOiEtuixiXlrrH7nxwhkcLUtCnIAooUXaC/AyGCCVfRkH0nnz “hunanmen@126.com”

<https://github.com/>>登录后点击settings，

![1589892043621](算法学习.assets/1589892043621.png)

![1589892128788](算法学习.assets/1589892128788.png)title可以不用写，输入公钥后点击Add SSH KEY

测试链接是否成功ssh -T git@github.com

yeweiwei@AT4341-DLP1 MINGW64 ~/.ssh
$ ssh -T git@github.com
The authenticity of host 'github.com (13.229.188.59)' can't be established.
RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'github.com,13.229.188.59' (RSA) to the list of known hosts.
Hi hunanmentest! You've successfully authenticated, but GitHub does not provide shell access.

回到git仓库命令界面执行命令：

yeweiwei@AT4341-DLP1 MINGW64 ~
$ cd learn_git/        //必须回到git  init的仓库，否则执行有问题

yeweiwei@AT4341-DLP1 MINGW64 ~/learn_git (master)
$ git push -u origin master
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 8 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (6/6), 939 bytes | 469.00 KiB/s, done.
Total 6 (delta 0), reused 0 (delta 0)
To github.com:hunanmentest/learn_git.git
 * [new branch]      master -> master
Branch 'master' set up to track remote branch 'master' from 'origin'.

yeweiwei@AT4341-DLP1 MINGW64 ~/learn_git (master)

git push -u origin master  //要配置好了ssh相关信息才可以执行

7.在修改learn_git.html,

yeweiwei@AT4341-DLP1 MINGW64 ~/learn_git (master)
$ git add learn_git.html           //添加到本地仓库

yeweiwei@AT4341-DLP1 MINGW64 ~/learn_git (master)
$ git commit -m "web 3.0"       //commit提交
[master 5863e6e] web 3.0
 1 file changed, 1 insertion(+), 4 deletions(-)

yeweiwei@AT4341-DLP1 MINGW64 ~/learn_git (master)
$ git push
Warning: Permanently added the RSA host key for IP address '13.250.177.223' to the list of known hosts.
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 283 bytes | 283.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:hunanmentest/learn_git.git
   e86dd96..5863e6e  master -> master



7.打开即刻训练营的代码地址

作业提交平台：GitHub 
仓库代码链接：https://github.com/algorithm009-class02 

原来参考                                                              你的仓库

Repo             ---------fork----彼此独立----------------》Repo

![1589893295743](算法学习.assets/1589893295743.png)

yeweiwei@AT4341-DLP1 MINGW64 ~/learn_git (master)
$ pwd
/c/Users/yeweiwei/learn_git                     //一定要在这个目录

yeweiwei@AT4341-DLP1 MINGW64 ~/learn_git (master)
$ git clone git@github.com:hunanmentest/algorithm009-class02.git     //代码clone到本地
Cloning into 'algorithm009-class02'...
Warning: Permanently added the RSA host key for IP address '52.74.223.119' to the list of known hosts.
remote: Enumerating objects: 18, done.
remote: Counting objects: 100% (18/18), done.
remote: Compressing objects: 100% (11/11), done.
remote: Total 18 (delta 2), reused 2 (delta 0), pack-reused 0
Receiving objects: 100% (18/18), 5.09 KiB | 1.27 MiB/s, done.
Resolving deltas: 100% (2/2), done.