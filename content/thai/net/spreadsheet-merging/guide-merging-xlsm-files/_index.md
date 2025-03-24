---
title: คำแนะนำในการรวมไฟล์ XLSM
linktitle: คำแนะนำในการรวมไฟล์ XLSM
second_title: GroupDocs.Merger .NET API
description: รวมไฟล์ XLSM เข้ากับ GroupDocs.Merger for .NET ได้อย่างราบรื่น รวมสมุดงาน Excel อย่างมีประสิทธิภาพโดยทางโปรแกรม เพิ่มความสามารถในการจัดการเอกสารของคุณ
weight: 13
url: /th/net/spreadsheet-merging/guide-merging-xlsm-files/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีการผสานไฟล์ XLSM (สมุดงานที่เปิดใช้งานมาโครของ Excel) GroupDocs.Merger เป็นไลบรารีอันทรงพลังที่ช่วยให้นักพัฒนาสามารถจัดการรูปแบบเอกสาร รวมถึงการผสาน การแยก และการแก้ไขไฟล์โดยทางโปรแกรม
## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
-  GroupDocs.Merger สำหรับ .NET: ดาวน์โหลดและติดตั้งไลบรารีจาก[ที่นี่](https://releases.groupdocs.com/merger/net/).
- สภาพแวดล้อมการพัฒนา: ตั้งค่า Visual Studio หรือสภาพแวดล้อมการพัฒนา .NET ที่เข้ากันได้
- ไฟล์ XLSM: เตรียมไฟล์ XLSM ที่คุณต้องการรวม

## นำเข้าเนมสเปซ
ขั้นแรก ให้รวมเนมสเปซที่จำเป็นในโครงการ .NET ของคุณ:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## ขั้นตอนที่ 1: กำหนดโฟลเดอร์เอาท์พุตและชื่อไฟล์
เริ่มต้นด้วยการกำหนดโฟลเดอร์เอาต์พุตและชื่อของไฟล์ XLSM ที่ผสาน:
```csharp
string outputFolder = "YourOutputDirectory";
string outputFile = Path.Combine(outputFolder, "merged.xlsm");
```
## ขั้นตอนที่ 2: โหลดและรวมไฟล์ XLSM
จากนั้น โหลดไฟล์ XLSM ต้นทางและรวมเป็นไฟล์เดียว:
```csharp
// โหลดไฟล์ XLSM ต้นทาง
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    // เพิ่มไฟล์ XLSM อื่นเพื่อรวม
    merger.Join("Your Sample File");
    // รวมไฟล์ XLSM และบันทึกผลลัพธ์
    merger.Save(outputFile);
}
```
## ขั้นตอนที่ 3: ตรวจสอบการผสานเสร็จสมบูรณ์
สุดท้าย แจ้งให้ผู้ใช้ทราบเกี่ยวกับความสำเร็จในการผสานและแสดงเส้นทางเอาต์พุต:
```csharp
Console.WriteLine("\nXLSM files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## บทสรุป
คุณได้เรียนรู้วิธีรวมไฟล์ XLSM โดยทางโปรแกรมแล้ว ไลบรารีนี้ทำให้งานจัดการเอกสารง่ายขึ้น ช่วยให้สามารถรวมไฟล์ภายในแอปพลิเคชัน .NET ของคุณได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### GroupDocs.Merger สามารถจัดการไฟล์ XLSM ขนาดใหญ่ได้หรือไม่
ใช่ GroupDocs.Merger จัดการไฟล์ XLSM ขนาดใหญ่ได้อย่างมีประสิทธิภาพโดยไม่มีปัญหาด้านประสิทธิภาพ
### GroupDocs.Merger รองรับไฟล์รูปแบบอื่นนอกเหนือจาก XLSM หรือไม่
ใช่ GroupDocs.Merger รองรับรูปแบบเอกสารที่หลากหลาย เช่น DOCX, PDF, PPTX และอื่นๆ
### GroupDocs.Merger เข้ากันได้กับแอปพลิเคชัน .NET Core หรือไม่
ใช่ GroupDocs.Merger เข้ากันได้กับทั้งสภาพแวดล้อม .NET Framework และ .NET Core
### ฉันสามารถรวมไฟล์ XLSM ที่เข้ารหัสโดยใช้ GroupDocs.Merger ได้หรือไม่
ใช่ GroupDocs.Merger รองรับการรวมไฟล์ XLSM ที่เข้ารหัสเข้ากับข้อมูลรับรองที่ถูกต้อง
### GroupDocs.Merger มีความสามารถในการประมวลผลเป็นชุดหรือไม่
ใช่ GroupDocs.Merger อนุญาตให้มีการประมวลผลเป็นชุดสำหรับการรวมไฟล์ XLSM หลายไฟล์พร้อมกัน