---
title: GroupDocs.Merger for .NET で DOC ファイルを結合する
linktitle: GroupDocs.Merger for .NET で DOC ファイルを結合する
second_title: GroupDocs.Merger .NET API
description: GroupDocs.Merger for .NET を使用して DOC ファイルをプログラムで結合する方法を学びます。ステップバイステップのガイドに従って、複数のドキュメントを 1 つにシームレスに結合します。
type: docs
weight: 10
url: /ja/net/document-merging/merge-doc-files/
---
## 導入
このチュートリアルでは、GroupDocs.Merger for .NET を使用して DOC ファイルを結合する方法について説明します。GroupDocs.Merger for .NET は、開発者がさまざまなドキュメント形式をプログラムで結合、分割、操作できるようにする強力な API です。この API を活用することで、複数の DOC ファイルを 1 つのドキュメントにシームレスに結合できます。GroupDocs.Merger for .NET を使用して DOC ファイルを結合するプロセスを段階的に説明します。
## 前提条件
始める前に、次の前提条件が設定されていることを確認してください。
1. Visual Studio: 開発マシンに Visual Studio をインストールします。
2.  GroupDocs.Merger for .NET: GroupDocs.Merger for .NETライブラリを入手します。[Webサイト](https://releases.groupdocs.com/merger/net/).
3. C# の知識: C# プログラミング言語の基本的な理解。
## 名前空間のインポート
GroupDocs.Merger for .NET の使用を開始するには、必要な名前空間を C# プロジェクトにインポートします。
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## ステップ1: 出力ディレクトリを設定する
まず、結合された DOC ファイルを保存する出力ディレクトリを指定します。
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.doc");
```
交換する`"Your Output Directory"`希望する出力フォルダーへのパスを入力します。
## ステップ2: ソースDOCファイルを読み込む
次に、GroupDocs.Merger を使用して結合するソース DOC ファイルを読み込みます。
```csharp
using (var merger = new Merger("Your Sample Document File"))
{
    //結合する別のDOCファイルを追加する
    merger.Join("Your Sample Document File 2");
    //DOC ファイルを結合して結果を保存する
    merger.Save(outputFile);
}
```
このコードスニペットでは:
- `"Your Sample Document File"`そして`"Your Sample Document File 2"`結合する DOC ファイルへのパスを表します。
- `merger.Join(...)`マージ操作に別の DOC ファイルを追加するために使用されます。
- `merger.Save(outputFile)`読み込まれたDOCファイルを結合し、結合された文書を指定された出力ファイルに保存します（`merged.doc`）。
必ず交換してください`"Your Sample Document File"`そして`"Your Sample Document File 2"`DOC ファイルへの実際のパスを入力します。
## 結論
このチュートリアルでは、GroupDocs.Merger for .NET を使用して DOC ファイルを結合するプロセスについて説明しました。上記の手順に従うことで、複数の DOC ファイルをプログラムで 1 つのドキュメントに効果的に結合できます。GroupDocs.Merger for .NET は、.NET アプリケーション内でドキュメント形式を操作する簡単で効率的な方法を提供します。

## よくある質問
### GroupDocs.Merger for .NET は DOC 以外のドキュメント形式も処理できますか?
はい、GroupDocs.Merger for .NET は、DOCX、PDF、XLSX、PPTX などのさまざまなドキュメント形式のマージをサポートしています。
### GroupDocs.Merger for .NET は .NET Core と互換性がありますか?
はい、GroupDocs.Merger for .NET は .NET Core および .NET Framework と互換性があります。
### GroupDocs.Merger for .NET を商用利用するにはライセンスが必要ですか?
はい、商用利用には有効なライセンスが必要です。ライセンスは以下から取得できます。[グループドキュメント](https://purchase.groupdocs.com/buy).
### GroupDocs.Merger for .NET を無料で試すことはできますか?
はい、無料トライアルを利用して GroupDocs.Merger for .NET を探索できます。[ここ](https://releases.groupdocs.com/).
### GroupDocs.Merger for .NET のテクニカル サポートはどこで受けられますか?
技術サポートとコミュニティ サポートについては、次のサイトにアクセスしてください。[GroupDocs フォーラム](https://forum.groupdocs.com/c/merger/32).