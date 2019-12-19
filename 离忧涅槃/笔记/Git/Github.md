github.com

## 一、基本概念

仓库（Repository）

收藏（Star）

复制克隆代码（Fork）

发起请求（Pull Request）

关注（Wach）

 事务卡片（lssue）

Github主页

仓库主页

个人主页

## 二、使用

1.下载Git

地址：https://git-scm.com/

2.设置名称

```
git config --global user.name "name"
```

3.设置用户名邮箱

```
git config --global user.email "email"
```

4.查看设置

```
git config --list
```

5.下载仓库

```
git clone "链接"
```



## 三、命令



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

```git
git add 文件名		添加到暂存区
```

暂存区

```
git commit -m"描述"
```

仓库

```
git push		上传到github仓库
```

### 2.拉取

```
git pull
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

## 四、管理远程仓库

