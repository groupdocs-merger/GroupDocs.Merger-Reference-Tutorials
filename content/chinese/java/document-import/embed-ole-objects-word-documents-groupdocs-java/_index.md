---
date: '2026-10-27'
description: 了解如何使用 GroupDocs.Merger for Java 将 PDF 嵌入 Word 文档并添加 PDF 到 Word 文件。一步步教程，帮助实现无缝
  OLE 嵌入。
keywords:
- how to embed pdf in word
- embed pdf in word document
- embed pdf as ole
- embed multiple pdfs word
- add pdf icon to word
lastmod: '2026-10-27'
og_description: 了解如何使用 GroupDocs.Merger for Java 将 PDF 嵌入 Word。请按照本简明教程，将 PDF 作为 OLE
  对象添加到 Word 文档中。
og_image_alt: Guide showing how to embed PDF files into Word documents using GroupDocs.Merger
  for Java
og_title: 使用 GroupDocs.Merger for Java 在 Word 中嵌入 PDF – 步骤指南
schemas:
- author: GroupDocs
  dateModified: '2026-10-27'
  description: Learn how to embed pdf in word documents and add pdf to word files
    with GroupDocs.Merger for Java. Step‑by‑step tutorial for seamless OLE embedding.
  headline: How to embed pdf in word using GroupDocs.Merger for Java – A comprehensive
    guide
  type: TechArticle
- description: Learn how to embed pdf in word documents and add pdf to word files
    with GroupDocs.Merger for Java. Step‑by‑step tutorial for seamless OLE embedding.
  name: How to embed pdf in word using GroupDocs.Merger for Java – A comprehensive
    guide
  steps:
  - name: define file paths and target page
    text: Set the source Word document, the PDF you want to embed, and where the OLE
      object should appear. - **`sourceFilePath`** – path to the existing Word file.
      - **`embeddedFilePath`** – the PDF you want to **add pdf to word**. - **`outputFilePath`**
      – where the new document will be saved. - **`pageNumber
  - name: configure OleWordProcessingOptions
    text: '`OleWordProcessingOptions` controls the visual representation of the embedded
      object. You can align the object to the left, center, or right, add a caption
      underneath, and even specify whether the embedded file should be displayed as
      an icon or as a preview. - **`setWidth()` / `setHeight()`** – cont'
  - name: initialize Merger and import the OLE object
    text: Create a `Merger` instance for the source document, import the OLE object,
      and save the result. - **`importDocument()`** – takes the `OleWordProcessingOptions`
      and inserts the PDF as an OLE object. - **`save()`** – writes the modified document
      to `outputFilePath`.
  - name: (optional) re‑apply configuration for additional objects
    text: If you need to embed more PDFs, repeat **Step 1‑3** with new file paths
      and page numbers. The same `OleWordProcessingOptions` class lets you control
      each object individually.
  type: HowTo
- questions:
  - answer: Embedding allows you to insert objects like PDFs into Word documents as
      links that maintain their original functionality.
    question: What is OLE embedding?
  - answer: Yes, each can be configured for different pages and sizes using separate
      `OleWordProcessingOptions`.
    question: Can I embed multiple OLE objects in one document?
  - answer: The limit is generally dictated by Word’s own constraints, but GroupDocs.Merger
      handles large files efficiently.
    question: Is there a limit on the size of embedded files?
  - answer: Verify that file paths are correct and that the JVM has enough memory.
      Check that the source PDF isn’t corrupted.
    question: How do I resolve embedding errors?
  - answer: You can reopen the Word file in Microsoft Word and edit the OLE object,
      or re‑run the Merger code with updated options.
    question: Can I modify embedded objects after insertion?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- Java document processing
- OLE embedding
- Word automation
- author: GroupDocs
  dateModified: '2026-10-27'
  description: Learn how to embed pdf in word documents and add pdf to word files
    with GroupDocs.Merger for Java. Step‑by‑step tutorial for seamless OLE embedding.
  headline: How to embed pdf in word using GroupDocs.Merger for Java – A comprehensive
    guide
  type: TechArticle
- description: Learn how to embed pdf in word documents and add pdf to word files
    with GroupDocs.Merger for Java. Step‑by‑step tutorial for seamless OLE embedding.
  name: How to embed pdf in word using GroupDocs.Merger for Java – A comprehensive
    guide
  steps:
  - name: Define file paths and target page
    text: Set the source Word document, the PDF you want to embed, and where the OLE
      object should appear. - **`sourceFilePath`** – path to the existing Word file.
      - **`embeddedFilePath`** – the PDF you want to **add pdf to word**. - **`outputFilePath`**
      – where the new document will be saved. - **`pageNumber`** – the page that will
      host the OLE object.
  - name: Configure OleWordProcessingOptions
    text: The `OleWordProcessingOptions` class defines how the OLE object looks inside
      the Word document. You can set width, height, alignment, and even a caption.
      - **`setWidth()` / `setHeight()`** – control how large the PDF icon appears
      inside the Word document.
  - name: Initialize Merger and import the OLE object
    text: Create a `Merger` instance for the source document, import the OLE object,
      and save the result. - **`importDocument()`** – takes the `OleWordProcessingOptions`
      and inserts the PDF as an OLE object. - **`save()`** – writes the modified document
      to `outputFilePath`.
  - name: (Optional) Re‑apply configuration for additional objects
    text: If you need to embed more PDFs, repeat **Step 1‑3** with new file paths
      and page numbers. The same `OleWordProcessingOptions` class lets you control
      each object individually.
  type: HowTo
- questions:
  - answer: Embedding allows you to insert objects like PDFs into Word documents as
      links that maintain their original functionality.
    question: What is OLE embedding?
  - answer: Yes, each can be configured for different pages and sizes using separate
      `OleWordProcessingOptions`.
    question: Can I embed multiple OLE objects in one document?
  - answer: The limit is generally dictated by Word’s own constraints, but GroupDocs.Merger
      handles large files efficiently.
    question: Is there a limit on the size of embedded files?
  - answer: Verify that file paths are correct and that the JVM has enough memory.
      Check that the source PDF isn’t corrupted.
    question: How do I resolve embedding errors?
  - answer: You can reopen the Word file in Microsoft Word and edit the OLE object,
      or re‑run the Merger code with updated options.
    question: Can I modify embedded objects after insertion?
  type: FAQPage
title: 使用 GroupDocs.Merger for Java 在 Word 中嵌入 PDF – 完整指南
type: docs
url: /zh/java/document-import/embed-ole-objects-word-documents-groupdocs-java/
weight: 1
---

# 如何使用 GroupDocs.Merger for Java 在 Word 中嵌入 PDF

将 PDF 直接嵌入 Word 文档可以显著提升协作效率，因为阅读者无需在文件之间切换。在本指南中，您将发现使用 GroupDocs.Merger for Java **how to embed pdf in word** 文档的方式，并看到关于 **add pdf to word** 工作流的实用技巧。我们将从库的设置到 OLE 对象的大小和位置自定义，全面演示如何自信地实现文档自动化。

## 快速答案
- **需要的库是什么？** GroupDocs.Merger for Java (latest version)  
- **我可以嵌入任何文件类型吗？** Yes – PDFs, images, spreadsheets, etc., as OLE objects  
- **我需要许可证吗？** A free trial works for development; a commercial license is required for production  
- **哪个 Java IDE 最适合？** IntelliJ IDEA, Eclipse, or any IDE that supports Maven/Gradle  
- **实现需要多长时间？** Roughly 10‑15 minutes for a basic embed  

## 什么是 embed pdf in word？
将 PDF 嵌入会在 Word 文件中创建一个 OLE（对象链接与嵌入）对象，使 PDF 能够直接从文档中打开。嵌入的文件保留其原始的格式和交互性，而 Word 文档保持为单一的自包含包。这种方式简化了分发，确保版本一致性，并为阅读者提供即时访问补充材料的能力，无需离开 Word 环境。

## 为什么使用 GroupDocs.Merger 将 pdf 添加到 word？
GroupDocs.Merger 自动化 OLE 插入、大小调整和定位，省去手动编辑的需求。该库支持多达 **30+ input and output formats**，并且可以在单批处理中嵌入 **hundreds of PDFs**，同时在典型 JVM 上将内存使用保持在 **200 MB** 以下。这种可扩展性使其非常适合大规模文档、合同或营销套件。

## 前置条件
- **库和依赖项：** Include the GroupDocs.Merger library via Maven or Gradle.  
- **开发环境：** IntelliJ IDEA, Eclipse, or any Java IDE.  
- **基础知识：** Familiarity with Java and document‑manipulation concepts.  

## 如何设置 GroupDocs.Merger for Java？
首先，使用 Maven、Gradle 或手动 JAR 下载将 GroupDocs.Merger 库添加到项目中。依赖解析后，导入核心类，例如 `Merger`、`OleWordProcessingOptions` 以及所需的 I/O 工具。确保项目目标为 Java 8 或更高版本，并且库版本与您的许可证匹配。

### Maven
将此依赖添加到您的 `pom.xml` 文件中：
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle
在您的 `build.gradle` 文件中加入以下内容：
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### 直接下载
或者，从 [GroupDocs.Merger for Java 发布页面](https://releases.groupdocs.com/merger/java/) 下载最新版本。

**获取许可证：** 您可以先使用免费试用，或获取临时许可证以评估功能后再购买。访问 [购买 GroupDocs](https://purchase.groupdocs.com/buy) 获取更多详情。

## 基本初始化是如何工作的？
`Merger` 类是 GroupDocs.Merger for Java 中所有文档处理操作的入口。创建 `Merger` 实例后，您可以调用诸如 `importDocument` 的方法来嵌入 OLE 对象。导入所需的类以便处理 OLE 对象：
```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OleWordProcessingOptions;
```

## 如何一步步将 PDF 嵌入 Word 文档？
嵌入 PDF 包括加载源 Word 文件，创建 `OleWordProcessingOptions` 实例以定义外观，然后使用 PDF 路径和选项调用 `importDocument`。库将在指定位置插入 OLE 对象，随后您保存文档以生成自包含文件。

### 步骤 1：定义文件路径和目标页
设置源 Word 文档、要嵌入的 PDF，以及 OLE 对象应出现的位置。
```java
String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.docx"; // Source Word document path
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf"; // File to be embedded as an OLE object
String outputFilePath = new File("YOUR_OUTPUT_DIRECTORY",
    "ImportDocumentToWordProcessing-" + Paths.get(sourceFilePath).getFileName().toString()).getPath();
int pageNumber = 2; // Page number where the OLE object will be inserted
```
- **`sourceFilePath`** – 现有 Word 文件的路径。  
- **`embeddedFilePath`** – 您想要 **add pdf to word** 的 PDF。  
- **`outputFilePath`** – 新文档将保存的位置。  
- **`pageNumber`** – 将承载 OLE 对象的页码。

### 步骤 2：配置 OleWordProcessingOptions
`OleWordProcessingOptions` 控制嵌入对象的视觉呈现。您可以将对象左对齐、居中或右对齐，添加下方标题，甚至指定嵌入文件是以图标还是预览形式显示。
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Set width of the embedded object (in points)
oleWordsOptions.setHeight(300); // Set height of the embedded object (in points)
```
- **`setWidth()` / `setHeight()`** – 控制 PDF 图标在 Word 文档中的显示大小。

### 步骤 3：初始化 Merger 并导入 OLE 对象
为源文档创建 `Merger` 实例，导入 OLE 对象并保存结果。
```java
Merger merger = new Merger(sourceFilePath);
{
    merger.importDocument(oleWordsOptions); // Embed the OLE object into the Word document
    merger.save(outputFilePath); // Save changes to a new output file
}
```
- **`importDocument()`** – 接受 `OleWordProcessingOptions` 并将 PDF 插入为 OLE 对象。  
- **`save()`** – 将修改后的文档写入 `outputFilePath`。

### 步骤 4：（可选）为其他对象重新应用配置
如果需要嵌入更多 PDF，请使用新的文件路径和页码重复 **Step 1‑3**。相同的 `OleWordProcessingOptions` 类允许您单独控制每个对象。

## 如何为高级场景配置 OleWordProcessingOptions？
`OleWordProcessingOptions` 是 OLE 嵌入的配置中心。您可以将对象左对齐、居中或右对齐，添加下方标题，甚至指定嵌入文件是以图标还是预览形式显示。下面的代码片段重复了基本配置以便说明：
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Width of the embedded object
oleWordsOptions.setHeight(300); // Height of the embedded object
```

## 嵌入 PDF 到 Word 的实际应用有哪些？
在许多专业场景中，嵌入 PDF 非常有价值，因为它将相关内容保持在一起，同时保留每个文件的原始格式。例如，技术手册可以包含详细的原理图，财务报告可以附加审计报表，法律合同可以嵌入附件，营销手册可以加入产品规格表——全部无需单独下载或外部链接。

## 性能考虑对大文档有什么影响？
在处理大型 Word 文件或多个 OLE 对象时，需要高效管理内存和 I/O。裁剪不必要的内容，仅嵌入所需页面，并使用 `-Xmx` 标志分配足够的 JVM 堆空间。最近的 GroupDocs.Merger 版本将处理速度提升 **up to 35 %**（最高提升 35%），针对超过 **200 pages**（200 页）的文档，并将峰值内存消耗降低约 **around 40 %**（约 40%），相较于早期版本。

## 常见问题及解决方案
典型问题包括文件路径错误、内存不足错误、源 PDF 损坏以及缺少 OLE 图标。确保 Word 和 PDF 路径为绝对路径或相对于项目根目录的正确相对路径，为大批量任务增加 JVM 堆大小，验证每个 PDF 在嵌入前能正常打开，并确认目标 Word 模板允许 OLE 插入。调整这些因素通常可以解决大多数嵌入失败的问题。

## 常见问答

**Q: 什么是 OLE 嵌入？**  
A: 嵌入允许您将 PDF 等对象作为链接插入 Word 文档，保持其原有功能。

**Q: 我可以在一个文档中嵌入多个 OLE 对象吗？**  
A: 可以，每个对象都可以使用单独的 `OleWordProcessingOptions` 为不同页面和尺寸进行配置。

**Q: 嵌入文件的大小有限制吗？**  
A: 限制通常由 Word 本身的约束决定，但 GroupDocs.Merger 能高效处理大文件。

**Q: 如何解决嵌入错误？**  
A: 确认文件路径正确且 JVM 有足够的内存。检查源 PDF 是否损坏。

**Q: 插入后我可以修改嵌入的对象吗？**  
A: 您可以在 Microsoft Word 中重新打开该 Word 文件并编辑 OLE 对象，或使用更新的选项重新运行 Merger 代码。

## 其他资源
- [GroupDocs.Merger 文档](https://docs.groupdocs.com/merger/java/)
- [API 参考](https://reference.groupdocs.com/merger/java/)
- [下载最新版本](https://releases.groupdocs.com/merger/java/)
- [购买 GroupDocs](https://purchase.groupdocs.com/buy)
- [免费试用](https://releases.groupdocs.com/merger/java/)
- [临时许可证](https://purchase.groupdocs.com/temporary-license/)
- [支持论坛](https://forum.groupdocs.com/c/merger/)

---

**最后更新：** 2026-10-27  
**测试环境：** GroupDocs.Merger for Java latest version  
**作者：** GroupDocs  

---

## 相关教程

- [如何使用 GroupDocs.Merger for Java 在 Excel 中嵌入 PDF - 导入 OLE 对象 – 步骤指南](/merger/java/document-import/import-ole-object-excel-groupdocs-merger-java/)
- [在 Java 中使用 GroupDocs.Merger 将图像嵌入为 OLE 对象：综合指南](/merger/java/image-operations/embed-images-ole-java-groupdocs-merger/)
- [使用 GroupDocs.Merger for Java 添加 PDF 附件 – 完整指南](/merger/java/format-specific-merging/embed-documents-pdf-groupdocs-merger-java/)