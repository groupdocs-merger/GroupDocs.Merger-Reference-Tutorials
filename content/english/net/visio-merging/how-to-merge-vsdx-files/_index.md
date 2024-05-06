---
title: How to Merge VSDX Files with GroupDocs.Merger for .NET
linktitle: How to Merge VSDX Files with GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: 
type: docs
weight: 12
url: /net/visio-merging/how-to-merge-vsdx-files/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Merger.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to merge multiple VSDX files into single file.
    /// For more details about merging Microsoft Visio File Format (.vsdx) files please check this documentation article 
    /// https://docs.groupdocs.com/merger/net/merge/vsdx
    /// </summary>
    internal static class MergeVsdx
    {
        public static void Run()
        {
            Console.WriteLine("=======================================================================");
            Console.WriteLine();
            Console.WriteLine("Example Basic Usage: MergeVsdx");
            Console.WriteLine();

            string outputFolder = "Your Output Directory";
            string outputFile = Path.Combine(outputFolder, "merged.vsdx");
            
            // Load the source VSDX file
            using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_VSDX))
            {
                // Add another VSDX file to merge
                merger.Join(Constants.SAMPLE_VSDX_2);
                // Merge VSDX files and save result
                merger.Save(outputFile);
            }

            Console.WriteLine("\nVSDX files merge completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}

            
            
```
