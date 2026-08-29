---
date: '2026-06-26'
description: GroupDocs.Merger for Java を使用して PDF ページを画像に変換し、ドキュメントをプレビューする方法を学びましょう
  – ページサムネイルを生成する高速で信頼性の高い方法です。
keywords:
- convert pdf pages to images
- document page previews
- GroupDocs.Merger Java
schemas:
- author: GroupDocs
  dateModified: '2026-06-26'
  description: Learn how to convert pdf pages to images and preview documents using
    GroupDocs.Merger for Java – the fast, reliable way to generate page thumbnails.
  headline: How to Convert PDF Pages to Images and Preview Documents with GroupDocs.Merger
    for Java
  type: TechArticle
- questions:
  - answer: It’s used for merging, splitting, and managing documents efficiently,
      including preview generation and format conversion.
    question: What is GroupDocs.Merger for Java used for?
  - answer: Wrap stream creation and closing in try‑catch blocks, as shown in the
      helper methods, to prevent memory leaks.
    question: How do I handle exceptions during stream operations?
  - answer: Yes, change the `PreviewMode` enum to PNG, BMP, or TIFF to suit your requirements.
    question: Can I generate previews in formats other than JPEG?
  - answer: Typical problems include incorrect file paths and forgetting to close
      streams, which can cause memory leaks.
    question: What are common issues with document preview generation?
  - answer: Use its API to connect with databases, web services, or other Java applications
      for seamless workflow automation.
    question: How can I integrate GroupDocs.Merger with other systems?
  type: FAQPage
title: GroupDocs.Merger for Java を使用して PDF ページを画像に変換し、ドキュメントをプレビューする方法
type: docs
url: /ja/java/document-information/generate-document-page-previews-groupdocs-merger-java/
weight: 1
---

# PDFページを画像に変換し、GroupDocs.Merger for Javaでドキュメントをプレビューする方法

現代のアプリケーションでは、ユーザーがファイル全体をダウンロードせずにドキュメントをざっと見ることができるよう、**pdfページを画像に変換**する必要があることがよくあります。このチュートリアルでは、GroupDocs.Merger for Java を使用して高品質なページプレビューを生成する方法を、セットアップからカスタムストレージの処理まで順を追って説明します。最後まで読むと、JDK 8+ 環境で動作するドキュメントサムネイル生成の再利用可能なソリューションが手に入ります。

## クイック回答
- **“preview documents”とは何ですか？** 各ページの軽量な画像表現を生成することです。  
- **プレビューに使用される形式は何ですか？** デフォルトは JPEG ですが、他の形式もサポートされています。  
- **ライセンスは必要ですか？** 開発には無料トライアルで動作しますが、本番環境では有料ライセンスが必要です。  
- **出力パスをカスタマイズできますか？** はい、カスタム `PageStreamFactory` を実装することで可能です。  
- **必要な Java バージョンは？** JDK 8 以降。

## 「ドキュメントをプレビューする方法」とは？
ドキュメントのプレビューとは、各ページのビジュアルサムネイル（通常は JPEG または PNG）を作成し、ユーザーがコンテンツを素早くざっと見ることができるようにすることです。この手法は、ファイルブラウザやコンテンツレビュー ポータル、そして多数のドキュメントを管理するあらゆるシステムにおいて UX を向上させ、ファイル全体を開かずに迅速な視覚的手がかりを提供します。

## なぜ GroupDocs.Merger for Java を使用するのか？
GroupDocs.Merger は、典型的な 2 GHz CPU 上で 1 ページあたり **0.5 秒未満**で PDF ページを画像に変換し、**50 以上の入力および出力形式**をサポートし、ファイル全体をメモリに読み込むことなくプレビューを直接ストレージへストリームできます。拡張可能な API により、画像品質、形式、保存先パスを完全に制御できます。

## 前提条件
- **GroupDocs.Merger for Java** ライブラリ（以下のインストール手順を参照）。  
- **JDK 8+** がマシンにインストールされていること。  
- IDE（IntelliJ IDEA、Eclipse、NetBeans）と、依存関係管理のための Maven または Gradle。

## GroupDocs.Merger for Java の設定
好みのビルドツールを使用してプロジェクトにライブラリを追加します。

**Maven:**  
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle:**  
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**直接ダウンロード:**  
または、最新バージョンを [GroupDocs.Merger for Java リリース](https://releases.groupdocs.com/merger/java/) からダウンロードしてください。

### ライセンス取得
- **無料トライアル:** 機能を試すために無料トライアルをダウンロードして開始します。  
- **一時ライセンス:** 開発中の拡張アクセスのために一時ライセンスを取得します。  
- **購入:** 本番環境でのフル使用には、[GroupDocs](https://purchase.groupdocs.com/buy) からライセンスを購入してください。

ライブラリを追加したら、プレビューしたいドキュメントへのパスで初期化します:

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

## ドキュメントをプレビューする方法: ステップバイステップガイド
ソースファイルを読み込み、`PageStreamFactory` を構成し、`generatePreview` を呼び出します。  
`generatePreview` は、提供されたオプションに従って各ドキュメントページを画像に変換するメソッドです。

### 手順 1: Merger を初期化し、PageStreamFactory を定義する
`Merger` は、ドキュメントのマージ、分割、プレビュー生成のメソッドを提供するコアクラスです。  
`PageStreamFactory` は、各プレビュー画像を書き込む場所をライブラリに指示するインターフェースです。

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

ここでは、各ページ画像を予測可能な命名規則で特定のフォルダーに書き込むカスタム実装を作成します。

```java
IPreviewOptions previewOption = new PreviewOptions(new PageStreamFactory() {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        return createStream(pageNumber);
    }
    
    @Override
    public void closePageStream(int pageNumber, OutputStream pageStream) {
        releasePageStream(pageNumber, pageStream);
    }
}, PreviewMode.JPEG);
```

### 手順 2: プレビューを生成する
`generatePreview` は、指定したオプションに基づいて変換プロセスを起動します。定義した `PageStreamFactory` に各ページ画像をストリームし、メモリ使用量を抑えます。

```java
merger.generatePreview(previewOption);
```

### ページを画像に変換 – カスタム PageStreamFactory
ファイル名や保存場所をより細かく制御したい場合は、独自のファクトリを実装してください。

```java
class CustomPageStreamFactory implements PageStreamFactory {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        String filePath = "YOUR_OUTPUT_DIRECTORY/image-" + pageNumber + ".jpg";
        return new FileOutputStream(filePath);
    }
    
    @Override
    public void closePageStream(int pageNumber, OutputStream pageStream) {
        try {
            if (pageStream != null) {
                pageStream.close();
            }
        } catch (Exception e) {
            throw new RuntimeException(e);
        }
    }
}
```

### ヘルパーメソッド – ストリーム管理
これらのユーティリティメソッドはコードを整理し、例外をきれいに処理します。

```java
private static String getImagePath(int pageNumber) {
    return "YOUR_OUTPUT_DIRECTORY/image-" + pageNumber + ".jpg";
}

private static OutputStream createStream(int pageNumber) {
    try {
        String imageFilePath = getImagePath(pageNumber);
        return new FileOutputStream(imageFilePath);
    } catch (FileNotFoundException e) {
        throw new RuntimeException(e);
    }
}

private static void releasePageStream(int pageNumber, OutputStream pageStream) {
    try {
        if (pageStream != null) {
            pageStream.close();
        }
    } catch (Exception e) {
        throw new RuntimeException(e);
    }
}
```

## ドキュメントサムネイル生成 – 実用的な応用
プレビュー生成は特に次のようなケースで有用です：

1. **Document Management Systems** – ユーザーはファイルを開かずにざっと見ることができます。  
2. **Content Review Platforms** – アップロード承認前に迅速なビジュアルチェックが可能です。  
3. **Educational Tools** – 学生は講義スライドや教科書のページをざっと見ることができます。  

## パフォーマンス上の考慮点
- **ストリームは速やかに解放**してメモリを確保します。  
- **ドキュメント全体をメモリに読み込むのは避ける**; ライブラリにページングを任せます。  
- **適切な画像品質設定**を使用して速度と視覚的忠実度のバランスを取ります。  

## よくある質問
**Q: GroupDocs.Merger for Java は何に使われますか？**  
A: マージ、分割、ドキュメントの効率的な管理に使用され、プレビュー生成や形式変換も含まれます。

**Q: ストリーム操作中の例外はどう処理すべきですか？**  
A: ヘルパーメソッドに示されているように、ストリームの作成とクローズを try‑catch ブロックで囲み、メモリリークを防止します。

**Q: JPEG 以外の形式でプレビューを生成できますか？**  
A: はい、要件に合わせて `PreviewMode` 列挙型を PNG、BMP、または TIFF に変更します。

**Q: ドキュメントプレビュー生成で一般的な問題は何ですか？**  
A: 主な問題は、ファイルパスが正しくないことやストリームを閉じ忘れることで、メモリリークが発生することです。

**Q: GroupDocs.Merger を他のシステムと統合するには？**  
A: API を使用してデータベース、ウェブサービス、または他の Java アプリケーションと接続し、シームレスなワークフロー自動化を実現します。

## リソース
- [GroupDocs.Merger for Java リリース](https://releases.groupdocs.com/merger/java/)  
- [ダウンロード](https://releases.groupdocs.com/merger/java/)  
- [ドキュメンテーション](https://docs.groupdocs.com/merger/java/)  
- [API リファレンス](https://reference.groupdocs.com/merger/java/)  
- [無料トライアル](https://releases.groupdocs.com/merger/java/)  
- [一時ライセンス](https://purchase.groupdocs.com/temporary-license/)  
- [購入](https://purchase.groupdocs.com/buy)  
- [GroupDocs](https://purchase.groupdocs.com/buy)  
- [サポート](https://forum.groupdocs.com/c/merger/)

**最終更新日:** 2026-06-26  
**テスト環境:** GroupDocs.Merger 最新バージョン (2025‑latest)  
**作者:** GroupDocs

## 関連チュートリアル
- [GroupDocs.Merger Java のドキュメントページ操作チュートリアル](/merger/java/page-operations/)  
- [GroupDocs.Merger for Java を使用して URL から PDF をロードする方法: 包括的ガイド](/merger/java/document-loading/load-pdf-url-groupdocs-merger-java/)  
- [GroupDocs.Merger Java で単一ページ PDF を作成する](/merger/java/document-splitting/)