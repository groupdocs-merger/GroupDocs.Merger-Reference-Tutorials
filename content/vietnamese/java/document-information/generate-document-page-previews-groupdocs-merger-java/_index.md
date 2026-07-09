---
date: '2026-06-26'
description: Tìm hiểu cách chuyển đổi các trang pdf thành hình ảnh và xem trước tài
  liệu bằng cách sử dụng GroupDocs.Merger cho Java – cách nhanh chóng, đáng tin cậy
  để tạo ảnh thu nhỏ của trang.
keywords:
- convert pdf pages to images
- document page previews
- GroupDocs.Merger Java
schemas:
- author: GroupDocs
  dateModified: '2026-06-26'
  description: Learn how to convert pdf pages to images and preview documents using
    GroupDocs.Merger for Java – the fast, reliable way to generate page thumbnails.
  headline: How to Convert PDF Pages to Images and Preview Documents with GroupDocs.Merger
    for Java
  type: TechArticle
- questions:
  - answer: It’s used for merging, splitting, and managing documents efficiently,
      including preview generation and format conversion.
    question: What is GroupDocs.Merger for Java used for?
  - answer: Wrap stream creation and closing in try‑catch blocks, as shown in the
      helper methods, to prevent memory leaks.
    question: How do I handle exceptions during stream operations?
  - answer: Yes, change the `PreviewMode` enum to PNG, BMP, or TIFF to suit your requirements.
    question: Can I generate previews in formats other than JPEG?
  - answer: Typical problems include incorrect file paths and forgetting to close
      streams, which can cause memory leaks.
    question: What are common issues with document preview generation?
  - answer: Use its API to connect with databases, web services, or other Java applications
      for seamless workflow automation.
    question: How can I integrate GroupDocs.Merger with other systems?
  type: FAQPage
title: Cách chuyển đổi các trang PDF thành hình ảnh và xem trước tài liệu với GroupDocs.Merger
  cho Java
type: docs
url: /vi/java/document-information/generate-document-page-previews-groupdocs-merger-java/
weight: 1
---

# Cách Chuyển Đổi Các Trang PDF Thành Hình Ảnh và Xem Trước Tài Liệu với GroupDocs.Merger cho Java

## Câu trả lời nhanh
- **“preview documents” có nghĩa là gì?** Tạo các biểu diễn hình ảnh nhẹ cho mỗi trang.  
- **Định dạng nào được sử dụng cho preview?** JPEG theo mặc định, nhưng các định dạng khác cũng được hỗ trợ.  
- **Tôi có cần giấy phép không?** Bản dùng thử miễn phí hoạt động cho phát triển; giấy phép trả phí cần thiết cho môi trường sản xuất.  
- **Tôi có thể tùy chỉnh đường dẫn đầu ra không?** Có, bằng cách triển khai một `PageStreamFactory` tùy chỉnh.  
- **Phiên bản Java nào được yêu cầu?** JDK 8 hoặc mới hơn.

## “preview documents” là gì?
Xem trước tài liệu có nghĩa là tạo các hình thu nhỏ trực quan (thường là JPEG hoặc PNG) cho mỗi trang để người dùng có thể lướt nhanh nội dung. Kỹ thuật này cải thiện trải nghiệm người dùng trong các trình duyệt tệp, cổng đánh giá nội dung và bất kỳ hệ thống nào quản lý số lượng lớn tài liệu, cung cấp một gợi ý hình ảnh nhanh mà không cần mở toàn bộ tệp.

## Tại sao nên sử dụng GroupDocs.Merger cho Java?
GroupDocs.Merger chuyển các trang PDF thành hình ảnh **dưới 0.5 giây mỗi trang trên CPU 2 GHz tiêu chuẩn**, hỗ trợ **hơn 50 định dạng đầu vào và đầu ra**, và cho phép bạn truyền trực tiếp các preview tới bộ nhớ lưu trữ mà không cần tải toàn bộ tệp vào bộ nhớ. API mở rộng của nó cũng cung cấp cho bạn toàn quyền kiểm soát chất lượng hình ảnh, định dạng và đường dẫn đích.

## Yêu cầu
- **GroupDocs.Merger for Java** library (xem phần cài đặt bên dưới).  
- **JDK 8+** đã được cài đặt trên máy của bạn.  
- Một IDE (IntelliJ IDEA, Eclipse, NetBeans) và Maven hoặc Gradle để quản lý phụ thuộc.  

## Cài đặt GroupDocs.Merger cho Java
Thêm thư viện vào dự án của bạn bằng công cụ xây dựng ưa thích.

**Maven:**  
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle:**  
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Tải trực tiếp:**  
Hoặc, tải phiên bản mới nhất từ [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Nhận giấy phép
- **Bản dùng thử:** Bắt đầu bằng cách tải bản dùng thử miễn phí để khám phá các tính năng.  
- **Giấy phép tạm thời:** Nhận giấy phép tạm thời để truy cập mở rộng trong quá trình phát triển.  
- **Mua:** Đối với việc sử dụng trong môi trường sản xuất đầy đủ, mua giấy phép từ [GroupDocs](https://purchase.groupdocs.com/buy).

Một khi thư viện đã được thêm, khởi tạo nó với đường dẫn tới tài liệu bạn muốn xem trước:

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

## Cách Xem Trước Tài Liệu: Hướng Dẫn Từng Bước
Tải tệp nguồn, cấu hình một `PageStreamFactory`, và gọi `generatePreview`.  
`generatePreview` là một phương thức chuyển mỗi trang tài liệu thành hình ảnh theo các tùy chọn đã cung cấp.

### Bước 1: Khởi tạo Merger và Định nghĩa PageStreamFactory
`Merger` là lớp cốt lõi cung cấp các phương thức để hợp nhất, tách và tạo preview cho tài liệu.  
`PageStreamFactory` là một giao diện cho biết thư viện sẽ ghi mỗi hình ảnh preview vào đâu.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

Ở đây chúng tôi tạo một triển khai tùy chỉnh để ghi mỗi hình ảnh trang vào một thư mục cụ thể với quy tắc đặt tên có thể dự đoán.

```java
IPreviewOptions previewOption = new PreviewOptions(new PageStreamFactory() {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        return createStream(pageNumber);
    }
    
    @Override
    public void closePageStream(int pageNumber, OutputStream pageStream) {
        releasePageStream(pageNumber, pageStream);
    }
}, PreviewMode.JPEG);
```

### Bước 2: Tạo các Preview
`generatePreview` kích hoạt quá trình chuyển đổi dựa trên các tùy chọn bạn cung cấp. Nó truyền mỗi hình ảnh trang tới `PageStreamFactory` mà bạn đã định nghĩa, đảm bảo sử dụng bộ nhớ thấp.

```java
merger.generatePreview(previewOption);
```

### Chuyển Trang Thành Hình Ảnh – PageStreamFactory Tùy Chỉnh
Nếu bạn cần kiểm soát nhiều hơn về việc đặt tên tệp hoặc vị trí lưu trữ, hãy triển khai factory của riêng bạn:

```java
class CustomPageStreamFactory implements PageStreamFactory {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        String filePath = "YOUR_OUTPUT_DIRECTORY/image-" + pageNumber + ".jpg";
        return new FileOutputStream(filePath);
    }
    
    @Override
    public void closePageStream(int pageNumber, OutputStream pageStream) {
        try {
            if (pageStream != null) {
                pageStream.close();
            }
        } catch (Exception e) {
            throw new RuntimeException(e);
        }
    }
}
```

### Phương Thức Hỗ Trợ – Quản Lý Streams
Các phương thức tiện ích này giúp giữ cho mã gọn gàng và xử lý ngoại lệ một cách sạch sẽ.

```java
private static String getImagePath(int pageNumber) {
    return "YOUR_OUTPUT_DIRECTORY/image-" + pageNumber + ".jpg";
}

private static OutputStream createStream(int pageNumber) {
    try {
        String imageFilePath = getImagePath(pageNumber);
        return new FileOutputStream(imageFilePath);
    } catch (FileNotFoundException e) {
        throw new RuntimeException(e);
    }
}

private static void releasePageStream(int pageNumber, OutputStream pageStream) {
    try {
        if (pageStream != null) {
            pageStream.close();
        }
    } catch (Exception e) {
        throw new RuntimeException(e);
    }
}
```

## Tạo Thumbnail Tài Liệu – Ứng Dụng Thực Tế
Tạo preview đặc biệt hữu ích cho:

1. **Document Management Systems** – Người dùng có thể lướt qua tệp mà không cần mở chúng.  
2. **Content Review Platforms** – Kiểm tra nhanh hình ảnh trước khi phê duyệt tải lên.  
3. **Educational Tools** – Sinh viên có thể xem nhanh các slide bài giảng hoặc trang sách giáo trình.  

## Các lưu ý về hiệu năng
- **Giải phóng streams kịp thời** để giải phóng bộ nhớ.  
- **Tránh tải toàn bộ tài liệu** vào bộ nhớ; để thư viện xử lý việc phân trang.  
- **Sử dụng chất lượng hình ảnh phù hợp** để cân bằng tốc độ và độ chính xác hình ảnh.  

## Câu hỏi thường gặp

**Q: GroupDocs.Merger for Java được dùng để làm gì?**  
A: Nó được dùng để hợp nhất, tách và quản lý tài liệu một cách hiệu quả, bao gồm tạo preview và chuyển đổi định dạng.

**Q: Làm thế nào để xử lý ngoại lệ trong quá trình thao tác stream?**  
A: Bao bọc việc tạo và đóng stream trong các khối try‑catch, như trong các phương thức hỗ trợ, để ngăn rò rỉ bộ nhớ.

**Q: Tôi có thể tạo preview ở định dạng khác ngoài JPEG không?**  
A: Có, thay đổi enum `PreviewMode` thành PNG, BMP hoặc TIFF để phù hợp với yêu cầu của bạn.

**Q: Những vấn đề thường gặp khi tạo preview tài liệu là gì?**  
A: Các vấn đề phổ biến bao gồm đường dẫn tệp không đúng và quên đóng stream, có thể gây rò rỉ bộ nhớ.

**Q: Làm thế nào tôi có thể tích hợp GroupDocs.Merger với các hệ thống khác?**  
A: Sử dụng API của nó để kết nối với cơ sở dữ liệu, dịch vụ web, hoặc các ứng dụng Java khác để tự động hoá quy trình làm việc một cách liền mạch.

## Tài nguyên
- [Bản phát hành GroupDocs.Merger cho Java](https://releases.groupdocs.com/merger/java/)  
- [Tải xuống](https://releases.groupdocs.com/merger/java/)  
- [Tài liệu](https://docs.groupdocs.com/merger/java/)  
- [Tham chiếu API](https://reference.groupdocs.com/merger/java/)  
- [Bản dùng thử miễn phí](https://releases.groupdocs.com/merger/java/)  
- [Giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/)  
- [Mua](https://purchase.groupdocs.com/buy)  
- [GroupDocs](https://purchase.groupdocs.com/buy)  
- [Hỗ trợ](https://forum.groupdocs.com/c/merger/)

**Cập nhật lần cuối:** 2026-06-26  
**Đã kiểm tra với:** GroupDocs.Merger latest version (2025‑latest)  
**Tác giả:** GroupDocs

## Hướng dẫn liên quan

- [Hướng dẫn thao tác trang tài liệu cho GroupDocs.Merger Java](/merger/java/page-operations/)
- [Cách tải PDF từ URL bằng GroupDocs.Merger cho Java: Hướng dẫn toàn diện](/merger/java/document-loading/load-pdf-url-groupdocs-merger-java/)
- [Tạo PDF một trang duy nhất với GroupDocs.Merger Java](/merger/java/document-splitting/)