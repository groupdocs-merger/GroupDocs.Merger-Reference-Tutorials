---
title: Guide to Merging Zip Files using GroupDocs.Merger for .NET
linktitle: Guide to Merging Zip Files using GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: 
type: docs
weight: 12
url: /net/merge-compress-files/guide-merging-zip-files/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Merger.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to merge multiple ZIP files into single file.
    /// For more details about merging Archive (.zip) files please check this documentation article 
    /// https://docs.groupdocs.com/merger/net/merge/archives/
    /// </summary>
    internal static class MergeZip
    {
        public static void Run()
        {
            Console.WriteLine("=======================================================================");
            Console.WriteLine();
            Console.WriteLine("Example Basic Usage: MergeZip");
            Console.WriteLine();

            string outputFolder = "Your Output Directory";
            string outputFile = Path.Combine(outputFolder, "merged.zip");
            
            // Load the source ZIP file
            using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_ZIP))
            {
                // Add another ZIP file to merge
                merger.Join(Constants.SAMPLE_ZIP);
                // Merge ZIP files and save result
                merger.Save(outputFile);
            }

            Console.WriteLine("\nZIP files merge completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}

            
            
```
