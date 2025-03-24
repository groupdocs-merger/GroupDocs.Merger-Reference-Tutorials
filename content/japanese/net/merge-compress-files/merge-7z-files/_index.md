---
title: 7z ファイルを結合する方法
linktitle: 7z ファイルを結合する方法
second_title: GroupDocs.Merger .NET API
description: GroupDocs.Merger for .NET を使用して 7z ファイルを簡単に結合します。ステップ バイ ステップ ガイドに従って、複数のアーカイブを 1 つにシームレスに結合します。
weight: 10
url: /ja/net/merge-compress-files/merge-7z-files/
---
## 導入
7z ファイルのマージは、強力なドキュメント操作ライブラリである GroupDocs.Merger for .NET を使用して効率的に行うことができます。このチュートリアルでは、プロセスを段階的にガイドし、7z ファイルをシームレスに簡単にマージできるようにします。
## 前提条件
始める前に、次のものがあることを確認してください。
- Visual Studio がシステムにインストールされています。
-  .NET ライブラリ用の GroupDocs.Merger がインストールされています。からダウンロードできます[ここ](https://releases.groupdocs.com/merger/net/).
- C# プログラミングの基本的な理解。

## 名前空間のインポート
まず、必要な名前空間を C# コードに含めます。
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## ステップ 1: ソース 7Z ファイルをロードする
まず、マージされた 7z ファイルの出力ディレクトリとファイル名を指定します。
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.7z");
```
## ステップ 2: 7Z ファイルをマージする
ソース 7Z ファイルをロードし、マージする別の 7Z ファイルを追加します。
```csharp
using (var merger = new Merger("Your Sample File"))
{
    merger.Join("Your Sample File");
    merger.Save(outputFile);
}
```
## ステップ 3: マージされた 7Z ファイルを保存する
マージ操作を実行し、結果のマージされた 7Z ファイルを保存します。
```csharp
Console.WriteLine("\n7Z files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## 結論
このチュートリアルでは、GroupDocs.Merger for .NET を使用して 7z ファイルをマージする方法を検討しました。これらの簡単な手順に従うことで、複数の 7z ファイルを単一の統合アーカイブに効率的に結合できます。

## よくある質問
### GroupDocs.Merger を使用して 2 つ以上の 7z ファイルを結合できますか?
はい、このライブラリを使用して任意の数の7zファイルを結合できます。各ファイルを`Join`方法。
### GroupDocs.Merger for .NET は他のアーカイブ形式と互換性がありますか?
はい、GroupDocs.Merger は、ZIP、7z、RAR などのアーカイブを含むさまざまなドキュメント形式のマージをサポートしています。
### GroupDocs.Merger に関する追加のサポートや支援はどこで受けられますか?
さらに詳しい情報については、[GroupDocs.Merger フォーラム](https://forum.groupdocs.com/c/merger/32).
### 購入前に GroupDocs.Merger for .NET を試すことはできますか?
はい、GroupDocs.Mergerの機能を試すには、[無料試用版](https://releases.groupdocs.com/).
### GroupDocs.Merger の一時ライセンスを取得するにはどうすればよいですか?
一時ライセンスが必要な場合は、[ここ](https://purchase.groupdocs.com/temporary-license/).