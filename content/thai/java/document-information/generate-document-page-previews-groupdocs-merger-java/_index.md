---
date: '2026-06-26'
description: เรียนรู้วิธีแปลงหน้าของ PDF เป็นภาพและแสดงตัวอย่างเอกสารโดยใช้ GroupDocs.Merger
  for Java – วิธีที่รวดเร็วและเชื่อถือได้ในการสร้างภาพย่อของหน้า.
keywords:
- convert pdf pages to images
- document page previews
- GroupDocs.Merger Java
schemas:
- author: GroupDocs
  dateModified: '2026-06-26'
  description: Learn how to convert pdf pages to images and preview documents using
    GroupDocs.Merger for Java – the fast, reliable way to generate page thumbnails.
  headline: How to Convert PDF Pages to Images and Preview Documents with GroupDocs.Merger
    for Java
  type: TechArticle
- questions:
  - answer: It’s used for merging, splitting, and managing documents efficiently,
      including preview generation and format conversion.
    question: What is GroupDocs.Merger for Java used for?
  - answer: Wrap stream creation and closing in try‑catch blocks, as shown in the
      helper methods, to prevent memory leaks.
    question: How do I handle exceptions during stream operations?
  - answer: Yes, change the `PreviewMode` enum to PNG, BMP, or TIFF to suit your requirements.
    question: Can I generate previews in formats other than JPEG?
  - answer: Typical problems include incorrect file paths and forgetting to close
      streams, which can cause memory leaks.
    question: What are common issues with document preview generation?
  - answer: Use its API to connect with databases, web services, or other Java applications
      for seamless workflow automation.
    question: How can I integrate GroupDocs.Merger with other systems?
  type: FAQPage
title: วิธีแปลงหน้าของ PDF เป็นภาพและแสดงตัวอย่างเอกสารด้วย GroupDocs.Merger for Java
type: docs
url: /th/java/document-information/generate-document-page-previews-groupdocs-merger-java/
weight: 1
---

# วิธีแปลงหน้าของ PDF เป็นภาพและแสดงตัวอย่างเอกสารด้วย GroupDocs.Merger สำหรับ Java

ในแอปพลิเคชันสมัยใหม่คุณมักต้อง **แปลงหน้าของ PDF เป็นภาพ** เพื่อให้ผู้ใช้สามารถดูเอกสารอย่างรวดเร็วโดยไม่ต้องดาวน์โหลดไฟล์ทั้งหมด บทแนะนำนี้จะพาคุณผ่านการสร้างตัวอย่างหน้าคุณภาพสูงด้วย GroupDocs.Merger สำหรับ Java ครอบคลุมตั้งแต่การตั้งค่าไปจนถึงการจัดการที่เก็บข้อมูลแบบกำหนดเอง เมื่อเสร็จสิ้นคุณจะมีโซลูชันที่ใช้ซ้ำได้สำหรับการสร้างรูปย่อเอกสารที่ทำงานบนสภาพแวดล้อม JDK 8+ ใดก็ได้

## คำตอบอย่างรวดเร็ว
- **“preview documents” หมายถึงอะไร?** การสร้างภาพตัวแทนที่มีน้ำหนักเบาของแต่ละหน้า.  
- **รูปแบบที่ใช้สำหรับการแสดงตัวอย่างคืออะไร?** โดยค่าเริ่มต้นเป็น JPEG แต่รองรับรูปแบบอื่นด้วย.  
- **ต้องการไลเซนส์หรือไม่?** การทดลองใช้ฟรีทำงานได้สำหรับการพัฒนา; จำเป็นต้องมีไลเซนส์แบบชำระเงินสำหรับการใช้งานจริง.  
- **ฉันสามารถกำหนดเส้นทางเอาต์พุตได้หรือไม่?** ได้, โดยการทำการ implement `PageStreamFactory` แบบกำหนดเอง.  
- **ต้องการเวอร์ชัน Java ใด?** JDK 8 หรือใหม่กว่า.

## “how to preview documents” คืออะไร?
การแสดงตัวอย่างเอกสารหมายถึงการสร้างรูปย่อภาพ (โดยปกติเป็น JPEG หรือ PNG) สำหรับแต่ละหน้าเพื่อให้ผู้ใช้สามารถเลื่อนดูเนื้อหาได้อย่างรวดเร็ว เทคนิคนี้ช่วยเพิ่ม UX ในตัวจัดการไฟล์, พอร์ทัลการตรวจสอบเนื้อหา, และระบบใด ๆ ที่จัดการเอกสารจำนวนมาก, ให้สัญญาณภาพที่เร็วโดยไม่ต้องเปิดไฟล์เต็ม

## ทำไมต้องใช้ GroupDocs.Merger สำหรับ Java?
GroupDocs.Merger แปลงหน้าของ PDF เป็นภาพ **ภายในเวลาน้อยกว่า 0.5 วินาทีต่อหน้าบน CPU 2 GHz ปกติ**, รองรับ **รูปแบบอินพุตและเอาต์พุตกว่า 50+**, และให้คุณสตรีมตัวอย่างโดยตรงไปยังที่เก็บข้อมูลโดยไม่ต้องโหลดไฟล์ทั้งหมดเข้าสู่หน่วยความจำ API ที่ขยายได้ยังให้คุณควบคุมคุณภาพภาพ, รูปแบบ, และเส้นทางปลายทางได้อย่างเต็มที่

## ข้อกำหนดเบื้องต้น
- **GroupDocs.Merger for Java** library (ดูการติดตั้งด้านล่าง).  
- **JDK 8+** ติดตั้งบนเครื่องของคุณ.  
- IDE (IntelliJ IDEA, Eclipse, NetBeans) และ Maven หรือ Gradle สำหรับการจัดการ dependencies.  

## การตั้งค่า GroupDocs.Merger สำหรับ Java
เพิ่มไลบรารีลงในโปรเจกต์ของคุณโดยใช้เครื่องมือสร้างที่คุณต้องการ

**Maven:**  
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle:**  
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**ดาวน์โหลดโดยตรง:**  
หรือคุณสามารถดาวน์โหลดเวอร์ชันล่าสุดจาก [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### การรับไลเซนส์
- **Free Trial:** เริ่มต้นด้วยการดาวน์โหลดการทดลองใช้ฟรีเพื่อสำรวจฟีเจอร์.  
- **Temporary License:** รับไลเซนส์ชั่วคราวเพื่อเข้าถึงเพิ่มเติมระหว่างการพัฒนา.  
- **Purchase:** สำหรับการใช้งานในผลิตจริง, ซื้อไลเซนส์จาก [GroupDocs](https://purchase.groupdocs.com/buy).

เมื่อเพิ่มไลบรารีแล้ว, เริ่มต้นด้วยการกำหนดเส้นทางไปยังเอกสารที่คุณต้องการแสดงตัวอย่าง:
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

## วิธีแสดงตัวอย่างเอกสาร: คู่มือขั้นตอนต่อขั้นตอน
โหลดไฟล์ต้นทาง, กำหนดค่า `PageStreamFactory`, และเรียก `generatePreview`.  
`generatePreview` เป็นเมธอดที่แปลงแต่ละหน้าของเอกสารเป็นภาพตามตัวเลือกที่ให้.

### ขั้นตอนที่ 1: เริ่มต้น Merger และกำหนด PageStreamFactory
`Merger` เป็นคลาสหลักที่ให้เมธอดสำหรับการรวม, แบ่ง, และสร้างตัวอย่างของเอกสาร.  
`PageStreamFactory` เป็นอินเทอร์เฟซที่บอกไลบรารีว่าจะเขียนภาพตัวอย่างแต่ละภาพไปที่ไหน.
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

ที่นี่เราสร้างการทำงานแบบกำหนดเองที่เขียนภาพแต่ละหน้าลงในโฟลเดอร์เฉพาะด้วยรูปแบบการตั้งชื่อที่คาดเดาได้.
```java
IPreviewOptions previewOption = new PreviewOptions(new PageStreamFactory() {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        return createStream(pageNumber);
    }
    
    @Override
    public void closePageStream(int pageNumber, OutputStream pageStream) {
        releasePageStream(pageNumber, pageStream);
    }
}, PreviewMode.JPEG);
```

### ขั้นตอนที่ 2: สร้างตัวอย่าง
`generatePreview` เริ่มกระบวนการแปลงตามตัวเลือกที่คุณระบุ. มันสตรีมภาพแต่ละหน้าต่อ `PageStreamFactory` ที่คุณกำหนด, เพื่อให้ใช้หน่วยความจำน้อย.
```java
merger.generatePreview(previewOption);
```

### แปลงหน้เป็นภาพ – Custom PageStreamFactory
หากคุณต้องการควบคุมการตั้งชื่อไฟล์หรือที่จัดเก็บมากขึ้น, ให้ทำการ implement factory ของคุณเอง:
```java
class CustomPageStreamFactory implements PageStreamFactory {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        String filePath = "YOUR_OUTPUT_DIRECTORY/image-" + pageNumber + ".jpg";
        return new FileOutputStream(filePath);
    }
    
    @Override
    public void closePageStream(int pageNumber, OutputStream pageStream) {
        try {
            if (pageStream != null) {
                pageStream.close();
            }
        } catch (Exception e) {
            throw new RuntimeException(e);
        }
    }
}
```

### วิธีช่วยเหลือ – การจัดการ Streams
เมธอดยูทิลิตี้เหล่านี้ช่วยให้โค้ดเป็นระเบียบและจัดการข้อยกเว้นอย่างสะอาด.
```java
private static String getImagePath(int pageNumber) {
    return "YOUR_OUTPUT_DIRECTORY/image-" + pageNumber + ".jpg";
}

private static OutputStream createStream(int pageNumber) {
    try {
        String imageFilePath = getImagePath(pageNumber);
        return new FileOutputStream(imageFilePath);
    } catch (FileNotFoundException e) {
        throw new RuntimeException(e);
    }
}

private static void releasePageStream(int pageNumber, OutputStream pageStream) {
    try {
        if (pageStream != null) {
            pageStream.close();
        }
    } catch (Exception e) {
        throw new RuntimeException(e);
    }
}
```

## การสร้างรูปย่อเอกสาร – การใช้งานจริง
การสร้างตัวอย่างมีประโยชน์เป็นพิเศษสำหรับ:

1. **Document Management Systems** – ผู้ใช้สามารถเลื่อนดูไฟล์โดยไม่ต้องเปิดไฟล์.  
2. **Content Review Platforms** – การตรวจสอบภาพอย่างรวดเร็วก่อนยอมรับการอัปโหลด.  
3. **Educational Tools** – นักเรียนสามารถดูสไลด์การบรรยายหรือหน้าหนังสือเรียนได้อย่างรวดเร็ว.  

## ข้อควรพิจารณาด้านประสิทธิภาพ
- **Release streams promptly** เพื่อปล่อยหน่วยความจำ.  
- **Avoid loading whole documents** เข้าสู่หน่วยความจำ; ให้ไลบรารีจัดการ paging.  
- **Use appropriate image quality** settings เพื่อสมดุลความเร็วและคุณภาพภาพ.  

## คำถามที่พบบ่อย

**Q: GroupDocs.Merger for Java ใช้ทำอะไร?**  
A: มันใช้สำหรับการรวม, แบ่ง, และจัดการเอกสารอย่างมีประสิทธิภาพ, รวมถึงการสร้างตัวอย่างและการแปลงรูปแบบ.

**Q: จะจัดการข้อยกเว้นระหว่างการทำงานของ stream อย่างไร?**  
A: ห่อการสร้างและปิด stream ด้วยบล็อก try‑catch ตามที่แสดงในเมธอดช่วยเหลือ, เพื่อป้องกันการรั่วไหลของหน่วยความจำ.

**Q: สามารถสร้างตัวอย่างในรูปแบบอื่นนอกจาก JPEG ได้หรือไม่?**  
A: ได้, เปลี่ยน enum `PreviewMode` เป็น PNG, BMP, หรือ TIFF ตามความต้องการของคุณ.

**Q: ปัญหาที่พบบ่อยในการสร้างตัวอย่างเอกสารคืออะไร?**  
A: ปัญหาทั่วไปรวมถึงเส้นทางไฟล์ไม่ถูกต้องและลืมปิด stream, ซึ่งอาจทำให้เกิดการรั่วไหลของหน่วยความจำ.

**Q: จะรวม GroupDocs.Merger กับระบบอื่นได้อย่างไร?**  
A: ใช้ API ของมันเพื่อเชื่อมต่อกับฐานข้อมูล, เว็บเซอร์วิส, หรือแอปพลิเคชัน Java อื่น ๆ เพื่อการทำงานอัตโนมัติที่ราบรื่น.

---

## แหล่งข้อมูล
- [การปล่อย GroupDocs.Merger for Java](https://releases.groupdocs.com/merger/java/)  
- [ดาวน์โหลด](https://releases.groupdocs.com/merger/java/)  
- [เอกสารประกอบ](https://docs.groupdocs.com/merger/java/)  
- [อ้างอิง API](https://reference.groupdocs.com/merger/java/)  
- [ทดลองใช้ฟรี](https://releases.groupdocs.com/merger/java/)  
- [ไลเซนส์ชั่วคราว](https://purchase.groupdocs.com/temporary-license/)  
- [ซื้อ](https://purchase.groupdocs.com/buy)  
- [GroupDocs](https://purchase.groupdocs.com/buy)  
- [สนับสนุน](https://forum.groupdocs.com/c/merger/)

**อัปเดตล่าสุด:** 2026-06-26  
**ทดสอบกับ:** GroupDocs.Merger latest version (2025‑latest)  
**ผู้เขียน:** GroupDocs

## บทแนะนำที่เกี่ยวข้อง

- [บทแนะนำการดำเนินการหน้าของเอกสารสำหรับ GroupDocs.Merger Java](/merger/java/page-operations/)
- [วิธีโหลด PDF จาก URL ด้วย GroupDocs.Merger for Java: คู่มือฉบับสมบูรณ์](/merger/java/document-loading/load-pdf-url-groupdocs-merger-java/)
- [สร้าง PDF หน้าหนึ่งด้วย GroupDocs.Merger Java](/merger/java/document-splitting/)