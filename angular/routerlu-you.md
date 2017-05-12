# 路由
>使用路由有至少3个步骤

1. 定义路由配置
>路由配置是一个Routes类型的数组。

2. 创建根路由模块
>跟路由模块包含了路由所需的各项服务，是路由工作流程得以正常执行的基础。
*根路由默认策略为PathLocationStrategy,需设置一个base路径

3. 添加RouterOutlet指令

## 路由策略
1. PathLocationStrategy(使用path部分来进行路由匹配)
>为服务器端渲染提供了可能
*浏览器需支持HTML5的history.pushState()方法

2. HashLocationStrategy(使用hash部分来进行路由匹配)
> 原理是利用了浏览器在处理hash部分的两个特性
*发送请求时不会带上hash部分的内容
*更改hash部分不会重新发送请求

## 路由跳转
1. 使用指令跳转
>使用RouterLink指令。
2. 使用代码跳转
>可以使用Router.navigateByUrl()或者Router.navigate()来跳转。