---
date: '2026-01-29'
description: 學習如何從 Word 文件中移除密碼，以及如何使用 GroupDocs.Merger for Java 移除密碼。包括逐步程式碼示例與最佳實踐。
keywords:
- remove passwords from documents
- GroupDocs Merger for Java
- document security
title: 使用 GroupDocs.Merger for Java 移除 Word 密碼
type: docs
url: /zh-hant/java/document-security/groupdocs-merger-java-remove-password-protection/
weight: 1
---

# 從 Word 中移除密碼（使用 GroupDocs.Merger for Java）

管理文件安全至關重要，而 **remove password from Word** 檔案是自動化文件工作流程的開發人員常見的需求。在本指南中，我們將說明如何使用 **GroupDocs.Merger for Java** 移除 Word（以及其他）文件的密碼保護。完成後，您將了解如何設定函式庫、載入受密碼保護的檔案、解鎖加密的檔案內容，並儲存未受保護的版本——全部以清晰、可投入生產的程式碼示範。

## 快速解答
- **主要方法是什麼？** `Merger.removePassword()` 會從已載入的文件中移除密碼。  
- **哪個類別用於載入受保護的檔案？** `LoadOptions` 讓您指定現有的密碼。  
- **我也可以解鎖 PDF 檔案嗎？** 可以——相同的方法適用於 PDF（`remove pdf password java`）。  
- **需要授權嗎？** 試用版可用於測試；正式環境需要完整授權。  
- **需要哪個 Java 版本？** Java 8 以上，並支援 Maven 或 Gradle。  

## 什麼是 “remove password from Word”？
從 Word 文件中移除密碼表示使用正確的密碼開啟加密檔案、去除加密，並儲存為乾淨的副本。這讓後續的流程（如合併、轉換或索引）能在無需人工干預的情況下運作。

## 為什麼使用 GroupDocs.Merger for Java？
GroupDocs.Merger 提供單一且高效能的 API，能處理多種格式（DOCX、PDF、PPTX 等）。它抽象化了低層的加密細節，讓您專注於業務邏輯，而不必關注檔案格式的特殊處理。

## 前置條件
- **Java Development Kit (JDK) 8 或以上** 已安裝。  
- **Maven 或 Gradle** 作為建置系統。  
- 具備 Java I/O 與例外處理的基本知識。  

### 必要的函式庫、版本與相依性
在您的專案中加入 GroupDocs.Merger for Java：

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

您也可以直接從 [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/) 下載函式庫。

### 環境設定需求
- 已安裝 Java Development Kit (JDK)。  
- 如 IntelliJ IDEA 或 Eclipse 等 IDE（非必須，但建議使用）。  

### 知識前提
假設您已熟悉基本的 Java 程式設計與檔案 I/O 操作。了解 Maven 或 Gradle 建置系統將有助於使用。

## 設定 GroupDocs.Merger for Java
### 安裝資訊
1. **Maven** 與 **Gradle**：使用上方程式碼片段加入相依性。  
2. **直接下載**：前往 [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/) 下載最新的 JAR。  

### 取得授權步驟
- 先透過下載取得 **免費試用**。  
- 若需要更長時間，可申請 **臨時授權**。  
- 前往 [GroupDocs.Merger purchase page](https://purchase.groupdocs.com/buy) 購買正式授權以供生產環境使用。  

安裝完成後，請依照以下方式初始化函式庫：

```java
import com.groupdocs.merger.Merger;
// Other necessary imports...
public class DocumentUnlocker {
    public static void main(String[] args) {
        // Initialize and setup code here
    }
}
```

## 實作指南
本節將說明如何使用 GroupDocs.Merger for Java **移除文件密碼**。

### 功能概覽：移除密碼保護
GroupDocs.Merger 支援文件操作，包括移除密碼。此功能可在不違背安全協定的前提下，簡化對受保護檔案的存取。

#### 步驟 1：定義檔案路徑與載入選項
首先，指定受保護文件的存放位置，並使用現有密碼設定載入選項：

```java
import com.groupdocs.merger.domain.options.LoadOptions;

String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_PROTECTED";
LoadOptions loadOptions = new LoadOptions("SAMPLE_PASSWORD");
```
*原因*：`LoadOptions` 類別可安全 **load password protected document**。

#### 步驟 2：初始化 Merger 物件
接著，使用檔案路徑與載入選項建立 `Merger` 物件：

```java
import com.groupdocs.merger.Merger;

Merger merger = new Merger(filePath, loadOptions);
```
*原因*：`Merger` 類別是處理文件的核心，封裝了所有功能，包括解鎖功能。

#### 步驟 3：移除密碼保護
使用 `removePassword()` 方法去除文件的密碼：

```java
merger.removePassword();
```
*原因*：此方法會修改文件結構以 **remove password**（或解鎖加密檔案），使其可在無密碼情況下開啟。

#### 步驟 4：儲存未受保護的文件
最後，將未受保護的文件儲存至您指定的位置：

```java
String filePathOut = "YOUR_OUTPUT_DIRECTORY/RemoveDocumentPassword-" + Paths.get(filePath).getFileName().toString();
merger.save(filePathOut);
```
*原因*：儲存可確保變更已提交，且文件會存放於新目錄或既有目錄中。

### 疑難排解技巧
- 確認在 `LoadOptions` 中提供了正確的密碼。  
- 檢查檔案路徑，以避免 `FileNotFoundException`。  
- 捕捉並記錄 Merger 方法拋出的任何例外，以便快速診斷問題。

## 實務應用
GroupDocs.Merger 多功能，應用包括：

1. **自動化文件處理** – 在進一步處理前批次解鎖多個檔案。  
2. **資料遷移專案** – 暫時移除密碼以安全遷移內容。  
3. **與內容管理系統 (CMS) 整合** – 強化 CMS 管理受保護文件的能力。  

## 效能考量
為了讓解決方案保持快速且節省記憶體：

- 盡可能使用串流 I/O。  
- 儲存後立即釋放 `Merger` 實例。  
- 在批次情境下，處理多個相同格式的檔案時，重複使用單一 `Merger` 實例。  

## 常見問題與解決方案
| 問題 | 解決方案 |
|-------|----------|
| `Incorrect password` 錯誤 | 再次確認傳遞給 `LoadOptions` 的密碼字串。 |
| `OutOfMemoryError` 在大型檔案上 | 將檔案分塊處理或增加 JVM 堆積大小（`-Xmx`）。 |
| `Unsupported file format` | 確認該檔案類型已列於 GroupDocs.Merger 支援的格式中。 |

## 常見問答
1. **GroupDocs.Merger for Java 的主要目的為何？**  
   - 促進文件操作，包括合併、分割以及 **remove password** 功能。  
2. **我可以在其他程式語言中使用此函式庫嗎？**  
   - 可以，GroupDocs 提供 .NET、C++ 等類似的 API。  
3. **在生產環境使用 GroupDocs.Merger 是否需要授權？**  
   - 商業部署必須取得完整購買授權。  
4. **在移除密碼時如何處理錯誤？**  
   - 捕捉例外、記錄堆疊追蹤，並可選擇以正確憑證重新嘗試。  
5. **哪些文件類型可以解鎖？**  
   - Word、Excel、PowerPoint、PDF 以及 GroupDocs.Merger 支援的其他多種格式。  

## 資源
- [GroupDocs Documentation](https://docs.groupdocs.com/merger/java/)
- [API Reference](https://reference.groupdocs.com/merger/java/)
- [Download Latest Version](https://releases.groupdocs.com/merger/java/)
- [Purchase Information](https://purchase.groupdocs.com/buy)
- [Free Trial](https://releases.groupdocs.com/merger/java/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [Support Forum](https://forum.groupdocs.com/c/merger/) 

---

**最後更新：** 2026-01-29  
**測試版本：** GroupDocs.Merger 23.12（最新）  
**作者：** GroupDocs