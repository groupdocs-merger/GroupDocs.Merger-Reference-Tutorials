---
date: '2026-02-19'
description: เรียนรู้วิธีฝัง PDF ในเอกสาร Word และเพิ่ม PDF ไปยังไฟล์ Word ด้วย GroupDocs.Merger
  สำหรับ Java คู่มือแบบขั้นตอนต่อขั้นตอนเพื่อการฝัง OLE อย่างราบรื่น.
keywords:
- embed OLE objects in Word documents
- GroupDocs Merger for Java tutorial
- import OLE objects using Java
title: วิธีฝัง PDF ใน Word ด้วย GroupDocs.Merger สำหรับ Java – คู่มือฉบับสมบูรณ์
type: docs
url: /th/java/document-import/embed-ole-objects-word-documents-groupdocs-java/
weight: 1
---

# วิธีฝัง PDF ใน Word ด้วย GroupDocs.Merger สำหรับ Java

การฝัง PDF โดยตรงภายในเอกสาร Word สามารถปรับปรุงการทำงานร่วมกันได้อย่างมาก เนื่องจากผู้อ่านไม่ต้องสลับไฟล์อีกต่อไป ในคู่มือนี้คุณจะได้ค้นพบ **วิธีฝัง pdf ใน word** ด้วย GroupDocs.Merger สำหรับ Java และดูเคล็ดลับการทำงานจริงเกี่ยวกับ **เพิ่ม pdf ไปยัง word** เราจะอธิบายทุกขั้นตอนตั้งแต่การตั้งค่าห้องสมุดจนถึงการปรับขนาดและตำแหน่งของอ็อบเจ็กต์ OLE เพื่อให้คุณสามารถอัตโนมัติการสร้างเอกสารได้อย่างมั่นใจ.

## Quick Answers
- **ไลบรารีที่ต้องการคืออะไร?** GroupDocs.Merger for Java (เวอร์ชันล่าสุด)  
- **ฉันสามารถฝังไฟล์ประเภทใดก็ได้หรือไม่?** ใช่ – PDF, รูปภาพ, สเปรดชีต ฯลฯ เป็นอ็อบเจ็กต์ OLE  
- **ฉันต้องการไลเซนส์หรือไม่?** การทดลองใช้ฟรีทำงานสำหรับการพัฒนา; จำเป็นต้องมีไลเซนส์เชิงพาณิชย์สำหรับการใช้งานจริง  
- **IDE ของ Java ตัวใดดีที่สุด?** IntelliJ IDEA, Eclipse หรือ IDE ใด ๆ ที่รองรับ Maven/Gradle  
- **การดำเนินการใช้เวลานานเท่าไหร่?** ประมาณ 10‑15 นาทีสำหรับการฝังพื้นฐาน  

## การฝัง pdf ใน word คืออะไร?
การฝัง PDF จะสร้างอ็อบเจ็กต์ OLE (Object Linking and Embedding) ภายในไฟล์ Word PDF ยังคงทำงานได้เต็มที่—ผู้ใช้สามารถดับเบิลคลิกไอคอนเพื่อเปิดในโปรแกรมดู PDF ในขณะที่เอกสาร Word ยังคงเป็นไฟล์เดียวที่ครบถ้วน

## ทำไมต้องเพิ่ม pdf ไปยัง word ด้วย GroupDocs.Merger?
- **เอกสารแหล่งเดียว:** เก็บสัญญา คู่มือ หรือรายงานไว้ด้วยกันโดยไม่มีลิงก์ภายนอก  
- **การเข้าถึงที่ดีขึ้น:** ผู้อ่านสามารถดู PDF ได้โดยไม่ต้องออกจากสภาพแวดล้อมของ Word  
- **เป็นมิตรกับการอัตโนมัติ:** เหมาะสำหรับการสร้างรายงานชุดหรือแพคเกจกฎหมายโดยอัตโนมัติ  
- **ขยายได้:** คุณสามารถ **ฝังหลาย pdfs word** เอกสารโดยใช้กระบวนการทำงานเดียวกันสำหรับแต่ละไฟล์  

## ข้อกำหนดเบื้องต้น
- **ไลบรารีและการพึ่งพา:** รวมไลบรารี GroupDocs.Merger ผ่าน Maven หรือ Gradle.  
- **สภาพแวดล้อมการพัฒนา:** IntelliJ IDEA, Eclipse หรือ IDE ของ Java ใด ๆ  
- **ความรู้พื้นฐาน:** ความคุ้นเคยกับ Java และแนวคิดการจัดการเอกสาร  

## การตั้งค่า GroupDocs.Merger สำหรับ Java
เพื่อฝังอ็อบเจ็กต์ OLE ก่อนอื่นให้เพิ่มไลบรารีลงในโปรเจกต์ของคุณ.

### Maven
เพิ่ม dependency นี้ลงในไฟล์ `pom.xml` ของคุณ:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle
ใส่นี้ในไฟล์ `build.gradle` ของคุณ:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### Direct Download
หรือคุณสามารถดาวน์โหลดเวอร์ชันล่าสุดจาก [GroupDocs.Merger for Java releases page](https://releases.groupdocs.com/merger/java/).

**การรับไลเซนส์:** คุณสามารถเริ่มต้นด้วยการทดลองใช้ฟรีหรือรับไลเซนส์ชั่วคราวเพื่อประเมินคุณสมบัติก่อนซื้อ เยี่ยมชม [Purchase GroupDocs](https://purchase.groupdocs.com/buy) สำหรับรายละเอียดเพิ่มเติม.

## การเริ่มต้นพื้นฐาน
นำเข้าคลาสที่จำเป็นเพื่อให้คุณสามารถทำงานกับอ็อบเจ็กต์ OLE:
```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OleWordProcessingOptions;
```

## คู่มือขั้นตอนการฝัง pdf ใน word

### Step 1: Define file paths and target page
กำหนดเอกสาร Word ต้นฉบับ, PDF ที่คุณต้องการฝัง, และตำแหน่งที่อ็อบเจ็กต์ OLE ควรปรากฏ.
```java
String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.docx"; // Source Word document path
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf"; // File to be embedded as an OLE object
String outputFilePath = new File("YOUR_OUTPUT_DIRECTORY",
    "ImportDocumentToWordProcessing-" + Paths.get(sourceFilePath).getFileName().toString()).getPath();
int pageNumber = 2; // Page number where the OLE object will be inserted
```
- **`sourceFilePath`** – เส้นทางไปยังไฟล์ Word ที่มีอยู่  
- **`embeddedFilePath`** – PDF ที่คุณต้องการ **เพิ่ม pdf ไปยัง word**  
- **`outputFilePath`** – ที่ที่จะบันทึกเอกสารใหม่  
- **`pageNumber`** – หน้าที่จะเป็นที่ตั้งของอ็อบเจ็กต์ OLE  

### Step 2: Configure OleWordProcessingOptions
ปรับแต่งลักษณะของ PDF ที่ฝังโดยกำหนดขนาดของมัน.
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Set width of the embedded object (in points)
oleWordsOptions.setHeight(300); // Set height of the embedded object (in points)
```
- **`setWidth()` / `setHeight()`** – ควบคุมขนาดของไอคอน PDF ที่ปรากฏในเอกสาร Word  

### Step 3: Initialize Merger and import the OLE object
สร้างอินสแตนซ์ `Merger` สำหรับเอกสารต้นฉบับ, นำเข้าอ็อบเจ็กต์ OLE, และบันทึกผลลัพธ์.
```java
Merger merger = new Merger(sourceFilePath);
{
    merger.importDocument(oleWordsOptions); // Embed the OLE object into the Word document
    merger.save(outputFilePath); // Save changes to a new output file
}
```
- **`importDocument()`** – รับ `OleWordProcessingOptions` และแทรก PDF เป็นอ็อบเจ็กต์ OLE  
- **`save()`** – เขียนเอกสารที่แก้ไขแล้วไปยัง `outputFilePath`  

### Step 4: (Optional) Re‑apply configuration for additional objects
หากคุณต้องการฝัง PDF เพิ่มเติม ให้ทำซ้ำ **ขั้นตอน 1‑3** ด้วยเส้นทางไฟล์และหมายเลขหน้าใหม่ คลาส `OleWordProcessingOptions` เดียวกันช่วยให้คุณควบคุมแต่ละอ็อบเจ็กต์แยกกันได้.

## การกำหนดค่า OleWordProcessingOptions (ขั้นสูง)
คุณสามารถปรับตำแหน่งเพิ่มเติม เช่น การจัดแนวอ็อบเจ็กต์หรือเพิ่มคำอธิบาย โค้ดตัวอย่างด้านล่างทำซ้ำการกำหนดค่าเบื้องต้นเพื่อความชัดเจน:
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Width of the embedded object
oleWordsOptions.setHeight(300); // Height of the embedded object
```

## การประยุกต์ใช้งานจริง
การฝัง PDF มีประโยชน์ในหลายสถานการณ์จริง:

1. **คู่มือเทคนิค** – แทรกแผนผังละเอียดหรือ PDF อ้างอิงโดยตรงในคู่มือ  
2. **รายงานการเงิน** – เพิ่ม PDF การตรวจสอบเสริมโดยไม่ทำให้การไหลของรายงานหลักขัดจังหวะ  
3. **สัญญากฎหมาย** – แนบภาคผนวกหรือเอกสารแนบเป็นอ็อบเจ็กต์ OLE เพื่อการเข้าถึงง่ายระหว่างการตรวจสอบ  
4. **แพคเกจการตลาด** – **แทรก pdf ลงใน word** โบรชัวร์เพื่อให้สเปคผลิตภัณฑ์พร้อมใช้งาน  

## ข้อควรพิจารณาด้านประสิทธิภาพ
เมื่อจัดการเอกสารขนาดใหญ่หรืออ็อบเจ็กต์ OLE หลายตัว ให้คำนึงถึงเคล็ดลับต่อไปนี้:

- **ตัดเนื้อหาที่ไม่จำเป็น** – ฝังเฉพาะหน้าที่คุณต้องการจริง ๆ  
- **จัดการหน่วยความจำ** – ใช้แฟล็ก `-Xmx` ของ Java เพื่อจัดสรรพื้นที่ heap เพียงพอสำหรับไฟล์ขนาดใหญ่  
- **อัปเดตอยู่เสมอ** – รุ่นใหม่ของ GroupDocs.Merger มักมีการปรับปรุงประสิทธิภาพ  

## ปัญหาทั่วไปและวิธีแก้
- **เส้นทางไฟล์ไม่ถูกต้อง:** ตรวจสอบว่าเส้นทางของ Word และ PDF เป็นแบบ absolute หรือ relative อย่างถูกต้องต่อโฟลเดอร์รากของโปรเจกต์  
- **ข้อผิดพลาดหน่วยความจำไม่พอ:** เพิ่มขนาด heap ของ JVM หรือประมวลผลเอกสารเป็นชุดเล็ก ๆ  
- **PDF เสียหาย:** ตรวจสอบว่า PDF ต้นฉบับเปิดได้ตามปกติในโปรแกรมดูก่อนฝัง  
- **ไอคอน OLE หาย:** ตรวจสอบว่าเทมเพลต Word ไม่ได้ถูกป้องกันการแทรก OLE  

## คำถามที่พบบ่อย

**Q: OLE embedding คืออะไร?**  
A: การฝังทำให้คุณสามารถแทรกอ็อบเจ็กต์เช่น PDF ลงในเอกสาร Word เป็นลิงก์ที่รักษาฟังก์ชันเดิมของมันไว้  

**Q: ฉันสามารถฝังอ็อบเจ็กต์ OLE หลายตัวในเอกสารเดียวได้หรือไม่?**  
A: ได้, แต่ละอ็อบเจ็กต์สามารถกำหนดค่าหน้าและขนาดต่าง ๆ ได้โดยใช้ `OleWordProcessingOptions` แยกกัน  

**Q: มีขีดจำกัดขนาดของไฟล์ที่ฝังหรือไม่?**  
A: ขีดจำกัดโดยทั่วไปขึ้นอยู่กับข้อจำกัดของ Word เอง, แต่ GroupDocs.Merger จัดการไฟล์ขนาดใหญ่ได้อย่างมีประสิทธิภาพ  

**Q: ฉันจะแก้ไขข้อผิดพลาดการฝังอย่างไร?**  
A: ตรวจสอบว่าเส้นทางไฟล์ถูกต้องและ JVM มีหน่วยความจำเพียงพอ ตรวจสอบว่า PDF ต้นฉบับไม่เสียหาย  

**Q: ฉันสามารถแก้ไขอ็อบเจ็กต์ที่ฝังหลังจากแทรกได้หรือไม่?**  
A: คุณสามารถเปิดไฟล์ Word ใน Microsoft Word แล้วแก้ไขอ็อบเจ็กต์ OLE, หรือรันโค้ด Merger ใหม่ด้วยตัวเลือกที่อัปเดต  

## แหล่งข้อมูลเพิ่มเติม
- [GroupDocs.Merger Documentation](https://docs.groupdocs.com/merger/java/)
- [API Reference](https://reference.groupdocs.com/merger/java/)
- [Download Latest Version](https://releases.groupdocs.com/merger/java/)
- [Purchase GroupDocs](https://purchase.groupdocs.com/buy)
- [Free Trial](https://releases.groupdocs.com/merger/java/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [Support Forum](https://forum.groupdocs.com/c/merger/)

---

**อัปเดตล่าสุด:** 2026-02-19  
**ทดสอบกับ:** GroupDocs.Merger for Java เวอร์ชันล่าสุด  
**ผู้เขียน:** GroupDocs  

---