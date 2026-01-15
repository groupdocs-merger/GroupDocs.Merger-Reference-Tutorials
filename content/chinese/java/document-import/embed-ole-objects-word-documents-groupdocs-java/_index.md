---
date: '2025-12-19'
description: 了解如何使用 GroupDocs.Merger for Java 将 PDF 嵌入 Word 文档并将 PDF 添加到 Word 文件。一步步教程，实现无缝
  OLE 嵌入。
keywords:
- embed OLE objects in Word documents
- GroupDocs Merger for Java tutorial
- import OLE objects using Java
title: 使用 GroupDocs.Merger for Java 将 PDF 嵌入 Word 的完整指南
type: docs
url: /zh/java/document-import/embed-ole-objects-word-documents-groupdocs-java/
weight: 1
---

# 如何使用 GroupDocs.Merger for Java 在 Word 中嵌入 PDF

将 PDF 直接嵌入 Word 文档可以显著提升协作，因为阅读者无需在文件之间切换。在本指南中，您将了解使用 GroupDocs.Merger for Java **如何在 Word 中嵌入 PDF** 文档，并看到关于 **将 PDF 添加到 Word** 工作流的实用技巧。我们将从库的设置到 OLE 对象的大小和位置自定义，逐步演示全部过程。

## 快速回答
- **需要的库是什么？** GroupDocs.Merger for Java (latest version)  
- **我可以嵌入任何文件类型吗？** 是的 – PDFs, images, spreadsheets, etc., as OLE objects  
- **我需要许可证吗？** 免费试用可用于开发；生产环境需要商业许可证  
- **哪款 Java IDE 最适合？** IntelliJ IDEA, Eclipse, or any IDE that supports Maven/Gradle  
- **实现需要多长时间？** 基本嵌入大约需要 10‑15 分钟  

## 什么是 Word 中嵌入 PDF？
将 PDF 嵌入会在 Word 文件中创建一个 OLE（对象链接与嵌入）对象。该 PDF 保持完整功能——用户可以双击图标在 PDF 查看器中打开，同时 Word 文档保持自包含。

## 为什么使用 GroupDocs.Merger 将 PDF 添加到 Word？
- **单一来源文档：** 将合同、手册或报告集中在一起，无需外部链接。  
- **提升可访问性：** 阅读者可以在不离开 Word 环境的情况下查看 PDF。  
- **自动化友好：** 非常适合以编程方式生成批量报告或法律文档包。  

## 前置条件
- **库与依赖：** 通过 Maven 或 Gradle 引入 GroupDocs.Merger 库。  
- **开发环境：** IntelliJ IDEA、Eclipse 或任何 Java IDE。  
- **基础知识：** 熟悉 Java 以及文档操作概念。  

## 设置 GroupDocs.Merger for Java
要嵌入 OLE 对象，首先将库添加到项目中。

### Maven
在你的 `pom.xml` 文件中添加以下依赖：
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle
在你的 `build.gradle` 文件中加入以下内容：
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### 直接下载
或者，从 [GroupDocs.Merger for Java releases page](https://releases.groupdocs.com/merger/java/) 下载最新版本。

**许可证获取：** 您可以使用免费试用开始，或获取临时许可证以在购买前评估功能。访问 [Purchase GroupDocs](https://purchase.groupdocs.com/buy) 获取更多详情。

## 基本初始化
导入所需的类，以便处理 OLE 对象：
```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OleWordProcessingOptions;
```

## 步骤指南：在 Word 中嵌入 PDF

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
- **`embeddedFilePath`** – 您想要 **将 PDF 添加到 Word** 的 PDF 文件。  
- **`outputFilePath`** – 新文档保存的位置。  
- **`pageNumber`** – 将承载 OLE 对象的页码。  

### 步骤 2：配置 OleWordProcessingOptions
通过设置尺寸来自定义嵌入 PDF 的外观。
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Set width of the embedded object (in points)
oleWordsOptions.setHeight(300); // Set height of the embedded object (in points)
```

- **`setWidth()` / `setHeight()`** – 控制 PDF 图标在 Word 文档中显示的大小。  

### 步骤 3：初始化 Merger 并导入 OLE 对象
为源文档创建 `Merger` 实例，导入 OLE 对象，并保存结果。
```java
Merger merger = new Merger(sourceFilePath);
{
    merger.importDocument(oleWordsOptions); // Embed the OLE object into the Word document
    merger.save(outputFilePath); // Save changes to a new output file
}
```

- **`importDocument()`** – 接受 `OleWordProcessingOptions` 并将 PDF 插入为 OLE 对象。  
- **`save()`** – 将修改后的文档写入 `outputFilePath`。  

### 步骤 4：（可选）为额外对象重新应用配置
如果需要嵌入更多 PDF，请使用新的文件路径和页码重复 **步骤 1‑3**。相同的 `OleWordProcessingOptions` 类可让您单独控制每个对象。

## 配置 OleWordProcessingOptions（高级）
您可以进一步微调位置，例如对齐对象或添加标题。下面的代码片段重复了基本配置以便说明清晰：
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Width of the embedded object
oleWordsOptions.setHeight(300); // Height of the embedded object
```

## 实际应用
在许多实际场景中嵌入 PDF 非常有用：

1. **技术手册** – 将详细的原理图或参考 PDF 直接插入指南。  
2. **财务报告** – 添加补充审计 PDF，而不打断主报告的连贯性。  
3. **法律合同** – 将附件或展品作为 OLE 对象附加，便于审阅时快速访问。  

## 性能考虑
处理大型文档或多个 OLE 对象时，请牢记以下提示：

- **裁剪不必要的内容** – 仅嵌入真正需要的页面。  
- **管理内存** – 使用 Java 的 `-Xmx` 标志为大文件分配足够的堆空间。  
- **保持更新** – 新版 GroupDocs.Merger 通常包含性能优化。  

## 常见问题

**问：什么是 OLE 嵌入？**  
**答：** 嵌入允许您将 PDF 等对象作为链接插入 Word 文档，保持其原有功能。

**问：我可以在一个文档中嵌入多个 OLE 对象吗？**  
**答：** 可以，每个对象可以使用单独的 `OleWordProcessingOptions` 配置不同的页码和尺寸。

**问：嵌入文件的大小有限制吗？**  
**答：** 限制通常由 Word 本身的约束决定，但 GroupDocs.Merger 能高效处理大文件。

**问：如何解决嵌入错误？**  
**答：** 确认文件路径正确且 JVM 有足够的内存。检查源 PDF 是否损坏。

**问：插入后我可以修改嵌入的对象吗？**  
**答：** 您可以在 Microsoft Word 中重新打开该 Word 文件并编辑 OLE 对象，或使用更新的选项重新运行 Merger 代码。

## 其他资源
- [GroupDocs.Merger Documentation](https://docs.groupdocs.com/merger/java/)
- [API Reference](https://reference.groupdocs.com/merger/java/)
- [Download Latest Version](https://releases.groupdocs.com/merger/java/)
- [Purchase GroupDocs](https://purchase.groupdocs.com/buy)
- [Free Trial](https://releases.groupdocs.com/merger/java/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [Support Forum](https://forum.groupdocs.com/c/merger/)

---

**最后更新：** 2025-12-19  
**测试环境：** GroupDocs.Merger for Java 最新版本  
**作者：** GroupDocs