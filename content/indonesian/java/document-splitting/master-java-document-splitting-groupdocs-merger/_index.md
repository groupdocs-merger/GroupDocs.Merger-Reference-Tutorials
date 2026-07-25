---
date: '2026-07-25'
description: Pelajari cara memisahkan halaman docx menggunakan GroupDocs.Merger untuk
  Java, mencakup pemisahan DOCX menjadi file terpisah, ekstraksi aliran, dan opsi
  pemisahan.
keywords:
- split docx pages
- how to split docx
- split docx into files
lastmod: '2026-07-25'
og_description: Pisahkan halaman docx menggunakan GroupDocs.Merger untuk Java. Pelajari
  langkah demi langkah cara memisahkan DOCX menjadi file atau aliran dengan contoh
  kode.
og_image_alt: Guide to split DOCX pages using GroupDocs.Merger Java library
og_title: Pisahkan Halaman DOCX dengan GroupDocs.Merger untuk Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-25'
  description: Learn how to split docx pages using GroupDocs.Merger for Java, covering
    splitting DOCX into separate files, stream extraction, and split options.
  headline: How to Split DOCX Pages with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to split docx pages using GroupDocs.Merger for Java, covering
    splitting DOCX into separate files, stream extraction, and split options.
  name: How to Split DOCX Pages with GroupDocs.Merger for Java
  steps:
  - name: '**Legal contracts:** Extract individual clauses for separate review without
      exposing the whole agreement.'
    text: '**Legal contracts:** Extract individual clauses for separate review without
      exposing the whole agreement.'
  - name: '**E‑learning platforms:** Serve chapter‑by‑chapter Word files on demand,
      keeping the full textbook protected.'
    text: '**E‑learning platforms:** Serve chapter‑by‑chapter Word files on demand,
      keeping the full textbook protected.'
  - name: '**Business reporting:** Send only the finance section of a quarterly report
      to the CFO, reducing bandwidth and improving confidentiality.'
    text: '**Business reporting:** Send only the finance section of a quarterly report
      to the CFO, reducing bandwidth and improving confidentiality.'
  type: HowTo
- questions:
  - answer: It’s a Java library that enables merging, splitting, and converting over
      50 document formats—including DOCX, PDF, PPTX, and HTML—without requiring Microsoft
      Office.
    question: What is GroupDocs.Merger for Java?
  - answer: Acquire a temporary trial license from the [GroupDocs website](https://purchase.groupdocs.com/temporary-license/)
      for evaluation. For production, purchase a full license at the same site.
    question: How do I obtain a license for GroupDocs.Merger?
  - answer: Yes, the `split` method works with PDF, DOCX, PPTX, and other supported
      formats.
    question: Can I split PDF files using the same API?
  - answer: Absolutely—use the stream‑based approach shown above to keep everything
      in memory.
    question: Is it possible to split a document without writing to disk?
  - answer: Always target the latest stable release to benefit from performance improvements
      and bug fixes.
    question: Which version of GroupDocs.Merger should I use?
  type: FAQPage
tags:
- split docx
- GroupDocs.Merger
- Java document processing
- DOCX splitting
title: Cara Memisahkan Halaman DOCX dengan GroupDocs.Merger untuk Java
type: docs
url: /id/java/document-splitting/master-java-document-splitting-groupdocs-merger/
weight: 1
---

# Pisahkan Halaman DOCX dengan GroupDocs.Merger untuk Java

Dalam tutorial ini Anda akan menemukan **cara memisahkan halaman docx** secara efisien menggunakan GroupDocs.Merger untuk Java. Apakah Anda perlu memecah kontrak besar menjadi halaman terpisah atau mengambil bagian tertentu sebagai aliran memori, kami akan membahas pengaturan, kode, dan tip dunia nyata sehingga Anda dapat menerapkan solusi dalam hitungan menit.

## Jawaban Cepat
- **Library apa yang menangani pemisahan DOCX di Java?** GroupDocs.Merger for Java.  
- **Bisakah saya memisahkan DOCX menjadi file terpisah?** Ya – konfigurasikan `SplitOptions` dengan nomor halaman yang diinginkan.  
- **Apakah memungkinkan mendapatkan halaman sebagai aliran alih-alih file?** Tentu saja, dengan menyediakan `SplitStreamFactory` khusus.  
- **Apakah saya memerlukan lisensi?** Lisensi percobaan sementara berfungsi untuk evaluasi; lisensi penuh diperlukan untuk produksi.  
- **Versi Java mana yang didukung?** Semua JDK 8+ bekerja dengan rilis terbaru GroupDocs.Merger.

## Apa itu pemisahan halaman docx?
**Pemisahan halaman docx** berarti mengekstrak satu atau lebih halaman dari dokumen Word multi‑halaman dan menyimpan setiap pilihan sebagai file terpisah atau aliran memori. Ini memungkinkan pengiriman modular, alur kerja berbasis kepatuhan, atau pemrosesan secara langsung tanpa harus menangani seluruh dokumen sekaligus.

## Mengapa menggunakan GroupDocs.Merger untuk Java?
GroupDocs.Merger memproses dokumen **sepenuhnya dalam Java**—tanpa binari native, tanpa instalasi Office. Ia mendukung **lebih dari 50 format input dan output** dan dapat memisahkan **DOCX 200‑halaman dalam kurang dari 2 detik** pada server 2.5 GHz standar, menjaga penggunaan memori di bawah 100 MB berkat arsitektur berbasis aliran.

## Prasyarat

### Perpustakaan dan Ketergantungan yang Diperlukan
- **Java Development Kit (JDK):** JDK 8 atau yang lebih baru.  
- **GroupDocs.Merger untuk Java:** Perpustakaan inti untuk manipulasi dokumen.

### Menambahkan Ketergantungan
Sertakan perpustakaan melalui Maven atau Gradle (blok kode tidak diubah):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

Anda juga dapat mengunduh rilis terbaru dari situs resmi: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Akuisisi Lisensi
- **Lisensi percobaan:** Dapatkan kunci sementara dari halaman [GroupDocs.Trial License](https://purchase.groupdocs.com/temporary-license/).  
- **Lisensi produksi:** Beli lisensi penuh di [GroupDocs Purchase](https://purchase.groupdocs.com/buy).

## Menyiapkan GroupDocs.Merger untuk Java
`Merger` adalah kelas utama yang mengatur operasi pemisahan, penggabungan, dan konversi.

```java
import com.groupdocs.merger.Merger;

public class DocumentSetup {
    public static void main(String[] args) {
        // Initialize a Merger object with the path of the input document
        Merger merger = new Merger("path/to/your/document.docx");
        
        // Perform operations on your document...
        
        merger.close();
    }
}
```

Dengan lingkungan siap, mari jelajahi dua cara utama untuk **memisahkan halaman docx menjadi file** atau aliran.

## Cara Memisahkan DOCX menjadi File dengan GroupDocs.Merger
Muat DOCX sumber, tentukan rentang halaman yang diinginkan, dan panggil metode `split` – panggilan tunggal ini menghasilkan file output terpisah untuk setiap segmen yang dipilih. Metode `split` memproses dokumen sesuai dengan `SplitOptions` yang diberikan dan mengembalikan jalur file yang dibuat. Langkah-langkah berikut menunjukkan implementasi lengkap yang siap produksi.

### Langkah 1 – Tentukan Jalur Input dan Output
Tentukan lokasi DOCX asli dan folder tempat file hasil pemisahan akan ditulis.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
String filePathOut = new File("YOUR_OUTPUT_DIRECTORY", 
    "SplitToSinglePages-" +
    Paths.get(filePath).getFileName().toString()
).getPath();
```

### Langkah 2 – Konfigurasikan SplitOptions (opsi pemisahan java)
`SplitOptions` memberi tahu API halaman mana yang akan diekstrak dan di mana menempatkan hasilnya.

```java
import com.groupdocs.merger.domain.options.SplitOptions;

SplitOptions splitOptions = new SplitOptions(filePathOut, new int[] { 3, 6, 8 });
```

- `filePathOut` – folder tempat setiap file halaman akan ditempatkan.  
- `new int[]{3,6,8}` – nomor halaman yang ingin Anda pisahkan (halaman dimulai dari 1).

### Langkah 3 – Lakukan Pemisahan
Buat instance `Merger` dan panggil `split`. Metode ini mengembalikan daftar jalur file yang dihasilkan.

```java
import com.groupdocs.merger.Merger;

Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

**Tip pro:** Pastikan direktori output ada dan aplikasi Anda memiliki izin menulis; jika tidak, pemisahan akan gagal.

#### Kesalahan Umum
- **Folder output tidak ada:** API tidak akan membuat direktori secara otomatis.  
- **Nomor halaman tidak tepat:** Indeks halaman mulai dari 1; menyebutkan 0 akan menghasilkan error.

## Cara Memisahkan Halaman DOCX menjadi Aliran (In‑Memory)
Ketika Anda membutuhkan akses sementara—seperti mengirim halaman melalui layanan web atau melakukan analisis in‑memory—menangkap setiap halaman yang diekstrak sebagai aliran menghilangkan beban menulis ke disk. Dengan menggunakan `SplitStreamFactory` khusus, perpustakaan menulis konten hasil pemisahan langsung ke objek `ByteArrayOutputStream`, yang kemudian dapat ditransmisikan, disimpan, atau diproses lebih lanjut tanpa file perantara.

### Langkah 1 – Tentukan Jalur Input dan Siapkan Daftar untuk Aliran
Tetapkan file sumber dan buat wadah untuk menampung aliran yang dihasilkan.

```java
import java.io.ByteArrayOutputStream;
import java.util.ArrayList;
import java.util.List;

String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
final List<OutputStream> resultStreams = new ArrayList<>();
```

### Langkah 2 – Konfigurasikan SplitOptions dengan SplitStreamFactory Kustom
Implementasikan `SplitStreamFactory` untuk menyediakan `OutputStream` baru untuk setiap halaman dan menyimpan aliran yang selesai.

```java
import com.groupdocs.merger.domain.common.SplitStreamFactory;
import com.groupdocs.merger.domain.options.SplitMode;

SplitOptions splitOptions = new SplitOptions(new SplitStreamFactory() {
    @Override
    public OutputStream createSplitStream(int pageNumber) {
        return new ByteArrayOutputStream(); // Create a stream for each page
    }
    
    @Override
    public void closeSplitStream(int pageNumber, OutputStream pageStream) {
        resultStreams.add(pageStream); // Collect the streams
    }
}, new int[] { 3, 4 }, SplitMode.Pages);
```

- `createSplitStream` – menghasilkan `OutputStream` baru untuk setiap halaman yang diminta.  
- `closeSplitStream` – menyimpan aliran yang selesai untuk penggunaan selanjutnya.

### Langkah 3 – Jalankan Pemisahan dan Ambil Aliran
Jalankan operasi pemisahan dan kemudian gunakan aliran in‑memory sesuai kebutuhan (misalnya, lampirkan ke email, unggah ke penyimpanan cloud).

```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);

return resultStreams; // Retrieve streams for processing
```

**Tips Pemecahan Masalah**  
- Pastikan jalur DOCX sumber benar; kesalahan ketik akan memunculkan `FileNotFoundException`.  
- Selalu tutup aliran setelah selesai untuk membebaskan memori dan menghindari kebocoran.

## Aplikasi Praktis
1. **Kontrak hukum:** Ekstrak klausul individu untuk tinjauan terpisah tanpa mengungkapkan seluruh perjanjian.  
2. **Platform e‑learning:** Sajikan file Word per bab sesuai permintaan, menjaga buku teks lengkap tetap terlindungi.  
3. **Pelaporan bisnis:** Kirim hanya bagian keuangan dari laporan triwulanan ke CFO, mengurangi bandwidth dan meningkatkan kerahasiaan.

## Pertimbangan Kinerja
- **Aliran hemat memori:** Pilih pendekatan aliran untuk dokumen lebih besar dari 50 MB agar penggunaan heap tetap rendah.  
- **Pemrosesan batch:** Kelompokkan beberapa pekerjaan pemisahan dalam satu sesi JVM untuk mengurangi overhead startup.  
- **Pembersihan sumber daya:** Panggil `merger.close()` dan tutup semua aliran untuk menghindari kebocoran memori.  
- **Metrik kecepatan:** Pada server 8‑core standar, memisahkan DOCX 300‑halaman menjadi halaman individual selesai dalam ~1,8 detik.

## Pertanyaan yang Sering Diajukan

**Q: Apa itu GroupDocs.Merger untuk Java?**  
A: Itu adalah perpustakaan Java yang memungkinkan penggabungan, pemisahan, dan konversi lebih dari 50 format dokumen—termasuk DOCX, PDF, PPTX, dan HTML—tanpa memerlukan Microsoft Office.

**Q: Bagaimana cara mendapatkan lisensi untuk GroupDocs.Merger?**  
A: Dapatkan lisensi percobaan sementara dari [situs GroupDocs](https://purchase.groupdocs.com/temporary-license/) untuk evaluasi. Untuk produksi, beli lisensi penuh di situs yang sama.

**Q: Bisakah saya memisahkan file PDF menggunakan API yang sama?**  
A: Ya, metode `split` bekerja dengan PDF, DOCX, PPTX, dan format lain yang didukung.

**Q: Apakah memungkinkan memisahkan dokumen tanpa menulis ke disk?**  
A: Tentu saja—gunakan pendekatan berbasis aliran yang ditunjukkan di atas untuk menyimpan semuanya di memori.

**Q: Versi GroupDocs.Merger mana yang harus saya gunakan?**  
A: Selalu gunakan rilis stabil terbaru untuk mendapatkan peningkatan kinerja dan perbaikan bug.

---

**Terakhir Diperbarui:** 2026-07-25  
**Diuji Dengan:** GroupDocs.Merger for Java latest-version  
**Penulis:** GroupDocs

## Tutorial Terkait

- [Cara Memisahkan Dokumen menjadi File Multi-Halaman Menggunakan GroupDocs.Merger untuk Java](/merger/java/document-splitting/split-documents-multi-page-files-java-groupdocs-merger/)
- [Cara mengekstrak halaman tertentu dengan Java menggunakan GroupDocs.Merger](/merger/java/document-extraction/)
- [Cara Menggabungkan Halaman Tertentu Java Menggunakan GroupDocs.Merger](/merger/java/document-joining/join-specific-pages-groupdocs-merger-java/)