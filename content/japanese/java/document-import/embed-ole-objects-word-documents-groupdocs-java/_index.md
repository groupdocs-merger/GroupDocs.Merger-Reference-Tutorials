---
date: '2026-02-19'
description: GroupDocs.Merger for Java を使用して、PDF を Word 文書に埋め込む方法と、PDF を Word ファイルに追加する方法を学びましょう。シームレスな
  OLE 埋め込みのためのステップバイステップチュートリアルです。
keywords:
- embed OLE objects in Word documents
- GroupDocs Merger for Java tutorial
- import OLE objects using Java
title: GroupDocs.Merger for Java を使用して PDF を Word に埋め込む方法 – 包括的ガイド
type: docs
url: /ja/java/document-import/embed-ole-objects-word-documents-groupdocs-java/
weight: 1
---

# GroupDocs.Merger for Java を使用した PDF の Word への埋め込み方法

PDF を Word 文書に直接埋め込むことで、読者がファイル間を切り替える必要がなくなり、コラボレーションが大幅に向上します。このガイドでは、GroupDocs.Merger for Java を使用して **how to embed pdf in word**（PDF を Word に埋め込む方法）を学び、**add pdf to word**（PDF を Word に追加）ワークフローに関する実用的なヒントをご紹介します。ライブラリのセットアップから OLE オブジェクトのサイズや配置のカスタマイズまで、ドキュメント作成を自動化できるようにステップバイステップで解説します。

## Quick Answers
- **必要なライブラリは何ですか？** GroupDocs.Merger for Java（latest version）  
- **任意のファイルタイプを埋め込めますか？** はい – PDFs, images, spreadsheets, etc., as OLE objects  
- **ライセンスは必要ですか？** A free trial works for development; a commercial license is required for production  
- **どの Java IDE が最適ですか？** IntelliJ IDEA, Eclipse, or any IDE that supports Maven/Gradle  
- **実装にどれくらい時間がかかりますか？** Roughly 10‑15 minutes for a basic embed  

## What is embed pdf in word?
PDF を埋め込むと、Word ファイル内に OLE（Object Linking and Embedding）オブジェクトが作成されます。PDF は完全に機能したままで、ユーザーはアイコンをダブルクリックして PDF ビューアで開くことができ、Word 文書は単体で完結した状態を保ちます。

## Why add pdf to word using GroupDocs.Merger?
- **シングルソースドキュメント:** Keep contracts, manuals, or reports together without external links.  
- **アクセシビリティの向上:** Readers can view the PDF without leaving the Word environment.  
- **自動化に適した:** Perfect for generating batch reports or legal packages programmatically.  
- **スケーラビリティ:** You can **embed multiple pdfs word** documents by re‑using the same workflow for each file.  

## Prerequisites
- **ライブラリと依存関係:** Include the GroupDocs.Merger library via Maven or Gradle.  
- **開発環境:** IntelliJ IDEA, Eclipse, or any Java IDE.  
- **基本知識:** Familiarity with Java and document manipulation concepts.

## Setting Up GroupDocs.Merger for Java
OLE オブジェクトを埋め込むには、まずプロジェクトにライブラリを追加します。

### Maven
`pom.xml` ファイルに次の依存関係を追加します:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle
`build.gradle` ファイルに次を含めます:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### Direct Download
あるいは、[GroupDocs.Merger for Java releases page](https://releases.groupdocs.com/merger/java/) から最新バージョンをダウンロードしてください。

**ライセンス取得:** 無料トライアルで開始するか、機能評価用に一時ライセンスを取得できます。詳細は [Purchase GroupDocs](https://purchase.groupdocs.com/buy) をご覧ください。

## Basic Initialization
OLE オブジェクトを操作できるように、必要なクラスをインポートします:
```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OleWordProcessingOptions;
```

## Step‑by‑Step Guide to embed pdf in word

### Step 1: Define file paths and target page
ソースとなる Word 文書、埋め込む PDF、OLE オブジェクトを配置する場所を設定します。
```java
String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.docx"; // Source Word document path
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf"; // File to be embedded as an OLE object
String outputFilePath = new File("YOUR_OUTPUT_DIRECTORY",
    "ImportDocumentToWordProcessing-" + Paths.get(sourceFilePath).getFileName().toString()).getPath();
int pageNumber = 2; // Page number where the OLE object will be inserted
```
- **`sourceFilePath`** – 既存の Word ファイルへのパス。  
- **`embeddedFilePath`** – **add pdf to word**（Word に追加したい PDF）。  
- **`outputFilePath`** – 新しい文書を保存する場所。  
- **`pageNumber`** – OLE オブジェクトを配置するページ番号。

### Step 2: Configure OleWordProcessingOptions
埋め込んだ PDF の外観を、サイズを設定してカスタマイズします。
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Set width of the embedded object (in points)
oleWordsOptions.setHeight(300); // Set height of the embedded object (in points)
```
- **`setWidth()` / `setHeight()`** – Word 文書内で PDF アイコンが表示される大きさを制御します。

### Step 3: Initialize Merger and import the OLE object
`Merger` インスタンスをソース文書に対して作成し、OLE オブジェクトをインポートして結果を保存します。
```java
Merger merger = new Merger(sourceFilePath);
{
    merger.importDocument(oleWordsOptions); // Embed the OLE object into the Word document
    merger.save(outputFilePath); // Save changes to a new output file
}
```
- **`importDocument()`** – `OleWordProcessingOptions` を受け取り、PDF を OLE オブジェクトとして挿入します。  
- **`save()`** – 変更された文書を `outputFilePath` に書き出します。

### Step 4: (Optional) Re‑apply configuration for additional objects
さらに PDF を埋め込む必要がある場合は、**Step 1‑3** を新しいファイルパスとページ番号で繰り返します。同じ `OleWordProcessingOptions` クラスを使用して、各オブジェクトを個別に制御できます。

## Configuring OleWordProcessingOptions (Advanced)
配置をさらに調整したり、オブジェクトの位置揃えやキャプションの追加が可能です。以下のコードスニペットは、基本設定を再掲して分かりやすくしています:
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Width of the embedded object
oleWordsOptions.setHeight(300); // Height of the embedded object
```

## Practical Applications
実用的な活用例

1. **テクニカルマニュアル** – 詳細な回路図や参照 PDF をガイドに直接挿入します。  
2. **財務レポート** – 主レポートの流れを途切れさせずに、補足監査 PDF を追加します。  
3. **法的契約書** – 付録や展示資料を OLE オブジェクトとして添付し、レビュー時に簡単にアクセスできるようにします。  
4. **マーケティングパッケージ** – **insert pdf into word**（PDF を Word に挿入）パンフレットで製品仕様を手元に置きます。

## Performance Considerations
大きな文書や複数の OLE オブジェクトを扱う際は、以下のポイントに留意してください：

- **不要なコンテンツを削減** – embed only the pages you really need.  
- **メモリ管理** – use Java’s `-Xmx` flag to allocate sufficient heap space for big files.  
- **最新状態を保つ** – newer GroupDocs.Merger releases often include performance optimizations.

## Common Issues and Solutions
- **ファイルパスが正しくない:** Verify that both the Word and PDF paths are absolute or correctly relative to the project root.  
- **メモリ不足エラー:** Increase JVM heap size or process documents in smaller batches.  
- **PDF が破損:** Ensure the source PDF opens normally in a viewer before embedding.  
- **OLE アイコンが欠如:** Check that the Word template isn’t protected against OLE insertion.

## Frequently Asked Questions

**Q: OLE 埋め込みとは何ですか？**  
A: 埋め込みにより、PDF などのオブジェクトを Word 文書にリンクとして挿入でき、元の機能を保持したまま使用できます。

**Q: 1 つの文書に複数の OLE オブジェクトを埋め込めますか？**  
A: はい、`OleWordProcessingOptions` を個別に設定することで、ページやサイズをそれぞれ指定できます。

**Q: 埋め込むファイルのサイズに制限はありますか？**  
A: 制限は主に Word の制約に依存しますが、GroupDocs.Merger は大容量ファイルも効率的に処理します。

**Q: 埋め込みエラーを解決するには？**  
A: ファイルパスが正しいこと、JVM に十分なメモリがあることを確認してください。また、元の PDF が破損していないかチェックします。

**Q: 挿入後に埋め込んだオブジェクトを変更できますか？**  
A: Microsoft Word で文書を再度開き OLE オブジェクトを編集するか、更新したオプションで Merger コードを再実行できます。

## Additional Resources
- [GroupDocs.Merger ドキュメント](https://docs.groupdocs.com/merger/java/)
- [API リファレンス](https://reference.groupdocs.com/merger/java/)
- [最新バージョンのダウンロード](https://releases.groupdocs.com/merger/java/)
- [GroupDocs の購入](https://purchase.groupdocs.com/buy)
- [無料トライアル](https://releases.groupdocs.com/merger/java/)
- [一時ライセンス](https://purchase.groupdocs.com/temporary-license/)
- [サポートフォーラム](https://forum.groupdocs.com/c/merger/)

---

**Last Updated:** 2026-02-19  
**Tested With:** GroupDocs.Merger for Java latest version  
**Author:** GroupDocs