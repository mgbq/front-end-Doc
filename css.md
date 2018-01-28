# CSS代码规范

## 语言规范

  1. 样式文件中不要出现大写的标签定义, 不要对 JS 钩子进行样式定义。

  2. 避免出现`.a.b`之类的定义, 如果做`hack`使用请注明。 ( ie6 不支持此定义 )

  3. 稀奇古怪的`hack`请加注释。

  4. 避免使用`!important`, 如果必须请加注释。

  5. 缩进以4个空格为基本单位[[参考]](http://www.cnblogs.com/kungfupanda/archive/2012/09/05/2671597.html)。

  6. 样式使用竖排, 不要使用横排以及 n 级缩进等。 

  7. 对于所有`hack`请放到每个样式定义的最后边。 

  8. class selector 层级尽量控制在 5 层以内。 

  9. 严格控制 `important` 关健字的使用场景，尽量少用。

## CSS 命名规则

  1. 样式类名全部用小写，首字符必须是字母，禁止数字或其他特殊字符。由以字母开头的小写
  字母`（a-z）`、数字`（0-9）`、中划线 `（-）`组成。

  2. 可以是单个单词，也可以是组合单词，要求能够描述清楚模块和元素的含义，使其具有语义
  化。避免使用 `123456…,red,blue,left,right`之类的（如颜色、字号大小等）矢量命名
  ，如`class="left-news"、class="2"` ，以避免当状态改变时名称失去意义。尽量用单个
  单词简单描述`class`名称。

  3. 双单词或多单词组合方式：形容词-名词、命名空间-名次、命名空间-形容词-名词。例如：
  `news-list、mod-feeds、mod-my-feeds、cell-title`

## 通用命名

  1. 页面框架命名，一般具有唯一性，推荐用ID命名

    ID名称|命名|ID名称  |命名
    :---------------|:---------------|:---------------|:---------------
    头部|header|主体|   main
    脚部|footer|容器|wrapper
    侧栏|sidebar|栏目|column
    布局|layout|| 

  2. 模块结构命名

    Class名称|命名|Class名称|命名
    :---------------|:---------------|:---------------|:---------------
    模块(如：新闻模块)  |mod (mod-news) |标题栏 |title
    内容    |content    |次级内容   |sub-content

  3. 导航结构命名

    Class名称|命名|Class名称|命名
    :---------------|:---------------|:---------------|:---------------
    导航    |nav    |主导航 |main-nav
    子导航| sub-nav |顶部导航   |top-nav
    菜单    |menu   |子菜单 |sub-menu

  4. 一般元素命名

    Class名称|命名|Class名称|命名
    :---------------|:---------------|:---------------|:---------------
    二级|   sub |面包屑|    breadcrumb
    标志    |logo   |广告   |bner(禁用banner或ad)
    登陆    |login  |注册   |register/reg
    搜索    |search |加入   |join
    状态    |status |按钮   |btn
    滚动    |scroll |标签页 |tab
    文章列表    |list|  短消息| msg/message
    当前的  |current    |提示小技巧 |tips
    图标    |icon|  注释|   note
    指南    |guide  |服务   |service
    热点    |hot    |新闻   |news
    下载    |download   |投票   |vote
    合作伙伴    |partner    |友情链接   |link
    版权|   copyright|  演示|   demo
    下拉框  |select |摘要   |summary
    翻页    |pages| 主题风格|   themes
    设置    |set    |成功|  suc
    按钮    |btn|   文本|   txt
    颜色    |color/c|   背景    |bg
    边框    |border/bor|    居中|   center
    上  |top/t  |下|    bottom/b
    左  |left/l |右 |right/r
    添加    |add    |删除   |del
    间隔    |sp|    段落    |p
    弹出层  |pop    |公共   |global/gb
    操作|   op  |密码   |pwd
    透明    |tran|  信息    |info
    重点    |hit    |预览   |pvw
    单行输入框| input|  首页    |index
    日志    |blog   |相册|  photo
    留言板  |guestbook| 用户|   user
    确认    |confirm    |取消   |cancel
    报错    |error||

  5. 全局皮肤样式

    文字颜色(命名空间text-xxx)

    ```
    text-c1, text-c2,text-c3……
    ```

    背景颜色(命名空间bg -xxx)

    ```
    bg-c1,bg-c2,bg-c3……
    ```

    边框颜色(命名空间border-xxx)

    ```
    border-c1,border-c2,border-c3……
    ```

## 属性使用

  1. z-index
  
    ```
    //右侧导航: 100-109 
    //弹窗: 110-119 
    //顶部: 90-99 
    //搜索: 80-89 
    //导航: 70-79 
    //主内容: 50-59 
    //底部: 40-49
    ```
  
  2. css属性使用缩写。

    **(╳)**
    ```css
    padding-top: 1px;
    padding-right: 2px;
    padding-bottom: 3px;
    padding-left: 4px;
    ```
    **(√)**
    ```css
    padding: 1px 2px 3px 4px;                          
    ```

  3. 0不带单位 (动画0%除外)。

    **(√)**
    ```css
    margin: 0;
    font-size: 0;
    ```

    **(╳)**
    ```css
    margin: 0px;  
    font-size: 0px;                        
    ```

  4. 使用简写的十六进制值。

    **(√)**

    ```css
    color: #edf;
    ```

    **(╳)**

    ```css
    color: #eeddff;                    
    ```

  5. `border`以 `width, style, color` 的顺序书写, `width`单位使用 `px/rem`, 例如:

    ```css
    border: 1px solid #000;  
    border-top: 1px solide #000;  
    border-top-color: red;  
    border: 0;
    ```

  6. `background:`以`color, image, repeat, position`的顺序来书写, `url`省略引号, 例如:

    ```css
    background:#003 url(http://www.taobao.com/loading.png) no-repeat 0 0;
    background-color:red;
    ```

  7. 尽量不使用 CSS expression, 大量使用时性能较差, 应尽量避免使用。

  8. CSS属性书写顺序参考:

    ```
    位置属性(position, top, right, z-index, display, float等)
    大小(width, height, padding, margin)
    文字系列(font, line-height, letter-spacing, color- text-align等)
    背景(background, border等)
    其他(animation, transition等)
    display
    float
    position
    z-index
    width
    height
    overflow
    left(right)
    top(bottom)
    text-xxx
    font-xxx
    color
    border
    background
    cursor
    ```

  9. 为了节省图片的开销，有时候小三角形可以用css border来生成, 看看本规范里面小三角按钮[[参考]](http://ued.taobao.com/blog/2010/08/css-border%E4%BD%BF%E7%94%A8%E5%B0%8F%E5%88%86%E4%BA%AB/):

## 注释规范

  1. 文件头注释:

    ```css
    /**
     * Style for module header.
     * @author djune
     * @version 1.0.0 build 2010-12-8
     * @modified xxx 2011-2-18
     */
    ```

  2. 对于html模块需要加注释。 

  3. 奇葩点的 hack 要加注释。

    ```css
    background-color: transparent; /* flexible background gradient */
    font-family: serif; /* text floating bug in ie6 */
    ```

  4. 修改别人的 CSS 请添加注释

    ```css
    /* 主要修改IE8浏览器兼容性问题 djune 2013-09-26 13:21 */
    ```

## CSS Module (模块定义)

  通常我们的页面模块html结构可以写成这样(.hd, .bd, .ft):

  通过语义化含义判断我们的结构具体怎么分配到这三个基本结构。

  html:

    ```html
    <div id="mod-xxx" class="mod-xxx">
      <div class="hd">Module Title</div>
      <div class="bd">
         Module body inner html constructs
      </div>
      <div class="ft">just a footer</div>
    </div>
    ```

  scss

    ```css
    .mod-xxx {
      border: 1px solid #ccc;
      .hd { font-weight: bold; }
      .bd { paddinig: 3px; }
      .ft { margin-botto: 3px; }
    }
    ```

  css:

    ```css
    .mod-xxx { border: 1px solid #ccc; }
    .mod-xxx .hd { font-weight: bold; }
    .mod-xxx .bd { paddinig: 3px; }
    .mod-xxx .ft { margin-botto: 3px; }
    ```

## 其他

  1. [sass](http://sass-lang.com/guide) 预编译, [compass 用法](http://compass-style.org/help/tutorials/)
  2. 合理运用sprites技术，注意png8和png24图片格式化的使用。[[参考]](http://www.w3cfuns.com/thread-5597974-1-1.html)。

