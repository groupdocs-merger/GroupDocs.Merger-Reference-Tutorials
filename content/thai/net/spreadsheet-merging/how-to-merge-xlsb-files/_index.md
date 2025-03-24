---
title: วิธีรวมไฟล์ XLSB
linktitle: วิธีรวมไฟล์ XLSB
second_title: GroupDocs.Merger .NET API
description: เรียนรู้วิธีผสานไฟล์ XLSB คำแนะนำทีละขั้นตอนนี้ทำให้งานการจัดการเอกสารง่ายขึ้น
weight: 12
url: /th/net/spreadsheet-merging/how-to-merge-xlsb-files/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีการผสานไฟล์ XLSB (Excel Binary Workbook) GroupDocs.Merger for .NET เป็น API การจัดการเอกสารที่มีประสิทธิภาพซึ่งช่วยให้นักพัฒนาสามารถผสาน แยก และจัดการรูปแบบเอกสารต่างๆ ภายในแอปพลิเคชัน .NET ของตนได้อย่างราบรื่น โดยเฉพาะเราจะเน้นที่การรวมไฟล์ XLSB โดยใช้ไลบรารีอเนกประสงค์นี้
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเจาะลึกบทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าข้อกำหนดเบื้องต้นต่อไปนี้:
- ติดตั้ง Visual Studio บนระบบของคุณแล้ว
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C#
- ดาวน์โหลด GroupDocs.Merger สำหรับไลบรารี .NET และอ้างอิงในโครงการของคุณ
  

## นำเข้าเนมสเปซ
ก่อนที่คุณจะเริ่มเขียนโค้ด ให้นำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## ขั้นตอนที่ 1: ตั้งค่าไดเรกทอรีผลลัพธ์ของคุณ
```csharp
string outputFolder = "Your Output Directory";
```
## ขั้นตอนที่ 2: กำหนดเส้นทางไฟล์เอาต์พุต
```csharp
string outputFile = Path.Combine(outputFolder, "merged.xlsb");
```
## ขั้นตอนที่ 3: โหลดไฟล์ XLSB ต้นฉบับ
```csharp
// โหลดไฟล์ XLSB ต้นทาง
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    // เพิ่มไฟล์ XLSB อื่นเพื่อรวม
    merger.Join("Your Sample File");
    // รวมไฟล์ XLSB และบันทึกผลลัพธ์
    merger.Save(outputFile);
}
```
## ขั้นตอนที่ 4: แสดงข้อความเสร็จสิ้นการผสาน
```csharp
Console.WriteLine("\nXLSB files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## บทสรุป
เมื่อทำตามขั้นตอนเหล่านี้ คุณจะสามารถรวมไฟล์ XLSB ได้อย่างง่ายดาย API นี้ทำให้งานจัดการเอกสารง่ายขึ้น และนำเสนอการผสานรวมเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น

## คำถามที่พบบ่อย
### GroupDocs.Merger สามารถจัดการไฟล์รูปแบบอื่นนอกเหนือจาก XLSB ได้หรือไม่
ใช่ GroupDocs.Merger รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง DOCX, PDF, XLSX, PPTX และอื่นๆ
### ฉันจะหาเอกสารเพิ่มเติมสำหรับ GroupDocs.Merger ได้ที่ไหน
 เยี่ยมชม[เอกสารประกอบ](https://tutorials.groupdocs.com/merger/net/) สำหรับคำแนะนำการใช้งานโดยละเอียดและการอ้างอิง API
### GroupDocs.Merger มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถเข้าถึง[ทดลองฟรี](https://releases.groupdocs.com/)เพื่อสำรวจคุณสมบัติของ GroupDocs.Merger
### ฉันจะรับการสนับสนุนด้านเทคนิคสำหรับ GroupDocs.Merger ได้อย่างไร
 เข้าร่วม[ฟอรัม GroupDocs](https://forum.groupdocs.com/c/merger/32) เพื่อถามคำถามและโต้ตอบกับชุมชน
### ฉันจะซื้อใบอนุญาตสำหรับ GroupDocs.Merger ได้ที่ไหน
 คุณสามารถซื้อใบอนุญาตได้จาก[หน้าซื้อ](https://purchase.groupdocs.com/buy).