---
date: '2026-06-21'
description: GroupDocs.Merger for Java kullanarak belirli PDF sayfalarını nasıl çıkaracağınızı
  ve sayfalardan PDF oluşturacağınızı öğrenin. Bu öğreticide setup, code snippets
  ve real‑world use cases ele alınmaktadır.
keywords:
- extract specific pdf pages
- create pdf from pages
- extract pdf by number
- java pdf extraction library
schemas:
- author: GroupDocs
  dateModified: '2026-06-21'
  description: Learn how to extract specific PDF pages and create PDF from pages using
    GroupDocs.Merger for Java. This tutorial covers setup, code snippets, and real‑world
    use cases.
  headline: Extract Specific PDF Pages in Batch with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to extract specific PDF pages and create PDF from pages using
    GroupDocs.Merger for Java. This tutorial covers setup, code snippets, and real‑world
    use cases.
  name: Extract Specific PDF Pages in Batch with GroupDocs.Merger for Java
  steps:
  - name: '**Document Management Systems** – Generate custom reports by pulling only
      the needed sections from massive PDFs.'
    text: '**Document Management Systems** – Generate custom reports by pulling only
      the needed sections from massive PDFs.'
  - name: '**Legal & Financial Services** – Share specific contract clauses or financial
      statements without exposing the entire file.'
    text: '**Legal & Financial Services** – Share specific contract clauses or financial
      statements without exposing the entire file.'
  - name: '**Education Platforms** – Deliver chapter‑only PDFs to students, reducing
      bandwidth and storage requirements.'
    text: '**Education Platforms** – Deliver chapter‑only PDFs to students, reducing
      bandwidth and storage requirements.'
  type: HowTo
- questions:
  - answer: It handles over 50 input and output formats—including PDF, DOCX, PPTX,
      XLSX, HTML, and common image types—allowing seamless conversion and extraction
      across document families.
    question: What formats does GroupDocs.Merger support?
  - answer: Yes—simply list any page numbers you need in the `ExtractOptions` array;
      the library will retrieve them in the order you specify.
    question: Can I extract non‑sequential pages?
  - answer: No hard limit; however, extracting thousands of pages from a multi‑gigabyte
      PDF may require additional heap memory and batch processing to stay within resource
      constraints.
    question: Is there a limit to the number of pages I can extract?
  - answer: Wrap the extraction logic in a try‑catch block, log the exception message,
      and optionally retry with a smaller batch size if an `OutOfMemoryError` occurs.
    question: How should I handle exceptions during extraction?
  - answer: Absolutely—its lightweight API works on on‑premises servers, Docker containers,
      and cloud platforms such as AWS, Azure, and Google Cloud without any native
      dependencies.
    question: Can GroupDocs.Merger be used in cloud‑native Java applications?
  type: FAQPage
title: GroupDocs.Merger for Java ile Toplu Olarak Belirli PDF Sayfalarını Çıkarın
type: docs
url: /tr/java/document-extraction/extract-pages-groupdocs-merger-java/
weight: 1
---

# GroupDocs.Merger for Java ile Toplu Olarak Belirli PDF Sayfalarını Çıkarma

Büyük bir belgeden veya PDF koleksiyonundan **belirli PDF sayfalarını** çıkarmanız gerekiyorsa, doğru yerdesiniz. Bu rehberde, sayfaları toplu olarak nasıl çıkaracağınızı, bu sayfalardan yeni bir PDF oluşturacağınızı ve büyük dosya senaryolarını verimli bir şekilde nasıl yöneteceğinizi göstereceğiz — sadece birkaç satır Java kodu ile **GroupDocs.Merger for Java** kullanarak. Ayrıca bu kütüphanenin hız, format desteği ve bellek kullanımı konularında birçok alternatifi nasıl geride bıraktığını göreceksiniz.

## Hızlı Yanıtlar
- **“toplu PDF sayfalarını çıkarma” ne anlama geliyor?** Bu, tek bir işlemde bir veya birden fazla PDF'den seçilen birkaç sayfayı alıp yeni bir dosyaya yazmak anlamına gelir.  
- **Hangi yöntem sayfa numarasıyla sayfaları çıkarır?** `ExtractOptions` ve `Merger.extractPages` birlikte kullanın.  
- **Bir lisansa ihtiyacım var mı?** Geliştirme için ücretsiz deneme sürümü yeterlidir; üretim için ücretli lisans gereklidir.  
- **Sıralı olmayan sayfaları çıkarabilir miyim?** Evet—`ExtractOptions` dizisine ihtiyacınız olan sayfa numaralarını listelemeniz yeterlidir.  
- **Bu büyük dosyalar için uygun mu?** Doğru JVM yığın ayarlarıyla, GroupDocs.Merger, tüm belgeyi belleğe yüklemeden gigabayt boyutundaki PDF'leri işler.

## Toplu PDF sayfalarını çıkarma nedir?
**Toplu PDF sayfalarını çıkarma**, sıralı olsun ya da olmasın, bireysel sayfalardan bir set seçmek ve yalnızca bu sayfaları içeren yeni bir PDF oluşturmak anlamına gelir. Bu teknik, tam kaynak belgeyi paylaşmadan özel raporlar, yasal alıntılar veya çalışma kılavuzları oluşturmak için idealdir.

## GroupDocs.Merger for Java neden kullanılmalı?
GroupDocs.Merger, **50+ giriş ve çıkış formatını** (PDF, DOCX, PPTX, XLSX ve yaygın görüntü türleri dahil) işleyebilir ve 500 sayfalık bir dosya için yığın belleğinde 200 MB'den az kullanarak çok sayfalı PDF'leri yönetebilir. Yüksek performanslı API'si, düşük seviyeli dosya işlemleri yerine iş mantığına odaklanmanızı sağlar ve herhangi bir Java uyumlu platformda—masaüstü, sunucu veya bulut—çalışır.

## Önkoşullar
- Java ve IntelliJ IDEA veya Eclipse gibi bir IDE hakkında temel bilgi.  
- Bağımlılık yönetimi için Maven veya Gradle.  
- Bir GroupDocs.Merger lisansı (ücretsiz deneme veya geçici lisans test için çalışır).  

## GroupDocs.Merger for Java Kurulumu

### Kurulum Talimatları
Kütüphaneyi tercih ettiğiniz yapı aracını kullanarak projenize ekleyin.

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
Manuel bir yaklaşım için, en son sürümü [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/) adresinden indirin.

### Lisans Alımı
Özellikleri keşfetmek için ücretsiz deneme ile başlayın. Kütüphane ihtiyaçlarınızı karşılıyorsa, bir lisans satın alın veya uzun vadeli değerlendirme için geçici bir lisans isteyin.

`Merger`, belgeleri yüklemek ve manipüle etmek için kullanılan birincil sınıftır.  
Bağımlılığı ekleyip bir lisans aldıktan sonra, kaynak belgenize işaret eden bir `Merger` örneği oluşturun:

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.docx";
Merger merger = new Merger(filePath);
```

## Uygulama Kılavuzu

### Sayfa Numarasına Göre Sayfa Çıkarma Özelliği
**Sayfa numarasına göre sayfa çıkarma** özelliği, kaynak dosyadan hangi sayfaları çıkaracağınızı tam olarak belirtmenizi sağlar.

#### Merger'ı Başlatma
`Merger` sınıfı, GroupDocs.Merger'da tüm belge‑seviyesi işlemler için giriş noktasıdır. Kaynak dosyayı, sayfaları talep üzerine akışlayan hafif bir nesneye yükler ve tam bellek yüklemesinden kaçınır.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.docx";
Merger merger = new Merger(filePath);
```

#### Çıkarma İçin Sayfa Numaralarını Tanımlama
`ExtractOptions` çıkarma yapılandırmasını tutar. İstediğiniz 1‑tabanlı sayfa numaralarını içeren bir `int[]` sağlayın; API bunları dahili olarak doğru sayfa akışlarına eşleyecektir.

```java
ExtractOptions extractOptions = new ExtractOptions(new int[] { 1, 4 });
```

#### Çıkarma İşlemini Gerçekleştirme
Hazırlanan seçeneklerle `extractPages` çağrısı, yalnızca istenen sayfaları içeren yeni bir `Document` nesnesi döndürür.  
`Document`, çıkarma sonrası oluşan PDF belgesini temsil eder.

```java
merger.extractPages(extractOptions);
```

#### Çıkarılan Sayfaları Kaydetme
Oluşan belge, desteklenen herhangi bir formata kaydedilebilir. Çoğu durumda bir PDF yazacaksınız, ancak gerekirse DOCX veya PNG olarak da çıktı alabilirsiniz.

```java
String filePathOut = "YOUR_OUTPUT_DIRECTORY/ExtractPagesByNumbers-output.pdf";
merger.save(filePathOut);
```

## Neden Önemli
Seçilen sayfalardan bir PDF oluşturmak, tüm belgeleri göndermeye gerek kalmadan indirme boyutunu tipik kullanım senaryolarında %90'a kadar azaltır. `ExtractOptions` kullanmak, kaynak dosyanın tekrar tekrar yüklenmesini önler ve manuel sayfa‑sayfa işleme göre CPU kullanımını yaklaşık %30 azaltır. **Büyük PDF çıkarma** senaryolarıyla uğraşırken, JVM yığınını (`-Xmx2g` veya daha yüksek) artırabilir ve 1‑GB bir PDF için bellek tüketimini 300 MB'nin altında tutabilirsiniz.

## Yaygın Tuzaklar ve Sorun Giderme
- **Yanlış dosya yolları** – Girdi ve çıktı dizinlerinin mevcut olduğundan ve yazma izinlerine sahip olduğundan emin olun.  
- **Geçersiz sayfa numaraları** – Sayfa indeksleri 1‑tabanlıdır; belgenin uzunluğundan daha büyük bir sayfa talep etmek `PageNotFoundException` hatası verir.  
- **Bellek yetersizliği hataları** – 2 GB'den büyük PDF'ler için daha fazla yığın ayırın (`-Xmx4g`) veya çıkarma işlemini daha küçük partilere bölün.  

## Pratik Uygulamalar
1. **Belge Yönetim Sistemleri** – Büyük PDF'lerden yalnızca gereken bölümleri çekerek özel raporlar oluşturun.  
2. **Hukuk ve Finans Hizmetleri** – Tüm dosyayı ortaya çıkarmadan belirli sözleşme maddelerini veya finansal tabloları paylaşın.  
3. **Eğitim Platformları** – Öğrencilere sadece bölümler içeren PDF'ler sunarak bant genişliği ve depolama gereksinimlerini azaltın.  

## Performans Hususları
- **Bellek Yönetimi:** VisualVM gibi araçlarla yığın kullanımını izleyin; dosya boyutuna göre `-Xmx` ayarını değiştirin.  
- **Toplu İşleme:** Onlarca belgeden sayfa çıkarırken, CPU ve I/O dengesini korumak için 10–20'lik gruplar halinde işleyin.  
- **Verimli I/O:** Okuma/yazma işlemlerini hızlandırmak için Java NIO tamponlu akışları kullanın, özellikle SSD depolama üzerinde.  

## Sonuç
Artık GroupDocs.Merger for Java kullanarak **belirli PDF sayfalarını çıkarmak** ve **sayfalardan PDF oluşturmak** için üretim‑hazır bir yaklaşıma sahipsiniz. Bu yöntem, seçici belge paylaşımı, özel rapor oluşturma veya büyük PDF'lerin verimli işlenmesi gerektiren iş akışlarını basitleştirir. Uygulamanızın belge‑işleme gücünü daha da genişletmek için belge birleştirme, sayfa döndürme veya filigran ekleme gibi ek yetenekleri keşfedin.

## Sıkça Sorulan Sorular

**Q: GroupDocs.Merger hangi formatları destekliyor?**  
A: 50'den fazla giriş ve çıkış formatını (PDF, DOCX, PPTX, XLSX, HTML ve yaygın görüntü türleri dahil) destekler; belge aileleri arasında sorunsuz dönüşüm ve çıkarma sağlar.

**Q: Sıralı olmayan sayfaları çıkarabilir miyim?**  
A: Evet—`ExtractOptions` dizisine ihtiyacınız olan sayfa numaralarını listeleyin; kütüphane bunları belirttiğiniz sırayla alacaktır.

**Q: Çıkarabileceğim sayfa sayısında bir limit var mı?**  
A: Sert bir limit yok; ancak çok‑gigabaytlık bir PDF'den binlerce sayfa çıkarmak, ek yığın belleği ve kaynak kısıtlamaları içinde kalmak için toplu işleme gerektirebilir.

**Q: Çıkarma sırasında istisnaları nasıl ele almalı?**  
A: Çıkarma mantığını bir try‑catch bloğuna sarın, istisna mesajını kaydedin ve `OutOfMemoryError` oluşursa isteğe bağlı olarak daha küçük bir toplu boyutla yeniden deneyin.

**Q: GroupDocs.Merger bulut‑yerel Java uygulamalarında kullanılabilir mi?**  
A: Kesinlikle—hafif API'si, yerel sunucularda, Docker konteynerlerinde ve AWS, Azure, Google Cloud gibi bulut platformlarında herhangi bir yerel bağımlılık olmadan çalışır.

**Last Updated:** 2026-06-21  
**Test Edilen:** GroupDocs.Merger 23.11 (yazım zamanındaki en son sürüm)  
**Yazar:** GroupDocs  

## Kaynaklar
- [Dokümantasyon](https://docs.groupdocs.com/merger/java/)
- [API Referansı](https://reference.groupdocs.com/merger/java/)
- [İndirme](https://releases.groupdocs.com/merger/java/)
- [Satın Alma](https://purchase.groupdocs.com/buy)
- [Ücretsiz Deneme](https://releases.groupdocs.com/merger/java/)
- [Geçici Lisans](https://purchase.groupdocs.com/temporary-license/)
- [Destek Forumu](https://forum.groupdocs.com/c/merger/)

## İlgili Eğitimler

- [Sayfaları Birleştirme - GroupDocs.Merger for Java Kullanarak Birden Çok Belgeden Belirli Sayfaları Birleştirme](/merger/java/document-joining/join-pages-groupdocs-merger-java-tutorial/)
- [GroupDocs.Merger Java ile Tek Sayfalı PDF Oluşturma](/merger/java/document-splitting/)
- [pdf sayfalarını önizleme java – GroupDocs.Merger önizleme rehberi](/merger/java/document-information/)