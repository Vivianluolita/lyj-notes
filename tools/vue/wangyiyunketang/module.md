### 网易云课堂学习-10.30 如何理解模块化

降低系统可维护性，解耦成细小的模块

-  模块化开发历程
    1. ```function -》 namespace 对象 -》 立即执行函数```
        1. 所存在的问题，命名空间（不同文件里同名的常量window.name）,依赖管理（script标签引入的先后顺序）
    2. Common.js
        1. 每一个文件都是一个模块，都会有自己的作用域。
        2. 内置的对象 exports module require
        3. 加载时同步的，加载完后才能执行
        4. 定义一模块，a.js可以先加载b.js c.js，并且把b.c对象传入，再执行callback
        ```
            a.js 依赖前置
            define(['b.js','c.js'],function(b,c){
                //
            })

            b.js
            define(function(){
                return {
                    // 接口对象
                }
            })
        ```
       
    3. AMD
        
- AMD,Commmand,Es6 Modile

- 模块化的运作原理