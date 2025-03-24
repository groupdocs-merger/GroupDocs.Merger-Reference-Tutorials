---
title: Merge BMP Files
linktitle: Merge BMP Files
second_title: GroupDocs.Merger .NET API
description: Learn how to merge BMP files using GroupDocs.Merger for .NET with this comprehensive tutorial. Develop your .NET applications efficiently.
weight: 10
url: /net/image-merging/merge-bmp-files/
---

# Merge BMP Files

## Introduction
In this tutorial, we'll explore how to merge BMP (Bitmap) files using GroupDocs.Merger for .NET. GroupDocs.Merger is a powerful API that enables developers to manipulate and merge various document formats programmatically within their .NET applications. By the end of this guide, you'll be able to efficiently merge BMP files step by step.
## Prerequisites
Before we begin, ensure you have the following:
- Visual Studio installed on your machine
- Basic knowledge of C# programming
- GroupDocs.Merger for .NET library. You can download it from [here](https://releases.groupdocs.com/merger/net/)
- Access to BMP files that you want to merge
## Import Namespaces
Start by importing the necessary namespaces for using GroupDocs.Merger in your C# project:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
Let's break down the process of merging BMP files into manageable steps:
## Step 1: Set Output Directory and File Name
Define the output directory and the name of the merged BMP file.
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.bmp");
```
## Step 2: Load Source BMP Files
Instantiate the `Merger` object by providing the path to the source BMP file.
```csharp
using (var merger = new Merger("Your Sample File"))
{
    // Define image join options with vertical join mode
    var joinOptions = new ImageJoinOptions(ImageJoinMode.Vertical);
    
    // Add another BMP file to merge
    merger.Join("Your Sample File", joinOptions);
    
    // Merge BMP files and save result
    merger.Save(outputFile);
}
```
## Step 3: Execute and Verify
Execute the code to merge the BMP files and verify the output location.
```csharp
Console.WriteLine("\nBMP files merge completed successfully. \nCheck output in {0}", outputFolder);
```
## Conclusion
In this tutorial, we learned how to merge BMP files using GroupDocs.Merger for .NET. By following the steps outlined above, you can seamlessly integrate BMP merging functionality into your .NET applications.

## FAQ's
### Can I merge BMP files of different dimensions using GroupDocs.Merger?
Yes, GroupDocs.Merger handles BMP files with varying dimensions efficiently during merging.
### Does GroupDocs.Merger support other image formats besides BMP?
Yes, GroupDocs.Merger supports various image formats such as JPEG, PNG, TIFF, and GIF, among others.
### Is GroupDocs.Merger compatible with .NET Core applications?
Yes, GroupDocs.Merger is compatible with both .NET Framework and .NET Core environments.
### Can I customize the merge options for BMP files?
Yes, GroupDocs.Merger provides extensive options to customize merging parameters for BMP files.
### Where can I get support for GroupDocs.Merger-related queries?
You can seek support and engage with the community at [GroupDocs Forum](https://forum.groupdocs.com/c/merger/32).
