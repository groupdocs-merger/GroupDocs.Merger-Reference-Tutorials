---
title: Guide to Merging SVG Files using GroupDocs.Merger for .NET
linktitle: Guide to Merging SVG Files using GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: 
type: docs
weight: 13
url: /net/image-merging/guide-merging-svg-files/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Merger.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to merge multiple SVG files into single file.
    /// For more details about merging image (.svg) files please check this documentation article
    /// https://docs.groupdocs.com/merger/net/merge/images/
    /// </summary>
    internal static class MergeSvg
    {
        public static void Run()
        {
            Console.WriteLine("=======================================================================");
            Console.WriteLine();
            Console.WriteLine("Example Basic Usage: MergeSvg");
            Console.WriteLine();

            string outputFolder = "Your Output Directory";
            string outputFile = Path.Combine(outputFolder, "merged.svg");
            
            // Load the source SVG file
            using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_SVG))
            {
                // Define image join options with vertical join mode
                var joinOptions = new GroupDocs.Merger.Domain.Options.ImageJoinOptions(GroupDocs.Merger.Domain.Options.ImageJoinMode.Vertical);
                // Add another SVG file to merge
                merger.Join(Constants.SAMPLE_SVG, joinOptions);
                // Merge SVG files and save result
                merger.Save(outputFile);
            }

            Console.WriteLine("\nSVG files merge completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}
```
