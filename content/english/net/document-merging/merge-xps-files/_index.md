---
title: Merge XPS Files using GroupDocs.Merger for .NET
linktitle: Merge XPS Files using GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: 
type: docs
weight: 20
url: /net/document-merging/merge-xps-files/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Merger.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to merge multiple XPS files into single file.
    /// For more details about merging Open XML Paper Specification (.xps) files please check this documentation article 
    /// https://docs.groupdocs.com/merger/net/merge/xps
    /// </summary>
    internal static class MergeXps
    {
        public static void Run()
        {
            Console.WriteLine("=======================================================================");
            Console.WriteLine();
            Console.WriteLine("Example Basic Usage: MergeXps");
            Console.WriteLine();

            string outputFolder = "Your Output Directory";
            string outputFile = Path.Combine(outputFolder, "merged.xps");
            
            // Load the source XPS file
            using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_XPS))
            {
                // Add another XPS file to merge
                merger.Join(Constants.SAMPLE_XPS_2);
                // Merge XPS files and save result
                merger.Save(outputFile);
            }

            Console.WriteLine("\nXPS files merge completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}

            
            
```
