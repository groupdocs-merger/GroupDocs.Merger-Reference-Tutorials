---
title: XLS Dosyalarını Birleştirme
linktitle: XLS Dosyalarını Birleştirme
second_title: GroupDocs.Merger .NET API'si
description: Sorunsuz belge işleme için GroupDocs.Merger'ı kullanarak Excel dosyalarını .NET'te nasıl birleştireceğinizi öğrenin. Adım adım eğitimimizi takip edin.
weight: 11
url: /tr/net/spreadsheet-merging/merging-xls-files/
type: docs
---
# XLS Dosyalarını Birleştirme

## giriiş
Bu dersimizde XLS (Excel) dosyalarının nasıl birleştirileceğini inceleyeceğiz. GroupDocs.Merger, geliştiricilerin .NET uygulamalarında belgeleri zahmetsizce birleştirmesine, bölmesine, yeniden düzenlemesine ve değiştirmesine olanak tanıyan güçlü bir belge işleme API'sidir. Özellikle, GroupDocs.Merger'ın sezgisel yöntemlerini kullanarak XLS dosyalarını adım adım birleştirmeye odaklanacağız.
## Önkoşullar
Başlamadan önce aşağıdaki önkoşulları oluşturduğunuzdan emin olun:
- Visual Studio: Visual Studio'yu makinenize yükleyin.
-  .NET için GroupDocs.Merger: .NET için GroupDocs.Merger'ı şu adresten indirip yükleyin:[Burada](https://releases.groupdocs.com/merger/net/).
- .NET Framework: .NET framework'ün kurulu olduğundan emin olun.
- Örnek XLS Dosyaları: Birleştirmek istediğiniz XLS dosyalarını hazırlayın.

## Ad Alanlarını İçe Aktar
Projenizde GroupDocs.Merger'ı kullanmak için gerekli ad alanlarını içe aktararak başlayın:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Adım 1: Çıkış Dizinini Başlatın
Öncelikle birleştirilmiş XLS dosyasını kaydetmek istediğiniz dizini belirtin:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.xls");
```
## Adım 2: XLS Dosyalarını Yükleyin ve Birleştirin
Şimdi GroupDocs.Merger kullanarak XLS dosyalarını yükleyip birleştirelim:
```csharp
// Kaynak XLS dosyasını yükleyin
using (var merger = new Merger("Your Sample File"))
{
    // Birleştirilecek başka bir XLS dosyası ekleyin
    merger.Join("Your Sample File");
    
    // XLS dosyalarını birleştirin ve sonucu kaydedin
    merger.Save(outputFile);
}
```
## Adım 3: Çıkış Konumunu Görüntüleyin
Son olarak, birleştirilmiş XLS dosyasının tamamlandığını ve konumunu belirten bir mesaj görüntüleyin:
```csharp
Console.WriteLine("\nXLS files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Çözüm
Bu dersimizde XLS dosyalarının nasıl birleştirileceğini öğrendik. Sağlanan adımları izleyerek, birden fazla Excel dosyasını .NET uygulamalarınızda programlı bir şekilde verimli bir şekilde birleştirebilirsiniz.

## SSS'ler
### GroupDocs.Merger diğer belge formatlarıyla uyumlu mu?
Evet, GroupDocs.Merger, PDF, DOCX, XLSX, PPTX ve daha fazlası gibi çeşitli belge formatlarını destekler.
### GroupDocs.Merger'ı kullanarak belgeleri bölebilir miyim?
Kesinlikle! GroupDocs.Merger, belgeleri gereksinimlerinize göre bölmenize olanak tanır.
### GroupDocs.Merger için daha fazla kaynağı ve desteği nerede bulabilirim?
Belgeleri inceleyebilir ve sorular sorabilirsiniz.[GroupDocs Forumu](https://forum.groupdocs.com/c/merger/32).
### GroupDocs.Merger'ın ücretsiz deneme sürümü mevcut mu?
 Evet, bir ile başlayabilirsiniz[ücretsiz deneme](https://releases.groupdocs.com/) işlevselliği değerlendirmek için.
### GroupDocs.Merger lisansını nasıl satın alabilirim?
 Ziyaret edin[satın alma sayfası](https://purchase.groupdocs.com/buy) İhtiyaçlarınıza uygun bir lisans almak için.