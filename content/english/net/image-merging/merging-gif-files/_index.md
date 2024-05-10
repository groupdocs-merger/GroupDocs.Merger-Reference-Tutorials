---
title: Merging GIF Files
linktitle: Merging GIF Files
second_title: GroupDocs.Merger .NET API
description: Learn how to merge GIF files using GroupDocs.Merger for .NET. Combine multiple GIFs programmatically with step-by-step instructions.
type: docs
weight: 11
url: /net/image-merging/merging-gif-files/
---
## Introduction
In this tutorial, you will learn how to merge GIF files using GroupDocs.Merger for .NET. GroupDocs.Merger is a powerful API that allows developers to manipulate document formats programmatically. By following the steps outlined below, you'll be able to efficiently merge multiple GIF files into a single output GIF file.
## Prerequisites
Before you begin, ensure you have the following prerequisites set up:
1. Development Environment: Install Visual Studio or any other preferred IDE for .NET development.
2. GroupDocs.Merger Library: Obtain and set up the GroupDocs.Merger library for .NET. You can download the library from [here](https://releases.groupdocs.com/merger/net/).
3. Input GIF Files: Prepare the GIF files that you want to merge.

## Import Namespaces
First, import the necessary namespaces into your .NET project:
```csharp
using System;
using System.IO;
```
## Step 1: Set Up Output Directory
```csharp
string outputFolder = "Your Output Directory";
```
Ensure to replace `"Your Output Directory"` with the path where you want to save the merged GIF file.
## Step 2: Define Output File Path
```csharp
string outputFile = Path.Combine(outputFolder, "merged.gif");
```
This step defines the full path and filename for the merged GIF output.
## Step 3: Load Source GIF File
```csharp
using (var merger = new Merger(Constants.SAMPLE_GIF))
{
    // Define image join options with vertical join mode
    var joinOptions = new ImageJoinOptions(ImageJoinMode.Vertical);
    // Add another GIF file to merge
    merger.Join(Constants.SAMPLE_GIF, joinOptions);
    // Merge GIF files and save result
    merger.Save(outputFile);
}
Console.WriteLine("\nGIF files merge completed successfully. \nCheck output in {0}", outputFolder);
```
Here's a breakdown of the code:
- `using (var merger = new Merger(Constants.SAMPLE_GIF))`: Load the source GIF file.
- `var joinOptions = new ImageJoinOptions(ImageJoinMode.Vertical)`: Define image join options with a vertical join mode.
- `merger.Join(Constants.SAMPLE_GIF, joinOptions)`: Add another GIF file to merge.
- `merger.Save(outputFile)`: Merge GIF files and save the result to `outputFile`.
- `Console.WriteLine(...)`: Display a success message along with the output folder path.

## Conclusion
By following this tutorial, you've learned how to merge GIF files using GroupDocs.Merger for .NET. This process enables you to efficiently combine multiple GIF files into a single output file, enhancing your document manipulation capabilities programmatically.

## FAQ's
### Q: Can GroupDocs.Merger for .NET be used to merge other file formats?
Yes, GroupDocs.Merger supports merging various document formats, including PDF, Word, Excel, PowerPoint, and more.
### Q: Is a license required to use GroupDocs.Merger for .NET?
Yes, you need a valid license to use GroupDocs.Merger in production. However, you can start with a free trial by visiting [here](https://releases.groupdocs.com/).
### Q: How can I get technical support for GroupDocs.Merger?
For technical assistance, visit the GroupDocs.Merger [forum](https://forum.groupdocs.com/c/merger/32) where you can ask questions and engage with the community.
### Q: Where can I find detailed documentation for GroupDocs.Merger for .NET?
Explore the comprehensive documentation [here](https://reference.groupdocs.com/merger/net/) for detailed insights into using GroupDocs.Merger in your .NET applications.
### Q: Can I obtain a temporary license for GroupDocs.Merger?
Yes, you can obtain a temporary license from [here](https://purchase.groupdocs.com/temporary-license/) to evaluate GroupDocs.Merger's capabilities before purchasing.
