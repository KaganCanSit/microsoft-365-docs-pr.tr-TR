---
title: eBulma'da İlgi Analizini Test Et (Premium)
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
description: Genel işleme kalitesini test etmek, karşılaştırmak ve doğrulamak için eBulma'da (Premium) Batch hesaplamasının ardından Test sekmesini kullanmayı öğrenin.
ms.openlocfilehash: e568552501a07c74e7500a1041e69f4994668cd2
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64991874"
---
# <a name="test-relevance-analysis-in-ediscovery-premium"></a>eBulma'da İlgi Analizini Test Et (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]
  
Microsoft Purview eKeşif(Premium) içindeki Test sekmesi, genel işleme kalitesini test etme, karşılaştırma ve doğrulamanızı sağlar. Bu testler Batch hesaplaması sonrasında gerçekleştirilir. Bir uzman, koleksiyondaki dosyaları etiketleyerek etiketlenen her dosyanın davayla ilgili olup olmadığı konusunda son kararı verir.
  
Tek ve birden çok sorunlu senaryolarda testler genellikle sorun başına gerçekleştirilir. Sonuçlar her test sonrasında görüntülenebilir ve test sonuçları belirtilen örnek test dosyalarıyla yeniden görüntülenebilir.
  
## <a name="testing-the-rest"></a>Gerisini test etme

"Geri Kalanları Test Et" testi, örneğin son eBulma (Premium) sonuçlarına göre yalnızca belirli bir İlgi kesme puanının üzerindeki dosyaları gözden geçirmek için önemli kararları doğrulamak için kullanılır. Uzman, belirli bir kesme puanı altındaki bir dosya örneğini inceler ve bu kümedeki ilgili dosyaların sayısını değerlendirir.
  
Bu test, istatistikler ve Gözden Geçirme kümesi ile Rest popülasyonunu test et arasında bir karşılaştırma sağlar. Gözden geçirme kümesinin sonuçları Eğitim sırasında İlgi'ye göre hesaplanır. Sonuçlar, ayarlara ve giriş parametrelerine dayalı hesaplamaları içerir, örneğin:
  
- Bir örnekteki dosya sayısının örnek istatistiklerini test edin ve ilgili dosyaları belirleyin.

- Gözden Geçirme kümesinin Ve Geri Kalanı'nın Population parametrelerinin tablosal karşılaştırması; örneğin, dosya sayısı, ilgili dosyaların tahmini sayısı, tahmini zenginlik ve başka bir ilgili dosyayı bulmanın ortalama maliyeti. Maliyet parametresi ayarları yönetici tarafından ayarlanabilir.

"Rest'i Test Et" testini çalıştırmak için:

1. **İlgi \> Testi** sekmesini açın.

2. **Test** sekmesinde **Yeni test'e** tıklayın. Aşağıdaki örnekte gösterildiği gibi **Test oluştur** iletişim kutusu görüntülenir.

    ![İlgi Rest sonuçlarını test edin.](../media/46e6898a-f929-4fd0-88d9-6f91d04b6ce2.png)
  
3. **Test adı** ve **Açıklama** alanına adı ve açıklamayı yazın.

4. **Test türü** listesinde **Kalanları test et'i** seçin

5. **Sorun / Kategori** listesinde sorun adını seçin.

6. **Yükle** listesinde yükü seçin. 

7. **Okuma %** alanında varsayılan değeri kabul edin veya kesme İlgi puanı için bir değer seçin. 

8. **Boyutu ayarla'da** veya varsayılan değeri kabul edin. Geri yükleme simgeleri varsayılan değerleri geri yükler.

9. **Etiketlemeyi başlat'a** tıklayın. Bir test örneği oluşturulur.

10. **İlgi \> Etiketi** sekmesindeki dosyaların her birini gözden geçirin ve etiketleyin ve işiniz bittiğinde **Hesapla'ya** tıklayın.

11. Test sekmesinde Sonuçları **görüntüle'ye** tıklayarak test sonuçlarını görebilirsiniz. Aşağıdaki ekran görüntüsünde bir örnek gösterilmiştir.

    ![Kalan sonuçları test edin.](../media/b95744a9-047d-4c29-992d-04fa7e58e58a.png)
  
Önceki ekran görüntüsünde, tablonun **Örnek parametreler** bölümünde, uzman tarafından etiketlenen örnekteki dosya sayısı ve bu örnekte bulunan ilgili dosyaların sayısı hakkında ayrıntılar yer alır.
  
Tablonun **Population parametreleri** bölümü, seçilen kesmenin altında bir puana sahip dosyaların küme popülasyonunu gözden geçirme ve seçili kesmenin üzerinde bir puana sahip dosyaların "Kalan" popülasyonu dahil olmak üzere test sonuçlarını içerir. Her popülasyon için aşağıdaki sonuçlar görüntülenir:
  
- Okuma yüzdesine sahip dosyaları içerir - Belirtilen kesme

- Toplam dosya sayısı

- İlgili dosyaların tahmini sayısı

- Tahmini zenginlik

- Başka bir ilgili dosyayı bulmanın ortalama gözden geçirme maliyeti

## <a name="testing-the-slice"></a>Dilimi test etme

"Test the Slice" testi, "Test the Rest" testine benzer, ancak İlgi Okuması % tarafından belirtilen dosya kümesinin bir kesimine test gerçekleştirir.

"Dilimi Test Et" testini çalıştırmak için:
  
1. **İlgi \> Testi** sekmesini açın.

2. **Test** sekmesinde **Yeni test'e** tıklayın. **Test oluştur** iletişim kutusu görüntülenir.

3. **Test adı** ve **Açıklama** alanına bilgileri yazın.

4. **Test türü** listesinde **Dilimi Test Et'i** seçin.

5. **Sorun** listesinde sorun adını seçin.

6. **Yükle** listesinde yükü seçin.

7. **Arasında okuma %** alanında varsayılan düşük ve yüksek aralık değerlerini kabul edin veya kesme İlgi puanları için değerleri seçin.

8. **Boyut ayarla** bölümünde bir değer seçin veya varsayılan değeri kabul edin.

    Geri yükleme simgeleri varsayılan değeri geri yükler.

9. **Etiketlemeyi başlat'a** tıklayın. Bir test örneği oluşturulur.

10. **İlgi \> Etiketi** sekmesindeki dosyaların her birini gözden geçirin ve etiketleyin ve işiniz bittiğinde **Hesapla'ya** tıklayın.

11. Test sekmesinde Sonuçları **görüntüle'ye** tıklayarak test sonuçlarını görebilirsiniz.
