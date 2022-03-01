---
title: Linux'ta Uç Nokta için Microsoft Defender'daki güncelleştirmeler
description: Linux'ta Uç Nokta için Microsoft Defender'da yapılan önemli değişikliklerin listesi.
keywords: microsoft, defender, Endpoint için Microsoft Defender, linux, whatsnew, sürüm
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: reference
ms.technology: mde
ms.openlocfilehash: 090c43ea1d2d9f2d158f94d1e509490c3faf4799
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63012000"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-linux"></a>Linux'ta Uç Nokta için Microsoft Defender'daki güncelleştirmeler

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="1015662-30121122156620"></a>101.56.62 (30.121122.15662.0)

- 101.53.02'de ortaya gelen ve birden çok müşteriyi etkileyen ürün kilitlenmesi düzeltildi

## <a name="1015302-30121112153020"></a>101.53.02 (30.121112.15302.0)

- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1015257-30121092152570"></a>101.52.57 (30.121092.15257.0)

- Java uygulamaları tarafından kullanılırken korumasız log4j jarları algılama özelliği eklendi. Makine, yüklenen log4j kavanozları ile Java işlemlerini çalıştırarak düzenli olarak inceleniyor. Bilgiler Uç Nokta için Microsoft Defender arka uç noktasına gönderilir ve portalın Güvenlik Açığı Yönetimi alanında ortaya çıkar.

## <a name="1014776-30121092147760"></a>101.47.76 (30.121092.14776.0)

- isteğe bağlı taramalar sırasında arşivlerin taranıp taranmamasını kontrol etmek için komut satırı aracına yeni bir anahtar eklendi. Bu, aracılığıyla yalnarak yalnarak yalndırıldı `mdatp config scan-archives --value [enabled/disabled]`. Varsayılan olarak, bu ayar olarak ayarlanır `enabled`.
- Hata düzeltmeleri

## <a name="1014513-30121082145130"></a>101.45.13 (30.121082.14513.0)

- Bu sürümden başlayarak, aşağıdaki dağıtımlara Uç Nokta desteği için Microsoft Defender'ı getiriyoruz: 
  - RHEL6.7-6.10 ve CentOS6.7-6.10 sürümleri.
  - Amazon Linux 2
  - Fedora 33 veya daha yüksek
- Hata düzeltmeleri


## <a name="1014500-30121072145000"></a>101.45.00 (30.121072.14500.0)

- Komut satırı aracına yeni anahtarlar eklendi:
  - Isteğe bağlı taramalar için paralellik derecesini kontrol altında bulundur. Bu, aracılığıyla yalnarak yalnarak yalndırıldı `mdatp config maximum-on-demand-scan-threads --value [number-between-1-and-64]`. Varsayılan olarak, paralellik derecesi `2` kullanılır.
  - Güvenlik zekası güncelleştirmeleri etkinleştirildikten veya devre dışı bırakıldıktan sonra taramaları denetleme. Bu, aracılığıyla yalnarak yalnarak yalndırıldı `mdatp config scan-after-definition-update --value [enabled/disabled]`. Varsayılan olarak, bu ayar olarak ayarlanır `enabled`.
- Ürün günlüğü düzeyini değiştirmek için artık yükseltme gerekiyor
- Hata düzeltmeleri

## <a name="1013998-30121062139980"></a>101.39.98 (30.121062.13998.0)

- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1013427-30121052134270"></a>101.34.27 (30.121052.13427.0)

- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1012964-30121042129640"></a>101.29.64 (30.121042.12964.0)

- Bu sürümden başlayarak, komut satırı istemcisi aracılığıyla tetiklenen isteğe bağlı virüsten koruma taramaları sırasında algılanan tehditler otomatik olarak düzeltilir. Kullanıcı arabirimi tarafından tetiklenen taramalar sırasında algılanan tehditlere yine el ile eylem gerekir.
- `mdatp diagnostic real-time-protection-statistics` şimdi iki ek anahtarı desteklemelidir:
  - `--sort`: çıktıyı taranan toplam dosya sayısına göre azalan düzende sıralar
  - `--top N`: en yüksek N sonuçlarını görüntüler (yalnızca belirtilen sonuçlar `--sort` için işe yarar)
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1012572-30121022125630"></a>101.25.72 (30.121022.12563.0)

- Linux'ta Uç Nokta için Microsoft Defender artık ABD Kamu müşterileri için önizlemede kullanılabilir. Daha fazla bilgi için bkz. [US Government müşterileri için Uç Nokta için Microsoft Defender](gov.md).
- DİYANE dosya sistemi olan sistemlerde Linux'ta Uç Nokta için Microsoft Defender kullanımının işletim sisteminin takılması sorunu düzeltildi
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1012563-30121022125630"></a>101.25.63 (30.121022.12563.0)

- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1012364-30121021123640"></a>101.23.64 (30.121021.12364.0)

- Bütün bir bağlama noktasının virüsten koruma dışlama listesine ekli olduğu durum için performans iyileştirmesi. Bu sürümden önce, bağlama noktasından kaynaklanan dosya etkinliği yine ürün tarafından işleniyor. Bu sürümden başlayarak, dışarıda bırakılan bağlama noktaları için dosya etkinliği engel oluyor ve bu da daha iyi ürün performansına yol açıyor
- Son isteğe bağlı tarama hakkında bilgileri görüntülemek için komut satırı aracına yeni bir seçenek eklendi. Son isteğe bağlı tarama hakkında bilgi görüntülemek için `mdatp health --details antivirus`
- Diğer performans iyileştirmeleri & düzeltmeleri

## <a name="1011853"></a>101.18.53

- EDR için Linux artık [genel kullanıma sunulmaktadır](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/edr-for-linux-is-now-is-generally-available/ba-p/2048539)
- Özel taramalar () sırasında AV dışlamalarını`--ignore-exclusions` yoksaymak için yeni bir komut satırı anahtarı (`mdatp scan custom`) eklendi
- Tanılama günlüklerinin `mdatp diagnostic create` farklı bir dizine kaydedilmiş olarak tutulmasını sağlayan yeni bir parametreyle (`--path [directory]`) genişletilmiş
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1011299"></a>101.12.99

- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1010476"></a>101.04.76

- Hata düzeltmeleri

## <a name="1010348"></a>101.03.48

- Hata düzeltmeleri

## <a name="1010255"></a>101.02.55

- Ürünün bazen bir yeniden başlatma / yükseltmeden sonra başlamama sorunu düzeltildi
- Ürün yükseltmeleri genelinde ara sunucu ayarlarının kalıcılıklarını iyileştirmesi sorunu düzeltildi

## <a name="1010075"></a>101.00.75

- Şu dosya sistem türleri için destek eklendi: `ecryptfs`, `fuse`, `fuseblk`, `jfs`, `nfs``overlay`, `ramfs`, `reiserfs`, `udf`ve`vfat`
- Komut satırı aracı [için yeni söz dizimi](linux-resources.md#configure-from-the-command-line).
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1009070"></a>100.90.70

> [!WARNING]
> Yüklü paketi 100.90.70'den önceki bir ürün sürümünden yükseltirken, Red Hat tabanlı ve SLES dağıtımlarında güncelleştirme başarısız olabilir. Bunun nedeni, dosya yolunda yapılan önemli bir değişikliktir. Geçici bir çözüm, eski paketi kaldırmak ve sonra daha yeni olan paketi yüklemektir. Bu sorun daha yeni sürümlerde yoktur.

- [Virüsten koruma dışlamaları artık joker karakterleri destekliyor](linux-exclusions.md#supported-exclusion-types)
- Komut satırı aracı [aracılığıyla performans sorunlarını](linux-support-perf.md) giderme `mdatp` özelliği eklendi
- Paket yüklemesini daha güçlü hale yapmaya yapılan iyileştirmeler
- Performans iyileştirmeleri & hata düzeltmeleri
