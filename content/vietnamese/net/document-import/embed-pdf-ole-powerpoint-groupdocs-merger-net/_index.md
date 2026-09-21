---
date: '2026-09-21'
description: Tìm hiểu cách nhúng PDF vào PowerPoint dưới dạng đối tượng OLE với GroupDocs.Merger
  cho .NET. Hướng dẫn từng bước này cho bạn biết các lời gọi API chính xác và các
  thực hành tốt nhất.
keywords:
- embed pdf in powerpoint
- convert pdf to ole
- insert pdf as ole
- add ole object powerpoint
lastmod: '2026-09-21'
og_description: nhúng PDF vào PowerPoint bằng GroupDocs.Merger cho .NET. Thực hiện
  theo hướng dẫn ngắn gọn này để thêm đối tượng OLE, cấu hình các tùy chọn và tránh
  các lỗi thường gặp.
og_image_alt: Screenshot of PowerPoint slide with embedded PDF OLE object using GroupDocs.Merger
og_title: nhúng PDF vào PowerPoint – nhúng PDF dưới dạng OLE với GroupDocs.Merger
schemas:
- author: GroupDocs
  dateModified: '2026-09-21'
  description: Learn how to embed pdf in powerpoint as an OLE object with GroupDocs.Merger
    for .NET. This step‑by‑step guide shows you the exact API calls and best practices.
  headline: How to embed pdf in powerpoint as OLE using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to embed pdf in powerpoint as an OLE object with GroupDocs.Merger
    for .NET. This step‑by‑step guide shows you the exact API calls and best practices.
  name: How to embed pdf in powerpoint as OLE using GroupDocs.Merger for .NET
  steps:
  - name: '**Corporate briefings** – attach the latest financial report without inflating
      the deck size.'
    text: '**Corporate briefings** – attach the latest financial report without inflating
      the deck size.'
  - name: '**Academic lectures** – provide full‑text research papers alongside slide
      summaries.'
    text: '**Academic lectures** – provide full‑text research papers alongside slide
      summaries.'
  - name: '**Project status updates** – embed a live project plan that stakeholders
      can open for details.'
    text: '**Project status updates** – embed a live project plan that stakeholders
      can open for details.'
  - name: '**Sales decks** – include product spec sheets that sales reps can open
      on demand.'
    text: '**Sales decks** – include product spec sheets that sales reps can open
      on demand.'
  - name: '**Technical workshops** – present schematics or datasheets that engineers
      can inspect instantly.'
    text: '**Technical workshops** – present schematics or datasheets that engineers
      can inspect instantly.'
  type: HowTo
- questions:
  - answer: Yes. Call `ImportDocument` for each PDF, specifying a different `SlideNumber`
      or position on the same slide.
    question: Can I embed multiple PDFs into a single presentation?
  - answer: The practical limit is dictated by your server’s memory; embeddings of
      up to 500 MB have been tested without issues when streaming.
    question: How large a PDF can I embed?
  - answer: Absolutely. The embedded PDF opens in the default viewer, preserving all
      internal links and bookmarks.
    question: Does the OLE object retain interactive elements like hyperlinks?
  - answer: Provide the password via the `Password` property of `OlePresentationOptions`
      before calling `ImportDocument`.
    question: What if the PDF is password‑protected?
  - answer: The OLE format is supported by PowerPoint 2007 and later, including Office
      365.
    question: Will the embedded object work on all versions of PowerPoint?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- OLE object
- PowerPoint automation
title: Cách nhúng PDF vào PowerPoint dưới dạng OLE bằng GroupDocs.Merger cho .NET
type: docs
url: /vi/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/
weight: 1
---

# Nhúng PDF vào PowerPoint dưới dạng OLE bằng GroupDocs.Merger cho .NET

Việc nhúng một tệp PDF trực tiếp vào một slide PowerPoint cho phép bạn giữ nguyên tài liệu gốc trong khi cung cấp cho khán giả quyền truy cập ngay lập tức. Trong hướng dẫn này, bạn sẽ học **cách nhúng pdf vào powerpoint** dưới dạng đối tượng OLE với GroupDocs.Merger cho .NET, xem các tùy chọn API cần thiết và khám phá các mẹo để đạt hiệu suất ổn định.

## Câu trả lời nhanh
- **Thư viện nào xử lý việc nhúng OLE?** GroupDocs.Merger cho .NET cung cấp lớp `OlePresentationOptions` cho mục đích này.  
- **Tôi có cần giấy phép không?** Giấy phép dùng thử hoạt động cho phát triển; giấy phép đầy đủ cần thiết cho môi trường sản xuất.  
- **Tôi có thể nhúng hơn một PDF không?** Có – lặp lại bước nhập cho mỗi slide bạn muốn.  
- **Các phiên bản .NET nào được hỗ trợ?** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7.  
- **Quá trình có tiết kiệm bộ nhớ không?** API truyền luồng các tệp, vì vậy ngay cả các PDF hàng trăm trang cũng có thể được nhúng mà không cần tải toàn bộ tệp vào bộ nhớ.

## Nhúng PDF vào PowerPoint là gì?
**embed pdf in powerpoint** có nghĩa là chèn một tệp PDF dưới dạng đối tượng OLE (Object Linking and Embedding) để slide hiển thị một biểu tượng hoặc bản xem trước, khi nhấp đúp sẽ mở PDF gốc trong trình xem mặc định. Cách tiếp cận này giữ nguyên định dạng, siêu liên kết và cài đặt bảo mật của tài liệu nguồn.

## Tại sao nên dùng nhúng OLE thay vì chuyển đổi PDF?
Việc nhúng giữ nguyên kích thước và bố cục tệp gốc, loại bỏ lỗi chuyển đổi và cho phép bạn cập nhật PDF nguồn mà không cần xuất lại bản trình chiếu. GroupDocs.Merger hỗ trợ **hơn 50 định dạng đầu vào và đầu ra** và có thể nhúng các PDF lên tới vài trăm megabyte trong khi truyền luồng dữ liệu để giữ mức sử dụng bộ nhớ dưới 100 MB.

## Yêu cầu trước
- Visual Studio 2022 (hoặc bất kỳ IDE nào tương thích với .NET)  
- .NET Framework 4.5+ hoặc .NET Core 3.1+ runtime  
- Giấy phép GroupDocs.Merger cho .NET hợp lệ (dùng thử hoặc thương mại)  
- Tệp PowerPoint (.pptx) và PDF bạn muốn nhúng  

## Cài đặt GroupDocs.Merger cho .NET

### Làm thế nào để cài đặt thư viện?
**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI** – tìm kiếm “GroupDocs.Merger” và nhấp **Install** để lấy phiên bản mới nhất.

### Làm thế nào để nhận giấy phép?
- **Dùng thử miễn phí** – đăng ký trên trang web GroupDocs để nhận khóa giấy phép tạm thời.  
- **Giấy phép tạm thời** – yêu cầu dùng thử mở rộng nếu bạn cần hơn 30 ngày.  
- **Mua đầy đủ** – mua giấy phép thương mại để sử dụng không giới hạn trong môi trường sản xuất.

### Làm thế nào để khởi tạo API?
`Merger` là lớp chính cung cấp các thao tác xử lý tài liệu như nhập, hợp nhất và chuyển đổi.  
Thêm các chỉ thị `using` cần thiết ở đầu tệp C# của bạn và tạo một thể hiện `Merger` với đường dẫn tới tệp giấy phép:

```csharp
using System;
using GroupDocs.Merger.Domain.Options;
using GroupDocs.Merger;
using System.IO;
```  

## Hướng dẫn triển khai

### Cách nhúng pdf vào powerpoint dưới dạng OLE?
Tải bản trình chiếu của bạn, cấu hình các tùy chọn OLE, và gọi phương thức nhập – toàn bộ thao tác hoàn thành trong ba bước logic.

**Bước 1 – xác định vị trí tệp**  
Xác định đường dẫn tuyệt đối hoặc tương đối cho PDF nguồn, tệp PowerPoint đích, và thư mục nơi bản trình chiếu đã chỉnh sửa sẽ được lưu.

**Bước 2 – cấu hình các tùy chọn OLE**  
`OlePresentationOptions` là lớp cho phép GroupDocs.Merger biết tệp nào sẽ được nhúng, trên slide nào, và tại tọa độ nào. Nó cũng cho phép bạn đặt chiều rộng, chiều cao và chế độ hiển thị của đối tượng đã nhúng.

**Bước 3 – nhập PDF**  
`ImportDocument` là lời gọi API Merger chèn đối tượng OLE vào tệp PowerPoint bằng các tùy chọn đã cung cấp. Phương thức truyền luồng PDF vào slide mà không tải toàn bộ tài liệu vào bộ nhớ.

#### Định nghĩa các mỏ neo
- `OlePresentationOptions` là bộ chứa tùy chọn định nghĩa tệp được nhúng, vị trí (X/Y), kích thước và số slide mục tiêu.  
- `ImportDocument` là lời gọi API Merger chèn đối tượng OLE vào tệp PowerPoint bằng các tùy chọn đã cung cấp.

## Tham số cấu hình chung
- **SlideNumber** – chỉ mục bắt đầu từ 1 của slide sẽ chứa đối tượng OLE.  
- **XCoordinate / YCoordinate** – vị trí đo bằng điểm từ góc trên‑trái của slide.  
- **Width / Height** – kích thước của vùng giữ chỗ OLE; đặt 0 để sử dụng kích thước mặc định.  
- **ObjectName** – tên thân thiện tùy chọn hiển thị khi đối tượng được chọn trong PowerPoint.

## Ứng dụng thực tiễn
Nhúng PDF dưới dạng đối tượng OLE tỏa sáng trong nhiều kịch bản thực tế:

1. **Báo cáo doanh nghiệp** – đính kèm báo cáo tài chính mới nhất mà không làm tăng kích thước bộ slide.  
2. **Bài giảng học thuật** – cung cấp các bài nghiên cứu đầy đủ bên cạnh tóm tắt slide.  
3. **Cập nhật trạng thái dự án** – nhúng kế hoạch dự án trực tiếp mà các bên liên quan có thể mở để xem chi tiết.  
4. **Bộ tài liệu bán hàng** – bao gồm các bảng thông số sản phẩm mà nhân viên bán hàng có thể mở khi cần.  
5. **Hội thảo kỹ thuật** – trình bày sơ đồ hoặc datasheet mà kỹ sư có thể kiểm tra ngay lập tức.

## Các cân nhắc về hiệu suất
Để giữ quá trình nhúng nhanh và tiết kiệm bộ nhớ:

- **Truyền luồng tệp** – GroupDocs.Merger đọc và ghi luồng, vì vậy ngay cả PDF 200 trang cũng chỉ dùng dưới 100 MB RAM.  
- **Xử lý hàng loạt** – khi cập nhật nhiều bản trình chiếu, tái sử dụng một thể hiện `Merger` duy nhất và đóng luồng kịp thời.  
- **Thay đổi kích thước PDF lớn** – nén hoặc giảm mẫu ảnh trong PDF nguồn nếu bạn nhận thấy thời gian tải chậm.

## Câu hỏi thường gặp

**Q: Tôi có thể nhúng nhiều PDF vào một bản trình chiếu không?**  
A: Có. Gọi `ImportDocument` cho mỗi PDF, chỉ định `SlideNumber` hoặc vị trí khác nhau trên cùng một slide.

**Q: Tôi có thể nhúng PDF có kích thước bao nhiêu?**  
A: Giới hạn thực tế phụ thuộc vào bộ nhớ máy chủ của bạn; việc nhúng lên tới 500 MB đã được thử nghiệm mà không gặp vấn đề khi truyền luồng.

**Q: Đối tượng OLE có giữ lại các yếu tố tương tác như siêu liên kết không?**  
A: Chắc chắn. PDF đã nhúng mở trong trình xem mặc định, giữ nguyên tất cả các liên kết nội bộ và dấu trang.

**Q: Nếu PDF được bảo vệ bằng mật khẩu thì sao?**  
A: Cung cấp mật khẩu qua thuộc tính `Password` của `OlePresentationOptions` trước khi gọi `ImportDocument`.

**Q: Đối tượng đã nhúng có hoạt động trên mọi phiên bản PowerPoint không?**  
A: Định dạng OLE được hỗ trợ bởi PowerPoint 2007 trở lên, bao gồm Office 365.

## Kết luận
Bây giờ bạn đã có quy trình hoàn chỉnh, sẵn sàng cho sản xuất để **nhúng pdf vào powerpoint** dưới dạng đối tượng OLE bằng GroupDocs.Merger cho .NET. Bằng cách truyền luồng tệp, cấu hình `OlePresentationOptions` và gọi `ImportDocument`, bạn có thể làm phong phú bản trình chiếu với các PDF gốc đồng thời giữ mức sử dụng bộ nhớ thấp và bảo toàn mọi tính năng tương tác. Khám phá các khả năng bổ sung của Merger như hợp nhất slide, chuyển đổi định dạng và chèn watermark để tự động hoá quy trình tài liệu của bạn hơn.

---

**Cập nhật lần cuối:** 2026-09-21  
**Kiểm thử với:** GroupDocs.Merger 23.12 cho .NET  
**Tác giả:** GroupDocs  

## Tài nguyên
- **Tài liệu:** [GroupDocs.Merger for .NET Documentation](https://docs.groupdocs.com/merger/net/)  
- **Tham chiếu API:** [GroupDocs.Merger API Reference](https://reference.groupdocs.com/merger/net/)  
- **Tải xuống:** [GroupDocs.Merger Downloads](https://releases.groupdocs.com/merger/net/)  
- **Mua:** [Buy GroupDocs License](https://purchase.groupdocs.com/buy)  
- **Dùng thử miễn phí:** [GroupDocs Free Trial](https://releases.groupdocs.com/merger/net/)  
- **Giấy phép tạm thời:** [Get a Temporary License](https://purchase.groupdocs.com/temporary-license)

```csharp
string filePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pptx"); // Presentation file path
string embeddedFilePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pdf"); // PDF to embed as OLE object
string outputDirectoryPath = "YOUR_OUTPUT_DIRECTORY"; // Output directory for modified presentation
string filePathOut = Path.Combine(outputDirectoryPath, "ModifiedPresentation.pptx"); // Output file path
```

```csharp
int pageNumber = 2; // Slide number to add OLE object
OlePresentationOptions oleSlidesOptions = new OlePresentationOptions(embeddedFilePath, pageNumber)
{
    X = 10, // X-coordinate for positioning the embedded object on the slide
    Y = 10  // Y-coordinate for positioning the embedded object on the slide
};
```

```csharp
using (Merger merger = new Merger(filePath)) // Initialize with presentation file path
{
    merger.ImportDocument(oleSlidesOptions); // Embed PDF as OLE using specified options
    merger.Save(filePathOut); // Save the modified presentation to output directory
}
```

## Hướng dẫn liên quan

- [Nhúng PDF vào Word bằng GroupDocs.Merger cho .NET: Hướng dẫn từng bước](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [Tải PDF từ URL trong .NET bằng GroupDocs.Merger: Hướng dẫn toàn diện](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)
- [Cách lấy thông tin tài liệu bằng GroupDocs.Merger cho .NET: Hướng dẫn toàn diện](/merger/net/document-information/retrieve-document-info-groupdocs-merger-dotnet/)