---
title: 使用 GroupDocs.Merger for .NET 合併 DOC 文件
linktitle: 使用 GroupDocs.Merger for .NET 合併 DOC 文件
second_title: GroupDocs.Merger .NET API
description: 了解如何使用 GroupDocs.Merger for .NET 以程式設計方式合併 DOC 檔案。按照我們的逐步指南將多個文件無縫合併為一個。
weight: 10
url: /zh-hant/net/document-merging/merge-doc-files/
type: docs
---
# 使用 GroupDocs.Merger for .NET 合併 DOC 文件

## 介紹
在本教學中，我們將探討如何使用 GroupDocs.Merger for .NET 合併 DOC 檔案。 GroupDocs.Merger for .NET 是一個功能強大的 API，可讓開發人員以程式設計方式組合、分割和操作各種文件格式。透過利用此 API，您可以將多個 DOC 檔案無縫合併到一個文件中。我們將提供逐步說明，引導您完成使用 GroupDocs.Merger for .NET 合併 DOC 檔案的流程。
## 先決條件
在開始之前，請確保您已設定以下先決條件：
1. Visual Studio：在開發電腦上安裝 Visual Studio。
2.  GroupDocs.Merger for .NET：取得 GroupDocs.Merger for .NET 程式庫。您可以從[網站](https://releases.groupdocs.com/merger/net/).
3. C# 知識：對 C# 程式語言的基本了解。
## 導入命名空間
若要開始使用 GroupDocs.Merger for .NET，請將必要的命名空間匯入到您的 C# 專案中：
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## 第 1 步：設定輸出目錄
首先指定將儲存合併的 DOC 檔案的輸出目錄：
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.doc");
```
代替`"Your Output Directory"`以及所需輸出資料夾的路徑。
## 步驟2：載入來源DOC文件
接下來，使用 GroupDocs.Merger 載入要合併的來源 DOC 檔案：
```csharp
using (var merger = new Merger("Your Sample Document File"))
{
    //新增另一個 DOC 文件進行合併
    merger.Join("Your Sample Document File 2");
    //合併DOC文件並儲存結果
    merger.Save(outputFile);
}
```
在此程式碼片段中：
- `"Your Sample Document File"`和`"Your Sample Document File 2"`代表您要合併的 DOC 檔案的路徑。
- `merger.Join(...)`用於將另一個 DOC 檔案新增至合併操作。
- `merger.Save(outputFile)`合併載入的DOC檔案並將合併的文檔儲存到指定的輸出檔案（`merged.doc`）。
確保更換`"Your Sample Document File"`和`"Your Sample Document File 2"`與 DOC 檔案的實際路徑。
## 結論
在本教學中，我們介紹了使用 GroupDocs.Merger for .NET 合併 DOC 檔案的流程。透過執行上述步驟，您可以透過程式設計有效地將多個 DOC 檔案合併到一個文件中。 GroupDocs.Merger for .NET 提供了一個簡單有效的方法來在 .NET 應用程式中操作文件格式。

## 常見問題解答
### GroupDocs.Merger for .NET 能否處理 DOC 以外的其他文件格式？
是的，GroupDocs.Merger for .NET 支援合併各種文件格式，例如 DOCX、PDF、XLSX、PPTX 等。
### GroupDocs.Merger for .NET 是否與 .NET Core 相容？
是的，GroupDocs.Merger for .NET 與 .NET Core 和 .NET Framework 相容。
### GroupDocs.Merger for .NET 是否需要商業用途授權？
是的，商業用途需要有效的許可證。您可以從以下位置取得許可證[集團文件](https://purchase.groupdocs.com/buy).
### 可以免費試用 GroupDocs.Merger for .NET 嗎？
是的，您可以透過免費試用版探索 GroupDocs.Merger for .NET[這裡](https://releases.groupdocs.com/).
### 在哪裡可以獲得 GroupDocs.Merger for .NET 的技術支援？
如需技術援助和社區支持，請訪問[集團文檔論壇](https://forum.groupdocs.com/c/merger/32).