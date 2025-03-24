---
title: PDF ファイルの結合
linktitle: PDF ファイルの結合
second_title: GroupDocs.Merger .NET API
description: シームレスなドキュメント管理のために、GroupDocs.Merger を使用して .NET で PDF ファイルをプログラム的に結合する方法を学びます。
weight: 19
url: /ja/net/document-merging/merging-pdf-files/
---
## 導入
ドキュメントの管理と操作の分野では、PDF ファイルの結合は開発者が頻繁に遭遇するタスクです。GroupDocs.Merger for .NET は、.NET アプリケーション内で PDF ドキュメントをシームレスに結合するための堅牢なソリューションを提供します。このチュートリアルでは、GroupDocs.Merger を使用して PDF ファイルを結合するプロセスを順を追って説明し、実装と使用方法を段階的に紹介します。
## 前提条件
チュートリアルに進む前に、次の前提条件を満たしていることを確認してください。
- Visual Studio がシステムにインストールされています。
- C# プログラミング言語の基本的な理解。
- GroupDocs.Merger for .NET ライブラリへのアクセス。

## 名前空間のインポート
まず、C# プロジェクトに必要な名前空間をインポートします。
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## ステップ1: 出力フォルダを初期化する
結合された PDF ファイルを保存する出力ディレクトリを設定します。
```csharp
string outputFolder = "Your_Output_Directory_Path";
```
## ステップ 2: 出力ファイルのパスを定義する
出力フォルダーのパスと、結合された PDF ファイルの希望する名前を組み合わせます。
```csharp
string outputFile = Path.Combine(outputFolder, "merged.pdf");
```
## ステップ3: ソースPDFファイルを読み込む
GroupDocs.Merger を使用して、結合するソース PDF ファイルを読み込みます。
```csharp
using (var merger = new GroupDocs.Merger.Merger("path_to_first_pdf"))
{
    //結合する別のPDFファイルを追加する
    merger.Join("path_to_second_pdf");
    
    //PDFファイルを結合して結果を保存する
    merger.Save(outputFile);
}
```
## ステップ 4: マージ操作を実行する
GroupDocs.Merger を使用して PDF ファイルを結合して保存し、マージ操作を実行します。
```csharp
Console.WriteLine("\nPDF files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## 結論
このチュートリアルでは、GroupDocs.Merger for .NET を使用して PDF ファイルを結合する方法について説明しました。これらの手順に従うことで、.NET アプリケーション内で複数の PDF ドキュメントを 1 つのファイルにシームレスに結合できます。

## よくある質問
### GroupDocs.Merger は大きな PDF ファイルを効率的に処理できますか?
はい、GroupDocs.Merger は大きな PDF ファイルを効率的に処理するように最適化されており、ドキュメント操作タスク中に最適なパフォーマンスを保証します。
### GroupDocs.Merger はパスワードで保護された PDF ファイルをサポートしていますか?
はい、GroupDocs.Merger は、必要な権限があれば、パスワードで保護された PDF ファイルの結合をサポートします。
### GroupDocs.Merger を使用して PDF 以外のドキュメント形式を結合できますか?
いいえ、GroupDocs.Merger は PDF の操作と結合タスク用に特別に設計されています。
### GroupDocs.Merger は .NET Core アプリケーションと互換性がありますか?
はい、GroupDocs.Merger は .NET Framework 環境と .NET Core 環境の両方と互換性があります。
### GroupDocs.Merger はマージ中にブックマークと注釈を保持しますか?
はい、GroupDocs.Merger では、PDF ファイルをマージするときにブックマーク、注釈、その他のドキュメント プロパティが保持されます。