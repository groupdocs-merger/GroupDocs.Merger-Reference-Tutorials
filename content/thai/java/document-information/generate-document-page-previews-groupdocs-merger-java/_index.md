---
date: '2026-01-24'
description: เรียนรู้วิธีแสดงตัวอย่างเอกสารโดยการสร้างตัวอย่างหน้าด้วย GroupDocs.Merger
  for Java ซึ่งเป็นวิธีที่เร็วในการแปลงหน้าเป็นภาพสำหรับการสร้างภาพย่อของเอกสาร.
keywords:
- GroupDocs.Merger for Java
- document page previews
- Java document management
title: วิธีแสดงตัวอย่างเอกสารด้วย GroupDocs.Merger สำหรับ Java
type: docs
url: /th/java/document-information/generate-document-page-previews-groupdocs-merger-java/
weight: 1
---

# วิธีดูตัวอย่างเอกสารด้วย GroupDocs.Merger for Java

การสร้างตัวอย่างหน้าเอกสารเป็นวิธีที่ทรงพลังในการ **ดูตัวอย่างเอกสาร** อย่างรวดเร็ว ให้ผู้ใช้เห็นภาพสแนปช็อตโดยไม่ต้องเปิดไฟล์เต็ม ในบทแนะนำนี้คุณจะได้เรียนรู้วิธีสร้างตัวอย่างเหล่านั้นโดยใช้ GroupDocs.Merger for Java ซึ่งเป็นไลบรารีที่ทำให้การ **แปลงหน้ามาเป็นภาพ** และการสนับสนุน **การสร้างภาพย่อของเอกสาร** ในแอปพลิเคชันของคุณเป็นเรื่องง่าย

## คำตอบสั้น
- **“preview documents” หมายถึงอะไร?** การสร้างภาพตัวแทนขนาดเล็กของแต่ละหน้า  
- **รูปแบบใดใช้สำหรับตัวอย่าง?** JPEG เป็นค่าเริ่มต้น แต่รองรับรูปแบบอื่น ๆ ด้วย  
- **ต้องมีลิขสิทธิ์หรือไม่?** สามารถใช้เวอร์ชันทดลองฟรีสำหรับการพัฒนา; ต้องมีลิขสิทธิ์แบบชำระเงินสำหรับการใช้งานจริง  
- **สามารถกำหนดเส้นทางการบันทึกผลลัพธ์ได้หรือไม่?** ได้โดยการทำงานกับ `PageStreamFactory` ที่กำหนดเอง  
- **ต้องใช้ Java เวอร์ชันใด?** JDK 8 หรือใหม่กว่า  

## “how to preview documents” คืออะไร?
การดูตัวอย่างเอกสารหมายถึงการสร้างภาพย่อ (มักเป็น JPEG หรือ PNG) สำหรับแต่ละหน้า เพื่อให้ผู้ใช้สามารถสแกนเนื้อหาได้อย่างรวดเร็ว เทคนิคนี้ช่วยปรับปรุงประสบการณ์ผู้ใช้ในระบบจัดการเอกสาร, พอร์ทัล, และแอปใด ๆ ที่ต้องจัดการไฟล์จำนวนมาก  

## ทำไมต้องใช้ GroupDocs.Merger for Java?
- **การแปลงที่เร็ว** ของหน้าเป็นภาพโดยไม่ต้องเปิดเอกสารเต็มใน UI  
- **รองรับหลายรูปแบบในตัว** (PDF, DOCX, XLSX, ฯลฯ)  
- **API ที่ขยายได้** ให้คุณควบคุมตำแหน่งและวิธีการบันทึกไฟล์ตัวอย่าง  

## ข้อกำหนดเบื้องต้น
- ไลบรารี **GroupDocs.Merger for Java** (ดูการติดตั้งด้านล่าง)  
- **JDK 8+** ติดตั้งบนเครื่องของคุณ  
- IDE (IntelliJ IDEA, Eclipse, NetBeans) และ Maven หรือ Gradle สำหรับการจัดการ dependencies  

## การตั้งค่า GroupDocs.Merger for Java
เพิ่มไลบรารีลงในโปรเจกต์ของคุณโดยใช้เครื่องมือสร้างที่คุณชอบ

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
หรือดาวน์โหลดเวอร์ชันล่าสุดจาก [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/)  

### การรับลิขสิทธิ์
- **เวอร์ชันทดลองฟรี:** เริ่มต้นโดยดาวน์โหลดเวอร์ชันทดลองเพื่อสำรวจฟีเจอร์  
- **ลิขสิทธิ์ชั่วคราว:** รับลิขสิทธิ์ชั่วคราวสำหรับการเข้าถึงเพิ่มเติมระหว่างการพัฒนา  
- **การซื้อ:** สำหรับการใช้งานในผลิตภัณฑ์เต็มรูปแบบ ให้ซื้อไลเซนส์จาก [GroupDocs](https://purchase.groupdocs.com/buy)  

เมื่อเพิ่มไลบรารีแล้ว ให้เริ่มต้นด้วยการระบุเส้นทางไปยังเอกสารที่ต้องการดูตัวอย่าง:

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

## วิธีดูตัวอย่างเอกสาร: คู่มือขั้นตอนโดยละเอียด

### ขั้นตอนที่ 1: เริ่มต้น Merger และกำหนด PageStreamFactory
`PageStreamFactory` บอกไลบรารีว่าจะเขียนภาพตัวอย่างแต่ละไฟล์ไปที่ไหน

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

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
เรียกเมธอด `generatePreview` พร้อมกับตัวเลือกที่คุณตั้งค่าไว้

```java
merger.generatePreview(previewOption);
```

### แปลงหน้าเป็นภาพ – PageStreamFactory ที่กำหนดเอง
หากต้องการควบคุมการตั้งชื่อไฟล์หรือที่จัดเก็บเพิ่มเติม ให้สร้างฟา́กทอรีของคุณเอง:

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

### เมธอดช่วยเหลือ – การจัดการ Stream
เมธอดยูทิลิตี้เหล่านี้ช่วยให้โค้ดเป็นระเบียบและจัดการข้อยกเว้นได้อย่างสะอาด

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

## การสร้างภาพย่อของเอกสาร – การใช้งานในชีวิตจริง
การสร้างตัวอย่างมีประโยชน์เป็นพิเศษสำหรับ:

1. **ระบบจัดการเอกสาร** – ผู้ใช้สามารถสแกนไฟล์โดยไม่ต้องเปิดเต็ม  
2. **แพลตฟอร์มตรวจสอบเนื้อหา** – ตรวจสอบภาพอย่างรวดเร็วก่อนอนุมัติการอัปโหลด  
3. **เครื่องมือการศึกษา** – นักเรียนสามารถมองดูสไลด์หรือหน้าหนังสือเรียนได้อย่างรวดเร็ว  

## พิจารณาด้านประสิทธิภาพ
- **ปล่อย Stream ทันที** เพื่อคืนหน่วยความจำ  
- **หลีกเลี่ยงการโหลดเอกสารทั้งหมด** เข้าเมโมรี; ให้ไลบรารีจัดการการแบ่งหน้า  
- **ตั้งค่าคุณภาพภาพที่เหมาะสม** เพื่อสมดุลระหว่างความเร็วและความคมชัด  

## คำถามที่พบบ่อย

**ถาม: GroupDocs.Merger for Java ใช้ทำอะไร?**  
ตอบ: ใช้สำหรับการรวม, แยก, และจัดการเอกสารอย่างมีประสิทธิภาพ รวมถึงการสร้างตัวอย่างด้วย  

**ถาม: จะจัดการข้อยกเว้นระหว่างการทำงานกับ Stream อย่างไร?**  
ตอบ: ห่อการสร้างและปิด Stream ด้วยบล็อก try‑catch ตามที่แสดงในเมธอดช่วยเหลือ  

**ถาม: สามารถสร้างตัวอย่างในรูปแบบอื่นนอกจาก JPEG ได้หรือไม่?**  
ตอบ: ได้, เปลี่ยนค่า enum `PreviewMode` เป็น PNG, BMP ฯลฯ ตามความต้องการ  

**ถาม: ปัญหาที่พบบ่อยในการสร้างตัวอย่างเอกสารคืออะไร?**  
ตอบ: ปัญหาทั่วไปรวมถึงเส้นทางไฟล์ไม่ถูกต้องและไม่ปิด Stream ซึ่งอาจทำให้เกิดการรั่วของหน่วยความจำ  

**ถาม: จะผสาน GroupDocs.Merger กับระบบอื่นได้อย่างไร?**  
ตอบ: ใช้ API ของมันเชื่อมต่อกับฐานข้อมูล, เว็บเซอร์วิส, หรือแอป Java อื่น ๆ เพื่อทำงานอัตโนมัติอย่างต่อเนื่อง  

## แหล่งข้อมูลเพิ่มเติม
- [Documentation](https://docs.groupdocs.com/merger/java/)  
- [API Reference](https://reference.groupdocs.com/merger/java/)  
- [Download](https://releases.groupdocs.com/merger/java/)  
- [Purchase](https://purchase.groupdocs.com/buy)  
- [Free Trial](https://releases.groupdocs.com/merger/java/)  
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- [Support](https://forum.groupdocs.com/c/merger/)  

---

**อัปเดตล่าสุด:** 2026-01-24  
**ทดสอบกับ:** GroupDocs.Merger เวอร์ชันล่าสุด (2025‑latest)  
**ผู้เขียน:** GroupDocs