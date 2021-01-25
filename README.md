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

## 暂存区
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
- 如果显示*** Please tell me who you are. 则需要填写配置，进行如下操作：
- 命令   git config --global user.name "你的git名称"
- 命令   git config --global user.email "你的git验证邮箱"
- 查看配置列表： git config --list
- 退出查看配置列表命令 :wq 回车

## 本地操作关键步骤总结
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

# 创建远程git仓库

## 官网创建准备
- 进入github官网
- 创建一个新的远程仓库(new)

## 将本地仓库与远程仓库关联
- git remote add origin https://github.com/1433223gg/GP5.git (你的远程仓库地址)
- origin 可以看成一个变量，可以自定义，指向后面的地址，一个本地仓库可以对应多个远程仓库
- git remote -v 查看本地仓库关联的远程仓库地址
- origin  https://github.com/1433223gg/GP5.git (fetch) //表示从该地址获取
- origin  https://github.com/1433223gg/GP5.git (push)  //表示到该地址添加

## 将本地仓库提交到远程仓库
- git push -u origin master  （第一次提交到远程或者修改关联的远程仓库地址时需要这么写，master是自定义的一个分支，相当于建立一个对分支的固定的链接）
- git push 将本地仓库提交到远程仓库（之后用这个就行，提交当前默认分支到远程仓库）
- -u origin master 设置默认的提交地址和分支

## 正常的提交（非第一次）总结
- git add . 提交到暂存区
- git commit -m '注释' 提交到本地仓库
- git push 提交到远程仓库(默认提交到origin上的master分支)

# 配置SSH公匙

## 配置公匙步骤
- (1) 首先检查电脑是否曾经生成过私钥公钥
cd ~/.ssh
若打开该文件夹为空，则表示没有生成过密钥，进入第二步。（~表示根目录）
- (2) 生成私钥
ssh-keygen -t rsa -C "your email"
命令要求输入密码，不用输，三个回车即可。
执行成功后，会在主目录.ssh路径下生成两个文件：id_rsa私钥文件；id_rsa.pub公钥文件； 
- (3) 配置公钥
登陆github帐户点击头像，然后 Settings -> 左栏点击 SSH and GPG keys -> 点击 New SSH key
在远程仓库github上添加title和key，和本地的一致。title可以自己取一个容易区分的名字，key为id_rsa.pub中的内容（全部复制，可用cat id_rsa.pub命令打开）
- (4) 修改关联的远程仓库地址
创建的项目中会有Code按钮，可以下载代码，点击下拉中clone里有SSH，复制其中的地址进行修改关联远程仓库地址操作
- git使用https协议，每次pull, push都要输入密码，相当的烦。
使用git协议，然后配置好SSH，这样可以省去每次都输密码。

## 修改关联的远程仓库地址
- git remote rm origin
- git remote add origin git@github.com:1433223gg/GP5.git (SSH地址)
- git push -u origin master (将本地仓库提交到指定的远程仓库位置，相当于第一次提交的操作) 如果回车运行过程中有yes/no选择，就选yes
- git remote -v 查看是否修改完成

# 项目工作中出现的真实情况

## 更新代码
- 到岗第一件事，更新代码
- git add .
  git commit -m
确保自己工作区代码先提交到本地仓库
- 然后再从远程更新到本地 git pull
- 如果出现更新內容和本地仓库內容冲突的情况，可以在vs编辑器中根据情况进行合并和选择

## 工作时要做的正常提交总结
- git add . 提交到暂存区
- git commit -m '注释' 提交到本地仓库
- git pull 先更新远程到本地
- git push 提交到远程仓库(默认提交到origin上的master分支)

## 代码更新到本地
1. 不能下载压缩包，这样并不能让我们参与到项目中去，不是一个版本库
2. 在创建的工作文件夹中打开命令框
git clone https://github.com/1433223gg/GP5.git （远程仓库地址）
克隆了整个版本库到当前文件夹
3. 要进入项目文件夹中，可以使用如 cd GP5 进入到项目路径，如果显示 work/GP5 (master)
有 master 说明可以进行版本库更新了，不需要对其进行任何设置，直接可以进行上面的正常工作提交操作

## 分支操作
- git branch 查看所有分支
- 当前分支名前面会有一个*号，如 * master
- git branch 分支名 创建一个分支，类似一个指针，指向特定的某个版本，类似于复制但不是复制出一整个备份，目的是方便修改，分支可以随意操作。
- git checkout 分支名 切换分支
- git merge 新分支名 合并某分支到当前，需要切换到要合并的项目当前分支中，再合并新分支，如果有冲突，需要先进行合并或选择，然后如果出现括号里不是master分支的情况，需要先add再commit。
- git branch -d 分支名  删除某分支
- git push origin 分支名  将某分支提交到远程（需要在master当前默认分支中操作）
- git pull origin 分支名 将某个分支更新到本地仓库

## fetch和pull的区别
1. 他们都用于从远程更新代码到本地
2. git fetch不会自动合并到当前分支(不会merge)
3. git pull会自动合并到当前分支(会自动merge)


123546
