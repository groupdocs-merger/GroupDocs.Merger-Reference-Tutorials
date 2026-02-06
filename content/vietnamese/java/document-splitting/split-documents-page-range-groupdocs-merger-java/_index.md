---
date: '2026-02-06'
description: Tìm hiểu cách trích xuất các trang cụ thể và tách tài liệu theo phạm
  vi trang bằng GroupDocs.Merger cho Java, bao gồm bộ lọc trang lẻ/chẵn.
keywords:
- GroupDocs.Merger for Java
- split documents by page range
- document management
title: Trích xuất các trang cụ thể bằng GroupDocs.Merger cho Java
type: docs
url: /vi/java/document-splitting/split-documents-page-range-groupdocs-merger-java/
weight: 1
---

# Trích xuất các trang cụ thể với GroupDocs.Merger cho Java

Hiệu quả **trích xuất các trang cụ thể** từ các tệp PDF, Word hoặc bản trình chiếu lớn mà không cần sao chép‑dán thủ công. Trong hướng dẫn này, bạn sẽ thấy cách chia tài liệu theo phạm vi trang, áp dụng các bộ lọc như trang lẻ/chẵn, và tạo các tệp một trang — tất cả với **GroupDocs.Merger cho Java**.

## Quick Answers
- **What does “extract specific pages” mean?** Nó có nghĩa là tạo các tài liệu mới chỉ chứa các trang bạn chọn từ tệp nguồn.  
- **Which formats are supported?** PDF, DOCX, PPTX, và nhiều định dạng phổ biến khác.  
- **Can I filter by odd or even pages?** Có, sử dụng tùy chọn `RangeMode` (ví dụ: `OddPages`).  
- **Do I need a license?** Bản dùng thử miễn phí đủ cho việc đánh giá; cần giấy phép vĩnh viễn cho môi trường sản xuất.  
- **Is it suitable for large documents?** Có — chia các phần tài liệu lớn để giữ mức sử dụng bộ nhớ thấp.

## What is extracting specific pages?
Trích xuất các trang cụ thể là quá trình lấy một tập con các trang từ tài liệu nguồn và lưu chúng thành một tệp mới, độc lập. Điều này hữu ích cho việc tạo báo cáo tập trung, chia sẻ các điều khoản hợp đồng, hoặc chuẩn bị tài liệu phát tay cho buổi thuyết trình.

## Why use GroupDocs.Merger for Java to split PDFs and Word documents?
- **Unified API** – Hoạt động với PDF, Word, PowerPoint và nhiều định dạng khác, vì vậy bạn không cần công cụ riêng biệt.  
- **Fine‑grained control** – Chọn chính xác phạm vi trang, bộ lọc lẻ/chẵn, hoặc chia thành các tệp một trang.  
- **Performance‑focused** – Xử lý các tệp lớn hiệu quả bằng cách stream các trang thay vì tải toàn bộ tài liệu vào bộ nhớ.  

## Prerequisites
- **GroupDocs.Merger for Java** (phiên bản mới nhất)  
- **JDK 8+**  
- Một IDE như IntelliJ IDEA hoặc Eclipse  
- Maven hoặc Gradle để quản lý phụ thuộc  

## Setting Up GroupDocs.Merger for Java
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

**Direct Download**: Bạn cũng có thể tải thư viện trực tiếp từ [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### License Acquisition
Bạn có thể lấy giấy phép qua:
- **Free Trial** – Kiểm tra đầy đủ tính năng không giới hạn.  
- **Temporary License** – Thời gian đánh giá kéo dài.  
- **Purchase** – Giấy phép sản xuất vĩnh viễn.

**Basic Initialization and Setup**  
Để khởi tạo GroupDocs.Merger, tạo một thể hiện của `Merger` với đường dẫn tài liệu của bạn:  
```java
import com.groupdocs.merger.Merger;

String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
Merger merger = new Merger(filePath);
```

## How to extract specific pages using GroupDocs.Merger for Java
Phần này hướng dẫn bạn cách chia tài liệu theo phạm vi trang đồng thời áp dụng bộ lọc trang lẻ.

### Step 1: Define Input and Output Paths
Đặt đường dẫn tệp nguồn và mẫu đích cho các tệp đã chia:  
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToSinglePagesByRangeWithFilter-Output.docx";
```

### Step 2: Configure Split Options (Range & Filter)
Tạo một đối tượng `SplitOptions` để chỉ định các trang cần trích xuất và bộ lọc sẽ áp dụng:  
```java
import com.groupdocs.merger.domain.options.SplitOptions;
import com.groupdocs.merger.domain.options.RangeMode;

SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7, RangeMode.OddPages);
```
- **filePathOut** – Mẫu tên tệp đích.  
- **3 và 7** – Số trang bắt đầu và kết thúc (bao gồm).  
- **RangeMode.OddPages** – Giữ lại chỉ các trang lẻ trong phạm vi, thực tế **trích xuất các trang cụ thể**.

### Step 3: Perform the Split Operation
Thực hiện chia bằng cách sử dụng các tùy chọn đã cấu hình:  
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

#### Troubleshooting Tips
- Kiểm tra lại các đường dẫn tệp có đúng và có thể truy cập được không.  
- Đảm bảo các số trang nằm trong tổng số trang của tài liệu; nếu không sẽ ném ra ngoại lệ.  

## How to split PDF into single pages (split pdf single pages)
Nếu bạn cần mỗi trang thành một PDF riêng, chỉ cần đặt `RangeMode` thành `AllPages` và chỉ định một phạm vi bao phủ toàn bộ tài liệu. Lớp `SplitOptions` cùng xử lý trường hợp này.

## How to split large document efficiently (split large document)
Khi làm việc với các tệp rất lớn, hãy cân nhắc chia chúng thành các phạm vi nhỏ hơn (ví dụ: 1‑100, 101‑200) để giảm áp lực bộ nhớ. Đóng thể hiện `Merger` sau mỗi thao tác để giải phóng tài nguyên.

## How to split PDF odd pages (split pdf odd pages)
Ví dụ ở trên đã minh họa bộ lọc `OddPages`. Thay `RangeMode.OddPages` bằng `RangeMode.EvenPages` để trích xuất các trang chẵn thay vì lẻ.

## Practical Applications
1. **Document Segmentation** – Chia hợp đồng thành các PDF mức điều khoản để dễ dàng xem xét.  
2. **Report Management** – Trích xuất một chương hoặc phụ lục cụ thể từ báo cáo thường niên dài.  
3. **Presentation Preparation** – Tách các slide riêng lẻ cho các buổi họp mục tiêu.  

Bạn cũng có thể tích hợp logic này với cơ sở dữ liệu hoặc hệ thống quản lý nội dung để tự động hoá quy trình làm việc.

## Performance Considerations
- **Memory Management** – Gọi `merger.close()` (hoặc sử dụng try‑with‑resources) sau khi xử lý để giải phóng các handle tệp.  
- **Selective Ranges** – Chỉ yêu cầu các trang thực sự cần thiết; điều này giảm thiểu I/O và sử dụng CPU.  

## Conclusion
Bạn đã có một phương pháp rõ ràng, từng bước để **trích xuất các trang cụ thể** từ bất kỳ loại tài liệu nào được hỗ trợ bằng GroupDocs.Merger cho Java. Khả năng này giúp tối ưu hoá quy trình tài liệu và cung cấp chính xác nội dung mà người dùng cần.

### Next Steps
- Thử nghiệm các giá trị `RangeMode` khác nhau (ví dụ: `EvenPages`, `AllPages`).  
- Kết hợp việc chia với chức năng **merge** để sắp xếp lại hoặc nối các trang đã trích xuất.  
- Khám phá toàn bộ API cho tài liệu có mật khẩu, watermark và nhiều hơn nữa.

## Frequently Asked Questions
**Q: What is GroupDocs.Merger for Java?**  
A: Thư viện mạnh mẽ cho phép hợp nhất, chia và sắp xếp lại các trang trên nhiều định dạng tài liệu.

**Q: Can I use GroupDocs.Merger with other programming languages?**  
A: Có, các khả năng tương tự cũng có sẵn cho .NET và C++.

**Q: How do I handle exceptions during document processing?**  
A: Bao bọc các lời gọi trong khối `try‑catch` và kiểm tra `MergerException` để có thông tin lỗi chi tiết.

**Q: Is it possible to split documents without filtering by odd/even pages?**  
A: Chắc chắn — đặt `RangeMode.AllPages` hoặc bỏ qua tham số bộ lọc để chia theo số trang chính xác.

**Q: What are the system requirements for using GroupDocs.Merger?**  
A: Java 8 trở lên và một IDE tương thích; không cần phụ thuộc native bổ sung.

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