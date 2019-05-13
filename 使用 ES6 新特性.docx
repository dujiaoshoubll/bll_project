webpack + Babel 使用 ES6 新特性
webpack 是一个模块加载器兼打包工具，Babel 是一款转码编译器，可以很方便地将 ES6、ES7 等当前浏览器不兼容的 JavaScript 新特性转码为 ES5 等当前浏览器普遍兼容的代码。将两者结合起来可以很方便地在项目中一边使用 ES6 编写代码，一边自动生成 ES5 代码
webpack & Babel
安装 webpack
npm install webpack -g
或者
npm init
npm install webpack --save-dev
安装 Babel 相关组件
# 安装加载器 babel-loader 和 Babel 的 API 代码 babel-core
npm install --save-dev babel-loader babel-core
# 安装 ES2015（ES6）的代码，用于转码
npm install babel-preset-es2015 --save-dev
# 用于转换一些 ES6 的新 API，如 Generator，Promise 等
npm install --save babel-polyfill
你可以在以下页面查看 JavaScript 的所需的转换代码模块进行按需安装
http://babeljs.io/docs/plugins/preset-es2015/
配置
类似于 Grunt 和 Gulp，webpack 也有其特定地配置文件 webpack.config.js
如下配置使用babel：
module.exports = {
    entry: [
        "babel-polyfill",
        "./index.js"
    ],
    output: {
        path: __dirname + '/output/',
        publicPath: "/output/",
        filename: 'index.js'
    },
    module: {
        loaders: [
            {
                test: /\.jsx?$/,
                exclude: /(node_modules|bower_components)/,
                loader: 'babel-loader', // 'babel-loader' is also a legal name to reference
                query: {
                    presets: ['es2015']
                }
            }
        ]
    }
};
•	entry——用于设置 webpack 执行打包文件的入口，是一个数组
•	output——用于指定生成文件的路径以及文件名等
o	path——指定生成文件路径
o	publicPath——指定域名公共路径
o	filename——指定生成文件的名称
•	module——主要用于配置 loaders
o	loaders——用于配置对应后缀的文件使用何种加载器进行处理
	test——使用正则表达式来指定某种特定的文件类型
	exclude——排除某个文件夹下的文件进行处理
	loader——指定相应的加载器，多个加载器使用 ! 进行连接，每个 loader 都可以省略其后缀，如 babel-loader 可以写成 babel
	query——指定加载器的配置信息，也可以使用 ? 直接连接在 loader 后面
以上只是涉及到我目前用到的一些配置信息的说明，更多的配置信息可以查阅官方文档，地址如下：
https://webpack.github.io/docs/configuration.html
开始
在有 webpack.config.js 文件的目录下使用一下命令行：
•	webpack——直接启动 webpack，默认配置文件为 webpack.config.js
•	webpack -w——监测启动 webpack，实时打包更新文件
•	webpack -p——对打包后的文件进行压缩
更多的命令可以查看官方文档下的说明，地址如下：
http://webpack.github.io/docs/cli.html


