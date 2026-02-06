---
date: '2026-02-06'
description: 學習如何使用 GroupDocs.Merger for Java 分割 DOCX 檔案，內容涵蓋將 DOCX 分割為多個檔案、Java 分割選項以及串流提取。
keywords:
- Java Document Splitting
- GroupDocs.Merger for Java
- Split DOCX Pages
title: 如何使用 GroupDocs.Merger for Java 拆分 DOCX
type: docs
url: /zh-hant/java/document-splitting/master-java-document-splitting-groupdocs-merger/
weight: 1
---

# 精通 Java 文件分割與 GroupDocs.Merger：將 DOCX 頁面分割為檔案與串流

在本教學中，您將學會使用 GroupDocs.Merger for Java 高效 **how to split docx** 文件。無論是需要將大型合約拆分成單獨頁面，或是將特定章節以串流形式抽取，我們都會一步步帶您完成，從環境設定到實務應用。

## 快速回答
- **哪個函式庫負責在 Java 中分割 DOCX？** GroupDocs.Merger for Java。  
- **可以將 DOCX 分割成多個檔案嗎？** 可以 – 使用 `SplitOptions` 並指定頁碼。  
- **能否取得頁面串流而非檔案？** 當然可以，只要提供自訂的 `SplitStreamFactory`。  
- **需要授權嗎？** 評估階段使用臨時試用授權即可；正式上線需購買正式授權。  
- **支援哪些 Java 版本？** 任何 JDK 8 以上皆可搭配最新的 GroupDocs.Merger 版本。

## 什麼是 “how to split docx”？
分割 DOCX 即是將多頁的 Word 文件切割成單獨的檔案（或串流），每個檔案包含一頁或多頁所選內容。此功能適用於模組化文件交付、合規工作流程，或是需要即時處理而不想產生暫存檔的情境。

## 為什麼選擇 GroupDocs.Merger for Java？
- **零相依處理：** 完全使用純 Java，無需本機二進位檔。  
- **細緻控制：** 可自行選擇頁碼、輸出格式，甚至是記憶體內的串流。  
- **可擴充效能：** 基於串流的分割方式可減少大型檔案的記憶體壓力。  

## 前置條件

### 必要的函式庫與相依性
- **Java Development Kit (JDK)：** JDK 8 或更新版本。  
- **GroupDocs.Merger for Java：** 用於文件操作的核心函式庫。

### 新增相依性
透過 Maven 或 Gradle 引入函式庫（程式碼區塊保持不變）：

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

您也可以從官方網站下載最新發行版：[GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/)。

### 取得授權
- **試用授權：** 前往 [GroupDocs.Trial License](https://purchase.groupdocs.com/temporary-license/) 取得臨時金鑰。  
- **正式授權：** 前往 [GroupDocs Purchase](https://purchase.groupdocs.com/buy) 購買完整授權。

## 設定 GroupDocs.Merger for Java
在 Java 專案中初始化函式庫：

```java
import com.groupdocs.merger.Merger;

public class DocumentSetup {
    public static void main(String[] args) {
        // Initialize a Merger object with the path of the input document
        Merger merger = new Merger("path/to/your/document.docx");
        
        // Perform operations on your document...
        
        merger.close();
    }
}
```

環境就緒後，我們將探討兩種主要的 **split docx into files** 或串流方式。

## 如何使用 GroupDocs.Merger 將 DOCX 分割成檔案

### 將文件分割為單頁檔案
#### 概述
此方法會為每個選取的頁面產生一個獨立檔案，適合分發單獨章節。

#### 步驟說明

**步驟 1 – 指定輸入與輸出路徑**  
設定原始 DOCX 的位置以及分割後檔案的儲存路徑。

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
String filePathOut = new File("YOUR_OUTPUT_DIRECTORY", 
    "SplitToSinglePages-" +
    Paths.get(filePath).getFileName().toString()
).getPath();
```

**步驟 2 – 設定 SplitOptions (split options java)**  
告訴函式庫要抽取哪些頁面。

```java
import com.groupdocs.merger.domain.options.SplitOptions;

SplitOptions splitOptions = new SplitOptions(filePathOut, new int[] { 3, 6, 8 });
```
- `filePathOut` – 每頁檔案要放置的資料夾。  
- `new int[]{3,6,8}` – 想要分割出的頁碼。

**步驟 3 – 執行分割**  
使用 `Merger` 實例執行操作。

```java
import com.groupdocs.merger.Merger;

Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

**小技巧：** 請確認輸出目錄已存在且應用程式具備寫入權限，否則分割會失敗。

### 常見陷阱
- **缺少輸出資料夾：** API 不會自動建立目錄。  
- **頁碼錯誤：** 頁碼從 1 開始，若指定 0 會拋出例外。

## 如何將 DOCX 頁面分割為串流（記憶體內）

### 概述
當需要暫時存取（例如透過 Web 服務傳送頁面）時，將頁面捕獲為串流可避免磁碟 I/O。

#### 步驟說明

**步驟 1 – 定義輸入路徑並建立串流清單**  

```java
import java.io.ByteArrayOutputStream;
import java.util.ArrayList;
import java.util.List;

String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
final List<OutputStream> resultStreams = new ArrayList<>();
```

**步驟 2 – 使用自訂 SplitStreamFactory 設定 SplitOptions**  

```java
import com.groupdocs.merger.domain.common.SplitStreamFactory;
import com.groupdocs.merger.domain.options.SplitMode;

SplitOptions splitOptions = new SplitOptions(new SplitStreamFactory() {
    @Override
    public OutputStream createSplitStream(int pageNumber) {
        return new ByteArrayOutputStream(); // Create a stream for each page
    }
    
    @Override
    public void closeSplitStream(int pageNumber, OutputStream pageStream) {
        resultStreams.add(pageStream); // Collect the streams
    }
}, new int[] { 3, 4 }, SplitMode.Pages);
```
- `createSplitStream` – 為每個請求的頁面產生新的 `OutputStream`。  
- `closeSplitStream` – 將完成的串流保存以供稍後使用。

**步驟 3 – 執行分割並取得串流**  

```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);

return resultStreams; // Retrieve streams for processing
```

**除錯提示**
- 確認來源 DOCX 路徑正確；拼寫錯誤會拋出 `FileNotFoundException`。  
- 使用完畢後務必關閉串流，以釋放記憶體。

## 實務應用
1. **法律合約：** 抽取單獨條款供審閱。  
2. **線上學習平台：** 逐章提供 Word 檔案，避免一次曝光整本教材。  
3. **商業報告：** 僅將季報的財務章節傳送給財務長。

## 效能考量
- **記憶體友善的串流：** 大於 50 MB 的文件建議使用串流方式。  
- **批次處理：** 在同一 JVM 會話中一次執行多個分割任務，可減少啟動開銷。  
- **資源清理：** 呼叫 `merger.close()` 並關閉所有串流，以避免記憶體泄漏。

## 結論
現在您已掌握如何使用 GroupDocs.Merger for Java **how to split docx** 為獨立檔案或記憶體內串流。這些技巧讓您能彈性因應任何商業需求，客製化文件交付方式。

**後續步驟**
- 嘗試不同的頁碼範圍與輸出格式（PDF、HTML 等）。  
- 結合分割與合併，在即時產生自訂文件套件。

## 常見問與答

**Q: 什麼是 GroupDocs.Merger for Java？**  
A: 這是一套 Java 函式庫，可對多種文件格式（包括 DOCX、PDF、PPTX 等）進行合併、分割與轉換。

**Q: 如何取得 GroupDocs.Merger 的授權？**  
A: 您可從 [GroupDocs website](https://purchase.groupdocs.com/temporary-license/) 取得臨時試用授權以進行評估；正式使用時請於同一網站購買完整授權。

**Q: 能否使用相同 API 分割 PDF 檔案？**  
A: 可以，`split` 方法同時支援 PDF、DOCX、PPTX 以及其他支援的格式。

**Q: 是否可以在不寫入磁碟的情況下分割文件？**  
A: 完全可以——使用上方示範的串流方式，所有操作皆在記憶體中完成。

**Q: 應該使用哪個版本的 GroupDocs.Merger？**  
A: 建議始終使用最新的穩定版，以獲得效能提升與錯誤修正。

---

**最後更新：** 2026-02-06  
**測試環境：** GroupDocs.Merger for Java 最新版  
**作者：** GroupDocs