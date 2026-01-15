---
date: '2025-12-19'
description: เรียนรู้วิธีฝัง PDF ในเอกสาร Word และเพิ่ม PDF ไปยังไฟล์ Word ด้วย GroupDocs.Merger
  สำหรับ Java คู่มือทีละขั้นตอนสำหรับการฝัง OLE อย่างราบรื่น
keywords:
- embed OLE objects in Word documents
- GroupDocs Merger for Java tutorial
- import OLE objects using Java
title: วิธีฝัง PDF ลงใน Word ด้วย GroupDocs.Merger สำหรับ Java – คู่มือฉบับสมบูรณ์
type: docs
url: /th/java/document-import/embed-ole-objects-word-documents-groupdocs-java/
weight: 1
---

# วิธีฝัง PDF ใน Word ด้วย GroupDocs.Merger สำหรับ Java

การฝัง PDF โดยตรงในเอกสาร Word สามารถปรับปรุงการทำงานร่วมกันได้อย่างมาก เนื่องจากผู้อ่านไม่ต้องสลับไฟล์อีกต่อไป ในคู่มือนี้คุณจะได้ค้นพบ **วิธีฝัง pdf ใน word** ด้วย GroupDocs.Merger สำหรับ Java และดูเคล็ดลับการทำงานจริงเกี่ยวกับ **add pdf to word** เราจะอธิบายทุกขั้นตอนตั้งแต่การตั้งค่าห้องสมุดจนถึงการปรับขนาดและตำแหน่งของอ็อบเจ็กต์ OLE

## Quick Answers
- **ไลบรารีที่ต้องการคืออะไร?** GroupDocs.Merger for Java (รุ่นล่าสุด)  
- **ฉันสามารถฝังไฟล์ประเภทใดก็ได้หรือไม่?** ใช่ – PDFs, images, spreadsheets, ฯลฯ, เป็นอ็อบเจ็กต์ OLE  
- **ฉันต้องการใบอนุญาตหรือไม่?** การทดลองใช้ฟรีทำงานสำหรับการพัฒนา; จำเป็นต้องมีใบอนุญาตเชิงพาณิชย์สำหรับการใช้งานจริง  
- **IDE Java ใดที่เหมาะสมที่สุด?** IntelliJ IDEA, Eclipse หรือ IDE ใดก็ได้ที่รองรับ Maven/Gradle  
- **การดำเนินการใช้เวลานานเท่าไหร่?** ประมาณ 10‑15 นาทีสำหรับการฝังพื้นฐาน  

## การฝัง pdf ใน word คืออะไร?
การฝัง PDF จะสร้างอ็อบเจ็กต์ OLE (Object Linking and Embedding) ภายในไฟล์ Word PDF ยังคงทำงานเต็มรูปแบบ—ผู้ใช้สามารถดับเบิลคลิกไอคอนเพื่อเปิดในโปรแกรมดู PDF ในขณะที่เอกสาร Word ยังคงเป็นไฟล์เดียว

## ทำไมต้องเพิ่ม pdf ลงใน word ด้วย GroupDocs.Merger?
- **เอกสารแหล่งเดียว:** เก็บสัญญา คู่มือ หรือรายงานไว้ด้วยกันโดยไม่ต้องใช้ลิงก์ภายนอก.  
- **การเข้าถึงที่ดีขึ้น:** ผู้อ่านสามารถดู PDF ได้โดยไม่ต้องออกจากสภาพแวดล้อมของ Word.  
- **เป็นมิตรกับการอัตโนมัติ:** เหมาะสำหรับการสร้างรายงานชุดหรือแพ็คเกจกฎหมายโดยอัตโนมัติ.  

## Prerequisites
- **ไลบรารีและการพึ่งพา:** รวมไลบรารี GroupDocs.Merger ผ่าน Maven หรือ Gradle.  
- **สภาพแวดล้อมการพัฒนา:** IntelliJ IDEA, Eclipse หรือ IDE Java ใดก็ได้.  
- **ความรู้พื้นฐาน:** ความคุ้นเคยกับ Java และแนวคิดการจัดการเอกสาร.  

## การตั้งค่า GroupDocs.Merger สำหรับ Java
เพื่อฝังอ็อบเจ็กต์ OLE ก่อนอื่นให้เพิ่มไลบรารีลงในโปรเจกต์ของคุณ.

### Maven
เพิ่มการพึ่งพานี้ในไฟล์ `pom.xml` ของคุณ:
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
หรือดาวน์โหลดเวอร์ชันล่าสุดจาก [GroupDocs.Merger for Java releases page](https://releases.groupdocs.com/merger/java/).

**การรับใบอนุญาต:** คุณสามารถเริ่มต้นด้วยการทดลองใช้ฟรีหรือรับใบอนุญาตชั่วคราวเพื่อประเมินคุณลักษณะก่อนซื้อ เยี่ยมชม [Purchase GroupDocs](https://purchase.groupdocs.com/buy) เพื่อดูรายละเอียดเพิ่มเติม.

## การเริ่มต้นพื้นฐาน
นำเข้าคลาสที่จำเป็นเพื่อให้คุณสามารถทำงานกับอ็อบเจ็กต์ OLE:
```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OleWordProcessingOptions;
```

## คู่มือขั้นตอนต่อขั้นตอนเพื่อฝัง pdf ใน word

### Step 1: Define file paths and target page
กำหนดเอกสาร Word ต้นฉบับ, PDF ที่ต้องการฝัง, และตำแหน่งที่อ็อบเจ็กต์ OLE ควรปรากฏ.
```java
String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.docx"; // Source Word document path
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf"; // File to be embedded as an OLE object
String outputFilePath = new File("YOUR_OUTPUT_DIRECTORY",
    "ImportDocumentToWordProcessing-" + Paths.get(sourceFilePath).getFileName().toString()).getPath();
int pageNumber = 2; // Page number where the OLE object will be inserted
```

- `sourceFilePath` – เส้นทางไปยังไฟล์ Word ที่มีอยู่.  
- `embeddedFilePath` – PDF ที่คุณต้องการ **add pdf to word**.  
- `outputFilePath` – ที่ที่จะบันทึกเอกสารใหม่.  
- `pageNumber` – หน้าที่จะเป็นโฮสต์ของอ็อบเจ็กต์ OLE.  

### Step 2: Configure OleWordProcessingOptions
ปรับแต่งลักษณะของ PDF ที่ฝังโดยกำหนดขนาดของมัน.
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Set width of the embedded object (in points)
oleWordsOptions.setHeight(300); // Set height of the embedded object (in points)
```

- `setWidth()` / `setHeight()` – ควบคุมขนาดไอคอน PDF ที่ปรากฏในเอกสาร Word.  

### Step 3: Initialize Merger and import the OLE object
สร้างอินสแตนซ์ `Merger` สำหรับเอกสารต้นฉบับ, นำเข้าอ็อบเจ็กต์ OLE, และบันทึกผลลัพธ์.
```java
Merger merger = new Merger(sourceFilePath);
{
    merger.importDocument(oleWordsOptions); // Embed the OLE object into the Word document
    merger.save(outputFilePath); // Save changes to a new output file
}
```

- `importDocument()` – รับ `OleWordProcessingOptions` และแทรก PDF เป็นอ็อบเจ็กต์ OLE.  
- `save()` – เขียนเอกสารที่แก้ไขแล้วไปยัง `outputFilePath`.  

### Step 4: (Optional) Re‑apply configuration for additional objects
หากต้องการฝัง PDF เพิ่มเติม ให้ทำซ้ำ **Step 1‑3** ด้วยเส้นทางไฟล์และหมายเลขหน้าที่ใหม่. คลาส `OleWordProcessingOptions` เดียวกันช่วยให้คุณควบคุมแต่ละอ็อบเจ็กต์แยกกัน.

## Configuring OleWordProcessingOptions (Advanced)
คุณสามารถปรับตำแหน่งเพิ่มเติม เช่น การจัดแนวอ็อบเจ็กต์หรือเพิ่มคำบรรยาย. โค้ดตัวอย่างด้านล่างทำซ้ำการกำหนดค่าพื้นฐานเพื่อความชัดเจน:
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Width of the embedded object
oleWordsOptions.setHeight(300); // Height of the embedded object
```

## Practical Applications
การฝัง PDF มีประโยชน์ในหลายสถานการณ์จริง:

1. **คู่มือเทคนิค** – แทรกแผนผังละเอียดหรือ PDF อ้างอิงโดยตรงในคู่มือ.  
2. **รายงานการเงิน** – เพิ่ม PDF ตรวจสอบเสริมโดยไม่ทำให้การไหลของรายงานหลักขาดตอน.  
3. **สัญญากฎหมาย** – แนบภาคผนวกหรือเอกสารแนบเป็นอ็อบเจ็กต์ OLE เพื่อการเข้าถึงง่ายระหว่างการตรวจสอบ.  

## Performance Considerations
เมื่อจัดการเอกสารขนาดใหญ่หรือหลายอ็อบเจ็กต์ OLE ให้คำนึงถึงเคล็ดลับต่อไปนี้:

- **ตัดเนื้อหาที่ไม่จำเป็น** – ฝังเฉพาะหน้าที่คุณต้องการจริงๆ.  
- **จัดการหน่วยความจำ** – ใช้แฟล็ก `-Xmx` ของ Java เพื่อจัดสรรพื้นที่ heap เพียงพอสำหรับไฟล์ขนาดใหญ่.  
- **อัปเดตอยู่เสมอ** – รุ่นใหม่ของ GroupDocs.Merger มักมีการปรับปรุงประสิทธิภาพ.  

## Frequently Asked Questions

**Q: OLE embedding คืออะไร?**  
A: การฝังทำให้คุณสามารถแทรกอ็อบเจ็กต์เช่น PDF ลงในเอกสาร Word เป็นลิงก์ที่รักษาฟังก์ชันเดิมไว้.

**Q: ฉันสามารถฝังอ็อบเจ็กต์ OLE หลายรายการในเอกสารเดียวได้หรือไม่?**  
A: ได้, แต่ละอ็อบเจ็กต์สามารถกำหนดค่าหน้าและขนาดต่างกันโดยใช้ `OleWordProcessingOptions` แยกกัน.

**Q: มีขีดจำกัดขนาดของไฟล์ที่ฝังหรือไม่?**  
A: ขีดจำกัดโดยทั่วไปขึ้นอยู่กับข้อจำกัดของ Word เอง, แต่ GroupDocs.Merger จัดการไฟล์ขนาดใหญ่ได้อย่างมีประสิทธิภาพ.

**Q: ฉันจะแก้ไขข้อผิดพลาดการฝังอย่างไร?**  
A: ตรวจสอบว่าเส้นทางไฟล์ถูกต้องและ JVM มีหน่วยความจำเพียงพอ. ตรวจสอบว่า PDF ต้นฉบับไม่เสียหาย.

**Q: ฉันสามารถแก้ไขอ็อบเจ็กต์ที่ฝังหลังจากแทรกได้หรือไม่?**  
A: คุณสามารถเปิดไฟล์ Word ใน Microsoft Word แล้วแก้ไขอ็อบเจ็กต์ OLE, หรือรันโค้ด Merger ใหม่ด้วยตัวเลือกที่อัปเดต.

## Additional Resources
- [เอกสาร GroupDocs.Merger](https://docs.groupdocs.com/merger/java/)
- [อ้างอิง API](https://reference.groupdocs.com/merger/java/)
- [ดาวน์โหลดเวอร์ชันล่าสุด](https://releases.groupdocs.com/merger/java/)
- [ซื้อ GroupDocs](https://purchase.groupdocs.com/buy)
- [ทดลองใช้ฟรี](https://releases.groupdocs.com/merger/java/)
- [ใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/)
- [ฟอรั่มสนับสนุน](https://forum.groupdocs.com/c/merger/)

---

**อัปเดตล่าสุด:** 2025-12-19  
**ทดสอบกับ:** GroupDocs.Merger for Java รุ่นล่าสุด  
**ผู้เขียน:** GroupDocs  

---