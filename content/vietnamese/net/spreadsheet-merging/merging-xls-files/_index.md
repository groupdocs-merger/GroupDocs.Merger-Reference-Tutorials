---
title: Hợp nhất các tệp XLS
linktitle: Hợp nhất các tệp XLS
second_title: API GroupDocs.Merger .NET
description: Tìm hiểu cách hợp nhất các tệp Excel trong .NET bằng GroupDocs.Merger để thao tác tài liệu liền mạch. Thực hiện theo hướng dẫn từng bước của chúng tôi.
type: docs
weight: 11
url: /vi/net/spreadsheet-merging/merging-xls-files/
---
## Giới thiệu
Trong hướng dẫn này, chúng ta sẽ khám phá cách hợp nhất các tệp XLS (Excel). GroupDocs.Merger là API thao tác tài liệu mạnh mẽ cho phép các nhà phát triển hợp nhất, phân tách, sắp xếp lại và thao tác tài liệu một cách dễ dàng trong các ứng dụng .NET của họ. Cụ thể, chúng tôi sẽ tập trung vào việc hợp nhất các tệp XLS từng bước bằng các phương pháp trực quan của GroupDocs.Merger.
## Điều kiện tiên quyết
Trước khi chúng tôi bắt đầu, hãy đảm bảo bạn đã thiết lập các điều kiện tiên quyết sau:
- Visual Studio: Cài đặt Visual Studio trên máy của bạn.
-  GroupDocs.Merger cho .NET: Tải xuống và cài đặt GroupDocs.Merger cho .NET từ[đây](https://releases.groupdocs.com/merger/net/).
- .NET Framework: Đảm bảo bạn đã cài đặt .NET framework.
- Tệp XLS mẫu: Chuẩn bị các tệp XLS bạn muốn hợp nhất.

## Nhập không gian tên
Bắt đầu bằng cách nhập các không gian tên cần thiết để sử dụng GroupDocs.Merger trong dự án của bạn:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Bước 1: Khởi tạo thư mục đầu ra
Đầu tiên, chỉ định thư mục bạn muốn lưu tệp XLS đã hợp nhất:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.xls");
```
## Bước 2: Tải và hợp nhất các tệp XLS
Bây giờ, hãy tải và hợp nhất các tệp XLS bằng GroupDocs.Merger:
```csharp
// Tải tệp XLS nguồn
using (var merger = new Merger("Your Sample File"))
{
    // Thêm một tệp XLS khác để hợp nhất
    merger.Join("Your Sample File");
    
    // Hợp nhất các tệp XLS và lưu kết quả
    merger.Save(outputFile);
}
```
## Bước 3: Hiển thị vị trí đầu ra
Cuối cùng, hiển thị thông báo cho biết hoàn thành và vị trí của tệp XLS đã hợp nhất:
```csharp
Console.WriteLine("\nXLS files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Phần kết luận
Trong hướng dẫn này, chúng ta đã học cách hợp nhất các tệp XLS. Bằng cách làm theo các bước được cung cấp, bạn có thể kết hợp nhiều tệp Excel theo cách lập trình một cách hiệu quả trong các ứng dụng .NET của mình.

## Câu hỏi thường gặp
### GroupDocs.Merger có tương thích với các định dạng tài liệu khác không?
Có, GroupDocs.Merger hỗ trợ nhiều định dạng tài liệu khác nhau như PDF, DOCX, XLSX, PPTX, v.v.
### Tôi có thể chia tài liệu bằng GroupDocs.Merger không?
Tuyệt đối! GroupDocs.Merger cho phép bạn chia nhỏ tài liệu dựa trên yêu cầu của mình.
### Tôi có thể tìm thêm tài nguyên và hỗ trợ cho GroupDocs.Merger ở đâu?
Bạn có thể khám phá tài liệu và đặt câu hỏi về[Diễn đàn GroupDocs](https://forum.groupdocs.com/c/merger/32).
### Có bản dùng thử miễn phí cho GroupDocs.Merger không?
 Có, bạn có thể bắt đầu bằng một[dùng thử miễn phí](https://releases.groupdocs.com/) để đánh giá chức năng.
### Làm cách nào tôi có thể mua giấy phép cho GroupDocs.Merger?
 Tham quan[trang mua hàng](https://purchase.groupdocs.com/buy) để có được giấy phép phù hợp với nhu cầu của bạn.