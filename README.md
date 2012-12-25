## webtest ##

测试使用项目

此项目将用于测试学习git以及关联github，在Organizations中如何管理项目，成员之间的文档合并问题等，通过此项目测试实践这些问题，以便其他项目减少出错！

这是webCoding下的测试项目，由cloudYan、cloudAi管理和测试。

详细的使用及测试数据将会在项目中放出来，同时还可以参看提交记录来学习使用！

克隆测试项目，命令如下：

    git clone git@github.com:webcoding/webtest.git

本文档的上述修改，可作为测试提交，下面记录产生的问题：

由于之前做过ssh绑定，直接提交成功了。

经过测试，但凡账户已经绑定的，新作为Organizations 的 Members时，就已经具备上传的权限了。

# 如何绑定？新测试 #

将原来的ssh绑定删除，重新开始，修改后提交

    git commit -a -m "restart test"
    git push

提示：

    Username for 'https://github.com':
	Password for 'https://clouda@github.com':

输入正确的用户名密码，提交成功。

## 通过ssh key与github网站帐户绑定 ##

**创建验证用的公钥**

在本地创建验证用的文件，使用命令：ssh-keygen -C 'you email address@gmail.com' -t rsa，会在用户目录 ~/.ssh/ 下建立相应的密钥文件

可以使用 ssh -v git@github.com 命令来测试链接是否畅通

    cd ~/.ssh
    ssh-keygen -C ‘cloudAi@qq.com’ -t rsa
    #输入文件名称保存即可，比如：id_rsa

如果不输入文件名默认为id_rsa，我们需要的是.pub公钥文件，例如：

> ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEA6FrM305gIKnZiLyFBciMDmUskheorVAS+5FtnAD4NFQ4
> 0CawtdnlOdxu8bXN4MBp0lGbhs8dofVK8BRtXY+d2elNMB3D6NZ3p3xu/+c40WHRpYcjAPwXACGxEfJB
> cuYby4HifDBDIx7eeSR4Pzp*********************************************31uQ+nbtMtc7
> AhmmrIXXtqORQOu02qGDmZIPACCD4mOjujGW0xA0sa+ZDbyP/8W2A+h9011OshEA/Dx9DCJJ6yIZZXqT
> iksMipztNV2GeKTnO/ztE8YrAJY6zZWA0/LDk3doqiJmF9zCx7RrFLkzww== cloudAi@qq.com

如果上面使用 ssh-keygen -t rsa，则会如下，最后的标记不同，不指定的话，就取电脑名

> ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEA14fD1iCPJut92HGZ0aLQchhEwFsXVN6SImxxd6wxYmmO
> khGre2dS3xw7jewwmDu5o8yuvySEw0u8QjE+1D8MmUZwrCK8BRtXqofS75RsvEgUhJUWpd0htrA2/dUl
> WREoc***********************************************K8BRtXqofS75azDq5SHyx9DkPyKX
> WDxt8GCjCXTdzFYvPMsf/gwzxi9/Rza7pevlyeMfLlrnukJ0jXMlxm/8Psu/hZrqViYjthaWjqT+HffR
> c5pOt9AkL3MKgRqueMdkpOgWQsb7EYYyTnh1NiLirXfRpecV3NI2yV6P8w== Jack@ALICE

**上传公钥**

在 github.com 的界面中 选择右上角的 Account Settings，然后选择 SSH Public Keys ，选择新加。

Title 可以随便命名(可以区分不同的绑定环境)，Key 的内容拷贝自 ~/.ssh/id_rsa.pub 中的内容，完成后，可以再使用 ssh -v git@github.com 进行测试。看到下面的信息表示验证成功。


这里要注意,之前如果绑定过，那么简单的删除是不够干净的。

**Fork测试**

Fork之后测试数据提交效果。测试完成，连接成功，push没问题了。

另一根网线测试，纠结的网线！纠结的端口，再一次测试！测试网线，跟防火墙有关系，还需要检查443端口有没有开放。

这个蛋疼的问题，原来由网线引起，昨天调试到了半夜，老是不管用，push不上去，可能这根网线连接的路由器接口有安全设置吧，出现连接不上，并且有提示如下：

    Read from remote host github.com: Connection reset by peer fatal: Could not read from remote repository.

    Please make sure you have the correct access rights and the repository exists.

但是换根网线完全好了，浪费了那么多时间！


**测试Fork的分支提交到主项目master上**

首先修改Fork分支，提交，并push到webcoding上

    git push git@github.com:webcoding/webtest.git master

下面将此修改再测试一下。
