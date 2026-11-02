---
date: '2026-11-02'
description: GroupDocs Merger for Java kullanarak PDF sayfalarını toplu olarak nasıl
  çıkaracağınızı ve sayfalardan PDF oluşturacağınızı öğrenin. Bu adım adım rehber,
  kurulum, kod parçacıkları ve gerçek dünya kullanım örneklerini kapsar.
keywords:
- batch extract pdf pages
- create pdf from pages
- java pdf extraction
- extract specific pdf pages
- java split pdf pages
lastmod: '2026-11-02'
og_description: GroupDocs Merger for Java kullanarak PDF sayfalarını toplu olarak
  nasıl çıkaracağınızı ve sayfalardan PDF oluşturacağınızı öğrenin. Adım adım kod
  ve gerçek dünya örneklerini izleyin.
og_image_alt: 'Developer guide: batch extract PDF pages with GroupDocs Merger for
  Java'
og_title: GroupDocs Merger for Java ile PDF sayfalarını toplu çıkarma
schemas:
- author: GroupDocs
  dateModified: '2026-11-02'
  description: Learn how to batch extract PDF pages and create PDF from pages using
    GroupDocs Merger for Java. This step‑by‑step guide covers setup, code snippets,
    and real‑world use cases.
  headline: Batch extract PDF pages with GroupDocs Merger for Java
  type: TechArticle
- description: Learn how to batch extract PDF pages and create PDF from pages using
    GroupDocs Merger for Java. This step‑by‑step guide covers setup, code snippets,
    and real‑world use cases.
  name: Batch extract PDF pages with GroupDocs Merger for Java
  steps:
  - name: '**Document management systems** – Generate custom reports by pulling only
      the needed sections from massive PDFs.'
    text: '**Document management systems** – Generate custom reports by pulling only
      the needed sections from massive PDFs.'
  - name: '**Legal & financial services** – Share specific contract clauses or financial
      statements without exposing the entire file.'
    text: '**Legal & financial services** – Share specific contract clauses or financial
      statements without exposing the entire file.'
  - name: '**Education platforms** – Deliver chapter‑only PDFs to students, reducing
      bandwidth and storage requirements.'
    text: '**Education platforms** – Deliver chapter‑only PDFs to students, reducing
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
tags:
- batch extract pdf
- GroupDocs Merger
- Java document processing
- PDF manipulation
- author: GroupDocs
  dateModified: '2026-11-02'
  description: Learn how to batch extract PDF pages and create PDF from pages using
    GroupDocs Merger for Java. This tutorial covers setup, code snippets, and real‑world
    use cases.
  headline: Batch extract PDF pages with GroupDocs Merger for Java
  type: TechArticle
- description: Learn how to batch extract PDF pages and create PDF from pages using
    GroupDocs Merger for Java. This tutorial covers setup, code snippets, and real‑world
    use cases.
  name: Batch extract PDF pages with GroupDocs Merger for Java
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
title: GroupDocs Merger for Java ile PDF sayfalarını toplu çıkarma
type: docs
url: /tr/java/document-extraction/extract-pages-groupdocs-merger-java/
weight: 1
---

# GroupDocs Merger for Java ile PDF sayfalarını toplu olarak çıkarma

Büyük bir belgeden veya PDF koleksiyonundan **PDF sayfalarını toplu olarak çıkarmanız** gerekiyorsa, doğru yerdesiniz. Bu rehberde, belirli sayfaları toplu olarak nasıl çıkaracağınızı, bu sayfalardan yeni bir PDF oluşturacağınızı ve büyük dosya senaryolarını verimli bir şekilde nasıl yöneteceğinizi göstereceğiz — sadece birkaç satır Java kodu kullanarak **GroupDocs.Merger for Java** ile. Ayrıca bu kütüphanenin hız, format desteği ve bellek kullanımı açısından birçok alternatifi nasıl geride bıraktığını göreceksiniz.

## Hızlı cevaplar
- **“PDF sayfalarını toplu olarak çıkarma” ne anlama geliyor?** Bu, tek bir işlemde bir veya birden fazla PDF'den seçilen birkaç sayfayı alıp yeni bir dosyaya yazmak anlamına gelir.  
- **Hangi yöntem sayfa numarasına göre sayfaları çıkarır?** `ExtractOptions` ve `Merger.extractPages` birlikte kullanın.  
- **Bir lisansa ihtiyacım var mı?** Geliştirme için ücretsiz deneme sürümü yeterlidir; üretim için ücretli lisans gereklidir.  
- **Sırasız sayfaları çıkarabilir miyim?** Evet—`ExtractOptions` dizisinde ihtiyacınız olan sayfa numaralarını listeleyin.  
- **Bu büyük dosyalar için uygun mu?** Uygun JVM yığın ayarlarıyla, GroupDocs.Merger gigabayt boyutundaki PDF'leri tüm belgeyi belleğe yüklemeden işler.

## Neden GroupDocs.Merger for Java kullanmalısınız?
GroupDocs.Merger, **50+ giriş ve çıkış formatını** (PDF, DOCX, PPTX, XLSX, HTML ve yaygın görüntü türleri dahil) işleyebilir ve 500 sayfalık bir dosya için 200 MB'den az yığın belleği kullanarak çok sayfalı PDF'leri yönetebilir. Yüksek performanslı API'si, düşük seviyeli dosya işlemleri yerine iş mantığına odaklanmanızı sağlar ve herhangi bir Java uyumlu platformda—masaüstü, sunucu veya bulut—çalışır.

## Önkoşullar
- Java ve IntelliJ IDEA veya Eclipse gibi bir IDE hakkında temel bilgi.  
- Bağımlılık yönetimi için Maven veya Gradle.  
- Bir GroupDocs.Merger lisansı (test için ücretsiz deneme veya geçici lisans yeterlidir).  

## GroupDocs.Merger for Java'ı kurma

### Kurulum talimatları
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

**Doğrudan indirme**  
Manuel bir yaklaşım için, en son sürümü [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/) adresinden indirin.

### Lisans edinme
Özellikleri keşfetmek için ücretsiz bir deneme sürümüyle başlayın. Kütüphane ihtiyaçlarınızı karşılıyorsa, bir lisans satın alın veya genişletilmiş değerlendirme için geçici bir lisans isteyin.

`Merger` sınıfı, GroupDocs.Merger'daki tüm belge‑seviyesi işlemler için giriş noktasıdır. Kaynak dosyayı, isteğe bağlı sayfa akışı sağlayan hafif bir nesneye yükler, tam bellek içinde yüklemeyi önler.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.docx";
Merger merger = new Merger(filePath);
```

## Uygulama rehberi

### Sayfa numarasına göre sayfa çıkarma özelliği
**Sayfa numarasına göre sayfa çıkarma** özelliği, kaynak dosyadan tam olarak hangi sayfaları alacağınızı belirtmenizi sağlar.

#### Merger'ı başlatma
Bağımlılığı ekleyip bir lisans aldıktan sonra, kaynak belgenize işaret eden bir `Merger` örneği oluşturun:

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.docx";
Merger merger = new Merger(filePath);
```

#### Çıkarma için sayfa numaralarını tanımlama
`ExtractOptions` çıkarma yapılandırmasını tutar. İstediğiniz 1‑tabanlı sayfa numaralarını içeren bir `int[]` sağlayın; API bunları dahili olarak doğru sayfa akışlarına eşleyecektir.

```java
ExtractOptions extractOptions = new ExtractOptions(new int[] { 1, 4 });
```

#### Çıkarma işlemini gerçekleştirme
`extractPages`, belirtilen sayfaları çıkaran ve yeni bir belge döndüren `Merger` sınıfının bir yöntemidir.  
Hazırlanan seçeneklerle `extractPages` çağrısı, yalnızca istenen sayfaları içeren yeni bir `Document` nesnesi döndürür. `Document`, çıkarma sonrası oluşan PDF belgesini temsil eder.

```java
merger.extractPages(extractOptions);
```

#### Çıkarılan sayfaları kaydetme
Oluşan belge, desteklenen herhangi bir formata kaydedilebilir. Çoğu durumda bir PDF yazacaksınız, ancak gerekirse DOCX veya PNG olarak da çıktı alabilirsiniz.

```java
String filePathOut = "YOUR_OUTPUT_DIRECTORY/ExtractPagesByNumbers-output.pdf";
merger.save(filePathOut);
```

## Neden bu önemli
Seçili sayfalardan bir PDF oluşturmak, tüm belgeleri göndermeye gerek kalmadan, tipik kullanım senaryolarında indirme boyutunu %90'a kadar azaltır. `ExtractOptions` kullanmak, kaynak dosyanın tekrar tekrar yüklenmesini önler; bu da manuel sayfa‑sayfa işleme göre CPU kullanımını yaklaşık %30 azaltır. **Büyük PDF çıkarma** senaryolarıyla uğraşırken, JVM yığınını (`-Xmx2g` veya daha yüksek) artırabilir ve 1 GB'lik bir PDF için bellek tüketimini 300 MB'nin altında tutabilirsiniz.

## Yaygın tuzaklar ve sorun giderme
- **Yanlış dosya yolları** – Giriş ve çıkış dizinlerinin mevcut olduğundan ve yazma izinlerine sahip olduğundan emin olun.  
- **Geçersiz sayfa numaraları** – Sayfa indeksleri 1‑tabanlıdır; belgenin uzunluğundan daha büyük bir sayfa talep etmek `PageNotFoundException` hatasına yol açar.  
- **Bellek yetersizliği hataları** – 2 GB'den büyük PDF'ler için daha fazla yığın ayırın (`-Xmx4g`) veya çıkarma işlemini daha küçük partilere bölün.  

## Pratik uygulamalar
1. **Belge yönetim sistemleri** – Büyük PDF'lerden yalnızca gereken bölümleri çekerek özel raporlar oluşturun.  
2. **Hukuki ve finansal hizmetler** – Tüm dosyayı ortaya çıkarmadan belirli sözleşme maddelerini veya finansal tabloları paylaşın.  
3. **Eğitim platformları** – Öğrencilere sadece bölümlerden oluşan PDF'ler sunarak bant genişliği ve depolama gereksinimlerini azaltın.  

## Performans hususları
- **Bellek yönetimi:** VisualVM gibi araçlarla yığın kullanımını izleyin; dosya boyutuna göre `-Xmx` ayarını değiştirin.  
- **Toplu işleme:** Onlarca belgeden sayfa çıkarırken, CPU ve I/O dengesini korumak için 10–20'lik gruplar halinde işleyin.  
- **Verimli I/O:** Okuma/yazma işlemlerini hızlandırmak için özellikle SSD depolamada Java NIO tamponlu akışları kullanın.  

## Sonuç
Artık GroupDocs.Merger for Java kullanarak **PDF sayfalarını toplu olarak çıkarma** ve **sayfalardan PDF oluşturma** için üretim‑hazır bir yaklaşıma sahipsiniz. Bu yöntem, seçici belge paylaşımı, özel rapor oluşturma veya büyük PDF'lerin verimli işlenmesi gibi iş akışlarını basitleştirir. Belge birleştirme, sayfa döndürme veya filigran ekleme gibi ek yetenekleri keşfederek uygulamanızın belge‑işleme gücünü daha da genişletebilirsiniz.

## Sıkça sorulan sorular

**Q: GroupDocs.Merger hangi formatları destekliyor?**  
A: 50'den fazla giriş ve çıkış formatını (PDF, DOCX, PPTX, XLSX, HTML ve yaygın görüntü türleri dahil) işler; belge aileleri arasında sorunsuz dönüşüm ve çıkarma sağlar.

**Q: Sırasız sayfaları çıkarabilir miyim?**  
A: Evet—`ExtractOptions` dizisinde ihtiyacınız olan sayfa numaralarını listeleyin; kütüphane onları belirttiğiniz sırayla getirir.

**Q: Çıkarabileceğim sayfa sayısında bir limit var mı?**  
A: Sert bir limit yok; ancak çok gigabaytlık bir PDF'den binlerce sayfa çıkarmak, ek yığın belleği ve kaynak kısıtlamaları içinde kalmak için toplu işleme gerektirebilir.

**Q: Çıkarma sırasında istisnaları nasıl ele almalı?**  
A: Çıkarma mantığını bir try‑catch bloğuna sarın, istisna mesajını kaydedin ve `OutOfMemoryError` oluşursa isteğe bağlı olarak daha küçük bir toplu boyutla yeniden deneyin.

**Q: GroupDocs.Merger bulut‑yerel Java uygulamalarında kullanılabilir mi?**  
A: Kesinlikle—hafif API'si, yerel sunucularda, Docker konteynerlerinde ve AWS, Azure ve Google Cloud gibi bulut platformlarında herhangi bir yerel bağımlılık olmadan çalışır.

---

**Son güncelleme:** 2026-11-02  
**Test edildiği sürüm:** GroupDocs.Merger 23.11 (yazım zamanındaki en son sürüm)  
**Yazar:** GroupDocs  

**Kaynaklar**  
- [Dokümantasyon](https://docs.groupdocs.com/merger/java/)  
- [API referansı](https://reference.groupdocs.com/merger/java/)  
- [İndirme](https://releases.groupdocs.com/merger/java/)  
- [Satın al](https://purchase.groupdocs.com/buy)  
- [Ücretsiz deneme](https://releases.groupdocs.com/merger/java/)  
- [Geçici lisans](https://purchase.groupdocs.com/temporary-license/)  
- [Destek forumu](https://forum.groupdocs.com/c/merger/)  

## İlgili öğreticiler
- [How to Merge Pages - Join Specific Pages from Multiple Documents Using GroupDocs.Merger for Java](/merger/java/document-joining/join-pages-groupdocs-merger-java-tutorial/)  
- [Create Single Page PDF with GroupDocs.Merger Java](/merger/java/document-splitting/)  
- [preview pdf pages java – GroupDocs.Merger preview guide](/merger/java/document-information/)