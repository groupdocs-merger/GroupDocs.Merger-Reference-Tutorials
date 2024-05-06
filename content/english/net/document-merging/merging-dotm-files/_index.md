---
title: Merging DOTM Files with GroupDocs.Merger for .NET
linktitle: Merging DOTM Files with GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: 
type: docs
weight: 14
url: /net/document-merging/merging-dotm-files/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Merger.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to merge multiple DOTM files into single file.
    /// For more details about merging Microsoft Word Macro-Enabled Template (.dotm) files please check this documentation article 
    /// https://docs.groupdocs.com/merger/net/merge/word/
    /// </summary>
    internal static class MergeDotm
    {
        public static void Run()
        {
            Console.WriteLine("=======================================================================");
            Console.WriteLine();
            Console.WriteLine("Example Basic Usage: MergeDotm");
            Console.WriteLine();

            string outputFolder = "Your Output Directory";
            string outputFile = Path.Combine(outputFolder, "merged.dotm");
            
            // Load the source DOTM file
            using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_DOTM))
            {
                // Add another DOTM file to merge
                merger.Join(Constants.SAMPLE_DOTM_2);
                // Merge DOTM files and save result
                merger.Save(outputFile);
            }

            Console.WriteLine("\nDOTM files merge completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}

            
            
```
