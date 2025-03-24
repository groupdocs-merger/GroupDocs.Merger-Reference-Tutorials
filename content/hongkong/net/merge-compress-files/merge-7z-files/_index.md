---
title: 如何合併 7z 文件
linktitle: 如何合併 7z 文件
second_title: GroupDocs.Merger .NET API
description: 使用 GroupDocs.Merger for .NET 輕鬆合併 7z 檔案。按照我們的逐步指南將多個檔案無縫地合併為一個。
weight: 10
url: /zh-hant/net/merge-compress-files/merge-7z-files/
---

# 如何合併 7z 文件

## 介紹
可以使用強大的文件操作庫 GroupDocs.Merger for .NET 有效率地合併 7z 檔案。本教學將逐步引導您完成整個過程，讓您輕鬆無縫地合併 7z 檔案。
## 先決條件
在開始之前，請確保您具備以下條件：
- Visual Studio 安裝在您的系統上。
- 安裝了 .NET 函式庫的 GroupDocs.Merger。您可以從以下位置下載：[這裡](https://releases.groupdocs.com/merger/net/).
- 對 C# 程式設計有基本了解。

## 導入命名空間
首先，在 C# 程式碼中包含必要的命名空間：
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## 第 1 步：載入來源 7Z 文件
首先指定合併的 7z 檔案的輸出目錄和檔案名稱：
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.7z");
```
## 步驟 2：合併 7Z 文件
載入來源 7Z 檔案並新增您要合併的另一個 7Z 檔案：
```csharp
using (var merger = new Merger("Your Sample File"))
{
    merger.Join("Your Sample File");
    merger.Save(outputFile);
}
```
## 步驟 3：儲存合併的 7Z 文件
執行合併操作並儲存合併後的7Z檔：
```csharp
Console.WriteLine("\n7Z files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## 結論
在本教學中，我們探討如何使用 GroupDocs.Merger for .NET 合併 7z 檔案。透過執行這些簡單的步驟，您可以有效地將多個 7z 檔案合併到一個統一的檔案中。

## 常見問題解答
### 我可以使用 GroupDocs.Merger 合併兩個以上的 7z 檔案嗎？
是的，您可以使用此程式庫將任意數量的 7z 檔案合併在一起。只需使用以下命令添加每個文件`Join`方法。
### GroupDocs.Merger for .NET 是否與其他存檔格式相容？
是的，GroupDocs.Merger 支援合併各種文件格式，包括 ZIP、7z 和 RAR 等存檔。
### 在哪裡可以找到有關 GroupDocs.Merger 的其他支援或協助？
如需進一步協助，請訪問[GroupDocs.Merger 論壇](https://forum.groupdocs.com/c/merger/32).
### 我可以在購買前嘗試 GroupDocs.Merger for .NET 嗎？
是的，您可以透過下載 GroupDocs.Merger 來探索 GroupDocs.Merger 的功能[免費試用版](https://releases.groupdocs.com/).
### 如何取得 GroupDocs.Merger 的臨時授權？
如果您需要臨時許可證，請訪問[這裡](https://purchase.groupdocs.com/temporary-license/).