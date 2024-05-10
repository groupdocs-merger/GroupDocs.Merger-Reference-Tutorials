---
title: Guide to Merging XLSM Files
linktitle: Guide to Merging XLSM Files
second_title: GroupDocs.Merger .NET API
description: Merge XLSM files seamlessly with GroupDocs.Merger for .NET. Efficiently combine Excel workbooks programmatically. Enhance your document manipulation capabilities.
type: docs
weight: 13
url: /net/spreadsheet-merging/guide-merging-xlsm-files/
---
## Introduction
In this tutorial, we'll explore how to merge XLSM (Excel Macro-Enabled Workbook) files. GroupDocs.Merger is a powerful library that allows developers to manipulate document formats, including merging, splitting, and modifying files programmatically.
## Prerequisites
Before you begin, ensure you have the following:
- GroupDocs.Merger for .NET: Download and install the library from [here](https://releases.groupdocs.com/merger/net/).
- Development Environment: Setup Visual Studio or any compatible .NET development environment.
- XLSM Files: Prepare the XLSM files you want to merge.

## Import Namespaces
First, include the necessary namespaces in your .NET project:
```csharp
using System;
using System.IO;
```
## Step 1: Define Output Folder and File Name
Begin by defining the output folder and the name of the merged XLSM file:
```csharp
string outputFolder = "YourOutputDirectory";
string outputFile = Path.Combine(outputFolder, "merged.xlsm");
```
## Step 2: Load and Merge XLSM Files
Next, load the source XLSM files and merge them into a single file:
```csharp
// Load the source XLSM file
using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_XLSM))
{
    // Add another XLSM file to merge
    merger.Join(Constants.SAMPLE_XLSM_2);
    // Merge XLSM files and save result
    merger.Save(outputFile);
}
```
## Step 3: Check Merge Completion
Finally, notify the user about the successful merge completion and display the output path:
```csharp
Console.WriteLine("\nXLSM files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusion
You've learned how to merge XLSM files programmatically. This library simplifies document manipulation tasks, enabling efficient file merging within your .NET applications.

## FAQ's
### Can GroupDocs.Merger handle large XLSM files?
Yes, GroupDocs.Merger efficiently handles large XLSM files without performance issues.
### Does GroupDocs.Merger support other file formats besides XLSM?
Yes, GroupDocs.Merger supports various document formats like DOCX, PDF, PPTX, and more.
### Is GroupDocs.Merger compatible with .NET Core applications?
Yes, GroupDocs.Merger is compatible with both .NET Framework and .NET Core environments.
### Can I merge encrypted XLSM files using GroupDocs.Merger?
Yes, GroupDocs.Merger supports merging encrypted XLSM files with the correct credentials.
### Does GroupDocs.Merger provide batch processing capabilities?
Yes, GroupDocs.Merger allows batch processing for merging multiple XLSM files simultaneously.
