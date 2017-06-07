## 关键步骤简化聚说明
    使用git在本地创建一个项目的过程

    $ makdir ~/hello-world    //创建一个项目hello-world
    $ cd ~/hello-world       //打开这个项目
    $ git init             //初始化 
    $ touch README
    $ git add README        //更新README文件
    $ git commit -m 'first commit'     //提交更新，并注释信息“first commit” 
    $ git remote add origin git@github.com:defnngj/hello-world.git     //连接远程github项目  
    $ git push -u origin master     //将本地项目更新到github项目上去
    //此步易出错,问题（Non-fast-forward）的出现原因在于：git仓库中已经有一部分代码，所以它不允许你直接把你的代码覆盖上去。于是你有2个选择方式：
    强推，即利用强覆盖方式用你本地的代码替代git仓库内的内容
      git push -f origin master

## 1、安装Git

下载Windows下的Git客户端并安装，安装很简单，基本一路Next下去。

## 2、安装Node.js

下载Node.js，安装Node.js也是一路Next下去。

## 3、Github配置

Github账号注册就不说了，登陆过后点击new repository，Repository name填写自己的名称 + .github.io，
例如（test.github.io，test就是你的github账号的名称）（由于我也是才刚刚接触Github没多久，暂时就不说我的账号了，哈哈哈，太Low了），其他的可以不用填写，也不需要改什么。


创建仓库截图

然后直接点Create repository就可以了。

## 4、配置Github SSH密钥

首先在桌面空白处鼠标右键选择Git Bash Here

ssh-keygen -t rsa -C "your's emaill address"
引号里面的内容输入你的邮箱地址，然后回车，会提示你文件保存的路径，这时候按回车键确认
然后会提示你输入密码，输入即可（输入密码是看不到的），然后会确认输入一次，就可以在刚刚的路径看到生成了两个文件，一个是id_rsa，另一个是id_rsa.pub，用notepadd++打开id_rsa.pub然后选中里面的全部内容，复制下来。

登录github，点击头像可以看到setting选项，点击进入
然后可以看到左边有一个SSH and GPG keys选项
点击就可以看到以下界面，点击New SSH



这里的Title随便填写，主要是为了方便管理密钥
然后把刚刚拷贝的内容粘贴到Key里面去
然后点击Add SSH key
到此，Github上面的SSH配置就算完成了

## 5、创建本地仓库与Github同步

首先是在本地的任意一个分区创建一个任意的文件夹，路径中最好不要用中文吧，反正你懂的
然后进入到刚刚创建的文件夹，右键，然后点击Git Bash Here


打开Git Bash

依次输入以下命令（前面的$符号就不要复制了哈）

* $ git init
* $ git config --global user.name "Your's name"
* $ git config --global user.email "Your's email address"
其中的Your's name替换成你的名称，Your's email address替换成你的邮件地址即可
然后再当前的文件夹下面新建一个README.md文件，然后右键用notepad++打开，随便写入一点内容，做一次简单的提交，输入以下命令
其中的yourname是github账号的名称，每个人是不一样的

* $ touch README.md
* $ git add README.md
* $ git commit -m "first commit"
* $ git remote add origin git@github.com:yourname/yourname.github.io.git
** 注意
    此处容易报错,提示出错信息：fatal: remote origin already exists.
    解决办法如下：
    1、先输入$ git remote rm origin
    2、再输入$ git remote add origin git@github.com:djqiang/gitdemo.git 就不会报错了！
    3、如果输入$ git remote rm origin 还是报错的话，error: Could not remove config section 'remote.origin'. 我们需要修改gitconfig文件的内容
    4、找到你的github的安装路径，我的是C:\Users\ASUS\AppData\Local\GitHub\PortableGit_ca477551eeb4aea0e4ae9fcd3358bd96720bb5c8\etc
    5、找到一个名为gitconfig的文件，打开它把里面的[remote "origin"]那一行删掉就好了！
  
* [github常见操作和常见错误处理](http://blog.csdn.net/dengjianqiang2011/article/details/9260435)

* $ git push -u origin master
** 注意
   此步易出错,问题（Non-fast-forward）的出现原因在于：git仓库中已经有一部分代码，所以它不允许你直接把你的代码覆盖上去。于是你有2个选择方式：
   强推，即利用强覆盖方式用你本地的代码替代git仓库内的内容
   git push -f origin master
      
这时候进入到github应该就可以看到仓库下面有一个刚刚提交的README.md的文档了。



