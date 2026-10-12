---
additionalTitle: GroupDocs API References
date: 2026-10-11
description: สำรวจ GroupDocs.Merger document merging API สำหรับการ merging, splitting
  ที่รวดเร็ว, cross‑platform และการประมวลผล PDFs, Office files, images และอื่น ๆ
is_root: true
keywords:
- groupdocs.merger document merging api
- document merging and splitting
- cross-platform document processing
lastmod: 2026-10-11
linktitle: GroupDocs.Merger Tutorials
og_description: GroupDocs.Merger document merging API ช่วยให้คุณสามารถ merge, split,
  reorder, และ secure เอกสารได้กว่า 50+ รูปแบบ. เรียนรู้การ integration ที่รวดเร็ว,
  cross‑platform สำหรับ .NET และ Java.
og_image_alt: Guide to using GroupDocs.Merger for merging and splitting documents
og_title: GroupDocs.Merger document merging API – คู่มือฉบับสมบูรณ์
schemas:
- author: GroupDocs
  dateModified: '2026-10-11'
  description: Explore the GroupDocs.Merger document merging API for fast, cross‑platform
    document merging, splitting, and processing of PDFs, Office files, images and
    more.
  headline: GroupDocs.Merger document merging API – complete guide to merging & splitting
  type: TechArticle
- questions:
  - answer: Yes, with a valid GroupDocs license. A free trial is available for evaluation.
    question: Can I use the API in a commercial product?
  - answer: Absolutely. You can open, modify, and re‑secure encrypted PDFs using the
      same API calls.
    question: Does the API support password‑protected PDFs?
  - answer: .NET Standard 2.0, .NET Framework 2.0+, .NET Core 2.0+, Mono 1.2+; Java
      7, 8, and 10+ are fully supported.
    question: Which .NET and Java versions are compatible?
  - answer: It streams data and uses memory‑efficient algorithms, allowing you to
      process multi‑gigabyte documents without exhausting system resources.
    question: How does the API handle very large files?
  - answer: While the core merging API focuses on structural operations, you can combine
      it with GroupDocs.Parser for advanced text extraction and OCR needs.
    question: Is there built‑in support for OCR or text extraction?
  type: FAQPage
tags:
- document merging
- groupdocs.merger
- .net document processing
- java document processing
title: GroupDocs.Merger document merging API – คู่มือฉบับสมบูรณ์สำหรับการ merging
  & splitting
type: docs
url: /th/
weight: 11
---

# GroupDocs.Merger document merging API – คู่มือฉบับเต็มสำหรับการรวมและแยกไฟล์

The **GroupDocs.Merger document merging API** ให้วิธีที่เร็วและข้ามแพลตฟอร์มในการรวม, แยก, และจัดการกับประเภทเอกสารที่หลากหลายโดยตรงจากแอปพลิเคชัน .NET หรือ Java ของคุณ ไม่ว่าคุณจะต้องการรวม PDF หลายไฟล์เป็นรายงานเดียว, แยกสัญญาขนาดใหญ่เป็นหน้าแยก, หรือจัดลำดับสไลด์ในงานนำเสนอ, API นี้จัดการได้ด้วยเพียงไม่กี่บรรทัดของโค้ด.

## คำตอบด่วน
- **API ทำอะไร?** มันรวม, แยก, จัดลำดับใหม่, และปกป้องเอกสารในรูปแบบกว่า 50 แบบ.  
- **แพลตฟอร์มที่รองรับคืออะไร?** .NET (Standard, Framework, Core, Mono) และ Java (J2SE 7‑10).  
- **ต้องใช้ซอฟต์แวร์ภายนอกหรือไม่?** ไม่—ไม่มีการพึ่งพา Microsoft Office หรือ Adobe.  
- **ฉันสามารถปกป้องเอกสารได้หรือไม่?** ได้, คุณสามารถเพิ่ม, ลบ, หรืออัปเดตรหัสผ่านและสิทธิ์ได้.  
- **มีขีดจำกัดขนาดไฟล์หรือไม่?** API นี้ได้รับการปรับให้เหมาะกับไฟล์ขนาดใหญ่และการดำเนินการแบบแบตช์.  

## GroupDocs.Merger document merging API คืออะไร?
โหลดไฟล์ของคุณและเรียกใช้เมธอด merge หรือ split ที่เหมาะสม – นั่นคือกระบวนการทำงานหลักของ GroupDocs.Merger document merging API. มันให้อินเทอร์เฟซเดียวที่สอดคล้องสำหรับการจัดการ PDF, เอกสาร Office, รูปภาพ, ไฟล์อาร์ไคฟ์, และอื่น ๆ พร้อมคงรูปแบบ, เมตาดาต้า, และการตั้งค่าความปลอดภัย.

GroupDocs.Merger document merging API เป็นไลบรารีที่มุ่งเน้นนักพัฒนา ซึ่งทำให้ซับซ้อนของการจัดการหลายรูปแบบเอกสารเป็นนามธรรม ช่วยให้คุณสามารถรวมไฟล์โดยโปรแกรม, แยกไฟล์ตามหน้า หรือช่วง, และใช้การดำเนินการหน้าขั้นสูง—all while preserving the original layout and metadata.

## ทำไมต้องเลือก GroupDocs.Merger document merging API?
คุณจะได้ความสอดคล้องข้ามแพลตฟอร์ม, การสนับสนุนรูปแบบที่กว้าง, ไม่มีการพึ่งพาภายนอก, ประสิทธิภาพสูง, และความปลอดภัยในตัว—ทั้งหมดในแพคเกจเดียว. API สตรีมข้อมูล, ดังนั้นแม้ไฟล์หลายกิกะไบต์ก็จะถูกประมวลผลด้วยการใช้หน่วยความจำต่ำ, ทำให้เหมาะกับงานแบตช์ฝั่งเซิร์ฟเวอร์.

## ปรับเปลี่ยนวิธีการจัดการเอกสารของคุณข้ามหลายแพลตฟอร์ม
GroupDocs.Merger ให้โซลูชันข้ามแพลตฟอร์มที่ทรงพลังสำหรับการจัดการเอกสารที่ทำให้การทำงานของนักพัฒนากับไฟล์ในแอปพลิเคชันเป็นเรื่องง่าย API ของเราช่วยให้คุณรวมหลายเอกสารเป็นไฟล์เดียว, แยกเอกสารเป็นส่วนย่อย, จัดลำดับหน้า, ใช้ตัวเลือกความปลอดภัย, และอื่น ๆ อีกมาก—ทั้งหมดด้วยโค้ดน้อยที่สุดและประสิทธิภาพสูงสุด.

ไม่ว่าคุณจะพัฒนาในสภาพแวดล้อม .NET หรือ Java, GroupDocs.Merger มอบความสามารถการประมวลผลเอกสารที่สอดคล้อง, มีประสิทธิภาพสูง, ทำงานร่วมกับรูปแบบไฟล์ยอดนิยมกว่า 50 แบบรวมถึง PDF, เอกสาร Office, รูปภาพ, และอื่น ๆ.

## คุณลักษณะหลักและความสามารถ
- **การรวมเอกสารอย่างครอบคลุม** – Combine entire documents or specific pages from multiple sources into a single cohesive file.  
- **การสนับสนุนข้ามรูปแบบ** – Merge different file formats into a unified document (e.g., DOC, XLSX, and images into a single PDF).  
- **การแยกเอกสารอัจฉริยะ** – Divide documents by page numbers, ranges, or extract specific pages as separate files.  
- **การดำเนินการหน้าขั้นสูง** – Move, remove, rotate, swap, and extract pages with precise control.  
- **การจัดการความปลอดภัย** – Add, remove, or update document passwords and permissions.  
- **การสนับสนุนวัตถุ OLE** – Insert documents as OLE objects within Word, Excel, PowerPoint, and Visio files.  
- **ไม่มีการพึ่งพาภายนอก** – Process documents without requiring Microsoft Office or Adobe software.  
- **ประสิทธิภาพสูง** – Optimized for processing large documents and batch operations efficiently.

## รูปแบบไฟล์ที่รองรับ
GroupDocs.Merger works with over 50 file formats across multiple categories:

- **เอกสาร**: PDF, DOC, DOCX, RTF, ODT, XPS, EPUB, HTML  
- **สเปรดชีต**: XLS, XLSX, XLSM, XLSB, ODS, CSV, TSV  
- **งานนำเสนอ**: PPT, PPTX, PPS, PPSX, ODP  
- **รูปภาพ**: JPG, PNG, BMP, GIF, TIFF, SVG  
- **แผนภาพ**: VSDX, VSDM, VSSX, VSTX, VDX, VSX, VTX  
- **ไฟล์อาร์ไคฟ์**: ZIP, TAR, 7Z  
- **และอื่น ๆ อีกมาก**

## [บทเรียน GroupDocs.Merger สำหรับ .NET](./net)

Discover how to integrate powerful document processing capabilities into your .NET applications. Our comprehensive .NET tutorials guide you through every aspect of the GroupDocs.Merger API, from basic operations to advanced implementation scenarios.

With GroupDocs.Merger for .NET, you can create robust document management solutions that work across various .NET frameworks including .NET Standard 2.0, .NET Framework 2.0+, .NET Core 2.0+, and Mono Framework 1.2+.

### บทเรียน .NET ที่จำเป็น

- [รวมและบีบอัดไฟล์](./net/merge-compress-files/) - เรียนรู้การรวมและบีบอัดรูปแบบไฟล์อาร์ไคฟ์ (7z, TAR, ZIP) อย่างมีประสิทธิภาพ  
- [การรวมรูปภาพ](./net/image-merging/) - เชี่ยวชาญเทคนิคการรวมรูปแบบภาพต่าง ๆ (BMP, GIF, PNG, SVG, TIFF)  
- [การรวมเอกสาร](./net/document-merging/) - รวม DOC, DOCX, PDF และรูปแบบเอกสารอื่น ๆ อย่างราบรื่น  
- [การรวมสเปรดชีต](./net/spreadsheet-merging/) - รวมไฟล์ Excel พร้อมคงข้อมูล, สูตร, และการจัดรูปแบบ  
- [การรวม Visio](./net/visio-merging/) - รวมแผนภาพและภาพวาด Visio ด้วยการควบคุมที่แม่นยำ  
- [การรวมงานนำเสนอ](./net/presentation-merging/) - รวมงานนำเสนอ PowerPoint พร้อมคงสไลด์และแอนิเมชัน  

### การดำเนินการ .NET ขั้นสูง

- [การโหลดเอกสาร](./net/document-loading/) - สำรวจเทคนิคต่าง ๆ สำหรับการโหลดเอกสารจากแหล่งต่าง ๆ  
- [ข้อมูลเอกสาร](./net/document-information/) - ดึงและวิเคราะห์เมตาดาต้าและคุณสมบัติของเอกสาร  
- [การรวมเอกสาร](./net/document-joining/) - เรียนรู้ตัวเลือกการรวมเอกสารขั้นสูงและการปรับแต่ง  
- [การรวมตามรูปแบบเฉพาะ](./net/format-specific-merging/) - ค้นหาเทคนิคการรวมที่ปรับให้เหมาะกับรูปแบบไฟล์เฉพาะ  
- [ตัวเลือกการรวมขั้นสูง](./net/advanced-joining-options/) - เชี่ยวชาญสถานการณ์การรวมเอกสารที่ซับซ้อน  
- [ความปลอดภัยของเอกสาร](./net/document-security/) - นำการปกป้องเอกสารที่แข็งแกร่งด้วยการจัดการรหัสผ่าน  
- [การดำเนินการหน้า](./net/page-operations/) - จัดการหน้าของเอกสารด้วยการควบคุมที่แม่นยำ  
- [การสกัดเอกสาร](./net/document-extraction/) - สกัดเนื้อหาเฉพาะจากเอกสารขนาดใหญ่  
- [การนำเข้าเอกสาร](./net/document-import/) - นำเข้าข้อมูลภายนอกเข้าสู่เอกสาร  
- [การดำเนินการรูปภาพ](./net/image-operations/) - ประมวลผลและจัดการไฟล์รูปภาพอย่างมีประสิทธิภาพ  
- [การแยกเอกสาร](./net/document-splitting/) - แบ่งเอกสารโดยใช้กลยุทธ์การแยกต่าง ๆ (การแยกเอกสาร)  
- [การดำเนินการข้อความ](./net/text-operations/) - ทำงานกับเอกสารที่เป็นข้อความอย่างมีประสิทธิภาพ  
- [การให้สิทธิ์ใช้งาน](./net/licensing/) - กำหนดค่า GroupDocs.Merger อย่างเหมาะสมในโครงการของคุณ  

## [บทเรียน GroupDocs.Merger สำหรับ Java](./java)

Transform your Java applications with powerful document processing capabilities. Our Java tutorials provide detailed guidance for implementing GroupDocs.Merger in Java environments, with complete examples that work across major platforms including Windows, Linux, and macOS.

GroupDocs.Merger for Java supports J2SE 7.0 (1.7), J2SE 8.0 (1.8), and Java 10, making it compatible with virtually any Java‑based development project.

### บทเรียน Java ที่จำเป็น

- [การโหลดเอกสาร](./java/document-loading/) - เชี่ยวชาญเทคนิคการโหลดเอกสารจากไฟล์, สตรีม, และ URL  
- [ข้อมูลเอกสาร](./java/document-information/) - ดึงเมตาดาต้าและคุณสมบัติที่มีค่า  
- [การรวมเอกสาร](./java/document-joining/) - รวมไฟล์หลายไฟล์เป็นเอกสารเดียวด้วยการควบคุมที่แม่นยำ  
- [การรวมตามรูปแบบเฉพาะ](./java/format-specific-merging/) - เรียนรู้แนวทางที่ปรับให้เหมาะกับรูปแบบไฟล์ต่าง ๆ  
- [ตัวเลือกการรวมขั้นสูง](./java/advanced-joining-options/) - สำรวจสถานการณ์การรวมที่ซับซ้อนและการปรับแต่ง  
- [ความปลอดภัยของเอกสาร](./java/document-security/) - นำการปกป้องเอกสารที่แข็งแกร่งและการควบคุมสิทธิ์  
- [การดำเนินการหน้า](./java/page-operations/) - จัดการหน้าต่าง ๆ ภายในเอกสาร  
- [การสกัดเอกสาร](./java/document-extraction/) - สกัดเนื้อหาเฉพาะจากเอกสาร  
- [การนำเข้าเอกสาร](./java/document-import/) - นำเข้าข้อมูลภายนอกเข้าสู่เอกสาร  
- [การดำเนินการรูปภาพ](./java/image-operations/) - ทำงานกับไฟล์รูปภาพและการแปลง  
- [การแยกเอกสาร](./java/document-splitting/) - แบ่งเอกสารโดยใช้กลยุทธ์การแยกต่าง ๆ (การแยกเอกสาร)  
- [การดำเนินการข้อความ](./java/text-operations/) - ประมวลผลเอกสารที่เป็นข้อความอย่างมีประสิทธิภาพ  
- [การให้สิทธิ์ใช้งาน](./java/licensing/) - กำหนดค่า GroupDocs.Merger ในสภาพแวดล้อม Java  

## กรณีการใช้งานทั่วไปและประโยชน์
- **การสร้างรายงานอัตโนมัติ:** Merge data‑driven PDFs and Excel sheets into a single report for distribution.  
- **การจัดการเอกสารทางกฎหมาย:** แยกสัญญาขนาดใหญ่เป็นส่วนย่อยเพื่อการตรวจสอบและลงนามที่ง่ายขึ้น.  
- **การย้ายเนื้อหา:** แปลงและรวมเอกสารเก่าจากหลายรูปแบบเป็นไฟล์ PDF มาตรฐาน.  
- **การส่งมอบเอกสารอย่างปลอดภัย:** ใส่รหัสผ่านและสิทธิ์ก่อนส่งไฟล์ที่เป็นความลับให้กับลูกค้า.  

## คำถามที่พบบ่อย

**ถาม: ฉันสามารถใช้ API นี้ในผลิตภัณฑ์เชิงพาณิชย์ได้หรือไม่?**  
ตอบ: ใช่, พร้อมใบอนุญาต GroupDocs ที่ถูกต้อง. มีรุ่นทดลองฟรีสำหรับการประเมิน.

**ถาม: API รองรับ PDF ที่มีการป้องกันด้วยรหัสผ่านหรือไม่?**  
ตอบ: แน่นอน. คุณสามารถเปิด, แก้ไข, และตั้งค่าการป้องกันใหม่ให้กับ PDF ที่เข้ารหัสโดยใช้เมธอดเดียวกัน.

**ถาม: เวอร์ชัน .NET และ Java ใดที่เข้ากันได้?**  
ตอบ: .NET Standard 2.0, .NET Framework 2.0+, .NET Core 2.0+, Mono 1.2+; Java 7, 8, และ 10+ รองรับเต็มที่.

**ถาม: API จัดการไฟล์ขนาดใหญ่มากอย่างไร?**  
ตอบ: มันสตรีมข้อมูลและใช้ขั้นตอนอัลกอริทึมที่ใช้หน่วยความจำน้อย, ทำให้คุณสามารถประมวลผลเอกสารหลายกิกะไบต์โดยไม่ทำให้ระบบทรัพยากรหมด.

**ถาม: มีการสนับสนุน OCR หรือการสกัดข้อความในตัวหรือไม่?**  
ตอบ: แม้ว่า API การรวมหลักจะเน้นการดำเนินการโครงสร้าง, คุณสามารถผสานกับ GroupDocs.Parser เพื่อการสกัดข้อความและ OCR ขั้นสูง.

**ถาม: ฉันจะเริ่มต้นอย่างรวดเร็วได้อย่างไร?**  
ตอบ: ติดตั้งแพคเกจ NuGet (`GroupDocs.Merger`) สำหรับ .NET หรือเพิ่ม dependency ของ Maven สำหรับ Java, แล้วทำตามบทเรียน “Document Loading” เพื่อโหลดไฟล์แรกของคุณ.

**ถาม: ฉันสามารถรวมไฟล์ประเภทต่าง ๆ เป็น PDF เดียวได้หรือไม่?**  
ตอบ: ได้ – API สามารถรวม PDF, Word, Excel, รูปภาพ, และรูปแบบอื่น ๆ จำนวนมากเป็นไฟล์ PDF เดียว.

---

**อัปเดตล่าสุด:** 2026-10-11  
**ทดสอบด้วย:** GroupDocs.Merger 23.12 (latest stable)  
**ผู้เขียน:** GroupDocs  

---