---
date: '2026-07-06'
description: 了解如何使用 GroupDocs.Merger for Java 检索受支持的文件类型，检查 supported extensions java，并将该列表集成到您的工作流中。
keywords:
- groupdocs merger supported formats
- check supported extensions java
- how to get supported file types java
schemas:
- author: GroupDocs
  dateModified: '2026-07-06'
  description: Learn how to retrieve supported file types with GroupDocs.Merger for
    Java, check supported extensions java, and integrate the list into your workflow.
  headline: GroupDocs.Merger Supported Formats – Retrieve Types in Java
  type: TechArticle
- description: Learn how to retrieve supported file types with GroupDocs.Merger for
    Java, check supported extensions java, and integrate the list into your workflow.
  name: GroupDocs.Merger Supported Formats – Retrieve Types in Java
  steps:
  - name: Obtain Supported File Types
    text: 'First, retrieve the list of supported file types from the `FileType` class:
      This method returns a list containing all the file types that GroupDocs.Merger
      supports.'
  - name: Display Supported Extensions
    text: 'Next, iterate through each `FileType` object and print its extension. This
      is the part where we **display supported extensions** for developers or end‑users:
      The loop goes through each supported file type and outputs its extension to
      the console.'
  - name: Confirmation Message
    text: 'Finally, output a confirmation message indicating successful retrieval:'
  type: HowTo
- questions:
  - answer: It’s a Java library that enables merging, splitting, and converting a
      wide range of document formats without requiring Microsoft Office.
    question: What is GroupDocs.Merger for Java?
  - answer: Add the Maven or Gradle dependency, obtain a trial or full license, and
      initialize the library as shown in the setup section.
    question: How do I get started with GroupDocs.Merger?
  - answer: Yes, a free trial is available for evaluation; a full license is required
      for production deployments.
    question: Can I use GroupDocs.Merger for free?
  - answer: Use the `FileType.getSupportedFileTypes()` method to retrieve a list of
      **70+** supported formats, including PDF, DOCX, PPTX, XLSX, HTML, and image
      types.
    question: What file types does GroupDocs.Merger support?
  - answer: Validate uploads against the supported list before processing; reject
      or convert unsupported files early to avoid runtime errors.
    question: How do I handle unsupported file types?
  type: FAQPage
title: GroupDocs.Merger 支持的格式 – 在 Java 中检索类型
type: docs
url: /zh/java/document-information/retrieve-supported-file-types-groupdocs-merger-java/
weight: 1
---

# GroupDocs.Merger 支持的格式 – 在 Java 中检索类型

在 Java 中处理各种文档格式如果不知道库实际支持哪些格式，很快会变成头疼的事。**GroupDocs.Merger 支持的格式** 为您提供可靠的参考点，让您能够验证上传、避免运行时错误，并设计更智能的文档管理流水线。在本教程中，您将看到如何使用 GroupDocs.Merger for Java 检索受支持文件类型的列表，了解其重要性，以及如何将该信息整合到实际应用中。

### 快速答案
- **检索受支持的文件类型 是做什么的？**  
  它返回 GroupDocs.Merger 可以处理的每种文档格式的列表。
- **哪个方法提供此列表？**  
  `FileType.getSupportedFileTypes()` 来自 `com.groupdocs.merger.domain` 包。
- **调用此方法是否需要许可证？**  
  在生产环境中需要试用版或正式许可证；该方法在评估模式下也可工作。
- **我可以仅筛选出需要的扩展名吗？**  
  是的——遍历返回的列表并保留您关心的扩展名。
- **此操作是否性能密集？**  
  不，它仅读取静态集合，运行几乎是瞬时的。

## GroupDocs.Merger 支持的格式有哪些？

GroupDocs.Merger 支持 **70+** 输入和输出格式——包括 PDF、DOCX、PPTX、XLSX、HTML 以及常见的图像类型——让您几乎可以处理任何业务文档。库的格式表内部存储为静态集合，因此获取它是 O(1) 操作，只需几毫秒即可完成，即使在普通硬件上也是如此。

## 如何在 Java 中检查受支持的扩展名？

调用静态的 `FileType.getSupportedFileTypes()` 方法，然后遍历返回的集合读取每个扩展名。此单行调用为您提供一个可直接使用的 `List<FileType>`，您可以对其进行筛选、显示或存储以供后续验证。

## 为什么在处理之前检索受支持的文件类型？

了解确切的格式列表可以防止可避免的异常，减少防御性编码的需求，并让您向用户展示明确的“允许的文件类型”提示。它还使您能够构建动态 UI 组件——例如仅显示兼容扩展名的文件选择过滤器——从而提升整体用户体验。

## 前置条件

- **Java Development Kit (JDK)：** 推荐使用 8 版或更高版本。  
- **Integrated Development Environment (IDE)：** 任意 IDE，如 IntelliJ IDEA 或 Eclipse 都可使用。  
- **GroupDocs.Merger Library：** 在项目依赖中包含此库。  

熟悉基本的 Java 编程概念并有在 Maven 或 Gradle 环境中使用库的经验也很有帮助。如果您是这些工具的新手，建议先查阅它们的文档。

## 为 Java 设置 GroupDocs.Merger

要在 Java 中使用 GroupDocs.Merger，请使用 Maven、Gradle 或直接从官方网站下载来在项目中设置该库。

### Maven 安装

Add the following dependency to your `pom.xml` file:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle 安装

Include this line in your `build.gradle` file:

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### 直接下载

或者，从 [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/) 下载最新版本。

#### 许可证获取步骤
1. **Free Trial：** 首先使用免费试用来探索库的功能。  
2. **Temporary License：** 如果需要无限制的扩展访问，可获取临时许可证。  
3. **Purchase：** 考虑购买正式许可证以进行长期使用。

## 基本初始化和设置

To initialize GroupDocs.Merger in your Java application, import the necessary classes:

```java
import com.groupdocs.merger.domain.FileType;
```

现在，让我们继续实现检索受支持文件类型的功能。

## 什么是 FileType 类？

`FileType` 类是 GroupDocs.Merger 中的核心模型，表示单个文档格式，公开其扩展名、MIME 类型和友好的显示名称。当您调用 `FileType.getSupportedFileTypes()` 获取完整格式目录时，会与此类交互。

## 如何检索受支持的文件类型？

要检索受支持的格式，只需调用 GroupDocs.Merger 库提供的静态方法 `FileType.getSupportedFileTypes()`。此调用返回一个包含库可处理的所有格式的 `List<FileType>`。该操作轻量，可在应用启动时或任何需要验证文件上传时执行。

### 步骤 1：获取受支持的文件类型

First, retrieve the list of supported file types from the `FileType` class:

```java
List<FileType> fileTypes = FileType.getSupportedFileTypes();
```

此方法返回一个包含 GroupDocs.Merger 支持的所有文件类型的列表。

### 步骤 2：显示受支持的扩展名

Next, iterate through each `FileType` object and print its extension. This is the part where we **display supported extensions** for developers or end‑users:

```java
for (FileType fileType : fileTypes) {
    System.out.println(fileType.getExtension());
}
```

接下来，遍历每个 `FileType` 对象并打印其扩展名。这就是我们为开发者或终端用户 **显示受支持的扩展名** 的部分：

### 步骤 3：确认信息

Finally, output a confirmation message indicating successful retrieval:

```java
System.out.println("Supported file types retrieved successfully.");
```

最后，输出一条确认信息，表明检索成功：

## 实际应用

了解受支持的文件类型对各种应用至关重要：
1. **Document Management Systems：** 根据类型自动对文档进行分类。  
2. **File Conversion Tools：** 在文件格式转换前确保兼容性。  
3. **Merging Applications：** 在合并前验证输入文件以防错误。  

与其他系统的集成——例如云存储或文档处理服务——可以进一步提升功能。

## 性能注意事项

When working with GroupDocs.Merger in Java, consider the following performance tips:
- **Optimize Memory Usage：** 在对象不再需要时释放它们。  
- **Batch Processing：** 批量处理文件以降低资源消耗。  
- **Asynchronous Operations：** 使用异步方法实现非阻塞操作。  

## 常见问题及解决方案

- **Dependency Issues：** 验证 Maven 或 Gradle 依赖是否正确声明；版本不匹配会导致类未找到错误。  
- **Library Version：** 始终使用最新的 GroupDocs.Merger 版本，以获得新添加的格式和错误修复。  
- **License Errors：** 如果看到许可证异常，请确认在代码中正确引用了试用或永久许可证文件。  

## 常见问答

**Q：GroupDocs.Merger for Java 是什么？**  
A：它是一个 Java 库，能够在无需 Microsoft Office 的情况下合并、拆分和转换多种文档格式。

**Q：如何开始使用 GroupDocs.Merger？**  
A：添加 Maven 或 Gradle 依赖，获取试用或正式许可证，并按照设置章节所示初始化库。

**Q：我可以免费使用 GroupDocs.Merger 吗？**  
A：是的，提供免费试用供评估；生产部署需要正式许可证。

**Q：GroupDocs.Merger 支持哪些文件类型？**  
A：使用 `FileType.getSupportedFileTypes()` 方法可检索 **70+** 支持的格式列表，包括 PDF、DOCX、PPTX、XLSX、HTML 和图像类型。

**Q：如何处理不受支持的文件类型？**  
A：在处理之前根据受支持列表验证上传；对不受支持的文件进行拒绝或转换，以避免运行时错误。

**Q：我可以仅筛选出需要的扩展名吗？**  
A：可以。在调用 `getSupportedFileTypes()` 后，遍历列表并保留您关心的扩展名。

**Q：开发构建是否需要许可证？**  
A：开发和测试可使用试用许可证；商业生产使用需正式许可证。

**Q：此方法会影响应用启动时间吗？**  
A：不会。受支持的文件类型列表是静态的，检索几乎是瞬时的。

**Q：随着新库版本，列表会变化吗？**  
A：新版本可能会添加或弃用格式；请始终使用最新版本以获取最新列表。

## 资源
- [文档](https://docs.groupdocs.com/merger/java/)
- [API 参考](https://reference.groupdocs.com/merger/java/)
- [下载](https://releases.groupdocs.com/merger/java/)
- [购买](https://purchase.groupdocs.com/buy)
- [免费试用](https://releases.groupdocs.com/merger/java/)
- [临时许可证](https://purchase.groupdocs.com/temporary-license/)
- [支持](https://forum.groupdocs.com/c/merger/) 

欢迎探索这些资源以获取更详细的信息和支持。祝编码愉快！

---

**最后更新：** 2026-07-06  
**测试环境：** GroupDocs.Merger 最新版本（截至 2026 年）  
**作者：** GroupDocs  

---

## 相关教程

- [GroupDocs.Merger for Java：许可证设置与文件存在性检查指南](/merger/java/licensing/groupdocs-merger-java-license-setup-file-existence-checks/)
- [使用 GroupDocs.Merger 加载本地文档 Java – 指南](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)
- [合并特定页面 Java – GroupDocs.Merger 文档合并教程](/merger/java/document-joining/)