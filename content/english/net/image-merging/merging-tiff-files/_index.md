---
title: Merging TIFF Files with GroupDocs.Merger for .NET
linktitle: Merging TIFF Files with GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: 
type: docs
weight: 16
url: /net/image-merging/merging-tiff-files/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Merger.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to merge multiple TIFF files into single file.
    /// For more details about merging image (.tiff) files please check this documentation article
    /// https://docs.groupdocs.com/merger/net/merge/images/
    /// https://docs.groupdocs.com/merger/net/getting-started/use-cases/how-to-merge-tiff-images-using-csharp/
    /// </summary>
    internal static class MergeTiff
    {
        public static void Run()
        {
            Console.WriteLine("=======================================================================");
            Console.WriteLine();
            Console.WriteLine("Example Basic Usage: MergeTiff");
            Console.WriteLine();

            string outputFolder = "Your Output Directory";
            string outputFile = Path.Combine(outputFolder, "merged.tiff");
            
            // Load the source TIFF file
            using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_TIFF))
            {
                // Define image join options with vertical join mode
                var joinOptions = new GroupDocs.Merger.Domain.Options.ImageJoinOptions(GroupDocs.Merger.Domain.Options.ImageJoinMode.Vertical);
                // Add another TIFF file to merge
                merger.Join(Constants.SAMPLE_TIFF, joinOptions);
                // Merge TIFF files and save result
                merger.Save(outputFile);
            }

            Console.WriteLine("\nTIFF files merge completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}
```
