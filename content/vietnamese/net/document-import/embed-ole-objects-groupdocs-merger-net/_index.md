---
date: '2026-09-21'
description: Tìm hiểu cách nhúng PDF vào các bảng tính Excel với GroupDocs.Merger
  for .NET, nâng cao cách trình bày dữ liệu và tính năng.
keywords:
- embed pdf in excel
- how to embed ole
- add ole object excel
- add ole to excel
lastmod: '2026-09-21'
og_description: Tìm hiểu cách nhúng PDF vào Excel với GroupDocs.Merger for .NET. Thực
  hiện các hướng dẫn từng bước, xem câu trả lời nhanh, và tránh các lỗi thường gặp.
og_image_alt: Developer guide showing PDF embedded in an Excel spreadsheet via GroupDocs.Merger
  for .NET
og_title: Cách nhúng PDF vào Excel bằng GroupDocs.Merger for .NET
schemas:
- author: GroupDocs
  dateModified: '2026-09-21'
  description: Learn how to embed PDF in Excel spreadsheets with GroupDocs.Merger
    for .NET, enhancing data presentation and functionality.
  headline: How to embed PDF in Excel using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to embed PDF in Excel spreadsheets with GroupDocs.Merger
    for .NET, enhancing data presentation and functionality.
  name: How to embed PDF in Excel using GroupDocs.Merger for .NET
  steps:
  - name: '**Free trial** – test the library without cost.'
    text: '**Free trial** – test the library without cost.'
  - name: '**Temporary license** – request a temporary license on the [temporary‑license
      page](https://purchase.groupdocs.com/temporary-license/).'
    text: '**Temporary license** – request a temporary license on the [temporary‑license
      page](https://purchase.groupdocs.com/temporary-license/).'
  - name: '**Purchase** – consider purchasing a license on the [GroupDocs purchase
      page](https://purchase.groupdocs.com/buy).'
    text: '**Purchase** – consider purchasing a license on the [GroupDocs purchase
      page](https://purchase.groupdocs.com/buy).'
  - name: '**Financial reports** – attach audited statements directly beside summary
      tables.'
    text: '**Financial reports** – attach audited statements directly beside summary
      tables.'
  - name: '**Project documentation** – keep design specs, risk analyses, or contracts
      within a master tracker.'
    text: '**Project documentation** – keep design specs, risk analyses, or contracts
      within a master tracker.'
  - name: '**Training dashboards** – embed user manuals or policy PDFs for quick reference
      by staff.'
    text: '**Training dashboards** – embed user manuals or policy PDFs for quick reference
      by staff.'
  type: HowTo
- questions:
  - answer: An OLE (Object Linking and Embedding) object stores another file (PDF,
      Word, image, etc.) inside a host document, allowing in‑place editing or opening.
    question: What is an OLE object?
  - answer: Yes—GroupDocs.Merger also supports Word, PowerPoint, and Visio files.
    question: Can I embed OLE objects in other Office formats?
  - answer: Provide the password when creating the `OleSpreadsheetOptions` instance;
      the library will decrypt the file automatically.
    question: How do I handle password‑protected PDFs?
  - answer: Technically no hard limit, but files larger than 10 MB may noticeably
      increase workbook load time.
    question: Is there a size limitation for embedded PDFs?
  - answer: Visit the official [GroupDocs Documentation](https://docs.groupdocs.com/merger/net/)
      for additional code samples and API references.
    question: Where can I find more examples?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- .NET Excel integration
title: Cách nhúng PDF vào Excel bằng GroupDocs.Merger for .NET
type: docs
url: /vi/net/document-import/embed-ole-objects-groupdocs-merger-net/
weight: 1
---

# Cách nhúng PDF vào Excel bằng GroupDocs.Merger cho .NET

## Giới thiệu

Nhúng PDF vào Excel cho phép bạn giữ các tài liệu hỗ trợ—như hợp đồng, báo cáo hoặc thông số kỹ thuật—ngay tại nơi dữ liệu tồn tại. Với **GroupDocs.Merger for .NET**, bạn có thể thêm các đối tượng OLE vào các ô chỉ với vài dòng mã, biến một bảng tính đơn giản thành một workbook tương tác, tự chứa. Hướng dẫn này sẽ đưa bạn qua mọi thứ cần biết, từ cài đặt đến khắc phục sự cố.

**Bạn sẽ học được**

- Cách thiết lập GroupDocs.Merger cho .NET trong dự án C#  
- Các bước chính xác để nhúng PDF (hoặc bất kỳ tệp tương thích OLE nào) vào một ô Excel  
- Các tùy chọn cấu hình, mẹo hiệu suất và những khó khăn thường gặp  

Hãy chắc chắn rằng bạn đã sẵn sàng trước khi bắt đầu.

## Câu trả lời nhanh
- **Tôi có thể nhúng bất kỳ loại tệp nào không?** Có — bất kỳ định dạng nào được hỗ trợ như đối tượng OLE (PDF, Word, hình ảnh, v.v.).  
- **Tôi có cần giấy phép cho việc phát triển không?** Bản dùng thử miễn phí hoạt động cho việc thử nghiệm; giấy phép vĩnh viễn cần thiết cho môi trường sản xuất.  
- **Phiên bản .NET nào được hỗ trợ?** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7+.  
- **Kích thước tệp Excel sẽ tăng đáng kể không?** Chỉ tăng theo kích thước của tài liệu được nhúng; giữ các tệp dưới vài MB để có hiệu suất tốt nhất.  
- **Có giới hạn số lượng đối tượng OLE không?** Thực tế không có, nhưng các workbook rất lớn có thể ảnh hưởng đến thời gian tải.

## PDF nhúng trong Excel là gì?

Nhúng PDF vào Excel chèn toàn bộ PDF dưới dạng đối tượng OLE có thể mở trực tiếp từ bảng tính. Người dùng nhấp vào biểu tượng và xem tài liệu gốc mà không rời Excel. Cách tiếp cận này bảo tồn bố cục gốc, cho phép tham chiếu nhanh và loại bỏ nhu cầu quản lý các tệp riêng biệt. PDF được nhúng hoạt động như bất kỳ đối tượng OLE nào khác, cho phép người dùng nhấp đúp vào biểu tượng để khởi chạy trình xem PDF trong khi vẫn ở trong môi trường Excel.

## Tại sao nên nhúng đối tượng OLE trong Excel?

GroupDocs.Merger hỗ trợ **120+ input and output formats** và có thể nhúng các đối tượng mà không tải toàn bộ tệp vào bộ nhớ, cho phép xử lý nhanh các PDF hàng trăm trang. Điều này giảm nhu cầu lưu trữ các kho tệp riêng biệt và giữ dữ liệu liên quan cùng nhau. Nó cũng đơn giản hoá việc kiểm soát phiên bản và đảm bảo mọi tài liệu liên quan đi cùng workbook, cải thiện sự hợp tác giữa các đội nhóm.

## Yêu cầu trước

- **GroupDocs.Merger for .NET** (gói NuGet mới nhất)  
- **.NET Framework** 4.5+ **or** **.NET Core/5+/6+**  
- Visual Studio 2022 hoặc mới hơn  
- Kiến thức cơ bản về C# và quen thuộc với I/O tệp  

## Cài đặt GroupDocs.Merger cho .NET

### Cài đặt

Thêm gói bằng một trong các phương pháp sau:

**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI**  
Tìm kiếm “GroupDocs.Merger” và cài đặt phiên bản mới nhất.

### Mua giấy phép

1. **Bản dùng thử** – thử thư viện mà không tốn phí.  
2. **Giấy phép tạm thời** – yêu cầu giấy phép tạm thời trên trang [temporary‑license page](https://purchase.groupdocs.com/temporary-license/).  
3. **Mua** – cân nhắc mua giấy phép trên [GroupDocs purchase page](https://purchase.groupdocs.com/buy).

### Khởi tạo cơ bản

`Merger` là điểm vào cho tất cả các thao tác.  
```csharp
using (Merger merger = new Merger("path_to_your_spreadsheet.xlsx"))
{
    // Your code to work with the document
}
```  

## Cách nhúng đối tượng OLE trong Excel?

Tải workbook nguồn, cấu hình các tùy chọn OLE, và để `Merger` chèn đối tượng. Các phần sau đây cung cấp quy trình ngắn gọn, sẵn sàng chạy.

### Tổng quan về tính năng
Nhúng đối tượng OLE cho phép bạn lưu một PDF hoàn chỉnh trong một ô, bảo tồn bố cục gốc và cho phép truy cập chỉ một cú nhấp từ Excel.

### Triển khai từng bước

#### 1. Đặt đường dẫn và số trang
Xác định bảng tính, tệp cần nhúng và địa chỉ ô mục tiêu.

```csharp
string filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
string embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_PDF";
int pageNumber = 2; // The specific page to embed

// Output path for the modified spreadsheet
string filePathOut = Path.Combine("YOUR_OUTPUT_DIRECTORY", "OUT_SAMPLE_NAME.xlsx");
```  

#### 2. Cấu hình OleSpreadsheetOptions
`OleSpreadsheetOptions` xác định vị trí đối tượng OLE sẽ được đặt trong worksheet và cách biểu tượng của nó hiển thị.  
```csharp
// Specify row and column indices for embedding
OleSpreadsheetOptions oleCellsOptions = new OleSpreadsheetOptions(embeddedFilePath, pageNumber)
{
    RowIndex = 2,
    ColumnIndex = 2
};
```  

#### 3. Khởi tạo Merger và thực hiện nhúng
Lớp `Merger` xử lý việc chèn thực tế. Sau khi gọi, workbook sẽ chứa biểu tượng OLE.

```csharp
using (Merger merger = new Merger(filePath))
{
    merger.ImportDocument(oleCellsOptions); // Import the specified document as an OLE object into the spreadsheet
    merger.Save(filePathOut); // Save the modified document
}
```  

### Mẹo khắc phục sự cố thường gặp
- Xác minh rằng tất cả các đường dẫn tệp là tuyệt đối hoặc được giải quyết đúng tương đối với tệp thực thi.  
- Đảm bảo số trang bạn chỉ định tồn tại trong PDF nguồn; nếu không sẽ ném ngoại lệ.  
- Nếu đối tượng nhúng không hiển thị, xác nhận rằng phiên bản Excel mục tiêu hỗ trợ OLE (hầu hết các phiên bản hiện đại đều hỗ trợ).

## Ứng dụng thực tế

Nhúng PDF vào Excel hữu ích cho:

1. **Báo cáo tài chính** – đính kèm báo cáo đã kiểm toán trực tiếp bên cạnh các bảng tóm tắt.  
2. **Tài liệu dự án** – giữ các thông số thiết kế, phân tích rủi ro hoặc hợp đồng trong một bảng theo dõi chính.  
3. **Bảng điều khiển đào tạo** – nhúng hướng dẫn sử dụng hoặc PDF chính sách để nhân viên tham khảo nhanh.

## Cân nhắc về hiệu suất

- **Kích thước tệp** – giữ PDF nhúng dưới 5 MB để tránh làm phình workbook.  
- **Sử dụng bộ nhớ** – `GroupDocs.Merger` truyền dữ liệu, vì vậy mức tiêu thụ bộ nhớ vẫn thấp ngay cả với các tệp nguồn lớn.  
- **Giải phóng đối tượng** – luôn gọi `Dispose()` trên các thể hiện `Merger` để giải phóng các handle tệp kịp thời.

## Câu hỏi thường gặp

**Q: OLE object là gì?**  
A: OLE (Object Linking and Embedding) là một đối tượng lưu trữ tệp khác (PDF, Word, hình ảnh, v.v.) bên trong tài liệu chủ, cho phép chỉnh sửa tại chỗ hoặc mở ra.

**Q: Tôi có thể nhúng đối tượng OLE trong các định dạng Office khác không?**  
A: Có — GroupDocs.Merger cũng hỗ trợ các tệp Word, PowerPoint và Visio.

**Q: Làm thế nào để xử lý PDF có mật khẩu?**  
A: Cung cấp mật khẩu khi tạo thể hiện `OleSpreadsheetOptions`; thư viện sẽ tự động giải mã tệp.

**Q: Có giới hạn kích thước cho PDF được nhúng không?**  
A: Kỹ thuật không có giới hạn cứng, nhưng các tệp lớn hơn 10 MB có thể làm tăng đáng kể thời gian tải workbook.

**Q: Tôi có thể tìm thêm ví dụ ở đâu?**  
A: Tham khảo [GroupDocs Documentation](https://docs.groupdocs.com/merger/net/) để có thêm mẫu mã và tham chiếu API.

## Tài nguyên bổ sung
- **Tài liệu**: [GroupDocs.Merger .NET Docs](https://docs.groupdocs.com/merger/net/)  
- **Tham chiếu API**: [GroupDocs API Reference](https://reference.groupdocs.com/merger/net/)  
- **Tải xuống**: [GroupDocs Releases](https://releases.groupdocs.com/merger/net/)  
- **Mua giấy phép GroupDocs**: [Buy GroupDocs License](https://purchase.groupdocs.com/buy)  
- **Dùng thử miễn phí**: [Try GroupDocs Free Trial](https://releases.groupdocs.com/merger/net/)  
- **Giấy phép tạm thời**: [Request Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Diễn đàn hỗ trợ**: [GroupDocs Support Forum](https://forum.groupdocs.com/c/merger)

---

**Cập nhật lần cuối:** 2026-09-21  
**Đã kiểm tra với:** GroupDocs.Merger 23.12 cho .NET  
**Tác giả:** GroupDocs

## Hướng dẫn liên quan

- [Nhúng PDF dưới dạng OLE trong PowerPoint bằng GroupDocs.Merger cho .NET: Hướng dẫn từng bước](/merger/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/)
- [Nhúng PDF trong Word bằng GroupDocs.Merger cho .NET: Hướng dẫn từng bước](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [Tải PDF từ URL trong .NET bằng GroupDocs.Merger: Hướng dẫn toàn diện](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}