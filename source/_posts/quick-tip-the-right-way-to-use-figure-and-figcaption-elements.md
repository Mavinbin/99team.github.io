title: 快捷技巧：使用figure&figcaption元素的正确方式
categories: 优秀译文
author: Mavinbin
---

> 本文翻译自：https://www.sitepoint.com/quick-tip-the-right-way-to-use-figure-and-figcaption-elements/

figure和figcaption元素是经常一起使用的两个语义化元素，如果你还没看过[规范](https://www.w3.org/TR/html5/grouping-content.html#the-figure-element)，还没有机会在你的项目中使用它们，或者不知道在项目中如何使用它们的话，这里有些关于如何正确使用它们的小技巧。

figure元素通常用于图片：

```html
<figure>
  <img src="dog.jpg" alt="Maltese Terrier">
</figure>
```

figure元素表示内容的自包含单元，这意味着你就算把元素移到文档之下很远的地方或者是文档的末尾，它都不会影响文档的含义。

因此，我们还需要记住的是，并不是每张图都是figure。

## figure中的多张图
你可以将多个img标签放在figure中，如果它们在你文档的上下文是相关联的。

```html
<figure>
  <img src="dog1.jpg" alt="Maltese Terrier">
  <img src="dog2.jpg" alt="Black Labrador">
  <img src="dog3.jpg" alt="Golden Retriever">
</figure>
```

## 能和figure一起用的其他元素
figure也并不限制仅图片可用，你可以为如下这样的东西使用它：
* 代码块
* 视频
* 音频剪辑，或
* 广告

这是figure用于代码块的一个例子：

```html
<figure>
  <pre>
    <code>
      p {
          color: #333;
          font-family: Helvetica, sans-serif;
          font-size: 1rem;
      }
    </code>
  </pre>
</figure>
```

## 将figure嵌套到另一个figure中
你可以将figure嵌套到另一个figure中，如果这么做有意义的话。这里，添加了ARIA的role属性来提高语义化。（译注：ARIA是Accessible Rich Internet Application的缩写，指无障碍互联网应用）

```html
<figure role="group">
  <figcaption>Dog breeds</figcaption>
  <figure>
    <img src="dog1.jpg" alt="Maltese Terrier">
    <figcaption>Adorable Maltese Terrier</figcaption>
  </figure>
  <figure>
    <img src="dog2.jpg" alt="Black Labrador">
    <figcaption>Cute black labrador</figcaption>
  </figure>
</figure>
```

想更深入地了解针对ARIA使用figure和figcaption元素，请查看我更早前的关于[如何通过HTML5有效地使用ARIA](http://www.sitepoint.com/how-to-use-aria-effectively-with-html5/)的文章。

## figcaption的正确用法
figcaption元素表示figure的标题或者图例。
不是每个figure都需要figcaption。
但是，当使用figcaption时，它理论上应该是figure块中的第一个或者最后一个元素。

```html
<figure>
  <figcaption>Three different breeds of dog.</figcaption>
  <img src="dog1.jpg" alt="Maltese Terrier">
  <img src="dog2.jpg" alt="Black Labrador">
  <img src="dog3.jpg" alt="Golden Retriever">
</figure>
```

或者

```html
<figure>
  <img src="dog1.jpg" alt="Maltese Terrier">
  <img src="dog2.jpg" alt="Black Labrador">
  <img src="dog3.jpg" alt="Golden Retriever">
  <figcaption>Three different breeds of dog.</figcaption>
</figure>
```

## 你也可以在figcaption中使用流元素
如果你需要给图片添加更多的语义，你可以使用如h1和p元素。

```html
<figure>
  <img src="dogs.jpg" alt="Group photo of dogs">
  <figcaption>
    <h2>Puppy School</h2>
    <p>Championship Class of 2016</p>
  </figcaption>
</figure>
```

你是否有任何关于使用figure和figcaption元素的其他技巧呢？
