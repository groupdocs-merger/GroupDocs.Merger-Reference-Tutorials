---
title: Merging XLS Files
linktitle: Merging XLS Files
second_title: GroupDocs.Merger .NET API
description: Learn how to merge Excel files in .NET using GroupDocs.Merger for seamless document manipulation. Follow our step-by-step tutorial.
weight: 11
url: /net/spreadsheet-merging/merging-xls-files/
---
## Introduction
In this tutorial, we will explore how to merge XLS (Excel) files. GroupDocs.Merger is a powerful document manipulation API that enables developers to merge, split, rearrange, and manipulate documents effortlessly within their .NET applications. Specifically, we will focus on merging XLS files step by step using GroupDocs.Merger's intuitive methods.
## Prerequisites
Before we begin, ensure you have the following prerequisites set up:
- Visual Studio: Install Visual Studio on your machine.
- GroupDocs.Merger for .NET: Download and install GroupDocs.Merger for .NET from [here](https://releases.groupdocs.com/merger/net/).
- .NET Framework: Make sure you have the .NET framework installed.
- Sample XLS Files: Prepare the XLS files you want to merge.

## Import Namespaces
Start by importing the necessary namespaces for using GroupDocs.Merger in your project:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Step 1: Initialize Output Directory
First, specify the directory where you want to save the merged XLS file:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.xls");
```
## Step 2: Load and Merge XLS Files
Now, let's load and merge the XLS files using GroupDocs.Merger:
```csharp
// Load the source XLS file
using (var merger = new Merger("Your Sample File"))
{
    // Add another XLS file to merge
    merger.Join("Your Sample File");
    
    // Merge XLS files and save result
    merger.Save(outputFile);
}
```
## Step 3: Display Output Location
Finally, display a message indicating the completion and location of the merged XLS file:
```csharp
Console.WriteLine("\nXLS files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusion
In this tutorial, we have learned how to merge XLS files. By following the provided steps, you can efficiently combine multiple Excel files programmatically within your .NET applications.

## FAQ's
### Is GroupDocs.Merger compatible with other document formats?
Yes, GroupDocs.Merger supports various document formats such as PDF, DOCX, XLSX, PPTX, and more.
### Can I split documents using GroupDocs.Merger?
Absolutely! GroupDocs.Merger allows you to split documents based on your requirements.
### Where can I find more resources and support for GroupDocs.Merger?
You can explore the documentation and ask questions on the [GroupDocs Forum](https://forum.groupdocs.com/c/merger/32).
### Is there a free trial available for GroupDocs.Merger?
Yes, you can start with a [free trial](https://releases.groupdocs.com/) to evaluate the functionality.
### How can I purchase a license for GroupDocs.Merger?
Visit the [purchase page](https://purchase.groupdocs.com/buy) to acquire a license tailored to your needs.
