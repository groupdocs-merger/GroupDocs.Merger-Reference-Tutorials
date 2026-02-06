---
date: '2026-02-06'
description: เรียนรู้วิธีแยกไฟล์ข้อความตามบรรทัดโดยใช้ GroupDocs.Merger สำหรับ Java
  คู่มือขั้นตอนต่อขั้นตอนสำหรับการแยกเอกสารอย่างมีประสิทธิภาพในโครงการ Java.
keywords:
- split text file line intervals Java
- document splitting GroupDocs.Merger
- Java document manipulation
title: วิธีแยกไฟล์ตามบรรทัดด้วย GroupDocs.Merger สำหรับ Java
type: docs
url: /th/java/document-splitting/split-text-file-line-intervals-groupdocs-merger-java/
weight: 1
---

# วิธีแยกไฟล์ตามบรรทัดโดยใช้ GroupDocs.Merger สำหรับ Java

การแบ่งไฟล์ข้อความขนาดใหญ่เป็นส่วนย่อยที่จัดการได้ง่ายขึ้น **ตามบรรทัด** เป็นความต้องการทั่วไปเมื่อคุณ ‑ เช่น ‑ ประมวลผลบันทึก, นำเข้าข้อมูลเป็นชุด, หรือจัดระเบียบรายงานยาว ในบทแนะนำนี้คุณจะได้เรียนรู้วิธี **แยกไฟล์ตามบรรทัด** ด้วย GroupDocs.Merger สำหรับ Java, เหตุผลที่วิธีนี้ช่วยประหยัดเวลา, และรับตัวอย่างโค้ดที่พร้อมใช้งาน

## คำตอบสั้น

- **What does “split file by lines” mean?** มันสร้างไฟล์ข้อความแยกต่างหากที่แต่ละไฟล์มีช่วงหมายเลขบรรทัดที่กำหนดจากเอกสารต้นฉบับ.  
- **Which library handles the split?** GroupDocs.Merger for Java ให้ API อย่างง่ายสำหรับการแยกตามช่วงบรรทัด.  
- **Do I need a license?** การทดลองใช้ฟรีทำงานสำหรับการทดสอบ; จำเป็นต้องมีลิขสิทธิ์ถาวรสำหรับการใช้งานในสภาพแวดล้อมการผลิต.  
- **Can I split by character count instead?** ไม่ได้โดยตรง—ใช้ขั้นตอนการเตรียมข้อมูลล่วงหน้าเพื่อปรับรูปแบบไฟล์ก่อนการแยก.  
- **What Java version is supported?** รองรับ Java 8+ runtime ใดก็ได้.

## “split file by lines” คืออะไร?

การแยกไฟล์ตามบรรทัดหมายถึงการนำเอกสารข้อความเดียวมาหารเป็นหลายไฟล์, แต่ละไฟล์มีช่วงบรรทัดต่อเนื่องที่กำหนด (เช่น บรรทัด 1‑3, 4‑6, เป็นต้น). เทคนิคนี้เหมาะสำหรับการประมวลผลเป็นชุด, การวิเคราะห์แบบขนาน, หรือเพียงแค่เพิ่มความอ่านง่าย.

## ทำไมต้องใช้ GroupDocs.Merger สำหรับ Java?

GroupDocs.Merger แยกการทำงานระดับต่ำของ file‑I/O ออก, ทำให้คุณโฟกัสที่ตรรกะธุรกิจ. มันจัดการไฟล์ขนาดใหญ่ได้อย่างมีประสิทธิภาพ, รองรับรูปแบบเอกสารหลายประเภท, และมี API ที่สะอาดและไหลลื่นซึ่งรวมเข้ากับการสร้างด้วย Maven หรือ Gradle ได้อย่างลงตัว.

## ข้อกำหนดเบื้องต้น

- **Java Development Kit (JDK) 8 or higher** – ตรวจสอบว่า `java` และ `javac` อยู่ใน PATH ของคุณ.  
- **GroupDocs.Merger for Java** – เพิ่มไลบรารีผ่าน Maven, Gradle หรือดาวน์โหลดโดยตรง.  
- **Basic Java knowledge** – คุณควรคุ้นเคยกับคลาส, เมธอด, และการจัดการข้อยกเว้น.

## การตั้งค่า GroupDocs.Merger สำหรับ Java

เพิ่มไลบรารีลงในโปรเจคของคุณโดยใช้หนึ่งในวิธีต่อไปนี้.

**Maven** – วาง dependency นี้ลงใน `pom.xml` ของคุณ:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle** – เพิ่มบรรทัดต่อไปนี้ใน `build.gradle`:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Direct Download** – คุณสามารถดาวน์โหลด JAR จากหน้า release อย่างเป็นทางการได้เช่นกัน: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### การรับลิขสิทธิ์

เริ่มต้นด้วยการทดลองใช้ฟรีเพื่อสำรวจ API. สำหรับงานในสภาพแวดล้อมการผลิต, รับลิขสิทธิ์ชั่วคราวหรือเต็มจากพอร์ทัลของ GroupDocs.

## วิธีแยกไฟล์ข้อความตามบรรทัด (การทำงานด้วย Java)

ด้านล่างเป็นขั้นตอนสั้น ๆ ทีละขั้นตอน. แต่ละขั้นจะอธิบายด้วยภาษาง่าย ๆ ก่อนบล็อกโค้ด, เพื่อให้คุณเข้าใจว่ากำลังเกิดอะไรขึ้น.

### ขั้นตอน 1: กำหนดเส้นทางแหล่งที่มาและผลลัพธ์

แรก, บอกไลบรารีว่าฟไฟล์ต้นฉบับของคุณอยู่ที่ไหนและส่วนที่แยกควรเขียนไปที่ไหน.
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.txt";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToLineRanges-" + Paths.get(filePath).getFileName().toString();
```

### ขั้นตอน 2: กำหนดค่าตัวเลือกการแยก

สร้างอินสแตนซ์ `TextSplitOptions` ที่อธิบายช่วงบรรทัดที่คุณต้องการ. อาร์เรย์ `new int[] { 3, 6 }` บอก API ให้ตัดหลังบรรทัด 3 และบรรทัด 6, ผลลัพธ์เป็นสองส่วน: บรรทัด 1‑3 และบรรทัด 4‑6.
```java
TextSplitOptions splitOptions = new TextSplitOptions(filePathOut, TextSplitMode.Interval, new int[] { 3, 6 });
```

### ขั้นตอน 3: เริ่มต้น Merger และดำเนินการแยก

สุดท้าย, สร้างอินสแตนซ์ `Merger` ด้วยไฟล์ต้นฉบับและเรียก `split()` พร้อมตัวเลือกที่คุณสร้างขึ้น.
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

เท่านี้! หลังจากการเรียกเสร็จสิ้น, คุณจะพบไฟล์ใหม่สองไฟล์ใน `YOUR_OUTPUT_DIRECTORY`, แต่ละไฟล์มีช่วงบรรทัดที่ระบุ.

## การประยุกต์ใช้จริง (ทำไมจึงสำคัญ)

1. **Data Processing Pipelines** – แบ่งไฟล์บันทึกขนาดมหาศาลเป็นชิ้นย่อยเพื่อการพาร์สแบบขนาน.  
2. **Document Management** – แปลงรายงานเดียวเป็นไฟล์ระดับบทเพื่อการแจกจ่ายที่ง่ายขึ้น.  
3. **Content Segmentation** – เตรียมส่วนของบทความขนาดใหญ่สำหรับแพลตฟอร์มการเผยแพร่ที่เจาะจง.

## เคล็ดลับประสิทธิภาพ

- **Stream‑line I/O** – ควรใช้ `Files.newBufferedReader` เมื่อจัดการไฟล์ขนาดใหญ่มากเพื่อรักษาการใช้หน่วยความจำน้อย.  
- **Close Resources** – แม้ว่า GroupDocs.Merger จะจัดการทำความสะอาดส่วนใหญ่, การปิดสตรีมที่กำหนดเองอย่างชัดเจนจะป้องกันการรั่วไหล.  
- **Monitor Memory** – การแยกไฟล์ขนาดกิกะไบต์อาจใช้หน่วยความจำมาก; จัดสรร heap เพียงพอ (`-Xmx2g` หรือสูงกว่า) หากจำเป็น.

## ปัญหาทั่วไปและวิธีแก้

| ปัญหา | สาเหตุ | วิธีแก้ |
|-------|--------|--------|
| `OutOfMemoryError` | ไฟล์ต้นฉบับขนาดใหญ่เกินขนาด heap. | เพิ่มขนาด heap ของ JVM หรือแยกโดยใช้ช่วงที่เล็กลง. |
| `FileNotFoundException` | เส้นทางไม่ถูกต้องหรือไม่มีสิทธิ์. | ตรวจสอบว่า `filePath` และ `filePathOut` เป็นแบบ absolute และสามารถเขียนได้. |
| Empty output files | อาร์เรย์ช่วงไม่ครอบคลุมเอกสารทั้งหมด. | ตรวจสอบว่าช่วงสุดท้ายสิ้นสุดที่หรือต่อจากจำนวนบรรทัดทั้งหมด. |

## ส่วนคำถามที่พบบ่อย

**Q: Can I split files based on character count instead of line numbers?**  
A: ปัจจุบัน GroupDocs.Merger สำหรับ Java มุ่งเน้นที่ช่วงบรรทัด. อย่างไรก็ตาม, คุณสามารถทำการเตรียมข้อความล่วงหน้าให้ตรงกับจำนวนอักขระต่อบรรทัดที่ต้องการก่อนใช้ฟีเจอร์นี้.

**Q: Is there a limit to how many intervals I can specify for splitting?**  
A: ไม่มีข้อจำกัดเฉพาะในไลบรารีเอง; อย่างไรก็ตาม, ประสิทธิภาพอาจลดลงเมื่อมีจำนวนการแยกมากเกินไปเนื่องจากความต้องการการประมวลผลที่เพิ่มขึ้น.

**Q: How do I handle errors during file splitting?**  
A: ใช้บล็อก try‑catch รอบโค้ดของคุณเพื่อจับและจัดการข้อยกเว้นอย่างมีประสิทธิภาพ. GroupDocs.Merger ให้ข้อความข้อผิดพลาดที่ละเอียดซึ่งช่วยในการแก้ไขปัญหา.

**Q: Does the library support other text‑based formats such as CSV or TSV?**  
A: ใช่, เนื่องจาก CSV และ TSV เป็นไฟล์ข้อความธรรมดา, ตรรกะช่วงบรรทัดเดียวกันใช้ได้. เพียงแค่จัดการพวกมันเป็นไฟล์ `.txt` ใน API.

**Q: Can I automate splitting for multiple files in a folder?**  
A: แน่นอน. ห่อหุ้มตรรกะข้างต้นในลูปที่วนผ่าน `Files.list(Paths.get("folder"))` และใช้ `TextSplitOptions` เดียวกันกับแต่ละไฟล์.

## แหล่งข้อมูล

- **Documentation:** [GroupDocs.Merger for Java Documentation](https://docs.groupdocs.com/merger/java/)  
- **API Reference:** [GroupDocs API Reference](https://reference.groupdocs.com/merger/java/)  
- **Download:** [Latest Releases](https://releases.groupdocs.com/merger/java/)  
- **Purchase and Licensing:** [Buy GroupDocs](https://purchase.groupdocs.com/buy)  
- **Free Trial:** [GroupDocs Free Trial](https://releases.groupdocs.com/merger/java/)  
- **Temporary License:** [Obtain Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Support Forum:** [GroupDocs Support](https://forum.groupdocs.com/c/merger)

---

**อัปเดตล่าสุด:** 2026-02-06  
**ทดสอบด้วย:** GroupDocs.Merger 23.12 for Java  
**ผู้เขียน:** GroupDocs