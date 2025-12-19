---
date: '2025-12-19'
description: 学习如何在 Excel 中嵌入 PDF 并使用 GroupDocs.Merger for Java 将文档导入 Excel。请遵循本详细指南，其中包含代码示例和故障排除技巧。
keywords:
- import OLE object into Excel
- embed PDF in Excel with Java
- use GroupDocs.Merger for document integration
title: 如何使用 GroupDocs.Merger for Java 在 Excel 中嵌入 PDF：导入 OLE 对象 – 步骤指南
type: docs
url: /zh/java/document-import/import-ole-object-excel-groupdocs-merger-java/
weight: 1
---

# 如何使用 GroupDocs.Merger for Java 在 Excel 中嵌入 PDF：一步一步指南

在 Excel 中嵌入 PDF 可以将静态电子表格转变为包含完整源文档的丰富交互式报告，文档就在您需要的地方。本文教程将教您 **如何在 Excel 中嵌入 PDF**，方法是使用 GroupDocs.Merger for Java 将 PDF 作为 OLE（对象链接与嵌入）对象导入。我们将逐一介绍所有前置条件，展示完整代码，并提供实用技巧，让您今天就能在自己的项目中使用此技术。

## 快速答案
- **“在 Excel 中嵌入 PDF” 是什么意思？** 指将 PDF 文件插入为 OLE 对象，以便可以直接从电子表格中打开 PDF。  
- **哪个库负责导入？** GroupDocs.Merger for Java 提供 `importDocument` 方法来完成此操作。  
- **需要许可证吗？** 免费试用可用于评估；生产环境需要商业许可证。  
- **可以嵌入其他文件类型吗？** 可以——Word、图片以及其他受支持的格式也可以作为 OLE 对象导入。  
- **此方法兼容 Java 8+ 吗？** 完全兼容——该库支持 Java 8 及更高版本。

## 什么是将 PDF 嵌入 Excel？
将 PDF 嵌入 Excel 是指将 PDF 存储在工作簿内部，作为 OLE 对象。用户双击该对象即可打开原始 PDF，而无需离开电子表格，这对于审计追踪、详细报告或参考文档尤为理想。

## 为什么使用 GroupDocs.Merger 将文档导入 Excel？
- **无缝集成：** 无需手动复制粘贴文件，API 自动处理位置和尺寸。  
- **自动化就绪：** 非常适合批量处理月度报告或以编程方式生成仪表盘。  
- **跨格式支持：** 支持 PDF、Word 文档、图片等多种格式，全部通过同一个库实现。

## 前置条件
- **Java Development Kit (JDK) 8 或更高版本** – 已在 IDE 中安装并配置。  
- **GroupDocs.Merger for Java** – 通过 Maven 或 Gradle 添加到项目中（见下文）。  
- **IDE** 如 IntelliJ IDEA 或 Eclipse，用于编辑和运行代码。  
- **基本的 Java 文件处理知识** – 您需要处理文件路径和流。

## 设置 GroupDocs.Merger for Java

### Maven
在 `pom.xml` 文件中添加以下依赖：

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle
在 `build.gradle` 文件中引入该库：

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

您也可以直接从 [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/) 下载最新版本。

#### 许可证获取步骤
1. **免费试用：** 开始免费试用以探索全部功能。  
2. **临时许可证：** 申请临时许可证以进行更长时间的测试。  
3. **购买：** 为商业部署获取完整许可证。

## 实现指南

### 步骤 1：定义文件路径并初始化对象
首先，设置 Excel 工作簿、要嵌入的 PDF 以及输出文件的路径。然后创建描述 OLE 对象显示位置的 `OleSpreadsheetOptions`。

```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OleSpreadsheetOptions;

public class ImportOLEToSpreadsheet {
    public static void main(String[] args) throws Exception {
        // Define the paths for input and output files.
        String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.xlsx";  // Excel file path
        String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf";  // PDF file to embed

        // Specify the output file path.
        String filePathOut = "YOUR_OUTPUT_DIRECTORY/ImportDocumentToSpreadsheet-output.xlsx";

        // Specify the page number of the OLE object and its position in the spreadsheet.
        int pageNumber = 2;  
        OleSpreadsheetOptions oleCellsOptions = new OleSpreadsheetOptions(embeddedFilePath, pageNumber);
        
        // Set the desired row and column indices for the OLE object placement.
        oleCellsOptions.setRowIndex(2); 
        oleCellsOptions.setColumnIndex(2);

        // Create a Merger instance for the target Excel file.
        Merger merger = new Merger(filePath);
    }
}
```

### 步骤 2：导入 OLE 文档
使用 `importDocument` 方法在您定义的位置将 PDF 嵌入为 OLE 对象。

```java
// Import the OLE document into the specified position in the spreadsheet.
merger.importDocument(oleCellsOptions);

// Save the updated spreadsheet to the output path.
merger.save(filePathOut);
```

**为什么使用 `importDocument`：** 此方法告诉 GroupDocs.Merger 将 PDF 视为 OLE 对象，既保留原始内容，又能在 Excel 中直接访问。

### 步骤 3：保存电子表格
最后，将更改持久化到新文件，以免修改原始工作簿。

```java
merger.save(filePathOut);
```

**关键配置选项：** 您可以进一步微调 `OleSpreadsheetOptions`——例如调整对象的大小、可见性，或设置为链接而非嵌入。

#### 故障排除提示
- **FileNotFoundException：** 再次确认提供的路径指向实际存在的文件。  
- **版本不匹配：** 确保使用的 GroupDocs.Merger 版本与您的 JDK 版本相匹配。  
- **PDF 损坏：** 在嵌入前先确认 PDF 能独立打开。

## 实际应用场景
在 Excel 中嵌入 OLE 对象在许多情境下都很有用：
1. **数据整合：** 将季度 PDF 合并到单个仪表盘工作簿中。  
2. **交互式演示：** 在会议期间提供可按需打开的详细规格表。  
3. **自动化报告：** 生成包含支持文档的月度财务报表。

## 性能考虑因素
- **内存管理：** 关闭不再使用的 `Merger` 实例以释放资源。  
- **批量处理：** 处理大量电子表格时，分小批次进行，以避免内存峰值。  
- **Java 最佳实践：** 对流使用 try‑with‑resources，并优雅地处理异常。

## 结论
现在，您已经拥有使用 GroupDocs.Merger for Java **在 Excel 中嵌入 PDF** 并 **将文档导入 Excel** 的完整生产级解决方案。尝试不同的文件类型，调整放置选项，并将此工作流集成到自动化报告管道中。

### 后续步骤
- 尝试嵌入 Word 文档或图片，观察 API 对其他格式的处理方式。  
- 探索 GroupDocs.Merger 的其他功能，如拆分、合并或转换文档。

## FAQ 部分

**Q1: 我可以在同一个 Excel 文件中嵌入多个 OLE 对象吗？**  
A1: 可以，通过对每个对象重复导入过程即可实现多对象嵌入。

**Q2: 哪些文件格式被支持作为 OLE 对象？**  
A2: GroupDocs.Merger 支持 PDF、Word 文档、Excel 文件、图片以及其他常见格式。

**Q3: 如何使用 GroupDocs.Merger 高效处理大文件？**  
A3: 通过将文件分批处理并及时释放 `Merger` 实例来优化内存使用。

**Q4: 如果嵌入的文件无法访问或已损坏怎么办？**  
A4: 在尝试嵌入之前先验证源文件的路径和完整性。损坏的文件会在导入时抛出异常。

**Q5: 我可以自定义 OLE 对象在 Excel 中的外观吗？**  
A5: 可以，`OleSpreadsheetOptions` 允许您设置行/列索引、大小和可见性，以定制对象在工作表中的显示方式。

## 资源

- **文档：** [GroupDocs.Merger for Java Documentation](https://docs.groupdocs.com/merger/java/)  
- **API 参考：** [API Reference Guide](https://reference.groupdocs.com/merger/java/)  
- **下载：** [Latest Releases](https://releases.groupdocs.com/merger/java/)  
- **购买：** [Buy GroupDocs.Merger for Java](https://purchase.groupdocs.com/buy)  
- **免费试用：** [Start a Free Trial](https://releases.groupdocs.com/merger/java/)  
- **临时许可证：** [Request a Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **支持：** [GroupDocs Forum](https://forum.groupdocs.com/c/merger/) 

---

**Last Updated:** 2025-12-19  
**Tested With:** GroupDocs.Merger for Java latest-version  
**Author:** GroupDocs