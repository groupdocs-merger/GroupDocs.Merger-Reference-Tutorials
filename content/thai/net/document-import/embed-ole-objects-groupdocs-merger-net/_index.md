---
date: '2026-09-21'
description: เรียนรู้วิธีฝัง PDF ในสเปรดชีต Excel ด้วย GroupDocs.Merger for .NET เพื่อเพิ่มการนำเสนอข้อมูลและฟังก์ชันการทำงาน
keywords:
- embed pdf in excel
- how to embed ole
- add ole object excel
- add ole to excel
lastmod: '2026-09-21'
og_description: เรียนรู้วิธีฝัง PDF ใน Excel ด้วย GroupDocs.Merger for .NET ปฏิบัติตามคำแนะนำทีละขั้นตอน
  ดูคำตอบอย่างรวดเร็ว และหลีกเลี่ยงข้อผิดพลาดทั่วไป
og_image_alt: Developer guide showing PDF embedded in an Excel spreadsheet via GroupDocs.Merger
  for .NET
og_title: วิธีฝัง PDF ใน Excel ด้วย GroupDocs.Merger for .NET
schemas:
- author: GroupDocs
  dateModified: '2026-09-21'
  description: Learn how to embed PDF in Excel spreadsheets with GroupDocs.Merger
    for .NET, enhancing data presentation and functionality.
  headline: How to embed PDF in Excel using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to embed PDF in Excel spreadsheets with GroupDocs.Merger
    for .NET, enhancing data presentation and functionality.
  name: How to embed PDF in Excel using GroupDocs.Merger for .NET
  steps:
  - name: '**Free trial** – test the library without cost.'
    text: '**Free trial** – test the library without cost.'
  - name: '**Temporary license** – request a temporary license on the [temporary‑license
      page](https://purchase.groupdocs.com/temporary-license/).'
    text: '**Temporary license** – request a temporary license on the [temporary‑license
      page](https://purchase.groupdocs.com/temporary-license/).'
  - name: '**Purchase** – consider purchasing a license on the [GroupDocs purchase
      page](https://purchase.groupdocs.com/buy).'
    text: '**Purchase** – consider purchasing a license on the [GroupDocs purchase
      page](https://purchase.groupdocs.com/buy).'
  - name: '**Financial reports** – attach audited statements directly beside summary
      tables.'
    text: '**Financial reports** – attach audited statements directly beside summary
      tables.'
  - name: '**Project documentation** – keep design specs, risk analyses, or contracts
      within a master tracker.'
    text: '**Project documentation** – keep design specs, risk analyses, or contracts
      within a master tracker.'
  - name: '**Training dashboards** – embed user manuals or policy PDFs for quick reference
      by staff.'
    text: '**Training dashboards** – embed user manuals or policy PDFs for quick reference
      by staff.'
  type: HowTo
- questions:
  - answer: An OLE (Object Linking and Embedding) object stores another file (PDF,
      Word, image, etc.) inside a host document, allowing in‑place editing or opening.
    question: What is an OLE object?
  - answer: Yes—GroupDocs.Merger also supports Word, PowerPoint, and Visio files.
    question: Can I embed OLE objects in other Office formats?
  - answer: Provide the password when creating the `OleSpreadsheetOptions` instance;
      the library will decrypt the file automatically.
    question: How do I handle password‑protected PDFs?
  - answer: Technically no hard limit, but files larger than 10 MB may noticeably
      increase workbook load time.
    question: Is there a size limitation for embedded PDFs?
  - answer: Visit the official [GroupDocs Documentation](https://docs.groupdocs.com/merger/net/)
      for additional code samples and API references.
    question: Where can I find more examples?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- .NET Excel integration
title: วิธีฝัง PDF ใน Excel ด้วย GroupDocs.Merger for .NET
type: docs
url: /th/net/document-import/embed-ole-objects-groupdocs-merger-net/
weight: 1
---

# วิธีฝัง PDF ใน Excel ด้วย GroupDocs.Merger สำหรับ .NET

## บทนำ

การฝัง PDF ใน Excel ช่วยให้คุณเก็บเอกสารสนับสนุน—เช่น สัญญา รายงาน หรือสเปคิฟิเคชัน—ไว้ตรงที่ข้อมูลอยู่ ด้วย **GroupDocs.Merger for .NET** คุณสามารถเพิ่มวัตถุ OLE ลงในเซลล์ได้เพียงไม่กี่บรรทัดของโค้ด ทำให้สเปรดชีตธรรมดากลายเป็นเวิร์กบุ๊กแบบโต้ตอบและมีทุกอย่างรวมอยู่ในตัวเอง บทแนะนำนี้จะพาคุณผ่านทุกสิ่งที่ต้องรู้ ตั้งแต่การติดตั้งจนถึงการแก้ไขปัญหา

**สิ่งที่คุณจะได้เรียนรู้**

- วิธีตั้งค่า GroupDocs.Merger for .NET ในโครงการ C#  
- ขั้นตอนที่แน่นอนในการฝัง PDF (หรือไฟล์ที่รองรับ OLE ใด ๆ) ลงในเซลล์ Excel  
- ตัวเลือกการกำหนดค่า เคล็ดลับประสิทธิภาพ และข้อผิดพลาดทั่วไป  

มาทำการยืนยันว่าคุณมีทุกอย่างพร้อมก่อนเริ่มกัน

## คำตอบอย่างรวดเร็ว
- **ฉันสามารถฝังไฟล์ประเภทใดก็ได้หรือไม่?** ใช่—รูปแบบใดก็ได้ที่รองรับเป็นวัตถุ OLE (PDF, Word, รูปภาพ ฯลฯ).  
- **ฉันต้องการไลเซนส์สำหรับการพัฒนาหรือไม่?** การทดลองใช้ฟรีสามารถใช้งานสำหรับการทดสอบ; จำเป็นต้องมีไลเซนส์ถาวรสำหรับการผลิต.  
- **เวอร์ชัน .NET ใดที่รองรับ?** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7+.  
- **ไฟล์ Excel จะเพิ่มขนาดอย่างมากหรือไม่?** เพิ่มเฉพาะขนาดของเอกสารที่ฝัง; ควรเก็บไฟล์ให้มีขนาดไม่เกินไม่กี่ MB เพื่อประสิทธิภาพที่ดีที่สุด.  
- **มีขีดจำกัดจำนวนวัตถุ OLE หรือไม่?** โดยปฏิบัติไม่มี, แต่เวิร์กบุ๊กขนาดใหญ่มากอาจส่งผลต่อเวลาโหลด.

## PDF ฝังใน Excel คืออะไร?

การฝัง PDF ใน Excel จะใส่ PDF ทั้งไฟล์เป็นวัตถุ OLE ที่สามารถเปิดได้โดยตรงจากสเปรดชีต ผู้ใช้คลิกไอคอนเพื่อดูเอกสารต้นฉบับโดยไม่ต้องออกจาก Excel วิธีนี้รักษาเลย์เอาต์เดิมไว้ ทำให้เข้าถึงได้อย่างรวดเร็ว และขจัดความจำเป็นในการจัดการไฟล์แยกต่างหาก PDF ที่ฝังทำงานเช่นวัตถุ OLE อื่น ๆ ให้ผู้ใช้ดับเบิลคลิกที่ไอคอนเพื่อเปิดโปรแกรมดู PDF ขณะอยู่ในสภาพแวดล้อมของ Excel

## ทำไมต้องฝังวัตถุ OLE ใน Excel?

GroupDocs.Merger รองรับ **รูปแบบการนำเข้าและส่งออกกว่า 120 ประเภท** และสามารถฝังวัตถุได้โดยไม่ต้องโหลดไฟล์ทั้งหมดเข้าสู่หน่วยความจำ ทำให้การประมวลผล PDF หลายร้อยหน้าเป็นไปอย่างรวดเร็ว สิ่งนี้ลดความจำเป็นในการมีคลังไฟล์แยกต่างหากและทำให้ข้อมูลที่เกี่ยวข้องอยู่รวมกัน นอกจากนี้ยังทำให้การควบคุมเวอร์ชันง่ายขึ้นและรับประกันว่าเอกสารที่เกี่ยวข้องทั้งหมดจะเดินทางพร้อมกับเวิร์กบุ๊ก เพิ่มการทำงานร่วมกันระหว่างทีม

## ข้อกำหนดเบื้องต้น

- **GroupDocs.Merger for .NET** (แพ็กเกจ NuGet ล่าสุด)  
- **.NET Framework** 4.5+ **หรือ** **.NET Core/5+/6+**  
- Visual Studio 2022 หรือใหม่กว่า  
- ความรู้พื้นฐานของ C# และความคุ้นเคยกับการทำงานไฟล์ I/O  

## การตั้งค่า GroupDocs.Merger สำหรับ .NET

### การติดตั้ง

เพิ่มแพ็กเกจโดยใช้วิธีใดวิธีหนึ่งต่อไปนี้:

**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI**  
ค้นหา “GroupDocs.Merger” และติดตั้งเวอร์ชันล่าสุด.

### การรับไลเซนส์

1. **Free trial** – ทดสอบไลบรารีโดยไม่มีค่าใช้จ่าย.  
2. **Temporary license** – ขอรับไลเซนส์ชั่วคราวที่หน้า [temporary‑license page](https://purchase.groupdocs.com/temporary-license/).  
3. **Purchase** – พิจารณาซื้อไลเซนส์ที่หน้า [GroupDocs purchase page](https://purchase.groupdocs.com/buy).

### การเริ่มต้นพื้นฐาน

`Merger` เป็นจุดเริ่มต้นสำหรับการดำเนินการทั้งหมด.  
```csharp
using (Merger merger = new Merger("path_to_your_spreadsheet.xlsx"))
{
    // Your code to work with the document
}
```  

## วิธีฝังวัตถุ OLE ใน Excel?

โหลดเวิร์กบุ๊กต้นฉบับของคุณ กำหนดค่าตัวเลือก OLE แล้วให้ `Merger` แทรกวัตถุ ส่วนต่อไปนี้จะให้กระบวนการทำงานที่กระชับและพร้อมใช้งาน

### ภาพรวมของฟีเจอร์
การฝังวัตถุ OLE ช่วยให้คุณเก็บ PDF ฉบับเต็มไว้ในเซลล์หนึ่ง คงรูปแบบเดิมและทำให้เข้าถึงด้วยคลิกเดียวจาก Excel

### การดำเนินการแบบขั้นตอนต่อขั้นตอน

#### 1. ตั้งค่าที่อยู่ไฟล์และหมายเลขหน้า
ระบุสเปรดชีต, ไฟล์ที่ต้องการฝัง, และที่อยู่เซลล์เป้าหมาย.  
```csharp
string filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
string embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_PDF";
int pageNumber = 2; // The specific page to embed

// Output path for the modified spreadsheet
string filePathOut = Path.Combine("YOUR_OUTPUT_DIRECTORY", "OUT_SAMPLE_NAME.xlsx");
```  

#### 2. กำหนดค่า OleSpreadsheetOptions
`OleSpreadsheetOptions` กำหนดตำแหน่งที่วัตถุ OLE จะถูกวางในแผ่นงานและลักษณะของไอคอนที่แสดง.  
```csharp
// Specify row and column indices for embedding
OleSpreadsheetOptions oleCellsOptions = new OleSpreadsheetOptions(embeddedFilePath, pageNumber)
{
    RowIndex = 2,
    ColumnIndex = 2
};
```  

#### 3. เริ่มต้น Merger และทำการฝัง
คลาส `Merger` จัดการการแทรกจริง หลังจากเรียกใช้ เวิร์กบุ๊กจะมีไอคอน OLE อยู่.  
```csharp
using (Merger merger = new Merger(filePath))
{
    merger.ImportDocument(oleCellsOptions); // Import the specified document as an OLE object into the spreadsheet
    merger.Save(filePathOut); // Save the modified document
}
```  

### เคล็ดลับการแก้ไขปัญหาทั่วไป
- ตรวจสอบให้แน่ใจว่าที่อยู่ไฟล์ทั้งหมดเป็นแบบ absolute หรือแก้ไขอย่างถูกต้องเมื่อสัมพันธ์กับไฟล์ปฏิบัติการ.  
- ตรวจสอบว่าหมายเลขหน้าที่ระบุมีอยู่ใน PDF ต้นฉบับ; หากไม่เช่นนั้นจะเกิดข้อยกเว้น.  
- หากวัตถุที่ฝังไม่แสดง ให้ยืนยันว่าเวอร์ชัน Excel เป้าหมายรองรับ OLE (ส่วนใหญ่รุ่นใหม่รองรับ).

## การประยุกต์ใช้งานจริง

การฝัง PDF ใน Excel มีประโยชน์สำหรับ:

1. **Financial reports** – แนบงบการเงินที่ตรวจสอบแล้วโดยตรงข้างตารางสรุป.  
2. **Project documentation** – เก็บสเปคการออกแบบ การวิเคราะห์ความเสี่ยง หรือสัญญาไว้ในตัวติดตามหลัก.  
3. **Training dashboards** – ฝังคู่มือผู้ใช้หรือ PDF นโยบายเพื่ออ้างอิงอย่างรวดเร็วโดยพนักงาน.

## ข้อควรพิจารณาด้านประสิทธิภาพ

- **File size** – เก็บ PDF ที่ฝังให้มีขนาดไม่เกิน 5 MB เพื่อหลีกเลี่ยงการทำให้เวิร์กบุ๊กบวม.  
- **Memory usage** – `GroupDocs.Merger` สตรีมข้อมูล ทำให้การใช้หน่วยความจำน้อยแม้ไฟล์ต้นฉบับใหญ่.  
- **Dispose objects** – ควรเรียก `Dispose()` บนอินสแตนซ์ของ `Merger` เสมอเพื่อปล่อยตัวจัดการไฟล์โดยเร็ว.

## คำถามที่พบบ่อย

**Q: OLE object คืออะไร?**  
A: OLE (Object Linking and Embedding) คือวัตถุที่เก็บไฟล์อื่น (PDF, Word, รูปภาพ ฯลฯ) ไว้ในเอกสารโฮสต์ ทำให้สามารถแก้ไขหรือเปิดได้ในที่เดียว  

**Q: ฉันสามารถฝังวัตถุ OLE ในรูปแบบ Office อื่นได้หรือไม่?**  
A: ใช่—GroupDocs.Merger ยังรองรับไฟล์ Word, PowerPoint, และ Visio ด้วย.  

**Q: ฉันจะจัดการกับ PDF ที่มีการป้องกันด้วยรหัสผ่านอย่างไร?**  
A: ให้รหัสผ่านเมื่อสร้างอินสแตนซ์ `OleSpreadsheetOptions`; ไลบรารีจะถอดรหัสไฟล์โดยอัตโนมัติ.  

**Q: มีขีดจำกัดขนาดสำหรับ PDF ที่ฝังหรือไม่?**  
A: โดยเทคนิคไม่มีขีดจำกัดที่แน่นอน แต่ไฟล์ที่ใหญ่กว่า 10 MB อาจทำให้เวลาโหลดเวิร์กบุ๊กเพิ่มขึ้นอย่างเห็นได้ชัด.  

**Q: ฉันจะหา ตัวอย่างเพิ่มเติมได้จากที่ไหน?**  
A: เยี่ยมชม [GroupDocs Documentation](https://docs.groupdocs.com/merger/net/) อย่างเป็นทางการเพื่อดูตัวอย่างโค้ดและอ้างอิง API เพิ่มเติม.  

## แหล่งข้อมูลเพิ่มเติม
- **เอกสาร**: [เอกสาร GroupDocs.Merger .NET](https://docs.groupdocs.com/merger/net/)  
- **อ้างอิง API**: [อ้างอิง API ของ GroupDocs](https://reference.groupdocs.com/merger/net/)  
- **ดาวน์โหลด**: [การเผยแพร่ GroupDocs](https://releases.groupdocs.com/merger/net/)  
- **การซื้อไลเซนส์**: [ซื้อไลเซนส์ GroupDocs](https://purchase.groupdocs.com/buy)  
- **ทดลองใช้ฟรี**: [ลองใช้ GroupDocs ฟรี](https://releases.groupdocs.com/merger/net/)  
- **ไลเซนส์ชั่วคราว**: [ขอไลเซนส์ชั่วคราว](https://purchase.groupdocs.com/temporary-license/)  
- **ฟอรั่มสนับสนุน**: [ฟอรั่มสนับสนุน GroupDocs](https://forum.groupdocs.com/c/merger)  

---

**อัปเดตล่าสุด:** 2026-09-21  
**ทดสอบด้วย:** GroupDocs.Merger 23.12 for .NET  
**ผู้เขียน:** GroupDocs

## บทแนะนำที่เกี่ยวข้อง

- [ฝัง PDF เป็น OLE ใน PowerPoint ด้วย GroupDocs.Merger สำหรับ .NET: คู่มือขั้นตอนต่อขั้นตอน](/merger/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/)  
- [ฝัง PDF ใน Word ด้วย GroupDocs.Merger สำหรับ .NET: คู่มือขั้นตอนต่อขั้นตอน](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)  
- [โหลด PDF จาก URL ใน .NET ด้วย GroupDocs.Merger: คู่มือเชิงลึก](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)  


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}