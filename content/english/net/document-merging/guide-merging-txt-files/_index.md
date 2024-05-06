---
title: Guide to Merging TXT Files with GroupDocs.Merger for .NET
linktitle: Guide to Merging TXT Files with GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: 
type: docs
weight: 18
url: /net/document-merging/guide-merging-txt-files/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Merger.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to merge multiple TXT files into single file.
    /// For more details about merging Plain Text File Format (.txt) files please check this documentation article 
    /// https://docs.groupdocs.com/merger/net/merge/word/
    /// </summary>
    internal static class MergeTxt
    {
        public static void Run()
        {
            Console.WriteLine("=======================================================================");
            Console.WriteLine();
            Console.WriteLine("Example Basic Usage: MergeTxt");
            Console.WriteLine();

            string outputFolder = "Your Output Directory";
            string outputFile = Path.Combine(outputFolder, "merged.txt");
            
            // Load the source TXT file
            using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_TXT))
            {
                // Add another TXT file to merge
                merger.Join(Constants.SAMPLE_TXT_2);
                // Merge TXT files and save result
                merger.Save(outputFile);
            }

            Console.WriteLine("\nTXT files merge completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}

            
            
```
