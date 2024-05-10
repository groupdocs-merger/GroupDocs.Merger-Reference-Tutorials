---
title: การรวมไฟล์ XLTM
linktitle: การรวมไฟล์ XLTM
second_title: GroupDocs.Merger .NET API
description: เรียนรู้วิธีผสานไฟล์ XLTM โดยทางโปรแกรม คำแนะนำทีละขั้นตอนพร้อมตัวอย่างโค้ด
type: docs
weight: 16
url: /th/net/spreadsheet-merging/merging-xltm-files/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีการรวมไฟล์ XLTM (เทมเพลตที่เปิดใช้งานมาโคร Excel) GroupDocs.Merger for .NET เป็นไลบรารีที่มีประสิทธิภาพซึ่งช่วยให้นักพัฒนาสามารถจัดการและผสานรูปแบบเอกสารต่างๆ โดยทางโปรแกรม คู่มือนี้จะแนะนำคุณตลอดกระบวนการรวมไฟล์ XLTM ทีละขั้นตอนโดยใช้ C#
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
- ติดตั้ง Visual Studio บนระบบของคุณแล้ว
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C#
-  ติดตั้ง GroupDocs.Merger สำหรับไลบรารี .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/merger/net/).
- เข้าถึงไฟล์ XLTM ที่คุณต้องการผสาน

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```

ตอนนี้ เรามาดำดิ่งสู่การรวมไฟล์ XLTM กัน
## ขั้นตอนที่ 1: เริ่มต้นไดเร็กทอรีเอาท์พุต
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.xltm");
```
 แทนที่`"Your Output Directory"` ด้วยเส้นทางที่คุณต้องการบันทึกไฟล์ XLTM ที่ผสาน
## ขั้นตอนที่ 2: รวมไฟล์ XLTM
```csharp
// โหลดไฟล์ XLTM ต้นทาง
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    // เพิ่มไฟล์ XLTM อื่นเพื่อรวม
    merger.Join("Your Sample File");
    //รวมไฟล์ XLTM และบันทึกผลลัพธ์
    merger.Save(outputFile);
}
```
ในข้อมูลโค้ดนี้:
- "ไฟล์ตัวอย่างของคุณ" และ "ไฟล์ตัวอย่างของคุณ" แสดงถึงเส้นทางไปยังไฟล์ XLTM อินพุตของคุณ ตรวจสอบให้แน่ใจว่าได้แทนที่สิ่งเหล่านี้ด้วยเส้นทางไฟล์จริง
## ขั้นตอนที่ 3: แสดงตำแหน่งเอาต์พุต
```csharp
Console.WriteLine("\nXLTM files merge completed successfully. \nCheck output in {0}", outputFolder);
```
รหัสนี้จะแสดงข้อความที่ระบุว่าการดำเนินการผสานเสร็จสมบูรณ์พร้อมกับเส้นทางไดเร็กทอรีเอาต์พุต

## บทสรุป
เมื่อทำตามบทช่วยสอนนี้ คุณได้เรียนรู้วิธีรวมไฟล์ XLTM แล้ว ไลบรารีนี้มีความสามารถที่ครอบคลุมสำหรับการจัดการเอกสาร ทำให้นักพัฒนามีชุดเครื่องมือที่มีประสิทธิภาพสำหรับการจัดการงานที่เกี่ยวข้องกับเอกสารโดยทางโปรแกรม

## คำถามที่พบบ่อย
### GroupDocs.Merger สามารถรวมรูปแบบเอกสารอื่นนอกเหนือจาก XLTM ได้หรือไม่
ใช่ GroupDocs.Merger รองรับการรวมรูปแบบเอกสารต่างๆ เช่น DOCX, XLSX, PPTX, PDF และอื่นๆ
### GroupDocs.Merger จำเป็นต้องมีใบอนุญาตสำหรับการใช้งานเชิงพาณิชย์หรือไม่
 ใช่ คุณจะต้องมีใบอนุญาตที่ถูกต้องเพื่อใช้ GroupDocs.Merger ในสภาพแวดล้อมเชิงพาณิชย์ คุณสามารถขอรับใบอนุญาตได้[ที่นี่](https://purchase.groupdocs.com/buy).
### GroupDocs.Merger มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถเข้าถึง GroupDocs.Merger รุ่นทดลองใช้ฟรีได้[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะหาเอกสารสำหรับ GroupDocs.Merger ได้ที่ไหน
คุณสามารถดูเอกสารประกอบฉบับสมบูรณ์สำหรับ GroupDocs.Merger[ที่นี่](https://reference.groupdocs.com/merger/net/).
### ฉันจะรับการสนับสนุนด้านเทคนิคสำหรับ GroupDocs.Merger ได้ที่ไหน
 หากต้องการความช่วยเหลือและการสนับสนุนด้านเทคนิค โปรดไปที่ฟอรัม GroupDocs.Merger[ที่นี่](https://forum.groupdocs.com/c/merger/32).