---
date: '2026-02-06'
description: 學習如何使用 GroupDocs.Merger for Java 按行分割文字檔。一步一步的指南，協助在 Java 專案中高效分割文件。
keywords:
- split text file line intervals Java
- document splitting GroupDocs.Merger
- Java document manipulation
title: 如何使用 GroupDocs.Merger for Java 按行分割檔案
type: docs
url: /zh-hant/java/document-splitting/split-text-file-line-intervals-groupdocs-merger-java/
weight: 1
---

# 如何使用 GroupDocs.Merger for Java 按行分割檔案

將大型文字檔案依 **按行** 分割成較小、更易管理的片段是常見需求，例如處理日誌、批次匯入資料，或重新整理冗長的報告。在本教學中，您將學習如何使用 GroupDocs.Merger for Java **按行分割檔案**，了解此方法如何節省時間，並取得可直接執行的程式碼範例。

## 快速解答
- **「按行分割檔案」是什麼意思？** 它會產生多個獨立的文字檔，每個檔案包含原始文件中指定範圍的行號。  
- **哪個函式庫負責分割？** GroupDocs.Merger for Java 提供簡易的 API 進行行區間分割。  
- **我需要授權嗎？** 免費試用可用於測試；正式環境需購買永久授權。  
- **我可以改用字元數量分割嗎？** 無法直接支援——需先透過前置處理將檔案重新整理後再分割。  
- **支援哪個 Java 版本？** 任意 Java 8 以上的執行環境皆相容。

## 什麼是「按行分割檔案」？
按行分割檔案是指將單一文字文件拆分成多個檔案，每個檔案包含特定範圍的連續行（例如，第 1‑3 行、第 4‑6 行，依此類推）。此技術適用於批次處理、平行分析，或單純提升可讀性。

## 為什麼要使用 GroupDocs.Merger for Java？
GroupDocs.Merger 抽象化低階檔案 I/O 工作，讓您專注於業務邏輯。它能有效處理大型檔案，支援多種文件格式，並提供簡潔、流暢的 API，能輕鬆整合至 Maven 或 Gradle 建置流程。

## 前置條件
- **Java Development Kit (JDK) 8 或以上** – 確保 `java` 與 `javac` 已加入 PATH。  
- **GroupDocs.Merger for Java** – 透過 Maven、Gradle 或直接下載方式加入函式庫。  
- **基本的 Java 知識** – 您應該熟悉類別、方法與例外處理。

## 設定 GroupDocs.Merger for Java
使用以下任一方式將函式庫加入您的專案。

**Maven** – 將此相依性貼到您的 `pom.xml` 中：
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

**直接下載** – 您也可以從官方發佈頁面取得 JAR： [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### 取得授權
先使用免費試用版探索 API。若用於正式環境，請從 GroupDocs 入口網站取得臨時或正式授權。

## 如何使用 Java 實作按行分割文字檔

以下提供簡潔的逐步說明。每個步驟在程式碼區塊前以淺顯語言說明，讓您清楚了解發生的事情。

### 步驟 1：定義來源與輸出路徑
首先，告訴函式庫原始檔案所在位置以及分割後的片段應寫入的目錄。
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.txt";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToLineRanges-" + Paths.get(filePath).getFileName().toString();
```

### 步驟 2：設定分割選項
建立 `TextSplitOptions` 實例以描述您想要的行區間。`new int[] { 3, 6 }` 陣列告訴 API 在第 3 行與第 6 行之後切割，產生兩個部分：第 1‑3 行與第 4‑6 行。
```java
TextSplitOptions splitOptions = new TextSplitOptions(filePathOut, TextSplitMode.Interval, new int[] { 3, 6 });
```

### 步驟 3：初始化 Merger 並執行分割
最後，以來源檔案建立 `Merger` 實例，並以剛剛建立的選項呼叫 `split()`。
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

完成！呼叫結束後，您會在 `YOUR_OUTPUT_DIRECTORY` 中看到兩個新檔案，每個檔案都包含指定的行範圍。

## 實務應用（為何重要）
1. **資料處理管線** – 將巨量日誌檔案切成較小的區塊以進行平行解析。  
2. **文件管理** – 將單一報告拆分為章節級別的檔案，便於分發。  
3. **內容分段** – 為大型文章的各段落做目標平台的發布準備。

## 效能建議
- **精簡 I/O** – 處理極大檔案時，建議使用 `Files.newBufferedReader` 以降低記憶體使用。  
- **關閉資源** – 雖然 GroupDocs.Merger 會處理大部分清理，仍建議明確關閉自訂串流以防止洩漏。  
- **監控記憶體** – 分割 GB 級檔案可能佔用大量記憶體；必要時請配置足夠的堆積空間（例如 `-Xmx2g` 或更高）。

## 常見問題與解決方案
| 問題 | 為何發生 | 解決方式 |
|-------|----------------|-----|
| `OutOfMemoryError` | 大型來源檔案超出堆積大小。 | 增加 JVM 堆積或使用較小的區間分割。 |
| `FileNotFoundException` | 路徑不正確或缺少權限。 | 確認 `filePath` 與 `filePathOut` 為絕對路徑且可寫入。 |
| Empty output files | 區間陣列未涵蓋整個文件。 | 確保最後的區間結束於或超過總行數。 |

## 常見問答

**Q: 我可以改用字元數量而非行號來分割檔案嗎？**  
A: 目前 GroupDocs.Merger for Java 只支援行區間。不過，您可以先對文字做前置處理，使每行符合期望的字元數，再使用此功能。

**Q: 我可以指定多少個區間進行分割？**  
A: 函式庫本身沒有特定上限；但若分割次數過多，可能因處理需求增加而影響效能。

**Q: 如何處理檔案分割過程中的錯誤？**  
A: 在程式碼周圍使用 try‑catch 區塊以有效捕捉與管理例外。GroupDocs.Merger 會提供詳細的錯誤訊息，協助除錯。

**Q: 函式庫是否支援其他文字格式，例如 CSV 或 TSV？**  
A: 支援，因為 CSV 與 TSV 為純文字檔，行區間邏輯同樣適用。只需在 API 中將它們視為 `.txt` 檔案即可。

**Q: 我可以自動化分割資料夾中的多個檔案嗎？**  
A: 當然可以。將上述邏輯包在迴圈中，遍歷 `Files.list(Paths.get("folder"))`，對每個檔案套用相同的 `TextSplitOptions`。

## 資源
- **文件說明：** [GroupDocs.Merger for Java Documentation](https://docs.groupdocs.com/merger/java/)  
- **API 參考：** [GroupDocs API Reference](https://reference.groupdocs.com/merger/java/)  
- **下載：** [Latest Releases](https://releases.groupdocs.com/merger/java/)  
- **購買與授權：** [Buy GroupDocs](https://purchase.groupdocs.com/buy)  
- **免費試用：** [GroupDocs Free Trial](https://releases.groupdocs.com/merger/java/)  
- **臨時授權：** [Obtain Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **支援論壇：** [GroupDocs Support](https://forum.groupdocs.com/c/merger)

---

**最後更新：** 2026-02-06  
**測試環境：** GroupDocs.Merger 23.12 for Java  
**作者：** GroupDocs