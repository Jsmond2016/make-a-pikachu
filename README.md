# 皮卡丘制作

![](https://i.loli.net/2018/01/31/5a717c36119e3.png)

[预览](http://js.jirengu.com/quyeneroju/7/edit)

## 目录：

- 鼻子(nose)
- 眼睛(eye)
- 脸颊(face)
- 上嘴唇(upperLip)
- 下嘴唇(lowerLip)
- 舌头(tongue)

## 整体布局和默认样式

### 布局
使用 `flex` 布局，水平和垂直居中

### 重置默认样式：

- `margin: 0`
- `padding: 0`
- `box-sizing: border-box`  目的是在使用的时候不用去测算具体的长度，设置padding和margin的时候不会改变盒子的宽高
- 包括 `*::before,*::after{box-sizing; border-box}` 

### 适配移动端

考虑到手机的屏幕宽度有限，从而看到全部的效果需要设置皮卡丘的整体宽度在手机屏幕宽度的范围以内；

皮卡丘的最大宽度 ==> 主流手机屏幕的最小宽度  （二者近似相等）

以确保所有的手机端都可以看到；

##  nose

实际上是一个圆形，让其右、下、左边框的`border` 颜色为透明即可

使用到知识点：  

- `border-radius: 50%;` 表示圆角
- `border-color: black transparent transparent transparent  `  上、右、下、左 边框的颜色分别为：黑色、透明、透明、透明
- 居中：使用绝对定位的时候，`left: 50%;` 实际上是左框线在中线上，需要使盒子的中线和外层需要居中的盒子的中线对齐才是居中，因此，需要往左移盒子一半的宽度，需要使用 负mafrgin: `margin-left: -length/2` ，或者使用 `transform: translateX(-50%)`  

## eye

依然是使用画圆的方法，设置背景色，边框厚度和颜色，绝对定位。

眼珠子因为在 eye 里面，使用的是 `::before{}` 进行设置。定位，边框、背景色同理；

## face

左右两边的 face 颊实际上就是2个圆，定位的方式需要 **注意** 

- 最好是以中线为参考线，不要以边框为参考线，
- 因为我们难以确定用户的屏幕宽度以及浏览器打开页面的大小是多少从而使用 js 去动态调节，简单好用的方式是以中线为参考线，不会影响整体布局；

## upperLip

难点在于如何实现 upperLip 的曲线？

![](https://i.loli.net/2018/01/31/5a717b54324b6.png)

原理是：

- 画一个长方形 ：给 div 设置宽高
- 设置长方形的左下角的圆角幅度 ：使用`border-radius` 设置圆角  
- 让其他的边框颜色和背景色同样的颜色 
- 旋转长方形的角度为合适角度 ：  `transform: rotate(n deg)` 



![](https://i.loli.net/2018/01/31/5a717b5432c6c.png)



##  lowerLip

lowerLip 实际上是一个椭圆，使用的依然是 `border-radius` 的知识点 

- `border-radius` 制作椭圆
- 外层 wrapper 定位 和 给定宽高，使用 overflow 使内部多余的椭圆部分看不见
- 细节处理：
  - 设置 lowerLip 的背景色为整体黄色和背景统一，遮盖在 wrapper 下面和 upperLip 上面多余的颜色
  - 调节  upperLip  的厚度和位置到合适的值以实现完美遮盖

![](https://i.loli.net/2018/01/31/5a717dc26a5f6.png)

## tongue 

实际上和lowerLip的原理相似，但是可以不用使用椭圆的了，设置一个合适大小的圆在 lowerLip 以内，设置背景色，让多余的 部分被  lowerLip overflow 即可完美实现。



参考资料：

- [border-radius](http://www.runoob.com/css3/css3-border-radius.html)
- [transform](http://www.runoob.com/cssref/css3-pr-transform.html)