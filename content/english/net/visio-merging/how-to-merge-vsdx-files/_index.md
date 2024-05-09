---
title: How to Merge VSDX Files with GroupDocs.Merger for .NET
linktitle: How to Merge VSDX Files with GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: Learn how to merge VSDX files programmatically using GroupDocs.Merger for .NET. This tutorial provides step-by-step instructions with code samples.
type: docs
weight: 12
url: /net/visio-merging/how-to-merge-vsdx-files/
---
## Introduction
In this tutorial, you'll learn how to merge VSDX (Visio Drawing) files using GroupDocs.Merger for .NET. GroupDocs.Merger for .NET is a powerful API that allows you to manipulate and merge various document formats seamlessly within your .NET applications.
## Prerequisites
Before you begin, ensure you have the following:
- Visual Studio: Make sure you have Visual Studio installed on your system.
- GroupDocs.Merger for .NET: Download and install GroupDocs.Merger for .NET from the [download page](https://releases.groupdocs.com/merger/net/).
- Basic Knowledge of C#: Familiarity with C# programming language and .NET development.

## Import Namespaces
Before you start coding, include the necessary namespaces in your C# file:
```csharp
using System;
using System.IO;
```
## Step 1: Set Up the Output Folder
Begin by specifying the directory where you want to save the merged VSDX file.
```csharp
string outputFolder = "Your Output Directory";
```
## Step 2: Specify the Output File Path
Define the path for the merged VSDX file using the `Path.Combine` method.
```csharp
string outputFile = Path.Combine(outputFolder, "merged.vsdx");
```
## Step 3: Load and Merge VSDX Files
Initialize the `Merger` object with the source VSDX file.
```csharp
using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_VSDX))
{
    // Add another VSDX file to merge
    merger.Join(Constants.SAMPLE_VSDX_2);
    
    // Merge VSDX files and save the result
    merger.Save(outputFile);
}
```
## Step 4: Display Completion Message
Finally, display a message confirming that the VSDX files have been successfully merged.
```csharp
Console.WriteLine("\nVSDX files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusion
In this tutorial, you've learned how to merge VSDX files using GroupDocs.Merger for .NET. You can now integrate this functionality into your .NET applications to combine multiple Visio files efficiently.

## FAQ's
### Can GroupDocs.Merger for .NET merge other document formats besides VSDX?
Yes, GroupDocs.Merger supports merging various formats including PDF, Word, Excel, PowerPoint, and more.
### Is GroupDocs.Merger for .NET compatible with .NET Core?
Yes, GroupDocs.Merger for .NET is compatible with .NET Core along with traditional .NET Framework.
### Where can I find detailed documentation for GroupDocs.Merger for .NET?
Refer to the comprehensive [documentation](https://reference.groupdocs.com/merger/net/) for GroupDocs.Merger for .NET.
### How can I obtain a temporary license for GroupDocs.Merger for .NET?
You can get a temporary license from the [temporary license page](https://purchase.groupdocs.com/temporary-license/).
### What support options are available for GroupDocs.Merger for .NET?
Visit the [GroupDocs forum](https://forum.groupdocs.com/c/merger/32) to get community support and assistance.
