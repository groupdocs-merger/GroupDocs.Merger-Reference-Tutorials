---
title: How to Merge XLSB Files with GroupDocs.Merger for .NET
linktitle: How to Merge XLSB Files with GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: Learn how to merge XLSB files using GroupDocs.Merger for .NET. This step-by-step guide simplifies document manipulation tasks.
type: docs
weight: 12
url: /net/spreadsheet-merging/how-to-merge-xlsb-files-groupdocs-merger-dotnet/
---
## Introduction
In this tutorial, we'll explore how to merge XLSB (Excel Binary Workbook) files using GroupDocs.Merger for .NET. GroupDocs.Merger for .NET is a powerful document manipulation API that allows developers to merge, split, and manipulate various document formats seamlessly within their .NET applications. Specifically, we'll focus on merging XLSB files using this versatile library.
## Prerequisites
Before we dive into the tutorial, ensure you have the following prerequisites set up:
- Visual Studio installed on your system.
- Basic knowledge of C# programming.
- GroupDocs.Merger for .NET library downloaded and referenced in your project.
  

## Import Namespaces
Before you begin coding, import the necessary namespaces into your C# project:
```csharp
using System;
using System.IO;
```
## Step 1: Set Up Your Output Directory
```csharp
string outputFolder = "Your Output Directory";
```
## Step 2: Define the Output File Path
```csharp
string outputFile = Path.Combine(outputFolder, "merged.xlsb");
```
## Step 3: Load the Source XLSB File
```csharp
// Load the source XLSB file
using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_XLSB))
{
    // Add another XLSB file to merge
    merger.Join(Constants.SAMPLE_XLSB_2);
    // Merge XLSB files and save result
    merger.Save(outputFile);
}
```
## Step 4: Display Merge Completion Message
```csharp
Console.WriteLine("\nXLSB files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusion
By following these steps, you can easily merge XLSB files using GroupDocs.Merger for .NET. This API simplifies document manipulation tasks and offers seamless integration into your .NET applications.

## FAQ's
### Can GroupDocs.Merger handle other file formats besides XLSB?
Yes, GroupDocs.Merger supports a wide range of document formats including DOCX, PDF, XLSX, PPTX, and more.
### Where can I find more documentation for GroupDocs.Merger?
Visit the [documentation](https://reference.groupdocs.com/merger/net/) for detailed usage instructions and API references.
### Is there a free trial available for GroupDocs.Merger?
Yes, you can access a [free trial](https://releases.groupdocs.com/) to explore the features of GroupDocs.Merger.
### How can I get technical support for GroupDocs.Merger?
Join the [GroupDocs forum](https://forum.groupdocs.com/c/merger/32) to ask questions and interact with the community.
### Where can I purchase a license for GroupDocs.Merger?
You can buy a license from the [purchase page](https://purchase.groupdocs.com/buy).
