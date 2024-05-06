---
title: Merge VSX Files using GroupDocs.Merger for .NET
linktitle: Merge VSX Files using GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: 
type: docs
weight: 17
url: /net/visio-merging/merge-vsx-files/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Merger.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to merge multiple VSX files into single file.
    /// For more details about merging Vector Scalar Extension (.vsx) files please check this documentation article 
    /// https://docs.groupdocs.com/merger/net/merge/vsx
    /// </summary>
    internal static class MergeVsx
    {
        public static void Run()
        {
            Console.WriteLine("=======================================================================");
            Console.WriteLine();
            Console.WriteLine("Example Basic Usage: MergeVsx");
            Console.WriteLine();

            string outputFolder = "Your Output Directory";
            string outputFile = Path.Combine(outputFolder, "merged.vsx");
            
            // Load the source VSX file
            using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_VSX))
            {
                // Add another VSX file to merge
                merger.Join(Constants.SAMPLE_VSX_2);
                // Merge VSX files and save result
                merger.Save(outputFile);
            }

            Console.WriteLine("\nVSX files merge completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}

            
            
```
