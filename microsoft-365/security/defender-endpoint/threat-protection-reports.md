---
title: Yeni Uç Nokta için Microsoft Defender'de tehdit Uç Nokta için Microsoft Defender
description: Tehdit koruması raporunu kullanarak uyarı algılamalarını, kategorileri ve önem derecelerini izleme
keywords: uyarı algılama, kaynak, kategoriye göre uyarı, önem derecesi, uyarı sınıflandırması, belirleme
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 55a620343aa7cda05def64acc9027925aaa96a1e
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472605"
---
# <a name="threat-protection-report-in-microsoft-defender-for-endpoint"></a>Yeni Uç Nokta için Microsoft Defender'de tehdit Uç Nokta için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Tehdit koruması raporu, kurumda oluşturulan uyarılar hakkında üst düzey bilgiler sağlar. Rapor, zaman içinde algılama kaynaklarını, kategorileri, önem önemlerini, durumları, sınıflandırmaları ve uyarıların belirlenmesini gösteren popüler bilgileri içerir.

Pano iki bölüm halinde yapılandırılmıştır:

:::image type="content" source="images/threat-protection-reports.png" alt-text="Tehdit koruması raporu" lightbox="images/threat-protection-reports.png":::

Bölüm|Açıklama
---|---
1|Uyarılar eğilimleri
2|Uyarı özeti

## <a name="alert-trends"></a>Eğilimleri uyarın
Varsayılan olarak, uyarı eğilimleri 30 günlük dönemdeki uyarı bilgilerini en son tam gün içinde sona erdirer. Kuruluşta oluşan eğilimlere daha iyi bir bakış açısı elde etmek için gösterilen zaman dönemini ayarlayarak raporlama dönemine ince ayarlarabilirsiniz. Zaman aralığını ayarlamak için, açılan liste seçeneklerinden bir zaman aralığı seçin:

- 30 gün
- 3 ay
- 6 ay
- Özel

> [!NOTE]
> Bu filtreler yalnızca uyarı eğilimleri bölümüne uygulanır. Uyarı özeti bölümünü etkilemez.

## <a name="alert-summary"></a>Uyarı özeti

Uyarı eğilimleri popüler uyarı bilgilerini gösterirken, uyarı özeti geçerli gün kapsamındaki uyarı bilgilerini gösterir.

 Uyarı özeti, ilgili filtrenin uygulandığı belirli bir uyarı kuyruğunda detaya gitmelerini sağlar. Örneğin, Algılama kaynakları EDR çubuğundaki Arama çubuğuna tıklanması, yalnızca algılama algılamaları sonucunda oluşturulan uyarıların sonuçlarıyla birlikte uyarıların EDR getirir.

> [!NOTE]
> Özet bölümüne yansıtilen veriler, geçerli tarihten 180 gün önce kapsamdadır. Örneğin, bugünün tarihi 5 Kasım 2019 ise, özet bölümündeki veriler 5 Mayıs 2019'dan 5 Kasım 2019'a kadar olan sayıları yansıtacak.
>
> Eğilimler bölümüne uygulanan filtre özet bölümüne uygulanmaz.

## <a name="alert-attributes"></a>Uyarı öznitelikleri

Rapor, aşağıdaki uyarı özniteliklerini görüntüleyen kartlardan yapılır:

- **Algılama kaynakları**: Uyarıları tetiklemek için alıcılar tarafından kullanılan verileri sağlayan algılayıcılar ve Uç Nokta için Microsoft Defender teknolojileri hakkında bilgi gösterir.
- **Tehdit kategorileri**: Güvenlik işlemleriniz için olası odak alanlarını gösteren uyarıları tetikleyen tehdit veya saldırı etkinlik türlerini gösterir.
- **Önem derecesi**: Uyarıların önem düzeyi gösterir ve uyarıların, organizasyon açısından tehditlere yönelik kolektif olası etkilerini ve bu uyarıların yanıt düzeyini gösterir.
- **Durum**: El ile uyarı yanıtlarının verimliliğini ve otomatik düzeltmenin (etkinse) ne kadar verimli olduğunu gösteren uyarıların çözüm durumunu gösterir.
- **Sınıflandırma & belirleme**: Uyarıları gerçek tehdit (doğru uyarılar) veya yanlış algılama (yanlış uyarılar) olarak sınıflandırılmış olun, çözüm üzerine nasıl sınıflandırılmış olduğunu gösterir. Bu kartlarda, çözülmüş uyarıların belirlenmesi, bulunan gerçek tehdit türleri veya yanlış algılanmış yasal etkinlikler gibi ek içgörüler de gösterir.

## <a name="filter-data"></a>Verilere filtre uygulama

Belirli özniteliklere yönelik uyarıları eklemek veya dışarıda tutmak için sağlanan filtreleri kullanın.

> [!NOTE]
> Bu filtreler **rapora** tüm kartlar için uygulanır.

Örneğin, yalnızca yüksek önem düzeyi uyarıları ile ilgili verileri göstermek için:

1. Uyarılar **için & Filtreleri ve** \> **Önem Derecesi** \> **> altında Yüksek'i** **seçin**.
2. Önem Derecesi'nin altındaki diğer tüm **seçeneklerin seçiminin** kaldırıldığından emin olmak.
3. **Uygula'ya seçin**.

## <a name="related-topic"></a>İlgili konu

- [Cihaz durumu ve uyumluluk raporu](machine-reports.md)
