
# 介绍
MOOC React 实战 —— 打造画廊应用 <br>
# 参考资源：
https://github.com/imzyf/gallery-by-react <br>
https://github.com/GigHubAccount/gallery-by-react
# 技术栈
* `React `框架
* `YEOMAN` 前端工具   [The web's scaffolding tool for modern webapps | Yeoman]( http://yeoman.io/)
* `Webpack` 前端自动化打包工具
* `HTML5/CSS3`
* `SCSS`编辑器
# 项目搭建
安装 Yeoman <br>
	`npm install -g yo` <br>
查看版本 <br>
`yo --version` <br>
安装 generator-react-webpack [Yeoman generator for ReactJS and Webpack](https://github.com/react-webpack-generators/generator-react-webpack)<br>

`npm install -g generator-react-webpack` <br>
查看generator-react-webpack的版本: <br>

在windows环境下：npm list --depth=0 -global <br>
Linux或者mac环境下：cnpm ls -g --depth=1 2>/dev/null | grep generator- <br>
生成项目 <br>
`yo react-webpack gallery-by-react` <br>
启动服务 <br>
`npm start` 或者`npm run serve` <br>

# 项目发布到github

## 使用相对地址 否则会报错
`cfg/default.js：`<br>
`publicPath: '/assets/',改为：publicPath: 'assets/',`
`src/index.html`
`<script type="text/javascript" src="/assets/app.js"></script>改成：<script type="text/javascript" src="assets/app.js"></script>`
## 项目打包
`npm run clean`  清空dist下的目录<br>
`npm run copy` 把src下的一级文件copy到dist目录<br>
`npm run dist`  把相应的资源文件打包到dist目录<br>
## 项目提交到 Git 仓库
` git status` <br>
` git add .` <br>
`git commit -m 'gallery-by-react'` <br>

## 推送到 GitHub Page：
` git push`<br>

# 遇到的问题
## 1 .scss文件无效 报错：cannot find module 'node-sass'
### 解决办法：通过淘宝的npm镜像安装node-sass
### 安装cnpm
` $ npm install -g cnpm --registry=https://registry.npm.taobao.org`  <br>
### 安装 node-sass
` $ cnpm install node-sass `<br>
ps:npm是美国的服务器，安装需要翻墙，速度很慢且可能失败，使用淘宝提供的cnpm更有效 <br>
## 2 git push到 GitHub时报错：fatal: unable to access 'https://github.com/YammyOne/gallery-by-react.git/': The requested URL returned error: 403
### 解决办法：在.git文件夹下的config文件中远程仓库url添加username@，如下
```
repositoryformatversion = 0
    filemode = false
    bare = false
    logallrefupdates = true
    symlinks = false
    ignorecase = true
[remote "origin"]
    url = https://YammyOne@github.com/YammyOne/gallery-by-react.git
    fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master

```


