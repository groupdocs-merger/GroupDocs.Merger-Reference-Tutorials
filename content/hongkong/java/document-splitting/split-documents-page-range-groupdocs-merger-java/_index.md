---
date: '2026-02-06'
description: 了解如何使用 GroupDocs.Merger for Java 提取特定頁面並按頁碼範圍分割文件，包括奇偶頁過濾。
keywords:
- GroupDocs.Merger for Java
- split documents by page range
- document management
title: 使用 GroupDocs.Merger for Java 提取特定頁面
type: docs
url: /zh-hant/java/document-splitting/split-documents-page-range-groupdocs-merger-java/
weight: 1
---

# 使用 GroupDocs.Merger for Java 提取特定頁面

高效地 **提取特定頁面** 從大型 PDF、Word 檔案或簡報，無需手動複製貼上。在本教學中，您將了解如何依頁碼範圍分割文件、套用奇偶頁過濾，以及產生單頁檔案——全部使用 **GroupDocs.Merger for Java**。

## 快速解答
- **「提取特定頁面」是什麼意思？** 它指的是建立只包含您從來源檔案中選取的頁面的新文件。  
- **支援哪些格式？** PDF、DOCX、PPTX 以及其他多種常見格式。  
- **可以依奇數或偶數頁過濾嗎？** 可以，使用 `RangeMode` 選項（例如 `OddPages`）。  
- **需要授權嗎？** 免費試用可用於評估；正式上線需購買永久授權。  
- **適用於大型文件嗎？** 是的——分割大型文件區段以降低記憶體使用量。  

## 何謂提取特定頁面？
提取特定頁面是指從來源文件中取出一部分頁面，並將其另存為新的獨立檔案。此功能可用於製作重點報告、分享合約條款，或準備簡報講義。

## 為何使用 GroupDocs.Merger for Java 來分割 PDF 與 Word 文件？
- **統一 API** – 支援 PDF、Word、PowerPoint 等多種格式，無需使用不同工具。  
- **細緻的控制** – 可選擇精確的頁碼範圍、奇偶頁過濾或單頁分割。  
- **效能導向** – 透過串流頁面而非一次載入整份文件，能有效處理大型檔案。  

## 前置條件
- **GroupDocs.Merger for Java**（最新版本）  
- **JDK 8+**  
- 如 IntelliJ IDEA 或 Eclipse 等 IDE  
- 用於相依管理的 Maven 或 Gradle  

## 設定 GroupDocs.Merger for Java
使用您偏好的建置工具將函式庫加入專案。

**Maven**  
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle**  
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**直接下載**：您也可以直接從 [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/) 下載函式庫。

### 取得授權
- **免費試用** – 測試完整功能且無限制。  
- **臨時授權** – 延長評估期間。  
- **購買** – 永久正式授權。

**基本初始化與設定**  
使用 `Merger` 類別並傳入文件路徑即可初始化 GroupDocs.Merger：  
```java
import com.groupdocs.merger.Merger;

String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
Merger merger = new Merger(filePath);
```

## 使用 GroupDocs.Merger for Java 提取特定頁面
本節將示範如何依頁碼範圍分割文件，同時套用奇數頁過濾。

### 步驟 1：定義輸入與輸出路徑
設定來源檔案以及分割檔案的目標檔名模式：  
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToSinglePagesByRangeWithFilter-Output.docx";
```

### 步驟 2：設定分割選項（範圍與過濾）
建立 `SplitOptions` 物件，告訴函式庫要提取哪些頁面以及套用哪種過濾：  
```java
import com.groupdocs.merger.domain.options.SplitOptions;
import com.groupdocs.merger.domain.options.RangeMode;

SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7, RangeMode.OddPages);
```
- **filePathOut** – 目標檔名模式。  
- **3 and 7** – 起始與結束頁碼（含）。  
- **RangeMode.OddPages** – 只保留範圍內的奇數頁，等同於 **提取特定頁面**。

### 步驟 3：執行分割操作
使用先前設定的選項執行分割：  
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

#### 疑難排解提示
- 確認檔案路徑正確且可存取。  
- 確認頁碼在文件的總頁數範圍內；否則會拋出例外。  

## 如何將 PDF 分割為單頁檔（split pdf single pages）
如果需要將每一頁保存為單獨的 PDF，只需將 `RangeMode` 設為 `AllPages`，並指定涵蓋整份文件的範圍。相同的 `SplitOptions` 類別即可處理此情況。

## 如何有效率地分割大型文件（split large document）
處理極大型檔案時，建議將其分成較小的範圍（例如 1‑100、101‑200）以降低記憶體負擔。每次操作後關閉 `Merger` 實例以釋放資源。

## 如何分割 PDF 奇數頁（split pdf odd pages）
上述範例已示範 `OddPages` 過濾。將 `RangeMode.OddPages` 換成 `RangeMode.EvenPages` 即可提取偶數頁。

## 實務應用
1. **文件分段** – 將合約切割成條款層級的 PDF，便於審閱。  
2. **報告管理** – 從冗長的年報中提取特定章節或附錄。  
3. **簡報準備** – 把單獨投影片抽出，以供特定會議使用。  

您亦可將此邏輯與資料庫或內容管理系統整合，實現工作流程自動化。

## 效能考量
- **記憶體管理** – 處理完畢後呼叫 `merger.close()`（或使用 try‑with‑resources）以釋放檔案句柄。  
- **選擇性範圍** – 僅請求真正需要的頁面，可減少 I/O 與 CPU 使用量。  

## 結論
您現在已掌握使用 GroupDocs.Merger for Java 從任何支援的文件類型 **提取特定頁面** 的清晰步驟。此功能可簡化文件工作流程，讓您精準提供使用者所需的內容。

### 後續步驟
- 嘗試不同的 `RangeMode` 值（例如 `EvenPages`、`AllPages`）。  
- 結合分割與 **merge** 功能，以重新排序或串接提取的頁面。  
- 探索完整 API，支援受密碼保護的文件、浮水印等功能。

## 常見問題
**Q: 什麼是 GroupDocs.Merger for Java？**  
A: 一個功能強大的函式庫，可在多種文件格式間執行合併、分割與重新排序頁面。

**Q: 可以在其他程式語言中使用 GroupDocs.Merger 嗎？**  
A: 可以，.NET 與 C++ 也提供類似的功能。

**Q: 文件處理過程中如何處理例外？**  
A: 將呼叫包在 `try‑catch` 區塊，並檢查 `MergerException` 以取得詳細錯誤資訊。

**Q: 能否在不使用奇偶頁過濾的情況下分割文件？**  
A: 當然可以——設定 `RangeMode.AllPages` 或省略過濾參數，即可依精確頁碼分割。

**Q: 使用 GroupDocs.Merger 的系統需求是什麼？**  
A: Java 8 或以上版本，配合相容的 IDE；不需額外的原生相依。

## 資源
- [GroupDocs.Merger 文件說明](https://docs.groupdocs.com/merger/java/)
- [API 參考](https://reference.groupdocs.com/merger/java/)
- [下載函式庫](https://releases.groupdocs.com/merger/java/)
- [購買授權](https://purchase.groupdocs.com/buy)
- [免費試用與臨時授權](https://releases.groupdocs.com/merger/java/)
- [支援論壇](https://forum.groupdocs.com/c/merger/)

---

**最後更新：** 2026-02-06  
**測試環境：** GroupDocs.Merger 最新版本（Java）  
**作者：** GroupDocs