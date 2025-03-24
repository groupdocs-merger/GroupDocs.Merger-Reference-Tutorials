---
title: XLS ファイルの結合
linktitle: XLS ファイルの結合
second_title: GroupDocs.Merger .NET API
description: GroupDocs.Merger を使用して .NET で Excel ファイルを結合し、シームレスなドキュメント操作を行う方法を学びます。ステップバイステップのチュートリアルに従ってください。
weight: 11
url: /ja/net/spreadsheet-merging/merging-xls-files/
---
## 導入
このチュートリアルでは、XLS (Excel) ファイルを結合する方法について説明します。GroupDocs.Merger は、開発者が .NET アプリケーション内で簡単にドキュメントを結合、分割、並べ替え、操作できるようにする強力なドキュメント操作 API です。具体的には、GroupDocs.Merger の直感的な方法を使用して、XLS ファイルを段階的に結合することに焦点を当てます。
## 前提条件
始める前に、次の前提条件が設定されていることを確認してください。
- Visual Studio: マシンに Visual Studio をインストールします。
-  GroupDocs.Merger for .NET: GroupDocs.Merger for .NETをダウンロードしてインストールします。[ここ](https://releases.groupdocs.com/merger/net/).
- .NET Framework: .NET Framework がインストールされていることを確認してください。
- サンプル XLS ファイル: 結合する XLS ファイルを準備します。

## 名前空間のインポート
まず、プロジェクトで GroupDocs.Merger を使用するために必要な名前空間をインポートします。
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## ステップ1: 出力ディレクトリを初期化する
まず、結合した XLS ファイルを保存するディレクトリを指定します。
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.xls");
```
## ステップ2: XLSファイルの読み込みと結合
次に、GroupDocs.Merger を使用して XLS ファイルを読み込んで結合します。
```csharp
//ソースXLSファイルをロードする
using (var merger = new Merger("Your Sample File"))
{
    //マージする別のXLSファイルを追加する
    merger.Join("Your Sample File");
    
    //XLSファイルを結合して結果を保存する
    merger.Save(outputFile);
}
```
## ステップ3: 出力場所を表示する
最後に、マージされた XLS ファイルの完了と場所を示すメッセージを表示します。
```csharp
Console.WriteLine("\nXLS files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## 結論
このチュートリアルでは、XLS ファイルを結合する方法を学びました。提供されている手順に従うことで、.NET アプリケーション内で複数の Excel ファイルをプログラム的に効率的に結合できます。

## よくある質問
### GroupDocs.Merger は他のドキュメント形式と互換性がありますか?
はい、GroupDocs.Merger は PDF、DOCX、XLSX、PPTX など、さまざまなドキュメント形式をサポートしています。
### GroupDocs.Merger を使用してドキュメントを分割できますか?
もちろんです! GroupDocs.Merger を使用すると、要件に応じてドキュメントを分割できます。
### GroupDocs.Merger に関するその他のリソースやサポートはどこで見つかりますか?
ドキュメントを参照して質問することができます。[GroupDocs フォーラム](https://forum.groupdocs.com/c/merger/32).
### GroupDocs.Merger の無料トライアルはありますか?
はい、次から始めることができます[無料トライアル](https://releases.groupdocs.com/)機能を評価します。
### GroupDocs.Merger のライセンスを購入するにはどうすればよいですか?
訪問[購入ページ](https://purchase.groupdocs.com/buy)ニーズに合わせたライセンスを取得します。