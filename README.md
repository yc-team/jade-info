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
