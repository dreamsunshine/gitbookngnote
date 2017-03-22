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