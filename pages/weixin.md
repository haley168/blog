##### 微信小程序的各种坑（各种bug）
1. [背景图片显示问题](http://www.wxapp-union.com/forum.php?mod=viewthread&tid=393)
>css中只能使用网络图片或者base64，而不能使用本地图片

1. [原生组件的使用camera、canvas、input、live-player、live-pusher、map、textarea、video](https://developers.weixin.qq.com/miniprogram/dev/component/native-component.html)
>原生组件的层级是最高的，所以页面中的其他组件无论设置 z-index 为多少，都无法盖在原生组件上，如果需要盖住，只能使用偏招，比如覆盖textarea，可以做一个view来接收数据，并且与textarea来回切换。

1. []()


