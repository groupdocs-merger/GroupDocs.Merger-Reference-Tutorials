---
date: '2026-01-24'
description: Tìm hiểu cách xem trước tài liệu bằng cách tạo bản xem trước các trang
  với GroupDocs.Merger cho Java, một cách nhanh chóng để chuyển các trang thành hình
  ảnh nhằm tạo thumbnail cho tài liệu.
keywords:
- GroupDocs.Merger for Java
- document page previews
- Java document management
title: Cách xem trước tài liệu bằng GroupDocs.Merger cho Java
type: docs
url: /vi/java/document-information/generate-document-page-previews-groupdocs-merger-java/
weight: 1
---

# Cách Xem Trước Tài Liệu với GroupDocs.Merger cho Java

Tạo các bản xem trước trang tài liệu là một cách mạnh m** nhanh chóng, cung cấp cho người dùng một hình ảnh nhanh mà không cần lời nhanh.  
 dụng cho bản xem trước?** JPEG mặc định, nhưng các định dạng khác cũng được hỗ trợ.  
- **Có cần giấy phép không?** Bản dùng thử miễn phí đủ cho phát triển; giấy phép trả phí cần thiết cho môi trường sản xuất.  
- **Tôi có thể tùy chỉnh đường dẫn đầu ra không?** Có, bằng cách triển khai một `PageStreamFactory` tùy chỉnh.  
- **Yêu cầu phiên bản Java nào?** JDK 8 trở lên.

## “Xem trước tài liệu” là gì?
Xem trước tài liệu có nghĩa là tạo các thumbnail trực quan (thường là JPEG hoặc PNG) cho mỗi trang để người dùng có thể lướt nhanh nội dung. Kỹ thuật này cải thiện trải nghiệm người dùng trong các hệ thống quản lý tài liệu, cổng thông tin và bất kỳ ứng dụng nào xử lý nhiều tệp.

## Tại sao nên dùng GroupDocs.Merger cho Java?
- **Chuyển đổi nhanh** các trang thành hình ảnh mà không cần mở toàn bộ tài liệu trong giao diện người dùng.  
- **Hỗ trợ tích hợp** cho nhiều định dạng (PDF, DOCX, XLSX, v.v.).  
- **API mở rộng** cho phép bạn kiểm soát nơi và cách các tệp xem trước được lưu.

## Yêu cầu trước
- Thư viện **GroupDocs.Merger cho Java** (xem phần cài đặt bên dưới).  
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
Hoặc tải phiên bản mới nhất từ [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Nhận giấy phép
- **Bản dùng thử:** Bắt đầu bằng cách tải bản dùng thử miễn phí để khám phá các tính năng.  
- **Giấy phép tạm thời:** Nhận giấy phép tạm thời để truy cập mở rộng trong quá trình phát triển.  
- **Mua bản quyền:** Đối với sử dụng sản xuất đầy đủ, mua giấy phép từ [GroupDocs](https://purchase.groupdocs.com/buy).

Sau khi thư viện được thêm, khởi tạo nó với đường dẫn tới tài liệu bạn muốn xem trước:

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

## Hướng dẫn Xem Trước Tài Liệu: Các bước chi tiết

### Bước 1: Khởi tạo Merger và Định nghĩa PageStreamFactory
`PageStreamFactory` cho thư viện biết nơi ghi mỗi hình ảnh xem trước.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

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

### Bước 2: Tạo các bản xem trước
Gọi phương thức `generatePreview` với các tùy chọn bạn vừa cấu hình.

```java
merger.generatePreview(previewOption);
```

### Chuyển đổi các trang thành hình ảnh – PageStreamFactory tùy chỉnh
Nếu bạn cần kiểm soát tên tệp hoặc vị trí lưu trữ, hãy triển khai factory của riêng bạn:

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

### Phương thức trợ giúp – Quản lý Streams
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

## Tạo Thumbnail Tài Liệu – Ứng dụng Thực tế
Việc tạo bản xem trước đặc biệt hữu ích cho:

1. **Hệ thống quản lýNền tảng đánh giá nội dung** – Kiểm tra nhanh hình ảnh trước khi ph. **Công cụ giáo dục** – Học sinh có thể xem nhanh các slide bài giảng hoặc trang sách giáo trình.

## Các lưu ý về hiệu năng
- **Giải phóng streams kịp thời** để giải phóng bộ nhớ.  
 làm gì?**  
ĐáchĐ: Bao bọc việc tạo và đóng stream trong khối try‑catch, như trong các phương thức trợ giúp.

**H: Tôi có thể tạo bản xem trước ở định dạng khác JPEG không?**  
Đ: Có, thay đổi enum `PreviewMode` sang PNG, BMP, v.v. tùy nhu cầu.

**H: Những vấn đề thường gặp khi tạo bản xem trước tài liệu là gì?**  
Đ: Các vấn đề phổ biến bao gồm đường dẫn tệp không đúng và không đóng streams, dẫn đến rò rỉ bộ nhớ.

**H: Làm sao tích hợp GroupDocs.Merger với các hệ thống khác?**  
Đ: Sử dụng API của nó để kết nối với cơ sở dữ liệu, dịch vụ web hoặc các ứng dụng Java khác, tạo quy trình làm việc tự động liền mạch.

## Tài nguyên bổ sung
- [Documentation](https://docs.groupdocs.com/merger/java/)
- [API Reference](https://reference.groupdocs.com/merger/java/)
- [Download](https://releases.groupdocs.com/merger/java/)
- [Purchase](https://purchase.groupdocs.com/buy)
- [Free Trial](https://releases.groupdocs.com/merger/java/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [Support](https://forum.groupdocs.com/c/merger/)

---

**Cập nhật lần cuối:** 2026-01-24  
**Đã kiểm tra với:** GroupDocs.Merger phiên bản mới nhất (2025‑latest)  
**Tác giả:** GroupDocs