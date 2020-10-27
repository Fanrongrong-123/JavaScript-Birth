## JavaScript发展史

        今天我就来扒一扒JavaScript的发展史。
        学习一门语言得从它的历史开始，这样好像就能切身的感受这门语言的设计者初衷，理解javascript的语法的由来，更利于之后的学习思维。
        JavaScript的创造者——布莱登，布莱登的主要的兴趣和方向是函数式编程，被公司临危受命，要求给浏览器添加一个脚本功能而且必须看上去与Java足够相似，但是比Java简单。布莱登为了应付差事只是用了十天事件把javascript设计出来了（不是实现）。为了更直观的表达这门新语言与Java的相似所以被命名为JavaScript。
        JavaScript的兴起是在2004年的愚人节，谷歌发布了在线网页Gmail,用来完成Gmail的技术之一就是JavaScript。javascript的诞生之初只是一个不起眼的小功能，布莱登可能也没想到可以用它来完成这么强大的应用。（如果布莱登能预见到，未来这种语言会这么流行，他会不会多花一点时间呢）
        现在的JavaScript每年更新一版，很难想象在1999年~2009年这十年间JavaScript没有更新一版，其中的第四版还死在了摇篮里。究其原因还是微软当时如日中天，不支持JavaScript。JavaScript母公司（网景）被微软（把IE6捆绑在xp系统里）搞得很狼狈。
        到这里JavaScript的发展史就讲完了，希望会对你有所帮助。
## JavaScript缺陷

1. 不适合开发大型程序

        Javascript没有名称空间（namespace），很难模块化；没有如何将代码分布在多个文件的规范；允许同名函数的重复定义，后面的定义可以覆盖前面的定义，很不利于模块化加载。


2. 非常小的标准库

        Javascript提供的标准函数库非常小，只能完成一些基本操作，很多功能都不具备。

3. null和undefined

        null属于对象（object）的一种，意思是该对象为空；undefined则是一种数据类型，表示未定义。（在编程实践中，null几乎没用）
        typeof null; // object
        typeof undefined; // undefined

        两者非常容易混淆，但是含义完全不同。
        var foo;
        alert(foo == null); // true
        alert(foo == undefined); // true
        alert(foo === null); // false
        alert(foo === undefined); // true

4. 全局变量难以控制

        Javascript的全局变量，在所有模块中都是可见的；任何一个函数内部都可以生成全局变量，这大大加剧了程序的复杂性。
        a = 1;
        (function(){
            b=2;
            alert(a);
            })(); // 1
            alert(b); //2

5. 自动插入行尾分号

       Javascript的所有语句，都必须以分号结尾。但是，如果你忘记加分号，解释器并不报错，而是为你自动加上分号。有时候，这会导致一些难以发现的错误。

       比如，下面这个函数根本无法达到预期的结果，返回值不是       一个对象，而是undefined。
       
       　　function(){
       
       　　　　return
       　　　　　　{
       　　　　　　　　i=1
       　　　　　　};
       　　}
       
       原因是解释器自动在return语句后面加上了分号。
       
       　　function(){

       　　　　return;
       　　　　　　{
       　　　　　　　　i=1
       　　　　　　};
       　　}
       
6. 加号运算符

       +号作为运算符，有两个含义，可以表示数字与数字的和，也可以表示字符与字符的连接。
       
       　　alert(1+10); // 11
       
       　　alert("1"+"10"); // 110
       
       如果一个操作项是字符，另一个操作项是数字，则数字自动转化为字符。
       
       　　alert(1+"10"); // 110
       
       　　alert("10"+1); // 101
       
       这样的设计，不必要地加剧了运算的复杂性，完全可以另行设置一个字符连接的运算符。
       
7. NaN

       NaN是一种数字，表示超出了解释器的极限。它有一些很奇怪的特性：
       
       　　NaN === NaN; //false
       
       　　NaN !== NaN; //true
       
       　　alert( 1 + NaN ); // NaN
       
       与其设计NaN，不如解释器直接报错，反而有利于简化程序。

8. 数组和对象的区分

       由于Javascript的数组也属于对象（object），所以要区分一个对象到底是不是数组，相当麻烦。Douglas Crockford的代码是这样的：
       
       　　if ( arr &&
       　　　　typeof arr === 'object' &&
       　　　　typeof arr.length === 'number' &&
       　　　　!arr.propertyIsEnumerable('length')){
       
       　　　　alert("arr is an array");
       
       　　}
       
9. == 和 ===

        ==用来判断两个值是否相等。当两个值类型不同时，会发生自动转换，得到的结果非常不符合直觉。
        
        　　"" == "0" // false
        
        　　0 == "" // true
        
        　　0 == "0" // true
        
        　　false == "false" // false
        
        　　false == "0" // true
        
        　　false == undefined // false
        
        　　false == null // false
        
        　　null == undefined // true
        
        　　" \t\r\n" == 0 // true
        
        因此，推荐任何时候都使用"==="（精确判断）比较符。

10. 基本类型的包装对象

        Javascript有三种基本数据类型：字符串、数字和布尔值。它们都有相应的建构函数，可以生成字符串对象、数字对象和布尔值对象。
        
        　　new Boolean(false);
        
        　　new Number(1234);
        
        　　new String("Hello World");
        
        与基本数据类型对应的对象类型，作用很小，造成的混淆却        很大。
        
        　　alert( typeof 1234); // number
        
        　　alert( typeof new Number(1234)); // object
        


        
