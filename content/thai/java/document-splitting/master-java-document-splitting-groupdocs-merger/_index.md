---
date: '2026-02-06'
description: เรียนรู้วิธีแยกไฟล์ DOCX ด้วย GroupDocs.Merger สำหรับ Java รวมถึงการแยก
  DOCX เป็นไฟล์หลายไฟล์ ตัวเลือกการแยกใน Java และการสกัดข้อมูลจากสตรีม
keywords:
- Java Document Splitting
- GroupDocs.Merger for Java
- Split DOCX Pages
title: วิธีแยกไฟล์ DOCX ด้วย GroupDocs.Merger สำหรับ Java
type: docs
url: /th/java/document-splitting/master-java-document-splitting-groupdocs-merger/
weight: 1
---

# การแยกเอกสาร Java อย่างเชี่ยวชาญด้วย GroupDocs.Merger: แยกหน้า DOCX เป็นไฟล์และสตรีม

ในบทแนะนำนี้คุณจะได้เรียนรู้ **วิธีการแยก docx** อย่างมีประสิทธิภาพด้วย GroupDocs.Merger สำหรับ Java ไม่ว่าคุณจะต้องการแยกสัญญาขนาดใหญ่เป็นหน้าแยกหรือดึงส่วนเฉพาะเป็นสตรีม เราจะพาคุณผ่านทุกขั้นตอน ตั้งแต่การตั้งค่าไปจนถึงการใช้งานจริง

## คำตอบสั้น ๆ
- **ไลบรารีใดที่จัดการการแยก DOCX ใน Java?** GroupDocs.Merger สำหรับ Java  
- **ฉันสามารถแยก DOCX เป็นไฟล์แยกได้หรือไม่?** ได้ – ใช้ `SplitOptions` พร้อมระบุเลขหน้า  
- **สามารถรับหน้าเป็นสตรีมแทนไฟล์ได้หรือไม่?** แน่นอน โดยการให้ `SplitStreamFactory` ที่กำหนดเอง  
- **ต้องการไลเซนส์หรือไม่?** ไลเซนส์ทดลองชั่วคราวเพียงพอสำหรับการประเมิน; ต้องมีไลเซนส์เต็มสำหรับการใช้งานจริง  
- **รองรับเวอร์ชัน Java ใดบ้าง?** JDK 8 ขึ้นไปทั้งหมดทำงานได้กับเวอร์ชันล่าสุดของ GroupDocs.Merger  

## “วิธีการแยก docx” คืออะไร?
การแยก DOCX หมายถึงการนำเอกสาร Word ที่มีหลายหน้าแล้วสร้างไฟล์ (หรือสตรีม) แยกที่บรรจุหนึ่งหรือหลายหน้าที่เลือกไว้ ซึ่งเป็นประโยชน์สำหรับการจัดส่งเอกสารแบบโมดูลาร์, กระบวนการปฏิบัติตามข้อกำหนด, หรือการประมวลผลแบบเรียลไทม์ที่ไม่ต้องการเก็บไฟล์ชั่วคราว

## ทำไมต้องใช้ GroupDocs.Merger สำหรับ Java?
- **การประมวลผลไม่มีการพึ่งพาไลบรารีภายนอก:** ทำงานด้วย Java แท้ ๆ ไม่ต้องใช้ไบนารีเนทีฟ  
- **การควบคุมละเอียด:** เลือกหน้า, รูปแบบผลลัพธ์, และสตรีมในหน่วยความจำได้ตามต้องการ  
- **ประสิทธิภาพขยายได้:** การแยกแบบสตรีมช่วยลดภาระหน่วยความจำสำหรับไฟล์ขนาดใหญ่  

## ข้อกำหนดเบื้องต้น

### ไลบรารีและการพึ่งพาที่จำเป็น
- **Java Development Kit (JDK):** JDK 8 หรือใหม่กว่า  
- **GroupDocs.Merger สำหรับ Java:** ไลบรารีหลักสำหรับการจัดการเอกสาร  

### การเพิ่ม Dependency
เพิ่มไลบรารีผ่าน Maven หรือ Gradle (โค้ดบล็อกไม่เปลี่ยน):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

คุณสามารถดาวน์โหลดเวอร์ชันล่าสุดได้จากเว็บไซต์อย่างเป็นทางการ: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/)

### การรับไลเซนส์
- **ไลเซนส์ทดลอง:** รับคีย์ชั่วคราวจากหน้า [GroupDocs.Trial License](https://purchase.groupdocs.com/temporary-license/)  
- **ไลเซนส์สำหรับการผลิต:** ซื้อไลเซนส์เต็มที่ [GroupDocs Purchase](https://purchase.groupdocs.com/buy)

## การตั้งค่า GroupDocs.Merger สำหรับ Java
เริ่มต้นใช้งานไลบรารีในโปรเจกต์ Java ของคุณ:

```java
import com.groupdocs.merger.Merger;

public class DocumentSetup {
    public static void main(String[] args) {
        // Initialize a Merger object with the path of the input document
        Merger merger = new Merger("path/to/your/document.docx");
        
        // Perform operations on your document...
        
        merger.close();
    }
}
```

เมื่อพร้อมแล้ว เราจะสำรวจสองวิธีหลักเพื่อ **แยก docx เป็นไฟล์** หรือสตรีม

## วิธีแยก DOCX เป็นไฟล์ด้วย GroupDocs.Merger

### แยกเอกสารเป็นหน้าเดี่ยว
#### ภาพรวม
วิธีนี้จะสร้างไฟล์แยกสำหรับแต่ละหน้าที่เลือก เหมาะสำหรับการแจกจ่ายส่วนย่อยของเอกสาร

#### ขั้นตอนแบบละเอียด

**ขั้นตอนที่ 1 – ระบุเส้นทางไฟล์ต้นฉบับและไฟล์ผลลัพธ์**  
กำหนดตำแหน่งที่ไฟล์ DOCX ต้นฉบับอยู่และที่ที่ไฟล์ที่แยกแล้วจะถูกบันทึก

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
String filePathOut = new File("YOUR_OUTPUT_DIRECTORY", 
    "SplitToSinglePages-" +
    Paths.get(filePath).getFileName().toString()
).getPath();
```

**ขั้นตอนที่ 2 – ตั้งค่า SplitOptions (split options java)**  
บอกไลบรารีว่าต้องการดึงหน้าใดบ้าง

```java
import com.groupdocs.merger.domain.options.SplitOptions;

SplitOptions splitOptions = new SplitOptions(filePathOut, new int[] { 3, 6, 8 });
```
- `filePathOut` – โฟลเดอร์ที่ไฟล์แต่ละหน้าจะถูกวางไว้  
- `new int[]{3,6,8}` – หมายเลขหน้าที่ต้องการแยกออก  

**ขั้นตอนที่ 3 – ดำเนินการแยก**  
เรียกใช้การทำงานผ่านอินสแตนซ์ `Merger`

```java
import com.groupdocs.merger.Merger;

Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

**เคล็ดลับ:** ตรวจสอบให้แน่ใจว่าโฟลเดอร์ผลลัพธ์มีอยู่และแอปพลิเคชันของคุณมีสิทธิ์เขียน; หากไม่เช่นนั้นการแยกจะล้มเหลว

### ข้อผิดพลาดที่พบบ่อย
- **ไม่มีโฟลเดอร์ผลลัพธ์:** API จะไม่สร้างไดเรกทอรีโดยอัตโนมัติ  
- **ระบุเลขหน้าไม่ถูกต้อง:** ดัชนีหน้าเริ่มที่ 1; การระบุ 0 จะทำให้เกิดข้อผิดพลาด

## วิธีแยกหน้า DOCX เป็นสตรีม (In‑Memory)

### ภาพรวม
เมื่อคุณต้องการเข้าถึงชั่วคราว—เช่น ส่งหน้าผ่านเว็บเซอร์วิส—การจับหน้าด้วยสตรีมช่วยหลีกเลี่ยงการอ่าน/เขียนดิสก์

#### ขั้นตอนแบบละเอียด

**ขั้นตอนที่ 1 – กำหนดเส้นทางไฟล์ต้นฉบับและเตรียม List สำหรับสตรีม**  

```java
import java.io.ByteArrayOutputStream;
import java.util.ArrayList;
import java.util.List;

String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
final List<OutputStream> resultStreams = new ArrayList<>();
```

**ขั้นตอนที่ 2 – ตั้งค่า SplitOptions พร้อม Custom SplitStreamFactory**  

```java
import com.groupdocs.merger.domain.common.SplitStreamFactory;
import com.groupdocs.merger.domain.options.SplitMode;

SplitOptions splitOptions = new SplitOptions(new SplitStreamFactory() {
    @Override
    public OutputStream createSplitStream(int pageNumber) {
        return new ByteArrayOutputStream(); // Create a stream for each page
    }
    
    @Override
    public void closeSplitStream(int pageNumber, OutputStream pageStream) {
        resultStreams.add(pageStream); // Collect the streams
    }
}, new int[] { 3, 4 }, SplitMode.Pages);
```
- `createSplitStream` – สร้าง `OutputStream` ใหม่สำหรับแต่ละหน้าที่ร้องขอ  
- `closeSplitStream` – เก็บสตรีมที่เสร็จสมบูรณ์ไว้ใช้ต่อไป  

**ขั้นตอนที่ 3 – ดำเนินการแยกและดึงสตรีมกลับมา**  

```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);

return resultStreams; // Retrieve streams for processing
```

**คำแนะนำการแก้ไขปัญหา**
- ตรวจสอบให้แน่ใจว่าเส้นทาง DOCX ต้นฉบับถูกต้อง; การพิมพ์ผิดจะทำให้เกิด `FileNotFoundException`  
- ปิดสตรีมทุกครั้งหลังใช้งานเพื่อคืนหน่วยความจำ

## การประยุกต์ใช้งานจริง
1. **สัญญากฎหมาย:** ดึงข้อกำหนดย่อยออกมาเพื่อการตรวจสอบแยกกัน  
2. **แพลตฟอร์ม E‑learning:** ให้บริการไฟล์ Word ทีละบทโดยไม่เปิดเผยหนังสือทั้งหมด  
3. **รายงานธุรกิจ:** ส่งเฉพาะส่วนการเงินของรายงานไตรมาสให้ CFO  

## พิจารณาด้านประสิทธิภาพ
- **สตรีมที่ใช้หน่วยความจำอย่างมีประสิทธิภาพ:** แนะนำวิธีสตรีมสำหรับเอกสารขนาดใหญ่ (>50 MB)  
- **การประมวลผลเป็นชุด:** รวมงานแยกหลายงานใน JVM เซสชันเดียวเพื่อ ลดค่าโอเวอร์เฮดการเริ่มต้น  
- **ทำความสะอาดทรัพยากร:** เรียก `merger.close()` และปิดสตรีมทั้งหมดเพื่อป้องกันการรั่วไหล  

## สรุป
ตอนนี้คุณรู้ **วิธีการแยก docx** เป็นไฟล์แยกหรือสตรีมในหน่วยความจำด้วย GroupDocs.Merger สำหรับ Java เทคนิคเหล่านี้ให้ความยืดหยุ่นในการจัดส่งเอกสารตามความต้องการของธุรกิจใด ๆ

**ขั้นตอนต่อไป**
- ทดลองใช้ช่วงหน้าต่าง ๆ และรูปแบบผลลัพธ์ต่าง ๆ (PDF, HTML ฯลฯ)  
- ผสานการแยกกับการรวมเพื่อสร้างแพคเกจแบบกำหนดเองแบบเรียลไทม์  

## คำถามที่พบบ่อย

**ถาม: GroupDocs.Merger สำหรับ Java คืออะไร?**  
ตอบ: เป็นไลบรารี Java ที่ช่วยให้ทำการรวม, แยก, และแปลงรูปแบบเอกสารหลากหลาย รวมถึง DOCX, PDF, PPTX ฯลฯ  

**ถาม: จะขอไลเซนส์สำหรับ GroupDocs.Merger ได้อย่างไร?**  
ตอบ: คุณสามารถรับไลเซนส์ทดลองชั่วคราวจาก [GroupDocs website](https://purchase.groupdocs.com/temporary-license/) เพื่อการประเมินค่าใช้จ่าย สำหรับการใช้งานจริงให้ซื้อไลเซนส์เต็มที่เว็บไซต์เดียวกัน  

**ถาม: สามารถแยกไฟล์ PDF ด้วย API เดียวกันได้หรือไม่?**  
ตอบ: ได้, เมธอด `split` ทำงานกับ PDF, DOCX, PPTX และรูปแบบที่รองรับอื่น ๆ  

**ถาม: สามารถแยกเอกสารโดยไม่เขียนลงดิสก์ได้หรือไม่?**  
ตอบ: แน่นอน—ใช้วิธีแยกแบบสตรีมตามที่แสดงด้านบนเพื่อเก็บทั้งหมดในหน่วยความจำ  

**ถาม: ควรใช้เวอร์ชันของ GroupDocs.Merger ใด?**  
ตอบ: ควรใช้เวอร์ชันเสถียรล่าสุดเสมอเพื่อรับประโยชน์จากการปรับปรุงประสิทธิภาพและการแก้ไขบั๊ก  

---

**อัปเดตล่าสุด:** 2026-02-06  
**ทดสอบกับ:** GroupDocs.Merger for Java เวอร์ชันล่าสุด  
**ผู้เขียน:** GroupDocs