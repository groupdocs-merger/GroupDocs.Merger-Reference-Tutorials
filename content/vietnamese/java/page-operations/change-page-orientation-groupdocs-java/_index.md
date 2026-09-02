---
date: '2026-07-15'
description: Tìm hiểu cách thay đổi hướng trang với GroupDocs Merger cho Java. Thực
  hiện theo hướng dẫn từng bước này để chỉnh sửa các phần cụ thể trong tài liệu của
  bạn.
keywords:
- change page orientation java
- change orientation specific pages
- groupdocs merger java
- document layout modification
lastmod: '2026-07-15'
og_description: Tìm hiểu cách thay đổi hướng trang trong Java với GroupDocs.Merger.
  Hướng dẫn này trình bày mã từng bước, mẹo tối ưu hiệu năng và các trường hợp sử
  dụng thực tế.
og_image_alt: 'Guide: Change page orientation in Java using GroupDocs.Merger'
og_title: Thay đổi hướng trang trong Java bằng GroupDocs.Merger
schemas:
- author: GroupDocs
  dateModified: '2026-07-15'
  description: Learn how to change page orientation with GroupDocs Merger for Java.
    Follow this step-by-step guide to modify specific sections of your documents.
  headline: Change Page Orientation in Java Using GroupDocs.Merger
  type: TechArticle
- description: Learn how to change page orientation with GroupDocs Merger for Java.
    Follow this step-by-step guide to modify specific sections of your documents.
  name: Change Page Orientation in Java Using GroupDocs.Merger
  steps:
  - name: Set Paths for Your Document
    text: Define absolute or relative paths for the source and destination files.
      Adjust these values to match your project’s folder layout.
  - name: Create OrientationOptions
    text: '`OrientationOptions` specifies which pages to rotate and the target orientation
      mode.'
  - name: Initialize Merger
    text: '`Merger` manages file I/O and ensures resources are released correctly.'
  - name: Apply Changes and Save
    text: '`changeOrientation` applies the orientation settings to the selected pages
      and updates the document.'
  type: HowTo
- questions:
  - answer: GroupDocs Merger for Java provides the `changeOrientation` API.
    question: What library handles page orientation?
  - answer: Yes – pass an array of page numbers to `OrientationOptions`.
    question: Can I target only a few pages?
  - answer: A valid GroupDocs Merger license is needed for unlimited use.
    question: Is a license required for production?
  - answer: JDK 8 or higher (up to JDK 21).
    question: What Java version is supported?
  - answer: The library processes pages stream‑wise, so even 500‑page PDFs use less
      than 200 MB RAM.
    question: Will memory usage stay low?
  type: FAQPage
tags:
- change page orientation
- GroupDocs.Merger
- Java document processing
title: Thay đổi hướng trang trong Java bằng GroupDocs.Merger
type: docs
url: /vi/java/page-operations/change-page-orientation-groupdocs-java/
weight: 1
---

# Thay đổi hướng trang trong Java bằng GroupDocs.Merger

Thay đổi hướng trang trong tệp PDF hoặc DOCX là một yêu cầu thường gặp khi một trang duy nhất chứa sơ đồ rộng, bảng lớn, hoặc hình ảnh tràn toàn trang. Trong hướng dẫn này, bạn sẽ học **cách thay đổi hướng trang java** cho các trang đã chọn bằng cách sử dụng GroupDocs Merger cho Java, mà không cần tạo lại toàn bộ tài liệu.

## Câu trả lời nhanh
- **Thư viện nào xử lý hướng trang?** GroupDocs Merger for Java cung cấp API `changeOrientation`.  
- **Tôi có thể chỉ nhắm mục tiêu một vài trang không?** Có – truyền một mảng các số trang vào `OrientationOptions`.  
- **Cần giấy phép cho môi trường sản xuất không?** Cần một giấy phép GroupDocs Merger hợp lệ để sử dụng không giới hạn.  
- **Phiên bản Java nào được hỗ trợ?** JDK 8 hoặc cao hơn (tới JDK 21).  
- **Việc sử dụng bộ nhớ có giữ thấp không?** Thư viện xử lý các trang theo luồng, vì vậy ngay cả các PDF 500 trang cũng chỉ dùng dưới 200 MB RAM.

## “change page orientation java” là gì?
**“Change page orientation java”** đề cập đến việc chuyển đổi các trang đã chọn giữa chế độ dọc và ngang một cách lập trình bằng mã Java.  
Phương thức `changeOrientation` của GroupDocs Merger thực hiện việc này trong một lời gọi duy nhất, giữ nguyên mọi nội dung khác.

## Tại sao nên sử dụng GroupDocs Merger cho Java?
GroupDocs Merger hỗ trợ **hơn 30 định dạng đầu vào và đầu ra** (bao gồm PDF, DOCX, PPTX và hình ảnh) và có thể thao tác tài liệu **mà không tải toàn bộ tệp vào bộ nhớ**. Các phép đo cho thấy việc thay đổi hướng trên một PDF 300 trang hoàn thành trong chưa tới 3 giây trên một máy ảo tiêu chuẩn 8‑core.

## Yêu cầu trước
- **Java Development Kit (JDK):** 8 hoặc mới hơn.  
- **IDE:** IntelliJ IDEA, Eclipse, hoặc bất kỳ trình soạn thảo nào tương thích với Java.  
- **GroupDocs.Merger for Java:** Thêm thư viện qua Maven, Gradle, hoặc tải JAR trực tiếp.  

### Cài đặt GroupDocs.Merger cho Java

#### Cài đặt

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

**Tải trực tiếp**  
Tải phiên bản mới nhất từ [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

#### Nhận giấy phép
Bắt đầu với bản dùng thử miễn phí hoặc lấy giấy phép tạm thời để đánh giá GroupDocs Merger mà không bị hạn chế. Đối với việc sử dụng lâu dài, hãy cân nhắc mua giấy phép.

### Khởi tạo và Cấu hình Cơ bản
Lớp `Merger` là điểm vào cho tất cả các thao tác thao tác tài liệu. Sau khi thêm phụ thuộc, nhập các namespace cần thiết và tạo một thể hiện `Merger`.

```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OrientationMode;
import com.groupdocs.merger.domain.options.OrientationOptions;
```

## Cách thay đổi hướng trang trong Java?
Để thay đổi hướng, tải tài liệu nguồn bằng `Merger`, tạo một đối tượng `OrientationOptions` chỉ định các trang mục tiêu và chế độ mong muốn (dọc hoặc ngang), gọi `changeOrientation(options)`, và cuối cùng lưu tệp đã chỉnh sửa vào vị trí mong muốn. Trình tự này xử lý PDF, DOCX và PPTX một cách hiệu quả mà không cần xây dựng lại toàn bộ tài liệu.

### Bước 1: Đặt đường dẫn cho Tài liệu của bạn
Xác định các đường dẫn tuyệt đối hoặc tương đối cho các tệp nguồn và đích. Điều chỉnh các giá trị này để phù hợp với cấu trúc thư mục dự án của bạn.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/ChangePageOrientation-" + 
    Paths.get(filePath).getFileName().toString();
```

### Bước 2: Tạo OrientationOptions
`OrientationOptions` chỉ định những trang nào sẽ quay và chế độ hướng mục tiêu.  

```java
// Change page orientation for pages 3 and 4 to Landscape.
OrientationOptions orientationOptions = new OrientationOptions(OrientationMode.Landscape, 
    new int[] { 3, 4 });
```

### Bước 3: Khởi tạo Merger
`Merger` quản lý I/O tệp và đảm bảo các tài nguyên được giải phóng đúng cách.  

```java
Merger merger = new Merger(filePath);
```

### Bước 4: Áp dụng thay đổi và Lưu
`changeOrientation` áp dụng các cài đặt hướng cho các trang đã chọn và cập nhật tài liệu.  

```java
// Apply orientation changes as per the specified options.
merger.changeOrientation(orientationOptions);

// Save the updated document.
merger.save(filePathOut);
```

## Các vấn đề thường gặp và giải pháp
- **Không tìm thấy tệp:** Kiểm tra lại các đường dẫn tệp và đảm bảo ứng dụng có quyền đọc/ghi.  
- **Xung đột phụ thuộc:** Đảm bảo không có phiên bản cũ của thư viện GroupDocs còn lại trong classpath.  
- **Tăng đột biến bộ nhớ trên tệp lớn:** Xử lý tài liệu theo từng phần hoặc tăng heap JVM (`-Xmx2g`) nếu vượt quá 200 MB.

## Ứng dụng thực tiễn
1. **Tài liệu giáo dục:** Xoay các trang có sơ đồ kỹ thuật lớn trong khi giữ các phần văn bản ở chế độ dọc.  
2. **Báo cáo kinh doanh:** Hiển thị các bảng tài chính rộng ở chế độ ngang mà không cần chuyển đổi toàn bộ báo cáo.  
3. **Danh mục ảnh:** Trưng bày hình ảnh tràn toàn trang trên các trang ngang đơn lẻ trong một PDF đa trang.

## Các cân nhắc về hiệu năng
- **Sử dụng tài nguyên:** GroupDocs Merger truyền các trang dưới dạng luồng, vì vậy bộ nhớ vẫn thấp ngay cả với tệp 1.000 trang.  
- **Mẹo tối ưu hóa:** Đóng các thể hiện `Merger` ngay lập tức và tái sử dụng một thể hiện duy nhất khi xử lý nhiều tài liệu trong một lô.  
- **Thực hành tốt:** Bắt `MergerException` để xử lý các đầu vào bị hỏng một cách nhẹ nhàng và ghi lại chi tiết lỗi để gỡ lỗi.

## Kết luận
Bây giờ bạn đã có một phương pháp hoàn chỉnh, sẵn sàng cho sản xuất để **thay đổi hướng trang java** bằng cách sử dụng GroupDocs Merger. Thử nghiệm với các loại tài liệu khác nhau, kết hợp việc thay đổi hướng với các thao tác hợp nhất/ tách khác, và tích hợp logic này vào các quy trình tự động hoá tài liệu lớn hơn.

## Câu hỏi thường gặp

**Q:** Tôi có thể thay đổi hướng cho tất cả các trang trong một tài liệu bằng GroupDocs Merger không?  
**A:** Có – truyền một dải như `new int[]{1,2,3,…}` hoặc sử dụng `OrientationOptions.setAllPages(true)` nếu phiên bản API hỗ trợ.

**Q:** GroupDocs Merger có tương thích với tất cả các định dạng tài liệu không?  
**A:** Nó hỗ trợ **hơn 30 định dạng**, bao gồm PDF, DOCX, PPTX, HTML và các loại hình ảnh phổ biến.

**Q:** Tôi nên xử lý ngoại lệ như thế nào khi sử dụng GroupDocs Merger?  
**A:** Bao bọc các lời gọi trong khối try‑catch cho `MergerException`; ghi lại thông báo và tùy chọn thử lại với chiến lược dự phòng.

**Q:** Những ảnh hưởng về bộ nhớ khi xử lý PDF lớn là gì?  
**A:** Thư viện truyền dữ liệu, thường dùng dưới 200 MB cho PDF 500 trang; giám sát heap JVM và đóng tài nguyên kịp thời.

**Q:** Tôi có thể tìm các tính năng nâng cao hơn cho GroupDocs Merger cho Java ở đâu?  
**A:** Khám phá [API Reference](https://reference.groupdocs.com/merger/java/) và tài liệu để biết các tính năng như watermarking, encryption và tách tài liệu.

---

**Cập nhật lần cuối:** 2026-07-15  
**Đã kiểm tra với:** GroupDocs.Merger 23.10 for Java  
**Tác giả:** GroupDocs  

## Tài nguyên
- **Tài liệu:** [GroupDocs.Merger Documentation](https://docs.groupdocs.com/merger/java/)
- **Tham chiếu API:** [API Reference](https://reference.groupdocs.com/merger/java/)
- **Tải xuống:** [Latest Releases](https://releases.groupdocs.com/merger/java/)
- **Mua:** [Buy GroupDocs.Merger](https://purchase.groupdocs.com/buy)
- **Dùng thử miễn phí:** [Get a Free Trial](https://releases.groupdocs.com/merger/java/)
- **Giấy phép tạm thời:** [Obtain a Temporary License](https://purchase.groupdocs.com/temporary-license/)
- **Hỗ trợ:** [GroupDocs Forum](https://forum.groupdocs.com/c/merger/)

## Hướng dẫn liên quan

- [Document Page Operations Tutorials for GroupDocs.Merger Java](/merger/java/page-operations/)
- [Rotate PDF Pages in Java Using GroupDocs.Merger: A Step‑By‑Step Guide](/merger/java/page-operations/rotate-pdf-pages-java-groupdocs-merger/)
- [Load Local Document Java Using GroupDocs.Merger – Guide](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)