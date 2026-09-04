---
date: '2026-08-26'
description: เรียนรู้วิธีใช้ GroupDocs Merger เพื่อฝังวัตถุ OLE ใน PowerPoint ด้วย
  Java คู่มือแบบทีละขั้นตอนจะแสดงวิธีการฝัง PDFs, spreadsheets และอื่น ๆ
keywords:
- groupdocs merger embed ole
- embed OLE objects in PowerPoint
- Java GroupDocs Merger
- OLE embedding in Java
lastmod: '2026-08-26'
og_description: เรียนรู้วิธีใช้ GroupDocs Merger เพื่อฝังวัตถุ OLE ใน PowerPoint ด้วย
  Java ปฏิบัติตามบทเรียนสั้น ๆ นี้เพื่อเพิ่ม PDFs, Excel sheets และไฟล์อื่น ๆ ลงบนสไลด์ของคุณโดยตรง
og_image_alt: 'Tutorial: embed OLE objects in PowerPoint using GroupDocs Merger for
  Java'
og_title: GroupDocs Merger ฝังวัตถุ OLE ใน PowerPoint ด้วย Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-26'
  description: Learn how to use GroupDocs Merger to embed OLE objects in PowerPoint
    with Java. This step‑by‑step guide shows you how to embed PDFs, spreadsheets,
    and more.
  headline: GroupDocs Merger embed OLE objects in PowerPoint with Java
  type: TechArticle
- description: Learn how to use GroupDocs Merger to embed OLE objects in PowerPoint
    with Java. This step‑by‑step guide shows you how to embed PDFs, spreadsheets,
    and more.
  name: GroupDocs Merger embed OLE objects in PowerPoint with Java
  steps:
  - name: define file paths
    text: Specify absolute or relative paths for both the target PPTX and the source
      file you wish to embed. java String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_PPTX";
      // Path to source presentation file String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_PDF";
      // Path to PDF to be embedded
  - name: configure `OlePresentationOptions`
    text: OlePresentationOptions defines the visual properties and source file for
      the OLE object to be embedded. java import com.groupdocs.merger.domain.options.OlePresentationOptions;
      int pageNumber = 1; // Page number for the OLE object int x = 100; // X position
      on slide int y = 200; // Y position on slid
  - name: embed the OLE object
    text: addOleObject inserts the configured OLE object into the specified slide
      of the presentation. java import com.groupdocs.merger.domain.options.OlePresentationOptions;
      try (Merger merger = new Merger(filePath)) { // Add embedded document as an
      OLE object merger.addOleObject(oleOptions); // Save the mod
  type: HowTo
- questions:
  - answer: PDFs, Excel workbooks, Word documents, PowerPoint files, and many other
      Office formats are supported.
    question: What file formats can be embedded using OLE in PowerPoint?
  - answer: Insert the OLE object on the Slide Master; all slides that inherit from
      that master will display it.
    question: How do I make the embedded object appear on every slide?
  - answer: Yes. Call `addOleObject` again with the same coordinates; the new file
      overwrites the previous one.
    question: Can I replace an existing OLE object without recreating the whole slide?
  - answer: A trial version is available for evaluation; a commercial license is required
      for production deployments.
    question: Is GroupDocs.Merger free to use?
  - answer: Incorrect file paths, unsupported document types, and excessively large
      embedded files that degrade performance.
    question: What are common pitfalls when embedding OLE objects?
  type: FAQPage
tags:
- embed OLE
- GroupDocs Merger
- Java PowerPoint
- OLE objects
- presentation automation
title: GroupDocs Merger ฝังวัตถุ OLE ใน PowerPoint ด้วย Java
type: docs
url: /th/java/document-import/embed-ole-object-ppt-java-groupdocs-merger/
weight: 1
---

# GroupDocs Merger ฝังวัตถุ OLE ใน PowerPoint ด้วย Java

ในบทแนะนำนี้คุณจะได้เรียนรู้วิธีการ **groupdocs merger embed ole** วัตถุลงในสไลด์ PowerPoint ด้วย Java. เมื่อจบคู่มือคุณจะสามารถแทรกไฟล์ PDF, แฟ้ม Excel, เอกสาร Word และไฟล์ที่รองรับอื่น ๆ ลงในงานนำเสนอของคุณ ทำให้สไลด์ของคุณเป็นอิสระและมีความโต้ตอบมากขึ้น.

## คำตอบอย่างรวดเร็ว
- **What is OLE?** Object Linking and Embedding ให้คุณแทรกไฟล์ประเภทอื่นภายในสไลด์ PowerPoint.  
- **Which library helps?** GroupDocs.Merger for Java มี API ที่ง่ายต่อการเพิ่มวัตถุ OLE.  
- **Do I need a license?** ใบอนุญาตชั่วคราวใช้ได้สำหรับการประเมิน; ต้องมีใบอนุญาตเต็มสำหรับการใช้งานจริง.  
- **Supported file types?** PDF, แฟ้ม Excel, เอกสาร Word, และรูปแบบอื่น ๆ อีกหลายประเภท.  
- **How long does it take?** ด้วยการตั้งค่า Maven/Gradle โค้ดหลักสามารถเขียนได้ภายในไม่ถึง 10 นาที.

## การฝัง OLE ใน PowerPoint คืออะไร

Object Linking and Embedding (OLE) ทำให้สไลด์ PowerPoint สามารถบรรจุการแสดงผลแบบเรียลไทม์ของเอกสารอื่นได้ เมื่อคุณดับเบิลคลิกวัตถุที่ฝังไว้ระหว่างการนำเสนอ ไฟล์ต้นฉบับจะเปิดในแอปพลิเคชันดั้งเดิมของมัน ทำให้ผู้ชมเข้าถึงข้อมูลโดยละเอียดได้ทันทีโดยไม่ต้องออกจากสไลด์เด็ค.

## ทำไมต้องฝังวัตถุ OLE ใน PowerPoint?

การฝังวัตถุ OLE จะรวมไฟล์สนับสนุนไว้ในงานนำเสนอเดียว ทำให้ผู้ชมสามารถเข้าถึงเนื้อหาเดิมได้โดยไม่ต้องออกจากสไลด์เด็ค วิธีนี้ช่วยรักษาการจัดรูปแบบ ลดความเสี่ยงของไฟล์หาย และทำให้การกระจายงานง่ายขึ้น ทำให้งานนำเสนอมีความน่าเชื่อถือและเป็นมืออาชีพมากขึ้น.

- **Keep all resources in one file** – ไม่จำเป็นต้องส่ง PDF หรือสเปรดชีตแยกต่างหาก.  
- **Maintain data fidelity** – ไฟล์ที่ฝังจะคงรูปแบบและฟังก์ชันเดิมไว้.  
- **Improve audience engagement** – ผู้ชมสามารถสำรวจแผนภูมิ ตาราง หรือสัญญาได้ทันที.  
- **Streamline version control** – PPTX ไฟล์เดียวเก็บวัสดุสนับสนุนทั้งหมด ลดความเสี่ยงของไฟล์ที่ไม่ตรงกัน.  

ประโยชน์เชิงปริมาณ: **GroupDocs Merger รองรับการฝังวัตถุ OLE จากไฟล์รูปแบบกว่า 30+ ประเภทและสามารถจัดการไฟล์ต้นฉบับขนาดสูงสุด 500 MB โดยไม่ทำให้การทำงานช้าลงอย่างเห็นได้ชัด**, ทำให้การเปลี่ยนสไลด์เป็นไปอย่างราบรื่นแม้กับเอกสารขนาดใหญ่.

## ควรใช้การฝัง OLE เมื่อใด

ใช้การฝัง OLE เมื่อใดก็ได้ที่คุณต้องการให้ข้อมูลเชิงลึกและโต้ตอบที่เสริมเนื้อหาในสไลด์ มันเหมาะสำหรับการแนบรายงานเต็ม, แผ่นข้อมูล, หรือเอกสารที่แก้ไขได้ที่ผู้ชมอาจต้องการสำรวจโดยตรงจากงานนำเสนอ เพื่อเพิ่มความชัดเจนและการมีส่วนร่วม.

1. **Business reports** – แนบ PDF เต็มรูปแบบเพื่อให้ผู้บริหารเปิดได้โดยตรงจากสไลด์.  
2. **Educational material** – ให้แผ่นงานหรือ ตารางข้อมูลที่นักเรียนสามารถสำรวจระหว่างการบรรยาย.  
3. **Project updates** – วางไฟล์ Excel แผนภูมิ Gantt บนสไลด์อัปเดตสถานะเพื่ออ้างอิงอย่างรวดเร็ว.  

การเข้าใจ **how to embed ole** ในสถานการณ์เหล่านี้ช่วยให้คุณทำให้งานนำเสนอเป็นอิสระและเป็นมืออาชีพ.

## ข้อกำหนดเบื้องต้น

- **Java Development Kit (JDK) 8+** – ตรวจสอบให้ `java -version` แสดงผลเป็น 1.8 หรือสูงกว่า.  
- **IDE** – IntelliJ IDEA, Eclipse หรือโปรแกรมแก้ไขใด ๆ ที่คุณชอบ.  
- **Maven or Gradle** – สำหรับการจัดการ dependencies.  
- **Basic Java knowledge** – คุณควรคุ้นเคยกับ `try‑with‑resources` และโค้ดเชิงวัตถุ.

## การตั้งค่า GroupDocs.Merger สำหรับ Java

### ข้อมูลการติดตั้ง

เพิ่มไลบรารี GroupDocs.Merger ไปยังโปรเจกต์ของคุณ:

**Maven:**
```java
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```
```

**Gradle:**
```java
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```
```

**ดาวน์โหลดโดยตรง:**  
ดาวน์โหลดเวอร์ชันล่าสุดจาก [การปล่อย GroupDocs.Merger สำหรับ Java](https://releases.groupdocs.com/merger/java/).

### การรับใบอนุญาต

รับใบอนุญาตชั่วคราวสำหรับการประเมินโดยไม่มีข้อจำกัดที่ [temporary license page](https://purchase.groupdocs.com/temporary-license/). สำหรับการใช้งานจริง ให้ซื้อใบอนุญาตจาก [GroupDocs website](https://purchase.groupdocs.com/buy).

### การเริ่มต้นพื้นฐาน

Merger เป็นคลาสหลักที่ให้เมธอดสำหรับจัดการงานนำเสนอ รวมถึงการเพิ่มวัตถุ OLE.
```java
```java
import com.groupdocs.merger.Merger;

public class PresentationMerger {
    public static void main(String[] args) {
        // Initialize Merger with the path to your document
        try (Merger merger = new Merger("path/to/your/presentation.pptx")) {
            System.out.println("Merger initialized successfully.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```
```

## วิธีการฝังวัตถุ OLE ใน PowerPoint ด้วย GroupDocs Merger สำหรับ Java

เพื่อฝังวัตถุ OLE ให้โหลดไฟล์ PPTX เป้าหมายด้วย Merger ตั้งค่า OlePresentationOptions ด้วยไฟล์ต้นฉบับและเลย์เอาต์ที่ต้องการ แล้วเรียกใช้ addOleObject กระบวนการสั้น ๆ สามขั้นตอนนี้จะใส่วัตถุลงในสไลด์ที่เลือกและบันทึกงานนำเสนอที่อัปเดต คุณยังสามารถปรับตำแหน่งและขนาดให้เหมาะกับการออกแบบสไลด์ได้.

### คำตอบโดยตรง
โหลดไฟล์ PowerPoint ของคุณด้วย `new Merger("presentation.pptx")` ตั้งค่าอินสแตนซ์ `OlePresentationOptions` ที่ชี้ไปยังไฟล์ต้นฉบับ และเรียก `addOleObject` พร้อมดัชนีสไลด์และพิกัดที่ต้องการ รูปแบบสามขั้นตอนนี้จะใส่วัตถุ OLE ในหนึ่งการเรียก API.

### ขั้นตอน 1: กำหนดเส้นทางไฟล์

ระบุเส้นทางแบบ absolute หรือ relative สำหรับทั้งไฟล์ PPTX เป้าหมายและไฟล์ต้นฉบับที่ต้องการฝัง.
```java
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_PPTX"; // Path to source presentation file
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_PDF"; // Path to PDF to be embedded
```
```

### ขั้นตอน 2: ตั้งค่า `OlePresentationOptions`

OlePresentationOptions กำหนดคุณสมบัติการแสดงผลและไฟล์ต้นฉบับสำหรับวัตถุ OLE ที่จะฝัง.
```java
```java
import com.groupdocs.merger.domain.options.OlePresentationOptions;

int pageNumber = 1; // Page number for the OLE object
int x = 100; // X position on slide
int y = 200; // Y position on slide
int width = 300; // Width of embedded object
int height = 400; // Height of embedded object

OlePresentationOptions oleOptions = new OlePresentationOptions(embeddedFilePath, pageNumber);
oleOptions.setX(x);
oleOptions.setY(y);
oleOptions.setWidth(width);
oleOptions.setHeight(height);
```
```

### ขั้นตอน 3: ฝังวัตถุ OLE

addOleObject จะใส่วัตถุ OLE ที่กำหนดไว้ลงในสไลด์ที่ระบุของงานนำเสนอ.
```java
```java
import com.groupdocs.merger.domain.options.OlePresentationOptions;

try (Merger merger = new Merger(filePath)) {
    // Add embedded document as an OLE object
    merger.addOleObject(oleOptions);
    
    // Save the modified presentation
    String outputPath = "YOUR_OUTPUT_DIRECTORY/modified_presentation.pptx";
    merger.save(outputPath);
    System.out.println("OLE Object added successfully.");
} catch (Exception e) {
    e.printStackTrace();
}
```
```

## ปัญหาที่พบบ่อยและวิธีแก้

- **File‑path accuracy:** ตรวจสอบให้แน่ใจว่าแต่ละเส้นทางชี้ไปยังไฟล์ที่มีอยู่และสามารถอ่านได้.  
- **Supported formats:** PowerPoint รองรับประเภท OLE บางประเภทเท่านั้น; PDF, Excel, และ Word เป็นตัวเลือกที่ปลอดภัย.  
- **Memory usage:** ใช้ `try‑with‑resources` (ตามที่แสดง) เพื่อให้แน่ใจว่าอินสแตนซ์ `Merger` ถูกปิดอย่างรวดเร็ว.  
- **Large embedded files:** หาก PPTX ทำงานช้า ให้บีบอัด PDF ต้นฉบับหรือแยกเป็นหน้าขนาดเล็กก่อนฝัง.  

## พิจารณาด้านประสิทธิภาพ

- **Optimize file sizes:** PDF ขนาดใหญ่สามารถทำให้การโหลดสไลด์ช้า; ควรบีบอัดก่อน.  
- **Java memory management:** รูปแบบ `try‑with‑resources` ที่แสดงด้านบนจะปล่อยทรัพยากรเนทีฟโดยอัตโนมัติ.  
- **Batch processing:** เมื่อฝังวัตถุลงในงานนำเสนอหลายไฟล์ ให้วนลูปผ่านรายการไฟล์และใช้อินสแตนซ์ `Merger` เดียวซ้ำเมื่อเป็นไปได้เพื่อลดภาระ.  

## คำถามที่พบบ่อย

**Q: รูปแบบไฟล์ใดบ้างที่สามารถฝังด้วย OLE ใน PowerPoint?**  
A: รองรับ PDF, แฟ้ม Excel, เอกสาร Word, ไฟล์ PowerPoint, และรูปแบบ Office อื่น ๆ อีกหลายประเภท.

**Q: จะทำอย่างไรให้วัตถุที่ฝังปรากฏบนทุกสไลด์?**  
A: แทรกวัตถุ OLE บน Slide Master; สไลด์ทั้งหมดที่สืบทอดจากมาสเตอร์นั้นจะแสดงวัตถุนี้.

**Q: ฉันสามารถแทนที่วัตถุ OLE ที่มีอยู่โดยไม่ต้องสร้างสไลด์ใหม่ทั้งหมดได้หรือไม่?**  
A: ได้. เรียก `addOleObject` อีกครั้งด้วยพิกัดเดียวกัน; ไฟล์ใหม่จะเขียนทับไฟล์เดิม.

**Q: GroupDocs.Merger ใช้ได้ฟรีหรือไม่?**  
A: มีเวอร์ชันทดลองให้ประเมินผล; จำเป็นต้องมีใบอนุญาตเชิงพาณิชย์สำหรับการใช้งานจริง.

**Q: ข้อผิดพลาดทั่วไปเมื่อฝังวัตถุ OLE มีอะไรบ้าง?**  
A: เส้นทางไฟล์ไม่ถูกต้อง, ประเภทเอกสารที่ไม่รองรับ, และไฟล์ที่ฝังขนาดใหญ่เกินไปซึ่งทำให้ประสิทธิภาพลดลง.

## แหล่งข้อมูลเพิ่มเติม

- [เอกสาร GroupDocs.Merger](https://docs.groupdocs.com/merger/java/)
- [อ้างอิง API](https://reference.groupdocs.com/merger/java/)
- [ดาวน์โหลด GroupDocs.Merger](https://releases.groupdocs.com/merger/java/)
- [ซื้อใบอนุญาต](https://purchase.groupdocs.com/buy)
- [ทดลองใช้งานฟรี](https://releases.groupdocs.com/merger/java/)
- [ใบอนุญาตชั่วคราว](https://purchase.groupdocs.com/temporary-license/)
- [ฟอรั่มสนับสนุน](https://forum.groupdocs.com/c/merger/)

---

**อัปเดตล่าสุด:** 2026-08-26  
**ทดสอบด้วย:** GroupDocs.Merger latest version (Java)  
**ผู้เขียน:** GroupDocs  

## บทแนะนำที่เกี่ยวข้อง

- [วิธีฝัง pdf ใน word ด้วย GroupDocs.Merger สำหรับ Java – คู่มือครบถ้วน](/merger/java/document-import/embed-ole-objects-word-documents-groupdocs-java/)
- [ฝังรูปภาพเป็นวัตถุ OLE ใน Java ด้วย GroupDocs.Merger: คู่มือครบถ้วน](/merger/java/image-operations/embed-images-ole-java-groupdocs-merger/)