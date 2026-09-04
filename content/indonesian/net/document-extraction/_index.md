---
date: 2026-08-31
description: Pelajari cara mengekstrak halaman PDF tertentu menggunakan GroupDocs.Merger
  untuk .NET. Panduan langkah demi langkah mencakup skenario ekstraksi Word, PDF,
  dan DOCX.
keywords:
- extract specific pages pdf
- how to extract pages
- extract pages from word
- extract pages from docx
- extract pages from pdf
lastmod: 2026-08-31
og_description: Pelajari cara mengekstrak halaman PDF tertentu menggunakan GroupDocs.Merger
  untuk .NET. Panduan terperinci membantu Anda mengambil halaman dari file PDF, Word,
  dan DOCX secara efisien.
og_image_alt: Guide showing how to extract specific pages from PDF documents using
  GroupDocs.Merger for .NET
og_title: Cara mengekstrak halaman PDF tertentu dengan GroupDocs.Merger
schemas:
- author: GroupDocs
  dateModified: '2026-08-31'
  description: Learn how to extract specific pages pdf using GroupDocs.Merger for
    .NET. Step-by-step guides cover Word, PDF, and DOCX extraction scenarios.
  headline: How to extract specific pages pdf with GroupDocs.Merger
  type: TechArticle
- description: Learn how to extract specific pages pdf using GroupDocs.Merger for
    .NET. Step-by-step guides cover Word, PDF, and DOCX extraction scenarios.
  name: How to extract specific pages pdf with GroupDocs.Merger
  steps:
  - name: create a merger instance
    text: The `Merger` class is the entry point for loading and manipulating documents.
      Instantiate the `Merger` class by passing the path of the source file. This
      object represents the document you will work with.
  - name: specify pages to extract
    text: Provide a list of page indexes (1‑based) or a range string such as `"1-3,5"`
      to tell the library which pages to keep.
  - name: save the extracted document
    text: Call `Save` on the `Document` object, supplying the output path and desired
      format (e.g., `SaveFormat.Pdf`). `SaveFormat` is an enumeration that specifies
      the output file type, such as PDF. The operation writes a new file containing
      only the selected pages.
  type: HowTo
- questions:
  - answer: Yes – the same `Extract` call works for DOCX, and you can save the result
      directly as PDF using `SaveFormat.Pdf`.
    question: Can I extract pages from a Word document as PDF?
  - answer: Absolutely. Provide a comma‑separated list like `"2,4,7"` or a mixed range
      `"1-2,5,8-10"`.
    question: Is it possible to extract non‑consecutive pages?
  - answer: Yes. Supply the password when opening the document; the API will decrypt
      it automatically.
    question: Does the library support encrypted PDFs?
  - answer: Images are preserved exactly as they appear on the selected pages; no
      extra conversion steps are needed.
    question: How does GroupDocs.Merger handle images inside PDFs?
  - answer: .NET Framework 4.6+, .NET Core 3.1+, and .NET 5/6/7 are fully supported.
    question: What .NET versions are officially supported?
  type: FAQPage
tags:
- document extraction
- GroupDocs.Merger
- .NET
- PDF processing
title: Cara mengekstrak halaman PDF tertentu dengan GroupDocs.Merger
type: docs
url: /id/net/document-extraction/
weight: 9
---

# Cara mengekstrak halaman spesifik pdf dengan GroupDocs.Merger

Mengekstrak halaman spesifik pdf adalah kebutuhan umum ketika Anda perlu menggunakan kembali, berbagi, atau mengarsipkan hanya sebagian dari dokumen yang lebih besar. Dengan GroupDocs.Merger untuk .NET Anda dapat secara programatis menarik halaman tunggal, rentang halaman, atau pilihan khusus dari file PDF, Word, dan DOCX tanpa penyuntingan manual. Tutorial ini memandu Anda melalui konsep, prasyarat, dan alur kerja langkah demi langkah sehingga Anda dapat mengintegrasikan ekstraksi halaman ke dalam aplikasi .NET apa pun.

## Jawaban Cepat
- **Apa arti “extract specific pages pdf”?** Artinya memilih halaman individu atau rentang dari PDF (atau format lain yang didukung) dan menyimpannya sebagai dokumen baru yang lebih kecil.  
- **Format apa yang didukung?** GroupDocs.Merger menangani lebih dari 50 format input dan output, termasuk PDF, DOCX, PPTX, dan gambar.  
- **Apakah saya memerlukan lisensi?** Lisensi sementara dapat digunakan untuk pengujian; lisensi penuh diperlukan untuk penggunaan produksi.  
- **Bisakah saya memproses file besar?** Ya – perpustakaan memproses file dengan ratusan halaman menggunakan streaming, menjaga penggunaan memori tetap rendah.  
- **Apakah .NET Core didukung?** Tentu – API berfungsi dengan .NET Framework 4.6+, .NET Core 3.1+, dan .NET 6/7.

## Apa itu extract specific pages pdf?
`extract specific pages pdf` mengacu pada operasi mengambil satu atau lebih halaman dari PDF yang ada (atau dokumen yang didukung) dan membuat PDF baru yang hanya berisi halaman‑halaman tersebut. Ini memungkinkan Anda berbagi hanya bagian yang relevan sambil menjaga file asli tetap utuh.

## Mengapa mengekstrak halaman spesifik pdf dengan GroupDocs.Merger?
GroupDocs.Merger memproses hingga **50+ format file** dan dapat mengekstrak halaman dari dokumen yang berisi **500+ halaman** dalam waktu kurang dari **2 detik** pada CPU server‑grade tipikal. API berfungsi tanpa memerlukan Microsoft Office atau Adobe Acrobat terpasang, yang mengurangi kompleksitas penyebaran dan biaya lisensi.

## Prasyarat
- .NET 6 SDK (atau .NET Core 3.1 / .NET Framework 4.6+) terpasang pada mesin pengembangan Anda.  
- Paket NuGet GroupDocs.Merger for .NET yang valid (`GroupDocs.Merger`) ditambahkan ke proyek Anda.  
- (Opsional) File lisensi sementara atau penuh jika Anda berencana menjalankan kode di luar periode evaluasi.

## Cara mengekstrak halaman spesifik pdf dalam C# dengan GroupDocs.Merger

Muat dokumen sumber, tentukan halaman yang Anda butuhkan, dan simpan hasilnya. Perpustakaan mengabstraksi semua detail spesifik format, sehingga kode yang sama berfungsi untuk PDF, DOCX, PPTX, dan lainnya.

Muat file sumber Anda dan panggil metode `Extract` dengan nomor halaman yang diinginkan. Metode `Extract` membuat dokumen baru yang hanya berisi halaman‑halaman yang ditentukan. Metode ini mengembalikan objek `Document` baru yang dapat Anda simpan segera. Objek `Document` mewakili representasi dalam memori dari file hasil.

### Langkah 1: buat instance merger
Kelas `Merger` adalah titik masuk untuk memuat dan memanipulasi dokumen. Buat instance kelas `Merger` dengan memberikan path file sumber. Objek ini mewakili dokumen yang akan Anda kerjakan.

### Langkah 2: tentukan halaman yang akan diekstrak
Berikan daftar indeks halaman (berbasis 1) atau string rentang seperti "1-3,5" untuk memberi tahu perpustakaan halaman mana yang akan dipertahankan.

### Langkah 3: simpan dokumen yang diekstrak
Panggil `Save` pada objek `Document`, menyediakan path output dan format yang diinginkan (mis., `SaveFormat.Pdf`). `SaveFormat` adalah enumerasi yang menentukan tipe file output, seperti PDF. Operasi ini menulis file baru yang hanya berisi halaman yang dipilih.

## Masalah umum dan solusi
- **Halaman off‑by‑one:** GroupDocs.Merger menggunakan penomoran halaman berbasis 1. Pastikan daftar Anda dimulai dari 1, bukan 0.  
- **File terlindungi kata sandi:** Berikan kata sandi ke konstruktor `Merger` atau gunakan objek `LoadOptions`. `LoadOptions` menyediakan pengaturan yang mengontrol cara dokumen dimuat, mis., mengaktifkan caching memori.  
- **File besar menyebabkan timeout:** Aktifkan streaming dengan mengatur `LoadOptions.UseMemoryCache = true` untuk menjaga penggunaan memori tetap rendah.

## Pertanyaan yang sering diajukan

**T: Bisakah saya mengekstrak halaman dari dokumen Word sebagai PDF?**  
J: Ya – pemanggilan `Extract` yang sama berfungsi untuk DOCX, dan Anda dapat menyimpan hasilnya langsung sebagai PDF menggunakan `SaveFormat.Pdf`.

**T: Apakah memungkinkan mengekstrak halaman yang tidak berurutan?**  
J: Tentu. Berikan daftar dipisahkan koma seperti "2,4,7" atau rentang campuran "1-2,5,8-10".

**T: Apakah perpustakaan mendukung PDF terenkripsi?**  
J: Ya. Berikan kata sandi saat membuka dokumen; API akan mendekripsinya secara otomatis.

**T: Bagaimana GroupDocs.Merger menangani gambar di dalam PDF?**  
J: Gambar dipertahankan persis seperti yang muncul pada halaman yang dipilih; tidak diperlukan langkah konversi tambahan.

**T: Versi .NET apa yang secara resmi didukung?**  
J: .NET Framework 4.6+, .NET Core 3.1+, dan .NET 5/6/7 didukung sepenuhnya.

## Tutorial yang tersedia

### [Ekstrak halaman spesifik dari dokumen dengan GroupDocs.Merger untuk .NET](./extract-pages-groupdocs-merger-net/)
Pelajari cara mengekstrak halaman spesifik secara efisien menggunakan GroupDocs.Merger untuk .NET. Ideal untuk mengelola Word, PDF, dan lainnya dalam lingkungan profesional.

### [Cara mengekstrak halaman spesifik dari dokumen menggunakan GroupDocs.Merger untuk .NET dalam C#](./extract-pages-groupdocs-merger-dotnet-csharp/)
Pelajari cara mengekstrak halaman spesifik dari dokumen menggunakan GroupDocs.Merger untuk .NET dengan panduan komprehensif ini. Permudah tugas manajemen dokumen Anda dengan mudah.

## Sumber daya tambahan

- [Dokumentasi GroupDocs.Merger untuk .net](https://docs.groupdocs.com/merger/net/)
- [Referensi API GroupDocs.Merger untuk .net](https://reference.groupdocs.com/merger/net/)
- [Unduh GroupDocs.Merger untuk .net](https://releases.groupdocs.com/merger/net/)
- [Forum GroupDocs.Merger](https://forum.groupdocs.com/c/merger)
- [Dukungan Gratis](https://forum.groupdocs.com/)
- [Lisensi Sementara](https://purchase.groupdocs.com/temporary-license/)

---

**Terakhir Diperbarui:** 2026-08-31  
**Diuji dengan:** GroupDocs.Merger 23.9 for .NET  
**Penulis:** GroupDocs

## Tutorial Terkait

- [Cara Menggabungkan Halaman PDF Spesifik dengan GroupDocs.Merger untuk .NET: Panduan Komprehensif](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [Cara Menggabungkan Halaman Spesifik dari Beberapa Dokumen Menggunakan GroupDocs.Merger untuk .NET](/merger/net/page-operations/groupdocs-merger-dotnet-specific-pages-merge/)
- [Putar Halaman PDF di .NET Menggunakan GroupDocs.Merger: Panduan Langkah demi Langkah](/merger/net/page-operations/rotate-pdf-pages-groupdocs-merger-dotnet/)