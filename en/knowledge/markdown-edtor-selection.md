# Problem

As we start writing usimg MarkDown, we need an editor.

# Requirement

1. **Version Control**, preferrably intergration with [Github](https://github.com)
1. **Live** Preview
1. **Offline** Editing, so Win10/Mac/Linux application only
1. **Customisable **Themes** and **Styles**
1. **Exportable** HTML Source Code
1. User friendly for **everyone**
1. Elegant File management
1. Website/Ebook/PDF generation

# Research

1. [简书](https://jianshu.com)
简书 is the least technical solution. It is by far the most elegant solution for most everyday users.
    1. **Warm color schema** while editing
    1. Good file management with **AutoSave**
    1. Powerful, yet simple editor options
    1. Live Preview, with **Optimisation for Chinese fonts**

  It fits almost all requirement, except for 3. While 简书 Provides mobile app which allows for **mobile** offline editing, it would be a pain in the ass and **inefficient** to write long texts on **small screens**. And since 简书 does not have a offline PC version, it's a deal breaker for us.
 
1. [Gitbook](https://gitbook.com)
Gitbook fits all requirements above. It even supports **AutoExport** to Website/Ebook/PDF. Its Chinese font support is poor, but this can be overcome by writing custom **CSS/SASS/LESS**, and yes, it does support the later two.

1. [SublineText3](sublimetext.com) + [OmniMarkdownPreviewer](https://github.com/timonwong/OmniMarkupPreviewer)
SublimeText is well known for its openess. Its developer communitiy also developed many plugins to extend its capabilities. For editing Markdown, **MarkdownEditing**, **MarkdownPreview**, **OmniMarkdownPreviewer** are the most popular ones in use. 

  After testing, **[OmniMarkdownPreviewer](https://github.com/timonwong/OmniMarkupPreviewer)** yields the most comfortable workflow due to its **LivePreview** feature. Note that preview is shown in a **browser**, so you'll have one more seperate window to manage.


# Solution & Reason

We end up going for [Gitbook](https://gitbook.com) in the end, because:
1. It's the most friendly editor, suitable for both developers, designers, even everyday users.
1. It has a wide range of functions, and can be used to generate Website/Ebook/PDF
1. It's one install to use, in comparison to sublime+plugins

# Author
[Jacktator](https://jacktator.com)