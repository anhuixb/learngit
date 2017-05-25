Git is a distributed version control system.
Git is free software.
在master中测试修改冲突！

git command
===========================================
# windows安装地址：https://pan.baidu.com/s/1kU5OCOB#list/path=%2Fpub%2Fgit
# 安装后，任何目录右击菜单，可以打开 Git Bash Here

# 自报家门（定义提交的用户信息）
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"

# 创建版本库
$ mkdir learngit
$ cd learngit
# 显示当前目录
$ pwd

# 目录变成Git仓库
$ git init

# 添加文件，添加到暂存区（文件编码：utf8 无BOM格式，使用notepad++编写，不要使用记事本；不要添加二进制文件，如word）
$ git add file1.txt
$ git add file2.txt
# 删除文件(先删除系统目录中文件，后删除版本库中文件)
$ rm file2.txt
$ git rm file2.txt
# 提交文件（提交到默认的master分支中）
$ git commit -m "提交文件说明"
# 检查仓库当前状态
$ git status
# 查看文件修改内容
$ git diff file1.txt

# 回退版本（HEAD^表示上一个，HEAD^^表示上上个，HEAD~100表示前100个，也可直接写版本号[可以只写开头字符]）
$ git reset --hard HEAD^

# 回退版本（加到暂存区后,未commit,撤销暂存区数据，还原工作区未add状态）
$ git reset HEAD file1.txt

# 还原工作区（1.未加到暂存区，还原到未修改前工作区状态；2.加到暂存区后又修改了，还原到加入暂存区时状态）
$ git checkout -- file1.txt

# 查看成功执行过的命令
$ git reflog

# 查看文件当前版本内容
cat file1.txt

# 查看历史记录（每条记录第一行十六进制字符串是版本号）
$ git log
# 查看历史记录（参数表示：每条记录显示一行）
$ git log --pretty=oneline
# 查看最近一条记录
$ git log -1

# 生成密钥
$ ssh-keygen -t rsa -C "anhuixb@163.com"
# 仓库目录同级，会生成.ssh目录，公钥内容添加到GitHub帐户中
# 关联远程库（要求GitHub添加repository，这里名称是:learngit）
$ git remote add origin git@github.com:anhuixb/learngit.git
# 以上使用git协议，速度更快或使用以下https
$ git remote add origin https://github.com/anhuixb/learngit.git
# 推送到远程库(第一次)
$ git push -u origin master
# 推送最新修改到远程库
$ git push origin master
# 查看远程库的信息(显示抓取fetch和推送push地址)
$ git remote -v

# 从远程库克隆到本地（这里gitskills是githup中创建的库）
# 先cd到根目录
$ cd ~
$ git clone git@github.com:anhuixb/gitskills.git

# 分支
# 查看当前分支(有星号，表示当前所在分支)
$ git branch
# 创建分支（这里dev是分支名称）
$ git branch dev
# 删除分支
$ git branch -d dev
# 删除一个没有被合并的分支（强行删除）
$ git branch -D dev
# 切换分支
$ git checkout dev
# 创建并切换分支
$ git checkout -b dev
# 指定分支合并到当前分支（删除分支历史）
$ git merge dev
# 指定分支合并到当前分支（保留分支历史）
$ git merge --no-ff -m "merge with no-ff" dev
# 合并远程库到本地（远程比本地代码要新，无法提交时）
$ git pull
# 本地分支和远程分支的创建链接关系（没有关系时合并远程库时会失败）
$ git branch --set-upstream dev origin/dev

# 分支合并冲突时（例如同时修改了同一行，内容还不一样，需要在合并出错后，手动更改文件，合并类似以下格式内容）
<<<<<<< HEAD
当前版本冲突行的内容
=======
被合并版本冲突行的内容
>>>>>>> dev

# 多个任务需要同时工作，但部分bug要优先处理提交，可以将之前的工作状态保存，在其它分支解决优先的bug并提交后，再恢复之前的分支工作状态
# 工作现场“储藏”起来
$ git stash
# 查询工作现场"储藏"记录
$ git stash list

# 恢复（保留被恢复的stash记录）
$ git stash apply stash@{0}
# 删除stash记录
$ git stash drop
# 恢复并删除stash记录
$ git stash pop

# 打标签（创建标签，往往是指定当前分支最新提交时的版本说明）
$ git tag v1.0
# 指定具体版本号的版本说明（版本号由log命令查询）
$ git tag v0.9 6224937
$ git tag -a v0.1 -m "这里是标签说明文字" 3628164
# 显示标签所在的版本具体信息
$ git show v1.0
# 推送标签到远程：推送一个、推送全部
$ git push origin v1.0
$ git push origin --tags
# 删除标签：先删除本地，在删除远程标签
$ git tag -d v1.0
$ git push origin :refs/tags/v1.0

# 忽略要提交的文件
# 仓库目录添加.gitignore文件，并提交到Git。文件内容是要忽略的文件名，或通配名，如*.ini
# 检查要提交的文件名是否是被忽略的文件
$ git check-ignore -v App.class

# 如果命令窗口中文字没有颜色可以设置
$ git config --global color.ui true

# 添加命令别名（比如简化commit为ci）
$ git config --global alias.ci commit
# 此时提交命令可以是
$ git ci -m "command easy..."
# 添加命令别名：log有颜色、有分支线的记录显示
$ git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
$ git lg

# 删除命令别名（添加命令时，加了--global全局命令）
# 打开仓库中.git/config文件，删除[alias]下的内容即可

# 删除命令别名（当前用户，没有加--global）
# 打开仓库中.gitconfig文件，删除[alias]下的内容即可
