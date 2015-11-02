<!--[TOC]-->

## 注释（Comment）
注释是写作者自己的标注记录，不被浏览器解析渲染。  
HTML 以`<!--`开头，以`-->`结尾的闭包定义注释，不在正文中显示。  
Markdown 沿用 [HTML Comment][HTML_COMMENT_REFID] 注释格式：  
`<!-- This text will not appear in the browser window. -->`
<!-- This text will not appear in the browser window. -->

**注释适用场景示例：**  
1.CSDN 博客默认会在网页生成TOC，而 GitHub 仍不支持`[TOC]`，因此在发布 Markdown 博客时可注释掉开头的 [TOC] 标签，在需要查看 OUTLINE 时再打开。  
`<!--[TOC]-->`

2.在博客 Markdown 源码开头，我通常使用注释来备注 git commit-hash-id 和 commit-date 信息，以便修订变更时回溯。  
`<!--commit 5326f29752b7ee3472aa00b40574bd585e3ef25b-->`
`<!--Mon Nov 2 00:36:40 2015 +0800-->`

3.在使用 Markdown 写作博客时，我喜欢采用参考式链接，然后在文末专门开辟一节用于定义文中用到的所有脚注和参考链接。借助 Haroopad/FoldingText/Marked2 的折叠特性，我习惯在末尾添加一行 Comment Heading，用于在阅读 Markdown 源码时折叠隐藏文末的参考区。  
`##<!--以下是本文的脚注和超链接-->`

## <font color='red'>标题（Header）</font>[^Header]
标题用于呈现文档组织结构，很多 Markdown 解析器都提供基于 Heading Levels 来生成文档大纲的 `[TOC]`（Table of Contents）标签，搜索引擎则使用标题为网页的结构和内容编制索引。  
一般论文或博客文档结构到3到4级即可，可参考《[毕业论文的国家标准格式与通用格式][]》、《[发表论文通用格式][]》和《[期刊论文格式][]》。

Markdown 支持两种标题的语法，类 [Setext][] 和类 [atx][] 形式。

### Setext Heading Format（2 level）
类 Setext 形式是用底线的形式，使用三个或以上 = 底线标记最高阶标题，使用三个或以上 - 底线标记第二阶标题。例如：

	This is an H1
	===

	This is an H2
	----

### Atx Heading Format（6 level）
类 Atx 形式则是在行首插入 1 到 6 个 # ，对应 6 阶标题（对应 HTML 中的 `<h1>` - `<h6>` 标签）。例如：

	# 这是一级标题（H1，通常用于文档标题）  
	## 这是二级标题（H2，渲染器会自动添加 hr 底线）  
	### 这是三级标题（H3）  
	#### 这是四级标题（H4）  
	##### 这是五级标题（H5）#####  
	###### 这是六级标题（H6）######

行首的 `#` 号个数决定标题阶数，行中（末）的 `#` 号则被视作普通字符。  
为美观起见，你也可以选择性地「闭合」类 atx 样式的标题，在行尾加上对应或不限数量的 # 号。

## 句段（Sentence / Paragraph）
### 换行
标准 Markdown 不支持自然换行（literal new line），有些扩展的 Markdown Render 支持自然换行。  
`#` 号标识的 Heading（H1-H6） 会自然换行，普通句段之间若要强制换行，可以在自然换行行尾追加两个（或以上）空格来实现。

**适时内嵌 HTML 的 `<br>` 控制换行**  
由于空格在 Markdown 中主要是起着控制排版的作用，因此在某些复杂的区块元素中，例如下文提到的 Table 表格中的 td 元素文本中，只能通过内嵌 HTML 的`<br>`（XHTML 自闭合写作 `<br />`）标签来实现局部换行。

### 分段
段落是由一个或多个连续的文本行组成，它的前后往往需要**空行**予以明示分隔。

> 在显示上看起来像是空的，例如只包含空格或（和）制表符的行，便会被视为空行。

**空行适用场景说明：**  
1.空行的上一句末无需再添加两个空格或`<br/>`换行了。  
2.句段之间引入空行，相当于间隔成段落（对应 HTML 的 `<p>` 标签）。  
3.尽管 Markdown Render 会对各阶 Heading（H1-H6）有特殊的格式渲染来凸显层级，但还是建议在章节（Section/Chapter）末尾适时插入空行，以示行文分割且方便阅读。  
4.一般建议在分割线（Horizontal Rules）的首行，块引用（Blockquote）、预格式化（Preformatted Code Block）、列表（List）、表格（Table）等区块元素的前后插入空行。

## 符号（Punctuation Characters）
### 转义字符
Markdown 精挑细选了一些符号组成了一套基于文本的标记语法。比如：

* 在文字两旁加上 \* 号，看起来就像\*强调\*。
* 多行行首添加 +（或 - 或 \*），看起来就是列表。
* 句段行首添加 > 号来引用区块，就像你曾在电子邮件中见过的那样。

可以使用反斜杠（\\）转义输入 Markdown 标记符号的原义字符。  

- - -
\#：行首的 <kbd>#</kbd> 号默认为H1，这里使用反斜杠转义显示原义字符。  

### 字符实体
在 Markdown 中，空格和制表符（tab）往往用于格式控制，例如：

- 行首的四个空格表示 `<pre>`；
- 引用、列表的 bullet 符号前的空行用于缩进层级；
- ...

普通段落一般都是顶格开始，无法使用空格或制表符来缩进，包括引用标记符（>）、列表标记符（bullet list indicator）后面的空格都无法实现缩进。  
如果硬要输入空格显示占位缩进效果，可以嵌入空格对应的 [HTML Entity][] 实体码。HTML 转义字符串（Escape Sequence），即字符实体（Character Entity），由三部分构成：

1. 第一部分是一个`&`符号，英文叫 ampersand；
2. 第二部分是实体（Entity）名字，或者是 `#` 加上实体编号（[Entity Code][]）；
3. 第三部分是一个分号（`;`）。

_ _ _
  普通自然行行首敲2个空格无占位缩进效果。  
&nbsp;&nbsp;&#160;&#160;该行行首添加了4个不断行的空白格：no-break space(`&nbsp;`或`&#160;`）  
&ensp;&ensp;&ensp;&ensp;该行行首添加了4个半方大的空白：en space（`&ensp;`或`&#8194;`）  
&emsp;&emsp;&#8195;&#8195;该行行首添加了4个全方大的空白：em space（`&emsp;`或`&#8195;`）

## 分隔线（Horizontal Rules）
你可以在一行中用三个以上的星号（*）或减号（-）或底线（_）来建立一个水平分隔线，对应 HTML 中的 `<hr>` 标签，用于Sentence/Section/Page Break。  
行内不能有其他东西，但你可以在星号或是减号中间插入空格。  
下面每种写法都可以建立起分隔线：

	---
	- - -
	-----

**注意：**
> 采用减号（-）分割时，最好空格隔开或上面空一行，不然三个以上连续的减号会误将上一行文字升级为二级标题！

## 文本格式（Text Styling）
文本格式包括强调、加粗、突出、下划线、删除线、脚标等增强修饰和丰富表现。

### 强调（Italic/Emphasize）
**说明：**  
星号（*）或下划线（_）包围的文字将会显示斜体，对应 HTML 中的 `<i>` / `<em>` 标签。

**语法：**

```Markdown
Some of these words *are emphasized*.
Some of these words _are emphasized also_.
```

**示例：**  
Some of these words *are emphasized*.  
Some of these words _are emphasized also_.

**[GFM][Github Flavored Markdown] 保持词内下划线：**
鉴于C语言等源码中，通常采用下划线定义变量，因此 GitHub Flavored Markdown 中忽略单词内的下划线，同时建议使用星号（*）闭包斜体。

_ _ _
下划线闭包单词斜体：wow _great_ stuff (源码：`wow _great_ stuff`)
忽略单词内的下划线：wow_great_stuff

### 加粗（Bold/Strong）
**说明：**  
两个星号（**）或下划线（__）包围的需要特别强调的文字将会加粗显示，对应 HTML 中的 `<b>` / `<strong>` 标签。

**语法：**

```Markdown
Use two asterisks for **strong emphasis**.
Or, if you prefer, __use two underscores instead__.
```

**示例：**  
Use two asterisks for **strong emphasis**.  
Or, if you prefer, __use two underscores instead__.

### 突出（Mark/Highlight）
**说明：**  
在 HTML 中，可以使用 `<mark>` 标签来高亮显示文字，以达到醒目的目的。  
标准 markdown 没有提供对应的标签支持，Macdown 和 Haroopad 均使用两个等号包围来突出高亮显示。

**语法：**  
Macdown 和 Haroopad：`==Highlight==`
[CriticMarkup][]语法：`{==Highlight==}`

**示例：**  
Macdown 和 Haroopad：==Highlight==

### 下划线（Underline）
**说明：**  
在 HTML 中，可以使用 `<u>` 标签来为文本添加下划线。  
标准 markdown 没有提供对应的标签支持，MMD（[MultiMarkdown][]） 提供了扩展支持。  
Macdown 使用星号表示强调，使用下划线表示下划线原义；Haroopad 则使用两个加号来标记下划线。

**语法：**  
Macdown：`_underline_`  
Haroopad：`++underline++`

**示例：**  
Macdown：_underline_  
Haroopad：++underline++

### 删除线（Strikethrough）
**说明：**  
在 HTML 中，可以使用 `<del>` 标签来定义文档中已被删除的文本（配合 `<ins>` 标签来描述文档中的更新和修正）。  
标准 markdown 没有提供对应的标签支持，GFM（[Github Flavored Markdown][]） 提供了扩展支持，使用两个波浪符号（~~）包围来给文本添加删除线。

**语法：**  
`~~Strikethrough~~`

**示例：**  
~~Strikethrough~~

### 脚标（Script）
标准 Markdown 不支持脚标，只能通过内嵌 HTML 的`<sup>`和`<sub>`标签来实现。

#### 上脚标：
Haroopad 语法：`^Superscript^`  
HTML 语法：`<sup>superscript</sup>`

**示例：**  
2^10^ = 2<sup>10</sup> = 1024;

#### 下脚标：
Haroopad 语法：`~Subscript~`  
HTML 语法：`<sub>subscript</sub>`

**示例：**  
H~2~O = H<sub>2</sub>O is a liquid.

## 链接（Hyperlink）
### 自动链接
当我们在书写一个网址时，有些 Markdown Render 能自动生成标题与网址一致的链接，这种链接也即**自动链接**。  
Markdown 支持以比较简短的自动链接形式来处理网址和电子邮件信箱，只要用尖括号包起来的文字， Markdown 就会自动把它转化成链接。  
对于 HTTP(s) 协议开头的超链接地址，甚至无需添加尖括号明示，也会生成自动链接。  

<http://daringfireball.net/projects/markdown/>

### 文字（text href）
Markdown 支持两种形式的超文本链接语法格式： 行内式（Inline）和参考式（Reference）两种形式。  
不管是哪一种，链接文字都是用方括号（[square brackets]）来标记。  

#### 行内式
只要在方块括号后面紧接着圆括号并插入链接网址即可在一行内构建链接，其语法格式为`[text](url)`，HTML 等效源码为 `<a href="url">text</a>`。  
如果是要链接到本机资源，可以使用相对路径（./path/to/your/resource）。

以下定义了一个指向 Daring Fireball Markdown 首页的超链接：

_ _ _
`[Daring Fireball Markdown](http://daringfireball.net/projects/markdown/)`  
[Daring Fireball Markdown](http://daringfireball.net/projects/markdown/)

- - -
如果你还想要加上链接的 title ，只要在网址后面用双引号把 title 文字包起来即可。

_ _ _
`[Daring Fireball Markdown](http://daringfireball.net/projects/markdown/ "Markdown Official Website")`  
[Daring Fireball Markdown](http://daringfireball.net/projects/markdown/ "Markdown Official Website")

- - -
将鼠标悬停在超链接文本上将会提示 “Markdown Official Website”。

#### 参考式
参考式的链接是在链接文字的括号后面再接上另一个方括号，在第二个方括号里面填入用以辨识链接的标记id，然后在其他地方给出该标记id真正的链接地址。

_ _ _
1.先定义参考refid：`[text][refid]`  
2.再定义refid所指：`[refid]:URL`

- - -
以下参考间接定义指向 Daring Fireball Markdown 首页的超链接：

_ _ _
1. 先定义参考id为markdown_homepage_refid：  
`[Daring Fireball Markdown][markdown_homepage_refid]`  
2. 再在其他地方定义markdown_homepage_refid指向的URL：  
`[markdown_homepage_refid]:http://daringfireball.net/projects/markdown/`  
3. 最终效果同行内式：  
[Daring Fireball Markdown][markdown_homepage_refid]  
[markdown_homepage_refid]:http://daringfireball.net/projects/markdown/

- - -
**说明：**

1. 你也可以选择性地在两个方括号中间加上一个空格。  
2. refid 所指 href URL 在文件任意处给出定义即可。    
3. `[refid]:URL` 的 URL 后面可以选择性地用单引号、双引号或是括弧闭包起来标记 title。  
下面这三种链接的定义都是相同的：  
`[foo]: http://example.com/  "Optional Title Here"`  
`[foo]: http://example.com/  'Optional Title Here'`  
`[foo]: http://example.com/  (Optional Title Here)`

### 图片（image href）
#### 插入图片
Markdown 使用一种和文本链接很相似的语法来插入图片，同样也允许两种样式： 行内式和参考式。  
不同的是，需要在链接文字方括号之前添加一个感叹号（!），其语法格式为 `![alt_text](url)`，HTML 等效源码为 `<img src="url" alt="text" />`，其中alt_text可以置空。  

_ _ _
daringfirefall logo:  
`![daringfirefall](http://daringfireball.net/graphics/logos/)`
![daringfirefall](http://daringfireball.net/graphics/logos/ "daringfirefall")

当然，你也可以像文字链接那样添加 title 以供鼠标悬停提示。

**说明：**  
Markdown 中的段落（包括图片）默认顶格左对齐，若要将图片居中，可以直接内嵌 HTML 的 `<img>` 标签，设置其*align*属性。如果还不行，可以通过封裹一层 div 设置其 `style="text-align:center"` 实现：

```HTML
<div style="text-align:center"><img src="http://my.csdn.net/uploads/avatar/9/D/B/1_phunxm.jpg" /></div>
```

<div style="text-align:center"><img src="http://my.csdn.net/uploads/avatar/9/D/B/1_phunxm.jpg" /></div>

#### 图片链接
如果拷贝了别人的图片插入到自己的博客中，最好在图片上给出一个超链接指向源头，方便追溯出处。  
我们在 Markdown 图片标记`![]()`外面再嵌套一层`[]()`即可建立图片超链接，点击图片即可跳转到链接地址。  
图片链接的格式看起来大概是这样的:  
`[![](img_url)](ref_url)`

_ _ _
定义 haroopad logo 指向首页：  
`[![](http://pad.haroopress.com/assets/images/logo-small.png "haroopad")](http://pad.haroopress.com/)`

[![](http://pad.haroopress.com/assets/images/logo-small.png "haroopad")](http://pad.haroopress.com/)

### 锚点（inner link）
HTML 中的 `<a>` 标签最重要的属性是 href ，它指示的链接目标，既可以是外部站点，也可以是页内锚点。页内锚点可以实现类似书签跳转的功能，最典型的就是点击 TOC 中的目录书签跳转到指定章节阅读。  
构建页内锚点的语法，类似参考式链接：

_ _ _
1. 先定义锚点id：`<a href="#auchor_id">bookmark_text</a>`  
2. 再定义一个id为auchor_id的对象（这里以`<p>`为例）：`<p id="auchor_id">auchor_text</p>` 
 
- - -

例如，我们在文末定义了id为end的 EOF（End Of File）：`<p id="end">The end！</p>`，然后通过`<a href="#end">Goto the End!</a>`指定书签“Goto the End!”跳转到文末“The End!”处：

<a href="#end">Goto the End!</a>

## 引用（Blockquote）
HTML 中的 `<blockquote>` 标签定义摘自另一个源的块引用。  
`<blockquote>` 与 `</blockquote>` 之间的所有文本都会从常规文本中分离出来，经常会在左右两边进行**缩进**，而且有时会使用**斜体**。也就是说，块引用拥有它们自己的<u>空间</u>。

Markdown 标记区块引用是使用类似 email 的引用方式，在断好的行前加上 `>` ：

```Markdown
> 爱上一个人  
> 恋上一座城
```

> 爱上一个人  
> 恋上一座城

- - -
行首的多重引用标记可以实现嵌套缩进效果（注意解梦时需要空行出梦）：

```Markdown
> 梦
>> 梦中梦
>>> 盗梦空间

>> 梦中梦

> 梦
```

> 梦
>> 梦中梦
>>> 盗梦空间

>> 梦中梦

> 梦

**说明：**  
若使用引用格式插入代码，行首的缩进格式丢失，需要自行补充空格占位符。  
一般不建议使用 blockquote（`>`）格式引用源代码，应采用 pre 格式引用代码。

## 代码（Code）
如果要标记行内代码片段，可以用**反引号闭包**；如果要插入跨行片段或块，可使用**预格式化**语法。  
本文在示范 Markdown 语法源码时，独行单句采用了行内代码格式，跨行代码片段则采用了代码块格式。

### 行内代码（Inline Code）
**说明：**

如果要标记行内代码片段，可以用反引号（backtick quotes）闭包，对应 HTML 中的 `<code>` 标签（把文本变成等宽字体，暗示是源程序代码）。  
如果要在代码区段内插入反引号，可以用多个反引号来开启和结束代码区段。  

**语法：**

Use the \`printf()\` function.(此处使用了反斜杠转义)

**示例：**

Use the `printf()` function.(\`printf()\`)
Use the`` `printf()` ``function.(\`\` \`printf()\` \`\`\`)

### 代码块（Code Blocks）
**说明：**

- Preformatted Code Block  
	如果要插入跨行片段或块，且要保持排版样式（包括空格、换行符和缩进），可使用**预格式化**引用语法格式。对应 HTML 中的 `<pre>` 标签。  
- Fenced Code Block  
	如果要支持编程语言语法高亮，则可以使用 GFM 扩展的基于 YAML[^YAML] 标记语言的 Fenced Code Block 引用语法格式。

**语法：**

- Preformatted Code Block  
	在句段的行首插入1个tab制表符或4个空格，则表示代码块。  
- [Fenced Code Block]  
	在句段行首和行末用三个反引号换行闭包，并在行首三个反引号后添加 [YAML][] 语言标识。

**示例：**

- Preformatted Code Block  
	将一段代码块整体向右缩进（<kbd>⌘</kbd> + <kbd>]</kbd>）即可测试。

	pre 格式存在以下缺陷：

	 - 对多tab及空格的缩进支持不完善！
	 - 将宏符号#（#include、#import）[误解][haroopad_bug_#536]为H1，可能会影响解析器的TOC！
	 - 将顶格空白行（包括行首带tab）误认为Paragraph Break，而割断代码块成片段！

- Fenced Code Block  
	以下演示了插入一段 Objective-C 代码：

	> 首行：\`\`\`obj-c  
	> 中间：Objective-C Code Block  
	> 末行：\`\`\`

```obj-c
//
//  main.m
//  EmptyApplication
//
//  Created by faner on 15/9/5.
//  Copyright © 2015年 faner. All rights reserved.
//

#import <UIKit/UIKit.h>
#import "AppDelegate.h"

int main(int argc, char * argv[]) {
	@autoreleasepool {
		return UIApplicationMain(argc, argv, nil, NSStringFromClass([AppDelegate class]));
	}
}
```

**注意：**

- Haroopad 编辑器将上述代码中的`#import`的第一个有效字符`#`[误解为 H1][haroopad_bug_#536]，导致 TOC 错乱或  Heading Focus Folding 失效。此时，可以在Fenced Code Block 行首添加空格或 tab 缩进。
- 关于 GitHub 配置 Fenced Code Block 语法高亮所使用的 YAML ，可参考[初探YAML][]、[YAML学习][]、[YAML学习总结][]、[YAML--想要爱你很容易][]。

## 列表（List）
GFM 等 Markdown 扩展支持和无序列表、有序列表和任务列表。

### 无序列表（Unordered List）
无序列表项目的行首使用星号、加号或减号作为列表标记：

```Markdown
- bullet list item 1 begin with a '-'
+ bullet list item 2 begin with a '+'
* bullet list item 3 begin with a '*'
```

示例效果：

- bullet list item 1 begin with a '-'
+ bullet list item 2 begin with a '+'
* bullet list item 3 begin with a '*'

和引用一样，无序列表可以通过在列表标记前面增加多重空格（或 tab）来实现嵌套效果。  
以下是针对本文 TOC 中【链接】这一章节的目录：

```Markdown
- 链接（Hyperlink）
 - 自动链接
 - 文字（text href） <!--行首1个空格-->
     - 行内式 <!--行首5个空格-->
     - 参考式
 - 图片（image href）
     - 插入图片
     - 图片链接
 - 锚点（inner link）
- 引用（Blockquote）
```

- - -

- 链接（Hyperlink）
 - 自动链接
 - 文字（text href）
     - 行内式
     - 参考式
 - 图片（image href）
     - 插入图片
     - 图片链接
 - 锚点（inner link）
- 引用（Blockquote）

### 有序列表（Ordered List）
有序列表项目的行首则使用数字接一个英文句点标记：

```Markdown
1. GETTING STARTED  
	Choosing Blogging Platform (WordPress)
2. GETTING YOUR BLOG ONLINE  
	Choosing Domain Name & Web Hosting
3. DESIGNING AND TWEAKING YOUR BLOG  
	Quick and easy ways to get your blog look the way you want
4. WRITING BLOG POSTS AND PAGES  
	Adding new content for your Blog (Posts, Pages, Images etc…)
```

[Step-by-step walkthrough for starting a blog](http://startbloggingonline.com/):

1. GETTING STARTED  
	Choosing Blogging Platform (WordPress)
2. GETTING YOUR BLOG ONLINE  
	Choosing Domain Name & Web Hosting
3. DESIGNING AND TWEAKING YOUR BLOG  
	Quick and easy ways to get your blog look the way you want
4. WRITING BLOG POSTS AND PAGES  
	Adding new content for your Blog (Posts, Pages, Images etc…)

有序列表和无序列表可以实现混合嵌套编排。

### 任务列表（Task Lit）
GFM 扩展支持把列表变成带勾选框的任务列表，只需要在列表标记后添加`[ ]`标记☐表示unchecked，在中括号中填写x（`[x]`）标记☑︎表示checked（filled）。

```Markdown
- [ ] task1 to do
- [x] task2 done
1. [ ] task3 to do
2. [x] task4 done
```

- - -

- [ ] task1 to do
- [x] task2 done
1. [ ] task3 to do
2. [x] task4 done

## 表格（Table）
You can create tables by assembling a list of words and dividing them with hyphens `-` (for the first row), and then separating each column with a pipe `|`:

First Header  | Second Header
------------- | -------------
Content Cell  | Content Cell
Content Cell  | Content Cell

For aesthetic purposes, you can also add extra pipes on the ends:

| First Header  | Second Header |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |

Note that the dashes at the top don't need to match the length of the header text exactly:

| Name | Description          |
| ------------- | ----------- |
| Help      | Display the help window.|
| Close     | Closes a window     |

You can also include inline Markdown such as links, bold, italics, or strikethrough:

| Name | Description          |
| ------------- | ----------- |
| Help      | ~~Display the~~ help window.|
| Close     | _Closes_ a window     |

Finally, by including colons `:` within the header row, you can define text to be left-aligned, right-aligned, or center-aligned:

| Left-Aligned  | Center Aligned  | Right Aligned |
| :------------ |:---------------:| -----:|
| col 3 is      | some wordy text | $1600 |
| col 2 is      | centered        |   $12 |
| zebra stripes | are neat        |    $1 |

A colon on the left-most side indicates a left-aligned column; a colon on the right-most side indicates a right-aligned column; a colon on both sides indicates a center-aligned column.

## 数学公式
You can render *LaTeX*[^LaTeX] mathematical expressions using **MathJax**[^MathJax], as on math.stackexchange.com:  
The *Gamma function* satisfying $\Gamma(n) = (n-1)!\quad\forall n\in\mathbb N$ is via the Euler integral

$$
\Gamma(z) = \int_0^\infty t^{z-1}e^{-t}dt\,.
$$

书写一个质能守恒公式

$$E=mc^2$$

可参考 [Mathjax与LaTex公式简介][]。

##<!--以下是本文的脚注和超链接-->
<p id="end">The end！</p>

[^Header]:这里的源码为`<font color='red'>标题（Header）</font>`，尝试使用 font.color 着色。

[^YAML]:[YAML](http://yaml.org/)是"YAML Ain't a Markup Language"（YAML不是一种置标语言）的递归缩写，早先YAML的意思其实是："Yet Another Markup Language"（另外一种置标语言）。

[^LaTeX]: [LaTeX](http://www.latex-project.org/)是一种基于 [ΤΕΧ](http://www.ctex.org/documents/shredder/tex_frame.html)的排版系统，它通过\section和\paragraph等语句，规定了每一句话在文章中所从属的层次，从而极大方便了对各个层次批量处理。可参考 [TeX 与 LaTeX](http://blog.csdn.net/dbzhang800/article/details/6820659)、[LaTeX 入门文档](http://liam0205.me/2014/09/08/latex-introduction/) 和 [LaTeX 入门教程](http://www.douban.com/note/330524120/)。

[^MathJax]: [MatchJax](http://meta.math.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference) 是一个JavaScript引擎，用来显示网络上的数学公式。MathJax可以解析Latex、MathML和ASCIIMathML的标记语言。 

[HTML_COMMENT_REFID]:http://home.wangjianshuo.com/cn/20070526_aeaeaehtmleccommentie.htm

[毕业论文的国家标准格式与通用格式]:http://www.zaojiance.com/news/news-detail-2013-10-09-23-55.html
[发表论文通用格式]:http://wenku.baidu.com/link?url=CCLjLN3lGmNVU6_TlAiTgSXZKNObnmFPEKuVXIw8OanlNhzy7vWhu-r-ekzb7GjUGoHKfnFehrClNFbB3yCgcOcJqVYYMuTfddxjw5gIPse
[期刊论文格式]:http://biyelunwen.yjbys.com/geshi/417273.html

[Setext]:http://docutils.sourceforge.net/mirror/setext.html
[atx]:http://www.aaronsw.com/2002/atx/

[HTML Entity]:http://114.xixik.com/character/
[Entity Code]:http://entity-lookup.leftlogic.com/

[CriticMarkup]:http://www.criticmarkup.com/
[MultiMarkdown]:http://fletcherpenney.net/multimarkdown/

[haroopad_bug_#536]:https://github.com/rhiokim/haroopad/issues/536

[Github Flavored Markdown]:https://help.github.com/articles/github-flavored-markdown/

[YAML]:https://github.com/github/linguist/blob/master/lib/linguist/languages.yml

[初探YAML]:http://www.cnblogs.com/chwkai/archive/2009/03/01/249924.html
[YAML学习]:http://blog.csdn.net/conquer0715/article/details/42108061
[YAML学习总结]:http://www.cnblogs.com/dbasys/archive/2007/06/11/2127620.html
[YAML--想要爱你很容易]:http://www.ibm.com/developerworks/cn/xml/x-1103linrr/

[Mathjax与LaTex公式简介]:http://mlworks.cn/posts/introduction-to-mathjax-and-latex-expression/
