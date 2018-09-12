# webstorm 10.0.1 学习笔记 [返回首页](/)


# 配置修改
## 编码格式问题
启动项目时，默认编码格式居然是gbk的，每次都需要手动改为utf-8，为了解决这个问题需要如下操作
> 1. file--close project
> 1. 右下角的setting=>editor=>file encoding 改为utf-8 这样设置的是软件的默认设置，如果开启项目的状态下设置，那么此时设置的是本项目的编码格式
> 1. [参考地址](https://cnodejs.org/topic/56021342272b724e5efefbfc)