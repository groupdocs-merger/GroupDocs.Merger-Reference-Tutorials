---
date: 2026-09-11
description: GroupDocs.Merger for .NET を使用して PDF を Word やその他の形式にインポートする方法を学びます。簡単な手順で
  embed PDF Word と add PDF attachments が可能です。
keywords:
- import pdf into word
- embed pdf word
- add pdf attachments
- embed ole excel
- convert diagram pdf
lastmod: 2026-09-11
og_description: GroupDocs.Merger for .NET を使用して PDF を Word やその他の形式にインポートする方法を学びます。embed
  PDF Word、add PDF attachments、OLE embedding が含まれます。
og_image_alt: Guide showing how to import PDF into Word using GroupDocs.Merger for
  .NET
og_title: GroupDocs.Merger for .NET を使用した PDF の Word へのインポート方法
schemas:
- author: GroupDocs
  dateModified: '2026-09-11'
  description: Learn how to import PDF into Word and other formats using GroupDocs.Merger
    for .NET, including embed PDF Word and add PDF attachments in a few easy steps.
  headline: How to import PDF into Word with GroupDocs.Merger for .NET
  type: TechArticle
- questions:
  - answer: Yes – use the `PageRange` option when calling `Insert` to specify which
      pages to embed.
    question: Can I import only selected pages of a PDF into Word?
  - answer: When embedding as an OLE object, hyperlinks remain functional inside the
      PDF viewer; when converting to native Word content, most hyperlinks are retained.
    question: Does the library preserve hyperlinks inside the PDF when imported?
  - answer: Absolutely. Loop through your PDF collection and call `Insert` for each
      file; the library merges them sequentially.
    question: Is it possible to batch‑import multiple PDFs into a single Word document?
  - answer: Vector graphics are preserved when the PDF is embedded as an OLE object;
      they render sharply at any zoom level.
    question: What if my PDF contains vector graphics?
  - answer: Yes – the .NET Standard build runs on Linux, macOS and Windows without
      any native dependencies.
    question: Does GroupDocs.Merger work on Linux containers?
  type: FAQPage
tags:
- import pdf
- GroupDocs.Merger
- .NET document processing
title: GroupDocs.Merger for .NET を使用した PDF の Word へのインポート方法
type: docs
url: /ja/net/document-import/
weight: 10
---

# PDF を Word にインポートする方法（GroupDocs.Merger for .NET）

このガイドでは、GroupDocs.Merger for .NET を使用して **import PDF into Word** および他のドキュメントタイプをインポートする方法をご紹介します。PDF を Word ファイルに埋め込む、既存のドキュメントに PDF を添付する、または図表、プレゼンテーション、スプレッドシート、ワードプロセッシングファイル間でコンテンツを移動する必要がある場合、このチュートリアルでは一般的なシナリオを順に解説し、重要性を説明し、迅速に作業を完了するための正確な手順を示します。

## クイック回答
- **PDF を Word 文書にインポートできますか？** Yes – GroupDocs.Merger lets you embed a PDF as an OLE object or as native content in a .docx file.  
- **別の PDF ライブラリが必要ですか？** いいえ、Merger SDK は追加の依存関係なしで PDF のインポートを処理します。  
- **サポートされている .NET バージョンはどれですか？** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7.  
- **本番環境でライセンスは必要ですか？** 本番環境では商用ライセンスが必要です。評価用に無料トライアルが利用可能です。  
- **インポートできる PDF の最大サイズはどれくらいですか？** ファイルあたり最大 500 MB まで、ドキュメント全体をメモリに読み込むことなくサポートされます。

## PDF を Word にインポートするとは？
PDF を Word にインポートするとは、PDF ファイルのコンテンツを Microsoft Word（.docx）ドキュメント内に配置することであり、埋め込みオブジェクトとして、または変換されたネイティブ要素として配置できます。レイアウト、画像、テキスト書式を保持しながら行われます。このプロセスはテキストの流れ、画像、表、ベクターグラフィックを保持でき、結果として得られる Word ファイルは元の PDF のレイアウトにできるだけ近い外観になります。

## このタスクに GroupDocs.Merger を使用する理由
GroupDocs.Merger は **30 以上の入力および出力フォーマット** をサポートし、**500 MB** までのドキュメントを RAM に完全にロードせずに処理できるため、サーバー側アプリケーションのメモリ負荷を軽減します。また、ライブラリは **組み込み OLE 埋め込み** を提供し、単一の API 呼び出しで PDF を Word、Excel、PowerPoint ファイルに直接添付できます。

## 前提条件
- .NET 開発環境（Visual Studio 2022 以降）。  
- GroupDocs.Merger for .NET NuGet パッケージがインストールされていること（`Install-Package GroupDocs.Merger`）。  
- 本番使用のための有効な GroupDocs.Merger ライセンス（テスト用に一時ライセンスが利用可能）。

## PDF を Word にインポートする手順

### PDF ファイルを Word 文書に埋め込むには？
`Merger` は GroupDocs.Merger SDK のコアクラスで、ドキュメント操作メソッドを提供します。  
`Insert` はソースドキュメントまたはオブジェクトを指定した位置にターゲットドキュメントに挿入します。  

`Merger` でソース PDF を読み込み、`Insert` を呼び出してターゲットの `.docx` に配置します。この操作は 2 行のコードで実行でき、OLE パッケージングを自動的に処理するため、PDF は Word 内でインタラクティブなオブジェクトとして表示されます。

### 既存の Word ファイルに PDF 添付ファイルを追加するには？
`AddAttachment` は外部ファイルをコンテナドキュメントに添付し、後で取得できるようパッケージ内に保存します。  

`Merger` インスタンスを作成し、Word 文書を開いて `AddAttachment` メソッドで PDF を添付します。添付ファイルは Word パッケージ内に保存され、文書の「Insert > Object」ダイアログから直接開くことができます。

### Excel スプレッドシートに OLE オブジェクト（PDF など）を埋め込むには？
`InsertOleObject` は PDF などの OLE オブジェクトをスプレッドシートのセルに埋め込み、Excel からインタラクティブに開くことができます。  

Excel ブックで `InsertOleObject` メソッドを使用します。このメソッドは PDF ファイルパスとセル位置を受け取り、PDF を OLE オブジェクトとして挿入し、ダブルクリックで開くことができます。

## よくある問題と解決策
- **PDF がアイコンとしてのみ表示される:** 対象の Word ファイルが `.docx` 拡張子で保存されていることを確認してください。古い `.doc` ファイルは埋め込み OLE オブジェクトをサポートしていません。  
- **大きな PDF のインポートが遅くなる:** インポート前に `MergerSettings.EnableMemoryOptimization = true` を呼び出して、メモリ使用量を低く保ちます。  
- **埋め込み PDF がクリックできない:** PDF ファイルがパスワードで保護されていないことを確認してください。Merger はパスワードを提供しない限り、暗号化された PDF を埋め込むことができません。

## よくある質問

**Q: PDF の選択したページだけを Word にインポートできますか？**  
A: はい – `Insert` 呼び出し時に `PageRange` オプションを使用して、埋め込むページを指定します。

**Q: ライブラリはインポート時に PDF 内のハイパーリンクを保持しますか？**  
A: OLE オブジェクトとして埋め込む場合、ハイパーリンクは PDF ビューア内で機能し続けます。ネイティブな Word コンテンツに変換する場合、ほとんどのハイパーリンクが保持されます。

**Q: �数の PDF を一つの Word 文書にバッチインポートすることは可能ですか？**  
A: もちろん可能です。PDF コレクションをループし、各ファイルに対して `Insert` を呼び出します。ライブラリはそれらを順次マージします。

**Q: PDF にベクターグラフィックが含まれている場合はどうなりますか？**  
A: PDF を OLE オブジェクトとして埋め込むと、ベクターグラフィックは保持され、任意のズームレベルでも鮮明に表示されます。

**Q: GroupDocs.Merger は Linux コンテナ上で動作しますか？**  
A: はい – .NET Standard ビルドは Linux、macOS、Windows 上でネイティブ依存関係なしで動作します。

## 利用可能なチュートリアル

### [GroupDocs.Merger for .NET を使用した PDF への添付ファイル追加：ステップバイステップガイド](./add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)
Learn how to add attachments to PDFs with GroupDocs.Merger for .NET. This step‑by‑step guide covers setup, implementation, and practical applications.

### [GroupDocs.Merger for .NET を使用した PowerPoint への PDF OLE 埋め込み：ステップバイステップガイド](./embed-pdf-ole-powerpoint-groupdocs-merger-net/)
Learn how to seamlessly embed a PDF file as an OLE object into your PowerPoint presentation with GroupDocs.Merger for .NET. Follow this comprehensive guide.

### [GroupDocs.Merger for .NET を使用した Word への PDF 埋め込み：ステップバイステップガイド](./embed-pdf-word-groupdocs-merger-dotnet/)
Learn how to seamlessly embed a PDF into a Microsoft Word document using GroupDocs.Merger for .NET. Enhance your documents with dynamic content efficiently.

### [GroupDocs.Merger for .NET を使用した Excel スプレッドシートへの OLE オブジェクト埋め込み方法](./embed-ole-objects-groupdocs-merger-net/)
Learn how to seamlessly embed OLE objects like PDFs into Excel spreadsheets using GroupDocs.Merger for .NET, enhancing data presentation and functionality.

## 追加リソース

- [GroupDocs.Merger for .net ドキュメント](https://docs.groupdocs.com/merger/net/)
- [GroupDocs.Merger for .net API リファレンス](https://reference.groupdocs.com/merger/net/)
- [GroupDocs.Merger for .net のダウンロード](https://releases.groupdocs.com/merger/net/)
- [GroupDocs.Merger フォーラム](https://forum.groupdocs.com/c/merger)
- [無料サポート](https://forum.groupdocs.com/)
- [一時ライセンス](https://purchase.groupdocs.com/temporary-license/)

---

**最終更新日:** 2026-09-11  
**テスト環境:** GroupDocs.Merger 23.12 for .NET  
**作者:** GroupDocs

## 関連チュートリアル

- [GroupDocs.Merger for .NET を使用した Word への PDF 埋め込み：ステップバイステップガイド](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [GroupDocs.Merger for .NET を使用した PDF への添付ファイル追加：ステップバイステップガイド](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)
- [GroupDocs.Merger を使用した .NET での URL からの PDF 読み込み：包括的ガイド](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)