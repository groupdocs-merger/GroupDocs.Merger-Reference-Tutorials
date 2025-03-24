---
title: การรวมไฟล์ SVGZ
linktitle: การรวมไฟล์ SVGZ
second_title: GroupDocs.Merger .NET API
description: เรียนรู้วิธีผสานไฟล์ SVGZ โดยใช้ GroupDocs.Merger สำหรับ .NET ด้วยบทช่วยสอนทีละขั้นตอนนี้ เพิ่มทักษะการจัดการเอกสารของคุณ
weight: 14
url: /th/net/image-merging/merging-svgz-files/
---

# การรวมไฟล์ SVGZ

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีการผสานไฟล์ SVGZ (Scalable Vector Graphics) โดยใช้ GroupDocs.Merger สำหรับ .NET GroupDocs.Merger เป็น API การจัดการเอกสารอันทรงพลังที่ช่วยให้นักพัฒนาสามารถดำเนินการต่างๆ บนเอกสารรูปแบบต่างๆ รวมถึงการผสาน การแยก และการจัดเรียงหน้าใหม่
## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- Visual Studio: ติดตั้ง Visual Studio IDE บนระบบของคุณ
-  GroupDocs.Merger สำหรับ .NET: ดาวน์โหลดและรวมไลบรารี GroupDocs.Merger ในโครงการของคุณ คุณสามารถค้นหาการดาวน์โหลด[ที่นี่](https://releases.groupdocs.com/merger/net/).
- ความเข้าใจพื้นฐานของ C#: ความคุ้นเคยกับภาษาการเขียนโปรแกรม C#

## นำเข้าเนมสเปซ
ขั้นแรก ให้รวมเนมสเปซที่จำเป็นสำหรับการเข้าถึงฟังก์ชัน GroupDocs.Merger:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```

ตอนนี้ เรามาแจกแจงขั้นตอนการรวมไฟล์ SVGZ โดยใช้ GroupDocs.Merger ให้เป็นขั้นตอนง่ายๆ:
## ขั้นตอนที่ 1: กำหนดไดเรกทอรีผลลัพธ์และไฟล์
เริ่มต้นด้วยการระบุไดเร็กทอรีที่จะบันทึกไฟล์ที่ผสาน:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.svgz");
```
 แทนที่`"Your Output Directory"` ด้วยเส้นทางที่ต้องการในระบบของคุณ
## ขั้นตอนที่ 2: โหลดไฟล์ SVGZ ต้นฉบับ
ใช้ GroupDocs.Merger เพื่อโหลดไฟล์ SVGZ ต้นฉบับ:
```csharp
using (var merger = new Merger("Your Sample File"))
{
    // กำหนดตัวเลือกการรวมรูปภาพด้วยโหมดการรวมแนวตั้ง
    var joinOptions = new ImageJoinOptions(ImageJoinMode.Vertical);
    // เพิ่มไฟล์ SVGZ อื่นเพื่อรวม
    merger.Join("Your Sample File", joinOptions);
    // รวมไฟล์ SVGZ และบันทึกผลลัพธ์
    merger.Save(outputFile);
}
```
 แทนที่`"Your Sample File"` พร้อมเส้นทางไปยังไฟล์ SVGZ ของคุณ
## ขั้นตอนที่ 3: ดำเนินการดำเนินการผสาน
ดำเนินการขั้นตอนการรวมและบันทึกไฟล์ SVGZ ที่ผสาน:
```csharp
Console.WriteLine("\nSVGZ files merge completed successfully. \nCheck output in {0}", outputFolder);
```
ข้อมูลโค้ดนี้จะรวมไฟล์ SVGZ ในแนวตั้ง และไฟล์ที่ผสานจะถูกบันทึกในไดเร็กทอรีเอาต์พุตที่ระบุ

## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีผสานไฟล์ SVGZ โดยใช้ GroupDocs.Merger สำหรับ .NET ด้วยการทำตามขั้นตอนเหล่านี้ คุณสามารถรวมความสามารถในการรวมเอกสารเข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### GroupDocs.Merger สามารถจัดการไฟล์รูปแบบอื่นนอกเหนือจาก SVGZ ได้หรือไม่
ใช่ GroupDocs.Merger รองรับรูปแบบเอกสารที่หลากหลาย รวมถึง PDF, Word, Excel, PowerPoint และอื่นๆ
### ฉันจะหาเอกสารโดยละเอียดสำหรับ GroupDocs.Merger ได้ที่ไหน
 เยี่ยมชม[เอกสารประกอบ](https://tutorials.groupdocs.com/merger/net/) สำหรับข้อมูลที่ครอบคลุมและตัวอย่างการใช้งาน
### GroupDocs.Merger มีรุ่นทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถเข้าถึงการทดลองใช้ฟรีได้[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนสำหรับ GroupDocs.Merger ได้อย่างไร
 เข้าร่วม[ฟอรัม GroupDocs](https://forum.groupdocs.com/c/merger/32) เพื่อขอความช่วยเหลือและโต้ตอบกับผู้ใช้รายอื่น
### ฉันจะซื้อใบอนุญาตสำหรับ GroupDocs.Merger ได้ที่ไหน
 ซื้อใบอนุญาต[ที่นี่](https://purchase.groupdocs.com/buy) หรือได้รับใบอนุญาตชั่วคราว[ที่นี่](https://purchase.groupdocs.com/temporary-license/).