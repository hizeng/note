# ims 项目

## 模块化

> 数据库 API 路由 三者之间的关系

### 对应所在的文件夹位置

models: 是项目与数据库交互的模块本项目引用第三方库 knex去操作数据库
        根据库表不同的表 创建不同的model 实质就是抛出对应的实例方法 
        
controllers:  引用 实例方法 操作数据库的行为 如 （req,res,next) 

routes:(api) 访问api中的路径（路径可以随意定义，主要用来标识 在app.js 中添加 （'/api'）与 index(页面跳转路由区分)
             随后的方法就是 调用controllers 中的方法 

### 页面数据初始化
    有个概念：钩子函数（生命周期）
    利用 created(){} 此方法会在 页面渲染之前 调用



### 后台页面 与 服务器 之间的关系

1.express node.js:localhost:3000
（访问数据库的api 定义在这里）

2.vue  localhost:8080
（调用api的方法定义在这里）

上述两者之间进行通讯 vue要引用第三方库 axios 方可访问 express 中定义的api

### 关于页面单例的编辑 删除问题
触发1.vue view中定义的方法 
axios.get('/api/user/' + id) 

生成api:2.express: api.js 中定义的 路径('/user/:id',controllers.methods);

操作数据库:3.controllers: methods(req,res,next){
    let id = req.params.id;

    这里的id 获取来源于 vue view 请求路径（中的 id)
}





