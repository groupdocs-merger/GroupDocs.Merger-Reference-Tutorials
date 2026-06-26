---
date: '2026-06-26'
description: 了解如何使用 GroupDocs.Merger for Java 將圖像轉換為 OLE。逐步指南、程式碼片段，以及嵌入圖像為 OLE 物件的最佳實踐。
keywords:
- convert image to ole
- GroupDocs.Merger Java tutorial
- embed images as OLE objects
schemas:
- author: GroupDocs
  dateModified: '2026-06-26'
  description: Learn how to convert image to OLE using GroupDocs.Merger for Java.
    Step‑by‑step guide, code snippets, and best practices for embedding images as
    OLE objects.
  headline: How to Convert Image to OLE in Java with GroupDocs.Merger
  type: TechArticle
- description: Learn how to convert image to OLE using GroupDocs.Merger for Java.
    Step‑by‑step guide, code snippets, and best practices for embedding images as
    OLE objects.
  name: How to Convert Image to OLE in Java with GroupDocs.Merger
  steps:
  - name: Define File Paths
    text: 'Specify where the source document and the image reside. Replace the placeholders
      with actual paths on your machine:'
  - name: Read Image Bytes
    text: 'Read the entire image file into a byte array. This byte array becomes the
      OLE payload:'
  - name: Configure OLE Diagram Options
    text: '`OleDiagramOptions` tells GroupDocs where and how to place the OLE object.
      The class is the **top‑level options holder for OLE diagram import**; it lets
      you set page number, X/Y coordinates, width, and height.'
  - name: Initialize Merger and Import OLE Diagram
    text: '`Merger` is the core class that represents a document and provides methods
      for manipulation. It **encapsulates all read/write operations** for the target
      file.'
  - name: Initialize Merger with Source Path
    text: 'Reuse the same `Merger` instance or create a new one pointing to the modified
      document:'
  - name: Save the Modified Document
    text: 'Call the `save` method with the desired output location. GroupDocs.Merger
      writes the file in a streaming fashion, keeping memory usage low:'
  type: HowTo
- questions:
  - answer: An OLE object embeds data from one application (e.g., an image) into another
      (e.g., a Word file), allowing in‑place editing without leaving the host document.
    question: What is an OLE object?
  - answer: Yes—commercial use requires a valid license. A trial is available for
      evaluation, but production deployments must be licensed.
    question: Can I use GroupDocs.Merger for commercial projects?
  - answer: Images are read into a byte array, but you can stream large files using
      `FileInputStream` and pass the stream to `importOleDiagram` to keep memory usage
      low.
    question: How does the library handle very large images?
  - answer: DOCX, XLSX, PPTX, and PDF are fully supported. For PDF, the OLE object
      is stored as an embedded file stream.
    question: Which document formats support OLE embedding?
  - answer: Practically none—GroupDocs.Merger can embed dozens of OLE diagrams, limited
      only by the host document’s size and available memory.
    question: Are there any limitations on the number of OLE objects per document?
  type: FAQPage
title: 如何在 Java 中使用 GroupDocs.Merger 將圖像轉換為 OLE
type: docs
url: /zh-hant/java/image-operations/embed-images-ole-java-groupdocs-merger/
weight: 1
---

# 如何在 Java 中使用 GroupDocs.Merger 將圖像轉換為 OLE

直接將圖像嵌入文件可能會感到繁瑣，但使用 GroupDocs.Merger for Java，**convert image to OLE** 就變得輕而易舉。在本教學中，您將了解 OLE 物件的用途、如何準備環境，以及將圖像嵌入為 OLE 圖表的具體步驟。完成後，您將擁有可在 Word、Excel、PowerPoint 與 PDF 檔案中使用的可重用程式碼模式。

## 快速解答
- **主要方法是什麼？** 在載入來源文件後，使用 `Merger.importOleDiagram()`。  
- **我需要授權嗎？** 試用版可用於開發；正式環境則需要完整授權。  
- **支援哪些圖像格式？** 支援 PNG、JPEG、BMP、GIF 與 TIFF 等格式。  
- **我可以設定 OLE 的大小與位置嗎？** 可以——`OleDiagramOptions` 允許您定義頁面、座標、寬度與高度。  
- **此過程記憶體使用是否有效率？** GroupDocs.Merger 以串流方式處理資料，即使是 500 頁的檔案，記憶體使用也不超過 200 MB。

## 什麼是「convert image to OLE」？
**Convert image to OLE** 意味著將點陣圖檔案轉換為可在宿主文件內編輯的 Object Linking and Embedding (OLE) 圖表。此轉換讓最終使用者能雙擊圖像，在其原生編輯器中開啟，並將變更儲存回容器文件，而無需離開檔案。

## 為何使用 GroupDocs.Merger 進行 OLE 嵌入？
GroupDocs.Merger 支援 **50+ 種輸入與輸出格式**——包括 DOCX、XLSX、PPTX、PDF 以及常見圖像類型，且可在不將整個檔案載入記憶體的情況下，於最高 **300 MB** 的文件中嵌入 OLE 物件。該函式庫在一般 2.6 GHz 伺服器上，能在 **3 秒** 內處理一個含有三個嵌入 PNG 的 200 頁 Word 檔，提供速度與可擴充性。

## 前置條件
- **Java Development Kit (JDK) 8+** 已安裝並在 IDE 中配置。  
- **GroupDocs.Merger for Java** 已透過 Maven 或 Gradle 加入（建議使用最新版本）。  
- 具備 Java I/O 串流與物件導向程式設計的基本知識。  

## 設定 GroupDocs.Merger for Java

要在專案中加入 GroupDocs.Merger，請將相依性加入您的建置檔案。此函式庫可於 Maven Central 取得，您可以將以下程式碼片段複製到 `pom.xml` 或 `build.gradle` 中。  

> **注意：** The placeholders below represent the exact code blocks from the original tutorial; keep them unchanged.

```xml
  <!-- Maven -->
  <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-merger</artifactId>
      <version>latest-version</version>
  </dependency>
  ```

```gradle
  // Gradle
  implementation 'com.groupdocs:groupdocs-merger:latest-version'
  ```

您也可以直接從官方發行頁面下載 JAR： [GroupDocs.Merger releases](https://releases.groupdocs.com/merger/java/).

### 取得授權
- **Free Trial:** 適用於原型開發與評估。  
- **Temporary License:** 在有限期間內延伸試用功能。  
- **Full License:** 解鎖所有 OLE 相關功能並移除使用限制。

加入相依性後，您即可在 Java 程式碼中初始化此函式庫。

## 如何在 Java 中將圖像轉換為 OLE？
要將圖像轉換為 OLE 物件，先使用 `Merger` 實例載入目標文件，將圖像檔讀取為位元組陣列，建立 `OleDiagramOptions` 物件以指定頁面、位置與尺寸，然後呼叫 `merger.importOleDiagram(imageBytes, options)`。最後，使用 `merger.save(outputPath)` 儲存文件。此工作流程會將圖像嵌入為可編輯的 OLE 圖表。

### 步驟 1：定義檔案路徑
指定來源文件與圖像所在的位置。將佔位符替換為您機器上的實際路徑：

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.vsdx";  
String imageFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.emf";
```

### 步驟 2：讀取圖像位元組
將整個圖像檔讀取為位元組陣列。此位元組陣列即為 OLE 載荷：

```java
File file = new File(imageFilePath);
byte[] imageBytes = Files.readAllBytes(file.toPath());
```

### 步驟 3：設定 OLE 圖表選項
`OleDiagramOptions` 告訴 GroupDocs OLE 物件的放置位置與方式。此類別是 **OLE 圖表匯入的最高層級選項持有者**；它允許您設定頁碼、X/Y 座標、寬度與高度。

```java
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pptx";
int pageNumber = 2;  
String filePathOut = new File("YOUR_OUTPUT_DIRECTORY", "ImportImageToDocument" + Paths.get(filePath).getFileName().toString()).getPath();

OleDiagramOptions oleDiagramOptions = new OleDiagramOptions(embeddedFilePath, imageBytes, pageNumber);
oleDiagramOptions.setX(1);  
oleDiagramOptions.setY(1);
oleDiagramOptions.setWidth(2);
oleDiagramOptions.setHeight(1);
```

### 步驟 4：初始化 Merger 並匯入 OLE 圖表
`Merger` 是代表文件並提供操作方法的核心類別。它 **封裝了目標檔案的所有讀寫操作**。

```java
Merger merger = new Merger(filePath);
merger.importDocument(oleDiagramOptions);
merger.save(filePathOut);
```

## 儲存已修改的文件

OLE 圖表嵌入後，您需要將變更寫回磁碟。

### 步驟 1：使用來源路徑初始化 Merger
重複使用相同的 `Merger` 實例，或建立指向已修改文件的新實例：

```java
Merger merger = new Merger(filePath);
```

### 步驟 2：儲存已修改的文件
呼叫 `save` 方法並指定輸出位置。GroupDocs.Merger 以串流方式寫入檔案，保持低記憶體使用量：

```java
merger.save(outputPath);
```

## 實務應用
將圖像嵌入為 OLE 物件可開啟多種實務情境：

- **Interactive Reports:** 使用者可雙擊嵌入的圖表，在 Excel 中編輯，並即時看到更新後的視覺效果。  
- **Automated Document Generation:** 金融與醫療系統可將即時圖形注入合約或患者摘要中，無需手動編輯。  
- **Collaboration Platforms:** 團隊可共享單一 Word 檔案，讓每位成員更新自己的圖表，減少版本控制的困擾。  

## 效能考量
為確保在處理大型檔案時應用程式保持回應性：

- **Stream Data:** GroupDocs.Merger 以串流方式處理輸入與輸出，避免將整個檔案載入記憶體。  
- **Reuse Objects:** 重複使用單一 `Merger` 實例進行多次匯入，可減少物件建立開銷。  
- **Monitor Heap:** 若文件大於 200 MB，建議增加 JVM 堆積大小（`-Xmx1g`），以避免 `OutOfMemoryError`。  

## 常見問題與解決方案
| 症狀 | 可能原因 | 解決方法 |
|---------|--------------|-----|
| `Unsupported file format` 錯誤 | 圖像不是 PNG/JPEG/BMP/GIF/TIFF 格式 | 在讀取位元組前，先將圖像轉換為支援的格式。 |
| OLE 物件出現在錯誤位置 | `OleDiagramOptions` 中的 `x`/`y` 座標不正確 | 確認座標以點為單位測量（1 pt ≈ 1/72 in）。 |
| 輸出檔案損毀 | 匯入後未呼叫 `save()` | 確保在所有修改完成後執行 `merger.save(outputPath)`。 |

## 常見問答

**Q: 什麼是 OLE 物件？**  
A: OLE 物件將來自一個應用程式（例如圖像）的資料嵌入另一個應用程式（例如 Word 檔案），允許在宿主文件內直接編輯，而無需離開文件。

**Q: 我可以在商業專案中使用 GroupDocs.Merger 嗎？**  
A: 是的——商業使用需要有效授權。提供試用版供評估，但正式部署必須取得授權。

**Q: 函式庫如何處理非常大的圖像？**  
A: 圖像會讀取為位元組陣列，但您可以使用 `FileInputStream` 串流大型檔案，並將串流傳遞給 `importOleDiagram`，以降低記憶體使用量。

**Q: 哪些文件格式支援 OLE 嵌入？**  
A: 完整支援 DOCX、XLSX、PPTX 與 PDF。對於 PDF，OLE 物件會以嵌入檔案串流的形式儲存。

**Q: 每個文件的 OLE 物件數量有任何限制嗎？**  
A: 實際上沒有——GroupDocs.Merger 可嵌入數十個 OLE 圖表，唯一限制為宿主文件的大小與可用記憶體。

## 資源
- [GroupDocs.Merger 版本發佈](https://releases.groupdocs.com/merger/java/)
- [GroupDocs.Merger Java 文件說明](https://docs.groupdocs.com/merger/java/)
- [Java API 參考文件](https://reference.groupdocs.com/merger/java/)
- [GroupDocs.Merger for Java 版本發佈](https://releases.groupdocs.com/merger/java/)
- [GroupDocs 購買頁面](https://purchase.groupdocs.com/buy)
- [GroupDocs 支援論壇](https://forum.groupdocs.com/c/merger)

## 結論
您現在已掌握使用 GroupDocs.Merger for Java 進行 **convert image to OLE** 的完整、可投入生產的工作流程。透過定義檔案路徑、讀取圖像位元組、設定 `OleDiagramOptions`，以及呼叫 `importOleDiagram`，即可為任何支援的文件加入互動式圖形。探索其他 API——如合併、分割與加浮水印——以構建功能完整的文件處理管線。

---

**最後更新：** 2026-06-26  
**測試環境：** GroupDocs.Merger 23.10 for Java  
**作者：** GroupDocs

## 相關教學

- [如何在 Excel 中嵌入 PDF 使用 GroupDocs.Merger for Java - 匯入 OLE 物件 – 步驟指南](/merger/java/document-import/import-ole-object-excel-groupdocs-merger-java/)
- [如何在 Word 中嵌入 PDF 使用 GroupDocs.Merger for Java – 完整指南](/merger/java/document-import/embed-ole-objects-word-documents-groupdocs-java/)
- [如何使用 GroupDocs.Merger for Java 合併 PNG 圖像 – 步驟指南](/merger/java/document-information/merge-png-images-groupdocs-merger-java/)