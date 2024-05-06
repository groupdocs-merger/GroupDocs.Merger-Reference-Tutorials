---
title: Merging SVGZ Files with GroupDocs.Merger for .NET
linktitle: Merging SVGZ Files with GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: 
type: docs
weight: 14
url: /net/image-merging/merging-svgz-files/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Merger.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to merge multiple SVGZ files into single file.
    /// For more details about merging image (.svgz) files please check this documentation article
    /// https://docs.groupdocs.com/merger/net/merge/images/
    /// </summary>
    internal static class MergeSvgz
    {
        public static void Run()
        {
            Console.WriteLine("=======================================================================");
            Console.WriteLine();
            Console.WriteLine("Example Basic Usage: MergeSvgz");
            Console.WriteLine();

            string outputFolder = "Your Output Directory";
            string outputFile = Path.Combine(outputFolder, "merged.svgz");
            
            // Load the source SVGZ file
            using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_SVGZ))
            {
                // Define image join options with vertical join mode
                var joinOptions = new GroupDocs.Merger.Domain.Options.ImageJoinOptions(GroupDocs.Merger.Domain.Options.ImageJoinMode.Vertical);
                // Add another SVGZ file to merge
                merger.Join(Constants.SAMPLE_SVGZ, joinOptions);
                // Merge SVGZ files and save result
                merger.Save(outputFile);
            }

            Console.WriteLine("\nSVGZ files merge completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}
```
