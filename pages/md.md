# markdown学习笔记 [返回首页](/)
> [参考资料](https://www.jianshu.com/p/0130ad32a08d)

# 基本语法
## 分级标题
> #--#6 === 表示一级标题 --- 二级标题

## 生成目录 TOC
> 引用 >

### 多层嵌套
```
> aaaaaaaaa
>> bbbbbbbbb
>>> cccccccccc

```

## 行内标记
  ``   `着重`
## 代码块
>
 用```生成块
>可配置语法(起始三撇后加 JavaScript)

## 插入链接
 中括号+小括号{前面是内容，后面是链接地址，最后可以加{:target="_blank"}

```
[](){:target="_blank"}
```

## 插入图片 ![](./01.png '描述')
```![name][01]
   [01]: ./01.png '描述'
```

## 插入图片带链接
  ```[![](./01.png '百度')](http://www.baidu.com){:target="_blank"}  ```
## 插入视频
 ```
   [![](./youku2.png)](http://v.youku.com/v_show/id_XMjgzNzM0NTYxNg==.html?spm=a2htv.20009910.contentHolderUnit2.A&from=y1.3-tv-grid-1007-9910.86804.1-2#paction){:target="_blank"}
 ```
## 有序表
```
1. 内容1
1. 内容2
1. 内容3
```

## 无序列表
* 内容1
* 内容2
* 内容3

### 续表嵌套 空格隔开

## 任务列表
```
- [x] 选项一
- [ ] 选项二
- [ ] [选项3]
```
## 表格
```
|    a    |       b       |      c     |
|:-------:|:------------- | ----------:|
|   居中  |     左对齐    |   右对齐   |
|=========|===============|============|

```

|    a    |       b       |      c     |
|:-------:|:------------- | ----------:|
|   居中  |     左对齐    |   右对齐   |
|=========|===============|============|

### [表格生成器](https://link.jianshu.com/?t=http://www.tablesgenerator.com/)

## 支持内嵌CSS样式
<p style="color: #AD5D0F;font-size: 16px; font-weight:bold">内联样式</p>

## 语义标记

|  描述	| 效果  | 	代码 |
|:----:|:----:|:----:|
|斜体|	斜体|	*斜体*|
|斜体|	斜体|	_斜体_|
|加粗|	加粗|	**加粗**|
|加粗+斜体|	加粗+斜体|	***加粗+斜体***|
|加粗+斜体|	加粗+斜体|	**_加粗+斜体_**|
|删除线|	删除线|	~~删除线~~|

## 语义标签
|描述|	效果|代码|
|:----:|:----:|:----:|
|斜体|	<i>斜体</i>|	<i>斜体</i>|
|加粗|	<b>加粗</b>|	<b>加粗</b>|
|强调|	<em>强调</em>|	<em>强调</em>|
|上标|	Za|	Z<sup>a</sup>|
|下标|	Za|	Z<sub>a</sub>|
|键盘文本| |<kbd>Ctrl</kbd>|
|换行| | |

## 公式 {#1}
> 注：1个$左对齐，2个居中

## 分隔符
> 注：最少三个 --- 或 ***或 * * *

## 脚注
> Markdown[^1]
[^1]: Markdown是一种纯文本标记语言

## 锚点
> 注：只有标题支持锚点， 跳转目录方括号后 保持空格

## 定义型列表

## 自动邮箱链接
<xxx@outlook.com>

## 流程图
```flow                     // 流程
st=>start: 开始|past:> http://www.baidu.com // 开始
e=>end: 结束              // 结束
c1=>condition: 条件1:>http://www.baidu.com[_parent]   // 判断条件
c2=>condition: 条件2      // 判断条件
c3=>condition: 条件3      // 判断条件
io=>inputoutput: 输出     // 输出
//----------------以上为定义参数-------------------------

//----------------以下为连接参数-------------------------
// 开始->判断条件1为no->判断条件2为no->判断条件3为no->输出->结束
st->c1(yes,right)->c2(yes,right)->c3(yes,right)->io->e
c1(no)->e                   // 条件1不满足->结束
c2(no)->e                   // 条件2不满足->结束
c3(no)->e                   // 条件3不满足->结束
```

st=>start: 开始|past:> http://www.baidu.com // 开始
e=>end: 结束              // 结束
c1=>condition: 条件1:>http://www.baidu.com[_parent]   // 判断条件
c2=>condition: 条件2      // 判断条件
c3=>condition: 条件3      // 判断条件
io=>inputoutput: 输出     // 输出
//----------------以上为定义参数-------------------------

//----------------以下为连接参数-------------------------
// 开始->判断条件1为no->判断条件2为no->判断条件3为no->输出->结束
st->c1(yes,right)->c2(yes,right)->c3(yes,right)->io->e
c1(no)->e                   // 条件1不满足->结束
c2(no)->e                   // 条件2不满足->结束
c3(no)->e

## 时序图
```sequence
A->>B: 你好
Note left of A: 我在左边     // 注释方向，只有左右，没有上下
Note right of B: 我在右边
B-->A: 很高兴认识你
```

A->>B: 你好
Note left of A: 我在左边     // 注释方向，只有左右，没有上下
Note right of B: 我在右边
B-->A: 很高兴认识你



