---
date: '2026-02-06'
description: เรียนรู้วิธีสกัดหน้าที่เฉพาะและแยกเอกสารตามช่วงหน้าโดยใช้ GroupDocs.Merger
  สำหรับ Java รวมถึงตัวกรองหน้าคี่/คู่
keywords:
- GroupDocs.Merger for Java
- split documents by page range
- document management
title: สกัดหน้าที่เฉพาะด้วย GroupDocs.Merger สำหรับ Java
type: docs
url: /th/java/document-splitting/split-documents-page-range-groupdocs-merger-java/
weight: 1
---

# แยกหน้าที่ต้องการด้วย GroupDocs.Merger สำหรับ Java

อย่างมีประสิทธิภาพ **extract specific pages** จากไฟล์ PDF, Word หรือพรีเซนเทชันขนาดใหญ่โดยไม่ต้องคัดลอก‑วางด้วยตนเอง ในบทแนะนำนี้คุณจะได้เห็นวิธีแยกเอกสารตามช่วงหน้า, ใช้ตัวกรองเช่นหน้าคี่/คู่, และสร้างไฟล์หน้าเดียว—ทั้งหมดด้วย **GroupDocs.Merger for Java**.

## คำตอบด่วน
- **“extract specific pages” หมายถึงอะไร?** หมายถึงการสร้างเอกสารใหม่ที่มีเฉพาะหน้าที่คุณเลือกจากไฟล์ต้นฉบับเท่านั้น.  
- **รูปแบบที่รองรับคืออะไร?** PDF, DOCX, PPTX, และรูปแบบยอดนิยมอื่น ๆ อีกหลายรูปแบบ.  
- **ฉันสามารถกรองตามหน้าคี่หรือคู่ได้หรือไม่?** ได้, โดยใช้ตัวเลือก `RangeMode` (เช่น `OddPages`).  
- **ฉันต้องการไลเซนส์หรือไม่?** การทดลองใช้ฟรีสามารถใช้งานเพื่อประเมินผลได้; จำเป็นต้องมีไลเซนส์ถาวรสำหรับการใช้งานจริง.  
- **เหมาะกับเอกสารขนาดใหญ่หรือไม่?** ใช่—แยกส่วนของเอกสารขนาดใหญ่เพื่อรักษาการใช้หน่วยความจำให้ต่ำ.

## การแยกหน้าที่ต้องการคืออะไร?
การแยกหน้าที่ต้องการคือกระบวนการนำส่วนย่อยของหน้าจากเอกสารต้นฉบับและบันทึกเป็นไฟล์ใหม่ที่เป็นอิสระ ซึ่งมีประโยชน์สำหรับการสร้างรายงานที่เน้นเฉพาะส่วน, การแชร์ข้อสัญญา, หรือการเตรียมเอกสารประกอบการพรีเซนเทชัน.

## ทำไมต้องใช้ GroupDocs.Merger สำหรับ Java เพื่อแยก PDF และเอกสาร Word?
- **Unified API** – ทำงานกับ PDF, Word, PowerPoint และอื่น ๆ ดังนั้นคุณไม่จำเป็นต้องใช้เครื่องมือแยกต่างหาก.  
- **Fine‑grained control** – เลือกช่วงหน้าที่แม่นยำ, ตัวกรองหน้าคี่/คู่, หรือการแยกหน้าเดี่ยว.  
- **Performance‑focused** – จัดการไฟล์ขนาดใหญ่อย่างมีประสิทธิภาพโดยสตรีมหน้าต่าง ๆ แทนการโหลดเอกสารทั้งหมดเข้าสู่หน่วยความจำ.  

## ข้อกำหนดเบื้องต้น
- **GroupDocs.Merger for Java** (เวอร์ชันล่าสุด)  
- **JDK 8+**  
- IDE เช่น IntelliJ IDEA หรือ Eclipse  
- Maven หรือ Gradle สำหรับการจัดการ dependencies  

## การตั้งค่า GroupDocs.Merger สำหรับ Java
เพิ่มไลบรารีลงในโปรเจกต์ของคุณโดยใช้เครื่องมือสร้างที่คุณต้องการ.

**Maven**
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle**
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Direct Download**: คุณสามารถดาวน์โหลดไลบรารีโดยตรงจาก [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### การรับไลเซนส์
คุณสามารถรับไลเซนส์ได้ผ่าน:
- **Free Trial** – ทดสอบคุณสมบัติทั้งหมดโดยไม่มีข้อจำกัด.  
- **Temporary License** – ระยะเวลาการประเมินที่ขยายออกไป.  
- **Purchase** – ไลเซนส์ถาวรสำหรับการใช้งานจริง.  

**การเริ่มต้นและตั้งค่าเบื้องต้น**  
เพื่อเริ่มต้น GroupDocs.Merger, สร้างอินสแตนซ์ของ `Merger` พร้อมเส้นทางไฟล์เอกสารของคุณ:
```java
import com.groupdocs.merger.Merger;

String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
Merger merger = new Merger(filePath);
```

## วิธีแยกหน้าที่ต้องการด้วย GroupDocs.Merger สำหรับ Java
ส่วนนี้จะอธิบายขั้นตอนการแยกเอกสารตามช่วงหน้าโดยใช้ตัวกรองหน้าคี่.

### ขั้นตอนที่ 1: กำหนดเส้นทางไฟล์เข้าและออก
กำหนดไฟล์ต้นทางและรูปแบบชื่อไฟล์ปลายทางสำหรับไฟล์ที่แยกออก:
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToSinglePagesByRangeWithFilter-Output.docx";
```

### ขั้นตอนที่ 2: ตั้งค่า Split Options (ช่วง & ตัวกรอง)
สร้างอ็อบเจกต์ `SplitOptions` ที่บอกไลบรารีว่าต้องแยกหน้าใดและใช้ตัวกรองใด:
```java
import com.groupdocs.merger.domain.options.SplitOptions;
import com.groupdocs.merger.domain.options.RangeMode;

SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7, RangeMode.OddPages);
```
- **filePathOut** – รูปแบบชื่อไฟล์ปลายทาง.  
- **3 and 7** – หมายเลขหน้าเริ่มต้นและสิ้นสุด (รวม).  
- **RangeMode.OddPages** – เก็บเฉพาะหน้าคี่ภายในช่วงนั้น, ซึ่งเป็นการ **extract specific pages** อย่างมีประสิทธิภาพ.  

### ขั้นตอนที่ 3: ดำเนินการแยก
ดำเนินการแยกโดยใช้ตัวเลือกที่กำหนด:
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

#### เคล็ดลับการแก้ไขปัญหา
- ตรวจสอบว่าเส้นทางไฟล์ถูกต้องและเข้าถึงได้.  
- ตรวจสอบว่าหมายเลขหน้าตรงกับจำนวนหน้าทั้งหมดของเอกสาร; หากไม่จะเกิดข้อยกเว้น.  

## วิธีแยก PDF เป็นหน้าเดี่ยว (split pdf single pages)
หากคุณต้องการให้แต่ละหน้ากลายเป็น PDF แยกไฟล์, เพียงตั้งค่า `RangeMode` เป็น `AllPages` และกำหนดช่วงที่ครอบคลุมเอกสารทั้งหมด. คลาส `SplitOptions` เดียวกันสามารถจัดการสถานการณ์นี้ได้.

## วิธีแยกเอกสารขนาดใหญ่อย่างมีประสิทธิภาพ (split large document)
เมื่อทำงานกับไฟล์ขนาดใหญ่มาก, ควรพิจารณาแยกเป็นช่วงย่อย ๆ (เช่น 1‑100, 101‑200) เพื่อลดภาระหน่วยความจำ. ปิดอินสแตนซ์ `Merger` หลังจากแต่ละการดำเนินการเพื่อปล่อยทรัพยากร.

## วิธีแยก PDF หน้าเลขคี่ (split pdf odd pages)
ตัวอย่างข้างต้นได้แสดงการใช้ตัวกรอง `OddPages` แล้ว. เปลี่ยน `RangeMode.OddPages` เป็น `RangeMode.EvenPages` เพื่อแยกหน้าคู่แทน.

## การประยุกต์ใช้งานจริง
1. **Document Segmentation** – แบ่งสัญญาเป็น PDF ระดับข้อเพื่อการตรวจสอบที่ง่ายขึ้น.  
2. **Report Management** – แยกบทหรือภาคผนวกเฉพาะจากรายงานประจำปีที่ยาว.  
3. **Presentation Preparation** – แยกสไลด์แต่ละหน้าสำหรับการประชุมที่เจาะจง.  

คุณยังสามารถรวมตรรกะนี้กับฐานข้อมูลหรือระบบจัดการเนื้อหาเพื่อทำให้กระบวนการทำงานอัตโนมัติได้.

## ข้อควรพิจารณาด้านประสิทธิภาพ
- **Memory Management** – เรียก `merger.close()` (หรือใช้ try‑with‑resources) หลังการประมวลผลเพื่อปล่อยไฟล์แฮนด์เดิล.  
- **Selective Ranges** – ขอเฉพาะหน้าที่คุณต้องการจริง ๆ; จะช่วยลดการใช้ I/O และ CPU.  

## สรุป
ตอนนี้คุณมีวิธีที่ชัดเจนและเป็นขั้นตอนเพื่อ **extract specific pages** จากเอกสารประเภทใดก็ได้ที่รองรับโดยใช้ GroupDocs.Merger สำหรับ Java. ความสามารถนี้ช่วยทำให้กระบวนการจัดการเอกสารของคุณเป็นระเบียบและทำให้คุณสามารถส่งมอบเนื้อหาที่ผู้ใช้ต้องการได้อย่างแม่นยำ.

### ขั้นตอนต่อไป
- ทดลองใช้ค่า `RangeMode` ต่าง ๆ (เช่น `EvenPages`, `AllPages`).  
- ผสานการแยกกับฟังก์ชัน **merge** เพื่อจัดลำดับใหม่หรือเชื่อมต่อหน้าที่แยกออก.  
- สำรวจ API เต็มรูปแบบสำหรับเอกสารที่มีการป้องกันด้วยรหัสผ่าน, วอเตอร์มาร์ค, และอื่น ๆ.  

## คำถามที่พบบ่อย
**Q: GroupDocs.Merger for Java คืออะไร?**  
A: ไลบรารีที่แข็งแรงที่ช่วยให้ทำการรวม, แยก, และจัดลำดับหน้าต่าง ๆ ในหลายรูปแบบเอกสาร.

**Q: ฉันสามารถใช้ GroupDocs.Merger กับภาษาโปรแกรมอื่นได้หรือไม่?**  
A: ใช่, มีความสามารถคล้ายกันสำหรับ .NET และ C++.

**Q: ฉันจะจัดการกับข้อยกเว้นระหว่างการประมวลผลเอกสารอย่างไร?**  
A: ห่อการเรียกใช้ในบล็อก `try‑catch` และตรวจสอบ `MergerException` เพื่อดูข้อมูลข้อผิดพลาดโดยละเอียด.

**Q: สามารถแยกเอกสารโดยไม่ใช้ตัวกรองหน้าคี่/คู่ได้หรือไม่?**  
A: แน่นอน—ตั้งค่า `RangeMode.AllPages` หรือไม่ระบุตัวกรองเพื่อแยกตามหมายเลขหน้าที่แน่นอน.

**Q: ความต้องการของระบบสำหรับการใช้ GroupDocs.Merger มีอะไรบ้าง?**  
A: Java 8 หรือสูงกว่าและ IDE ที่เข้ากันได้; ไม่ต้องการ dependencies เนทีฟเพิ่มเติม.

## แหล่งข้อมูล
- [เอกสารประกอบ GroupDocs.Merger](https://docs.groupdocs.com/merger/java/)
- [อ้างอิง API](https://reference.groupdocs.com/merger/java/)
- [ดาวน์โหลดไลบรารี](https://releases.groupdocs.com/merger/java/)
- [ซื้อไลเซนส์](https://purchase.groupdocs.com/buy)
- [ทดลองใช้ฟรีและไลเซนส์ชั่วคราว](https://releases.groupdocs.com/merger/java/)
- [ฟอรั่มสนับสนุน](https://forum.groupdocs.com/c/merger/)

---

**อัปเดตล่าสุด:** 2026-02-06  
**ทดสอบด้วย:** GroupDocs.Merger เวอร์ชันล่าสุด (Java)  
**ผู้เขียน:** GroupDocs