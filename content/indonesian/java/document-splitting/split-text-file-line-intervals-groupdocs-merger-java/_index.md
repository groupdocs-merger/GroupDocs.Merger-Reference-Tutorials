---
date: '2026-02-06'
description: Pelajari cara memisahkan file teks per baris menggunakan GroupDocs.Merger
  untuk Java. Panduan langkah demi langkah untuk pemisahan dokumen yang efisien dalam
  proyek Java.
keywords:
- split text file line intervals Java
- document splitting GroupDocs.Merger
- Java document manipulation
title: Cara Membagi File Berdasarkan Baris dengan GroupDocs.Merger untuk Java
type: docs
url: /id/java/document-splitting/split-text-file-line-intervals-groupdocs-merger-java/
weight: 1
---

# Cara Membagi File per Baris Menggunakan GroupDocs.Merger untuk Java

Membagi file teks besar menjadi potongan‑potongan yang lebih kecil dan lebih mudah dikelola **per baris** adalah kebutuhan umum ketika Anda ‑ misalnya ‑ memproses log, mengimpor data secara batch, atau menyusun ulang laporan yang panjang. Pada tutorial ini Anda akan belajar cara **membagi file per baris** dengan GroupDocs.Merger untuk Java, melihat mengapa pendekatan ini menghemat waktu, dan mendapatkan contoh kode yang siap dijalankan.

## Jawaban Cepat
- **Apa arti “membagi file per baris”?** Ini membuat file teks terpisah yang masing‑masing berisi rentang nomor baris tertentu dari dokumen asli.  
- **Perpustakaan mana yang menangani pembagian?** GroupDocs.Merger untuk Java menyediakan API sederhana untuk pembagian interval baris.  
- **Apakah saya memerlukan lisensi?** Versi percobaan gratis cukup untuk pengujian; lisensi permanen diperlukan untuk penggunaan produksi.  
- **Bisakah saya membagi berdasarkan jumlah karakter?** Tidak secara langsung—gunakan langkah pra‑pemrosesan untuk mengubah file sebelum dibagi.  
- **Versi Java apa yang didukung?** Semua runtime Java 8+ kompatibel.

## Apa itu “membagi file per baris”?
Membagi file per baris berarti mengambil satu dokumen teks dan memecahnya menjadi beberapa file, masing‑masing berisi rentang baris berurutan tertentu (misalnya, baris 1‑3, 4‑6, dst.). Teknik ini ideal untuk pemrosesan batch, analisis paralel, atau sekadar meningkatkan keterbacaan.

## Mengapa Menggunakan GroupDocs.Merger untuk Java?
GroupDocs.Merger mengabstraksi pekerjaan I/O file tingkat rendah, memungkinkan Anda fokus pada logika bisnis. Ia menangani file besar secara efisien, mendukung banyak format dokumen, dan menawarkan API yang bersih serta fluida yang terintegrasi dengan baik pada build Maven atau Gradle.

## Prasyarat
- **Java Development Kit (JDK) 8 atau lebih tinggi** – pastikan `java` dan `javac` ada di PATH Anda.  
- **GroupDocs.Merger untuk Java** – tambahkan pustaka melalui Maven, Gradle, atau unduhan langsung.  
- **Pengetahuan dasar Java** – Anda seharusnya nyaman dengan kelas, metode, dan penanganan pengecualian.

## Menyiapkan GroupDocs.Merger untuk Java
Tambahkan pustaka ke proyek Anda menggunakan salah satu metode di bawah ini.

**Maven** – tempelkan dependensi ini ke dalam `pom.xml` Anda:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle** – sertakan baris berikut di `build.gradle`:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Unduhan Langsung** – Anda juga dapat mengambil JAR dari halaman rilis resmi: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Akuisisi Lisensi
Mulailah dengan percobaan gratis untuk menjelajahi API. Untuk beban kerja produksi, dapatkan lisensi sementara atau penuh dari portal GroupDocs.

## Cara Membagi File Teks per Baris (Implementasi Java)

Berikut adalah panduan singkat langkah‑demi‑langkah. Setiap langkah dijelaskan dengan bahasa sederhana sebelum blok kode, sehingga Anda tahu persis apa yang terjadi.

### Langkah 1: Tentukan Jalur Sumber dan Output
Pertama, beri tahu pustaka di mana file asli Anda berada dan ke mana fragmen yang dibagi harus ditulis.
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.txt";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToLineRanges-" + Paths.get(filePath).getFileName().toString();
```

### Langkah 2: Konfigurasikan Opsi Pembagian
Buat instance `TextSplitOptions` yang mendeskripsikan interval baris yang Anda inginkan. Array `new int[] { 3, 6 }` memberi tahu API untuk memotong setelah baris 3 dan baris 6, menghasilkan dua bagian: baris 1‑3 dan baris 4‑6.
```java
TextSplitOptions splitOptions = new TextSplitOptions(filePathOut, TextSplitMode.Interval, new int[] { 3, 6 });
```

### Langkah 3: Inisialisasi Merger dan Jalankan Pembagian
Akhirnya, buat objek `Merger` dengan file sumber dan panggil `split()` dengan opsi yang baru saja Anda buat.
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

Itu saja! Setelah pemanggilan selesai, Anda akan menemukan dua file baru di `YOUR_OUTPUT_DIRECTORY`, masing‑masing berisi rentang baris yang ditentukan.

## Aplikasi Praktis (Mengapa Ini Penting)
1. **Pipeline Pemrosesan Data** – Memecah file log raksasa menjadi potongan lebih kecil untuk parsing paralel.  
2. **Manajemen Dokumen** – Mengubah satu laporan menjadi file per bab untuk distribusi yang lebih mudah.  
3. **Segmentasi Konten** – Menyiapkan bagian‑bagian artikel besar untuk platform publikasi yang ditargetkan.

## Tips Kinerja
- **Stream‑line I/O** – Pilih `Files.newBufferedReader` saat menangani file sangat besar untuk menjaga penggunaan memori tetap rendah.  
- **Tutup Sumber Daya** – Meskipun GroupDocs.Merger menangani sebagian besar pembersihan, menutup stream kustom secara eksplisit dapat mencegah kebocoran.  
- **Pantau Memori** – Membagi file berukuran gigabyte dapat mengonsumsi banyak memori; alokasikan heap yang cukup (`-Xmx2g` atau lebih) bila diperlukan.

## Masalah Umum dan Solusinya
| Masalah | Mengapa Terjadi | Solusi |
|-------|----------------|-----|
| `OutOfMemoryError` | File sumber besar melebihi heap. | Tingkatkan heap JVM atau bagi dengan interval yang lebih kecil. |
| `FileNotFoundException` | Jalur tidak tepat atau izin kurang. | Pastikan `filePath` dan `filePathOut` bersifat absolut dan dapat ditulisi. |
| File output kosong | Array interval tidak mencakup seluruh dokumen. | Pastikan interval terakhir berakhir pada atau melewati total jumlah baris. |

## Bagian FAQ

**T: Bisakah saya membagi file berdasarkan jumlah karakter alih‑alih nomor baris?**  
J: Saat ini, GroupDocs.Merger untuk Java berfokus pada interval baris. Namun, Anda dapat memproses teks terlebih dahulu agar setiap baris memiliki jumlah karakter yang diinginkan sebelum menggunakan fitur ini.

**T: Apakah ada batas berapa banyak interval yang dapat saya tentukan untuk pembagian?**  
J: Tidak ada batas khusus dalam pustaka; namun, kinerja dapat menurun jika jumlah split terlalu banyak karena peningkatan beban proses.

**T: Bagaimana cara menangani error selama pembagian file?**  
J: Bungkus kode Anda dengan blok try‑catch untuk menangkap dan mengelola pengecualian secara efektif. GroupDocs.Merger menyediakan pesan error yang detail untuk membantu pemecahan masalah.

**T: Apakah pustaka ini mendukung format berbasis teks lain seperti CSV atau TSV?**  
J: Ya, karena CSV dan TSV adalah file teks biasa, logika interval baris yang sama dapat diterapkan. Perlakukan mereka sebagai file `.txt` dalam API.

**T: Bisakah saya mengotomatisasi pembagian untuk banyak file dalam satu folder?**  
J: Tentu. Bungkus logika di atas dalam loop yang mengiterasi `Files.list(Paths.get("folder"))` dan terapkan `TextSplitOptions` yang sama pada setiap file.

## Sumber Daya
- **Dokumentasi:** [GroupDocs.Merger for Java Documentation](https://docs.groupdocs.com/merger/java/)  
- **Referensi API:** [GroupDocs API Reference](https://reference.groupdocs.com/merger/java/)  
- **Unduhan:** [Latest Releases](https://releases.groupdocs.com/merger/java/)  
- **Pembelian dan Lisensi:** [Buy GroupDocs](https://purchase.groupdocs.com/buy)  
- **Percobaan Gratis:** [GroupDocs Free Trial](https://releases.groupdocs.com/merger/java/)  
- **Lisensi Sementara:** [Obtain Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Forum Dukungan:** [GroupDocs Support](https://forum.groupdocs.com/c/merger)

---

**Terakhir Diperbarui:** 2026-02-06  
**Diuji Dengan:** GroupDocs.Merger 23.12 untuk Java  
**Penulis:** GroupDocs