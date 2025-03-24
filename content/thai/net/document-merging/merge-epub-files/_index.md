---
title: รวมไฟล์ EPUB
linktitle: รวมไฟล์ EPUB
second_title: GroupDocs.Merger .NET API
description: เรียนรู้วิธีผสานไฟล์ EPUB โดยใช้โปรแกรม GroupDocs.Merger สำหรับ .NET ปฏิบัติตามบทช่วยสอนทีละขั้นตอนของเรา
weight: 17
url: /th/net/document-merging/merge-epub-files/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีการรวมไฟล์ EPUB โดยใช้ GroupDocs.Merger สำหรับ .NET GroupDocs.Merger for .NET เป็นไลบรารีที่มีประสิทธิภาพซึ่งช่วยให้นักพัฒนาสามารถจัดการและผสานรูปแบบเอกสารต่างๆ ภายในแอปพลิเคชัน .NET ของตนได้อย่างราบรื่น โดยเฉพาะอย่างยิ่ง เราจะมุ่งเน้นไปที่การรวมไฟล์ EPUB ทีละขั้นตอนโดยใช้ไลบรารีนี้
## ข้อกำหนดเบื้องต้น
ก่อนดำเนินการต่อ ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นต่อไปนี้:
1. สภาพแวดล้อมการพัฒนา: มี Visual Studio หรือสภาพแวดล้อมการพัฒนา .NET อื่นติดตั้งอยู่
2.  GroupDocs.Merger สำหรับ .NET: ดาวน์โหลดและติดตั้ง GroupDocs.Merger สำหรับไลบรารี .NET คุณสามารถรับได้จาก[หน้าดาวน์โหลด](https://releases.groupdocs.com/merger/net/).
3. ไฟล์ EPUB: เตรียมไฟล์ EPUB ที่คุณต้องการรวมสำหรับการทดสอบ

## นำเข้าเนมสเปซ
ขั้นแรก นำเข้าเนมสเปซที่จำเป็นเพื่อทำงานกับ GroupDocs.Merger ในโปรเจ็กต์ .NET ของคุณ:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## ขั้นตอนที่ 1: กำหนดไดเรกทอรีผลลัพธ์และชื่อไฟล์
ตั้งค่าไดเร็กทอรีเอาต์พุตที่จะบันทึกไฟล์ EPUB ที่รวมเข้าด้วยกัน
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.epub");
```
 แทนที่`"Your Output Directory"` ด้วยเส้นทางไดเร็กทอรีเอาต์พุตที่คุณต้องการ
## ขั้นตอนที่ 2: โหลดไฟล์ EPUB ต้นฉบับ
 ใช้`Merger` จากไลบรารี GroupDocs.Merger เพื่อโหลดไฟล์ EPUB ต้นทางที่คุณต้องการผสาน
```csharp
using (var merger = new GroupDocs.Merger.Merger("Path_To_First_EPUB"))
{
    merger.Join("Path_To_Second_EPUB");
    // เพิ่มไฟล์ EPUB เพิ่มเติมหากจำเป็น
    // Merger.Join("Path_To_Third_EPUB");
    
    // รวมไฟล์ EPUB และบันทึกผลลัพธ์
    merger.Save(outputFile);
}
```
 แทนที่`"Path_To_First_EPUB"` และ`"Path_To_Second_EPUB"` พร้อมเส้นทางไปยังไฟล์ EPUB ของคุณ คุณสามารถเพิ่มมากขึ้น`merger.Join()` เรียกร้องให้รวมไฟล์ EPUB เพิ่มเติมในการรวม
## ขั้นตอนที่ 3: บันทึกไฟล์ EPUB ที่ผสาน
ดำเนินการดำเนินการผสานและบันทึกไฟล์ EPUB ที่ผสานเข้าด้วยกัน
```csharp
Console.WriteLine("\nEPUB files merge completed successfully. \nCheck output in {0}", outputFolder);
```
ข้อมูลโค้ดนี้ดำเนินการผสานและแสดงข้อความแสดงความสำเร็จพร้อมกับไดเร็กทอรีเอาต์พุต

## บทสรุป
ในบทช่วยสอนนี้ เราได้สาธิตวิธีการรวมไฟล์ EPUB โดยใช้ GroupDocs.Merger สำหรับ .NET ด้วยการทำตามขั้นตอนเหล่านี้ คุณสามารถรวมความสามารถในการรวมเอกสารเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### ถาม: GroupDocs.Merger สามารถรวมรูปแบบเอกสารอื่นๆ ได้หรือไม่
ใช่ GroupDocs.Merger รองรับการรวมรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, DOCX, XLSX, PPTX และอื่นๆ
### ถาม: GroupDocs.Merger สำหรับ .NET ใช้งานได้ฟรีหรือไม่
 GroupDocs.Merger for .NET เป็นไลบรารีเชิงพาณิชย์ แต่คุณสามารถสำรวจฟีเจอร์ต่างๆ ของมันได้ด้วยการทดลองใช้ฟรี เยี่ยม[ที่นี่](https://releases.groupdocs.com/) สำหรับรุ่นทดลอง
### ถาม: ฉันจะขอความช่วยเหลือและการสนับสนุนเพิ่มเติมสำหรับ GroupDocs.Merger ได้จากที่ไหน
 คุณสามารถค้นหาเอกสารและการสนับสนุนที่ครอบคลุมได้ที่[ฟอรัม GroupDocs.Merger](https://forum.groupdocs.com/c/merger/32).
### ถาม: ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Merger ได้อย่างไร
 สามารถรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Merger ได้[ที่นี่](https://purchase.groupdocs.com/temporary-license/).
### ถาม: ฉันจะซื้อ GroupDocs.Merger สำหรับ .NET ได้ที่ไหน
 คุณสามารถซื้อใบอนุญาตสำหรับ GroupDocs.Merger สำหรับ .NET[ที่นี่](https://purchase.groupdocs.com/buy).