---
title: 合併 PDF 文件
linktitle: 合併 PDF 文件
second_title: GroupDocs.Merger .NET API
description: 了解如何使用 GroupDocs.Merger 在 .NET 中以程式設計方式合併 PDF 文件，以實現無縫文件管理。
weight: 19
url: /zh-hant/net/document-merging/merging-pdf-files/
type: docs
---
# 合併 PDF 文件

## 介紹
在文件管理和操作領域，合併 PDF 文件是開發人員遇到的常見任務。 GroupDocs.Merger for .NET 提供了一個強大的解決方案，可在 .NET 應用程式中無縫組合 PDF 文件。本教學將引導您完成使用 GroupDocs.Merger 合併 PDF 檔案的流程，以展示逐步實施和使用。
## 先決條件
在深入學習本教程之前，請確保您具備以下先決條件：
- Visual Studio 安裝在您的系統上。
- 對 C# 程式語言有基本了解。
- 存取 GroupDocs.Merger for .NET 程式庫。

## 導入命名空間
首先在 C# 專案中導入必要的命名空間：
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## 第 1 步：初始化輸出資料夾
設定將儲存合併的 PDF 檔案的輸出目錄：
```csharp
string outputFolder = "Your_Output_Directory_Path";
```
## 步驟2：定義輸出檔案路徑
將輸出資料夾路徑與合併 PDF 檔案的所需名稱結合：
```csharp
string outputFile = Path.Combine(outputFolder, "merged.pdf");
```
## 第 3 步：載入來源 PDF 文件
使用 GroupDocs.Merger 載入要合併的來源 PDF 檔案：
```csharp
using (var merger = new GroupDocs.Merger.Merger("path_to_first_pdf"))
{
    //新增另一個 PDF 文件進行合併
    merger.Join("path_to_second_pdf");
    
    //合併 PDF 文件並儲存結果
    merger.Save(outputFile);
}
```
## 第四步：執行合併操作
透過使用 GroupDocs.Merger 加入並儲存 PDF 檔案來執行合併操作：
```csharp
Console.WriteLine("\nPDF files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## 結論
在本教學中，我們探討如何使用 GroupDocs.Merger for .NET 合併 PDF 檔案。透過執行這些步驟，您可以在 .NET 應用程式中將多個 PDF 文件無縫合併為一個文件。

## 常見問題解答
### GroupDocs.Merger 能否有效處理大型 PDF 檔案？
是的，GroupDocs.Merger 經過最佳化，可有效處理大型 PDF 文件，確保文件操作任務期間的最佳效能。
### GroupDocs.Merger 是否支援受密碼保護的 PDF 檔案？
是的，GroupDocs.Merger 支援合併受密碼保護的 PDF 文件，前提是您擁有必要的權限。
### 我可以使用 GroupDocs.Merger 合併非 PDF 文件格式嗎？
不，GroupDocs.Merger 是專門為 PDF 操作和合併任務而設計的。
### GroupDocs.Merger 與 .NET Core 應用程式相容嗎？
是的，GroupDocs.Merger 與 .NET Framework 和 .NET Core 環境相容。
### GroupDocs.Merger 在合併期間是否保留書籤和註釋？
是的，GroupDocs.Merger 可確保在合併 PDF 檔案時保留書籤、註解和其他文件屬性。