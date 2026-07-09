---
date: '2026-03-17'
description: Học cách nhúng PDF vào Excel và nhập tài liệu vào Excel bằng GroupDocs.Merger
  cho Java. Theo dõi hướng dẫn chi tiết này kèm ví dụ mã và mẹo khắc phục sự cố.
keywords:
- import OLE object into Excel
- embed PDF in Excel with Java
- use GroupDocs.Merger for document integration
title: Cách nhúng PDF vào Excel bằng GroupDocs.Merger cho Java – Nhập đối tượng OLE
  – Hướng dẫn từng bước
type: docs
url: /vi/java/document-import/import-ole-object-excel-groupdocs-merger-java/
weight: 1
---

# Cách nhúng PDF vào Excel bằng GroupDocs.Merger cho Java: Hướng dẫn từng bước

Việc nhúng PDF vào Excel có thể biến một bảng tính tĩnh thành một báo cáo phong phú, tương tác, chứa toàn bộ tài liệu nguồn ngay tại vị trí bạn cần. Trong hướng dẫn này, bạn sẽ học **cách nhúng PDF vào Excel** bằng cách nhập một tệp PDF dưới dạng đối tượng OLE (Object Linking and Embedding) với GroupDocs.Merger cho Java. Chúng tôi sẽ đi qua mọi yêu cầu tiên quyết, trình bày mã chính xác, và cung cấp các mẹo thực tiễn để bạn có thể bắt đầu áp dụng kỹ thuật này trong các dự án của mình ngay hôm nay.

## Câu trả lời nhanh
- **“embed PDF in Excel” có nghĩa là gì?** Nó có nghĩa là chèn một tệp PDF dưới dạng đối tượng OLE để PDF có thể được mở trực tiếp từ bảng tính.  
- **Thư viện nào xử lý việc nhập?** GroupDocs.Merger cho Java cung cấp phương thức `importDocument` cho mục đích này.  
- **Tôi có cần giấy phép không?** Bản dùng thử miễn phí đủ cho việc đánh giá; giấy phép thương mại cần thiết cho môi trường sản xuất.  
- **Tôi có thể nhúng các loại tệp khác không?** Có – Word, hình ảnh và các định dạng được hỗ trợ khác cũng có thể được nhập dưới dạng đối tượng OLE.  
- **Cách tiếp cận này có tương thích với Java 8+ không?** Chắc chắn – thư viện hỗ trợ Java 8 và các phiên bản mới hơn.

## Nhúng PDF vào Excel là gì?
Nhúng PDF vào Excel lưu trữ PDF bên trong workbook dưới dạng đối tượng OLE. Người dùng có thể nhấp đúp vào đối tượng để mở PDF gốc mà không rời khỏi bảng tính, rất thích hợp cho các chuỗi kiểm toán, báo cáo chi tiết, hoặc tài liệu tham khảo.

## Tại sao nên nhúng PDF vào Excel với GroupDocs.Merger?
- **Tích hợp liền mạch:** Không cần sao chép‑dán thủ công; API xử lý vị trí và kích thước.  
- **Sẵn sàng tự động hóa:** Hoàn hảo cho việc xử lý hàng loạt báo cáo hàng tháng hoặc tạo bảng điều khiển một cách lập trình.  
- **Hỗ trợ đa định dạng:** Hoạt động với PDF, tài liệu Word, hình ảnh và hơn thế nữa, tất cả qua một thư viện duy nhất.  
- **Tập trung vào hiệu năng:** Được thiết kế để làm việc hiệu quả với các workbook lớn và nhiều đối tượng OLE.

## Cách nhúng PDF vào Excel – Các yêu cầu trước
- **Java Development Kit (JDK) 8 trở lên** – đã được cài đặt và cấu hình trong IDE của bạn.  
- **GroupDocs.Merger cho Java** – thêm vào dự án của bạn qua Maven hoặc Gradle (xem bên dưới).  
- **Một IDE** như IntelliJ IDEA hoặc Eclipse để chỉnh sửa và chạy mã.  
- **Kiến thức cơ bản về xử lý tệp Java** – bạn sẽ làm việc với các đường dẫn tệp và luồng.

## Cài đặt GroupDocs.Merger cho Java

### Maven
Thêm phụ thuộc sau vào tệp `pom.xml` của bạn:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle
Bao gồm thư viện trong tệp `build.gradle` của bạn:

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

Bạn cũng có thể tải phiên bản mới nhất trực tiếp từ [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

#### Các bước lấy giấy phép
1. **Bản dùng thử:** Bắt đầu với bản dùng thử miễn phí để khám phá tất cả tính năng.  
2. **Giấy phép tạm thời:** Yêu cầu giấy phép tạm thời để thử nghiệm kéo dài.  
3. **Mua:** Nhận giấy phép đầy đủ cho triển khai thương mại.

## Triển khai từng bước

### Bước 1: Xác định đường dẫn tệp và khởi tạo đối tượng
Đầu tiên, thiết lập các đường dẫn cho workbook Excel của bạn, PDF muốn nhúng, và tệp đầu ra. Sau đó tạo `OleSpreadsheetOptions` mô tả vị trí mà đối tượng OLE sẽ xuất hiện.

```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OleSpreadsheetOptions;

public class ImportOLEToSpreadsheet {
    public static void main(String[] args) throws Exception {
        // Define the paths for input and output files.
        String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.xlsx";  // Excel file path
        String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf";  // PDF file to embed

        // Specify the output file path.
        String filePathOut = "YOUR_OUTPUT_DIRECTORY/ImportDocumentToSpreadsheet-output.xlsx";

        // Specify the page number of the OLE object and its position in the spreadsheet.
        int pageNumber = 2;  
        OleSpreadsheetOptions oleCellsOptions = new OleSpreadsheetOptions(embeddedFilePath, pageNumber);
        
        // Set the desired row and column indices for the OLE object placement.
        oleCellsOptions.setRowIndex(2); 
        oleCellsOptions.setColumnIndex(2);

        // Create a Merger instance for the target Excel file.
        Merger merger = new Merger(filePath);
    }
}
```

### Bước 2: Nhập tài liệu OLE
Sử dụng phương thức `importDocument` để nhúng PDF dưới dạng đối tượng OLE tại vị trí bạn đã xác định.

```java
// Import the OLE document into the specified position in the spreadsheet.
merger.importDocument(oleCellsOptions);

// Save the updated spreadsheet to the output path.
merger.save(filePathOut);
```

**Tại sao chúng ta dùng `importDocument`:** Phương thức này chỉ cho GroupDocs.Merger xử lý PDF như một đối tượng OLE, giữ nguyên nội dung gốc đồng thời cho phép truy cập từ trong Excel.

### Bước 3: Lưu bảng tính
Lưu các thay đổi vào một tệp mới để giữ nguyên workbook gốc không bị thay đổi.

```java
merger.save(filePathOut);
```

**Các tùy chọn cấu hình chính:** Bạn có thể tinh chỉnh thêm `OleSpreadsheetOptions`—ví dụ, điều chỉnh kích thước đối tượng, độ hiển thị, hoặc việc nó nên được liên kết thay vì nhúng.

## Những lỗi thường gặp & Mẹo khắc phục
- **FileNotFoundException:** Kiểm tra lại các đường dẫn bạn cung cấp để chắc chắn chúng trỏ tới các tệp tồn tại.  
- **Không khớp phiên bản:** Đảm bảo phiên bản GroupDocs.Merger bạn dùng tương thích với phiên bản JDK của bạn.  
- **PDF hỏng:** Kiểm tra PDF có mở được độc lập trước khi nhúng.  
- **Áp lực bộ nhớ:** Khi xử lý nhiều workbook, đóng mỗi instance `Merger` hoặc sử dụng try‑with‑resources để giải phóng tài nguyên.

## Ứng dụng thực tiễn
Nhúng các đối tượng OLE vào Excel hữu ích trong nhiều tình huống:
1. **Hợp nhất dữ liệu:** Gộp các PDF quý vào một workbook bảng điều khiển duy nhất.  
2. **Bài thuyết trình tương tác:** Cung cấp các bản mô tả chi tiết mở khi cần trong cuộc họp.  
3. **Báo cáo tự động:** Tạo báo cáo tài chính hàng tháng tự động bao gồm tài liệu hỗ trợ.

## Các lưu ý về hiệu năng
- **Quản lý bộ nhớ:** Đóng mọi instance `Merger` không còn cần để giải phóng tài nguyên.  
- **Xử lý hàng loạt:** Khi xử lý hàng chục bảng tính, thực hiện theo các lô nhỏ để tránh tăng đột biến bộ nhớ.  
- **Thực hành tốt trong Java:** Sử dụng try‑with‑resources cho các luồng và xử lý ngoại lệ một cách nhẹ nhàng.

## Kết luận
Bạn đã có một giải pháp hoàn chỉnh, sẵn sàng cho môi trường sản xuất để **nhúng PDF vào Excel** và **nhập tài liệu vào Excel** bằng GroupDocs.Merger cho Java. Hãy thử nghiệm với các loại tệp khác nhau, điều chỉnh các tùy chọn vị trí, và tích hợp quy trình này vào các pipeline báo cáo tự động của bạn.

### Các bước tiếp theo
- Thử nhúng tài liệu Word hoặc hình ảnh để xem API xử lý các định dạng khác như thế nào.  
- Khám phá các khả năng bổ sung của GroupDocs.Merger như tách, hợp nhất hoặc chuyển đổi tài liệu.

## Phần Câu hỏi thường gặp

**Q1: Tôi có thể nhúng nhiều đối tượng OLE trong một tệp Excel duy nhất không?**  
A1: Có, bạn có thể nhúng nhiều đối tượng OLE bằng cách lặp lại quy trình nhập cho mỗi đối tượng.

**Q2: Những định dạng tệp nào được hỗ trợ làm đối tượng OLE?**  
A2: GroupDocs.Merger hỗ trợ PDF, tài liệu Word, tệp Excel, hình ảnh và một số định dạng phổ biến khác.

**Q3: Làm thế nào để xử lý các tệp lớn một cách hiệu quả với GroupDocs.Merger?**  
A3: Tối ưu việc sử dụng bộ nhớ bằng cách xử lý tệp theo các lô nhỏ hơn và giải phóng các instance `Merger` kịp thời.

**Q4: Nếu tệp được nhúng không thể truy cập hoặc bị hỏng thì sao?**  
A4: Kiểm tra đường dẫn và tính toàn vẹn của tệp nguồn trước khi cố nhúng. Tệp hỏng sẽ gây ra ngoại lệ trong quá trình nhập.

**Q5: Tôi có thể tùy chỉnh giao diện của các đối tượng OLE trong Excel không?**  
A5: Có, `OleSpreadsheetOptions` cho phép bạn đặt chỉ số hàng/cột, kích thước và độ hiển thị để điều chỉnh cách đối tượng hiển thị trong worksheet.

## Tài nguyên

- **Tài liệu:** [GroupDocs.Merger for Java Documentation](https://docs.groupdocs.com/merger/java/)  
- **Tham khảo API:** [API Reference Guide](https://reference.groupdocs.com/merger/java/)  
- **Tải xuống:** [Latest Releases](https://releases.groupdocs.com/merger/java/)  
- **Mua:** [Buy GroupDocs.Merger for Java](https://purchase.groupdocs.com/buy)  
- **Dùng thử miễn phí:** [Start a Free Trial](https://releases.groupdocs.com/merger/java/)  
- **Giấy phép tạm thời:** [Request a Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Hỗ trợ:** [GroupDocs Forum](https://forum.groupdocs.com/c/merger/) 

---

**Cập nhật lần cuối:** 2026-03-17  
**Được kiểm tra với:** GroupDocs.Merger for Java latest-version  
**Tác giả:** GroupDocs