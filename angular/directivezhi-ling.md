# 指令
指令分为3类：属性指令、结构指令、组件
1、属性指令：以元素属性的形式来使用的指令
2、结构指令：可以用来改变dom树的结构，如NgIf
3、组件：被用来构造带有自定义行为的可重用视图。

#自定义属性指令
> 一个属性指令需要一个控制器类，使用@Directive来装饰，装饰器指定了用以标记指令所关联属性的选择器，控制器类实现指令对应的特定行为。

        import {Directive,ElementRef} from '@angular/core'
        
        @Directive({
                selector:'[myBeautifulBackground]'
        })
        export class BeautifulBackgroundDirective{
                constructor(el:ElementRef){
                        el.nativeElement.style.backgroundColor='yellow'
                }
        }
        
* 为指令绑定输入属性，使用@Input
* 响应用户操作，使用@HostListener装饰器

# 自定义结构指令
* 引入@Directive装饰器
* 添加css属性选择器
* 声明一个input属性
* 将装饰器应用在指令实现类上
        import {Directive,Input,TemplateRef,ViewContainerRef} from '@angular/core' 
        @Directive({selector:'[myUnless]'})
        export class UnlessDirective{
                @Input('myUnless') set condition(newCondition:boolean){
                        if(!newCondition){
                                this.viewContainer.cerateEmbeddedView(this.templateRef)
                        }else{
                                this.viewContainer.clear()
                        }
                }
                
                constructor(private templateRef:TemplateRef<any>,private viewContainer:ViewContainerRef){}
        }