---
date: '2026-06-26'
description: 了解如何使用 GroupDocs.Merger for Java 将 PDF 页面转换为图像并预览文档——快速、可靠的页面缩略图生成方式。
keywords:
- convert pdf pages to images
- document page previews
- GroupDocs.Merger Java
schemas:
- author: GroupDocs
  dateModified: '2026-06-26'
  description: Learn how to convert pdf pages to images and preview documents using
    GroupDocs.Merger for Java – the fast, reliable way to generate page thumbnails.
  headline: How to Convert PDF Pages to Images and Preview Documents with GroupDocs.Merger
    for Java
  type: TechArticle
- questions:
  - answer: It’s used for merging, splitting, and managing documents efficiently,
      including preview generation and format conversion.
    question: What is GroupDocs.Merger for Java used for?
  - answer: Wrap stream creation and closing in try‑catch blocks, as shown in the
      helper methods, to prevent memory leaks.
    question: How do I handle exceptions during stream operations?
  - answer: Yes, change the `PreviewMode` enum to PNG, BMP, or TIFF to suit your requirements.
    question: Can I generate previews in formats other than JPEG?
  - answer: Typical problems include incorrect file paths and forgetting to close
      streams, which can cause memory leaks.
    question: What are common issues with document preview generation?
  - answer: Use its API to connect with databases, web services, or other Java applications
      for seamless workflow automation.
    question: How can I integrate GroupDocs.Merger with other systems?
  type: FAQPage
title: 使用 GroupDocs.Merger for Java 将 PDF 页面转换为图像并预览文档的方法
type: docs
url: /zh/java/document-information/generate-document-page-previews-groupdocs-merger-java/
weight: 1
---

# 如何将 PDF 页面转换为图像并使用 GroupDocs.Merger for Java 预览文档

在现代应用程序中，您经常需要 **将 PDF 页面转换为图像**，以便用户无需下载整个文件即可快速浏览文档。本教程将指导您使用 GroupDocs.Merger for Java 生成高质量的页面预览，涵盖从设置到自定义存储处理的全部内容。完成后，您将拥有一个可在任何 JDK 8+ 环境下运行的文档缩略图生成可复用解决方案。

## 快速答案
- **“预览文档”是什么意思？** 生成每页的轻量级图像表示。  
- **预览使用哪种格式？** 默认是 JPEG，但支持其他格式。  
- **我需要许可证吗？** 免费试用可用于开发；生产环境需要付费许可证。  
- **我可以自定义输出路径吗？** 可以，通过实现自定义 `PageStreamFactory`。  
- **需要哪个 Java 版本？** JDK 8 或更高版本。

## 什么是“预览文档”？
文档预览是指为每页创建可视化缩略图（通常为 JPEG 或 PNG），以便用户快速浏览内容。此技术可提升文件浏览器、内容审查门户以及任何管理大量文档的系统的用户体验，提供快速的视觉提示，而无需打开完整文件。

## 为什么使用 GroupDocs.Merger for Java？
GroupDocs.Merger 能在典型的 2 GHz CPU 上 **每页不到 0.5 秒** 将 PDF 页面转换为图像，支持 **50 多种输入和输出格式**，并且可以直接将预览流式传输到存储，而无需将整个文件加载到内存中。其可扩展的 API 还让您能够完全控制图像质量、格式和目标路径。

## 前置条件
- **GroupDocs.Merger for Java** 库（请参见下面的安装说明）。  
- **JDK 8+** 已在您的机器上安装。  
- 一个 IDE（IntelliJ IDEA、Eclipse、NetBeans）以及用于依赖管理的 Maven 或 Gradle。  

## 设置 GroupDocs.Merger for Java
使用您偏好的构建工具将库添加到项目中。

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

**直接下载:**  
或者，从 [GroupDocs.Merger for Java 发布](https://releases.groupdocs.com/merger/java/) 下载最新版本。

### 许可证获取
- **免费试用：** 首先下载免费试用版以探索功能。  
- **临时许可证：** 在开发期间获取临时许可证以获得更长的访问时间。  
- **购买：** 对于完整的生产使用，请从 [GroupDocs](https://purchase.groupdocs.com/buy) 购买许可证。  

添加库后，使用要预览的文档路径进行初始化：

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

## 如何预览文档：分步指南
加载源文件，配置 `PageStreamFactory`，并调用 `generatePreview`。  
`generatePreview` 是一个根据提供的选项将每个文档页面转换为图像的方法。

### 步骤 1：初始化 Merger 并定义 PageStreamFactory
`Merger` 是提供文档合并、拆分和生成预览方法的核心类。  
`PageStreamFactory` 是一个接口，告诉库每个预览图像写入的位置。

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

这里我们创建一个自定义实现，将每页图像写入具有可预测命名方案的特定文件夹。

```java
IPreviewOptions previewOption = new PreviewOptions(new PageStreamFactory() {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        return createStream(pageNumber);
    }
    
    @Override
    public void closePageStream(int pageNumber, OutputStream pageStream) {
        releasePageStream(pageNumber, pageStream);
    }
}, PreviewMode.JPEG);
```

### 步骤 2：生成预览
`generatePreview` 根据您提供的选项触发转换过程。它将每页图像流式传输到您定义的 `PageStreamFactory`，确保低内存使用。

```java
merger.generatePreview(previewOption);
```

### 将页面转换为图像 – 自定义 PageStreamFactory
如果您需要对文件命名或存储位置进行更多控制，请实现您自己的工厂：

```java
class CustomPageStreamFactory implements PageStreamFactory {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        String filePath = "YOUR_OUTPUT_DIRECTORY/image-" + pageNumber + ".jpg";
        return new FileOutputStream(filePath);
    }
    
    @Override
    public void closePageStream(int pageNumber, OutputStream pageStream) {
        try {
            if (pageStream != null) {
                pageStream.close();
            }
        } catch (Exception e) {
            throw new RuntimeException(e);
        }
    }
}
```

### 辅助方法 – 管理流
这些实用方法保持代码整洁，并干净地处理异常。

```java
private static String getImagePath(int pageNumber) {
    return "YOUR_OUTPUT_DIRECTORY/image-" + pageNumber + ".jpg";
}

private static OutputStream createStream(int pageNumber) {
    try {
        String imageFilePath = getImagePath(pageNumber);
        return new FileOutputStream(imageFilePath);
    } catch (FileNotFoundException e) {
        throw new RuntimeException(e);
    }
}

private static void releasePageStream(int pageNumber, OutputStream pageStream) {
    try {
        if (pageStream != null) {
            pageStream.close();
        }
    } catch (Exception e) {
        throw new RuntimeException(e);
    }
}
```

## 文档缩略图生成 – 实际应用
生成预览尤其有用在以下场景：

1. **文档管理系统** – 用户可以在不打开文件的情况下快速浏览。  
2. **内容审查平台** – 在批准上传之前进行快速的视觉检查。  
3. **教育工具** – 学生可以快速浏览讲义幻灯片或教材页面。  

## 性能考虑因素
- **及时释放流** 以释放内存。  
- **避免将整个文档加载到内存**；让库处理分页。  
- **使用适当的图像质量** 设置，以在速度和视觉保真度之间取得平衡。  

## 常见问题
**问：GroupDocs.Merger for Java 用于什么？**  
答：它用于高效地合并、拆分和管理文档，包括预览生成和格式转换。

**问：如何在流操作期间处理异常？**  
答：如辅助方法所示，将流的创建和关闭包装在 try‑catch 块中，以防止内存泄漏。

**问：我可以生成除 JPEG 之外的其他格式的预览吗？**  
答：可以，将 `PreviewMode` 枚举更改为 PNG、BMP 或 TIFF，以满足您的需求。

**问：文档预览生成的常见问题有哪些？**  
答：常见问题包括文件路径不正确以及忘记关闭流，这可能导致内存泄漏。

**问：如何将 GroupDocs.Merger 与其他系统集成？**  
答：使用其 API 与数据库、Web 服务或其他 Java 应用程序连接，实现无缝的工作流自动化。

---

## 资源
- [GroupDocs.Merger for Java 发布](https://releases.groupdocs.com/merger/java/)  
- [下载](https://releases.groupdocs.com/merger/java/)  
- [文档](https://docs.groupdocs.com/merger/java/)  
- [API 参考](https://reference.groupdocs.com/merger/java/)  
- [免费试用](https://releases.groupdocs.com/merger/java/)  
- [临时许可证](https://purchase.groupdocs.com/temporary-license/)  
- [购买](https://purchase.groupdocs.com/buy)  
- [GroupDocs](https://purchase.groupdocs.com/buy)  
- [支持](https://forum.groupdocs.com/c/merger/)  

**最后更新：** 2026-06-26  
**测试环境：** GroupDocs.Merger latest version (2025‑latest)  
**作者：** GroupDocs

## 相关教程
- [GroupDocs.Merger Java 文档页面操作教程](/merger/java/page-operations/)  
- [如何使用 GroupDocs.Merger for Java 从 URL 加载 PDF：综合指南](/merger/java/document-loading/load-pdf-url-groupdocs-merger-java/)  
- [使用 GroupDocs.Merger Java 创建单页 PDF](/merger/java/document-splitting/)