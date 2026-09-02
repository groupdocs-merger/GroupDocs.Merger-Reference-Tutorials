---
date: '2026-07-15'
description: Java用GroupDocs Mergerを使用してページの向きを変更する方法を学びましょう。ドキュメントの特定のセクションを変更するためのステップバイステップガイドです。
keywords:
- change page orientation java
- change orientation specific pages
- groupdocs merger java
- document layout modification
lastmod: '2026-07-15'
og_description: JavaでGroupDocs.Mergerを使用してページの向きを変更する方法を学びます。このガイドでは、ステップバイステップのコード、パフォーマンスのヒント、実際のユースケースを紹介します。
og_image_alt: 'Guide: Change page orientation in Java using GroupDocs.Merger'
og_title: JavaでGroupDocs.Mergerを使用してページの向きを変更する
schemas:
- author: GroupDocs
  dateModified: '2026-07-15'
  description: Learn how to change page orientation with GroupDocs Merger for Java.
    Follow this step-by-step guide to modify specific sections of your documents.
  headline: Change Page Orientation in Java Using GroupDocs.Merger
  type: TechArticle
- description: Learn how to change page orientation with GroupDocs Merger for Java.
    Follow this step-by-step guide to modify specific sections of your documents.
  name: Change Page Orientation in Java Using GroupDocs.Merger
  steps:
  - name: Set Paths for Your Document
    text: Define absolute or relative paths for the source and destination files.
      Adjust these values to match your project’s folder layout.
  - name: Create OrientationOptions
    text: '`OrientationOptions` specifies which pages to rotate and the target orientation
      mode.'
  - name: Initialize Merger
    text: '`Merger` manages file I/O and ensures resources are released correctly.'
  - name: Apply Changes and Save
    text: '`changeOrientation` applies the orientation settings to the selected pages
      and updates the document.'
  type: HowTo
- questions:
  - answer: GroupDocs Merger for Java provides the `changeOrientation` API.
    question: What library handles page orientation?
  - answer: Yes – pass an array of page numbers to `OrientationOptions`.
    question: Can I target only a few pages?
  - answer: A valid GroupDocs Merger license is needed for unlimited use.
    question: Is a license required for production?
  - answer: JDK 8 or higher (up to JDK 21).
    question: What Java version is supported?
  - answer: The library processes pages stream‑wise, so even 500‑page PDFs use less
      than 200 MB RAM.
    question: Will memory usage stay low?
  type: FAQPage
tags:
- change page orientation
- GroupDocs.Merger
- Java document processing
title: JavaでGroupDocs.Mergerを使用してページの向きを変更する
type: docs
url: /ja/java/page-operations/change-page-orientation-groupdocs-java/
weight: 1
---

# JavaでGroupDocs.Mergerを使用してページの向きを変更する

## クイック回答
- **ページの向きを処理するライブラリは何ですか？** GroupDocs Merger for Javaは `changeOrientation` API を提供します。  
- **特定のページだけを対象にできますか？** はい – `OrientationOptions` にページ番号の配列を渡します。  
- **本番環境でライセンスは必要ですか？** 無制限に使用するには有効な GroupDocs Merger ライセンスが必要です。  
- **サポートされている Java バージョンは？** JDK 8 以上（JDK 21 まで）。  
- **メモリ使用量は低く抑えられますか？** ライブラリはページをストリーム処理するため、500 ページの PDF でも 200 MB 未満の RAM で処理できます。

## “change page orientation java” とは？
**“Change page orientation java”** は、Java コードを使用して選択したページを縦向きと横向きにプログラムで切り替えることを指します。  
GroupDocs Merger の `changeOrientation` メソッドは、単一の呼び出しでこれを実行し、他のすべてのコンテンツを保持します。

## なぜ GroupDocs Merger for Java を使用するのか？
GroupDocs Merger は **30 以上の入力および出力フォーマット**（PDF、DOCX、PPTX、画像など）をサポートし、**ファイル全体をメモリに読み込まずに** ドキュメントを操作できます。ベンチマークでは、標準的な 8 コア VM 上で 300 ページの PDF の向き変更が 3 秒未満で完了することが示されています。

## 前提条件
- **Java Development Kit (JDK)：** 8 以上。  
- **IDE：** IntelliJ IDEA、Eclipse、または任意の Java 対応エディタ。  
- **GroupDocs.Merger for Java：** Maven、Gradle、または直接 JAR ダウンロードでライブラリを追加します。  

### GroupDocs.Merger for Java の設定

#### インストール

**Maven**  
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle**  
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**直接ダウンロード**  
最新バージョンは [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/) からダウンロードしてください。

#### ライセンス取得
まずは無料トライアルで始めるか、一時ライセンスを取得して制限なく GroupDocs Merger を評価してください。長期的に使用する場合は、ライセンスの購入をご検討ください。

### 基本的な初期化と設定
`Merger` クラスはすべてのドキュメント操作のエントリーポイントです。依存関係を追加したら、必要な名前空間をインポートし、`Merger` インスタンスを作成します。

```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OrientationMode;
import com.groupdocs.merger.domain.options.OrientationOptions;
```

## Javaでページの向きを変更する方法は？
向きを変更するには、`Merger` でソースドキュメントを読み込み、対象ページと目的のモード（縦向きまたは横向き）を指定した `OrientationOptions` オブジェクトを作成し、`changeOrientation(options)` を呼び出し、最後に変更されたファイルを目的の場所に保存します。この手順により、PDF、DOCX、PPTX を全体を再構築せずに効率的に処理できます。

### 手順 1: ドキュメントのパスを設定する
ソースファイルと保存先ファイルの絶対パスまたは相対パスを定義します。これらの値をプロジェクトのフォルダー構成に合わせて調整してください。

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/ChangePageOrientation-" + 
    Paths.get(filePath).getFileName().toString();
```

### 手順 2: OrientationOptions を作成する
`OrientationOptions` は、回転させるページと対象の向きモードを指定します。  

```java
// Change page orientation for pages 3 and 4 to Landscape.
OrientationOptions orientationOptions = new OrientationOptions(OrientationMode.Landscape, 
    new int[] { 3, 4 });
```

### 手順 3: Merger を初期化する
`Merger` はファイル I/O を管理し、リソースが正しく解放されることを保証します。  

```java
Merger merger = new Merger(filePath);
```

### 手順 4: 変更を適用して保存する
`changeOrientation` は選択したページに向き設定を適用し、ドキュメントを更新します。  

```java
// Apply orientation changes as per the specified options.
merger.changeOrientation(orientationOptions);

// Save the updated document.
merger.save(filePathOut);
```

## よくある問題と解決策
- **File Not Found（ファイルが見つかりません）：** ファイルパスが正しいこと、アプリケーションに読み書き権限があることを確認してください。  
- **Dependency Conflicts（依存関係の競合）：** クラスパスに古いバージョンの GroupDocs ライブラリが残っていないことを確認してください。  
- **Memory Spikes on Large Files（大きなファイルでのメモリ急増）：** ドキュメントをチャンクで処理するか、200 MB を超える場合は JVM ヒープ（`-Xmx2g`）を増やしてください。

## 実用的な活用例
1. **教育資料：** 大規模なエンジニアリング図面を回転させ、テキスト部分は縦向きのままにします。  
2. **ビジネスレポート：** 広い財務表を横向きで表示し、レポート全体を変換せずに済ませます。  
3. **写真ポートフォリオ：** 複数ページの PDF 内で、単一の横向きページにフルブリード画像を掲載します。

## パフォーマンス上の考慮点
- **Resource Usage（リソース使用量）：** GroupDocs Merger はページをストリーム処理するため、1,000 ページのファイルでもメモリ使用量は低く抑えられます。  
- **Optimization Tips（最適化のヒント）：** `Merger` インスタンスは速やかに閉じ、バッチで多数のドキュメントを処理する際は単一インスタンスを再利用してください。  
- **Best Practices（ベストプラクティス）：** `MergerException` を捕捉して破損した入力を適切に処理し、デバッグのためにエラー詳細をログに記録します。

## 結論
これで、GroupDocs Merger を使用して **change page orientation java** を実行する完全な本番対応の方法が手に入りました。さまざまなドキュメントタイプで試し、向き変更を他のマージ/分割操作と組み合わせ、より大規模なドキュメント自動化パイプラインに統合してください。

## よくある質問

**Q:** GroupDocs Merger でドキュメント内のすべてのページの向きを変更できますか？  
**A:** はい – `new int[]{1,2,3,…}` のような範囲を渡すか、API バージョンがサポートしていれば `OrientationOptions.setAllPages(true)` を使用してください。

**Q:** GroupDocs Merger はすべてのドキュメント形式に対応していますか？  
**A:** はい – **30 以上のフォーマット**（PDF、DOCX、PPTX、HTML、一般的な画像タイプ）をサポートしています。

**Q:** GroupDocs Merger を使用する際の例外処理はどうすべきですか？  
**A:** `MergerException` 用の try‑catch ブロックで呼び出しをラップし、メッセージをログに記録し、必要に応じてフォールバック戦略で再試行してください。

**Q:** 大きな PDF のメモリへの影響は？  
**A:** ライブラリはデータをストリーム処理し、500 ページの PDF でも通常 200 MB 未満です。JVM ヒープを監視し、リソースは速やかに閉じてください。

**Q:** GroupDocs Merger for Java の高度な機能はどこで見つけられますか？  
**A:** [API Reference](https://reference.groupdocs.com/merger/java/) とドキュメントで、透かし、暗号化、ドキュメント分割などの機能を確認してください。

---

**最終更新日：** 2026-07-15  
**テスト環境：** GroupDocs.Merger 23.10 for Java  
**作者：** GroupDocs  

## リソース
- **Documentation:** [GroupDocs.Merger Documentation](https://docs.groupdocs.com/merger/java/)
- **API Reference:** [API Reference](https://reference.groupdocs.com/merger/java/)
- **Download:** [Latest Releases](https://releases.groupdocs.com/merger/java/)
- **Purchase:** [Buy GroupDocs.Merger](https://purchase.groupdocs.com/buy)
- **Free Trial:** [Get a Free Trial](https://releases.groupdocs.com/merger/java/)
- **Temporary License:** [Obtain a Temporary License](https://purchase.groupdocs.com/temporary-license/)
- **Support:** [GroupDocs Forum](https://forum.groupdocs.com/c/merger/)

## 関連チュートリアル

- [Document Page Operations Tutorials for GroupDocs.Merger Java](/merger/java/page-operations/)
- [Rotate PDF Pages in Java Using GroupDocs.Merger: A Step‑By‑Step Guide](/merger/java/page-operations/rotate-pdf-pages-java-groupdocs-merger/)
- [Load Local Document Java Using GroupDocs.Merger – Guide](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)