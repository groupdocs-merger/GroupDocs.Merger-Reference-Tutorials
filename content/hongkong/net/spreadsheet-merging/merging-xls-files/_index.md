---
title: 合併 XLS 文件
linktitle: 合併 XLS 文件
second_title: GroupDocs.Merger .NET API
description: 了解如何使用 GroupDocs.Merger 在 .NET 中合併 Excel 文件以實現無縫文件操作。請按照我們的逐步教學進行操作。
type: docs
weight: 11
url: /zh-hant/net/spreadsheet-merging/merging-xls-files/
---
## 介紹
在本教學中，我們將探討如何合併 XLS (Excel) 檔案。 GroupDocs.Merger 是一個功能強大的文件操作 API，使開發人員能夠在其 .NET 應用程式中輕鬆合併、分割、重新排列和操作文件。具體來說，我們將重點放在使用 GroupDocs.Merger 的直覺方法逐步合併 XLS 檔案。
## 先決條件
在我們開始之前，請確保您已設定以下先決條件：
- Visual Studio：在您的電腦上安裝 Visual Studio。
-  GroupDocs.Merger for .NET：從下列位置下載並安裝 GroupDocs.Merger for .NET[這裡](https://releases.groupdocs.com/merger/net/).
- .NET Framework：確保您已安裝 .NET Framework。
- 範例 XLS 檔案：準備要合併的 XLS 檔案。

## 導入命名空間
首先匯入在專案中使用 GroupDocs.Merger 所需的命名空間：
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## 步驟1：初始化輸出目錄
首先，指定要儲存合併的 XLS 檔案的目錄：
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.xls");
```
## 第 2 步：載入並合併 XLS 文件
現在，讓我們使用 GroupDocs.Merger 載入並合併 XLS 檔案：
```csharp
//載入來源 XLS 文件
using (var merger = new Merger("Your Sample File"))
{
    //新增另一個要合併的 XLS 文件
    merger.Join("Your Sample File");
    
    //合併 XLS 檔案並儲存結果
    merger.Save(outputFile);
}
```
## 步驟3：顯示輸出位置
最後，顯示一則訊息，指示合併的 XLS 檔案的完成和位置：
```csharp
Console.WriteLine("\nXLS files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## 結論
在本教程中，我們學習如何合併 XLS 檔案。透過遵循提供的步驟，您可以在 .NET 應用程式中以程式設計方式有效地組合多個 Excel 檔案。

## 常見問題解答
### GroupDocs.Merger 是否與其他文件格式相容？
是的，GroupDocs.Merger 支援各種文件格式，例如 PDF、DOCX、XLSX、PPTX 等。
### 我可以使用 GroupDocs.Merger 拆分文件嗎？
絕對地！ GroupDocs.Merger 可讓您根據需要拆分文件。
### 在哪裡可以找到更多關於 GroupDocs.Merger 的資源和支援？
您可以瀏覽文件並提出問題[集團文檔論壇](https://forum.groupdocs.com/c/merger/32).
### GroupDocs.Merger 是否有免費試用版？
是的，您可以從[免費試用](https://releases.groupdocs.com/)來評估功能。
### 如何購買 GroupDocs.Merger 的許可證？
參觀[購買頁面](https://purchase.groupdocs.com/buy)取得適合您需求的許可證。