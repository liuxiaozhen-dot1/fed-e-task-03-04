什么是SSR
Vue SSR（Vue.js Server-Side Rendering） 是 Vue.js 官方提供的一个服务端渲染（同构应用）解
决方案
使用它可以构建同构应用
还是基于原有的 Vue.js 技术栈
官方文档的解释：Vue.js 是构建客户端应用程序的框架。默认情况下，可以在浏览器中输出 Vue
组件，进行生成 DOM 和操作 DOM。然而，也可以将同一个组件渲染为服务器端的 HTML 字符
串，将它们直接发送到浏览器，最后将这些静态标记"激活"为客户端上完全可交互的应用程序。
服务器渲染的 Vue.js 应用程序也可以被认为是"同构"或"通用"，因为应用程序的大部分代码都可
以在服务器和客户端上运行。

```js

// 创建一个 Vue 实例
 const Vue = require("vue"); const app = new Vue({ template: `<div>{{ message }}</div>`, data: { message: "Hello World", }, }); 
//创建一个 renderer
  const renderer = require("vue-server-renderer").createRenderer();
// 将 Vue 实例渲染为 HTML
 renderer.renderToString(app, (err, html) => { if (err) throw err; console.log(html); 
```

服务端渲染
renderer.renderToString 渲染了什么？
renderer 是如何拿到 entry-server 模块的？
createBundleRenderer 中的 serverBundle
server Bundle 是 Vue SSR 构建的一个特殊的 JSON 文件
entry：入口
files：所有构建结果资源列表
maps：源代码 source map 信息
server-bundle.js 就是通过 server.entry.js 构建出来的结果文件
最终把渲染结果注入到模板中
（2）客户端渲染
vue-ssr-client-manifest.json
publicPath：访问静态资源的根相对路径，与 webpack 配置中的 publicPath 一致
all：打包后的所有静态资源文件路径
initial：页面初始化时需要加载的文件，会在页面加载时配置到 preload 中
async：页面跳转时需要加载的文件，会在页面加载时配置到 prefetch 中
modules：项目的各个模块包含的文件的序号，对应 all 中文件的顺序；moduleIdentifier和 和all数组中文件的映射关系（modules对象是我们查找文件引用的重要数据）

##### Gridsome

- Gridsome 是由Vue.js驱动的Jamstack框架，用于构建默认情况下快速生成的静态生成的网站和应用。
- Gridsome是Vue提供支持的静态站点生成器，用于为任何无头CMS，本地文件或API构建可用于CDN的网站
- 使用Vue.js，webpack和Node.js等现代工具构建网站。通过npm进行热重载并访问任何软件包，并使用自动前缀在您喜欢的预处理器（如Sass或Less）中编写CSS。
- 基于 Vue.js 的 Jamstack 框架
- Gridsome 使开发人员可以轻松构建默认情况下快速生成的静态生成的网站和应用程序
- Gridsome允许在内容里面引用任何CMS或数据源。
从WordPress，Contentful或任何其他无头CMS或API中提取数据，并在组件和页面中使用GraphQL访问它。

使用场景
- 不适合管理系统
- 简单页面展示
- 想要有更好的 SEO
- 想要有更好的渲染性能





