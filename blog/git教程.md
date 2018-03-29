## git之间是仓库和仓库之间的关系

![微信图片_20180328223248.jpg](https://i.loli.net/2018/03/28/5abba7e03ddca.jpg)

如上图所示，本地文件夹之内的代码管理和远程repository之间关系是不同的

### 新建git repository的方法 
1.从远程的repository中`git clone xxx.git "指定目录"`克隆远程repository
   这样项目中就自带了.git 文件，里面会带有所有代码的hash快照状态和commit状态
2.本地`git init`目录，这样目录中就会出现.git的文件
   所以，你git clone了别人的代码，再git init了它。它就是没有携带别人劳动成果的代码，
可以直接在原来的基础上修改自己的代码再push到自己的git地址上

### 本地working和repository之间的操作
   - 在working directory和本地的repository之间还有一个stage area。
   - 三者之间的代码如长图所示修改，可以用`git status`查看相应是否进入缓存状态来查看

### 远程repository和本地的repository之间的联系
  - 建立联系的方式是用ssh，公私钥配对的方式来建立
    `$ ssh-keygen -t rsa -C "your_email@youremail.com"`
    用以上命令行来生成本地设备的公私钥文件，将`~/.ssh`中的id_rsa.pub公钥配置到远程的git服务器上
  只有公私钥配对的设备之间才可以pull push代码，不然什么阿猫阿狗都能改repository的代码，不是晕菜了。
 - 远程服务器怎么知道提交的是谁呢
    `git config --global user.name "youname"
     git config --global user.email "youemail@163.com"`

以上命令行全局配置了你的git，这样不管推送给remote就知道是谁推送的了。



### 本地对远程repository的设置(git remote)

*应用场景：*如果你不是一套代码推送多个git库，其实没有必要学这个，当时被这个知识点搞晕了很久



 >tip：对git remote命令行的操作，并不能对真正的远程repository有任何影响，

  仅仅是本地对remote repository的操作更加的方便便捷而已，毕竟你一套代码会推送多个远程git库



- 一套代码推送多个remote repository

 `git remote -v`查看当前git push的远程库名称和地址

 `git remote add youname git@github.giti `因为git要求每台远程主机上要有主机名，所以在push之前你可以给主机名命名（默认origin）

 `git remote remove yousetname` 删除本地git中给远程主机配置的名字

`git remote set-url youname git@yougit.git`重命名远程git的名字



### 远程repository和本地代码的提交

##### - 基本的`git pull` 和 `git push`

 在push之前pull一下代码更新

 - 建立分支branch

##### *应用场景：*A和B和C要分别开发不同的功能

![微信图片_20180328230824.jpg](https://i.loli.net/2018/03/28/5abbb02aa6a53.jpg)

建立分支，是本地的repository建立属于自己的分支，再push到远程的库中
`git branch youbranchname`建立分支名称
`git checkout youbranchname`切换到分支下开发功能
`git merge`合同分支，一定要在master的情况下去做合并

### 代码冲突
代码冲突难免的，随缘HEAD，这个主要还是看diff软件做冲突管理，下次再说



 

   