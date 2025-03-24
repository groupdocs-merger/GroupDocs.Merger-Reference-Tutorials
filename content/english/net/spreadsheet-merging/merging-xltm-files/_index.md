---
title: Merging XLTM Files
linktitle: Merging XLTM Files
second_title: GroupDocs.Merger .NET API
description: Learn how to merge XLTM files programmatically. Step-by-step guide with code examples.
weight: 16
url: /net/spreadsheet-merging/merging-xltm-files/
---

# Merging XLTM Files

## Introduction
In this tutorial, we will explore how to merge XLTM (Excel Macro-Enabled Template) files. GroupDocs.Merger for .NET is a powerful library that enables developers to manipulate and merge various document formats programmatically. This guide will walk you through the process of merging XLTM files step by step using C#.
## Prerequisites
Before getting started, ensure you have the following prerequisites in place:
- Visual Studio installed on your system.
- Basic knowledge of C# programming.
- GroupDocs.Merger for .NET library installed. You can download it from [here](https://releases.groupdocs.com/merger/net/).
- Access to XLTM files that you want to merge.

## Import Namespaces
Begin by importing the necessary namespaces into your C# project.
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```

Now, let's dive into merging XLTM files.
## Step 1: Initialize Output Directory
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.xltm");
```
Replace `"Your Output Directory"` with the path where you want to save the merged XLTM file.
## Step 2: Merge XLTM Files
```csharp
// Load the source XLTM file
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    // Add another XLTM file to merge
    merger.Join("Your Sample File");
    // Merge XLTM files and save result
    merger.Save(outputFile);
}
```
In this code snippet:
- "Your Sample File" and "Your Sample File" represent the paths to your input XLTM files. Ensure to replace these with the actual file paths.
## Step 3: Display Output Location
```csharp
Console.WriteLine("\nXLTM files merge completed successfully. \nCheck output in {0}", outputFolder);
```
This code will display a message indicating the successful completion of the merge operation along with the output directory path.

## Conclusion
By following this tutorial, you've learned how to merge XLTM files. This library offers extensive capabilities for document manipulation, providing developers with a robust toolset for handling document-related tasks programmatically.

## FAQ's
### Can GroupDocs.Merger merge other document formats besides XLTM?
Yes, GroupDocs.Merger supports merging various document formats such as DOCX, XLSX, PPTX, PDF, and more.
### Does GroupDocs.Merger require a license for commercial use?
Yes, you will need a valid license to use GroupDocs.Merger in a commercial environment. You can obtain a license [here](https://purchase.groupdocs.com/buy).
### Is there a free trial available for GroupDocs.Merger?
Yes, you can access a free trial of GroupDocs.Merger [here](https://releases.groupdocs.com/).
### Where can I find documentation for GroupDocs.Merger?
You can refer to the complete documentation for GroupDocs.Merger [here](https://tutorials.groupdocs.com/merger/net/).
### Where can I get technical support for GroupDocs.Merger?
For technical assistance and support, visit the GroupDocs.Merger forum [here](https://forum.groupdocs.com/c/merger/32).