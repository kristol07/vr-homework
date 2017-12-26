# 虚拟现实技术及应用课程大作业
# -- _基于A-frame的简易架子鼓VR实现_

## 作者：刘林 学号：SY1624106

## 1. A-Frame开发框架
> A web framework for building virtual reality experiences. Make WebVR with HTML and Entity-Component. Works on Vive, Rift, desktop, mobile platforms.

简单地说，A-Frame就是一个在web上用来实现3D和虚拟现实体验的开源框架，官方网站：[A-Frame](https://aframe.io/)

一些比较有名的项目包括：
* A-Painter: 在网页中实现虚拟现实画画，详见 [A-Painter](https://github.com/aframevr/a-painter)，
* aframe-audioanalyser-component: 虚拟现实下的音频可视化，详见 [Audioanalyser](https://github.com/ngokevin/kframe/tree/master/components/audioanalyser/)

## 2. 应用功能介绍
基于A-Frame简单实现了架子鼓的虚拟现实体验，用户可以通过光标点击乐器，并听到乐器的变化及听到其发出相应的乐器声音。
此外还有与真实模型的对比。

## 3. 应用设计过程
* 在网上寻找相应的架子鼓模型（参考 [架子鼓模型](https://sketchfab.com/models/3ed0f09afae546c3b6b2ac6816259b5b) ），初步设计架子鼓的样子，并利用A-Frame的Entity-Component-System中的基础的元素，如圆柱体，圆面等，调整其位置，转角，大小等设计出原型。

* 对Cymbal和Drum进行贴图，添加声音、动画，使其与用户能够产生初步互动。

* 完善场景设计，引用开源的Environment模块加入森林场景；导入真实的架子鼓模型

## 4. 应用成果展示
成果可在[VR-Homework](https://vr-homework.glitch.me/) 在线体验

在电脑中观看效果如下：
图1：![pic1](https://github.com/Joelliu/vr-homework/blob/master/result/pic1.png?raw=true)
图2：![pic2](https://github.com/Joelliu/vr-homework/blob/master/result/pic2.png?raw=true)
在电脑网页打开的情况下，使用快捷键Ctrl+Alt+I可以打开A-Frame的Inspector工具，效果如下：
图3：![pic3](https://github.com/Joelliu/vr-homework/blob/master/result/pic3.png?raw=true)

除了观看之外，还能够移动光标点击乐器器件使其发出相应的位置变化和声音信息。

还可以用手机浏览器打开网站，在加载成功后点击右下角的Cardboard图标，即可用虚拟现实眼镜设备观看。

可能存在的问题：
手机浏览器情况下加载较慢，可能是 glitch.com 网页的原因；
加载出来的场景观看时移动反应很慢，Environment模块、音频文件太大导致性能不是很好。

缺点：
缺乏更多的交互操作，用户只能固定在一个位置不能移动，且只能用光标一次点击一个，不能实现乐器的完整功能；
模型制作效果简陋，和真实模型差距较大。

## 5. 代码解释

```html
<script>这里是需要利用的框架、模块，包括A-Frame框架，使用到的Environment-Forest模块</script>

<a-assets>这里是需要利用的音频，图片素材，包括乐器的声音，乐器的纹理贴图</a-assets>

<a-scene environment="preset: forest">这是构建整个场景所需的代码，其中使用了森林场景
  <a-entity>这是一个个物体的代码，包括cylinder，circle，sound，text，model等可以看作是entity，所有这些都写在scene代码中间</a-entity>
  <a-camera>确定相机信息，通常就是处于原点（注意电脑和手机上的初始点不同）
   <a-cursor>产生一个光标，使用户知道视角中心在哪</a-cursor>
  </a-camera>
<a-scene>
```



