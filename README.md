jade-info
=========

show some info about jade


#### 工具

* 推荐：[online official](http://jade-lang.com/)
* [online html2jade](http://html2jade.aaron-powell.com/)



#### 标签

```shell
html
```

会转换为：

```shell
<html></html>
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
