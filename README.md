### GIT第二天

#### 本地和远程仓库相关联（推荐在已经有代码的情况下）

```
# 在github中创建仓库
# 如果项目目录没有文件，在项目目录下新建一个文件（建议是README.md）
git init
git add .
git commit -m "first commit"
# git remote add这一步是做关联，地址写自己仓库的地址，只写一次
git remote add origin https://github.com/niuxi091/git-learn.git
# 推送到网络仓库,-u及后面的代码只需要第一次推送的时候输入
git push -u origin master
```

#### HTTPS协议和SSH协议的区别

- HTTPS协议 - 提交的时候会验证用户信息（验人）

- SSH协议 - 需要进行配置，配置好后不会有验证弹窗（验机器）

#### SSH的配置

##### 生成key

1. 打开Git命令行

2. ```
   # 生成key的命令，注意，邮箱地址要填写github登录的邮箱
   ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   ```

3. 在`C:/Users/用户名/.ssh`下查看生成的key文件`id_rsa`是私钥文件，`id_rsa.pub`是公钥文件

##### 添加密钥到Github

1. 复制刚生成的`id-rsa.pub`文件的内容
2. 在github中点击右上角自己的头像，然后点击settings
3. 点击右侧菜单栏中的`SSH and GPG keys`
4. 点击右侧`New SSH key`按钮
5. 将复制的公钥内容放到`key`中，`title`中建议输入电脑名称，然后点击添加
6. 在git命令行中输入`ssh -T git@github.com`，显示`Hi niuxi091! You've successfully authenticated, but GitHub does not provide shell access.`则配置成功

#### 更换远程仓库地址

1. `git remote rm origin` - 删除已经配置的网络仓库地址
2. `git remote add origin ssh地址`

#### 提交步骤

1. `git add .`
2. `git commit -m "message"`
3. `git push`

#### 全新仓库创建（在项目没开始的时候使用）

1. 在github中新建仓库，选择生成一个文件（README或.gitignore都可以）
2. 在项目页面`code`按钮下复制ssh地址
3. 找到想存放项目的目录，右键打开git命令行
4. 在命令行输入`git clone 仓库ssh地址`
5. 不需要任何配置，直接使用`add commit push`就可以进行推送，注意，要在下载的项目目录中打开命令行使用

#### 分支

##### 查看当前仓库分支

```
git branch
# master是默认的主分支名称
```

##### 新建分支

```
# 新建分支，确保在主分支上新建
git branch 分支名称
# 切换到新建分支
git checkout 分支名称
# 新建分支同时切换过去（建议使用）
git checkout -b 分支名称
```

##### 合并分支（确保在主分支master上）

```
git merge 分支名
```

##### 删除分支

```
git branch -d 分支名
```

##### 推送分支到远程仓库

```
git push -u origin 分支名
```

##### 查看远程分支

```
git remote show 远程仓库名
```

##### 下载远程分支到本地

```
git checkout -b 本地分支名 远程仓库名/远程分支名
```

##### 更新代码(远程仓库的代码要比本地代码新，当git push失败时可以先更新为最新代码然后再推送)

```
git pull
```

##### 删除远程分支

```
git push origin --delete 远程分支名
```

