Git is a distributed version control system.
Git is free software.


git command
===========================================
# windows安装地址：https://pan.baidu.com/s/1kU5OCOB#list/path=%2Fpub%2Fgit
# 安装后，打开 Git Bash

# 自报家门
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
