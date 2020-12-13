# 向GitHub提交代码

## 1. SSH

你拥有了一个 GitHub 账号之后， 就可以自由的 clone 或者下载其他项目， 也可以创建自己的项目， 但是你没法提交代码。  提交代码之前一定是需要某种授权的， 而 GitHub 上一般都是基于 SSH 授权的 。

那么什么是 SSH 呢？ 简单点说， SSH是一种网络协议， 用于计算机之间的加密登录。 目前是每一台 Linux 电脑的标准配置。 而大多数 Git 服务器都会选择使用 SSH 公钥来进行授权，所以想要在 GitHub 提交代码的第一步就是要先添加 SSH key 配置。  



## 2.生成SSH key

Linux 与 Mac 都是默认安装了 SSH ， 而 Windows 系统安装了 Git Bash 应该也是带了 SSH的。 大家可以在终端（ win下在 Git Bash 里） 输入 ssh 如果出现以下提示证明你本机已经安装 SSH， 否则请搜索自行安装下。  

![image-20201213161244844](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20201213161244844.png)

紧接着输入 ssh-keygen -t rsa ， 什么意思呢？ 就是指定 rsa 算法生成密钥， 接着连续三个回
车键（ 不需要输入密码） ， 然后就会生成两个文件 id_rsa 和 id_rsa.pub ， 而 id_rsa 是密钥，
id_rsa.pub 就是公钥。 这两文件默认分别在如下目录里生成：  

Linux/Mac 系统 在 ~/.ssh 下， win系统在 /c/Documents and Settings/username/.ssh 下，
都是隐藏文件。  

接下来要做的是把 id_rsa.pub 的内容添加到 GitHub 上， 这样你本地的 id_rsa 密钥跟 GitHub
上的 id_rsa.pub 公钥进行配对， 授权成功才可以提交代码。  



## 3. GitHub 上添加 SSH key  

在 GitHub 上的设置页面， 点击最左侧 SSH and GPG keys , 然后点击右上角的 New SSH key 按钮：  

![image-20201213161538952](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20201213161538952.png)

需要做的只是在 Key 那栏把 id_rsa.pub 公钥文件里的内容复制粘贴进去就可以了（ 上述示例
为了安全粘贴的公钥是无效的） ， Title 那栏不需要填写， 点击 Add SSH key 按钮就ok了。  

## 4. Push & Pull  

```
git push origin master
```

意思就是把本地代码推到远程 master 分支。  

```
git pull origin master
```

意思就是把远程最新的代码更新到本地。 一般我们在 push 之前都会先 pull ， 这样不容易冲
突  。

## 5.提交代码

可以先将github上的项目下载到本地，执行如下：

```
git clone https://github.com/850319644/test.git
```

这个时候该项目本身就已经是一个git 仓库了， 不需要执行 git init 进行初始化， 而且甚至都已经关联好了远程仓库， 我们只需要在这个 test 目录下任意修改或者添加文件， 然后进行 commit ， 之后就可以执行：  

```
git push origin master
```

假设我们本地有个 test2 的项目， 我们需要的是在 GitHub 上建一个 test 的项目， 然后把本地
test2 上的所有代码 commit 记录提交到 GitHub 上的 test 项目。

第一步就是在 GitHub 上建一个 test 项目， 这个想必大家都会了， 就不用多讲了。
第二步把本地 test2 项目与 GitHub 上的 test 项目进行关联， 切换到 test2 目录， 执行如下命
令：  

```
git remote add origin https://github.com/850319644/test.git
```

 origin 是给这个项目的远程仓库起的名字，名字可以随便取  

查看我们当前项目有哪些远程仓库可以执行如下命令：

```
git remote -v  
```

默认向 GitHub 上的 test 目录提交了代码， 而这个代码是在 master 分支。   

```
git push origin master
```

友情提醒， 在提交代码之前先要设置下自己的用户名与邮箱， 这些信息会出现在所有
的 commit 记录里， 执行以下代码就可以设置：  

```
git config —global user.name "stormzhang"
git config —global user.email "stormzhang.dev@gmail.com"  
```