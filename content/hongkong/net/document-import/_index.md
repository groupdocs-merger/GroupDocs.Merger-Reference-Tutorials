---
date: 2026-09-11
description: 了解如何使用 GroupDocs.Merger for .NET 將 PDF 匯入 Word 及其他格式，包括在簡單的幾個步驟中嵌入 PDF
  到 Word 以及新增 PDF 附件。
keywords:
- import pdf into word
- embed pdf word
- add pdf attachments
- embed ole excel
- convert diagram pdf
lastmod: 2026-09-11
og_description: 了解如何使用 GroupDocs.Merger for .NET 將 PDF 匯入 Word 及其他格式，涵蓋嵌入 PDF 到 Word、新增
  PDF 附件以及 OLE 嵌入。
og_image_alt: Guide showing how to import PDF into Word using GroupDocs.Merger for
  .NET
og_title: 如何使用 GroupDocs.Merger for .NET 將 PDF 匯入 Word
schemas:
- author: GroupDocs
  dateModified: '2026-09-11'
  description: Learn how to import PDF into Word and other formats using GroupDocs.Merger
    for .NET, including embed PDF Word and add PDF attachments in a few easy steps.
  headline: How to import PDF into Word with GroupDocs.Merger for .NET
  type: TechArticle
- questions:
  - answer: Yes – use the `PageRange` option when calling `Insert` to specify which
      pages to embed.
    question: Can I import only selected pages of a PDF into Word?
  - answer: When embedding as an OLE object, hyperlinks remain functional inside the
      PDF viewer; when converting to native Word content, most hyperlinks are retained.
    question: Does the library preserve hyperlinks inside the PDF when imported?
  - answer: Absolutely. Loop through your PDF collection and call `Insert` for each
      file; the library merges them sequentially.
    question: Is it possible to batch‑import multiple PDFs into a single Word document?
  - answer: Vector graphics are preserved when the PDF is embedded as an OLE object;
      they render sharply at any zoom level.
    question: What if my PDF contains vector graphics?
  - answer: Yes – the .NET Standard build runs on Linux, macOS and Windows without
      any native dependencies.
    question: Does GroupDocs.Merger work on Linux containers?
  type: FAQPage
tags:
- import pdf
- GroupDocs.Merger
- .NET document processing
title: 如何使用 GroupDocs.Merger for .NET 將 PDF 匯入 Word
type: docs
url: /zh-hant/net/document-import/
weight: 10
---

# 如何使用 GroupDocs.Merger for .NET 將 PDF 匯入 Word

在本指南中，您將了解如何 **將 PDF 匯入 Word** 以及其他文件類型，使用 GroupDocs.Merger for .NET。無論您需要在 Word 檔案中嵌入 PDF、將 PDF 附加到現有文件，或在圖表、簡報、試算表與文字處理檔之間移動內容，本教學都會帶您走過最常見的情境，說明其重要性，並展示快速完成任務的確切步驟。

## 快速回答
- **我可以將 PDF 匯入 Word 文件嗎？** 可以 – GroupDocs.Merger 允許您將 PDF 以 OLE 物件或原生內容的形式嵌入 .docx 檔案。  
- **我需要額外的 PDF 函式庫嗎？** 不需要，Merger SDK 內建 PDF 匯入功能，無需其他相依性。  
- **支援哪些 .NET 版本？** .NET Framework 4.5+、.NET Core 3.1+、.NET 5/6/7。  
- **正式環境需要授權嗎？** 正式環境必須使用商業授權；亦提供免費試用版供評估使用。  
- **可以匯入多大的 PDF？** 單檔支援最高 500 MB，且不會將整個文件載入記憶體。

## 什麼是將 PDF 匯入 Word？
將 PDF 匯入 Word 意指將 PDF 檔案的內容放入 Microsoft Word (.docx) 文件中，可作為嵌入物件或轉換為原生元素，同時保留版面配置、圖片與文字格式。此過程能保留文字流、圖片、表格與向量圖形，確保產生的 Word 檔案盡可能接近原始 PDF 的版面。

## 為什麼要使用 GroupDocs.Merger 來完成此任務？
GroupDocs.Merger 支援 **30+ 輸入與輸出格式**，且可在不將整個文件載入 RAM 的情況下處理最高 **500 MB** 的文件，減輕伺服器端應用程式的記憶體壓力。此函式庫亦提供 **內建 OLE 嵌入** 功能，讓您只需一次 API 呼叫即可將 PDF 直接附加至 Word、Excel 或 PowerPoint 檔案。

## 前置條件
- .NET 開發環境（Visual Studio 2022 或更新版本）。  
- 已安裝 GroupDocs.Merger for .NET NuGet 套件 (`Install-Package GroupDocs.Merger`)。  
- 用於正式環境的有效 GroupDocs.Merger 授權（測試可使用臨時授權）。

## 如何一步步將 PDF 匯入 Word

### 如何將 PDF 檔案嵌入 Word 文件？
`Merger` 是 GroupDocs.Merger SDK 的核心類別，提供文件操作方法。  
`Insert` 可將來源文件或物件插入目標文件的指定位置。

使用 `Merger` 載入來源 PDF，然後呼叫 `Insert` 將其放入目標 `.docx`。此操作只需兩行程式碼，且會自動處理 OLE 包裝，使 PDF 以互動物件的形式顯示於 Word 中。

### 如何將 PDF 附件加入現有的 Word 檔案？
`AddAttachment` 可將外部檔案附加至容器文件，並儲存在套件內以供日後取用。

建立 `Merger` 實例，開啟 Word 文件，使用 `AddAttachment` 方法將 PDF 附加。附件會儲存在 Word 套件內，使用者可直接從文件的「插入 > 物件」對話框開啟。

### 如何將 OLE 物件（如 PDF）嵌入 Excel 試算表？
`InsertOleObject` 可將 OLE 物件（例如 PDF）嵌入試算表儲存格，讓使用者在 Excel 中點擊即開啟。

在 Excel 活頁簿上呼叫 `InsertOleObject` 方法。此方法接受 PDF 檔案路徑與儲存格位置，將 PDF 以 OLE 物件形式插入，使用者可雙擊開啟。

## 常見問題與解決方案
- **PDF 只顯示圖示：** 請確保目標 Word 檔案為 `.docx` 副檔名；舊版 `.doc` 不支援嵌入 OLE 物件。  
- **大型 PDF 匯入緩慢：** 在匯入前設定 `MergerSettings.EnableMemoryOptimization = true`，以降低記憶體使用量。  
- **嵌入的 PDF 無法點擊：** 請確認 PDF 未設定密碼保護；Merger 無法在未提供密碼的情況下嵌入加密 PDF。

## 常見問答

**Q: 我可以只匯入 PDF 的特定頁面到 Word 嗎？**  
A: 可以 – 在呼叫 `Insert` 時使用 `PageRange` 參數指定要嵌入的頁面。

**Q: 匯入時會保留 PDF 內的超連結嗎？**  
A: 以 OLE 物件方式嵌入時，超連結在 PDF 檢視器中仍可使用；轉換為原生 Word 內容時，大多數超連結會被保留。

**Q: 能否批次匯入多個 PDF 到同一個 Word 文件？**  
A: 完全可以。遍歷 PDF 集合，對每個檔案呼叫 `Insert`；函式庫會依序合併它們。

**Q: 若 PDF 含有向量圖形，會怎樣？**  
A: 向量圖形在以 OLE 物件嵌入時會被保留，放大縮小皆保持清晰。

**Q: GroupDocs.Merger 能在 Linux 容器上執行嗎？**  
A: 能 – .NET Standard 版可在 Linux、macOS 與 Windows 上執行，且不需任何原生相依性。

## 可用教學

### [Add Attachments to PDFs Using GroupDocs.Merger for .NET&#58; A Step‑By‑Step Guide](./add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)
了解如何使用 GroupDocs.Merger for .NET 為 PDF 添加附件。此步驟說明涵蓋設定、實作與實務應用。

### [Embed PDF as OLE in PowerPoint using GroupDocs.Merger for .NET&#58; A Step‑By‑Step Guide](./embed-pdf-ole-powerpoint-groupdocs-merger-net/)
了解如何將 PDF 檔案作為 OLE 物件無縫嵌入 PowerPoint 簡報，使用 GroupDocs.Merger for .NET。請參考完整教學。

### [Embed PDF in Word Using GroupDocs.Merger for .NET&#58; A Step‑By‑Step Guide](./embed-pdf-word-groupdocs-merger-dotnet/)
了解如何使用 GroupDocs.Merger for .NET 無縫將 PDF 嵌入 Microsoft Word 文件，提升文件的動態內容效能。

### [How to Embed OLE Objects in Excel Spreadsheets Using GroupDocs.Merger for .NET](./embed-ole-objects-groupdocs-merger-net/)
了解如何使用 GroupDocs.Merger for .NET 將 OLE 物件（如 PDF）嵌入 Excel 試算表，增強資料呈現與功能性。

## 其他資源

- [GroupDocs.Merger for .net Documentation](https://docs.groupdocs.com/merger/net/)
- [GroupDocs.Merger for .net API Reference](https://reference.groupdocs.com/merger/net/)
- [Download GroupDocs.Merger for .net](https://releases.groupdocs.com/merger/net/)
- [GroupDocs.Merger Forum](https://forum.groupdocs.com/c/merger)
- [Free Support](https://forum.groupdocs.com/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)

---

**最後更新：** 2026-09-11  
**測試版本：** GroupDocs.Merger 23.12 for .NET  
**作者：** GroupDocs

## 相關教學

- [Embed PDF in Word Using GroupDocs.Merger for .NET: A Step-by-Step Guide](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [Add Attachments to PDFs Using GroupDocs.Merger for .NET: A Step-by-Step Guide](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)
- [Loading PDF from URL in .NET Using GroupDocs.Merger: A Comprehensive Guide](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)