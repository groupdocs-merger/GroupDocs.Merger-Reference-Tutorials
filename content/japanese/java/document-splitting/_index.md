---
date: 2026-05-22
description: GroupDocs.Merger for Java を使用して単一ページ PDF ファイルの作成方法と PDF の分割方法を学びます。split
  pdf java のステップバイステップガイドやその他の情報が含まれています。
keywords:
- create single page pdf
- docx to pdf java
- split pdf java
- pdf split by range
- split pdf odd even
schemas:
- author: GroupDocs
  dateModified: '2026-05-22'
  description: Learn how to create single page PDF files and split PDFs using GroupDocs.Merger
    for Java. Includes step-by-step guides for split pdf java and more.
  headline: Create Single Page PDF with GroupDocs.Merger Java
  type: TechArticle
- description: Learn how to create single page PDF files and split PDFs using GroupDocs.Merger
    for Java. Includes step-by-step guides for split pdf java and more.
  name: Create Single Page PDF with GroupDocs.Merger Java
  steps:
  - name: Initialize the Merger
    text: The `Merger` class is GroupDocs.Merger's core component that loads a source
      document and provides split operations. Create an instance by passing the file
      path or an input stream.
  - name: Define the split criteria
    text: Choose the exact page number or range you need. For a single‑page extraction,
      you’ll specify a range like `1‑1`. When you need to **split pdf by range**,
      you can pass multiple ranges such as `1‑5, 6‑10`.
  - name: Execute the split
    text: Call the appropriate `split` method. For example, `merger.split(new int[]{1})`
      extracts the first page, while `merger.splitByRange(new int[][]{{1,5},{6,10}})`
      handles multiple ranges in one call.
  - name: Save the result
    text: Write each output to a file path or return it as a `java.io.InputStream`.
      This makes it easy to integrate with web APIs or store the result in cloud storage.
      > **Pro tip:** When working with large PDFs, call `merger.setOptimizeResources(true)`
      before splitting to reduce memory consumption.
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then perform any split
      operation as usual.
    question: Can I split a password‑protected PDF?
  - answer: Provide a page list containing only odd numbers (e.g., 1,3,5…) to the
      `split` method.
    question: How do I split only the odd pages of a PDF?
  - answer: Absolutely. After loading the DOCX, call `saveAsPdf` on each split segment.
    question: Is it possible to split a DOCX directly into PDFs?
  - answer: PDF, DOCX, PPTX, TXT, HTML, and many image formats (PNG, JPEG, etc.).
    question: What formats does GroupDocs.Merger support for splitting?
  - answer: No. A single GroupDocs.Merger license covers all supported formats.
    question: Do I need a separate license for each file type?
  type: FAQPage
title: GroupDocs.Merger Java を使用して単一ページ PDF を作成
type: docs
url: /ja/java/document-splitting/
weight: 12
---

# GroupDocs.Merger Javaで単一ページPDFを作成する

大きなドキュメントから **単一ページPDF** を作成したり、PDF をより扱いやすいサイズに分割したりしたい場合は、ここが最適です。このガイドでは、最も一般的な分割シナリオ（複数ページファイル、ページ範囲、奇数/偶数ページ、DOCX の分割、さらにはテキストベースの分割）を、Java 用の強力な GroupDocs.Merger ライブラリを使用して解説します。チュートリアルの最後までに、これらの手法を自分のアプリケーションに統合し、ドキュメント処理のパフォーマンスを向上させ、コードベースをクリーンで保守しやすくする方法が正確に分かります。

## クイック回答
- **“create single page PDF” は何を意味しますか？** それは、ソースドキュメントから 1 ページを抽出し、独立した PDF ファイルとして保存することを意味します。  
- **どのライブラリがこの作業を処理しますか？** GroupDocs.Merger for Java は、すべての分割操作に対してフルエントな API を提供します。  
- **ライセンスは必要ですか？** 開発には一時ライセンスで動作しますが、本番環境ではフルライセンスが必要です。  
- **PDF の奇数ページと偶数ページを分割できますか？** はい。GroupDocs.Merger を使用すると、奇数・偶数のページ番号でフィルタリングできます。  
- **DOCX の分割はサポートされていますか？** もちろんです。DOCX ファイルをページ単位またはカスタム範囲で分割できます。  

## “単一ページPDFを作成する” とは？
単一ページの PDF を作成するとは、複数ページのソースドキュメント（PDF、DOCX、PPTX など）から 1 ページだけを抽出し、独自の PDF ファイルとして保存することです。特定のページだけが必要な請求書、証明書、プレビュー画像の生成に便利です。

## なぜ GroupDocs.Merger for Java を使用するのか？
GroupDocs.Merger for Java は、さまざまなドキュメント形式を扱える単一で一貫した API を提供し、高性能かつ低メモリ使用を実現します。複雑なファイル処理を抽象化することで、ビジネスロジックに集中でき、低レベルの処理詳細に煩わされることがありません。

- **統一された API** – PDF、DOCX、PPTX、画像、その他多数の形式に対応します。  
- **高性能** – 大容量ファイルやバッチ処理に最適化されており、ファイル全体をメモリにロードせずに最大 2 GB のドキュメントを処理できます。  
- **細かな制御** – ページ範囲、奇数/偶数ページ、またはカスタム区切りで分割できます。  
- **ストリーム対応** – 出力をファイルに保存したり、Web サービス向けにストリームとして返したりできます。  

## 前提条件
- Java 8 以上。  
- プロジェクトに GroupDocs.Merger for Java を追加（Maven/Gradle）。  
- 有効な（一時またはフル）GroupDocs ライセンスファイル。  

## 単一ページPDFの作成方法
GroupDocs.Merger を使用して単一ページ PDF を作成するには、ソースファイルを読み込み、正確なページまたは範囲を指定し、分割操作を呼び出し、最後に結果を保存します。このワークフローにより、元のドキュメントは変更されず、抽出されたページが独立した PDF ファイルとして保存されます。

`Merger` クラスは、ソースドキュメントを読み込み、分割機能を提供するコアコンポーネントです。

### 手順 1: Merger の初期化
`Merger` クラスは GroupDocs.Merger のコアコンポーネントで、ソースドキュメントを読み込み、分割操作を提供します。ファイルパスまたは入力ストリームを渡してインスタンスを作成します。

### 手順 2: 分割基準の定義
必要な正確なページ番号または範囲を選択します。単一ページの抽出の場合は、`1‑1` のような範囲を指定します。**範囲で PDF を分割** したい場合は、`1‑5, 6‑10` のように複数の範囲を渡すことができます。

### 手順 3: 分割の実行
適切な `split` メソッドを呼び出します。例えば、`merger.split(new int[]{1})` は最初のページを抽出し、`merger.splitByRange(new int[][]{{1,5},{6,10}})` は一度の呼び出しで複数の範囲を処理します。

### 手順 4: 結果の保存
各出力をファイルパスに書き込むか、`java.io.InputStream` として返します。これにより、Web API への統合やクラウドストレージへの保存が容易になります。

> **プロのコツ:** 大きな PDF を扱う場合、分割前に `merger.setOptimizeResources(true)` を呼び出してメモリ使用量を削減してください。

## PDF Java ファイルを複数ページに分割する方法
`Merger` クラスは PDF ファイルの読み込みと操作のための主要 API を提供します。PDF をページごとの個別ファイルに分割するには、Merger インスタンスでドキュメントを読み込み、パラメータなしで split メソッドを呼び出すだけです。ライブラリは各ページごとに新しい PDF を自動的に作成し、元のコンテンツとメタデータを保持します。請求書やレポートのバッチ処理に最適です。

## PDF の奇数・偶数ページを分割する方法
`Merger` クラスはドキュメントの分割操作を実行するコアコンポーネントです。PDF から奇数ページまたは偶数ページだけが必要な場合、分割関数に目的のページ番号リストを渡します。Merger は指定されたページだけを含む新しいドキュメントを生成し、奇数ページまたは偶数ページのコンテンツを別々のファイルとしてすばやく作成できます。

## DOCX ファイルを分割する方法 (how to split docx)
`Merger` クラスは DOCX ファイルでも動作します。`splitByPage` を使用してページごとに 1 つの DOCX（または PDF）を生成するか、PDF 出力が必要な場合は `saveAsPdf` と組み合わせます。これにより、**docx to pdf java** 変換ワークフローを単一ステップで実行できます。

## ドキュメントを複数ページのファイルに分割する方法
`Merger` クラスは分割操作のページ付けとファイル作成を処理します。大きなドキュメントを固定サイズのチャンクに分割したい場合は、出力ファイルあたりのページ数を指定します。Merger はソースを順に処理し、指定されたページ数を含む新しい PDF を作成します。これにより、アーカイブ、配布、広範なドキュメントの並列処理が簡素化されます。

## 利用可能なチュートリアル

### [GroupDocs.Merger for Java を使用してドキュメントを複数ページファイルに分割する方法](./split-documents-multi-page-files-java-groupdocs-merger/)
GroupDocs.Merger for Java を使用して、大きなドキュメントを効率的に小さな複数ページファイルに分割する方法を学びます。簡単にドキュメント管理を最適化できます。

### [GroupDocs.Merger for Java を使用してテキストファイルを行間隔で分割する方法 | ドキュメント分割ガイド](./split-text-file-line-intervals-groupdocs-merger-java/)
GroupDocs.Merger for Java を使用して、行間隔でテキストファイルを扱いやすいセクションに分割する方法を学びます。効率的なドキュメント処理のための包括的なガイドです。

### [GroupDocs.Merger for Java でページ範囲によるドキュメント分割をマスターする](./split-documents-page-range-groupdocs-merger-java/)
GroupDocs.Merger for Java を使用して、特定のページ範囲でドキュメントを分割する方法を学びます。ドキュメント管理を効率化し、奇数/偶数ページなどのフィルタを適用できます。

### [GroupDocs.Merger&#58; 包括的ガイドでドキュメント分割をマスター](./master-document-splitting-groupdocs-merger-java/)
GroupDocs.Merger for Java を使用して、ドキュメントを単一ページに効率的に分割する方法を学びます。このガイドでは、セットアップ、実装、実用的な応用例を取り上げます。

### [GroupDocs.Merger&#58; DOCX ページをファイルとストリームに分割する Java ドキュメント分割のマスター](./master-java-document-splitting-groupdocs-merger/)
GroupDocs.Merger for Java を使用して、DOCX ドキュメントを個別のページまたはストリームに効率的に分割する方法を学びます。このガイドでは、セットアップ、実装、実用的な応用例を取り上げます。

## 追加リソース
- [GroupDocs.Merger for Java ドキュメント](https://docs.groupdocs.com/merger/java/)
- [GroupDocs.Merger for Java API リファレンス](https://reference.groupdocs.com/merger/java/)
- [GroupDocs.Merger for Java のダウンロード](https://releases.groupdocs.com/merger/java/)
- [GroupDocs.Merger フォーラム](https://forum.groupdocs.com/c/merger)
- [無料サポート](https://forum.groupdocs.com/)
- [一時ライセンス](https://purchase.groupdocs.com/temporary-license/)

## よくある問題と解決策

| 問題 | 解決策 |
|-------|----------|
| **大容量 PDF でのメモリオーバーロード** | リソース最適化を有効にする: `merger.setOptimizeResources(true);` |
| **分割後のページ番号が正しくない** | ページインデックスは 0 ではなく 1 から始まることを覚えておいてください。 |
| **ライセンスが見つかりません** | `GroupDocs.Merger.lic` ファイルへのパスを確認し、クラスパスに含まれていることを確認してください。 |
| **DOCX の分割で空ページが生成される** | ソース DOCX に適切な改ページがあるか確認してください。ない場合は、代替として `splitByParagraph` を使用します。 |

## よくある質問

**Q: パスワード保護された PDF を分割できますか？**  
A: はい。パスワードパラメータでドキュメントを読み込み、通常通り分割操作を実行できます。

**Q: PDF の奇数ページだけを分割するには？**  
A: 奇数番号だけ（例: 1,3,5…）のページリストを `split` メソッドに渡します。

**Q: DOCX を直接 PDF に分割できますか？**  
A: もちろんです。DOCX を読み込んだ後、各分割セグメントで `saveAsPdf` を呼び出します。

**Q: GroupDocs.Merger がサポートする分割可能なフォーマットは何ですか？**  
A: PDF、DOCX、PPTX、TXT、HTML、そして多数の画像フォーマット（PNG、JPEG など）。

**Q: ファイルタイプごとに別々のライセンスが必要ですか？**  
A: いいえ。単一の GroupDocs.Merger ライセンスでサポートされているすべての形式をカバーします。

---

**最終更新日:** 2026-05-22  
**テスト環境:** GroupDocs.Merger 23.11 for Java  
**作者:** GroupDocs

## 関連チュートリアル

- [split pdf java: GroupDocs.Merger を使用したドキュメント分割](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [GroupDocs.Merger for Java でページ範囲によるドキュメント分割をマスター](/merger/java/document-splitting/split-documents-page-range-groupdocs-merger-java/)
- [GroupDocs.Merger for Java を使用した PDF の効率的な結合: ステップバイステップガイド](/merger/java/format-specific-merging/merge-pdfs-groupdocs-merger-java-tutorial/)