---
title: 如何合并 7z 文件
linktitle: 如何合并 7z 文件
second_title: GroupDocs.Merger .NET API
description: 使用 GroupDocs.Merger for .NET 轻松合并 7z 文件。按照我们的分步指南将多个档案无缝地合并为一个。
weight: 10
url: /zh/net/merge-compress-files/merge-7z-files/
type: docs
---
# 如何合并 7z 文件

## 介绍
可以使用强大的文档操作库 GroupDocs.Merger for .NET 高效地合并 7z 文件。本教程将逐步指导您完成整个过程，让您轻松无缝地合并 7z 文件。
## 先决条件
在开始之前，请确保您具备以下条件：
- Visual Studio 安装在您的系统上。
- 安装了 .NET 库的 GroupDocs.Merger。您可以从以下位置下载：[这里](https://releases.groupdocs.com/merger/net/).
- 对 C# 编程有基本了解。

## 导入命名空间
首先，在 C# 代码中包含必要的命名空间：
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## 第 1 步：加载源 7Z 文件
首先指定合并的 7z 文件的输出目录和文件名：
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.7z");
```
## 步骤 2：合并 7Z 文件
加载源 7Z 文件并添加您要合并的另一个 7Z 文件：
```csharp
using (var merger = new Merger("Your Sample File"))
{
    merger.Join("Your Sample File");
    merger.Save(outputFile);
}
```
## 步骤 3：保存合并的 7Z 文件
执行合并操作并保存合并后的7Z文件：
```csharp
Console.WriteLine("\n7Z files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## 结论
在本教程中，我们探讨了如何使用 GroupDocs.Merger for .NET 合并 7z 文件。通过执行这些简单的步骤，您可以有效地将多个 7z 文件合并到一个统一的存档中。

## 常见问题解答
### 我可以使用 GroupDocs.Merger 合并两个以上的 7z 文件吗？
是的，您可以使用此库合并任意数量的 7z 文件。只需使用`Join`方法。
### GroupDocs.Merger for .NET 是否与其他档案格式兼容？
是的，GroupDocs.Merger 支持合并各种文档格式，包括 ZIP、7z 和 RAR 等档案。
### 在哪里可以找到有关 GroupDocs.Merger 的更多支持或帮助？
如需进一步帮助，请访问[GroupDocs.Merger 论坛](https://forum.groupdocs.com/c/merger/32).
### 我可以在购买之前试用 GroupDocs.Merger for .NET 吗？
是的，您可以通过下载来探索 GroupDocs.Merger 的功能[免费试用版](https://releases.groupdocs.com/).
### 如何获得 GroupDocs.Merger 的临时许可证？
如果您需要临时许可证，请访问[这里](https://purchase.groupdocs.com/temporary-license/).