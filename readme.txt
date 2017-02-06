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

# 添加文件（utf8 无BOM格式，使用notepad++编写，不要使用记事本，不要添加word文件）
$ git add file1.txt
$ git add file2.txt
# 提交文件
$ git commit -m "提交文件说明"
# 检查仓库当前状态
$ git status
# 查看文件修改内容
$ git diff file1.txt

# 回退版本（^表示上一个^^表示上上个~100表示前100个）
$ git reset --hard HEAD^

# 撤销回退版本
$ git reset --hard 版本号(可以不写全)

# 查看执行过的命令
$ git reflog

# 查看文件当前版本内容
cat file1.txt

# 查看历史记录（每条记录第一行十六进制字符串是版本号）
$ git log
# 查看历史记录（参数表示：每条记录显示一行）
$ git log --pretty=oneline
