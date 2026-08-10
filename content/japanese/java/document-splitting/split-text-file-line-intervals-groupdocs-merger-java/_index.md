---
date: '2026-07-25'
description: GroupDocs.Merger for Java を使用して行単位でファイルを分割する方法を学びます – Java プロジェクトで効率的にドキュメントを分割するための
  step‑by‑step ガイドです。
keywords:
- split file by lines
- split large text file
- split file into parts
- split text file java
- java document splitting
lastmod: '2026-07-25'
og_description: GroupDocs.Merger for Java を使用して行単位でファイルを分割します。このガイドでは、大きなテキストファイルを迅速にパーツに分割する方法を、code
  examples と best‑practice tips を交えて紹介します。
og_image_alt: 'Developer guide: split file by lines in Java using GroupDocs.Merger'
og_title: GroupDocs.Merger for Java で行単位にファイルを分割 – Fast & Easy
schemas:
- author: GroupDocs
  dateModified: '2026-07-25'
  description: Learn how to split file by lines using GroupDocs.Merger for Java –
    a step‑by‑step guide for efficient document splitting in Java projects.
  headline: How to Split File by Lines with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to split file by lines using GroupDocs.Merger for Java –
    a step‑by‑step guide for efficient document splitting in Java projects.
  name: How to Split File by Lines with GroupDocs.Merger for Java
  steps:
  - name: Define Source and Output Paths
    text: First, tell the library where your original file lives and where the split
      fragments should be written.
  - name: Configure the Split Options
    text: 'Create a `TextSplitOptions` instance that describes the line intervals
      you want. The `new int[] { 3, 6 }` array tells the API to cut after line 3 and
      line 6, producing two parts: lines 1‑3 and lines 4‑6. **Definition:** `TextSplitOptions`
      is a configuration object that holds the line‑interval array '
  - name: Initialise the Merger and Execute the Split
    text: Finally, instantiate `Merger` with the source file and call `split()` with
      the options you just built. **Definition:** `Merger` is the core class in GroupDocs.Merger
      that orchestrates document manipulation operations such as splitting, merging,
      and extracting pages. When the `split()` call finishes,
  type: HowTo
- questions:
  - answer: Currently, GroupDocs.Merger for Java focuses on line intervals. However,
      you can preprocess your text to match the desired character count per line before
      using this feature.
    question: Can I split files based on character count instead of line numbers?
  - answer: There is no hard limit in the library; performance may degrade if you
      request thousands of tiny splits because each split incurs I/O overhead.
    question: Is there a limit to how many intervals I can specify for splitting?
  - answer: Wrap the splitting logic in a try‑catch block and log `MergerException`
      details. The API provides clear messages that pinpoint the failure point.
    question: How do I handle errors during file splitting?
  - answer: Yes, because CSV and TSV are plain‑text files, the same line‑interval
      logic applies. Treat them as `.txt` files when calling the API.
    question: Does the library support other text‑based formats such as CSV or TSV?
  - answer: Absolutely. Iterate over `Files.list(Paths.get("folder"))`, apply the
      same `TextSplitOptions` to each file, and collect the generated parts.
    question: Can I automate splitting for multiple files in a folder?
  type: FAQPage
tags:
- split file by lines
- GroupDocs.Merger
- Java document processing
- text file splitting
- java tutorial
title: GroupDocs.Merger for Java を使用した行単位でのファイル分割方法
type: docs
url: /ja/java/document-splitting/split-text-file-line-intervals-groupdocs-merger-java/
weight: 1
---

# GroupDocs.Merger for Java を使用した行単位でのファイル分割方法

If you need to **split file by lines**—for example, to break a massive log file into bite‑size chunks, feed batches of data into a pipeline, or turn a long report into separate chapter files—this tutorial shows you exactly how to do it with GroupDocs.Merger for Java. You’ll see why the library is a time‑saver, get a ready‑to‑run implementation, and learn practical tips that keep your application fast and reliable.

## クイック回答
- **“split file by lines” とは何ですか？** 元のドキュメントから指定された行番号の範囲を含む個別のテキストファイルを作成します。  
- **分割を処理するライブラリはどれですか？** GroupDocs.Merger for Java は、行間隔での分割用のシンプルな API を提供します。  
- **ライセンスは必要ですか？** テストには無料トライアルが利用でき、実稼働には永続ライセンスが必要です。  
- **文字数で分割できますか？** 直接はできません。分割前にファイルを再構成する前処理ステップを使用してください。  
- **サポートされている Java バージョンは何ですか？** Java 8 以降のランタイムであればすべて互換性があります。

## “split file by lines” とは何ですか？
**Split file by lines** は、単一のテキストドキュメントを複数のファイルに分割し、各ファイルが連続した特定の行範囲（例: 行 1‑3、4‑6 など）を含むことを意味します。このアプローチは、データを並列処理したり、メモリ負荷を減らしたり、長いファイルを簡単にナビゲートできるようにしたりするのに最適です。

## GroupDocs.Merger for Java を使用する理由
GroupDocs.Merger は低レベルのファイル I/O を抽象化し、ビジネスロジックに集中できるようにします。ドキュメント全体をメモリにロードせずに最大 2 GB のファイルを効率的に処理し、**70+** の入力および出力フォーマットをサポートし、Maven や Gradle ビルドとスムーズに統合できる流暢な API を提供します。このライブラリを使用すると、手作業の I/O ループと比較して開発時間を最大 **80 %** 短縮できます。

## 前提条件
- **Java Development Kit (JDK) 8 以上** – `java` と `javac` が PATH に含まれていることを確認してください。  
- **GroupDocs.Merger for Java** – Maven、Gradle、または直接ダウンロードでライブラリを追加します。  
- **Basic Java knowledge** – クラス、メソッド、例外処理に慣れている必要があります。

## GroupDocs.Merger for Java の設定
以下の方法のいずれかでプロジェクトにライブラリを追加します。

**Maven** – `pom.xml` にこの依存関係を貼り付けます:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle** – `build.gradle` に以下の行を追加します:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Direct Download** – 公式リリースページから JAR を取得することもできます: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### ライセンス取得
API を試すには無料トライアルから始めます。実稼働環境では、GroupDocs ポータルから一時ライセンスまたはフルライセンスを取得してください。

## 行単位でテキストファイルを分割する方法（Java 実装）
以下は簡潔なステップバイステップの解説です。各ステップは実際のコードが配置されるプレースホルダーの前に平易な言葉で説明されているので、何が起きているか正確に把握できます。

### 手順 1: ソースと出力パスの定義
まず、元のファイルの場所と分割されたフラグメントを書き込む場所をライブラリに指示します。
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.txt";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToLineRanges-" + Paths.get(filePath).getFileName().toString();
```

### 手順 2: 分割オプションの設定
必要な行間隔を記述した `TextSplitOptions` インスタンスを作成します。`new int[] { 3, 6 }` 配列は、API に対して行 3 と行 6 の後でカットするよう指示し、2 つのパート（行 1‑3 と行 4‑6）を生成します。  
**Definition:** `TextSplitOptions` は、行間隔配列とオプションの出力命名規則を保持する設定オブジェクトです。
```java
TextSplitOptions splitOptions = new TextSplitOptions(filePathOut, TextSplitMode.Interval, new int[] { 3, 6 });
```

### 手順 3: Merger の初期化と分割の実行
最後に、ソースファイルで `Merger` をインスタンス化し、先ほど作成したオプションで `split()` を呼び出します。  
**Definition:** `Merger` は、分割、結合、ページ抽出などのドキュメント操作を統括する GroupDocs.Merger のコアクラスです。
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

`split()` 呼び出しが完了すると、`YOUR_OUTPUT_DIRECTORY` に指定された行範囲を含む 2 つの新しいファイルが作成されます。

## 実用的な応用（なぜ重要か）
1. **Data Processing Pipelines** – 巨大なログファイルを小さなチャンクに分割して並列解析し、全体の処理時間を大幅に短縮します。  
2. **Document Management** – 単一のレポートを章単位のファイルに変換し、異なるチームへの配布を容易にします。  
3. **Content Segmentation** – 大規模な記事のセクションをターゲットプラットフォーム向けに準備し、SEO と可読性を向上させます。

## パフォーマンスのヒント
- **Stream‑line I/O** – 非常に大きなファイルを扱う場合は、メモリ使用量を抑えるために `Files.newBufferedReader` を使用してください。  
- **Close Resources** – GroupDocs.Merger がほとんどのクリーンアップを処理しますが、カスタムストリームは明示的に閉じてリークを防ぎます。  
- **Monitor Memory** – ギガバイト規模のファイルを分割するとメモリ使用量が多くなるため、必要に応じて十分なヒープ（`-Xmx2g` 以上）を割り当ててください。  
- **Batch Processing** – 多数のファイルを分割する場合、`Merger` インスタンスを再利用してオブジェクト生成のオーバーヘッドを削減します。

## よくある問題と解決策
| 問題 | 発生理由 | 対策 |
|-------|----------------|-----|
| `OutOfMemoryError` | 大きなソースファイルがヒープを超過しています。 | JVM ヒープを増やすか、より小さな間隔で分割してください。 |
| `FileNotFoundException` | パスが間違っているか、権限が不足しています。 | `filePath` と `filePathOut` が絶対パスで書き込み可能であることを確認してください。 |
| Empty output files | 間隔配列がドキュメント全体をカバーしていません。 | 最後の間隔が総行数以上で終わるようにしてください。 |

## よくある質問

**Q: 行番号ではなく文字数でファイルを分割できますか？**  
A: 現在、GroupDocs.Merger for Java は行間隔に焦点を当てています。ただし、この機能を使用する前に、目的の文字数に合わせてテキストを前処理し、行ごとの文字数を調整することは可能です。

**Q: 分割用に指定できる間隔の数に制限はありますか？**  
A: ライブラリに明確な上限はありませんが、数千もの小さな分割を要求すると、各分割が I/O オーバーヘッドを伴うため、パフォーマンスが低下する可能性があります。

**Q: ファイル分割中のエラーはどのように処理しますか？**  
A: 分割ロジックを try‑catch ブロックで囲み、`MergerException` の詳細をログに記録してください。API は失敗箇所を特定する明確なメッセージを提供します。

**Q: ライブラリは CSV や TSV などのテキストベースのフォーマットもサポートしていますか？**  
A: はい、CSV と TSV はプレーンテキストファイルなので、同じ行間隔ロジックが適用されます。API を呼び出す際は `.txt` ファイルとして扱ってください。

**Q: フォルダー内の複数ファイルの分割を自動化できますか？**  
A: もちろんです。`Files.list(Paths.get("folder"))` でフォルダー内のファイルを列挙し、各ファイルに同じ `TextSplitOptions` を適用して生成されたパーツを収集してください。

## 追加リソース
- [GroupDocs.Merger for Java リリース](https://releases.groupdocs.com/merger/java/)
- [GroupDocs.Merger for Java ドキュメント](https://docs.groupdocs.com/merger/java/)
- [GroupDocs API リファレンス](https://reference.groupdocs.com/merger/java/)
- [最新リリース](https://releases.groupdocs.com/merger/java/)
- [GroupDocs を購入](https://purchase.groupdocs.com/buy)
- [GroupDocs 無料トライアル](https://releases.groupdocs.com/merger/java/)
- [一時ライセンス取得](https://purchase.groupdocs.com/temporary-license/)
- [GroupDocs サポート](https://forum.groupdocs.com/c/merger)

---

**最終更新日:** 2026-07-25  
**テスト環境:** GroupDocs.Merger 23.12 for Java  
**作者:** GroupDocs

## 関連チュートリアル
- [GroupDocs.Merger for Java を使用してテキストファイルを行単位のドキュメントに分割する方法](/merger/java/text-operations/split-text-file-lines-groupdocs-merger-java/)
- [split pdf java: GroupDocs.Merger を使用したドキュメント分割](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [GroupDocs.Merger を使用したローカルドキュメントの Java 読み込み – ガイド](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)