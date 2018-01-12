# rkIMComponent
仁科互动即时通讯工具组件
## 打包相关说明
1. 打包im时运行
``` 
cd /apps-ingage-web/src/main/webapp
gulp pack:im
```
2. 开发用，监听im的改动并实时编译
```
gulp watch:im
```
3. 测试灰度打包时执行
```
gulp beforepack --env gray    //一般只在运维部署时执行，本地不需要执行。执行后会对文件内容进行替换。慎用。
```

## 架构设计
1. IM架构设计图
`/doc/IMStructure.html`
2. [脑图](http://10.10.0.115/doc/website/frontend/index.html#/content/frontend/md/servicecloud/lbb_brain)

## 测试方式
> 组件代码在 https://crm-devtest88.xiaoshouyi.com/admin/ 中可以获取
打开crm-设置-系统设置-客服设置-小组件-组件代码

- 小组件（网页客服组件外部调用代码）

```
\\正式环境
<script id="rkCustomerScript" src="https://crm-devtest88.xiaoshouyi.com/embeded/im/loader/loader.js" data-config='{"tenant":"4ec2b44d166728f14f0ae3982844519d","wrapId":"rkCustomerWrap","skillScope":"13205,13203","headPage":"robot"}'> </script>

\\测试环境: 需要增加一个targetUrl:测试环境域名
<script id="rkCustomerScript" src="https://crm-devtest88.xiaoshouyi.com/embeded/im/loader/loader.js" data-config='{"tenant":"4ec2b44d166728f14f0ae3982844519d","wrapId":"rkCustomerWrap","skillScope":"13205,13203","headPage":"robot","targetUrl":"crm-dev.xiaoshouyi.com"}'> </script>
```

- H5页面（外部链接地址）
`https://crm-devtest88.xiaoshouyi.com/embeded/im/iframe-h5.html?tenantToken=4ec2b44d166728f14f0ae3982844519d&&skillScope=13205,13203&&headPage=robot`

- 生成小组件的演示地址（已弃用）
`http://10.10.0.115/public/serviceclound/test.html`

## 文件结构说明
`/doc/embeded目录结构.png`
```
/embeded
    /im
        /chat
            /build                              //打包的dist
            /lib                                //js lib
            /module                             
                /chat                           //IM基础组件
                /customerService                //客服小组件的，其中包括一个chat实例（csChat），继承自$.rk.chatBaseCtrl
                imBase.js   
            /source                             //样式资源文件
        /loader                  
```