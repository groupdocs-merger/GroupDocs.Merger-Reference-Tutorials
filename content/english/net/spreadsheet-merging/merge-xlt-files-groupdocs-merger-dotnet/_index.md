---
title: Merge XLT Files using GroupDocs.Merger for .NET
linktitle: Merge XLT Files using GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: 
type: docs
weight: 15
url: /net/spreadsheet-merging/merge-xlt-files-groupdocs-merger-dotnet/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Merger.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to merge multiple XLT files into single file.
    /// For more details about merging Microsoft Excel Template (.xlt) files please check this documentation article 
    /// https://docs.groupdocs.com/merger/net/merge/xlt
    /// </summary>
    internal static class MergeXlt
    {
        public static void Run()
        {
            Console.WriteLine("=======================================================================");
            Console.WriteLine();
            Console.WriteLine("Example Basic Usage: MergeXlt");
            Console.WriteLine();

            string outputFolder = "Your Output Directory";
            string outputFile = Path.Combine(outputFolder, "merged.xlt");
            
            // Load the source XLT file
            using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_XLT))
            {
                // Add another XLT file to merge
                merger.Join(Constants.SAMPLE_XLT_2);
                // Merge XLT files and save result
                merger.Save(outputFile);
            }

            Console.WriteLine("\nXLT files merge completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}

            
            
```
