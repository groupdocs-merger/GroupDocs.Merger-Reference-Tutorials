---
title: 合併 SVGZ 文件
linktitle: 合併 SVGZ 文件
second_title: GroupDocs.Merger .NET API
description: 透過此逐步教學，了解如何使用 GroupDocs.Merger for .NET 合併 SVGZ 檔案。提升您的文件處理技能。
weight: 14
url: /zh-hant/net/image-merging/merging-svgz-files/
type: docs
---
# 合併 SVGZ 文件

## 介紹
在本教學中，我們將探討如何使用 GroupDocs.Merger for .NET 合併 SVGZ（可縮放向量圖形）檔案。 GroupDocs.Merger 是一個功能強大的文件操作 API，可讓開發人員對不同的文件格式執行各種操作，包括合併、分割和重新排列頁面。
## 先決條件
在開始之前，請確保您具備以下條件：
- Visual Studio：在您的系統上安裝 Visual Studio IDE。
-  GroupDocs.Merger for .NET：下載 GroupDocs.Merger 函式庫並包含在您的專案中。你可以找到下載的[這裡](https://releases.groupdocs.com/merger/net/).
- 對C#的基本了解：熟悉C#程式語言。

## 導入命名空間
首先，包含存取 GroupDocs.Merger 功能所需的命名空間：
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```

現在，讓我們將使用 GroupDocs.Merger 合併 SVGZ 檔案的過程分解為簡單的步驟：
## 第 1 步：定義輸出目錄和文件
首先指定儲存合併檔案的目錄：
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.svgz");
```
代替`"Your Output Directory"`與系統上所需的路徑。
## 步驟 2：載入來源 SVGZ 文件
使用 GroupDocs.Merger 載入來源 SVGZ 檔案：
```csharp
using (var merger = new Merger("Your Sample File"))
{
    //使用垂直連接模式定義影像連接選項
    var joinOptions = new ImageJoinOptions(ImageJoinMode.Vertical);
    //新增另一個 SVGZ 檔案進行合併
    merger.Join("Your Sample File", joinOptions);
    //合併 SVGZ 檔案並儲存結果
    merger.Save(outputFile);
}
```
代替`"Your Sample File"`以及 SVGZ 檔案的路徑。
## 第三步：執行合併操作
執行合併程序並儲存合併的 SVGZ 檔案：
```csharp
Console.WriteLine("\nSVGZ files merge completed successfully. \nCheck output in {0}", outputFolder);
```
此程式碼片段垂直合併 SVGZ 文件，合併後的文件保存在指定的輸出目錄中。

## 結論
在本教學中，我們學習如何使用 GroupDocs.Merger for .NET 合併 SVGZ 檔案。透過執行這些步驟，您可以將文件合併功能有效地整合到您的 .NET 應用程式中。

## 常見問題解答
### GroupDocs.Merger 可以處理 SVGZ 以外的其他檔案格式嗎？
是的，GroupDocs.Merger 支援各種文件格式，包括 PDF、Word、Excel、PowerPoint 等。
### 在哪裡可以找到 GroupDocs.Merger 的詳細文件？
參觀[文件](https://tutorials.groupdocs.com/merger/net/)獲取全面的資訊和使用範例。
### GroupDocs.Merger 是否有免費試用版？
是的，您可以免費試用[這裡](https://releases.groupdocs.com/).
### 我如何獲得 GroupDocs.Merger 的支援？
加入[集團文檔論壇](https://forum.groupdocs.com/c/merger/32)尋求協助並與其他使用者互動。
### 哪裡可以購買 GroupDocs.Merger 的許可證？
購買許可證[這裡](https://purchase.groupdocs.com/buy)或獲得臨時許可證[這裡](https://purchase.groupdocs.com/temporary-license/).