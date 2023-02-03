<a name="uRGdg"></a>
## 版本控制

---

版本控制（Resvision control）是一种在开发过程中用于管理我们对文件、目录或工程等内容的修改历史，方便查看更改历史记录，备份以便恢复以前的软件工程技术。
> 版本控制分类

1. 本地版本控制
2. 集中式版本控制
3. 分布式版本控制
> Git与SVN最主要的区别

SVN是集中式版本控制系统，版本库是集中放在中央服务器的，而工作的时候，用的都是自己的电脑，所以首先要从中央服务器得到最新的版本，然后工作，完成工作后，需要把推送到中央服务器。集中式版本控制是必须联网才能工作，对网络带宽要求较高。<br />Git是分布式版本控制系统，没有中央服务器，每个人的电脑就是一个完整版的版本库，工作的时候不需要联网，因为版本都在自己电脑上。协同方法是这样：比如说自己再电脑上改了文件A，其他人也在电脑上改了文件A，这时，你们两之间只需要把各自修改推送给对方，就可以相互见到对方的修改。Git可以直接看到更新了哪些代码和文件<br />**Git是目前世界上最先进的分布式版本控制系统。**

- Git Bash：Unix与Linux风格的命令行，使用最多，推荐最多
- Git CMD：Windows风格的命令行
- Git GUI：图形界面的Git，不建议初学者使用，尽量先熟悉常用的命令
<a name="V6xtH"></a>
## 基本的Linux命令学习

---

1. `cd`：改变目录
2. `cd..`：回退到上一个目录
3. `pwd`：显示当前所在的目录路径
4. `clear`：清屏
5. `ls`（`ll`）：都是列出当前目录中的所有文件，只不过ll列出的内容更为详细
6. `touch`：新建一个文件
7. `rm`：删除一个文件
8. `mkdir`：新建一个目录，就是新建一个文件夹
9. `rm -r`：删除一个文件夹【`rm -rf /` --切勿在Linux系统中使用，递归删除根目录】
10. `mv`：移动文件【mv 需要移动文件 目标文件夹】
11. `reset`：重新初始化终端/清屏
12. `history`：查看历史命令
13. `help`：帮助
14. `exit`：退出
15. `#`：注释 

Git 配置

- `git config -l`
- `git config --system --list` 查看系统配置
- `git config --global --list` 用户配置
- `git config --global user.name "Lee"` #名称
- `git config --global user.email Lee@qq.com` #邮箱

<a name="zM16o"></a>
## Git基本理论

---

- Workspace：工作区，就是平时存放项目代码的地方
- Index/Stage：暂存区，用于临时存放改动，事实上它只是一个文件夹，保存即将提交到文件列表信息
- Repository：仓库区(或本地仓库)，就是安全存放数据的位置，这里面有提交到所有版本的数据，其中HEAD指向最新版如仓库的版本
- Remote：远程仓库，托管代码的服务器，可以简单的认为是项目中的一台电脑用于远程数据交换

![image.png](https://cdn.nlark.com/yuque/0/2022/png/32917541/1664798966836-a44cc661-db6f-4cbf-b103-8eadabacf208.png#averageHue=%23ece3d5&clientId=u557a4893-68bd-4&from=paste&height=482&id=ub80b7425&name=image.png&originHeight=482&originWidth=495&originalType=binary&ratio=1&rotation=0&showTitle=false&size=80303&status=done&style=none&taskId=u9992cf9f-4db3-4373-9e9b-63e7ebc4a0a&title=&width=495)

<a name="l0U1p"></a>
## Git项目搭建

---

![image.png](https://cdn.nlark.com/yuque/0/2022/png/32917541/1664799691815-75c5f67f-8ebc-4031-8acd-e853dfd5f49c.png#averageHue=%23e0dfd9&clientId=u557a4893-68bd-4&from=paste&height=413&id=u83754b04&name=image.png&originHeight=413&originWidth=1321&originalType=binary&ratio=1&rotation=0&showTitle=false&size=142434&status=done&style=none&taskId=uc1ea0bf1-ce72-45d2-bdb7-950a62bc4d2&title=&width=1321)

<a name="UlmTR"></a>
### Git使用前配置

1. 配置提交人姓名：git config --global user.name “提交人姓名” # (对当前系统用户有效)
2. 配置提交人姓名：git config --global user.email  “提交人邮箱” # (对当前系统用户有效)<br />作用：识别开发人员，与github的账户无关
3. 查看git配置信息：git config --list

注意<br />1.如果要对配置信息进行修改，重复上述命令即可。<br />2. 配置只需要执行一次。
<a name="PSe8H"></a>
### 常用提交步骤
```bash
#设置用户签名
git config --global user.name 用户名
#设置用户邮箱
git config --global user.email 邮箱
#初始化本地库
git init
#在一个空的文件夹中创建一个项目目录，进入目录创建的目录中，
#右击使用git bash here控制台输入该命令，目录下自动生成 .git目录，该项目即成功被git托管
#新建的文件会被定义成为追踪文件，不会被git托管

#查看当前项目的状态
git status
#将文件添加至暂存区
git add hello.txt
#将文件移出暂存区，该文件变回未追踪文件
git rm --cached hello.txt
#将暂存区提交到本地库
git commit -m "first commit" hello.txt
#查看引用日志信息，查看提交过的版本
git reflog
#查看详情日志信息
git log
#版本穿梭
git reset --hard 指定版本码
#查看分支
git branch -v
#创建分支
git branch 分支名称
#切换分支
git checkout 分支名称

#在当前分支下修改文件，不会影响到其他分支的代码，切换回去看看

#合并分支
git merge 分支名

#创建远程库别名

#将远程库地址加到本地，用名称origin指代远程库
git remote add origin https://gitee.com/
#查看远程库别名
git remote -v
#拉取分支
git pull test master
#克隆代码
#克隆代码会做以下操作，1.拉取代码，2.初始化本地创库，3.创建别名
git clone
```

> <a name="WVQej"></a>
#### 本地仓库搭建

创建本地仓库的方法有两种：一种是创建全新的仓库，另一种是克隆远程仓库

- 创建全新的仓库，需要用GIT管理的项目的根目录执行：
```bash
# 在当前目录新建立一个Git代码库
$ git init
```

- 克隆远程仓库
```bash
# 克隆一个项目和它的整个代码历史（版本信息）
$ git clone [url]
```
```bash
# 添加所有文件到暂存区
$ git add . 
# 提交暂存区中的内容到本地仓库  -m 提交消息
$ git commit -m "消息内容"
```
<a name="PK3FA"></a>
## 文件操作

---

> 文件的4种状态

- Untracked：未跟踪，此文件在文件夹中，但并没有加入到git库，不参加版本控制。通过`git add`状态变为`Staged`
- Unmodify：文件已经入库，未修改，即版本库中的文件快照内容与文件夹中完全一致。这种类型的文件有两种去处，如果它被修改，而变为`Modified`.如果使用`git rm`移出版本库，则成为`Untracked`文件
- Modified：文件已修改，仅仅是修改，并没有其他的操作。这个文件也有两个去处，通过`git add`可进入暂存`staged`状态，使用`git checkout`则丢弃修改过的，返回到`unmodify`状态，这个`git checkout`即从仓库中取出文件，覆盖当前修改！
- Staged：暂存状态，执行`git commit`则将修改同步到库中，这时库中的文件和本地文件又变为一致，文件为`Unmodify`状态。执行`git reset HEAD filename`取消暂存，文件状态为`Modified`
```bash
# 查看文件指定状态
$ git status [filename]

# 查看所有文件状态
$ git status
```

> 忽略文件

有些时候我们不想把某些文件纳入版本控制中，比如数据库文件，临时文件，设计文件等<br />在主目录下建立“`.gitignore`”文件，此文件有如下规则：

1. 忽略文件中的空行或以（#）开始的行
2. 可以使用Linux通配符。例如星号（*）代表任意多个字符，问号（?）代表一个字符，方括号（[ abc]）代表可选字符范围，大括号（{string1,string2,...}）代表可选的字符串等
3. 如果名称的最前面有一个感叹号（!），表示例外规则，将不被忽略
4. 如果名称的最前面是一个路径分隔符（/），表示要忽略的文件在此目录下，而子目录的文件不忽略
5. 如果名称的最后一个路径分隔符（/），表示要忽略的是此目录下该名称的子目录，而非文件（默认文件或目录都忽略）
```bash
#为注释
*.txt				#忽略所有 .txt结尾的文件，这样的话上传就不会被选中
!lib.txt		#但lib.txt除外
/temp				#仅忽略项目根目录下的文件，不包括其他目录temp
build/			#忽略build/目录下的所有文件
doc/*.txt		#会忽略doc/notes.txt但不包括 doc/server/arch.txt文件
```

<a name="SG9yp"></a>
## 码云

---

设置本机绑定SSH公钥，实现免密码登录
```bash
# 进入 C:\User\Administrator\.ssh 目录
# 生成公钥
ssh-keygen
```
<a name="iY8AD"></a>
## <br />GIT分支
```bash
# 列出所有本地分支
$ git branch

# 列出所有的远程分支
$ git branch -r
$git branch -v

# 新建一个分支，但依然停留在当前分支  $git branch dev
$ git branch [branch -name]

# 新建一个分支，并切换到该分支
$ git checkout -b [branch]

# 合并指定分支到当前分支
$ git merge [branch-name]

# 删除分支
$ git branch -d [branch-name]

# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]

```
