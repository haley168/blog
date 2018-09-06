### 微信小游戏的各种坑及注意事项（各种bug）[返回首页](/)

#### 开发工具--Cocos Creator
[Cocos Creator](http://docs.cocos.com/creator/manual/zh/getting-started/introduction.html)
###### 无法显示任何内容
>报错：vconsole.min.js:11 TypeError: Cannot read property 'getExtension' of null
>原因：QQ浏览器对webgl的支持有问题
>解决办法：改为使用chrome浏览器就好了