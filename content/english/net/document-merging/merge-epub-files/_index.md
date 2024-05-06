---
title: Merge EPUB Files using GroupDocs.Merger for .NET
linktitle: Merge EPUB Files using GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: 
type: docs
weight: 17
url: /net/document-merging/merge-epub-files/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Merger.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to merge multiple EPUB files into single file.
    /// For more details about merging Digital E-Book File Format (.epub) files please check this documentation article 
    /// https://docs.groupdocs.com/merger/net/merge/epub
    /// </summary>
    internal static class MergeEpub
    {
        public static void Run()
        {
            Console.WriteLine("=======================================================================");
            Console.WriteLine();
            Console.WriteLine("Example Basic Usage: MergeEpub");
            Console.WriteLine();

            string outputFolder = "Your Output Directory";
            string outputFile = Path.Combine(outputFolder, "merged.epub");
            
            // Load the source EPUB file
            using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_EPUB))
            {
                // Add another EPUB file to merge
                merger.Join(Constants.SAMPLE_EPUB_2);
                // Merge EPUB files and save result
                merger.Save(outputFile);
            }

            Console.WriteLine("\nEPUB files merge completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}

            
            
```
