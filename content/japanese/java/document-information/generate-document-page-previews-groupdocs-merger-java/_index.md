---
date: '2026-01-24'
description: GroupDocs.Merger for Java を使用してページプレビューを生成し、ドキュメントのサムネイル作成のためにページを画像に変換する高速な方法で、ドキュメントのプレビュー方法を学びましょう。
keywords:
- GroupDocs.Merger for Java
- document page previews
- Java document management
title: GroupDocs.Merger for Java を使用したドキュメントのプレビュー方法
type: docs
url: /ja/java/document-information/generate-document-page-previews-groupdocs-merger-java/
weight: 1
---

# GroupDocs.Merger for Java を使用したドキュメントのプレビュー方法

ドキュメントページのプレビューを作成することは、**how to preview documents** を迅速に行う強力な方法であり、ユーザーにファイル全体を開かずに視覚的なスナップショットを提供します。このチュートリアルでは、GroupDocs.Merger for Java を使用してプレビューを生成する方法を学びます。このライブラリは、**convert pages to images** を簡単に行い、アプリケーションで **document thumbnail generation** をサポートします。

## クイック回答
- **What does “preview documents” mean?** 各ページの軽量な画像表現を生成することです。  
- **Which format is used for previews?** デフォルトは JPEG ですが、他の形式もサポートされています。  
- **Do I need a license?** 開発には無料トライアルが利用でき、製品版には有料ライセンスが必要です。  
- **Can I customize the output path?** はい、カスタム `PageStreamFactory` を実装することで可能です。  
- **What Java version is required?** JDK 8 以降です。

## “how to preview documents” とは何ですか？
ドキュメントのプレビューとは、各ページの視覚的サムネイル（主に JPEG や PNG）を作成し、ユーザーがコンテンツを素早くざっと見ることができるようにすることです。この手法は、ドプリケーションにおけるユーザーエクスペリエンスを向上させerger for Java を使用するのか？
- **Fast conversion** UI で全文書を開かずにページを画像に変換します。  
- **Built‑in support** 多くの形式（PDF、DOCX、XLSX +** がマシン（ for Java の設定
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

**Direct Download:**  
あるいは、最新バージョンを [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/) からダウンロードしてください。

### ライセンス取得
- **Free Trial:** 機能を試すために無料トライアルをダウンロードしてください。  
- **Temporary License:** 開発中の拡張アクセスのために一時ライセンスを取得してください。  
- **Purchase:** 本番環境でのフル使用には、[GroupDocs](https://purchase.groupdocs.com/buy) からライセンスを購入してください。

ライブラリを追加したら、プレビューしたいドキュメントのパスで初期化します。

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

## ドキュメントをプレビューする方法：ステップバイステップガイド

### 手順 1: Merger を初期化し、PageStreamFactory を定義する
`PageStreamFactory` は、各プレビュー画像の書き込み先をライブラリに指示します。

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

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
先ほど設定したオプションを使用して `generatePreview` メソッドを呼び出します。

```java
merger.generatePreview(previewOption);
```

### ページを画像に変換 – カスタム PageStreamFactory
ファイル名や保存場所をより細かく制御したい場合は、独自のファクトリを実装します。

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
これらのユーティリティメソッドはコードを整理し、例外処理をきれいに行います。

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

## ドキュメントサムネイル生成 – 実用例
プレビュー生成は特に以下の用途で有用です：

1. **Document Management Systems** – ユーザーはファイルを開かずにざっと閲覧できます。  
2. **Content Review Platforms** – アップロード承認前に迅速な視覚的チェックが可能です。  
3. **Educational Tools** – 学生は講義スライドや教科書のページをざっと見ることができます。  

## パフォーマンス上の考慮点
- **Release streams promptly** メモリ解放のためにストリームを速やかに解放します。  
- **Avoid loading whole documents** メモリに全文書を読み込むのは避け、ライブラリにページングを任せます。  
- **Use appropriate image quality** 速度と画質のバランスを取るために適切な画像品質設定を使用します。  

## よくある質問

**Q: What is GroupDocs.Merger for Java used for?**  
A: ドキュメントのマージ、分割、効率的な管理に使用され、プレビュー生成も含まれます。

**Q: How do I handle exceptions during stream operations?**  
A: ヘルパーメソッドに示すように、ストリームの作成とクローズを try‑catch ブロックでラップします。

**Q: Can I generate previews in formats other than JPEG?**  
A: はい、`PreviewMode` 列挙型を PNG、BMP などに変更すれば、必要に応じた形式で生成できます。

**Q: What are common issues with document preview generation?**  
A: 主な問題は、ファイルパスが間違っていることやストリームを閉じ忘れることです。これらはメモリリークにつながります。

**Q: How can I integrate GroupDocs.Merger with other systems?**  
A: API を使用してデータベース、Web サービス、または他の Java アプリケーションと接続し、シームレスなワークフロー自動化を実現できます。

## 追加リソース
- [ドキュメント](https://docs.groupdocs.com/merger/java/)
- [API リファレンス](https://reference.groupdocs.com/merger/java/)
- [ダウンロード](https://releases.groupdocs.com/merger/java/)
- [購入](https://purchase.groupdocs.com/buy)
- [無料トライアル](https://releases.groupdocs.com/merger/java/)
- [一時ライセンス](https://purchase.groupdocs.com/temporary-license/)
- [サポート](https://forum.groupdocs.com/c/merger/)

---

**最終更新日:** 2026-01-24  
**テスト環境:** GroupDocs.Merger 最新バージョン (2025‑latest)  
**作者:** GroupDocs  

---