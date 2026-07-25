---
date: '2026-07-25'
description: 了解如何使用 GroupDocs.Merger for Java 按行分割檔案——逐步指南，助您在 Java 專案中高效執行文件分割。
keywords:
- split file by lines
- split large text file
- split file into parts
- split text file java
- java document splitting
lastmod: '2026-07-25'
og_description: 使用 GroupDocs.Merger for Java 按行分割檔案。本指南示範如何快速將大型文字檔分割成多個部分，並提供程式碼範例與最佳實踐技巧。
og_image_alt: 'Developer guide: split file by lines in Java using GroupDocs.Merger'
og_title: 使用 GroupDocs.Merger for Java 按行分割檔案 – 快速且簡易
schemas:
- author: GroupDocs
  dateModified: '2026-07-25'
  description: Learn how to split file by lines using GroupDocs.Merger for Java –
    a step‑by‑step guide for efficient document splitting in Java projects.
  headline: How to Split File by Lines with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to split file by lines using GroupDocs.Merger for Java –
    a step‑by‑step guide for efficient document splitting in Java projects.
  name: How to Split File by Lines with GroupDocs.Merger for Java
  steps:
  - name: Define Source and Output Paths
    text: First, tell the library where your original file lives and where the split
      fragments should be written.
  - name: Configure the Split Options
    text: 'Create a `TextSplitOptions` instance that describes the line intervals
      you want. The `new int[] { 3, 6 }` array tells the API to cut after line 3 and
      line 6, producing two parts: lines 1‑3 and lines 4‑6. **Definition:** `TextSplitOptions`
      is a configuration object that holds the line‑interval array '
  - name: Initialise the Merger and Execute the Split
    text: Finally, instantiate `Merger` with the source file and call `split()` with
      the options you just built. **Definition:** `Merger` is the core class in GroupDocs.Merger
      that orchestrates document manipulation operations such as splitting, merging,
      and extracting pages. When the `split()` call finishes,
  type: HowTo
- questions:
  - answer: Currently, GroupDocs.Merger for Java focuses on line intervals. However,
      you can preprocess your text to match the desired character count per line before
      using this feature.
    question: Can I split files based on character count instead of line numbers?
  - answer: There is no hard limit in the library; performance may degrade if you
      request thousands of tiny splits because each split incurs I/O overhead.
    question: Is there a limit to how many intervals I can specify for splitting?
  - answer: Wrap the splitting logic in a try‑catch block and log `MergerException`
      details. The API provides clear messages that pinpoint the failure point.
    question: How do I handle errors during file splitting?
  - answer: Yes, because CSV and TSV are plain‑text files, the same line‑interval
      logic applies. Treat them as `.txt` files when calling the API.
    question: Does the library support other text‑based formats such as CSV or TSV?
  - answer: Absolutely. Iterate over `Files.list(Paths.get("folder"))`, apply the
      same `TextSplitOptions` to each file, and collect the generated parts.
    question: Can I automate splitting for multiple files in a folder?
  type: FAQPage
tags:
- split file by lines
- GroupDocs.Merger
- Java document processing
- text file splitting
- java tutorial
title: 如何使用 GroupDocs.Merger for Java 按行分割檔案
type: docs
url: /zh-hant/java/document-splitting/split-text-file-line-intervals-groupdocs-merger-java/
weight: 1
---

# 如何使用 GroupDocs.Merger for Java 按行分割檔案

如果您需要**按行分割檔案**——例如，將巨大的日誌檔案切成易於處理的塊、將資料批次輸入管道，或將長報告轉成獨立章節檔案——本教學將向您展示如何使用 GroupDocs.Merger for Java 完成此操作。您將了解此函式庫如何節省時間、獲得可直接執行的實作範例，並學習保持應用程式快速且可靠的實用技巧。

## 快速回答
- **什麼是「按行分割檔案」？** 它會建立多個獨立的文字檔，每個檔案包含原始文件中定義的行號範圍。  
- **哪個函式庫負責分割？** GroupDocs.Merger for Java 提供簡易的 API 進行行區間分割。  
- **我需要授權嗎？** 免費試用可用於測試；正式環境需購買永久授權。  
- **我可以改用字元數分割嗎？** 直接不支援——請先透過前置處理將檔案重新整理後再分割。  
- **支援哪個 Java 版本？** 任意 Java 8 以上的執行環境皆相容。  

## 什麼是「按行分割檔案」？
**按行分割檔案**指將單一文字文件拆分成多個檔案，每個檔案包含特定連續行的範圍（例如，第 1‑3 行、第 4‑6 行，依此類推）。當您需要平行處理資料、降低記憶體壓力，或僅是讓長檔案更易於瀏覽時，此方法非常適合。

## 為何使用 GroupDocs.Merger for Java？
GroupDocs.Merger 抽象化低階檔案 I/O，讓您專注於業務邏輯。它能高效處理最高 2 GB 的檔案而無需將整個文件載入記憶體，支援**超過 70 種**輸入與輸出格式，並提供流暢的 API，能順利整合至 Maven 或 Gradle 建置。使用此函式庫可將開發時間縮短最多**80 %**，相較於自行編寫 I/O 迴圈。

## 前置條件
- **Java Development Kit (JDK) 8 或以上** – 確認 `java` 與 `javac` 已加入 PATH。  
- **GroupDocs.Merger for Java** – 透過 Maven、Gradle 或直接下載方式加入函式庫。  
- **基本的 Java 知識** – 您應該熟悉類別、方法與例外處理。  

## 設定 GroupDocs.Merger for Java
使用以下任一方式將函式庫加入您的專案。

**Maven** – 將以下相依性貼到您的 `pom.xml` 中：
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle** – 在 `build.gradle` 中加入以下行：
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**直接下載** – 您也可以從官方發行頁面取得 JAR： [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/)

### 取得授權
先使用免費試用版探索 API。若用於正式環境，請從 GroupDocs 入口網站取得臨時或完整授權。

## 如何使用 Java 實作按行分割文字檔
以下是一個簡潔的逐步說明。每一步都以簡單語言解釋，然後是標示實際程式碼所在位置的佔位符，讓您清楚了解每個步驟的作用。

### 步驟 1：定義來源與輸出路徑
首先，告訴函式庫原始檔案的位置以及分割後片段的寫入路徑。
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.txt";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToLineRanges-" + Paths.get(filePath).getFileName().toString();
```

### 步驟 2：設定分割選項
建立一個 `TextSplitOptions` 實例，用以描述您想要的行區間。`new int[] { 3, 6 }` 陣列告訴 API 在第 3 行與第 6 行之後切割，產生兩個部分：第 1‑3 行與第 4‑6 行。  
**定義：** `TextSplitOptions` 為配置物件，保存行區間陣列以及可選的輸出命名規則。  
```java
TextSplitOptions splitOptions = new TextSplitOptions(filePathOut, TextSplitMode.Interval, new int[] { 3, 6 });
```

### 步驟 3：初始化 Merger 並執行分割
最後，以來源檔案建立 `Merger` 實例，並以剛才建立的選項呼叫 `split()`。  
**定義：** `Merger` 為 GroupDocs.Merger 的核心類別，負責協調文件操作，如分割、合併與抽取頁面。  
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

當 `split()` 呼叫完成後，您會在 `YOUR_OUTPUT_DIRECTORY` 中看到兩個新檔案，每個檔案皆包含指定的行範圍。

## 實務應用（為何重要）
1. **資料處理管道** – 將巨大的日誌檔案切成較小的塊以平行解析，顯著縮短整體處理時間。  
2. **文件管理** – 將單一報告拆分成章節檔案，便於分發給不同團隊。  
3. **內容分段** – 為大型文章的各段落做目標平台的發佈準備，提升 SEO 與可讀性。  

## 效能建議
- **精簡 I/O** – 處理極大檔案時，建議使用 `Files.newBufferedReader` 以降低記憶體使用。  
- **關閉資源** – 雖然 GroupDocs.Merger 會處理大部分清理，仍建議明確關閉自訂串流以防止洩漏。  
- **監控記憶體** – 分割 GB 級檔案可能消耗大量記憶體；必要時配置足夠的堆積空間（如 `-Xmx2g` 或更高）。  
- **批次處理** – 分割多個檔案時，重複使用同一個 `Merger` 實例以減少物件建立開銷。  

## 常見問題與解決方案
| 問題 | 發生原因 | 解決方式 |
|-------|----------------|-----|
| `OutOfMemoryError` | 來源檔案過大，超出堆積記憶體。 | 增加 JVM 堆積大小或使用較小的區間進行分割。 |
| `FileNotFoundException` | 路徑不正確或缺少權限。 | 確認 `filePath` 與 `filePathOut` 為絕對路徑且可寫入。 |
| Empty output files | 區間陣列未涵蓋整個文件。 | 確保最後的區間結束於或超過總行數。 |

## 常見問答

**Q: 我可以改用字元數而非行號來分割檔案嗎？**  
A: 目前 GroupDocs.Merger for Java 只支援行區間分割。但您可以先對文字進行前置處理，使每行符合所需的字元數，再使用此功能。

**Q: 我可以指定多少個區間進行分割？**  
A: 函式庫沒有硬性上限；若請求成千上萬的極小分割，因每次分割都會產生 I/O 開銷，效能可能下降。

**Q: 如何處理檔案分割過程中的錯誤？**  
A: 將分割邏輯包在 try‑catch 區塊中，並記錄 `MergerException` 的詳細資訊。API 會提供明確的訊息指出失敗點。

**Q: 函式庫是否支援其他文字格式，如 CSV 或 TSV？**  
A: 支援，因為 CSV 與 TSV 為純文字檔，行區間邏輯同樣適用。呼叫 API 時可將它們視為 `.txt` 檔案。

**Q: 我可以自動化分割資料夾中的多個檔案嗎？**  
A: 當然可以。遍歷 `Files.list(Paths.get("folder"))`，對每個檔案套用相同的 `TextSplitOptions`，並收集產生的片段。

## 其他資源
- [GroupDocs.Merger for Java 版本發佈](https://releases.groupdocs.com/merger/java/)
- [GroupDocs.Merger for Java 文件](https://docs.groupdocs.com/merger/java/)
- [GroupDocs API 參考](https://reference.groupdocs.com/merger/java/)
- [最新發佈](https://releases.groupdocs.com/merger/java/)
- [購買 GroupDocs](https://purchase.groupdocs.com/buy)
- [GroupDocs 免費試用](https://releases.groupdocs.com/merger/java/)
- [取得臨時授權](https://purchase.groupdocs.com/temporary-license/)
- [GroupDocs 支援](https://forum.groupdocs.com/c/merger)

---

**最後更新：** 2026-07-25  
**測試環境：** GroupDocs.Merger 23.12 for Java  
**作者：** GroupDocs

## 相關教學
- [如何使用 GroupDocs.Merger for Java 將文字檔分割成獨立行文件](/merger/java/text-operations/split-text-file-lines-groupdocs-merger-java/)
- [split pdf java：使用 GroupDocs.Merger 進行文件分割](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [使用 GroupDocs.Merger 載入本機文件 – 指南](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)