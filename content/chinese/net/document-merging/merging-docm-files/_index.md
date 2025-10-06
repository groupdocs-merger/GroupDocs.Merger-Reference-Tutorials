---
title: 合并 DOCM 文件
linktitle: 合并 DOCM 文件
second_title: GroupDocs.Merger .NET API
description: 了解如何使用 GroupDocs.Merger for .NET 无缝合并 DOCM 文件。适用于 .NET 应用程序的简单而高效的文档操作。
weight: 11
url: /zh/net/document-merging/merging-docm-files/
type: docs
---
# 合并 DOCM 文件

## 介绍
在本教程中，我们将探讨如何使用 GroupDocs.Merger for .NET 合并 DOCM（Microsoft Word 宏启用文档）文件。该库提供了强大的文档操作功能，允许开发人员在其 .NET 应用程序中无缝合并、拆分、提取和操作各种文档格式。
## 先决条件
在开始之前，请确保您满足以下先决条件：
- 开发环境：Visual Studio 或任何首选的 .NET 开发环境。
-  GroupDocs.Merger for .NET 库：从以下位置下载该库[这里](https://releases.groupdocs.com/merger/net/)并将其包含在您的项目中。
- 示例 DOCM 文件：准备您想要合并的 DOCM 文件。
  

## 导入命名空间
首先，在 C# 项目中包含使用 GroupDocs.Merger 所需的命名空间：
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```

让我们将合并过程分解为简单的步骤：
## 步骤 1：设置输出目录
定义保存合并文件的输出目录：
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.docm");
```
代替`"Your Output Directory"`以及要保存合并的 DOCM 文件的路径。
## 第 2 步：加载并合并 DOCM 文件
加载源 DOCM 文件并使用 GroupDocs.Merger 将它们合并在一起：
```csharp
//加载源DOCM文件
using (var merger = new GroupDocs.Merger.Merger("Your Sample Document File"M))
{
    //添加另一个 DOCM 文件进行合并
    merger.Join("Your Sample Document File"M_2);
    //合并DOCM文件并保存结果
    merger.Save(outputFile);
}
```
在此代码中：
- `"Your Sample Document File"M`和`"Your Sample Document File"M_2`是输入 DOCM 文件的占位符。
- `merger.Join(...)`将另一个 DOCM 文件添加到合并过程中。
- `merger.Save(outputFile)`将合并的 DOCM 文件保存到指定位置。
## 第 3 步：显示完成消息
最后，显示一条消息以确认合并操作成功：
```csharp
Console.WriteLine("\nDOCM files merge completed successfully. \nCheck output in {0}", outputFolder);
```
此消息通知用户合并过程已成功完成以及合并文件的位置。

## 结论
在本教程中，我们介绍了如何使用 GroupDocs.Merger for .NET 合并 DOCM 文件。此库简化了复杂的文档操作任务，为开发人员提供了一套强大的工具，可以在其 .NET 应用程序中无缝处理各种文档格式。

### 常见问题解答
#### 1. 除了 DOCM 之外，GroupDocs.Merger 还能处理其他文档格式吗？
是的，GroupDocs.Merger 支持多种文档格式，包括 DOCX、PDF、XLSX、PPTX 等。
#### 2. 如何获得 GroupDocs.Merger 的临时许可证？
您可以从申请临时许可证[这里](https://purchase.groupdocs.com/temporary-license/).
#### 3. 在哪里可以找到对 GroupDocs.Merger 的额外支持？
如需更多支持和讨论，请访问[GroupDocs.Merger 论坛](https://forum.groupdocs.com/c/merger/32).
#### 4. GroupDocs.Merger 与 .NET Core 应用程序兼容吗？
是的，GroupDocs.Merger 与 .NET Framework 和 .NET Core 应用程序兼容。
#### 5. 购买之前我可以测试 GroupDocs.Merger 吗？
是的，您可以探索免费试用版[这里](https://releases.groupdocs.com/).