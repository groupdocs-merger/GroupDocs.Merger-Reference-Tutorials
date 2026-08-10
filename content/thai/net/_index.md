---
date: 2026-08-10
description: เรียนรู้วิธีแยกไฟล์ PDF ด้วย GroupDocs.Merger for .NET. คำแนะนำ C# ช่วยคุณแยก
  PDF ขนาดใหญ่, ดึงหน้าออก, และรวมรูปภาพเป็น PDF อย่างมีประสิทธิภาพ.
is_root: true
keywords:
- how to split pdf
- combine images into pdf
- secure pdf with password
- extract pages from pdf
- merge powerpoint presentations
lastmod: 2026-08-10
linktitle: บทแนะนำ GroupDocs.Merger for .NET
og_description: เรียนรู้วิธีแยกไฟล์ PDF ด้วย GroupDocs.Merger for .NET. คำแนะนำ C#
  ช่วยคุณแยก PDF ขนาดใหญ่, ดึงหน้าออก, และรวมรูปภาพเป็น PDF อย่างมีประสิทธิภาพ.
og_image_alt: 'Developer guide: split PDF files using GroupDocs.Merger for .NET in
  C#'
og_title: วิธีแยก PDF ด้วย GroupDocs.Merger for .NET – คำแนะนำ
schemas:
- author: GroupDocs
  dateModified: '2026-08-10'
  description: Learn how to split PDF files with GroupDocs.Merger for .NET. C# tutorials
    guide you to split large PDFs, extract pages, and combine images into PDF efficiently.
  headline: How to split PDF with GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to split PDF files with GroupDocs.Merger for .NET. C# tutorials
    guide you to split large PDFs, extract pages, and combine images into PDF efficiently.
  name: How to split PDF with GroupDocs.Merger for .NET
  steps:
  - name: load the PDF document
    text: Create a `PdfDocument` instance by passing the file path or a stream. The
      constructor reads the document header without loading all pages into memory.
  - name: split by page range
    text: Use the `Split` method, providing a `PageRange` object that defines the
      start and end pages. The method returns a collection of new `PdfDocument` objects,
      each representing the requested segment.
  - name: save the resulting files
    text: Iterate over the split documents and call `Save` with a unique file name.
      You can also apply compression or password protection before saving.
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then use `Split` or
      `Extract` as you would with an unprotected file.
    question: Can I split a password‑protected PDF?
  - answer: There is no hard limit; the library streams pages, so you can split PDFs
      with thousands of pages as long as you have sufficient disk space for the output
      files.
    question: How many pages can I split at once?
  - answer: It supports cross‑format merging, allowing you to combine PPTX slides
      with PDF pages into a single PDF output.
    question: Does GroupDocs.Merger support merging PowerPoint files with PDFs?
  - answer: Enable streaming mode (`PdfLoadOptions.Stream = true`) to keep memory
      usage low while splitting or extracting pages.
    question: What is the recommended way to handle very large PDFs?
  - answer: Yes. Use the `Bookmarks` collection to identify chapter start pages and
      programmatically call `Split` for each range.
    question: Is there a way to automate splitting of every chapter in a PDF?
  type: FAQPage
tags:
- split PDF
- GroupDocs.Merger
- C# document processing
- PDF manipulation
- document merging
title: วิธีแยก PDF ด้วย GroupDocs.Merger for .NET
type: docs
url: /th/net/
weight: 10
---

# วิธีการแยก PDF ด้วย GroupDocs.Merger สำหรับ .NET

## การจัดการเอกสารขั้นสูงด้วย GroupDocs.Merger

`GroupDocs.Merger for .NET` เป็นไลบรารี .NET ที่ช่วยให้นักพัฒนาสามารถรวม, แยก, และจัดการเอกสารได้กว่า 50 รูปแบบไฟล์ หากคุณต้องการทราบ **วิธีการแยก PDF** คู่มือนี้จะแสดงขั้นตอนที่แม่นยำโดยใช้ GroupDocs.Merger for .NET พร้อมสถานการณ์จริงและเคล็ดลับการปฏิบัติที่ดีที่สุด

## คำตอบอย่างรวดเร็ว
- **วิธีการแยก PDF เป็นหน้าเดี่ยว?** เรียก `PdfDocument.Split` พร้อมช่วงหน้าที่ `1‑1` สำหรับแต่ละหน้า.  
- **ฉันสามารถดึงเฉพาะหน้าที่ต้องการได้หรือไม่?** ได้ – ส่งหมายเลขหน้าที่ต้องการไปยัง `Split` หรือ `Extract`.  
- **รองรับการป้องกันด้วยรหัสผ่านหรือไม่?** แน่นอน; ใช้ `PdfDocument.Protect` ก่อนบันทึก.  
- **วิธีการรวมรูปภาพเป็น PDF?** โหลดแต่ละรูปเป็น `PdfPage` แล้วเพิ่มลงในเอกสารใหม่.  
- **สำหรับ PDF ขนาดใหญ่ล่ะ?** ใช้โหมดสตรีมมิงเพื่อหลีกเลี่ยงการโหลดไฟล์ทั้งหมดเข้าสู่หน่วยความจำ.

## อะไรคือวิธีการแยก PDF?
**How to split PDF** หมายถึงกระบวนการแยกไฟล์ PDF หลายหน้าเป็นเอกสาร PDF ย่อยแยกกัน—โดยอิงจากหน้าเดี่ยว, ช่วงหน้า, หรือเกณฑ์ที่กำหนดเอง—โดยใช้ API โปรแกรม การทำเช่นนี้มักใช้เพื่อแยกส่วน, ลดขนาดไฟล์, หรือเตรียมเอกสารสำหรับการแจกจ่าย การดำเนินการนี้สามารถทำได้โดยโปรแกรมผ่านไลบรารีเช่น GroupDocs.Merger ซึ่งให้เมธอดสำหรับระบุช่วงหน้าที่แน่นอนและการตั้งค่าการส่งออก

## ทำไมต้องใช้ GroupDocs.Merger สำหรับการแยก PDF?
GroupDocs.Merger ประมวลผลรูปแบบไฟล์เข้าและออก **55+** รูปแบบ, รองรับ PDF ขนาดถึง **2 GB** โดยไม่ต้องโหลดเต็มในหน่วยความจำ, และสามารถแยก PDF 500 หน้าได้ภายใน **3 วินาที** บนเซิร์ฟเวอร์ทั่วไป ตัวเลขประสิทธิภาพที่ระบุทำให้เป็นตัวเลือกที่เชื่อถือได้สำหรับสายงานเอกสารที่ต้องการความเร็วสูง

## วิธีการแยกไฟล์ PDF ด้วย GroupDocs.Merger?
PdfDocument คือคลาสหลักที่แทนไฟล์ PDF ภายใน GroupDocs.Merger เพื่อแยก PDF ก่อนอื่นให้โหลดไฟล์ต้นทางเข้าสู่ตัวอย่าง PdfDocument แล้วระบุหน้าที่ต้องการดึงโดยใช้เมธอด Split เมธอดจะคืนค่าออบเจ็กต์ PdfDocument แยกสำหรับแต่ละส่วน ซึ่งคุณสามารถบันทึกแยกกันได้ วิธีนี้ทำงานกับขนาดเอกสารใด ๆ และต้องการเพียงไม่กี่บรรทัดของโค้ด

### ขั้นตอนที่ 1: โหลดเอกสาร PDF
สร้างอินสแตนซ์ `PdfDocument` โดยส่งพาธไฟล์หรือสตรีม ตัวสร้างจะอ่านส่วนหัวของเอกสารโดยไม่โหลดทุกหน้าเข้าสู่หน่วยความจำ

### ขั้นตอนที่ 2: แยกตามช่วงหน้า
ใช้เมธอด `Split` โดยให้วัตถุ `PageRange` ที่กำหนดหน้าต้นและหน้าสุดท้าย เมธอดจะคืนคอลเลกชันของออบเจ็กต์ `PdfDocument` ใหม่แต่ละออบเจ็กต์แทนส่วนที่ร้องขอ

### ขั้นตอนที่ 3: บันทึกไฟล์ที่ได้
วนลูปผ่านเอกสารที่แยกและเรียก `Save` พร้อมชื่อไฟล์ที่ไม่ซ้ำกัน คุณยังสามารถใช้การบีบอัดหรือการป้องกันด้วยรหัสผ่านก่อนบันทึกได้

## วิธีการรวมรูปภาพเป็น PDF?
PdfDocument เป็นคลาสหลักที่ใช้สร้างไฟล์ PDF ใหม่ใน GroupDocs.Merger เพื่อรวมรูปภาพ ให้โหลดไฟล์รูปแต่ละไฟล์และเพิ่มเป็นหน้ใหม่ในอินสแตนซ์ PdfDocument ใหม่โดยใช้เมธอด AddPage หลังจากเพิ่มรูปทั้งหมดแล้ว ให้บันทึกเอกสาร ซึ่งจะรักษาความละเอียดดั้งเดิมและฝังรูปเป็นหน้าที่อิงเวกเตอร์เมื่อรูปแบบรองรับ ผลลัพธ์คือ PDF คุณภาพสูงที่มีรูปภาพทั้งหมดที่ให้มา

## วิธีการปกป้อง PDF ด้วยรหัสผ่าน?
PdfDocument คือออบเจ็กต์ที่แทนเอกสาร PDF และให้ฟีเจอร์ความปลอดภัย หลังจากโหลดหรือสร้าง PdfDocument ให้เรียกเมธอด Protect พร้อมรหัสผ่านผู้ใช้และแฟล็กสิทธิ์เพิ่มเติมเช่นการพิมพ์หรือการคัดลอก เมธอดจะเข้ารหัสไฟล์ และเมื่อคุณเรียก Save ต่อไป PDF ที่ได้จะเปิดได้เฉพาะผู้ใช้ที่รู้รหัสผ่านเท่านั้น เพื่อรับประกันความลับ

## วิธีการดึงหน้าจาก PDF?
PdfDocument คือคลาสหลักที่แทนไฟล์ PDF ใน GroupDocs.Merger เพื่อดึงหน้า ให้สร้างอินสแตนซ์ PdfDocument ด้วยไฟล์ต้นทาง แล้วเรียกเมธอด Extract พร้อมรายการหมายเลขหน้าที่ต้องการเก็บ เมธอดจะคืนค่า PdfDocument ใหม่ที่มีเฉพาะหน้าที่เลือก ซึ่งคุณสามารถบันทึกเป็น PDF แยกได้ เทคนิคนี้มีประโยชน์สำหรับสร้างรายงานแบบกำหนดเองหรือแชร์ส่วนเฉพาะ

## วิธีการรวมงานนำเสนอ PowerPoint?
Merge คือเมธอดที่ GroupDocs.Merger ให้มาเพื่อเชื่อมต่อหลายเอกสารเป็นไฟล์ผลลัพธ์เดียว เพื่อรวมงานนำเสนอ PowerPoint ให้โหลดไฟล์ .pptx แต่ละไฟล์เป็นออบเจ็กต์ Document แล้วเรียกเมธอด Merge บน PdfDocument หรือ PresentationDocument ใหม่ พร้อมส่งคอลเลกชันของเอกสารต้นทาง ไลบรารีจะรักษาแอนิเมชันสไลด์, การเปลี่ยนแปลง, และรูปแบบ ทำให้ได้งานนำเสนอรวมที่สามารถบันทึกเป็น PDF หรือ PPTX

## วิธีการแยกหน้าขนาดใหญ่ของ PDF?
PdfLoadOptions.Stream เป็นคุณสมบัติที่เปิดโหมดสตรีมมิง ทำให้ GroupDocs.Merger สามารถประมวลผลไฟล์ PDF ขนาดใหญ่โดยไม่ต้องโหลดเอกสารทั้งหมดเข้าสู่หน่วยความจำ เมื่อทำงานกับ PDF ขนาดใหญ่มาก ให้ตั้งค่า PdfLoadOptions.Stream เป็น true ก่อนโหลดไฟล์ วิธีนี้ลดการใช้หน่วยความจำและให้คุณแยกหรือดึงหน้าต่าง efficiently แม้ไฟล์ใหญ่กว่า 1 GB โดยยังคงประสิทธิภาพ

## คุณลักษณะหลักและความสามารถ
- **รวมหลายเอกสาร** จากรูปแบบกว่า 55 รูปแบบเป็นไฟล์เดียวที่สอดคล้องกัน  
- **รวมหน้าหรือช่วงหน้าที่ระบุ** จากเอกสารต้นทางต่าง ๆ  
- **แยกเอกสาร** ตามหมายเลขหน้า, ช่วงหน้า, หรือเกณฑ์หน้าเลขคี่/คู่  
- **จัดการลำดับหน้า** ด้วยการย้าย, ลบ, หมุน, หรือสลับ  
- **ปกป้องเอกสาร** ด้วยการตั้งรหัสผ่านและการควบคุมสิทธิ์แบบละเอียด  
- **ดึงหน้าที่ระบุ** เพื่อสร้างเอกสารใหม่ที่มุ่งเป้า  
- **ประมวลผลรูปแบบกว่า 55** รวมถึง PDF, Office, รูปภาพ, และไฟล์บีบอัดด้วย API เดียว  

## หมวดหมู่บทเรียน GroupDocs.Merger สำหรับ .NET

### [รวมและบีบอัดไฟล์](./merge-compress-files/)
เรียนรู้การรวมและบีบอัดไฟล์รูปแบบ 7z, TAR, และ ZIP อย่างมีประสิทธิภาพ บทเรียนของเราจะพาคุณผ่านการรวมไฟล์บีบอัดด้วย GroupDocs.Merger for .NET พร้อมตัวอย่าง C# ครบถ้วน

### [การรวมรูปภาพ](./image-merging/)
เชี่ยวชาญเทคนิคการรวม BMP, GIF, PNG, SVG, TIFF และรูปแบบอื่น ๆ ค้นพบวิธีการรวมรูปภาพเป็นเอกสารเดียวโดยคงคุณภาพและรูปแบบ

### [การรวมเอกสาร](./document-merging/)
รวม DOC, DOCX, PDF, RTF และรูปแบบเอกสารต่าง ๆ เป็นไฟล์เดียว บทเรียนเหล่านี้ครอบคลุมสถานการณ์การรวมเอกสารพร้อมขั้นตอนการทำงานและแนวปฏิบัติที่ดีที่สุด

### [การรวมสเปรดชีต](./spreadsheet-merging/)
รวมไฟล์ Excel (XLAM, XLS, XLSX, XLSM, XLTX) และรูปแบบสเปรดชีตอื่น ๆ พร้อมรักษาความสมบูรณ์ของข้อมูล, สูตร, และรูปแบบด้วยคำแนะนำทีละขั้นตอน

### [การรวม Visio](./visio-merging/)
รวมแผนภาพและภาพวาด Visio (VDX, VSDM, VSDX, VSSM, VSSX) อย่างมีประสิทธิภาพด้วยบทเรียนเฉพาะสำหรับการจัดการเอกสารแผนภาพในแอปพลิเคชัน .NET

### [การรวมงานนำเสนอ](./presentation-merging/)
เรียนรู้การรวม PowerPoint และรูปแบบงานนำเสนออื่น ๆ (PPS, PPSX, PPT, OTP) พร้อมคงสไลด์, แอนิเมชัน, และรูปแบบด้วยตัวอย่างโค้ดครบถ้วน

### [การโหลดเอกสาร](./document-loading/)
ค้นพบวิธีการโหลดเอกสารจากไฟล์, สตรีม, และ URL พร้อมการกำหนดค่าที่เหมาะสมสำหรับรูปแบบต่าง ๆ ทำความเข้าใจขั้นตอนแรกที่สำคัญในการประมวลผลเอกสาร

### [ข้อมูลเอกสาร](./document-information/)
สกัดเมตาดาต้าที่มีค่าจากเอกสารรวมถึงรายละเอียดรูปแบบ, จำนวนหน้า, และคุณสมบัติต่าง ๆ เรียนรู้การวิเคราะห์เอกสารด้วยโปรแกรมก่อนการประมวลผล

### [การรวมเอกสาร](./document-joining/)
รวมไฟล์หลายไฟล์อย่างไร้รอยต่อด้วยเทคนิคการรวมขั้นสูง บทเรียนของเราจะแสดงวิธีการรวมเอกสารด้วยการควบคุมเนื้อหาและโครงสร้างอย่างแม่นยำ

### [การรวมตามรูปแบบเฉพาะ](./format-specific-merging/)
สำรวจการดำเนินการรวมที่ปรับให้เหมาะกับรูปแบบไฟล์เฉพาะ เรียนรู้เทคนิคพิเศษสำหรับประเภทเอกสารต่าง ๆ เพื่อให้ได้ผลลัพธ์ที่ดีที่สุด

### [ตัวเลือกการรวมขั้นสูง](./advanced-joining-options/)
ยกระดับการรวมเอกสารด้วยบทเรียนขั้นสูงที่ครอบคลุมการเลือกหน้าซับซ้อน, การรวมข้ามรูปแบบ, และกลยุทธ์การคงรักษาเนื้อหา

### [ความปลอดภัยของเอกสาร](./document-security/)
นำการปกป้องเอกสารไปใช้จริง เรียนรู้การเพิ่ม, ลบ, และอัปเดตรหัสผ่าน, จัดการสิทธิ์, และรับรองความลับของเอกสารในแอปพลิเคชันของคุณ

### [การดำเนินการกับหน้า](./page-operations/)
ควบคุมหน้าต่างเอกสารอย่างแม่นยำด้วยบทเรียนการจัดลำดับใหม่, หมุน, ลบ, และแก้ไขหน้าเดี่ยวเพื่อการจัดการเอกสารที่กำหนดเอง

### [การสกัดเอกสาร](./document-extraction/)
สกัดเนื้อหาเฉพาะจากเอกสารด้วยคู่มือโดยละเอียด เรียนรู้การเลือกและบันทึกหน้า หรือส่วนที่ต้องการเป็นไฟล์แยกด้วยโค้ดขั้นต่ำ

### [การนำเข้าเอกสาร](./document-import/)
เพิ่มเนื้อหาภายนอกลงในเอกสารรวมถึงวัตถุ OLE และไฟล์ฝัง เรียนรู้การนำเข้าข้อมูลจากแหล่งต่าง ๆ เพื่อเสริมความสมบูรณ์ของเอกสาร

### [การดำเนินการกับรูปภาพ](./image-operations/)
ประมวลผลไฟล์รูปภาพอย่างมีประสิทธิภาพด้วยบทเรียนครบวงจรของเราที่ครอบคลุมการรวมรูป, การแปลง, และเทคนิคการจัดการรูปภาพในแอป .NET ของคุณ

### [การแยกเอกสาร](./document-splitting/)
แบ่งเอกสารอย่างชาญฉลาดเป็นส่วนย่อยด้วยบทเรียนการแยกเอกสารตามหมายเลขหน้า, ช่วงหน้า, และเกณฑ์ที่กำหนดเอง

### [การดำเนินการกับข้อความ](./text-operations/)
ทำงานกับเอกสารประเภทข้อความอย่างมีประสิทธิภาพด้วยคู่มือการประมวลผล TXT, CSV, และรูปแบบข้อความอื่น ๆ รวมถึงเทคนิคการแยกและรวมบรรทัด

### [การให้สิทธิ์ใช้งาน](./licensing/)
กำหนดค่า GroupDocs.Merger อย่างถูกต้องในโปรเจกต์ของคุณด้วยบทเรียนการให้สิทธิ์ที่ละเอียด ครอบคลุมทุกสถานการณ์การปรับใช้และสภาพแวดล้อม

## รูปแบบไฟล์ที่รองรับ

GroupDocs.Merger for .NET รองรับ **กว่า 55** รูปแบบเอกสารยอดนิยม รวมถึง:

- **รูปแบบเอกสาร**: PDF, DOC, DOCX, RTF, ODT, XPS, EPUB, HTML
- **สเปรดชีต**: XLS, XLSX, XLSM, XLSB, ODS, CSV, TSV
- **งานนำเสนอ**: PPT, PPTX, PPS, PPSX, ODP
- **รูปภาพ**: BMP, GIF, JPG, PNG, SVG, TIFF
- **ไดอะแกรม**: VDX, VSDX, VSX, VTX, VSTX, VSSX
- **ไฟล์บีบอัด**: ZIP, TAR, 7Z
- **และอื่น ๆ อีกมาก!**

## คำถามที่พบบ่อย

**Q: ฉันสามารถแยก PDF ที่มีการป้องกันด้วยรหัสผ่านได้หรือไม่?**  
A: ได้. โหลดเอกสารพร้อมพารามิเตอร์รหัสผ่าน แล้วใช้ `Split` หรือ `Extract` เช่นเดียวกับไฟล์ที่ไม่ได้ป้องกัน

**Q: ฉันสามารถแยกได้กี่หน้าพร้อมกัน?**  
A: ไม่มีขีดจำกัดที่แน่นอน; ไลบรารีสตรีมหน้าต่าง ๆ ดังนั้นคุณสามารถแยก PDF ที่มีหลายพันหน้าได้ตราบใดที่มีพื้นที่ดิสก์เพียงพอสำหรับไฟล์ผลลัพธ์

**Q: GroupDocs.Merger รองรับการรวมไฟล์ PowerPoint กับ PDF หรือไม่?**  
A: รองรับการรวมข้ามรูปแบบ ทำให้คุณสามารถรวมสไลด์ PPTX กับหน้าของ PDF เป็นไฟล์ PDF เดียวได้

**Q: วิธีที่แนะนำในการจัดการ PDF ขนาดใหญ่มากคืออะไร?**  
A: เปิดโหมดสตรีมมิง (`PdfLoadOptions.Stream = true`) เพื่อลดการใช้หน่วยความจำขณะแยกหรือดึงหน้า

**Q: มีวิธีอัตโนมัติในการแยกแต่ละบทใน PDF หรือไม่?**  
A: มี. ใช้คอลเลกชัน `Bookmarks` เพื่อระบุหน้าที่เริ่มต้นของแต่ละบทและเรียก `Split` สำหรับแต่ละช่วงโดยโปรแกรม

---

**อัปเดตล่าสุด:** 2026-08-10  
**ทดสอบกับ:** GroupDocs.Merger 23.9 for .NET  
**ผู้เขียน:** GroupDocs

## บทเรียนที่เกี่ยวข้อง

- [วิธีการรวมไฟล์ PDF อย่างมีประสิทธิภาพโดยใช้ GroupDocs.Merger สำหรับ .NET](/merger/net/format-specific-merging/merge-pdfs-groupdocs-merger-net/)
- [วิธีการรวมหน้าต่าง PDF เฉพาะด้วย GroupDocs.Merger สำหรับ .NET: คู่มือฉบับสมบูรณ์](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [วิธีการรวมไฟล์ PDF พร้อมบุ๊กมาร์กโดยใช้ GroupDocs.Merger สำหรับ .NET](/merger/net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/)