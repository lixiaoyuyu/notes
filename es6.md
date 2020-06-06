[TOC]



### **Symbol**

1.获取方式

1.1获取对象含有的所有symbol属性

 Object.getOwnPropertySymbols()

2 获取对象的所有属性包括symbol属性

Reflect.ownKeys(obj)



2.全局symbol (无论设置环境的symbol是否在全局)

全局设置

Symbol.for() 

全局获取

Symbol. keyFor ()



### **String**

1. `String.fromCharCode()`方法，不 可以识别大于`0xFFFF`的字符

​    `String.fromCodePoint()`方法，可以识别大于`0xFFFF`的字符， 

**2。实例方法**

- **includes()**：返回布尔值，表示是否找到了参数字符串。      
- **startsWith()**：返回布尔值，表示参数字符串是否在原字符串的头部。
- **endsWith()**：返回布尔值，表示参数字符串是否在原字符串的尾部。
-  `trimStart()`消除字符串头部的空格，`trimEnd()`消除尾部的空格 
-  `padStart()`用于头部补全，`padEnd()`用于尾部补全。        'xxx'.padEnd(2, 'ab') // 'xxx'
-  `repeat`（）方法返回一个新字符串，表示将原字符串重复`n`次。  'na'.repeat('3') // "nanana"
-  `matchAll()`方法返回一个正则表达式在当前字符串的所有匹配，

###  **Number**

1.数值方法

-  `Number.isFinite()`用来检查一个数值是否为有限的（finite），即不是`Infinity`。 
-  `Number.isNaN()`用来检查一个值是否为`NaN`。  

​       全局方法`isFinite()`和`isNaN()`的区别在于，传统方法先调用`Number()`将非数值的值转为数值，再进行判          断，而这两个新方法只对数值有效，

-   ES6 将全局方法`parseInt()`和`parseFloat()`，移植到`Number`对象上面，行为完全保持不变。 

```javascript
Number.parseInt === parseInt // true
Number.parseFloat === parseFloat
```

-  `Number.isInteger()`用来判断一个数值是否为整数。 
-  `Number.MAX_SAFE_INTEGER`和`Number.MIN_SAFE_INTEGER`这两个常量，用来表示这个范围的上下限。

​      `Number.isSafeInteger()`则是用来判断一个整数是否落在这个范围之内。  ( JavaScript 能够准确表示的整数范围在`-2^53`到`2^53`之间（不含两个端点） ) 

### Math

-  `Math.trunc`方法用于去除一个数的小数部分，返回整数部分。 （ 对于非数值，`Math.trunc`内部使用`Number`方法将其先转为数值。 ）

```javascript
Math.trunc(NaN);      // NaN
Math.trunc('foo');    // NaN
Math.trunc();         // NaN
Math.trunc(undefined) // NaN
```

### 函数

1.函数属性

-  指定了默认值以后，函数的`length`属性，将返回没有指定默认值的参数个数。也就是说，指定了默认值后，`length`属性将失真。 

-  函数的`name`属性，返回该函数的函数名。 `bind`返回的函数，`name`属性值会加上`bound`前缀。函数表达式如果函数有名字 只能在内部使用 name 值为命名的值（函数会在上下文中选择合适的值赋值给name）

2.箭头函数

箭头函数有几个使用注意点。

（1）函数体内的`this`对象，就是定义时所在的对象，而不是使用时所在的对象。

（2）不可以当作构造函数，也就是说，不可以使用`new`命令，否则会抛出一个错误。

（3）不可以使用`arguments`对象，该对象在函数体内不存在。如果要用，可以用 rest 参数代替。

（4）不可以使用`yield`命令，因此箭头函数不能用作 Generator 函数。

### Array

1. Array方法

-  `Array.from`方法用于将两类对象转为真正的数组：类似数组的对象（array-like object）和可遍历（iterable）的对象（包括 ES6 新增的数据结构 Set 和 Map）  参数是一个真正的数组，`Array.from`会返回一个一模一样的新数组。 

-  `Array.of`方法用于将一组值，转换为数组。 

2.实例方法

-  copyWithin( target ，start,end)  在当前数组内部，将指定位置的成员复制到其他位置（会覆盖原有成员），然后返回当前数组（不包括末尾） 

-  `find`(target)方法，用于找出第一个符合条件的数组成员  直到找出第一个返回值为`true`的成员，然后返回该成员。如果没有符合条件的成员，则返回`undefined`。 

-  findIndex(target)  返回第一个符合条件的数组成员的位置，如果所有成员都不符合条件，则返回`-1`。 

-  `fill`(val,start,end)方法使用给定值，填充一个数组。 (不包括末尾)

-    `keys()`是对键名的遍历、`values()`是对键值的遍历，`entries()`是对键值对的遍历。 

-   includes 返回一个布尔值，表示某个数组是否包含给定的值，  第二个参数表示搜索的起始位置，默认为`0` 

-  `flat()`用于将嵌套的数组“拉平”，变成一维的数组。该方法返回一个新数组 ( `flat()`默认只会“拉平”一层，如果想要“拉平”多层的嵌套数组，可以将`flat()`方法的参数写成一个整数，表示想要拉平的层数，默认为1 )

-  `flatMap()`方法对原数组的每个成员执行一个函数（相当于执行`Array.prototype.map()`），然后对返回值组成的数组执行`flat()`方法。该方法返回一个新数组，不改变原数组。 

-  `in`运算符  判断指定位置是否有值  

  ```javascript
  0 in [undefined, undefined, undefined] // true
  0 in [, , ,] // false
  ```



### Object

1. 对象的属性，有两种方法。

   ```javascript
   // 方法一
   obj.foo = true;
   
   // 方法二
   obj['a' + 'bc'] = 123;
   ```

 一是直接用标识符作为属性名，方法二是用表达式作为属性名， 对象方法同样适用

2.对象方法

-  函数的`name`属性，返回函数名。对象方法也是函数，因此也有`name`属性。 

-  如果对象的方法使用了取值函数（`getter`）和存值函数（`setter`），则`name`属性不是在该方法上面，而是该方法的属性的描述对象的`get`和`set`属性上面，返回值是方法名前加上`get`和`set`。 

  ```javascript
  const obj = {
    get foo() {},
    set foo(x) {}
  };
  
  obj.foo.name
  // TypeError: Cannot read property 'name' of undefined
  
  const descriptor = Object.getOwnPropertyDescriptor(obj, 'foo');
  
  descriptor.get.name // "get foo"
  descriptor.set.name // "set foo"
  ```

-  `bind`方法创造的函数，`name`属性返回`bound`加上原函数的名字；`Function`构造函数创造的函数，`name`属性返回`anonymous`。 

  Symbol 值，那么`name`属性返回的是这个 Symbol 值的描述。 

3.可枚举性 需注意以下

- `for...in`循环：只遍历对象自身的和继承的可枚举的属性。

- `Object.keys()`：返回对象自身的所有可枚举的属性的键名。

- `JSON.stringify()`：只串行化对象自身的可枚举的属性。

- `Object.assign()`： 忽略`enumerable`为`false`的属性，只拷贝对象自身的可枚举的属性

4.对象的遍历次序

- 首先遍历所有数值键，按照数值升序排列。
- 其次遍历所有字符串键，按照加入时间升序排列。
- 最后遍历所有 Symbol 键，按照加入时间升序排列。

5.super

-  `super`，指向当前对象的原型对象。 

- ```javascript
  const proto = {
    x: 'hello',
    foo() {
      console.log(this.x);
    },
  };
  
  const obj = {
    x: 'world',
    foo() {
      super.foo();
    }
  }
  
  Object.setPrototypeOf(obj, proto);
  
  obj.foo() // "world"
  ```

6.对象也可以使用扩展运算符

-  扩展运算符后面不是对象，则会自动将其转为对象 

-  扩展运算符后面是一个空对象，则没有任何效果。 

-  由于数组是特殊的对象，所以对象的扩展运算符也可以用于数组。 

- ```javascript
  let foo = { ...['a', 'b', 'c'] };
  foo
  // {0: "a", 1: "b", 2: "c"}
  
  {...{}, a: 1}
  // { a: 1 }
  
  // 等同于 {...Object(1)}
  {...1} // {}
  ```

7.链判断运算符  ？.

- `obj?.prop` // 对象属性

- `obj?.[expr]` // 同上

- `func?.(...args)` // 函数或对象方法的调用

- ```javascript
  a?.b
  // 等同于
  a == null ? undefined : a.b
  
  a?.[x]
  // 等同于
  a == null ? undefined : a[x]
  
  a?.b()
  // 等同于
  a == null ? undefined : a.b()
  
  a?.()
  // 等同于
  a == null ? undefined : a()
  ```

7.1 短路机制 

   - ```javascript
     a?.[++x]
     // 等同于
     a == null ? undefined : a[++x]
     ```

 ，如果`a`是`undefined`或`null`，那么`x`不会进行递增运算。也就是说，链判断运算符一旦为真，右侧的表达式就不再求值。 

7.2 delete 运算符 

```javascript
delete a?.b
// 等同于
a == null ? undefined : delete a.b
```

 上面代码中，如果`a`是`undefined`或`null`，会直接返回`undefined`，而不会进行`delete`运算。 

7.3 括号的影响 

```javascript
(a?.b).c
// 等价于
(a == null ? undefined : a.b).c
```

  如果属性链有圆括号，链判断运算符对圆括号外部没有影响，只对圆括号内部有影响。 ，`?.`对圆括号外部没有影响，不管`a`对象是否存在，圆括号后面的`.c`总是会执行。  一般来说，使用`?.`运算符的场合，不应该使用圆括号。 

8.Null 判断运算符`??`

-  它的行为类似`||`，但是只有运算符左侧的值为`null`或`undefined`时，才会返回右侧的值  (还未支持)

```javascript
const animationDuration = response.settings?.animationDuration ?? 300;
```

-  如果多个逻辑运算符一起使用，必须用括号表明优先级，否则会报错。 

9.对象新增方法

-  Object.is（val1,val2）  用来比较两个值是否严格相等，与严格比较运算符（===）的行为基本一致。
-  `Object.assign`方法用于对象的合并 ( 第一个参数是目标对象，后面的参数都是源对象 ，值不能为null或undefine,不是目标对象则不影响)   如果目标对象与源对象有同名属性，或多个源对象有同名属性，则后面的属性会覆盖前面的属性。  属性名为 Symbol 值的属性，也会被`Object.assign`拷贝   实行的是浅拷贝， 

-  `Object.getOwnPropertyDescriptor()`方法会返回某个对象属性 （非继承属性） 的描述对象 

-  `__proto__`属性（前后各两个下划线），用来读取或设置当前对象的原型对象  
- `Object.setPrototypeOf()`（ 用来设置一个对象的原型对象 ）、
- `Object.getPrototypeOf()`（ 用于读取一个对象的原型对象 ）、 
- 原型必须为对象或者null
-  Object.keys  返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（enumerable）属性的键名。 
-  `Object.values`方法返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（enumerable）属性的键值。 
-  `Object.entries()`方法返回一个数组，成员是参数对象自身的（不含继承的）所有可遍历（enumerable）属性的键值对数组。 
-  `Object.fromEntries()`方法是`Object.entries()`的逆操作，用于将一个键值对数组转为对象。 

### Set（new set([任意值]) 初始化）

 它类似于数组，但是成员的值都是唯一的，没有重复的值。 

1.实例方法

- `Set.prototype.size`：返回`Set`实例的成员总数。

1.1操作方法（用于操作数据）

- `Set.prototype.add(value)`：添加某个值，返回 Set 结构本身。
- `Set.prototype.delete(value)`：删除某个值，返回一个布尔值，表示删除是否成功。
- `Set.prototype.has(value)`：返回一个布尔值，表示该值是否为`Set`的成员。
- `Set.prototype.clear()`：清除所有成员，没有返回值

1.2 遍历方法， 

`Set.prototype.keys()`：返回键名的遍历器

`Set.prototype.values()`：返回键值的遍历器

`Set.prototype.entries()`：返回键值对的遍历器

`Set.prototype.forEach()`：使用回调函数遍历每个成员

### weakSet （同set但是值必须为对象 且是有应用的对象）

- WeakSet 结构与 Set 类似，也是不重复的值的集合 
- WeakSet 的成员只能是对象 
- WeakSet 中的对象都是弱引用，即垃圾回收机制不考虑 WeakSet 对该对象的引用  （如果weakSet的属性没有了引用 会被垃圾回收，但set不会）

1.实例方法

- **WeakSet.prototype.add(value)**：向 WeakSet 实例添加一个新成员。
- **WeakSet.prototype.delete(value)**：清除 WeakSet 实例的指定成员。
- **WeakSet.prototype.has(value)**：返回一个布尔值，表示某个值是否在 

### Map

-  数组，任何具有 Iterator 接口、且每个成员都是一个双元素的数组的数据结构都可以当作`Map`构造函数的参数 
- 各种类型的值（包括对象）都可以当作键 
-  对同一个键多次赋值，后面的值将覆盖前面的值。 
-  只有对同一个对象的引用，Map 结构才将其视为同一个键 

```javascript
const map = new Map();

map.set(['a'], 555);
map.get(['a']) // undefined
```

 上面代码的`set`和`get`方法，表面是针对同一个键，但实际上这是两个不同的数组实例，内存地址是不一样的，因此`get`方法无法读取该键，返回`undefined`。 

  Map 的键实际上是跟内存地址绑定的，只要内存地址不一样，就视为两个键 

1.实例方法

1.1操作方法

- `size`属性返回 Map 结构的成员总数。
-  **Map.prototype.set(key, value)**  `set`方法设置键名`key`对应的键值为`value`，然后返回整个 Map 结构。如果`key`已经有值，则键值会被更新，否则就新生成该键。  可以采用链式写法。 
- **Map.prototype.get(key)**  `get`方法读取`key`对应的键值，如果找不到`key`，返回`undefined` 
- **Map.prototype.has(key)**`has`方法返回一个布尔值，表示某个键是否在当前 Map 对象之中
- **Map.prototype.delete(key)**`delete`方法删除某个键，返回`true`。如果删除失败，返回`false`。
- **Map.prototype.clear()**`clear`方法清除所有成员，没有返回值。

1.2 遍历方法

- `Map.prototype.keys()`：返回键名的遍历器。
- `Map.prototype.values()`：返回键值的遍历器。
- `Map.prototype.entries()`：返回所有成员的遍历器。
- `Map.prototype.forEach()`：遍历 Map 的所有成员。

### WeakMap

- `WeakMap`只接受对象作为键名（`null`除外），不接受其他类型的值作为键名。 
- 键名所引用的对象都是弱引用  只要所引用的对象的其他引用都被清除，垃圾回收机制就会释放该对象所占用的内存 
- WeakMap 弱引用的只是键名，而不是键值。键值依然是正常引用。 

### Class

-  `class`可以看作只是一个语法糖 

-  定义“类”的方法的时候，前面不需要加上`function`这个关键字，直接把函数定义放进去了就可以了。另外，方法之间不需要逗号分隔 

-  ，类的数据类型就是函数，类本身就指向构造函数。 

-  类的所有方法都定义在类的`prototype`属性上面。 

-  在类的实例上面调用方法，其实就是调用原型上的方法。 

-  ，类的内部所有定义的方法，都是不可枚举的 

-  类必须使用`new`调用 

- 实例的属性除非显式定义在其本身（即定义在`this`对象上），否则都是定义在原型上（即定义在`class`上）。 

-  类的所有实例共享一个原型对象。

-  可以通过实例的`__proto__`属性为“类”添加方法。  

-  类和模块的内部，默认就是严格模式 

-  **不存在提升** 

-  如果在一个方法前，加上`static`关键字，就表示该方法不会被实例继承，而是直接通过类来调用，这就称为“静态方法”。  如果静态方法包含`this`关键字，这个`this`指的是类，而不是实例。  静态方法可以与非静态方法重名。  父类的静态方法，可以被子类继承。

- 

-    静态属性指的是 Class 本身的属性，即`Class.propName`，而不是定义在实例对象（`this`）上的属性。 

- ```javascript
  // 老写法
  class Foo {
    // ...
  }
  Foo.prop = 1;
  
  // 新写法
  class Foo {
    static prop = 1;
  }
  ```

-  在“类”的内部可以使用`get`和`set`关键字，对某个属性设置存值函数和取值函数，拦截该属性的存取行为。 

- ```javascript
  class MyClass {
    get prop() {
      return 'getter';
    }
    set prop(value) {
      console.log('setter: '+value);
    }
  }
  
  let inst = new MyClass();
  inst.prop = 123;
  // setter: 123
  inst.prop
  // 'getter'
  ```

**继承**

-  Class 可以通过`extends`关键字实现继承， 

-  子类必须在`constructor`方法中调用`super`方法，否则新建实例时会报错 

-  在子类的构造函数中，只有调用`super`之后，才可以使用`this`关键字 

  

 **`super`关键字** 

-  既可以当作函数使用，也可以当作对象使用。 
-  `super`作为函数调用时，代表父类的构造函数  `super`虽然代表了父类`A`的构造函数，但是返回的是子类`B`的实例，即`super`内部的`this`指的是`B`的实例 
-  `super`作为对象时，在普通方法中，指向父类的原型对象；在静态方法中，指向父类。  定义在父类实例上的方法或属性，是无法通过`super`调用的 
-  在子类普通方法中通过`super`调用父类的方法时，方法内部的`this`指向当前的子类实例。 
-  使用`super`的时候，必须显式指定是作为函数、还是作为对象使用， 
-  Class 作为构造函数的语法糖，同时有`prototype`属性和`__proto__`属性，因此同时存在两条继承链。  子类的`__proto__`属性，表示构造函数的继承，总是指向父类。  子类`prototype`属性的`__proto__`属性，表示方法的继承，总是指向父类的`prototype`属性。 

1.`constructor`方法 

-  `constructor`方法是类的默认方法，通过`new`命令生成对象实例时，自动调用该方法。一个类必须有`constructor`方法，如果没有显式定义，一个空的`constructor`方法会被默认添加。 
-  `constructor`方法默认返回实例对象（即`this`），完全可以指定返回另外一个对象。 
-   实例属性除了定义在`constructor()`方法里面的`this`上面，也可以定义在类的最顶层。

 2.`new.target`属性 

-  `new`是从构造函数生成实例对象的命令 
-  该属性一般用在构造函数之中，返回`new`命令作用于的那个构造函数 
-  如果构造函数不是通过`new`命令或`Reflect.construct()`调用的，`new.target`会返回`undefined` 
-  Class 内部调用`new.target`，返回当前 Class。  子类继承父类时，`new.target`会返回子类。 

### Module

-  `export`命令用于规定模块的对外接口，`import`命令用于输入其他模块提供的功能。 
-   ES6 模块输出的是值的引用。
-    ES6 模块是编译时输出接口。 
-   ES6 模块不是对象，它的对外接口只是一种静态定义，在代码静态解析阶段就会生成。 

1.export

- `export`命令除了输出变量，还可以输出函数或类（class）。 
- `export`输出的变量就是本来的名字，但是可以使用`as`关键字重命名。 
- `export`命令规定的是对外的接口，必须与模块内部的变量建立一一对应关系。 
- `export`语句输出的接口，与其对应的值是动态绑定关系，即通过该接口，可以取到模块内部实时的值。 
- `export`命令可以出现在模块的任何位置，只要处于模块顶层就可以 

1.1 `export default`命令 

-  为模块指定默认输出。  

- 其他模块加载该模块时，`import`命令可以为该匿名函数指定任意名字。  用在非匿名函数前，也是可以的 

-  一个模块只能有一个默认输出 

-   本质上，`export default`就是 输出一个叫做`default`的变量或方法，然后系统允许你为它取任意名字 

-  `export default`命令其实只是输出一个叫做`default`的变量，所以它后面不能跟变量声明语句。  可以直接将一个值写在`export default`之后  export default 42;

  ```javascript
  // 正确
  export var a = 1;
  // 正确
  var a = 1;
  export default a;
  // 错误
  export default var 
  
  export default a的含义是将变量a的值赋给变量default  a = 1;             
  ```

2.import 

- `import`命令接受一对大括号，里面指定要从其他模块导入的变量名。大括号里面的变量名，必须与被导入模块对外接口的名称相同。 

- 如果想为输入的变量重新取一个名字，`import`命令要使用`as`关键字，将输入的变量重命名。 

- `import`命令输入的变量都是只读的，因为它的本质是输入接口。也就是说，不允许在加载模块的脚本里面，改写接口。  如果`a`是一个对象，改写`a`的属性是允许的。 

- `import`后面的`from`指定模块文件的位置，可以是相对路径，也可以是绝对路径，`.js`后缀可以省略。如果只是模块名，不带有路径，那么必须有配置文件，告诉 JavaScript 引擎该模块的位置。 

- `import`命令具有提升效果，会提升到整个模块的头部，首先执行。 

- `import`是静态执行，所以不能使用表达式和变量 

- `import`语句会执行所加载的模块 

- 多次重复执行同一句`import`语句，那么只会执行一次，而不会执行多次。 

-  目前阶段，通过 Babel 转码，CommonJS 模块的`require`命令和 ES6 模块的`import`命令，可以写在同一个模块里面，但是最好不要这样做 

-  在一条`import`语句中，同时输入默认方法和其他接口 

  ```javascriptj
  import _, { each, forEach } from 'lodash';
  ```

2.1整体加载

-  除了指定加载某个输出值，还可以使用整体加载，即用星号（`*`）指定一个对象，所有输出值都加载在这个对象上面。 

  ```javascript
  import * as circle from './circle';
  
  console.log('圆面积：' + circle.area(4));
  console.log('圆周长：' + circle.circumference(14));
  ```

-  模块整体加载所在的那个对象（上例是`circle`），应该是可以静态分析的，所以不允许运行时改变 

3.export 与 import 的复合写法 

-  如果在一个模块之中，先输入后输出同一个模块，`import`语句可以与`export`语句写在一起。 

  ```javascript
  export { foo, bar } from 'my_module';
  
  // 可以简单理解为
  import { foo, bar } from 'my_module';
  export { foo, bar };
  ```

   `export`和`import`语句可以结合在一起，写成一行。但需要注意的是，写成一行以后，`foo`和`bar`实际上并没有被导入当前模块，只是相当于对外转发了这两个接口，导致当前模块不能直接使用`foo`和`bar`。 

4.加载实现

-  浏览器通过` script `标签加载 JavaScript 脚本。 

-  默认情况下，浏览器是同步加载 JavaScript 脚本，即渲染引擎遇到`` script ``标签就会停下来，等到执行完脚本，再继续向下渲染。如果是外部脚本，还必须加入脚本下载的时间。  如果脚本体积很大，下载和执行的时间就会很长，因此造成浏览器堵塞 

-  浏览器允许脚本异步加载 

  ```html
  <script src="path/to/myModule.js" defer></script>
  <script src="path/to/myModule.js" async></script>
  ```

    <script>标签打开defer或async属性，脚本就会异步加载。渲染引擎遇到这一行命令，就会开始下载外部脚本，但不会等它下载和执行，而是直接执行后面的命令。  
        defer与async的区别是：defer要等到整个页面在内存中正常渲染结束（DOM 结构完全生成，以及其他脚本执行完成），才会执行；async一旦下载完，渲染引擎就会中断渲染，执行这个脚本以后，再继续渲染。一句话，defer是“渲染完再执行”，async是“下载完就执行”。另外，如果有多个defer脚本，会按照它们在页面出现的顺序加载，而多个async脚本是不能保证加载顺序的。

-  浏览器加载 ES6 模块，也使用``标签，但是要加入`type="module"`属性。 

  ```
  <script type="module" src="./foo.js"></script>
  ```

-  浏览器对于带有`type="module"`的``，都是异步加载，不会造成堵塞浏览器，即等到整个页面渲染完，再执行模块脚本，等同于打开了``标签的`defer`属性。 

-  如果网页有多个``，它们会按照在页面出现的顺序依次执行。 async属性也可以打开 一旦使用了`async`属性，``就不会按照在页面出现的顺序执行，而是只要该模块加载完成，就执行该模块。 

-  ES6 模块也允许内嵌在网页中，语法行为与加载外部脚本完全一致。 

- 加载外部模块要注意

  ```
  - 代码是在模块作用域之中运行，而不是在全局作用域运行。模块内部的顶层变量，外部不可见。
  - 模块脚本自动采用严格模式，不管有没有声明`use strict`。
  - 模块之中，可以使用`import`命令加载其他模块（`.js`后缀不可省略，需要提供绝对 URL 或相对 URL），也可以使用`export`命令输出对外接口。
  - 模块之中，顶层的`this`关键字返回`undefined`，而不是指向`window`。也就是说，在模块顶层使用`this`关键字，是无意义的。
  - 同一个模块如果加载多次，将只执行一次
  ```

- 

- 