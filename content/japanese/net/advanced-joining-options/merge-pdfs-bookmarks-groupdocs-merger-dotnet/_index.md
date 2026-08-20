---
date: '2026-08-20'
description: GroupDocs.Merger for .NET を使用してブックマーク付き PDF を結合する方法を学びます。セットアップ、コード例、PDF
  文書を結合するベストプラクティスを含みます。
keywords:
- merge pdfs with bookmarks
- merge pdf with bookmarks
- combine pdf documents c#
lastmod: '2026-08-20'
og_description: GroupDocs.Merger for .NET を使用してブックマーク付き PDF を結合する方法を学びます。ナビゲーションを保持しながら
  PDF 文書を結合するステップバイステップのコードをご覧ください。
og_image_alt: Guide showing PDF merge with bookmarks in .NET using GroupDocs.Merger
og_title: GroupDocs.Merger for .NET を使用してブックマーク付き PDF を結合する方法
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for .NET,
    including setup, code examples, and best practices for combining PDF documents.
  headline: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for .NET,
    including setup, code examples, and best practices for combining PDF documents.
  name: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
  steps:
  - name: define directory paths
    text: Set up source and output folders so the code can locate the PDFs you want
      to merge. csharp string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY"; string
      outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
  - name: load the primary PDF
    text: '`Merger` represents the main document you’ll append others to. csharp using
      (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
      { // Code to merge additional files will be here. }'
  - name: configure bookmark‑preserving options
    text: '`PdfJoinOptions` controls how the merge behaves; the `UseBookmarks` flag
      tells the engine to keep existing bookmarks. csharp var pdfJoinOptions = new
      PdfJoinOptions { UseBookmarks = true };'
  - name: add additional PDFs
    text: Call `Join` for each extra file. The library automatically merges their
      bookmark trees under the main document’s outline. csharp merger.Join(Path.Combine(documentDirectory,
      "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
  - name: save the merged PDF
    text: Specify the output path and format; the library writes a single PDF that
      retains all bookmark entries. csharp string outputFile = Path.Combine(outputDirectory,
      "merged.pdf"); merger.Save(outputFile);
  type: HowTo
- questions:
  - answer: GroupDocs.Merger is a .NET library that lets you merge, split, rotate,
      and otherwise manipulate PDF and other document formats programmatically.
    question: What is GroupDocs.Merger?
  - answer: Yes – call `Join` repeatedly or pass a collection of file paths to merge
      any number of PDFs in one operation.
    question: Can I merge more than two PDF files at a time?
  - answer: Obtain a permanent license from the GroupDocs purchase page; the trial
      license works only for evaluation and expires after 30 days.
    question: How do I handle licensing for production use?
  - answer: Ensure `PdfJoinOptions.UseBookmarks` is set to `true` and that each source
      PDF actually contains bookmarks before merging.
    question: My merged PDF shows no bookmarks—what went wrong?
  - answer: Absolutely – it supports .NET Core 3.1+, .NET 5/6, and the full .NET Framework
      4.6.1+.
    question: Is the library compatible with .NET Core and .NET Framework?
  type: FAQPage
tags:
- merge pdf
- GroupDocs.Merger
- .NET PDF processing
title: GroupDocs.Merger for .NET を使用してブックマーク付き PDF を結合する方法
type: docs
url: /ja/net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/
weight: 1
---

# GroupDocs.Merger for .NET を使用したブックマーク付き PDF のマージ方法

複数の PDF ファイルをマージし、元のブックマークをそのまま保持することで、手動での再構成にかかる時間を何時間も節約できます。このチュートリアルでは、GroupDocs.Merger for .NET を使用して **ブックマーク付き PDF をマージ** する方法を、プロジェクトのセットアップから完全な本番対応コードサンプルまで学びます。

## クイック回答
- **どのライブラリがブックマーク保持マージをサポートしていますか？** GroupDocs.Merger for .NET.  
- **複数の PDF を同時にマージできますか？** はい – 必要なだけソースファイルを追加できます。  
- **開発にライセンスは必要ですか？** テストには無料トライアルで動作しますが、本番環境では永続ライセンスが必要です。  
- **.NET Core はサポートされていますか？** 完全にサポートしています – ライブラリは .NET Core、.NET 5/6、そしてフル .NET Framework で動作します。  
- **取り扱える最大ファイルサイズは？** ドキュメントあたり最大 2 GB で、全体をメモリに読み込まずに処理できます。

## ブックマーク付き PDF のマージとは何ですか？
**ブックマーク付き PDF のマージ** とは、�数の PDF ドキュメントを 1 つのファイルに結合し、各ソースドキュメントのブックマーク階層をそのまま保持することを意味します。生成された PDF は元のナビゲーション構造を保持し、読者は各個別ファイルから由来するセクションへ直接ジャンプできるため、大規模なレポートやマニュアルの統合に不可欠です。

## なぜブックマーク付き PDF をマージするのか？
PDF をマージする際にブックマークを保持すると、統合ドキュメント内のナビゲーションが向上し、ユーザーはファイル全体をスクロールせずに特定の章やセクションを素早く見つけられます。GroupDocs.Merger は元のアウトライン階層を維持し、手動での再構成作業を削減、最大 2 GB の大容量ファイルを最小限のメモリで処理できるため、エンタープライズ規模のワークフローに最適です。

## 前提条件
- **.NET Core SDK**（3.1 以降）または **.NET Framework**（4.6.1 以上）。  
- **Visual Studio 2022** または .NET 開発をサポートする任意の IDE。  
- 基本的な C# の知識とファイル I/O の経験。  

## GroupDocs.Merger for .NET のセットアップ

### インストール
以下のコマンドのいずれかでライブラリをプロジェクトに追加します。

**.NET CLI:**  
```  
```bash
dotnet add package GroupDocs.Merger
```  
```  

**Package Manager:**  
```  
```powershell
Install-Package GroupDocs.Merger
```  
```  

**NuGet Package Manager UI:**  
- 「GroupDocs.Merger」を検索し、最新バージョンをインストールします。

### ライセンス取得
- **無料トライアル:** [GroupDocs リリース](https://releases.groupdocs.com/merger/net/) ページからダウンロードしてください。  
- **一時ライセンス:** [GroupDocs 一時ライセンスページ](https://purchase.groupdocs.com/temporary-license/) から取得してください。  
- **フルライセンス:** [GroupDocs 購入ページ](https://purchase.groupdocs.com/buy) で購入してください。  

### 基本的な初期化
`Merger` クラスはすべてのマージ操作のエントリーポイントです。  
```  
```csharp
using GroupDocs.Merger;
```  
```  
この名前空間により、PDF 操作機能のすべてにアクセスできます。

## .NET でブックマーク付き PDF をマージする方法

メインの PDF を読み込み、ブックマーク処理を設定し、追加ファイルを加えて結果を保存します – これらは数行のコードで実行できます。

**直接回答（40‑70 語）:**  
最初の PDF で `Merger` インスタンスを作成し、`PdfJoinOptions.UseBookmarks` を有効にして、`Join` で各後続 PDF を追加し、`Save` を呼び出して結合ファイルを書き出します。この方法はすべての元のブックマーク階層を保持し、単一パスで実行されるためメモリ使用量を最小化します。

### 手順 1: ディレクトリパスの定義
コードがマージしたい PDF を見つけられるように、ソースフォルダーと出力フォルダーを設定します。  
```  
```csharp
   string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY";
   string outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
   ```  
```  

### 手順 2: メイン PDF の読み込み
`Merger` は、他の PDF を追加するメインドキュメントを表します。  
```  
```csharp
   using (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
   {
       // Code to merge additional files will be here.
   }
   ```  
```  

### 手順 3: ブックマーク保持オプションの設定
`PdfJoinOptions` はマージの動作を制御し、`UseBookmarks` フラグはエンジンに既存のブックマークを保持させます。  
```  
```csharp
   var pdfJoinOptions = new PdfJoinOptions { UseBookmarks = true };
   ```  
```  

### 手順 4: 追加 PDF の追加
各追加ファイルに対して `Join` を呼び出します。ライブラリは自動的にそれらのブックマークツリーをメインドキュメントのアウトライン下にマージします。  
```  
```csharp
   merger.Join(Path.Combine(documentDirectory, "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
   ```  
```  

### 手順 5: マージされた PDF の保存
出力パスと形式を指定します。ライブラリはすべてのブックマークエントリを保持した単一の PDF を書き出します。  
```  
```csharp
   string outputFile = Path.Combine(outputDirectory, "merged.pdf");
   merger.Save(outputFile);
   ```  
```  

## よくある問題と解決策
- **ブックマークが欠落している:** `PdfJoinOptions` で `UseBookmarks = true` が設定されているか確認してください。  
- **パスエラー:** `Path.Combine` を使用し、マージ前にファイルの存在を確認してください。  
- **大容量ファイルでメモリが急増:** PDF を順次処理し、各保存後に `Merger` オブジェクトを破棄してください。

## 実用的な活用例
1. **財務レポートの統合** – 四半期ごとのセクションをブックマークで即座にアクセス可能にします。  
2. **講義資料のパッケージ化** – 講義 PDF をマージし、学生向けに章ナビゲーションを保持します。  
3. **プロジェクト文書のバンドル** – 設計仕様書、テスト計画、リリースノートを単一の検索可能なファイルに結合します。

## パフォーマンス上の考慮点
- 20 個以上の PDF をマージする場合は、RAM 使用量を抑えるために 1 ファイルずつ処理します。  
- 最新の .NET ランタイム（例: .NET 6）を使用して、JIT コンパイルとガベージコレクションの効率を最適化します。  
- 500 MB を超える PDF については、`MergerSettings` でストリーミングモードを有効にし、ドキュメント全体をメモリに読み込まないようにします。

## よくある質問

**Q: GroupDocs.Merger とは何ですか？**  
A: GroupDocs.Merger は、PDF やその他のドキュメント形式をプログラムからマージ、分割、回転、その他操作できる .NET ライブラリです。

**Q: 同時に 2 つ以上の PDF をマージできますか？**  
A: はい – `Join` を繰り返し呼び出すか、ファイルパスのコレクションを渡して、任意の数の PDF を一度にマージできます。

**Q: 本番環境でのライセンスはどう扱えばよいですか？**  
A: GroupDocs の購入ページから永続ライセンスを取得してください。トライアルライセンスは評価目的のみで、30 日で期限切れになります。

**Q: マージした PDF にブックマークが表示されません—何が問題ですか？**  
A: `PdfJoinOptions.UseBookmarks` が `true` に設定されていること、そして各ソース PDF に実際にブックマークが含まれていることをマージ前に確認してください。

**Q: ライブラリは .NET Core と .NET Framework の両方に対応していますか？**  
A: 完全に対応しています – .NET Core 3.1 以降、.NET 5/6、そしてフル .NET Framework 4.6.1 以上をサポートします。

## リソース
- [ドキュメンテーション](https://docs.groupdocs.com/merger/net/)  
- [API リファレンス](https://reference.groupdocs.com/merger/net/)  
- [GroupDocs.Merger のダウンロード](https://releases.groupdocs.com/merger/net/)  
- [ライセンス購入](https://purchase.groupdocs.com/buy)  
- [無料トライアル版](https://releases.groupdocs.com/merger/net/)  
- [一時ライセンス](https://purchase.groupdocs.com/temporary-license/)  
- [サポートフォーラム](https://forum.groupdocs.com/c/merger/)  

---

**最終更新日:** 2026-08-20  
**テスト環境:** GroupDocs.Merger 23.11 for .NET  
**作者:** GroupDocs

## 関連チュートリアル

- [GroupDocs.Merger for .NET で特定の PDF ページをマージする方法：包括的ガイド](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)  
- [GroupDocs.Merger for .NET を使用してドキュメントを簡単に結合する方法：包括的ガイド](/merger/net/document-joining/groupdocs-merger-net-document-joining-guide/)  
- [GroupDocs.Merger for .NET で PDF に添付ファイルを追加する方法：ステップバイステップガイド](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)