### GIT第二天

#### 本地和远程仓库相关联

```
# 在项目目录下新建一个文件（建议是README.md）
git init
git add .
git commit -m "first commit"
# git remote add这一步是做关联，地址写自己仓库的地址
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