---
title: รวมไฟล์ DOC เข้ากับ GroupDocs.Merger สำหรับ .NET
linktitle: รวมไฟล์ DOC เข้ากับ GroupDocs.Merger สำหรับ .NET
second_title: GroupDocs.Merger .NET API
description: เรียนรู้วิธีผสานไฟล์ DOC โดยทางโปรแกรมโดยใช้ GroupDocs.Merger สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเราเพื่อรวมเอกสารหลายฉบับเป็นเอกสารเดียวได้อย่างราบรื่น
weight: 10
url: /th/net/document-merging/merge-doc-files/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีการรวมไฟล์ DOC โดยใช้ GroupDocs.Merger สำหรับ .NET GroupDocs.Merger for .NET เป็น API ที่ทรงพลังซึ่งช่วยให้นักพัฒนาสามารถรวม แยก และจัดการรูปแบบเอกสารต่างๆ โดยทางโปรแกรม ด้วยการใช้ประโยชน์จาก API นี้ คุณสามารถรวมไฟล์ DOC หลายไฟล์เป็นเอกสารเดียวได้อย่างราบรื่น เราจะให้คำแนะนำทีละขั้นตอนเพื่อแนะนำคุณตลอดกระบวนการรวมไฟล์ DOC โดยใช้ GroupDocs.Merger สำหรับ .NET
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าข้อกำหนดเบื้องต้นต่อไปนี้:
1. Visual Studio: ติดตั้ง Visual Studio บนเครื่องพัฒนาของคุณ
2.  GroupDocs.Merger สำหรับ .NET: รับไลบรารี GroupDocs.Merger สำหรับ .NET คุณสามารถดาวน์โหลดได้จาก[เว็บไซต์](https://releases.groupdocs.com/merger/net/).
3. ความรู้เกี่ยวกับ C#: ความเข้าใจพื้นฐานเกี่ยวกับภาษาการเขียนโปรแกรม C#
## นำเข้าเนมสเปซ
หากต้องการเริ่มทำงานกับ GroupDocs.Merger สำหรับ .NET ให้นำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## ขั้นตอนที่ 1: ตั้งค่าไดเรกทอรีผลลัพธ์
เริ่มต้นด้วยการระบุไดเร็กทอรีเอาต์พุตที่จะบันทึกไฟล์ DOC ที่ผสาน:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.doc");
```
 แทนที่`"Your Output Directory"` พร้อมเส้นทางไปยังโฟลเดอร์เอาต์พุตที่คุณต้องการ
## ขั้นตอนที่ 2: โหลดไฟล์ DOC ซอร์ส
จากนั้น โหลดไฟล์ DOC ต้นทางที่คุณต้องการผสานโดยใช้ GroupDocs.Merger:
```csharp
using (var merger = new Merger("Your Sample Document File"))
{
    // เพิ่มไฟล์ DOC อื่นเพื่อรวม
    merger.Join("Your Sample Document File 2");
    // รวมไฟล์ DOC และบันทึกผลลัพธ์
    merger.Save(outputFile);
}
```
ในข้อมูลโค้ดนี้:
- `"Your Sample Document File"` และ`"Your Sample Document File 2"` แสดงถึงเส้นทางไปยังไฟล์ DOC ที่คุณต้องการรวม
- `merger.Join(...)` ใช้เพื่อเพิ่มไฟล์ DOC อื่นในการดำเนินการผสาน
- `merger.Save(outputFile)` รวมไฟล์ DOC ที่โหลดและบันทึกเอกสารที่ผสานไปยังไฟล์เอาต์พุตที่ระบุ (`merged.doc`-
 ตรวจสอบให้แน่ใจว่าคุณเปลี่ยน`"Your Sample Document File"` และ`"Your Sample Document File 2"` พร้อมเส้นทางจริงไปยังไฟล์ DOC ของคุณ
## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงกระบวนการรวมไฟล์ DOC โดยใช้ GroupDocs.Merger สำหรับ .NET ด้วยการทำตามขั้นตอนที่อธิบายไว้ข้างต้น คุณสามารถรวมไฟล์ DOC หลายไฟล์ไว้ในเอกสารเดียวโดยทางโปรแกรมได้อย่างมีประสิทธิภาพ GroupDocs.Merger for .NET มอบวิธีที่ตรงไปตรงมาและมีประสิทธิภาพในการจัดการรูปแบบเอกสารภายในแอปพลิเคชัน .NET ของคุณ

## คำถามที่พบบ่อย
### GroupDocs.Merger for .NET สามารถจัดการรูปแบบเอกสารอื่นนอกเหนือจาก DOC ได้หรือไม่
ใช่ GroupDocs.Merger สำหรับ .NET รองรับการรวมรูปแบบเอกสารต่างๆ เช่น DOCX, PDF, XLSX, PPTX และอื่นๆ
### GroupDocs.Merger สำหรับ .NET เข้ากันได้กับ .NET Core หรือไม่
ใช่ GroupDocs.Merger สำหรับ .NET เข้ากันได้กับ .NET Core และ .NET Framework
### GroupDocs.Merger for .NET จำเป็นต้องมีใบอนุญาตสำหรับการใช้งานเชิงพาณิชย์หรือไม่
 ใช่ จำเป็นต้องมีใบอนุญาตที่ถูกต้องสำหรับการใช้งานเชิงพาณิชย์ คุณสามารถขอรับใบอนุญาตได้จาก[GroupDocs](https://purchase.groupdocs.com/buy).
### ฉันสามารถทดลองใช้ GroupDocs.Merger สำหรับ .NET ได้ฟรีหรือไม่
 ใช่ คุณสามารถสำรวจ GroupDocs.Merger สำหรับ .NET ได้พร้อมให้ทดลองใช้ฟรี[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนทางเทคนิคสำหรับ GroupDocs.Merger for .NET ได้ที่ไหน
 สำหรับความช่วยเหลือด้านเทคนิคและการสนับสนุนชุมชน โปรดไปที่[ฟอรัม GroupDocs](https://forum.groupdocs.com/c/merger/32).