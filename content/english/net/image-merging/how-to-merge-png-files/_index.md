---
title: How to Merge PNG Files
linktitle: How to Merge PNG Files
second_title: GroupDocs.Merger .NET API
description: Learn how to merge PNG files using GroupDocs.Merger for .NET. Step-by-step guide for seamless integration in your .NET applications.
type: docs
weight: 12
url: /net/image-merging/how-to-merge-png-files/
---
## Introduction
In this tutorial, we'll learn how to merge PNG files using GroupDocs.Merger for .NET. GroupDocs.Merger is a powerful library that allows developers to manipulate and combine various document formats seamlessly. By following this guide, you'll be able to merge PNG files effortlessly within your .NET applications.
## Prerequisites
Before diving into the tutorial, ensure you have the following:
1. Visual Studio: Make sure you have Visual Studio installed on your development machine.
2. GroupDocs.Merger for .NET: Download and install the GroupDocs.Merger library from the [website](https://releases.groupdocs.com/merger/net/).
3. Basic Understanding of C#: Familiarity with C# programming language and .NET environment.

## Import Namespaces
Begin by importing the necessary namespaces into your C# project:
```csharp
using System;
using System.IO;
```
## Step 1: Load Source PNG Files
First, define the output directory and path for the merged PNG file:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.png");
```
## Step 2: Merge PNG Files
Load the source PNG files and merge them together:
```csharp
using (var merger = new Merger(Constants.SAMPLE_PNG))
{
    // Define image join options with horizontal join mode
    var joinOptions = new ImageJoinOptions(ImageJoinMode.Horizontal);
    
    // Add another PNG file to merge
    merger.Join(Constants.SAMPLE_PNG, joinOptions);
    
    // Merge PNG files and save result
    merger.Save(outputFile);
}
```
## Step 3: Output Merged PNG File
Finally, display a success message and provide the path to the merged PNG file:
```csharp
Console.WriteLine("\nPNG files merge completed successfully. \nCheck output in {0}", outputFolder);
```
Congratulations! You have successfully merged PNG files using GroupDocs.Merger for .NET. Feel free to explore more features and functionalities offered by GroupDocs.Merger to enhance your document processing capabilities.


## Conclusion
In this tutorial, we covered the process of merging PNG files using GroupDocs.Merger for .NET. By following the outlined steps, you can seamlessly integrate document manipulation functionalities into your .NET applications.
## FAQ's
### Is GroupDocs.Merger compatible with other image formats besides PNG?
Yes, GroupDocs.Merger supports a wide range of document and image formats including JPG, TIFF, PDF, DOCX, and more.
### Can I customize the merging options such as orientation or layout?
Absolutely! GroupDocs.Merger offers various options to control how documents and images are merged, allowing for flexible customization.
### Where can I find more resources and support for GroupDocs.Merger?
Visit the [GroupDocs.Merger forum](https://forum.groupdocs.com/c/merger/32) for community support and explore the [documentation](https://reference.groupdocs.com/merger/net/) for detailed guidance.
### Is there a trial version available to test GroupDocs.Merger before purchasing?
Yes, you can download a free trial from the [GroupDocs website](https://releases.groupdocs.com/) to evaluate the library's capabilities.
### How can I obtain a temporary license for GroupDocs.Merger?
Get a temporary license from the [GroupDocs purchase page](https://purchase.groupdocs.com/temporary-license/) to unlock additional features during the trial period.
