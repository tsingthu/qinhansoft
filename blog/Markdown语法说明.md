# 概述

## 宗旨

Markdown的目标是实现“易读易写”。

可读性，无论如何，都是最重要的。一份事业Markdown格式撰写的文件应该可以直接以纯文本发布，并且看起来不会像是由许多标签或是格式指令所构成。Markdown语法受到一些既有text-to-HTML格式的影响，包括Setext、atx、Textile、reStructuredText、Grutatext和EtText，而最大灵感来源其实是纯文本电子邮件的格式。

总之，Markdown的语法全由一些符号所组成，这些符号经过精挑细选，其作用一目了然。比如：在文字两旁加上星号，看起来就像*强调*。Markdown的列表看起来，嗯，就是列表。Markdown的区块引用看起来就真的像是引用一段文字，就像你曾在电子邮件中见过的那样。

## 兼容HTML

Markdown语法的目标是：成为一种适用于网络的书写语音。

Markdown不是想要取代HTML，甚至也没有要和它接近，它的语法种类很少，只对应HTML标记的一小部分。Markdown的构想不是要使得HTML文档更容易写。在我看来，HTML已经很容易写了。Markdown的理念是，能让文档更容易读、写和随意改。HTML是一种发布的格式，Markdown是一种书写的格式。就这样，Markdown的格式语法只涵盖纯文本可以涵盖的范围。

不在Markdown涵盖范围内的标签，都可以直接在文档里面用HTML撰写。不需要额外标注这是HTML或是Markdown；只要直接加标签就可以了。

要制约的纸伞一些HTML区块元素——比如`<div>`、`<table>`、`<p>`等标签，必须在前后加上空行与其它内容区隔开，还要求它们的开始标签与结尾标签不能使用制表符或空格来缩进。Markdown的生成器有足够智能，不会在HTML区块标签外加上不必要的`<p>`标签。

例子如下，在Markdown文件里加上一段HTML表格：

```
这是一个普通段落。
<table>
    <tr>
    <td>Foo</td>
    </tr>
</table>
这是另一个普通段落。
```

请注意，在HTML区块标签间的Markdown格式语法将不会被处理。比如，你在HTML区块内使用Markdown样式的`*强调*`会没有效果。

HTML的区段（行内）标签如`<span>`、`<cite>`、`<del>`可以在Markdown的段落、列表或是标题里随意使用。依照个人习惯，甚至可以不用Markdown格式，而直接采用HTML标签来初始化。举例说明：如果比较喜欢HTML的`<a>`或`<img>`标签，可以直接使用这些标签，而不用Markdown提供的链接或是图像标签语法。

和处在HTML区块标签间不同，Markdown语法在HTML区段标签间是有效的。