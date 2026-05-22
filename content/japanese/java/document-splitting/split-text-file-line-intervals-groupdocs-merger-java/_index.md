---
date: '2026-02-06'
description: GroupDocs.Merger for Java を使用してテキストファイルを行単位で分割する方法を学びましょう。Java プロジェクトで効率的にドキュメントを分割するためのステップバイステップガイドです。
keywords:
- split text file line intervals Java
- document splitting GroupDocs.Merger
- Java document manipulation
title: GroupDocs.Merger for Java を使用した行単位でのファイル分割方法
type: docs
url: /ja/java/document-splitting/split-text-file-line-intervals-groupdocs-merger-java/
weight: 1
---

# GroupDocs.Merger for Java を使用した行単位でのファイル分割方法

大きなテキストファイルを **行単位** で、より小さく扱いやすい部分に分割することは、たとえばログを処理したり、バッチでデータをインポートしたり、長大なレポートを再構成したりする際に一般的なニーズです。このチュートリアルでは、GroupDocs.Merger for Java を使って **ファイルを行単位で分割** する方法を正確に学び、このアプローチが時間を節約できる理由を確認し、すぐに実行できるコードサンプルを入手できます。

## Quick Answers
- **“split file by lines” とは何ですか？** 元のドキュメントから指定した行番号の範囲を含む別々のテキストファイルを作成します。  
- **どのライブラリが分割を担当しますか？** GroupDocs.Merger for Java が行間隔分割用のシンプルな API を提供します。  
- **ライセンスは必要ですか？** 無料トライアルでテスト可能です。本番環境で使用するには永続ライセンスが必要です。  
- **文字数で分割できますか？** 直接はできません。分割前に前処理でファイルを再構成してください。  
- **サポートされている Java バージョンは？** Java 8 以上のランタイムであればすべて対応します。

## “split file by lines” とは？
ファイルを行単位で分割するとは、単一のテキストドキュメントを複数のファイルに分割し、各ファイルが連続した特定の行範囲（例：行 1‑3、4‑6 など）を含むようにすることです。この手法はバッチ処理、並列解析、または単に可読性を向上させる際に最適です。

## Why Use GroupDocs.Merger for Java?
GroupDocs.Merger は低レベルのファイル I/O 作業を抽象化し、ビジネスロジックに集中できるようにします。大容量ファイルを効率的に処理し、さまざまなドキュメント形式をサポートし、Maven や Gradle ビルドとシームレスに統合できるクリーンで流暢な API を提供します。

## Prerequisites
- **Java Development Kit (JDK) 8 以上** – `java` と `javac` が PATH に含まれていることを確認してください。  
- **GroupDocs.Merger for Java** – Maven、Gradle、または直接ダウンロードでライブラリを追加します。  
- **Basic Java knowledge** – クラス、メソッド、例外処理に慣れていることが前提です。

## Setting Up GroupDocs.Merger for Java
以下のいずれかの方法でプロジェクトにライブラリを追加してください。

**Maven** – この依存関係を `pom.xml` に貼り付けます:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle** – `build.gradle` に次の行を追加します:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Direct Download** – 公式リリースページから JAR を取得することもできます: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### License Acquisition
まずは無料トライアルで API を試してみてください。本番環境で使用する場合は、GroupDocs ポータルから一時ライセンスまたはフルライセンスを取得します。

## How to Split Text File by Lines (Java Implementation)

以下は簡潔なステップバイステップの解説です。各ステップはコードブロックの前に平易な説明が付いているので、何が行われているかがすぐに分かります。

### Step 1: Define Source and Output Paths
最初に、元ファイルの場所と分割されたフラグメントを書き出す先をライブラリに伝えます。
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.txt";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToLineRanges-" + Paths.get(filePath).getFileName().toString();
```

### Step 2: Configure the Split Options
`TextSplitOptions` インスタンスを作成し、希望する行間隔を指定します。`new int[] { 3, 6 }` 配列は、API に対して行 3 と行 6 の後でカットするよう指示し、結果として 2 つのパート（行 1‑3 と行 4‑6）を生成します。
```java
TextSplitOptions splitOptions = new TextSplitOptions(filePathOut, TextSplitMode.Interval, new int[] { 3, 6 });
```

### Step 3: Initialise the Merger and Execute the Split
最後に、`Merger` をソースファイルでインスタンス化し、先ほど作成したオプションで `split()` を呼び出します。
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

以上です！呼び出しが完了すると、`YOUR_OUTPUT_DIRECTORY` に指定した行範囲を含む 2 つの新しいファイルが作成されます。

## Practical Applications (Why This Matters)
1. **Data Processing Pipelines** – 巨大なログファイルを小さなチャンクに分割し、並列解析を容易にします。  
2. **Document Management** – 1 つのレポートを章単位のファイルに分割し、配布を簡素化します。  
3. **Content Segmentation** – 大規模な記事を対象プラットフォーム向けにセクション分けして準備します。

## Performance Tips
- **Stream‑line I/O** – 非常に大きなファイルを扱う場合は `Files.newBufferedReader` を使用してメモリ使用量を抑えましょう。  
- **Close Resources** – GroupDocs.Merger がほとんどのクリーンアップを行いますが、カスタムストリームは明示的に閉じてリークを防止してください。  
- **Monitor Memory** – ギガバイト級のファイルを分割するとメモリ消費が激しくなることがあります。必要に応じてヒープサイズ（例：`-Xmx2g` 以上）を確保してください。

## Common Issues and Solutions
| Issue | Why It Happens | Fix |
|-------|----------------|-----|
| `OutOfMemoryError` | 大容量のソースファイルがヒープを超過します。 | JVM ヒープを増やすか、間隔を小さくして分割してください。 |
| `FileNotFoundException` | パスが間違っている、または権限が不足しています。 | `filePath` と `filePathOut` が絶対パスで書き込み可能か確認してください。 |
| Empty output files | 区間配列がドキュメント全体をカバーしていません。 | 最後の区間が総行数以上になるよう設定してください。 |

## FAQ Section

**Q: Can I split files based on character count instead of line numbers?**  
A: 現在、GroupDocs.Merger for Java は行間隔に特化しています。ただし、分割前にテキストを前処理して、希望する文字数ごとに行を調整すれば実現可能です。

**Q: Is there a limit to how many intervals I can specify for splitting?**  
A: ライブラリ自体に特定の上限はありませんが、分割数が過剰になると処理負荷が増大し、パフォーマンスが低下する可能性があります。

**Q: How do I handle errors during file splitting?**  
A: コードを try‑catch ブロックで囲み、例外を適切に捕捉・管理してください。GroupDocs.Merger は詳細なエラーメッセージを提供し、トラブルシューティングに役立ちます。

**Q: Does the library support other text‑based formats such as CSV or TSV?**  
A: はい。CSV や TSV もプレーンテキストファイルなので、同じ行間隔ロジックが適用できます。API では `.txt` ファイルとして扱ってください。

**Q: Can I automate splitting for multiple files in a folder?**  
A: もちろんです。`Files.list(Paths.get("folder"))` を使ってフォルダー内のファイルをループ処理し、同じ `TextSplitOptions` を各ファイルに適用すれば自動化できます。

## Resources
- **Documentation:** [GroupDocs.Merger for Java Documentation](https://docs.groupdocs.com/merger/java/)  
- **API Reference:** [GroupDocs API Reference](https://reference.groupdocs.com/merger/java/)  
- **Download:** [Latest Releases](https://releases.groupdocs.com/merger/java/)  
- **Purchase and Licensing:** [Buy GroupDocs](https://purchase.groupdocs.com/buy)  
- **Free Trial:** [GroupDocs Free Trial](https://releases.groupdocs.com/merger/java/)  
- **Temporary License:** [Obtain Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Support Forum:** [GroupDocs Support](https://forum.groupdocs.com/c/merger)

---

**Last Updated:** 2026-02-06  
**Tested With:** GroupDocs.Merger 23.12 for Java  
**Author:** GroupDocs