---
date: '2025-12-19'
description: 了解如何在 Excel 中嵌入 PDF，並使用 GroupDocs.Merger for Java 將文件匯入 Excel。請參考本詳細指南，內含程式碼範例與故障排除技巧。
keywords:
- import OLE object into Excel
- embed PDF in Excel with Java
- use GroupDocs.Merger for document integration
title: 如何使用 GroupDocs.Merger for Java 在 Excel 中嵌入 PDF：匯入 OLE 物件 – 步驟教學
type: docs
url: /zh-hant/java/document-import/import-ole-object-excel-groupdocs-merger-java/
weight: 1
---

# 如何使用 GroupDocs.Merger for Java 在 Excel 中嵌入 PDF：一步一步指南

將 PDF 嵌入 Excel 可以把靜態試算表變成一個富含互動性的報告，完整的原始文件就直接出現在需要的地方。在本教學中，你將學習 **how to embed PDF in Excel**，透過 GroupDocs.Merger for Java 將 PDF 以 OLE（Object Linking and Embedding）物件匯入。我們會逐一說明所有前置條件、展示完整程式碼，並提供實用技巧，讓你今天就能在自己的專案中使用此技術。

## 快速回答
- **“embed PDF in Excel” 是什麼意思？** 它表示將 PDF 檔案插入為 OLE 物件，讓使用者可以直接從試算表開啟 PDF。  
- **哪個函式庫負責匯入？** GroupDocs.Merger for Java 提供 `importDocument` 方法來完成此工作。  
- **我需要授權嗎？** 免費試用可用於評估；正式上線需購買商業授權。  
- **我可以嵌入其他檔案類型嗎？** 可以——Word、圖片及其他支援格式亦可作為 OLE 物件匯入。  
- **此方法是否相容於 Java 8+？** 完全相容——此函式庫支援 Java 8 及更新版本。

## 什麼是將 PDF 嵌入 Excel？
將 PDF 嵌入 Excel 會把 PDF 儲存在活頁簿內部，作為 OLE 物件。使用者只要雙擊該物件，即可在不離開試算表的情況下開啟原始 PDF，這對於稽核追蹤、詳細報告或參考文件非常理想。

## 為什麼要使用 GroupDocs.Merger 將文件匯入 Excel？
- **Seamless integration:** 無需手動複製貼上檔案；API 會自動處理位置與尺寸。  
- **Automation‑ready:** 非常適合批次處理月報或程式化產生儀表板。  
- **Cross‑format support:** 支援 PDF、Word 文件、圖片等多種格式，全部透過同一函式庫完成。

## 前置條件
- **Java Development Kit (JDK) 8 or higher** – 已在 IDE 中安裝並設定。  
- **GroupDocs.Merger for Java** – 透過 Maven 或 Gradle 加入專案（見下方說明）。  
- **An IDE** 如 IntelliJ IDEA 或 Eclipse，用於編輯與執行程式碼。  
- **Basic Java file‑handling knowledge** – 需要處理檔案路徑與串流。

## 設定 GroupDocs.Merger for Java

### Maven
將以下相依性加入 `pom.xml` 檔案中：

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle
在 `build.gradle` 檔案中加入函式庫：

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

你也可以直接從 [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/) 下載最新版本。

#### 取得授權步驟
1. **Free Trial:** 先使用免費試用以探索全部功能。  
2. **Temporary License:** 申請臨時授權以延長測試時間。  
3. **Purchase:** 取得正式授權以供商業部署使用。

## 實作指南

### 步驟 1：定義檔案路徑並初始化物件
首先設定 Excel 活頁簿、欲嵌入的 PDF 以及輸出檔案的路徑。接著建立 `OleSpreadsheetOptions`，描述 OLE 物件的顯示位置。

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

### 步驟 2：匯入 OLE 文件
使用 `importDocument` 方法將 PDF 以 OLE 物件的形式嵌入至先前定義的位置。

```java
// Import the OLE document into the specified position in the spreadsheet.
merger.importDocument(oleCellsOptions);

// Save the updated spreadsheet to the output path.
merger.save(filePathOut);
```

**Why we use `importDocument`:** 此方法告訴 GroupDocs.Merger 將 PDF 視為 OLE 物件，保留原始內容，同時讓 Excel 內部即可存取。

### 步驟 3：儲存試算表
最後將變更寫入新檔案，確保原始活頁簿保持不變。

```java
merger.save(filePathOut);
```

**Key configuration options:** 你可以進一步調整 `OleSpreadsheetOptions`——例如調整物件大小、可見性，或改為連結而非嵌入。

#### 疑難排解技巧
- **FileNotFoundException:** 再次確認提供的路徑指向實際存在的檔案。  
- **Version mismatch:** 確保使用的 GroupDocs.Merger 版本與 JDK 版本相符。  
- **Corrupt PDF:** 在嵌入前先確認 PDF 能獨立開啟。

## 實務應用
Embedding OLE objects in Excel is useful in many scenarios:
1. **Data Consolidation:** 合併季報 PDF 成為單一儀表板活頁簿。  
2. **Interactive Presentations:** 於會議中即時開啟詳細規格說明書。  
3. **Automated Reporting:** 產生每月財務報表時自動加入相關佐證文件。

## 效能考量
- **Memory Management:** 關閉不再使用的 `Merger` 實例以釋放資源。  
- **Batch Processing:** 處理大量試算表時，分批執行以避免記憶體激增。  
- **Java Best Practices:** 使用 try‑with‑resources 處理串流，並妥善捕捉例外。

## 結論
你現在已擁有一套完整、可直接投入生產環境的 **embedding PDF in Excel** 與 **importing document into Excel** 解決方案，使用 GroupDocs.Merger for Java。可自行嘗試不同檔案類型、調整放置選項，並將此工作流程整合至自動化報表管線中。

### 下一步
- 嘗試嵌入 Word 文件或圖片，觀察 API 如何處理其他格式。  
- 探索 GroupDocs.Merger 的其他功能，如分割、合併或轉換文件。

## 常見問答

**Q1: Can I embed multiple OLE objects in a single Excel file?**  
A1: 可以，透過對每個物件重複匯入程序即可。

**Q2: What file formats are supported as OLE objects?**  
A2: GroupDocs.Merger 支援 PDF、Word 文件、Excel 檔案、圖片以及其他常見格式。

**Q3: How do I handle large files efficiently with GroupDocs.Merger?**  
A3: 透過分批處理檔案並及時釋放 `Merger` 實例，以最佳化記憶體使用。

**Q4: What if the embedded file is not accessible or is corrupted?**  
A4: 先確認來源檔案的路徑與完整性；若檔案損毀，匯入時會拋出例外。

**Q5: Can I customize the appearance of OLE objects in Excel?**  
A5: 可以，`OleSpreadsheetOptions` 允許設定列/欄索引、尺寸與可見性，以調整物件在工作表中的呈現方式。

## 資源

- **Documentation:** [GroupDocs.Merger for Java Documentation](https://docs.groupdocs.com/merger/java/)  
- **API Reference:** [API Reference Guide](https://reference.groupdocs.com/merger/java/)  
- **Download:** [Latest Releases](https://releases.groupdocs.com/merger/java/)  
- **Purchase:** [Buy GroupDocs.Merger for Java](https://purchase.groupdocs.com/buy)  
- **Free Trial:** [Start a Free Trial](https://releases.groupdocs.com/merger/java/)  
- **Temporary License:** [Request a Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Support:** [GroupDocs Forum](https://forum.groupdocs.com/c/merger/) 

---

**Last Updated:** 2025-12-19  
**Tested With:** GroupDocs.Merger for Java latest-version  
**Author:** GroupDocs