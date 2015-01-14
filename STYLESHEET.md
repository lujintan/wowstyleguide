#样式表文件开发规范

* 【建议】所有样式表文件，使用less文件
* 【建议】通用文件命名建议：

    ```javascript
    .
    ├── src         //源文件目录
        ├── less         //less 样式文件目录
            ├── reset.less       //通用样式重置
            ├── tools.less       //通用工具类css（clearfix, wordwrap, ...）
            ├── layout.less      //通用布局类css
            ├── grid.less        //栅格化 css
            ├── responsive.less  //基础响应式样式布局文件
    ```

* 【强制】css最外层选择器建议使用类选择器，最外层class命名规范（主要为了防止样式覆盖现象出现）：
    * common模块下的通用css：g-xxx
    * 模块下css：m(module)-xxx(模块名)-xxx
    * 组件下css：w(widget)-xxx(组件名)-xxx
* 【建议】不使用@import语法，如果有import需求，使用less的import语法
* 【强制】伪元素选择器使用`"::"`，伪类选择器使用`":"`，示例：

    ```css
    /*伪元素*/
    p::after{
        content: " ";
    }
    /*
        主要伪元素选择器：
        ::after, ::before, ::first-letter, ::first-line, ::selection
    */
    
    /*伪类*/
    a:hover{
        color: #000;
    }
    /*
        主要伪类选择器：
        :active, :checked, :disabled, :empty, :enabled, :first-child, :first-of-type, :focus, 
        :hover, :in-range, :invalid, :lang(language), :last-child, :last-of-type, :link, :not(selector),
        :nth-child(n), :nth-last-child(n), :nth-last-of-type(n), :nth-of-type(n), :only-of-type, :only-child,
        :optional, :out-of-range, :read-only, :read-write, :required, :root, :target, :valid, :visited
    */
    
    ```

* 【建议】css类选择器缩写建议
    * hd  : header
    * ft  : footer
    * ma  : main
    * wp  : wrapper
    * inr : inner
    * bg  : background
    * nav : navigator
    * bt  : button
    * sd  : sidebar
    * lg  : logo
    * bnr : banner
    * ct  : content
    * tl  : title
* 【建议】响应式布局样式文件书写建议：

    ```javascript
    .
    ├── less                 //样式文件目录
        ├── home.less                   //默认页面最小宽度样式
        ├── home_width_l_1280.less      //浏览器宽度 <= 1280px && > min 样式
        ├── home_width_l_1680.less      //浏览器宽度 <= 1600px && > 1280 样式
        ├── home_width_l_1920.less      //浏览器宽度 <= 1920px && > 1600 样式
        ├── ...
    ```
* 【建议】z-index的使用：
    * 页面内容需要设置z-index的情况，z-index < 100
    * 页面漂浮广告窗：z-index:100，漂浮框内容
    * 吸顶导航：z-index: 200
    * 回顶部、问题反馈等浮层：z-index: 300
    * 浮动tip(如hover后的用户卡片)：z-index: 400
    * 弹层遮罩层：z-index:1000
    * 弹层窗体：z-index:1100
    * 绝对顶级层：z-index:10000
    * 建议底层css工具类中进行通用z-index封装
