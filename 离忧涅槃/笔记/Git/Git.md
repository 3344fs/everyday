版本管理器，可异地开发，多人协同开发

网站：http://github.com

## 安装配置

​	下载后一直下一步

+ 检测

  桌面鼠标右击查看

  cmd 中 git --version

+ 全局配置

1. 打开 git base here
   1. git config --list	查看目前的配置列表
   2. git config --global user.name "用户名"
   3. git config --global user.email "邮箱"



## 管理文件夹

文件夹中打开git，写入 git init

完成后会出现 .git 文件夹


## 命令

ls 	查看当前目录下文件

la -a		查看当前目录下所有文件（包括隐藏文件）

clear		清屏

touch		新建文件

rm -rf		删除文件

### 1.提交

```
git status		查看
```

工作区

```
git add 文件名		添加到暂存区

git add --all/./*	把所有文件添加到暂存区
```

暂存区

```
git reset HEAD -- 文件/文件夹名		把暂存区文件拉回到工作区，注意 -- 和名称中间有个空格

git commit -m"描述"	把暂存区内所有内容存入仓储中
```

仓库

```
git log		查看仓库的所有版本
git reset --hard 版本ID	回到某个版本

git remote add origin 地址	设置上传地址
git push -u origin 分支(master)		上传到github仓库
```

### 2.拉取

```
git pull	拉取更新远程最新代码
```



### 3.删除

删除文件

```
rm 文件名
```

git 中删除

```
git rm 文件名
```

## 管理远程仓库

