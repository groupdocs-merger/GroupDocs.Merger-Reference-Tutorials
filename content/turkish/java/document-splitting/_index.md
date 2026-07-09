---
date: 2026-05-22
description: GroupDocs.Merger for Java kullanarak tek sayfalı PDF dosyaları oluşturmayı
  ve PDF'leri bölmeyi öğrenin. split pdf java ve daha fazlası için adım adım kılavuzlar
  içerir.
keywords:
- create single page pdf
- docx to pdf java
- split pdf java
- pdf split by range
- split pdf odd even
schemas:
- author: GroupDocs
  dateModified: '2026-05-22'
  description: Learn how to create single page PDF files and split PDFs using GroupDocs.Merger
    for Java. Includes step-by-step guides for split pdf java and more.
  headline: Create Single Page PDF with GroupDocs.Merger Java
  type: TechArticle
- description: Learn how to create single page PDF files and split PDFs using GroupDocs.Merger
    for Java. Includes step-by-step guides for split pdf java and more.
  name: Create Single Page PDF with GroupDocs.Merger Java
  steps:
  - name: Initialize the Merger
    text: The `Merger` class is GroupDocs.Merger's core component that loads a source
      document and provides split operations. Create an instance by passing the file
      path or an input stream.
  - name: Define the split criteria
    text: Choose the exact page number or range you need. For a single‑page extraction,
      you’ll specify a range like `1‑1`. When you need to **split pdf by range**,
      you can pass multiple ranges such as `1‑5, 6‑10`.
  - name: Execute the split
    text: Call the appropriate `split` method. For example, `merger.split(new int[]{1})`
      extracts the first page, while `merger.splitByRange(new int[][]{{1,5},{6,10}})`
      handles multiple ranges in one call.
  - name: Save the result
    text: Write each output to a file path or return it as a `java.io.InputStream`.
      This makes it easy to integrate with web APIs or store the result in cloud storage.
      > **Pro tip:** When working with large PDFs, call `merger.setOptimizeResources(true)`
      before splitting to reduce memory consumption.
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then perform any split
      operation as usual.
    question: Can I split a password‑protected PDF?
  - answer: Provide a page list containing only odd numbers (e.g., 1,3,5…) to the
      `split` method.
    question: How do I split only the odd pages of a PDF?
  - answer: Absolutely. After loading the DOCX, call `saveAsPdf` on each split segment.
    question: Is it possible to split a DOCX directly into PDFs?
  - answer: PDF, DOCX, PPTX, TXT, HTML, and many image formats (PNG, JPEG, etc.).
    question: What formats does GroupDocs.Merger support for splitting?
  - answer: No. A single GroupDocs.Merger license covers all supported formats.
    question: Do I need a separate license for each file type?
  type: FAQPage
title: GroupDocs.Merger Java ile Tek Sayfalı PDF Oluşturun
type: docs
url: /tr/java/document-splitting/
weight: 12
---

# Tek Sayfalık PDF Oluşturma - GroupDocs.Merger Java

Eğer daha büyük belgelerden **tek sayfalık PDF** dosyaları oluşturmanız veya PDF'leri daha yönetilebilir parçalara bölmeniz gerekiyorsa, doğru yerdesiniz. Bu kılavuz, çok sayfalı dosyalar, sayfa aralıkları, tek/çift sayfalar, DOCX bölme ve hatta metin tabanlı bölmeler gibi en yaygın bölme senaryolarını güçlü GroupDocs.Merger Java kütüphanesini kullanarak adım adım anlatır. Bu öğreticinin sonunda bu teknikleri kendi uygulamalarınıza nasıl entegre edeceğinizi, belge işleme performansını nasıl artıracağınızı ve kod tabanınızı temiz ve sürdürülebilir tutacağınızı tam olarak öğreneceksiniz.

## Hızlı Yanıtlar
- **“Tek sayfalık PDF oluşturma” ne anlama geliyor?** Bir kaynak belgeden tek bir sayfa çıkarıp bağımsız bir PDF dosyası olarak kaydetmek anlamına gelir.  
- **Bu işi hangi kütüphane yapıyor?** GroupDocs.Merger for Java, tüm bölme işlemleri için akıcı bir API sağlar.  
- **Lisans gerekir mi?** Geliştirme için geçici bir lisans yeterlidir; üretim ortamı için tam lisans gereklidir.  
- **PDF'yi tek ve çift sayfalara ayırabilir miyim?** Evet—GroupDocs.Merger, sayfaları tek/çift numaralara göre filtrelemenize izin verir.  
- **DOCX bölme destekleniyor mu?** Kesinlikle; DOCX dosyalarını sayfa‑sayfa veya özel aralıklarla bölebilirsiniz.  

## “Tek sayfalık PDF oluşturma” nedir?
Tek sayfalık PDF oluşturma, çok sayfalı bir kaynak belge (PDF, DOCX, PPTX vb.) alıp yalnızca bir sayfayı kendi PDF dosyasına çıkarmak anlamına gelir. Bu, sadece belirli bir sayfanın gerektiği faturalar, sertifikalar veya ön izleme görselleri oluşturmak için faydalıdır.

## Neden GroupDocs.Merger for Java kullanmalı?
GroupDocs.Merger for Java, birçok belge formatını tek bir tutarlı API ile işleyerek yüksek performans ve düşük bellek kullanımı sunar. Karmaşık dosya işlemlerini soyutlayarak geliştirmeyi basitleştirir; böylece düşük seviyeli işleme detaylarıyla uğraşmak yerine iş mantığınıza odaklanabilirsiniz.

- **Unified API** – PDF, DOCX, PPTX, görüntüler ve birçok diğer formatla çalışır.  
- **High performance** – Büyük dosyalar ve toplu işlemler için optimize edilmiştir; tüm dosyayı belleğe yüklemeden 2 GB’a kadar belge işleyebilir.  
- **Fine‑grained control** – Sayfa aralığı, tek/çift sayfalar veya özel ayırıcılarla bölme yapabilirsiniz.  
- **Stream‑friendly** – Çıktı bir dosyaya kaydedilebilir veya web servisleri için bir akış olarak döndürülebilir.  

## Önkoşullar
- Java 8 veya daha yenisi.  
- Projenize eklenmiş GroupDocs.Merger for Java (Maven/Gradle).  
- Geçerli (geçici veya tam) bir GroupDocs lisans dosyası.

## Tek sayfalık PDF nasıl oluşturulur?
GroupDocs.Merger ile tek sayfalık PDF oluşturmak, kaynak dosyayı yüklemeyi, kesin sayfa ya da aralığı belirtmeyi, bölme işlemini çağırmayı ve son olarak sonucu kalıcı hale getirmeyi içerir. Bu iş akışı, orijinal belgenin dokunulmaz kalmasını sağlarken çıkarılan sayfanın bağımsız bir PDF dosyası olarak kaydedilmesini sağlar.

`Merger` sınıfı, kaynak belgeleri yükleyen ve bölme işlevselliği sağlayan temel bileşendir.

### Adım 1: Merger'ı Başlatın
`Merger` sınıfı, GroupDocs.Merger'ın kaynak belgeyi yükleyen ve bölme işlemlerini sağlayan çekirdek bileşenidir. Dosya yolunu ya da bir giriş akışını geçirerek bir örnek oluşturun.

### Adım 2: Bölme kriterlerini tanımlayın
İhtiyacınız olan kesin sayfa numarasını ya da aralığını seçin. Tek sayfa çıkarmak için `1‑1` gibi bir aralık belirtirsiniz. **Aralığa göre pdf bölme** gerektiğinde `1‑5, 6‑10` gibi birden fazla aralık geçirebilirsiniz.

### Adım 3: Bölmeyi yürütün
Uygun `split` metodunu çağırın. Örneğin, `merger.split(new int[]{1})` ilk sayfayı çıkarırken, `merger.splitByRange(new int[][]{{1,5},{6,10}})` bir çağrıda birden fazla aralığı işler.

### Adım 4: Sonucu kaydedin
Her çıktıyı bir dosya yoluna yazın ya da `java.io.InputStream` olarak döndürün. Bu, web API'leriyle entegrasyonu veya sonucu bulut depolamada saklamayı kolaylaştırır.

> **Pro tip:** Büyük PDF'lerle çalışırken bölmeden önce `merger.setOptimizeResources(true)` çağırarak bellek tüketimini azaltın.

## PDF java dosyalarını birden çok sayfaya nasıl bölünür
`Merger` sınıfı, PDF dosyalarını yüklemek ve manipüle etmek için birincil API'yi sağlar. Bir PDF'yi ayrı tek‑sayfalık dosyalara bölmek için belgeyi Merger örneğiyle yükleyip parametresiz split metodunu çağırmanız yeterlidir. Kütüphane, her sayfa için yeni bir PDF otomatik olarak oluşturur, orijinal içerik ve meta verileri korur; bu, faturalar ya da raporlar gibi toplu işleme senaryoları için idealdir.

## PDF tek ve çift sayfaları nasıl bölünür
`Merger` sınıfı, belgeler üzerinde bölme işlemlerini gerçekleştiren çekirdek bileşendir. PDF'den yalnızca tek ya da çift sayfaları almak istediğinizde, istediğiniz sayfa numaralarının bir listesini split fonksiyonuna verin. Merger, sadece bu sayfaları içeren yeni bir belge üretir; böylece tek‑numaralı ya da çift‑numaralı içerikler için ayrı dosyalar hızlıca oluşturabilirsiniz.

## docx dosyaları nasıl bölünür (docx bölme)
`Merger` sınıfı aynı zamanda DOCX dosyalarıyla da çalışır. `splitByPage` metodunu kullanarak her sayfa için bir DOCX (veya PDF) oluşturabilir veya PDF çıktısı gerekiyorsa `saveAsPdf` ile birleştirebilirsiniz. Bu, **docx to pdf java** dönüşüm iş akışını tek adımda kapsar.

## Belgeleri çok‑sayfalı dosyalara nasıl bölünür
`Merger` sınıfı, bölme işlemleri için sayfalama ve dosya oluşturma görevlerini üstlenir. Büyük bir belgeyi sabit boyutlu parçalar halinde bölmek isterseniz, çıktı dosyası başına sayfa sayısını belirtin. Merger, kaynak belgeyi dolaşarak tanımlı sayfa sayısına sahip yeni PDF'ler oluşturur; bu, arşivleme, dağıtım ve geniş belgelerin paralel işlenmesini basitleştirir.

## Kullanılabilir Eğitimler

### [How to Split Documents into Multi-Page Files Using GroupDocs.Merger for Java](./split-documents-multi-page-files-java-groupdocs-merger/)
GroupDocs.Merger for Java kullanarak büyük belgeleri daha küçük, çok‑sayfalı dosyalara verimli bir şekilde bölmeyi öğrenin. Belge yönetimini kolayca optimize edin.

### [How to Split a Text File by Line Intervals Using GroupDocs.Merger for Java | Document Splitting Guide](./split-text-file-line-intervals-groupdocs-merger-java/)
GroupDocs.Merger for Java ile metin dosyalarını satır aralıklarıyla yönetilebilir bölümlere ayırmayı öğrenin. Etkili belge işleme için kapsamlı bir rehber.

### [Master Document Splitting by Page Range with GroupDocs.Merger for Java](./split-documents-page-range-groupdocs-merger-java/)
GroupDocs.Merger for Java kullanarak belgeleri belirli sayfa aralıklarıyla bölmeyi öğrenin. Belge yönetimini akıcı hale getirin ve tek/çift sayfa gibi filtreleri uygulayın.

### [Master Document Splitting with GroupDocs.Merger&#58; A Comprehensive Guide](./master-document-splitting-groupdocs-merger-java/)
GroupDocs.Merger for Java ile belgeleri tek sayfalara verimli bir şekilde bölmeyi öğrenin. Bu rehber kurulum, uygulama ve pratik kullanım örneklerini kapsar.

### [Master Java Document Splitting with GroupDocs.Merger&#58; Split DOCX Pages into Files and Streams](./master-java-document-splitting-groupdocs-merger/)
GroupDocs.Merger for Java kullanarak DOCX belgelerini ayrı sayfalara ya da akışlara bölmeyi öğrenin. Kurulum, uygulama ve pratik senaryolar bu rehberde yer alıyor.

## Ek Kaynaklar

- [GroupDocs.Merger for Java Documentation](https://docs.groupdocs.com/merger/java/)
- [GroupDocs.Merger for Java API Reference](https://reference.groupdocs.com/merger/java/)
- [Download GroupDocs.Merger for Java](https://releases.groupdocs.com/merger/java/)
- [GroupDocs.Merger Forum](https://forum.groupdocs.com/c/merger)
- [Free Support](https://forum.groupdocs.com/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)

## Yaygın Sorunlar ve Çözümler
| Issue | Solution |
|-------|----------|
| **Büyük PDF'lerde bellek aşımı** | Kaynak optimizasyonunu etkinleştirin: `merger.setOptimizeResources(true);` |
| **Bölme sonrası hatalı sayfa numaraları** | Sayfa indekslemesinin 0 değil 1'den başladığını unutmayın. |
| **Lisans bulunamadı** | `GroupDocs.Merger.lic` dosyanızın yolunu doğrulayın ve sınıf yolunda (classpath) olduğundan emin olun. |
| **DOCX bölündüğünde boş sayfalar oluşuyor** | Kaynak DOCX'in doğru sayfa sonları içerdiğinden emin olun; aksi takdirde yedek olarak `splitByParagraph` kullanın. |

## Sık Sorulan Sorular

**S: Şifre korumalı bir PDF'i bölüp ayırabilir miyim?**  
C: Evet. Belgeyi şifre parametresiyle yükleyin, ardından istediğiniz bölme işlemini normal şekilde gerçekleştirin.

**S: PDF'in sadece tek sayfalarını nasıl ayırırım?**  
C: `split` metoduna yalnızca tek sayıları içeren bir liste (ör. 1,3,5…) verin.

**S: DOCX'i doğrudan PDF'lere bölmek mümkün mü?**  
C: Kesinlikle. DOCX'i yükledikten sonra her bölünmüş segment için `saveAsPdf` metodunu çağırın.

**S: GroupDocs.Merger hangi formatları bölme için destekliyor?**  
C: PDF, DOCX, PPTX, TXT, HTML ve birçok görüntü formatı (PNG, JPEG vb.).

**S: Her dosya türü için ayrı bir lisans almam gerekiyor mu?**  
C: Hayır. Tek bir GroupDocs.Merger lisansı tüm desteklenen formatları kapsar.

**Last Updated:** 2026-05-22  
**Tested With:** GroupDocs.Merger 23.11 for Java  
**Author:** GroupDocs

## İlgili Eğitimler

- [split pdf java: Document Splitting with GroupDocs.Merger](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [Master Document Splitting by Page Range with GroupDocs.Merger for Java](/merger/java/document-splitting/split-documents-page-range-groupdocs-merger-java/)
- [Efficiently Merge PDFs Using GroupDocs.Merger for Java: A Step‑by‑Step Guide](/merger/java/format-specific-merging/merge-pdfs-groupdocs-merger-java-tutorial/)