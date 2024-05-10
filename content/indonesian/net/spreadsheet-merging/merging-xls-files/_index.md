---
title: Menggabungkan File XLS
linktitle: Menggabungkan File XLS
second_title: GroupDocs.Merger .NET API
description: Pelajari cara menggabungkan file Excel di .NET menggunakan GroupDocs.Merger untuk manipulasi dokumen yang lancar. Ikuti tutorial langkah demi langkah kami.
type: docs
weight: 11
url: /id/net/spreadsheet-merging/merging-xls-files/
---
## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menggabungkan file XLS (Excel). GroupDocs.Merger adalah API manipulasi dokumen canggih yang memungkinkan pengembang menggabungkan, membagi, mengatur ulang, dan memanipulasi dokumen dengan mudah dalam aplikasi .NET mereka. Secara khusus, kami akan fokus pada penggabungan file XLS langkah demi langkah menggunakan metode intuitif GroupDocs.Merger.
## Prasyarat
Sebelum kita mulai, pastikan Anda telah menyiapkan prasyarat berikut:
- Visual Studio: Instal Visual Studio di mesin Anda.
-  GroupDocs.Merger untuk .NET: Unduh dan instal GroupDocs.Merger untuk .NET dari[Di Sini](https://releases.groupdocs.com/merger/net/).
- .NET Framework: Pastikan Anda telah menginstal .NET framework.
- Contoh File XLS: Siapkan file XLS yang ingin Anda gabungkan.

## Impor Namespace
Mulailah dengan mengimpor namespace yang diperlukan untuk menggunakan GroupDocs.Merger di proyek Anda:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Langkah 1: Inisialisasi Direktori Output
Pertama, tentukan direktori tempat Anda ingin menyimpan file XLS yang digabungkan:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.xls");
```
## Langkah 2: Muat dan Gabungkan File XLS
Sekarang, mari muat dan gabungkan file XLS menggunakan GroupDocs.Merger:
```csharp
// Muat file XLS sumber
using (var merger = new Merger("Your Sample File"))
{
    // Tambahkan file XLS lain untuk digabungkan
    merger.Join("Your Sample File");
    
    // Gabungkan file XLS dan simpan hasilnya
    merger.Save(outputFile);
}
```
## Langkah 3: Tampilkan Lokasi Keluaran
Terakhir, tampilkan pesan yang menunjukkan penyelesaian dan lokasi file XLS yang digabungkan:
```csharp
Console.WriteLine("\nXLS files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Kesimpulan
Dalam tutorial ini, kita telah mempelajari cara menggabungkan file XLS. Dengan mengikuti langkah-langkah yang disediakan, Anda dapat menggabungkan beberapa file Excel secara efisien secara terprogram dalam aplikasi .NET Anda.

## FAQ
### Apakah GroupDocs.Merger kompatibel dengan format dokumen lain?
Ya, GroupDocs.Merger mendukung berbagai format dokumen seperti PDF, DOCX, XLSX, PPTX, dan lainnya.
### Bisakah saya membagi dokumen menggunakan GroupDocs.Merger?
Sangat! GroupDocs.Merger memungkinkan Anda membagi dokumen berdasarkan kebutuhan Anda.
### Di mana saya dapat menemukan lebih banyak sumber daya dan dukungan untuk GroupDocs.Merger?
Anda dapat menjelajahi dokumentasi dan mengajukan pertanyaan di[Forum Grup Dokumen](https://forum.groupdocs.com/c/merger/32).
### Apakah ada uji coba gratis yang tersedia untuk GroupDocs.Merger?
 Ya, Anda bisa mulai dengan a[uji coba gratis](https://releases.groupdocs.com/) untuk mengevaluasi fungsionalitasnya.
### Bagaimana saya bisa membeli lisensi untuk GroupDocs.Merger?
 Mengunjungi[halaman pembelian](https://purchase.groupdocs.com/buy) untuk memperoleh lisensi yang disesuaikan dengan kebutuhan Anda.