---
date: '2025-12-19'
description: 學習如何在 Word 文件中嵌入 PDF，並使用 GroupDocs.Merger for Java 將 PDF 添加至 Word 檔案。一步一步的教學，實現無縫
  OLE 嵌入。
keywords:
- embed OLE objects in Word documents
- GroupDocs Merger for Java tutorial
- import OLE objects using Java
title: 如何使用 GroupDocs.Merger for Java 在 Word 中嵌入 PDF – 全面指南
type: docs
url: /zh-hant/java/document-import/embed-ole-objects-word-documents-groupdocs-java/
weight: 1
---

# 如何使用 GroupDocs.Merger for Java 在 Word 中嵌入 pdf

將 PDF 直接嵌入 Word 文件中可以大幅提升協作，因為讀者不再需要在檔案之間切換。在本指南中，您將了解 **如何在 word 中嵌入 pdf**，使用 GroupDocs.Merger for Java，並看到關於 **將 pdf 加入 word** 工作流程的實用技巧。我們將從設定函式庫到自訂 OLE 物件的大小與位置，逐步說明。

## 快速解答
- **需要的函式庫是什麼？** GroupDocs.Merger for Java (latest version)  
- **我可以嵌入任何檔案類型嗎？** Yes – PDFs, images, spreadsheets, etc., as OLE objects  
- **我需要授權嗎？** A free trial works for development; a commercial license is required for production  
- **哪個 Java IDE 最適合？** IntelliJ IDEA, Eclipse, or any IDE that supports Maven/Gradle  
- **實作需要多長時間？** Roughly 10‑15 minutes for a basic embed  

## 什麼是將 pdf 嵌入 word？
將 PDF 嵌入會在 Word 檔案中建立 OLE（Object Linking and Embedding）物件。PDF 仍然保持完整功能——使用者可以雙擊圖示在 PDF 檢視器中開啟，同時 Word 文件保持自包含。

## 為什麼使用 GroupDocs.Merger 將 pdf 加入 word？
- **單一來源文件：** Keep contracts, manuals, or reports together without external links.  
- **提升可及性：** Readers can view the PDF without leaving the Word environment.  
- **自動化友好：** Perfect for generating batch reports or legal packages programmatically.  

## 前置條件
- **函式庫與相依性：** Include the GroupDocs.Merger library via Maven or Gradle.  
- **開發環境：** IntelliJ IDEA, Eclipse, or any Java IDE.  
- **基本知識：** Familiarity with Java and document manipulation concepts.  

## 設定 GroupDocs.Merger for Java
要嵌入 OLE 物件，首先將函式庫加入您的專案。

### Maven
將此相依性加入您的 `pom.xml` 檔案：
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle
在您的 `build.gradle` 檔案中加入以下內容：
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### 直接下載
或者，從 [GroupDocs.Merger for Java releases page](https://releases.groupdocs.com/merger/java/) 下載最新版本。

**授權取得：** 您可以先使用免費試用版，或取得臨時授權以評估功能後再購買。前往 [Purchase GroupDocs](https://purchase.groupdocs.com/buy) 了解更多資訊。

## 基本初始化
匯入所需的類別，以便處理 OLE 物件：
```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OleWordProcessingOptions;
```

## 步驟指南：將 pdf 嵌入 word

### 步驟 1：定義檔案路徑與目標頁面
設定來源 Word 文件、欲嵌入的 PDF，以及 OLE 物件要顯示的位置。
```java
String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.docx"; // Source Word document path
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf"; // File to be embedded as an OLE object
String outputFilePath = new File("YOUR_OUTPUT_DIRECTORY",
    "ImportDocumentToWordProcessing-" + Paths.get(sourceFilePath).getFileName().toString()).getPath();
int pageNumber = 2; // Page number where the OLE object will be inserted
```

- **`sourceFilePath`** – path to the existing Word file.  
- **`embeddedFilePath`** – the PDF you want to **將 pdf 加入 word**.  
- **`outputFilePath`** – where the new document will be saved.  
- **`pageNumber`** – the page that will host the OLE object.  

### 步驟 2：設定 OleWordProcessingOptions
透過設定尺寸，自訂嵌入 PDF 的外觀。
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Set width of the embedded object (in points)
oleWordsOptions.setHeight(300); // Set height of the embedded object (in points)
```

- **`setWidth()` / `setHeight()`** – control how large the PDF icon appears inside the Word document.  

### 步驟 3：初始化 Merger 並匯入 OLE 物件
為來源文件建立 `Merger` 實例，匯入 OLE 物件，並儲存結果。
```java
Merger merger = new Merger(sourceFilePath);
{
    merger.importDocument(oleWordsOptions); // Embed the OLE object into the Word document
    merger.save(outputFilePath); // Save changes to a new output file
}
```

- **`importDocument()`** – takes the `OleWordProcessingOptions` and inserts the PDF as an OLE object.  
- **`save()`** – writes the modified document to `outputFilePath`.  

### 步驟 4：（可選）重新套用設定以加入更多物件
如果需要嵌入更多 PDF，請使用新的檔案路徑與頁碼，重複 **步驟 1‑3**。相同的 `OleWordProcessingOptions` 類別可讓您個別控制每個物件。

## 設定 OleWordProcessingOptions（進階）
您還可以進一步調整放置方式，例如對齊物件或加入說明文字。以下程式碼片段重複基本設定以示說明：
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Width of the embedded object
oleWordsOptions.setHeight(300); // Height of the embedded object
```

## 實務應用
在許多實務情境中，嵌入 PDF 都相當有用：

1. **Technical Manuals** – Insert detailed schematics or reference PDFs directly into the guide.  
2. **Financial Reports** – Add supplemental audit PDFs without breaking the flow of the main report.  
3. **Legal Contracts** – Attach annexes or exhibits as OLE objects for easy access during review.  

## 效能考量
處理大型文件或多個 OLE 物件時，請留意以下建議：

- **Trim unnecessary content** – embed only the pages you really need.  
- **Manage memory** – use Java’s `-Xmx` flag to allocate sufficient heap space for big files.  
- **Stay up‑to‑date** – newer GroupDocs.Merger releases often include performance optimizations.  

## 常見問題

**Q: 什麼是 OLE 嵌入？**  
A: 嵌入允許您將 PDF 等物件插入 Word 文件，作為保留原始功能的連結。

**Q: 我可以在同一文件中嵌入多個 OLE 物件嗎？**  
A: 可以，每個物件皆可使用不同的 `OleWordProcessingOptions` 進行頁面與尺寸的設定。

**Q: 嵌入檔案的大小有上限嗎？**  
A: 限制通常由 Word 本身的限制決定，但 GroupDocs.Merger 能有效處理大型檔案。

**Q: 我該如何解決嵌入錯誤？**  
A: 請確認檔案路徑正確且 JVM 記憶體足夠。亦需檢查來源 PDF 是否損毀。

**Q: 插入後我可以修改嵌入的物件嗎？**  
A: 您可以在 Microsoft Word 中重新開啟該文件並編輯 OLE 物件，或使用更新的選項重新執行 Merger 程式碼。

## 其他資源
- [GroupDocs.Merger Documentation](https://docs.groupdocs.com/merger/java/)
- [API Reference](https://reference.groupdocs.com/merger/java/)
- [Download Latest Version](https://releases.groupdocs.com/merger/java/)
- [Purchase GroupDocs](https://purchase.groupdocs.com/buy)
- [Free Trial](https://releases.groupdocs.com/merger/java/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [Support Forum](https://forum.groupdocs.com/c/merger/)

---

**最後更新：** 2025-12-19  
**測試環境：** GroupDocs.Merger for Java latest version  
**作者：** GroupDocs