# 1. HTML 表格基础

### 1.1 什么是表格？

表格是由行和列组成的结构化数据集(表格数据)，它能够使你简捷迅速地查找某个表示不同类型数据之间的某种关系的值 

#### 表格是如何工作的？

表格的一个特点就是严格. 通过在行和列的标题之间进行视觉关联的方法，就可以让信息能够很简单地被解读出来。



#### 表格风格

使用 CSS 来优化表格样式。



#### 不应该使用表格来进行页面布局

早期因为 CSS 技术不成熟，浏览器支持性不好，很多地方都是用表格进行页面布局，以提升兼容性。现在并不提倡这种做法。



1. 表格布局减少了视觉受损用户的可访问性。
2. 表格会产生很多标签。使代码变得更难以维护。
3. 表格不能自动响应。





### 1.2 使用 th 元素添加标题

#### 为什么使用标题是有用的？

当标题明显突出的时候，你可以更加简单地找到你想找的数据，设计上也会看起来更好。而且表格也会有默认的样式来突出表头。



### 1.3 允许单元格跨越多行和列



* 使用 colspan 合并列，使一个单元格拥有多个单元格的宽度。
* 使用 rowspan 合并行，使一个单元格拥有多个单元格的高度。



### 1.4 为表格中的列提供共同的样式



HTML 中允许使用 col 和 colgroup 元素来定义整列数据的样式信息。

```html
<table>
  <colgroup>
    <col>
    <col style="background-color: yellow">
  </colgroup>
  <tr>
    <th>Data 1</th>
    <th>Data 2</th>
  </tr>
  <tr>
    <td>Calcutta</td>
    <td>Orange</td>
  </tr>
  <tr>
    <td>Robots</td>
    <td>Jazz</td>
  </tr>
</table>
```

使用 span 属性可以将样式信息应用的所有列（span 的值表示想要让这个样式应用到表格中多少列）：

```html
<colgroup>
  <col style="background-color: yellow" span="2">
</colgroup>
```



> colgroup 定义的样式会同时影响 thead，tbody ，tfoot 中的列。



# 2. HTML 表格高级功能与可访问性

在这个模块中将会讨论表格的高级功能，比如**表格的标题/摘要，以及表格中各行分组成头部、正文、页脚部分，提高视力受阻用户的可访问性**。



### 2.1 使用 caption 为表格增加一个标题



```html
<table>
  <caption>Dinosaurs in the Jurassic period</caption>

  ...
</table>
```



### 2.2 使用 thead tfoot tobdy 结构化表格



* thead 标识表头结构。table 的头部位置，或者 colgroup元素下，通常代表第一行。
* tfoot 放在 table 的底部，或者 thead 的下面（但是浏览器依然会把它呈现在表格的底部），是表格的最后一行。 通常用于表示对前面所有行的总结。
* tbody 用于表示表格主体部分。



> tbody 总是包含在表中的，如果没有在代码中指定它，那就是隐士的。



### 2.3 嵌套表格

在一个表格中嵌套另一个表格是被允许的，但是要包括完整的结构。只是通常不建议这么做。



### 2.4 建立表头和其列之间的联系（解决表格嵌套时，对视力受阻用户的阅读障碍问题）



#### 使用列和行的标题

屏幕阅读设备会识别所有的标题，然后在它们和它们所关联的单元格之间产生编程关联。



#####  scope 属性



##### Id 和标题属性

使用 id 和 headers 属性替换 scop 属性，来创建标题和单元格之间的联系。

例如：

```html
<thead>
  <tr>
    <th id="purchase">Purchase</th>
    <th id="location">Location</th>
    <th id="date">Date</th>
    <th id="evaluation">Evaluation</th>
    <th id="cost">Cost (€)</th>
  </tr>
</thead>
<tbody>
<tr>
  <th id="haircut">Haircut</th>
  <td headers="location haircut">Hairdresser</td>
  <td headers="date haircut">12/09</td>
  <td headers="evaluation haircut">Great idea</td>
  <td headers="cost haircut">30</td>
</tr>
```

