---
title: How to Merge 7z Files
linktitle: How to Merge 7z Files
second_title: GroupDocs.Merger .NET API
description: Effortlessly merge 7z files using GroupDocs.Merger for .NET. Follow our step-by-step guide to combine multiple archives into one seamlessly.
weight: 10
url: /net/merge-compress-files/merge-7z-files/
---
## Introduction
Merging 7z files can be efficiently done using GroupDocs.Merger for .NET, a powerful document manipulation library. This tutorial will guide you through the process step by step, allowing you to seamlessly merge your 7z files with ease.
## Prerequisites
Before you begin, ensure you have the following:
- Visual Studio installed on your system.
- GroupDocs.Merger for .NET library installed. You can download it from [here](https://releases.groupdocs.com/merger/net/).
- Basic understanding of C# programming.

## Import Namespaces
First, include the necessary namespaces in your C# code:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Step 1: Load Source 7Z File
Begin by specifying the output directory and file name for the merged 7z file:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.7z");
```
## Step 2: Merge 7Z Files
Load the source 7Z file and add another 7Z file that you wish to merge:
```csharp
using (var merger = new Merger("Your Sample File"))
{
    merger.Join("Your Sample File");
    merger.Save(outputFile);
}
```
## Step 3: Save Merged 7Z File
Execute the merge operation and save the resulting merged 7Z file:
```csharp
Console.WriteLine("\n7Z files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusion
In this tutorial, we explored how to merge 7z files using GroupDocs.Merger for .NET. By following these straightforward steps, you can efficiently combine multiple 7z files into a single, unified archive.

## FAQ's
### Can I merge more than two 7z files using GroupDocs.Merger?
Yes, you can merge any number of 7z files together using this library. Simply add each file using the `Join` method.
### Is GroupDocs.Merger for .NET compatible with other archive formats?
Yes, GroupDocs.Merger supports merging various document formats, including archives like ZIP, 7z, and RAR.
### Where can I find additional support or assistance with GroupDocs.Merger?
For further assistance, visit the [GroupDocs.Merger forum](https://forum.groupdocs.com/c/merger/32).
### Can I try GroupDocs.Merger for .NET before purchasing?
Yes, you can explore the functionalities of GroupDocs.Merger by downloading the [free trial version](https://releases.groupdocs.com/).
### How can I obtain a temporary license for GroupDocs.Merger?
If you require a temporary license, visit [here](https://purchase.groupdocs.com/temporary-license/).
