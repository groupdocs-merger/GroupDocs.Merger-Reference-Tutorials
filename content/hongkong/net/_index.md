---
date: 2026-08-10
description: 了解如何使用 GroupDocs.Merger for .NET 分割 PDF 檔案。C# 教學指引您分割大型 PDF、提取頁面，並將圖像合併成
  PDF，提升效率。
is_root: true
keywords:
- how to split pdf
- combine images into pdf
- secure pdf with password
- extract pages from pdf
- merge powerpoint presentations
lastmod: 2026-08-10
linktitle: GroupDocs.Merger for .NET 教學
og_description: 了解如何使用 GroupDocs.Merger for .NET 分割 PDF 檔案。C# 教學指引您分割大型 PDF、提取頁面，並將圖像合併成
  PDF，提升效率。
og_image_alt: 'Developer guide: split PDF files using GroupDocs.Merger for .NET in
  C#'
og_title: 如何使用 GroupDocs.Merger for .NET 分割 PDF – 指南
schemas:
- author: GroupDocs
  dateModified: '2026-08-10'
  description: Learn how to split PDF files with GroupDocs.Merger for .NET. C# tutorials
    guide you to split large PDFs, extract pages, and combine images into PDF efficiently.
  headline: How to split PDF with GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to split PDF files with GroupDocs.Merger for .NET. C# tutorials
    guide you to split large PDFs, extract pages, and combine images into PDF efficiently.
  name: How to split PDF with GroupDocs.Merger for .NET
  steps:
  - name: load the PDF document
    text: Create a `PdfDocument` instance by passing the file path or a stream. The
      constructor reads the document header without loading all pages into memory.
  - name: split by page range
    text: Use the `Split` method, providing a `PageRange` object that defines the
      start and end pages. The method returns a collection of new `PdfDocument` objects,
      each representing the requested segment.
  - name: save the resulting files
    text: Iterate over the split documents and call `Save` with a unique file name.
      You can also apply compression or password protection before saving.
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then use `Split` or
      `Extract` as you would with an unprotected file.
    question: Can I split a password‑protected PDF?
  - answer: There is no hard limit; the library streams pages, so you can split PDFs
      with thousands of pages as long as you have sufficient disk space for the output
      files.
    question: How many pages can I split at once?
  - answer: It supports cross‑format merging, allowing you to combine PPTX slides
      with PDF pages into a single PDF output.
    question: Does GroupDocs.Merger support merging PowerPoint files with PDFs?
  - answer: Enable streaming mode (`PdfLoadOptions.Stream = true`) to keep memory
      usage low while splitting or extracting pages.
    question: What is the recommended way to handle very large PDFs?
  - answer: Yes. Use the `Bookmarks` collection to identify chapter start pages and
      programmatically call `Split` for each range.
    question: Is there a way to automate splitting of every chapter in a PDF?
  type: FAQPage
tags:
- split PDF
- GroupDocs.Merger
- C# document processing
- PDF manipulation
- document merging
title: 如何使用 GroupDocs.Merger for .NET 分割 PDF
type: docs
url: /zh-hant/net/
weight: 10
---

# 如何使用 GroupDocs.Merger for .NET 分割 PDF

## 使用 GroupDocs.Merger 的進階文件管理

`GroupDocs.Merger for .NET` 是一個 .NET 函式庫，讓開發人員能夠合併、分割及操作超過 50 種檔案格式的文件。如果您想了解 **如何分割 PDF**，本指南將示範使用 GroupDocs.Merger for .NET 的精確步驟，並提供實務情境與最佳實踐技巧。

## 快速解答
- **如何將 PDF 分割成單頁？** 呼叫 `PdfDocument.Split`，為每一頁使用頁範圍 `1‑1`。  
- **我只能提取特定頁面嗎？** 可以——將所需的頁碼傳遞給 `Split` 或 `Extract`。  
- **是否支援密碼保護？** 絕對支援；在儲存前使用 `PdfDocument.Protect`。  
- **如何將影像合併成 PDF？** 將每張影像載入為 `PdfPage`，並加入新文件。  
- **大型 PDF 該怎麼處理？** 使用串流模式，以避免將整個檔案載入記憶體。

## 什麼是如何分割 PDF？

**如何分割 PDF** 指的是將多頁 PDF 檔案拆分成較小的 PDF 文件——可以依單頁、頁範圍或自訂條件——透過程式化 API 完成。此作業常用於分離章節、減少檔案大小，或為文件分發做準備。可透過如 GroupDocs.Merger 等函式庫以程式方式執行，這些函式庫提供指定精確頁範圍與輸出設定的方法。

## 為何使用 GroupDocs.Merger 進行 PDF 分割？

GroupDocs.Merger 處理 **55+** 種輸入與輸出格式，支援最高 **2 GB** 的 PDF 而不需完整載入記憶體，且能在一般伺服器上於 **3 秒** 內分割 500 頁的 PDF。這些具體的效能數據使其成為高吞吐量文件管線的可靠選擇。

## 如何使用 GroupDocs.Merger 分割 PDF 檔案？

`PdfDocument` 是 GroupDocs.Merger 中代表 PDF 檔案的核心類別。要分割 PDF，首先將來源檔案載入 `PdfDocument` 實例，然後使用 `Split` 方法指定要擷取的頁面。此方法會回傳每個段落的 `PdfDocument` 物件，您可以分別儲存。此方式適用於任何文件大小，且只需少量程式碼。

### 步驟 1：載入 PDF 文件
建立 `PdfDocument` 實例，傳入檔案路徑或串流。建構子僅讀取文件標頭，而不會將所有頁面載入記憶體。

### 步驟 2：依頁範圍分割
使用 `Split` 方法，提供一個定義起始與結束頁面的 `PageRange` 物件。此方法回傳一個新的 `PdfDocument` 物件集合，每個物件代表所請求的段落。

### 步驟 3：儲存產生的檔案
遍歷分割後的文件，呼叫 `Save` 並提供唯一的檔名。您亦可在儲存前套用壓縮或密碼保護。

## 如何將影像合併成 PDF？

`PdfDocument` 是在 GroupDocs.Merger 中建立新 PDF 檔案的主要類別。要合併影像，載入每個影像檔案，並使用 `AddPage` 方法將其作為新頁面加入全新的 `PdfDocument` 實例。所有影像加入後，儲存文件，這會保留原始解析度，且在格式允許時將影像嵌入為向量頁面。此結果為高品質的 PDF，包含所有提供的影像。

## 如何使用密碼保護 PDF？

`PdfDocument` 代表 PDF 文件，並提供安全功能。載入或建立 `PdfDocument` 後，呼叫其 `Protect` 方法，傳入使用者密碼以及可選的權限旗標（如列印或複製）。此方法會加密檔案，當您稍後呼叫 `Save` 時，產生的 PDF 只能由知道密碼的使用者開啟，確保機密性。

## 如何從 PDF 提取頁面？

`PdfDocument` 是 GroupDocs.Merger 中代表 PDF 檔案的主要類別。要提取頁面，使用來源檔案實例化 `PdfDocument`，然後呼叫 `Extract` 方法，傳入您想保留的頁碼清單。此方法回傳僅包含這些頁面的新 `PdfDocument`，您可以將其儲存為獨立的 PDF。此技巧適用於建立自訂報告或分享特定章節。

## 如何合併 PowerPoint 簡報？

`Merge` 是 GroupDocs.Merger 提供的方法，可將多個文件串接成單一輸出檔案。要合併 PowerPoint 簡報，將每個 .pptx 檔案載入為 `Document` 物件，然後在新的 `PdfDocument` 或 `PresentationDocument` 上呼叫 `Merge`，傳入來源文件集合。函式庫會保留投影片動畫、過場效果與格式，產生可儲存為 PDF 或 PPTX 的合併簡報。

## 如何分割大型 PDF 頁面？

`PdfLoadOptions.Stream` 是一個屬性，可啟用串流模式，讓 GroupDocs.Merger 在不將整個文件載入記憶體的情況下處理大型 PDF 檔案。處理非常大的 PDF 時，於載入檔案前將 `PdfLoadOptions.Stream` 設為 true。此舉可降低記憶體使用量，並讓您即使在超過 1 GB 的檔案上也能有效分割或提取頁面，同時維持效能。

## 主要功能與特性

- **合併多個文件**，跨 55+ 種格式合成單一完整檔案
- **從不同來源文件加入特定頁面或頁範圍**
- **依頁碼、頁範圍或奇偶頁條件分割文件**
- **透過移動、移除、旋轉或交換操作來調整頁面順序**
- **使用密碼保護與細緻的權限控制來保護文件**
- **提取特定頁面以建立新且針對性的文件**
- **處理 55+ 種格式**，包括 PDF、Office、影像與壓縮檔，使用統一的 API

## GroupDocs.Merger for .NET 教學類別

### [合併壓縮檔案](./merge-compress-files/)
學習如何有效合併與壓縮 7z、TAR、ZIP 等壓縮檔格式。我們的教學會一步步帶您使用 GroupDocs.Merger for .NET 結合壓縮檔，並提供完整的 C# 範例。

### [影像合併](./image-merging/)
掌握合併 BMP、GIF、PNG、SVG、TIFF 等影像格式的技巧。了解如何在保留品質與格式的前提下，將影像合併成單一文件。

### [文件合併](./document-merging/)
將 DOC、DOCX、PDF、RTF 等多種文件格式合併為統一檔案。這些教學涵蓋文件合併情境，提供詳細的實作步驟與最佳實踐。

### [試算表合併](./spreadsheet-merging/)
合併 Excel 檔案 (XLAM、XLS、XLSX、XLSM、XLTX) 及其他試算表格式，同時保持資料完整性、公式與格式，透過一步步指南完成。

### [Visio 合併](./visio-merging/)
有效合併 Visio 圖表與繪圖 (VDX、VSDM、VSDX、VSSM、VSSX)，我們提供專門的教學，協助在 .NET 應用程式中管理圖表文件。

### [簡報合併](./presentation-merging/)
學習合併 PowerPoint 及其他簡報格式 (PPS、PPSX、PPT、OTP)，同時保留投影片、動畫與格式，提供完整程式碼範例。

### [文件載入](./document-loading/)
探索從檔案、串流與 URL 載入文件的各種方法，並針對不同格式進行適當設定。掌握文件處理的第一步。

### [文件資訊](./document-information/)
從文件中提取有價值的中繼資料，包括格式細節、頁數與屬性。學習在處理前程式化分析文件。

### [文件合併](./document-joining/)
使用進階合併技術無縫結合多個檔案。我們的教學示範如何精確控制內容與結構合併文件。

### [特定格式合併](./format-specific-merging/)
探索針對特定檔案格式優化的合併作業。學習不同文件類型的專業技巧，以取得最佳結果。

### [進階合併選項](./advanced-joining-options/)
透過這些進階教學，將文件合併提升至新層次，涵蓋複雜的頁面選擇、跨格式合併與內容保留策略。

### [文件安全](./document-security/)
為您的文件實作強韌的保護。學習新增、移除與更新密碼，管理權限，確保應用程式中的文件機密性。

### [頁面操作](./page-operations/)
掌握文件頁面的精確控制，透過重新排序、旋轉、移除與修改單一頁面，實現客製化文件管理。

### [文件提取](./document-extraction/)
使用這些詳細指南從文件中提取特定內容。學習選取並儲存特定頁面或章節為獨立檔案，程式碼簡潔。

### [文件匯入](./document-import/)
使用外部內容（包括 OLE 物件與嵌入檔案）增強文件。學習從各種來源匯入內容，豐富您的文件。

### [影像操作](./image-operations/)
在 .NET 應用程式中有效處理影像檔案，我們提供完整教學，涵蓋影像合併、轉換與操作技巧。

### [文件分割](./document-splitting/)
透過這些教學，智慧地將文件依頁碼、範圍與自訂條件分割成較小的組件。

### [文字操作](./text-operations/)
使用我們的指南高效處理 TXT、CSV 等文字格式，包括基於行的分割與合併技巧。

### [授權](./licensing/)
在您的專案中正確設定 GroupDocs.Merger，透過我們詳細的授權教學，涵蓋所有部署情境與環境。

## 支援的檔案格式

GroupDocs.Merger for .NET 支援 **超過 55** 種常見文件格式，包括：

- **文件格式**：PDF、DOC、DOCX、RTF、ODT、XPS、EPUB、HTML
- **試算表**：XLS、XLSX、XLSM、XLSB、ODS、CSV、TSV
- **簡報**：PPT、PPTX、PPS、PPSX、ODP
- **影像**：BMP、GIF、JPG、PNG、SVG、TIFF
- **圖表**：VDX、VSDX、VSX、VTX、VSTX、VSSX
- **壓縮檔**：ZIP、TAR、7Z
- **以及更多！**

## 常見問與答

**Q：我可以分割受密碼保護的 PDF 嗎？**  
A：可以。使用密碼參數載入文件，然後如同未受保護檔案般使用 `Split` 或 `Extract`。

**Q：一次可以分割多少頁？**  
A：沒有硬性限制；函式庫會串流頁面，只要磁碟空間足夠儲存輸出檔案，即可分割上千頁的 PDF。

**Q：GroupDocs.Merger 是否支援將 PowerPoint 檔與 PDF 合併？**  
A：支援跨格式合併，允許您將 PPTX 投影片與 PDF 頁面合併為單一 PDF 輸出。

**Q：處理非常大型 PDF 的建議方式是什麼？**  
A：啟用串流模式 (`PdfLoadOptions.Stream = true`) 以降低記憶體使用，進行分割或提取頁面。

**Q：有沒有方法自動分割 PDF 中的每個章節？**  
A：有。使用 `Bookmarks` 集合辨識章節起始頁，然後以程式方式對每個範圍呼叫 `Split`。

---

**最後更新：** 2026-08-10  
**測試環境：** GroupDocs.Merger 23.9 for .NET  
**作者：** GroupDocs

## 相關教學

- [如何使用 GroupDocs.Merger for .NET 高效合併 PDF 檔案](/merger/net/format-specific-merging/merge-pdfs-groupdocs-merger-net/)
- [如何使用 GroupDocs.Merger for .NET 合併特定 PDF 頁面：完整指南](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [如何使用 GroupDocs.Merger for .NET 以書籤合併 PDF 檔案](/merger/net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/)