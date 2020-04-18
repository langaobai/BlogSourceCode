title: npm包管理常用命令（不定时更新）
author: LanGaoBai
author_id: defaultAuthorId
language: zh-CN
tags:

  - node
  - npm
categories:
  - node
date: 2020-04-02 09:55:00

---

### 介绍

一段时间一段时间不做node项目，会忘记一些基本命令，甚至常用的npm包管理命令都会不太记得，好记性不如烂笔头，还是都赶紧记一记好了；

### npm命令

#### 配置

##### 查看修改命令

```shell
$ npm config set <key> <value> [–global]
# 获取npm配置
$ npm config get <key>
# 获取npm当前镜像地址
$ npm config get registory
# 删除npm配置
$ npm config delete <key>
# 删除代理设置
$ npm config delete proxy
# 在编辑器中打开npm配置文件
$ npm config edit
```

##### 修改镜像地址

```shell
#查看
npm config get registry
#修改
npm config set registry http://registry.npm.taobao.org  //将registry设置为淘宝镜像
```

#### 升级

```shell
$ npm -g install npm ( 最新稳定版 ) 或
$ npm -g install npm@2.9.1 ( 指定版本 )
## 其他模块
$ npm update [-g] [<name> [<name> … ]]
#更新指定name列表中的模块。-g参数更新全局安装的模块。

#如果没有指定name，且不是在某个模块内，会更新当前目录依赖的所有包都会被更新（包括全局和模块内）；如果当前目录在某个模块目录内，会更新该模块依赖的模块，所以不指定name直接运行npm update时，最好在某个模块内运行，以免更新到其他不想更新的模块。
```

#### 发布项目到npm

```shell
# 1. 在官网注册npm账号
# 2. 用户验证，命令行执行
$ npm adduser
# 3. 发布模块，在模块的根文件夹执行
$ npm publish
# 4. 更新版本
# 如果是git库时，会为新版本号创建一条提交信息，package版本号会自动递增。
$ npm version 0.0.4
$ npm publish
```

#### 创建package.json文件

```shell
$ npm init
```

#### 安装模块

```shell
$ npm install <name> [–save|–save-dev|–save-optional]
# 安装并更新package.json中的版本配置
# 添加–save 参数安装的模块的名字及其版本信息会出现在package.json的dependencies选项中
# 添加–save-dev 参数安装的模块的名字及其版本信息会出现在package.json的devDependencies选项中
# 添加–save-optional 参数安装的模块的名字及其版本信息会出现在package.json的optionalDependencies选项中
```
#### 删除模块

```shell
$ npm rm <name>
$ npm r <name>
$ npm uninstall <name>
$ npm un <name>
```

#### 更新模块

```shell
$ npm update [-g] [<name> [<name> … ]]
# 更新指定name列表中的模块。-g参数更新全局安装的模块。
```

#### 执行脚本

```shell
$ npm run []
```

### 其他

#### 可选参数说明

```shell
--save // 将模块依赖关系写入到package.json文件的dependencies参数中
-dev // 将模块依赖关系写入到package.json文件的devDependencies参数中
-g // 表示全局
@+version // 安装指定版本
```



#### 参考网站

[Phoenix_Black](https://www.jianshu.com/u/9e41392f1b7b)

[NPM中文网](https://www.npmjs.com.cn/cli/npm/)

[菜鸟教程](https://www.runoob.com/nodejs/nodejs-npm.html)