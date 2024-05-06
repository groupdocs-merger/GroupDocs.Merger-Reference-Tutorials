---
title: Guide to Merging DOT Files using GroupDocs.Merger for .NET
linktitle: Guide to Merging DOT Files using GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: 
type: docs
weight: 13
url: /net/document-merging/guide-merging-dot-files/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Merger.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to merge multiple DOT files into single file.
    /// For more details about merging Microsoft Word Document Template (.dot) files please check this documentation article 
    /// https://docs.groupdocs.com/merger/net/merge/word/
    /// </summary>
    internal static class MergeDot
    {
        public static void Run()
        {
            Console.WriteLine("=======================================================================");
            Console.WriteLine();
            Console.WriteLine("Example Basic Usage: MergeDot");
            Console.WriteLine();

            string outputFolder = "Your Output Directory";
            string outputFile = Path.Combine(outputFolder, "merged.dot");
            
            // Load the source DOT file
            using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_DOT))
            {
                // Add another DOT file to merge
                merger.Join(Constants.SAMPLE_DOT_2);
                // Merge DOT files and save result
                merger.Save(outputFile);
            }

            Console.WriteLine("\nDOT files merge completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}

            
            
```
