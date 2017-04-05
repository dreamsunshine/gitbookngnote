#组件
    >组件用来包装特定的功能，是angular应用的最小逻辑单元。


* 创建一个组件只需3个步骤
    1. 从`@angular/core`中引入Component装饰器
    2. 建立一个普通的类，并用`@Component`装饰它
    3. 在`@Component`中，设置slector自定义标签和template模板
    
            //contactItem.component.ts
            import {Component} from '@angular/core'
            @Component({
                selector:'contact-item',
                template:`
                    <div>
                        <p>张三</p>
                        <p>13100000000</p>
                    </div>
                `
            })
            export class ContactItemComponent{}
    
    * 组件元数据
        1. selector(定义组件匹配的标签)
        2. template||templateUrl
        3.styles||styleUrls
    
    * 组件与模块
        使用@NgModule来创建模块，一个应用有多个模块，但只有一个根模块
        
                //app.mobule.ts
                import {NgModule} from '@angular/core'
                import {BrowserModule} from '@angular/platform-browser'
                import {ContactItemComponent} from './contactItem.component'
                import {platformBrowserDynamic} from '@angular/platform-browser-dynamic'
                @NgModule({
                    imports:[BrowserModule],
                    declarations:[ContactItemComponent],
                    bootstrap:[ContactItemComponent]
                })
                export class AppModule{}
                platformBrowserDynamic().bootstrapModule(AppModule)
                
        1. bootstra用于指定根组件，
        2. declarations用于指定属于这个模块的视图类（组件、指令、管道）
        3. exports导出视图类
        4. imports引入模块或者路由
        5. providers指定模块依赖的服务
        

* 组件交互
    
    1. 组件的输入输出属性（@Input  @Output）,组件元数据中亦可使用inputs、outputs
    2. 父组件向子组件传递数据
        * 通过@input完成数据输入
        * setter拦截输入属性
        * ngOnchanges监听数据变化
    3. 子组件向父组件传递数据（通常使用事件传递）
    4. 通过局部变量实现数据交互
    5. 使用@ViewChild实现数据交互