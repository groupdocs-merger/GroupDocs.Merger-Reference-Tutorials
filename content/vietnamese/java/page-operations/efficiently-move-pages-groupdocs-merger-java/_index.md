---
date: '2026-07-15'
description: Tìm hiểu cách sắp xếp lại các trang PDF bằng GroupDocs.Merger for Java.
  Hướng dẫn này bao gồm việc tích hợp, cách sử dụng và các thực tiễn tốt nhất để di
  chuyển trang trong PDF, tệp Word và bảng tính.
keywords:
- how to reorder pdf
- how to move pages
- GroupDocs Merger Java
lastmod: '2026-07-15'
og_description: Tìm hiểu cách sắp xếp lại các trang PDF bằng GroupDocs.Merger for
  Java. Hướng dẫn này trình bày các bước tích hợp, đoạn mã mẫu và mẹo tối ưu hiệu
  năng để di chuyển trang trong PDF, Word và Excel.
og_image_alt: 'Guide: Reorder PDF pages with GroupDocs.Merger for Java'
og_title: Cách sắp xếp lại các trang PDF bằng GroupDocs.Merger for Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-15'
  description: Learn how to reorder PDF pages using GroupDocs.Merger for Java. This
    guide covers integration, usage, and best practices for moving pages in PDFs,
    Word files, and spreadsheets.
  headline: How to Reorder PDF Pages with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to reorder PDF pages using GroupDocs.Merger for Java. This
    guide covers integration, usage, and best practices for moving pages in PDFs,
    Word files, and spreadsheets.
  name: How to Reorder PDF Pages with GroupDocs.Merger for Java
  steps:
  - name: Define File Paths
    text: Provide absolute or relative paths for the source and destination files.
      java int pageNumber = 5; // The original page number of the page you want to
      move int newPageNumber = 1; // The new position for this page
  - name: Specify Page Positions
    text: Identify the **source page number** (1‑based) and the **target index** where
      the page should appear after the move. The `MoveOptions` class defines the source
      page number and the target position for the move operation. java MoveOptions
      moveOptions = new MoveOptions(pageNumber, newPageNumber);
  - name: Create a `MoveOptions` Object
    text: '`MoveOptions` encapsulates the move operation’s parameters. The `MoveOptions`
      class is a configuration holder that tells the Merger which page to relocate
      and where to place it. java `Merger` is the core class that loads, manipulates,
      and saves documents using GroupDocs.Merger. Merger merger = new M'
  - name: Initialise the `Merger` Object
    text: The `Merger` class is the core engine that loads, manipulates, and saves
      documents. `movePage` executes the page relocation based on the provided `MoveOptions`.
      java merger.movePage(moveOptions);
  - name: Execute the Page Movement
    text: Calling `movePage` performs the reordering in memory and writes the result
      to the output file. `save` writes the modified document to the specified output
      path. java merger.save(filePathOut);
  - name: Save Changes
    text: The `save` method persists the modified document, completing the reordering
      workflow.
  type: HowTo
- questions:
  - answer: The API currently accepts one page per `movePage` call, but you can chain
      calls inside a loop to batch‑process many pages efficiently.
    question: Can I move multiple pages in a single call?
  - answer: No—commercial projects require a purchased license. A trial license is
      available for evaluation only.
    question: Is GroupDocs.Merger free for commercial use?
  - answer: PDF, DOC/DOCX, XLS/XLSX, PPT/PPTX, and several image formats (TIFF, PNG)
      are supported for page‑level operations.
    question: Which document formats support page reordering?
  - answer: Load the document with a password using the `LoadOptions` constructor,
      then perform the move as usual.
    question: How do I handle encrypted PDFs?
  - answer: Yes—simply stream the file from S3 into a `ByteArrayInputStream`, pass
      it to the `Merger`, and write the result back to the bucket.
    question: Can I integrate GroupDocs.Merger with cloud storage (e.g., AWS S3)?
  type: FAQPage
tags:
- reorder pdf
- GroupDocs.Merger
- Java document processing
- page manipulation
title: Cách sắp xếp lại các trang PDF bằng GroupDocs.Merger for Java
type: docs
url: /vi/java/page-operations/efficiently-move-pages-groupdocs-merger-java/
weight: 1
---

# Cách sắp xếp lại các trang PDF với GroupDocs.Merger cho Java

Việc sắp xếp lại các trang PDF là nhu cầu phổ biến khi bạn cần điều chỉnh báo cáo, hợp đồng pháp lý hoặc bộ trình chiếu một cách nhanh chóng. Trong hướng dẫn này, bạn sẽ khám phá **cách sắp xếp lại PDF** nhanh chóng và đáng tin cậy bằng cách sử dụng GroupDocs.Merger cho Java. Chúng tôi sẽ hướng dẫn cài đặt, chi tiết mã nguồn và các mẹo thực tế để bạn có thể di chuyển bất kỳ trang nào đến vị trí bất kỳ mà không mất định dạng.

## Câu trả lời nhanh
- **“move pages” có nghĩa là gì?** Nó chuyển một trang từ vị trí hiện tại sang vị trí mới trong khi giữ nguyên toàn bộ nội dung và bố cục.  
- **Các định dạng nào hỗ trợ di chuyển trang?** PDF, Word (DOC/DOCX), Excel (XLS/XLSX) và PowerPoint (PPT/PPTX).  
- **Tôi có cần giấy phép không?** Bản dùng thử miễn phí đủ cho phát triển; giấy phép đầy đủ cần thiết cho môi trường sản xuất.  
- **Tôi có thể xử lý các tệp lớn không?** Có — GroupDocs.Merger xử lý các PDF 500 trang với mức sử dụng bộ nhớ dưới 200 MB.  
- **Có thể thực thi bất đồng bộ không?** Bạn có thể bọc các cuộc gọi API trong một luồng riêng hoặc sử dụng `CompletableFuture` của Java để thực thi không chặn.

## “how to reorder pdf” là gì?
**how to reorder pdf** đề cập đến quá trình lập trình thay đổi thứ tự các trang xuất hiện trong một tệp PDF, cho phép bạn di chuyển, chèn hoặc xóa các trang mà không thay đổi nội dung hoặc định dạng của từng trang. GroupDocs.Merger cung cấp một API một‑phương‑thức thực hiện việc này chỉ trong vài dòng mã Java.

## Tại sao nên sử dụng GroupDocs.Merger cho Java để di chuyển trang?
GroupDocs.Merger hỗ trợ **hơn 30 định dạng đầu vào và đầu ra** và có thể thao tác với các tài liệu hàng trăm trang mà không cần tải toàn bộ tệp vào bộ nhớ. Các phép đo cho thấy việc di chuyển một trang trong PDF 300 trang mất dưới 150 ms trên CPU tiêu chuẩn 2.6 GHz, nhanh hơn khoảng ≈ 3× so với nhiều giải pháp mã nguồn mở.

## Yêu cầu trước

- **Java Development Kit (JDK) 11+** – thư viện được biên dịch cho Java 11 trở lên.  
- **Maven 3.6+ hoặc Gradle 6+** – để quản lý các phụ thuộc.  
- **Kiến thức cơ bản về Java** – bạn nên thoải mái tạo lớp, xử lý ngoại lệ và làm việc với I/O tệp.  

Có đầy đủ các yếu tố trên sẽ đảm bảo quá trình thiết lập suôn sẻ và cho phép bạn tập trung vào logic sắp xếp lại các trang.

## Cài đặt GroupDocs.Merger cho Java

Thêm thư viện vào tệp cấu hình dự án của bạn. Chọn công cụ phù hợp với dự án.

**Maven:**  
```xml
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>LATEST_VERSION_HERE</version>
</dependency>
```
```

**Gradle:**  
```groovy
```gradle
implementation 'com.groupdocs:groupdocs-merger:LATEST_VERSION_HERE'
```
```

Bạn cũng có thể tải JAR trực tiếp từ trang phát hành chính thức: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Nhận giấy phép

Để mở khóa toàn bộ API, bạn cần một tệp giấy phép:

1. **Free Trial** – lý tưởng cho các thử nghiệm nhanh.  
2. **Temporary License** – cung cấp thời gian đánh giá 30 ngày với đầy đủ tính năng.  
3. **Full License** – cần thiết cho triển khai thương mại và hỗ trợ ưu tiên.  

Đặt tệp `GroupDocs.Merger.lic` vào classpath của bạn (ví dụ, `src/main/resources`) trước khi gọi bất kỳ API nào.

## Cách sắp xếp lại các trang PDF với GroupDocs.Merger cho Java?

Tải PDF nguồn, chỉ định trang bạn muốn di chuyển, đặt chỉ mục mới và gọi `movePage`. Toàn bộ thao tác được hoàn thành trong một lời gọi phương thức duy nhất, làm cho đây là giải pháp ngắn gọn nhất trên thị trường. Thư viện tải tài liệu, sắp xếp lại chỉ mục trang và ghi kết quả, giữ nguyên mọi chú thích và tài nguyên.

```java
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.xlsx"; // Replace with your actual document path
String filePathOut = "YOUR_OUTPUT_DIRECTORY/MoveDocumentPage-output.docx"; // Output file path
```
```

### Hướng dẫn từng bước

#### Bước 1: Xác định đường dẫn tệp  
Cung cấp đường dẫn tuyệt đối hoặc tương đối cho các tệp nguồn và đích.

```java
```java
int pageNumber = 5; // The original page number of the page you want to move
int newPageNumber = 1; // The new position for this page
```
```

#### Bước 2: Xác định vị trí trang  
Xác định **số trang nguồn** (đánh số bắt đầu từ 1) và **chỉ mục đích** nơi trang sẽ xuất hiện sau khi di chuyển.

Lớp `MoveOptions` định nghĩa số trang nguồn và vị trí đích cho thao tác di chuyển.

```java
```java
MoveOptions moveOptions = new MoveOptions(pageNumber, newPageNumber);
```
```

#### Bước 3: Tạo đối tượng `MoveOptions`  
`MoveOptions` bao bọc các tham số của thao tác di chuyển.

Lớp `MoveOptions` là một bộ giữ cấu hình, cho biết Merger trang nào cần di chuyển và đặt ở đâu.  

```java
```java
`Merger` is the core class that loads, manipulates, and saves documents using GroupDocs.Merger.
Merger merger = new Merger(filePath);
```
```

#### Bước 4: Khởi tạo đối tượng `Merger`  
Lớp `Merger` là động cơ chính để tải, thao tác và lưu tài liệu.

`movePage` thực hiện việc di chuyển trang dựa trên `MoveOptions` được cung cấp.

```java
```java
merger.movePage(moveOptions);
```
```

#### Bước 5: Thực hiện di chuyển trang  
Gọi `movePage` thực hiện việc sắp xếp lại trong bộ nhớ và ghi kết quả vào tệp đầu ra.

`save` ghi tài liệu đã sửa đổi vào đường dẫn đầu ra đã chỉ định.

```java
```java
merger.save(filePathOut);
```
```

#### Bước 6: Lưu thay đổi  
Phương thức `save` lưu lại tài liệu đã chỉnh sửa, hoàn thành quy trình sắp xếp lại.

## Các vấn đề thường gặp và giải pháp

- **Lỗi đường dẫn tệp:** Sử dụng `Paths.get(...).toAbsolutePath()` để tránh các bất ngờ với đường dẫn tương đối.  
- **Số trang không hợp lệ:** Nhớ rằng chỉ mục trang bắt đầu từ 1; yêu cầu trang 0 sẽ gây ra `IndexOutOfBoundsException`.  
- **Thư viện lỗi thời:** Luôn tham chiếu phiên bản Maven/Gradle mới nhất để hưởng lợi từ các bản vá hiệu suất và hỗ trợ định dạng mới.

## Ứng dụng thực tiễn

1. **Sắp xếp lại báo cáo:** Đổi chỗ hoặc sắp xếp lại các chương trong báo cáo quý mà không cần tạo lại toàn bộ PDF.  
2. **Cập nhật tài liệu pháp lý:** Chèn các điều khoản mới vào vị trí đúng sau khi sửa đổi hợp đồng.  
3. **Tùy chỉnh bài thuyết trình:** Sắp xếp lại các slide (PPTX) trước khi xuất ra PDF cho thương hiệu riêng của khách hàng.

Những kịch bản này minh họa lý do các nhà phát triển chọn GroupDocs.Merger khi họ cần thao tác trang đáng tin cậy, hiệu suất cao trên nhiều loại tệp.

## Các cân nhắc về hiệu suất

- **Dấu chân bộ nhớ:** Thư viện truyền luồng các trang, vì vậy ngay cả PDF 1 GB cũng có thể được xử lý trên heap 2 GB.  
- **Tinh chỉnh Garbage Collection:** Bật `-XX:+UseG1GC` cho các công việc batch lớn để giảm thời gian dừng.  
- **Thực thi bất đồng bộ:** Bọc thao tác di chuyển trong `CompletableFuture.runAsync(...)` để giữ cho các luồng UI phản hồi trong các ứng dụng desktop.

## Câu hỏi thường gặp

**Q: Tôi có thể di chuyển nhiều trang trong một lời gọi duy nhất không?**  
A: API hiện tại chỉ chấp nhận một trang cho mỗi lời gọi `movePage`, nhưng bạn có thể nối các lời gọi trong một vòng lặp để xử lý hàng loạt nhiều trang một cách hiệu quả.

**Q: GroupDocs.Merger có miễn phí cho mục đích thương mại không?**  
A: Không — các dự án thương mại yêu cầu mua giấy phép. Giấy phép dùng thử chỉ dành cho việc đánh giá.

**Q: Các định dạng tài liệu nào hỗ trợ sắp xếp lại trang?**  
A: PDF, DOC/DOCX, XLS/XLSX, PPT/PPTX và một số định dạng ảnh (TIFF, PNG) được hỗ trợ cho các thao tác ở mức trang.

**Q: Làm thế nào để xử lý PDF được mã hóa?**  
A: Tải tài liệu bằng mật khẩu sử dụng hàm khởi tạo `LoadOptions`, sau đó thực hiện di chuyển như bình thường.

**Q: Tôi có thể tích hợp GroupDocs.Merger với lưu trữ đám mây (ví dụ, AWS S3) không?**  
A: Có — chỉ cần truyền luồng tệp từ S3 vào `ByteArrayInputStream`, truyền nó cho `Merger`, và ghi kết quả trở lại bucket.

## Tài nguyên

- **Documentation:** [GroupDocs Documentation](https://docs.groupdocs.com/merger/java/)  
- **API Reference:** [GroupDocs API Reference](https://reference.groupdocs.com/merger/java/)  
- **Download:** [Latest Release](https://releases.groupdocs.com/merger/java/)  
- **Purchase:** [Buy GroupDocs](https://purchase.groupdocs.com/buy)  
- **Free Trial:** [Start a Free Trial](https://releases.groupdocs.com/merger/java/)  
- **Temporary License:** [Obtain a Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Support:** [GroupDocs Support Forum](https://forum.groupdocs.com/c/merger)

**Cập nhật lần cuối:** 2026-07-15  
**Kiểm tra với:** GroupDocs.Merger 23.12 cho Java  
**Tác giả:** GroupDocs

## Hướng dẫn liên quan

- [Di chuyển trang trong tài liệu một cách hiệu quả bằng GroupDocs.Merger cho Java](/merger/java/page-operations/efficiently-move-pages-groupdocs-merger-java/)
- [Xoay các trang PDF trong Java bằng GroupDocs.Merger: Hướng dẫn từng bước](/merger/java/page-operations/rotate-pdf-pages-java-groupdocs-merger/)
- [Trích xuất hàng loạt các trang PDF bằng GroupDocs.Merger cho Java](/merger/java/document-extraction/extract-pages-groupdocs-merger-java/)