# 微信小游戏--FlappyBird[返回首页](/)
## [在线Demo](https://haley168.github.io/flappyBird/index.html){:target="_blank"}
## 开发工具--Cocos Creator
[Cocos Creator](http://docs.cocos.com/creator/manual/zh/getting-started/introduction.html)
[Cocos Creator v2.0 用户手册](http://docs.cocos.com/creator/manual/zh/)
[API参考](http://docs.cocos.com/creator/api/zh/)
## 参考资料
[韩超老师在腾讯课堂](https://ke.qq.com/user/index/index.html#/plan/cid=313749&term_id=100372324)
[完整版代码下载](/download/flappyBird_2.rar)
## 文档说明
> 压缩包内含开发源码及微信端和网页版项目代码

## 游戏概述
> 屏幕尺寸：288*512
> 小鸟由于重力作用会不断下沉，通过点击屏幕可以使小鸟向上飞行。

## 效果图(整理中)
![开始之前](/img/flappyBird/1.png)
![游戏结束](/img/flappyBird/2.png)
![游戏结束](/img/flappyBird/3.png)
![游戏结束，PC版](/img/flappyBird/5.png)
![游戏结束，微信版](/img/flappyBird/4.png)

---
## 1.结构
### 资源结构
>assets
>> Scene
>>> main

>> Script
>>> mainContorller

>> Texture
>>> bg_day
>>> bird0_0
>>> bird0_1
>>> bird0_2
>>> button_resume
>>> pipe_down
>>> pipe_up
>>> text_game_over
>>> title

---
## 2.层级管理器
> Canvas
>> bg_day
>> bg_day
>> birdParent
>>> bird0_0
>>> bird0_1
>>> bird0_2

>> pipeParent0
>>> pipe_up
>>> pipe_down

>> pipeParent1
>>> pipe_up
>>> pipe_down

>> pipeParent2
>>> pipe_up
>>> pipe_down
>> btn
>> Label
>> text_game_over
>> button_resume
>> title

---
## 3.变量
> time:number=0
speed:number=0
wScreen:number=288
wPipe:number=52
hBird:number=34
wBird:number=24
score:number=0
isGameStart:bollean=false

---
## 4.节点、精灵、Label
> @property(cc.Sprite) bird0: cc.Sprite = null;
@property(cc.Sprite) bird1: cc.Sprite = null;
@property(cc.Sprite) bird2: cc.Sprite = null;
@property(cc.Sprite) bird3: cc.Sprite = null;
@property(cc.Node) birdParent:cc.Node=null;

> @property(cc.Node) bg0:cc.Node=null;
@property(cc.Node) bg1:cc.Node=null;

> @property(cc.Node) pipeParent0:cc.Node=null;
@property(cc.Node) pipeParent1:cc.Node=null;
@property(cc.Node) pipeParent2:cc.Node=null;

> @property(cc.Label) lbScore:cc.Label=null;

> @property(cc.Node) nodeGameOver:cc.Node=null;

> @property(cc.Button) btnStart:cc.Button=null;

> @property(cc.Node) title:cc.Node=null;

---
## 5.方法
> start
```
start () {
        this.initPipe();
    }
```
> update
```
update (dt) {
        let timeTmp=this.time+dt;
        this.time=timeTmp;
        if(this.time>0.5){
            if(this.bird0.node.active){
                this.bird0.node.active=false;
                this.bird1.node.active=true;
            }else if(this.bird1.node.active){
                this.bird1.node.active=false;
                this.bird2.node.active=true;
            }else if(this.bird2.node.active){
                this.bird2.node.active=false;
                this.bird3.node.active=true;
            }else if(this.bird3.node.active){
                this.bird3.node.active=false;
                this.bird0.node.active=true;
            }
            this.time=0;
        }

        if(!this.isGameStart){
            return;
        }
        this.speed=this.speed-0.05;
        this.birdParent.y=this.birdParent.y+this.speed;
        this.birdParent.rotation=-this.speed*10;

        this.moveBg(this.bg0);
        this.moveBg(this.bg1);

        this.movePipe(this.pipeParent0,this.wScreen,this.wPipe);
        this.movePipe(this.pipeParent1,this.wScreen,this.wPipe);
        this.movePipe(this.pipeParent2,this.wScreen,this.wPipe);

        this.checkCollision(this.birdParent,this.pipeParent0,this.wBird,this.hBird,this.wPipe);
        this.checkCollision(this.birdParent,this.pipeParent1,this.wBird,this.hBird,this.wPipe);
        this.checkCollision(this.birdParent,this.pipeParent2,this.wBird,this.hBird,this.wPipe);

    }
```
> moveBg
```
moveBg(bg:cc.Node){
        bg.x=bg.x-1;
        if(bg.x<-this.wScreen){
            bg.x=bg.x+this.wScreen*2;
        }
    }
```
> movePipe
```
movePipe(pipe:cc.Node,wScreen:number,wPipe:number){
        var y=30;
        pipe.x=pipe.x-3;
        if(pipe.x<-wScreen/2-wPipe/2){
            pipe.x=pipe.x+wScreen+wPipe;
            pipe.y=y-Math.random()*y;
            this.score=this.score+1;
            this.lbScore.string=this.score;
        }
    }
```
> onClickUp
```
// 背景点击事件
    onClickUp(){
      this.speed=2.2;
    }
```
> onBtnStart
```
// 游戏开始
    onClickStart(){
        this.nodeGameOver.active=false;
        this.btnStart.active=false;
        this.isGameStart=true;
        this.title.active=false;
        this.reset();
    }
```

> checkCollision
```
// 碰撞检查
    checkCollision(bird:cc.Node,pipe:cc.Node){
    // 左边界检测
        if(bird.x-wBird/2>pipe.x+wPipe/2){
            return;
        }
    // 右边界检测
        if(bird.x+wBird/2<pipe.x-wPipe/2){
            return;
        }
    // 中间位置检测
        if(bird.y+hBird/2<pipe.y+50&&bird.y-wBird/2>pipe.y-50){
            return;
        }
        //console.log('发生了碰撞');
        this.gameOver();
    }
```

> gameOver()
```
// 游戏结束
    gameOver(){
        this.nodeGameOver.active=true;
        this.btnStart.active=true;
        this.isGameStart=false;
        this.title.active=true;
    }
```
> reset()
```
// 游戏重置
    reset(){
        this.nodeGameOver.active=false;
        this.btnStart.active=false;
        this.birdParent.x=0;
        this.birdParent.y=0;
        this.speed=0;
        this.pipeInit();
        this.score=0;
        this.lbScore.string='0';
    }
```
> pipeInit()
 ```
    // 管子初始化
    pipeInit(){
        let pipeStartOffsetX:number=200;
        let spaceX=(this.wScreen+this.wPipe)/3;
        this.pipeParent0.x=pipeStartOffsetX+spaceX*0;
        this.pipeParent1.x=pipeStartOffsetX+spaceX*1;
        this.pipeParent2.x=pipeStartOffsetX+spaceX*2;
    }
```

--------
## 6.开始制作游戏
### 小鸟扇翅膀
> 实现原理,多张 **4张** 图来回切换
新建4个节点，bird0-bird4,将bird0_0 bird0_1 bird0_1 bird0_2 分别拖动至相应位置

### 小鸟受重力作用，下沉
> 通过改变speed将y值一直减小

### 点击按钮后小鸟向上飞
> 通过改变spped将y值一直增加

### 背景图向左移动
> 需要有自减参数

### 管子移动
> 需要有自减参数

### 碰撞检查
> 排除不碰撞的部分，剩下就是发生碰撞的位置

### 小鸟添加旋转
> rotation加上speed的数字

### 计分器，管子移出屏幕后，记1分
> 添加label节点，新建变量score

### 主流程控制
> 开始按钮和游戏结束提示

### 游戏开始控制
>
---

## 7.问题整理
### 无法显示任何内容
>报错：vconsole.min.js:11 TypeError: Cannot read property 'getExtension' of null
>原因：QQ浏览器对webgl的支持有问题
>解决办法：改为使用chrome浏览器就好了

### 小鸟翅膀闪动飞快
> 丢失如下代码：this.time=0;
### 小鸟丢失翅膀在下的帧
> 将canvas里面的小鸟删除，重新拖进一下
### 没开始之前，小鸟乱飞
> 小鸟的某一帧的基准点不在0点
### 管子不显示
> 移动管子的函数写错了

### 控制参数不变的问题
> 有时候修改js代码中的参数值，cocos里面的值并不随着改变。