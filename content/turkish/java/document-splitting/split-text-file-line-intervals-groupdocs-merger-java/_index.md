---
date: '2026-02-06'
description: GroupDocs.Merger for Java kullanarak bir metin dosyasını satırlara göre
  nasıl böleceğinizi öğrenin. Java projelerinde verimli belge bölme için adım adım
  bir rehber.
keywords:
- split text file line intervals Java
- document splitting GroupDocs.Merger
- Java document manipulation
title: GroupDocs.Merger for Java ile Dosyayı Satırlara Göre Bölme
type: docs
url: /tr/java/document-splitting/split-text-file-line-intervals-groupdocs-merger-java/
weight: 1
---

# GroupDocs.Merger for Java ile Satır Satır Dosya Bölme

Büyük bir metin dosyasını daha küçük, daha yönetilebilir parçalara **satır satır** bölmek, örneğin günlükleri işlemek, toplu veri içe aktarmak veya uzun raporları yeniden düzenlemek gibi durumlarda yaygın bir ihtiyaçtır. Bu öğreticide GroupDocs.Merger for Java ile **dosyayı satır satır bölmeyi** tam olarak öğrenecek, bu yaklaşımın zaman tasarrufu sağladığını görecek ve çalıştırmaya hazır bir kod örneği alacaksınız.

## Hızlı Yanıtlar
- **“Dosyayı satır satır bölmek” ne anlama gelir?** Orijinal belgeden belirli bir satır aralığını içeren ayrı metin dosyaları oluşturur.  
- **Hangi kütüphane bölmeyi gerçekleştirir?** GroupDocs.Merger for Java, satır aralıklı bölme için basit bir API sağlar.  
- **Bir lisansa ihtiyacım var mı?** Test için ücretsiz deneme sürümü yeterlidir; üretim kullanımı için kalıcı bir lisans gereklidir.  
- **Bunun yerine karakter sayısına göre bölme yapabilir miyim?** Doğrudan mümkün değildir—bölmeden önce dosyayı yeniden şekillendirmek için bir ön‑işleme adımı kullanın.  
- **Hangi Java sürümü destekleniyor?** Java 8+ çalıştırma ortamının herhangi biri uyumludur.

## “Dosyayı satır satır bölmek” nedir?
Dosyayı satır satır bölmek, tek bir metin belgesini birden fazla dosyaya ayırmak anlamına gelir; her dosya belirli bir art arda gelen satır aralığını (ör. satır 1‑3, 4‑6, vb.) içerir. Bu teknik, toplu işleme, paralel analiz veya sadece okunabilirliği artırma açısından idealdir.

## Neden GroupDocs.Merger for Java Kullanmalı?
GroupDocs.Merger, düşük seviyeli dosya‑I/O işini soyutlayarak iş mantığına odaklanmanızı sağlar. Büyük dosyaları verimli bir şekilde işler, birçok belge formatını destekler ve Maven ya da Gradle projeleriyle sorunsuz entegrasyon sağlayan temiz, akıcı bir API sunar.

## Önkoşullar
- **Java Development Kit (JDK) 8 veya üzeri** – `java` ve `javac`'in PATH'ınızda olduğundan emin olun.  
- **GroupDocs.Merger for Java** – kütüphaneyi Maven, Gradle veya doğrudan indirme yoluyla ekleyin.  
- **Temel Java bilgisi** – sınıflar, metodlar ve istisna yönetimi konusunda rahat olmalısınız.

## GroupDocs.Merger for Java Kurulumu
Projeye aşağıdaki yöntemlerden birini kullanarak kütüphaneyi ekleyin.

**Maven** – bu bağımlılığı `pom.xml` dosyanıza yapıştırın:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle** – `build.gradle` dosyanıza aşağıdaki satırı ekleyin:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Doğrudan İndirme** – resmi sürüm sayfasından JAR dosyasını da alabilirsiniz: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Lisans Edinme
API'yi keşfetmek için ücretsiz bir deneme sürümüyle başlayın. Üretim iş yükleri için GroupDocs portalından geçici ya da tam bir lisans temin edin.

## Satır Satır Metin Dosyası Bölme (Java Uygulaması)

Aşağıda özlü, adım adım bir rehber bulacaksınız. Her adım, kod bloğundan önce sade bir dille açıklanmıştır, böylece ne olduğunu tam olarak anlayabilirsiniz.

### Adım 1: Kaynak ve Çıktı Yollarını Tanımlama
İlk olarak, kütüphaneye orijinal dosyanızın nerede bulunduğunu ve bölünmüş parçaların nereye yazılacağını söyleyin.
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.txt";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToLineRanges-" + Paths.get(filePath).getFileName().toString();
```

### Adım 2: Bölme Seçeneklerini Yapılandırma
İstediğiniz satır aralıklarını tanımlayan bir `TextSplitOptions` örneği oluşturun. `new int[] { 3, 6 }` dizisi, API'ye 3. satır ve 6. satırdan sonra kesme yapmasını söyler; böylece iki parça oluşur: satır 1‑3 ve satır 4‑6.
```java
TextSplitOptions splitOptions = new TextSplitOptions(filePathOut, TextSplitMode.Interval, new int[] { 3, 6 });
```

### Adım 3: Merger'ı Başlatma ve Bölmeyi Çalıştırma
Son olarak, kaynak dosyayla `Merger` nesnesini oluşturun ve az önce oluşturduğunuz seçeneklerle `split()` metodunu çağırın.
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

Hepsi bu! Çağrı tamamlandığında, `YOUR_OUTPUT_DIRECTORY` içinde iki yeni dosya bulacaksınız; her biri belirtilen satır aralıklarını içerir.

## Pratik Uygulamalar (Neden Önemli?)
1. **Veri İşleme Hatları** – büyük günlük dosyalarını paralel ayrıştırma için daha küçük parçalara bölün.  
2. **Belge Yönetimi** – tek bir raporu dağıtımı kolaylaştırmak için bölüm‑seviyesinde dosyalara dönüştürün.  
3. **İçerik Bölümlendirme** – büyük bir makalenin bölümlerini hedefli yayın platformları için hazırlayın.

## Performans İpuçları
- **Akıcı I/O** – çok büyük dosyalarla çalışırken bellek kullanımını düşük tutmak için `Files.newBufferedReader` tercih edin.  
- **Kaynakları Kapatın** – GroupDocs.Merger çoğu temizlik işlemini yapsa da, özel akışları açıkça kapatmak sızıntıları önler.  
- **Belleği İzleyin** – gigabayt‑boyutundaki dosyaları bölmek bellek yoğun olabilir; gerekirse yeterli yığın ayırın (`-Xmx2g` veya daha yüksek).

## Yaygın Sorunlar ve Çözümleri
| Sorun | Neden Oluşur | Çözüm |
|-------|--------------|------|
| `OutOfMemoryError` | Kaynak dosya yığını aşıyor. | JVM yığın boyutunu artırın veya daha küçük aralıklarla bölün. |
| `FileNotFoundException` | Yanlış yol veya eksik izinler. | `filePath` ve `filePathOut`'un mutlak ve yazılabilir olduğundan emin olun. |
| Boş çıktı dosyaları | Aralık dizisi belgenin tamamını kapsamaz. | Son aralığın toplam satır sayısına eşit ya da daha fazla olduğundan emin olun. |

## SSS Bölümü

**S: Dosyaları satır numaraları yerine karakter sayısına göre bölebilir miyim?**  
C: Şu anda GroupDocs.Merger for Java satır aralıklarına odaklanmaktadır. Ancak, bu özelliği kullanmadan önce istediğiniz karakter sayısına göre satırları eşleyecek şekilde metninizi ön‑işlemden geçirebilirsiniz.

**S: Bölme için belirleyebileceğim aralık sayısında bir limit var mı?**  
C: Kütüphane içinde belirli bir limit yoktur; ancak aşırı sayıda bölme, işlem gereksinimlerinin artması nedeniyle performansı düşürebilir.

**S: Dosya bölme sırasında hataları nasıl yönetebilirim?**  
C: Kodunuzun etrafına try‑catch blokları ekleyerek istisnaları yakalayın ve etkili bir şekilde yönetin. GroupDocs.Merger, sorunları gidermeye yardımcı olabilecek ayrıntılı hata mesajları sağlar.

**S: Kütüphane CSV veya TSV gibi diğer metin tabanlı formatları destekliyor mu?**  
C: Evet, CSV ve TSV düz metin dosyaları olduğundan aynı satır‑aralığı mantığı uygulanır. API'de onları `.txt` dosyaları gibi ele alın.

**S: Bir klasördeki birden fazla dosya için bölmeyi otomatikleştirebilir miyim?**  
C: Kesinlikle. Yukarıdaki mantığı `Files.list(Paths.get("folder"))` ile klasördeki dosyaları döngüye alarak ve aynı `TextSplitOptions`'ı her dosyaya uygulayarak genişletebilirsiniz.

## Kaynaklar
- **Documentation:** [GroupDocs.Merger for Java Documentation](https://docs.groupdocs.com/merger/java/)  
- **API Reference:** [GroupDocs API Reference](https://reference.groupdocs.com/merger/java/)  
- **Download:** [Latest Releases](https://releases.groupdocs.com/merger/java/)  
- **Purchase and Licensing:** [Buy GroupDocs](https://purchase.groupdocs.com/buy)  
- **Free Trial:** [GroupDocs Free Trial](https://releases.groupdocs.com/merger/java/)  
- **Temporary License:** [Obtain Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Support Forum:** [GroupDocs Support](https://forum.groupdocs.com/c/merger)

---

**Son Güncelleme:** 2026-02-06  
**Test Edilen Sürüm:** GroupDocs.Merger 23.12 for Java  
**Yazar:** GroupDocs