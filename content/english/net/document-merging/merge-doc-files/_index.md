---
title: Merge DOC Files with GroupDocs.Merger for .NET
linktitle: Merge DOC Files with GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: 
type: docs
weight: 10
url: /net/document-merging/merge-doc-files/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Merger.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to merge multiple DOC files into single file.
    /// For more details about merging Microsoft Word Document (.doc) files please check this documentation article 
    /// https://docs.groupdocs.com/merger/net/merge/word/
    /// </summary>
    internal static class MergeDoc
    {
        public static void Run()
        {
            Console.WriteLine("=======================================================================");
            Console.WriteLine();
            Console.WriteLine("Example Basic Usage: MergeDoc");
            Console.WriteLine();

            string outputFolder = "Your Output Directory";
            string outputFile = Path.Combine(outputFolder, "merged.doc");
            
            // Load the source DOC file
            using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_DOC))
            {
                // Add another DOC file to merge
                merger.Join(Constants.SAMPLE_DOC_2);
                // Merge DOC files and save result
                merger.Save(outputFile);
            }

            Console.WriteLine("\nDOC files merge completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}

            
            
```
