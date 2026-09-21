---
date: '2026-09-21'
description: เรียนรู้วิธีฝัง pdf ใน powerpoint เป็นวัตถุ OLE ด้วย GroupDocs.Merger
  สำหรับ .NET คู่มือขั้นตอนต่อขั้นตอนนี้จะแสดงการเรียก API ที่แม่นยำและแนวปฏิบัติที่ดีที่สุด
keywords:
- embed pdf in powerpoint
- convert pdf to ole
- insert pdf as ole
- add ole object powerpoint
lastmod: '2026-09-21'
og_description: ฝัง pdf ใน powerpoint ด้วย GroupDocs.Merger สำหรับ .NET ทำตามบทแนะนำสั้นนี้เพื่อเพิ่มวัตถุ
  OLE ตั้งค่าตัวเลือก และหลีกเลี่ยงข้อผิดพลาดทั่วไป
og_image_alt: Screenshot of PowerPoint slide with embedded PDF OLE object using GroupDocs.Merger
og_title: ฝัง pdf ใน powerpoint – ฝัง PDF เป็น OLE ด้วย GroupDocs.Merger
schemas:
- author: GroupDocs
  dateModified: '2026-09-21'
  description: Learn how to embed pdf in powerpoint as an OLE object with GroupDocs.Merger
    for .NET. This step‑by‑step guide shows you the exact API calls and best practices.
  headline: How to embed pdf in powerpoint as OLE using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to embed pdf in powerpoint as an OLE object with GroupDocs.Merger
    for .NET. This step‑by‑step guide shows you the exact API calls and best practices.
  name: How to embed pdf in powerpoint as OLE using GroupDocs.Merger for .NET
  steps:
  - name: '**Corporate briefings** – attach the latest financial report without inflating
      the deck size.'
    text: '**Corporate briefings** – attach the latest financial report without inflating
      the deck size.'
  - name: '**Academic lectures** – provide full‑text research papers alongside slide
      summaries.'
    text: '**Academic lectures** – provide full‑text research papers alongside slide
      summaries.'
  - name: '**Project status updates** – embed a live project plan that stakeholders
      can open for details.'
    text: '**Project status updates** – embed a live project plan that stakeholders
      can open for details.'
  - name: '**Sales decks** – include product spec sheets that sales reps can open
      on demand.'
    text: '**Sales decks** – include product spec sheets that sales reps can open
      on demand.'
  - name: '**Technical workshops** – present schematics or datasheets that engineers
      can inspect instantly.'
    text: '**Technical workshops** – present schematics or datasheets that engineers
      can inspect instantly.'
  type: HowTo
- questions:
  - answer: Yes. Call `ImportDocument` for each PDF, specifying a different `SlideNumber`
      or position on the same slide.
    question: Can I embed multiple PDFs into a single presentation?
  - answer: The practical limit is dictated by your server’s memory; embeddings of
      up to 500 MB have been tested without issues when streaming.
    question: How large a PDF can I embed?
  - answer: Absolutely. The embedded PDF opens in the default viewer, preserving all
      internal links and bookmarks.
    question: Does the OLE object retain interactive elements like hyperlinks?
  - answer: Provide the password via the `Password` property of `OlePresentationOptions`
      before calling `ImportDocument`.
    question: What if the PDF is password‑protected?
  - answer: The OLE format is supported by PowerPoint 2007 and later, including Office
      365.
    question: Will the embedded object work on all versions of PowerPoint?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- OLE object
- PowerPoint automation
title: วิธีฝัง pdf ใน powerpoint เป็น OLE ด้วย GroupDocs.Merger สำหรับ .NET
type: docs
url: /th/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/
weight: 1
---

# ฝัง PDF ใน PowerPoint เป็น OLE ด้วย GroupDocs.Merger สำหรับ .NET

การฝัง PDF โดยตรงลงในสไลด์ PowerPoint ช่วยให้คุณคงเอกสารต้นฉบับไว้โดยไม่เปลี่ยนแปลงขณะให้ผู้ชมเข้าถึงได้ทันที ในบทแนะนำนี้คุณจะได้เรียนรู้ **วิธีฝัง PDF ใน PowerPoint** เป็นอ็อบเจ็กต์ OLE ด้วย GroupDocs.Merger สำหรับ .NET, ดูตัวเลือก API ที่จำเป็น, และค้นหาเคล็ดลับเพื่อประสิทธิภาพที่เชื่อถือได้.

## คำตอบด่วน
- **ไลบรารีใดจัดการการฝัง OLE?** GroupDocs.Merger for .NET ให้คลาส `OlePresentationOptions` สำหรับวัตถุประสงค์นี้.  
- **ฉันต้องการไลเซนส์หรือไม่?** ไลเซนส์ทดลองใช้งานได้สำหรับการพัฒนา; ไลเซนส์เต็มรูปแบบจำเป็นสำหรับการใช้งานในสภาพแวดล้อมการผลิต.  
- **ฉันสามารถฝัง PDF มากกว่าหนึ่งไฟล์ได้หรือไม่?** ได้ – ทำซ้ำขั้นตอนการนำเข้าสำหรับแต่ละสไลด์ที่คุณต้องการ.  
- **เวอร์ชัน .NET ที่รองรับคืออะไร?** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7.  
- **กระบวนการนี้มีประสิทธิภาพด้านหน่วยความจำหรือไม่?** API สตรีมไฟล์, ดังนั้นแม้ PDF หลายร้อยหน้า ก็สามารถฝังได้โดยไม่ต้องโหลดไฟล์ทั้งหมดเข้าสู่หน่วยความจำ.

## การฝัง PDF ใน PowerPoint คืออะไร?
**ฝัง PDF ใน PowerPoint** หมายถึงการแทรกไฟล์ PDF เป็นอ็อบเจ็กต์ OLE (Object Linking and Embedding) เพื่อให้สไลด์แสดงไอคอนหรือพรีวิวที่เมื่อดับเบิลคลิกจะเปิด PDF ต้นฉบับในโปรแกรมดูเริ่มต้น วิธีนี้รักษาการจัดรูปแบบ, ลิงก์, และการตั้งค่าความปลอดภัยของเอกสารต้นฉบับ.

## ทำไมต้องใช้การฝัง OLE แทนการแปลง PDF?
การฝังช่วยคงขนาดไฟล์และรูปแบบเดิมไว้, ขจัดข้อผิดพลาดจากการแปลง, และให้คุณอัปเดต PDF ต้นฉบับโดยไม่ต้องส่งออกพรีเซนเทชันใหม่ GroupDocs.Merger รองรับ **รูปแบบอินพุตและเอาต์พุตกว่า 50+** และสามารถฝัง PDF ขนาดหลายร้อยเมกะไบต์ได้โดยสตรีมข้อมูลเพื่อให้การใช้หน่วยความจำน้อยกว่า 100 MB.

## ข้อกำหนดเบื้องต้น
- Visual Studio 2022 (หรือ IDE ที่รองรับ .NET ใดก็ได้)  
- .NET Framework 4.5+ หรือ .NET Core 3.1+ runtime  
- ไลเซนส์ GroupDocs.Merger สำหรับ .NET ที่ถูกต้อง (ทดลองหรือเชิงพาณิชย์)  
- ไฟล์ PowerPoint (.pptx) และ PDF ที่คุณต้องการฝัง  

## การตั้งค่า GroupDocs.Merger สำหรับ .NET

### ฉันจะติดตั้งไลบรารีอย่างไร?
**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI** – search for “GroupDocs.Merger” and click **Install** to get the latest version.

### ฉันจะได้รับไลเซนส์อย่างไร?
- **Free trial** – sign up on the GroupDocs website for a temporary license key.  
- **Temporary license** – request an extended trial if you need more than 30 days.  
- **Full purchase** – buy a commercial license for unlimited production use.

### ฉันจะเริ่มต้นใช้งาน API อย่างไร?
`Merger` is the primary class that provides document manipulation operations such as import, merge, and conversion.  
Add the required `using` directives at the top of your C# file and create a `Merger` instance with the license file path:

```csharp
using System;
using GroupDocs.Merger.Domain.Options;
using GroupDocs.Merger;
using System.IO;
```  

## คู่มือการใช้งาน

### วิธีฝัง PDF ใน PowerPoint เป็น OLE?
โหลดพรีเซนเทชันของคุณ, กำหนดค่าตัวเลือก OLE, และเรียกเมธอด import – การดำเนินการทั้งหมดเสร็จสิ้นในสามขั้นตอนเชิงตรรกะ.

**ขั้นตอน 1 – กำหนดตำแหน่งไฟล์**  
ระบุตำแหน่งเส้นทางแบบ absolute หรือ relative สำหรับ PDF ต้นฉบับ, ไฟล์ PowerPoint ปลายทาง, และโฟลเดอร์ที่พรีเซนเทชันที่แก้ไขจะถูกบันทึก.

**ขั้นตอน 2 – กำหนดค่าตัวเลือก OLE**  
`OlePresentationOptions` คือคลาสที่บอก GroupDocs.Merger ว่าไฟล์ใดจะฝัง, บนสไลด์ใด, และที่พิกัดใด. นอกจากนี้ยังให้คุณตั้งค่าความกว้าง, ความสูง, และโหมดการแสดงของอ็อบเจ็กต์ที่ฝัง.

**ขั้นตอน 3 – นำเข้า PDF**  
`ImportDocument` คือการเรียก API ของ Merger ที่แทรกอ็อบเจ็กต์ OLE ลงในไฟล์ PowerPoint โดยใช้ตัวเลือกที่กำหนด วิธีนี้สตรีม PDF ไปยังสไลด์โดยไม่โหลดเอกสารทั้งหมดเข้าสู่หน่วยความจำ.

#### ตัวกำหนดนิยาม
- `OlePresentationOptions` คือคอนเทนเนอร์ของตัวเลือกที่กำหนดไฟล์ที่ฝัง, ตำแหน่ง (X/Y), ขนาด, และหมายเลขสไลด์เป้าหมาย.  
- `ImportDocument` คือการเรียก API ของ Merger ที่แทรกอ็อบเจ็กต์ OLE ลงในไฟล์ PowerPoint โดยใช้ตัวเลือกที่ให้มา.

## พารามิเตอร์การกำหนดค่าทั่วไป
- **SlideNumber** – ดัชนีเริ่มจาก 1 ของสไลด์ที่จะแสดงอ็อบเจ็กต์ OLE.  
- **XCoordinate / YCoordinate** – ตำแหน่งวัดเป็นจุดจากมุมซ้ายบนของสไลด์.  
- **Width / Height** – มิติของตำแหน่งวาง OLE; ตั้งเป็น 0 เพื่อใช้ขนาดเริ่มต้น.  
- **ObjectName** – ชื่อที่เป็นมิตร (ไม่บังคับ) ที่แสดงเมื่ออ็อบเจ็กต์ถูกเลือกใน PowerPoint.

## การประยุกต์ใช้งานจริง
การฝัง PDF เป็นอ็อบเจ็กต์ OLE มีประโยชน์ในหลายสถานการณ์จริง:
1. **การบรรยายองค์กร** – แนบรายงานการเงินล่าสุดโดยไม่ทำให้ขนาดสไลด์เพิ่มขึ้น.  
2. **การบรรยายทางวิชาการ** – ให้เอกสารวิจัยเต็มข้อความพร้อมสรุปสไลด์.  
3. **อัปเดตสถานะโครงการ** – ฝังแผนโครงการแบบเรียลไทม์ที่ผู้มีส่วนได้ส่วนเสียสามารถเปิดดูรายละเอียด.  
4. **สไลด์การขาย** – รวมแผ่นสเปคสินค้าให้พนักงานขายเปิดตามต้องการ.  
5. **เวิร์กช็อปเทคนิค** – นำเสนอแผนภาพหรือข้อมูลจำเพาะที่วิศวกรสามารถตรวจสอบได้ทันที.

## พิจารณาด้านประสิทธิภาพ
เพื่อให้กระบวนการฝังเร็วและเป็นมิตรต่อหน่วยความจำ:
- **สตรีมไฟล์** – GroupDocs.Merger อ่านและเขียนสตรีม, ดังนั้นแม้ PDF 200 หน้า ก็ใช้ RAM น้อยกว่า 100 MB.  
- **ประมวลผลเป็นชุด** – เมื่ออัปเดตพรีเซนเทชันหลายไฟล์, ใช้ `Merger` อินสแตนซ์เดียวและปิดสตรีมโดยเร็ว.  
- **ปรับขนาด PDF ขนาดใหญ่** – บีบอัดหรือทำดาวน์ซัมพล์ภาพใน PDF ต้นฉบับหากพบว่าการโหลดช้า.

## คำถามที่พบบ่อย

**ถาม: ฉันสามารถฝัง PDF หลายไฟล์ในพรีเซนเทชันเดียวได้หรือไม่?**  
A: ได้. เรียก `ImportDocument` สำหรับแต่ละ PDF, ระบุ `SlideNumber` หรือตำแหน่งที่แตกต่างกันบนสไลด์เดียวกัน.

**ถาม: ฉันสามารถฝัง PDF ขนาดเท่าไหร่ได้?**  
A: ขีดจำกัดเชิงปฏิบัติกำหนดโดยหน่วยความจำของเซิร์ฟเวอร์ของคุณ; การฝังขนาดสูงสุดถึง 500 MB ได้รับการทดสอบแล้วว่าไม่มีปัญหาเมื่อสตรีม.

**ถาม: อ็อบเจ็กต์ OLE รักษาองค์ประกอบเชิงโต้ตอบเช่นลิงก์หรือไม่?**  
A: แน่นอน. PDF ที่ฝังจะเปิดในโปรแกรมดูเริ่มต้น, รักษาลิงก์ภายในและบุ๊กมาร์กทั้งหมด.

**ถาม: ถ้า PDF มีการป้องกันด้วยรหัสผ่านจะทำอย่างไร?**  
A: ให้รหัสผ่านผ่านคุณสมบัติ `Password` ของ `OlePresentationOptions` ก่อนเรียก `ImportDocument`.

**ถาม: อ็อบเจ็กต์ที่ฝังจะทำงานบน PowerPoint ทุกเวอร์ชันหรือไม่?**  
A: รูปแบบ OLE รองรับโดย PowerPoint 2007 และรุ่นต่อไป รวมถึง Office 365.

## สรุป
ตอนนี้คุณมีเวิร์กโฟลว์ครบถ้วนพร้อมใช้งานในสภาพแวดล้อมการผลิตสำหรับ **ฝัง PDF ใน PowerPoint** เป็นอ็อบเจ็กต์ OLE ด้วย GroupDocs.Merger สำหรับ .NET. ด้วยการสตรีมไฟล์, การกำหนดค่า `OlePresentationOptions`, และการเรียก `ImportDocument`, คุณสามารถเสริมพรีเซนเทชันด้วย PDF ต้นฉบับพร้อมรักษาการใช้หน่วยความจำให้ต่ำและคงคุณลักษณะเชิงโต้ตอบทั้งหมด. สำรวจความสามารถเพิ่มเติมของ Merger เช่น การรวมสไลด์, การแปลงรูปแบบ, และการใส่ลายน้ำเพื่อทำให้กระบวนการเอกสารของคุณอัตโนมัติมากยิ่งขึ้น.

---

**อัปเดตล่าสุด:** 2026-09-21  
**ทดสอบด้วย:** GroupDocs.Merger 23.12 for .NET  
**ผู้เขียน:** GroupDocs  

## แหล่งข้อมูล
- **เอกสาร:** [เอกสาร GroupDocs.Merger สำหรับ .NET](https://docs.groupdocs.com/merger/net/)  
- **อ้างอิง API:** [อ้างอิง API ของ GroupDocs.Merger](https://reference.groupdocs.com/merger/net/)  
- **ดาวน์โหลด:** [ดาวน์โหลด GroupDocs.Merger](https://releases.groupdocs.com/merger/net/)  
- **ซื้อ:** [ซื้อไลเซนส์ GroupDocs](https://purchase.groupdocs.com/buy)  
- **ทดลองใช้ฟรี:** [ทดลองใช้ฟรีของ GroupDocs](https://releases.groupdocs.com/merger/net/)  
- **ไลเซนส์ชั่วคราว:** [รับไลเซนส์ชั่วคราว](https://purchase.groupdocs.com/temporary-license)

```csharp
string filePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pptx"); // Presentation file path
string embeddedFilePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pdf"); // PDF to embed as OLE object
string outputDirectoryPath = "YOUR_OUTPUT_DIRECTORY"; // Output directory for modified presentation
string filePathOut = Path.Combine(outputDirectoryPath, "ModifiedPresentation.pptx"); // Output file path
```

```csharp
int pageNumber = 2; // Slide number to add OLE object
OlePresentationOptions oleSlidesOptions = new OlePresentationOptions(embeddedFilePath, pageNumber)
{
    X = 10, // X-coordinate for positioning the embedded object on the slide
    Y = 10  // Y-coordinate for positioning the embedded object on the slide
};
```

```csharp
using (Merger merger = new Merger(filePath)) // Initialize with presentation file path
{
    merger.ImportDocument(oleSlidesOptions); // Embed PDF as OLE using specified options
    merger.Save(filePathOut); // Save the modified presentation to output directory
}
```

## บทแนะนำที่เกี่ยวข้อง

- [ฝัง PDF ใน Word ด้วย GroupDocs.Merger สำหรับ .NET: คู่มือขั้นตอนต่อขั้นตอน](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [โหลด PDF จาก URL ใน .NET ด้วย GroupDocs.Merger: คู่มือครบวงจร](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)
- [วิธีดึงข้อมูลเอกสารด้วย GroupDocs.Merger สำหรับ .NET: คู่มือครบวงจร](/merger/net/document-information/retrieve-document-info-groupdocs-merger-dotnet/)