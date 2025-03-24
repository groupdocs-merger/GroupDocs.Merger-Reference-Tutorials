---
title: 使用 GroupDocs.Merger for .NET 合并 DOC 文件
linktitle: 使用 GroupDocs.Merger for .NET 合并 DOC 文件
second_title: GroupDocs.Merger .NET API
description: 了解如何使用 GroupDocs.Merger for .NET 以编程方式合并 DOC 文件。按照我们的分步指南将多个文档无缝合并为一个。
weight: 10
url: /zh/net/document-merging/merge-doc-files/
---
## 介绍
在本教程中，我们将探讨如何使用 GroupDocs.Merger for .NET 合并 DOC 文件。 GroupDocs.Merger for .NET 是一个功能强大的 API，允许开发人员以编程方式组合、拆分和操作各种文档格式。通过利用此 API，您可以将多个 DOC 文件无缝合并到一个文档中。我们将提供分步说明，指导您完成使用 GroupDocs.Merger for .NET 合并 DOC 文件的过程。
## 先决条件
在开始之前，请确保您已设置以下先决条件：
1. Visual Studio：在您的开发机器上安装 Visual Studio。
2.  GroupDocs.Merger for .NET：获取 GroupDocs.Merger for .NET 库。您可以从[网站](https://releases.groupdocs.com/merger/net/).
3. C# 知识：对 C# 编程语言有基本的了解。
## 导入命名空间
要开始使用 GroupDocs.Merger for .NET，请将必要的命名空间导入到您的 C# 项目中：
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## 步骤 1：设置输出目录
首先指定保存合并的 DOC 文件的输出目录：
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.doc");
```
代替`"Your Output Directory"`使用您想要的输出文件夹的路径。
## 步骤2：加载源DOC文件
接下来，使用 GroupDocs.Merger 加载要合并的源 DOC 文件：
```csharp
using (var merger = new Merger("Your Sample Document File"))
{
    //添加另一个 DOC 文件进行合并
    merger.Join("Your Sample Document File 2");
    //合并 DOC 文件并保存结果
    merger.Save(outputFile);
}
```
在此代码片段中：
- `"Your Sample Document File"`和`"Your Sample Document File 2"`表示您想要合并的 DOC 文件的路径。
- `merger.Join(...)`用于将另一个DOC文件添加到合并操作中。
- `merger.Save(outputFile)`合并已加载的 DOC 文件并将合并的文档保存到指定的输出文件 (`merged.doc`）。
确保更换`"Your Sample Document File"`和`"Your Sample Document File 2"`使用您的 DOC 文件的实际路径。
## 结论
在本教程中，我们介绍了使用 GroupDocs.Merger for .NET 合并 DOC 文件的过程。通过遵循上面概述的步骤，您可以有效地以编程方式将多个 DOC 文件合并为一个文档。GroupDocs.Merger for .NET 提供了一种在 .NET 应用程序中操作文档格式的直接而有效的方式。

## 常见问题解答
### GroupDocs.Merger for .NET 是否可以处理除了 DOC 之外的其他文档格式？
是的，GroupDocs.Merger for .NET 支持合并各种文档格式，例如 DOCX、PDF、XLSX、PPTX 等。
### .NET 的 GroupDocs.Merger 是否与 .NET Core 兼容？
是的，GroupDocs.Merger for .NET 与 .NET Core 和 .NET Framework 兼容。
### GroupDocs.Merger for .NET 是否需要许可证才能用于商业用途？
是的，商业使用需要有效的许可证。您可以从[群组文档](https://purchase.groupdocs.com/buy).
### 我可以免费试用 GroupDocs.Merger for .NET 吗？
是的，您可以通过免费试用探索 GroupDocs.Merger for .NET[这里](https://releases.groupdocs.com/).
### 在哪里可以获得 GroupDocs.Merger for .NET 的技术支持？
如需技术援助和社区支持，请访问[GroupDocs 论坛](https://forum.groupdocs.com/c/merger/32).