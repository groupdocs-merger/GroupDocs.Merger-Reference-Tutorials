---
title: XLSM Dosyalarını Birleştirme Kılavuzu
linktitle: XLSM Dosyalarını Birleştirme Kılavuzu
second_title: GroupDocs.Merger .NET API'si
description: XLSM dosyalarını GroupDocs.Merger for .NET ile sorunsuz bir şekilde birleştirin. Excel çalışma kitaplarını programlı bir şekilde verimli bir şekilde birleştirin. Belge işleme yeteneklerinizi geliştirin.
type: docs
weight: 13
url: /tr/net/spreadsheet-merging/guide-merging-xlsm-files/
---
## giriiş
Bu eğitimde XLSM (Excel Makro Etkin Çalışma Kitabı) dosyalarının nasıl birleştirileceğini inceleyeceğiz. GroupDocs.Merger, geliştiricilerin dosyaları programlı olarak birleştirme, bölme ve değiştirme dahil olmak üzere belge formatlarını değiştirmesine olanak tanıyan güçlü bir kitaplıktır.
## Önkoşullar
Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:
-  GroupDocs.Merger for .NET: Kitaplığı şuradan indirip yükleyin:[Burada](https://releases.groupdocs.com/merger/net/).
- Geliştirme Ortamı: Visual Studio'yu veya uyumlu herhangi bir .NET geliştirme ortamını kurun.
- XLSM Dosyaları: Birleştirmek istediğiniz XLSM dosyalarını hazırlayın.

## Ad Alanlarını İçe Aktar
Öncelikle .NET projenize gerekli ad alanlarını ekleyin:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Adım 1: Çıktı Klasörünü ve Dosya Adını Tanımlayın
Çıktı klasörünü ve birleştirilmiş XLSM dosyasının adını tanımlayarak başlayın:
```csharp
string outputFolder = "YourOutputDirectory";
string outputFile = Path.Combine(outputFolder, "merged.xlsm");
```
## Adım 2: XLSM Dosyalarını Yükleyin ve Birleştirin
Daha sonra kaynak XLSM dosyalarını yükleyin ve bunları tek bir dosyada birleştirin:
```csharp
// Kaynak XLSM dosyasını yükleyin
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    // Birleştirmek için başka bir XLSM dosyası ekleyin
    merger.Join("Your Sample File");
    // XLSM dosyalarını birleştirin ve sonucu kaydedin
    merger.Save(outputFile);
}
```
## 3. Adım: Birleştirmenin Tamamlandığını Kontrol Edin
Son olarak, birleştirmenin başarıyla tamamlandığını kullanıcıya bildirin ve çıktı yolunu görüntüleyin:
```csharp
Console.WriteLine("\nXLSM files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Çözüm
XLSM dosyalarını programlı olarak nasıl birleştireceğinizi öğrendiniz. Bu kitaplık, belge işleme görevlerini basitleştirerek .NET uygulamalarınız içinde verimli dosya birleştirmeye olanak tanır.

## SSS'ler
### GroupDocs.Merger büyük XLSM dosyalarını işleyebilir mi?
Evet, GroupDocs.Merger büyük XLSM dosyalarını performans sorunları olmadan verimli bir şekilde işler.
### GroupDocs.Merger, XLSM'nin yanı sıra diğer dosya formatlarını da destekliyor mu?
Evet, GroupDocs.Merger, DOCX, PDF, PPTX ve daha fazlası gibi çeşitli belge formatlarını destekler.
### GroupDocs.Merger .NET Core uygulamalarıyla uyumlu mu?
Evet, GroupDocs.Merger hem .NET Framework hem de .NET Core ortamlarıyla uyumludur.
### GroupDocs.Merger'ı kullanarak şifrelenmiş XLSM dosyalarını birleştirebilir miyim?
Evet, GroupDocs.Merger, şifrelenmiş XLSM dosyalarının doğru kimlik bilgileriyle birleştirilmesini destekler.
### GroupDocs.Merger toplu işleme yetenekleri sağlıyor mu?
Evet, GroupDocs.Merger, birden fazla XLSM dosyasının aynı anda birleştirilmesi için toplu işleme izin verir.