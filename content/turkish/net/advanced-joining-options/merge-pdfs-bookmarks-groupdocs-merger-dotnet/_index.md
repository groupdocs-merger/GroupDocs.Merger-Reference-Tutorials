---
date: '2026-08-20'
description: GroupDocs.Merger for .NET kullanarak yer imleriyle PDF'leri nasıl birleştireceğinizi
  öğrenin; kurulum, kod örnekleri ve PDF belgelerini birleştirirken en iyi uygulamaları
  içerir.
keywords:
- merge pdfs with bookmarks
- merge pdf with bookmarks
- combine pdf documents c#
lastmod: '2026-08-20'
og_description: GroupDocs.Merger for .NET kullanarak yer imleriyle PDF'leri nasıl
  birleştireceğinizi öğrenin. Navigasyonu koruyarak PDF belgelerini birleştirmek için
  adım adım kodu izleyin.
og_image_alt: Guide showing PDF merge with bookmarks in .NET using GroupDocs.Merger
og_title: GroupDocs.Merger for .NET kullanarak yer imleriyle PDF'leri birleştirme
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for .NET,
    including setup, code examples, and best practices for combining PDF documents.
  headline: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for .NET,
    including setup, code examples, and best practices for combining PDF documents.
  name: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
  steps:
  - name: define directory paths
    text: Set up source and output folders so the code can locate the PDFs you want
      to merge. csharp string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY"; string
      outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
  - name: load the primary PDF
    text: '`Merger` represents the main document you’ll append others to. csharp using
      (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
      { // Code to merge additional files will be here. }'
  - name: configure bookmark‑preserving options
    text: '`PdfJoinOptions` controls how the merge behaves; the `UseBookmarks` flag
      tells the engine to keep existing bookmarks. csharp var pdfJoinOptions = new
      PdfJoinOptions { UseBookmarks = true };'
  - name: add additional PDFs
    text: Call `Join` for each extra file. The library automatically merges their
      bookmark trees under the main document’s outline. csharp merger.Join(Path.Combine(documentDirectory,
      "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
  - name: save the merged PDF
    text: Specify the output path and format; the library writes a single PDF that
      retains all bookmark entries. csharp string outputFile = Path.Combine(outputDirectory,
      "merged.pdf"); merger.Save(outputFile);
  type: HowTo
- questions:
  - answer: GroupDocs.Merger is a .NET library that lets you merge, split, rotate,
      and otherwise manipulate PDF and other document formats programmatically.
    question: What is GroupDocs.Merger?
  - answer: Yes – call `Join` repeatedly or pass a collection of file paths to merge
      any number of PDFs in one operation.
    question: Can I merge more than two PDF files at a time?
  - answer: Obtain a permanent license from the GroupDocs purchase page; the trial
      license works only for evaluation and expires after 30 days.
    question: How do I handle licensing for production use?
  - answer: Ensure `PdfJoinOptions.UseBookmarks` is set to `true` and that each source
      PDF actually contains bookmarks before merging.
    question: My merged PDF shows no bookmarks—what went wrong?
  - answer: Absolutely – it supports .NET Core 3.1+, .NET 5/6, and the full .NET Framework
      4.6.1+.
    question: Is the library compatible with .NET Core and .NET Framework?
  type: FAQPage
tags:
- merge pdf
- GroupDocs.Merger
- .NET PDF processing
title: GroupDocs.Merger for .NET kullanarak yer imleriyle PDF'leri birleştirme
type: docs
url: /tr/net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/
weight: 1
---

# GroupDocs.Merger for .NET kullanarak yer imleriyle pdf'leri birleştirme

Birden fazla PDF dosyasını orijinal yer imlerini koruyarak birleştirmek, saatler süren manuel yeniden düzenlemeyi önleyebilir. Bu öğreticide GroupDocs.Merger for .NET kullanarak **yer imleriyle pdf'leri birleştirmeyi** proje kurulumundan tam, üretim‑hazır kod örneğine kadar öğreneceksiniz.

## Hızlı cevaplar
- **Hangi kütüphane yer imi koruyan birleştirmeleri destekler?** GroupDocs.Merger for .NET.  
- **Bir seferde iki PDF'den fazla birleştirebilir miyim?** Evet – ihtiyacınız kadar kaynak dosya ekleyebilirsiniz.  
- **Geliştirme için lisansa ihtiyacım var mı?** Test için ücretsiz deneme çalışır; üretim için kalıcı bir lisans gereklidir.  
- **.NET Core destekleniyor mu?** Kesinlikle – kütüphane .NET Core, .NET 5/6 ve tam .NET Framework ile çalışır.  
- **Kullanabileceği en büyük dosya boyutu nedir?** Belge başına 2 GB'a kadar, tüm dosyayı belleğe yüklemeden işlenir.

## Yer imleriyle pdf'leri birleştirme nedir?
**Yer imleriyle pdf'leri birleştirme**, birkaç PDF belgesini tek bir dosyada birleştirirken her kaynak belgenin yer imi hiyerarşisini korumak anlamına gelir. Ortaya çıkan PDF, orijinal gezinme yapısını korur ve okuyucuların her bir dosyadan gelen bölümlere doğrudan atlamasını sağlar; bu, büyük raporlar veya derlenmiş kılavuzlar için çok önemlidir.

## Yer imleriyle pdf'leri birleştirme neden önemlidir?
PDF'leri birleştirirken yer imlerini korumak, birleştirilmiş belgelerde gezinmeyi iyileştirir, kullanıcıların tüm dosyada kaydırma yapmadan belirli bölümleri veya bölümleri hızlıca bulmasını sağlar. GroupDocs.Merger, orijinal taslak hiyerarşisini korur, manuel yeniden düzenleme çabasını azaltır ve minimum bellek kullanarak 2 GB'a kadar büyük dosyaları destekler; bu da kurumsal ölçekli iş akışları için idealdir.

## Önkoşullar
- **.NET Core SDK** (3.1 veya sonrası) veya **.NET Framework** (4.6.1+).  
- **Visual Studio 2022** veya .NET geliştirmeyi destekleyen herhangi bir IDE.  
- Temel C# bilgisi ve dosya I/O konularına aşinalık.  

## GroupDocs.Merger for .NET Kurulumu

### Kurulum
Kütüphaneyi projenize aşağıdaki komutlardan biriyle ekleyin:

**.NET CLI:**  
```  
```bash
dotnet add package GroupDocs.Merger
```  
```  

**Package Manager:**  
```  
```powershell
Install-Package GroupDocs.Merger
```  
```  

**NuGet Package Manager UI:**  
- “GroupDocs.Merger” aratın ve en son sürümü yükleyin.

### Lisans edinimi
- **Ücretsiz deneme:** [GroupDocs Releases](https://releases.groupdocs.com/merger/net/) sayfasından indirin.  
- **Geçici lisans:** [GroupDocs Temporary License Page](https://purchase.groupdocs.com/temporary-license/) üzerinden alın.  
- **Tam lisans:** [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy) adresinden satın alın.

### Temel başlatma
`Merger` sınıfı tüm birleştirme işlemleri için giriş noktasıdır.  
```  
```csharp
using GroupDocs.Merger;
```  
```  
Bu ad alanı, PDF manipülasyon özelliklerinin tam setine erişim sağlar.

## .NET'te yer imleriyle pdf'leri nasıl birleştirirsiniz

Ana PDF'nizi yükleyin, yer imi işleme ayarlarını yapılandırın, ek dosyalar ekleyin ve sonucu kaydedin – tüm bunlar birkaç kısa kod satırıyla.

**Doğrudan cevap (40‑70 kelime):**  
İlk PDF ile bir `Merger` örneği oluşturun, `PdfJoinOptions.UseBookmarks` özelliğini etkinleştirin, sonraki her PDF'yi `Join` ile ekleyin ve birleştirilmiş dosyayı yazmak için `Save` çağırın. Bu yaklaşım, tüm orijinal yer imi hiyerarşisini korur ve tek bir geçişte çalışarak bellek tüketimini en aza indirir.

### Adım 1: dizin yollarını tanımlayın
Kodun birleştirmek istediğiniz PDF'leri bulabilmesi için kaynak ve çıktı klasörlerini ayarlayın.  
```  
```csharp
   string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY";
   string outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
   ```  
```  

### Adım 2: ana PDF'yi yükleyin
`Merger`, diğerlerini ekleyeceğiniz ana belgeyi temsil eder.  
```  
```csharp
   using (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
   {
       // Code to merge additional files will be here.
   }
   ```  
```  

### Adım 3: yer imi koruma seçeneklerini yapılandırın
`PdfJoinOptions`, birleştirmenin nasıl davranacağını kontrol eder; `UseBookmarks` bayrağı motorun mevcut yer imlerini korumasını sağlar.  
```  
```csharp
   var pdfJoinOptions = new PdfJoinOptions { UseBookmarks = true };
   ```  
```  

### Adım 4: ek PDF'ler ekleyin
Her ek dosya için `Join` çağırın. Kütüphane, yer imi ağaçlarını otomatik olarak ana belgenin taslağı altına birleştirir.  
```  
```csharp
   merger.Join(Path.Combine(documentDirectory, "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
   ```  
```  

### Adım 5: birleştirilmiş PDF'yi kaydedin
Çıktı yolunu ve formatını belirtin; kütüphane tüm yer imi girişlerini koruyan tek bir PDF yazar.  
```  
```csharp
   string outputFile = Path.Combine(outputDirectory, "merged.pdf");
   merger.Save(outputFile);
   ```  
```  

## Yaygın sorunlar ve çözümler
- **Yer imleri eksik:** `PdfJoinOptions` içinde `UseBookmarks = true` olduğundan emin olun.  
- **Yol hataları:** Birleştirmeden önce `Path.Combine` kullanın ve dosyanın varlığını kontrol edin.  
- **Büyük dosyalar bellek dalgalanmalarına neden olur:** PDF'leri sıralı işleyin ve her kaydetmeden sonra `Merger` nesnesini serbest bırakın.

## Pratik uygulamalar
1. **Finansal raporların birleştirilmesi** – çeyrek bölümlerini yer imleri aracılığıyla anında erişilebilir tutun.  
2. **Ders materyali paketleri** – ders PDF'lerini birleştirirken öğrenciler için bölüm gezinmesini koruyun.  
3. **Proje dokümantasyonu paketleri** – tasarım spesifikasyonlarını, test planlarını ve sürüm notlarını tek, aranabilir bir dosyada birleştirin.

## Performans değerlendirmeleri
- 20'den fazla PDF birleştirirken RAM kullanımını düşük tutmak için bir seferde bir dosya işleyin.  
- En yeni .NET çalışma zamanını (ör. .NET 6) kullanarak optimal JIT derlemesi ve çöp toplama verimliliği elde edin.  
- 500 MB'den büyük PDF'ler için, tüm belgeyi belleğe yüklememek amacıyla `MergerSettings` aracılığıyla akış modunu etkinleştirin.

## Sıkça sorulan sorular

**Q: GroupDocs.Merger nedir?**  
A: GroupDocs.Merger, PDF ve diğer belge formatlarını programlı olarak birleştirmenize, bölmenize, döndürmenize ve başka şekillerde manipüle etmenize olanak tanıyan bir .NET kütüphanesidir.

**Q: Aynı anda iki PDF'den fazla birleştirebilir miyim?**  
A: Evet – `Join` metodunu tekrarlayarak veya bir dosya yolu koleksiyonu geçirerek tek bir işlemde istediğiniz sayıda PDF'yi birleştirebilirsiniz.

**Q: Üretim kullanımında lisanslamayı nasıl yönetirim?**  
A: GroupDocs satın alma sayfasından kalıcı bir lisans edinin; deneme lisansı sadece değerlendirme amaçlı çalışır ve 30 gün sonra sona erer.

**Q: Birleştirdiğim PDF'de yer imleri görünmüyor—ne yanlış gitti?**  
A: `PdfJoinOptions.UseBookmarks` değerinin `true` olduğundan ve her kaynak PDF'nin birleştirmeden önce gerçekten yer imi içerdiğinden emin olun.

**Q: Kütüphane .NET Core ve .NET Framework ile uyumlu mu?**  
A: Kesinlikle – .NET Core 3.1+, .NET 5/6 ve tam .NET Framework 4.6.1+ desteklenir.

## Kaynaklar
- [Dokümantasyon](https://docs.groupdocs.com/merger/net/)  
- [API Referansı](https://reference.groupdocs.com/merger/net/)  
- [GroupDocs.Merger'ı İndir](https://releases.groupdocs.com/merger/net/)  
- [Lisans Satın Al](https://purchase.groupdocs.com/buy)  
- [Ücretsiz Deneme Sürümü](https://releases.groupdocs.com/merger/net/)  
- [Geçici Lisans](https://purchase.groupdocs.com/temporary-license/)  
- [Destek Forumu](https://forum.groupdocs.com/c/merger/)  

---

**Son Güncelleme:** 2026-08-20  
**Test Edilen Versiyon:** GroupDocs.Merger 23.11 for .NET  
**Yazar:** GroupDocs

## İlgili Öğreticiler

- [GroupDocs.Merger for .NET ile Belirli PDF Sayfalarını Birleştirme: Kapsamlı Rehber](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [GroupDocs.Merger for .NET ile Belgeleri Kolayca Birleştirme: Kapsamlı Rehber](/merger/net/document-joining/groupdocs-merger-net-document-joining-guide/)
- [GroupDocs.Merger for .NET ile PDF'lere Ek Dosya Ekleme: Adım Adım Rehber](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)