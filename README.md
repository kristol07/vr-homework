#  _基于A-frame的简易架子鼓和音乐播放器VR实现_

## 作者：刘林  /&nbsp;  学号：SY1624106

## 1. A-Frame开发框架
> A web framework for building virtual reality experiences. Make WebVR with HTML and Entity-Component. Works on Vive, Rift, desktop, mobile platforms.

简单地说，A-Frame就是一个在web上用来实现3D和虚拟现实体验的开源框架，官方网站：[A-Frame](https://aframe.io/)

一些比较有意思的项目包括：
* A-Painter: 在网页中实现虚拟现实画画，详见 [A-Painter](https://github.com/aframevr/a-painter)，
* aframe-audioanalyser-component: 虚拟现实下的音频可视化，详见 [Audioanalyser](https://github.com/ngokevin/kframe/tree/master/components/audioanalyser/)
* [Minecraft简略版](https://css-tricks.com/minecraft-webvr-html-using-frame/)

## 2. 应用功能介绍
- 基于A-Frame简单实现了**架子鼓**的虚拟现实体验，用户可以通过光标点击乐器，并听到乐器的变化及听到其发出相应的乐器声音；
- 实现简单的**音乐播放器**功能，用户将光标移动到真实架子鼓模型旁的粉红色方块上网页将自动播放音乐，点击方块实现暂停，移出再移入可重新播放；
- 实现简单的点歌（切换歌曲）功能，用户点击真实架子鼓模型上方的任一张图片，可将播放歌曲切换成相应歌曲。

## 3. 应用设计过程
* 在网上寻找相应的架子鼓模型（参考 [架子鼓模型](https://sketchfab.com/models/3ed0f09afae546c3b6b2ac6816259b5b) ），初步设计架子鼓的样子，并利用A-Frame的Entity-Component-System中的基础的元素，如圆柱体，圆面等，调整其位置，转角，大小等设计出原型；

* 对Cymbal和Drum进行贴图，添加声音、动画，使其与用户能够产生初步互动；

* 完善场景设计，引用开源的Environment模块加入森林场景；导入真实的架子鼓模型；

* 参考[原有项目](https://bird-error.glitch.me/)的代码，实现图片点击动画，再利用框架的sound元素设计实现简单的音乐播放器功能。

## 4. 应用成果展示
成果可在[VR-Homework](https://vr-homework.glitch.me/) 在线体验

在电脑中观看效果如下：

![pic1](https://github.com/Joelliu/vr-homework/blob/master/result/pic1.png?raw=true)

![pic2](https://github.com/Joelliu/vr-homework/blob/master/result/pic4.png?raw=true)

在电脑网页打开的情况下，使用快捷键Ctrl+Alt+I可以打开A-Frame的Inspector工具，效果如下：

![pic3](https://github.com/Joelliu/vr-homework/blob/master/result/pic5.png?raw=true)

除了观看之外，还能够**移动光标点击乐器器件使其发出相应的位置变化和声音信息**。

且网页在加载成功后，**将光标移至真实模型旁的粉红色方块上网页将会自动播放音乐，点击上方的任一图片可以实现切换歌曲**。

还可以用手机浏览器打开网站，在加载成功后点击右下角的Cardboard图标，即可用虚拟现实眼镜设备观看。

## 5. 总结
实现了VR下的简单架子鼓功能和音乐播放器功能。

可能存在的问题：
+ 手机浏览器情况下加载较慢，可能是 glitch.com 网页的原因；
+ 加载出来的场景观看时移动反应很慢，Environment模块、音频、图片都需要加载，文件太大导致性能不是很好；
+ 无法播放音乐、切换歌曲，打击乐器也无法听到声音；
+ 电脑浏览器情况下观看正常，但是无法实现cardboard模式。

缺点：
- 缺乏更多的交互操作，用户只能固定在一个位置不能移动，且只能用光标一次点击一个，不能实现架子鼓的完整功能；
- 模型制作效果简陋，和真实模型差距较大。

## 6. 代码解释

```html
<script>这里是需要利用的框架、模块，包括A-Frame框架，使用到的Environment-Forest模块</script>

<a-assets>这里是需要利用的音频，图片素材，包括乐器的声音，乐器的纹理贴图</a-assets>

<a-scene environment="preset: forest">这是构建整个场景所需的代码，其中使用了森林场景
  <a-entity>这是一个个物体的代码，包括cylinder，circle，sound，text，model等可以看作是entity，所有这些都写在scene代码中间</a-entity>
  <a-camera>确定相机信息，通常就是处于原点（注意电脑和手机上的初始点不同）
   <a-cursor>产生一个光标，使用户知道视角中心在哪</a-cursor>
  </a-camera>
<a-scene>
  
<a-animation>这里是实现动画和互动的功能，包括击鼓发出声音，以及鼓位置、转动变化</a-animation>
  
<script>最后的javascript代码参考了原有项目(见应用设计过程介绍)的一些代码（初学者并不熟悉javascript）,增强应用互动特性，实现播放、暂停、切换歌曲功能</script>
```
