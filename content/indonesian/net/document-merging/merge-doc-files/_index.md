---
title: Gabungkan File DOC dengan GroupDocs.Merger untuk .NET
linktitle: Gabungkan File DOC dengan GroupDocs.Merger untuk .NET
second_title: GroupDocs.Merger .NET API
description: Pelajari cara menggabungkan file DOC secara terprogram menggunakan GroupDocs.Merger untuk .NET. Ikuti panduan langkah demi langkah kami untuk menggabungkan beberapa dokumen menjadi satu dengan lancar.
weight: 10
url: /id/net/document-merging/merge-doc-files/
---

# Gabungkan File DOC dengan GroupDocs.Merger untuk .NET

## Perkenalan
Dalam tutorial ini, kita akan mempelajari cara menggabungkan file DOC menggunakan GroupDocs.Merger untuk .NET. GroupDocs.Merger for .NET adalah API canggih yang memungkinkan pengembang menggabungkan, membagi, dan memanipulasi berbagai format dokumen secara terprogram. Dengan memanfaatkan API ini, Anda dapat dengan mudah menggabungkan beberapa file DOC menjadi satu dokumen. Kami akan memberikan petunjuk langkah demi langkah untuk memandu Anda melalui proses penggabungan file DOC menggunakan GroupDocs.Merger untuk .NET.
## Prasyarat
Sebelum kita mulai, pastikan Anda telah menyiapkan prasyarat berikut:
1. Visual Studio: Instal Visual Studio di mesin pengembangan Anda.
2.  GroupDocs.Merger untuk .NET: Dapatkan perpustakaan GroupDocs.Merger untuk .NET. Anda dapat mengunduhnya dari[situs web](https://releases.groupdocs.com/merger/net/).
3. Pengetahuan tentang C#: Pemahaman dasar bahasa pemrograman C#.
## Impor Namespace
Untuk mulai bekerja dengan GroupDocs.Merger untuk .NET, impor namespace yang diperlukan ke proyek C# Anda:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Langkah 1: Siapkan Direktori Output
Mulailah dengan menentukan direktori keluaran tempat file DOC gabungan akan disimpan:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.doc");
```
 Mengganti`"Your Output Directory"` dengan jalur ke folder keluaran yang Anda inginkan.
## Langkah 2: Muat File DOC Sumber
Selanjutnya, muat file DOC sumber yang ingin Anda gabungkan menggunakan GroupDocs.Merger:
```csharp
using (var merger = new Merger("Your Sample Document File"))
{
    // Tambahkan file DOC lain untuk digabungkan
    merger.Join("Your Sample Document File 2");
    // Gabungkan file DOC dan simpan hasilnya
    merger.Save(outputFile);
}
```
Dalam cuplikan kode ini:
- `"Your Sample Document File"` Dan`"Your Sample Document File 2"` mewakili jalur ke file DOC yang ingin Anda gabungkan.
- `merger.Join(...)` digunakan untuk menambahkan file DOC lain ke operasi penggabungan.
- `merger.Save(outputFile)` menggabungkan file DOC yang dimuat dan menyimpan dokumen gabungan ke file keluaran yang ditentukan (`merged.doc`).
 Pastikan Anda menggantinya`"Your Sample Document File"` Dan`"Your Sample Document File 2"` dengan jalur sebenarnya ke file DOC Anda.
## Kesimpulan
Dalam tutorial ini, kami telah membahas proses menggabungkan file DOC menggunakan GroupDocs.Merger untuk .NET. Dengan mengikuti langkah-langkah yang diuraikan di atas, Anda dapat menggabungkan beberapa file DOC secara efektif ke dalam satu dokumen secara terprogram. GroupDocs.Merger untuk .NET menyediakan cara yang mudah dan efisien untuk memanipulasi format dokumen dalam aplikasi .NET Anda.

## FAQ
### Bisakah GroupDocs.Merger for .NET menangani format dokumen lain selain DOC?
Ya, GroupDocs.Merger untuk .NET mendukung penggabungan berbagai format dokumen seperti DOCX, PDF, XLSX, PPTX, dan banyak lagi.
### Apakah GroupDocs.Merger untuk .NET kompatibel dengan .NET Core?
Ya, GroupDocs.Merger untuk .NET kompatibel dengan .NET Core dan .NET Framework.
### Apakah GroupDocs.Merger untuk .NET memerlukan lisensi untuk penggunaan komersial?
 Ya, lisensi yang valid diperlukan untuk penggunaan komersial. Anda dapat memperoleh lisensi dari[Grup Dokumen](https://purchase.groupdocs.com/buy).
### Bisakah saya mencoba GroupDocs.Merger untuk .NET secara gratis?
 Ya, Anda dapat menjelajahi GroupDocs.Merger untuk .NET dengan uji coba gratis yang tersedia[Di Sini](https://releases.groupdocs.com/).
### Di mana saya bisa mendapatkan dukungan teknis untuk GroupDocs.Merger untuk .NET?
 Untuk bantuan teknis dan dukungan komunitas, kunjungi[Forum Grup Dokumen](https://forum.groupdocs.com/c/merger/32).