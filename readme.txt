一、Git 基本使用命令
工作区add=>[版本库:1暂存区stage(commit)=>2master分支]
1.右键Get Bush Here
2.$Mkdir 文件名
3.pwd 代表目录
------------------------------------------------------------------
4.git init 初始化即创建一个空盒
5.git add readme.txt  用命令git add告诉Git，把文件添加到仓库
6.git commit -m "提交的说明内容"
----------------以上基本完成一个提交的过程-----------------------
7.git status 命令可以让我们时刻掌握仓库当前的状态
8.git diff 查看不同
9.git log 查看每次提交的日志简要信息加上 --pretty=oneline 即git log --pretty=onelone
10.git reset --hard HEAD^ 返回上一版本=>Git必须知道当前版本是哪个版本，在Git中，用HEAD表示当前版本，上一个版本就是HEAD^，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。
11. git reset --hard 1094a 如果git 没有关掉使用模糊查询可以从回退的版本回到新的版本如1904指的版本号
12.git reflog 查看提交的版本信息；即 如果不知道版本的id 用git reflog查看命令历史，以便确定要回到未来的哪个版本。
-------------------------------------------------------------------
git 提交需要先add 然后再commit 首先add的意思是：将要提交的内容添加到暂存区，然后使用commit 命令将其提交到版本库
-------------------------------------------------------------------
13.cat file 查看内容file指的文件名 cat readme.txt
14.git checkout -- file 假如编写的代码有问题想回滚到原来，即在add暂存区前，将工作区的内容回滚到初始，即丢弃修改 file 代指文件名称；如git checkout -- readme.txt
15.git reset Head file 可以把暂存区的内容撤销到工作区 然后 再使用14 即可回到初始
16.git rm file其中file指的文件名,使用指令删除git rm test.txt ，删除完成后要记得提交哦删除版本库中不能恢复，删除工作区的但版本库没有删除能恢复
===========================================================================================
二、git 关联gitHub
第1步：创建SSH Key，在用户主目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：
$ ssh-keygen -t rsa -C "youremail@example.com"
你需要把邮件地址换成你自己的邮件地址，然后一路回车，使用默认值即可，由于这个Key也不是用于军事目的，所以也无需设置密码。
如果一切顺利的话，可以在用户主目录里找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。

第2步：登陆GitHub，打开“Account settings”，“SSH Keys”添加本地的公钥即可
-------------------------------------------------------------------------------------
你已经在本地创建了一个Git仓库后，又想在GitHub创建一个Git仓库，并且让这两个仓库进行远程同步，这样，GitHub上的仓库既可以作为备份，又可以让其他人通过该仓库来协作，真是一举多得。
1.首先再GitHub创建Repository 
2.在本地的仓库运行命令：$ git remote add origin https://github.com/JaMinFu/Code.git
3.把本地推送到远端 $ git push -u origin master 远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。推送成功后GitHub页面中看到远程库的内容已经和本地一模一样，
后面从本地提交就可以通过简化命令 $ git push origin master
4.$ git clone git@github.com:JaMinFu/gitskills.git 克隆远端文件 cd file =>ls 查看拉取的文件
--------------------------------分支------------------------------------------------
(分支运用情景，假设你准备开发一个新功能，但是需要两周才能完成，第一周你写了50%的代码，如果立刻提交，由于代码还没写完，不完整的代码库会导致别人不能干活了。如果等代码全部写完再一次提交，又存在丢失每天进度的巨大风险。
现在有了分支，就不用怕了。你创建了一个属于你自己的分支，别人看不到，还继续在原来的分支上正常工作，而你在自己的分支上干活，想提交就提交，直到开发完毕后，再一次性合并到原来的分支上，这样，既安全，又不影响别人工作。)
1.git branch 查看分支
2.git branch <name> 创建分支
3.git switch<name> 切换分支或者（git checkout <name>注意别混淆git checkout --file）
4.创建+切换分支git switch -c <name>或 git checkout -b <name>
5.合并某分支到当前分支git merge <name>
6.删除分支 git branch -d <name>
Creating a new branch is quick & simple.



