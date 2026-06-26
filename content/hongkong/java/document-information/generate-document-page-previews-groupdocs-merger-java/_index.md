---
date: '2026-06-26'
description: 了解如何使用 GroupDocs.Merger for Java 將 PDF 頁面轉換為圖像並預覽文件——快速且可靠的頁面縮圖生成方式。
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
title: 如何使用 GroupDocs.Merger for Java 將 PDF 頁面轉換為圖像並預覽文件
type: docs
url: /zh-hant/java/document-information/generate-document-page-previews-groupdocs-merger-java/
weight: 1
---

# 如何將 PDF 頁面轉換為圖像並使用 GroupDocs.Merger for Java 預覽文件

在現代應用程式中，您常常需要 **將 PDF 頁面轉換為圖像**，讓使用者能在不下載整個檔案的情況下快速瀏覽文件。本教學將帶您使用 GroupDocs.Merger for Java 產生高品質的頁面預覽，涵蓋從設定到自訂儲存處理的全部步驟。完成後，您將擁有一個可重複使用的文件縮圖產生解決方案，適用於任何 JDK 8+ 環境。

## 快速解答
- **「預覽文件」是什麼意思？** 產生每頁的輕量圖像表示。  
- **預覽使用哪種格式？** 預設為 JPEG，但亦支援其他格式。  
- **我需要授權嗎？** 免費試用可用於開發；正式環境需購買授權。  
- **我可以自訂輸出路徑嗎？** 可以，透過實作自訂的 `PageStreamFactory`。  
- **需要哪個 Java 版本？** JDK 8 或更新版本。  

## 什麼是「預覽文件」？
文件預覽是指為每頁建立視覺縮圖（通常為 JPEG 或 PNG），讓使用者能快速瀏覽內容。此技術可提升檔案瀏覽器、內容審核平台以及任何管理大量文件的系統之使用者體驗，提供快速的視覺提示，而無需開啟完整檔案。

## 為什麼使用 GroupDocs.Merger for Java？
GroupDocs.Merger 能在一般 2 GHz CPU 上將 PDF 頁面轉換為圖像 **每頁低於 0.5 秒**，支援 **超過 50 種輸入與輸出格式**，並允許您直接將預覽串流至儲存空間，而無需將整個檔案載入記憶體。其可擴充的 API 亦讓您完整掌控圖像品質、格式與目標路徑。

## 前置條件
- **GroupDocs.Merger for Java** 函式庫（請參閱以下安裝說明）。  
- **JDK 8+** 已安裝於您的機器上。  
- 一個 IDE（IntelliJ IDEA、Eclipse、NetBeans）以及 Maven 或 Gradle 用於相依性管理。  

## 設定 GroupDocs.Merger for Java
使用您偏好的建置工具將函式庫加入專案。

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

**直接下載:**  
或者，從 [GroupDocs.Merger for Java 版本發佈](https://releases.groupdocs.com/merger/java/) 下載最新版本。

### 取得授權
- **免費試用：** 先下載免費試用版以探索功能。  
- **臨時授權：** 取得臨時授權以在開發期間延長使用。  
- **購買：** 若要正式投入生產，請從 [GroupDocs](https://purchase.groupdocs.com/buy) 購買授權。  

加入函式庫後，使用您想要預覽的文件路徑進行初始化：

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

## 如何預覽文件：逐步指南
載入來源檔案，設定 `PageStreamFactory`，然後呼叫 `generatePreview`。  
`generatePreview` 是一個根據提供的選項將每個文件頁面轉換為圖像的方法。

### 步驟 1：初始化 Merger 並定義 PageStreamFactory
`Merger` 是提供文件合併、分割與產生預覽等方法的核心類別。  
`PageStreamFactory` 是一個介面，告訴函式庫每個預覽圖像的寫入位置。

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

此處我們建立自訂實作，將每頁圖像寫入特定資料夾，使用可預測的命名規則。

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

### 步驟 2：產生預覽
`generatePreview` 依據您提供的選項觸發轉換程序。它將每頁圖像串流至您定義的 `PageStreamFactory`，確保低記憶體使用量。

```java
merger.generatePreview(previewOption);
```

### 將頁面轉換為圖像 – 自訂 PageStreamFactory
如果您需要更細緻的檔案命名或儲存位置控制，請實作自己的工廠：

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

### 輔助方法 – 管理串流
這些工具方法可保持程式碼整潔，並乾淨地處理例外情況。

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

## 文件縮圖產生 – 實務應用
產生預覽特別適用於以下情況：

1. **文件管理系統** – 使用者可在不開啟檔案的情況下快速瀏覽。  
2. **內容審核平台** – 在批准上傳前進行快速視覺檢查。  
3. **教育工具** – 學生可快速瀏覽課程投影片或教科書頁面。  

## 效能考量
- **及時釋放串流** 以釋放記憶體。  
- **避免將整個文件載入記憶體**；讓函式庫處理分頁。  
- **使用適當的圖像品質** 設定，以在速度與視覺真實度之間取得平衡。  

## 常見問題

**Q: GroupDocs.Merger for Java 的用途是什麼？**  
A: 它用於高效地合併、分割與管理文件，包含預覽產生與格式轉換。

**Q: 如何在串流操作期間處理例外情況？**  
A: 如輔助方法所示，將串流的建立與關閉包在 try‑catch 區塊中，以防止記憶體泄漏。

**Q: 我可以產生非 JPEG 格式的預覽嗎？**  
A: 可以，將 `PreviewMode` 列舉改為 PNG、BMP 或 TIFF，以符合您的需求。

**Q: 文件預覽產生常見的問題是什麼？**  
A: 常見問題包括檔案路徑不正確以及忘記關閉串流，這可能導致記憶體泄漏。

**Q: 我該如何將 GroupDocs.Merger 與其他系統整合？**  
A: 使用其 API 連接資料庫、Web 服務或其他 Java 應用程式，以實現無縫工作流程自動化。

---

## 資源
- [GroupDocs.Merger for Java 版本發佈](https://releases.groupdocs.com/merger/java/)  
- [下載](https://releases.groupdocs.com/merger/java/)  
- [文件說明](https://docs.groupdocs.com/merger/java/)  
- [API 參考](https://reference.groupdocs.com/merger/java/)  
- [免費試用](https://releases.groupdocs.com/merger/java/)  
- [臨時授權](https://purchase.groupdocs.com/temporary-license/)  
- [購買](https://purchase.groupdocs.com/buy)  
- [GroupDocs](https://purchase.groupdocs.com/buy)  
- [支援](https://forum.groupdocs.com/c/merger/)

**最後更新：** 2026-06-26  
**測試環境：** GroupDocs.Merger latest version (2025‑latest)  
**作者：** GroupDocs

## 相關教學

- [GroupDocs.Merger Java 文件頁面操作教學](/merger/java/page-operations/)
- [如何使用 GroupDocs.Merger for Java 從 URL 載入 PDF：完整指南](/merger/java/document-loading/load-pdf-url-groupdocs-merger-java/)
- [使用 GroupDocs.Merger Java 建立單頁 PDF](/merger/java/document-splitting/)