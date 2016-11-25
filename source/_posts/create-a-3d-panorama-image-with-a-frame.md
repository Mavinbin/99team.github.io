title: 使用 A-Frame 创建 3D 全景图
date: 2016-10-22 10:11:28
categories: 优秀译文
author: 米粒
---

{% asset_img aframe.png A-Frame %}


在 Mozilla 工作的五年里我见过许多很棒的项目。它们有的很受欢迎，有的很小众，但它们始终没有激起我与 MozVR 团队做 WebVR 和 [A-Frame](https://aframe.io) 项目的热情。

A-Frame 是一个致力于成为“构建 Web 虚拟现实的模块”，一个使用标记语言 或 JavaScript 在浏览器中创建 VR 体验的库。迫不急待的想使用这个项目就让我们从简单的示例开始：创建一个交互式的全景图比如[这个](https://aframe.io/examples/showcase/sky/)!

[查看DEMO](https://davidwalsh.name/demo/3d-panorama-image.html)

## 获取 3D 图片

获取一张符合全景效果要求（公认的柱状全景格式）的 3D 图片的最简单方式就是使用手机。Dan Zajdband 的 [Guri VR: 我们其它人的虚拟现实](https://source.opennews.org/en-US/articles/virtual-reality-rest-us/)识别 APP iOS版([谷歌街景](https://itunes.apple.com/app/id904418768?mt=8240)) 和安桌版
([Photo Sphere](https://support.google.com/googlecamera/?hl=en#2839084) 或 [Cardboard Camera](https://play.google.com/store/apps/details?id=com.google.vr.cyclops&hl=en))。Dan 的这篇优秀文章还提到 Flickr 上的 [Equirectangular 群组](https://www.flickr.com/groups/equirectangular/)，如果你想简单的获取一张图片来实验的话。

使用手机来获取一张可用图像可能是个不小的挑战 -- 你要保证在旋转手机的时候非常平稳来避免边缘出现锯齿。

_友情提示：案例中我为 A-Frame 提供了一个样品图像，因为谷歌街景的图片大小有 10M，直接将这么大的图片展现出来就太禽兽了。如果你想看我用 GSV 应用制作的图片[点击这里](https://davidwalsh.name/demo/3d-panorama-circle.jpg)。这张图片的视角是我站在生活中小路上的中间。_

## 使用 A-Frame 创建全景效果

不管信不信，获取一张好的图片是最困难的部分，因为 A-Frame 可以非常容易的将图片转成 3D 可视化。
`` A-Frame 元素可以用来创建全景效果 ``:

```
<a-scene>
<a-sky src="https://davidwalsh.name/demo/3d-image.jpg" rotation="0 -130 0"></a-sky>
</a-scene>

```

以上代码是 A-Frame 常用语法（由HTML编写）；你也可以使用 JavaScript 来创建元素：

```
// 创建场景
var scene = document.createElement('a-scene');

// 创建天空
var sky = document.createElement('a-sky');
sky.src = '3d-image.jpg';
sky.setAttribute('rotation', { x: 0, y: -130, y: 0 });

// 插入到页面中
scene.appendChild(sky);
document.body.appendChild(scene);

```

[`rotation` 属性](https://aframe.io/docs/0.2.0/components/rotation.html) 用来接收空间分隔 `x`, `y`, 和 `z` 轴旋转值；你可以使用它们来自定义视角位置。

A-Frame 可以让你点击、固定以及拖动组件来旋转图像。你也可以点击 VR 眼镜按钮在手机（cardboard maWebVR 所有网页 -- 这是下一件大事！完成一个不错的装饰！）或支持 WebVR 的浏览器上以 3D 模式查看图像。

[查看DEMO](https://davidwalsh.name/demo/3d-panorama-image.html)

## A-Frame 简单创建 3D！

当我说获取照片是困难的部分时并没有夸张；因为使用 A-Frame 来创建 3D 全景效果时仅需要使用少量的标记语言。创建全景图是一个流行的使用案例，但该效果仅仅是 A-Frame 的冰山一角。还想了解 A-Frame 可以做什么？查看更多案例请访问 [A-Frame 官网](https://aframe.io/) 以及 期待在所有网页中看到更多关于 WebVR 的事 -- 这是下一件大事！