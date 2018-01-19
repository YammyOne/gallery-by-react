showList(obj, level) {
        var sourceStruct = obj[0]
        var dirCount = 0
        var fileCount = 0
            // 字符集
        var charSet = {
            'node': '├── ', //节点
            'pipe': '│   ', // 上下链接
            'last': '└── ', // 最后的file或folder需要回勾
            'indent': '    ' // 缩进
        };

        function log(file, depth, parentHasNextSibling) {
           // console.log("log:")
            if (!parentHasNextSibling && depth.length > 1) {
                // Replace a pipe with an indent if the parent does not have a next sibling.
                depth[depth.length - 2] = charSet.indent;
            }
            if(file.lastIndexOf('/') > -1){
                file = file.substring(file.lastIndexOf('/')+1)
            }
            console.log(depth.join('') + file);
        }

        // 由于已经有缓存数据了，因此对数据进行遍历搜索
        // 如果type 是file 就不需要继续
        // 如果type 是directory 对临时数组
        function walk(path, depth, parentHasNextSibling) {
          //  console.log(path)

            var childrenLen = path.length - 1
           // console.log(childrenLen)
            var loop = true

            if (depth.length >= level) {
                loop = false
            }
            if (loop) {
                path.forEach(function walkChildren(child, index) {
                    var newdepth = !!depth ? depth.slice(0) : []
                    var isLast = (index >= childrenLen)

                    if (isLast) {
                        newdepth.push(charSet.last)
                    } else {
                        newdepth.push(charSet.node)
                    }
                    if(child.type == "file"){
                      log(child.name, newdepth, parentHasNextSibling)
                    }else{
                      log(child.path, newdepth, parentHasNextSibling)

                    }

                    if (child.type == "directory") {
                        var childPath = child.children
                        if (!isLast) {
                            newdepth.pop()
                            newdepth.push(charSet.pipe)
                        }
                        walk(childPath, newdepth, !isLast)
                    }

                })
                loop = !loop
            }

        }

        walk(sourceStruct.children, [])
        //console.log(sourceStruct)
        console.log('level:' + level)
        console.log('目录及文件罗列完毕')

    },

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
 解决办法：通过淘宝的`npm`镜像安装`node-sass` <br>
 安装`cnpm`<br>
` $ npm install -g cnpm --registry=https://registry.npm.taobao.org`  <br>
 安装 `node-sass`<br>
` $ cnpm install node-sass `<br>
ps:npm是美国的服务器，安装需要翻墙，速度很慢且可能失败，使用淘宝提供的cnpm更有效 <br>
## 2 git push到 GitHub时报错：fatal: unable to access 'https://github.com/YammyOne/gallery-by-react.git/': The requested URL returned error: `403`
 解决办法：在`.git`文件夹下的`config`文件中远程仓库`url`添加`username@`，如下<br>
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
    再次 git push 
    在弹框中输入github账户的用户名和密码即可成功！
 若继续报错`403`，则 再次修改，添加`username:password@`，如下 <br>
 ```
 repositoryformatversion = 0
    filemode = false
    bare = false
    logallrefupdates = true
    symlinks = false
    ignorecase = true
[remote "origin"]
    url = https://YammyOne:mypassword@github.com/YammyOne/gallery-by-react.git
    fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master

 ```

