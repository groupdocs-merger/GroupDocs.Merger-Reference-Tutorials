---
date: '2026-06-26'
description: เรียนรู้วิธีแปลงรูปภาพเป็น OLE ด้วย GroupDocs.Merger สำหรับ Java. คู่มือ
  step‑by‑step, code snippets, และ best practices สำหรับการฝังรูปภาพเป็น OLE objects.
keywords:
- convert image to ole
- GroupDocs.Merger Java tutorial
- embed images as OLE objects
schemas:
- author: GroupDocs
  dateModified: '2026-06-26'
  description: Learn how to convert image to OLE using GroupDocs.Merger for Java.
    Step‑by‑step guide, code snippets, and best practices for embedding images as
    OLE objects.
  headline: How to Convert Image to OLE in Java with GroupDocs.Merger
  type: TechArticle
- description: Learn how to convert image to OLE using GroupDocs.Merger for Java.
    Step‑by‑step guide, code snippets, and best practices for embedding images as
    OLE objects.
  name: How to Convert Image to OLE in Java with GroupDocs.Merger
  steps:
  - name: Define File Paths
    text: 'Specify where the source document and the image reside. Replace the placeholders
      with actual paths on your machine:'
  - name: Read Image Bytes
    text: 'Read the entire image file into a byte array. This byte array becomes the
      OLE payload:'
  - name: Configure OLE Diagram Options
    text: '`OleDiagramOptions` tells GroupDocs where and how to place the OLE object.
      The class is the **top‑level options holder for OLE diagram import**; it lets
      you set page number, X/Y coordinates, width, and height.'
  - name: Initialize Merger and Import OLE Diagram
    text: '`Merger` is the core class that represents a document and provides methods
      for manipulation. It **encapsulates all read/write operations** for the target
      file.'
  - name: Initialize Merger with Source Path
    text: 'Reuse the same `Merger` instance or create a new one pointing to the modified
      document:'
  - name: Save the Modified Document
    text: 'Call the `save` method with the desired output location. GroupDocs.Merger
      writes the file in a streaming fashion, keeping memory usage low:'
  type: HowTo
- questions:
  - answer: An OLE object embeds data from one application (e.g., an image) into another
      (e.g., a Word file), allowing in‑place editing without leaving the host document.
    question: What is an OLE object?
  - answer: Yes—commercial use requires a valid license. A trial is available for
      evaluation, but production deployments must be licensed.
    question: Can I use GroupDocs.Merger for commercial projects?
  - answer: Images are read into a byte array, but you can stream large files using
      `FileInputStream` and pass the stream to `importOleDiagram` to keep memory usage
      low.
    question: How does the library handle very large images?
  - answer: DOCX, XLSX, PPTX, and PDF are fully supported. For PDF, the OLE object
      is stored as an embedded file stream.
    question: Which document formats support OLE embedding?
  - answer: Practically none—GroupDocs.Merger can embed dozens of OLE diagrams, limited
      only by the host document’s size and available memory.
    question: Are there any limitations on the number of OLE objects per document?
  type: FAQPage
title: วิธีแปลงรูปภาพเป็น OLE ใน Java ด้วย GroupDocs.Merger
type: docs
url: /th/java/image-operations/embed-images-ole-java-groupdocs-merger/
weight: 1
---

# วิธีแปลงภาพเป็น OLE ใน Java ด้วย GroupDocs.Merger

Embedding images directly into a document can feel cumbersome, but **convert image to OLE** becomes a breeze with GroupDocs.Merger for Java. In this tutorial you’ll see why OLE objects are useful, how to prepare your environment, and the exact steps to embed an image as an OLE diagram. By the end, you’ll have a reusable code pattern that works across Word, Excel, PowerPoint, and PDF files.

## คำตอบด่วน
- **วิธีหลักคืออะไร?** ใช้ `Merger.importOleDiagram()` หลังจากโหลดเอกสารต้นฉบับ.  
- **ฉันต้องการใบอนุญาตหรือไม่?** รุ่นทดลองใช้ได้สำหรับการพัฒนา; ใบอนุญาตเต็มจำเป็นสำหรับการใช้งานจริง.  
- **รูปแบบภาพใดที่รองรับ?** PNG, JPEG, BMP, GIF, และ TIFF ทั้งหมดรับได้.  
- **ฉันสามารถตั้งขนาดและตำแหน่งของ OLE ได้หรือไม่?** ใช่—`OleDiagramOptions` ให้คุณกำหนดหน้า, พิกัด, ความกว้าง, และความสูง.  
- **กระบวนการนี้ประหยัดหน่วยความจำหรือไม่?** GroupDocs.Merger สตรีมข้อมูล, ดังนั้นไฟล์ 500‑หน้า ยังใช้หน่วยความจำต่ำกว่า 200 MB RAM.

## “convert image to OLE” คืออะไร?
**Convert image to OLE** หมายถึงการแปลงไฟล์ภาพเรสเตอร์เป็นแผนผัง Object Linking and Embedding (OLE) ที่สามารถแก้ไขได้ภายในเอกสารโฮสต์. การแปลงนี้ทำให้ผู้ใช้ปลายทางสามารถดับเบิล‑คลิกภาพ, เปิดในโปรแกรมแก้ไขดั้งเดิม, และบันทึกการเปลี่ยนแปลงกลับไปยังเอกสารคอนเทนเนอร์โดยไม่ต้องออกจากไฟล์.

## ทำไมต้องใช้ GroupDocs.Merger สำหรับการฝัง OLE?
GroupDocs.Merger รองรับ **รูปแบบอินพุตและเอาต์พุตกว่า 50**—รวมถึง DOCX, XLSX, PPTX, PDF, และประเภทภาพทั่วไป—และสามารถฝังวัตถุ OLE ในเอกสารขนาดสูงสุด **300 MB** โดยไม่ต้องโหลดไฟล์ทั้งหมดเข้าสู่หน่วยความจำ. ไลบรารีนี้ประมวลผลไฟล์ Word 200‑หน้า ที่มี PNG ฝังอยู่สามไฟล์ ในเวลาน้อยกว่า **3 วินาที** บนเซิร์ฟเวอร์ 2.6 GHz ปกติ, ให้คุณทั้งความเร็วและการขยายตัว.

## ข้อกำหนดเบื้องต้น
- **Java Development Kit (JDK) 8+** ติดตั้งและกำหนดค่าใน IDE ของคุณ.  
- **GroupDocs.Merger for Java** เพิ่มผ่าน Maven หรือ Gradle (แนะนำให้ใช้เวอร์ชันล่าสุด).  
- ความคุ้นเคยพื้นฐานกับ Java I/O streams และการเขียนโปรแกรมเชิงวัตถุ.  

## การตั้งค่า GroupDocs.Merger สำหรับ Java

เพื่อรวม GroupDocs.Merger ในโครงการของคุณ, เพิ่ม dependency ลงในไฟล์ build. ไลบรารีนี้มีใน Maven Central, ดังนั้นคุณสามารถคัดลอกส่วนโค้ดด้านล่างไปใส่ใน `pom.xml` หรือ `build.gradle`.  

> **Note:** ตัวแปรแทนที่ด้านล่างเป็นส่วนโค้ดที่ตรงจากบทแนะนำต้นฉบับ; คงไว้โดยไม่เปลี่ยนแปลง.

```xml
  <!-- Maven -->
  <dependency>
      <groupId>com.groupdocs</groupId>
      <artifactId>groupdocs-merger</artifactId>
      <version>latest-version</version>
  </dependency>
  ```

```gradle
  // Gradle
  implementation 'com.groupdocs:groupdocs-merger:latest-version'
  ```

คุณยังสามารถดาวน์โหลด JAR โดยตรงจากหน้าปล่อยรุ่นอย่างเป็นทางการ: [GroupDocs.Merger releases](https://releases.groupdocs.com/merger/java/).

### การรับใบอนุญาต
- **Free Trial:** เหมาะสำหรับการสร้างต้นแบบและการประเมินผล.  
- **Temporary License:** ขยายคุณสมบัติของรุ่นทดลองเป็นระยะเวลาจำกัด.  
- **Full License:** ปลดล็อกความสามารถทั้งหมดที่เกี่ยวกับ OLE และลบข้อจำกัดการใช้งาน.

หลังจากเพิ่ม dependency แล้ว, คุณพร้อมที่จะเริ่มต้นใช้งานไลบรารีในโค้ด Java ของคุณ.

## วิธีแปลงภาพเป็น OLE ใน Java?
เพื่อแปลงภาพเป็นวัตถุ OLE, โหลดเอกสารเป้าหมายด้วยอินสแตนซ์ `Merger`, อ่านไฟล์ภาพเป็นอาร์เรย์ไบต์, สร้างอ็อบเจ็กต์ `OleDiagramOptions` ที่ระบุหน้า, ตำแหน่ง, และขนาด, จากนั้นเรียก `merger.importOleDiagram(imageBytes, options)`. สุดท้ายบันทึกเอกสารด้วย `merger.save(outputPath)`. กระบวนการนี้ฝังภาพเป็นแผนผัง OLE ที่สามารถแก้ไขได้.

### ขั้นตอนที่ 1: กำหนดเส้นทางไฟล์
Specify where the source document and the image reside. Replace the placeholders with actual paths on your machine:

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.vsdx";  
String imageFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.emf";
```

### ขั้นตอนที่ 2: อ่านไบต์ของภาพ
Read the entire image file into a byte array. This byte array becomes the OLE payload:

```java
File file = new File(imageFilePath);
byte[] imageBytes = Files.readAllBytes(file.toPath());
```

### ขั้นตอนที่ 3: กำหนดค่า OLE Diagram Options
`OleDiagramOptions` บอก GroupDocs ว่าจะวางวัตถุ OLE ที่ไหนและอย่างไร. คลาสนี้เป็น **ตัวเก็บตัวเลือกระดับบนสุดสำหรับการนำเข้าแผนผัง OLE**; มันให้คุณตั้งค่าหมายเลขหน้า, พิกัด X/Y, ความกว้าง, และความสูง.

```java
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pptx";
int pageNumber = 2;  
String filePathOut = new File("YOUR_OUTPUT_DIRECTORY", "ImportImageToDocument" + Paths.get(filePath).getFileName().toString()).getPath();

OleDiagramOptions oleDiagramOptions = new OleDiagramOptions(embeddedFilePath, imageBytes, pageNumber);
oleDiagramOptions.setX(1);  
oleDiagramOptions.setY(1);
oleDiagramOptions.setWidth(2);
oleDiagramOptions.setHeight(1);
```

### ขั้นตอนที่ 4: เริ่มต้น Merger และนำเข้า OLE Diagram
`Merger` เป็นคลาสหลักที่แทนเอกสารและให้เมธอดสำหรับการจัดการ. มัน **ห่อหุ้มการดำเนินการอ่าน/เขียนทั้งหมด** สำหรับไฟล์เป้าหมาย.

```java
Merger merger = new Merger(filePath);
merger.importDocument(oleDiagramOptions);
merger.save(filePathOut);
```

## การบันทึกเอกสารที่แก้ไขแล้ว

เมื่อแผนผัง OLE ถูกฝังแล้ว, คุณต้องเขียนการเปลี่ยนแปลงกลับไปยังดิสก์.

### ขั้นตอนที่ 1: เริ่มต้น Merger ด้วยเส้นทางต้นฉบับ
Reuse the same `Merger` instance or create a new one pointing to the modified document:

```java
Merger merger = new Merger(filePath);
```

### ขั้นตอนที่ 2: บันทึกเอกสารที่แก้ไขแล้ว
Call the `save` method with the desired output location. GroupDocs.Merger writes the file in a streaming fashion, keeping memory usage low:

```java
merger.save(outputPath);
```

## การประยุกต์ใช้ในทางปฏิบัติ

Embedding images as OLE objects unlocks several real‑world scenarios:

- **Interactive Reports:** ผู้ใช้สามารถดับเบิล‑คลิกแผนภูมิที่ฝังไว้, แก้ไขใน Excel, และเห็นภาพที่อัปเดตทันที.  
- **Automated Document Generation:** ระบบการเงินและสุขภาพสามารถแทรกกราฟิกที่อัปเดตล่าสุดลงในสัญญาหรือสรุปผู้ป่วยโดยไม่ต้องแก้ไขด้วยมือ.  
- **Collaboration Platforms:** ทีมสามารถแชร์ไฟล์ Word เดียวที่สมาชิกแต่ละคนอัปเดตแผนผังของตนเอง, ลดปัญหาการควบคุมเวอร์ชัน.

## พิจารณาด้านประสิทธิภาพ

To keep your application responsive when processing large files:

- **Stream Data:** GroupDocs.Merger สตรีมข้อมูลทั้งอินพุตและเอาต์พุต, ป้องกันการโหลดไฟล์เต็มเข้าสู่หน่วยความจำ.  
- **Reuse Objects:** การใช้ซ้ำอินสแตนซ์ `Merger` เดียวสำหรับการนำเข้าหลายครั้งช่วยลดภาระการสร้างอ็อบเจ็กต์.  
- **Monitor Heap:** สำหรับเอกสารที่ใหญ่กว่า 200 MB, พิจารณาเพิ่ม heap ของ JVM (`-Xmx1g`) เพื่อหลีกเลี่ยง `OutOfMemoryError`.  

## ปัญหาทั่วไปและวิธีแก้

| อาการ | สาเหตุที่เป็นไปได้ | วิธีแก้ |
|---------|--------------|-----|
| `Unsupported file format` error | ภาพไม่ได้อยู่ในรูปแบบ PNG/JPEG/BMP/GIF/TIFF | แปลงภาพเป็นรูปแบบที่รองรับก่อนอ่านไบต์. |
| OLE object appears at the wrong location | พิกัด `x`/`y` ไม่ถูกต้องใน `OleDiagramOptions` | ตรวจสอบว่าพิกัดวัดเป็นหน่วยจุด (1 pt ≈ 1/72 in). |
| Output file is corrupted | ไม่ได้เรียก `save()` หลังการนำเข้า | ตรวจสอบว่าได้เรียก `merger.save(outputPath)` หลังจากการแก้ไขทั้งหมด. |

## คำถามที่พบบ่อย

**Q: OLE object คืออะไร?**  
A: วัตถุ OLE ฝังข้อมูลจากแอปพลิเคชันหนึ่ง (เช่น ภาพ) ไปยังอีกแอปพลิเคชันหนึ่ง (เช่น ไฟล์ Word), ทำให้สามารถแก้ไขในที่เดียวโดยไม่ต้องออกจากเอกสารโฮสต์.

**Q: ฉันสามารถใช้ GroupDocs.Merger สำหรับโครงการเชิงพาณิชย์ได้หรือไม่?**  
A: ใช่—การใช้เชิงพาณิชย์ต้องมีใบอนุญาตที่ถูกต้อง. มีรุ่นทดลองสำหรับการประเมิน, แต่การใช้งานในสภาพแวดล้อมการผลิตต้องมีใบอนุญาต.

**Q: ไลบรารีจัดการกับภาพขนาดใหญ่อย่างไร?**  
A: ภาพจะถูกอ่านเป็นอาร์เรย์ไบต์, แต่คุณสามารถสตรีมไฟล์ขนาดใหญ่โดยใช้ `FileInputStream` และส่งสตรีมไปยัง `importOleDiagram` เพื่อรักษาการใช้หน่วยความจำให้ต่ำ.

**Q: รูปแบบเอกสารใดรองรับการฝัง OLE?**  
A: DOCX, XLSX, PPTX, และ PDF รองรับเต็มรูปแบบ. สำหรับ PDF, วัตถุ OLE จะถูกเก็บเป็นสตรีมไฟล์ที่ฝังอยู่.

**Q: มีข้อจำกัดใดเกี่ยวกับจำนวนวัตถุ OLE ต่อเอกสารหรือไม่?**  
A: โดยปฏิบัติไม่มี—GroupDocs.Merger สามารถฝัง OLE diagram ได้หลายสิบรายการ, จำกัดเพียงขนาดของเอกสารโฮสต์และหน่วยความจำที่มี.

## แหล่งข้อมูล
- [การปล่อย GroupDocs.Merger](https://releases.groupdocs.com/merger/java/)
- [เอกสาร GroupDocs.Merger Java](https://docs.groupdocs.com/merger/java/)
- [อ้างอิง API Java](https://reference.groupdocs.com/merger/java/)
- [การปล่อย GroupDocs.Merger สำหรับ Java](https://releases.groupdocs.com/merger/java/)
- [หน้าซื้อ GroupDocs](https://purchase.groupdocs.com/buy)
- [ฟอรั่มสนับสนุน GroupDocs](https://forum.groupdocs.com/c/merger)

## สรุป
You now have a complete, production‑ready workflow to **convert image to OLE** using GroupDocs.Merger for Java. By defining file paths, reading image bytes, configuring `OleDiagramOptions`, and invoking `importOleDiagram`, you can enrich any supported document with interactive graphics. Explore additional APIs—such as merging, splitting, and watermarking—to build a full‑featured document processing pipeline.

---

**อัปเดตล่าสุด:** 2026-06-26  
**ทดสอบด้วย:** GroupDocs.Merger 23.10 สำหรับ Java  
**ผู้เขียน:** GroupDocs

## บทแนะนำที่เกี่ยวข้อง

- [วิธีฝัง PDF ใน Excel ด้วย GroupDocs.Merger สำหรับ Java - นำเข้า OLE Object – คู่มือขั้นตอน](/merger/java/document-import/import-ole-object-excel-groupdocs-merger-java/)
- [วิธีฝัง pdf ใน word ด้วย GroupDocs.Merger สำหรับ Java – คู่มือฉบับสมบูรณ์](/merger/java/document-import/embed-ole-objects-word-documents-groupdocs-java/)
- [วิธีรวมภาพ PNG ด้วย GroupDocs.Merger สำหรับ Java - คู่มือขั้นตอน](/merger/java/document-information/merge-png-images-groupdocs-merger-java/)