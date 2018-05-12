# Object.defineProperty
js中神奇的Object.defineProperty方法

 
这个方法可牛比了。这么说吧，vue.js是通过它实现双向绑定的。俗称属性拦截器。
而且专门用来监控对象属性变化的Object.observe方法也被草案发起人撤回了(此方法在node环境中仍能使用)。
可见defineProperty的威力之大。


首先看一下官方的定义：

Object.defineProperty()

方法会直接在一个对象上定义一个新属性，或者修改一个已经存在的属性， 并返回这个对象。
   语法：

              Object.defineProperty(obj,prop,descriptor)


            参数

            obj  需要定义属性的对象。

            prop 需定义或修改的属性的名字。

            descriptor 将被定义或修改的属性的描述符。


对象里目前存在的属性描述符有两种主要形式：(数据描述符) 和 (存取描述符)。
数据描述符是一个拥有可写或不可写值的属性。存取描述符是由一对 getter-setter 函数功能来描述的属性。
描述符必须是两种形式之一；不能同时是两者。


    (数据描述符) 和 (存取描述符) 均具有以下可选键值：

     configurable
     当且仅当该属性的 configurable 为 true 时，该属性描述符才能够被改变，也能够被删除。默认为 false。

     enumerable
    当且仅当该属性的 enumerable 为 true 时，该属性才能够出现在对象的枚举属性中。默认为 false。


数据描述符同时具有以下可选键值：

      value
      该属性对应的值。可以是任何有效的 JavaScript 值（数值，对象，函数等）。默认为 undefined。

    这也就是为神马

      writable
      当且仅当该属性的 writable 为 true 时，该属性才能被赋值运算符改变。默认为 false。
      
      
      
 
存取描述符（第三个参数对象）同时具有以下可选键值：

      get
      一个给属性提供 getter 的方法，如果没有 getter 则为undefined。
      当我们读取某个属性的时候，其实是在对象内部调用了该方法，此方法必须要有return语句。
      该方法返回值被用作属性值。默认为 undefined。

     set
     一个给属性提供 setter 的方法，如果没有 setter 则为 undefined。
     该方法将接受唯一参数，并将该参数的新值分配给该属性。
     默认为 undefined。也就是说，当我们设置某个属性的时候，实际上是在对象的内部调用了该方法。     
      

要注意的一点是：在 descriptor 中不能同时设置访问器（get 和 set）和 wriable 或 value，否则会错，
就是说想用 get 和 set，就不能用 writable 或 value 中的任何一个。      
      
      
      
      
      
      








