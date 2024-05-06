---
title: Merging XLSX Files with GroupDocs.Merger for .NET
linktitle: Merging XLSX Files with GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: 
type: docs
weight: 14
url: /net/spreadsheet-merging/merging-xlsx-files-groupdocs-merger-dotnet/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Merger.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to merge multiple XLSX files into single file.
    /// For more details about merging Microsoft Excel Open XML Spreadsheet (.xlsx) files please check this documentation article 
    /// https://docs.groupdocs.com/merger/net/merge/xlsx
    /// </summary>
    internal static class MergeXlsx
    {
        public static void Run()
        {
            Console.WriteLine("=======================================================================");
            Console.WriteLine();
            Console.WriteLine("Example Basic Usage: MergeXlsx");
            Console.WriteLine();

            string outputFolder = "Your Output Directory";
            string outputFile = Path.Combine(outputFolder, "merged.xlsx");
            
            // Load the source XLSX file
            using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_XLSX))
            {
                // Add another XLSX file to merge
                merger.Join(Constants.SAMPLE_XLSX_2);
                // Merge XLSX files and save result
                merger.Save(outputFile);
            }

            Console.WriteLine("\nXLSX files merge completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}

            
            
```
