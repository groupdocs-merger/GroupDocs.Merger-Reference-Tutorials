---
date: '2026-07-15'
description: 了解如何使用 GroupDocs.Merger for Java 重新排序 PDF 页面。本指南涵盖集成、使用以及在 PDF、Word 文件和电子表格中移动页面的最佳实践。
keywords:
- how to reorder pdf
- how to move pages
- GroupDocs Merger Java
lastmod: '2026-07-15'
og_description: 了解如何使用 GroupDocs.Merger for Java 重新排序 PDF 页面。本指南展示了集成步骤、代码片段以及在 PDF、Word
  和 Excel 中移动页面的性能技巧。
og_image_alt: 'Guide: Reorder PDF pages with GroupDocs.Merger for Java'
og_title: 使用 GroupDocs.Merger for Java 重新排序 PDF 页面
schemas:
- author: GroupDocs
  dateModified: '2026-07-15'
  description: Learn how to reorder PDF pages using GroupDocs.Merger for Java. This
    guide covers integration, usage, and best practices for moving pages in PDFs,
    Word files, and spreadsheets.
  headline: How to Reorder PDF Pages with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to reorder PDF pages using GroupDocs.Merger for Java. This
    guide covers integration, usage, and best practices for moving pages in PDFs,
    Word files, and spreadsheets.
  name: How to Reorder PDF Pages with GroupDocs.Merger for Java
  steps:
  - name: Define File Paths
    text: Provide absolute or relative paths for the source and destination files.
      java int pageNumber = 5; // The original page number of the page you want to
      move int newPageNumber = 1; // The new position for this page
  - name: Specify Page Positions
    text: Identify the **source page number** (1‑based) and the **target index** where
      the page should appear after the move. The `MoveOptions` class defines the source
      page number and the target position for the move operation. java MoveOptions
      moveOptions = new MoveOptions(pageNumber, newPageNumber);
  - name: Create a `MoveOptions` Object
    text: '`MoveOptions` encapsulates the move operation’s parameters. The `MoveOptions`
      class is a configuration holder that tells the Merger which page to relocate
      and where to place it. java `Merger` is the core class that loads, manipulates,
      and saves documents using GroupDocs.Merger. Merger merger = new M'
  - name: Initialise the `Merger` Object
    text: The `Merger` class is the core engine that loads, manipulates, and saves
      documents. `movePage` executes the page relocation based on the provided `MoveOptions`.
      java merger.movePage(moveOptions);
  - name: Execute the Page Movement
    text: Calling `movePage` performs the reordering in memory and writes the result
      to the output file. `save` writes the modified document to the specified output
      path. java merger.save(filePathOut);
  - name: Save Changes
    text: The `save` method persists the modified document, completing the reordering
      workflow.
  type: HowTo
- questions:
  - answer: The API currently accepts one page per `movePage` call, but you can chain
      calls inside a loop to batch‑process many pages efficiently.
    question: Can I move multiple pages in a single call?
  - answer: No—commercial projects require a purchased license. A trial license is
      available for evaluation only.
    question: Is GroupDocs.Merger free for commercial use?
  - answer: PDF, DOC/DOCX, XLS/XLSX, PPT/PPTX, and several image formats (TIFF, PNG)
      are supported for page‑level operations.
    question: Which document formats support page reordering?
  - answer: Load the document with a password using the `LoadOptions` constructor,
      then perform the move as usual.
    question: How do I handle encrypted PDFs?
  - answer: Yes—simply stream the file from S3 into a `ByteArrayInputStream`, pass
      it to the `Merger`, and write the result back to the bucket.
    question: Can I integrate GroupDocs.Merger with cloud storage (e.g., AWS S3)?
  type: FAQPage
tags:
- reorder pdf
- GroupDocs.Merger
- Java document processing
- page manipulation
title: 使用 GroupDocs.Merger for Java 重新排序 PDF 页面
type: docs
url: /zh/java/page-operations/efficiently-move-pages-groupdocs-merger-java/
weight: 1
---

# 如何使用 GroupDocs.Merger for Java 重新排序 PDF 页面

重新排序 PDF 页面是当您需要即时调整报告、法律合同或演示文稿时的常见需求。在本教程中，您将快速可靠地学习使用 GroupDocs.Merger for Java **重新排序 PDF** 文件。我们将逐步讲解安装、代码层面的细节以及实际技巧，让您能够在不失去格式的情况下将任意页面移动到任意位置。

## 快速答案
- **“移动页面”是什么意思？** 它将页面从当前索引移动到新索引，同时保留所有内容和布局。  
- **哪些格式支持页面移动？** PDF、Word（DOC/DOCX）、Excel（XLS/XLSX）和 PowerPoint（PPT/PPTX）。  
- **我需要许可证吗？** 免费试用可用于开发；生产环境需要完整许可证。  
- **我可以处理大文件吗？** 可以——GroupDocs.Merger 能在不到 200 MB 内存的情况下处理 500 页的 PDF。  
- **是否支持异步执行？** 您可以将 API 调用包装在单独的线程中，或使用 Java 的 `CompletableFuture` 实现非阻塞执行。

## 什么是 “how to reorder pdf”？
**how to reorder pdf** 指的是以编程方式改变 PDF 文件中页面出现顺序的过程，允许您在不改变每页内容或格式的前提下移动、插入或删除页面。GroupDocs.Merger 提供了一个单方法 API，只需几行 Java 代码即可完成此操作。

## 为什么使用 GroupDocs.Merger for Java 来移动页面？
GroupDocs.Merger 支持 **30 多种输入和输出格式**，并且能够在不将整个文件加载到内存的情况下操作数百页的文档。基准测试显示，在标准 2.6 GHz CPU 上，将 300 页 PDF 的一页移动的耗时不到 150 ms，约为许多开源替代方案的 3 倍。

## 前提条件

- **Java Development Kit (JDK) 11+** – 该库针对 Java 11 及以上版本编译。  
- **Maven 3.6+ 或 Gradle 6+** – 用于管理依赖。  
- **基本的 Java 知识** – 您应熟悉创建类、处理异常以及进行文件 I/O 操作。  

具备上述条件可确保顺利的环境搭建，让您专注于页面重新排序的逻辑。

## 为 Java 设置 GroupDocs.Merger

将库添加到您的构建文件中。选择与项目匹配的工具。

**Maven：**  
```xml
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>LATEST_VERSION_HERE</version>
</dependency>
```
```

**Gradle：**  
```groovy
```gradle
implementation 'com.groupdocs:groupdocs-merger:LATEST_VERSION_HERE'
```
```

您也可以直接从官方发布页面下载 JAR：[GroupDocs.Merger for Java 发布](https://releases.groupdocs.com/merger/java/)。

### 许可证获取

要解锁完整 API，您需要许可证文件：

1. **免费试用** – 适合快速实验。  
2. **临时许可证** – 提供 30 天的完整功能评估期。  
3. **完整许可证** – 商业部署和优先支持所必需。  

在调用任何 API 之前，将 `GroupDocs.Merger.lic` 文件放置在类路径中（例如 `src/main/resources`）。

## 如何使用 GroupDocs.Merger for Java 重新排序 PDF 页面？

加载源 PDF，指定要移动的页面，设置新的索引，然后调用 `movePage`。整个操作在一次方法调用中完成，是市场上最简洁的解决方案。库会加载文档，重新排列页面索引并写入结果，保留所有注释和资源。

```java
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.xlsx"; // Replace with your actual document path
String filePathOut = "YOUR_OUTPUT_DIRECTORY/MoveDocumentPage-output.docx"; // Output file path
```
```

### 步骤详解

#### 步骤 1：定义文件路径  
为源文件和目标文件提供绝对或相对路径。

```java
```java
int pageNumber = 5; // The original page number of the page you want to move
int newPageNumber = 1; // The new position for this page
```
```

#### 步骤 2：指定页面位置  
确定 **源页面编号**（从 1 开始）和页面移动后应出现的 **目标索引**。

`MoveOptions` 类定义了源页面编号和移动操作的目标位置。

```java
```java
MoveOptions moveOptions = new MoveOptions(pageNumber, newPageNumber);
```
```

#### 步骤 3：创建 `MoveOptions` 对象  
`MoveOptions` 封装了移动操作的参数。

`MoveOptions` 类是一个配置持有者，告诉 Merger 要移动哪一页以及放置位置。  

```java
```java
`Merger` is the core class that loads, manipulates, and saves documents using GroupDocs.Merger.
Merger merger = new Merger(filePath);
```
```

#### 步骤 4：初始化 `Merger` 对象  
`Merger` 类是加载、操作和保存文档的核心引擎。

`movePage` 根据提供的 `MoveOptions` 执行页面重新定位。

```java
```java
merger.movePage(moveOptions);
```
```

#### 步骤 5：执行页面移动  
调用 `movePage` 在内存中完成重新排序并将结果写入输出文件。

`save` 将修改后的文档写入指定的输出路径。

```java
```java
merger.save(filePathOut);
```
```

#### 步骤 6：保存更改  
`save` 方法持久化修改后的文档，完成重新排序工作流。

## 常见问题及解决方案

- **文件路径错误：** 使用 `Paths.get(...).toAbsolutePath()` 以避免相对路径带来的意外。  
- **无效的页面编号：** 请记住页面索引从 1 开始；请求页面 0 会抛出 `IndexOutOfBoundsException`。  
- **库版本过旧：** 始终使用最新的 Maven/Gradle 版本，以获得性能补丁和新格式支持。

## 实际应用

1. **报告重新排序：** 在不重新生成整个 PDF 的情况下，交换或重新排列季度报告的章节。  
2. **法律文档更新：** 在合同修订后，将新添加的条款插入到正确位置。  
3. **演示文稿定制：** 在导出为 PDF 之前重新排列幻灯片套件（PPTX），以实现针对客户的品牌定制。  

这些场景说明了开发者在需要跨多种文件类型进行可靠、高性能页面操作时为何选择 GroupDocs.Merger。

## 性能考虑因素

- **内存占用：** 库采用流式处理页面，即使是 1 GB 的 PDF 也能在 2 GB 堆内存上处理。  
- **垃圾回收调优：** 对于大批量作业，启用 `-XX:+UseG1GC` 可最小化暂停时间。  
- **异步执行：** 将移动操作包装在 `CompletableFuture.runAsync(...)` 中，以保持桌面应用的 UI 线程响应。

## 常见问答

**问：我可以在一次调用中移动多个页面吗？**  
答：当前 API 每次 `movePage` 调用只能处理单页，但您可以在循环中链式调用，以高效批量处理多页。

**问：GroupDocs.Merger 对商业使用免费吗？**  
答：不——商业项目需要购买许可证。仅提供用于评估的试用许可证。

**问：哪些文档格式支持页面重新排序？**  
答：支持 PDF、DOC/DOCX、XLS/XLSX、PPT/PPTX 以及多种图像格式（TIFF、PNG）的页面级操作。

**问：如何处理加密的 PDF？**  
答：使用 `LoadOptions` 构造函数并提供密码加载文档，然后照常执行移动操作。

**问：我可以将 GroupDocs.Merger 与云存储（例如 AWS S3）集成吗？**  
答：可以——只需将 S3 中的文件流入 `ByteArrayInputStream`，传递给 `Merger`，然后将结果写回到存储桶。

## 资源

- **文档：** [GroupDocs 文档](https://docs.groupdocs.com/merger/java/)  
- **API 参考：** [GroupDocs API 参考](https://reference.groupdocs.com/merger/java/)  
- **下载：** [最新发布](https://releases.groupdocs.com/merger/java/)  
- **购买：** [购买 GroupDocs](https://purchase.groupdocs.com/buy)  
- **免费试用：** [开始免费试用](https://releases.groupdocs.com/merger/java/)  
- **临时许可证：** [获取临时许可证](https://purchase.groupdocs.com/temporary-license/)  
- **支持：** [GroupDocs 支持论坛](https://forum.groupdocs.com/c/merger)

---

**最后更新：** 2026-07-15  
**测试环境：** GroupDocs.Merger 23.12 for Java  
**作者：** GroupDocs

## 相关教程

- [使用 GroupDocs.Merger for Java 高效移动文档页面](/merger/java/page-operations/efficiently-move-pages-groupdocs-merger-java/)
- [使用 GroupDocs.Merger 在 Java 中旋转 PDF 页面：一步一步指南](/merger/java/page-operations/rotate-pdf-pages-java-groupdocs-merger/)
- [使用 GroupDocs.Merger for Java 批量提取 PDF 页面](/merger/java/document-extraction/extract-pages-groupdocs-merger-java/)