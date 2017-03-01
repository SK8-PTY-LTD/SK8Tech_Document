# 问题起因

因营销媒体需要，最近开始写各类原创文章。经调查，一片好文章需要经过3个步骤

1. 文案策划
2. 文字编写
3. 配图排版

而**文字编写**中，MarkDown为最高效纯编辑方式之一，所以，需要一个适合的MarkDown编辑器。

# 需求限制

1. **版本控制**, 最好是能够和[Github](https://github.com)相连接,
1. **实时预览**，也就是编辑的时候可以瞬间看到变化,
1. **离线编辑**, 并且需要Win10/Mac/Linux平台都能够支持,
1. **自定义**的**样式**和**主题**
1. **导出** HTML 源码
1. 方便使用，要普通用户（非码农）也可以习惯使用
1. 精简的文件管理
1. 自动生成网页/电子书/PDF

# 搜索调查

1. [简书](https://jianshu.com)
简书是使用最简单，不需要技术流就能使用的编辑器。他是市面上最优雅的MarkDown编辑器，碾压同行，望尘莫及。事实上，我们使用简书编辑了好几篇文章。
    1. **暖色调**的编辑环境
    1. **自动保存**文字，极好的文件管理
    1. **强大**，却**优雅**的编辑器
    1. **实时预览**，并且对**中文字体**有着非常好的优化

  除了离线编辑，他几乎满足了我们所有的需求。虽然简书推出了App，让作者可以在**移动**环境下**离线**码子，但是长时间盯着**小屏幕**码子真的很蛋疼，以及**低效**。既然简书并没有一个PC端可以使用的离线版本，只好无奈Pass。
 
1. [Gitbook](https://gitbook.com)
  顾名思义，Gitbook是国外出的一款与Git深度相连的MarkDown编辑器。它满足我们所有需求的同时，甚至还有“自动导出”文档网站/电子书/PDF的功能。简直吊炸天。唯一缺点是它的中文字体显示不是很友好，不过这个可以通过自定义**CSS/SASS/LESS**来解决。没错，你没看错，它还支持SASS和LESS。

  注意：Gitbook还在高速发展阶段，所以整个工具都是英文的，暂时也没找到汉化版，所以对英文有点要求。不过会写MarkDown的你，这点点问题应该是小Case啦~

1. [SublineText3](sublimetext.com) + [OmniMarkdownPreviewer](https://github.com/timonwong/OmniMarkupPreviewer)
SublimeText是一个免费开源的编辑器，它有着庞大的开发者社区为之开发各类牛逼哄哄的功能插件。要编辑MarkDown的话，我推荐以下主流插件，**MarkdownEditing**, **MarkdownPreview**, **OmniMarkdownPreviewer**.

  亲测后，我们最喜欢**[OmniMarkdownPreviewer](https://github.com/timonwong/OmniMarkupPreviewer)** 给我们带来的编辑流程。爽就一个字，我只说一次。
  
    注意：**[OmniMarkdownPreviewer](https://github.com/timonwong/OmniMarkupPreviewer)**带来的**实时预览**是在**浏览器**中查看的。也就是说编辑时，至少需要开2个窗口，强迫症渗入。


# Solution & Reason

We end up going for [Gitbook](https://gitbook.com) in the end, because:

1. It's the most friendly editor, suitable for both developers, designers, even everyday users.
1. It has a wide range of functions, and can be used to generate Website/Ebook/PDF
1. It's one install to use, in comparison to sublime+plugins

# Author
[Jacktator](https://jacktator.com)