# HTML5学习笔记



## HTML文档的后缀名

- .html
- .htm

## 实例解析

- **<!DOCTYPE html>** 声明为 HTML5 文档
- **<html>** 元素是 HTML 页面的根元素
- **<head>** 元素包含了文档的元（meta）数据，如 **<meta charset="utf-8">** 定义网页编码格式为 **utf-8**。
- **<title>** 元素描述了文档的标题
- **<body>** 元素包含了可见的页面内容
- **<h1>** 元素定义一个大标题
- **<p>** 元素定义一个段落

**注：**在浏览器的页面上使用键盘上的 F12 按键开启调试模式，就可以看到组成标签。

## 什么是HTML?

HTML 是用来描述网页的一种语言。

- HTML 指的是超文本标记语言: **H**yper**T**ext **M**arkup **L**anguage
- HTML 不是一种编程语言，而是一种**标记**语言
- 标记语言是一套**标记标签** (markup tag)
- HTML 使用标记标签来**描述**网页
- HTML 文档包含了HTML **标签**及**文本**内容
- HTML文档也叫做 **web 页面**

## HTML 标签

HTML 标记标签通常被称为 HTML 标签 (HTML tag)。

- HTML 标签是由*尖括号*包围的关键词，比如 <html>
- HTML 标签通常是*成对出现*的，比如 <b> 和 </b>
- 标签对中的第一个标签是*开始标签*，第二个标签是*结束标签*
- 开始和结束标签也被称为*开放标签*和*闭合标签*

## HTML 元素

"HTML 标签" 和 "HTML 元素" 通常都是描述同样的意思.

但是严格来讲, 一个 HTML 元素包含了开始标签与结束标签

## Web 浏览器

Web浏览器（如谷歌浏览器，Internet Explorer，Firefox，Safari）是用于读取HTML文件，并将其作为网页显示。

浏览器并不是直接显示的HTML标签，但可以使用标签来决定如何展现HTML页面的内容给用户



1、***.html** 文件跟 ***.jpg** 文件(f盘)在不同目录下：

```
<img src="file:///f:/*.jpg" width="300" height="120"/>
```

2、***.html** 文件跟 ***.jpg** 图片在相同目录下：

```
<img src="*.jpg" width="300" height="120"/>
```

3、***.html** 文件跟 ***.jpg** 图片在不同目录下：

a、图片 ***.jpg** 在 **image** 文件夹中，*.html 跟 **image** 在同一目录下：

```
<img src="image/*.jpg/"width="300" height="120"/>
```

b、图片 ***.jpg** 在 **image** 文件夹中，***.html** 在 **connage** 文件夹中，**image** 跟 **connage** 在同一目录下：

```
<img src="../image/*.jpg/"width="300" height="120"/>
```

4、如果图片来源于网络，那么写绝对路径：

```
<img src="http://static.runoob.com/images/runoob-logo.png" width="300" height="120"/>
```



**HTML 中 href、src 区别**

href 是 Hypertext Reference 的缩写，表示超文本引用。用来建立当前元素和文档之间的链接。常用的有：link、a。例如：

```
<link href="reset.css" rel=”stylesheet“/>
```

浏览器会识别该文档为 css 文档，并行下载该文档，并且不会停止对当前文档的处理。这也是建议使用 link，而不采用 @import 加载 css 的原因。 src 是 source 的缩写，src 的内容是页面必不可少的一部分，是引入。src 指向的内容会嵌入到文档中当前标签所在的位置。常用的有：img、script、iframe。例如:

```
<script src="script.js"></script>
```

当浏览器解析到该元素时，会暂停浏览器的渲染，直到该资源加载完毕。这也是将js脚本放在底部而不是头部得原因。

简而言之，src 用于替换当前元素；href 用于在当前文档和引用资源之间建立联系。



**MacOS 如何加载图片以及文件目录有空格**

MacOS 是没有硬盘分区的，所以引用文件直接：

```
<img src="file:///Users/usrn/location" width="x" height="y"/>
```

假设文件目录有空格，直接将空格换成：

```
%20
```

如下:

```
<img src="file:///Users/usrn/Desktop/location/space%20space/Images/IMG.png" width="x" height="y"/>
```

## HTML 元素语法

- HTML 元素以**开始标签**起始
- HTML 元素以**结束标签**终止
- **元素的内容**是开始标签与结束标签之间的内容
- 某些 HTML 元素具有**空内容（empty content）**
- 空元素**在开始标签中进行关闭**（以开始标签的结束而结束）
- 大多数 HTML 元素可拥有**属性**

# HTML 属性

------

属性是 HTML 元素提供的附加信息。

------

## HTML 属性

- HTML 元素可以设置**属性**
- 属性可以在元素中添加**附加信息**
- 属性一般描述于**开始标签**
- 属性总是以名称/值对的形式出现，**比如：name="value"**。

| class | 为html元素定义一个或多个类名（classname）(类名从样式文件引入) |
| ----- | ------------------------------------------------------------ |
| id    | 定义元素的唯一id                                             |
| style | 规定元素的行内样式（inline style）                           |
| title | 描述了元素的额外信息 (作为工具条使用)                        |

1. 属性和属性值，尽量小写，本来这样做也方便些。
2. class 属性可以多用 **class=" "** （引号里面可以填入多个class属性）
3. id 属性只能单独设置 **id=" "**（只能填写一个，多个无效）

# HTML 链接

nofollow 是 HTML 页面中 a 标签的属性值。这个标签的意义是告诉搜索引擎"不要追踪此网页上的链接或不要追踪此特定链接"。

nofollow 是 HTML 页面中 a 标签的属性值。它的出现为网站管理员提供了一种方式，即告诉搜索引擎"不要追踪此网页上的链接"或"不要追踪此特定链接"。这个标签的意义是告诉搜索引擎这个链接不是经过作者信任的，所以这个链接不是一个信任票。

```
<a href="http://www.runoob.com/" target="_blank" rel="noopener noreferrer">访问菜鸟教程!</a> 
```

后面最好加上：

```
rel="noopener noreferrer"
```

意思是不会打开其他的网站，因为恶意病毒可能会修改你的浏览器空白页地址。



## HTML <head> 元素

<head> 元素包含了所有的头部标签元素。在 <head>元素中你可以插入脚本（scripts）, 样式文件（CSS），及各种meta信息。

可以添加在头部区域的元素标签为: <title>, <style>, <meta>, <link>, <script>, <noscript> 和 <base>。



## HTML <title> 元素

<title> 标签定义了不同文档的标题。

<title> 在 HTML/XHTML 文档中是必须的。

<title> 元素:

- 定义了浏览器工具栏的标题
- 当网页添加到收藏夹时，显示在收藏夹中的标题
- 显示在搜索引擎结果页面的标题



## HTML <base> 元素

<base> 标签描述了基本的链接地址/链接目标，该标签作为HTML文档中所有的链接标签的默认链接:

```
<head>
<base href="http://www.runoob.com/images/" target="_blank">
</head>
```

------

## HTML <link> 元素

<link> 标签定义了文档与外部资源之间的关系。

<link> 标签通常用于链接到样式表:

```
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
```



------

## HTML <style> 元素

<style> 标签定义了HTML文档的样式文件引用地址.

在<style> 元素中你也可以直接添加样式来渲染 HTML 文档:

```
<head>
<style type="text/css">
body {background-color:yellow}
p {color:blue}
</style>
</head>
```



## HTML <meta> 元素

meta标签描述了一些基本的元数据。

<meta> 标签提供了元数据.元数据也不显示在页面上，但会被浏览器解析。

META 元素通常用于指定网页的描述，关键词，文件的最后修改时间，作者，和其他元数据。

元数据可以使用于浏览器（如何显示内容或重新加载页面），搜索引擎（关键词），或其他Web服务。

<meta> 一般放置于 <head> 区域



## <meta> 标签- 使用实例

为搜索引擎定义关键词:

```
<meta name="keywords" content="HTML, CSS, XML, XHTML, JavaScript">
```

为网页定义描述内容:

```
<meta name="description" content="免费 Web & 编程 教程">
```

定义网页作者:

```
<meta name="author" content="Runoob">
```

每30秒钟刷新当前页面:

```
<meta http-equiv="refresh" content="30">
```



HTML<title>元素不仅可以显示文本，也可以在左侧显示logo等图片。

显示时，要将<link>标签放入<head>里。

举例：

```
<!doctype HTML>
<html>
<head>
<link rel="shortcut icon" href="图片url">
<title>这是一个带图片的标签</title>
</head>
<body>
……
……
……
</body>
</html>
```



**head 标签和 header 标签的不同**

head 标签用于定义文档头部，它是所有头部元素的容器。<head> 中的元素可以引用脚本、指示浏览器在哪里找到样式表、提供元信息等等。

如：

```
<html>
  <head>
     <title>文档标题</title>
  </head>
</html>
```

header 标签用于定义文档的页眉（介绍信息）。

如：

```
<html>
  <body>
    <header>
        <p>段落</p>
        <h1>一级标题</h1>
    </header>
  </body>
</html>
```

注意千万不要弄混。



表格三要素 **table、tr、td** 缺一不可。

<table> 标签常用属性：

```
border="1"   表格边框的宽度
bordercolor="#fff"   表格边框的颜色
cellspacing="5"   单元格之间的间距
width="500"   表格的总宽度
height="100"   表格的总高度
align="right"   表格整体对齐方式    (参数有  left、center、right)
bgcolor="#fff"   表格整体的背景色
```

<tr> 标签的常用属性:

```
bgcolor="#fff"    行的颜色
align="right"    行内文字的水平对齐方式    (参数有left、center、right)
valign="top"     行内文字的垂直对齐方式    (参数有top、middle、bottom)
```

<td>、<th> 标签的常用属性:

```
width="500"    单元格的宽度，设置后对当前一列的单元格都有影响
height="100"   单元格的高度，设置后对当前一行的单元格都有影响
bgcolor="fff"  单元格的背景色
align="right"  单元格文字的水平对齐方式    (参数left、center、right)
rowspan="3"    合并垂直水平方向的单元格
colspan="3"    合并水平方向单元格
valign="top"   单元格文字的垂直对齐方式    (参数middle、bottom、top) 
```

引号里的数字和颜色代码均可以更改。

表格结构语义标签：

-  1.<table>：表格根元素。
-  2.<thead>：表格头。
-  3.<tbody>：表格体。
-  4.<tfoot>：表格尾，一般可忽略该结构。
-  5.<tr>：表格行。

表格内容标签：

-  1.<th>：表头单元格。
-  2.<td>：表体单元格。

跨列：colspan

跨行：rowspan

单元格内边距：cellpadding

单元格外边距：cellspacing

col 和 colgroup 用于便捷定义表格指定列的样式。

## 注意事项 - 有用提示

**提示:** 列表项内部可以使用段落、换行符、图片、链接以及其他列表等等。

## HTML <script> 标签

<script> 标签用于定义客户端脚本，比如 JavaScript。

<script> 元素既可包含脚本语句，也可通过 src 属性指向外部脚本文件。

JavaScript 最常用于图片操作、表单验证以及内容动态更新。

# [HTML 速查列表](https://www.runoob.com/html/html-quicklist.html)

