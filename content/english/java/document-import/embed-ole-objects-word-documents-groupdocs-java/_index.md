---
title: "How to embed pdf in word using GroupDocs.Merger for Java – A Comprehensive Guide"
description: "Learn how to embed pdf in word documents and add pdf to word files with GroupDocs.Merger for Java. Step‑by‑step tutorial for seamless OLE embedding."
date: "2025-12-19"
weight: 1
url: "/java/document-import/embed-ole-objects-word-documents-groupdocs-java/"
keywords:
- embed OLE objects in Word documents
- GroupDocs Merger for Java tutorial
- import OLE objects using Java
type: docs
---

# How to embed pdf in word using GroupDocs.Merger for Java

Embedding a PDF directly inside a Word document can dramatically improve collaboration, because readers no longer need to switch between files. In this guide you’ll discover **how to embed pdf in word** documents using GroupDocs.Merger for Java, and see practical tips on **add pdf to word** workflows. We’ll walk through everything from setting up the library to customizing the size and placement of the OLE object.

## Quick Answers
- **What library is required?** GroupDocs.Merger for Java (latest version)  
- **Can I embed any file type?** Yes – PDFs, images, spreadsheets, etc., as OLE objects  
- **Do I need a license?** A free trial works for development; a commercial license is required for production  
- **Which Java IDE works best?** IntelliJ IDEA, Eclipse, or any IDE that supports Maven/Gradle  
- **How long does the implementation take?** Roughly 10‑15 minutes for a basic embed  

## What is embed pdf in word?
Embedding a PDF creates an OLE (Object Linking and Embedding) object inside the Word file. The PDF remains fully functional—users can double‑click the icon to open it in a PDF viewer, while the Word document stays self‑contained.

## Why add pdf to word using GroupDocs.Merger?
- **Single‑source documentation:** Keep contracts, manuals, or reports together without external links.  
- **Improved accessibility:** Readers can view the PDF without leaving the Word environment.  
- **Automation friendly:** Perfect for generating batch reports or legal packages programmatically.

## Prerequisites
- **Libraries & Dependencies:** Include the GroupDocs.Merger library via Maven or Gradle.  
- **Development Environment:** IntelliJ IDEA, Eclipse, or any Java IDE.  
- **Basic Knowledge:** Familiarity with Java and document manipulation concepts.

## Setting Up GroupDocs.Merger for Java
To embed OLE objects, first add the library to your project.

### Maven
Add this dependency to your `pom.xml` file:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle
Include this in your `build.gradle` file:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### Direct Download
Alternatively, download the latest version from the [GroupDocs.Merger for Java releases page](https://releases.groupdocs.com/merger/java/).

**License Acquisition:** You can start with a free trial or obtain a temporary license to evaluate features before purchasing. Visit [Purchase GroupDocs](https://purchase.groupdocs.com/buy) for more details.

## Basic Initialization
Import the required classes so you can work with OLE objects:

```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OleWordProcessingOptions;
```

## Step‑by‑Step Guide to embed pdf in word

### Step 1: Define file paths and target page
Set the source Word document, the PDF you want to embed, and where the OLE object should appear.

```java
String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.docx"; // Source Word document path
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf"; // File to be embedded as an OLE object
String outputFilePath = new File("YOUR_OUTPUT_DIRECTORY",
    "ImportDocumentToWordProcessing-" + Paths.get(sourceFilePath).getFileName().toString()).getPath();
int pageNumber = 2; // Page number where the OLE object will be inserted
```

- **`sourceFilePath`** – path to the existing Word file.  
- **`embeddedFilePath`** – the PDF you want to **add pdf to word**.  
- **`outputFilePath`** – where the new document will be saved.  
- **`pageNumber`** – the page that will host the OLE object.

### Step 2: Configure OleWordProcessingOptions
Customize the appearance of the embedded PDF by setting its dimensions.

```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Set width of the embedded object (in points)
oleWordsOptions.setHeight(300); // Set height of the embedded object (in points)
```

- **`setWidth()` / `setHeight()`** – control how large the PDF icon appears inside the Word document.

### Step 3: Initialize Merger and import the OLE object
Create a `Merger` instance for the source document, import the OLE object, and save the result.

```java
Merger merger = new Merger(sourceFilePath);
{
    merger.importDocument(oleWordsOptions); // Embed the OLE object into the Word document
    merger.save(outputFilePath); // Save changes to a new output file
}
```

- **`importDocument()`** – takes the `OleWordProcessingOptions` and inserts the PDF as an OLE object.  
- **`save()`** – writes the modified document to `outputFilePath`.

### Step 4: (Optional) Re‑apply configuration for additional objects
If you need to embed more PDFs, repeat **Step 1‑3** with new file paths and page numbers. The same `OleWordProcessingOptions` class lets you control each object individually.

## Configuring OleWordProcessingOptions (Advanced)
You can further tweak placement, such as aligning the object or adding a caption. The code snippet below repeats the basic configuration for clarity:

```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Width of the embedded object
oleWordsOptions.setHeight(300); // Height of the embedded object
```

## Practical Applications
Embedding PDFs is useful in many real‑world scenarios:

1. **Technical Manuals** – Insert detailed schematics or reference PDFs directly into the guide.  
2. **Financial Reports** – Add supplemental audit PDFs without breaking the flow of the main report.  
3. **Legal Contracts** – Attach annexes or exhibits as OLE objects for easy access during review.

## Performance Considerations
When handling large documents or multiple OLE objects, keep these tips in mind:

- **Trim unnecessary content** – embed only the pages you really need.  
- **Manage memory** – use Java’s `-Xmx` flag to allocate sufficient heap space for big files.  
- **Stay up‑to‑date** – newer GroupDocs.Merger releases often include performance optimizations.

## Frequently Asked Questions

**Q: What is OLE embedding?**  
A: Embedding allows you to insert objects like PDFs into Word documents as links that maintain their original functionality.

**Q: Can I embed multiple OLE objects in one document?**  
A: Yes, each can be configured for different pages and sizes using separate `OleWordProcessingOptions`.

**Q: Is there a limit on the size of embedded files?**  
A: The limit is generally dictated by Word’s own constraints, but GroupDocs.Merger handles large files efficiently.

**Q: How do I resolve embedding errors?**  
A: Verify that file paths are correct and that the JVM has enough memory. Check that the source PDF isn’t corrupted.

**Q: Can I modify embedded objects after insertion?**  
A: You can reopen the Word file in Microsoft Word and edit the OLE object, or re‑run the Merger code with updated options.

## Additional Resources
- [GroupDocs.Merger Documentation](https://docs.groupdocs.com/merger/java/)
- [API Reference](https://reference.groupdocs.com/merger/java/)
- [Download Latest Version](https://releases.groupdocs.com/merger/java/)
- [Purchase GroupDocs](https://purchase.groupdocs.com/buy)
- [Free Trial](https://releases.groupdocs.com/merger/java/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [Support Forum](https://forum.groupdocs.com/c/merger/)

---

**Last Updated:** 2025-12-19  
**Tested With:** GroupDocs.Merger for Java latest version  
**Author:** GroupDocs  

---