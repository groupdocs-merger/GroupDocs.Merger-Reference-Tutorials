---
title: How to Merge XLSB Files with GroupDocs.Merger for .NET
linktitle: How to Merge XLSB Files with GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: 
type: docs
weight: 12
url: /net/spreadsheet-merging/how-to-merge-xlsb-files-groupdocs-merger-dotnet/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Merger.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to merge multiple XLSB files into single file.
    /// For more details about merging Microsoft Excel Binary Spreadsheet File (.xlsb) files please check this documentation article 
    /// https://docs.groupdocs.com/merger/net/merge/xlsb
    /// </summary>
    internal static class MergeXlsb
    {
        public static void Run()
        {
            Console.WriteLine("=======================================================================");
            Console.WriteLine();
            Console.WriteLine("Example Basic Usage: MergeXlsb");
            Console.WriteLine();

            string outputFolder = "Your Output Directory";
            string outputFile = Path.Combine(outputFolder, "merged.xlsb");
            
            // Load the source XLSB file
            using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_XLSB))
            {
                // Add another XLSB file to merge
                merger.Join(Constants.SAMPLE_XLSB_2);
                // Merge XLSB files and save result
                merger.Save(outputFile);
            }

            Console.WriteLine("\nXLSB files merge completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}

            
            
```
