---
title: Advanced eDiscovery'te ilgi düzeyi çözümlemesi Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
titleSuffix: Office 365
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 1b092f7c-ea55-44f5-b419-63f3458fd7e0
ROBOTS: NOINDEX, NOFOLLOW
description: Bir bütün olarak işleme kalitesini test etmek, karşılaştırmak ve doğrulamak için Advanced eDiscovery sonra Test sekmesini kullanmayı öğrenin.
ms.openlocfilehash: 0ea34ce101f6891670a0b646380c965a4391ea32
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973734"
---
# <a name="test-relevance-analysis-in-advanced-ediscovery"></a>Advanced eDiscovery'te ilgi düzeyi çözümlemesi Advanced eDiscovery
  
Advanced eDiscovery'daki Test sekmesi, işlemenin genel kalitesini test, karşılaştırma ve doğrulamanızı sağlar. Bu sınamalar Toplu işlem hesaplaması sonrasında yapılır. Bir uzman koleksiyonda yer alan dosyaları etiketleerek, her etiketli dosyanın bu dosyayla ilgili olup olmadığı konusunda son karar vermelerini sağlar.
  
Tek ve çok soruna sahip senaryolarda, testler genellikle her soruna göre gerçekleştirilir. Sonuçlar her sınamadan sonra sınanarak sınanarak, belirtilen örnek test dosyalarıyla yeniden çalışabilirsiniz.
  
## <a name="testing-the-rest"></a>Gerisini test etme

"Rest'i test edin" testi, örneğin son alınan sonuçları temel alarak yalnızca belirli bir İlgi düzeyi kesme puanının üzerindeki dosyaları gözden geçirmek Advanced eDiscovery kullanılır. Uzman bu küme içindeki ilgili dosyaların sayısını değerlendirmek için, seçilen kesme puanı altında bir dosya örneğini gözden kullanır.
  
Bu test, Gözden Geçirme kümesiyle Rest popülasyonu test etmek arasında istatistikler ve karşılaştırma sağlar. Gözden geçirme kümesi, Eğitim sırasında uygunluk düzeyine göre hesaplanan sonuçlardır. Sonuçlar, aşağıdakiler gibi ayarlara ve giriş parametrelerine dayalı hesaplamaları içerir:
  
- Bir örnekteki dosya sayısının ve ilgili dosyaların örnek istatistiklerini test etmek.

- Gözden Geçir kümesi ve Kalan'ın Nüfus parametrelerinin sekmeli karşılaştırması; örneğin dosya sayısı, ilgili dosyaların tahmini sayısı, tahmini zenginlik ve başka bir uygun dosyayı bulmanın ortalama maliyeti. Maliyet parametresi ayarları yönetici tarafından ayarlanır.

"Rest'i test etmek" testini çalıştırmak için:

1. İlgi **Düzeyi Sınaması \> sekmesini** açma.

2. Sına **sekmesinde** Yeni **test'e tıklayın**. Aşağıdaki **örnekte** gösterildiği gibi, Sınama oluştur iletişim kutusu görüntülenir.

    ![İlgi Düzeyi Testi Rest sonuçları.](../media/46e6898a-f929-4fd0-88d9-6f91d04b6ce2.png)
  
3. Test **adı ve** **Açıklama'ya**, adı ve açıklamayı yazın.

4. Test **türü listesinde** Kalanları **Sına'ya tıklayın**

5. Sorun **/ Kategori listesinde** sorun adını seçin.

6. Yükle **listesinde** , yükü seçin. 

7. % **Okuma'da**, varsayılan değeri kabul etmek veya kesme ilgi düzeyi puanı için bir değer seçin. 

8. Boyutu **ayarla'da** veya varsayılan değeri kabul et'i seçin. Geri yükleme simgeleri varsayılan değerleri geri yükleyecek.

9. **Etiketlemeye başla'ya tıklayın**. Bir test örneği oluşturulur.

10. Uygunluk Etiketi sekmesinde dosyaların her bir değerini gözden **geçirin ve \> etiketlenin** ve bittiğinde, Hesapla'ya **tıklayın**.

11. Test sekmesinde Sonuçları **görüntüle'ye tıklar** ve sınama sonuçlarını görebilirsiniz. Aşağıdaki ekran görüntüsünde bir örnek gösterilmektedir.

    ![Kalan sonuçları test etmek için.](../media/b95744a9-047d-4c29-992d-04fa7e58e58a.png)
  
Önceki ekran görüntüsünde, tablonun Örnek parametreler bölümünde, örnekteki dosya sayısıyla ilgili uzman tarafından etiketlenen ayrıntılar ve bu örnekte bulunan ilgili dosyaların sayısı yer alır.
  
**Tablonun Nüfus** parametreleri bölümü, seçilen kesme şeklinde puanın altında bir puanla gözden geçirme kümesi dosya popülasyonu ve seçili kesme şeklinde puanın üzerinde olan dosyaların "Geri Kalan" popülasyonu da içinde olmak üzere test sonuçlarını içerir. Her popülasyon için aşağıdaki sonuçlar görüntülenir:
  
- %okundu - Belirtilen kesmeyi içeren dosyaları içerir

- Toplam dosya sayısı

- İlgili dosyaların tahmini sayısı

- Tahmini zenginlik

- Başka bir ilgili dosyayı bulmanın ortalama gözden geçirme maliyeti

## <a name="testing-the-slice"></a>Dilimi test etme

"Dilimi Test Etme" testi,"Rest'i test etme" sınamasına benzer, ancak dosyanın Uygunlik Okuma % ile belirtilen bir segmentinde sınama yapar.

"Dilimi Sına" testini çalıştırmak için:
  
1. İlgi **Düzeyi Sınaması \> sekmesini** açma.

2. Sına **sekmesinde** Yeni **test'e tıklayın**. Sınama **oluştur iletişim** kutusu görüntülenir.

3. Test **adı ve** **Açıklama'ya** bilgileri yazın.

4. Test **türü listesinde Dilimi** **Sına'ya tıklayın**.

5. Sorun **listesinden** sorunun adını seçin.

6. Yükle **listesinde** , yükü seçin.

7. % **Okuma arasında seçeneğinde**, varsayılan düşük ve yüksek aralık değerlerini kabul etme veya uygun uygunluk puanları için değerleri seçin.

8. Boyutu **ayarla'da** bir değer seçin veya varsayılan değeri kabul eder.

    Geri yükleme simgeleri varsayılan değeri geri yükleyecek.

9. **Etiketlemeye başla'ya tıklayın**. Bir test örneği oluşturulur.

10. Uygunluk Etiketi sekmesinde dosyaların her bir değerini gözden **geçirin ve \> etiketlenin** ve bittiğinde, Hesapla'ya **tıklayın**.

11. Test sekmesinde Sonuçları **görüntüle'ye tıklar** ve sınama sonuçlarını görebilirsiniz.
