---
date: '2026-08-26'
description: 了解如何使用 GroupDocs Merger 透過 Java 在 PowerPoint 中嵌入 OLE objects。本分步指南將示範如何嵌入
  PDF、試算表等檔案。
keywords:
- groupdocs merger embed ole
- embed OLE objects in PowerPoint
- Java GroupDocs Merger
- OLE embedding in Java
lastmod: '2026-08-26'
og_description: 了解如何使用 GroupDocs Merger 透過 Java 在 PowerPoint 中嵌入 OLE objects。請參考本精簡教學，直接在投影片上加入
  PDF、Excel 工作表及其他檔案。
og_image_alt: 'Tutorial: embed OLE objects in PowerPoint using GroupDocs Merger for
  Java'
og_title: 使用 Java 在 PowerPoint 中嵌入 OLE objects 的 GroupDocs Merger
schemas:
- author: GroupDocs
  dateModified: '2026-08-26'
  description: Learn how to use GroupDocs Merger to embed OLE objects in PowerPoint
    with Java. This step‑by‑step guide shows you how to embed PDFs, spreadsheets,
    and more.
  headline: GroupDocs Merger embed OLE objects in PowerPoint with Java
  type: TechArticle
- description: Learn how to use GroupDocs Merger to embed OLE objects in PowerPoint
    with Java. This step‑by‑step guide shows you how to embed PDFs, spreadsheets,
    and more.
  name: GroupDocs Merger embed OLE objects in PowerPoint with Java
  steps:
  - name: define file paths
    text: Specify absolute or relative paths for both the target PPTX and the source
      file you wish to embed. java String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_PPTX";
      // Path to source presentation file String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_PDF";
      // Path to PDF to be embedded
  - name: configure `OlePresentationOptions`
    text: OlePresentationOptions defines the visual properties and source file for
      the OLE object to be embedded. java import com.groupdocs.merger.domain.options.OlePresentationOptions;
      int pageNumber = 1; // Page number for the OLE object int x = 100; // X position
      on slide int y = 200; // Y position on slid
  - name: embed the OLE object
    text: addOleObject inserts the configured OLE object into the specified slide
      of the presentation. java import com.groupdocs.merger.domain.options.OlePresentationOptions;
      try (Merger merger = new Merger(filePath)) { // Add embedded document as an
      OLE object merger.addOleObject(oleOptions); // Save the mod
  type: HowTo
- questions:
  - answer: PDFs, Excel workbooks, Word documents, PowerPoint files, and many other
      Office formats are supported.
    question: What file formats can be embedded using OLE in PowerPoint?
  - answer: Insert the OLE object on the Slide Master; all slides that inherit from
      that master will display it.
    question: How do I make the embedded object appear on every slide?
  - answer: Yes. Call `addOleObject` again with the same coordinates; the new file
      overwrites the previous one.
    question: Can I replace an existing OLE object without recreating the whole slide?
  - answer: A trial version is available for evaluation; a commercial license is required
      for production deployments.
    question: Is GroupDocs.Merger free to use?
  - answer: Incorrect file paths, unsupported document types, and excessively large
      embedded files that degrade performance.
    question: What are common pitfalls when embedding OLE objects?
  type: FAQPage
tags:
- embed OLE
- GroupDocs Merger
- Java PowerPoint
- OLE objects
- presentation automation
title: 使用 Java 在 PowerPoint 中嵌入 OLE objects 的 GroupDocs Merger
type: docs
url: /zh-hant/java/document-import/embed-ole-object-ppt-java-groupdocs-merger/
weight: 1
---

# GroupDocs Merger 在 PowerPoint 中嵌入 OLE 物件（使用 Java）

在本教學中，您將了解如何使用 Java 將 **groupdocs merger embed ole** 物件嵌入 PowerPoint 投影片。完成本指南後，您將能直接在簡報中插入 PDF、Excel 活頁簿、Word 文件以及其他支援的檔案，讓您的簡報自成一體且更具互動性。

## 快速解答
- **什麼是 OLE？** Object Linking and Embedding 允許您在 PowerPoint 投影片中插入其他檔案類型。  
- **哪個函式庫可以協助？** GroupDocs.Merger for Java 提供簡易的 API 以加入 OLE 物件。  
- **我需要授權嗎？** 臨時授權可用於評估；正式環境則需完整授權。  
- **支援的檔案類型？** PDF、Excel 活頁簿、Word 文件以及其他多種格式。  
- **需要多長時間？** 使用 Maven/Gradle 設定後，核心程式碼可在 10 分鐘內完成撰寫。

## 在 PowerPoint 中的 OLE 嵌入是什麼？

Object Linking and Embedding（OLE）允許 PowerPoint 投影片包含另一份文件的即時呈現。於簡報時雙擊嵌入的物件，即會在其原生應用程式中開啟原始檔案，讓觀眾即時取得詳細資料而無需離開投影片。

## 為什麼在 PowerPoint 中嵌入 OLE 物件？

將 OLE 物件嵌入可將支援檔案整合於簡報內，確保觀眾無需離開投影片即可存取原始內容。此方式保留格式、降低遺失檔案的風險，並簡化分發，使簡報更可靠且更具專業感。

- **將所有資源保存在單一檔案中** – 無需另行傳送 PDF 或試算表。  
- **維持資料完整性** – 嵌入的檔案保留其原始格式與功能。  
- **提升觀眾參與度** – 觀眾可即時探索圖表、表格或合約。  
- **簡化版本控制** – 單一 PPTX 包含所有支援資料，降低檔案不匹配的風險。  

具體效益：**GroupDocs Merger 支援超過 30 種檔案格式的 OLE 物件嵌入，且可處理高達 500 MB 的來源檔案而不會明顯變慢**，確保即使面對大型文件亦能順暢切換投影片。

## 何時應使用 OLE 嵌入？

只要需要提供與投影片敘事相輔相成的詳細、互動式內容，即可使用 OLE 嵌入。它非常適合附加完整報告、資料表或可編輯文件，讓觀眾可直接從簡報中探索，提升清晰度與參與感。

1. **商業報告** – 附加完整 PDF，讓主管可直接在投影片上開啟。  
2. **教學教材** – 提供工作表或資料表，讓學生在講課時可探索。  
3. **專案更新** – 在狀態更新投影片上放置甘特圖 Excel 檔，以便快速參考。  

了解在這些情境下 **how to embed ole** 的做法，可協助您保持簡報自成一體且具專業性。

## 前置條件

- **Java Development Kit (JDK) 8+** – 確認 `java -version` 顯示 1.8 或以上。  
- **IDE** – IntelliJ IDEA、Eclipse，或您偏好的任何編輯器。  
- **Maven 或 Gradle** – 用於相依性管理。  
- **基本的 Java 知識** – 您應熟悉 `try‑with‑resources` 以及物件導向程式碼。

## 設定 GroupDocs.Merger（Java 版）

### 安裝資訊

將 GroupDocs.Merger 函式庫加入您的專案：

**Maven:**
```java
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```
```

**Gradle:**
```java
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```
```

**直接下載：**  
將最新版本從 [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/) 下載。

### 取得授權

在 [temporary license page](https://purchase.groupdocs.com/temporary-license/) 取得臨時授權以進行無限制的評估。正式環境則需從 [GroupDocs website](https://purchase.groupdocs.com/buy) 購買授權。

### 基本初始化

Merger 是核心類別，提供操作簡報的各種方法，包括加入 OLE 物件。

```java
```java
import com.groupdocs.merger.Merger;

public class PresentationMerger {
    public static void main(String[] args) {
        // Initialize Merger with the path to your document
        try (Merger merger = new Merger("path/to/your/presentation.pptx")) {
            System.out.println("Merger initialized successfully.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```
```

## 如何使用 GroupDocs Merger（Java）在 PowerPoint 中嵌入 OLE 物件

要嵌入 OLE 物件，先使用 Merger 載入目標 PPTX，再以來源檔案與期望版面配置設定 OlePresentationOptions，最後呼叫 addOleObject。這個簡潔的三步驟流程會將物件插入指定投影片並儲存更新後的簡報。您亦可調整位置與大小參數以符合投影片設計。

### 直接答案

使用 `new Merger("presentation.pptx")` 載入 PowerPoint 檔案，設定指向來源檔案的 `OlePresentationOptions` 實例，並以目標投影片索引與座標呼叫 `addOleObject`。此三步驟模式可在一次 API 呼叫中插入 OLE 物件。

### 步驟 1：定義檔案路徑

為目標 PPTX 與欲嵌入的來源檔案指定絕對或相對路徑。

```java
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_PPTX"; // Path to source presentation file
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_PDF"; // Path to PDF to be embedded
```
```

### 步驟 2：設定 `OlePresentationOptions`

OlePresentationOptions 定義要嵌入之 OLE 物件的視覺屬性與來源檔案。

```java
```java
import com.groupdocs.merger.domain.options.OlePresentationOptions;

int pageNumber = 1; // Page number for the OLE object
int x = 100; // X position on slide
int y = 200; // Y position on slide
int width = 300; // Width of embedded object
int height = 400; // Height of embedded object

OlePresentationOptions oleOptions = new OlePresentationOptions(embeddedFilePath, pageNumber);
oleOptions.setX(x);
oleOptions.setY(y);
oleOptions.setWidth(width);
oleOptions.setHeight(height);
```
```

### 步驟 3：嵌入 OLE 物件

addOleObject 會將設定好的 OLE 物件插入簡報中指定的投影片。

```java
```java
import com.groupdocs.merger.domain.options.OlePresentationOptions;

try (Merger merger = new Merger(filePath)) {
    // Add embedded document as an OLE object
    merger.addOleObject(oleOptions);
    
    // Save the modified presentation
    String outputPath = "YOUR_OUTPUT_DIRECTORY/modified_presentation.pptx";
    merger.save(outputPath);
    System.out.println("OLE Object added successfully.");
} catch (Exception e) {
    e.printStackTrace();
}
```
```

## 常見問題與解決方案

- **檔案路徑正確性**：請再次確認每個路徑皆指向現有且可讀取的檔案。  
- **支援的格式**：PowerPoint 只支援特定 OLE 類型；PDF、Excel 與 Word 為安全選擇。  
- **記憶體使用**：使用 `try‑with‑resources`（如範例所示）以確保 `Merger` 實例及時關閉。  
- **大型嵌入檔案**：若 PPTX 變得緩慢，請先壓縮來源 PDF 或將其分割成較小的頁面再進行嵌入。  

## 效能考量

- **優化檔案大小**：大型 PDF 可能導致投影片載入變慢；建議先壓縮。  
- **Java 記憶體管理**：上述的 `try‑with‑resources` 模式會自動釋放原生資源。  
- **批次處理**：在大量簡報嵌入物件時，可遍歷檔案清單並盡可能重複使用單一 `Merger` 實例，以減少開銷。  

## 常見問答

**Q: 使用 OLE 在 PowerPoint 中可以嵌入哪些檔案格式？**  
A: 支援 PDF、Excel 活頁簿、Word 文件、PowerPoint 檔案以及其他多種 Office 格式。

**Q: 如何讓嵌入的物件出現在每張投影片上？**  
A: 將 OLE 物件插入投影片母片；所有繼承該母片的投影片皆會顯示它。

**Q: 是否可以在不重新建立整張投影片的情況下取代現有的 OLE 物件？**  
A: 可以。再次以相同座標呼叫 `addOleObject`，新檔案會覆寫舊檔案。

**Q: GroupDocs.Merger 可以免費使用嗎？**  
A: 提供試用版供評估使用；正式部署需購買商業授權。

**Q: 嵌入 OLE 物件時常見的陷阱是什麼？**  
A: 檔案路徑錯誤、不支援的文件類型，以及過大的嵌入檔案會導致效能下降。

## 其他資源

- [GroupDocs.Merger 文件說明](https://docs.groupdocs.com/merger/java/)
- [API 參考文件](https://reference.groupdocs.com/merger/java/)
- [下載 GroupDocs.Merger](https://releases.groupdocs.com/merger/java/)
- [購買授權](https://purchase.groupdocs.com/buy)
- [免費試用](https://releases.groupdocs.com/merger/java/)
- [臨時授權](https://purchase.groupdocs.com/temporary-license/)
- [支援論壇](https://forum.groupdocs.com/c/merger/)

---
**最後更新：** 2026-08-26  
**測試環境：** GroupDocs.Merger 最新版本（Java）  
**作者：** GroupDocs  

## 相關教學

- [如何使用 GroupDocs.Merger（Java）在 Word 中嵌入 PDF – 完整指南](/merger/java/document-import/embed-ole-objects-word-documents-groupdocs-java/)
- [在 Java 中使用 GroupDocs.Merger 將影像嵌入為 OLE 物件 – 完整指南](/merger/java/image-operations/embed-images-ole-java-groupdocs-merger/)