---
date: '2026-10-06'
description: Tìm hiểu cách nhúng PDF vào Excel và nhập tài liệu vào Excel bằng GroupDocs.Merger
  for Java. Tham khảo hướng dẫn chi tiết này với các ví dụ mã và mẹo khắc phục sự
  cố.
keywords:
- how to embed pdf excel
- GroupDocs Merger Java OLE
- embed PDF in Excel Java
lastmod: '2026-10-06'
og_description: Tìm hiểu cách nhúng PDF vào Excel với GroupDocs.Merger for Java. Hướng
  dẫn này trình bày mã từng bước, các yêu cầu trước, và mẹo để nhập đối tượng OLE
  thành công.
og_image_alt: Illustration of embedding a PDF as an OLE object in an Excel worksheet
  using Java
og_title: Cách nhúng PDF vào Excel bằng GroupDocs.Merger for Java
schemas:
- author: GroupDocs
  dateModified: '2026-10-06'
  description: Learn how to embed PDF in Excel and import a document into Excel with
    GroupDocs.Merger for Java. Follow this detailed guide with code examples and troubleshooting
    tips.
  headline: How to embed PDF in Excel using GroupDocs.Merger for Java – a step‑by‑step
    guide
  type: TechArticle
- description: Learn how to embed PDF in Excel and import a document into Excel with
    GroupDocs.Merger for Java. Follow this detailed guide with code examples and troubleshooting
    tips.
  name: How to embed PDF in Excel using GroupDocs.Merger for Java – a step‑by‑step
    guide
  steps:
  - name: define file paths and initialize objects
    text: First, set up the paths for your Excel workbook, the PDF you want to embed,
      and the output file. Then create the `OleSpreadsheetOptions` that describe where
      the OLE object will appear. **Definition anchor:** `OleSpreadsheetOptions` configures
      the target cell, size, and display properties of an OLE o
  - name: import the OLE document
    text: Use the `importDocument` method to embed the PDF as an OLE object at the
      location you defined. **Definition anchor:** `importDocument` tells GroupDocs.Merger
      to treat the supplied file as an OLE object, preserving its original binary
      content while linking it to the worksheet. **Why we use `importDoc
  - name: save the spreadsheet
    text: Persist the changes to a new file so you keep the original workbook untouched.
      **Key configuration options:** You can further tweak `OleSpreadsheetOptions`—for
      example, adjusting the object's size, visibility, or whether it should be linked
      rather than embedded.
  type: HowTo
- questions:
  - answer: Yes, repeat the `importDocument` call for each object, adjusting the `OleSpreadsheetOptions`
      to target different cells.
    question: Can I embed multiple OLE objects in a single Excel file?
  - answer: GroupDocs.Merger supports PDFs, Word documents, Excel files, images, and
      several other common formats—over **30+** types in total.
    question: What file formats are supported as OLE objects?
  - answer: Process files in smaller batches, use streaming APIs, and dispose of `Merger`
      instances promptly to keep memory usage low.
    question: How do I handle large files efficiently with GroupDocs.Merger?
  - answer: Verify the source file’s path and integrity before attempting to embed
      it. A corrupted file will raise an exception during import.
    question: What if the embedded file is not accessible or is corrupted?
  - answer: Yes, `OleSpreadsheetOptions` lets you set row/column indices, size, and
      visibility to tailor how the object looks in the worksheet.
    question: Can I customize the appearance of OLE objects in Excel?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- Java OLE object
- Excel integration
title: Cách nhúng PDF vào Excel bằng GroupDocs.Merger for Java – hướng dẫn chi tiết
  từng bước
type: docs
url: /vi/java/document-import/import-ole-object-excel-groupdocs-merger-java/
weight: 1
---

# Cách nhúng PDF vào Excel bằng GroupDocs.Merger cho Java

Việc nhúng PDF vào Excel có thể biến một bảng tính tĩnh thành một báo cáo phong phú, tương tác, chứa toàn bộ tài liệu nguồn ngay tại nơi bạn cần. Trong hướng dẫn này, bạn sẽ học **cách nhúng PDF vào Excel** bằng cách nhập một tệp PDF dưới dạng đối tượng OLE (Object Linking and Embedding) với GroupDocs.Merger cho Java. Chúng tôi sẽ đi qua mọi điều kiện tiên quyết, cho bạn thấy mã chính xác, và đưa ra các mẹo thực tế để bạn có thể bắt đầu sử dụng kỹ thuật này trong các dự án của mình ngay hôm nay.

## Câu trả lời nhanh
- **“embed PDF in Excel” có nghĩa là gì?** Nó có nghĩa là chèn một tệp PDF dưới dạng đối tượng OLE để PDF có thể được mở trực tiếp từ bảng tính.  
- **Thư viện nào xử lý việc nhập?** GroupDocs.Merger cho Java cung cấp phương thức `importDocument` cho mục đích này.  
- **Tôi có cần giấy phép không?** Bản dùng thử miễn phí đủ cho việc đánh giá; giấy phép thương mại là bắt buộc cho việc sử dụng trong môi trường sản xuất.  
- **Tôi có thể nhúng các loại tệp khác không?** Có – Word, hình ảnh và các định dạng được hỗ trợ khác cũng có thể được nhập dưới dạng đối tượng OLE.  
- **Phương pháp này có tương thích với Java 8+ không?** Hoàn toàn – thư viện hỗ trợ Java 8 và các phiên bản mới hơn.

## Nhúng PDF vào Excel là gì?
Việc nhúng PDF vào Excel lưu trữ PDF bên trong workbook dưới dạng đối tượng OLE, cho phép người dùng nhấp đúp vào biểu tượng và mở PDF gốc mà không rời khỏi bảng tính. Kỹ thuật này lý tưởng cho các chuỗi kiểm toán, báo cáo chi tiết, hoặc bất kỳ trường hợp nào bạn cần giữ tài liệu nguồn gắn chặt với dữ liệu tóm tắt.

## Tại sao nên nhúng PDF vào Excel bằng GroupDocs.Merger?
Việc nhúng các tệp PDF bằng GroupDocs.Merger loại bỏ việc sao chép‑dán thủ công và đảm bảo vị trí nhất quán trên hàng ngàn workbook. Thư viện hỗ trợ **hơn 30 định dạng đầu vào và đầu ra** và có thể xử lý workbook lên tới **500 MB** mà không cần tải toàn bộ tệp vào bộ nhớ, cung cấp tự động hoá nhanh chóng, tiết kiệm bộ nhớ cho các quy trình báo cáo quy mô lớn.

## Cách nhúng PDF vào Excel – các điều kiện tiên quyết
Trước khi bắt đầu viết mã, hãy đảm bảo môi trường phát triển của bạn đáp ứng các điều kiện sau. Bạn phải cài đặt JDK tương thích, thêm thư viện GroupDocs.Merger vào dự án, và có một IDE sẵn sàng để chỉnh sửa và chạy mã. Kiến thức về xử lý tệp Java cũng sẽ giúp bạn theo dõi các ví dụ một cách suôn sẻ.

- Java Development Kit (JDK) 8 hoặc cao hơn, đã được cài đặt và thêm vào `PATH` của bạn.  
- GroupDocs.Merger cho Java – thêm nó vào dự án của bạn qua Maven hoặc Gradle (xem các phần bên dưới).  
- Một IDE như IntelliJ IDEA hoặc Eclipse để chỉnh sửa và chạy mã.  
- Kiến thức cơ bản về xử lý tệp và stream trong Java.  

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

Bạn cũng có thể tải phiên bản mới nhất trực tiếp từ [Tài liệu GroupDocs.Merger cho Java](https://releases.groupdocs.com/merger/java/).

#### Các bước lấy giấy phép
1. **Free trial:** Bắt đầu với bản dùng thử miễn phí để khám phá tất cả các tính năng.  
2. **Temporary license:** Yêu cầu giấy phép tạm thời để thử nghiệm kéo dài.  
3. **Purchase:** Nhận giấy phép đầy đủ cho việc triển khai thương mại.  

## Triển khai từng bước

### Bước 1: xác định đường dẫn tệp và khởi tạo đối tượng
Đầu tiên, thiết lập các đường dẫn cho workbook Excel của bạn, PDF muốn nhúng, và tệp đầu ra. Sau đó tạo `OleSpreadsheetOptions` mô tả vị trí mà đối tượng OLE sẽ xuất hiện.

**Definition anchor:** `OleSpreadsheetOptions` cấu hình ô mục tiêu, kích thước và thuộc tính hiển thị của một đối tượng OLE trong worksheet Excel.  

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

### Bước 2: nhập tài liệu OLE
Sử dụng phương thức `importDocument` để nhúng PDF dưới dạng đối tượng OLE tại vị trí bạn đã định nghĩa.

**Definition anchor:** `importDocument` chỉ cho GroupDocs.Merger xử lý tệp được cung cấp như một đối tượng OLE, giữ nguyên nội dung nhị phân gốc trong khi liên kết nó với worksheet.  

```java
// Import the OLE document into the specified position in the spreadsheet.
merger.importDocument(oleCellsOptions);

// Save the updated spreadsheet to the output path.
merger.save(filePathOut);
```

**Why we use `importDocument`:** Phương thức này đảm bảo PDF vẫn hoạt động đầy đủ khi mở từ Excel, tự động xử lý việc đóng gói nhị phân và siêu dữ liệu quan hệ cần thiết.

### Bước 3: lưu bảng tính
Lưu các thay đổi vào một tệp mới để giữ nguyên workbook gốc.

```java
merger.save(filePathOut);
```

**Key configuration options:** Bạn có thể tinh chỉnh thêm `OleSpreadsheetOptions`—ví dụ, điều chỉnh kích thước, hiển thị, hoặc việc nó nên được liên kết thay vì nhúng.

## Các lỗi thường gặp & mẹo khắc phục
- **FileNotFoundException:** Kiểm tra lại các đường dẫn bạn cung cấp để chắc chắn chúng trỏ tới các tệp tồn tại.  
- **Version mismatch:** Đảm bảo phiên bản GroupDocs.Merger bạn dùng phù hợp với phiên bản JDK của bạn.  
- **Corrupt PDF:** Xác minh PDF mở độc lập trước khi nhúng.  
- **Memory pressure:** Khi xử lý nhiều workbook, đóng nhanh mỗi instance của `Merger` hoặc sử dụng try‑with‑resources để giải phóng tài nguyên.  

## Ứng dụng thực tiễn
Embedding OLE objects in Excel is useful in many scenarios:
1. **Data consolidation:** Hợp nhất các PDF quý thành một workbook bảng điều khiển duy nhất.  
2. **Interactive presentations:** Cung cấp các bản mô tả chi tiết mở theo yêu cầu trong cuộc họp.  
3. **Automated reporting:** Tạo báo cáo tài chính hàng tháng tự động bao gồm tài liệu hỗ trợ.  

## Các lưu ý về hiệu năng
- **Memory management:** Đóng bất kỳ instance `Merger` nào không còn cần để giải phóng tài nguyên.  
- **Batch processing:** Khi xử lý hàng chục bảng tính, xử lý chúng theo các lô nhỏ để tránh tăng đột biến bộ nhớ.  
- **Java best practices:** Sử dụng try‑with‑resources cho streams và xử lý ngoại lệ một cách nhẹ nhàng.  

## Kết luận
Bạn giờ đã có một giải pháp hoàn chỉnh, sẵn sàng cho môi trường sản xuất để **nhúng PDF vào Excel** và **nhập tài liệu vào Excel** bằng GroupDocs.Merger cho Java. Thử nghiệm với các loại tệp khác nhau, điều chỉnh các tùy chọn vị trí, và tích hợp quy trình này vào các pipeline báo cáo tự động của bạn.

### Các bước tiếp theo
- Thử nhúng tài liệu Word hoặc hình ảnh để xem API xử lý các định dạng khác như thế nào.  
- Khám phá các khả năng bổ sung của GroupDocs.Merger như tách, hợp nhất, hoặc chuyển đổi tài liệu.  

## Câu hỏi thường gặp

**Q: Bạn có thể nhúng nhiều đối tượng OLE trong một tệp Excel duy nhất không?**  
A: Có, lặp lại lời gọi `importDocument` cho mỗi đối tượng, điều chỉnh `OleSpreadsheetOptions` để nhắm tới các ô khác nhau.

**Q: Các định dạng tệp nào được hỗ trợ làm đối tượng OLE?**  
A: GroupDocs.Merger hỗ trợ PDF, tài liệu Word, tệp Excel, hình ảnh và một số định dạng phổ biến khác—hơn **30+** loại tổng cộng.

**Q: Làm thế nào để xử lý các tệp lớn một cách hiệu quả với GroupDocs.Merger?**  
A: Xử lý tệp theo các lô nhỏ hơn, sử dụng API streaming, và giải phóng các instance `Merger` kịp thời để giữ mức sử dụng bộ nhớ thấp.

**Q: Nếu tệp được nhúng không thể truy cập hoặc bị hỏng thì sao?**  
A: Xác minh đường dẫn và tính toàn vẹn của tệp nguồn trước khi cố gắng nhúng. Tệp bị hỏng sẽ gây ra ngoại lệ trong quá trình nhập.

**Q: Tôi có thể tùy chỉnh giao diện của các đối tượng OLE trong Excel không?**  
A: Có, `OleSpreadsheetOptions` cho phép bạn đặt chỉ số hàng/cột, kích thước và hiển thị để điều chỉnh cách đối tượng hiển thị trong worksheet.  

## Tài nguyên

- **Tài liệu:** [Tài liệu GroupDocs.Merger cho Java](https://docs.groupdocs.com/merger/java/)
- **Tham khảo API:** [Hướng dẫn Tham khảo API](https://reference.groupdocs.com/merger/java/)
- **Tải xuống:** [Bản phát hành mới nhất](https://releases.groupdocs.com/merger/java/)
- **Mua:** [Mua GroupDocs.Merger cho Java](https://purchase.groupdocs.com/buy)
- **Dùng thử miễn phí:** [Bắt đầu Dùng thử Miễn phí](https://releases.groupdocs.com/merger/java/)
- **Giấy phép tạm thời:** [Yêu cầu Giấy phép Tạm thời](https://purchase.groupdocs.com/temporary-license/)
- **Hỗ trợ:** [Diễn đàn GroupDocs](https://forum.groupdocs.com/c/merger/) 

---

**Cập nhật lần cuối:** 2026-10-06  
**Đã kiểm tra với:** GroupDocs.Merger cho Java phiên bản mới nhất  
**Tác giả:** GroupDocs

## Hướng dẫn liên quan

- [Nhúng Đối tượng Ole Ppt Java Groupdocs Merger](/merger/java/document-import/embed-ole-object-ppt-java-groupdocs-merger/)
- [Cách nhúng pdf vào word bằng GroupDocs.Merger cho Java – Hướng dẫn Toàn diện](/merger/java/document-import/embed-ole-objects-word-documents-groupdocs-java/)
- [Merge PDF Java: Tải Tài liệu Cục bộ Sử dụng GroupDocs.Merger – Hướng dẫn](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)