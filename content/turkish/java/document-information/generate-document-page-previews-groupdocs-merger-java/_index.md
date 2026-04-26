---
date: '2026-01-24'
description: GroupDocs.Merger for Java ile sayfa önizlemeleri oluşturarak belgeleri
  önizlemeyi öğrenin; sayfaları görüntülere dönüştürerek belge küçük resimleri oluşturmanın
  hızlı bir yoludur.
keywords:
- GroupDocs.Merger for Java
- document page previews
- Java document management
title: GroupDocs.Merger for Java ile Belgeleri Önizleme
type: docs
url: /tr/java/document-information/generate-document-page-previews-groupdocs-merger-java/
weight: 1
---

# GroupDocs.Merger for Java ile Belgeleri Önizleme

Belge sayfa önizlemeleri oluşturmak, **belgeleri önizleme** işlemini hızlı bir şekilde yapmanın güçlü bir yoludur; kullanıcıya tam dosyayı açmadan görsel bir anlık görüntü sunar. Bu öğreticide, GroupDocs.Merger for Java kullanarak bu önizlemeleri nasıl oluşturacağınızı öğreneceksiniz; bu kütüphane **sayfaları görüntülere dönüştürmeyi** ve uygulamalarınızda **belge küçük resim oluşturmayı** kolaylaştırır.

## Hızlı Yanıtlar
- **“preview documents” ne anlama geliyor?** Her sayfanın hafif görüntü temsillerini oluşturmak.  
- **Önizlemeler için hangi format kullanılıyor?** Varsayılan olarak JPEG, ancak diğer formatlar da desteklenir.  
- **Lisans gerekli mi?** Geliştirme için ücretsiz deneme çalışır; üretim için ücretli lisans gerekir.  
- **Çıktı yolunu özelleştirebilir miyim?** Evet, özel bir `PageStreamFactory` uygulayarak.  
- **Hangi Java sürümü gerekiyor?** JDK 8 veya üzeri.

## “Belge önizleme” nedir?
Belgeleri önizlemek, her sayfa için görsel küçük resimler (genellikle JPEG veya PNG) oluşturmak anlamına gelir; böylece kullanıcılar içeriği hızlıca gözden geçirebilir. Bu teknik, belge yönetim sistemlerinde, portalarda ve çok sayıda dosya işleyen herhangi bir uygulamada kullanıcı deneyimini artırır.

## Neden GroupDocs.Merger for Java kullanmalı?
- **Hızlı dönüşüm** sayfaları tam belgeyi UI'da açmadan görüntülere.  
- **Yerleşik destek** birçok format için (PDF, DOCX, XLSX, vb.).  
- **Genişletilebilir API** önizleme dosyalarının nerede ve nasıl kaydedileceğini kontrol etmenizi sağlar.

## Önkoşullar
- **GroupDocs.Merger for Java** kütüphanesi (aşağıdaki kuruluma bakın).  
- **JDK 8+** makinenizde kurulu.  
- Bir IDE (IntelliJ IDEA, Eclipse, NetBeans) ve bağımlılık yönetimi için Maven veya Gradle.

## GroupDocs.Merger for Java Kurulumu
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

**Doğrudan İndirme:**  
Alternatif olarak, en son sürümü [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/) adresinden indirin.

### Lisans Alımı
- **Ücretsiz Deneme:** Özellikleri keşfetmek için ücretsiz deneme sürümünü indirin.  
- **Geçici Lisans:** Geliştirme sırasında genişletilmiş erişim için geçici bir lisans alın.  
- **Satın Alma:** Tam üretim kullanımı için [GroupDocs](https://purchase.groupdocs.com/buy) adresinden lisans satın alın.

Kütüphane eklendikten sonra, önizlemek istediğiniz belgenin yolu ile başlatın:

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

## Belgeleri Önizleme: Adım Adım Kılavuz

### Adım 1: Merger'ı Başlatın ve bir PageStreamFactory Tanımlayın
`PageStreamFactory`, her önizleme görüntüsünün nereye yazılacağını kütüphaneye bildirir.

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

### Adım 2: Önizlemeleri Oluşturun
Az önce yapılandırdığınız seçeneklerle `generatePreview` metodunu çağırın.

```java
merger.generatePreview(previewOption);
```

### Sayfaları Görüntülere Dönüştür – Özel PageStreamFactory
Dosya adlandırması veya depolama konumu üzerinde daha fazla kontrol gerekiyorsa, kendi fabrikanızı uygulayın:

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
Bu yardımcı metodlar kodu düzenli tutar ve istisnaları temiz bir şekilde ele alır.

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

1. **Belge Yönetim Sistemleri** – Kullanıcılar dosyaları açmadan gözden geçirebilir.  
2. **İçerik İnceleme Platformları** – Yüklemeleri onaylamadan önce hızlı görsel kontroller.  
3. **Eğitim Araçları** – Öğrenciler ders slaytlarına veya ders kitabı sayfalarına göz atabilir.

## Performans Düşünceleri
- **Akışları hızlıca serbest bırakın** belleği boşaltmak için.  
- **Tüm belgeleri belleğe yüklemekten kaçının**; kütüphanenin sayfalama yapmasına izin verin.  
- **Uygun görüntü kalitesi** ayarlarını kullanarak hız ve görsel doğruluk arasında denge kurun.

## Sıkça Sorulan Sorular

**Q:** GroupDocs.Merger for Java ne için kullanılır?  
**A:** Belgeleri verimli bir şekilde birleştirmek, bölmek ve yönetmek için kullanılır; ayrıca önizleme oluşturmayı da kapsar.

**Q:** Akış işlemleri sırasında istisnaları nasıl yönetirim?  
**A:** Yardımcı metodlarda gösterildiği gibi, akış oluşturma ve kapatma işlemlerini try‑catch bloklarıyla sarın.

**Q:** JPEG dışındaki formatlarda önizleme oluşturabilir miyim?  
**A:** Evet, ihtiyaçlarınıza göre `PreviewMode` enum'ını PNG, BMP vb. olarak değiştirin.

**Q:** Belge önizleme oluştururken yaygın sorunlar nelerdir?  
**A:** Tipik problemler arasında hatalı dosya yolları ve akışların kapatılmaması bulunur; bu durum bellek sızıntılarına yol açabilir.

**Q:** GroupDocs.Merger'ı diğer sistemlerle nasıl entegre edebilirim?  
**A:** API'sini kullanarak veritabanları, web servisleri veya diğer Java uygulamalarıyla bağlanabilir ve sorunsuz iş akışı otomasyonu sağlayabilirsiniz.

## Ek Kaynaklar
- [Dokümantasyon](https://docs.groupdocs.com/merger/java/)
- [API Referansı](https://reference.groupdocs.com/merger/java/)
- [İndirme](https://releases.groupdocs.com/merger/java/)
- [Satın Alma](https://purchase.groupdocs.com/buy)
- [Ücretsiz Deneme](https://releases.groupdocs.com/merger/java/)
- [Geçici Lisans](https://purchase.groupdocs.com/temporary-license/)
- [Destek](https://forum.groupdocs.com/c/merger/)

---

**Son Güncelleme:** 2026-01-24  
**Test Edilen Versiyon:** GroupDocs.Merger latest version (2025‑latest)  
**Yazar:** GroupDocs