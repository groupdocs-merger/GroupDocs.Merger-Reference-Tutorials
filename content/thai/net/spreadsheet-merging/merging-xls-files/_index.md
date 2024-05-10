---
title: การรวมไฟล์ XLS
linktitle: การรวมไฟล์ XLS
second_title: GroupDocs.Merger .NET API
description: เรียนรู้วิธีผสานไฟล์ Excel ใน .NET โดยใช้ GroupDocs.Merger เพื่อการจัดการเอกสารที่ราบรื่น ปฏิบัติตามบทช่วยสอนทีละขั้นตอนของเรา
type: docs
weight: 11
url: /th/net/spreadsheet-merging/merging-xls-files/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีการรวมไฟล์ XLS (Excel) GroupDocs.Merger เป็น API การจัดการเอกสารอันทรงพลังที่ช่วยให้นักพัฒนาสามารถผสาน แยก จัดเรียงใหม่ และจัดการเอกสารได้อย่างง่ายดายภายในแอปพลิเคชัน .NET ของตน โดยเฉพาะอย่างยิ่ง เราจะมุ่งเน้นไปที่การรวมไฟล์ XLS ทีละขั้นตอนโดยใช้วิธีการที่ใช้งานง่ายของ GroupDocs.Merger
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณได้ตั้งค่าข้อกำหนดเบื้องต้นต่อไปนี้:
- Visual Studio: ติดตั้ง Visual Studio บนเครื่องของคุณ
-  GroupDocs.Merger สำหรับ .NET: ดาวน์โหลดและติดตั้ง GroupDocs.Merger สำหรับ .NET จาก[ที่นี่](https://releases.groupdocs.com/merger/net/).
- .NET Framework: ตรวจสอบให้แน่ใจว่าคุณได้ติดตั้ง .NET Framework แล้ว
- ตัวอย่างไฟล์ XLS: เตรียมไฟล์ XLS ที่คุณต้องการรวม

## นำเข้าเนมสเปซ
เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นสำหรับการใช้ GroupDocs.Merger ในโปรเจ็กต์ของคุณ:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## ขั้นตอนที่ 1: เริ่มต้นไดเร็กทอรีเอาท์พุต
ขั้นแรก ให้ระบุไดเร็กทอรีที่คุณต้องการบันทึกไฟล์ XLS ที่ผสาน:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.xls");
```
## ขั้นตอนที่ 2: โหลดและรวมไฟล์ XLS
ตอนนี้ มาโหลดและรวมไฟล์ XLS โดยใช้ GroupDocs.Merger:
```csharp
// โหลดไฟล์ XLS ต้นทาง
using (var merger = new Merger("Your Sample File"))
{
    // เพิ่มไฟล์ XLS อื่นเพื่อรวม
    merger.Join("Your Sample File");
    
    // รวมไฟล์ XLS และบันทึกผลลัพธ์
    merger.Save(outputFile);
}
```
## ขั้นตอนที่ 3: แสดงตำแหน่งเอาต์พุต
สุดท้าย ให้แสดงข้อความระบุความสมบูรณ์และตำแหน่งของไฟล์ XLS ที่ผสาน:
```csharp
Console.WriteLine("\nXLS files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีรวมไฟล์ XLS ด้วยการทำตามขั้นตอนที่ให้ไว้ คุณสามารถรวมไฟล์ Excel หลายไฟล์ทางโปรแกรมภายในแอปพลิเคชัน .NET ของคุณได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### GroupDocs.Merger สามารถใช้งานร่วมกับเอกสารรูปแบบอื่นได้หรือไม่
ใช่ GroupDocs.Merger รองรับรูปแบบเอกสารที่หลากหลาย เช่น PDF, DOCX, XLSX, PPTX และอื่นๆ
### ฉันสามารถแยกเอกสารโดยใช้ GroupDocs.Merger ได้หรือไม่
อย่างแน่นอน! GroupDocs.Merger ช่วยให้คุณสามารถแบ่งเอกสารตามความต้องการของคุณ
### ฉันจะหาแหล่งข้อมูลเพิ่มเติมและการสนับสนุนสำหรับ GroupDocs.Merger ได้ที่ไหน
คุณสามารถสำรวจเอกสารและถามคำถามได้ที่[ฟอรัม GroupDocs](https://forum.groupdocs.com/c/merger/32).
### GroupDocs.Merger มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถเริ่มต้นด้วย[ทดลองฟรี](https://releases.groupdocs.com/) เพื่อประเมินการทำงาน
### ฉันจะซื้อใบอนุญาตสำหรับ GroupDocs.Merger ได้อย่างไร
 เยี่ยมชม[หน้าซื้อ](https://purchase.groupdocs.com/buy) เพื่อรับใบอนุญาตที่เหมาะกับความต้องการของคุณ