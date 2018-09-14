# cocos creator 物理弹球学习笔记 [返回首页](/)
# 腾讯课堂

# 资料下载

[学前资料](/download/ball/ballTexture.rar)

## 物理碰撞
### 启用物理世界
```javascript
  let manager=cc.director.getPhysicsManager();
  manager.enabled=true; //启用物理世界
  let Bits = cc.PhysicsManager.DrawBits;
  manager.debugDrawFlags="e_none";//设置调试绘制标志，很可惜没设置成功
    Bits[0] // e_none
    0:"e_none"
    1:"e_shapeBit"//绘制形状
    2:"e_jointBit"//绘制关节链接信息
    4:"e_aabbBit"//绘制包围盒
    8:"e_pairBit"
    16:"e_centerOfMassBit"
    32:"e_particleBit"
    63:"e_all"
    64:"e_controllerBit"
```


### 刚体 RigidBody
```
  刚体 RigidBody
    getMass 获取刚体的质量。
    gravityScale Number 缩放应用在此刚体上的重力值（重力对刚体的影响）
    linearVelocity Vec2 刚体在世界坐标下的线性速度
    linearDamping 用于衰减刚体的线性速度。（线性阻力）
    angularVelocity Number 刚体的角速度
    angularDamping Number Angular damping 用于衰减刚体的角速度。（旋转阻力）
    enabledContactListener Boolean 是否启用接触接听器。
  刚体类型  cc.RigidBodyType
    Static  零质量，零速度，可以手动移动。
    Kinematic  零质量，可以被设置速度。
    Dynamic  有质量，可以设置速度，力等。
    Animated  Kinematic 类型的扩展，可以被动画控制动画效果。
```
### 碰撞 Collider
```
  物理碰撞形状
    Box 四边形
    Chain 链条
    Circle 圆形
    Polygon 多边形
  物理碰撞
    sensor 是否为传感器类型，产生回调，但不发生碰撞效果
    density 碰撞体密度
    friction 碰撞体摩擦力
    restitution 弹性系数
```
### Vec2
```
  Vec2原名Point，它既可以表示一个二维坐标点，又可以表示一个二维向量。
  直接使用v2
```
