<div align="center">
  <a href="https://nicelinks.site?from=github">
    <img width="200" height="200" src="https://raw.githubusercontent.com/nicejade/quickapp-boilerplate-template/master/src/assets/images/logo.png" alt="快应用脚手架模板">
  </a>
</div>

<h1 align="center">快应用脚手架模板</h1>

<div align="center">
  🔨 致力于构建更为优雅的<strong><a href="">快应用</a></strong>开发脚手架模板
</div>

<br>

<div align="center">
  <a href="https://circleci.com/gh/nicejade/quickapp-boilerplate-template">
    <img src="https://circleci.com/gh/nicejade/quickapp-boilerplate-template/tree/master.svg?style=svg" alt="Build Status">
  </a>
  <a href="https://nodejs.org/en/">
    <img src="https://img.shields.io/badge/node-%3E=%206.0.0-green.svg" alt="node version">
  </a>
  <a href="https://nicelinks.site/post/5c16083e819ae45de1453caa">
    <img src="https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat" alt="Prettier">
  </a>
  <a href="https://github.com/nicejade/quickapp-boilerplate-template">
    <img src="https://img.shields.io/github/license/nicejade/quickapp-boilerplate-template.svg" alt="LICENSE">
  </a>
  <a href="https://nice.lovejade.cn/zh/article/quickapp-boilerplate-template.html">
    <img src="https://img.shields.io/badge/chat-on%20blog-brightgreen.svg" alt="Chat On My Blog">
  </a>
  <a href="https://aboutme.lovejade.cn/?from=github"><img src="https://img.shields.io/badge/Author-nicejade-%23a696c8.svg" alt="Author nicejade"></a>
</div>

## 组织结构

```
├── sign                # 存储 rpk 包签名模块;
│   ├── debug           # 调试环境证书/私钥文件
│   └── release         # 正式环境证书/私钥文件
└── src
│   ├── assets          # 公用的资源(images/styles/字体...)
│   │   ├──images       # 存储 png/jpg/svg 等公共图片资源
│   │   ├──js           # 存储公共 javaScript 代码资源
│   │   └──styles       # 存放 less/css/sass 等公共样式资源
│   ├── helper          # 项目自定义辅助各类工具
│   │   ├──apis         # 存储与后台请求接口相关(已封装好)
│   │   ├──ajax.js      # 对系统提供的 fetch api 进行链式封装
│   │   └──utils        # 存放项目所封装的工具类方法
│   ├── pages           # 统一存放项目页面级代码
│   ├── app.ux          # 应用程序代码的人口文件
│   └── manifest.json   # 配置快应用基本信息
└── package.json        # 定义项目需要的各种模块及配置信息
```

## 如何使用

```bash
npm i -g poetry-cli

# 创建RN项目
poetry init my-project

# ? 请选择使用的模板
  umi
❯ quickapp
  taro
  electron
  next

yarn start # 推荐 ✅✅

# 或者运行以下命令
yarn server & yarn watch

# 或者在终端一 Tab 下运行：
yarn server
# 在终端另一 Tab 下运行：
yarn watch

# ✨ 新增「快应用」页面
yarn gen YourPageName
```

用一台 `Android` 手机，下载安装[「快应用」调试器](https://www.quickapp.cn/docCenter/post/69)，打开后操作`扫码安装`，扫描如上命令生成的二维码，即可看到效果；更多讯息，请参见[快应用环境搭建](https://nice.lovejade.cn/zh/article/develop-quick-app-experience-notes.html#环境搭建)。

## 改进优势

有必要谈及的是，此项目秉承在[高效开发 Web 单页应用解决方案](https://nice.lovejade.cn/zh/article/vue-webpack-boilerplate-template.html)中所传递的理念：为**高效开发**而设计；相比于其内置的简陋 Demo，她具有以下诸多优点：

- [x] **对项目结构进行优化**；如上组织结构所示，将各资源模块，更专业的分门别类，使之可以便捷的去编写、维护、查找，同时也是基于前端开发既定共识去设计，更容易为初接触者所理解 & 上手；
- [x] **更优雅的处理数据请求**；采用 `Promise` 对系统内置请求 `@system.fetch` 进行封装，并抛出至全局，使得可以极简的进行链式调用，同时便捷地处理返回数据，并能够使用  `finally`，设计详情可参见[如何优雅处理「快应用」数据请求
](https://quickapp.lovejade.cn/how-to-elegantly-handle-quickapp-request/)；
- [x] **内置了样式处理方案**；「快应用」支持 `less`, `sass` 的预编译；这里采取 `less` 方案，并内置了部分变量，以及常用混合方法，使得可以轻松开启样式编写、复用、修改等；
- [x] **封装了常用方法**；在 `helper/utils` 路径下，有对日期、字符串、系统等常用方法，分别进行封装，统一暴露给 `global.$utils`，使得维护方式更加合理且健壮，同时又可以便捷的使用，高效开发；当然，你也可以根据需要自行增删、抑或扩展；
- [x] **简化开始开发流程**； 注入 [Concurrently](https://github.com/kimmobrunfeldt/concurrently) 插件，使可以运行 `yarn start` 即可开始开发，而无需更多命令，从而简洁开发流程；
- [x] **优化本地开发端口设定**；「快应用」默认端口为 `12306`，虽说可自定义端口，但使用体验却不够友好；此处参考 `creat-react-app` 设定，对本地开发地址端口使用进行优化：如果 🈯️ 定端口(默认: `8080`)被占用，则向上递增寻找新的可用端口(如：8081 / 8082 / … )；
- [x] **浏览器打开调试主页二维码**；运行 `yarn start`，会启动 HTTP 调试服务器，并将该地址在**命令行终端**显示，手机端用快应用调试器扫码，即可下载并运行 rpk 包；当终端积累的信息流多了，就造成扫码不便；故增设在浏览器打开调试主页二维码；如想不使用此功能，在 _command/server.js_ 文件中，将 **autoOpenBrowser** 设置为 `false` 即可；
- [x] **集成轻粒子统计分析**； [轻粒子](https://nicelinks.site/post/5bdfa8ba9fa22b1b40974f63)作为官方推荐统计方案，此脚手架已做接入；使用时只需修改 [statistics.config.js](https://github.com/nicejade/quickapp-boilerplate-template/blob/master/src/assets/js/statistics.config.js) 中的 `app_key`，为在[轻粒子](http://www.qinglizi.cn/)所申请的快应用 KEY 即可；
- [x] **添加新增页面命令脚本**；使得可以一键生成新页面，只需运行：`yarn gen YourPageName` （命名推荐统一为大驼峰，将会在 `pages` 路径下新建该页面文件夹）命令即可，当然，也可以根据需要，自行定定制模板：*/command/gen/template.ux*；
- [x] **集成 [Prettier](https://prettier.io/) & [Eslint](https://eslint.org/)**；在检测代码中潜在问题的同时，统一团队代码规范、风格（`js`，`less`，`scss`等），从而促使写出高质量代码，以提升工作效率(尤其针对团队开发)。
- [x] **编写 [prettier-plugin-quickapp](https://github.com/nicejade/prettier-plugin-quickapp) 插件**；为快应用编写 `prettier` 插件，使其可以针对 `.ux`/`.mix` 文件也能很好地工作，从而进一步完善代码风格及规范。
- [x] **新增文件监听命令**：引入 [onchange](https://github.com/Qard/onchange) 依赖来监听文件变化；使得在开发时，运行 `yarn prettier-watch` 命令，即可对所修改的 `*.md` `*.ux` `*.js` 等文件，进行 **Prettier** 格式化，从而大幅度提升编写效率。
- [ ] ... ...

## 内置命令

|  命令 | 描述  | 备注 |
|---|---|---|
| `yarn start`  | 开启服务(server)和监听(watch)  | 附魔[多步优化](https://nice.lovejade.cn/zh/article/quickapp-boilerplate-template.html#%E6%94%B9%E8%BF%9B%E4%BC%98%E5%8A%BF)，一键开启开发，强烈推荐 ✔️|
| `yarn server`  | 开启服务(server)  | 如不嫌麻烦，可使用，不推荐 |
| `yarn watch`  | 开启监听(watch)  | 如不嫌麻烦，可使用，不推荐 |
| `yarn build ` | 编译打包，生成 `rpk`包  | 对内置 `hap build` 命令的转接 |
| `yarn release ` | 生成 `rpk`包并增加签名  | 对内置 `hap release` 命令的转接  |
| `yarn gen `  | 新增「快应用」页面 | 助你高效生成页面，模版可自定义，推荐 ✓|
| `yarn prettier`  | 一键美化代码(js/css/less/ux)  | 实在是团队开发好帮手，推荐 ✓ |
| `yarn prettier-watch`  | 对变化代码文件格式、实时美化 | 极大提升代码编写效率，强烈推荐 ✔️|

