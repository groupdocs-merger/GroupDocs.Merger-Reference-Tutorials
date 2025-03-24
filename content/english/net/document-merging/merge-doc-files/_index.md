---
title: Merge DOC Files with GroupDocs.Merger for .NET
linktitle: Merge DOC Files with GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: Learn how to merge DOC files programmatically using GroupDocs.Merger for .NET. Follow our step-by-step guide to seamlessly combine multiple documents into one.
weight: 10
url: /net/document-merging/merge-doc-files/
---
## Introduction
In this tutorial, we will explore how to merge DOC files using GroupDocs.Merger for .NET. GroupDocs.Merger for .NET is a powerful API that allows developers to combine, split, and manipulate various document formats programmatically. By leveraging this API, you can seamlessly merge multiple DOC files into a single document. We will provide step-by-step instructions to guide you through the process of merging DOC files using GroupDocs.Merger for .NET.
## Prerequisites
Before we begin, ensure that you have the following prerequisites set up:
1. Visual Studio: Install Visual Studio on your development machine.
2. GroupDocs.Merger for .NET: Obtain the GroupDocs.Merger for .NET library. You can download it from the [website](https://releases.groupdocs.com/merger/net/).
3. Knowledge of C#: Basic understanding of C# programming language.
## Import Namespaces
To start working with GroupDocs.Merger for .NET, import the necessary namespaces into your C# project:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Step 1: Set Up Output Directory
Begin by specifying the output directory where the merged DOC file will be saved:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.doc");
```
Replace `"Your Output Directory"` with the path to your desired output folder.
## Step 2: Load Source DOC Files
Next, load the source DOC files that you want to merge using GroupDocs.Merger:
```csharp
using (var merger = new Merger("Your Sample Document File"))
{
    // Add another DOC file to merge
    merger.Join("Your Sample Document File 2");
    // Merge DOC files and save result
    merger.Save(outputFile);
}
```
In this code snippet:
- `"Your Sample Document File"` and `"Your Sample Document File 2"` represent the paths to the DOC files you wish to merge.
- `merger.Join(...)` is used to add another DOC file to the merge operation.
- `merger.Save(outputFile)` combines the loaded DOC files and saves the merged document to the specified output file (`merged.doc`).
Ensure that you replace `"Your Sample Document File"` and `"Your Sample Document File 2"` with the actual paths to your DOC files.
## Conclusion
In this tutorial, we have covered the process of merging DOC files using GroupDocs.Merger for .NET. By following the steps outlined above, you can effectively combine multiple DOC files into a single document programmatically. GroupDocs.Merger for .NET provides a straightforward and efficient way to manipulate document formats within your .NET applications.

## FAQ's
### Can GroupDocs.Merger for .NET handle other document formats besides DOC?
Yes, GroupDocs.Merger for .NET supports merging various document formats such as DOCX, PDF, XLSX, PPTX, and more.
### Is GroupDocs.Merger for .NET compatible with .NET Core?
Yes, GroupDocs.Merger for .NET is compatible with .NET Core and .NET Framework.
### Does GroupDocs.Merger for .NET require a license for commercial use?
Yes, a valid license is required for commercial usage. You can obtain a license from [GroupDocs](https://purchase.groupdocs.com/buy).
### Can I try GroupDocs.Merger for .NET for free?
Yes, you can explore GroupDocs.Merger for .NET with a free trial available [here](https://releases.groupdocs.com/).
### Where can I get technical support for GroupDocs.Merger for .NET?
For technical assistance and community support, visit the [GroupDocs forum](https://forum.groupdocs.com/c/merger/32).
