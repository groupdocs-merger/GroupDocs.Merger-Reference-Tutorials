---
additionalTitle: GroupDocs API References
date: 2026-10-11
description: 高速で cross‑platform なドキュメントマージ、分割、PDF、Office ファイル、画像などの処理を実現する GroupDocs.Merger
  document merging API をご紹介します。
is_root: true
keywords:
- groupdocs.merger document merging api
- document merging and splitting
- cross-platform document processing
lastmod: 2026-10-11
linktitle: GroupDocs.Merger チュートリアル
og_description: GroupDocs.Merger document merging API は、50 以上のフォーマットにわたるドキュメントの merge、split、reorder、secure
  を可能にします。.NET と Java 向けの fast、cross‑platform 統合方法をご紹介します。
og_image_alt: Guide to using GroupDocs.Merger for merging and splitting documents
og_title: GroupDocs.Merger document merging API – 完全ガイド
schemas:
- author: GroupDocs
  dateModified: '2026-10-11'
  description: Explore the GroupDocs.Merger document merging API for fast, cross‑platform
    document merging, splitting, and processing of PDFs, Office files, images and
    more.
  headline: GroupDocs.Merger document merging API – complete guide to merging & splitting
  type: TechArticle
- questions:
  - answer: Yes, with a valid GroupDocs license. A free trial is available for evaluation.
    question: Can I use the API in a commercial product?
  - answer: Absolutely. You can open, modify, and re‑secure encrypted PDFs using the
      same API calls.
    question: Does the API support password‑protected PDFs?
  - answer: .NET Standard 2.0, .NET Framework 2.0+, .NET Core 2.0+, Mono 1.2+; Java
      7, 8, and 10+ are fully supported.
    question: Which .NET and Java versions are compatible?
  - answer: It streams data and uses memory‑efficient algorithms, allowing you to
      process multi‑gigabyte documents without exhausting system resources.
    question: How does the API handle very large files?
  - answer: While the core merging API focuses on structural operations, you can combine
      it with GroupDocs.Parser for advanced text extraction and OCR needs.
    question: Is there built‑in support for OCR or text extraction?
  type: FAQPage
tags:
- document merging
- groupdocs.merger
- .net document processing
- java document processing
title: GroupDocs.Merger document merging API – マージと分割の完全ガイド
type: docs
url: /ja/
weight: 11
---

# GroupDocs.Merger ドキュメント結合 API – 結合と分割の完全ガイド

**GroupDocs.Merger ドキュメント結合 API** は、.NET または Java アプリケーションから直接、さまざまなドキュメントタイプを高速かつクロスプラットフォームで結合、分割、操作できる方法を提供します。複数の PDF を単一のレポートに結合したり、大きな契約書を個別のページに分割したり、プレゼンテーションのスライド順序を入れ替えたりする必要がある場合でも、この API は数行のコードで対応できます。

## クイック回答
- **API の機能は何ですか？** 50 以上のフォーマットにわたってドキュメントを結合、分割、順序変更、保護します。  
- **サポートされているプラットフォームは？** .NET（Standard、Framework、Core、Mono）および Java（J2SE 7‑10）。  
- **外部ソフトウェアは必要ですか？** いいえ—Microsoft Office や Adobe の依存関係はありません。  
- **ドキュメントを保護できますか？** はい、パスワードや権限の追加、削除、更新が可能です。  
- **ファイルサイズに制限はありますか？** この API は大容量ファイルやバッチ処理に最適化されています。  

## GroupDocs.Merger ドキュメント結合 API とは？

ファイルをロードし、適切な結合または分割メソッドを呼び出す—これが GroupDocs.Merger ドキュメント結合 API の基本的なワークフローです。PDF、Office ドキュメント、画像、アーカイブなどを扱うための単一で一貫したインターフェイスを提供し、レイアウト、メタデータ、セキュリティ設定を保持します。

GroupDocs.Merger ドキュメント結合 API は、開発者向けのライブラリで、複数のドキュメントフォーマットの取り扱いの複雑さを抽象化します。プログラムからファイルを結合したり、ページや範囲で分割したり、高度なページ操作を適用したりでき、元のレイアウトやメタデータを保持します。

## なぜ GroupDocs.Merger ドキュメント結合 API を選ぶのか？

クロスプラットフォームの一貫性、幅広いフォーマットサポート、外部依存なし、高性能、組み込みのセキュリティをすべてひとつにまとめたパッケージが手に入ります。API はデータをストリーミングするため、マルチギガバイトのファイルでも低メモリフットプリントで処理でき、サーバー側のバッチジョブに最適です。

## 複数プラットフォームでのドキュメント管理方法を変革する

GroupDocs.Merger は、ドキュメント操作のための強力なクロスプラットフォームソリューションを提供し、開発者がアプリケーション内でファイルを扱う作業を効率化します。包括的な API により、複数のドキュメントを1つに結合したり、ドキュメントを小さなコンポーネントに分割したり、ページ順序を変更したり、セキュリティオプションを適用したり、その他多数の操作を最小限のコードで最大の効率で実行できます。

.NET または Java 環境で開発している場合でも、GroupDocs.Merger は 50 以上の一般的なファイル形式（PDF、Office ドキュメント、画像など）とシームレスに連携し、一貫した高性能なドキュメント処理機能を提供します。

## 主な機能と特長
- **包括的なドキュメント結合** – 複数のソースから全体のドキュメントまたは特定のページを組み合わせて、1つの統合ファイルにします。  
- **クロスフォーマットサポート** – 異なるファイル形式を統合ドキュメントに結合します（例：DOC、XLSX、画像を単一の PDF に）。  
- **スマートなドキュメント分割** – ページ番号、範囲でドキュメントを分割したり、特定のページを別ファイルとして抽出したりします。  
- **高度なページ操作** – ページの移動、削除、回転、入れ替え、抽出を正確に制御できます。  
- **セキュリティ管理** – ドキュメントのパスワードや権限を追加、削除、更新できます。  
- **OLE オブジェクトサポート** – Word、Excel、PowerPoint、Visio ファイル内にドキュメントを OLE オブジェクトとして挿入できます。  
- **外部依存なし** – Microsoft Office や Adobe ソフトウェアを必要とせずにドキュメントを処理できます。  
- **高性能** – 大容量ドキュメントやバッチ操作の処理に最適化されています。  

## サポートされているファイル形式
GroupDocs.Merger は、複数のカテゴリにわたる 50 以上のファイル形式に対応しています：

- **ドキュメント**: PDF, DOC, DOCX, RTF, ODT, XPS, EPUB, HTML  
- **スプレッドシート**: XLS, XLSX, XLSM, XLSB, ODS, CSV, TSV  
- **プレゼンテーション**: PPT, PPTX, PPS, PPSX, ODP  
- **画像**: JPG, PNG, BMP, GIF, TIFF, SVG  
- **ダイアグラム**: VSDX, VSDM, VSSX, VSTX, VDX, VSX, VTX  
- **アーカイブ**: ZIP, TAR, 7Z  
- **その他多数**  

## [GroupDocs.Merger for .NET チュートリアル](./net)

強力なドキュメント処理機能を .NET アプリケーションに統合する方法を紹介します。包括的な .NET チュートリアルでは、基本操作から高度な実装シナリオまで、GroupDocs.Merger API のすべての側面を案内します。

GroupDocs.Merger for .NET を使用すると、.NET Standard 2.0、.NET Framework 2.0 以降、.NET Core 2.0 以降、Mono Framework 1.2 以降など、さまざまな .NET フレームワークで動作する堅牢なドキュメント管理ソリューションを作成できます。

### 必須 .NET チュートリアル

- [アーカイブ結合と圧縮](./net/merge-compress-files/) - アーカイブ形式（7z、TAR、ZIP）を効率的に結合および圧縮する方法を学びます  
- [画像結合](./net/image-merging/) - 各種画像形式（BMP、GIF、PNG、SVG、TIFF）を結合するテクニックを習得します  
- [ドキュメント結合](./net/document-merging/) - DOC、DOCX、PDF などのドキュメント形式をシームレスに結合します  
- [スプレッドシート結合](./net/spreadsheet-merging/) - データ、数式、書式を保持しながら Excel ファイルを結合します  
- [Visio 結合](./net/visio-merging/) - Visio の図や描画を正確に結合します  
- [プレゼンテーション結合](./net/presentation-merging/) - スライドとアニメーションを保持しながら PowerPoint プレゼンテーションを結合します  

### 高度な .NET 操作

- [ドキュメント読み込み](./net/document-loading/) - 様々なソースからドキュメントを読み込む手法を探ります  
- [ドキュメント情報](./net/document-information/) - ドキュメントのメタデータとプロパティを抽出・分析します  
- [ドキュメント結合](./net/document-joining/) - 高度なドキュメント結合オプションとカスタマイズを学びます  
- [フォーマット別結合](./net/format-specific-merging/) - 特定のファイル形式向けに最適化された結合手法を紹介します  
- [高度な結合オプション](./net/advanced-joining-options/) - 複雑なドキュメント結合シナリオを習得します  
- [ドキュメントセキュリティ](./net/document-security/) - パスワード管理による堅牢なドキュメント保護を実装します  
- [ページ操作](./net/page-operations/) - 正確なコントロールでドキュメントページを操作します  
- [ドキュメント抽出](./net/document-extraction/) - 大きなドキュメントから特定のコンテンツを抽出します  
- [ドキュメントインポート](./net/document-import/) - 外部コンテンツをドキュメントにインポートします  
- [画像操作](./net/image-operations/) - 画像ファイルを効果的に処理・操作します  
- [ドキュメント分割](./net/document-splitting/) - 様々な分割戦略でドキュメントを分割します（ドキュメント分割）  
- [テキスト操作](./net/text-operations/) - テキストベースのドキュメントを効率的に扱います  
- [ライセンス設定](./net/licensing/) - プロジェクトで GroupDocs.Merger を適切に設定します  

## [GroupDocs.Merger for Java チュートリアル](./java)

強力なドキュメント処理機能で Java アプリケーションを変革します。Java チュートリアルでは、Windows、Linux、macOS など主要プラットフォームで動作する完全なサンプルを交えて、Java 環境で GroupDocs.Merger を実装するための詳細なガイダンスを提供します。

GroupDocs.Merger for Java は J2SE 7.0（1.7）、J2SE 8.0（1.8）、Java 10 をサポートしており、事実上すべての Java ベースの開発プロジェクトと互換性があります。

### 必須 Java チュートリアル

- [ドキュメント読み込み](./java/document-loading/) - ファイル、ストリーム、URL からドキュメントを読み込むテクニックを習得します  
- [ドキュメント情報](./java/document-information/) - 有用なドキュメントメタデータとプロパティを抽出します  
- [ドキュメント結合](./java/document-joining/) - 複数ファイルを単一ドキュメントに正確に結合します  
- [フォーマット別結合](./java/format-specific-merging/) - 異なるファイル形式向けに最適化されたアプローチを学びます  
- [高度な結合オプション](./java/advanced-joining-options/) - 複雑な結合シナリオとカスタマイズを探ります  
- [ドキュメントセキュリティ](./java/document-security/) - 堅牢なドキュメント保護と権限管理を実装します  
- [ページ操作](./java/page-operations/) - ドキュメント内の個別ページを操作します  
- [ドキュメント抽出](./java/document-extraction/) - ドキュメントから特定のコンテンツを抽出します  
- [ドキュメントインポート](./java/document-import/) - 外部コンテンツをドキュメントにインポートします  
- [画像操作](./java/image-operations/) - 画像ファイルと変換を扱います  
- [ドキュメント分割](./java/document-splitting/) - 様々な分割戦略でドキュメントを分割します（ドキュメント分割）  
- [テキスト操作](./java/text-operations/) - テキストベースのドキュメントを効果的に処理します  
- [ライセンス設定](./java/licensing/) - Java 環境で GroupDocs.Merger を設定します  

## 一般的なユースケースとメリット
- - **自動レポート生成:** データ駆動型 PDF と Excel シートを結合し、配布用の単一レポートを作成します。  
- - **法務ドキュメント管理:** 大規模な契約書を個別のセクションに分割し、レビューや署名を容易にします。  
- - **コンテンツ移行:** 複数のフォーマットからレガシードキュメントを変換・結合し、標準化された PDF アーカイブにします。  
- - **安全なドキュメント配信:** 機密ファイルをクライアントに送信する前にパスワードと権限を設定します。  

## よくある質問

**Q: 商用製品で API を使用できますか？**  
A: はい、有効な GroupDocs ライセンスがあれば使用可能です。評価用の無料トライアルも提供されています。

**Q: API はパスワード保護された PDF をサポートしていますか？**  
A: もちろんです。同じ API 呼び出しで暗号化された PDF を開き、変更し、再度保護できます。

**Q: 対応している .NET と Java のバージョンは？**  
A: .NET Standard 2.0、.NET Framework 2.0 以降、.NET Core 2.0 以降、Mono 1.2 以降；Java 7、8、10 以降が完全にサポートされています。

**Q: 非常に大きなファイルはどのように処理されますか？**  
A: データをストリーミングし、メモリ効率の高いアルゴリズムを使用するため、システムリソースを使い果たすことなくマルチギガバイトのドキュメントを処理できます。

**Q: OCR やテキスト抽出の組み込みサポートはありますか？**  
A: コアの結合 API は構造操作に焦点を当てていますが、GroupDocs.Parser と組み合わせることで高度なテキスト抽出や OCR に対応できます。

**Q: すぐに始めるにはどうすればよいですか？**  
A: .NET 用に NuGet パッケージ（`GroupDocs.Merger`）をインストールするか、Java 用に Maven 依存関係を追加し、まずは「ドキュメント読み込み」チュートリアルに従って最初のファイルをロードしてください。

**Q: 異なるファイルタイプを 1 つの PDF に結合できますか？**  
A: はい、API は PDF、Word、Excel、画像、その他多数のフォーマットを単一の PDF 出力に結合できます。

**最終更新日:** 2026-10-11  
**テスト環境:** GroupDocs.Merger 23.12（最新安定版）  
**作者:** GroupDocs