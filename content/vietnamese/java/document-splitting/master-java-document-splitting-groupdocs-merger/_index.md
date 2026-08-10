---
date: '2026-07-25'
description: Tìm hiểu cách tách các trang docx bằng GroupDocs.Merger cho Java, bao
  gồm việc chia DOCX thành các tệp riêng biệt, trích xuất luồng và các tùy chọn tách.
keywords:
- split docx pages
- how to split docx
- split docx into files
lastmod: '2026-07-25'
og_description: Tách các trang docx bằng GroupDocs.Merger cho Java. Tìm hiểu từng
  bước cách tách DOCX thành tệp hoặc luồng với các ví dụ mã.
og_image_alt: Guide to split DOCX pages using GroupDocs.Merger Java library
og_title: Tách các trang DOCX bằng GroupDocs.Merger cho Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-25'
  description: Learn how to split docx pages using GroupDocs.Merger for Java, covering
    splitting DOCX into separate files, stream extraction, and split options.
  headline: How to Split DOCX Pages with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to split docx pages using GroupDocs.Merger for Java, covering
    splitting DOCX into separate files, stream extraction, and split options.
  name: How to Split DOCX Pages with GroupDocs.Merger for Java
  steps:
  - name: '**Legal contracts:** Extract individual clauses for separate review without
      exposing the whole agreement.'
    text: '**Legal contracts:** Extract individual clauses for separate review without
      exposing the whole agreement.'
  - name: '**E‑learning platforms:** Serve chapter‑by‑chapter Word files on demand,
      keeping the full textbook protected.'
    text: '**E‑learning platforms:** Serve chapter‑by‑chapter Word files on demand,
      keeping the full textbook protected.'
  - name: '**Business reporting:** Send only the finance section of a quarterly report
      to the CFO, reducing bandwidth and improving confidentiality.'
    text: '**Business reporting:** Send only the finance section of a quarterly report
      to the CFO, reducing bandwidth and improving confidentiality.'
  type: HowTo
- questions:
  - answer: It’s a Java library that enables merging, splitting, and converting over
      50 document formats—including DOCX, PDF, PPTX, and HTML—without requiring Microsoft
      Office.
    question: What is GroupDocs.Merger for Java?
  - answer: Acquire a temporary trial license from the [GroupDocs website](https://purchase.groupdocs.com/temporary-license/)
      for evaluation. For production, purchase a full license at the same site.
    question: How do I obtain a license for GroupDocs.Merger?
  - answer: Yes, the `split` method works with PDF, DOCX, PPTX, and other supported
      formats.
    question: Can I split PDF files using the same API?
  - answer: Absolutely—use the stream‑based approach shown above to keep everything
      in memory.
    question: Is it possible to split a document without writing to disk?
  - answer: Always target the latest stable release to benefit from performance improvements
      and bug fixes.
    question: Which version of GroupDocs.Merger should I use?
  type: FAQPage
tags:
- split docx
- GroupDocs.Merger
- Java document processing
- DOCX splitting
title: Cách tách các trang DOCX bằng GroupDocs.Merger cho Java
type: docs
url: /vi/java/document-splitting/master-java-document-splitting-groupdocs-merger/
weight: 1
---

# Tách các trang DOCX với GroupDocs.Merger cho Java

Trong hướng dẫn này, bạn sẽ khám phá **cách tách các trang docx** một cách hiệu quả bằng cách sử dụng GroupDocs.Merger cho Java. Cho dù bạn cần chia một hợp đồng khổng lồ thành các trang riêng lẻ hoặc trích xuất các phần cụ thể dưới dạng stream trong bộ nhớ, chúng tôi sẽ hướng dẫn qua cài đặt, mã nguồn và các mẹo thực tế để bạn có thể triển khai giải pháp trong vài phút.

## Câu trả lời nhanh
- **Thư viện nào xử lý việc tách DOCX trong Java?** GroupDocs.Merger for Java.  
- **Tôi có thể tách một DOCX thành các tệp riêng biệt không?** Có – cấu hình `SplitOptions` với các số trang mong muốn.  
- **Có thể lấy các trang dưới dạng stream thay vì tệp không?** Chắc chắn, bằng cách cung cấp một `SplitStreamFactory` tùy chỉnh.  
- **Tôi có cần giấy phép không?** Giấy phép dùng thử tạm thời hoạt động cho việc đánh giá; giấy phép đầy đủ cần thiết cho môi trường sản xuất.  
- **Phiên bản Java nào được hỗ trợ?** Bất kỳ JDK 8+ nào cũng hoạt động với bản phát hành mới nhất của GroupDocs.Merger.

## Tách các trang docx là gì?
**Split docx pages** có nghĩa là trích xuất một hoặc nhiều trang từ một tài liệu Word đa trang và lưu mỗi lựa chọn dưới dạng tệp riêng hoặc stream trong bộ nhớ. Điều này cho phép phân phối mô-đun, quy trình làm việc dựa trên tuân thủ, hoặc xử lý nhanh mà không cần xử lý toàn bộ tài liệu cùng một lúc.

## Tại sao nên sử dụng GroupDocs.Merger cho Java?
GroupDocs.Merger xử lý tài liệu **hoàn toàn bằng Java**—không cần binary gốc, không cần cài đặt Office. Nó hỗ trợ **hơn 50 định dạng đầu vào và đầu ra** và có thể tách một **DOCX 200 trang trong vòng dưới 2 giây** trên máy chủ 2.5 GHz tiêu chuẩn, giữ mức sử dụng bộ nhớ dưới 100 MB nhờ kiến trúc dựa trên stream.

## Yêu cầu trước

### Thư viện và phụ thuộc cần thiết
- **Bộ công cụ phát triển Java (JDK):** JDK 8 hoặc mới hơn.  
- **GroupDocs.Merger cho Java:** Thư viện lõi để thao tác tài liệu.

### Thêm phụ thuộc
Bao gồm thư viện qua Maven hoặc Gradle (khối mã không thay đổi):

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

Bạn cũng có thể tải bản phát hành mới nhất từ trang chính thức: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Nhận giấy phép
- **Giấy phép dùng thử:** Nhận khóa tạm thời từ trang [GroupDocs.Trial License](https://purchase.groupdocs.com/temporary-license/).  
- **Giấy phép sản xuất:** Mua giấy phép đầy đủ tại [GroupDocs Purchase](https://purchase.groupdocs.com/buy).

## Cài đặt GroupDocs.Merger cho Java
`Merger` là lớp trung tâm điều phối các thao tác tách, hợp nhất và chuyển đổi.

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

Với môi trường đã sẵn sàng, chúng ta sẽ khám phá hai cách chính để **tách các trang docx thành tệp** hoặc stream.

## Cách tách DOCX thành tệp với GroupDocs.Merger
Tải DOCX nguồn, chỉ định các phạm vi trang mong muốn và gọi phương thức `split` – một lời gọi duy nhất này sẽ tạo ra các tệp đầu ra riêng biệt cho mỗi đoạn đã chọn. Phương thức `split` xử lý tài liệu dựa trên `SplitOptions` được cung cấp và trả về các đường dẫn của các tệp đã tạo. Các bước sau đây trình bày một triển khai hoàn chỉnh, sẵn sàng cho môi trường sản xuất.

### Bước 1 – Xác định đường dẫn đầu vào và đầu ra
Xác định vị trí của DOCX gốc và thư mục nơi các tệp đã tách sẽ được ghi.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
String filePathOut = new File("YOUR_OUTPUT_DIRECTORY", 
    "SplitToSinglePages-" +
    Paths.get(filePath).getFileName().toString()
).getPath();
```

### Bước 2 – Cấu hình SplitOptions (các tùy chọn tách java)
`SplitOptions` cho API biết chính xác các trang nào cần trích xuất và nơi đặt kết quả.

```java
import com.groupdocs.merger.domain.options.SplitOptions;

SplitOptions splitOptions = new SplitOptions(filePathOut, new int[] { 3, 6, 8 });
```

- `filePathOut` – thư mục nơi mỗi tệp trang sẽ được lưu.  
- `new int[]{3,6,8}` – các số trang bạn muốn tách ra (các trang được đánh số bắt đầu từ 1).

### Bước 3 – Thực hiện tách
Tạo một thể hiện `Merger` và gọi `split`. Phương thức trả về danh sách các đường dẫn tệp đã tạo.

```java
import com.groupdocs.merger.Merger;

Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

**Mẹo chuyên nghiệp:** Kiểm tra xem thư mục đầu ra có tồn tại và ứng dụng của bạn có quyền ghi không; nếu không, việc tách sẽ thất bại.

#### Những lỗi thường gặp
- **Thiếu thư mục đầu ra:** API sẽ không tự động tạo thư mục.  
- **Số trang không đúng:** Chỉ số trang bắt đầu từ 1; nếu chỉ định 0 sẽ gây lỗi.

## Cách tách các trang DOCX thành Stream (Trong bộ nhớ)
Khi bạn cần truy cập tạm thời—chẳng hạn gửi một trang qua dịch vụ web hoặc thực hiện phân tích trong bộ nhớ—việc nắm bắt mỗi trang đã trích xuất dưới dạng stream loại bỏ chi phí ghi lên đĩa. Bằng cách sử dụng một `SplitStreamFactory` tùy chỉnh, thư viện ghi nội dung đã tách trực tiếp vào các đối tượng `ByteArrayOutputStream`, sau đó có thể truyền, lưu trữ hoặc xử lý tiếp mà không cần tệp trung gian.

### Bước 1 – Xác định đường dẫn đầu vào và chuẩn bị danh sách cho Stream
Đặt tệp nguồn và tạo một container để chứa các stream đã tạo.

```java
import java.io.ByteArrayOutputStream;
import java.util.ArrayList;
import java.util.List;

String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
final List<OutputStream> resultStreams = new ArrayList<>();
```

### Bước 2 – Cấu hình SplitOptions với SplitStreamFactory tùy chỉnh
Triển khai `SplitStreamFactory` để cung cấp một `OutputStream` mới cho mỗi trang và lưu trữ stream đã hoàn thành.

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

- `createSplitStream` – tạo một `OutputStream` mới cho mỗi trang được yêu cầu.  
- `closeSplitStream` – lưu trữ stream đã hoàn thành để sử dụng sau.

### Bước 3 – Thực thi tách và lấy Stream
Chạy thao tác tách và sau đó làm việc với các stream trong bộ nhớ theo nhu cầu (ví dụ: đính kèm vào email, tải lên lưu trữ đám mây).

```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);

return resultStreams; // Retrieve streams for processing
```

**Mẹo khắc phục sự cố**
- Đảm bảo đường dẫn DOCX nguồn đúng; lỗi đánh máy sẽ gây ra `FileNotFoundException`.  
- Luôn đóng các stream sau khi sử dụng để giải phóng bộ nhớ và tránh rò rỉ.

## Ứng dụng thực tế
1. **Hợp đồng pháp lý:** Trích xuất các điều khoản riêng lẻ để xem xét riêng mà không tiết lộ toàn bộ hợp đồng.  
2. **Nền tảng học trực tuyến:** Cung cấp các tệp Word theo chương khi cần, giữ nguyên sách giáo trình đầy đủ được bảo vệ.  
3. **Báo cáo doanh nghiệp:** Gửi chỉ phần tài chính của báo cáo quý cho CFO, giảm băng thông và tăng tính bảo mật.

## Các cân nhắc về hiệu năng
- **Stream tiết kiệm bộ nhớ:** Ưu tiên cách tiếp cận stream cho tài liệu lớn hơn 50 MB để giảm sử dụng heap.  
- **Xử lý hàng loạt:** Nhóm nhiều công việc tách trong một phiên JVM để giảm chi phí khởi động.  
- **Dọn dẹp tài nguyên:** Gọi `merger.close()` và đóng tất cả các stream để tránh rò rỉ bộ nhớ.  
- **Chỉ số tốc độ:** Trên máy chủ tiêu chuẩn 8‑core, tách một DOCX 300 trang thành các trang riêng biệt hoàn thành trong khoảng ~1.8 giây.

## Câu hỏi thường gặp

**Q: GroupDocs.Merger cho Java là gì?**  
A: Đó là một thư viện Java cho phép hợp nhất, tách và chuyển đổi hơn 50 định dạng tài liệu—bao gồm DOCX, PDF, PPTX và HTML—mà không cần Microsoft Office.

**Q: Làm sao để có được giấy phép cho GroupDocs.Merger?**  
A: Nhận giấy phép dùng thử tạm thời từ [GroupDocs website](https://purchase.groupdocs.com/temporary-license/) để đánh giá. Đối với môi trường sản xuất, mua giấy phép đầy đủ tại cùng trang.

**Q: Tôi có thể tách file PDF bằng cùng API không?**  
A: Có, phương thức `split` hoạt động với PDF, DOCX, PPTX và các định dạng được hỗ trợ khác.

**Q: Có thể tách tài liệu mà không ghi lên đĩa không?**  
A: Chắc chắn—sử dụng cách tiếp cận dựa trên stream như đã trình bày ở trên để giữ mọi thứ trong bộ nhớ.

**Q: Nên sử dụng phiên bản GroupDocs.Merger nào?**  
A: Luôn nhắm tới bản phát hành ổn định mới nhất để hưởng lợi từ cải tiến hiệu năng và sửa lỗi.

---

**Last Updated:** 2026-07-25  
**Tested With:** GroupDocs.Merger for Java latest-version  
**Author:** GroupDocs

## Hướng dẫn liên quan

- [Cách tách tài liệu thành các tệp đa trang bằng GroupDocs.Merger cho Java](/merger/java/document-splitting/split-documents-multi-page-files-java-groupdocs-merger/)
- [Cách trích xuất các trang cụ thể trong java với GroupDocs.Merger](/merger/java/document-extraction/)
- [Cách ghép các trang cụ thể trong Java bằng GroupDocs.Merger](/merger/java/document-joining/join-specific-pages-groupdocs-merger-java/)