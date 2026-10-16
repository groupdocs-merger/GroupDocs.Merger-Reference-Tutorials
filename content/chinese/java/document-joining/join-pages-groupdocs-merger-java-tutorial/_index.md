---
date: '2026-10-16'
description: 了解如何在 Java 中使用 GroupDocs.Merger 提取和合并页面。本指南涵盖设置、选择页面范围、合并 PDFs/DOCX 以及性能技巧。
keywords:
- extract and merge pages
- merge documents java
- groupdocs merger java
lastmod: '2026-10-16'
og_description: 了解如何在 Java 中使用 GroupDocs.Merger 提取和合并页面，这是一款支持超过 50 种格式并高效处理大型文档的强大库。
og_image_alt: Guide showing how to extract and merge pages in Java with GroupDocs.Merger
og_title: 如何在 Java 中使用 GroupDocs.Merger 提取和合并页面
schemas:
- author: GroupDocs
  dateModified: '2026-10-16'
  description: Learn how to extract and merge pages in Java using GroupDocs.Merger.
    This guide covers setup, selecting page ranges, merging PDFs/DOCX, and performance
    tips.
  headline: How to extract and merge pages in Java with GroupDocs.Merger
  type: TechArticle
- description: Learn how to extract and merge pages in Java using GroupDocs.Merger.
    This guide covers setup, selecting page ranges, merging PDFs/DOCX, and performance
    tips.
  name: How to extract and merge pages in Java with GroupDocs.Merger
  steps:
  - name: '**Document consolidation:** Pull selected chapters from several textbooks
      into a single PDF for quick review.'
    text: '**Document consolidation:** Pull selected chapters from several textbooks
      into a single PDF for quick review.'
  - name: '**Report generation:** Combine key sections from financial PDFs and Excel‑derived
      PDFs into one executive summary.'
    text: '**Report generation:** Combine key sections from financial PDFs and Excel‑derived
      PDFs into one executive summary.'
  - name: '**Research compilation:** Merge excerpts from multiple academic papers
      (PDF, DOCX) into a single reference document.'
    text: '**Research compilation:** Merge excerpts from multiple academic papers
      (PDF, DOCX) into a single reference document.'
  type: HowTo
- questions:
  - answer: Yes, simply call `merger.join()` repeatedly for each additional source
      file.
    question: Can I merge more than two documents?
  - answer: It supports PDF, DOCX, DOC, PPTX, PPT, XLSX, XLS, and many other common
      office formats—over 50 in total.
    question: What file types does GroupDocs.Merger support?
  - answer: Use the `extract` method with `PageExtractOptions` to save selected pages
      as a new file. This is covered under the **extract pages java** use case.
    question: How do I extract pages from a document without merging?
  - answer: The library imposes no hard cap; practical limits depend on your system’s
      memory and CPU.
    question: Is there a limit to the number of pages I can join?
  - answer: Absolutely—concatenate timestamps or UUIDs to the filename using `PathConstants.getOutputFilePath()`
      or custom logic.
    question: Can I generate dynamic output file names?
  type: FAQPage
tags:
- merge pages
- GroupDocs.Merger
- Java document processing
- PDF manipulation
- DOCX merging
title: 如何在 Java 中使用 GroupDocs.Merger 提取和合并页面
type: docs
url: /zh/java/document-joining/join-pages-groupdocs-merger-java-tutorial/
weight: 1
---

# 如何在 Java 中使用 GroupDocs.Merger 提取并合并页面

在本综合教程中，您将学习如何使用 GroupDocs.Merger for Java 从 PDF、DOCX 文件、电子表格以及许多其他文档类型中**提取并合并页面**。无论您是需要组装自定义手册、从多本书中提取章节，还是从分散的源文件生成简洁报告，本指南都将通过清晰的说明和实际案例，带您完整掌握整个过程。

## 快速答案
- **主要使用场景是什么？** 将 PDF、DOCX、XLSX、PPTX 等受支持格式的选定页面合并为单个输出文件。  
- **哪个库负责此功能？** GroupDocs.Merger for Java。  
- **我需要许可证吗？** 免费试用可用于评估；生产环境需要付费许可证。  
- **需要哪个 Java 版本？** Java 8 或更高版本。  
- **我可以合并超过两个文件吗？** 可以——对每个额外的源文档重复调用 `join`。

## 什么是提取并合并页面？

`extract and merge pages` 是指从一个或多个源文档中选择特定页码或页范围，并将它们拼接成新文件的过程。这消除了手动复制粘贴，并确保生成的文档保留原始的格式、字体和图像。

## 为什么使用 GroupDocs.Merger for Java？

GroupDocs.Merger for Java 是一个多功能库，使开发者能够以编程方式操作文档，支持超过 50 种格式，高速处理且低内存消耗，非常适合企业环境中的服务器端文档工作流和大规模批处理操作。

- **格式灵活性：** 支持 50 多种输入和输出格式，包括 PDF、DOCX、PPTX、XLSX 以及图像文件，几乎可以处理任何办公文档。  
- **性能导向：** 仅处理您请求的页面，从而降低内存消耗。  
- **易于集成：** 通过 Maven 或 Gradle 提供，拥有清晰的 API 文档且无外部依赖。  

## 前置条件
- 基本的 Java 编程知识。  
- 用于依赖管理的 Maven 或 Gradle。  
- 如 IntelliJ IDEA 或 Eclipse 等 IDE。  

## 设置 GroupDocs.Merger for Java

使用以下方法之一将库添加到项目中。

**Maven:**  
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle:**  
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

或者直接从 [GroupDocs.Merger for Java 发布版](https://releases.groupdocs.com/merger/java/) 下载最新版本。

### 获取许可证
要解锁所有功能，您需要许可证。您可以先使用免费试用，或在[购买页面](https://purchase.groupdocs.com/buy)购买完整许可证。也可以获取临时许可证用于短期评估。

## 如何在 Java 中提取并合并页面？

`Merger` 类是创建和管理文档合并操作的主要 API 组件。使用 `Merger` 构造函数加载每个源文档，指定所需的确切页码，然后调用 `join` 进行合并。最后，将合并结果保存为所需格式。整个端到端流程仅需四次方法调用，并在所有受支持的文件类型中保持一致。

## 提取并合并特定页面的分步指南

### 步骤 1：使用主文档初始化 Merger
```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.PageJoinOptions;

String filePath = YOUR_DOCUMENT_DIRECTORY + "/sample.pdf"; // Source PDF document path
Merger merger = new Merger(filePath);
```

### 步骤 2：定义要合并的页面
```java
// Specify the page numbers you wish to join (e.g., pages 1 and 2)
PageJoinOptions joinOptions = new PageJoinOptions(1, 2);
```

### 步骤 3：从第二个文档合并选定页面
```java
// Path to your DOCX file\ String docxFilePath = YOUR_DOCUMENT_DIRECTORY + "/sample.docx";
merger.join(docxFilePath, joinOptions);
```

### 步骤 4：保存结果并释放资源
```java
String outputFilePath = YOUR_OUTPUT_DIRECTORY + "/CrossJoinPagesFromVariousDocuments-output.pdf";
merger.save(outputFilePath);

try {
    merger.close();
} catch (Exception e) {
    // Handle exceptions appropriately
}
```

### 步骤 5（可选）：使用常量集中管理文件路径
```java
import java.nio.file.Paths;
import java.io.File;

public class PathConstants {
    public static final String DOCUMENT_BASE_PATH = YOUR_DOCUMENT_DIRECTORY;
    public static final String OUTPUT_BASE_PATH = YOUR_OUTPUT_DIRECTORY;

    public static String getDocumentPath(String fileName) {
        return DOCUMENT_BASE_PATH + "/" + fileName;
    }

    public static String getOutputFilePath() {
        File outputFile = new File(OUTPUT_BASE_PATH, "CrossJoinPagesFromVariousDocuments-output.pdf");
        return outputFile.getPath();
    }
}
```

使用常量可以使代码更简洁，并简化以后路径的更改。

## 实际应用

以下是 **提取并合并页面** 发挥优势的几个实际场景：

1. **文档合并：** 将多本教材中的选定章节提取到单个 PDF 中，以便快速查看。  
2. **报告生成：** 将财务 PDF 和由 Excel 生成的 PDF 中的关键章节合并为一份执行摘要。  
3. **研究汇编：** 将多篇学术论文（PDF、DOCX）的摘录合并为单个参考文档。

## 性能考虑因素
- **关闭 Merger** 后释放本机资源。  
- **仅选择所需页面** 而不是合并整个文件；这可显著缩短处理时间。  
- **优雅地处理异常**，以避免在源文件缺失或损坏时导致崩溃。  

## 常见问题与解决方案

| 问题 | 解决方案 |
|-------|----------|
| **在大文件上出现 `OutOfMemoryError`** | 将页面分成更小的批次处理，并在每个批次后关闭 Merger。 |
| **不受支持的文件格式** | 确认该格式已列在 GroupDocs.Merger 支持的格式列表中（PDF、DOCX、XLSX、PPTX 等）。 |
| **许可证未生效** | 确保许可证文件放置在应用程序根目录，或通过 `License license = new License(); license.setLicense("path/to/license.lic");` 进行设置。 |

## 常见问题

**问：我可以合并超过两个文档吗？**  
答：可以，只需对每个额外的源文件重复调用 `merger.join()`。

**问：GroupDocs.Merger 支持哪些文件类型？**  
答：它支持 PDF、DOCX、DOC、PPTX、PPT、XLSX、XLS 等多种常见办公格式，总计超过 50 种。

**问：如何在不合并的情况下提取文档页面？**  
答：使用带有 `PageExtractOptions` 的 `extract` 方法将选定页面保存为新文件。这在 **extract pages java** 用例中有说明。

**问：合并页面的数量有没有限制？**  
答：库本身没有硬性上限；实际限制取决于系统的内存和 CPU。

**问：我可以生成动态的输出文件名吗？**  
答：完全可以——使用 `PathConstants.getOutputFilePath()` 或自定义逻辑，将时间戳或 UUID 拼接到文件名中。

## 资源
- [文档](https://docs.groupdocs.com/merger/java/)
- [API 参考](https://reference.groupdocs.com/merger/java/)
- [下载 GroupDocs.Merger for Java](https://releases.groupdocs.com/merger/java/)
- [购买许可证](https://purchase.groupdocs.com/buy)
- [免费试用](https://releases.groupdocs.com/merger/java/)
- [临时许可证](https://purchase.groupdocs.com/temporary-license/)
- [支持论坛](https://forum.groupdocs.com/c/merger/)

浏览这些链接，以加深您的专业知识并解决遇到的任何问题。

---

**Last Updated:** 2026-10-16  
**Tested With:** GroupDocs.Merger for Java 最新版本  
**Author:** GroupDocs

## 相关教程

- [提取页面 Groupdocs Merger Java 指南](/merger/java/document-extraction/extract-pages-groupdocs-merger-java-guide/)
- [合并 PDF Java：使用 GroupDocs.Merger for Java 高效合并 PDF – 步骤指南](/merger/java/format-specific-merging/merge-pdfs-groupdocs-merger-java-tutorial/)
- [移动页面 Java – GroupDocs.Merger 文档页面操作教程](/merger/java/page-operations/)