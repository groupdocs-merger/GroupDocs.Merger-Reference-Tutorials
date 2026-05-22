---
date: '2026-02-06'
description: Tìm hiểu cách tách các tệp DOCX bằng GroupDocs.Merger cho Java, bao gồm
  tách docx thành các tệp, các tùy chọn tách trong Java và trích xuất luồng.
keywords:
- Java Document Splitting
- GroupDocs.Merger for Java
- Split DOCX Pages
title: Cách tách DOCX bằng GroupDocs.Merger cho Java
type: docs
url: /vi/java/document-splitting/master-java-document-splitting-groupdocs-merger/
weight: 1
---

# Thành thạo việc tách tài liệu Java với GroupDocs.Merger: Tách các trang DOCX thành tệp và luồng

Trong hướng dẫn này, bạn sẽ khám phá **cách tách docx** một cách hiệu quả bằng GroupDocs.Merger cho Java. Cho dù bạn cần chia một hợp đồng lớn thành các trang riêng biệt hoặc trích xuất các phần cụ thể dưới dạng luồng, chúng tôi sẽ hướng dẫn bạn qua từng bước, từ cài đặt đến việc sử dụng thực tế.

## Câu trả lời nhanh
- **Thư viện nào xử lý việc tách DOCX trong Java?** GroupDocs.Merger cho Java.  
- **Tôi có thể tách một DOCX thành các tệp riêng biệt không?** Có – sử dụng `SplitOptions` với số trang.  
- **Có thể nhận các trang dưới dạng luồng thay vì tệp không?** Chắc chắn, bằng cách cung cấp một `SplitStreamFactory` tùy chỉnh.  
- **Tôi có cần giấy phép không?** Một giấy phép dùng thử tạm thời là đủ cho việc đánh giá; giấy phép đầy đủ cần thiết cho môi trường sản xuất.  
- **Các phiên bản Java nào được hỗ trợ?** Bất kỳ JDK 8+ nào cũng hoạt động với bản phát hành GroupDocs.Merger mới nhất.

## “Cách tách docx” là gì?
Việc tách một DOCX có nghĩa là lấy một tài liệu Word đa trang và tạo các tệp (hoặc luồng) riêng lẻ chứa một hoặc nhiều trang được chọn. Điều này hữu ích cho việc cung cấp tài liệu theo mô-đun, quy trình tuân thủ, hoặc xử lý ngay lập tức mà không cần lưu các tệp tạm thời.

## Tại sao nên sử dụng GroupDocs.Merger cho Java?
- **Xử lý không phụ thuộc:** Hoạt động với Java thuần, không cần binary gốc.  
- **Kiểm soát chi tiết:** Chọn các trang chính xác, định dạng đầu ra, và thậm chí các luồng trong bộ nhớ.  
- **Hiệu năng mở rộng:** Việc tách dựa trên luồng giảm áp lực bộ nhớ cho các tệp lớn.

## Yêu cầu trước

### Thư viện và phụ thuộc cần thiết
- **Java Development Kit (JDK):** JDK 8 hoặc mới hơn.  
- **GroupDocs.Merger cho Java:** Thư viện cốt lõi để thao tác tài liệu.

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
Khởi tạo thư viện trong dự án Java của bạn:

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

Với môi trường đã sẵn sàng, chúng ta sẽ khám phá hai cách chính để **tách docx thành tệp** hoặc luồng.

## Cách tách DOCX thành tệp với GroupDocs.Merger

### Tách tài liệu thành các trang riêng lẻ

#### Tổng quan
Cách tiếp cận này tạo một tệp riêng cho mỗi trang được chọn, hoàn hảo để phân phối các phần riêng lẻ.

#### Thực hiện từng bước

**Bước 1 – Xác định đường dẫn đầu vào và đầu ra**  
Xác định vị trí của tệp DOCX gốc và nơi lưu các tệp đã tách.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
String filePathOut = new File("YOUR_OUTPUT_DIRECTORY", 
    "SplitToSinglePages-" +
    Paths.get(filePath).getFileName().toString()
).getPath();
```

**Bước 2 – Cấu hình SplitOptions (split options java)**  
Cho thư viện biết các trang nào cần trích xuất.

```java
import com.groupdocs.merger.domain.options.SplitOptions;

SplitOptions splitOptions = new SplitOptions(filePathOut, new int[] { 3, 6, 8 });
```
- `filePathOut` – thư mục nơi mỗi tệp trang sẽ được đặt.  
- `new int[]{3,6,8}` – các số trang bạn muốn tách.

**Bước 3 – Thực hiện tách**  
Chạy thao tác với đối tượng `Merger`.

```java
import com.groupdocs.merger.Merger;

Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

**Mẹo chuyên nghiệp:** Kiểm tra xem thư mục đầu ra có tồn tại và ứng dụng của bạn có quyền ghi không; nếu không, quá trình tách sẽ thất bại.

### Những lỗi thường gặp
- **Thiếu thư mục đầu ra:** API sẽ không tự động tạo thư mục.  
- **Số trang không đúng:** Chỉ mục trang bắt đầu từ 1; chỉ định 0 sẽ gây lỗi.

## Cách tách các trang DOCX thành luồng (Trong bộ nhớ)

### Tổng quan
Khi bạn cần truy cập tạm thời—ví dụ, gửi một trang qua dịch vụ web—việc nắm bắt các trang dưới dạng luồng giúp tránh I/O đĩa.

#### Thực hiện từng bước

**Bước 1 – Xác định đường dẫn đầu vào và chuẩn bị danh sách cho các luồng**  

```java
import java.io.ByteArrayOutputStream;
import java.util.ArrayList;
import java.util.List;

String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
final List<OutputStream> resultStreams = new ArrayList<>();
```

**Bước 2 – Cấu hình SplitOptions với một SplitStreamFactory tùy chỉnh**  

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
- `closeSplitStream` – lưu luồng đã hoàn thành để sử dụng sau.

**Bước 3 – Thực thi tách và lấy các luồng**  

```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);

return resultStreams; // Retrieve streams for processing
```

### Mẹo khắc phục sự cố
- Đảm bảo đường dẫn DOCX nguồn đúng; lỗi chính tả sẽ gây ra `FileNotFoundException`.  
- Luôn đóng các luồng sau khi sử dụng để giải phóng bộ nhớ.

## Ứng dụng thực tiễn
1. **Hợp đồng pháp lý:** Trích xuất các điều khoản riêng lẻ để xem xét độc lập.  
2. **Nền tảng e‑learning:** Cung cấp các tệp Word theo chương mà không tiết lộ toàn bộ sách giáo trình.  
3. **Báo cáo doanh nghiệp:** Gửi chỉ phần tài chính của báo cáo quý cho CFO.

## Các cân nhắc về hiệu năng
- **Luồng tiết kiệm bộ nhớ:** Ưu tiên cách tiếp cận luồng cho các tài liệu lớn (>50 MB).  
- **Xử lý hàng loạt:** Nhóm nhiều công việc tách trong một phiên JVM để giảm chi phí khởi động.  
- **Dọn dẹp tài nguyên:** Gọi `merger.close()` và đóng tất cả các luồng để tránh rò rỉ.

## Kết luận
Bây giờ bạn đã biết **cách tách docx** thành các tệp riêng biệt hoặc luồng trong bộ nhớ bằng cách sử dụng GroupDocs.Merger cho Java. Những kỹ thuật này mang lại cho bạn sự linh hoạt để tùy chỉnh việc cung cấp tài liệu cho bất kỳ nhu cầu kinh doanh nào.

**Bước tiếp theo**
- Thử nghiệm với các phạm vi trang và định dạng đầu ra khác nhau (PDF, HTML, v.v.).  
- Kết hợp tách và hợp nhất để tái tạo các gói tùy chỉnh ngay lập tức.  

## Câu hỏi thường gặp

**Q: GroupDocs.Merger cho Java là gì?**  
A: Đó là một thư viện Java cho phép hợp nhất, tách và chuyển đổi nhiều định dạng tài liệu, bao gồm DOCX, PDF, PPTX và nhiều hơn nữa.

**Q: Làm thế nào để tôi có được giấy phép cho GroupDocs.Merger?**  
A: Bạn có thể nhận giấy phép dùng thử tạm thời từ [trang web GroupDocs](https://purchase.groupdocs.com/temporary-license/) để đánh giá. Đối với sử dụng trong sản xuất, mua giấy phép đầy đủ tại cùng trang web.

**Q: Tôi có thể tách các tệp PDF bằng cùng API không?**  
A: Có, phương thức `split` hoạt động với PDF, DOCX, PPTX và các định dạng được hỗ trợ khác.

**Q: Có thể tách một tài liệu mà không ghi ra đĩa không?**  
A: Chắc chắn—sử dụng cách tiếp cận dựa trên luồng như đã trình bày ở trên để giữ mọi thứ trong bộ nhớ.

**Q: Tôi nên sử dụng phiên bản GroupDocs.Merger nào?**  
A: Luôn chọn bản phát hành ổn định mới nhất để được hưởng các cải tiến hiệu năng và sửa lỗi.

---

**Cập nhật lần cuối:** 2026-02-06  
**Kiểm tra với:** GroupDocs.Merger for Java latest-version  
**Tác giả:** GroupDocs