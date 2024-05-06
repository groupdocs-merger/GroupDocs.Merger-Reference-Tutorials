---
title: Guide to Merging VSSM Files using GroupDocs.Merger for .NET
linktitle: Guide to Merging VSSM Files using GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: 
type: docs
weight: 13
url: /net/visio-merging/guide-merging-vssm-files/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Merger.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to merge multiple VSSM files into single file.
    /// For more details about merging Microsoft Visio Macro Enabled File Format (.vssm) files please check this documentation article 
    /// https://docs.groupdocs.com/merger/net/merge/vssm
    /// </summary>
    internal static class MergeVssm
    {
        public static void Run()
        {
            Console.WriteLine("=======================================================================");
            Console.WriteLine();
            Console.WriteLine("Example Basic Usage: MergeVssm");
            Console.WriteLine();

            string outputFolder = "Your Output Directory";
            string outputFile = Path.Combine(outputFolder, "merged.vssm");
            
            // Load the source VSSM file
            using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_VSSM))
            {
                // Add another VSSM file to merge
                merger.Join(Constants.SAMPLE_VSSM_2);
                // Merge VSSM files and save result
                merger.Save(outputFile);
            }

            Console.WriteLine("\nVSSM files merge completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}

            
            
```
