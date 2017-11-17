---
title:  "欢迎使用 ALab 团队技术博客（样篇）"
author: Louis
header:
  image: /assets/images/unsplash-image-9.jpg
read_time: true
categories: 
  - Sample
tags:
  - Sample
  - ALab
toc: true
toc_label: "Blog Sample"
---
这是一篇利用**Markdown**格式编写的一篇博客样本，大家可以参考这篇样本来编写博客，这里主要介绍ALab团队技术博客的编写注意事项。欢迎大家利用此博客进行：
- *整理知识，学习笔记*
- *记录对有关技术问题的思考*
- *撰写技术方案工程实践文稿（代码支持）*
- *撰写技术方案算法文稿（LaTex公式支持）*

这是一个搭建在[Github Pages](https://pages.github.com/)上，利用[Jekyll](https://jekyllrb.com/)静态页面引擎，并使用[minimal-mistakes](https://github.com/mmistakes/minimal-mistakes)模板的博客。

## 编写技术博客步骤

以下是第一次使用的步骤：

1. 克隆ALab团队技术博客代码库[Aqara-ALab/blog](https://github.com/Aqara-ALab/blog)
2. 在/_data/authors.yml文件中补充作者信息，可以参考Louis，直接复制一份，进行修改
3. 在/assets/images/文件夹下创建一个以作者名称命名的文件夹，用于存放博客文章中会用到的图片
4. 编写Markdown格式的博客文章，存放至/_posts/文件夹下，博客文章的名称格式为：年-月-日-标题名称.md，如：2017-11-17-blog-sample.md（标题中多个英文字符之间用“-”间隔，若为中文标题，则无需间隔）
5. 提交至代码库[Aqara-ALab/blog](https://github.com/Aqara-ALab/blog)
6. 稍等片刻（30秒以内），刷新博客主页，即可看到博客文章，若需重新编辑，可重复步骤4、5

后续再提交博客文章，也只需要步骤4、5、6即可。

## 编写博客文章格式规范

一篇博客文章分为两部分内容：

- 博客文章的配置信息
- 博客文章的正文内容

### 配置信息

由于此博客是利用Jekyll静态页面引擎，博客文章的配置信息是YAML标记语言，这是一种专门用于配置文件的语言，相关介绍可参考：[YAML 语言教程](http://www.ruanyifeng.com/blog/2016/07/yaml.html?f=tt)。但其实我们这里所用到的配置信息比较常见的有：

- title：文章的标题
- author: 作者，请填写补充在/_data/authors.yml文件中的作者名称
- header: 博客文章的头部，可放图片，图片放至/assets/images/文件夹下，这里指定相对路径即可
- categories: 该文章的分组，可填写多个
- tags: 该文章的标签，可填写多个
- toc: 是否展示子标题列表

具体可参考这篇文章的配置信息，如下：

```yaml
---
title:  "Blog Sample"
author: Louis
header:
  image: /assets/images/alab-head.jpg
read_time: true
categories: 
  - Sample
tags:
  - Sample
  - ALab
toc: true
toc_label: "Blog Sample"
---
```
### 正文内容

该博客支持Markdown格式，我们使用的是[kramdown](https://kramdown.gettalong.org/)解析器，利用[mathjax](https://www.mathjax.org/)支持Latex公式的编写，支持代码的编写。

**关于Markdown**

关于Markdown，大家可以参考这篇文章的介绍：[Markdown新手指南](http://www.jianshu.com/p/q81RER)，在Windows系统环境，有一些常用的Markdown编辑软件，如：[MarkdownPad](http://markdownpad.com/)，[Yu Writer](https://ivarptr.github.io/yu-writer.site/)，[有道云笔记](http://note.youdao.com/)等等。

## 支持的功能

下面简单介绍一些常用的Markdown格式的编写规范：

Markdown 是一种方便记忆、书写的纯文本标记语言，用户可以使用这些标记符号以最小的输入代价生成极富表现力的文档：譬如您正在阅读的这份文档。它使用简单的符号标记不同的标题，分割不同的段落，**粗体** 或者 *斜体* 某些文字，更棒的是，它还可以

### 1. 图片

外部图片链接地址：
```md
![alab-logo](http://7d9jr9.com1.z0.glb.clouddn.com/alab-avatar-lucency.png)
```

![alab-logo](http://7d9jr9.com1.z0.glb.clouddn.com/alab-avatar-lucency.png)
 
内部图片链接地址：
```md
![alab-logo-gray](https://aqara-alab.github.io/blog/assets/images/alab-avatar-gray.png)
```
![alab-logo-gray](https://aqara-alab.github.io/blog/assets/images/alab-avatar-gray.png)

内部相对链接地址：
```md
![alab-logo-gray]({{ site.url }}{{ site.baseurl }}/assets/images/alab-avatar-lucency.png)
```
![alab-logo-gray]({{ site.url }}{{ site.baseurl }}/assets/images/alab-avatar-lucency.png)

#### 图片的排列

**One Up**

```html
<figure>
	<a href="/blog/assets/images/alab-avatar.png"><img src="/blog/assets/images/alab-avatar-gray.png"></a>
	<figcaption><a href="/blog/assets/images/alab-avatar.png" title="ALab logo">请点击：）</a>.</figcaption>
</figure>
```

图片可点击：

<figure>
	<a href="/blog/assets/images/alab-avatar.png"><img src="/blog/assets/images/alab-avatar-gray.png"></a>
	<figcaption><a href="/blog/assets/images/alab-avatar.png" title="ALab logo">请点击：）</a>.</figcaption>
</figure>

**Two Up**

Apply the `half` class like so to display two images side by side that share the same caption.

```html
<figure class="half">
    <a href="/blog/assets/images/louis/sample-img-1-l.jpg"><img src="/blog/assets/images/louis/sample-img-1-s.jpg"></a>
    <a href="/blog/assets/images/sample-img-2-l.jpg"><img src="/blog/assets/images/sample-img-2-s.jpg"></a>
    <figcaption>Caption describing these two images.</figcaption>
</figure>
```
And you'll get something that looks like this:

<figure class="half">
	<a href="/blog/assets/images/louis/sample-img-1-l.jpg"><img src="/blog/assets/images/louis/sample-img-1-s.jpg"></a>
	<a href="/blog/assets/images/louis/sample-img-2-l.jpg"><img src="/blog/assets/images/louis/sample-img-2-s.jpg"></a>
	<figcaption>Two images.</figcaption>
</figure>

**Three Up**

Apply the `third` class like so to display three images side by side that share the same caption.

```html
<figure class="third">
	<img src="/blog/assets/images/alab-avatar-gray.png">
	<img src="/blog/assets/images/alab-avatar-lucency.png">
	<img src="/blog/assets/images/alab-avatar-gray.png">
	<figcaption>Caption describing these three images.</figcaption>
</figure>
```
And you'll get something that looks like this:

<figure class="third">
	<img src="/blog/assets/images/alab-avatar-gray.png">
	<img src="/blog/assets/images/alab-avatar-lucency.png">
	<img src="/blog/assets/images/alab-avatar-gray.png">
	<figcaption>Three images.</figcaption>
</figure>

**居中**
```md
![image-center]({{ site.url }}{{ site.baseurl }}/assets/images/louis/sample-img-580x300.jpg){: .align-center}
```
![image-center]({{ site.url }}{{ site.baseurl }}/assets/images/louis/sample-img-580x300.jpg){: .align-center}

**居右**
```md
![image-right]({{ site.url }}{{ site.baseurl }}/assets/images/louis/sample-img-300x200.jpg){: .align-right}
```
![image-right]({{ site.url }}{{ site.baseurl }}/assets/images/louis/sample-img-300x200.jpg){: .align-right}

And now we're going to shift things to the **right align**. Again, there should be plenty of room above, below, and to the left of the image. Just look at him there --- Hey guy! Way to rock that right side. I don't care what the left aligned image says, you look great. Don't let anyone else tell you differently.

```html
<figure class="align-center">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/louis/sample-img-580x300.jpg" alt="">
  <figcaption>Look at 580 x 300 getting some love.</figcaption>
</figure> 
```
<figure class="align-center">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/louis/sample-img-580x300.jpg" alt="">
  <figcaption>Look at 580 x 300 getting some love.</figcaption>
</figure> 

The figure above happens to be **centered**. The caption also has a link in it, just to see if it does anything funky.

```html
<figure style="width: 150px" class="align-left">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/louis/sample-img-300x200.jpg" alt="">
  <figcaption>Itty-bitty caption.</figcaption>
</figure> 
```
<figure style="width: 150px" class="align-left">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/louis/sample-img-300x200.jpg" alt="">
  <figcaption>Itty-bitty caption.</figcaption>
</figure> 

The rest of this paragraph is filler for the sake of seeing the text wrap around the 150×150 image, which is **left aligned**.


## 2. 列表

- markdown格式的便捷性
- markdown格式的通用性
- markdown格式的不足

**Ordered -- Unordered -- Ordered**

```md
1. ordered item
2. ordered item 
  * **unordered**
  * **unordered** 
    1. ordered item
    2. ordered item
3. ordered item
4. ordered item
```

1. ordered item
2. ordered item 
  * **unordered**
  * **unordered** 
    1. ordered item
    2. ordered item
3. ordered item
4. ordered item

### 3. Latex公式

```md
$$E=mc^2$$
```

$$E=mc^2$$
或者，来一个更复杂的：

```md
$$
\begin{align*}
  & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
  = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
  & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
      \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
      \vdots & \ddots & \vdots \\
      \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
    \end{array} \right)
  \left( \begin{array}{c}
      y_1 \\
      \vdots \\
      y_n
    \end{array} \right)
\end{align*}
$$
```

$$
\begin{align*}
  & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
  = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
  & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
      \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
      \vdots & \ddots & \vdots \\
      \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
    \end{array} \right)
  \left( \begin{array}{c}
      y_1 \\
      \vdots \\
      y_n
    \end{array} \right)
\end{align*}
$$

### 4. 代码编辑

```python
@requires_authorization
class SomeClass:
    pass

if __name__ == '__main__':
    # A comment
    print 'hello world'
```

```html
{% raw %}<nav class="pagination" role="navigation">
  {% if page.previous %}
    <a href="{{ site.url }}{{ page.previous.url }}" class="btn" title="{{ page.previous.title }}">Previous article</a>
  {% endif %}
  {% if page.next %}
    <a href="{{ site.url }}{{ page.next.url }}" class="btn" title="{{ page.next.title }}">Next article</a>
  {% endif %}
</nav><!-- /.pagination -->{% endraw %}
```

{% highlight html linenos %}
{% raw %}<nav class="pagination" role="navigation">
  {% if page.previous %}
    <a href="{{ site.url }}{{ page.previous.url }}" class="btn" title="{{ page.previous.title }}">Previous article</a>
  {% endif %}
  {% if page.next %}
    <a href="{{ site.url }}{{ page.next.url }}" class="btn" title="{{ page.next.title }}">Next article</a>
  {% endif %}
</nav><!-- /.pagination -->{% endraw %}
{% endhighlight %}

**Code Blocks in Lists**

1. Do step 1.
2. Now do this:
   
   ```ruby
   def print_hi(name)
     puts "Hi, #{name}"
   end
   print_hi('Tom')
   #=> prints 'Hi, Tom' to STDOUT.
   ```
        
3. Now you can do this.

### 5. 绘制表格

```md
| 项目        | 价格   |  数量  |
| --------   | -----:  | :----:  |
| 计算机     | \$1600 |   5     |
| 手机        |   \$12   |   12   |
| 管线        |    \$1    |  234  |
```

| 项目        | 价格   |  数量  |
| --------   | -----:  | :----:  |
| 计算机     | \$1600 |   5     |
| 手机        |   \$12   |   12   |
| 管线        |    \$1    |  234  |


总而言之，不同于其它 *所见即所得* 的编辑器：你只需使用键盘专注于书写文本内容，就可以生成印刷级的排版格式，省却在键盘和工具栏之间来回切换，调整内容和格式的麻烦。**Markdown 在流畅的书写和印刷级的阅读体验之间找到了平衡。** 目前它已经成为世界上最大的技术分享网站 GitHub 和 技术问答网站 StackOverFlow 的御用书写格式。

## 更多

关于此博客模板，还有很多功能可以使用，大家如果有兴趣，可以参考[minimal-mistakes quick start guide](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)


## 参考文献：

[minimal-mistakes quick start guide](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)

[支持 **LaTeX** 编辑显示支持](http://meta.math.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference)



