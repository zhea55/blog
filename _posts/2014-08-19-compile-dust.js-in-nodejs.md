---
layout: post
title: 在nodejs中编译dust.js模板
date: 2014-08-19 22:07
---

### 添加语法高亮
- sublime通过<code>CTRL SHIFT P</code>安装[Dust.js](https://sublime.wbond.net/packages/Dust.js)
- webstorm、intellij idea可以安装[Dust.js](https://github.com/yifanz/Intellij-Dust)

新建dust模板时，使用dust作为文件后缀。比如：<code>comment.dust</code>

{% picture sublime-dust.png alt="sublime截图预览" %}

### 安装dust的编译依赖文件
{% highlight sh%}
$ npm install dustjs-linkedin
{% endhighlight %}

> 如果只安装了官方提供的编译依赖，则需要require以后，调用dust.compile方法进行编译

这里我们继续安装[dusterjs](https://github.com/dmix/dusterjs)插件，将这个项目下载下来，放在你的项目根目录。
{% highlight sh %}
+-- sample
+-- .gitignore
+-- README.md
+-- duster.js           //自动检测文件改动并编译dust的主文件
+-- duster.json         //配置输入dust模板的目录，和输出js的目录
+-- package.json        //项目所需依赖，需要手动npm update获取依赖
{% endhighlight %}


### 配置dusterjs插件
首先打开duster.json文件
{% highlight json%}
{
    "raw_dir": "/src/main/resources/resources/js/dusts",
    "pre_dir": "/src/main/resources/resources/js/templates/compiled"
}
{% endhighlight %}

- <code>raw_dir</code>dust模板所在目录
- <code>pre_dir</code>输出编译好的js文件目录

配置好以后，使用命令行进入项目根目录，然后
{% highlight sh %}
$ npm update
$ node duster.js
{% endhighlight %}

>启动duster.js以后，在模板目录内新建、保存模板，都会自动进行编译

{% picture dusterjs.png alt="dusterjs自动编译模板" %}


### 在浏览器中使用编译后的模板

{% highlight html %}
<script src='/your/path/comment.js' /></script>
{% endhighlight %}

{% highlight js %}
//上面的script代码一定要在render之前执行
dust.render('comment', { comment: comment }, function(err, out) {
  if(!err) {
    $('#someDiv').append(out);
  }
});
{% endhighlight %}

