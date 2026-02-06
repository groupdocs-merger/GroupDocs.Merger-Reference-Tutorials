---
date: '2026-02-06'
description: Tìm hiểu cách tách một tệp văn bản theo từng dòng bằng GroupDocs.Merger
  cho Java. Hướng dẫn từng bước để tách tài liệu hiệu quả trong các dự án Java.
keywords:
- split text file line intervals Java
- document splitting GroupDocs.Merger
- Java document manipulation
title: Cách tách tệp theo dòng bằng GroupDocs.Merger cho Java
type: docs
url: /vi/java/document-splitting/split-text-file-line-intervals-groupdocs-merger-java/
weight: 1
---

# Cách Tách Tệp Theo Dòng Sử Dụng GroupDocs.Merger cho Java

Việc chia một tệp văn bản lớn thành các phần nhỏ hơn, dễ quản lý hơn **theo dòng** là nhu cầu phổ biến khi bạn ‑ ví dụ ‑ xử lý log, nhập dữ liệu hàng loạt, hoặc tái cấu trúc các báo cáo dài. Trong hướng dẫn này, bạn sẽ học cách **tách tệp theo dòng** bằng GroupDocs.Merger cho Java, hiểu vì sao cách tiếp cận này tiết kiệm thời gian, và nhận một mẫu mã sẵn sàng chạy.

## Câu trả lời nhanh
- **“split file by lines” có nghĩa là gì?** Nó tạo ra các tệp văn bản riêng biệt, mỗi tệp chứa một phạm vi số dòng được xác định từ tài liệu gốc.  
- **Thư viện nào thực hiện việc tách?** GroupDocs.Merger cho Java cung cấp một API đơn giản để tách theo khoảng dòng.  
- **Tôi có cần giấy phép không?** Bản dùng thử miễn phí đủ cho việc thử nghiệm; giấy phép vĩnh viễn cần thiết cho môi trường sản xuất.  
- **Tôi có thể tách theo số ký tự thay vì dòng không?** Không trực tiếp—cần thực hiện một bước tiền xử lý để thay đổi cấu trúc tệp trước khi tách.  
- **Phiên bản Java nào được hỗ trợ?** Bất kỳ môi trường chạy Java 8+ nào cũng tương thích.

## “split file by lines” là gì?
Tách một tệp theo dòng có nghĩa là lấy một tài liệu văn bản duy nhất và chia nó thành nhiều tệp, mỗi tệp chứa một phạm vi dòng liên tiếp nhất định (ví dụ: dòng 1‑3, 4‑6, v.v.). Kỹ thuật này lý tưởng cho xử lý hàng loạt, phân tích song song, hoặc đơn giản là cải thiện khả năng đọc.

## Tại sao nên sử dụng GroupDocs.Merger cho Java?
GroupDocs.Merger trừu tượng hoá công việc I/O tệp cấp thấp, cho phép bạn tập trung vào logic nghiệp vụ. Nó xử lý các tệp lớn một cách hiệu quả, hỗ trợ nhiều định dạng tài liệu, và cung cấp một API sạch sẽ, linh hoạt, dễ tích hợp với các dự án Maven hoặc Gradle.

## Yêu cầu trước
- **Java Development Kit (JDK) 8 trở lên** – đảm bảo `java` và `javac` có trong PATH của bạn.  
- **GroupDocs.Merger cho Java** – thêm thư viện qua Maven, Gradle, hoặc tải trực tiếp.  
- **Kiến thức cơ bản về Java** – bạn nên quen thuộc với các lớp, phương thức và xử lý ngoại lệ.

## Cài đặt GroupDocs.Merger cho Java
Thêm thư viện vào dự án của bạn bằng một trong các phương pháp dưới đây.

**Maven** – dán phần phụ thuộc này vào `pom.xml` của bạn:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle** – thêm dòng sau vào `build.gradle`:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Direct Download** – bạn cũng có thể tải JAR từ trang phát hành chính thức: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Nhận giấy phép
Bắt đầu với bản dùng thử miễn phí để khám phá API. Đối với các công việc sản xuất, hãy lấy giấy phép tạm thời hoặc đầy đủ từ cổng thông tin GroupDocs.

## Cách Tách Tệp Văn Bản Theo Dòng (Triển khai Java)

Dưới đây là hướng dẫn ngắn gọn, từng bước. Mỗi bước được giải thích bằng ngôn ngữ đơn giản trước khối mã, để bạn biết chính xác những gì đang diễn ra.

### Bước 1: Xác định Đường dẫn Nguồn và Đầu ra
Đầu tiên, cho thư viện biết tệp gốc của bạn nằm ở đâu và các phần tách ra sẽ được ghi vào đâu.
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.txt";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToLineRanges-" + Paths.get(filePath).getFileName().toString();
```

### Bước 2: Cấu hình tùy chọn tách
Tạo một thể hiện `TextSplitOptions` mô tả các khoảng dòng bạn muốn. Mảng `new int[] { 3, 6 }` thông báo cho API cắt sau dòng 3 và dòng 6, tạo ra hai phần: dòng 1‑3 và dòng 4‑6.
```java
TextSplitOptions splitOptions = new TextSplitOptions(filePathOut, TextSplitMode.Interval, new int[] { 3, 6 });
```

### Bước 3: Khởi tạo Merger và Thực hiện tách
Cuối cùng, khởi tạo `Merger` với tệp nguồn và gọi `split()` với các tùy chọn bạn vừa tạo.
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

Xong rồi! Sau khi lệnh hoàn thành, bạn sẽ thấy hai tệp mới trong `YOUR_OUTPUT_DIRECTORY`, mỗi tệp chứa các phạm vi dòng đã chỉ định.

## Ứng dụng thực tiễn (Tại sao điều này quan trọng)
1. **Data Processing Pipelines** – Chia các tệp log khổng lồ thành các phần nhỏ hơn để phân tích song song.  
2. **Document Management** – Chuyển một báo cáo duy nhất thành các tệp cấp chương để dễ phân phối hơn.  
3. **Content Segmentation** – Chuẩn bị các phần của một bài viết lớn cho các nền tảng xuất bản mục tiêu.

## Mẹo hiệu năng
- **Stream‑line I/O** – Ưu tiên sử dụng `Files.newBufferedReader` khi làm việc với tệp rất lớn để giảm mức sử dụng bộ nhớ.  
- **Close Resources** – Mặc dù GroupDocs.Merger xử lý hầu hết việc dọn dẹp, việc đóng các luồng tùy chỉnh một cách rõ ràng sẽ tránh rò rỉ.  
- **Monitor Memory** – Tách các tệp có kích thước gigabyte có thể tiêu tốn nhiều bộ nhớ; hãy cấp phát heap đủ (`-Xmx2g` hoặc cao hơn) nếu cần.

## Các vấn đề thường gặp và giải pháp
| Vấn đề | Nguyên nhân | Cách khắc phục |
|-------|-------------|----------------|
| `OutOfMemoryError` | Tệp nguồn quá lớn vượt quá heap. | Tăng heap JVM hoặc tách bằng các khoảng nhỏ hơn. |
| `FileNotFoundException` | Đường dẫn không đúng hoặc thiếu quyền. | Kiểm tra `filePath` và `filePathOut` là tuyệt đối và có quyền ghi. |
| Empty output files | Mảng khoảng không bao phủ toàn bộ tài liệu. | Đảm bảo khoảng cuối kết thúc tại hoặc vượt qua tổng số dòng. |

## Phần Câu hỏi thường gặp

**Q: Tôi có thể tách tệp dựa trên số ký tự thay vì số dòng không?**  
A: Hiện tại, GroupDocs.Merger cho Java tập trung vào các khoảng dòng. Tuy nhiên, bạn có thể tiền xử lý văn bản để đạt số ký tự mong muốn trên mỗi dòng trước khi sử dụng tính năng này.

**Q: Có giới hạn số lượng khoảng mà tôi có thể chỉ định để tách không?**  
A: Thư viện không có giới hạn cụ thể; tuy nhiên, hiệu năng có thể giảm khi số lượng tách quá nhiều do yêu cầu xử lý tăng lên.

**Q: Làm thế nào để xử lý lỗi khi tách tệp?**  
A: Thực hiện các khối try‑catch quanh mã của bạn để bắt và quản lý ngoại lệ một cách hiệu quả. GroupDocs.Merger cung cấp các thông báo lỗi chi tiết giúp khắc phục sự cố.

**Q: Thư viện có hỗ trợ các định dạng dựa trên văn bản khác như CSV hoặc TSV không?**  
A: Có, vì CSV và TSV là các tệp văn bản thuần, logic khoảng dòng vẫn áp dụng. Chỉ cần xử lý chúng như các tệp `.txt` trong API.

**Q: Tôi có thể tự động tách nhiều tệp trong một thư mục không?**  
A: Chắc chắn. Đặt logic trên trong một vòng lặp duyệt qua `Files.list(Paths.get("folder"))` và áp dụng cùng `TextSplitOptions` cho mỗi tệp.

## Tài nguyên
- **Documentation:** [GroupDocs.Merger for Java Documentation](https://docs.groupdocs.com/merger/java/)  
- **API Reference:** [GroupDocs API Reference](https://reference.groupdocs.com/merger/java/)  
- **Download:** [Latest Releases](https://releases.groupdocs.com/merger/java/)  
- **Purchase and Licensing:** [Buy GroupDocs](https://purchase.groupdocs.com/buy)  
- **Free Trial:** [GroupDocs Free Trial](https://releases.groupdocs.com/merger/java/)  
- **Temporary License:** [Obtain Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Support Forum:** [GroupDocs Support](https://forum.groupdocs.com/c/merger)

---

**Last Updated:** 2026-02-06  
**Tested With:** GroupDocs.Merger 23.12 for Java  
**Author:** GroupDocs