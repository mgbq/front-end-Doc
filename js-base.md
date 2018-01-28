#js代码规范二（base）

  前端开发团队遵循和约定的代码书写规范，意在提高代码的规范性和可维护性, 同时良好的代码习惯也能充分体现个人的职业素养。

##基本格式

  1. 代码统一采用Tab缩进（4个空格，可以在编辑器设置），如：Eclipse 用户可以ctrl+shif+f功能键盘，为了统一缩进风格，大家可以用eclipse自定义团队缩进风格，然后然后导入，按住ctrl+shif+f格式化即。[参考](http://www.cnblogs.com/kungfupanda/archive/2012/09/05/2671597.html)

  2. 语句的结尾处必须用分号，这是一个好习惯，特别是在代码会被压缩的情况下。

  3. 模块代码AMD方式组织。define(), 模块依赖用 commonjs require()

    ```javascript
    define(function(require, exports, module) {
        'use strict';
    
        var _ = require('underscore');
    
        var queue = [];
    
        var initModule = function() {
            _.each(queue, function(v, i) {
                // do something
            });
        };
    
        module.exports = {
            init: initModule
        };
    });
    ```

  4. 字符串变量值统一用单引号(')

    ```javascript
    var s = 'hello world';
    var html = '<div class="header"></div>';
    console.log(s + ', my name is cat');
    ```

  5. 注意使用空格/空行

    完整示例
    
    ```javascript
    function walk(holder, key) {
    
        // The walk method is used to recursively walk the resulting structure so
        // that modifications can be made.
    
        var k, v, value = holder[key];
        if (value && typeof value === 'object') {
            for (k in value) {
                if (Object.prototype.hasOwnProperty.call(value, k)) {
                    v = walk(value, k);
                    if (v !== undefined) {
                        value[k] = v;
                    } else {
                        delete value[k];
                    }
                }
            }
        }
    
        return reviver.call(holder, key, value);
    }
    ```

    需要前后加空格的运算符包括:

    ```
    =, ==, ===, !=, !==, >, <, <=, >= , ? :, -, +, +=, -=, /, *, %, &&, &, ||, |, {}
    ```

    不需要出现空格的包括: ` ;, ., (), []`
                        
    后边带空格的包括:

    ```
    ,, if, for, while, do, catch, with, new,
    ```

    非三元表达式中的:

    ```javascript
    a += 2;
    b = true ? a : 1;
    ```

    括号中的参数之间加空格:

    ```javascript
    get(x, b, c);
    function get(a, b, c) {
        // work with a,b,c
    }
    ```

    注释符前后要有空格

    代码段前后保留空行, 类，方法，函数前后保留空行

  6. 避免使用全局变量, 如果不能避免则尽量减少数量;

  7. 三元操作符不要涉及大段的复杂的代码, 如果可以请改为 if else;

  8. 奇淫技巧必须注释, 注释应该更多地体现为什么要这样，而不是会怎么样;

  9. 将每条语句放置在一个单独的代码行中保持可读性, 不要出现 aNum++; anOtherNum++;在同一行, var 也一样;

    **(√)**
    
    ```javascript
    aNum++;
    anOtherNum++;
    ```

    **(╳)**

    ```javascript
    aNum++; anOtherNum++;
    ```

### 命名规范

  通常,使用 `functionNamesLikeThis`, `variableNamesLikeThis`, `ClassNamesLikeThis`, `EnumNamesLikeThis`, `methodNamesLikeThis`, 和 `SYMBOLICCONSTANTSLIKE_THIS`.

  1. 常规的命名方式

    ```javascript
    var variableNamesLikeThis = '...',  // 变量
        CONSTANTS_LIKE_THIS = '...';    // 常量
    
    // 函数
    function functionNamesLikeThis() {
        ...
    };
    
    // 构造类
    function ClassNamesLikeThis() {
        ...
    };
    
    // 方法&属性等
    ClassNamesLikeThis.methodNamesLikeThis = function(){
        ...
    };
    ```

  2. 属性和方法

    文件或类中的`私有`属性, 变量和方法名应该以下划线 "_" 开头.

    保护属性, 变量和方法名不需要下划线开头, 和公共变量名一样.

    方法名按描述过程或描述项的方式, 动名词结合. 来命名, 以小写字母开头, 连接词使用混合大小写的驼峰形式, 例如: `getAncestorByTagName`.

  3. 方法和函数参数

    函数的参数个数不固定时, 应该添加最后一个参数 args 为参数的个数. 你也可以不设置 args 而取代使用 arguments.

    可选和可变参数应该在 @param (Optional) 标记中说明清楚.

  4. Getters 和 Setters

    不强制要求使用Getters和Setters，但当你使用时，Getters应该命名成`getFoo()`形式，同理Setters应该名称成`setFoo(v)`形式

    对于返回值是布尔类型（Boolean）的Getters方法也可以写成`isFoo()`的形式

    ```javascript
    // 定义一个叫学生的构造类
    function Student() {
        ...
    };
    
    Student.prototype.getName = function() {
        ...
    };
    
    Student.prototype.setName = function(name) {
        ...
    };
    
    // 返回值为布尔类型的Getters方法
    Student.prototype.isGirl= function() {
        if (...) {
            return true;
        } else {
            return false;
        }
    };
    ```

  5. 私有

    如果你要把构造类的方法，变量或属性设置为私有的话，请用下划线开头来命名，如：“_privite”

  6. 文件名应该使用小写字符, 以避免在有些系统平台上不识别大小写的命名方式. 文件名以.js结尾, 不要包含除 "-"外的标点符号，jquery插件看情况定.

  7. 构造函数.

    使用首字母大写的形式, 通常为名词, 例如: `Class`;

    但是, 对于内部基类, 也就是不直接调用生成实例的基类, 使用 _ 和首字母大写的形式命名, 例如: `_Base`;

  8. 布尔值以 is 开头的驼峰形式, 例如 `var isGirl = true`;

  9. this命名, 尽量以能表达当前实例意义的名称, 通用命名为self;

    ```javascript
    Pager.protoype.goto = function() {
        var pager = this, index = page.currentIndex + 1;
        setTimeout(function() {
            page.doRequest(index);
        });
    };
    function foo1(){
        var self = this;
        setTimeout(function() {
            console.log(self.name);
        }, 1);
    }
    function foo2(name){
        var self = this;
        self.name = name;
        foo1.call(self);
    }
    ```

  10. 在循环中, 尽量使用单字符变量名称, 例如: i, j, k, m, n;

  11. 避免使用保留字或语言构造命名;

    ```
    abstract boolean break byte case catch char class const
    continue default do double else extends false final finally
    float for function goto if implements import in instanceof
    int interface long native new null package private protected
    public return short assets super switch synchronized this
    throw throws transient true try var void while with
    ```

  12. 尽量保持所有名称最短, 但是一定要保证名称具有描述性;

  13. js钩子命名必须以j开头的驼峰命名，并且不能此钩子不能有应用样式

    **(√)**
    
    ```html
    <button class="jSubmit">提交</button>
    <button id="jSubmit">提交</button>
    ```

    **(╳)**

    ```html
    <button class="submit">提交</button>
    <button id="submit">提交</button>
    ```

### 基本格式

  1. 变量声明

    变量使用var语句声明

    变量使用前必须先声明

    尽量减少使用全局变量，全局变量使用“g”开头

    同一作用域块内的变量尽量使用一个“var”语句来声明

    **(√)**

    ```javascript
    var gName = '';
    function foo() {
        var name = '...',
            sex = '...',
            age = '';
        ....
    };
    ```

    **(╳)**

    ```javascript
    var name = '';
    function foo() {
        var name = '...';
        var sex = '...';
        var age = '';
        ....
    };
    ```

  2. 字符串

    用单引号包裹：创建字符串对象时，优先使用单引号，当你的字符串中包含html代码片段时将格外方便

    ```javascript
    var myString = '待我长发及腰时那还是人吗？  不是，绝对是神！';
    ```

    长字符串:

    字符串太长需要换行时，不要使用转义符“\”来处理行尾的换行，请用字符串相加来替换

    在编译时, 不能忽略行起始位置的空白字符; "\" 后的空白字符会产生奇怪的错误; 虽然大多数脚本引擎支持这种写法, 但它不是 ECMAScript
    的标准规范.

    **(√)**

    ```javascript
    var myString = '带我长发及腰时'+
        '那还是人吗？ '+
        '不是，绝对是神！';
    ```

    **(╳)**

    ```javascript
    var myString = '带我长发及腰时 \
        那还是人吗？ \
        不是，绝对是神！ \';
    ```

  3. 常量

    常量的形式如: NAMES_LIKE_THIS, 即使用大写字符, 并用下划线分隔.

    ```javascript
    var SECONDS_IN_A_MINUTE = 60;
    ```

  4. 总是使用分号.

    如果仅依靠语句间的隐式分隔, 有时会很麻烦. 你自己更能清楚哪里是语句的起止.而且有些情况下, 漏掉分号会很危险:

  5. 函数声明

    尽量不要使用全局函数

    内部函数应该跟在 var 语句后面

    不要在语句块内声明函数，如果确实需要，请使用函数表达式：

    同一作用域块内的变量尽量使用一个“var”语句来声明

    **(√)**
    
    ```javascript
    // 但仍旧不建议在语句块内声明函数，即使是表达式的方式
    if (...) {
        var fooName = function() {
            ...;
        };
    }
    ```

    **(╳)**

    ```javascript
    if (...) {
        function fooName() {
            ...;
        }
    }
    ```

  6. 块内函数声明: 不要在块内声明一个函数. 

    不要写成.

    **(╳)**

    ```javascript
    if (x) {
        function foo() {}
    }
    ```

    虽然很多 JS 引擎都支持块内声明函数, 但它不属于 ECMAScript 规范 (见 ECMA-262, 第13和14条).
    各个浏览器糟糕的实现相互不兼容, 有些也与未来 ECMAScript 草案相违背. ECMAScript 只允许在脚本的根语句或函数中声明函数.
    如果确实需要在块中定义函数, 建议使用函数表达式来初始化变量:

    ```javascript
    if (x) {
        var foo = function() {}
    }
    ```

  7. 闭包，用起来要小心，因为如果处理不当很容易导致内存泄漏. 及时释放闭包变量引用, destory() 方法的设计. 

  8. eval(): 只用于解析序列化串

    eval() 会让程序执行的比较混乱, 当`eval()`里面包含用户输入的话就更加危险. 可以用其他更佳的, 更清晰, 更安全的方式写你的代码,
    所以一般情况下请不要使用`eval()`. 当碰到一些需要解析序列化串的情况下, 使用`eval`很容易实现.

    这是一个常用的`input`标签里面的属性

    ```html
    <input id="jUser" type="hidden" data-user="{'name':'djune','age':30}" />
    ```

    我们通常如此调用(基于jquery实现)

    ```javascript
    var user = $("#jUser").attr("data-user");
    var user = eval('('+user+')');
    console.log(user.name);
    ```

  9. with() {}: 不要使用 

  10. this: 仅在对象构造器, 方法, 闭包中使用. 

    `this`的语义很特别. 有时它引用一个全局对象(大多数情况下), 调用者的作用域(使用 eval时), DOM 树中的节点(添加事件处理函数时),
    新创建的对象(使用一个构造器), 或者其他对象(如果函数被`call()` 或`apply()`).

    使用时很容易出错, 所以只有在下面两个情况时才能使用:

    在构造器中 对象的方法(包括创建的闭包)中

  11. for-in 循环: 只用于 object/map/hash 的遍历,对 Array 用 for-in 循环有时会出错. 因为它并不是从 0 到 length - 1 进行遍历, 而是所有出现在对象及其原型链的键值. 下面就是一些失败的使用案例: 

    ```javascript
    // 本来只要输出0，1；结果输出了0,1,djune;
    var a = [0, 1];
    a.buhu = 'djune';
    for (var i in a) {
        console.log(a[i]);
    }
    ```

  12. 尽量不修改内置对象的原型 

    千万不要修改内置对象, 如`Object.prototype`和`Array.prototype` 的原型. 而修改内置对象, 如
    `Function.prototype`的原型, 虽然少危险些, 但仍会导致调试时的诡异现象. 所以也要避免修改其原型.

  13. Object{}和 Array[]

    使用“{}”替代“new Object()”来创建对象

    使用“[]”替代“new Array()”来创建数组,使用 Array 构造器很容易因为传参不恰当导致错误

    ```javascript
    var obj = {
        a: 1,
        b: 2,
        'say hello': 'hello'
    };
    
    var arr = [1, 2, 'hello'];
    ```

  14. 进行对比操作时，尽量使用“===”和“!==”

### 注释

  1. 类注释 

    每个类的定义都要附带一份注释, 描述类的功能和用法. 也需要说明构造器参数.

    如果该类继承自其它类, 应该使用 @extends 标记.

    如果该类是对接口的实现, 应该使用 @implements 标记.

    ```javascript
    /**
     * Class making something fun and easy.
     * @param {string} arg1 An argument that makes this more interesting.
     * @param {Array.} arg2 List of numbers to be processed.
     * @constructor
     * @extends {goog.Disposable}
     */
    project.MyClass = function(arg1, arg2) {
        // ...
    };
    goog.inherits(project.MyClass, goog.Disposable);
    ```

  2. 方法与函数的注释 

    提供参数的说明. 使用完整的句子, 并用第三人称来书写方法说明.

    ```javascript
    /**
     * Converts text to some completely different text.
     * @param {string} arg1 An argument that makes this more interesting.
     * @return {string} Some return value.
     */
    MyClass.prototype.someMethod = function(arg1) {
        // ...
    };

    /**
     * Operates on an instance of MyClass and returns something.
     * @param {project.MyClass} obj Instance of MyClass which leads to a long
     *     comment that needs to be wrapped to two lines.
     * @return {boolean} Whether something occured.
     */
    function PR_someMethod(obj) {
        // ...
    }
    ```

    对于一些简单的, 不带参数的 getters, 说明可以忽略.

    ```javascript
    /**
     * @return {Element} The element for the component.
     */
    Component.prototype.getElement = function() {
        return this._element;
    };
    ```

  3. 属性注释

    ```javascript
    /**
     * Maximum number of things per pane.
     * @type {number}
     */
    project.MyClass.prototype.someProperty = 4;
    ```
                      
  4. 类型转换的注释 

    有时, 类型检查不能很准确地推断出表达式的类型, 所以应该给它添加类型标记注释来明确之, 并且必须在表达式和类型标签外面包裹括号.

    ```javascript
    function setFoo(x) (/* @type {Number} */ x) { ... }
    ```

  5. 枚举

    ```javascript
    /**
     * Enum for tri-state values.
     * @enum {number}
     */
    project.TriState = {
        TRUE: 1,
        FALSE: -1,
        MAYBE: 0
    };
    ```
                      
    注意一下, 枚举也具有有效类型, 所以可以当成参数类型来用.

    ```javascript
    /**
     * Sets project state.
     * @param {project.TriState} state New project state.
     */
    project.setState = function(state) {
        // ...
    };
    ```

  6. JSDoc 缩进

    如果你在 @param, @return, @supported, @this 或 @deprecated 中断行, 需要像在代码中一样,
    使用4个空格作为一个缩进层次.

    ```javascript
    /**
     * Illustrates line wrapping for long param/return descriptions.
     * @param {string} foo This is a param with a description too long to fit in
     *     one line.
     * @return {number} This returns something that has a description too long to
     *     fit in one line.
     */
    project.MyClass.prototype.method = function(foo) {
        return 5;
    };
    ```

    不要在 @fileoverview 标记中进行缩进.

    虽然不建议, 但也可对说明文字进行适当的排版对齐. 不过, 这样带来一些负面影响, 就是当你每次修改变量名时, 都得重新排版说明文字以保持和变量名对齐.

    ```javascript
    /**
     * This is NOT the preferred indentation method.
     * @param {string} foo This is a param with a description too long to fit in
     *                     one line.
     * @return {number} This returns something that has a description too long to
     *                  fit in one line.
     */
    project.MyClass.prototype.method = function(foo) {
        return 5;
    };
    ```

  7. 例子注释:

    ```javascript
    /**
     * @example
     * var bleeper = makeBleep(3);
     * bleeper.flop();
     */
    ```

  8. Typedefs:

    有时类型会很复杂. 比如下面的函数, 接收 Element 参数

    ```javascript
    /**
     * @param {string} tagName
     * @param {(string|Element|Text|Array)} contents
     * @return {Element}
     */
    goog.createElement = function(tagName, contents) {
        ...
    };
    ```

    你可以使用 @typedef 标记来定义个常用的类型表达式
    
    ```javascript
    /** @typedef {(string|Element|Text|Array)} */
    goog.ElementContent;
    
    /**
    * @param {string} tagName
    * @param {goog.ElementContent} contents
    * @return {Element}
    */
    goog.createElement = function(tagName, contents) {
        ...
    };
    ```

### 接口

  1. 单一职能原则: 一个函数或者一个类只应该负责一件事, 这可以为我们后期的维护以及测试节省很多的成本.

  2. 接口分离原则.

    跟单一职能原则联系比较紧密, 遵循单一职能原则, 将功能进行拆分.

    比如: dojo.style 方法, 它本身包含了 get 和 set 两个接口, 应该将其拆分, 如 YUI.DOM.setStyle,
    YUI.DOM.getStyle.

  3. 不要过多的干预使用者:

    我们不应该想当然的认为使用者应该怎样使用, 而应与实践相结合提供接口.

    比如: 异步请求的回调函数, 我们应该为使用者提供什么样的参数? 添加什么样的作用域? 这个应该由用户来决定, 而不是由我们来决定.

### 数据

  1. 返回的数据以标准的 JSON 格式来书写.

    ```javascript
    {
        "data": {
            "name": "djune",
            "age": 30,
            "other": [1, 2]
        },
        "result": 405,
        "message": "系统错误, 请稍候再试"
    }
    ```

### 参考文档

  1. [Google JavaScript Style Guide](http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml)

