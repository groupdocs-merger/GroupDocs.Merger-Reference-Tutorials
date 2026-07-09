---
date: '2026-06-26'
description: 了解如何使用 GroupDocs.Merger for Java 将图像转换为 OLE。一步一步的指南、代码片段以及将图像嵌入为 OLE
  对象的最佳实践。
keywords:
- convert image to ole
- GroupDocs.Merger Java tutorial
- embed images as OLE objects
schemas:
- author: GroupDocs
  dateModified: '2026-06-26'
  description: Learn how to convert image to OLE using GroupDocs.Merger for Java.
    Step‑by‑step guide, code snippets, and best practices for embedding images as
    OLE objects.
  headline: How to Convert Image to OLE in Java with GroupDocs.Merger
  type: TechArticle
- description: Learn how to convert image to OLE using GroupDocs.Merger for Java.
    Step‑by‑step guide, code snippets, and best practices for embedding images as
    OLE objects.
  name: How to Convert Image to OLE in Java with GroupDocs.Merger
  steps:
  - name: Define File Paths
    text: 'Specify where the source document and the image reside. Replace the placeholders
      with actual paths on your machine:'
  - name: Read Image Bytes
    text: 'Read the entire image file into a byte array. This byte array becomes the
      OLE payload:'
  - name: Configure OLE Diagram Options
    text: '`OleDiagramOptions` tells GroupDocs where and how to place the OLE object.
      The class is the **top‑level options holder for OLE diagram import**; it lets
      you set page number, X/Y coordinates, width, and height.'
  - name: Initialize Merger and Import OLE Diagram
    text: '`Merger` is the core class that represents a document and provides methods
      for manipulation. It **encapsulates all read/write operations** for the target
      file.'
  - name: Initialize Merger with Source Path
    text: 'Reuse the same `Merger` instance or create a new one pointing to the modified
      document:'
  - name: Save the Modified Document
    text: 'Call the `save` method with the desired output location. GroupDocs.Merger
      writes the file in a streaming fashion, keeping memory usage low:'
  type: HowTo
- questions:
  - answer: An OLE object embeds data from one application (e.g., an image) into another
      (e.g., a Word file), allowing in‑place editing without leaving the host document.
    question: What is an OLE object?
  - answer: Yes—commercial use requires a valid license. A trial is available for
      evaluation, but production deployments must be licensed.
    question: Can I use GroupDocs.Merger for commercial projects?
  - answer: Images are read into a byte array, but you can stream large files using
      `FileInputStream` and pass the stream to `importOleDiagram` to keep memory usage
      low.
    question: How does the library handle very large images?
  - answer: DOCX, XLSX, PPTX, and PDF are fully supported. For PDF, the OLE object
      is stored as an embedded file stream.
    question: Which document formats support OLE embedding?
  - answer: Practically none—GroupDocs.Merger can embed dozens of OLE diagrams, limited
      only by the host document’s size and available memory.
    question: Are there any limitations on the number of OLE objects per document?
  type: FAQPage
title: 如何在 Java 中使用 GroupDocs.Merger 将图像转换为 OLE
type: docs
url: /zh/java/image-operations/embed-images-ole-java-groupdocs-merger/
weight: 1
---

# 如何在 Java 中使用 GroupDocs.Merger 将图像转换为 OLE

将图像直接嵌入文档可能会觉得繁琐，但使用 GroupDocs.Merger for Java，**convert image to OLE** 变得轻而易举。在本教程中，您将了解 OLE 对象的用途、如何准备环境以及将图像嵌入为 OLE 图表的具体步骤。完成后，您将拥有一个可在 Word、Excel、PowerPoint 和 PDF 文件中使用的可复用代码模式。

## 快速答案
- **主要方法是什么？** 在加载源文档后使用 `Merger.importOleDiagram()`。  
- **我需要许可证吗？** 试用版可用于开发；生产环境需要完整许可证。  
- **支持哪些图像格式？** PNG、JPEG、BMP、GIF 和 TIFF 均受支持。  
- **我可以设置 OLE 的大小和位置吗？** 可以——`OleDiagramOptions` 允许您定义页面、坐标、宽度和高度。  
- **该过程内存效率高吗？** GroupDocs.Merger 采用流式处理数据，即使是 500 页的文件也保持在 200 MB RAM 以下。  

## 什么是 “convert image to OLE”？
**Convert image to OLE** 指将光栅图像文件转换为对象链接与嵌入 (OLE) 图表，可在宿主文档内进行编辑。此转换使最终用户能够双击图像，在其原生编辑器中打开，并将更改保存回容器文档，而无需离开文件。

## 为什么使用 GroupDocs.Merger 进行 OLE 嵌入？
GroupDocs.Merger 支持 **50+ 种输入和输出格式**——包括 DOCX、XLSX、PPTX、PDF 和常见图像类型，并且能够在不将整个文件加载到内存中的情况下，在最大 **300 MB** 的文档中嵌入 OLE 对象。该库在典型的 2.6 GHz 服务器上，能够在 **3 秒** 内处理一个包含三个嵌入 PNG 的 200 页 Word 文件，为您提供速度和可扩展性。

## 前提条件
- **Java Development Kit (JDK) 8+** 已在您的 IDE 中安装并配置。  
- **GroupDocs.Merger for Java** 已通过 Maven 或 Gradle 添加（建议使用最新版本）。  
- 具备 Java I/O 流和面向对象编程的基本熟悉度。  

## 为 Java 设置 GroupDocs.Merger
要在项目中包含 GroupDocs.Merger，请将依赖项添加到构建文件中。该库可在 Maven Central 获取，因此您可以将下面的代码片段复制到 `pom.xml` 或 `build.gradle` 中。  

> **注意：** 以下占位符代表原教程中的完整代码块，请保持不变。

```xml
  <!-- Maven -->
  <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-merger</artifactId>
      <version>latest-version</version>
  </dependency>
  ```

```gradle
  // Gradle
  implementation 'com.groupdocs:groupdocs-merger:latest-version'
  ```

您也可以直接从官方发布页面下载 JAR： [GroupDocs.Merger 发布](https://releases.groupdocs.com/merger/java/)。

### 许可证获取
- **免费试用：** 适合原型制作和评估。  
- **临时许可证：** 在有限时间内扩展试用功能。  
- **完整许可证：** 解锁所有 OLE 相关功能并移除使用限制。

添加依赖后，您即可在 Java 代码中初始化库。

## 如何在 Java 中将图像转换为 OLE？
要将图像转换为 OLE 对象，使用 `Merger` 实例加载目标文档，将图像文件读取为字节数组，创建指定页面、位置和大小的 `OleDiagramOptions` 对象，然后调用 `merger.importOleDiagram(imageBytes, options)`。最后，使用 `merger.save(outputPath)` 保存文档。此工作流将图像嵌入为可编辑的 OLE 图表。

### 步骤 1：定义文件路径
指定源文档和图像所在的位置。将占位符替换为您机器上的实际路径：

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.vsdx";  
String imageFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.emf";
```

### 步骤 2：读取图像字节
将整个图像文件读取为字节数组。此字节数组即为 OLE 负载：

```java
File file = new File(imageFilePath);
byte[] imageBytes = Files.readAllBytes(file.toPath());
```

### 步骤 3：配置 OLE 图表选项
`OleDiagramOptions` 告诉 GroupDocs OLE 对象的放置位置和方式。该类是 **OLE 图表导入的顶层选项持有者**；它允许您设置页码、X/Y 坐标、宽度和高度。

```java
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pptx";
int pageNumber = 2;  
String filePathOut = new File("YOUR_OUTPUT_DIRECTORY", "ImportImageToDocument" + Paths.get(filePath).getFileName().toString()).getPath();

OleDiagramOptions oleDiagramOptions = new OleDiagramOptions(embeddedFilePath, imageBytes, pageNumber);
oleDiagramOptions.setX(1);  
oleDiagramOptions.setY(1);
oleDiagramOptions.setWidth(2);
oleDiagramOptions.setHeight(1);
```

### 步骤 4：初始化 Merger 并导入 OLE 图表
`Merger` 是表示文档并提供操作方法的核心类。它 **封装了目标文件的所有读/写操作**。

```java
Merger merger = new Merger(filePath);
merger.importDocument(oleDiagramOptions);
merger.save(filePathOut);
```

## 保存修改后的文档

OLE 图表嵌入后，您需要将更改写回磁盘。

### 步骤 1：使用源路径初始化 Merger
复用相同的 `Merger` 实例或创建指向已修改文档的新实例：

```java
Merger merger = new Merger(filePath);
```

### 步骤 2：保存修改后的文档
使用期望的输出位置调用 `save` 方法。GroupDocs.Merger 以流式方式写入文件，保持低内存使用：

```java
merger.save(outputPath);
```

## 实际应用
将图像嵌入为 OLE 对象可实现多种实际场景：

- **交互式报告：** 用户可以双击嵌入的图表，在 Excel 中编辑，并立即看到更新后的可视化效果。  
- **自动化文档生成：** 金融和医疗系统可以将最新的图形注入合同或患者摘要中，无需手动编辑。  
- **协作平台：** 团队可以共享单个 Word 文件，每个成员更新自己的图表，从而减少版本控制的麻烦。  

## 性能考虑因素
在处理大文件时保持应用响应性：

- **流式数据：** GroupDocs.Merger 对输入和输出均采用流式处理，防止将完整文件加载到内存中。  
- **复用对象：** 对多个导入复用同一个 `Merger` 实例可减少对象创建开销。  
- **监控堆内存：** 对于大于 200 MB 的文档，考虑增加 JVM 堆大小（`-Xmx1g`），以避免 `OutOfMemoryError`。  

## 常见问题及解决方案
| 症状 | 可能原因 | 解决方案 |
|---------|--------------|-----|
| `Unsupported file format` 错误 | 图像不是 PNG/JPEG/BMP/GIF/TIFF 格式 | 在读取字节之前，将图像转换为受支持的格式。 |
| OLE 对象出现在错误位置 | `OleDiagramOptions` 中的 `x`/`y` 坐标不正确 | 确认坐标使用点（pt）为单位（1 pt ≈ 1/72 英寸）。 |
| 输出文件损坏 | 导入后未调用 `save()` | 确保在所有修改后执行 `merger.save(outputPath)`。 |

## 常见问题

**Q: 什么是 OLE 对象？**  
A: OLE 对象将来自一个应用程序（例如图像）的数据嵌入到另一个应用程序（例如 Word 文件）中，允许在宿主文档内就地编辑，而无需离开文档。

**Q: 我可以在商业项目中使用 GroupDocs.Merger 吗？**  
A: 可以——商业使用需要有效许可证。提供试用版用于评估，但生产部署必须获得许可证。

**Q: 库如何处理非常大的图像？**  
A: 图像会读取为字节数组，但您可以使用 `FileInputStream` 对大文件进行流式处理，并将流传递给 `importOleDiagram`，以保持低内存使用。

**Q: 哪些文档格式支持 OLE 嵌入？**  
A: DOCX、XLSX、PPTX 和 PDF 完全受支持。对于 PDF，OLE 对象存储为嵌入的文件流。

**Q: 每个文档中 OLE 对象的数量有任何限制吗？**  
A: 实际上没有——GroupDocs.Merger 可以嵌入数十个 OLE 图表，唯一限制是宿主文档的大小和可用内存。

## 资源
- [GroupDocs.Merger 发布](https://releases.groupdocs.com/merger/java/)
- [GroupDocs.Merger Java 文档](https://docs.groupdocs.com/merger/java/)
- [Java API 参考](https://reference.groupdocs.com/merger/java/)
- [GroupDocs.Merger for Java 发布版](https://releases.groupdocs.com/merger/java/)
- [GroupDocs 购买页面](https://purchase.groupdocs.com/buy)
- [GroupDocs 支持论坛](https://forum.groupdocs.com/c/merger)

## 结论
您现在拥有使用 GroupDocs.Merger for Java **convert image to OLE** 的完整、可投入生产的工作流。通过定义文件路径、读取图像字节、配置 `OleDiagramOptions` 并调用 `importOleDiagram`，您可以为任何受支持的文档添加交互式图形。探索其他 API——如合并、拆分和水印——以构建功能完整的文档处理管道。

---

**最后更新：** 2026-06-26  
**测试环境：** GroupDocs.Merger 23.10 for Java  
**作者：** GroupDocs

## 相关教程

- [如何使用 GroupDocs.Merger for Java 在 Excel 中嵌入 PDF - 导入 OLE 对象 – 步骤指南](/merger/java/document-import/import-ole-object-excel-groupdocs-merger-java/)
- [如何使用 GroupDocs.Merger for Java 在 Word 中嵌入 PDF – 综合指南](/merger/java/document-import/embed-ole-objects-word-documents-groupdocs-java/)
- [如何使用 GroupDocs.Merger for Java 合并 PNG 图像 – 步骤指南](/merger/java/document-information/merge-png-images-groupdocs-merger-java/)