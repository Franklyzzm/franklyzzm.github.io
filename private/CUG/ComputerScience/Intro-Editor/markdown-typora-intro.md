# Markdown & Typora 入門 Intro

**Markdown** 是由 [John Gruber](http://daringfireball.net/) 创建的； 這是[原始指南](http://daringfireball.net/projects/markdown/syntax)。 但是，其语法在不同的解析器或编辑器之间有所不同。 **Typora** 使用 [GitHub Flavored Markdown][GFM]。

**Markdown** is created by [John Gruber](http://daringfireball.net/); the original guideline is [here](http://daringfireball.net/projects/markdown/syntax). Its syntax, however, varies between different parsers or editors. **Typora** is using [GitHub Flavored Markdown][GFM].

[TOC]

## 区块元素 Block Elements

### 段落和换行 Paragraph and line breaks

一个 Markdown 段落是由一个或多个连续的文本行组成，它的前后要有一个以上的空行（空行的定义是显示上看起来像是空的，便会被视为空行。比方说，若某一行只包含空格和制表符，则该行也会被视为空行）。普通段落不该用空格或制表符来缩进。

「由一个或多个连续的文本行组成」这句话其实暗示了 Markdown 允许段落内的强迫换行（插入换行符），这个特性和其他大部分的 text-to-HTML 格式不一样（包括 Movable Type 的「Convert Line Breaks」选项），其它的格式会把每个换行符都转成 ` ` 标签。

如果你*确实*想要依赖 Markdown 来插入 ` ` 标签的话，在插入处先按入两个以上的空格然后回车。

的确，需要多费点事（多加空格）来产生 ` ` ，但是简单地「每个换行都转换为 ` `」的方法在 Markdown 中并不适合， Markdown 中 email 式的 区块引用 和多段落的 列表 在使用换行来排版的时候，不但更好用，还更方便阅读。

### 标题 Headers

Markdown 支持两种标题的语法，类 [Setext]和类 [atx]形式。

类 Setext 形式是用底线的形式，利用 `=` （最高阶标题）和 `-` （第二阶标题），例如：

```
這是一級標題
=============

這是二級標題
-------------
```

任何数量的 `=` 和 `-` 都可以有效果。

类 Atx 形式则是在行首插入 1 到 6 个 `#` hash，对应到标题 1 到 6 阶，例如：

```
# 这是一級標題

## 这是二級標題

###### 这是六級標題
```

你可以选择性地「闭合」类 atx 样式的标题，这纯粹只是美观用的，若是觉得这样看起来比较舒适，你就可以在行尾加上 `#`，而行尾的 `#` 数量也不用和开头一样（行首的井字符数量决定标题的阶数）：

```
# 这是一級標題 #

## 这是二級標題 ##

### 这是三級標題 ######
```

### 区块引用 Blockquotes

Markdown 标记区块引用是使用类似 email 中用 `>` 的引用方式。如果你还熟悉在 email 信件中的引言部分，你就知道怎么在 Markdown 文件中建立一个区块引用，那会看起来像是你自己先断好行，然后在每行的最前面加上 `>` ：

```
> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
> consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
> Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.
> 
> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
> id sem consectetuer libero luctus adipiscing.
```



Markdown 也允许你偷懒只在整个段落的第一行最前面加上 `>` ：

```
> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
id sem consectetuer libero luctus adipiscing.
```

区块引用可以嵌套（例如：引用内的引用），只要根据层次加上不同数量的 `>` ：

```
> This is the first level of quoting.
>
> > This is nested blockquote.
>
> Back to the first level.
```



引用的区块内也可以使用其他的 Markdown 语法，包括标题、列表、代码区块等：

```
> ## 这是一个标题。
> 
> 1.   这是第一行列表项。
> 2.   这是第二行列表项。
> 
> 给出一些例子代码：
> 
>     return shell_exec("echo $input | $markdown_script");
```



任何像样的文本编辑器都能轻松地建立 email 型的引用。例如在 BBEdit 中，你可以选取文字后然后从选单中选择*增加引用阶层*。

### 列表 Lists

Markdown 支持有序列表和无序列表。

无序列表使用星号、加号或是减号作为列表标记：

```
*   Red
*   Green
*   Blue
```

等同于：

```
+   Red
+   Green
+   Blue
```

也等同于：

```
-   Red
-   Green
-   Blue
```

有序列表则使用数字接着一个英文句点：

```
1.  Bird
2.  McHale
3.  Parish
```

很重要的一点是，你在列表标记上使用的数字并不会影响输出的 HTML 结果，上面的列表所产生的 HTML 标记为：

```
<ol>
<li>Bird</li>
<li>McHale</li>
<li>Parish</li>
</ol>
```

如果你的列表标记写成：

```
1.  Bird
1.  McHale
1.  Parish
```

或甚至是：

```
3. Bird
1. McHale
8. Parish
```

你都会得到完全相同的 HTML 输出。重点在于，你可以让 Markdown 文件的列表数字和输出的结果相同，或是你懒一点，你可以完全不用在意数字的正确性。

如果你使用懒惰的写法，建议第一个项目最好还是从 1. 开始，因为 Markdown 未来可能会支持有序列表的 start 属性。

列表项目标记通常是放在最左边，但是其实也可以缩进，最多 3 个空格，项目标记后面则一定要接着至少一个空格或制表符。

要让列表看起来更漂亮，你可以把内容用固定的缩进整理好：

```
*   Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
    Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
    viverra nec, fringilla in, laoreet vitae, risus.
*   Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
    Suspendisse id sem consectetuer libero luctus adipiscing.
```

但是如果你懒，那也行：

```
*   Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
viverra nec, fringilla in, laoreet vitae, risus.
*   Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
Suspendisse id sem consectetuer libero luctus adipiscing.
```

如果列表项目间用空行分开，在输出 HTML 时 Markdown 就会将项目内容用 `` 标签包起来，举例来说：

```
*   Bird
*   Magic
```

会被转换为：

```
<ul>
<li>Bird</li>
<li>Magic</li>
</ul>
```

但是这个：

```
*   Bird

*   Magic
```

会被转换为：

```
<ul>
<li><p>Bird</p></li>
<li><p>Magic</p></li>
</ul>
```

列表项目可以包含多个段落，每个项目下的段落都必须缩进 4 个空格或是 1 个制表符：

```
1.  This is a list item with two paragraphs. Lorem ipsum dolor
    sit amet, consectetuer adipiscing elit. Aliquam hendrerit
    mi posuere lectus.

    Vestibulum enim wisi, viverra nec, fringilla in, laoreet
    vitae, risus. Donec sit amet nisl. Aliquam semper ipsum
    sit amet velit.

2.  Suspendisse id sem consectetuer libero luctus adipiscing.
```

如果你每行都有缩进，看起来会看好很多，当然，再次地，如果你很懒惰，Markdown 也允许：

```
*   This is a list item with two paragraphs.

    This is the second paragraph in the list item. You're
only required to indent the first line. Lorem ipsum dolor
sit amet, consectetuer adipiscing elit.

*   Another item in the same list.
```

如果要在列表项目内放进引用，那 `>` 就需要缩进：

```
*   A list item with a blockquote:

    > This is a blockquote
    > inside a list item.
```

如果要放代码区块的话，该区块就需要缩进*两次*，也就是 8 个空格或是 2 个制表符：

```
*   一列表项包含一个列表区块：

        <代码写在这>
```

当然，项目列表很可能会不小心产生，像是下面这样的写法：

```
1986. What a great season.
```

换句话说，也就是在行首出现*数字-句点-空白*，要避免这样的状况，你可以在句点前面加上反斜杠。

```
1986\. What a great season.
```

### 代码区块

和程序相关的写作或是标签语言原始码通常会有已经排版好的代码区块，通常这些区块我们并不希望它以一般段落文件的方式去排版，而是照原来的样子显示，Markdown 会用 `` 和 `` 标签来把代码区块包起来。

要在 Markdown 中建立代码区块很简单，只要简单地缩进 4 个空格或是 1 个制表符就可以，例如，下面的输入：

```
这是一个普通段落：

    这是一个代码区块。
```

Markdown 会转换成：

```
<p>这是一个普通段落：</p>

<pre><code>这是一个代码区块。
</code></pre>
```

这个每行一阶的缩进（4 个空格或是 1 个制表符），都会被移除，例如：

```
Here is an example of AppleScript:

    tell application "Foo"
        beep
    end tell
```

会被转换为：

```
<p>Here is an example of AppleScript:</p>

<pre><code>tell application "Foo"
    beep
end tell
</code></pre>
```

一个代码区块会一直持续到没有缩进的那一行（或是文件结尾）。

在代码区块里面， `&` 、 `<` 和 `>` 会自动转成 HTML 实体，这样的方式让你非常容易使用 Markdown 插入范例用的 HTML 原始码，只需要复制贴上，再加上缩进就可以了，剩下的 Markdown 都会帮你处理，例如：

```
    <div class="footer">
        &copy; 2004 Foo Corporation
    </div>
```

会被转换为：

```
<pre><code>&lt;div class="footer"&gt;
    &amp;copy; 2004 Foo Corporation
&lt;/div&gt;
</code></pre>
```

代码区块中，一般的 Markdown 语法不会被转换，像是星号便只是星号，这表示你可以很容易地以 Markdown 语法撰写 Markdown 语法相关的文件。

### 分隔线

你可以在一行中用三个以上的星号、减号、底线来建立一个分隔线，行内不能有其他东西。你也可以在星号或是减号中间插入空格。下面每种写法都可以建立分隔线：

```
* * *

***

*****

- - -

---------------------------------------
```

------

## 区段元素

### 链接

Markdown 支持两种形式的链接语法： *行内式*和*参考式*两种形式。

不管是哪一种，链接文字都是用 [方括号] 来标记。

要建立一个*行内式*的链接，只要在方块括号后面紧接着圆括号并插入网址链接即可，如果你还想要加上链接的 title 文字，只要在网址后面，用双引号把 title 文字包起来即可，例如：

```
This is [an example](http://example.com/ "Title") inline link.

[This link](http://example.net/) has no title attribute.
```

会产生：

```
<p>This is <a href="http://example.com/" title="Title">
an example</a> inline link.</p>

<p><a href="http://example.net/">This link</a> has no
title attribute.</p>
```

如果你是要链接到同样主机的资源，你可以使用相对路径：

```
See my [About](/about/) page for details.
```

*参考式*的链接是在链接文字的括号后面再接上另一个方括号，而在第二个方括号里面要填入用以辨识链接的标记：

```
This is [an example][id] reference-style link.
```

你也可以选择性地在两个方括号中间加上一个空格：

```
This is [an example] [id] reference-style link.
```

接着，在文件的任意处，你可以把这个标记的链接内容定义出来：

```
[id]: http://example.com/  "Optional Title Here"
```

链接内容定义的形式为：

* 方括号（前面可以选择性地加上至多三个空格来缩进），里面输入链接文字
* 接着一个冒号
* 接着一个以上的空格或制表符
* 接着链接的网址
* 选择性地接着 title 内容，可以用单引号、双引号或是括弧包着

下面这三种链接的定义都是相同：

```
[foo]: http://example.com/  "Optional Title Here"
[foo]: http://example.com/  'Optional Title Here'
[foo]: http://example.com/  (Optional Title Here)
```

**请注意：**有一个已知的问题是 Markdown.pl 1.0.1 会忽略单引号包起来的链接 title。

链接网址也可以用方括号包起来：

```
[id]: <http://example.com/>  "Optional Title Here"
```

你也可以把 title 属性放到下一行，也可以加一些缩进，若网址太长的话，这样会比较好看：

```
[id]: http://example.com/longish/path/to/resource/here
    "Optional Title Here"
```

网址定义只有在产生链接的时候用到，并不会直接出现在文件之中。

链接辨别标签可以有字母、数字、空白和标点符号，但是并*不*区分大小写，因此下面两个链接是一样的：

```
[link text][a]
[link text][A]
```

*隐式链接标记*功能让你可以省略指定链接标记，这种情形下，链接标记会视为等同于链接文字，要用隐式链接标记只要在链接文字后面加上一个空的方括号，如果你要让 "Google" 链接到 google.com，你可以简化成：

```
[Google][]
```

然后定义链接内容：

```
[Google]: http://google.com/
```

由于链接文字可能包含空白，所以这种简化型的标记内也许包含多个单词：

```
Visit [Daring Fireball][] for more information.
```

然后接着定义链接：

```
[Daring Fireball]: http://daringfireball.net/
```

链接的定义可以放在文件中的任何一个地方，我比较偏好直接放在链接出现段落的后面，你也可以把它放在文件最后面，就像是注解一样。

下面是一个参考式链接的范例：

```
I get 10 times more traffic from [Google] [1] than from
[Yahoo] [2] or [MSN] [3].

  [1]: http://google.com/        "Google"
  [2]: http://search.yahoo.com/  "Yahoo Search"
  [3]: http://search.msn.com/    "MSN Search"
```

如果改成用链接名称的方式写：

```
I get 10 times more traffic from [Google][] than from
[Yahoo][] or [MSN][].

  [google]: http://google.com/        "Google"
  [yahoo]:  http://search.yahoo.com/  "Yahoo Search"
  [msn]:    http://search.msn.com/    "MSN Search"
```

上面两种写法都会产生下面的 HTML。

```
<p>I get 10 times more traffic from <a href="http://google.com/"
title="Google">Google</a> than from
<a href="http://search.yahoo.com/" title="Yahoo Search">Yahoo</a>
or <a href="http://search.msn.com/" title="MSN Search">MSN</a>.</p>
```

下面是用行内式写的同样一段内容的 Markdown 文件，提供作为比较之用：

```
I get 10 times more traffic from [Google](http://google.com/ "Google")
than from [Yahoo](http://search.yahoo.com/ "Yahoo Search") or
[MSN](http://search.msn.com/ "MSN Search").
```

参考式的链接其实重点不在于它比较好写，而是它比较好读，比较一下上面的范例，使用参考式的文章本身只有 81 个字符，但是用行内形式的却会增加到 176 个字元，如果是用纯 HTML 格式来写，会有 234 个字元，在 HTML 格式中，标签比文本还要多。

使用 Markdown 的参考式链接，可以让文件更像是浏览器最后产生的结果，让你可以把一些标记相关的元数据移到段落文字之外，你就可以增加链接而不让文章的阅读感觉被打断。

### 强调

Markdown 使用星号（`*`）和底线（`_`）作为标记强调字词的符号，被 `*` 或 `_` 包围的字词会被转成用 `` 标签包围，用两个 `*` 或 `_` 包起来的话，则会被转成 ``，例如：

```
*single asterisks*

_single underscores_

**double asterisks**

__double underscores__
```

会转成：

```
<em>single asterisks</em>

<em>single underscores</em>

<strong>double asterisks</strong>

<strong>double underscores</strong>
```

你可以随便用你喜欢的样式，唯一的限制是，你用什么符号开启标签，就要用什么符号结束。

强调也可以直接插在文字中间：

```
un*frigging*believable
```

但是**如果你的 `\*` 和 `_` 两边都有空白的话，它们就只会被当成普通的符号**。

如果要在文字前后直接插入普通的星号或底线，你可以用反斜线：

```
\*this text is surrounded by literal asterisks\*
```

### 代码

如果要标记一小段行内代码，你可以用反引号把它包起来（```），例如：

```
Use the `printf()` function.
```

会产生：

```
<p>Use the <code>printf()</code> function.</p>
```

如果要在代码区段内插入反引号，你可以用多个反引号来开启和结束代码区段：

```
``There is a literal backtick (`) here.``
```

这段语法会产生：

```
<p><code>There is a literal backtick (`) here.</code></p>
```

代码区段的起始和结束端都可以放入一个空白，起始端后面一个，结束端前面一个，这样你就可以在区段的一开始就插入反引号：

```
A single backtick in a code span: `` ` ``

A backtick-delimited string in a code span: `` `foo` ``
```

会产生：

```
<p>A single backtick in a code span: <code>`</code></p>

<p>A backtick-delimited string in a code span: <code>`foo`</code></p>
```

在代码区段内，`&` 和方括号**都**会被自动地转成 HTML 实体，这使得插入 HTML 原始码变得很容易，Markdown 会把下面这段：

```
Please don't use any `<blink>` tags.
```

转为：

```
<p>Please don't use any <code>&lt;blink&gt;</code> tags.</p>
```

你也可以这样写：

```
`&#8212;` is the decimal-encoded equivalent of `&mdash;`.
```

以产生：

```
<p><code>&amp;#8212;</code> is the decimal-encoded
equivalent of <code>&amp;mdash;</code>.</p>
```

### 图片

很明显地，要在纯文字应用中设计一个「自然」的语法来插入图片是有一定难度的。

Markdown 使用一种和链接很相似的语法来标记图片，同样也允许两种样式： *行内式*和*参考式*。

行内式的图片语法看起来像是：

```
![Alt text](/path/to/img.jpg)

![Alt text](/path/to/img.jpg "Optional title")
```

详细叙述如下：

* 一个惊叹号 `!`
* 接着一个方括号，里面放上图片的替代文字
* 接着一个普通括号，里面放上图片的网址，最后还可以用引号包住并加上 选择性的 'title' 文字。

参考式的图片语法则长得像这样：

```
![Alt text][id]
```

「id」是图片参考的名称，图片参考的定义方式则和连结参考一样：

```
[id]: url/to/image  "Optional title attribute"
```

到目前为止， Markdown 还没有办法指定图片的宽高，如果你需要的话，你可以使用普通的 `` 标签。

------

## 其它

### 自动链接

Markdown 支持以比较简短的自动链接形式来处理网址和电子邮件信箱，只要是用方括号包起来， Markdown 就会自动把它转成链接。一般网址的链接文字就和链接地址一样，例如：

```
<http://example.com/>
```

Markdown 会转为：

```
<a href="http://example.com/">http://example.com/</a>
```

邮址的自动链接也很类似，只是 Markdown 会先做一个编码转换的过程，把文字字符转成 16 进位码的 HTML 实体，这样的格式可以糊弄一些不好的邮址收集机器人，例如：

```
<address@example.com>
```

Markdown 会转成：

```
<a href="&#x6D;&#x61;i&#x6C;&#x74;&#x6F;:&#x61;&#x64;&#x64;&#x72;&#x65;
&#115;&#115;&#64;&#101;&#120;&#x61;&#109;&#x70;&#x6C;e&#x2E;&#99;&#111;
&#109;">&#x61;&#x64;&#x64;&#x72;&#x65;&#115;&#115;&#64;&#101;&#120;&#x61;
&#109;&#x70;&#x6C;e&#x2E;&#99;&#111;&#109;</a>
```

在浏览器里面，这段字串（其实是 `[address@example.com](mailto:address@example.com)`）会变成一个可以点击的「address@example.com」链接。

（这种作法虽然可以糊弄不少的机器人，但并不能全部挡下来，不过总比什么都不做好些。不管怎样，公开你的信箱终究会引来广告信件的。）

### 反斜杠

Markdown 可以利用反斜杠来插入一些在语法中有其它意义的符号，例如：如果你想要用星号加在文字旁边的方式来做出强调效果（但不用 `` 标签），你可以在星号的前面加上反斜杠：

```
\*literal asterisks\*
```

Markdown 支持以下这些符号前面加上反斜杠来帮助插入普通的符号：

```
\   反斜线
`   反引号
*   星号
_   底线
{}  花括号
[]  方括号
()  括弧
#   井字号
+   加号
-   减号
.   英文句点
!   惊叹号
```



## 高級功能

### 流程圖 Flowcharts

For more details see [these instructions](https://mermaid-js.github.io/mermaid/#/flowchart).

Possible FlowChart orientations are:

* TB - top to bottom
* TD - top-down/ same as top to bottom
* BT - bottom to top
* RL - right to left
* LR - left to right



~~~gfm
```mermaid
graph LR
A[Hard edge] -->B(Round edge)
    B --> C{Decision}
    C -->|One| D[Result one]
    C -->|Two| E[Result two]
```
~~~

```mermaid
graph LR
A[Hard edge] -->B(Round edge)
    B --> C{Decision}
    C -->|One| D[Result one]
    C -->|Two| E[Result two]
```

```mermaid
graph LR
    A[Hard edge] -->|Link text| B(Round edge)
    B --> C{Decision}
    C -->|One| D[Result one]
    C -->|Two| E[Result two]
```



### Sequence Diagrams

This feature uses [js-sequence](https://bramp.github.io/js-sequence-diagrams/), which turns the following code block into a rendered diagram:

~~~gfm
```sequence
Alice->Bob: Hello Bob, how are you?
Note right of Bob: Bob thinks
Bob-->Alice: I am good thanks!
```
~~~

For more details, please see [this syntax explanation](https://bramp.github.io/js-sequence-diagrams/#syntax).

```sequence
Alice->Bob: Hello Bob, how are you?
Note right of Bob: Bob thinks
Bob-->Alice: I am good thanks!
```

### Flowcharts

This feature uses [flowchart.js](http://flowchart.js.org/), which turns the following code block into a rendered diagram:

~~~gfm
```flow
st=>start: Start
op=>operation: Your Operation
cond=>condition: Yes or No?
e=>end

st->op->cond
cond(yes)->e
cond(no)->op
```
~~~

```flow
st=>start: Start
op=>operation: Your Operation
cond=>condition: Yes or No?
e=>end

st->op->cond
cond(yes)->e
cond(no)->op
```

### Mermaid

Typora also has integration with [mermaid](https://mermaid-js.github.io/mermaid/#/), which supports sequence diagrams, flowcharts, Gantt charts, class and state diagrams, and pie charts.

### Sequence Diagrams

For more details see [these instructions](https://mermaid-js.github.io/mermaid/#/sequenceDiagram).

~~~gfm
```mermaid
%% Example of sequence diagram
  sequenceDiagram
    Alice->>Bob: Hello Bob, how are you?
    alt is sick
    Bob->>Alice: Not so good :(
    else is well
    Bob->>Alice: Feeling fresh like a daisy
    end
    opt Extra response
    Bob->>Alice: Thanks for asking
    end
```
~~~

```mermaid
%% Example of sequence diagram
  sequenceDiagram
    Alice->>Bob: Hello Bob, how are you?
    alt is sick
    Bob->>Alice: Not so good :(
    else is well
    Bob->>Alice: Feeling fresh like a daisy
    end
    opt Extra response
    Bob->>Alice: Thanks for asking
    end
```

### Flowcharts

For more details see [these instructions](https://mermaid-js.github.io/mermaid/#/flowchart).

~~~gfm
```mermaid
graph LR
A[Hard edge] -->B(Round edge)
    B --> C{Decision}
    C -->|One| D[Result one]
    C -->|Two| E[Result two]
```
~~~





### Gantt Charts

For more details see [these instructions](https://mermaid-js.github.io/mermaid/#gantt).

~~~gfm
```mermaid
%% Example with selection of syntaxes
        gantt
        dateFormat  YYYY-MM-DD
        title Adding GANTT diagram functionality to mermaid

        section A section
        Completed task            :done,    des1, 2014-01-06,2014-01-08
        Active task               :active,  des2, 2014-01-09, 3d
        Future task               :         des3, after des2, 5d
        Future task2               :         des4, after des3, 5d

        section Critical tasks
        Completed task in the critical line :crit, done, 2014-01-06,24h
        Implement parser and jison          :crit, done, after des1, 2d
        Create tests for parser             :crit, active, 3d
        Future task in critical line        :crit, 5d
        Create tests for renderer           :2d
        Add to mermaid                      :1d

        section Documentation
        Describe gantt syntax               :active, a1, after des1, 3d
        Add gantt diagram to demo page      :after a1  , 20h
        Add another diagram to demo page    :doc1, after a1  , 48h

        section Last section
        Describe gantt syntax               :after doc1, 3d
        Add gantt diagram to demo page      : 20h
        Add another diagram to demo page    : 48h
```
~~~

```mermaid
%% Example with selection of syntaxes
        gantt
        dateFormat  YYYY-MM-DD
        title Adding GANTT diagram functionality to mermaid

        section A section
        Completed task            :done,    des1, 2014-01-06,2014-01-08
        Active task               :active,  des2, 2014-01-09, 3d
        Future task               :         des3, after des2, 5d
        Future task2               :         des4, after des3, 5d

        section Critical tasks
        Completed task in the critical line :crit, done, 2014-01-06,24h
        Implement parser and jison          :crit, done, after des1, 2d
        Create tests for parser             :crit, active, 3d
        Future task in critical line        :crit, 5d
        Create tests for renderer           :2d
        Add to mermaid                      :1d

        section Documentation
        Describe gantt syntax               :active, a1, after des1, 3d
        Add gantt diagram to demo page      :after a1  , 20h
        Add another diagram to demo page    :doc1, after a1  , 48h

        section Last section
        Describe gantt syntax               :after doc1, 3d
        Add gantt diagram to demo page      : 20h
        Add another diagram to demo page    : 48h
```



### Class Diagrams

For more details see [these instructions](https://mermaid-js.github.io/mermaid/#/classDiagram).

~~~gfm
```mermaid
classDiagram
      Animal <|-- Duck
      Animal <|-- Fish
      Animal <|-- Zebra
      Animal : +int age
      Animal : +String gender
      Animal: +isMammal()
      Animal: +mate()
      class Duck{
          +String beakColor
          +swim()
          +quack()
      }
      class Fish{
          -int sizeInFeet
          -canEat()
      }
      class Zebra{
          +bool is_wild
          +run()
      }
```
~~~

```mermaid
classDiagram
      Animal <|-- Duck
      Animal <|-- Fish
      Animal <|-- Zebra
      Animal : +int age
      Animal : +String gender
      Animal: +isMammal()
      Animal: +mate()
      class Duck{
          +String beakColor
          +swim()
          +quack()
      }
      class Fish{
          -int sizeInFeet
          -canEat()
      }
      class Zebra{
          +bool is_wild
          +run()
      }
```



### State Diagrams

For more details see [these instructions](https://mermaidjs.github.io/#/stateDiagram).

~~~gfm
```mermaid
stateDiagram
    [*] --> Still
    Still --> [*]

    Still --> Moving
    Moving --> Still
    Moving --> Crash
    Crash --> [*]
```
~~~

```mermaid
stateDiagram
    [*] --> Still
    Still --> [*]

    Still --> Moving
    Moving --> Still
    Moving --> Crash
    Crash --> [*]
```



### Pie Charts

~~~gfm
```mermaid
pie
    title Pie Chart
    "Dogs" : 386
    "Cats" : 85
    "Rats" : 150 
```
~~~



```mermaid
pie
    title Pie Chart
    "Dogs" : 386
    "Cats" : 85
    "Rats" : 150 
```





## Reference

* https://en.wikipedia.org/wiki/Markdown
* https://daringfireball.net/projects/markdown/syntax
* https://markdown-zh.readthedocs.io/en/latest/
* https://mermaid-js.github.io/mermaid/#/flowchart
* https://support.typora.io/Draw-Diagrams-With-Markdown/

