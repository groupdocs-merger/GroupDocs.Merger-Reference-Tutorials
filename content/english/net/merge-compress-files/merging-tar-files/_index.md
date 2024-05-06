---
title: Merging Tar Files with GroupDocs.Merger for .NET
linktitle: Merging Tar Files with GroupDocs.Merger for .NET
second_title: GroupDocs.Merger .NET API
description: 
type: docs
weight: 11
url: /net/merge-compress-files/merging-tar-files/
---

## Complete Source Code
```csharp
using System;
using System.IO;

namespace GroupDocs.Merger.Examples.CSharp.BasicUsage
{
    /// <summary>
    /// This example demonstrates how to merge multiple TAR files into single file.
    /// For more details about merging Archive (.tar) files please check this documentation article 
    /// https://docs.groupdocs.com/merger/net/merge/archives/
    /// </summary>
    internal static class MergeTar
    {
        public static void Run()
        {
            Console.WriteLine("=======================================================================");
            Console.WriteLine();
            Console.WriteLine("Example Basic Usage: MergeTar");
            Console.WriteLine();

            string outputFolder = "Your Output Directory";
            string outputFile = Path.Combine(outputFolder, "merged.tar");
            
            // Load the source TAR file
            using (var merger = new GroupDocs.Merger.Merger(Constants.SAMPLE_TAR))
            {
                // Add another TAR file to merge
                merger.Join(Constants.SAMPLE_TAR);
                // Merge TAR files and save result
                merger.Save(outputFile);
            }

            Console.WriteLine("\nTAR files merge completed successfully. \nCheck output in {0}", outputFolder);
        }
    }
}

            
            
```
