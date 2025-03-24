---
title: รวมไฟล์ DOTX
linktitle: รวมไฟล์ DOTX
second_title: GroupDocs.Merger .NET API
description: เรียนรู้วิธีผสานไฟล์ DOTX ใน .NET โดยใช้ GroupDocs.Merger ได้อย่างง่ายดาย เพิ่มความสามารถในการจัดการเอกสารของคุณ
weight: 15
url: /th/net/document-merging/merge-dotx-files/
---

# รวมไฟล์ DOTX

## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีการผสานไฟล์ DOTX (เทมเพลต Word) โดยใช้ GroupDocs.Merger สำหรับ .NET GroupDocs.Merger เป็น API อันทรงประสิทธิภาพที่ช่วยให้นักพัฒนาสามารถจัดการรูปแบบเอกสารต่างๆ ภายในแอปพลิเคชัน .NET ได้อย่างราบรื่น ด้วยการใช้ประโยชน์จาก API นี้ คุณสามารถรวมไฟล์ DOTX หลายไฟล์ลงในเอกสารเดียวได้อย่างมีประสิทธิภาพโดยใช้โค้ดเพียงไม่กี่บรรทัด
## ข้อกำหนดเบื้องต้น
ก่อนที่จะเข้าสู่บทช่วยสอน ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- ติดตั้ง Visual Studio บนเครื่องของคุณแล้ว
- ติดตั้ง .NET SDK (เวอร์ชันที่เข้ากันได้) แล้ว
-  ติดตั้ง GroupDocs.Merger สำหรับ .NET แล้ว (อ้างอิงถึงไฟล์[คู่มือการติดตั้ง](https://tutorials.groupdocs.com/merger/net/) สำหรับรายละเอียด)
- ความรู้พื้นฐานเกี่ยวกับการเขียนโปรแกรม C#

## นำเข้าเนมสเปซ
ในการเริ่มต้น ให้นำเข้าเนมสเปซที่จำเป็นลงในโปรเจ็กต์ C# ของคุณ:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## ขั้นตอนที่ 1: ตั้งค่าไดเร็กทอรีเอาต์พุตและชื่อไฟล์
ขั้นแรก ให้กำหนดเส้นทางไดเร็กทอรีเอาต์พุตและชื่อของไฟล์ DOTX ที่ผสาน
```csharp
string outputFolder = "YourOutputDirectory";
string outputFile = Path.Combine(outputFolder, "merged.dotx");
```
 แทนที่`"YourOutputDirectory"` ด้วยเส้นทางที่คุณต้องการบันทึกไฟล์ DOTX ที่ผสาน
## ขั้นตอนที่ 2: รวมไฟล์ DOTX
จากนั้น ให้ใช้ GroupDocs.Merger เพื่อรวมไฟล์ DOTX หลายไฟล์ให้เป็นเอกสารเดียว
```csharp
// โหลดไฟล์ DOTX ต้นทาง
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    // เพิ่มไฟล์ DOTX อื่นเพื่อรวม
    merger.Join("Your Sample File");
    
    // รวมไฟล์ DOTX และบันทึกผลลัพธ์
    merger.Save(outputFile);
}
Console.WriteLine("\nDOTX files merge completed successfully. \nCheck output in {0}", outputFolder);
```
ในข้อมูลโค้ดนี้:
- `"Your Sample File"` และ`"Your Sample File"` แสดงถึงเส้นทางไปยังไฟล์ DOTX ที่คุณต้องการรวม แทนที่สิ่งเหล่านี้ด้วยเส้นทางไฟล์จริงของคุณ
- `merger.Join()` ใช้เพื่อเพิ่มไฟล์ DOTX เพิ่มเติมในการควบรวมกิจการ
- `merger.Save()` รวมไฟล์ DOTX และบันทึกผลลัพธ์ที่ผสานตามที่ระบุ`outputFile` เส้นทาง.

## บทสรุป
ในบทช่วยสอนนี้ เราได้กล่าวถึงวิธีการรวมไฟล์ DOTX โดยใช้ GroupDocs.Merger สำหรับ .NET ด้วยการทำตามขั้นตอนเหล่านี้และใช้ประโยชน์จาก GroupDocs.Merger คุณสามารถจัดการไฟล์เทมเพลต Word ภายในแอปพลิเคชัน .NET ของคุณได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### GroupDocs.Merger สามารถรวมรูปแบบเอกสารอื่นนอกเหนือจาก DOTX ได้หรือไม่
ใช่ GroupDocs.Merger รองรับการรวมรูปแบบเอกสารต่างๆ เช่น DOCX, XLSX, PPTX, PDF และอื่นๆ
### GroupDocs.Merger เข้ากันได้กับ .NET Core หรือไม่
ใช่ GroupDocs.Merger เข้ากันได้กับทั้ง .NET Framework และ .NET Core
### ฉันจะหาการสนับสนุนหรือเอกสารเพิ่มเติมสำหรับ GroupDocs.Merger ได้ที่ไหน
 คุณสามารถอ้างถึง[เอกสาร GroupDocs.Merger](https://tutorials.groupdocs.com/merger/net/) สำหรับการอ้างอิง API โดยละเอียดและตัวอย่างการใช้งาน
### GroupDocs.Merger เสนอให้ทดลองใช้ฟรีหรือไม่
 ใช่ คุณสามารถเข้าถึง[รุ่นทดลองใช้ฟรี](https://releases.groupdocs.com/) เพื่อประเมิน GroupDocs.Merger
### ฉันจะซื้อใบอนุญาตสำหรับ GroupDocs.Merger ได้อย่างไร
 คุณสามารถซื้อใบอนุญาตได้จาก[เว็บไซต์กรุ๊ปดอคส์](https://purchase.groupdocs.com/buy) ตามความต้องการการใช้งานของคุณ