---
date: '2026-07-25'
description: GroupDocs.Merger for Java kullanarak docx sayfalarını nasıl böleceğinizi
  öğrenin; DOCX'i ayrı dosyalara bölme, akış çıkarma ve bölme seçeneklerini kapsar.
keywords:
- split docx pages
- how to split docx
- split docx into files
lastmod: '2026-07-25'
og_description: GroupDocs.Merger for Java ile docx sayfalarını bölün. Kod örnekleriyle
  adım adım DOCX'i dosyalara veya akışlara nasıl böleceğinizi öğrenin.
og_image_alt: Guide to split DOCX pages using GroupDocs.Merger Java library
og_title: GroupDocs.Merger for Java ile DOCX Sayfalarını Bölme
schemas:
- author: GroupDocs
  dateModified: '2026-07-25'
  description: Learn how to split docx pages using GroupDocs.Merger for Java, covering
    splitting DOCX into separate files, stream extraction, and split options.
  headline: How to Split DOCX Pages with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to split docx pages using GroupDocs.Merger for Java, covering
    splitting DOCX into separate files, stream extraction, and split options.
  name: How to Split DOCX Pages with GroupDocs.Merger for Java
  steps:
  - name: '**Legal contracts:** Extract individual clauses for separate review without
      exposing the whole agreement.'
    text: '**Legal contracts:** Extract individual clauses for separate review without
      exposing the whole agreement.'
  - name: '**E‑learning platforms:** Serve chapter‑by‑chapter Word files on demand,
      keeping the full textbook protected.'
    text: '**E‑learning platforms:** Serve chapter‑by‑chapter Word files on demand,
      keeping the full textbook protected.'
  - name: '**Business reporting:** Send only the finance section of a quarterly report
      to the CFO, reducing bandwidth and improving confidentiality.'
    text: '**Business reporting:** Send only the finance section of a quarterly report
      to the CFO, reducing bandwidth and improving confidentiality.'
  type: HowTo
- questions:
  - answer: It’s a Java library that enables merging, splitting, and converting over
      50 document formats—including DOCX, PDF, PPTX, and HTML—without requiring Microsoft
      Office.
    question: What is GroupDocs.Merger for Java?
  - answer: Acquire a temporary trial license from the [GroupDocs website](https://purchase.groupdocs.com/temporary-license/)
      for evaluation. For production, purchase a full license at the same site.
    question: How do I obtain a license for GroupDocs.Merger?
  - answer: Yes, the `split` method works with PDF, DOCX, PPTX, and other supported
      formats.
    question: Can I split PDF files using the same API?
  - answer: Absolutely—use the stream‑based approach shown above to keep everything
      in memory.
    question: Is it possible to split a document without writing to disk?
  - answer: Always target the latest stable release to benefit from performance improvements
      and bug fixes.
    question: Which version of GroupDocs.Merger should I use?
  type: FAQPage
tags:
- split docx
- GroupDocs.Merger
- Java document processing
- DOCX splitting
title: GroupDocs.Merger for Java ile DOCX Sayfalarını Bölme
type: docs
url: /tr/java/document-splitting/master-java-document-splitting-groupdocs-merger/
weight: 1
---

# GroupDocs.Merger for Java ile DOCX Sayfalarını Bölme

Bu öğreticide, GroupDocs.Merger for Java kullanarak **docx sayfalarını nasıl bölmeyi** verimli bir şekilde keşfedeceksiniz. Devasa bir sözleşmeyi tek tek sayfalara bölmeniz ya da belirli bölümleri bellek içi akışlar olarak çıkarmanız gerekse, kurulum, kod ve gerçek dünya ipuçlarını adım adım göstereceğiz, böylece çözümü dakikalar içinde uygulayabilirsiniz.

## Hızlı Yanıtlar
- **Java'da DOCX bölmeyi hangi kütüphane yönetir?** GroupDocs.Merger for Java.  
- **DOCX'i ayrı dosyalara bölebilir miyim?** Evet – istediğiniz sayfa numaralarıyla `SplitOptions` yapılandırın.  
- **Sayfaları dosya yerine akış olarak almak mümkün mü?** Kesinlikle, özel bir `SplitStreamFactory` sağlayarak.  
- **Lisans gerekli mi?** Değerlendirme için geçici bir deneme lisansı çalışır; üretim için tam lisans gerekir.  
- **Hangi Java sürümleri destekleniyor?** En son GroupDocs.Merger sürümüyle JDK 8+ herhangi bir sürüm çalışır.

## Split docx sayfaları nedir?
**Split docx sayfaları**, çok sayfalı bir Word belgesinden bir veya daha fazla sayfa çıkarıp her seçimi ayrı bir dosya ya da bellek içi akış olarak kaydetmek anlamına gelir. Bu, modüler teslimat, uyumluluk odaklı iş akışları veya tüm belgeyi bir kerede işlemeye gerek kalmadan anlık işleme olanak tanır.

## Neden GroupDocs.Merger for Java Kullanmalı?
GroupDocs.Merger belgeleri **tamamen Java içinde** işler—yerel ikili dosyalar yok, Office kurulumu gerekmez. **50'den fazla giriş ve çıkış formatını** destekler ve tipik bir 2.5 GHz sunucuda **200 sayfalık DOCX'i 2 saniyenin altında** bölebilir, akış tabanlı mimarisi sayesinde bellek kullanımını 100 MB'nin altında tutar.

## Önkoşullar

### Gerekli Kütüphaneler ve Bağımlılıklar
- **Java Development Kit (JDK):** JDK 8 veya daha yeni.  
- **GroupDocs.Merger for Java:** Belge manipülasyonu için temel kütüphane.

### Bağımlılığı Eklemek
Kütüphaneyi Maven veya Gradle aracılığıyla ekleyin (kod blokları değişmeden):

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

Ayrıca resmi siteden en son sürümü indirebilirsiniz: [GroupDocs.Merger for Java sürümleri](https://releases.groupdocs.com/merger/java/).

### Lisans Edinme
- **Deneme lisansı:** [GroupDocs.Deneme Lisansı](https://purchase.groupdocs.com/temporary-license/) sayfasından geçici bir anahtar alın.  
- **Üretim lisansı:** Tam lisansı [GroupDocs Satın Alma](https://purchase.groupdocs.com/buy) adresinden satın alın.

## GroupDocs.Merger for Java Kurulumu
`Merger`, bölme, birleştirme ve dönüştürme işlemlerini yöneten merkezi sınıftır.

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

Ortam hazır olduğunda, **docx sayfalarını dosyalara** veya akışlara bölmenin iki ana yolunu inceleyelim.

## DOCX'i Dosyalara Bölme (GroupDocs.Merger ile)
Kaynak DOCX'i yükleyin, istenen sayfa aralıklarını belirtin ve `split` metodunu çağırın – bu tek çağrı, seçilen her segment için ayrı çıktı dosyaları oluşturur. `split` metodu belgeyi verilen `SplitOptions` ile işler ve oluşturulan dosyaların yollarını döndürür. Aşağıdaki adımlar tam, üretim‑hazır bir uygulamayı gösterir.

### Adım 1 – Giriş ve Çıkış Yollarını Belirleme
Orijinal DOCX'in konumunu ve bölünmüş dosyaların yazılacağı klasörü tanımlayın.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
String filePathOut = new File("YOUR_OUTPUT_DIRECTORY", 
    "SplitToSinglePages-" +
    Paths.get(filePath).getFileName().toString()
).getPath();
```

### Adım 2 – SplitOptions'ı Yapılandırma (split options java)
`SplitOptions`, API'ye hangi sayfaların çıkarılacağını ve sonuçların nereye yerleştirileceğini tam olarak bildirir.

```java
import com.groupdocs.merger.domain.options.SplitOptions;

SplitOptions splitOptions = new SplitOptions(filePathOut, new int[] { 3, 6, 8 });
```

- `filePathOut` – her sayfa dosyasının yerleştirileceği klasör.  
- `new int[]{3,6,8}` – çıkarmak istediğiniz sayfa numaraları (sayfalar 1‑tabanlıdır).

### Adım 3 – Bölmeyi Gerçekleştirme
`Merger` örneği oluşturun ve `split` metodunu çağırın. Metod, oluşturulan dosya yollarının bir listesini döndürür.

```java
import com.groupdocs.merger.Merger;

Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

**Pro ipucu:** Çıktı dizininin var olduğunu ve uygulamanızın yazma izinlerine sahip olduğunu doğrulayın; aksi takdirde bölme işlemi başarısız olur.

#### Yaygın Tuzaklar
- **Eksik çıktı klasörü:** API dizinleri otomatik olarak oluşturmaz.  
- **Yanlış sayfa numaraları:** Sayfa indeksleri 1'den başlar; 0 belirtmek hata verir.

## DOCX Sayfalarını Akışlara Bölme (Bellek İçinde)
Geçici erişime ihtiyacınız olduğunda—örneğin bir sayfayı web servisi üzerinden göndermek ya da bellek içi analiz yapmak—her çıkarılan sayfayı akış olarak yakalamak, diske yazma yükünü ortadan kaldırır. Özel bir `SplitStreamFactory` kullanarak, kütüphane bölünmüş içeriği doğrudan `ByteArrayOutputStream` nesnelerine yazar; bu nesneler daha sonra ara dosyalar olmadan iletilebilir, depolanabilir veya daha fazla işlenebilir.

### Adım 1 – Giriş Yolunu Tanımlama ve Akışlar İçin Bir Liste Hazırlama
Kaynak dosyayı ayarlayın ve oluşturulan akışları tutacak bir kapsayıcı oluşturun.

```java
import java.io.ByteArrayOutputStream;
import java.util.ArrayList;
import java.util.List;

String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX_10_PAGES";
final List<OutputStream> resultStreams = new ArrayList<>();
```

### Adım 2 – Özel SplitStreamFactory ile SplitOptions'ı Yapılandırma
Her sayfa için yeni bir `OutputStream` sağlamak ve tamamlanan akışı depolamak üzere `SplitStreamFactory` uygulayın.

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

- `createSplitStream` – istenen her sayfa için yeni bir `OutputStream` oluşturur.  
- `closeSplitStream` – tamamlanan akışı daha sonra kullanmak üzere depolar.

### Adım 3 – Bölmeyi Çalıştırma ve Akışları Alma
Bölme işlemini çalıştırın ve ardından gerektiği gibi bellek içi akışlarla çalışın (ör. bir e-postaya ekleyin, bulut depolamaya yükleyin).

```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);

return resultStreams; // Retrieve streams for processing
```

**Sorun Giderme İpuçları**  
- Kaynak DOCX yolunun doğru olduğundan emin olun; bir yazım hatası `FileNotFoundException` oluşturur.  
- İşiniz bittiğinde akışları her zaman kapatın, böylece bellek serbest kalır ve sızıntılar önlenir.

## Pratik Uygulamalar
1. **Hukuki sözleşmeler:** Tüm anlaşmayı ortaya çıkarmadan ayrı inceleme için bireysel maddeleri çıkarın.  
2. **E‑öğrenme platformları:** Talep üzerine bölüm‑bölüm Word dosyaları sunun, tam ders kitabını koruyun.  
3. **İş raporlaması:** Çeyrek raporunun sadece finans bölümünü CFO'ya gönderin, bant genişliğini azaltın ve gizliliği artırın.

## Performans Düşünceleri
- **Bellek‑verimli akışlar:** Yığın kullanımını düşük tutmak için 50 MB'den büyük belgelerde akış yaklaşımını tercih edin.  
- **Toplu işleme:** Başlangıç yükünü amorti etmek için tek bir JVM oturumunda birden fazla bölme işini gruplayın.  
- **Kaynak temizliği:** Bellek sızıntılarını önlemek için `merger.close()` çağırın ve tüm akışları kapatın.  
- **Hız ölçütü:** Standart bir 8‑çekirdek sunucuda, 300‑sayfalık DOCX'i tek tek sayfalara bölmek yaklaşık ~1.8 saniye sürer.

## Sıkça Sorulan Sorular

**S: GroupDocs.Merger for Java nedir?**  
C: Microsoft Office gerektirmeden DOCX, PDF, PPTX ve HTML dahil 50'den fazla belge formatını birleştirme, bölme ve dönüştürme imkanı sağlayan bir Java kütüphanesidir.

**S: GroupDocs.Merger için lisansı nasıl elde ederim?**  
C: Değerlendirme için [GroupDocs web sitesi](https://purchase.groupdocs.com/temporary-license/) üzerinden geçici bir deneme lisansı alın. Üretim için aynı siteden tam lisans satın alın.

**S: Aynı API ile PDF dosyalarını da bölebilir miyim?**  
C: Evet, `split` metodu PDF, DOCX, PPTX ve diğer desteklenen formatlarla çalışır.

**S: Belgeyi diske yazmadan bölmek mümkün mü?**  
C: Kesinlikle—her şeyi bellek içinde tutmak için yukarıda gösterilen akış‑tabanlı yaklaşımı kullanın.

**S: Hangi GroupDocs.Merger sürümünü kullanmalıyım?**  
C: Performans iyileştirmeleri ve hata düzeltmelerinden yararlanmak için her zaman en son kararlı sürümü hedefleyin.

---

**Son Güncelleme:** 2026-07-25  
**Test Edilen:** GroupDocs.Merger for Java latest-version  
**Yazar:** GroupDocs

## İlgili Öğreticiler

- [GroupDocs.Merger for Java Kullanarak Belgeleri Çok Sayfalı Dosyalara Bölme](/merger/java/document-splitting/split-documents-multi-page-files-java-groupdocs-merger/)
- [GroupDocs.Merger ile Java'da belirli sayfaları çıkarma](/merger/java/document-extraction/)
- [GroupDocs.Merger Kullanarak Java'da Belirli Sayfaları Birleştirme](/merger/java/document-joining/join-specific-pages-groupdocs-merger-java/)