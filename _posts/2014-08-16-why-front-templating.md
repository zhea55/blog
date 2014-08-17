---
layout: post
title: 为什么要在前端渲染数据？
date: 2014-08-16 12:31
---

### 减少数据传输
先来看看传统的后台数据渲染，这里以[freemarker](http://freemarker.org/)举例：

    <#list bookList as book>
      <h2>${book.title}</h2>
      <p>${book.authorName}</p>
    </#list>


{% highlight html %}
<!-- 输出结果为 -->

<h2>你一定爱读的极简欧洲史</h2>
<p>约翰•赫斯特</p>
<h2>我们台湾这些年</h2>
<p>廖信忠</p>
<h2>白光</h2>
<p>连城三纪彦(Renjo Mikihiko)</p>
...
{% endhighlight %}

输出的<code>html</code>中包含了很多标签。嗯，我想说

- 这些标签也占用了网络传输量。
- 后端进行渲染，占用的是服务器端的资源。

通常情况下，我们面对的模板都要复杂得多，每个标签有很多属性，比如：<code>id</code>、<code>classname</code>、<code>attribute</code>...

也就是说，每一次网络请求，这些重复的内容都会从后台传输到浏览器。


{% picture server-side-templating.png alt="服务器端渲染流程" %}
{% picture client-side-templating.png alt="服务器端渲染流程" %}

### 前后端开发解耦
传统的后端渲染流程，导致后端开发人员需要维护混乱不堪的代码。
>   <code>html</code>里面少一个<code>></code>，或者<code>"</code>都可能导致很隐含的bug

换到前端渲染，后端开发人员只需要提供数据，无需关心渲染逻辑。
