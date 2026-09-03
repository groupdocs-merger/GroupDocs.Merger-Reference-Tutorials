---
date: '2026-08-15'
description: Learn how to create vertical photo collage by merging images vertically
  with GroupDocs.Merger for Java. This tutorial shows how to join images, build a
  collage, and handle files efficiently.
images:
- /java/format-specific-merging/join-multiple-images-vertically-groupdocs-merger-java/og-image.png
keywords:
- create vertical photo collage
- join multiple images vertically
- combine images into one java
- GroupDocs.Merger for Java
- image merging tutorial
lastmod: '2026-08-15'
og_description: Create vertical photo collage using GroupDocs.Merger for Java. This
  guide walks you through merging multiple images vertically, supported formats, performance
  tips, and real‑world use cases.
og_image_alt: Guide showing how to merge images vertically in Java with GroupDocs.Merger
og_title: Create vertical photo collage with GroupDocs.Merger for Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-15'
  description: Learn how to create vertical photo collage by merging images vertically
    with GroupDocs.Merger for Java. This tutorial shows how to join images, build
    a collage, and handle files efficiently.
  headline: How to merge images vertically using GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to create vertical photo collage by merging images vertically
    with GroupDocs.Merger for Java. This tutorial shows how to join images, build
    a collage, and handle files efficiently.
  name: How to merge images vertically using GroupDocs.Merger for Java
  steps:
  - name: define paths and initialize the merger
    text: First, point the library at your source image and decide where the merged
      result will be saved.
  - name: configure join options
    text: Tell GroupDocs.Merger that you want a **vertical** layout.
  - name: add additional images
    text: Use the `join` method for each extra picture you want to stack below the
      previous one. You can repeat this call as many times as needed to **add images
      to file** and create a long vertical collage.
  - name: save the merged image
    text: Finally, write the combined picture to disk.
  type: HowTo
- questions:
  - answer: PNG, BMP, JPG, and other common static formats are supported.
    question: What image formats can I combine with this method?
  - answer: No hard limit; the practical limit is memory availability. Add images
      sequentially with `join`.
    question: Is there a limit to the number of images I can join?
  - answer: Resize or compress the source images before merging, or use Java’s `ImageIO`
      to reduce quality.
    question: My output file is too large—what can I do?
  - answer: The current API focuses on static images; animated GIFs are not supported
      for vertical joining.
    question: Can I merge animated GIFs vertically?
  - answer: Purchase a license through the GroupDocs portal; a temporary license is
      available for testing.
    question: How do I obtain a production license?
  type: FAQPage
tags:
- create vertical photo collage
- GroupDocs.Merger
- Java image merging
- vertical collage
- image processing
title: How to merge images vertically using GroupDocs.Merger for Java
type: docs
url: /java/format-specific-merging/join-multiple-images-vertically-groupdocs-merger-java/
weight: 1
---

# How to merge images vertically using GroupDocs.Merger for Java

In this step‑by‑step guide you’ll **create vertical photo collage** by merging several images into one tall picture using GroupDocs.Merger for Java. Whether you need a scroll‑friendly banner, a report appendix, or a simple collage, this tutorial explains why vertical merging matters, shows the exact API calls, and gives you practical tips to keep memory usage low.

## Quick answers
- **What library can I use?** GroupDocs.Merger for Java.
- **Can I join more than three images?** Yes – add as many as you need.
- **Which image formats are supported?** PNG, BMP, JPG, and other common static formats.
- **Do I need a license for development?** A free trial works for testing; a paid license is required for production.
- **Is the process memory‑efficient?** Load only required images and save promptly to keep memory usage low.

## What is image merging?
Image merging is the technique of combining two or more separate image files into a single composite image. When the images are stacked **vertically**, the result looks like a tall photo strip—perfect for a **vertical photo collage** or assembling visual sections of a report.

## Why use GroupDocs.Merger for Java?
GroupDocs.Merger for Java lets you join multiple images vertically with just a few lines of code. It supports **50+ static image formats**, processes files in memory without creating temporary files, and can handle multi‑hundred‑page documents while staying under 200 MB of heap memory on a typical server.

## Prerequisites

- Java Development Kit (JDK) 8 or newer.
- An IDE such as IntelliJ IDEA or Eclipse.
- Maven or Gradle for dependency management.
- Basic familiarity with Java syntax (no deep image‑processing knowledge required).

## Setting up GroupDocs.Merger for Java

### Using Maven
Add the dependency to your `pom.xml` file:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Using Gradle
Include the library in your `build.gradle` file:

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### Direct download
Alternatively, you can download the latest version from [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

#### License acquisition steps
1. **Free trial** – explore all features without a cost.  
2. **Temporary license** – obtain a short‑term key for extended testing.  
3. **Purchase** – buy a permanent license for production use.

Once the library is added, import the main class in your Java file:

```java
import com.groupdocs.merger.Merger;
```

## How to merge images vertically

Load your source pictures, tell the API to use a vertical layout, add each picture, and save the result. This four‑step pattern lets you **create vertical photo collage** with minimal code and optimal performance.

### Step 1: define paths and initialize the merger
First, point the library at your source image and decide where the merged result will be saved.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_PNG";
String filePathOut = new File("YOUR_OUTPUT_DIRECTORY", 
    "CrossJoinMultipleDocuments-" + Paths.get(filePath).getFileName().toString()).getPath();

// Initialize Merger with the first image file.
Merger merger = new Merger(filePath);
```

### Step 2: configure join options
Tell GroupDocs.Merger that you want a **vertical** layout.

```java
ImageJoinOptions imageJoinOptions = new ImageJoinOptions(ImageJoinMode.Vertical);
```

### Step 3: add additional images
Use the `join` method for each extra picture you want to stack below the previous one.

```java
merger.join("YOUR_DOCUMENT_DIRECTORY/SAMPLE_BMP", imageJoinOptions); // Second image.
merger.join("YOUR_DOCUMENT_DIRECTORY/SAMPLE_JPG", imageJoinOptions); // Third image.
```

You can repeat this call as many times as needed to **add images to file** and create a long vertical collage.

### Step 4: save the merged image
Finally, write the combined picture to disk.

```java
merger.save(filePathOut);
```

### Expected result
The output file will contain all supplied images aligned one after another from top to bottom, forming a single tall image that can be used in reports, presentations, or web galleries.

## Common issues and solutions
- **Incorrect file paths** – double‑check that each path points to an existing image and that your application has read/write permissions.
- **Unsupported format** – ensure the image type is among the supported static formats (PNG, BMP, JPG). Animated GIFs are not processed by this feature.
- **Out‑of‑memory errors** – when merging many high‑resolution images, consider resizing them before joining or increase the JVM heap size (`-Xmx` flag).

## Practical applications

| Use case | How it helps |
|----------|--------------|
| **Create a vertical photo collage** | Combine vacation snapshots into a single scrollable image. |
| **Assemble visual report sections** | Merge charts, diagrams, and screenshots for a unified PDF export. |
| **Prepare marketing assets** | Stack product images for a sleek, scroll‑friendly web banner. |

## Performance tips
- Load only the images you need at a time; release references after `save` to let the garbage collector free memory.
- Use SSD storage for the source and destination folders to speed up I/O.
- When processing large batches, run the merge in a background thread to keep the UI responsive.

## Conclusion
You now have a complete, step‑by‑step solution for **how to merge images** vertically using GroupDocs.Merger for Java. Experiment with different image sets, try other join modes (horizontal, grid), and integrate this logic into larger automation pipelines.

**Next steps**
- Explore the **ImageJoinMode.Horizontal** option for side‑by‑side collages.
- Combine the merged image with PDF generation using GroupDocs.PDF for end‑to‑end document creation.

## Frequently asked questions

**Q: What image formats can I combine with this method?**  
A: PNG, BMP, JPG, and other common static formats are supported.

**Q: Is there a limit to the number of images I can join?**  
A: No hard limit; the practical limit is memory availability. Add images sequentially with `join`.

**Q: My output file is too large—what can I do?**  
A: Resize or compress the source images before merging, or use Java’s `ImageIO` to reduce quality.

**Q: Can I merge animated GIFs vertically?**  
A: The current API focuses on static images; animated GIFs are not supported for vertical joining.

**Q: How do I obtain a production license?**  
A: Purchase a license through the GroupDocs portal; a temporary license is available for testing.

---

**Last Updated:** 2026-08-15  
**Tested With:** GroupDocs.Merger latest version (as of 2026)  
**Author:** GroupDocs  

**Resources**  
- [Documentation](https://docs.groupdocs.com/merger/java/)  
- [API Reference](https://reference.groupdocs.com/merger/java/)  
- [Download](https://releases.groupdocs.com/merger/java/)  
- [Purchase](https://purchase.groupdocs.com/buy)  
- [Free trial](https://releases.groupdocs.com/merger/java/)  
- [Temporary license](https://purchase.groupdocs.com/temporary-license/)  
- [Support](https://forum.groupdocs.com/c/merger/)

## Related Tutorials

- [How to Perform a Vertical Image Merge of EMF Files Using GroupDocs.Merger for Java](/merger/java/format-specific-merging/master-merging-emf-files-groupdocs-java/)
- [How to Merge Multiple ODP Files Using GroupDocs.Merger for Java](/merger/java/format-specific-merging/merge-multiple-odp-files-groupdocs-java/)
- [How to Merge Multiple VSX Files Using GroupDocs.Merger for Java](/merger/java/format-specific-merging/merge-multiple-vsx-files-groupdocs-merger-java/)