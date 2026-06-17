---
date: 2026-05-22
description: 了解如何使用 GroupDocs.Merger for Java 建立單頁 PDF 檔案並分割 PDF。包括 split pdf java
  的逐步指南以及更多內容。
keywords:
- create single page pdf
- docx to pdf java
- split pdf java
- pdf split by range
- split pdf odd even
schemas:
- author: GroupDocs
  dateModified: '2026-05-22'
  description: Learn how to create single page PDF files and split PDFs using GroupDocs.Merger
    for Java. Includes step-by-step guides for split pdf java and more.
  headline: Create Single Page PDF with GroupDocs.Merger Java
  type: TechArticle
- description: Learn how to create single page PDF files and split PDFs using GroupDocs.Merger
    for Java. Includes step-by-step guides for split pdf java and more.
  name: Create Single Page PDF with GroupDocs.Merger Java
  steps:
  - name: Initialize the Merger
    text: The `Merger` class is GroupDocs.Merger's core component that loads a source
      document and provides split operations. Create an instance by passing the file
      path or an input stream.
  - name: Define the split criteria
    text: Choose the exact page number or range you need. For a single‑page extraction,
      you’ll specify a range like `1‑1`. When you need to **split pdf by range**,
      you can pass multiple ranges such as `1‑5, 6‑10`.
  - name: Execute the split
    text: Call the appropriate `split` method. For example, `merger.split(new int[]{1})`
      extracts the first page, while `merger.splitByRange(new int[][]{{1,5},{6,10}})`
      handles multiple ranges in one call.
  - name: Save the result
    text: Write each output to a file path or return it as a `java.io.InputStream`.
      This makes it easy to integrate with web APIs or store the result in cloud storage.
      > **Pro tip:** When working with large PDFs, call `merger.setOptimizeResources(true)`
      before splitting to reduce memory consumption.
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then perform any split
      operation as usual.
    question: Can I split a password‑protected PDF?
  - answer: Provide a page list containing only odd numbers (e.g., 1,3,5…) to the
      `split` method.
    question: How do I split only the odd pages of a PDF?
  - answer: Absolutely. After loading the DOCX, call `saveAsPdf` on each split segment.
    question: Is it possible to split a DOCX directly into PDFs?
  - answer: PDF, DOCX, PPTX, TXT, HTML, and many image formats (PNG, JPEG, etc.).
    question: What formats does GroupDocs.Merger support for splitting?
  - answer: No. A single GroupDocs.Merger license covers all supported formats.
    question: Do I need a separate license for each file type?
  type: FAQPage
title: 使用 GroupDocs.Merger Java 建立單頁 PDF
type: docs
url: /zh-hant/java/document-splitting/
weight: 12
---

# 使用 GroupDocs.Merger Java 建立單頁 PDF

如果您需要從較大的文件中 **建立單頁 PDF**，或只是將 PDF 拆分成更易於處理的片段，您來對地方了。本指南將帶您了解最常見的拆分情境——多頁文件、頁碼範圍、奇偶頁、DOCX 拆分，甚至基於文字的拆分——使用功能強大的 GroupDocs.Merger Java 函式庫。完成本教學後，您將清楚如何將這些技術整合到自己的應用程式中、提升文件處理效能，並保持程式碼乾淨且易於維護。

## 快速解答
- **「建立單頁 PDF」是什麼意思？** 這表示從來源文件中擷取單一頁面，並將其儲存為獨立的 PDF 檔案。  
- **哪個函式庫負責此工作？** GroupDocs.Merger for Java 提供流暢的 API 以執行所有拆分操作。  
- **我需要授權嗎？** 開發階段可使用臨時授權；正式上線則需完整授權。  
- **可以拆分 PDF 的奇偶頁嗎？** 可以——GroupDocs.Merger 允許依奇數或偶數頁碼過濾。  
- **支援 DOCX 拆分嗎？** 當然支援；您可以逐頁或依自訂範圍拆分 DOCX 檔案。  

## 「建立單頁 PDF」是什麼？
建立單頁 PDF 牽涉到將多頁來源文件（PDF、DOCX、PPTX 等）中的單一頁面擷取出來，並存成自己的 PDF 檔案。此功能常用於產生發票、證書或預覽圖像，只需要特定頁面時特別方便。

## 為什麼使用 GroupDocs.Merger for Java？
GroupDocs.Merger for Java 提供單一且一致的 API，能處理多種文件格式，同時具備高效能與低記憶體使用量。它透過抽象複雜的檔案處理，讓開發者專注於業務邏輯，而非底層處理細節。

- **Unified API** – Works with PDF, DOCX, PPTX, images, and many other formats.  
- **High performance** – Optimized for large files and batch operations; it can process documents up to 2 GB without loading the entire file into memory.  
- **Fine‑grained control** – Split by page range, odd/even pages, or custom delimiters.  
- **Stream‑friendly** – Output can be saved to a file or returned as a stream for web services.  

## 前置條件
- Java 8 或更新版本。  
- 已於專案中加入 GroupDocs.Merger for Java（Maven/Gradle）。  
- 有效的（臨時或完整）GroupDocs 授權檔案。  

## 如何建立單頁 PDF？
使用 GroupDocs.Merger 建立單頁 PDF 的流程包括載入來源檔案、指定精確的頁碼或範圍、呼叫拆分操作，最後將結果保存。此工作流程確保原始文件保持不變，且擷取的頁面會另存為獨立的 PDF 檔案。

`Merger` 類別是載入來源文件並提供拆分功能的核心元件。

### 步驟 1：初始化 Merger
`Merger` 類別是 GroupDocs.Merger 的核心元件，負責載入來源文件並提供拆分操作。透過傳入檔案路徑或輸入串流即可建立實例。

### 步驟 2：定義拆分條件
選擇您需要的精確頁碼或範圍。若要進行單頁擷取，您會指定類似 `1‑1` 的範圍。當需要 **split pdf by range** 時，可傳入多個範圍，例如 `1‑5, 6‑10`。

### 步驟 3：執行拆分
呼叫適當的 `split` 方法。例如 `merger.split(new int[]{1})` 會擷取第一頁，而 `merger.splitByRange(new int[][]{{1,5},{6,10}})` 則一次處理多個範圍。

### 步驟 4：儲存結果
將每個輸出寫入檔案路徑或以 `java.io.InputStream` 形式返回。這讓您能輕鬆整合至 Web API，或將結果存放於雲端儲存。

> **專業提示：** 在處理大型 PDF 時，於拆分前呼叫 `merger.setOptimizeResources(true)` 以降低記憶體使用量。

## 如何將 PDF java 檔案拆分為多頁
`Merger` 類別提供載入與操作 PDF 檔案的主要 API。要將 PDF 拆分為單頁檔案，只需使用 Merger 實例載入文件，然後呼叫不帶參數的 `split` 方法。函式庫會自動為每一頁建立新的 PDF，保留原始內容與中繼資料，非常適合批次處理發票或報表。

## 如何拆分 PDF 奇偶頁
`Merger` 類別是執行文件拆分的核心元件。當您只需要 PDF 的奇數或偶數頁時，將所需的頁碼列表傳入 `split` 函式。Merger 會產生僅包含這些頁面的新文件，讓您快速建立奇數頁或偶數頁的獨立檔案。

## 如何拆分 docx 檔案（如何拆分 docx）
`Merger` 類別同樣支援 DOCX 檔案。使用 `splitByPage` 可為每一頁產生一個 DOCX（或 PDF），若需要 PDF 輸出，可再結合 `saveAsPdf`。此流程一次完成 **docx to pdf java** 的轉換工作。

## 如何將文件拆分為多頁檔案
`Merger` 類別負責拆分操作時的分頁與檔案建立。如果您想將大型文件切割成固定頁數的區塊，只需指定每個輸出檔案的頁數。Merger 會遍歷來源文件，為每個定義的頁數建立新 PDF，簡化大量文件的歸檔、分發與平行處理。

## 可用教學

### [如何使用 GroupDocs.Merger for Java 拆分文件為多頁檔案](./split-documents-multi-page-files-java-groupdocs-merger/)
了解如何使用 GroupDocs.Merger for Java 高效地將大型文件拆分為較小的多頁檔案，輕鬆優化文件管理。

### [如何使用 GroupDocs.Merger for Java 依行間隔拆分文字檔案 | 文件拆分指南](./split-text-file-line-intervals-groupdocs-merger-java/)
學習如何透過行間隔將文字檔案拆分為可管理的段落，使用 GroupDocs.Merger for Java 提升文件處理效率。

### [掌握使用 GroupDocs.Merger for Java 依頁碼範圍拆分文件](./split-documents-page-range-groupdocs-merger-java/)
了解如何使用 GroupDocs.Merger for Java 依特定頁碼範圍拆分文件，並可同時套用奇偶頁等過濾條件。

### [掌握使用 GroupDocs.Merger 的文件拆分：完整指南](./master-document-splitting-groupdocs-merger-java/)
深入了解如何使用 GroupDocs.Merger for Java 高效拆分文件為單頁，涵蓋設定、實作與實務應用。

### [掌握 Java 文件拆分與 GroupDocs.Merger&#58; 將 DOCX 頁面拆分為檔案與串流](./master-java-document-splitting-groupdocs-merger/)
學習如何使用 GroupDocs.Merger for Java 將 DOCX 文件拆分為獨立頁面或串流，提供完整的設定與實作說明。

## 其他資源

- [GroupDocs.Merger for Java 文件說明](https://docs.groupdocs.com/merger/java/)
- [GroupDocs.Merger for Java API 參考](https://reference.groupdocs.com/merger/java/)
- [下載 GroupDocs.Merger for Java](https://releases.groupdocs.com/merger/java/)
- [GroupDocs.Merger 論壇](https://forum.groupdocs.com/c/merger)
- [免費支援](https://forum.groupdocs.com/)
- [臨時授權](https://purchase.groupdocs.com/temporary-license/)

## 常見問題與解決方案
| Issue | Solution |
|-------|----------|
| **大型 PDF 記憶體過載** | 啟用資源最佳化：`merger.setOptimizeResources(true);` |
| **拆分後頁碼不正確** | 請記住頁碼索引從 1 開始，而非 0。 |
| **未找到授權** | 確認 `GroupDocs.Merger.lic` 檔案的路徑，並確保其已加入 classpath。 |
| **拆分 DOCX 後出現空白頁** | 確保來源 DOCX 有正確的分頁符號；若無，請改用 `splitByParagraph` 作為備用方案。 |

## 常見問答

**Q: 可以拆分受密碼保護的 PDF 嗎？**  
A: 可以。使用帶有密碼參數載入文件，之後即可照常執行任何拆分操作。

**Q: 如何只拆分 PDF 的奇數頁？**  
A: 將只包含奇數頁碼的列表（例如 1,3,5…）傳入 `split` 方法即可。

**Q: 能直接將 DOCX 拆分成 PDF 嗎？**  
A: 完全可以。載入 DOCX 後，對每個拆分段落呼叫 `saveAsPdf`。

**Q: GroupDocs.Merger 支援哪些格式的拆分？**  
A: PDF、DOCX、PPTX、TXT、HTML，以及多種影像格式（PNG、JPEG 等）。

**Q: 每種檔案類型需要單獨授權嗎？**  
A: 不需要。單一的 GroupDocs.Merger 授權即可涵蓋所有支援的格式。

**最後更新：** 2026-05-22  
**測試環境：** GroupDocs.Merger 23.11 for Java  
**作者：** GroupDocs  

## 相關教學

- [split pdf java：使用 GroupDocs.Merger 進行文件拆分](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [掌握使用 GroupDocs.Merger for Java 依頁碼範圍拆分文件](/merger/java/document-splitting/split-documents-page-range-groupdocs-merger-java/)
- [使用 GroupDocs.Merger for Java 高效合併 PDF：逐步指南](/merger/java/format-specific-merging/merge-pdfs-groupdocs-merger-java-tutorial/)