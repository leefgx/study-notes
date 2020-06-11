# CSS学习笔记



CSS 规则由两个主要的部分构成：选择器，以及一条或多条声明:

![img](https://www.runoob.com/wp-content/uploads/2013/07/632877C9-2462-41D6-BD0E-F7317E4C42AC.jpg)

选择器通常是您需要改变样式的 HTML 元素。

每条声明由一个属性和一个值组成。

属性（property）是您希望设置的样式属性（style attribute）。每个属性有一个值。属性和值被冒号分开。



**css 选择器**

如果你要在 html 标签中设置 CSS 样式，那么你有四种方法，即 css 选择器有四种。

除了提到的 id 和 class 选择器外，第三种选择器为标签选择器，即以 html 标签作为 css 修饰所用的选择器。

实例

```
<style>
h3{
    color:red;
}
</style>
<h3>菜鸟教程</h3>
```

第四种选择器即直接在标签内部写css代码。

实例

```
<h3 style="color:red;">菜鸟教程</h3>
```

这四种 css 选择器有修饰上的优先级，即：

**第四种 > id > class > 第三种**

## 多重样式优先级深入概念

优先级是浏览器是通过判断哪些属性值与元素最相关以决定并应用到该元素上的。优先级仅由选择器组成的匹配规则决定的。

优先级就是分配给指定的CSS声明的一个权重，它由匹配的选择器中的每一种选择器类型的数值决定。

### 优先级顺序

下列是一份优先级逐级增加的选择器列表：

- 通用选择器（*）
- 元素(类型)选择器
- 类选择器
- 属性选择器
- 伪类
- ID 选择器
- 内联样式

### !important 规则例外

当 !important 规则被应用在一个样式声明中时,该样式声明会覆盖CSS中任何其他的声明, 无论它处在声明列表中的哪里. 尽管如此, !important规则还是与优先级毫无关系.使用 !important 不是一个好习惯，因为它改变了你样式表本来的级联规则，从而使其难以调试。

一些经验法则：

- **Always** 要优化考虑使用样式规则的优先级来解决问题而不是 `!important`
- **Only** 只在需要覆盖全站或外部 css（例如引用的 ExtJs 或者 YUI ）的特定页面中使用 `!important`
- **Never** 永远不要在全站范围的 css 上使用` !important`
- **Never** 永远不要在你的插件中使用 `!important`

### 权重计算:

![img](https://www.runoob.com/wp-content/uploads/2017/06/jc6_002_thumb.png)

解释：

-  \1. 内联样式表的权值最高 1000；
-  \2. ID 选择器的权值为 100
-  \3. Class 类选择器的权值为 10
-  \4. HTML 标签选择器的权值为 1



利用选择器的权值进行计算比较，em 显示蓝色，示例如下：https://c.runoob.com/codedemo/3048

### CSS 优先级法则：

-  A 选择器都有一个权值，权值越大越优先；
-  B 当权值相等时，后出现的样式表设置要优于先出现的样式表设置；
-  C 创作者的规则高于浏览者：即网页编写者设置的CSS 样式的优先权高于浏览器所设置的样式；
-  D 继承的CSS 样式不如后来指定的CSS 样式；
-  E 在同一组属性设置中标有“!important”规则的优先级最大；示例如下：https://c.runoob.com/codedemo/3049 
  结果：在Firefox 下显示为蓝色；在IE 6 下显示为红色；

### 这里引入一张流行的CSS权重关系图：

![img](https://www.runoob.com/wp-content/uploads/2017/06/css_weight.png)

### 更多参考资料

- **CSS 样式优先级**：[//www.runoob.com/w3cnote/css-style-priority.html](http://www.runoob.com/w3cnote/css-style-priority.html)

## 错误的说法

在学习过程中，你可能发现给选择器加权值的说法，即 ID 选择器权值为 100，类选择器权值为 10，标签选择器权值为 1，当一个选择器由多个 ID 选择器、类选择器或标签选择器组成时，则将所有权值相加，然后再比较权值。这种说法其实是有问题的。比如一个由 11 个类选择器组成的选择器和一个由 1 个 ID 选择器组成的选择器指向同一个标签，按理说 110 > 100，应该应用前者的样式，然而事实是应用后者的样式。错误的原因是：**权重的进制是并不是十进制，CSS 权重进制在 IE6 为 256，后来扩大到了 65536，现代浏览器则采用更大的数量。**。还是拿刚刚的例子说明。11 个类选择器组成的选择器的总权值为 110，但因为 11 个均为类选择器，所以其实总权值最多不能超过 100， 你可以理解为 99.99，所以最终应用后者样式。



### CSS 背景

CSS 背景属性用于定义HTML元素的背景。

CSS 属性定义背景效果:

- background-color
- background-image
- background-repeat
- background-attachment
- background-position



