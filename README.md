jade-info
=========

show some info about jade


#### 工具

* 推荐：[online official](http://jade-lang.com/)
* [online html2jade](http://html2jade.aaron-powell.com/)



#### 标签

```shell
p
```

会转换为：

```shell
<p></p>
```

* jade能自动识别自闭和标签

```shell
input
```

会转换为：

```shell
<input/>
```


#### 文本

> 如何在标签里面加上文本

```shell
p 我是yc-team
```

会转换为：

```shell
<p>我是yc-team</p>
```

* 标签里面如果有标签？

其实是一样的，直接写就行

```shell
p Welcome to wandoujia fe, we want <b>you</b>
```

会转换为：

```shell
<p>Welcome to wandoujia fe, we want <b>you</b></p>
```

* 标签里面如果有大段的块内容？

比如很多script里面，注意是script后面有一个.

```shell
script.
  console.log('Welcome to join wandoujia-fe')
```

会转换为：

```shell
<script>console.log('Welcome to join wandoujia-fe')</script>
```


#### 属性

> 支持 ( ) 来分割属性

```shell
a(rel="nofollow", href="http://www.wandoujia.com/join#getJobInfo=1") 招聘
```

会转换为：

```shell
<a rel="nofollow" href="http://www.wandoujia.com/join#getJobInfo=1">招聘</a>
```


#### 注释

* 单行注释

```shell 
// changed by yc-team 
```

会转换为：

```shell 
<!-- changed by yc-team -->
```

* 多行注释

```shell 
body
  //
    p 测试代码by yaochun
```

会转换为：

```shell
<body>
  <!--p 测试代码by yaochun 
  -->
</body>
```

* 不输出的注释

> 加一个短横线 - 

```shell
//- 这段注释不会输出
p 文本测试by yaochun
```

会转换为：

```shell
<p>文本测试by yaochun</p>
```

> 注意： 很多文档里面提到的条件注释已经不再支持



#### doctype

添加一个doctype只需要doctype，然后再跟一个可选的值，默认是html

```shell
doctype html
```

会转换为：

```shell
<!DOCTYPE html>
```

注释：

> !!! 这种简写的方式已经被抛弃了~

可选值还有如下：

- xml
- transitional
- srict
- frameset
- 1.1
- basic
- mobile




#### 设置id

> 默认标签是div

```shell
#content
p#info
```

#### 设置class

> 语法就是.classname

```shell
a.btn
```

会转换为：

```shell
<a class="btn"></a>
```

#### 1个id和多个class

> 其实连着写就可以了

```shell
a#download-btn.btn.blue-btn
```

会转换为：

```shell
<a id="download-btn" class="btn blue-btn"></a>
```



#### 代码

* 不会被缓冲代码

```shell
- for (var i = 0; i < 3; i++)
  li yc-team
```

会转换为：

```shell
<li>yc-team</li>
<li>yc-team</li>
<li>yc-team</li>
```

* 被缓冲代码

```shell
p= 'Welcome to wandoujia fe, we want you'
```

会转换为：

```shell
<p>Welcome to wandoujia fe, we want you</p>
```

> 这里注意一下 = 默认会转义内容

```shell
p= 'Welcome to wandoujia fe, we want <b>you</b>'
```

会转换为：

```shell
<p>Welcome to wandoujia fe, we want &lt;b&gt;you&lt;/b&gt;</p>
```

那如何处理那些不想被转义的呢？

```shell
p!= 'Welcome to wandoujia fe, we want <b>you</b>'
```

会转换为：

```shell
<p>Welcome to wandoujia fe, we want <b>you</b></p>
```

#### 循环

> jade支持each用作循环

语法结构：

```shell
each VAL[,KEY] in OBJ
```

- VAL是值
- KEY是键，可选
- OBJ是对象，array or object

* 先看一个数组的例子

```shell
- var jobs = ["fe", "wandoujia", "beijing", "We want you"]
each job in jobs
  li= job
```

会转换为：

```shell
<li>fe</li>
<li>wandoujia</li>
<li>beijing</li>
<li>We want you</li>
```


* 再看一个对象的例子

```shell
- var jobs = {"catagory" : "fe", "company" : "wandoujia", "local" : "beijing"}
each val,key in jobs
  li #{key} : #{val}
```

会转换为：

```shell
<li>catagory : fe</li>
<li>company : wandoujia</li>
<li>local : beijing</li>
```


#### Case

> case主要的作用和js里面的switch一样

* 方式一

```shell
- var apples = 1
case apples
  when 0
    p you have no apples
  when 1
    p you have an apple
  default
    p you have #{apples} apples
```

会转换为：

```shell
<p>you have an apple</p>
```

* 方式二

有部分人可能有写出这样，当然我还是推荐第一站方式

```shell
- var apples = 1
case apples
  when 0: p you have no apples
  when 1: p you have an apple
  default: p you have #{apples} apples
```

* 方式三

有些时候，确实有需求合并一些when的情况

```shell
- var apples = 1
case apples
  when 0
   when 1
    p you have few apples
  default
    p you have #{apples} apples
```

当apples这个值为0或者1的时候会转换为：

```shell
<p>you have few apples</p>
```


#### 过滤器

* 支持markdown

> 必须是已经安装 markdown-js 或者 node-discount

```shell
:markdown
  我们来自豌豆荚前端，欢迎有志之士加盟，简历发送至zhangyaochun@wandoujia.com
```

会转换为：

```shell
<p>我们来自豌豆荚前端，欢迎有志之士加盟，简历发送至zhangyaochun@wandoujia.com</p>
```


#### Mixins

* 不带任何参数的mixin

```shell
mixin join
  ul
    li 我们需要一帮人
    li 喜欢前端
    li 了解前端
    li 愿意在前端不断学习奋斗的
    li 你是吗？
    li 快来加入我们把

+join()
```

会转换为：

```shell
<ul>
  <li>我们需要一帮人</li>
  <li>喜欢前端</li>
  <li>了解前端</li>
  <li>愿意在前端不断学习奋斗的</li>
  <li>你是吗？</li>
  <li>快来加入我们把</li>
</ul>
```


* 带参数的mixin

```shell
mixin join(company)
  ul
    li 我们 #{company} 需要一帮人
    li 喜欢前端
    li 了解前端
    li 愿意在前端不断学习奋斗的
    li 你是吗？
    li 快来加入我们 #{company} 把

+join('wandoujia')
```


会转换为：

```shell
<ul>
  <li>我们 wandoujia 需要一帮人</li>
  <li>喜欢前端</li>
  <li>了解前端</li>
  <li>愿意在前端不断学习奋斗的</li>
  <li>你是吗？</li>
  <li>快来加入我们 wandoujia 把</li>
</ul>
```

* minxin里面还支持block

```shell
mixin join(company)
  ul
    li 我们需要一帮人
    li 喜欢前端
    li 了解前端
    li 愿意在前端不断学习奋斗的    
    if block
      block
    else  
      li 你是吗？
      li 快来加入我们把

+join('wandoujia')
  li 我们这有神马？
  li 我们这个有一帮能折腾的老师阿姨
  li 我们这有美丽的阿姨
  li 我们每周都有技术交流
  li 我们这可以用很多开源的新技术
```

会转换为：

```shell
<ul>
  <li>我们需要一帮人</li>
  <li>喜欢前端</li>
  <li>了解前端</li>
  <li>愿意在前端不断学习奋斗的</li>
  <li>我们这有神马？</li>
  <li>我们这个有一帮能折腾的老师阿姨</li>
  <li>我们这有美丽的阿姨</li>
  <li>我们每周都有技术交流</li>
  <li>我们这可以用很多开源的新技术</li>
</ul>
```


* minxin里面还支持attributes

```shell
mixin link(href, name)
  a(class!=attributes.class, title!=attributes.title, href=href)= name

+link('http://wandoujia.com/join', '豌豆荚前端招聘')(class="btn", title="招聘啦，小伙伴快来点")  
```

会转换为：

```shell
<a title="招聘啦，小伙伴快来点" href="http://wandoujia.com/join" class="btn">豌豆荚前端招聘</a>
```


#### 包含

> 有点类似freemaker，通过include来载入一些jade模板
