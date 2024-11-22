## BKFlow前端开发文档

### 目录结构

```md
|-- builds // webpack构建相关配置文件
|-- src
|  |-- App.vue
|  |-- api // 异步请求api配置
|  |  |-- ajax.ts // 请求方法
|  |  |-- cancelRequest.js  // 取消请求函数
|  |-- assets  // 静态资源目录
|  |-- components   公共组件
|  |  |-- layout // 导航栏组件
|  |  |-- DecisionTable  // 决策表组件
|  |  |-- ProcessCanvas // 横板画布
|  |  |-- VerticalCanvas // 竖版画布
|  |  |-- common
|  |  |   |-- modal // 异常状态弹框组件
|  |  |   |-- RenderForm // 根据配置自动生成表单组件
|  |  |   |-- searchSelect // 表格搜索框
|  |  |   |-- TableRenderHeader.vue // 表格自定义表头
|  |  |   |-- TableSettingContent.vue // 表格自定义设置功能
|  |  |   |-- TemplateCanvas // 画布组件（旧版）
|  |  |   |-- CodeEditor.vue // monaco-editor编辑器组件
|  |  |-- Individualization
|  |  |   |-- MemberSelect // 人员选择器
|  |-- config
|  |  |-- i18n  // 国际化组件
|  |-- constants  // 常量配置
|  |-- directives // 自定义指令
|  |-- main.js  // 入口文件
|  |-- views  // 各页面组件
|  |-- router  // 路由配置
|  |-- scss  // 样式
|  |-- store  // vuex
|  |-- utils  // 工具函数
|  |-- mixins  // 混入模块
|-- static // 打包后的文件
|  |-- css
|  |-- fonts
|  |-- img
|  |-- js
|  |-- index-prod.html
|  |-- login_success.html // 登录成功页
|  |-- json.works.js
```

### 主要依赖库
前端开发环境主要基于 vue 全家桶 + webpack, 组件主要使用magic-box vue组件库，主要依赖列表如下：

- vue
- vue-router
- vuex
- axios
- bk-magic-vue
- bkui-form
- element-ui
- antv/x6
- monaco-editor
- vee-validate
- xlsx
- xss

`若需要增加第三方依赖，优先选择前端团队其他项目有实际使用的，选择新依赖需要注意满足开源协议的要求。`

### 本地开发配置

- #### 安装依赖
```
npm install
```

- #### 代理配置
打开build/webpack.dev.conf.js   

`根据代理环境设置相应的SITE_URL，例如：const SITE_URL = '/xxx-xxx/'`   

在proxyPath里面添加需要代理的接口前缀, 例如：   
```
const proxyPath = [ 'api/', 'api/*' ]
```

在devServer.proxy设置代理理的接口, 例如：   
```
proxy: [{
    context,
    target: 'http://xxxx.xxxx.com',
    secure: false,
    changeOrigin: true,
    headers: {
    referer: 'http://xxxx.xxxx.com',
}]
```

打开index-dev.html   

`根据代理环境设置默认SITE_URL和APP_CODE`

- #### 项目运行
```
npm run dev
```

### 开发注意：

1.**决策表**
- 导入、导出（协议比较复杂）
  协议地址：https://tapd.woa.com/tapd_fe/70120217/story/detail/1070120217119248396?from_iteration_id=1070120217001983577

2.**X6画布**
`X6画布是一套新版画布，但流程的数据格式还是旧版的。故需要前端将格式转为X6画布支持的格式，函数地址：utils/graphJson.js`


### 代码规范

编写前端代码时应遵循:

- [蓝鲸前端团队的通用规范](http://radosgw.open.oa.com/bkapp-dev-guide-prod/%E5%89%8D%E7%AB%AF%E5%BC%80%E5%8F%91%E8%A7%84%E8%8C%83/index.html)
- vue 官方推荐的书写规范
- 项目代码规范（已配置 eslint），本地开发时 eslint 校验 vue 文件若出现错误，则必须解决问题后提交代码
