---
date: '2026-09-21'
description: 了解如何使用 GroupDocs.Merger for .NET 在 PowerPoint 中將 PDF 嵌入為 OLE 物件。本分步指南會展示精確的
  API 呼叫與最佳實踐。
keywords:
- embed pdf in powerpoint
- convert pdf to ole
- insert pdf as ole
- add ole object powerpoint
lastmod: '2026-09-21'
og_description: 使用 GroupDocs.Merger for .NET 在 PowerPoint 中嵌入 PDF。請參考本精簡教學，了解如何新增
  OLE 物件、設定選項，並避免常見問題。
og_image_alt: Screenshot of PowerPoint slide with embedded PDF OLE object using GroupDocs.Merger
og_title: 在 PowerPoint 中嵌入 PDF – 以 OLE 方式嵌入 PDF（使用 GroupDocs.Merger）
schemas:
- author: GroupDocs
  dateModified: '2026-09-21'
  description: Learn how to embed pdf in powerpoint as an OLE object with GroupDocs.Merger
    for .NET. This step‑by‑step guide shows you the exact API calls and best practices.
  headline: How to embed pdf in powerpoint as OLE using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to embed pdf in powerpoint as an OLE object with GroupDocs.Merger
    for .NET. This step‑by‑step guide shows you the exact API calls and best practices.
  name: How to embed pdf in powerpoint as OLE using GroupDocs.Merger for .NET
  steps:
  - name: '**Corporate briefings** – attach the latest financial report without inflating
      the deck size.'
    text: '**Corporate briefings** – attach the latest financial report without inflating
      the deck size.'
  - name: '**Academic lectures** – provide full‑text research papers alongside slide
      summaries.'
    text: '**Academic lectures** – provide full‑text research papers alongside slide
      summaries.'
  - name: '**Project status updates** – embed a live project plan that stakeholders
      can open for details.'
    text: '**Project status updates** – embed a live project plan that stakeholders
      can open for details.'
  - name: '**Sales decks** – include product spec sheets that sales reps can open
      on demand.'
    text: '**Sales decks** – include product spec sheets that sales reps can open
      on demand.'
  - name: '**Technical workshops** – present schematics or datasheets that engineers
      can inspect instantly.'
    text: '**Technical workshops** – present schematics or datasheets that engineers
      can inspect instantly.'
  type: HowTo
- questions:
  - answer: Yes. Call `ImportDocument` for each PDF, specifying a different `SlideNumber`
      or position on the same slide.
    question: Can I embed multiple PDFs into a single presentation?
  - answer: The practical limit is dictated by your server’s memory; embeddings of
      up to 500 MB have been tested without issues when streaming.
    question: How large a PDF can I embed?
  - answer: Absolutely. The embedded PDF opens in the default viewer, preserving all
      internal links and bookmarks.
    question: Does the OLE object retain interactive elements like hyperlinks?
  - answer: Provide the password via the `Password` property of `OlePresentationOptions`
      before calling `ImportDocument`.
    question: What if the PDF is password‑protected?
  - answer: The OLE format is supported by PowerPoint 2007 and later, including Office
      365.
    question: Will the embedded object work on all versions of PowerPoint?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- OLE object
- PowerPoint automation
title: 如何使用 GroupDocs.Merger for .NET 在 PowerPoint 中以 OLE 方式嵌入 PDF
type: docs
url: /zh-hant/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/
weight: 1
---

# 在 PowerPoint 中以 OLE 方式嵌入 PDF，使用 GroupDocs.Merger for .NET

將 PDF 直接嵌入 PowerPoint 投影片，可讓您保持原始文件完整，同時讓觀眾即時存取。於本教學中，您將學習 **如何在 PowerPoint 中嵌入 PDF** 作為 OLE 物件，使用 GroupDocs.Merger for .NET，了解所需的 API 選項，並發掘可靠效能的技巧。

## 快速回答
- **哪個函式庫負責 OLE 嵌入？** GroupDocs.Merger for .NET 提供 `OlePresentationOptions` 類別以實現此功能。  
- **我需要授權嗎？** 試用授權可用於開發；正式授權則需於生產環境使用。  
- **我可以嵌入多個 PDF 嗎？** 可以——對每個目標投影片重複匯入步驟。  
- **支援哪些 .NET 版本？** .NET Framework 4.5+、.NET Core 3.1+、.NET 5/6/7。  
- **此過程記憶體效率高嗎？** API 以串流方式處理檔案，即使是上百頁的 PDF 也能在不將整個檔案載入記憶體的情況下嵌入。

## 何謂在 PowerPoint 中嵌入 PDF？
**在 PowerPoint 中嵌入 PDF** 指將 PDF 檔案作為 OLE（Object Linking and Embedding）物件插入，使投影片顯示圖示或預覽，雙擊時會在預設檢視器中開啟原始 PDF。此方式可保留來源文件的格式、超連結與安全設定。

## 為何使用 OLE 嵌入而非轉換 PDF？
嵌入可保持原始檔案大小與版面不變，避免轉換錯誤，且能在不重新匯出簡報的情況下更新來源 PDF。GroupDocs.Merger 支援 **50+ 種輸入與輸出格式**，且可嵌入高達數百 MB 的 PDF，同時以串流方式處理資料，使記憶體使用量低於 100 MB。

## 前置條件
- Visual Studio 2022（或任何相容 .NET 的 IDE）  
- .NET Framework 4.5+ 或 .NET Core 3.1+ 執行環境  
- 有效的 GroupDocs.Merger for .NET 授權（試用或商業）  
- 一個 PowerPoint (.pptx) 檔案以及您想要嵌入的 PDF  

## 設定 GroupDocs.Merger for .NET

### 如何安裝函式庫？
**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI** – 搜尋 “GroupDocs.Merger” 並點擊 **Install** 取得最新版本。

### 如何取得授權？
- **免費試用** – 在 GroupDocs 官方網站註冊以取得臨時授權金鑰。  
- **臨時授權** – 若需要超過 30 天，可申請延長試用。  
- **正式購買** – 購買商業授權以無限制使用於生產環境。

### 如何初始化 API？
`Merger` 是提供文件操作（如匯入、合併與轉換）的主要類別。  
在 C# 檔案頂部加入必要的 `using` 指令，並使用授權檔案路徑建立 `Merger` 實例：

```csharp
using System;
using GroupDocs.Merger.Domain.Options;
using GroupDocs.Merger;
using System.IO;
```  

## 實作指南

### 如何以 OLE 方式在 PowerPoint 中嵌入 PDF？
載入簡報、設定 OLE 選項，然後呼叫匯入方法——整個操作分為三個邏輯步驟完成。

**步驟 1 – 定義檔案位置**  
指定來源 PDF、目標 PowerPoint 檔案以及修改後簡報要儲存的資料夾之絕對或相對路徑。

**步驟 2 – 設定 OLE 選項**  
`OlePresentationOptions` 是告訴 GroupDocs.Merger 要嵌入哪個檔案、於哪張投影片以及座標位置的類別。它亦可設定嵌入物件的寬度、高度與顯示模式。

**步驟 3 – 匯入 PDF**  
`ImportDocument` 為 Merger API 的呼叫，使用提供的選項將 OLE 物件插入 PowerPoint 檔案。此方法以串流方式將 PDF 載入投影片，無需將整個文件載入記憶體。

#### 定義說明
- `OlePresentationOptions` 為定義嵌入檔案、其位置 (X/Y)、大小與目標投影片編號的選項容器。  
- `ImportDocument` 為 Merger API 的呼叫，使用提供的選項將 OLE 物件插入 PowerPoint 檔案。

## 常見設定參數
- **SlideNumber** – 承載 OLE 物件之投影片的 1 起始索引。  
- **XCoordinate / YCoordinate** – 從投影片左上角起算，以點 (points) 為單位的座標位置。  
- **Width / Height** – OLE 佔位區的寬度與高度；設為 0 以使用預設尺寸。  
- **ObjectName** – 可選的友好名稱，於 PowerPoint 中選取物件時顯示。

## 實務應用
將 PDF 以 OLE 物件嵌入於多種實務情境中表現卓越：

1. **公司簡報** – 附上最新財務報告，且不會使簡報檔案過大。  
2. **學術講座** – 提供完整研究論文，配合投影片摘要。  
3. **專案狀態更新** – 嵌入即時專案計畫，讓利害關係人可開啟查看細節。  
4. **銷售簡報** – 包含產品規格表，讓業務人員可隨時開啟。  
5. **技術工作坊** – 呈現圖表或資料表，讓工程師即時檢視。

## 效能考量
為了讓嵌入過程快速且節省記憶體：

- **串流檔案** – GroupDocs.Merger 以串流方式讀寫，即使是 200 頁的 PDF 也只佔用不到 100 MB 記憶體。  
- **批次處理** – 更新多個簡報時，重複使用同一個 `Merger` 實例，並及時關閉串流。  
- **調整大型 PDF** – 若發現載入緩慢，可壓縮或降採樣來源 PDF 中的圖像。

## 常見問答

**Q: 我可以在同一個簡報中嵌入多個 PDF 嗎？**  
A: 可以。對每個 PDF 呼叫 `ImportDocument`，並指定不同的 `SlideNumber` 或同一投影片上的不同位置。

**Q: 我能嵌入多大的 PDF？**  
A: 實際上限受伺服器記憶體限制；以串流方式測試過最高可達 500 MB，未見問題。

**Q: OLE 物件會保留超連結等互動元素嗎？**  
A: 當然會。嵌入的 PDF 會在預設檢視器開啟，保留所有內部連結與書籤。

**Q: 若 PDF 受密碼保護該怎麼辦？**  
A: 在呼叫 `ImportDocument` 前，於 `OlePresentationOptions` 的 `Password` 屬性提供密碼。

**Q: 嵌入的物件能在所有版本的 PowerPoint 上運作嗎？**  
A: OLE 格式自 PowerPoint 2007 起即受支援，亦包括 Office 365。

## 結論
您現在已掌握使用 GroupDocs.Merger for .NET 以 OLE 物件 **在 PowerPoint 中嵌入 PDF** 的完整、可投入生產的工作流程。透過串流檔案、設定 `OlePresentationOptions`，並呼叫 `ImportDocument`，即可在簡報中加入原始 PDF，同時保持低記憶體使用並保留所有互動功能。可進一步探索 Merger 的其他功能，如合併投影片、格式轉換與加浮水印，以自動化文件流程。

---

**最後更新：** 2026-09-21  
**測試環境：** GroupDocs.Merger 23.12 for .NET  
**作者：** GroupDocs  

## 資源
- **文件說明：** [GroupDocs.Merger for .NET Documentation](https://docs.groupdocs.com/merger/net/)  
- **API 參考：** [GroupDocs.Merger API Reference](https://reference.groupdocs.com/merger/net/)  
- **下載：** [GroupDocs.Merger Downloads](https://releases.groupdocs.com/merger/net/)  
- **購買：** [Buy GroupDocs License](https://purchase.groupdocs.com/buy)  
- **免費試用：** [GroupDocs Free Trial](https://releases.groupdocs.com/merger/net/)  
- **臨時授權：** [Get a Temporary License](https://purchase.groupdocs.com/temporary-license)

```csharp
string filePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pptx"); // Presentation file path
string embeddedFilePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pdf"); // PDF to embed as OLE object
string outputDirectoryPath = "YOUR_OUTPUT_DIRECTORY"; // Output directory for modified presentation
string filePathOut = Path.Combine(outputDirectoryPath, "ModifiedPresentation.pptx"); // Output file path
```

```csharp
int pageNumber = 2; // Slide number to add OLE object
OlePresentationOptions oleSlidesOptions = new OlePresentationOptions(embeddedFilePath, pageNumber)
{
    X = 10, // X-coordinate for positioning the embedded object on the slide
    Y = 10  // Y-coordinate for positioning the embedded object on the slide
};
```

```csharp
using (Merger merger = new Merger(filePath)) // Initialize with presentation file path
{
    merger.ImportDocument(oleSlidesOptions); // Embed PDF as OLE using specified options
    merger.Save(filePathOut); // Save the modified presentation to output directory
}
```

## 相關教學

- [在 Word 中嵌入 PDF 使用 GroupDocs.Merger for .NET：逐步指南](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [在 .NET 中從 URL 載入 PDF使用 GroupDocs.Merger：完整指南](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)
- [如何使用 GroupDocs.Merger for .NET 取得文件資訊：完整指南](/merger/net/document-information/retrieve-document-info-groupdocs-merger-dotnet/)