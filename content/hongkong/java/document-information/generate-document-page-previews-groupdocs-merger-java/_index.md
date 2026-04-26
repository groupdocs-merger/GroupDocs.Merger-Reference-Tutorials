---
date: '2026-01-24'
description: 了解如何使用 GroupDocs.Merger for Java 產生頁面預覽，以快速將頁面轉換為圖像，生成文件縮圖。
keywords:
- GroupDocs.Merger for Java
- document page previews
- Java document management
title: 如何使用 GroupDocs.Merger for Java 預覽文件
type: docs
url: /zh-hant/java/document-information/generate-document-page-previews-groupdocs-merger-java/
weight: 1
---

ger for預覽是一種快速 **預覽文件** 的強大方式，讓使用者在不開啟完整檔案的情況下即可看到視覺快照。在本教學中，您將學習如何使用 GroupDocs.Merger for Java 產生這些預覽，該函式庫可輕鬆 **將頁面轉換為影像**，並支援 **文件縮圖產生**。

## 快速解答
- **什麼是「預覽文件」？** 產生每頁的輕量影像表示。  
- **預覽使用哪種格式？** 預設為 JPEG，但亦支援其他格式。  
- **是否需要授權？** 免費試用可用於開發；正式環境需購買授權。  
- **可以自訂輸出路徑嗎？** 可以，。  
- **需要哪個 Java 版本？** JDK 8 或更新版本 PNG），（PDF- **可擴充的 API** 讓您可控制預覽檔案的儲存位置與方式。  

## 前置條件
- **GroupDocs.Merger for Java** 函式庫（請參閱以下安裝說明）。  
- 已在機器上安裝 **JDK 8+**。  
- 具備 IDE（IntelliJ IDEA、Eclipse、NetBeans）以及 Maven 或 Gradle 以管理相依性。  

## 設定 GroupDocs.Merger for Java
使用您偏好的建置工具將函式庫加入專案中。

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
或者，從 [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/) 下載最新版本。

### 取得授權
- **免費試用：** 先下載免費試用版以體驗功能。  
- **臨時授權：** 於開發期間取得臨時授權以延長使用。  
- **購買：** 正式上線時，請從 [GroupDocs](https://purchase.groupdocs.com/buy) 購買授權。  

函式庫加入後，使用欲預覽文件的路徑進行初始化：

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

## 如何預覽文件：逐步指南

### 步驟 1：初始化 Merger 並定義 PageStreamFactory
`PageStreamFactory` 告訴函式庫每個預覽影像的寫入位置。

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

### 步驟 2：產生預覽
呼叫 `generatePreview` 方法，並傳入剛剛設定的選項。

```java
merger.generatePreview(previewOption);
```

### 將頁面轉換為影像 – 自訂 PageStreamFactory
若需更細緻地控制檔案命名或儲存位置，可自行實作工廠：

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
產生預覽特別適用於以下情境：

1. **文件管理系統** – 使用者可在不開啟檔案的情況下快速瀏覽。  
2. **內容審核平台** – 在批准上傳前進行快速視覺檢查。  
3. **教育工具** – 學生可快速瀏覽課程投影片或教科書頁面。  

## 效能考量
- **及時釋放串流** 以釋放記憶體。  
- **避免將整個文件載入記憶體**；讓函式庫自行分頁處理。  
- **使用適當的影像品質設定**，在速度與視覺真實度之間取得平衡。  

## 常見問題

**Q: GroupDocs.Merger for Java 的用途是什麼？**  
A: 它用於高效地合併、分割與管理文件，亦包括產生預覽。

**Q: 如何在串流操作期間處理例外？**  
A: 如輔助方法所示，將串流的建立與關閉包在 try‑catch 區塊中。

**Q: 能否產生 JPEG 以外格式的預覽？**  
A: 可以，將 `PreviewMode` 列舉改為 PNG、BMP 等，以符合需求。

**Q: 文件預覽產生常見的問題是什麼？**  
A: 常見問題包括檔案路徑錯誤以及未關閉串流，可能導致記憶體洩漏。

**Q: 如何將 GroupDocs.Merger 與其他系統整合？**  
A: 使用其 API 連接資料庫、Web 服務或其他 Java 應用程式，以實現無縫工作流程自動化。

## 其他資源
- [文件說明](https://docs.groupdocs.com/merger/java/)
- [API 參考](https://reference.groupdocs.com/merger/java/)
- [下載](https://releases.groupdocs.com/merger/java/)
- [購買](https://purchase.groupdocs.com/buy)
- [免費試用](https://releases.groupdocs.com/merger/java/)
- [臨時授權](https://purchase.groupdocs.com/temporary-license/)
- [支援](https://forum.groupdocs.com/c/merger/)

---

**最後更新：** 試環境：** GroupDocs.Merger 最新版本 (2025‑latest)  
**作者：** GroupDocs