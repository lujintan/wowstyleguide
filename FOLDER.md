#开发目录规范

##目录结构划分

####目录划分规则：

* 一级目录主要按照职能进行划分
* 二级目录主要按照文件类型进行划分

####目录结构：

```javascript
.
├── package.json    //声明&配置文件
├── src             //源文件目录
    ├── css             //css 样式文件目录
    ├── less            //less 样式文件目录
    ├── js              //js 文件目录
    ├── image           //图片文件目录(可包含png,gif,jpg等)
    ├── swf             //flash文件
    ├── tpl             //smarty后端模板文件
    ├── widget          //组件目录（可能包含一组tpl + js + css + image）
        ├── ui_xxx          //展示类型组件
            ├── main.js         //组件入口文件
            ├── main.less       //组件入口css文件
            ├── README.md       //组件说明文档
        ├── dialog_xxx     //展示类型组件
            ├── main.js         //组件入口文件
            ├── main.css        //组件入口css文件
            ├── README.md       //组件说明文档
├── lib             //前端lib
    ├── require.js
    ├── bootstrap
        ├── a_xxx.css
        ├── b_xxx.css
├── test            //测试数据目录
├── doc             //模块说明文档，采用markdown语法书写
├── dist            //编译产出代码
```

## package.json  配置规范
* 【强制】模块根目录必须有package.json文件，进行模块的基本信息描述和编译基础配置
* package.json主要配置信息如下

    ```javascript
    {
        "name": "xxx",                          //模块名称
        "description": "Concatenate files.",    //描述信息
        "version": "1.0.1",                     //模块版本
        "url": "http://www.aaa.com/bbb",        //对应线上地址
        "author": [{                            //负责人信息
            "name": "xxx",                          //姓名
            "mail": "xxx@xxx.com"                   //邮箱
        }],
        "wow": {        //wow编译配置
            ...
        }
    }
    ```

## src目录文件规范
* 【强制】src目录下按照文件类型进行分类（图片&组件类文件除外）
* 【建议】同一模块，尽量不出现同一功能的多种类型文件；例：尽量不在一个项目中既使用less又使用css

## lib目录文件规范
* 【强制】lib目录下只能存放第三方lib文件
* 【强制】若第三方lib只有一个文件；如：require.js则直接放入lib目录下
* 【强制】若第三方lib存在一组文件；如：bootstrap,则为该lib单独创建目录，将该lib的一组文件放入相应目录

## test目录文件规范
* 【强制】test目录下只能存放测试数据文件，文件类型为：json|js

## doc目录文件规范
* 【强制】doc目录下文档使用markdown语法进行书写
