---
title: Merge PPS Files with GroupDocs.Merger for .NET
linktitle: Merge PPS Files with GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: 
type: docs
weight: 10
url: /net/presentation-merging/merge-pps-files/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Merger.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to merge multiple PPS files into single file.
    /// For more details about merging Microsoft PowerPoint Slide Show (.pps) files please check this documentation article 
    /// https://docs.groupdocs.com/merger/net/merge/pps
    /// </summary>
    internal static class MergePps
    {
        public static void Run()
        {
            Console.WriteLine("=======================================================================");
            Console.WriteLine();
            Console.WriteLine("Example Basic Usage: MergePps");
            Console.WriteLine();

            string outputFolder = "Your Output Directory";
            string outputFile = Path.Combine(outputFolder, "merged.pps");
            
            // Load the source PPS file
            using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_PPS))
            {
                // Add another PPS file to merge
                merger.Join(Constants.SAMPLE_PPS_2);
                // Merge PPS files and save result
                merger.Save(outputFile);
            }

            Console.WriteLine("\nPPS files merge completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}

            
            
```
