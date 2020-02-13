---
title:
- 文章标题 | 服务名称
description: ''
keywords: ''
author:
- GITHUB USERNAME
manager:
- ALIAS
ms.date: 04/28/2016
ms.topic: article
ms.prod: ''
ms.service: ''
ms.technology: ''
ms.assetid:
- GET ONE FROM guidgenerator.com
ms.openlocfilehash: ed2d00541c2d89efd0f8cd6aa60f29c527656fc0
ms.sourcegitcommit: 5178aec0244e023e73546f3d10f1a76eaf1f4a3e
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 02/03/2020
ms.locfileid: "76971829"
---
# <a name="metadata-and-markdown-template"></a>元数据和标记模板

此 docs.ms 模板包含 Markdown 语法示例，并介绍了如何设置元数据。 它在所有 EM 试验存储库的根目录下均可用，（例如，~/Azure-RMSDocs-pr /template.md），并应读取为标记文件，你还可以参考[已发布的版本](https://stage.docs.microsoft.com/en-us/rights-management/template)，查看示例标记的呈现方式。

创建标记文件时，应将模板复制到新的文件，按下面所指定的那样填写元数据，将上方的 H1 标题设置为该文章的标题并删除内容。 


## <a name="metadata"></a>元数据 

上方是完整的元数据块，分为必填字段和可选字段；有关更多详细信息，请参阅 [OPS 元数据速查表](https://ppe.msdn.microsoft.com/en-us/ce-csi-docs/ops/ops-onboarding/managing-content/content-meta-data)。 下面是一些关键注意事项：

- 冒号（：）和元数据元素的值之间**必须**有一个空格。
- 如果可选的元数据元素没有值，用 # 注释该元素（不要留空或使用 "na"）；如果你要向注释的元素添加值，请务必删除 #。
- 如果值（例如，title）中有冒号，将会导致元数据分析程序失效。 将冒号替换为 HTML 编码 &#58;（例如“title：Azure Rights Management&#58; the basics | Azure RMS”）。
- **title**：此标题显示在搜索引擎结果中。 此标题应以竖线 (|) 结尾，后跟服务名称（示例如上）。 此标题不需要（可能也不应该）与 H1 标题中的标题完全相同。 大约应包含 65 个字符（包括“| SERVICE NAME”）
- **author**、**manager**、**reviewer**：“author”字段应包含创建者的 Github 用户名  ，而不是别名。  相比之下，“manager”和“reviewer”字段应包含别名。 ms.reviewer 指定与文章或服务相关的 PM 姓名。
- **ms.assetid**：此为 CAPS 文章的 GUID。 新建 Markdown 文件时，请从 [https://www.guidgenerator.com](https://www.guidgenerator.com) 获取 GUID。 
- **ms.prod**、**ms.service**、**ms.technology**、**ms.devlang**、**ms.topic**、**ms.tgt_pltfrm**：可在[此处](https://microsoft.sharepoint.com/teams/STBCSI/Insights/_layouts/15/WopiFrame.aspx?sourcedoc=%7b7A321BF1-0611-4184-84DA-A0E964C435FA%7d&file=WEDCS_MasterList_CSIValues.xlsx&action=default)找到这些元素的可能值。

## <a name="basic-markdown-and-gfm"></a>基本 Markdown 和 GFM

支持所有基本 Markdown 和 Github 式 Markdown。 有关详细信息，请参阅：

- [基线 Markdown 语法](https://daringfireball.net/projects/markdown/syntax)
- [Github 式 Markdown (GFM) 文档](https://guides.github.com/features/mastering-markdown)

## <a name="headings"></a>标题

一级和二级标题示例如上。 

主题中必须  只能有一个一级标题（显示为页内标题）。  

二级标题生成页内 TOC，显示在页内标题下方的“在本文中”部分。

### <a name="third-level-heading"></a>三级标题
#### <a name="fourth-level-heading"></a>四级标题
##### <a name="fifth-level-heading"></a>五级标题
###### <a name="sixth-level-heading"></a>六级标题

## <a name="text-styling"></a>文本样式

*斜体* 

**粗体** 

~~删除线~~



## <a name="links"></a>Links

若要链接到同一存储库中的 Markdown 文件，请使用[相对链接](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2)。 

- 例如：[什么是 Azure 权限管理](./understand-explore/what-is-azure-rights-management.md)

若要链接到同一 Markdown 文件中的标头，请查看已发布文章的源，查找标头 ID（例如，`id="blockquote"`），并通过“# + ID”的模式（例如，`#blockquote`）进行链接。

- 例如：[引用标记](#blockquote)

若要链接到同一存储库中 Markdown 文件的标头，请结合使用相对链接和井号标签链接。

- 示例：[注册过程的技术概述](./understand-explore/rms-for-individuals-user-signup.md#technical-overview-of-the-sign-up-process)

若要链接到外部文件，请使用完整的 URL 作为链接。

- 例如：[Github](http://www.github.com)

Markdown 文件中的 URL 会转换为可单击链接。

- 示例： http://www.github.com

## <a name="lists"></a>列表

### <a name="ordered-lists"></a>经过排序的列表

1. 这 
1. 是
1. 在此视图中，
1. 经过排序的
1. 列表  


#### <a name="ordered-list-with-an-embedded-list"></a>带有嵌入式列表、经过排序的列表

1. 此处
1. 为
1. 一个
1. 嵌入
    1. Scarlett 小姐
    1. Plum 教授
1. 经过排序的
1. 列表


### <a name="unordered-lists"></a>未经排序的列表

- 此
- 是
- a
- 项目符号
- 列表


#### <a name="unordered-list-with-an-embedded-lists"></a>带有嵌入式列表、未经排序的列表

- 此 
- 项目符号 
- 列表
  - Peacock 太太
  - Green 先生
- 包含  
- other
    1. Mustard 上校
    1. White 夫人
- 列表


## <a name="horizontal-rule"></a>水平标尺

---

## <a name="tables"></a>表

| 表        | 是           | 酷  |
| ------------- |:-------------:| -----:|
| 第 3 列是      | 右对齐 | $1600 |
| 第 2 列是      | 居中对齐      |   $12 |
| 第 1 列是默认 | 左对齐     |    $1 |


## <a name="code"></a>代码

### <a name="codeblock"></a>代码块

    function fancyAlert(arg) {
      if(arg) {
        $.docs({div:'#foo'})
      }
    }

### <a name="in-line-code"></a>内联代码

这是 `in-line code` 示例。

## <a name="blockquotes"></a>引用标记

> 干旱持续至今，长达一千万年之久，可怕的蜥蜴的极盛时代已结束很久。 在赤道的这个大陆（后来被称为“非洲”）上，生存大战的凶残程度已达到新的高潮，但胜利者仍是未知。 在这片贫瘠干涸的土地上，只有小巧、敏捷或凶猛的生物才可能繁衍生息，甚至才可能抱有生存下去的期望。

## <a name="images"></a>图像

### <a name="static-image"></a>静态图像

![这是替换文字](./media/AzRMS_elements.png)

### <a name="linked-image"></a>链接图像

[![链接图像的替换文字](./media/AzRMS_elements.png)](https://azure.microsoft.com) 

### <a name="animated-gif"></a>动画 GIF

![动画 GIF](./media/hololens.gif)

## <a name="alerts"></a>警报

### <a name="note"></a>备注

> [!NOTE]
> 这是说明

### <a name="warning"></a>警告

> [!WARNING]
> 这是警告

### <a name="tip"></a>提示

> [!TIP]
> 这是提示

### <a name="important"></a>重要

> [!IMPORTANT]
> 这是重要事项

## <a name="videos"></a>视频

### <a name="channel-9"></a>第 9 频道

<iframe src="http://channel9.msdn.com/Series/Azure-Active-Directory-Videos-Demos/Azure-Active-Directory-Connect-Express-Settings/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>


### <a name="youtube"></a>Youtube

<iframe width="420" height="315" src="https://www.youtube.com/embed/R6_eWWfNB54" frameborder="0" allowfullscreen></iframe>

## <a name="docsms-extensions"></a>docs.ms 扩展

### <a name="button"></a>按钮

> [!div class="button"]
[按钮链接](/rights-management)

### <a name="selector"></a>选择器

> [!div class="op_single_selector"]
- [foo](/rights-management/template.md)
- [栏](/rights-management/scratch.md)

### <a name="step-by-step"></a>分步说明

>[!div class="step-by-step"]
[上一步](https://www.example.com)
[下一步](https://www.example.com)
