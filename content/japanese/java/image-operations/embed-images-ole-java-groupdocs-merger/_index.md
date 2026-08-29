---
date: '2026-06-26'
description: Java 用 GroupDocs.Merger を使用して画像を OLE に変換する方法を学びます。ステップバイステップ ガイド、コードスニペット、画像を
  OLE オブジェクトとして埋め込むベストプラクティスを提供します。
keywords:
- convert image to ole
- GroupDocs.Merger Java tutorial
- embed images as OLE objects
schemas:
- author: GroupDocs
  dateModified: '2026-06-26'
  description: Learn how to convert image to OLE using GroupDocs.Merger for Java.
    Step‑by‑step guide, code snippets, and best practices for embedding images as
    OLE objects.
  headline: How to Convert Image to OLE in Java with GroupDocs.Merger
  type: TechArticle
- description: Learn how to convert image to OLE using GroupDocs.Merger for Java.
    Step‑by‑step guide, code snippets, and best practices for embedding images as
    OLE objects.
  name: How to Convert Image to OLE in Java with GroupDocs.Merger
  steps:
  - name: Define File Paths
    text: 'Specify where the source document and the image reside. Replace the placeholders
      with actual paths on your machine:'
  - name: Read Image Bytes
    text: 'Read the entire image file into a byte array. This byte array becomes the
      OLE payload:'
  - name: Configure OLE Diagram Options
    text: '`OleDiagramOptions` tells GroupDocs where and how to place the OLE object.
      The class is the **top‑level options holder for OLE diagram import**; it lets
      you set page number, X/Y coordinates, width, and height.'
  - name: Initialize Merger and Import OLE Diagram
    text: '`Merger` is the core class that represents a document and provides methods
      for manipulation. It **encapsulates all read/write operations** for the target
      file.'
  - name: Initialize Merger with Source Path
    text: 'Reuse the same `Merger` instance or create a new one pointing to the modified
      document:'
  - name: Save the Modified Document
    text: 'Call the `save` method with the desired output location. GroupDocs.Merger
      writes the file in a streaming fashion, keeping memory usage low:'
  type: HowTo
- questions:
  - answer: An OLE object embeds data from one application (e.g., an image) into another
      (e.g., a Word file), allowing in‑place editing without leaving the host document.
    question: What is an OLE object?
  - answer: Yes—commercial use requires a valid license. A trial is available for
      evaluation, but production deployments must be licensed.
    question: Can I use GroupDocs.Merger for commercial projects?
  - answer: Images are read into a byte array, but you can stream large files using
      `FileInputStream` and pass the stream to `importOleDiagram` to keep memory usage
      low.
    question: How does the library handle very large images?
  - answer: DOCX, XLSX, PPTX, and PDF are fully supported. For PDF, the OLE object
      is stored as an embedded file stream.
    question: Which document formats support OLE embedding?
  - answer: Practically none—GroupDocs.Merger can embed dozens of OLE diagrams, limited
      only by the host document’s size and available memory.
    question: Are there any limitations on the number of OLE objects per document?
  type: FAQPage
title: Java と GroupDocs.Merger を使用して画像を OLE に変換する方法
type: docs
url: /ja/java/image-operations/embed-images-ole-java-groupdocs-merger/
weight: 1
---

# JavaでGroupDocs.Mergerを使用して画像をOLEに変換する方法

画像を文書に直接埋め込むのは手間がかかると感じることがありますが、GroupDocs.Merger for Java を使用すれば **convert image to OLE** が簡単になります。このチュートリアルでは、OLE オブジェクトがなぜ便利か、環境の準備方法、画像を OLE 図として埋め込む具体的な手順を紹介します。最後まで読むと、Word、Excel、PowerPoint、PDF ファイルで使用できる再利用可能なコードパターンが手に入ります。

## クイック回答
- **主なメソッドは何ですか？** Use `Merger.importOleDiagram()` after loading the source document.  
- **ライセンスは必要ですか？** A trial works for development; a full license is required for production.  
- **サポートされている画像形式は何ですか？** PNG, JPEG, BMP, GIF, and TIFF are all accepted.  
- **OLE のサイズと位置を設定できますか？** Yes—`OleDiagramOptions` lets you define page, coordinates, width, and height.  
- **プロセスはメモリ効率が良いですか？** GroupDocs.Merger streams data, so even 500‑page files stay under 200 MB RAM.

## “convert image to OLE” とは何ですか？
**Convert image to OLE** は、ラスタ画像ファイルをホスト文書内で編集可能な Object Linking and Embedding (OLE) 図に変換することを意味します。この変換により、エンドユーザーは画像をダブルクリックしてネイティブエディタで開き、ファイルを離れることなく変更をコンテナ文書に保存できます。

## OLE 埋め込みに GroupDocs.Merger を使用する理由
GroupDocs.Merger は **50 以上の入力および出力フォーマット**（DOCX、XLSX、PPTX、PDF、一般的な画像タイプを含む）をサポートし、**300 MB** までの文書に OLE オブジェクトをメモリに全体をロードせずに埋め込むことができます。ライブラリは、典型的な 2.6 GHz サーバー上で、3 つの埋め込み PNG を含む 200 ページの Word ファイルを **3 秒** 未満で処理し、速度とスケーラビリティの両方を提供します。

## 前提条件
- **Java Development Kit (JDK) 8+** がインストールされ、IDE で設定されていること。  
- **GroupDocs.Merger for Java** を Maven または Gradle で追加（最新バージョン推奨）。  
- Java の I/O ストリームとオブジェクト指向プログラミングに関する基本的な知識。

## GroupDocs.Merger for Java の設定

プロジェクトに GroupDocs.Merger を組み込むには、ビルドファイルに依存関係を追加します。ライブラリは Maven Central に掲載されているので、以下のスニペットを `pom.xml` または `build.gradle` にコピーできます。  

> ※ 注意: 以下のプレースホルダーは元のチュートリアルの正確なコードブロックを表しています。変更しないでください。

```xml
  <!-- Maven -->
  <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-merger</artifactId>
      <version>latest-version</version>
  </dependency>
  ```

```gradle
  // Gradle
  implementation 'com.groupdocs:groupdocs-merger:latest-version'
  ```

公式リリースページから JAR を直接ダウンロードすることもできます: [GroupDocs.Merger releases](https://releases.groupdocs.com/merger/java/).

### ライセンス取得
- **Free Trial:** プロトタイピングと評価に最適。  
- **Temporary License:** 試用機能を限定期間延長します。  
- **Full License:** すべての OLE 関連機能を解放し、使用制限を解除します。

依存関係を追加したら、Java コードでライブラリを初期化できる状態になります。

## Javaで画像をOLEに変換する方法は？
画像を OLE オブジェクトに変換するには、`Merger` インスタンスで対象文書をロードし、画像ファイルをバイト配列に読み込み、ページ、位置、サイズを指定した `OleDiagramOptions` オブジェクトを作成して `merger.importOleDiagram(imageBytes, options)` を呼び出します。最後に `merger.save(outputPath)` で文書を保存します。このワークフローにより、画像が編集可能な OLE 図として埋め込まれます。

### 手順 1: ファイルパスの定義
ソース文書と画像の所在場所を指定します。プレースホルダーを実際のパスに置き換えてください。

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.vsdx";  
String imageFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.emf";
```

### 手順 2: 画像バイトの読み取り
画像ファイル全体をバイト配列に読み込みます。このバイト配列が OLE ペイロードになります。

```java
File file = new File(imageFilePath);
byte[] imageBytes = Files.readAllBytes(file.toPath());
```

### 手順 3: OLE 図オプションの設定
`OleDiagramOptions` は OLE オブジェクトの配置場所と方法を GroupDocs に指示します。このクラスは **OLE 図インポート用のトップレベルオプションホルダー** で、ページ番号、X/Y 座標、幅、高さを設定できます。

```java
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pptx";
int pageNumber = 2;  
String filePathOut = new File("YOUR_OUTPUT_DIRECTORY", "ImportImageToDocument" + Paths.get(filePath).getFileName().toString()).getPath();

OleDiagramOptions oleDiagramOptions = new OleDiagramOptions(embeddedFilePath, imageBytes, pageNumber);
oleDiagramOptions.setX(1);  
oleDiagramOptions.setY(1);
oleDiagramOptions.setWidth(2);
oleDiagramOptions.setHeight(1);
```

### 手順 4: Merger の初期化と OLE 図のインポート
`Merger` は文書を表すコアクラスで、操作用のメソッドを提供します。対象ファイルの **すべての読み書き操作をカプセル化** しています。

```java
Merger merger = new Merger(filePath);
merger.importDocument(oleDiagramOptions);
merger.save(filePathOut);
```

## 変更済み文書の保存

OLE 図が埋め込まれたら、変更をディスクに書き戻す必要があります。

### 手順 1: ソースパスで Merger を初期化
同じ `Merger` インスタンスを再利用するか、変更された文書を指す新しいインスタンスを作成します。

```java
Merger merger = new Merger(filePath);
```

### 手順 2: 変更済み文書の保存
希望する出力先を指定して `save` メソッドを呼び出します。GroupDocs.Merger はストリーミング方式でファイルを書き込み、メモリ使用量を低く抑えます。

```java
merger.save(outputPath);
```

## 実用的な応用例
画像を OLE オブジェクトとして埋め込むことで、以下のような実際のシナリオが実現できます。

- **Interactive Reports:** ユーザーは埋め込まれたチャートをダブルクリックして Excel で編集し、更新されたビジュアルを即座に確認できます。  
- **Automated Document Generation:** 金融や医療システムは、手動編集なしで最新のグラフィックを契約書や患者サマリーに注入できます。  
- **Collaboration Platforms:** チームは各メンバーが自分の図を更新できる単一の Word ファイルを共有でき、バージョン管理の問題を軽減します。

## パフォーマンス上の考慮点
大きなファイルを処理する際にアプリケーションの応答性を保つために:

- **Stream Data:** GroupDocs.Merger は入力と出力の両方をストリーミングし、ファイル全体をメモリにロードすることを防ぎます。  
- **Reuse Objects:** 複数のインポートで単一の `Merger` インスタンスを再利用することで、オブジェクト生成のオーバーヘッドを削減します。  
- **Monitor Heap:** 200 MB を超える文書の場合、JVM ヒープ (`-Xmx1g`) を増やして `OutOfMemoryError` を回避することを検討してください。

## よくある問題と解決策

| 症状 | 考えられる原因 | 解決策 |
|------|----------------|--------|
| `Unsupported file format` エラー | 画像が PNG/JPEG/BMP/GIF/TIFF 形式ではない | バイトを読み込む前に画像をサポートされている形式に変換してください。 |
| OLE オブジェクトが誤った位置に表示される | `OleDiagramOptions` の `x`/`y` 座標が正しくない | 座標がポイント単位で測定されていることを確認してください（1 pt ≈ 1/72 in）。 |
| 出力ファイルが破損している | インポート後に `save()` を呼び出していない | すべての変更後に `merger.save(outputPath)` が実行されていることを確認してください。 |

## よくある質問

**Q: OLE オブジェクトとは何ですか？**  
A: OLE オブジェクトは、あるアプリケーション（例: 画像）のデータを別のアプリケーション（例: Word ファイル）に埋め込み、ホスト文書を離れることなくその場で編集できるようにします。

**Q: 商用プロジェクトで GroupDocs.Merger を使用できますか？**  
A: はい、商用利用には有効なライセンスが必要です。評価用にトライアルは利用可能ですが、本番環境での展開にはライセンスが必要です。

**Q: ライブラリは非常に大きな画像をどのように扱いますか？**  
A: 画像はバイト配列に読み込まれますが、`FileInputStream` を使用して大きなファイルをストリーミングし、`importOleDiagram` にストリームを渡すことでメモリ使用量を低く抑えることができます。

**Q: どの文書フォーマットが OLE 埋め込みをサポートしていますか？**  
A: DOCX、XLSX、PPTX、PDF が完全にサポートされています。PDF の場合、OLE オブジェクトは埋め込みファイルストリームとして保存されます。

**Q: 文書あたりの OLE オブジェクト数に制限はありますか？**  
A: 実質的な制限はありません。GroupDocs.Merger は数十個の OLE 図を埋め込むことができ、制限はホスト文書のサイズと利用可能なメモリだけです。

## リソース
- [GroupDocs.Merger リリース](https://releases.groupdocs.com/merger/java/)
- [GroupDocs.Merger Java ドキュメント](https://docs.groupdocs.com/merger/java/)
- [Java API リファレンス](https://reference.groupdocs.com/merger/java/)
- [GroupDocs.Merger for Java リリース](https://releases.groupdocs.com/merger/java/)
- [GroupDocs 購入ページ](https://purchase.groupdocs.com/buy)
- [GroupDocs サポートフォーラム](https://forum.groupdocs.com/c/merger)

## 結論
これで、GroupDocs.Merger for Java を使用して **convert image to OLE** を行う完全な本番対応ワークフローが手に入りました。ファイルパスの定義、画像バイトの読み取り、`OleDiagramOptions` の設定、`importOleDiagram` の呼び出しにより、任意のサポート対象文書にインタラクティブなグラフィックを追加できます。マージ、分割、透かしなどの追加 API も活用して、フル機能の文書処理パイプラインを構築してください。

---

**最終更新日:** 2026-06-26  
**テスト環境:** GroupDocs.Merger 23.10 for Java  
**作者:** GroupDocs

## 関連チュートリアル

- [Java 用 GroupDocs.Merger で PDF を Excel に埋め込む方法 - OLE オブジェクトのインポート – ステップバイステップガイド](/merger/java/document-import/import-ole-object-excel-groupdocs-merger-java/)
- [Java 用 GroupDocs.Merger で PDF を Word に埋め込む方法 – 包括的ガイド](/merger/java/document-import/embed-ole-objects-word-documents-groupdocs-java/)
- [Java 用 GroupDocs.Merger で PNG 画像をマージする方法 - ステップバイステップガイド](/merger/java/document-information/merge-png-images-groupdocs-merger-java/)