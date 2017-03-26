# 基本类型
boolean、number、string、array、tuple(元组)、enum（枚举）、any、null、undefined、void、never

* 数组类型：

    `let arr:number[]或者arr:Array<number>`
* 元组类型:表示已知元素数量和类型的数组
    
    `let x:[number,string]`
* 枚举类型

    `enum Color {Red,Green,Blue};`
    `let c:Color=Color.green;`

#声明和解构
    * let const具有块级作用域
    ## 解构
    
        * 数组解构
            
            `let input:number[]=[1,2]`
            `let [first,second]=input`
        * 对象解构
        
            `let test={x:0,y=2}`
            `let {x,y}=test`

#函数
    * 参数及返回值均可声明类型
        
        ·function test(x:string):string{return x;}·
    
    * 函数重载   >根据参数类型判断调用
    * 箭头函数自动绑定this
#类
    * 实例
        
        class Car {
        
            engine:string;
            
            constructor (engine:string) {
            
                this.engine=engine
                
            }   
        }
        
                      
    * 继承与多态
        ## 使用extends即可实现继承，派生类构造函数必须调用super()
        
    * 修饰符（public、private、protected）
    
    * 静态属性(static)
    
    * 抽象类（abstract,必须包含抽象方法、切不能直接实例化）
    
#模块
    * 使用import或export导入导出
    
    * 设计原则
        * 尽可能顶层导出
        * 明确地列出导入的名字
        * 使用命名空间模式导出
        * 使用模块包装进行扩展:导出新对象实现新功能

#接口
1. 属性类型接口
        interface Fullname{
            firstName:string;
            lastName:string;
        }
2. 函数类型接口   :   (需明确函数的参数列表和返回值类型)
        interface encrypt{
            (val:string,salt:string):string
        }
3. 可索引类型接口(描述通过索引得到的类型，比如Obj[0])   
        interface UserArray{
            \[index:number]:string
        }
4.  类类型接口
        interface Animal{
            name:string;
            setName(n:string):void;
        }
5. 接口扩展


#装饰器
1. 装饰器是一种特殊类型的声明，以@符号开始,返回函数
2. 方法装饰器：应用于方法的属性描述符上，用来监视、修改或替换方法定义，运行时传入3个参数：类的原型对象，方法的名字，成员属性的描述
        class TestClass{
            @log
            testMethod(arg:string){
                return "logmsg:"+arg;
            }
        }
        function log(target:Object,propertyKey:string,descriptor:TypedPropertyDescriptor<any>){
            let origin=descriptor.value;
            descriptor.value=function(...args:any[]){
                console.log('args:'+JSON.stringify(args));
                let result=origin.apply(this,args);
                console.log('the result-'+result);
                return result;
            }
            return descriptor;
        }
3. 类装饰器:应用于类构造函数，监视、修改、替换类定义
4. 参数装饰器
5. 属性装饰器

#泛型