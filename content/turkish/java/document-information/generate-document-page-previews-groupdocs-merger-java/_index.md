---
date: '2026-06-26'
description: GroupDocs.Merger for Java kullanarak pdf sayfalarını görsellere dönüştürmeyi
  ve belgeleri önizlemeyi öğrenin – sayfa küçük resimleri oluşturmanın hızlı ve güvenilir
  yolu.
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
title: PDF Sayfalarını Görsellere Dönüştürme ve Belgeleri Önizleme – GroupDocs.Merger
  for Java ile
type: docs
url: /tr/java/document-information/generate-document-page-previews-groupdocs-merger-java/
weight: 1
---

# PDF Sayfalarını Görsellere Dönüştürme ve GroupDocs.Merger for Java ile Belgeleri Önizleme

Modern uygulamalarda, kullanıcıların tüm dosyayı indirmeden bir belgeye göz atabilmeleri için genellikle **pdf sayfalarını görsellere dönüştürmek** gerekir. Bu öğretici, GroupDocs.Merger for Java ile yüksek kaliteli sayfa önizlemeleri oluşturmayı, kurulumdan özel depolama yönetimine kadar her şeyi adım adım gösterir. Sonunda, JDK 8+ ortamında çalışan belge küçük resim oluşturma için yeniden kullanılabilir bir çözüme sahip olacaksınız.

## Hızlı Yanıtlar
- **“preview documents” ne anlama geliyor?** Her sayfanın hafif görüntü temsillerini oluşturma.  
- **Önizlemeler için hangi format kullanılır?** Varsayılan olarak JPEG, ancak diğer formatlar da desteklenir.  
- **Lisans gerekli mi?** Geliştirme için ücretsiz deneme çalışır; üretim için ücretli lisans gerekir.  
- **Çıktı yolunu özelleştirebilir miyim?** Evet, özel bir `PageStreamFactory` uygulayarak.  
- **Hangi Java sürümü gerekiyor?** JDK 8 veya üzeri.

## “Belgeleri önizleme” nedir?
Belge önizleme, her sayfa için görsel küçük resimler (genellikle JPEG veya PNG) oluşturmak anlamına gelir, böylece kullanıcılar içeriği hızlıca gözden geçirebilir. Bu teknik, dosya tarayıcıları, içerik‑inceleme portalları ve büyük sayıda belge yöneten herhangi bir sistemde kullanıcı deneyimini artırır, tam dosyayı açmadan hızlı bir görsel ipucu sağlar.

## GroupDocs.Merger for Java neden kullanılmalı?
GroupDocs.Merger, tipik bir 2 GHz CPU'da **sayfa başına 0.5 saniyenin altında** PDF sayfalarını görsellere dönüştürür, **50+ giriş ve çıkış formatını** destekler ve önizlemeleri tüm dosyayı belleğe yüklemeden doğrudan depolamaya akıtmanıza olanak tanır. Genişletilebilir API'si, görüntü kalitesi, format ve hedef yol üzerinde tam kontrol sağlar.

## Önkoşullar
- **GroupDocs.Merger for Java** kütüphanesi (aşağıdaki kurulum bölümüne bakın).  
- **JDK 8+** makinenizde kurulu olmalı.  
- Bir IDE (IntelliJ IDEA, Eclipse, NetBeans) ve bağımlılık yönetimi için Maven veya Gradle.

## GroupDocs.Merger for Java'ı Kurma
Tercih ettiğiniz derleme aracını kullanarak kütüphaneyi projenize ekleyin.

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

**Direct Download:**  
Alternatively, download the latest version from [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Lisans Alımı
- **Free Trial:** Özellikleri keşfetmek için ücretsiz deneme sürümünü indirin.  
- **Temporary License:** Geliştirme sırasında genişletilmiş erişim için geçici bir lisans edinin.  
- **Purchase:** Tam üretim kullanımı için [GroupDocs](https://purchase.groupdocs.com/buy) adresinden lisans satın alın.

Kütüphane eklendikten sonra, önizlemek istediğiniz belgenin yolu ile başlatın:

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

## Belgeleri Önizleme: Adım Adım Kılavuz
Kaynak dosyayı yükleyin, bir `PageStreamFactory` yapılandırın ve `generatePreview` metodunu çağırın.  
`generatePreview`, sağlanan seçeneklere göre her belge sayfasını bir görsele dönüştüren bir yöntemdir.

### Adım 1: Merger'ı Başlatma ve PageStreamFactory Tanımlama
`Merger`, belgeleri birleştirme, bölme ve önizleme oluşturma yöntemlerini sağlayan temel sınıftır.  
`PageStreamFactory`, kütüphaneye her önizleme görselinin nereye yazılacağını belirten bir arayüzdür.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

Burada, her sayfa görselini öngörülebilir bir adlandırma şemasıyla belirli bir klasöre yazan özel bir uygulama oluşturuyoruz.

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

### Adım 2: Önizlemeleri Oluşturma
`generatePreview`, sağladığınız seçeneklere göre dönüşüm sürecini başlatır. Her sayfa görselini tanımladığınız `PageStreamFactory`'ye akıtarak düşük bellek kullanımını sağlar.

```java
merger.generatePreview(previewOption);
```

### Sayfaları Görsellere Dönüştürme – Özel PageStreamFactory
Dosya adlandırması veya depolama konumu üzerinde daha fazla kontrol ihtiyacınız varsa, kendi fabrikasını uygulayın:

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

### Yardımcı Metodlar – Akışları Yönetme
Bu yardımcı metodlar kodu düzenli tutar ve istisnaları temiz bir şekilde yönetir.

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

## Belge Küçük Resim Oluşturma – Pratik Uygulamalar
Önizlemeler oluşturmak özellikle şu durumlarda faydalıdır:

1. **Document Management Systems** – Kullanıcılar dosyaları açmadan göz atabilir.  
2. **Content Review Platforms** – Yüklemeleri onaylamadan önce hızlı görsel kontroller.  
3. **Educational Tools** – Öğrenciler ders slaytlarına veya ders kitabı sayfalarına göz atabilir.  

## Performans Düşünceleri
- **Akışları zamanında serbest bırakın** belleği boşaltmak için.  
- **Tüm belgeleri belleğe yüklemekten kaçının**; kütüphane sayfalama işlemini yapsın.  
- **Uygun görüntü kalitesi** ayarlarını kullanarak hız ve görsel doğruluk arasında denge kurun.  

## Sık Sorulan Sorular

**S: GroupDocs.Merger for Java ne için kullanılır?**  
C: Belgeleri verimli bir şekilde birleştirme, bölme ve yönetme, ayrıca önizleme oluşturma ve format dönüştürme için kullanılır.

**S: Akış işlemleri sırasında istisnaları nasıl yönetirim?**  
C: Yardımcı metodlarda gösterildiği gibi, akış oluşturma ve kapatma işlemlerini try‑catch bloklarıyla sararak bellek sızıntılarını önleyin.

**S: JPEG dışındaki formatlarda önizleme oluşturabilir miyim?**  
C: Evet, `PreviewMode` enum'ını PNG, BMP veya TIFF olarak değiştirerek gereksinimlerinize uygun hale getirebilirsiniz.

**S: Belge önizleme oluştururken yaygın sorunlar nelerdir?**  
C: Tipik problemler arasında hatalı dosya yolları ve akışların kapatılmayı unutması bulunur; bu durum bellek sızıntılarına yol açabilir.

**S: GroupDocs.Merger'ı diğer sistemlerle nasıl entegre edebilirim?**  
C: API'sini kullanarak veritabanları, web servisleri veya diğer Java uygulamalarıyla bağlanabilir ve sorunsuz iş akışı otomasyonu sağlayabilirsiniz.

---

## Kaynaklar
- [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/)  
- [Download](https://releases.groupdocs.com/merger/java/)  
- [Documentation](https://docs.groupdocs.com/merger/java/)  
- [API Reference](https://reference.groupdocs.com/merger/java/)  
- [Free Trial](https://releases.groupdocs.com/merger/java/)  
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- [Purchase](https://purchase.groupdocs.com/buy)  
- [GroupDocs](https://purchase.groupdocs.com/buy)  
- [Support](https://forum.groupdocs.com/c/merger/)

**Son Güncelleme:** 2026-06-26  
**Test Edilen:** GroupDocs.Merger son sürüm (2025‑latest)  
**Yazar:** GroupDocs

## İlgili Eğitimler

- [Document Page Operations Tutorials for GroupDocs.Merger Java](/merger/java/page-operations/)
- [How to Load a PDF from a URL Using GroupDocs.Merger for Java: A Comprehensive Guide](/merger/java/document-loading/load-pdf-url-groupdocs-merger-java/)
- [Create Single Page PDF with GroupDocs.Merger Java](/merger/java/document-splitting/)