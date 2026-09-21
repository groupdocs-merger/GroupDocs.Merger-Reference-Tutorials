---
date: '2026-09-21'
description: GroupDocs.Merger for .NET ile PDF'yi Excel elektronik tablolarına nasıl
  gömeceğinizi öğrenin, veri sunumunu ve işlevselliği artırın.
keywords:
- embed pdf in excel
- how to embed ole
- add ole object excel
- add ole to excel
lastmod: '2026-09-21'
og_description: GroupDocs.Merger for .NET ile PDF'yi Excel'e nasıl gömeceğinizi öğrenin.
  Adım adım talimatları izleyin, hızlı cevapları görün ve yaygın hatalardan kaçının.
og_image_alt: Developer guide showing PDF embedded in an Excel spreadsheet via GroupDocs.Merger
  for .NET
og_title: GroupDocs.Merger for .NET kullanarak PDF'yi Excel'e nasıl gömülür
schemas:
- author: GroupDocs
  dateModified: '2026-09-21'
  description: Learn how to embed PDF in Excel spreadsheets with GroupDocs.Merger
    for .NET, enhancing data presentation and functionality.
  headline: How to embed PDF in Excel using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to embed PDF in Excel spreadsheets with GroupDocs.Merger
    for .NET, enhancing data presentation and functionality.
  name: How to embed PDF in Excel using GroupDocs.Merger for .NET
  steps:
  - name: '**Free trial** – test the library without cost.'
    text: '**Free trial** – test the library without cost.'
  - name: '**Temporary license** – request a temporary license on the [temporary‑license
      page](https://purchase.groupdocs.com/temporary-license/).'
    text: '**Temporary license** – request a temporary license on the [temporary‑license
      page](https://purchase.groupdocs.com/temporary-license/).'
  - name: '**Purchase** – consider purchasing a license on the [GroupDocs purchase
      page](https://purchase.groupdocs.com/buy).'
    text: '**Purchase** – consider purchasing a license on the [GroupDocs purchase
      page](https://purchase.groupdocs.com/buy).'
  - name: '**Financial reports** – attach audited statements directly beside summary
      tables.'
    text: '**Financial reports** – attach audited statements directly beside summary
      tables.'
  - name: '**Project documentation** – keep design specs, risk analyses, or contracts
      within a master tracker.'
    text: '**Project documentation** – keep design specs, risk analyses, or contracts
      within a master tracker.'
  - name: '**Training dashboards** – embed user manuals or policy PDFs for quick reference
      by staff.'
    text: '**Training dashboards** – embed user manuals or policy PDFs for quick reference
      by staff.'
  type: HowTo
- questions:
  - answer: An OLE (Object Linking and Embedding) object stores another file (PDF,
      Word, image, etc.) inside a host document, allowing in‑place editing or opening.
    question: What is an OLE object?
  - answer: Yes—GroupDocs.Merger also supports Word, PowerPoint, and Visio files.
    question: Can I embed OLE objects in other Office formats?
  - answer: Provide the password when creating the `OleSpreadsheetOptions` instance;
      the library will decrypt the file automatically.
    question: How do I handle password‑protected PDFs?
  - answer: Technically no hard limit, but files larger than 10 MB may noticeably
      increase workbook load time.
    question: Is there a size limitation for embedded PDFs?
  - answer: Visit the official [GroupDocs Documentation](https://docs.groupdocs.com/merger/net/)
      for additional code samples and API references.
    question: Where can I find more examples?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- .NET Excel integration
title: GroupDocs.Merger for .NET kullanarak PDF'yi Excel'e nasıl gömülür
type: docs
url: /tr/net/document-import/embed-ole-objects-groupdocs-merger-net/
weight: 1
---

# GroupDocs.Merger for .NET kullanarak PDF'i Excel'e nasıl gömülür

## Giriş

PDF'i Excel'e gömmek, sözleşmeler, raporlar veya teknik özellikler gibi destekleyici belgeleri verilerin bulunduğu yerde tutmanıza olanak tanır. **GroupDocs.Merger for .NET** ile sadece birkaç satır kodla hücrelere OLE nesneleri ekleyebilir, sade bir elektronik tabloyu etkileşimli, kendi içinde bütünleşik bir çalışma kitabına dönüştürebilirsiniz. Bu öğretici, kurulumdan sorun giderime kadar bilmeniz gereken her şeyi adım adım anlatıyor.

**Öğrenecekleriniz**

- C# projesinde GroupDocs.Merger for .NET'i nasıl kuracağınızı  
- Bir PDF'i (veya herhangi bir OLE‑uyumlu dosyayı) bir Excel hücresine gömmek için tam adımlar  
- Yapılandırma seçenekleri, performans ipuçları ve yaygın tuzaklar  

Başlamadan önce her şeyin hazır olduğundan emin olalım.

## Hızlı cevaplar
- **Herhangi bir dosya türünü gömebilir miyim?** Evet—OLE nesnesi olarak desteklenen herhangi bir format (PDF, Word, görüntü vb.).  
- **Geliştirme için lisansa ihtiyacım var mı?** Ücretsiz deneme sürümü test için çalışır; üretim için kalıcı bir lisans gereklidir.  
- **Hangi .NET sürümleri destekleniyor?** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7+.  
- **Excel dosya boyutu önemli ölçüde artacak mı?** Yalnızca gömülü belgenin boyutu kadar; en iyi performans için dosyaları birkaç MB'nin altında tutun.  
- **OLE nesnelerinin sayısında bir limit var mı?** Pratikte yok, ancak çok büyük çalışma kitapları yükleme süresini etkileyebilir.

## Excel'de PDF gömme nedir?

PDF'i Excel'e gömmek, tüm PDF'i bir OLE nesnesi olarak ekler ve bu nesne elektronik tablodan doğrudan açılabilir. Kullanıcılar simgeye tıklayarak orijinal belgeyi Excel'den çıkmadan görüntüler. Bu yöntem orijinal düzeni korur, hızlı referans sağlar ve ayrı dosyaları yönetme ihtiyacını ortadan kaldırır. Gömülü PDF, diğer OLE nesneleri gibi davranır; kullanıcılar simgeye çift tıklayarak PDF görüntüleyiciyi Excel ortamında açabilir.

## Neden Excel'de OLE nesneleri gömülür?

GroupDocs.Merger **120+ giriş ve çıkış formatını** destekler ve nesneleri tüm dosyayı belleğe yüklemeden gömebilir, çok sayfalı PDF'lerin hızlı işlenmesini sağlar. Bu, ayrı dosya depolarına olan ihtiyacı azaltır ve ilgili verileri bir arada tutar. Ayrıca sürüm kontrolünü basitleştirir ve tüm ilgili belgelerin çalışma kitabıyla birlikte taşınmasını sağlayarak ekipler arasındaki iş birliğini geliştirir.

## Önkoşullar

- **GroupDocs.Merger for .NET** (en son NuGet paketi)  
- **.NET Framework** 4.5+ **veya** **.NET Core/5+/6+**  
- Visual Studio 2022 veya daha yeni bir sürüm  
- Temel C# bilgisi ve dosya I/O'ya aşinalık  

## GroupDocs.Merger for .NET'i Kurma

### Kurulum

Paketi aşağıdaki yöntemlerden biriyle ekleyin:

**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI**  
“GroupDocs.Merger”ı arayın ve en son sürümü yükleyin.

### Lisans edinme

1. **Ücretsiz deneme** – kütüphaneyi maliyetsiz test edin.  
2. **Geçici lisans** – [temporary‑license page](https://purchase.groupdocs.com/temporary-license/) adresinden geçici bir lisans isteyin.  
3. **Satın alma** – [GroupDocs purchase page](https://purchase.groupdocs.com/buy) adresinden bir lisans satın almayı düşünün.

### Temel başlatma

`Merger` tüm işlemler için giriş noktasıdır.  
```csharp
using (Merger merger = new Merger("path_to_your_spreadsheet.xlsx"))
{
    // Your code to work with the document
}
```  

## Excel'de OLE nesneleri nasıl gömülür?

Kaynak çalışma kitabınızı yükleyin, OLE seçeneklerini yapılandırın ve nesneyi ekletmek için `Merger`'ı kullanın. Aşağıdaki bölümler size özlü, çalıştırmaya hazır bir iş akışı sunar.

### Özelliğin genel bakışı
OLE nesnelerini gömmek, bir hücre içinde tam bir PDF saklamanızı sağlar, orijinal düzeni korur ve Excel'den tek tıkla erişim imkanı verir.

### Adım adım uygulama

#### 1. Yolları ve sayfa numarasını ayarlayın
Elektronik tabloyu, gömülecek dosyayı ve hedef hücre adresini belirtin.

```csharp
string filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
string embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_PDF";
int pageNumber = 2; // The specific page to embed

// Output path for the modified spreadsheet
string filePathOut = Path.Combine("YOUR_OUTPUT_DIRECTORY", "OUT_SAMPLE_NAME.xlsx");
```  

#### 2. OleSpreadsheetOptions'ı yapılandırın
`OleSpreadsheetOptions` OLE nesnesinin çalışma sayfasında nerede konumlandırılacağını ve simgesinin nasıl görüneceğini tanımlar.  
```csharp
// Specify row and column indices for embedding
OleSpreadsheetOptions oleCellsOptions = new OleSpreadsheetOptions(embeddedFilePath, pageNumber)
{
    RowIndex = 2,
    ColumnIndex = 2
};
```  

#### 3. Merger'ı başlatın ve gömme işlemini gerçekleştirin
`Merger` sınıfı gerçek eklemeyi gerçekleştirir. Çağrıdan sonra, çalışma kitabı OLE simgesini içerir.

```csharp
using (Merger merger = new Merger(filePath))
{
    merger.ImportDocument(oleCellsOptions); // Import the specified document as an OLE object into the spreadsheet
    merger.Save(filePathOut); // Save the modified document
}
```  

### Yaygın sorun giderme ipuçları
- Tüm dosya yollarının mutlak olduğundan veya çalıştırılabilir dosyaya göre doğru şekilde çözüldüğünden emin olun.  
- Belirttiğiniz sayfa numarasının kaynak PDF'de mevcut olduğunu doğrulayın; aksi takdirde bir istisna fırlatılır.  
- Gömülü nesne görüntülenmiyorsa, hedef Excel sürümünün OLE'yi desteklediğini (çoğu modern sürüm destekler) doğrulayın.

## Pratik uygulamalar

Excel'de PDF gömmek şunlar için faydalıdır:

1. **Finansal raporlar** – denetlenmiş beyanları özet tabloların yanına doğrudan ekleyin.  
2. **Proje belgeleri** – tasarım özelliklerini, risk analizlerini veya sözleşmeleri ana izleyicide tutun.  
3. **Eğitim panoları** – kullanıcı kılavuzlarını veya politika PDF'lerini çalışanlar için hızlı referans olarak gömün.

## Performans değerlendirmeleri

- **Dosya boyutu** – çalışma kitabının şişmesini önlemek için gömülü PDF'leri 5 MB'nin altında tutun.  
- **Bellek kullanımı** – `GroupDocs.Merger` verileri akış olarak işler, bu yüzden büyük kaynak dosyalarda bile bellek tüketimi düşük kalır.  
- **Nesneleri serbest bırakın** – dosya tutamaçlarını hızlıca serbest bırakmak için `Merger` örneklerinde her zaman `Dispose()` çağırın.

## Sıkça sorulan sorular

**S: OLE nesnesi nedir?**  
C: OLE (Object Linking and Embedding) nesnesi, bir ana belge içinde başka bir dosyayı (PDF, Word, görüntü vb.) saklar ve yerinde düzenleme veya açma imkanı sağlar.

**S: OLE nesnelerini diğer Office formatlarına gömebilir miyim?**  
C: Evet—GroupDocs.Merger ayrıca Word, PowerPoint ve Visio dosyalarını da destekler.

**S: Şifre korumalı PDF'leri nasıl yönetirim?**  
C: `OleSpreadsheetOptions` örneğini oluştururken şifreyi sağlayın; kütüphane dosyayı otomatik olarak çözer.

**S: Gömülü PDF'ler için bir boyut sınırlaması var mı?**  
C: Teknik olarak kesin bir limit yok, ancak 10 MB'den büyük dosyalar çalışma kitabının yükleme süresini belirgin şekilde artırabilir.

**S: Daha fazla örnek nerede bulunabilir?**  
C: Ek kod örnekleri ve API referansları için resmi [GroupDocs Documentation](https://docs.groupdocs.com/merger/net/) sayfasını ziyaret edin.

## Ek kaynaklar
- **Dokümantasyon**: [GroupDocs.Merger .NET Docs](https://docs.groupdocs.com/merger/net/)  
- **API referansı**: [GroupDocs API Reference](https://reference.groupdocs.com/merger/net/)  
- **İndirilenler**: [GroupDocs Releases](https://releases.groupdocs.com/merger/net/)  
- **Lisans satın alma**: [Buy GroupDocs License](https://purchase.groupdocs.com/buy)  
- **Ücretsiz deneme**: [Try GroupDocs Free Trial](https://releases.groupdocs.com/merger/net/)  
- **Geçici lisans**: [Request Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Destek forumu**: [GroupDocs Support Forum](https://forum.groupdocs.com/c/merger)

---

**Son Güncelleme:** 2026-09-21  
**Test edilen sürüm:** GroupDocs.Merger 23.12 for .NET  
**Yazar:** GroupDocs

## İlgili Öğreticiler

- [PowerPoint'ta OLE olarak PDF gömme using GroupDocs.Merger for .NET&#58; Adım Adım Kılavuz](/merger/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/)
- [Word'de PDF gömme Using GroupDocs.Merger for .NET&#58; Adım Adım Kılavuz](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [.NET'te URL'den PDF yükleme Using GroupDocs.Merger&#58; Kapsamlı Rehber](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}