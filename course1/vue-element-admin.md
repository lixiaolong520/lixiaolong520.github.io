[vue-element-admin 官方指南](https://panjiachen.github.io/vue-element-admin-site/zh/guide/)

# 准备
## package.json
scripts节点：相当于在命令和里直接输入script中的命令
```json
{
   "scripts": {
    "dev": "vue-cli-service serve",
    "build:prod": "vue-cli-service build",
    "build:pre": "vue-cli-service build --mode pre", 
    "build:dev": "vue-cli-service build --mode dev",
    "preview": "node build/index.js --preview",
    "lint": "eslint --ext .js,.vue src",
    "test:unit": "jest --clearCache && vue-cli-service test:unit",
    "test:ci": "npm run lint && npm run test:unit",
    "svgo": "svgo -f src/icons/svg --config=src/icons/svgo.yml",
    "new": "plop"
  }
}
```
mode 后边的对应的是根目录.env.development,.env.pre等文件名
dependencies和devDependencies的区别


## eslint
禁用方法：
vue.config.js文件中增加如下代码
```javascript
   chainWebpack(config){
        config.module.rules.delete('eslint')
   } 

```
单个禁用可以修改.eslintrc.js

## plop
[说明](https://medium.com/@nicoespeon/plop-a-micro-generator-to-ease-your-daily-life-7767f0a34db)
自动生成文件名View Component 命令行创建工具


## mock.js
[Mock.js官网文档](https://github.com/nuysoft/Mock/wiki/Getting-Started)
## webpack config
### devtool 配置sourceMap类型
### dev_Server
### externals
### resolve
### watchOptions.aggregateTimeout 编译延迟
### 修改端口号
修改vue.config.js文件中
```javascript
// If your port is set to 80,
// use administrator privileges to execute the command line.
// For example, Mac: sudo npm run
    const port = 9527 // dev port
```
   


## dev-tools
[离线安装地址](https://github.com/vuejs/vue-devtools)
## store,directive,filter目录

---
## axios修改所有请求头
找到项目文件 src/utils/request.js,VUE_APP_BASE_API 为.env.[mode]文件中配置的值
```javascript
const service = axios.create({
  baseURL: process.env.VUE_APP_BASE_API, // url = base url + request url
  withCredentials: false, // send cookies when cross-domain requests
  timeout: 50000, // request timeout
  headers: {
    'Content-Type': 'application/json; charset=UTF-8',
    // 'Proxy-Connection':'keep-alive',
    'Accept': '*/*'
  }, 
})
```

截获所有的Response
```javascript
// response interceptor
service.interceptors.response.use( 
  response => {
    const res = response.data
    // if the custom code is not 20000, it is judged as an error.
    if (response.status !== 200 && response.status !== 204) {
      // 50008: Illegal token; 50012: Other clients logged in; 50014: Token expired;
      if (res.code === 401) {
        // to re-login
        MessageBox.confirm('登录超时，请重新登录', '确认退出', {
          confirmButtonText: '重新登录',
          cancelButtonText: '取消',
          type: '警告'
        }).then(() => {
          store.dispatch('user/resetToken').then(() => {
            location.reload()
          })
        })
      }else{
        Message({
          message: res.message || 'error',
          type: 'error',
          duration: 5 * 1000
        })
        return Promise.reject(res.message || '接口错误')
      }

    } else {
      return res
    }
  },
  error => {
    console.log('err' + error) // for debug
    Message({
      message: error.message,
      type: 'error',
      duration: 5 * 1000
    })
    return Promise.reject(error)
  }
)
```
##封装现有的Jquery插件为Vue component
//Audio为Jquery插件
```html
<template>
  <audio :src="url" class="txb-audio" controls="controls">
    您的浏览器不支持
  </audio>
</template>
```
```javascript 
  require('@/utils/txb/audio');
  export default {
    name: 'myAudio',
    props: {
      url: {
        type: String
      }
    },
    mounted() {
      $(this.$el).Audio();
    },
    data() {
      return {
        dialogTableVisible: false
      }
    }
  } 
```
##路由和权限控制
###基础参考文件
src/permission.js
src/router
src/store/modules/user.js
其中permission.js中
> NProgress为导航条插件
> router.beforeEach 和 router.afterEach 是页面进入退出的总控制中心 
###左侧导航的权限控制
组件名：src/layout/components/Sidebar/index.vue
mapgetters中permission_routes为权限过滤后的菜单列表

##使用背景图片
1. 放入src/assets文件夹中
2. 参考代码,@符号前边需要增加~
```css
.ui-audio {
    background: url(~@/assets/audio.png) 10px center no-repeat #009688;
    background-size: 18px 18px;
    cursor: pointer;
    border: 1px solid #cad6df;
    height: 24px;
    line-height: 24px;
    width: 100px;
    border-radius: 5px
  }
```
##基础颜色样式修改
src/styles文件中variables.scss文件定义了各种颜色变量

##mixin的使用
mixin相当于多继承，在高级语言java .net中 一个类只能继承一个父类，可以实现多个接口
而通过mixin设计模式，可以让Vue实例多继承多个父类
参考vue-element-admin中的chart模块resize mixin



# question:
1. this.$nextTick什么时候用？
2. Vue的Computed有什么用，解决了什么问题？
3. vuex有什么用，解决了什么问题？
4. sass有什么用，解决了什么问题？

# realworld question:
<img src="pics/列表枚举.png" alt="drawing" width="500" height="300"/>
写法:
```javascript
export const binds = [
  {key: "", text: "绑定状态"},
  {key: "1", text: "已绑定"},
  {key: "0", text: "未绑定"}
];
export const bindsMap = makeMap(binds);
```
<img src="pics/编辑页面.png" alt="drawing" width="300" height="200"/>
问题：
1. 当修改时候怎么绑定时候重新赋值Form对象
2. 新增时候 怎么做Form表单验证 动态添加出来的组件

答案：




   