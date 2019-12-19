## 下载安装

不需要自己安装，在安装 node 的时候直接安装好了

npm --version 可查看 （有的可简写为 npm -v，但不是所有的都可以简写）

-g 安装在全局

## 使用

+ 下载

  1. npm install 包名

     下载某个包

  2. npm i --save-dev 包名

     包分为项目依赖和开发依赖，开发依赖在打包后不存在（如gulp），而项目依赖会在项目打包后存在（如 jQuery），这里添加 --save-dev 是为了和项目依赖区分，他们会在

  3. npm install / npm i

     下载配置项的所有文件

+ 项目管理

  npm init

  可用 npm init -y 快速生成项目，全部走默认值

  会提示选项

  1. package name： 项目名称
  2. version：版本号
  3. description：描述
  4. entry point：入口文件，默认为 index.js
  5. test command:描述，可不用管
  6. git repository：git 仓库文件夹
  7. keywords：关键字
  8. author：作者
  9. license：监听指令（不用管，做端对端测试用）
  10. 结束



## 卸载

​	npm uninstall 包名



## 缓存

第一次下载较慢，之后会变快，是因为有缓存，但是如果第一次下载有误，之后的下载会一直有误

+ 清除缓存

  1. 代码清除缓存

     npm cache clear -f

  2. 手动清除缓存（有时候代码无法清除时候）

     在 c/用户/本机名字/appData/Roaming 中找到 `npm-cache` 删除掉就行

     

## nrm

是一个电脑上的工具包，可更改 npm 的下载地址

+ 下载

  npm i -g nrm

+ 使用

  1. nrm test

     检测可以使用的下载地址的延迟信息，前边有 * 的是当前使用的

  2. nrm use 地址名称

     切换镜像源地址，例：`nrm use yarn`

