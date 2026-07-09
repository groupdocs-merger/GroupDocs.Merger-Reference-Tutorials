---
date: 2026-05-22
description: Tìm hiểu cách tạo các tệp PDF đơn trang và tách PDF bằng GroupDocs.Merger
  cho Java. Bao gồm các hướng dẫn chi tiết từng bước cho split pdf java và hơn nữa.
keywords:
- create single page pdf
- docx to pdf java
- split pdf java
- pdf split by range
- split pdf odd even
schemas:
- author: GroupDocs
  dateModified: '2026-05-22'
  description: Learn how to create single page PDF files and split PDFs using GroupDocs.Merger
    for Java. Includes step-by-step guides for split pdf java and more.
  headline: Create Single Page PDF with GroupDocs.Merger Java
  type: TechArticle
- description: Learn how to create single page PDF files and split PDFs using GroupDocs.Merger
    for Java. Includes step-by-step guides for split pdf java and more.
  name: Create Single Page PDF with GroupDocs.Merger Java
  steps:
  - name: Initialize the Merger
    text: The `Merger` class is GroupDocs.Merger's core component that loads a source
      document and provides split operations. Create an instance by passing the file
      path or an input stream.
  - name: Define the split criteria
    text: Choose the exact page number or range you need. For a single‑page extraction,
      you’ll specify a range like `1‑1`. When you need to **split pdf by range**,
      you can pass multiple ranges such as `1‑5, 6‑10`.
  - name: Execute the split
    text: Call the appropriate `split` method. For example, `merger.split(new int[]{1})`
      extracts the first page, while `merger.splitByRange(new int[][]{{1,5},{6,10}})`
      handles multiple ranges in one call.
  - name: Save the result
    text: Write each output to a file path or return it as a `java.io.InputStream`.
      This makes it easy to integrate with web APIs or store the result in cloud storage.
      > **Pro tip:** When working with large PDFs, call `merger.setOptimizeResources(true)`
      before splitting to reduce memory consumption.
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then perform any split
      operation as usual.
    question: Can I split a password‑protected PDF?
  - answer: Provide a page list containing only odd numbers (e.g., 1,3,5…) to the
      `split` method.
    question: How do I split only the odd pages of a PDF?
  - answer: Absolutely. After loading the DOCX, call `saveAsPdf` on each split segment.
    question: Is it possible to split a DOCX directly into PDFs?
  - answer: PDF, DOCX, PPTX, TXT, HTML, and many image formats (PNG, JPEG, etc.).
    question: What formats does GroupDocs.Merger support for splitting?
  - answer: No. A single GroupDocs.Merger license covers all supported formats.
    question: Do I need a separate license for each file type?
  type: FAQPage
title: Tạo PDF Đơn Trang với GroupDocs.Merger Java
type: docs
url: /vi/java/document-splitting/
weight: 12
---

# Tạo PDF một trang duy nhất với GroupDocs.Merger Java

Nếu bạn cần **create single page PDF** từ các tài liệu lớn hơn hoặc chỉ đơn giản là tách các tệp PDF thành các phần dễ quản lý hơn, bạn đã đến đúng nơi. Hướng dẫn này sẽ đưa bạn qua các kịch bản tách phổ biến nhất — tệp đa trang, phạm vi trang, các trang lẻ/chẵn, tách DOCX, và thậm chí tách dựa trên văn bản — sử dụng thư viện mạnh mẽ GroupDocs.Merger cho Java. Khi kết thúc tutorial này, bạn sẽ biết chính xác cách tích hợp các kỹ thuật này vào ứng dụng của mình, cải thiện hiệu suất xử lý tài liệu và giữ cho mã nguồn sạch sẽ, dễ bảo trì.

## Câu trả lời nhanh
- **“create single page PDF” có nghĩa là gì?** It means extracting one page from a source document and saving it as an independent PDF file.  
- **Thư viện nào thực hiện công việc này?** GroupDocs.Merger for Java provides a fluent API for all splitting operations.  
- **Tôi có cần giấy phép không?** A temporary license works for development; a full license is required for production.  
- **Tôi có thể tách các trang lẻ và chẵn của PDF không?** Yes—GroupDocs.Merger lets you filter pages by odd/even numbers.  
- **Có hỗ trợ tách DOCX không?** Absolutely; you can split DOCX files page‑by‑page or by custom ranges.  

## “create single page PDF” là gì?
Creating a single‑page PDF involves taking a multi‑page source document (PDF, DOCX, PPTX, etc.) and extracting just one page into its own PDF file. This is useful for generating invoices, certificates, or preview images where only a specific page is required.

## Tại sao nên sử dụng GroupDocs.Merger cho Java?
GroupDocs.Merger for Java offers a single, consistent API that handles many document formats while delivering high performance and low memory usage. It simplifies development by abstracting complex file handling, allowing you to focus on business logic rather than low‑level processing details.

- **Unified API** – Works with PDF, DOCX, PPTX, images, and many other formats.  
- **High performance** – Optimized for large files and batch operations; it can process documents up to 2 GB without loading the entire file into memory.  
- **Fine‑grained control** – Split by page range, odd/even pages, or custom delimiters.  
- **Stream‑friendly** – Output can be saved to a file or returned as a stream for web services.

## Yêu cầu trước
- Java 8 or newer.  
- GroupDocs.Merger for Java added to your project (Maven/Gradle).  
- A valid (temporary or full) GroupDocs license file.

## Cách tạo PDF một trang duy nhất?
Creating a single‑page PDF with GroupDocs.Merger involves loading the source file, specifying the exact page or range, invoking the split operation, and finally persisting the result. This workflow ensures the original document remains untouched while the extracted page is saved as an independent PDF file.

The `Merger` class is the core component that loads source documents and provides split functionality.

### Bước 1: Khởi tạo Merger
The `Merger` class is GroupDocs.Merger's core component that loads a source document and provides split operations. Create an instance by passing the file path or an input stream.

### Bước 2: Xác định tiêu chí tách
Choose the exact page number or range you need. For a single‑page extraction, you’ll specify a range like `1‑1`. When you need to **split pdf by range**, you can pass multiple ranges such as `1‑5, 6‑10`.

### Bước 3: Thực hiện tách
Call the appropriate `split` method. For example, `merger.split(new int[]{1})` extracts the first page, while `merger.splitByRange(new int[][]{{1,5},{6,10}})` handles multiple ranges in one call.

### Bước 4: Lưu kết quả
Write each output to a file path or return it as a `java.io.InputStream`. This makes it easy to integrate with web APIs or store the result in cloud storage.

> **Pro tip:** When working with large PDFs, call `merger.setOptimizeResources(true)` before splitting to reduce memory consumption.

## Cách tách các tệp PDF java thành nhiều trang
The `Merger` class provides the primary API for loading and manipulating PDF files. To divide a PDF into separate one‑page files, you simply load the document with the Merger instance and call the split method without parameters. The library automatically creates a new PDF for each page, preserving original content and metadata, which is ideal for batch processing of invoices or reports.

## Cách tách các trang lẻ/chẵn của PDF
The `Merger` class is the core component that performs split operations on documents. When you need only odd or even pages from a PDF, provide a list of the desired page numbers to the split function. The Merger will generate a new document containing just those pages, allowing you to quickly create separate files for odd‑numbered or even‑numbered content.

## Cách tách các tệp docx (cách tách docx)
The `Merger` class also works with DOCX files. Use `splitByPage` to generate one DOCX (or PDF) per page, or combine it with `saveAsPdf` if you need PDF output. This covers the **docx to pdf java** conversion workflow in a single step.

## Cách tách tài liệu thành các tệp đa trang
The `Merger` class handles pagination and file creation for split operations. If you prefer to break a large document into fixed‑size chunks, specify the number of pages per output file. The Merger will iterate through the source, creating new PDFs each containing the defined page count, which simplifies archiving, distribution, and parallel processing of extensive documents.

## Các hướng dẫn có sẵn

### [Cách tách tài liệu thành các tệp đa trang bằng GroupDocs.Merger cho Java](./split-documents-multi-page-files-java-groupdocs-merger/)
Learn how to efficiently split large documents into smaller, multi-page files using GroupDocs.Merger for Java. Optimize document management with ease.

### [Cách tách tệp văn bản theo khoảng dòng bằng GroupDocs.Merger cho Java | Hướng dẫn tách tài liệu](./split-text-file-line-intervals-groupdocs-merger-java/)
Learn how to split text files into manageable sections using line intervals with GroupDocs.Merger for Java. A comprehensive guide for efficient document handling.

### [Tách tài liệu theo phạm vi trang với GroupDocs.Merger cho Java](./split-documents-page-range-groupdocs-merger-java/)
Learn how to split documents into specific page ranges using GroupDocs.Merger for Java. Streamline document management and apply filters like odd/even pages.

### [Tách tài liệu nâng cao với GroupDocs.Merger: Hướng dẫn toàn diện](./master-document-splitting-groupdocs-merger-java/)
Learn how to efficiently split documents into single pages using GroupDocs.Merger for Java. This guide covers setup, implementation, and practical applications.

### [Tách tài liệu Java nâng cao với GroupDocs.Merger: Tách các trang DOCX thành tệp và luồng](./master-java-document-splitting-groupdocs-merger/)
Learn how to efficiently split DOCX documents into separate pages or streams using GroupDocs.Merger for Java. This guide covers setup, implementation, and practical applications.

## Tài nguyên bổ sung

- [Tài liệu GroupDocs.Merger cho Java](https://docs.groupdocs.com/merger/java/)
- [Tham chiếu API GroupDocs.Merger cho Java](https://reference.groupdocs.com/merger/java/)
- [Tải xuống GroupDocs.Merger cho Java](https://releases.groupdocs.com/merger/java/)
- [Diễn đàn GroupDocs.Merger](https://forum.groupdocs.com/c/merger)
- [Hỗ trợ miễn phí](https://forum.groupdocs.com/)
- [Giấy phép tạm thời](https://purchase.groupdocs.com/temporary-license/)

## Các vấn đề thường gặp và giải pháp
| Vấn đề | Giải pháp |
|-------|----------|
| **Quá tải bộ nhớ trên các PDF lớn** | Enable resource optimization: `merger.setOptimizeResources(true);` |
| **Số trang không đúng sau khi tách** | Remember that page indexing starts at 1, not 0. |
| **Không tìm thấy giấy phép** | Verify the path to your `GroupDocs.Merger.lic` file and ensure it’s included in the classpath. |
| **Kết quả tách DOCX có các trang trống** | Ensure the source DOCX has proper page breaks; otherwise, use `splitByParagraph` as a fallback. |

## Câu hỏi thường gặp

**Q: Tôi có thể tách PDF được bảo vệ bằng mật khẩu không?**  
A: Yes. Load the document with the password parameter, then perform any split operation as usual.

**Q: Làm sao tôi chỉ tách các trang lẻ của PDF?**  
A: Provide a page list containing only odd numbers (e.g., 1,3,5…) to the `split` method.

**Q: Có thể tách DOCX trực tiếp thành PDF không?**  
A: Absolutely. After loading the DOCX, call `saveAsPdf` on each split segment.

**Q: GroupDocs.Merger hỗ trợ những định dạng nào để tách?**  
A: PDF, DOCX, PPTX, TXT, HTML, and many image formats (PNG, JPEG, etc.).

**Q: Tôi có cần giấy phép riêng cho mỗi loại tệp không?**  
A: No. A single GroupDocs.Merger license covers all supported formats.

**Cập nhật lần cuối:** 2026-05-22  
**Được kiểm tra với:** GroupDocs.Merger 23.11 for Java  
**Tác giả:** GroupDocs

## Hướng dẫn liên quan

- [split pdf java: Tách tài liệu với GroupDocs.Merger](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [Tách tài liệu theo phạm vi trang với GroupDocs.Merger cho Java](/merger/java/document-splitting/split-documents-page-range-groupdocs-merger-java/)
- [Kết hợp PDF hiệu quả bằng GroupDocs.Merger cho Java: Hướng dẫn từng bước](/merger/java/format-specific-merging/merge-pdfs-groupdocs-merger-java-tutorial/)