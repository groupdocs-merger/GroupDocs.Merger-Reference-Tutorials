---
title: EPUB ファイルを結合する
linktitle: EPUB ファイルを結合する
second_title: GroupDocs.Merger .NET API
description: GroupDocs.Merger for .NET を使用して EPUB ファイルをプログラムで結合する方法を学びます。ステップバイステップのチュートリアルに従ってください。
weight: 17
url: /ja/net/document-merging/merge-epub-files/
type: docs
---
# EPUB ファイルを結合する

## 導入
このチュートリアルでは、GroupDocs.Merger for .NET を使用して EPUB ファイルを結合する方法について説明します。GroupDocs.Merger for .NET は、開発者が .NET アプリケーション内でさまざまなドキュメント形式をシームレスに操作および結合できるようにする強力なライブラリです。具体的には、このライブラリを使用して EPUB ファイルを段階的に結合することに焦点を当てます。
## 前提条件
続行する前に、次の前提条件が満たされていることを確認してください。
1. 開発環境: Visual Studio または別の .NET 開発環境がインストールされていること。
2.  GroupDocs.Merger for .NET: GroupDocs.Merger for .NETライブラリをダウンロードしてインストールします。[ダウンロードページ](https://releases.groupdocs.com/merger/net/).
3. EPUB ファイル: テスト用にマージする EPUB ファイルを準備します。

## 名前空間のインポート
まず、.NET プロジェクトで GroupDocs.Merger を操作するために必要な名前空間をインポートします。
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## ステップ1: 出力ディレクトリとファイル名を定義する
結合された EPUB ファイルを保存する出力ディレクトリを設定します。
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.epub");
```
交換する`"Your Output Directory"`希望する出力ディレクトリ パスを入力します。
## ステップ2: ソースEPUBファイルを読み込む
使用`Merger`GroupDocs.Merger ライブラリのクラスを使用して、マージするソース EPUB ファイルを読み込みます。
```csharp
using (var merger = new GroupDocs.Merger.Merger("Path_To_First_EPUB"))
{
    merger.Join("Path_To_Second_EPUB");
    //必要に応じてEPUBファイルを追加します
    //merger.Join("Path_To_Third_EPUB");
    
    // EPUBファイルを結合して結果を保存する
    merger.Save(outputFile);
}
```
交換する`"Path_To_First_EPUB"`そして`"Path_To_Second_EPUB"`EPUBファイルへのパスを追加します。`merger.Join()`追加の EPUB ファイルをマージに含めるように呼び出します。
## ステップ3: 結合したEPUBファイルを保存する
マージ操作を実行し、結果として得られたマージされた EPUB ファイルを保存します。
```csharp
Console.WriteLine("\nEPUB files merge completed successfully. \nCheck output in {0}", outputFolder);
```
このコード スニペットはマージ操作を実行し、出力ディレクトリとともに成功メッセージを表示します。

## 結論
このチュートリアルでは、GroupDocs.Merger for .NET を使用して EPUB ファイルを結合する方法を説明しました。これらの手順に従うことで、ドキュメント結合機能を .NET アプリケーションに効率的に統合できます。

## よくある質問
### Q: GroupDocs.Merger は他のドキュメント形式をマージできますか?
はい。GroupDocs.Merger は、PDF、DOCX、XLSX、PPTX などを含む幅広いドキュメント形式の結合をサポートしています。
### Q: GroupDocs.Merger for .NET は無料で使用できますか?
 GroupDocs.Merger for .NET は商用ライブラリですが、無料試用版でその機能を試すことができます。訪問[ここ](https://releases.groupdocs.com/)体験版の場合。
### Q: GroupDocs.Merger に関するその他のヘルプとサポートはどこで入手できますか?
包括的なドキュメントとサポートは、次の場所で見つけることができます。[GroupDocs.Merger フォーラム](https://forum.groupdocs.com/c/merger/32).
### Q: GroupDocs.Merger の一時ライセンスを取得するにはどうすればよいですか?
 GroupDocs.Merger の一時ライセンスを取得できます[ここ](https://purchase.groupdocs.com/temporary-license/).
### Q: GroupDocs.Merger for .NET はどこで購入できますか?
 GroupDocs.Merger for .NET のライセンスを購入できます。[ここ](https://purchase.groupdocs.com/buy).