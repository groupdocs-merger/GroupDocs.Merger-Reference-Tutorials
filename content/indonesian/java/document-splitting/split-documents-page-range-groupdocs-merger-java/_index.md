---
date: '2026-07-25'
description: Pelajari cara memisahkan halaman dokumen Word menggunakan GroupDocs.Merger
  untuk Java, dengan contoh langkah demi langkah untuk PDF, DOCX, dan PPTX, serta
  filter halaman ganjil/genap.
keywords:
- split word document pages
- how to split pdf
- split pdf by range
- GroupDocs.Merger Java
- document page extraction
lastmod: '2026-07-25'
og_description: Pelajari cara memisahkan halaman dokumen Word menggunakan GroupDocs.Merger
  untuk Java, dengan contoh langkah demi langkah untuk PDF, DOCX, dan PPTX, serta
  filter halaman ganjil/genap.
og_image_alt: Guide to split word document pages using GroupDocs.Merger for Java
og_title: Pisahkan Halaman Dokumen Word dengan GroupDocs.Merger untuk Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-25'
  description: Learn how to split word document pages using GroupDocs.Merger for Java,
    with step‑by‑step examples for PDF, DOCX, and PPTX, plus odd/even page filters.
  headline: Split Word Document Pages with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to split word document pages using GroupDocs.Merger for Java,
    with step‑by‑step examples for PDF, DOCX, and PPTX, plus odd/even page filters.
  name: Split Word Document Pages with GroupDocs.Merger for Java
  steps:
  - name: Define Input and Output Paths
    text: 'Set the source file and the destination pattern for the split files:'
  - name: Configure Split Options (Range & Filter)
    text: 'The `SplitOptions` class tells the library which pages to extract and which
      filter to apply. `RangeMode` is an enumeration that specifies which pages to
      include, such as odd, even, or all pages. The `filePathOut` property defines
      the naming pattern, while `startPage` and `endPage` set the inclusive '
  - name: Perform the Split Operation
    text: 'Execute the split using the configured options:'
  type: HowTo
- questions:
  - answer: GroupDocs.Merger for Java is a robust library that enables merging, splitting,
      and reordering pages across many document formats, including PDF, DOCX, and
      PPTX.
    question: What is GroupDocs.Merger for Java?
  - answer: Yes, similar capabilities exist for .NET and C++.
    question: Can I use GroupDocs.Merger with other programming languages?
  - answer: '`MergerException` is the exception type thrown by GroupDocs.Merger when
      a processing error occurs. Wrap calls in `try‑catch` blocks and inspect `MergerException`
      for detailed error information.'
    question: How do I handle exceptions during document processing?
  - answer: Absolutely—set `RangeMode.AllPages` or omit the filter parameter to split
      by exact page numbers.
    question: Is it possible to split documents without filtering by odd/even pages?
  - answer: Java 8 or higher and a compatible IDE; no additional native dependencies
      are required.
    question: What are the system requirements for using GroupDocs.Merger?
  type: FAQPage
tags:
- split word document pages
- GroupDocs.Merger
- Java document processing
- PDF splitting
- page range extraction
title: Pisahkan Halaman Dokumen Word dengan GroupDocs.Merger untuk Java
type: docs
url: /id/java/document-splitting/split-documents-page-range-groupdocs-merger-java/
weight: 1
---

# Membagi Halaman Dokumen Word dengan GroupDocs.Merger untuk Java

Dalam tutorial ini Anda akan belajar cara **memisahkan halaman dokumen word**—dan format lain seperti PDF dan PPTX—menggunakan GroupDocs.Merger untuk Java. Apakah Anda perlu mengeluarkan satu klausul kontrak, menghasilkan hand‑out dari presentasi, atau memecah laporan besar menjadi bagian‑bagian yang dapat dikelola, API memungkinkan Anda menentukan rentang halaman yang tepat, filter ganjil/genap, atau output satu‑halaman dengan hanya beberapa baris kode.

## Jawaban Cepat
- **Apa arti “extract specific pages”?** Artinya membuat dokumen baru yang hanya berisi halaman yang Anda pilih dari file sumber.  
- **Format apa yang didukung?** PDF, DOCX, PPTX, dan banyak format populer lainnya.  
- **Bisakah saya memfilter berdasarkan halaman ganjil atau genap?** Ya, menggunakan opsi `RangeMode` (misalnya, `OddPages`).  
- **Apakah saya memerlukan lisensi?** Trial gratis dapat digunakan untuk evaluasi; lisensi permanen diperlukan untuk produksi.  
- **Apakah cocok untuk dokumen besar?** Ya—bagi bagian dokumen besar untuk menjaga penggunaan memori tetap rendah.

## Apa itu mengekstrak halaman tertentu?
Mengekstrak halaman tertentu berarti mengambil subset halaman yang dipilih dari dokumen asli dan membuat file baru yang independen yang hanya berisi halaman‑halaman tersebut. Teknik ini berguna untuk menghasilkan laporan terfokus, membagikan klausul kontrak individual, atau mendistribusikan slide presentasi tertentu tanpa mengungkapkan seluruh dokumen sumber.

## Mengapa menggunakan GroupDocs.Merger untuk Java untuk membagi PDF dan dokumen Word?
Muat hanya halaman yang Anda butuhkan dan biarkan GroupDocs.Merger menangani pekerjaan berat. Perpustakaan ini mendukung **lebih dari 50 format input dan output**, dapat memproses file hingga **2 GB** tanpa memuat seluruh dokumen ke memori, dan menyediakan API yang konsisten di seluruh PDF, DOCX, PPTX, dan lainnya—sehingga Anda tidak perlu menggunakan banyak alat.

## Prasyarat
- **GroupDocs.Merger for Java** (versi terbaru)  
- **JDK 8+**  
- Sebuah IDE seperti IntelliJ IDEA atau Eclipse  
- Maven atau Gradle untuk manajemen dependensi  

## Menyiapkan GroupDocs.Merger untuk Java
Tambahkan perpustakaan ke proyek Anda menggunakan alat build pilihan Anda.

**Maven**  
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle**  
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Unduhan Langsung**: Anda juga dapat mengunduh perpustakaan secara langsung dari [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Akuisisi Lisensi
Anda dapat memperoleh lisensi melalui:
- **Trial Gratis** – Menguji semua fitur tanpa batasan.  
- **Lisensi Sementara** – Periode evaluasi yang diperpanjang.  
- **Pembelian** – Lisensi produksi permanen.

**Inisialisasi Dasar dan Penyiapan**  
The `Merger` class adalah titik masuk untuk semua operasi pemisahan. Ia mewakili dokumen dalam memori dan menyediakan metode untuk memanipulasi halaman. Untuk menginisialisasi GroupDocs.Merger, buat sebuah instance `Merger` dengan jalur dokumen Anda:  
```java
import com.groupdocs.merger.Merger;

String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
Merger merger = new Merger(filePath);
```

## Cara mengekstrak halaman tertentu menggunakan GroupDocs.Merger untuk Java
Untuk mengekstrak halaman tertentu, muat dokumen sumber dengan instance `Merger`, konfigurasikan objek `SplitOptions` dengan halaman mulai dan akhir yang diinginkan serta opsional set `RangeMode` (misalnya, `OddPages` atau `EvenPages`). Kemudian panggil `merger.split(options)` yang akan membuat file baru yang hanya berisi halaman yang dipilih.

### Jawaban Langsung
Buat sebuah instance `Merger`, konfigurasikan objek `SplitOptions` dengan `RangeMode.OddPages` dan halaman mulai/akhir yang diinginkan, kemudian panggil `merger.split(options)`. Alur satu‑langkah ini mengekstrak hanya halaman ganjil dalam rentang yang ditentukan dan menuliskannya ke pola output yang Anda berikan.

### Langkah 1: Tentukan Jalur Input dan Output
Tetapkan file sumber dan pola tujuan untuk file hasil pemisahan:  
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToSinglePagesByRangeWithFilter-Output.docx";
```

### Langkah 2: Konfigurasikan Opsi Pemisahan (Rentang & Filter)
Kelas `SplitOptions` memberi tahu perpustakaan halaman mana yang akan diekstrak dan filter apa yang akan diterapkan. `RangeMode` adalah enumerasi yang menentukan halaman mana yang akan disertakan, seperti ganjil, genap, atau semua halaman. Properti `filePathOut` mendefinisikan pola penamaan, sementara `startPage` dan `endPage` menetapkan rentang inklusif. `RangeMode.OddPages` mempertahankan hanya halaman ganjil dalam rentang tersebut, secara efektif **mengekstrak halaman tertentu**.  
```java
import com.groupdocs.merger.domain.options.SplitOptions;
import com.groupdocs.merger.domain.options.RangeMode;

SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7, RangeMode.OddPages);
```

### Langkah 3: Lakukan Operasi Pemisahan
Jalankan pemisahan menggunakan opsi yang telah dikonfigurasi:  
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

#### Tips Pemecahan Masalah
- Pastikan jalur file sudah benar dan dapat diakses.  
- Pastikan nomor halaman berada dalam total jumlah halaman dokumen; jika tidak, pengecualian akan dilempar.  

## Cara membagi PDF menjadi halaman tunggal (split pdf single pages)
Untuk membagi PDF menjadi halaman individual, buka file dengan instance `Merger` dan set `RangeMode.AllPages` dalam objek `SplitOptions`. Tentukan pola penamaan output, lalu panggil `merger.split(options)`. Perpustakaan akan menghasilkan satu file PDF terpisah untuk setiap halaman, mempertahankan konten dan format asli.

## Cara membagi dokumen besar secara efisien (split large document)
Saat memproses dokumen yang sangat besar, bagi menjadi rentang halaman yang lebih kecil (mis., 1‑100, 101‑200) untuk mengurangi konsumsi memori. Buat `SplitOptions` terpisah untuk setiap rentang, jalankan `merger.split(options)` secara berurutan, dan tutup instance `Merger` setelah setiap batch. Pendekatan ini menjaga penggunaan CPU dan I/O tetap dapat dikelola.

## Cara membagi PDF halaman ganjil (split pdf odd pages)
Untuk mengekstrak hanya halaman bernomor ganjil dari PDF, konfigurasikan objek `SplitOptions` dengan `RangeMode.OddPages`. Tetapkan pola output yang diinginkan dan opsional definisikan rentang halaman jika Anda tidak memerlukan seluruh dokumen. Panggil `merger.split(options)` dan perpustakaan akan menghasilkan file yang hanya berisi halaman ganjil.

## Aplikasi Praktis
1. **Segmentasi Dokumen** – Memecah kontrak menjadi PDF per klausul untuk memudahkan peninjauan.  
2. **Manajemen Laporan** – Mengekstrak bab atau lampiran tertentu dari laporan tahunan yang panjang.  
3. **Persiapan Presentasi** – Mengisolasi slide individual untuk pertemuan yang ditargetkan.  

Anda juga dapat mengintegrasikan logika ini dengan basis data atau sistem manajemen konten untuk mengotomatiskan alur kerja.

## Pertimbangan Kinerja
- **Manajemen Memori** – Panggil `merger.close()` (atau gunakan try‑with‑resources) setelah pemrosesan untuk melepaskan handle file.  
- **Rentang Selektif** – Hanya minta halaman yang benar‑benar Anda butuhkan; ini meminimalkan penggunaan I/O dan CPU.

## Kesimpulan
Anda kini memiliki metode langkah‑demi‑langkah yang jelas untuk **membagi halaman dokumen word** (dan format lain yang didukung) menggunakan GroupDocs.Merger untuk Java. Kemampuan ini menyederhanakan alur kerja dokumen Anda dan memungkinkan Anda menyajikan konten yang tepat sesuai kebutuhan pengguna.

### Langkah Selanjutnya
- Bereksperimen dengan nilai `RangeMode` yang berbeda (mis., `EvenPages`, `AllPages`).  
- Gabungkan pemisahan dengan fungsi **merge** untuk menyusun ulang atau menggabungkan halaman yang diekstrak.  
- Jelajahi seluruh API untuk dokumen yang dilindungi kata sandi, watermark, dan lainnya.  

## Pertanyaan yang Sering Diajukan
**Q: Apa itu GroupDocs.Merger untuk Java?**  
A: GroupDocs.Merger untuk Java adalah perpustakaan yang kuat yang memungkinkan penggabungan, pemisahan, dan penyusunan ulang halaman di banyak format dokumen, termasuk PDF, DOCX, dan PPTX.

**Q: Bisakah saya menggunakan GroupDocs.Merger dengan bahasa pemrograman lain?**  
A: Ya, kemampuan serupa tersedia untuk .NET dan C++.

**Q: Bagaimana cara menangani pengecualian selama pemrosesan dokumen?**  
A: `MergerException` adalah tipe pengecualian yang dilempar oleh GroupDocs.Merger ketika terjadi kesalahan pemrosesan. Bungkus pemanggilan dalam blok `try‑catch` dan periksa `MergerException` untuk informasi detail tentang kesalahan.

**Q: Apakah memungkinkan membagi dokumen tanpa memfilter halaman ganjil/genap?**  
A: Tentu—set `RangeMode.AllPages` atau hilangkan parameter filter untuk membagi berdasarkan nomor halaman yang tepat.

**Q: Apa persyaratan sistem untuk menggunakan GroupDocs.Merger?**  
A: Java 8 atau lebih tinggi dan IDE yang kompatibel; tidak diperlukan dependensi native tambahan.

## Sumber Daya
- [Dokumentasi GroupDocs.Merger](https://docs.groupdocs.com/merger/java/)
- [Referensi API](https://reference.groupdocs.com/merger/java/)
- [Unduh Perpustakaan](https://releases.groupdocs.com/merger/java/)
- [Beli Lisensi](https://purchase.groupdocs.com/buy)
- [Trial Gratis dan Lisensi Sementara](https://releases.groupdocs.com/merger/java/)
- [Forum Dukungan](https://forum.groupdocs.com/c/merger/)

---

**Terakhir Diperbarui:** 2026-07-25  
**Diuji Dengan:** Versi terbaru GroupDocs.Merger (Java)  
**Penulis:** GroupDocs

## Tutorial Terkait
- [Menghapus Halaman Secara Efisien dari Dokumen Word Menggunakan GroupDocs.Merger untuk Java](/merger/java/page-operations/remove-pages-groupdocs-merger-java-word-documents/)
- [Manajemen Dokumen Master - Menggabungkan Dokumen Word dengan GroupDocs.Merger untuk Java](/merger/java/document-joining/groupdocs-merger-java-word-document-management/)
- [Cara Membagi Dokumen menjadi File Multi‑Halaman Menggunakan GroupDocs.Merger untuk Java](/merger/java/document-splitting/split-documents-multi-page-files-java-groupdocs-merger/)