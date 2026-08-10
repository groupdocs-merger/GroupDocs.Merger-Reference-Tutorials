---
date: '2026-07-15'
description: Pelajari cara mengubah orientasi halaman dengan GroupDocs Merger untuk
  Java. Ikuti panduan langkah demi langkah ini untuk memodifikasi bagian tertentu
  dari dokumen Anda.
keywords:
- change page orientation java
- change orientation specific pages
- groupdocs merger java
- document layout modification
lastmod: '2026-07-15'
og_description: Pelajari cara mengubah orientasi halaman di Java dengan GroupDocs.Merger.
  Panduan ini menampilkan kode langkah demi langkah, tips kinerja, dan contoh penggunaan
  dunia nyata.
og_image_alt: 'Guide: Change page orientation in Java using GroupDocs.Merger'
og_title: Ubah Orientasi Halaman di Java Menggunakan GroupDocs.Merger
schemas:
- author: GroupDocs
  dateModified: '2026-07-15'
  description: Learn how to change page orientation with GroupDocs Merger for Java.
    Follow this step-by-step guide to modify specific sections of your documents.
  headline: Change Page Orientation in Java Using GroupDocs.Merger
  type: TechArticle
- description: Learn how to change page orientation with GroupDocs Merger for Java.
    Follow this step-by-step guide to modify specific sections of your documents.
  name: Change Page Orientation in Java Using GroupDocs.Merger
  steps:
  - name: Set Paths for Your Document
    text: Define absolute or relative paths for the source and destination files.
      Adjust these values to match your project’s folder layout.
  - name: Create OrientationOptions
    text: '`OrientationOptions` specifies which pages to rotate and the target orientation
      mode.'
  - name: Initialize Merger
    text: '`Merger` manages file I/O and ensures resources are released correctly.'
  - name: Apply Changes and Save
    text: '`changeOrientation` applies the orientation settings to the selected pages
      and updates the document.'
  type: HowTo
- questions:
  - answer: GroupDocs Merger for Java provides the `changeOrientation` API.
    question: What library handles page orientation?
  - answer: Yes – pass an array of page numbers to `OrientationOptions`.
    question: Can I target only a few pages?
  - answer: A valid GroupDocs Merger license is needed for unlimited use.
    question: Is a license required for production?
  - answer: JDK 8 or higher (up to JDK 21).
    question: What Java version is supported?
  - answer: The library processes pages stream‑wise, so even 500‑page PDFs use less
      than 200 MB RAM.
    question: Will memory usage stay low?
  type: FAQPage
tags:
- change page orientation
- GroupDocs.Merger
- Java document processing
title: Ubah Orientasi Halaman di Java Menggunakan GroupDocs.Merger
type: docs
url: /id/java/page-operations/change-page-orientation-groupdocs-java/
weight: 1
---

# Ubah Orientasi Halaman di Java Menggunakan GroupDocs.Merger

Mengubah orientasi halaman dalam file PDF atau DOCX adalah kebutuhan yang sering muncul ketika satu halaman berisi diagram lebar, tabel besar, atau gambar full‑bleed. Dalam tutorial ini Anda akan mempelajari **how to change page orientation java** untuk halaman yang dipilih menggunakan GroupDocs Merger untuk Java, tanpa harus membuat ulang seluruh dokumen.

## Jawaban Cepat
- **Library apa yang menangani orientasi halaman?** GroupDocs Merger untuk Java menyediakan API `changeOrientation`.  
- **Apakah saya dapat menargetkan hanya beberapa halaman?** Ya – kirimkan array nomor halaman ke `OrientationOptions`.  
- **Apakah lisensi diperlukan untuk produksi?** Lisensi GroupDocs Merger yang valid diperlukan untuk penggunaan tak terbatas.  
- **Versi Java apa yang didukung?** JDK 8 atau lebih tinggi (hingga JDK 21).  
- **Apakah penggunaan memori tetap rendah?** Perpustakaan memproses halaman secara streaming, sehingga bahkan PDF 500‑halaman menggunakan kurang dari 200 MB RAM.

## Apa itu “change page orientation java”?
**“Change page orientation java”** mengacu pada penggantian orientasi halaman yang dipilih antara mode potret dan lanskap secara programatis menggunakan kode Java.  
Metode `changeOrientation` milik GroupDocs Merger melakukan ini dalam satu panggilan, mempertahankan semua konten lainnya.

## Mengapa Menggunakan GroupDocs Merger untuk Java?
GroupDocs Merger mendukung **lebih dari 30 format input dan output** (termasuk PDF, DOCX, PPTX, dan gambar) dan dapat memanipulasi dokumen **tanpa memuat seluruh file ke memori**. Benchmark menunjukkan perubahan orientasi pada PDF 300‑halaman selesai dalam kurang dari 3 detik pada VM standar dengan 8‑core.

## Prasyarat
- **Java Development Kit (JDK):** 8 atau lebih baru.  
- **IDE:** IntelliJ IDEA, Eclipse, atau editor kompatibel Java apa pun.  
- **GroupDocs.Merger untuk Java:** Tambahkan perpustakaan melalui Maven, Gradle, atau unduhan JAR langsung.  

### Menyiapkan GroupDocs.Merger untuk Java

#### Instalasi

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

**Unduh Langsung**  
Unduh versi terbaru dari [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

#### Akuisisi Lisensi
Mulailah dengan percobaan gratis atau dapatkan lisensi sementara untuk mengevaluasi GroupDocs Merger tanpa batasan. Untuk penggunaan jangka panjang, pertimbangkan membeli lisensi.

### Inisialisasi dan Pengaturan Dasar
Kelas `Merger` adalah titik masuk untuk semua operasi manipulasi dokumen. Setelah menambahkan dependensi, impor namespace yang diperlukan dan buat instance `Merger`.

```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OrientationMode;
import com.groupdocs.merger.domain.options.OrientationOptions;
```

## Cara Mengubah Orientasi Halaman di Java?
Untuk mengubah orientasi, muat dokumen sumber dengan `Merger`, buat objek `OrientationOptions` yang menentukan halaman target dan mode yang diinginkan (potret atau lanskap), panggil `changeOrientation(options)`, dan akhirnya simpan file yang telah dimodifikasi ke lokasi yang diinginkan. Urutan ini menangani PDF, DOCX, dan PPTX secara efisien tanpa harus membangun ulang seluruh dokumen.

### Langkah 1: Atur Jalur untuk Dokumen Anda
Tentukan jalur absolut atau relatif untuk file sumber dan tujuan. Sesuaikan nilai-nilai ini agar cocok dengan struktur folder proyek Anda.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/ChangePageOrientation-" + 
    Paths.get(filePath).getFileName().toString();
```

### Langkah 2: Buat OrientationOptions
`OrientationOptions` menentukan halaman mana yang akan diputar dan mode orientasi target.  

```java
// Change page orientation for pages 3 and 4 to Landscape.
OrientationOptions orientationOptions = new OrientationOptions(OrientationMode.Landscape, 
    new int[] { 3, 4 });
```

### Langkah 3: Inisialisasi Merger
`Merger` mengelola I/O file dan memastikan sumber daya dibebaskan dengan benar.  

```java
Merger merger = new Merger(filePath);
```

### Langkah 4: Terapkan Perubahan dan Simpan
`changeOrientation` menerapkan pengaturan orientasi ke halaman yang dipilih dan memperbarui dokumen.  

```java
// Apply orientation changes as per the specified options.
merger.changeOrientation(orientationOptions);

// Save the updated document.
merger.save(filePathOut);
```

## Masalah Umum dan Solusinya
- **File Tidak Ditemukan:** Verifikasi bahwa jalur file sudah benar dan aplikasi memiliki izin baca/tulis.  
- **Konflik Dependensi:** Pastikan tidak ada versi lama dari perpustakaan GroupDocs yang masih berada di classpath.  
- **Lonjakan Memori pada File Besar:** Proses dokumen dalam potongan atau tingkatkan heap JVM (`-Xmx2g`) jika Anda melebihi 200 MB.

## Aplikasi Praktis
1. **Materi Pendidikan:** Putar halaman dengan skematik teknik besar sambil mempertahankan bagian teks dalam mode potret.  
2. **Laporan Bisnis:** Tampilkan tabel keuangan lebar dalam mode lanskap tanpa mengonversi seluruh laporan.  
3. **Portofolio Fotografi:** Tampilkan gambar full‑bleed pada halaman lanskap tunggal dalam PDF multi‑halaman.

## Pertimbangan Kinerja
- **Penggunaan Sumber Daya:** GroupDocs Merger melakukan streaming halaman, sehingga memori tetap rendah bahkan untuk file 1.000‑halaman.  
- **Tips Optimasi:** Tutup instance `Merger` dengan cepat dan gunakan kembali satu instance saat memproses banyak dokumen dalam batch.  
- **Praktik Terbaik:** Tangkap `MergerException` untuk menangani input yang rusak secara elegan dan catat detail kesalahan untuk debugging.

## Kesimpulan
Anda kini memiliki metode lengkap yang siap produksi untuk **change page orientation java** menggunakan GroupDocs Merger. Bereksperimenlah dengan berbagai jenis dokumen, gabungkan perubahan orientasi dengan operasi merge/split lainnya, dan integrasikan logika ini ke dalam pipeline otomatisasi dokumen yang lebih besar.

## Pertanyaan yang Sering Diajukan

**Q:** Apakah saya dapat mengubah orientasi untuk semua halaman dalam dokumen dengan GroupDocs Merger?  
**A:** Ya – kirimkan rentang seperti `new int[]{1,2,3,…}` atau gunakan `OrientationOptions.setAllPages(true)` jika versi API mendukungnya.

**Q:** Apakah GroupDocs Merger kompatibel dengan semua format dokumen?  
**A:** Ia mendukung **lebih dari 30 format**, termasuk PDF, DOCX, PPTX, HTML, dan tipe gambar umum.

**Q:** Bagaimana cara menangani pengecualian saat menggunakan GroupDocs Merger?  
**A:** Bungkus panggilan dalam blok try‑catch untuk `MergerException`; catat pesan dan opsional mencoba kembali dengan strategi fallback.

**Q:** Apa implikasi memori untuk PDF besar?  
**A:** Perpustakaan melakukan streaming data, biasanya menggunakan kurang dari 200 MB untuk PDF 500‑halaman; pantau heap JVM dan tutup sumber daya dengan cepat.

**Q:** Di mana saya dapat menemukan fitur lanjutan untuk GroupDocs Merger untuk Java?  
**A:** Jelajahi [Referensi API](https://reference.groupdocs.com/merger/java/) dan dokumentasi untuk fitur seperti watermarking, enkripsi, dan pemisahan dokumen.

---

**Terakhir Diperbarui:** 2026-07-15  
**Diuji Dengan:** GroupDocs.Merger 23.10 untuk Java  
**Penulis:** GroupDocs  

## Sumber Daya
- **Dokumentasi:** [Dokumentasi GroupDocs.Merger](https://docs.groupdocs.com/merger/java/)  
- **Referensi API:** [Referensi API](https://reference.groupdocs.com/merger/java/)  
- **Unduh:** [Rilis Terbaru](https://releases.groupdocs.com/merger/java/)  
- **Beli:** [Beli GroupDocs.Merger](https://purchase.groupdocs.com/buy)  
- **Uji Coba Gratis:** [Dapatkan Uji Coba Gratis](https://releases.groupdocs.com/merger/java/)  
- **Lisensi Sementara:** [Dapatkan Lisensi Sementara](https://purchase.groupdocs.com/temporary-license/)  
- **Dukungan:** [Forum GroupDocs](https://forum.groupdocs.com/c/merger/)

## Tutorial Terkait

- [Tutorial Operasi Halaman Dokumen untuk GroupDocs.Merger Java](/merger/java/page-operations/)  
- [Putar Halaman PDF di Java Menggunakan GroupDocs.Merger: Panduan Langkah‑per‑Langkah](/merger/java/page-operations/rotate-pdf-pages-java-groupdocs-merger/)  
- [Muat Dokumen Lokal Java Menggunakan GroupDocs.Merger – Panduan](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)