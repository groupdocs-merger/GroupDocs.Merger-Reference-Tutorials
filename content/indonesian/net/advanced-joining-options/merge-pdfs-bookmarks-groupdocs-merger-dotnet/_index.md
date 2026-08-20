---
date: '2026-08-20'
description: Pelajari cara menggabungkan PDF dengan bookmark menggunakan GroupDocs.Merger
  untuk .NET, termasuk pengaturan, contoh kode, dan praktik terbaik untuk menggabungkan
  dokumen PDF.
keywords:
- merge pdfs with bookmarks
- merge pdf with bookmarks
- combine pdf documents c#
lastmod: '2026-08-20'
og_description: Pelajari cara menggabungkan PDF dengan bookmark menggunakan GroupDocs.Merger
  untuk .NET. Ikuti kode langkah‑demi‑langkah untuk menggabungkan dokumen PDF sambil
  mempertahankan navigasi.
og_image_alt: Guide showing PDF merge with bookmarks in .NET using GroupDocs.Merger
og_title: Cara menggabungkan PDF dengan bookmark menggunakan GroupDocs.Merger untuk
  .NET
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for .NET,
    including setup, code examples, and best practices for combining PDF documents.
  headline: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for .NET,
    including setup, code examples, and best practices for combining PDF documents.
  name: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
  steps:
  - name: define directory paths
    text: Set up source and output folders so the code can locate the PDFs you want
      to merge. csharp string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY"; string
      outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
  - name: load the primary PDF
    text: '`Merger` represents the main document you’ll append others to. csharp using
      (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
      { // Code to merge additional files will be here. }'
  - name: configure bookmark‑preserving options
    text: '`PdfJoinOptions` controls how the merge behaves; the `UseBookmarks` flag
      tells the engine to keep existing bookmarks. csharp var pdfJoinOptions = new
      PdfJoinOptions { UseBookmarks = true };'
  - name: add additional PDFs
    text: Call `Join` for each extra file. The library automatically merges their
      bookmark trees under the main document’s outline. csharp merger.Join(Path.Combine(documentDirectory,
      "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
  - name: save the merged PDF
    text: Specify the output path and format; the library writes a single PDF that
      retains all bookmark entries. csharp string outputFile = Path.Combine(outputDirectory,
      "merged.pdf"); merger.Save(outputFile);
  type: HowTo
- questions:
  - answer: GroupDocs.Merger is a .NET library that lets you merge, split, rotate,
      and otherwise manipulate PDF and other document formats programmatically.
    question: What is GroupDocs.Merger?
  - answer: Yes – call `Join` repeatedly or pass a collection of file paths to merge
      any number of PDFs in one operation.
    question: Can I merge more than two PDF files at a time?
  - answer: Obtain a permanent license from the GroupDocs purchase page; the trial
      license works only for evaluation and expires after 30 days.
    question: How do I handle licensing for production use?
  - answer: Ensure `PdfJoinOptions.UseBookmarks` is set to `true` and that each source
      PDF actually contains bookmarks before merging.
    question: My merged PDF shows no bookmarks—what went wrong?
  - answer: Absolutely – it supports .NET Core 3.1+, .NET 5/6, and the full .NET Framework
      4.6.1+.
    question: Is the library compatible with .NET Core and .NET Framework?
  type: FAQPage
tags:
- merge pdf
- GroupDocs.Merger
- .NET PDF processing
title: Cara menggabungkan PDF dengan bookmark menggunakan GroupDocs.Merger untuk .NET
type: docs
url: /id/net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/
weight: 1
---

# Cara menggabungkan pdf dengan bookmark menggunakan GroupDocs.Merger untuk .NET

Menggabungkan beberapa file PDF sambil mempertahankan bookmark asli dapat menghemat berjam‑jam kerja manual. Dalam tutorial ini Anda akan belajar cara **menggabungkan pdf dengan bookmark** menggunakan GroupDocs.Merger untuk .NET, mulai dari penyiapan proyek hingga contoh kode lengkap yang siap produksi.

## Jawaban Cepat
- **Perpustakaan mana yang mendukung penggabungan yang mempertahankan bookmark?** GroupDocs.Merger untuk .NET.  
- **Bisakah saya menggabungkan lebih dari dua PDF sekaligus?** Ya – tambahkan sebanyak file sumber yang Anda perlukan.  
- **Apakah saya memerlukan lisensi untuk pengembangan?** Versi percobaan gratis dapat digunakan untuk pengujian; lisensi permanen diperlukan untuk produksi.  
- **Apakah .NET Core didukung?** Tentu – perpustakaan ini bekerja dengan .NET Core, .NET 5/6, dan .NET Framework lengkap.  
- **Berapa ukuran file terbesar yang dapat ditangani?** Hingga 2 GB per dokumen, diproses tanpa memuat seluruh file ke memori.

## Apa itu menggabungkan pdf dengan bookmark?
**Menggabungkan pdf dengan bookmark** berarti mengambil beberapa dokumen PDF dan menggabungkannya menjadi satu file sekaligus menjaga hierarki bookmark masing‑masing dokumen sumber tetap utuh. PDF yang dihasilkan mempertahankan struktur navigasi asli, memungkinkan pembaca melompat langsung ke bagian‑bagian yang berasal dari tiap file individu, yang sangat penting untuk laporan besar atau manual yang dikompilasi.

## Mengapa menggabungkan pdf dengan bookmark?
Mempertahankan bookmark saat menggabungkan PDF meningkatkan navigasi dalam dokumen yang dikonsolidasikan, memungkinkan pengguna dengan cepat menemukan bab atau bagian tertentu tanpa harus menggulir seluruh file. GroupDocs.Merger menjaga hierarki outline asli, mengurangi upaya reorganisasi manual, dan mendukung file besar hingga 2 GB dengan penggunaan memori minimal, menjadikannya ideal untuk alur kerja berskala perusahaan.

## Prasyarat
- **.NET Core SDK** (3.1 atau lebih baru) atau **.NET Framework** (4.6.1+).  
- **Visual Studio 2022** atau IDE apa pun yang mendukung pengembangan .NET.  
- Pengetahuan dasar C# dan familiaritas dengan I/O file.  

## Menyiapkan GroupDocs.Merger untuk .NET

### Instalasi
Tambahkan perpustakaan ke proyek Anda dengan salah satu perintah berikut:

**.NET CLI:**  
```  
```bash
dotnet add package GroupDocs.Merger
```  
```  

**Package Manager:**  
```  
```powershell
Install-Package GroupDocs.Merger
```  
```  

**NuGet Package Manager UI:**  
- Cari “GroupDocs.Merger” dan instal versi terbaru.

### Akuisisi Lisensi
- **Versi percobaan:** Unduh dari halaman [GroupDocs Releases](https://releases.groupdocs.com/merger/net/).  
- **Lisensi sementara:** Dapatkan melalui [GroupDocs Temporary License Page](https://purchase.groupdocs.com/temporary-license/).  
- **Lisensi penuh:** Beli di [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy).

### Inisialisasi Dasar
Kelas `Merger` adalah titik masuk untuk semua operasi penggabungan.  
```  
```csharp
using GroupDocs.Merger;
```  
```  
Namespace ini memberi Anda akses ke seluruh rangkaian fitur manipulasi PDF.

## Cara menggabungkan pdf dengan bookmark di .NET

Muat PDF utama Anda, konfigurasikan penanganan bookmark, tambahkan file tambahan, dan simpan hasilnya – semua dalam beberapa baris kode yang singkat.

**Jawaban langsung (40‑70 kata):**  
Buat instance `Merger` dengan PDF pertama, aktifkan `PdfJoinOptions.UseBookmarks`, tambahkan setiap PDF berikutnya melalui `Join`, dan panggil `Save` untuk menulis file gabungan. Pendekatan ini mempertahankan setiap hierarki bookmark asli dan dijalankan dalam satu kali proses, meminimalkan konsumsi memori.

### Langkah 1: definisikan jalur direktori
Siapkan folder sumber dan output sehingga kode dapat menemukan PDF yang ingin Anda gabungkan.  
```  
```csharp
   string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY";
   string outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
   ```  
```  

### Langkah 2: muat PDF utama
`Merger` mewakili dokumen utama yang akan Anda tambahkan dokumen lain.  
```  
```csharp
   using (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
   {
       // Kode untuk menggabungkan file tambahan akan ditempatkan di sini.
   }
   ```  
```  

### Langkah 3: konfigurasikan opsi yang mempertahankan bookmark
`PdfJoinOptions` mengontrol cara penggabungan berperilaku; flag `UseBookmarks` memberi tahu mesin untuk mempertahankan bookmark yang ada.  
```  
```csharp
   var pdfJoinOptions = new PdfJoinOptions { UseBookmarks = true };
   ```  
```  

### Langkah 4: tambahkan PDF tambahan
Panggil `Join` untuk setiap file ekstra. Perpustakaan secara otomatis menggabungkan pohon bookmark mereka di bawah outline dokumen utama.  
```  
```csharp
   merger.Join(Path.Combine(documentDirectory, "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
   ```  
```  

### Langkah 5: simpan PDF yang telah digabung
Tentukan jalur output dan format; perpustakaan menulis satu PDF yang mempertahankan semua entri bookmark.  
```  
```csharp
   string outputFile = Path.Combine(outputDirectory, "merged.pdf");
   merger.Save(outputFile);
   ```  
```  

## Masalah umum dan solusi
- **Bookmark tidak muncul:** Pastikan `UseBookmarks = true` di `PdfJoinOptions`.  
- **Kesalahan jalur:** Gunakan `Path.Combine` dan periksa keberadaan file sebelum menggabungkan.  
- **File besar menyebabkan lonjakan memori:** Proses PDF secara berurutan dan buang objek `Merger` setelah setiap penyimpanan.

## Aplikasi praktis
1. **Menggabungkan laporan keuangan** – pertahankan bagian kuartalan dapat diakses langsung melalui bookmark.  
2. **Paket materi kuliah** – gabungkan PDF kuliah sambil mempertahankan navigasi bab untuk mahasiswa.  
3. **Bundel dokumentasi proyek** – satukan spesifikasi desain, rencana uji, dan catatan rilis menjadi satu file yang dapat dicari.

## Pertimbangan kinerja
- Proses satu file pada satu waktu ketika menggabungkan lebih dari 20 PDF untuk menjaga penggunaan RAM tetap rendah.  
- Gunakan runtime .NET terbaru (misalnya .NET 6) untuk kompilasi JIT optimal dan efisiensi garbage‑collection.  
- Untuk PDF lebih besar dari 500 MB, aktifkan mode streaming melalui `MergerSettings` agar tidak memuat seluruh dokumen ke memori.

## Pertanyaan yang sering diajukan

**T: Apa itu GroupDocs.Merger?**  
J: GroupDocs.Merger adalah perpustakaan .NET yang memungkinkan Anda menggabungkan, memisahkan, memutar, dan memanipulasi format dokumen PDF serta format dokumen lainnya secara programatik.

**T: Bisakah saya menggabungkan lebih dari dua file PDF sekaligus?**  
J: Ya – panggil `Join` berulang kali atau berikan koleksi jalur file untuk menggabungkan sejumlah PDF dalam satu operasi.

**T: Bagaimana cara menangani lisensi untuk penggunaan produksi?**  
J: Dapatkan lisensi permanen dari halaman pembelian GroupDocs; lisensi percobaan hanya berlaku untuk evaluasi dan kedaluwarsa setelah 30 hari.

**T: PDF yang saya gabungkan tidak menampilkan bookmark—apa yang salah?**  
J: Pastikan `PdfJoinOptions.UseBookmarks` disetel ke `true` dan setiap PDF sumber memang berisi bookmark sebelum digabungkan.

**T: Apakah perpustakaan ini kompatibel dengan .NET Core dan .NET Framework?**  
J: Tentu – ia mendukung .NET Core 3.1+, .NET 5/6, dan .NET Framework lengkap 4.6.1+.

## Sumber daya
- [Documentation](https://docs.groupdocs.com/merger/net/)  
- [API Reference](https://reference.groupdocs.com/merger/net/)  
- [Download GroupDocs.Merger](https://releases.groupdocs.com/merger/net/)  
- [Purchase License](https://purchase.groupdocs.com/buy)  
- [Free Trial Version](https://releases.groupdocs.com/merger/net/)  
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- [Support Forum](https://forum.groupdocs.com/c/merger/)  

---

**Terakhir Diperbarui:** 2026-08-20  
**Diuji Dengan:** GroupDocs.Merger 23.11 untuk .NET  
**Penulis:** GroupDocs

## Tutorial Terkait

- [How to Merge Specific PDF Pages with GroupDocs.Merger for .NET: A Comprehensive Guide](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [How to Easily Join Documents Using GroupDocs.Merger for .NET: A Comprehensive Guide](/merger/net/document-joining/groupdocs-merger-net-document-joining-guide/)
- [Add Attachments to PDFs Using GroupDocs.Merger for .NET: A Step-by-Step Guide](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)