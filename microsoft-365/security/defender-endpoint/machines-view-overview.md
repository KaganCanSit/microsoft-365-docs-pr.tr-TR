---
title: Uç nokta cihazlar için Microsoft Defender listesini görüntüleme ve düzenleme
description: İncelemeleri geliştirmek için Cihazlar listesinden kullanabileceğiniz sıralama, filtreleme ve listenin dışarı aktarma gibi kullanılabilir özellikleri hakkında bilgi edinebilirsiniz.
keywords: sıralama, filtreleme, dışarı aktarma, csv, cihaz adı, etki alanı, son görülen, iç IP, durum, etkin uyarılar, etkin kötü amaçlı yazılım algılamaları, tehdit kategorisi, uyarıları gözden geçirme, ağ, bağlantı, kötü amaçlı yazılım, tür, parola çalmak, fidye yazılımı, istismar, tehdit, genel kötü amaçlı yazılım, istenmeyen yazılım
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
ms.openlocfilehash: bef6685f6bf3a998e9b37504fc5ea5e67b4f1bfd
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998025"
---
# <a name="view-and-organize-the-microsoft-defender-for-endpoint-devices-list"></a>Uç Nokta Cihazları için Microsoft Defender listesini görüntüleme ve düzenleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-machinesview-abovefoldlink)

Cihazlar **listesinde** , ağda uyarıların oluşturulmuş olduğu cihazların listesi görüntülenir. Varsayılan olarak, kuyruk son 30 gün içinde görülen cihazları görüntüler.

En çok risk altında olan cihazların kolayca tanımlanması için etki alanı, risk düzeyi, işletim sistemi platformu gibi bilgileri ve diğer ayrıntıları bir bakışta görebilirsiniz.

Cihaz listesi görünümünü özelleştirmek için seçebileceğiniz çeşitli seçenekler vardır. Üst gezintiden şunlarıabilirsiniz:

- Sütun ekleme veya kaldırma
- Listenin tamamını CSV biçiminde dışarı aktarma
- Sayfa başına göstermek istediğiniz öğe sayısını seçin
- Filtre uygulama

Ekleme işlemi sırasında Cihazlar listesi, **algılayıcı** verilerini bildirmeye başlayan cihazlarla aşamalı olarak doldurulur. Çevrimiçi duruma geldiklerinde eklenilen uç noktalarınızı izlemek için bu görünümü kullanın veya çevrimdışı çözümleme için tam uç nokta listesini CSV dosyası olarak indirin.

> [!NOTE]
> Cihaz listesini dışarı aktardıysanız, bu liste, organizasyonlar'daki tüm cihazlarınızı içerir. İndirmek, kuruma ne kadar büyük olduğunu bağlı olarak önemli ölçüde zaman alsa da bu kadar uzun olabilir. Listeyi CSV biçiminde dışarı aktaran veriler filtrelenmemiş bir şekilde görüntülenir. CSV dosyası, görünümde kendisine uygulanan filtrelerden bağımsız olarak, kuruluşta tüm cihazları içerir.

![Cihaz listesiyle birlikte cihazlar listesinin görüntüsü.](images/device-inventory.png)

## <a name="sort-and-filter-the-device-list"></a>Cihaz listesini sıralama ve filtreleme

Uyarı listesini sınırlandırarak daha odaklanmış bir görünüm elde etmek için aşağıdaki filtreleri uygulayabilirsiniz.

### <a name="device-name"></a>Cihaz adı

Araştırırken ilgilendiğin cihazın adını seçin.

### <a name="domain"></a>Etki alanı

Araştırırken ilgilendiğin etki alanını seçin.

### <a name="risk-level"></a>Risk düzeyi

Risk düzeyi, cihaz üzerinde etkin uyarıların türleri ve önem düzeyi de içinde olmak üzere bir etmenler birleşimine bağlı olarak cihazın genel risk değerlendirmesini yansıtmaktadır. Etkin uyarıları çözümleme, düzeltme etkinliklerini onaylama ve sonraki uyarıları gizleme, risk düzeyini düşürebilir.

### <a name="exposure-level"></a>Pozlama düzeyi

Etkilenme düzeyi, bekleyen güvenlik önerilerinin kümülatif etkisine bağlı olarak cihazın geçerli etkilenme düzeyini yansıtmaktadır. Olası düzeyler düşük, orta ve yüksektir. Düşük pozlama, cihazlarınızı açıklardan yararlanmaya karşı daha az korumasız olduğu anlamına gelir.

Pozlama düzeyi "Veri yok" ifadesini belirtiyorsa, bunun birkaç nedeni olabilir:

- Cihaz raporlamayı 30'dan fazla gün için durdurdu. Bu durumda devre dışı olduğu kabul edilir ve maruz kalma durumu hesaplanmayacaktır.
- Cihaz işletim sistemi desteklenmiyor- Uç Nokta için [Microsoft Defender için en düşük gereksinimlere bakın](minimum-requirements.md).
- Eski aracısı olan cihaz (pek olası değil).

### <a name="os-platform"></a>Işletim Sistemi Platformu

Yalnızca ilgilendiğin işletim sistemi platformlarını seçin.

### <a name="windows-versions"></a>Windows sürümleri

Yalnızca araştır Windows ilgili sürümleri seçin.

### <a name="health-state"></a>Durum

Aşağıdaki cihaz durumuna göre filtre uygulama:

- **Etkin**: Algılayıcı verilerini etkin bir şekilde hizmete bildiren cihazlar.
- **Etkin değil**: 7 gün boyunca sinyalleri göndermeyi durduran cihazlar.
- **Yanlış Yapılandırılmış: Hizmetle** iletişim engeli olan veya algılayıcı verilerini gönderemeyen cihazlar. Yanlış yapılandırılmış cihazlar, aşağıdakiler için daha fazla sınıflandırılabilir:
  - Algılayıcı verisi yok
  - Engelli iletişimler

  Hatalı yapılandırılmış cihazlardaki sorunları çözme hakkında daha fazla bilgi için bkz. [Uygun olmayan algılayıcıları düzeltme](fix-unhealthy-sensors.md).

### <a name="onboarding-status"></a>Ekleme durumu

Ekleme durumu, cihazın şu anda Uç Nokta için Microsoft Defender'a ekli olup olmadığını gösterir. Aşağıdaki eyaletlere göre filtre yapabilirsiniz:

- **Ekli**: Uç nokta, Uç Nokta için Microsoft Defender'a ekli olarak gönderilir.

- **Kullanılabilir**: Uç nokta ağda desteklenen bir cihaz olarak bulundu ancak şu anda eklemedi. Microsoft bu cihazları işe eklemeyi kesinlikle önermektedir.

- **Desteklenmiyor**: Uç nokta ağda bulundu ancak Uç Nokta için Microsoft Defender tarafından desteklenmiyor.

- **Yetersiz bilgi**: Sistem, cihazın desteklanabilirliğini belirleyemedi.

### <a name="last-device-update"></a>Son cihaz güncelleştirmesi

Cihazınızın en son ne zaman güncelleştirilmiş olduğunu temel alarak görünüme filtre uygulama.

### <a name="first-seen"></a>İlk görülen

Görünümlerinizi, cihazın ağda ilk ne zaman görüntülandığına veya Uç nokta algılayıcısı için Microsoft Defender tarafından ilk ne zaman bildirildiğına göre filtrele.

### <a name="tags"></a>Etiketler

Listeyi, tek tek cihazlara ekleytilen gruplama ve etiketlemeye göre filtrele. Bkz [. Cihaz etiketlerini oluşturma ve yönetme](machine-tags.md).

## <a name="related-topics"></a>İlgili konular

- [Uç Nokta Cihazları için Microsoft Defender listesinde cihazları araştırma](investigate-machines.md)
