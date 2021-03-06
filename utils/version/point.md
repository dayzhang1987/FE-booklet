# Git要点

　　本文将总结Git要点

&nbsp;

### 版本管理工具

【作用】

　　1、备份文件

　　2、记录历史

　　3、回到过去

　　4、对比差异

【分类】

　　1、手动版本控制(又叫人肉VCS)

　　2、LVCS 本地

　　3、CVCS 集中式(如SVN)

　　4、DVCS 分布式(如Git)

&nbsp;

### Git优缺点

【优点】

　　1、 快速、灵活。每个开发中本地都有全量仓库，提交到本地非常快

　　2、 离线工作，能避免单点故障。即便远端代码服务器崩溃，开发者也能继续工作，无需等待修复。一定程度也是一种安全备份

　　3、 任意两个开发者之间可以很容易的合并和解决冲突

【缺点】

　　1、 学习曲线稍微陡峭一些，要多花一点学习时间

　　2、 代码保密性差，不便于权限控制。一旦开发者把整个库克隆下来就可以完全公开所有代码和版本信息，权限控制需要另外一套系统来保证

&nbsp;

### 三种状态

　　1、已提交(commited)：该文件已经被安全地保存在本地数据库中了

　　2、已修改(modified)：表示修改了某个文件，但还没有提交保存

　　3、已暂存(staged)：把已修改的文件放在下次提交时要保存的清单中

![git_point1](https://pic.xiaohuochai.site/blog/git_point1.png)

&nbsp;

### 基本操作

　　1、获取仓库

　　使用git init创建仓库或使用git clone获取远程仓库

　　2、创建开发分支

　　使用git checkout -b dev创建dev分支

　　3、开发程序，修改代码文件

　　4、跟踪文件并提交到本地仓库

　　使用git add .跟踪文件，使用git commit -m 'xxx'提交到本地仓库

　　5、远程操作

　　使用git remote add origin git://xxxxx&nbsp;添加元素仓库，使用git push origin dev&nbsp;将本地的dev分支推送到远程的dev分支

　　[注意1]git push origin dev是git push origin dev:dev的缩写，如果省略:dev，默认地，远程服务器使用和本地相同的分支

　　[注意2]远程库的默认名称为origin，当然也可以起名为其他名称

　　6、当前功能开发完毕后，到master分支处理

　　使用git checkout master切换到master分支后，使用git pull origin master，获取master分支上的更新。使用git log -p来查看更新。处理后，使用git merge dev将dev分支合并到master分支上，然后使用git push origin master将本地master分支推送到远程master分支上

&nbsp;

### 注意事项

　　1、Unix的哲学是&ldquo;没有消息就是好消息&rdquo;，git也类似。当没有任何返回时，表示操作成功

　　2、&nbsp;版本控制系统只能跟踪文本文件的改动，比如TXT文件，网页，所有的程序代码等等。图片、视频这些二进制文件，虽然也能由版本控制系统管理，但没法跟踪文件的变化，只能把二进制文件每次改动串起来，也就是只知道图片从100KB改成了120KB，但到底改了啥，版本控制系统不知道，也没法知道

　　Microsoft的Word格式是二进制格式，因此，版本控制系统是没法跟踪Word文件的改动

　　3、使用Windows的同学千万不要使用Windows自带的记事本编辑任何文本文件。原因是Microsoft开发记事本的团队使用了一个非常弱智的行为来保存UTF-8编码的文件，他们自作聪明地在每个文件开头添加了0xefbbbf(十六进制)的字符，会让你遇到很多不可思议的问题

　　4、git commit -am可以写成git commit -a -m，但不能写成git commit -m -a

　　5、切换分支之前，最好要保证工作区干净

　　6、rebase和merge的区别如下

　　merge会根据两个分支的共同祖先和两个分支的更新提交进行一个三方合并，并保存这两个分支

　　rebase并没有进行合并操作，只是提取了当前分支的修改，将其复制在了目标分支的最新提交后面，并删除了当前分支

　　rebase可以产生一个更为整洁的提交历史，但若使用rebase操作，一定要确保没有其他人会使用被删除的分支

