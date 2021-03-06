# Typescript 学习笔记
## 开始学习Typescript

   1.安装typescript  运行命令 tsc 把ts文件转成js文件
   2.如果想要更方便的实现，全局安装  ts-node *命令：* npm install -g ts-node *注意版本8.10.2*
      或者参考：https://blog.csdn.net/Arno_2022/article/details/121513609

## Typescript 的静态类型 Static Typing

   1. 静态类型
   `const count : number = 1;`
   '：类型' 决定 变量count的类型，不可改变
   2. 自定义静态类型
   ```
      interface People {
         name: string,
         age: number
      }
   ```
   3. 基础静态类型和对象静态类型
      ###### 基础静态类型包括：string number null undefined boolean void symbol 等...
      ###### 对象基础类型 
         就像是*2.* 那样在对象中声明静态类型，不光可以是对象，也可以是一个数组
         比如：`const peo: string [] = ['张三','李四','王五']`
         表明在数组中的值都必须是字符串类型，而不能是其他类型
      ###### 类 *CLass* 
         （对象形式的对象类型）
         ```
            class Person{}
            const zhangsan : Person = new Person()
         ```
         声明 *zhangsan* 必须属于 *Person*类 
         （函数类型的对象类型）
         ```
            const people :()=>string =()=>{}
            // 
         ```
         声明 必须是一个函数并且有返回值是一个字符串
   4. 类型注解(*type annotation*)和类型推断(*type inference*)
      ###### 类型注解 ：number 
      告诉声明的变量是一个什么类型，就是类型注解
      ###### 类型推断 
      如果没有给定变量类型直接赋值，根据值判断类型，就是类型推断
      + 如果 <font color=#fca60b>TS</font> 能够自动分析变量类型，我们就什么也不需要做了
      + 如果 <font color=#fca60b>TS</font> 无法分析变量类型的话，我们就需要使用类型注解
   5. 函数参数 和 返回类型

      ```
         function sayHello(): void{
            console.log('Hello World')
         }
      ```
      *void* 无  表示函数没有返回值

      ```
         function errorFun(): never{
            throw new Error()
            console.log('Hello World')
         }
      ```
      *never* 永远执行不完 死循环  错误方法 *似乎没啥用*

      ```
         function add({one,two} : {one: number,two: number}): never{
            
            return one + two 
         }
         const total = add ({one:1,two:2})
      ```
      函数传参是一个对象
   6. 数组类型注解
      + 单一的
      ```
         const numberArr: number [] = [1,2,3]
         const stringArr: string [] = ['a','b','c']
         const undefinedArr: undefined [] = [undefined,undefined]
      ```
      + 多元的
      ```
         const arr: (number | string) [] = [2,'a',3]
      ```
      + 包含对象
      ```
      const peoples: {name: string,age: number}[] = [
         {name: '张三',age: 12},
         {name: '李四',age: 13}
      ]
      ```
      但是写起来麻烦，所以有一个方便的办法，
      + *类型别名 tyoe alias*
      ``` 
         type Lady = {name: string,age: number}
         const peoples : Lady[] = [
            {name: '张三',age: 12},
            {name: '李四',age: 12}
         ]
      ```
      + 也可以用类名 *Class*
      ``` 
         class Madam = {
            name: string;
            age: number;
         }
         const peoples : Madam[] = [
            {name: '张三',age: 12},
            {name: '李四',age: 12}
         ]
      ```
   7. <font color=#fca60b>元组</font>的使用和类型约束
      ```
         const arr : [string,string,number] = ['zhangsan','teacher',26]
      ```
      按顺序定义，更为严谨，元组
   8. <font color=#fca60b>interface 接口</font>
      在定义数据类型用的相同处比较多时，可以用interface来优化，
      和类型别名很相似，但是有一点不同
      就是类型别名是可以直接直接给类型，但是接口需要传递为一个对象
      更为严谨
      ```
         interface Girl {
            name: string;
            age: number;
            hight: number;
         }
         type Girl = string
      ```
      interface用于解耦，约束传入的参数，只要符合他规范的都可以传，
      class就必须精确的才行
      如果某个属性的值是可有可无的，那么
      ```
         interface Girl {
            name: string;
            age: number;
            hight: number;
            waistline ?: number;
         }
      ```
      Typescript同时也提供了可以写任何类型的值
      ```
         interface Girl {
            name: string;
            age: number;
            hight: number;
            waistline ?: number;
            [propname:string]:any;
         }
      ```
      










































注：MD语法参考>https://www.jianshu.com/p/191d1e21f7ed