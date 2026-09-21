---
date: '2026-09-21'
description: Pelajari cara menyisipkan PDF ke dalam spreadsheet Excel dengan GroupDocs.Merger
  for .NET, meningkatkan penyajian data dan fungsionalitas.
keywords:
- embed pdf in excel
- how to embed ole
- add ole object excel
- add ole to excel
lastmod: '2026-09-21'
og_description: Pelajari cara menyisipkan PDF di Excel dengan GroupDocs.Merger for
  .NET. Ikuti petunjuk langkah demi langkah, lihat jawaban cepat, dan hindari jebakan
  umum.
og_image_alt: Developer guide showing PDF embedded in an Excel spreadsheet via GroupDocs.Merger
  for .NET
og_title: Cara menyisipkan PDF di Excel menggunakan GroupDocs.Merger for .NET
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
title: Cara menyisipkan PDF di Excel menggunakan GroupDocs.Merger for .NET
type: docs
url: /id/net/document-import/embed-ole-objects-groupdocs-merger-net/
weight: 1
---

# Cara menyematkan PDF di Excel menggunakan GroupDocs.Merger untuk .NET

## Pendahuluan

Menempatkan PDF di Excel memungkinkan Anda menyimpan dokumen pendukung—seperti kontrak, laporan, atau spesifikasi—langsung di tempat data berada. Dengan **GroupDocs.Merger untuk .NET**, Anda dapat menambahkan objek OLE ke sel hanya dengan beberapa baris kode, mengubah spreadsheet biasa menjadi buku kerja interaktif yang berdiri sendiri. Tutorial ini memandu Anda melalui semua yang perlu diketahui, mulai dari instalasi hingga pemecahan masalah.

**Apa yang akan Anda pelajari**

- Cara menyiapkan GroupDocs.Merger untuk .NET dalam proyek C#  
- Langkah-langkah tepat untuk menyematkan PDF (atau file kompatibel OLE apa pun) ke dalam sel Excel  
- Opsi konfigurasi, tips kinerja, dan jebakan umum  

Mari pastikan Anda memiliki semua yang diperlukan sebelum memulai.

## Jawaban Cepat
- **Apakah saya dapat menyematkan jenis file apa pun?** Ya—semua format yang didukung sebagai objek OLE (PDF, Word, gambar, dll.).  
- **Apakah saya memerlukan lisensi untuk pengembangan?** Versi percobaan gratis dapat digunakan untuk pengujian; lisensi permanen diperlukan untuk produksi.  
- **Versi .NET mana yang didukung?** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7+.  
- **Apakah ukuran file Excel akan meningkat secara dramatis?** Hanya sebesar ukuran dokumen yang disematkan; pertahankan file di bawah beberapa MB untuk kinerja terbaik.  
- **Apakah ada batasan jumlah objek OLE?** Praktis tidak ada, tetapi buku kerja yang sangat besar dapat memengaruhi waktu pemuatan.

## Apa itu menyematkan PDF di Excel?

Menempatkan PDF di Excel menyisipkan seluruh PDF sebagai objek OLE yang dapat dibuka langsung dari spreadsheet. Pengguna mengklik ikon dan melihat dokumen asli tanpa meninggalkan Excel. Pendekatan ini mempertahankan tata letak asli, memungkinkan referensi cepat, dan menghilangkan kebutuhan mengelola file terpisah. PDF yang disematkan berperilaku seperti objek OLE lainnya, memungkinkan pengguna mengklik ganda ikon untuk meluncurkan penampil PDF sambil tetap berada dalam lingkungan Excel.

## Mengapa menyematkan objek OLE di Excel?

GroupDocs.Merger mendukung **lebih dari 120 format input dan output** dan dapat menyematkan objek tanpa memuat seluruh file ke memori, memungkinkan pemrosesan cepat PDF berjumlah ratusan halaman. Ini mengurangi kebutuhan repositori file terpisah dan menjaga data terkait tetap bersama. Selain itu, mempermudah kontrol versi dan memastikan semua dokumentasi relevan ikut bersama buku kerja, meningkatkan kolaborasi antar tim.

## Prasyarat

- **GroupDocs.Merger untuk .NET** (paket NuGet terbaru)  
- **.NET Framework** 4.5+ **atau** **.NET Core/5+/6+**  
- Visual Studio 2022 atau yang lebih baru  
- Pengetahuan dasar C# dan familiaritas dengan file I/O  

## Menyiapkan GroupDocs.Merger untuk .NET

### Instalasi

Tambahkan paket menggunakan salah satu metode berikut:

**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI**  
Cari “GroupDocs.Merger” dan instal versi terbaru.

### Akuisisi Lisensi

1. **Free trial** – uji pustaka tanpa biaya.  
2. **Temporary license** – minta lisensi sementara di [halaman lisensi sementara](https://purchase.groupdocs.com/temporary-license/).  
3. **Purchase** – pertimbangkan membeli lisensi di [halaman pembelian GroupDocs](https://purchase.groupdocs.com/buy).

### Inisialisasi Dasar

`Merger` adalah titik masuk untuk semua operasi.  
```csharp
using (Merger merger = new Merger("path_to_your_spreadsheet.xlsx"))
{
    // Your code to work with the document
}
```  

## Cara menyematkan objek OLE di Excel?

Muat workbook sumber Anda, konfigurasikan opsi OLE, dan biarkan `Merger` menyisipkan objek. Bagian berikut memberikan alur kerja singkat yang siap dijalankan.

### Ikhtisar fitur
Menyematkan objek OLE memungkinkan Anda menyimpan PDF lengkap di dalam sel, mempertahankan tata letak asli dan memungkinkan akses satu klik dari Excel.

### Implementasi langkah demi langkah

#### 1. Tetapkan jalur dan nomor halaman
Tentukan spreadsheet, file yang akan disematkan, dan alamat sel target.

```csharp
string filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
string embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_PDF";
int pageNumber = 2; // The specific page to embed

// Output path for the modified spreadsheet
string filePathOut = Path.Combine("YOUR_OUTPUT_DIRECTORY", "OUT_SAMPLE_NAME.xlsx");
```  

#### 2. Konfigurasikan OleSpreadsheetOptions
`OleSpreadsheetOptions` mendefinisikan di mana objek OLE akan ditempatkan di lembar kerja dan bagaimana ikonnya muncul.  
```csharp
// Specify row and column indices for embedding
OleSpreadsheetOptions oleCellsOptions = new OleSpreadsheetOptions(embeddedFilePath, pageNumber)
{
    RowIndex = 2,
    ColumnIndex = 2
};
```  

#### 3. Inisialisasi Merger dan lakukan penyematan
Kelas `Merger` menangani penyisipan sebenarnya. Setelah pemanggilan, workbook berisi ikon OLE.

```csharp
using (Merger merger = new Merger(filePath))
{
    merger.ImportDocument(oleCellsOptions); // Import the specified document as an OLE object into the spreadsheet
    merger.Save(filePathOut); // Save the modified document
}
```  

### Tips pemecahan masalah umum
- Verifikasi bahwa semua jalur file bersifat absolut atau terresolusi dengan benar relatif terhadap executable.  
- Pastikan nomor halaman yang Anda tentukan ada dalam PDF sumber; jika tidak, akan muncul pengecualian.  
- Jika objek yang disematkan tidak tampil, pastikan versi Excel target mendukung OLE (sebagian besar versi modern melakukannya).

## Aplikasi Praktis

Menempatkan PDF di Excel berguna untuk:

1. **Laporan keuangan** – lampirkan pernyataan audit langsung di samping tabel ringkasan.  
2. **Dokumentasi proyek** – simpan spesifikasi desain, analisis risiko, atau kontrak dalam pelacak utama.  
3. **Dashboard pelatihan** – sematkan manual pengguna atau PDF kebijakan untuk referensi cepat oleh staf.

## Pertimbangan Kinerja

- **Ukuran file** – pertahankan PDF yang disematkan di bawah 5 MB untuk menghindari pembengkakan workbook.  
- **Penggunaan memori** – `GroupDocs.Merger` melakukan streaming data, sehingga konsumsi memori tetap rendah bahkan dengan file sumber besar.  
- **Dispose objek** – selalu panggil `Dispose()` pada instance `Merger` untuk melepaskan handle file dengan cepat.

## Pertanyaan yang Sering Diajukan

**Q: Apa itu objek OLE?**  
A: Objek OLE (Object Linking and Embedding) menyimpan file lain (PDF, Word, gambar, dll.) di dalam dokumen host, memungkinkan penyuntingan atau pembukaan di tempat.

**Q: Bisakah saya menyematkan objek OLE dalam format Office lain?**  
A: Ya—GroupDocs.Merger juga mendukung file Word, PowerPoint, dan Visio.

**Q: Bagaimana cara menangani PDF yang dilindungi kata sandi?**  
A: Berikan kata sandi saat membuat instance `OleSpreadsheetOptions`; pustaka akan mendekripsi file secara otomatis.

**Q: Apakah ada batasan ukuran untuk PDF yang disematkan?**  
A: Secara teknis tidak ada batas keras, tetapi file lebih besar dari 10 MB dapat meningkatkan waktu pemuatan workbook secara signifikan.

**Q: Di mana saya dapat menemukan contoh lebih lanjut?**  
A: Kunjungi [Dokumentasi GroupDocs resmi](https://docs.groupdocs.com/merger/net/) untuk contoh kode tambahan dan referensi API.

## Sumber Daya Tambahan
- **Dokumentasi**: [GroupDocs.Merger .NET Docs](https://docs.groupdocs.com/merger/net/)  
- **Referensi API**: [GroupDocs API Reference](https://reference.groupdocs.com/merger/net/)  
- **Unduhan**: [GroupDocs Releases](https://releases.groupdocs.com/merger/net/)  
- **Pembelian lisensi**: [Buy GroupDocs License](https://purchase.groupdocs.com/buy)  
- **Percobaan gratis**: [Try GroupDocs Free Trial](https://releases.groupdocs.com/merger/net/)  
- **Lisensi sementara**: [Request Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Forum dukungan**: [GroupDocs Support Forum](https://forum.groupdocs.com/c/merger)

---

**Terakhir Diperbarui:** 2026-09-21  
**Diuji dengan:** GroupDocs.Merger 23.12 untuk .NET  
**Penulis:** GroupDocs

## Tutorial Terkait

- [Menyematkan PDF sebagai OLE di PowerPoint menggunakan GroupDocs.Merger untuk .NET&#58; Panduan Langkah demi Langkah](/merger/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/)
- [Menyematkan PDF di Word Menggunakan GroupDocs.Merger untuk .NET&#58; Panduan Langkah demi Langkah](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [Memuat PDF dari URL di .NET Menggunakan GroupDocs.Merger&#58; Panduan Komprehensif](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}