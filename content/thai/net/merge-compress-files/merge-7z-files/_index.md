---
title: วิธีรวมไฟล์ 7z
linktitle: วิธีรวมไฟล์ 7z
second_title: GroupDocs.Merger .NET API
description: รวมไฟล์ 7z ได้อย่างง่ายดายโดยใช้ GroupDocs.Merger สำหรับ .NET ปฏิบัติตามคำแนะนำทีละขั้นตอนของเราเพื่อรวมไฟล์เก็บถาวรหลายรายการเป็นไฟล์เดียวได้อย่างราบรื่น
weight: 10
url: /th/net/merge-compress-files/merge-7z-files/
---
## การแนะนำ
การรวมไฟล์ 7z สามารถทำได้อย่างมีประสิทธิภาพโดยใช้ GroupDocs.Merger สำหรับ .NET ซึ่งเป็นไลบรารีการจัดการเอกสารอันทรงพลัง บทช่วยสอนนี้จะแนะนำคุณตลอดกระบวนการทีละขั้นตอน ช่วยให้คุณสามารถรวมไฟล์ 7z ของคุณได้อย่างราบรื่นอย่างง่ายดาย
## ข้อกำหนดเบื้องต้น
ก่อนที่คุณจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีสิ่งต่อไปนี้:
- ติดตั้ง Visual Studio บนระบบของคุณแล้ว
-  ติดตั้ง GroupDocs.Merger สำหรับไลบรารี .NET แล้ว คุณสามารถดาวน์โหลดได้จาก[ที่นี่](https://releases.groupdocs.com/merger/net/).
- ความเข้าใจพื้นฐานเกี่ยวกับการเขียนโปรแกรม C#

## นำเข้าเนมสเปซ
ขั้นแรก ใส่เนมสเปซที่จำเป็นในโค้ด C# ของคุณ:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## ขั้นตอนที่ 1: โหลดไฟล์ Source 7Z
เริ่มต้นด้วยการระบุไดเร็กทอรีเอาต์พุตและชื่อไฟล์สำหรับไฟล์ 7z ที่ผสาน:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.7z");
```
## ขั้นตอนที่ 2: รวมไฟล์ 7Z
โหลดไฟล์ 7Z ต้นทางและเพิ่มไฟล์ 7Z อื่นที่คุณต้องการรวม:
```csharp
using (var merger = new Merger("Your Sample File"))
{
    merger.Join("Your Sample File");
    merger.Save(outputFile);
}
```
## ขั้นตอนที่ 3: บันทึกไฟล์ 7Z ที่ผสาน
ดำเนินการดำเนินการผสานและบันทึกไฟล์ 7Z ที่ผสานเข้าด้วยกัน:
```csharp
Console.WriteLine("\n7Z files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## บทสรุป
ในบทช่วยสอนนี้ เราได้สำรวจวิธีการรวมไฟล์ 7z โดยใช้ GroupDocs.Merger สำหรับ .NET ด้วยการทำตามขั้นตอนที่ตรงไปตรงมาเหล่านี้ คุณจะสามารถรวมไฟล์ 7z หลายไฟล์เป็นไฟล์เก็บถาวรแบบรวมเป็นหนึ่งเดียวได้อย่างมีประสิทธิภาพ

## คำถามที่พบบ่อย
### ฉันสามารถรวมไฟล์ 7z มากกว่าสองไฟล์โดยใช้ GroupDocs.Merger ได้หรือไม่
 ใช่ คุณสามารถรวมไฟล์ 7z จำนวนเท่าใดก็ได้เข้าด้วยกันโดยใช้ไลบรารีนี้ เพียงเพิ่มแต่ละไฟล์โดยใช้นามสกุล`Join` วิธี.
### GroupDocs.Merger for .NET เข้ากันได้กับรูปแบบไฟล์เก็บถาวรอื่นๆ หรือไม่
ใช่ GroupDocs.Merger รองรับการรวมรูปแบบเอกสารที่หลากหลาย รวมถึงไฟล์เก็บถาวร เช่น ZIP, 7z และ RAR
### ฉันจะรับการสนับสนุนหรือความช่วยเหลือเพิ่มเติมเกี่ยวกับ GroupDocs.Merger ได้ที่ไหน
 หากต้องการความช่วยเหลือเพิ่มเติม โปรดไปที่[ฟอรัม GroupDocs.Merger](https://forum.groupdocs.com/c/merger/32).
### ฉันสามารถลองใช้ GroupDocs.Merger สำหรับ .NET ก่อนซื้อได้หรือไม่
 ใช่ คุณสามารถสำรวจฟังก์ชันการทำงานของ GroupDocs.Merger ได้โดยการดาวน์โหลด[รุ่นทดลองใช้ฟรี](https://releases.groupdocs.com/).
### ฉันจะขอรับใบอนุญาตชั่วคราวสำหรับ GroupDocs.Merger ได้อย่างไร
 หากคุณต้องการใบอนุญาตชั่วคราว โปรดไปที่[ที่นี่](https://purchase.groupdocs.com/temporary-license/).