#通用文件开发规范

### 样式表文件

* 【强制】CSS编码规范遵循公司整体[《CSS编码规范》](http://styleguide.baidu.com/style/css/index.html)

* 【建议】通用css文件命名建议：

    ```javascript
    .
    ├── src         //源文件目录
        ├── css         //css 样式文件目录
            ├── reset.css       //通用样式重置
            ├── tools.css       //通用工具类css（clearfix, wordwrap, ...）
            ├── layout.css      //通用布局类css
            ├── grid.css        //栅格化 css
    ```

* 【建议】css最外层选择器建议使用类选择器，最外层class命名建议：
    * common模块下的通用css：g-xxx
    * 模块下css：m(module)-xxx(模块名)-xxx
    * 组件下css：w(widget)-xxx(组件名)-xxx
* 【建议】不使用@import语法，如果有import需求，使用less的import
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

###JavaScript文件
* 【建议】建议common中定义全站统一的命名空间：x

    ```javascript
    x = {
        util: {},       //通用工具方法
        conf: {},       //通用展示
        data: {},       //通用数据
        m: {            //module, 分配给各模块去定义的命名空间
            home: {},       //为home模块的命名空间
            user: {}        //为user模块的命名空间
        }
    };
    ```

* 【建议】页面同步引入脚本数量建议限制在2个以内，其中包含base脚本和模块脚本供以初始化&首屏加载
* 【建议】base脚本量尽量保证gzip后60k以内
* 【建议】组件引入都以异步方式，按加载时机进行打包：
    * 页面加载后马上异步引入
    * 页面domready后异步引入
    * 页面onload后异步引入
    * 当具体功能触发时异步引入
* 【建议】cookie的使用&命名规则
    * 禁止向baidu域下添加cookie
    * cookie建议命名：模块名_页面名_xxx

###图片文件
* 【强制】文件命名规范如下：

    ```
    spr_xxx     //sprite类型图片
    ico_xxx     //图标类型图片
    logo_xxx    //logo类型图片
    bg_xxx      //背景类型图片
    ```

* 【强制】通过Photoshop生成的图片，必须选用web格式并且不可带任何元信息
* 【建议】ico类图片一般选用png格式
    * 只包含全透明效果不包含半透明效果图片，选用png8
    * 包含半透明效果图片，选用png24
* 【建议】编译时引入图片压缩功能，上线之前统一进行图片压缩
