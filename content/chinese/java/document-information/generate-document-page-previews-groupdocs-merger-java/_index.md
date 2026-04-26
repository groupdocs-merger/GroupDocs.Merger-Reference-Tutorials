---
date: '2026-01-24'
description: 了解如何使用 GroupDocs.Merger for Java 通过生成页面预览来预览文档，这是一种将页面转换为图像以生成文档缩略图的快速方法。
keywords:
- GroupDocs.Merger for Java
- document page previews
- Java document management
title: 如何使用 GroupDocs.Merger for Java 预览文档
type: docs
url: /zh/java/document-information/generate-document-page-previews-groupdocs-merger-java/
weight: 1
---

# 如何使用 GroupDocs.Merger for Java 预览文档

创建文档页面预览是一种快速 **how to preview documents** 的强大方式，能够在不打开完整文件的情况下为用户提供可视化的快照。在本教程中，您将学习如何使用 GroupDocs.Merger for Java 生成这些预览，该库可以轻松 **convert pages to images** 并支持在您的应用程序中 **document thumbnail generation**。

## 快速答案
- **“preview documents” 是什么意思？** 生成每页的轻量级图像表示。  
- **预览使用哪种格式？** 默认使用 JPEG，但也支持其他格式。  
- **我需要许可证吗？** 免费试用可用于开发；生产环境需要付费许可证。  
- **我可以自定义输出路径吗？** 可以，通过实现自定义 `PageStreamFactory`。  
- **需要哪个 Java 版本？** JDK 8 或更高版本。

## 什么是 “how to preview documents”？
预览文档是指为每页创建可视化缩略图（通常为 JPEG 或 PNG），以便用户快速浏览内容。这种技术可提升文档管理系统、门户以及任何处理大量文件的应用的用户体验。

## 为什么使用 GroupDocs.Merger for Java？
- **快速转换** 将页面转换为图像，而无需在 UI 中打开完整文档。  
- **内置支持** 支持多种格式（PDF、DOCX、XLSX 等）。  
- **可扩展的 API** 让您控制预览文件的保存位置和方式。  

## 前置条件
- **GroupDocs.Merger for Java** 库（见下方安装）。  
- 已在机器上安装 **JDK 8+**。  
- 一个 IDE（IntelliJ IDEA、Eclipse、NetBeans）以及用于依赖管理的 Maven 或 Gradle。  

## 设置 GroupDocs.Merger for Java
使用您喜欢的构建工具将库添加到项目中。

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
或者，从 [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/) 下载最新版本。

### 获取许可证
- **免费试用：** 首先下载免费试用版以探索功能。  
- **临时许可证：** 获取临时许可证以在开发期间获得更长的访问权限。  
- **购买：** 对于完整的生产使用，请从 [GroupDocs](https://purchase.groupdocs.com/buy) 购买许可证。

库添加后，使用要预览的文档路径进行初始化：

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

## 如何预览文档：分步指南

### 步骤 1：初始化 Merger 并定义 PageStreamFactory
`PageStreamFactory` 告诉库每个预览图像的写入位置。

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

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
调用 `generatePreview` 方法并传入您刚配置的选项。

```java
merger.generatePreview(previewOption);
```

### 将页面转换为图像 – 自定义 PageStreamFactory
如果您需要对文件命名或存储位置进行更细粒度的控制，请实现您自己的工厂：

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
生成预览尤其适用于：

1. **文档管理系统** – 用户可以在不打开文件的情况下快速浏览。  
2. **内容审查平台** – 在批准上传之前进行快速的视觉检查。  
3. **教育工具** – 学生可以快速浏览讲义幻灯片或教材页面。  

## 性能考虑
- **及时释放流** 以释放内存。  
- **避免将整个文档加载** 到内存中；让库处理分页。  
- **使用适当的图像质量** 设置，以在速度和视觉保真度之间取得平衡。  

## 常见问题

**Q: GroupDocs.Merger for Java 用于什么？**  
A: 它用于高效地合并、拆分和管理文档，包括预览生成。

**Q: 如何在流操作期间处理异常？**  
A: 像辅助方法中展示的那样，将流的创建和关闭包装在 try‑catch 块中。

**Q: 我可以生成除 JPEG 之外格式的预览吗？**  
A: 可以，将 `PreviewMode` 枚举更改为 PNG、BMP 等，以满足您的需求。

**Q: 文档预览生成的常见问题是什么？**  
A: 常见问题包括文件路径不正确以及未关闭流，这可能导致内存泄漏。

**Q: 如何将 GroupDocs.Merger 与其他系统集成？**  
A: 使用其 API 与数据库、Web 服务或其他 Java 应用程序连接，实现无缝的工作流自动化。

## 其他资源
- [文档](https://docs.groupdocs.com/merger/java/)
- [API 参考](https://reference.groupdocs.com/merger/java/)
- [下载](https://releases.groupdocs.com/merger/java/)
- [购买](https://purchase.groupdocs.com/buy)
- [免费试用](https://releases.groupdocs.com/merger/java/)
- [临时许可证](https://purchase.groupdocs.com/temporary-license/)
- [支持](https://forum.groupdocs.com/c/merger/)

---

**最后更新：** 2026-01-24  
**测试使用：** GroupDocs.Merger latest version (2025‑latest)  
**作者：** GroupDocs