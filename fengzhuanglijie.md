# 封装的思路

## 针对ims项目：

> 封装之前 要完成一次数据请求的过程：

1. 在vue的原型上 定义axios对象 给 vue实例调用：

2. view 页面触发事件 
 this.axios.get(请求的访问服务器地址的路由,{请求的数据})
3. router api:
创建生成访问服务器的地址（router.get(url,methods) methdos:controller中的方法 用来操作数据库的方法）

4. constoller 调用kenx.js


导致：在每个页面 都直接调用 vue实例上axios对象；


## 实现封装：

`this.axios.get(methods)(url,data)):
Methods:axios对象的方法；
URL：访问服务器的地址；
data:请求所携带的参数；
将上面三者提取出来 （pageOBJ.Methods(require.methods,data);`

***

    本次项目对封装的误解原因： router api 路径 只要请求类型不一样路径相同不受影响 

    试想一下  如果每次进行请求操作 路径都不相同 那么 封装路径 就变得毫无意义了  

    请求所有客户： /api/user
    请求修改客户：/api/user/edit/:id
    删除单个客户：/api/user/del/:id

    竟然封装的核心是提取公共部分，减少重复代码，和 便于 扩展 和维护代码 

    那么 api 的路劲 必然是 统一的 /api/user

    对于代码的封装 应该从 要封装的（执行过程开始到结束） 代码执行最后最尾最都督的位置 为突破口 
    然后 慢慢 回退 利用模块的思想 

    我中有你 一层一层嵌套  a<b<c 

