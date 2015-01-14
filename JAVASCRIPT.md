#JavaScript 文件开发规范

###常规Js文件开发规范

说明：常规js文件不会进行amd包裹，即可以直接引入调用
* 【强制】js文件的目录位置：src/js
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
* 【建议】页面同步引入脚本数量（打包后）建议限制在2个以内，其中包含base脚本和模块脚本供以初始化&首屏加载
* 【建议】base脚本量尽量保证gzip后60k以内
* 【建议】组件引入都以异步方式，按加载时机进行打包：
    * 页面加载后马上异步引入
    * 页面domready后异步引入
    * 页面onload后异步引入
    * 当具体功能触发时异步引入

###spg handler开发规范

说明：spg handler即为单页面应用的子页面的处理逻辑，handler接口定义：

    ```javascript
        interface Handler{
            /**
             * Will execute when block render
             * @param elem the container of the block
             * @param data : {
             *          data        //data which is used to render block
             *          urlKeys     //matched from router "(:xxx)"
             *          params      //the url parameter
             *          location    //the Window's location object
             *          title       //the page's title
             *      }
             */
            init(elem: Element, data: Object): void;

            /**
             * Will execute when page re-render
             * @param elem
             * @param data
             */
            repaint(elem: Element, data: Object): void;

            /**
             * Will execute when page destroy
             * @param elem
             * @param data
             */
            destroy(elem: Element, data: Object): void;
        }
    ```

* 【强制】handler文件必须放置于src/js/handler目录下
* 【强制】handler文件必须实现Handler接口，即必须exports,init方法，destroy方法（可选），repaint方法（可选）
* 【强制】文件引入（require）必须放置于文件顶部，方法导出（module.exports）必须放置于页尾

###spg dt开发规范

说明：spg dt即为单页面的数据转换器，即从server端取回的数据源会经过dt的过滤之后，再进行模板的渲染，dt文件形如：

    ```javascript
        module.exports = function(dsData){
            //dsData 为server直接打回的数据
            //......

            return renderData;
            //返回渲染模板的数据，也可以返回promise
            //若返回`promise`，则renderData会作为resolve的第一个参数
            //关于`promise`的相关问题，可参见promise的相关规范
        }
    ```

* 【强制】dt文件必须放置于src/js/dt目录下
* 【强制】dt文件直接导出一个方法，方法参数为server返回的数据源，返回值为渲染模板的数据

###widget 开发

说明： 请参见[组件开发规范](./WIDGET.md)
