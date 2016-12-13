title: 理解使用HTML5布局页面的合适方式
categories: 优秀译文
author: Mavinbin
---

> 本文翻译自：http://www.developer.com/lang/understanding-the-proper-way-to-lay-out-a-page-with-html5.html

## 引言
浏览器中渲染的网页由许多东西组成-logo、信息文本、图片、超链接、导航结构等等。
HTML5为网页提供了一系列允许你创建结构化布局的标签。这些元素通常被称为语义化标签，因为它们能够清楚地给开发者和浏览器传达它们的意义和目的。本文将讨论一些有助于网页布局的重要的HTML5标签。

## 语义化标签
语义化标签能够将自身的含义和使用目的清晰地传达给开发者和浏览器。网页开发者频繁地使用`<div>`标签来给网页布局，然而，`<div>`标签本身并不能传达它在网页中表示什么。`<div>`标签可能包裹着导航按钮或者放置博客帖子的列表，但是使用`<div>`几乎不能给开发者和浏览器传达更多的信息。通常CSS类给`<div>`元素揭示了一些其预期的使用目的。比如考虑下面的标记：

```html
<div class="header">...</div>
```

在上面的标记中，CSS类header会让你想到这个`<div>`可能是用来干嘛的。然而，上面例子中的CSS类不能很容易地被识别这个`<div>`可能是用来干嘛的。这是因为，`<div>`是一个具有通用目的的元素，它不具有特定的文档职责（译注：即在html文档中没有特定含义），只是简单地标记一个网页的分割块或者小节，但是不能指示这个小节里能放什么。

HTML5包含了一系列的标记元素来克服这个难题。这些元素拥有有意义的名称，因此只需通过看这些元素，你就能想到它们的内容。这些HTML5的语义化标签罗列如下（这里列出的不是详尽的列表）：

* `<header>`
* `<footer>`
* `<section>`
* `<arcticle>`
* `<aside>`
* `<nav>`

正如你所见的，这些元素非常有表达力，你可以马上想到其预期的使用目的。下图展示了一个使用这些元素来设计的简单网页布局：

{% asset_img page_layout.png 页面布局 %}

上图展示了一个各种元素的典型排版。请注意，它们在网页中的准确位置纯粹依赖于布局。例如，`<aside>`元素可以被放置在`<section>`元素的左边或者甚至是上面或下面。

下图展示了利用这些元素的实际网页：

{% asset_img actual_page.png 实际页面 %}

既然你对语义化元素有了一些想法，那么让我们来讨论每个元素的更多细节。出于我们讨论的目的，我们将以上面的简单网页为例子。

## header元素
`<header>`元素表示整个网页或者一个小节的头部。W3C规范定义`<header>`元素是像这样的：

> `<header>`元素表示一组具有引导性或者导航性的辅助。header元素通常是用来包含小节的标题，但这不是必需的。header元素还可以用于包裹小节的内容表格、搜索表单或者任何相关的logo。

上面的解释告诉我们，`<header>`元素可以包含标题、logo图片、支持文本和可选的导航结构。大部分网页具有以logo、标语和/或支持文本组成的页面标题，header元素扮演着所有这些元素的容器的角色。请注意，header元素不仅可以用于整个网页，而且可以用于网页中独立的小节中。例如，除了页面级别的header，你可以在页面小节的联系信息中使用header元素。

下面的标记展示了`<header>`元素如何用在我们例子的网页中的：

```html
<header>
  <h1>This is page heading</h1>
</header>
```

## nav元素
`<nav>`元素用于放置导航按钮或者任意的导航结构，如超链接。W3C规范定义`<nav>`元素是像这样的：

> `<nav>`元素表示带有导航链接的小节。

`<nav>`小节可以包含从网站到其他网页或者相同网页的其他部分的链接（译注：即页面跳转和页内锚点）。建议只把`<nav>`标签使用于主导航结构，而不要用于超链接的小集合（比如通常放在网页底部的跳转链接）。

下面的标记展示了`<nav>`元素如何用在我们例子的网页中的：

```html
<nav>
  <ul>
    <li><a href="#">Home</a></li>
    <li><a href="#">About Us</a></li>
    <li><a href="#">Contact Us</a></li>
  </ul>
</nav>
```

## section元素
按照W3C规范，`<section>`元素表示文档或者应用的通用小节。`<section>`元素不能与`<div>`混淆，`<section>`元素是内容的主题组，而`<div>`没有任何这样的限制。W3C规范进一步明确-`<section>`只适用于在文档大纲中明确列出的内容。`<section>`元素可以使用的一些例子包括网页的联系信息小节、网页的公告小节和标签化的用户界面的标签页（译注：即tab结构）。section通常有一些标题。

下面的标记展示了`<section>`元素的看起来如何：

```html
<section>
  <h1>This is a section heading</h1>
  <p>
    Hello world! Hello world! Hello world!
    Hello world! Hello world! Hello world!
    Hello world! Hello world! Hello world!
  </p>
</section>
```

section也可以有自己的`<header>`元素和`<footer>`元素。section元素和包含章节的印刷书的小节或者包含新闻条目的新闻报纸的小节是相似的。

## article元素
`<arcticle>`元素表示如博客帖子、论坛帖子或者评论这种独立内容的条目小节。article元素中的内容在内容聚合的情况下，要能独立分发或者可重用。

下面的标记展示了`<article>`元素看起来如何：

```html
<article>
  <h1>This is article heading</h1>
  <p>
    Hello world! Hello world! Hello world!
    Hello world! Hello world! Hello world!
    Hello world! Hello world! Hello world!
  </p>
</article>
```

你会发现，人们有时一起使用`<section>`和`<article>`或者使用嵌套的`<article>`，目前没有严格和准确的规则来决定它们的嵌套方式。无论何时一起使用它们，试着确保生成的结构满足W3C规范所给定的各种元素的预期使用目的。

## aside元素
`<aside>`元素用于放置与周围内容相关的内容，但同时本身是一个独立块。如果你从页面中去掉`<aside>`，它不能改变或者修改主体页面内容的含义或者明晰度。将它考虑成是一个侧边栏，它提供一些额外的、相关的，但独立的关于讨论的话题的信息。一些`<aside>`的例子包括-额外的信息、相关的链接和上下文广告。`<aside>`可以放置任何包含文本信息和图片类型的内容。例如，`<aside>`在例子的页面中使用看起来像这样：

```html
<aside>
  <figure>
    <img src="images/laptop.png" height="100px" width="100px" />
    <figcaption>Figure caption goes here</figcaption>
  </figure>
  <p>
    Hello world! Hello world! Hello world!
    Hello world! Hello world! Hello world!
  </p>
</aside>
```

正如你所见，上面展示的`<aside>`元素包含一个`<figure>`元素和以`<p>`元素的形式组合的一些文本。`<figure>`元素用于表示图表，它依次包含`<img>`和`<figcaption>`元素。`<img>`标签指向实际显示的图片，`<figcaption>`元素则放置着图表的标题。

## footer元素
`<footer>`元素表示整个页面或者`<section>`元素的底部，它用于包含如版权声明的底部信息。例子的网页中的`<footer>`元素看起来像这样：

```html
<footer>
  <hr />
  Copyright (C) 2013. All rights reserved.
</footer>
```

## 案例网页的完整标记

```html
<!DOCTYPE html>
<html>
<head>
    <title>Sample HTML5 Layout</title>
    <link href="StyleSheet.css" rel="stylesheet" />
</head>
<body>
    <header>
        <h1>This is page heading</h1>
    </header>
    <nav>
        <ul>
            <li><a href="#">Home</a></li>
            <li><a href="#">About Us</a></li>
            <li><a href="#">Contact Us</a></li>
        </ul>
    </nav>
    <article>
        <h1>This is article heading</h1>
        <p>
            Hello world! Hello world! Hello world!
            Hello world! Hello world! Hello world!
            Hello world! Hello world! Hello world!
        </p>
    </article>
    <aside>
        <figure>
            <img src="images/laptop.png" height="100px" width="100px" />
            <figcaption>Figure caption goes here</figcaption>
        </figure>
        <p>
            Hello world! Hello world! Hello world!
            Hello world! Hello world! Hello world!
        </p>
    </aside>
    <section>
        <h1>This is a section heading</h1>
        <p>
            Hello world! Hello world! Hello world!
            Hello world! Hello world! Hello world!
            Hello world! Hello world! Hello world!
        </p>
    </section>
    <footer>
        <hr />
        Copyright (C) 2013. All rights reserved.
    </footer>
</body>
</html>
```

## 为案例网页创建CSS

在前面创建的案例网页中有StyleSheet.css链接其中。这个样式表包含了一些管理各种语义化元素的外观和感觉的CSS规则。在更真实的情况下，你可能会创建CSS类，然后把它们附到各自的元素上。不过，在这个例子中，为元素定义的样式展示如下：

```css
article
{
    padding:5px;
    border:dotted 3px #ff006e;
    margin-top:5px;
}

header
{
    padding:0px;
    text-align:center;
}

aside
{
    margin-top:5px;
    background-color:#f0eaea;
    padding:5px;
    text-align:center;
    font-style:italic;
    border:double 3px #b200ff;
}

section
{
    padding:5px;
    border:dashed 3px #0026ff;
    margin-top:5px;
}

footer
{
    padding:5px;
    text-align:center;
    font-weight:bold;
}

nav
{
    text-align:center;
}
ul li
{
    display:inline;
    padding-left:5px;
    padding-right:5px;
    text-align:left;
    font-size:16px;
    font-weight:bold;
}
```

上面定义的CSS规则非常的直截了当，不需要解释。简单地把这些规则添加到新的样式表文件中，然后在你先前做的案例网页中链接这个样式表。

## 总结
本文讲到了能够用于网页合适布局的HTML5的语义化标记元素。不像`<div>`元素，语义化元素预期是用于特定目的的。我们在本文讲到的元素包括`<header>`、`<nav>`、`<footer>`、`<section>`、`<arcticle>`和`<aside>`。
