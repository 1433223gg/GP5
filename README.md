# readme文档
- 项目说明文档
- 一般都与项目放在一起

# git本地操作

## 初始化版本库
- git init
- 初始化成功后，当前目录后面有(master)，有master说明是一个版本库
- 初始化成功后，当前目录下有个隐藏文件.git（不要对其进行任何操作）

## 工作区
- 持有实际文件（当前能直接看到的文件夹文件）
- 我们平时增删改查的文件都是工作区的内容

## 提交到暂存区
- 可以理解为我们看不到的一个地方，不需要直接去操作这个区域
- 本地仓库的一个主要组成部分

## 本地仓库
- 可以理解为我们看不到的一个地方，不需要直接去操作这个区域
- 也是存在于用户电脑中的
- 用于存储项目代码及版本项目记录等信息，一般工作区的文件代码都要在本地仓库中

## 提交到暂存区
- git add 文件名
- 将工作区的变动提交到暂存区（增删改）
- git add .
- 将当前工作区目录下的所有变动提交到暂存区

## 查看状态（辅助命令）
- git status
- 查看工作区和暂存区的状态（增删改）

## 查看日志
- git log      完整版日志
- git reflog   简单版日志

## 提交到本地仓库
- git commit -m '提交注释'
- 注释用以方便查看版本信息
- 将暂存区代码提交到本地仓库
- git status 查看状态显示
- 如果显示*** Please tell me who you are. 则需要填写配置
- 命令   git config --global user.name "你的git名称"
- 命令   git config --global user.email "你的git验证邮箱"
- 查看配置列表： git config --list
- 退出查看配置列表命令 :wq 回车

## 本地操作关键步骤
1. git init(第一次创建新的版本库时需要)
2. git add .
3. git commit -m '注释'

## 查看日志
- git log      完整版日志
- git reflog   简单版日志

## 版本回退
- git reset --hard HEAD^(回退几个版本就加几个^)
- git reset --hard 版本号(回退到某个指定版本)
- 注意把当前代码先提交到本地仓库
- 工作区代码自动变为指定版本的代码，会被替换掉
- 回退到某一版本之后，从当前版本到之前的版本之间的日志会被删除

## 查看变动
- git diff 文件名
- 会列出该文件前后的差异

## git命令行中的其他操作命令：
- 命令  cd d:  进入相应的磁盘 
- 命令  cd  进入文件夹
- 命令 cd ..  返回上一层目录
- 命令  mkdir  创建目录 
- 命令  pwd 显示当前工作目录的全路径
- 命令 touch xx  新建xx文件
- 命令 vi xx  编辑xx文件，按i切换到编辑模式，按esc切换到命令模式，输入冒号:wq 回- 车，保存并返回
- 命令  rm  删除文件
- 命令  ls 查看当前目录的所有文件
- 命令 clear  清屏

# 创建远程仓库

## 官网创建准备
- 进入github官网
- 创建一个新的远程仓库

## 将本地仓库与远程仓库关联
- git remote add origin https://github.com/1433223gg/GP5.git (你的远程仓库地址)
- origin 可以看成一个变量，指向后面的地址
- git remote -v 查看本地仓库关联的远程仓库地址
- origin  https://github.com/1433223gg/GP5.git (fetch) //表示从该地址获取
- origin  https://github.com/1433223gg/GP5.git (push)  //表示到该地址添加

## 将本地仓库提交到远程仓库
- git push -u origin master  （第一次提交到远程需要这么写，master是自定义的）
- git push 将本地仓库提交到远程仓库（之后用这个就行）
- -u origin master 设置默认的提交地址和分支

## 正常提交（非第一次）
- git add . 提交到暂存区
- git commit -m '注释' 提交到本地仓库
- git push 提交到远程仓库(默认提交到origin上的master分支)

