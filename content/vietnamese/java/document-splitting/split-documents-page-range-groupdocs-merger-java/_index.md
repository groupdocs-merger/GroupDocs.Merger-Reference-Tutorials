---
date: '2026-07-25'
description: Tìm hiểu cách tách các trang tài liệu Word bằng GroupDocs.Merger cho
  Java, với các ví dụ từng bước cho PDF, DOCX và PPTX, cộng thêm bộ lọc trang lẻ/chẵn.
keywords:
- split word document pages
- how to split pdf
- split pdf by range
- GroupDocs.Merger Java
- document page extraction
lastmod: '2026-07-25'
og_description: Tìm hiểu cách tách các trang tài liệu Word bằng GroupDocs.Merger cho
  Java, với các ví dụ từng bước cho PDF, DOCX và PPTX, cộng thêm bộ lọc trang lẻ/chẵn.
og_image_alt: Guide to split word document pages using GroupDocs.Merger for Java
og_title: Tách các trang tài liệu Word bằng GroupDocs.Merger cho Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-25'
  description: Learn how to split word document pages using GroupDocs.Merger for Java,
    with step‑by‑step examples for PDF, DOCX, and PPTX, plus odd/even page filters.
  headline: Split Word Document Pages with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to split word document pages using GroupDocs.Merger for Java,
    with step‑by‑step examples for PDF, DOCX, and PPTX, plus odd/even page filters.
  name: Split Word Document Pages with GroupDocs.Merger for Java
  steps:
  - name: Define Input and Output Paths
    text: 'Set the source file and the destination pattern for the split files:'
  - name: Configure Split Options (Range & Filter)
    text: 'The `SplitOptions` class tells the library which pages to extract and which
      filter to apply. `RangeMode` is an enumeration that specifies which pages to
      include, such as odd, even, or all pages. The `filePathOut` property defines
      the naming pattern, while `startPage` and `endPage` set the inclusive '
  - name: Perform the Split Operation
    text: 'Execute the split using the configured options:'
  type: HowTo
- questions:
  - answer: GroupDocs.Merger for Java is a robust library that enables merging, splitting,
      and reordering pages across many document formats, including PDF, DOCX, and
      PPTX.
    question: What is GroupDocs.Merger for Java?
  - answer: Yes, similar capabilities exist for .NET and C++.
    question: Can I use GroupDocs.Merger with other programming languages?
  - answer: '`MergerException` is the exception type thrown by GroupDocs.Merger when
      a processing error occurs. Wrap calls in `try‑catch` blocks and inspect `MergerException`
      for detailed error information.'
    question: How do I handle exceptions during document processing?
  - answer: Absolutely—set `RangeMode.AllPages` or omit the filter parameter to split
      by exact page numbers.
    question: Is it possible to split documents without filtering by odd/even pages?
  - answer: Java 8 or higher and a compatible IDE; no additional native dependencies
      are required.
    question: What are the system requirements for using GroupDocs.Merger?
  type: FAQPage
tags:
- split word document pages
- GroupDocs.Merger
- Java document processing
- PDF splitting
- page range extraction
title: Tách các trang tài liệu Word bằng GroupDocs.Merger cho Java
type: docs
url: /vi/java/document-splitting/split-documents-page-range-groupdocs-merger-java/
weight: 1
---

# Tách các trang tài liệu Word bằng GroupDocs.Merger cho Java

Trong hướng dẫn này, bạn sẽ học cách **tách các trang tài liệu Word**—và các định dạng khác như PDF và PPTX—bằng cách sử dụng GroupDocs.Merger cho Java. Cho dù bạn cần trích xuất một điều khoản hợp đồng duy nhất, tạo tài liệu phát tay từ một bản trình bày, hoặc chia một báo cáo lớn thành các phần dễ quản lý, API cho phép bạn chỉ định các phạm vi trang chính xác, bộ lọc lẻ/chẵn, hoặc xuất ra từng trang riêng lẻ chỉ với vài dòng mã.

## Câu trả lời nhanh
- **“extract specific pages” có nghĩa là gì?** Nó có nghĩa là tạo các tài liệu mới chỉ chứa các trang bạn chọn từ tệp nguồn.  
- **Các định dạng nào được hỗ trợ?** PDF, DOCX, PPTX và nhiều định dạng phổ biến khác.  
- **Có thể lọc theo trang lẻ hoặc chẵn không?** Có, bằng cách sử dụng tùy chọn `RangeMode` (ví dụ: `OddPages`).  
- **Có cần giấy phép không?** Bản dùng thử miễn phí đủ cho việc đánh giá; giấy phép vĩnh viễn cần thiết cho môi trường sản xuất.  
- **Có phù hợp với tài liệu lớn không?** Có—cắt các phần tài liệu lớn để giữ mức sử dụng bộ nhớ thấp.

## Khái niệm trích xuất các trang cụ thể
Trích xuất các trang cụ thể có nghĩa là lấy một tập hợp các trang đã chọn từ tài liệu gốc và tạo một tệp mới, độc lập, chỉ chứa những trang đó. Kỹ thuật này hữu ích cho việc tạo báo cáo tập trung, chia sẻ các điều khoản hợp đồng riêng lẻ, hoặc phân phối các slide trình chiếu cụ thể mà không tiết lộ toàn bộ tài liệu nguồn.

## Tại sao nên sử dụng GroupDocs.Merger cho Java để tách PDF và tài liệu Word?
Chỉ tải các trang bạn cần và để GroupDocs.Merger thực hiện công việc nặng. Thư viện hỗ trợ **hơn 50 định dạng đầu vào và đầu ra**, có thể xử lý các tệp lên tới **2 GB** mà không cần tải toàn bộ tài liệu vào bộ nhớ, và cung cấp một API nhất quán cho PDF, DOCX, PPTX và nhiều định dạng khác—giúp bạn tránh việc phải dùng nhiều công cụ.

## Yêu cầu trước
- **GroupDocs.Merger for Java** (phiên bản mới nhất)  
- **JDK 8+**  
- Một IDE như IntelliJ IDEA hoặc Eclipse  
- Maven hoặc Gradle để quản lý phụ thuộc  

## Cài đặt GroupDocs.Merger cho Java
Thêm thư viện vào dự án của bạn bằng công cụ xây dựng ưa thích.

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

**Tải xuống trực tiếp**: Bạn cũng có thể tải thư viện trực tiếp từ [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Nhận giấy phép
Bạn có thể nhận giấy phép qua:
- **Free Trial** – Kiểm tra đầy đủ tính năng mà không có giới hạn.  
- **Temporary License** – Thời gian đánh giá kéo dài.  
- **Purchase** – Giấy phép sản xuất vĩnh viễn.

**Khởi tạo và Cấu hình Cơ bản**  
Lớp `Merger` là điểm vào cho tất cả các thao tác tách. Nó đại diện cho một tài liệu trong bộ nhớ và cung cấp các phương thức để thao tác các trang. Để khởi tạo GroupDocs.Merger, tạo một thể hiện của `Merger` với đường dẫn tài liệu của bạn:  
```java
import com.groupdocs.merger.Merger;

String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
Merger merger = new Merger(filePath);
```

## Cách trích xuất các trang cụ thể bằng GroupDocs.Merger cho Java
Để trích xuất các trang cụ thể, tải tài liệu nguồn bằng một thể hiện `Merger`, cấu hình một đối tượng `SplitOptions` với các trang bắt đầu và kết thúc mong muốn và tùy chọn đặt `RangeMode` (ví dụ: `OddPages` hoặc `EvenPages`). Sau đó gọi `merger.split(options)` để tạo các tệp mới chỉ chứa các trang đã chọn.

### Câu trả lời trực tiếp
Tạo một thể hiện `Merger`, cấu hình một đối tượng `SplitOptions` với `RangeMode.OddPages` và các trang bắt đầu/kết thúc mong muốn, sau đó gọi `merger.split(options)`. Quy trình một bước này chỉ trích xuất các trang lẻ trong phạm vi đã chỉ định và ghi chúng vào mẫu đầu ra bạn cung cấp.

### Bước 1: Xác định Đường dẫn Đầu vào và Đầu ra
Đặt tệp nguồn và mẫu đích cho các tệp đã tách:  
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToSinglePagesByRangeWithFilter-Output.docx";
```

### Bước 2: Cấu hình Split Options (Phạm vi & Bộ lọc)
Lớp `SplitOptions` cho thư viện biết các trang nào cần trích xuất và bộ lọc nào sẽ áp dụng. `RangeMode` là một enumeration xác định các trang sẽ bao gồm, như lẻ, chẵn, hoặc tất cả các trang. Thuộc tính `filePathOut` định nghĩa mẫu đặt tên, trong khi `startPage` và `endPage` thiết lập phạm vi bao gồm. `RangeMode.OddPages` giữ lại chỉ các trang lẻ trong phạm vi đó, thực tế **trích xuất các trang cụ thể**.  
```java
import com.groupdocs.merger.domain.options.SplitOptions;
import com.groupdocs.merger.domain.options.RangeMode;

SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7, RangeMode.OddPages);
```

### Bước 3: Thực hiện Hoạt động Tách
Thực thi việc tách bằng các tùy chọn đã cấu hình:  
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

#### Mẹo Khắc phục sự cố
- Xác minh rằng các đường dẫn tệp là chính xác và có thể truy cập.  
- Đảm bảo các số trang nằm trong tổng số trang của tài liệu; nếu không sẽ ném ra một ngoại lệ.

## Cách tách PDF thành các trang riêng lẻ (split pdf single pages)
Để tách một PDF thành các trang riêng lẻ, mở tệp bằng một thể hiện `Merger` và đặt `RangeMode.AllPages` trong một đối tượng `SplitOptions`. Xác định mẫu đặt tên đầu ra, sau đó gọi `merger.split(options)`. Thư viện sẽ tạo một tệp PDF riêng cho mỗi trang, giữ nguyên nội dung và định dạng gốc.

## Cách tách tài liệu lớn một cách hiệu quả (split large document)
Khi xử lý các tài liệu rất lớn, hãy tách chúng thành các phạm vi trang nhỏ hơn (ví dụ: 1‑100, 101‑200) để giảm tiêu thụ bộ nhớ. Tạo các `SplitOptions` riêng cho mỗi phạm vi, chạy `merger.split(options)` tuần tự, và đóng thể hiện `Merger` sau mỗi lô. Cách tiếp cận này giúp duy trì mức sử dụng CPU và I/O ở mức có thể kiểm soát.

## Cách tách các trang lẻ của PDF (split pdf odd pages)
Để trích xuất chỉ các trang số lẻ từ một PDF, cấu hình một đối tượng `SplitOptions` với `RangeMode.OddPages`. Đặt mẫu đầu ra mong muốn và tùy chọn xác định phạm vi trang nếu bạn không cần toàn bộ tài liệu. Gọi `merger.split(options)` và thư viện sẽ tạo các tệp chỉ chứa các trang lẻ.

## Ứng dụng Thực tiễn
1. **Document Segmentation** – Chia hợp đồng thành các PDF mức điều khoản để dễ xem xét.  
2. **Report Management** – Trích xuất một chương hoặc phụ lục cụ thể từ báo cáo thường niên dài.  
3. **Presentation Preparation** – Tách các slide riêng lẻ cho các cuộc họp mục tiêu.  

Bạn cũng có thể tích hợp logic này với cơ sở dữ liệu hoặc hệ thống quản lý nội dung để tự động hoá các quy trình công việc.

## Các cân nhắc về hiệu năng
- **Memory Management** – Gọi `merger.close()` (hoặc dựa vào try‑with‑resources) sau khi xử lý để giải phóng các handle tệp.  
- **Selective Ranges** – Chỉ yêu cầu các trang thực sự cần thiết; điều này giảm thiểu việc I/O và sử dụng CPU.  

## Kết luận
Bây giờ bạn đã có một phương pháp rõ ràng, từng bước để **tách các trang tài liệu Word** (và các định dạng hỗ trợ khác) bằng cách sử dụng GroupDocs.Merger cho Java. Khả năng này giúp tối ưu hoá quy trình tài liệu của bạn và cho phép bạn cung cấp chính xác nội dung mà người dùng cần.

### Các bước tiếp theo
- Thử nghiệm với các giá trị `RangeMode` khác nhau (ví dụ: `EvenPages`, `AllPages`).  
- Kết hợp việc tách với chức năng **merge** để sắp xếp lại hoặc nối các trang đã trích xuất.  
- Khám phá toàn bộ API cho tài liệu được bảo mật bằng mật khẩu, watermark và các tính năng khác.  

## Câu hỏi thường gặp
**Q: GroupDocs.Merger for Java là gì?**  
A: GroupDocs.Merger for Java là một thư viện mạnh mẽ cho phép hợp nhất, tách và sắp xếp lại các trang trên nhiều định dạng tài liệu, bao gồm PDF, DOCX và PPTX.

**Q: Có thể sử dụng GroupDocs.Merger với các ngôn ngữ lập trình khác không?**  
A: Có, các khả năng tương tự tồn tại cho .NET và C++.

**Q: Làm thế nào để xử lý ngoại lệ khi xử lý tài liệu?**  
A: `MergerException` là loại ngoại lệ được ném ra bởi GroupDocs.Merger khi xảy ra lỗi xử lý. Bao bọc các lời gọi trong khối `try‑catch` và kiểm tra `MergerException` để có thông tin chi tiết về lỗi.

**Q: Có thể tách tài liệu mà không lọc theo trang lẻ/chẵn không?**  
A: Chắc chắn—đặt `RangeMode.AllPages` hoặc bỏ qua tham số bộ lọc để tách theo các số trang chính xác.

**Q: Yêu cầu hệ thống để sử dụng GroupDocs.Merger là gì?**  
A: Java 8 trở lên và một IDE tương thích; không cần các phụ thuộc native bổ sung.

## Tài nguyên
- [Tài liệu GroupDocs.Merger](https://docs.groupdocs.com/merger/java/)
- [Tham chiếu API](https://reference.groupdocs.com/merger/java/)
- [Tải thư viện](https://releases.groupdocs.com/merger/java/)
- [Mua giấy phép](https://purchase.groupdocs.com/buy)
- [Bản dùng thử và Giấy phép tạm thời](https://releases.groupdocs.com/merger/java/)
- [Diễn đàn hỗ trợ](https://forum.groupdocs.com/c/merger/)

**Cập nhật lần cuối:** 2026-07-25  
**Đã kiểm tra với:** GroupDocs.Merger phiên bản mới nhất (Java)  
**Tác giả:** GroupDocs

## Hướng dẫn liên quan
- [Loại bỏ các trang một cách hiệu quả khỏi tài liệu Word bằng GroupDocs.Merger cho Java](/merger/java/page-operations/remove-pages-groupdocs-merger-java-word-documents/)
- [Quản lý tài liệu chính - Hợp nhất tài liệu Word với GroupDocs.Merger cho Java](/merger/java/document-joining/groupdocs-merger-java-word-document-management/)
- [Cách tách tài liệu thành các tệp đa trang bằng GroupDocs.Merger cho Java](/merger/java/document-splitting/split-documents-multi-page-files-java-groupdocs-merger/)