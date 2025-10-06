---
title: Merge VSTM Files
linktitle: Merge VSTM Files
second_title: GroupDocs.Merger .NET API
description: Learn how to merge VSTM files effortlessly using GroupDocs.Merger for .NET. Follow our step-by-step tutorial and your document manipulation capabilities.
weight: 15
url: /net/visio-merging/merge-vstm-files/
type: docs
---
# Merge VSTM Files

## Introduction
In this tutorial, we will explore how to merge VSTM (VSTemplate) files using GroupDocs.Merger for .NET. GroupDocs.Merger is a powerful document manipulation API that allows developers to merge, split, and manipulate various document formats seamlessly within their .NET applications.
## Prerequisites
Before you begin, ensure you have the following prerequisites set up:
1. Visual Studio: Install Visual Studio IDE on your development machine.
2. GroupDocs.Merger for .NET: Obtain and install the GroupDocs.Merger for .NET library. You can download it from [here](https://releases.groupdocs.com/merger/net/).
3. .NET Framework: Ensure you have .NET Framework installed (version 4.6.1 or above).
4. Basic Understanding of C#: Familiarity with C# programming language.

## Import Namespaces
Before diving into the code, make sure to import the necessary namespaces in your C# project:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Step 1: Set Output Directory
First, specify the output directory where the merged file will be saved.
```csharp
string outputFolder = "Your Output Directory";
```
## Step 2: Define Output File Path
Combine the output directory with the desired output file name.
```csharp
string outputFile = Path.Combine(outputFolder, "merged.vstm");
```
## Step 3: Load Source VSTM File
Initialize the `Merger` object by loading the source VSTM file.
```csharp
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    // Add another VSTM file to merge
    merger.Join("Your Sample File");
    // Merge VSTM files and save result
    merger.Save(outputFile);
}
```
## Step 4: Merge and Save
Add additional VSTM files to the `Merger` object using the `Join` method, then merge them together and save the result to the specified output file.
```csharp
Console.WriteLine("\nVSTM files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusion
In this tutorial, we have covered the essential steps to merge VSTM files using GroupDocs.Merger for .NET. By following these steps and utilizing the powerful capabilities of the GroupDocs.Merger library, you can efficiently manipulate VSTM files within your .NET applications.

## FAQ's
### Can I merge VSTM files of different formats using GroupDocs.Merger?
Yes, GroupDocs.Merger supports merging VSTM files of various formats seamlessly.
### Is GroupDocs.Merger compatible with .NET Core applications?
Yes, GroupDocs.Merger is compatible with both .NET Framework and .NET Core.
### How can I obtain a temporary license for GroupDocs.Merger?
You can acquire a temporary license for GroupDocs.Merger from [here](https://purchase.groupdocs.com/temporary-license/).
### Does GroupDocs.Merger support merging encrypted VSTM files?
Yes, GroupDocs.Merger can handle encrypted VSTM files during the merging process.
### Where can I find additional support for GroupDocs.Merger?
For additional support, visit the [GroupDocs.Merger forum](https://forum.groupdocs.com/c/merger/32) to engage with the community and seek assistance.
