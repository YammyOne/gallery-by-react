# 目录结构
> ---cfg  这里存放 webpack 配置
> > >---base.js  webpack 基础配置
> > >---defaults.js  webpack 一些其他的默认配置
> > >---dev.js       测试环境的 webpack 配置，启动 npm run start 的时候会使用这份 webpack 设置。
> > >---dist.js      线上环境的 webpack 配置，启动 npm run dist 的时候会使用。
> > >---test.js      做单元测试的时候使用 npm run test。
> ---dist           webpack 存放最终打包输出的用于生产环境的项目文件
> ---src                       # 存放开发环境项目源码
> >---/actions/               # flux actions目录（没用到）
> >---/components/            # 组件目录
> >---/config/                # 配置目录（没用到）
> >---/sources/               # flux datasources目录（没用到）
> >---/stores/                # flux stores(没用到)
> >---/styles/                # 样式文件目录，内有一个App.css基础css文件
> >---index.html              # 项目入口文件
> >---index.js                # js入口文件
> ---/test/                    # 单元测试和集成测试目录
> ---.babelrc                  # Babel 配置文件
> ---.editorconfig             # EditorConfig 插件配置文件，用于统一编码风格。
> ---.eslintrc                 # ESLint代码风格检测配置文件
> ---.gitignore                # 需要 git 同步时忽略文件夹的配置文件
> ---.yo-rc.json               # yeoman的配置文件
> ---karma.conf.js             # karma测试框架的配置
> ---package.json              # npm 的依赖配置项
> ---server.js                 # 项目运行的js文件，命令可查看package.json中的script
> ---webpack.config.js         # webpack配置文件，不同环境的配置项在cfg目录下
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




