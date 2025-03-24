---
title: รวมไฟล์ BMP
linktitle: รวมไฟล์ BMP
second_title: GroupDocs.Merger .NET API
description: เรียนรู้วิธีผสานไฟล์ BMP โดยใช้ GroupDocs.Merger สำหรับ .NET ด้วยบทช่วยสอนที่ครอบคลุมนี้ พัฒนาแอพพลิเคชั่น .NET ของคุณอย่างมีประสิทธิภาพ
weight: 10
url: /th/net/image-merging/merge-bmp-files/
---

# รวมไฟล์ BMP

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีการผสานไฟล์ BMP (บิตแมป) โดยใช้ GroupDocs.Merger สำหรับ .NET GroupDocs.Merger เป็น API อันทรงประสิทธิภาพที่ช่วยให้นักพัฒนาสามารถจัดการและผสานรูปแบบเอกสารต่างๆ โดยใช้โปรแกรมภายในแอปพลิเคชัน .NET ของตนได้ ในตอนท้ายของคู่มือนี้ คุณจะสามารถรวมไฟล์ BMP ทีละขั้นตอนได้อย่างมีประสิทธิภาพ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่ม ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- ติดตั้ง Visual Studio บนเครื่องของคุณแล้ว
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C#
-  GroupDocs.Merger สำหรับไลบรารี .NET คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/merger/net/)
- เข้าถึงไฟล์ BMP ที่คุณต้องการรวม
## นำเข้าเนมสเปซ
เริ่มต้นด้วยการนำเข้าเนมสเปซที่จำเป็นสำหรับการใช้ GroupDocs.Merger ในโปรเจ็กต์ C# ของคุณ:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
เรามาแจกแจงขั้นตอนการรวมไฟล์ BMP ออกเป็นขั้นตอนที่สามารถจัดการได้:
## ขั้นตอนที่ 1: ตั้งค่าไดเร็กทอรีเอาต์พุตและชื่อไฟล์
กำหนดไดเร็กทอรีเอาต์พุตและชื่อของไฟล์ BMP ที่ผสาน
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.bmp");
```
## ขั้นตอนที่ 2: โหลดไฟล์ BMP ซอร์ส
 ยกตัวอย่าง`Merger` วัตถุโดยระบุเส้นทางไปยังไฟล์ BMP ต้นทาง
```csharp
using (var merger = new Merger("Your Sample File"))
{
    // กำหนดตัวเลือกการรวมรูปภาพด้วยโหมดการรวมแนวตั้ง
    var joinOptions = new ImageJoinOptions(ImageJoinMode.Vertical);
    
    // เพิ่มไฟล์ BMP อื่นเพื่อรวม
    merger.Join("Your Sample File", joinOptions);
    
    // รวมไฟล์ BMP และบันทึกผลลัพธ์
    merger.Save(outputFile);
}
```
## ขั้นตอนที่ 3: ดำเนินการและตรวจสอบ
รันโค้ดเพื่อรวมไฟล์ BMP และตรวจสอบตำแหน่งเอาต์พุต
```csharp
Console.WriteLine("\nBMP files merge completed successfully. \nCheck output in {0}", outputFolder);
```
## บทสรุป
ในบทช่วยสอนนี้ เราได้เรียนรู้วิธีผสานไฟล์ BMP โดยใช้ GroupDocs.Merger สำหรับ .NET ด้วยการทำตามขั้นตอนที่อธิบายไว้ข้างต้น คุณสามารถรวมฟังก์ชันการรวม BMP เข้ากับแอปพลิเคชัน .NET ของคุณได้อย่างราบรื่น

## คำถามที่พบบ่อย
### ฉันสามารถรวมไฟล์ BMP ที่มีขนาดต่างกันโดยใช้ GroupDocs.Merger ได้หรือไม่
ใช่ GroupDocs.Merger จัดการไฟล์ BMP ที่มีขนาดแตกต่างกันได้อย่างมีประสิทธิภาพในระหว่างการรวม
### GroupDocs.Merger รองรับรูปแบบรูปภาพอื่นนอกเหนือจาก BMP หรือไม่
ใช่ GroupDocs.Merger รองรับรูปแบบรูปภาพที่หลากหลาย เช่น JPEG, PNG, TIFF และ GIF และอื่นๆ
### GroupDocs.Merger เข้ากันได้กับแอปพลิเคชัน .NET Core หรือไม่
ใช่ GroupDocs.Merger เข้ากันได้กับทั้งสภาพแวดล้อม .NET Framework และ .NET Core
### ฉันสามารถปรับแต่งตัวเลือกการรวมไฟล์ BMP ได้หรือไม่
ใช่ GroupDocs.Merger มีตัวเลือกมากมายในการปรับแต่งพารามิเตอร์การรวมสำหรับไฟล์ BMP
### ฉันจะรับการสนับสนุนสำหรับคำถามที่เกี่ยวข้องกับ GroupDocs.Merger ได้ที่ไหน
 คุณสามารถขอรับการสนับสนุนและมีส่วนร่วมกับชุมชนได้ที่[ฟอรัม GroupDocs](https://forum.groupdocs.com/c/merger/32).