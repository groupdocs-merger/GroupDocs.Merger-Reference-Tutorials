---
date: '2026-02-06'
description: GroupDocs.Merger for Java を使用して、特定のページを抽出し、ページ範囲で文書を分割する方法を学びます（奇数/偶数ページのフィルタを含む）。
keywords:
- GroupDocs.Merger for Java
- split documents by page range
- document management
title: GroupDocs.Merger for Javaで特定のページを抽出する
type: docs
url: /ja/java/document-splitting/split-documents-page-range-groupdocs-merger-java/
weight: 1
---

# GroupDocs.Merger for Java を使用した特定ページの抽出

大きな PDF、Word ファイル、またはプレゼンテーションから手動のコピー＆ペーストなしで、**extract specific pages** を効率的に行います。このチュートリアルでは、ページ範囲で文書を分割し、奇数/偶数ページなどのフィルタを適用し、単一ページのファイルを生成する方法を **GroupDocs.Merger for Java** で紹介します。

## Quick Answers
- **「extract specific pages」とは何ですか？** ソースファイルから選択したページだけを含む新しいドキュメントを作成することを意味します。  
- **対応フォーマットは何ですか？** PDF、DOCX、PPTX など、数多くの一般的なフォーマットに対応しています。  
- **奇数ページや偶数ページでフィルタできますか？** はい、`RangeMode` オプション（例: `OddPages`）を使用します。  
- **ライセンスは必要ですか？** 評価用の無料トライアルで動作しますが、本番環境では永続ライセンスが必要です。  
- **大容量ドキュメントでも使用できますか？** はい—大きな文書を分割してメモリ使用量を抑えることができます。

## What is extracting specific pages?
特定ページの抽出とは、ソースドキュメントからページのサブセットを取り出し、独立した新しいファイルとして保存するプロセスです。レポートの一部だけを作成したり、契約書の条項を共有したり、プレゼンテーションの配布資料を用意したりする際に便利です。

## Why use GroupDocs.Merger for Java to split PDFs and Word documents?
- **Unified API** – PDF、Word、PowerPoint など幅広い形式に対応しているため、別々のツールを用意する必要がありません。  
- **Fine‑grained control** – 正確なページ範囲や奇数/偶数フィルタ、単一ページ分割などを自由に指定できます。  
- **Performance‑focused** – ドキュメント全体をメモリに読み込むのではなく、ページ単位でストリーミング処理するため、大容量ファイルでも効率的に扱えます。  

## Prerequisites
- **GroupDocs.Merger for Java**（最新バージョン）  
- **JDK 8+**  
- IntelliJ IDEA や Eclipse などの IDE  
- Maven または Gradle による依存関係管理  

## Setting Up GroupDocs.Merger for Java
お好みのビルドツールを使ってライブラリをプロジェクトに追加します。

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

**Direct Download**: ライブラリは [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/) から直接ダウンロードすることもできます。

### License Acquisition
ライセンスは以下の方法で取得できます:
- **Free Trial** – 制限なしでフル機能をテストできます。  
- **Temporary License** – 評価期間を延長できます。  
- **Purchase** – 永続的な本番ライセンスです。

**Basic Initialization and Setup**  
GroupDocs.Merger を初期化するには、ドキュメントパスを指定して `Merger` のインスタンスを作成します:
```java
import com.groupdocs.merger.Merger;

String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
Merger merger = new Merger(filePath);
```

## How to extract specific pages using GroupDocs.Merger for Java
このセクションでは、ページ範囲で文書を分割しながら奇数ページフィルタを適用する手順を示します。

### Step 1: Define Input and Output Paths
ソースファイルと分割後ファイルの出力パターンを設定します:
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToSinglePagesByRangeWithFilter-Output.docx";
```

### Step 2: Configure Split Options (Range & Filter)
ライブラリに抽出対象ページと適用するフィルタを指示する `SplitOptions` オブジェクトを作成します:
```java
import com.groupdocs.merger.domain.options.SplitOptions;
import com.groupdocs.merger.domain.options.RangeMode;

SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7, RangeMode.OddPages);
```
- **filePathOut** – 出力ファイル名のパターン。  
- **3 と 7** – 開始ページと終了ページ（両端含む）。  
- **RangeMode.OddPages** – 範囲内の奇数ページのみを残し、実質的に **extract specific pages** を実行します。

### Step 3: Perform the Split Operation
設定したオプションで分割処理を実行します:
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

#### Troubleshooting Tips
- ファイルパスが正しくアクセス可能か確認してください。  
- ページ番号が文書全体のページ数以内か確認してください。範囲外の場合は例外がスローされます。  

## How to split PDF into single pages (split pdf single pages)
各ページを個別の PDF として取得したい場合は、`RangeMode` を `AllPages` に設定し、文書全体をカバーする範囲を指定します。同じ `SplitOptions` クラスで対応できます。

## How to split large document efficiently (split large document)
非常に大きなファイルを扱う際は、1‑100、101‑200 などの小さな範囲に分割してメモリ負荷を軽減します。各操作後に `Merger` インスタンスを閉じてリソースを解放してください。

## How to split PDF odd pages (split pdf odd pages)
上記例はすでに `OddPages` フィルタを示しています。偶数ページを抽出したい場合は `RangeMode.OddPages` を `RangeMode.EvenPages` に置き換えてください。

## Practical Applications
1. **Document Segmentation** – 契約書を条項単位の PDF に分割し、レビューを容易にします。  
2. **Report Management** – 長大な年次報告書から特定の章や付録だけを抽出します。  
3. **Presentation Preparation** – 個別スライドを抽出して、対象会議用に配布します。  

このロジックをデータベースやコンテンツ管理システムと組み合わせれば、ワークフローの自動化も可能です。

## Performance Considerations
- **Memory Management** – 処理後は `merger.close()`（または try‑with‑resources）を呼び出してファイルハンドルを解放します。  
- **Selective Ranges** – 本当に必要なページだけをリクエストすることで、I/O と CPU の使用量を最小限に抑えられます。  

## Conclusion
これで、**extract specific pages** を任意のサポート対象ドキュメントから取得するための、明確な手順が分かりました。GroupDocs.Merger for Java を活用すれば、ドキュメントワークフローが大幅に効率化され、ユーザーが必要とする正確なコンテンツを提供できます。

### Next Steps
- `RangeMode` のさまざまな値（例: `EvenPages`、`AllPages`）を試してみてください。  
- 分割後に **merge** 機能と組み合わせて、抽出したページの順序変更や結合を行います。  
- パスワード保護された文書、透かし付与など、フル API を探索してみましょう。

## Frequently Asked Questions
**Q: GroupDocs.Merger for Java とは何ですか？**  
A: 多数のドキュメント形式に対して、ページのマージ、分割、並び替えを実現する堅牢なライブラリです。

**Q: 他のプログラミング言語でも GroupDocs.Merger を使用できますか？**  
A: はい、.NET や C++ 向けにも同様の機能が提供されています。

**Q: ドキュメント処理中に例外が発生した場合はどう対処すればよいですか？**  
A: `try‑catch` ブロックで呼び出しをラップし、`MergerException` を確認して詳細なエラー情報を取得してください。

**Q: 奇数/偶数ページのフィルタを使用せずに文書を分割できますか？**  
A: もちろんです。`RangeMode.AllPages` を設定するか、フィルタパラメータを省略して正確なページ番号で分割できます。

**Q: GroupDocs.Merger のシステム要件は何ですか？**  
A: Java 8 以上と対応 IDE があれば動作します。追加のネイティブ依存関係は不要です。

## Resources
- [GroupDocs.Merger Documentation](https://docs.groupdocs.com/merger/java/)
- [API Reference](https://reference.groupdocs.com/merger/java/)
- [Download the Library](https://releases.groupdocs.com/merger/java/)
- [Purchase License](https://purchase.groupdocs.com/buy)
- [Free Trial and Temporary License](https://releases.groupdocs.com/merger/java/)
- [Support Forum](https://forum.groupdocs.com/c/merger/)

---

**Last Updated:** 2026-02-06  
**Tested With:** GroupDocs.Merger latest version (Java)  
**Author:** GroupDocs