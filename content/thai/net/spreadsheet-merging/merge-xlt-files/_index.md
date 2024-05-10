---
title: รวมไฟล์ XLT
linktitle: รวมไฟล์ XLT
second_title: GroupDocs.Merger .NET API
description: เรียนรู้วิธีผสานไฟล์ XLT รวมเทมเพลต Excel โดยทางโปรแกรมใน C# เข้ากับคำแนะนำทีละขั้นตอนนี้
type: docs
weight: 15
url: /th/net/spreadsheet-merging/merge-xlt-files/
---
## การแนะนำ
ในบทช่วยสอนนี้ เราจะสำรวจวิธีการรวมไฟล์ XLT (เทมเพลต Excel) GroupDocs.Merger เป็น API ที่ทรงพลังซึ่งช่วยให้นักพัฒนาจัดการรูปแบบเอกสารต่างๆ รวมถึงไฟล์ Excel ได้ด้วยการเขียนโปรแกรม ด้วยการรวมไฟล์ XLT คุณสามารถรวมเทมเพลตหลายรายการไว้ในเอกสารเดียว ปรับปรุงขั้นตอนการทำงานของคุณและเพิ่มประสิทธิภาพ
## ข้อกำหนดเบื้องต้น
ก่อนที่เราจะเริ่มต้น ตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:
1.  GroupDocs.Merger สำหรับ .NET: คุณสามารถดาวน์โหลด API ได้จาก[ที่นี่](https://releases.groupdocs.com/merger/net/).
2. สภาพแวดล้อมการพัฒนา: ติดตั้ง Visual Studio หรือ IDE ที่รองรับ
3. ความรู้พื้นฐานของ C#: ความคุ้นเคยกับภาษาการเขียนโปรแกรม C# และการพัฒนา .NET

## นำเข้าเนมสเปซ
ในการเริ่มต้น ให้นำเข้าเนมสเปซที่จำเป็นในโปรเจ็กต์ C# ของคุณ:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## ขั้นตอนที่ 1: ตั้งค่าไดเรกทอรีผลลัพธ์
 เริ่มต้นด้วยการกำหนดไดเร็กทอรีเอาต์พุตที่จะบันทึกไฟล์ XLT ที่ผสานเข้าด้วยกัน แทนที่`"Your Output Directory"` ด้วยเส้นทางที่คุณต้องการ
```csharp
string outputFolder = "Your Output Directory";
```
## ขั้นตอนที่ 2: กำหนดเส้นทางไฟล์เอาต์พุต
ระบุชื่อและเส้นทางสำหรับไฟล์ XLT ที่ผสานภายในไดเร็กทอรีเอาต์พุต
```csharp
string outputFile = Path.Combine(outputFolder, "merged.xlt");
```
## ขั้นตอนที่ 3: โหลดและรวมไฟล์ XLT
ใช้ GroupDocs.Merger เพื่อโหลดและรวมไฟล์ XLT ต้นฉบับ ที่นี่ เราจะสาธิตการรวมไฟล์ XLT สองไฟล์เข้าด้วยกัน
```csharp
// โหลดไฟล์ XLT ต้นทาง
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    // เพิ่มไฟล์ XLT อื่นเพื่อรวม
    merger.Join("Your Sample File");
    // รวมไฟล์ XLT และบันทึกผลลัพธ์
    merger.Save(outputFile);
}
Console.WriteLine("\nXLT files merge completed successfully. \nCheck output in {0}", outputFolder);
```
ในข้อมูลโค้ดนี้:
- `"Your Sample File"` และ`"Your Sample File"` แสดงถึงเส้นทางไปยังไฟล์ XLT ต้นทาง
- `merger.Join()` ใช้เพื่อเพิ่มไฟล์ XLT อื่นสำหรับการรวม
- `merger.Save()` ถูกเรียกให้รวมไฟล์ XLT และบันทึกผลลัพธ์ตามที่ระบุ`outputFile`.

## บทสรุป
ในบทช่วยสอนนี้ เราได้ศึกษาวิธีการรวมไฟล์ XLT ด้วยการทำตามขั้นตอนเหล่านี้ คุณจะสามารถรวมเทมเพลต Excel หลายเทมเพลตให้เป็นเอกสารเดียวได้อย่างมีประสิทธิภาพ เพิ่มความสามารถในการจัดการเอกสารภายในแอปพลิเคชัน .NET ของคุณ

## คำถามที่พบบ่อย
### ฉันสามารถรวมไฟล์ XLT มากกว่าสองไฟล์ได้หรือไม่
ได้ คุณสามารถรวมไฟล์ XLT หลายไฟล์ได้โดยการเพิ่มตามลำดับโดยใช้`merger.Join()`.
### GroupDocs.Merger เข้ากันได้กับรูปแบบไฟล์ Excel อื่น ๆ เช่น XLSX หรือ XLS หรือไม่
ใช่ GroupDocs.Merger รองรับไฟล์ Excel หลากหลายรูปแบบ รวมถึง XLSX, XLS และ XLT
### ฉันจะหาตัวอย่างและเอกสารประกอบเพิ่มเติมสำหรับ GroupDocs.Merger for .NET ได้ที่ไหน
 มีเอกสารรายละเอียดและตัวอย่างโค้ดให้ใช้งาน[ที่นี่](https://reference.groupdocs.com/merger/net/).
### GroupDocs.Merger มีเวอร์ชันทดลองใช้งานสำหรับการทดสอบหรือไม่
 ใช่ คุณสามารถดาวน์โหลดเวอร์ชันทดลองใช้ฟรีได้จาก[ที่นี่](https://releases.groupdocs.com/).
### ฉันจะรับการสนับสนุนด้านเทคนิคหรือความช่วยเหลือเกี่ยวกับ GroupDocs.Merger ได้อย่างไร
 สำหรับความช่วยเหลือด้านเทคนิคและการสนับสนุนชุมชน โปรดไปที่[ฟอรัม GroupDocs.Merger](https://forum.groupdocs.com/c/merger/32).