---
title: How to Merge PPT Files with GroupDocs.Merger for .NET
linktitle: How to Merge PPT Files with GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: 
type: docs
weight: 12
url: /net/presentation-merging/how-to-merge-ppt-files/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Merger.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to merge multiple PPT files into single file.
    /// For more details about merging PowerPoint Presentation (.ppt) files please check this documentation article 
    /// https://docs.groupdocs.com/merger/net/merge/ppt
    /// </summary>
    internal static class MergePpt
    {
        public static void Run()
        {
            Console.WriteLine("=======================================================================");
            Console.WriteLine();
            Console.WriteLine("Example Basic Usage: MergePpt");
            Console.WriteLine();

            string outputFolder = "Your Output Directory";
            string outputFile = Path.Combine(outputFolder, "merged.ppt");
            
            // Load the source PPT file
            using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_PPT))
            {
                // Add another PPT file to merge
                merger.Join(Constants.SAMPLE_PPT_2);
                // Merge PPT files and save result
                merger.Save(outputFile);
            }

            Console.WriteLine("\nPPT files merge completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}

            
            
```
