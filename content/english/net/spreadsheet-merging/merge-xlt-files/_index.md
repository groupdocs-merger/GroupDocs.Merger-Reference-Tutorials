---
title: Merge XLT Files
linktitle: Merge XLT Files
second_title: GroupDocs.Merger .NET API
description: Learn how to merge XLT files. Combine Excel templates programmatically in C# with this step-by-step guide.
weight: 15
url: /net/spreadsheet-merging/merge-xlt-files/
---
## Introduction
In this tutorial, we'll explore how to merge XLT (Excel Template) files. GroupDocs.Merger is a powerful API that allows developers to manipulate various document formats, including Excel files, programmatically. By merging XLT files, you can combine multiple templates into a single document, streamlining your workflow and enhancing efficiency.
## Prerequisites
Before we begin, ensure you have the following prerequisites:
1. GroupDocs.Merger for .NET: You can download the API from [here](https://releases.groupdocs.com/merger/net/).
2. Development Environment: Install Visual Studio or any compatible IDE.
3. Basic Knowledge of C#: Familiarity with C# programming language and .NET development.

## Import Namespaces
To get started, import the necessary namespaces in your C# project:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Step 1: Set Up the Output Directory
Begin by defining an output directory where the merged XLT file will be saved. Replace `"Your Output Directory"` with your desired path.
```csharp
string outputFolder = "Your Output Directory";
```
## Step 2: Define the Output File Path
Specify the name and path for the merged XLT file within the output directory.
```csharp
string outputFile = Path.Combine(outputFolder, "merged.xlt");
```
## Step 3: Load and Merge XLT Files
Utilize GroupDocs.Merger to load and merge the source XLT files. Here, we'll demonstrate merging two XLT files.
```csharp
// Load the source XLT file
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    // Add another XLT file to merge
    merger.Join("Your Sample File");
    // Merge XLT files and save result
    merger.Save(outputFile);
}
Console.WriteLine("\nXLT files merge completed successfully. \nCheck output in {0}", outputFolder);
```
In this code snippet:
- `"Your Sample File"` and `"Your Sample File"` represent paths to the source XLT files.
- `merger.Join()` is used to add another XLT file for merging.
- `merger.Save()` is called to merge the XLT files and save the result to the specified `outputFile`.

## Conclusion
In this tutorial, we've explored how to merge XLT files. By following these steps, you can efficiently combine multiple Excel templates into a unified document, enhancing document management capabilities within your .NET applications.

## FAQ's
### Can I merge more than two XLT files?
Yes, you can merge multiple XLT files by sequentially adding them using `merger.Join()`.
### Is GroupDocs.Merger compatible with other Excel file formats like XLSX or XLS?
Yes, GroupDocs.Merger supports various Excel file formats, including XLSX, XLS, and XLT.
### Where can I find more examples and documentation for GroupDocs.Merger for .NET?
Detailed documentation and code samples are available [here](https://tutorials.groupdocs.com/merger/net/).
### Is there a trial version of GroupDocs.Merger available for testing?
Yes, you can download a free trial version from [here](https://releases.groupdocs.com/).
### How can I get technical support or assistance with GroupDocs.Merger?
For technical assistance and community support, visit the [GroupDocs.Merger forum](https://forum.groupdocs.com/c/merger/32).
