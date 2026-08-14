---
date: 2026-05-22
description: Pelajari cara membuat file PDF satu halaman dan memisahkan PDF menggunakan
  GroupDocs.Merger untuk Java. Termasuk panduan langkah demi langkah untuk split pdf
  java dan lainnya.
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
title: Buat PDF Satu Halaman dengan GroupDocs.Merger Java
type: docs
url: /id/java/document-splitting/
weight: 12
---

# Buat PDF Satu Halaman dengan GroupDocs.Merger Java

Jika Anda perlu **membuat PDF satu halaman** dari dokumen yang lebih besar atau sekadar memisahkan PDF menjadi bagian‑bagian yang lebih mudah dikelola, Anda berada di tempat yang tepat. Panduan ini akan membawa Anda melalui skenario pemisahan yang paling umum—file multi‑halaman, rentang halaman, halaman ganjil/genap, pemisahan DOCX, dan bahkan pemisahan berbasis teks—menggunakan pustaka kuat GroupDocs.Merger untuk Java. Pada akhir tutorial ini Anda akan tahu persis cara mengintegrasikan teknik‑teknik ini ke dalam aplikasi Anda, meningkatkan kinerja penanganan dokumen, dan menjaga basis kode tetap bersih serta mudah dipelihara.

## Jawaban Cepat
- **Apa arti “create single page PDF”?** Itu berarti mengekstrak satu halaman dari dokumen sumber dan menyimpannya sebagai file PDF yang independen.  
- **Perpustakaan mana yang menangani pekerjaan ini?** GroupDocs.Merger untuk Java menyediakan API yang fluida untuk semua operasi pemisahan.  
- **Apakah saya memerlukan lisensi?** Lisensi sementara dapat digunakan untuk pengembangan; lisensi penuh diperlukan untuk produksi.  
- **Bisakah saya memisahkan PDF halaman ganjil dan genap?** Ya—GroupDocs.Merger memungkinkan Anda memfilter halaman berdasarkan nomor ganjil/genap.  
- **Apakah pemisahan DOCX didukung?** Tentu saja; Anda dapat memisahkan file DOCX halaman‑per‑halaman atau berdasarkan rentang khusus.  

## Apa itu “create single page PDF”?
Membuat PDF satu halaman melibatkan mengambil dokumen sumber multi‑halaman (PDF, DOCX, PPTX, dll.) dan mengekstrak hanya satu halaman ke dalam file PDF terpisah. Ini berguna untuk menghasilkan faktur, sertifikat, atau gambar pratinjau di mana hanya halaman tertentu yang diperlukan.

## Mengapa menggunakan GroupDocs.Merger untuk Java?
GroupDocs.Merger untuk Java menawarkan satu API konsisten yang menangani banyak format dokumen sekaligus memberikan kinerja tinggi dan penggunaan memori rendah. Ini menyederhanakan pengembangan dengan mengabstraksi penanganan file yang kompleks, memungkinkan Anda fokus pada logika bisnis daripada detail pemrosesan tingkat rendah.

- **Unified API** – Bekerja dengan PDF, DOCX, PPTX, gambar, dan banyak format lainnya.  
- **High performance** – Dioptimalkan untuk file besar dan operasi batch; dapat memproses dokumen hingga 2 GB tanpa memuat seluruh file ke memori.  
- **Fine‑grained control** – Memisahkan berdasarkan rentang halaman, halaman ganjil/genap, atau delimiter khusus.  
- **Stream‑friendly** – Output dapat disimpan ke file atau dikembalikan sebagai stream untuk layanan web.

## Prasyarat
- Java 8 atau yang lebih baru.  
- GroupDocs.Merger untuk Java telah ditambahkan ke proyek Anda (Maven/Gradle).  
- File lisensi GroupDocs yang valid (sementara atau penuh).

## Cara Membuat PDF Satu Halaman?
Membuat PDF satu halaman dengan GroupDocs.Merger melibatkan memuat file sumber, menentukan halaman atau rentang yang tepat, memanggil operasi pemisahan, dan akhirnya menyimpan hasilnya. Alur kerja ini memastikan dokumen asli tetap tidak tersentuh sementara halaman yang diekstrak disimpan sebagai file PDF independen.

Kelas `Merger` adalah komponen inti yang memuat dokumen sumber dan menyediakan fungsi pemisahan.

### Langkah 1: Inisialisasi Merger
Kelas `Merger` adalah komponen inti GroupDocs.Merger yang memuat dokumen sumber dan menyediakan operasi pemisahan. Buat sebuah instance dengan memberikan jalur file atau input stream.

### Langkah 2: Tentukan Kriteria Pemisahan
Pilih nomor halaman atau rentang yang tepat yang Anda butuhkan. Untuk ekstraksi satu halaman, Anda akan menentukan rentang seperti `1‑1`. Ketika Anda perlu **split pdf by range**, Anda dapat memberikan beberapa rentang seperti `1‑5, 6‑10`.

### Langkah 3: Jalankan Pemisahan
Panggil metode `split` yang sesuai. Misalnya, `merger.split(new int[]{1})` mengekstrak halaman pertama, sementara `merger.splitByRange(new int[][]{{1,5},{6,10}})` menangani beberapa rentang dalam satu panggilan.

### Langkah 4: Simpan Hasil
Tuliskan setiap output ke jalur file atau kembalikan sebagai `java.io.InputStream`. Ini memudahkan integrasi dengan API web atau penyimpanan hasil di cloud.

> **Pro tip:** Saat bekerja dengan PDF besar, panggil `merger.setOptimizeResources(true)` sebelum melakukan pemisahan untuk mengurangi konsumsi memori.

## Cara Memisahkan File PDF Java menjadi Beberapa Halaman
Kelas `Merger` menyediakan API utama untuk memuat dan memanipulasi file PDF. Untuk membagi PDF menjadi file satu‑halaman terpisah, cukup muat dokumen dengan instance Merger dan panggil metode split tanpa parameter. Pustaka secara otomatis membuat PDF baru untuk setiap halaman, mempertahankan konten dan metadata asli, yang ideal untuk pemrosesan batch faktur atau laporan.

## Cara Memisahkan Halaman Ganjil Genap PDF
Kelas `Merger` adalah komponen inti yang melakukan operasi pemisahan pada dokumen. Ketika Anda hanya memerlukan halaman ganjil atau genap dari PDF, berikan daftar nomor halaman yang diinginkan ke fungsi split. Merger akan menghasilkan dokumen baru yang berisi hanya halaman‑halaman tersebut, memungkinkan Anda dengan cepat membuat file terpisah untuk konten bernomor ganjil atau genap.

## Cara Memisahkan File docx (cara memisahkan docx)
Kelas `Merger` juga bekerja dengan file DOCX. Gunakan `splitByPage` untuk menghasilkan satu DOCX (atau PDF) per halaman, atau gabungkan dengan `saveAsPdf` jika Anda memerlukan output PDF. Ini mencakup alur kerja konversi **docx to pdf java** dalam satu langkah.

## Cara Memisahkan Dokumen menjadi File Multi‑Halaman
Kelas `Merger` menangani pagination dan pembuatan file untuk operasi pemisahan. Jika Anda lebih suka memecah dokumen besar menjadi potongan berukuran tetap, tentukan jumlah halaman per file output. Merger akan mengiterasi sumber, membuat PDF baru yang masing‑masing berisi jumlah halaman yang ditentukan, yang menyederhanakan pengarsipan, distribusi, dan pemrosesan paralel dokumen yang luas.

## Tutorial yang Tersedia

### [Cara Memisahkan Dokumen menjadi File Multi‑Halaman Menggunakan GroupDocs.Merger untuk Java](./split-documents-multi-page-files-java-groupdocs-merger/)
Pelajari cara memisahkan dokumen besar menjadi file‑file multi‑halaman yang lebih kecil secara efisien menggunakan GroupDocs.Merger untuk Java. Optimalkan manajemen dokumen dengan mudah.

### [Cara Memisahkan File Teks berdasarkan Interval Baris Menggunakan GroupDocs.Merger untuk Java | Panduan Pemisahan Dokumen](./split-text-file-line-intervals-groupdocs-merger-java/)
Pelajari cara memisahkan file teks menjadi bagian‑bagian yang dapat dikelola menggunakan interval baris dengan GroupDocs.Merger untuk Java. Panduan komprehensif untuk penanganan dokumen yang efisien.

### [Menguasai Pemisahan Dokumen berdasarkan Rentang Halaman dengan GroupDocs.Merger untuk Java](./split-documents-page-range-groupdocs-merger-java/)
Pelajari cara memisahkan dokumen menjadi rentang halaman tertentu menggunakan GroupDocs.Merger untuk Java. Sederhanakan manajemen dokumen dan terapkan filter seperti halaman ganjil/genap.

### [Menguasai Pemisahan Dokumen dengan GroupDocs.Merger&#58; Panduan Komprehensif](./master-document-splitting-groupdocs-merger-java/)
Pelajari cara memisahkan dokumen menjadi halaman tunggal secara efisien menggunakan GroupDocs.Merger untuk Java. Panduan ini mencakup pengaturan, implementasi, dan aplikasi praktis.

### [Menguasai Pemisahan Dokumen Java dengan GroupDocs.Merger&#58; Memisahkan Halaman DOCX menjadi File dan Stream](./master-java-document-splitting-groupdocs-merger/)
Pelajari cara memisahkan dokumen DOCX menjadi halaman terpisah atau stream menggunakan GroupDocs.Merger untuk Java. Panduan ini mencakup pengaturan, implementasi, dan aplikasi praktis.

## Sumber Daya Tambahan

- [Dokumentasi GroupDocs.Merger untuk Java](https://docs.groupdocs.com/merger/java/)
- [Referensi API GroupDocs.Merger untuk Java](https://reference.groupdocs.com/merger/java/)
- [Unduh GroupDocs.Merger untuk Java](https://releases.groupdocs.com/merger/java/)
- [Forum GroupDocs.Merger](https://forum.groupdocs.com/c/merger)
- [Dukungan Gratis](https://forum.groupdocs.com/)
- [Lisensi Sementara](https://purchase.groupdocs.com/temporary-license/)

## Masalah Umum dan Solusinya
| Issue | Solution |
|-------|----------|
| **Memory overload on large PDFs** | Aktifkan optimasi sumber daya: `merger.setOptimizeResources(true);` |
| **Incorrect page numbers after splitting** | Ingat bahwa indeks halaman dimulai dari 1, bukan 0. |
| **License not found** | Verifikasi jalur ke file `GroupDocs.Merger.lic` Anda dan pastikan file tersebut termasuk dalam classpath. |
| **Splitting DOCX results in empty pages** | Pastikan DOCX sumber memiliki pemisah halaman yang tepat; jika tidak, gunakan `splitByParagraph` sebagai alternatif. |

## Pertanyaan yang Sering Diajukan

**Q: Bisakah saya memisahkan PDF yang dilindungi kata sandi?**  
A: Ya. Muat dokumen dengan parameter kata sandi, kemudian lakukan operasi pemisahan apa pun seperti biasa.

**Q: Bagaimana cara memisahkan hanya halaman ganjil dari PDF?**  
A: Berikan daftar halaman yang hanya berisi nomor ganjil (mis., 1,3,5…) ke metode `split`.

**Q: Apakah memungkinkan memisahkan DOCX langsung menjadi PDF?**  
A: Tentu saja. Setelah memuat DOCX, panggil `saveAsPdf` pada setiap segmen yang dipisahkan.

**Q: Format apa saja yang didukung GroupDocs.Merger untuk pemisahan?**  
A: PDF, DOCX, PPTX, TXT, HTML, dan banyak format gambar (PNG, JPEG, dll.).

**Q: Apakah saya memerlukan lisensi terpisah untuk setiap tipe file?**  
A: Tidak. Satu lisensi GroupDocs.Merger mencakup semua format yang didukung.

**Terakhir Diperbarui:** 2026-05-22  
**Diuji Dengan:** GroupDocs.Merger 23.11 untuk Java  
**Penulis:** GroupDocs

## Tutorial Terkait

- [split pdf java: Pemisahan Dokumen dengan GroupDocs.Merger](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [Menguasai Pemisahan Dokumen berdasarkan Rentang Halaman dengan GroupDocs.Merger untuk Java](/merger/java/document-splitting/split-documents-page-range-groupdocs-merger-java/)
- [Menggabungkan PDF Secara Efisien Menggunakan GroupDocs.Merger untuk Java: Panduan Langkah‑per‑Langkah](/merger/java/format-specific-merging/merge-pdfs-groupdocs-merger-java-tutorial/)