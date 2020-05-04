---
layout: '[layout]'
title: Diff-synatx-in-code-blocks
date: 2020-04-12 13:23:32
tags:
    - Markdown
    - Writing skills
categories: Writing
abbrlink: diff-synatx-in-code-blocks
toc: true
---

这几次看别人博客时总是发现了一些东西，比如有的博客中总是出现下面的这种样式：

```diff
// this is a test.
- this is removed;
+ this is added.
```

> 这样的样式，很方便：红色表示被删减，绿色表示被增加。人眼对色彩是非常敏感的，这样鲜明的对比很容易被人识别出来，方便阅读博客。

第一次见到`diff syntax`这个词是在这个[地方](https://io-oi.me/tech/hexo-next-optimization/#fnref:1)，其中讲述到这个功能的地方如下图

![image-diff_example](diff-synatx-in-code-blocks/diff_example.jpg)

当时很想找到如何才能在自己博客的代码段实现这个功能，百度中也未搜索到这个东西，在不知道这个功能名称的前提下去根据功能的描述进行搜索，很费脑筋去想关键词，这样一来如果自己的描述关键词不沾边，结果可想而知。



想要实现这个效果：
在代码块中制定语言，在**```**后加上`diff`表示语言，然后接着如下进行书写就可以了。

```
- removed
+ added
```

## 参考文档

[1] [打造个性超赞博客 Hexo + NexT + GitHub Pages 的超深度优化](https://io-oi.me/tech/hexo-next-optimization/#fnref:1)
[2] [stackoverflow: Diff syntax highlighting in Github Markdown](https://stackoverflow.com/questions/40883421/diff-syntax-highlighting-in-github-markdown)
[3] [MarkdownDiffExample.md](https://gist.github.com/salmedina/ad8bea4f46de97ea132f71b0bca73663#file-markdowndiffexample-md)
