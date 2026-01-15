---
date: '2025-12-19'
description: Tìm hiểu cách nhúng PDF vào tài liệu Word và thêm PDF vào tệp Word với
  GroupDocs.Merger cho Java. Hướng dẫn từng bước để nhúng OLE một cách liền mạch.
keywords:
- embed OLE objects in Word documents
- GroupDocs Merger for Java tutorial
- import OLE objects using Java
title: Cách nhúng PDF vào Word bằng GroupDocs.Merger cho Java – Hướng dẫn toàn diện
type: docs
url: /vi/java/document-import/embed-ole-objects-word-documents-groupdocs-java/
weight: 1
---

# Cách nhúng pdf vào word bằng GroupDocs.Merger cho Java

Nhúng một tệp PDF trực tiếp vào trong tài liệu Word có thể cải thiện đáng kể khả năng cộng tác, vì người đọc không còn phải chuyển đổi giữa các tệp. Trong hướng dẫn này, bạn sẽ khám phá **cách nhúng pdf vào word** bằng GroupDocs.Merger cho Java, và xem các mẹo thực tế về quy trình **thêm pdf vào word**. Chúng tôi sẽ hướng dẫn mọi thứ từ việc thiết lập thư viện đến tùy chỉnh kích thước và vị trí của đối tượng OLE.

## Câu trả lời nhanh
- **Thư viện nào được yêu cầu?** GroupDocs.Merger cho Java (phiên bản mới nhất)  
- **Tôi có thể nhúng bất kỳ loại tệp nào không?** Có – PDFs, hình ảnh, bảng tính, v.v., dưới dạng đối tượng OLE  
- **Tôi có cần giấy phép không?** Bản dùng thử miễn phí hoạt động cho phát triển; giấy phép thương mại cần thiết cho môi trường sản xuất  
- **IDE Java nào hoạt động tốt nhất?** IntelliJ IDEA, Eclipse, hoặc bất kỳ IDE nào hỗ trợ Maven/Gradle  
- **Thời gian triển khai khoảng bao lâu?** Khoảng 10‑15 phút cho một việc nhúng cơ bản  

## Nhúng pdf vào word là gì?
Nhúng một PDF tạo ra một đối tượng OLE (Object Linking and Embedding) bên trong tệp Word. PDF vẫn giữ đầy đủ chức năng — người dùng có thể nhấp đúp vào biểu tượng để mở nó trong trình xem PDF, trong khi tài liệu Word vẫn tự chứa.

## Tại sao thêm pdf vào word bằng GroupDocs.Merger?
- **Tài liệu nguồn duy nhất:** Giữ hợp đồng, hướng dẫn hoặc báo cáo cùng nhau mà không cần liên kết bên ngoài.  
- **Cải thiện khả năng truy cập:** Người đọc có thể xem PDF mà không rời khỏi môi trường Word.  
- **Thân thiện với tự động hoá:** Hoàn hảo cho việc tạo báo cáo hàng loạt hoặc gói pháp lý một cách lập trình.  

## Yêu cầu trước
- **Thư viện & Phụ thuộc:** Bao gồm thư viện GroupDocs.Merger qua Maven hoặc Gradle.  
- **Môi trường phát triển:** IntelliJ IDEA, Eclipse, hoặc bất kỳ IDE Java nào.  
- **Kiến thức cơ bản:** Quen thuộc với Java và các khái niệm thao tác tài liệu.  

## Cài đặt GroupDocs.Merger cho Java
Để nhúng các đối tượng OLE, trước tiên thêm thư viện vào dự án của bạn.

### Maven
Add this dependency to your `pom.xml` file:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle
Include this in your `build.gradle` file:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### Tải trực tiếp
Hoặc, tải phiên bản mới nhất từ [trang phát hành GroupDocs.Merger cho Java](https://releases.groupdocs.com/merger/java/).

**Mua giấy phép:** Bạn có thể bắt đầu với bản dùng thử miễn phí hoặc lấy giấy phép tạm thời để đánh giá tính năng trước khi mua. Truy cập [Mua GroupDocs](https://purchase.groupdocs.com/buy) để biết thêm chi tiết.

## Khởi tạo cơ bản
Nhập các lớp cần thiết để bạn có thể làm việc với các đối tượng OLE:
```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OleWordProcessingOptions;
```

## Hướng dẫn từng bước để nhúng pdf vào word

### Bước 1: Xác định đường dẫn tệp và trang mục tiêu
Đặt tài liệu Word nguồn, PDF bạn muốn nhúng, và vị trí mà đối tượng OLE sẽ xuất hiện.
```java
String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.docx"; // Source Word document path
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf"; // File to be embedded as an OLE object
String outputFilePath = new File("YOUR_OUTPUT_DIRECTORY",
    "ImportDocumentToWordProcessing-" + Paths.get(sourceFilePath).getFileName().toString()).getPath();
int pageNumber = 2; // Page number where the OLE object will be inserted
```

- **`sourceFilePath`** – đường dẫn tới tệp Word hiện có.  
- **`embeddedFilePath`** – PDF bạn muốn **thêm pdf vào word**.  
- **`outputFilePath`** – nơi tài liệu mới sẽ được lưu.  
- **`pageNumber`** – trang sẽ chứa đối tượng OLE.  

### Bước 2: Cấu hình OleWordProcessingOptions
Tùy chỉnh giao diện của PDF đã nhúng bằng cách đặt kích thước của nó.
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Set width of the embedded object (in points)
oleWordsOptions.setHeight(300); // Set height of the embedded object (in points)
```

- **`setWidth()` / `setHeight()`** – kiểm soát kích thước biểu tượng PDF xuất hiện trong tài liệu Word.

### Bước 3: Khởi tạo Merger và nhập đối tượng OLE
Tạo một thể hiện `Merger` cho tài liệu nguồn, nhập đối tượng OLE, và lưu kết quả.
```java
Merger merger = new Merger(sourceFilePath);
{
    merger.importDocument(oleWordsOptions); // Embed the OLE object into the Word document
    merger.save(outputFilePath); // Save changes to a new output file
}
```

- **`importDocument()`** – nhận `OleWordProcessingOptions` và chèn PDF dưới dạng đối tượng OLE.  
- **`save()`** – ghi tài liệu đã chỉnh sửa vào `outputFilePath`.  

### Bước 4: (Tùy chọn) Áp dụng lại cấu hình cho các đối tượng bổ sung
Nếu bạn cần nhúng thêm PDF, lặp lại **Bước 1‑3** với các đường dẫn tệp và số trang mới. Lớp `OleWordProcessingOptions` giống nhau cho phép bạn kiểm soát từng đối tượng riêng lẻ.

## Cấu hình OleWordProcessingOptions (Nâng cao)
Bạn có thể tinh chỉnh vị trí hơn nữa, chẳng hạn căn chỉnh đối tượng hoặc thêm chú thích. Đoạn mã dưới đây lặp lại cấu hình cơ bản để rõ ràng:
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Width of the embedded object
oleWordsOptions.setHeight(300); // Height of the embedded object
```

## Ứng dụng thực tiễn
Nhúng PDF hữu ích trong nhiều tình huống thực tế:

1. **Sổ tay kỹ thuật** – Chèn các sơ đồ chi tiết hoặc PDF tham khảo trực tiếp vào hướng dẫn.  
2. **Báo cáo tài chính** – Thêm các PDF kiểm toán bổ sung mà không làm gián đoạn luồng của báo cáo chính.  
3. **Hợp đồng pháp lý** – Đính kèm phụ lục hoặc tài liệu phụ dưới dạng đối tượng OLE để dễ dàng truy cập trong quá trình xem xét.  

## Các cân nhắc về hiệu năng
Khi xử lý tài liệu lớn hoặc nhiều đối tượng OLE, hãy lưu ý các mẹo sau:

- **Cắt giảm nội dung không cần thiết** – chỉ nhúng các trang bạn thực sự cần.  
- **Quản lý bộ nhớ** – sử dụng cờ `-Xmx` của Java để cấp phát đủ bộ nhớ heap cho các tệp lớn.  
- **Cập nhật thường xuyên** – các phiên bản mới của GroupDocs.Merger thường bao gồm các tối ưu hoá hiệu năng.  

## Câu hỏi thường gặp

**Q: OLE embedding là gì?**  
A: Nhúng cho phép bạn chèn các đối tượng như PDF vào tài liệu Word dưới dạng liên kết vẫn giữ nguyên chức năng gốc.

**Q: Tôi có thể nhúng nhiều đối tượng OLE trong một tài liệu không?**  
A: Có, mỗi đối tượng có thể được cấu hình cho các trang và kích thước khác nhau bằng cách sử dụng các `OleWordProcessingOptions` riêng biệt.

**Q: Có giới hạn kích thước cho các tệp được nhúng không?**  
A: Giới hạn thường do Word quy định, nhưng GroupDocs.Merger xử lý các tệp lớn một cách hiệu quả.

**Q: Làm thế nào để giải quyết lỗi nhúng?**  
A: Kiểm tra lại các đường dẫn tệp và đảm bảo JVM có đủ bộ nhớ. Kiểm tra xem PDF nguồn có bị hỏng không.

**Q: Tôi có thể chỉnh sửa các đối tượng đã nhúng sau khi chèn không?**  
A: Bạn có thể mở lại tệp Word trong Microsoft Word và chỉnh sửa đối tượng OLE, hoặc chạy lại mã Merger với các tùy chọn cập nhật.

## Tài nguyên bổ sung
- [Tài liệu GroupDocs.Merger](https://docs.groupdocs.com/merger/java/)
- [Tham chiếu API](https://reference.groupdocs.com/merger/java/)
- [Tải phiên bản mới nhất](https://releases.groupdocs.com/merger/java/)
- [Mua GroupDocs](https://purchase.groupdocs.com/buy)
- [Dùng thử miễn phí](https://releases.groupdocs.com/merger/java/)
- [Giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/)
- [Diễn đàn hỗ trợ](https://forum.groupdocs.com/c/merger/)

---

**Cập nhật lần cuối:** 2025-12-19  
**Đã kiểm tra với:** GroupDocs.Merger cho Java phiên bản mới nhất  
**Tác giả:** GroupDocs