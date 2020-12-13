# 1.git安装

Git是一个版本控制系统，即一个工具，使用之前要先下载安装，mac和Linux上自带git，不需要下载，主要是Windows系统需要安装。安装链接如下：

Windows：https://gitforwindows.org/

Linux(ubuntu)：apt-get install git

# 2.Git命令列表

判断git是否安装成功，可以在命令行输入git，如果出现以下命令，证明已经安装成功。

![image-20201213152340288](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20201213152340288.png)

上面是一些常用的git命令，命令后有英文解释。



# 3.Git常用命令

### 3.1 新建一个文件夹，并切换到其中

```
mkdir workspace
cd workspace
touch test.md
```

### 3.2 初始化厂库

```
git init
```

执行完该命令后，workspace已经是一个git仓库了。

![image-20201213153207815](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20201213153207815.png)

### 3.3 获取状态

```
git status
```

![image-20201213153225920](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20201213153225920.png)

第一行显示我们所在的分支

第二行显示提交信息

第三行显示可以提交的文件

### 3.3 提交到git仓库

```
git add file_name
git add .     #提交所有文件
```

![image-20201213153543805](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20201213153543805.png)

先新建一个文件，再将其提交到仓库，此时再用git status 可以看到提交信息

![image-20201213153731118](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20201213153731118.png)

### 3.4 正式提交

```
git commit -m "first"
```

commit 是提交的意思， -m 代表是提交信息， 执行了以上命令代表我们已经正式进行了第一次提交。  

### 3.5 查看提交日志

```
git log
```

输入可以看到如下：

![image-20201213154434912](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20201213154434912.png)

git log 命令可以查看所有产生的 commit 记录， 所以可以看到已经产生了一条 commit 记录，
而提交时候的附带信息叫 'first commit' 。  

### 3.6 git add 和git commit 的区别

首先 git add 是先把改动添加到一个「暂存区」 ， 你可以理解成是一个缓存区域， 临时保存你的改动， 而 git commit 才是最后真正的提交。 这样做的好处就是防止误提交， 当然也有办法把这两步合并成一步。

### 3.7 获取分支

执行 git init 初始化git仓库之后会默认生成一个主分支 master ， 也是你所在的默认分支， 也基
本是实际开发正式环境下的分支， 一般情况下 master 分支不会轻易直接在上面操作的， 你们
可以输入 git branch 查看下当前分支情况  

```
git branch              #获取分支
```

![image-20201213154926131](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20201213154926131.png)

星号表示目前所在分支

也可以新建分支

```
git branch branch_name  #新建分支branch_name
```

![image-20201213155015842](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20201213155015842.png)

新建并切换分支：

```
git chechout -b a
```

  这个命令的意思就是新建一个a分支， 并且自动切换到a分支。  

### 3.8 合并分支

```
git merge
```

A同学在a分支代码写的不亦乐乎， 终于他的功能完工了， 并且测试也都ok了， 准备要上线了， 这个时候就需要把他的代码合并到主分支master上来， 然后发布。 git merge 就是合并分支用到的命令， 针对这个情况， 需要先做两步， 第一步是切换到 master 分支， 如果你已经在了就不用切换了， 第二步执行 git merge a ， 意思就是把a分支的代码合并过来  

### 3.9 删除分支

```
git branch -d a 
```

a分支的代码已经顺利合并到master 分支来了， 那么a分支没用了， 需要删除， 这个时候执行 git branch -d a 就可以把a分支删除了。  

