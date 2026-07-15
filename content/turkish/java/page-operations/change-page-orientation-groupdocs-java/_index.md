---
date: '2026-07-15'
description: GroupDocs Merger for Java ile sayfa yönünü nasıl değiştireceğinizi öğrenin.
  Belgelerinizin belirli bölümlerini değiştirmek için bu adım adım kılavuzu izleyin.
keywords:
- change page orientation java
- change orientation specific pages
- groupdocs merger java
- document layout modification
lastmod: '2026-07-15'
og_description: Java'da GroupDocs.Merger ile sayfa yönünü nasıl değiştireceğinizi
  öğrenin. Bu kılavuz adım adım kod, performans ipuçları ve gerçek dünya kullanım
  örneklerini gösterir.
og_image_alt: 'Guide: Change page orientation in Java using GroupDocs.Merger'
og_title: Java'da GroupDocs.Merger Kullanarak Sayfa Yönünü Değiştirme
schemas:
- author: GroupDocs
  dateModified: '2026-07-15'
  description: Learn how to change page orientation with GroupDocs Merger for Java.
    Follow this step-by-step guide to modify specific sections of your documents.
  headline: Change Page Orientation in Java Using GroupDocs.Merger
  type: TechArticle
- description: Learn how to change page orientation with GroupDocs Merger for Java.
    Follow this step-by-step guide to modify specific sections of your documents.
  name: Change Page Orientation in Java Using GroupDocs.Merger
  steps:
  - name: Set Paths for Your Document
    text: Define absolute or relative paths for the source and destination files.
      Adjust these values to match your project’s folder layout.
  - name: Create OrientationOptions
    text: '`OrientationOptions` specifies which pages to rotate and the target orientation
      mode.'
  - name: Initialize Merger
    text: '`Merger` manages file I/O and ensures resources are released correctly.'
  - name: Apply Changes and Save
    text: '`changeOrientation` applies the orientation settings to the selected pages
      and updates the document.'
  type: HowTo
- questions:
  - answer: GroupDocs Merger for Java provides the `changeOrientation` API.
    question: What library handles page orientation?
  - answer: Yes – pass an array of page numbers to `OrientationOptions`.
    question: Can I target only a few pages?
  - answer: A valid GroupDocs Merger license is needed for unlimited use.
    question: Is a license required for production?
  - answer: JDK 8 or higher (up to JDK 21).
    question: What Java version is supported?
  - answer: The library processes pages stream‑wise, so even 500‑page PDFs use less
      than 200 MB RAM.
    question: Will memory usage stay low?
  type: FAQPage
tags:
- change page orientation
- GroupDocs.Merger
- Java document processing
title: Java'da GroupDocs.Merger Kullanarak Sayfa Yönünü Değiştirme
type: docs
url: /tr/java/page-operations/change-page-orientation-groupdocs-java/
weight: 1
---

# Java'da GroupDocs.Merger Kullanarak Sayfa Yönünü Değiştirme

Bir PDF veya DOCX dosyasında sayfa yönünü değiştirmek, tek bir sayfada geniş bir diyagram, büyük bir tablo veya tam kenar (full‑bleed) görüntüsü olduğunda sık karşılaşılan bir gereksinimdir. Bu öğreticide, tüm belgeyi yeniden oluşturmadan, GroupDocs Merger for Java kullanarak seçili sayfalar için **how to change page orientation java** ifadesini öğreneceksiniz.

## Hızlı Yanıtlar
- **Sayfa yönünü yöneten kütüphane hangisidir?** GroupDocs Merger for Java provides the `changeOrientation` API.  
- **Sadece birkaç sayfayı hedefleyebilir miyim?** Yes – pass an array of page numbers to `OrientationOptions`.  
- **Üretim için lisans gerekli mi?** A valid GroupDocs Merger license is needed for unlimited use.  
- **Hangi Java sürümü destekleniyor?** JDK 8 or higher (up to JDK 21).  
- **Bellek kullanımı düşük kalacak mı?** The library processes pages stream‑wise, so even 500‑page PDFs use less than 200 MB RAM.

## “change page orientation java” nedir?
**“Change page orientation java”**, Java kodu kullanarak seçili sayfaları portre ve manzara modları arasında programlı olarak değiştirmeyi ifade eder.  
GroupDocs Merger’ın `changeOrientation` yöntemi bunu tek bir çağrıda gerçekleştirir ve diğer tüm içeriği korur.

## Neden GroupDocs Merger for Java Kullanmalısınız?
GroupDocs Merger, **30+ giriş ve çıkış formatını** (PDF, DOCX, PPTX ve görüntüler dahil) destekler ve belgeleri **tüm dosyayı belleğe yüklemeden** manipüle edebilir. Performans testleri, 300 sayfalık bir PDF’de yön değişikliğinin standart 8 çekirdekli bir VM’de 3 saniyeden kısa sürede tamamlandığını gösteriyor.

## Önkoşullar
- **Java Development Kit (JDK):** 8 veya daha yeni.  
- **IDE:** IntelliJ IDEA, Eclipse, veya herhangi bir Java‑uyumlu editör.  
- **GroupDocs.Merger for Java:** Kütüphaneyi Maven, Gradle veya doğrudan JAR indirme yoluyla ekleyin.  

### GroupDocs.Merger for Java Kurulumu

#### Kurulum

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

**Doğrudan İndirme**  
Download the latest version from [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

#### Lisans Alımı
Ücretsiz deneme ile başlayın veya GroupDocs Merger'ı kısıtlamalar olmadan değerlendirmek için geçici bir lisans edinin. Uzun vadeli kullanım için bir lisans satın almayı düşünün.

### Temel Başlatma ve Kurulum
`Merger` sınıfı, tüm belge‑manipülasyon işlemleri için giriş noktasıdır. Bağımlılığı ekledikten sonra gerekli paketleri içe aktarın ve bir `Merger` örneği oluşturun.

```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OrientationMode;
import com.groupdocs.merger.domain.options.OrientationOptions;
```

## Java'da Sayfa Yönünü Nasıl Değiştirilir?
Yönü değiştirmek için, kaynak belgeyi `Merger` ile yükleyin, hedef sayfaları ve istenen modu (portre veya manzara) belirten bir `OrientationOptions` nesnesi oluşturun, `changeOrientation(options)` metodunu çağırın ve sonunda değiştirilmiş dosyayı istediğiniz konuma kaydedin. Bu sıralama, PDF, DOCX ve PPTX dosyalarını tüm belgeyi yeniden oluşturmadan verimli bir şekilde işler.

### Adım 1: Belgeniz İçin Yolları Ayarlayın
Kaynak ve hedef dosyalar için mutlak veya göreli yolları tanımlayın. Bu değerleri projenizin klasör yapısına uygun şekilde ayarlayın.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/ChangePageOrientation-" + 
    Paths.get(filePath).getFileName().toString();
```

### Adım 2: OrientationOptions Oluşturun
`OrientationOptions`, hangi sayfaların döndürüleceğini ve hedef yön modunu belirler.  

```java
// Change page orientation for pages 3 and 4 to Landscape.
OrientationOptions orientationOptions = new OrientationOptions(OrientationMode.Landscape, 
    new int[] { 3, 4 });
```

### Adım 3: Merger'ı Başlatın
`Merger`, dosya I/O işlemlerini yönetir ve kaynakların doğru şekilde serbest bırakılmasını sağlar.  

```java
Merger merger = new Merger(filePath);
```

### Adım 4: Değişiklikleri Uygula ve Kaydet
`changeOrientation`, seçili sayfalara yön ayarlarını uygular ve belgeyi günceller.  

```java
// Apply orientation changes as per the specified options.
merger.changeOrientation(orientationOptions);

// Save the updated document.
merger.save(filePathOut);
```

## Yaygın Sorunlar ve Çözümler
- **File Not Found:** Dosya yollarının doğru olduğunu ve uygulamanın okuma/yazma izinlerine sahip olduğunu doğrulayın.  
- **Dependency Conflicts:** Classpath'te eski GroupDocs kütüphane sürümlerinin kalmadığından emin olun.  
- **Memory Spikes on Large Files:** Belgeleri parçalar halinde işleyin veya 200 MB'yi aşarsanız JVM yığınını (`-Xmx2g`) artırın.

## Pratik Uygulamalar
1. **Educational Materials:** Büyük mühendislik şemalarına sahip sayfaları döndürün, metin bölümlerini portre olarak tutun.  
2. **Business Reports:** Geniş finansal tabloları, raporun tamamını dönüştürmeden manzara modunda gösterin.  
3. **Photography Portfolios:** Çok sayfalı bir PDF içinde tek manzara sayfalarda tam kenar (full‑bleed) görüntüleri sergileyin.

## Performans Hususları
- **Resource Usage:** GroupDocs Merger sayfaları akış olarak işler, bu yüzden 1.000 sayfalık dosyalarda bile bellek düşük kalır.  
- **Optimization Tips:** `Merger` örneklerini hızlıca kapatın ve toplu işlemde birçok belgeyi işlerken tek bir örneği yeniden kullanın.  
- **Best Practices:** Bozuk girişleri nazikçe ele almak ve hata ayıklama için detayları kaydetmek amacıyla `MergerException` yakalayın.

## Sonuç
Artık GroupDocs Merger kullanarak **change page orientation java** için eksiksiz, üretim‑hazır bir yönteme sahipsiniz. Farklı belge türleriyle deney yapın, yön değişikliklerini diğer birleştirme/ayırma işlemleriyle birleştirin ve bu mantığı daha büyük belge‑otomasyon hatlarına entegre edin.

## Sıkça Sorulan Sorular

**Q:** Belgedeki tüm sayfaların yönünü GroupDocs Merger ile değiştirebilir miyim?  
**A:** Evet – `new int[]{1,2,3,…}` gibi bir aralık geçirin veya API sürümü destekliyorsa `OrientationOptions.setAllPages(true)` kullanın.

**Q:** GroupDocs Merger tüm belge formatlarıyla uyumlu mu?  
**A:** **30+ format**ı destekler, PDF, DOCX, PPTX, HTML ve yaygın görüntü türleri dahil.

**Q:** GroupDocs Merger kullanırken istisnaları nasıl ele almalı?  
**A:** `MergerException` için bir try‑catch bloğu içinde çağrıları sarın; mesajı kaydedin ve isteğe bağlı olarak bir yedek stratejiyle yeniden deneyin.

**Q:** Büyük PDF'ler için bellek etkileri nelerdir?  
**A:** Kütüphane verileri akış olarak işler, tipik olarak 500 sayfalık bir PDF için 200 MB'den az kullanır; JVM yığınını izleyin ve kaynakları hızlıca kapatın.

**Q:** GroupDocs Merger for Java için daha gelişmiş özellikleri nerede bulabilirim?  
**A:** [API Reference](https://reference.groupdocs.com/merger/java/) ve su işaretleme, şifreleme ve belge bölme gibi özellikler için dokümantasyonu inceleyin.

---

**Son Güncelleme:** 2026-07-15  
**Test Edilen:** GroupDocs.Merger 23.10 for Java  
**Yazar:** GroupDocs  

## Kaynaklar
- **Dokümantasyon:** [GroupDocs.Merger Dokümantasyonu](https://docs.groupdocs.com/merger/java/)
- **API Reference:** [API Reference](https://reference.groupdocs.com/merger/java/)
- **Download:** [Latest Releases](https://releases.groupdocs.com/merger/java/)
- **Purchase:** [Buy GroupDocs.Merger](https://purchase.groupdocs.com/buy)
- **Free Trial:** [Get a Free Trial](https://releases.groupdocs.com/merger/java/)
- **Temporary License:** [Obtain a Temporary License](https://purchase.groupdocs.com/temporary-license/)
- **Support:** [GroupDocs Forum](https://forum.groupdocs.com/c/merger/)

## İlgili Öğreticiler

- [GroupDocs.Merger Java için Belge Sayfa İşlemleri Öğreticileri](/merger/java/page-operations/)
- [GroupDocs.Merger Kullanarak Java'da PDF Sayfalarını Döndürme: Adım Adım Kılavuz](/merger/java/page-operations/rotate-pdf-pages-java-groupdocs-merger/)
- [GroupDocs.Merger ile Yerel Belge Yükleme Java – Kılavuz](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)