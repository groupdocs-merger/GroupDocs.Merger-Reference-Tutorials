---
title: Merging VSDM Files
linktitle: Merging VSDM Files
second_title: GroupDocs.Merger .NET API
description: Learn how to merge VSDM files using GroupDocs.Merger for .NET. Simplify your document management tasks with this easy-to-use library.
type: docs
weight: 11
url: /net/visio-merging/merging-vsdm-files/
---
## Introduction
In this tutorial, we'll explore how to merge VSDM (Visio Macro-Enabled Drawing) files using the powerful GroupDocs.Merger for .NET library. This library allows seamless manipulation of various document formats within .NET applications, including merging, splitting, and modifying document properties.
## Prerequisites
Before diving into this tutorial, ensure you have the following prerequisites set up:
- Visual Studio installed on your machine.
- Basic knowledge of C# and .NET framework.
- GroupDocs.Merger for .NET library downloaded and referenced in your project.
- Access to the VSDM files you want to merge.

## Import Namespaces
First, let's import the necessary namespaces into our C# project.
```csharp
using System;
using System.IO;
```
## Step 1: Load Source VSDM Files
Begin by initializing the output directory and specifying the output file path where the merged VSDM file will be saved.
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.vsdm");
```
## Step 2: Merge VSDM Files
Next, use the GroupDocs.Merger library to load and merge the VSDM files. Start by instantiating the `Merger` class with the path to the first VSDM file.
```csharp
using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_VSDM))
{
    // Add another VSDM file to merge
    merger.Join(Constants.SAMPLE_VSDM_2);
    // Merge VSDM files and save result
    merger.Save(outputFile);
}
```
## Step 3: Save Merged File
Execute the merge operation by calling the `Join` method and specifying the path to the second VSDM file. Then, use the `Save` method to save the merged VSDM file to the previously defined output path.

## Conclusion
In this tutorial, we've covered the essential steps to merge VSDM files using GroupDocs.Merger for .NET. This library offers a straightforward way to manipulate various document formats programmatically within .NET applications, enabling you to efficiently merge VSDM files.

## FAQ's
### Can I merge more than two VSDM files simultaneously?
Yes, you can merge multiple VSDM files together by calling the `Join` method for each file you want to merge.
### Does GroupDocs.Merger for .NET support other file formats?
Yes, GroupDocs.Merger supports a wide range of document formats, including PDF, DOCX, XLSX, PPTX, and more.
### Is GroupDocs.Merger for .NET free to use?
GroupDocs.Merger for .NET is a commercial library with both free trial and paid licensing options available.
### How can I handle exceptions while merging files?
You can implement error handling mechanisms around the merge operation to catch and handle exceptions gracefully.
### Where can I find more resources and support for GroupDocs.Merger?
You can visit the [GroupDocs.Merger forum](https://forum.groupdocs.com/c/merger/32) for support, documentation, and community discussions.
