---
title: 如何合并 VSDX 文件
linktitle: 如何合并 VSDX 文件
second_title: GroupDocs.Merger .NET API
description: 了解如何使用 GroupDocs.Merger for .NET 以编程方式合并 VSDX 文件。本教程提供了带有代码示例的分步说明。
weight: 12
url: /zh/net/visio-merging/how-to-merge-vsdx-files/
---

# 如何合并 VSDX 文件

## 介绍
在本教程中，您将学习如何使用 GroupDocs.Merger for .NET 合并 VSDX（Visio 绘图）文件。GroupDocs.Merger for .NET 是一个功能强大的 API，可让您在 .NET 应用程序中无缝操作和合并各种文档格式。
## 先决条件
在开始之前，请确保您具备以下条件：
- Visual Studio：确保您的系统上安装了 Visual Studio。
-  GroupDocs.Merger for .NET：从[下载页面](https://releases.groupdocs.com/merger/net/).
- C#基础知识：熟悉C#编程语言和.NET开发。

## 导入命名空间
在开始编码之前，请在 C# 文件中包括必要的命名空间：
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## 步骤 1：设置输出文件夹
首先指定要保存合并的 VSDX 文件的目录。
```csharp
string outputFolder = "Your Output Directory";
```
## 步骤 2：指定输出文件路径
使用定义合并的 VSDX 文件的路径`Path.Combine`方法。
```csharp
string outputFile = Path.Combine(outputFolder, "merged.vsdx");
```
## 步骤 3：加载和合并 VSDX 文件
初始化`Merger`对象与源 VSDX 文件。
```csharp
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    //添加另一个 VSDX 文件进行合并
    merger.Join("Your Sample File");
    
    //合并 VSDX 文件并保存结果
    merger.Save(outputFile);
}
```
## 步骤 4：显示完成消息
最后，显示一条消息确认 VSDX 文件已成功合并。
```csharp
Console.WriteLine("\nVSDX files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## 结论
在本教程中，您学习了如何使用 GroupDocs.Merger for .NET 合并 VSDX 文件。现在，您可以将此功能集成到 .NET 应用程序中，以高效地合并多个 Visio 文件。

## 常见问题解答
### .NET 的 GroupDocs.Merger 除了可以合并 VSDX 之外还能合并其他文档格式吗？
是的，GroupDocs.Merger 支持合并各种格式，包括 PDF、Word、Excel、PowerPoint 等。
### .NET 的 GroupDocs.Merger 是否与 .NET Core 兼容？
是的，GroupDocs.Merger for .NET 与 .NET Core 以及传统的 .NET Framework 兼容。
### 在哪里可以找到有关 .NET 的 GroupDocs.Merger 的详细文档？
请参阅综合[文档](https://tutorials.groupdocs.com/merger/net/)适用于 .NET 的 GroupDocs.Merger。
### 如何获得 GroupDocs.Merger for .NET 的临时许可证？
您可以从[临时执照页面](https://purchase.groupdocs.com/temporary-license/).
### GroupDocs.Merger for .NET 有哪些支持选项？
参观[GroupDocs 论坛](https://forum.groupdocs.com/c/merger/32)获得社区的支持和帮助。