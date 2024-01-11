### 1️⃣ uni-app + vue3 + vite4 + 🍍pinia + uni-mini-router + uviewPlus 基础框架

### 2️⃣ 流程图

![流程图](/src/static/imgs/flowChart/20230711143944.png)

### 3️⃣ 工程说明

```shell
1.全局封装svg组件; # (用法：<svg-icon name="xxx" class="xxx" />)
2.基于eslint统一代码规范;
3.基于prettier统一代码风格;
4.基于pinia完成对数据的状态管理;
5.基于vite4完成对uni-app的打包;
6.基于auto-imports减少文件引入;
7.基于uni.request统一封装请求拦截和响应拦截;
8.基于uviewPlus完成对uni-app的UI组件的封装;
9.基于uni.storage统一进行数据缓存并进行aes加密;
10.基于uni-mini-router统一处理路由配置和路由鉴权;
11.基于uniapp组件和uviewPlus组件,封装动态表单; 
# f_input:输入框
# f_checkbox：单选|多选
# f_textarea：多行文本
# f_calendar：日历选择器
# f_datetimePicker：时间弹出选择器
# f_dataPicker：单列选择器

# 1.用法：
<h-form ref="hForm" :formData="formData"></h-form>

# 2.校验表单：通过ref获取表单组件实例，调用formCheck方法
const hForm = ref(null) # 获取表单组件实例
const onSubmit = (data) => {
  hForm.value.formCheck().then((res) => {
    console.log("提交的表单数据", res.data)
  }).catch((err) => {
    console.log("校验失败", err)
  })
})

# 3.表单重置：通过ref获取表单组件实例，调用resetForm方法
const onCancel = () => {
  hForm.value.resetForm()
}
```

### 4️⃣ 平台兼容性说明

```shell
1.小程序：解决使用deep修改样式,在小程序中不生效的问题
    <!--uniapp中小程序样式穿透问题-->
    <!--#ifdef MP-WEIXIN-->
    <script>
    export default {
      options: { styleIsolation: "shared" }
    }
    </script>
    <!--#endif-->
```

### 5️⃣ 工程目录

```shell
|- XXX项目                  
    ├─ src
    │   ├─api # 接口相关
    │   │   ├─ api # api
    │   │   │    ├─login.js
    │   │   │    └─ ...
    │   │   └─ ...
    │   │
    │   ├─assets # 静态资源目录
    │   │   └─...
    │   │
    │   ├─components # 组件目录
    │   │   └─...
    │   │
    │   ├─config # 配置文件
    │   │   ├─ index.js # 全局配置文件
    │   │   ├─ env.development.js # 开发环境配置文件
    │   │   └─ env.production.js # 生产环境配置文件
    │   │
    │   ├─http # request相关目录
    │   │   ├─ request.js # request封装
    │   │   └─ status.js # 状态码
    │   │
    │   ├─pages # 页面
    │   │   ├─ home # 首页
    │   │   │    └─index.vue
    │   │   └─...
    │   │
    │   ├─pagesA # 分包页面（小程序）
    │   │   ├─ list # 列表页
    │   │   │    ├─test1.vue
    │   │   │    └─...
    │   │   └─ ...
    │   │
    │   ├─router # 路由
    │   │   ├─ index.js # 路由配置
    │   │   ├─ guard.js # 路由守卫
    │   │   └─ ...
    │   │
    │   ├─static # 静态公共文件
    │   │   ├─ imgs # 图片
    │   │   │    └─...
    │   │   ├─ svgs # svgs
    │   │   └─ ...
    │   │
    │   ├─store # 状态管理模式(pinia)
    │   │   ├─ modules # 数据模块
    │   │   │    ├─login.js
    │   │   │    └─...
    │   │   │
    │   │   └─ index.js
    │   │
    │   ├─uni_modules # uniapp官方组件库（注：git提交时不能忽略）
    │   │    ├─ ...
    │   │    └─ uni-scss # scss
    │   │
    │   ├─utils # 工具类
    │   │    ├─ cache # 缓存
    │   │    ├─ AES  # aes 加密
    │   │    └─ util.js # 工具类
    │   │ 
    │   └─ App.vue
    │   └─ main.js
    │   └─ auto-imports.d.ts # 自动导入
    │   └─ manifest.json
    │   └─ pages.json
    │   └─ shime-uni.d.ts
    │   └─ uni.scss
    │ 
    │
    ├─ .gitignore
    ├─ .prettierrc.js
    ├─ index.html
    ├─ package.json
    ├─ README.md
    └─ vite.config.ts
```

