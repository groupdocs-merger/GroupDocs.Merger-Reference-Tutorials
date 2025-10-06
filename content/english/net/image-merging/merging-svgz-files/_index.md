---
title: Merging SVGZ Files
linktitle: Merging SVGZ Files
second_title: GroupDocs.Merger .NET API
description: Learn how to merge SVGZ files using GroupDocs.Merger for .NET with this step-by-step tutorial. Enhance your document manipulation skills.
weight: 14
url: /net/image-merging/merging-svgz-files/
type: docs
---
# Merging SVGZ Files

## Introduction
In this tutorial, we will explore how to merge SVGZ (Scalable Vector Graphics) files using GroupDocs.Merger for .NET. GroupDocs.Merger is a powerful document manipulation API that allows developers to perform various operations on different document formats, including merging, splitting, and rearranging pages.
## Prerequisites
Before you begin, ensure you have the following:
- Visual Studio: Install Visual Studio IDE on your system.
- GroupDocs.Merger for .NET: Download and include the GroupDocs.Merger library in your project. You can find the download [here](https://releases.groupdocs.com/merger/net/).
- Basic understanding of C#: Familiarity with C# programming language.

## Import Namespaces
First, include the necessary namespaces for accessing GroupDocs.Merger functionalities:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```

Now, let's break down the process of merging SVGZ files using GroupDocs.Merger into simple steps:
## Step 1: Define Output Directory and File
Begin by specifying the directory where the merged file will be saved:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.svgz");
```
Replace `"Your Output Directory"` with the desired path on your system.
## Step 2: Load the Source SVGZ File
Use GroupDocs.Merger to load the source SVGZ file:
```csharp
using (var merger = new Merger("Your Sample File"))
{
    // Define image join options with vertical join mode
    var joinOptions = new ImageJoinOptions(ImageJoinMode.Vertical);
    // Add another SVGZ file to merge
    merger.Join("Your Sample File", joinOptions);
    // Merge SVGZ files and save result
    merger.Save(outputFile);
}
```
Replace `"Your Sample File"` with the path to your SVGZ file.
## Step 3: Execute the Merge Operation
Execute the merging process and save the merged SVGZ file:
```csharp
Console.WriteLine("\nSVGZ files merge completed successfully. \nCheck output in {0}", outputFolder);
```
This code snippet joins SVGZ files vertically, and the merged file is saved in the specified output directory.

## Conclusion
In this tutorial, we've learned how to merge SVGZ files using GroupDocs.Merger for .NET. By following these steps, you can integrate document merging capabilities into your .NET applications efficiently.

## FAQ's
### Can GroupDocs.Merger handle other file formats besides SVGZ?
Yes, GroupDocs.Merger supports various document formats, including PDF, Word, Excel, PowerPoint, and more.
### Where can I find detailed documentation for GroupDocs.Merger?
Visit the [documentation](https://tutorials.groupdocs.com/merger/net/) for comprehensive information and usage examples.
### Is there a free trial available for GroupDocs.Merger?
Yes, you can access the free trial [here](https://releases.groupdocs.com/).
### How can I get support for GroupDocs.Merger?
Join the [GroupDocs forum](https://forum.groupdocs.com/c/merger/32) to seek assistance and interact with other users.
### Where can I purchase a license for GroupDocs.Merger?
Purchase a license [here](https://purchase.groupdocs.com/buy) or obtain a temporary license [here](https://purchase.groupdocs.com/temporary-license/).
