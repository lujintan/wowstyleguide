#模块划分&命名

* 【强制】开发人员分模块进行代码开发，模块必须以产品功能维度进行划分
```javascript
例如：

XXX平台
├── 主站            //home 模块
├── 个人后台        //console 模块
    ├── 后台配置        //console 模块 —— backend
    ├── 管理页          //console 模块 —— management
    ├── ...
├── 消息中心        //message 模块
    ├── 消息列表页      //message 模块 —— list
    ├── 消息详情页      //message 模块 —— detail
├── 用户中心        //user 模块
    ├── 用户详情页      //user 模块 —— detail
    ├── 用户注册页      //user 模块 —— register
    ├── 资质状态页      //user 模块 —— status
├── ...
```
* 【强制】同级模块必须有通用模块以存放该级其他模块的通用资源，通用模块命名：common
```javascript
例如：
xxx
├── common
├── home
├── console
├── ...
```
* 【强制】除common外其他模块之间功能上避免出现耦合，互相之间不可进行资源引用
