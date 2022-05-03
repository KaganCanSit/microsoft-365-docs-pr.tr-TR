---
title: Linux'ta Uç Nokta için Microsoft Defender'deki yenilikler
description: Linux'ta Uç Nokta için Microsoft Defender için önemli değişikliklerin listesi.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, linux, whatsnew, release
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
ms.openlocfilehash: 385b139390192d172b3bbbcbefd5efc2b793d4ab
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65173498"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-linux"></a>Linux'ta Uç Nokta için Microsoft Defender'deki yenilikler

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="1016577-30122032165770"></a>101.65.77 (30.122032.16577.0)

- `conflicting_applications` içindeki alanı `mdatp health` yalnızca en son 10 işlemi gösterecek şekilde ve işlem adlarını içerecek şekilde geliştirildi. Bu, Linux için Uç Nokta için Microsoft Defender hangi işlemlerin çakışıyor olduğunu belirlemeyi kolaylaştırır.
- Hata düzeltmeleri

## <a name="1016274-30122022162740"></a>101.62.74 (30.122022.16274.0)

- Ürünün eski çekirdek sürümlerinde çalışırken boyutu 2 GB'tan büyük dosyalara erişimi yanlış engellemesi sorunu giderildi
- Hata düzeltmeleri

## <a name="1016093-30122012160930"></a>101.60.93 (30.122012.16093.0)

- Bu sürüm [CVE-2022-23278](https://msrc-blog.microsoft.com/2022/03/08/guidance-for-cve-2022-23278-spoofing-in-microsoft-defender-for-endpoint/) için bir güvenlik güncelleştirmesi içerir

## <a name="1016005-30122012160050"></a>101.60.05 (30.122012.16005.0)

- RHEL 6.10 için çekirdek sürümü 2.6.32-754.43.1.el6.x86_64 desteği eklendi
- Hata düzeltmeleri

## <a name="1015880-30122012158800"></a>101.58.80 (30.122012.15880.0)

- Komut satırı aracı artık karantinaya alınan dosyaların dosyanın ilk algılandığı konumdan farklı bir konuma geri yüklenmesini destekliyor. Bu işlem aracılığıyla `mdatp threat quarantine restore --id [threat-id] --path [destination-folder]`yapılabilir.
- Bu sürümden başlayarak Linux için ağ koruması isteğe bağlı olarak değerlendirilebilir
- Hata düzeltmeleri

## <a name="1015662-30121122156620"></a>101.56.62 (30.121122.15662.0)

- 101.53.02'de ortaya çıkan ve birden çok müşteriyi etkileyen bir ürün kilitlenmesi düzeltildi

## <a name="1015302-30121112153020"></a>101.53.02 (30.121112.15302.0)

- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1015257-30121092152570"></a>101.52.57 (30.121092.15257.0)

- Java uygulamaları tarafından kullanılan güvenlik açığı olan log4j jar'larını algılama özelliği eklendi. Makine, yüklenen log4j jar'ları ile Java işlemlerini çalıştırmak için düzenli aralıklarla incelenir. Bilgiler Uç Nokta için Microsoft Defender arka ucuna bildirilir ve portalın Güvenlik Açığı Yönetimi alanında kullanıma sunulur.

## <a name="1014776-30121092147760"></a>101.47.76 (30.121092.14776.0)

- İsteğe bağlı taramalar sırasında arşivlerin taranıp taranmayacağını denetlemek için komut satırı aracına yeni bir anahtar eklendi. Bu, aracılığıyla `mdatp config scan-archives --value [enabled/disabled]`yapılandırılabilir. Bu, varsayılan olarak olarak `enabled`ayarlanır.
- Hata düzeltmeleri

## <a name="1014513-30121082145130"></a>101.45.13 (30.121082.14513.0)

- Bu sürümden başlayarak, aşağıdaki dağıtımlara Uç Nokta için Microsoft Defender destek getiriyoruz: 
  - RHEL6.7-6.10 ve CentOS6.7-6.10 sürümleri.
  - Amazon Linux 2
  - Fedora 33 veya üzeri
- Hata düzeltmeleri


## <a name="1014500-30121072145000"></a>101.45.00 (30.121072.14500.0)

- Komut satırı aracına yeni anahtarlar eklendi:
  - İsteğe bağlı taramalar için paralellik derecesini denetleme. Bu, aracılığıyla `mdatp config maximum-on-demand-scan-threads --value [number-between-1-and-64]`yapılandırılabilir. Varsayılan olarak, bir paralellik `2` derecesi kullanılır.
  - Güvenlik bilgileri güncelleştirmelerinin etkinleştirilip etkinleştirilmediğini veya devre dışı bırakılıp bırakılmayacağını denetleyin. Bu, aracılığıyla `mdatp config scan-after-definition-update --value [enabled/disabled]`yapılandırılabilir. Bu, varsayılan olarak olarak `enabled`ayarlanır.
- Ürün günlüğü düzeyini değiştirmek için artık yükseltme gerekiyor
- Hata düzeltmeleri

## <a name="1013998-30121062139980"></a>101.39.98 (30.121062.13998.0)

- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1013427-30121052134270"></a>101.34.27 (30.121052.13427.0)

- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1012964-30121042129640"></a>101.29.64 (30.121042.12964.0)

- Bu sürümden başlayarak, komut satırı istemcisi aracılığıyla tetiklenen isteğe bağlı virüsten koruma taramaları sırasında algılanan tehditler otomatik olarak düzeltilir. Kullanıcı arabirimi aracılığıyla tetiklenen taramalar sırasında algılanan tehditler yine de el ile eylem gerektirir.
- `mdatp diagnostic real-time-protection-statistics` şimdi iki ek anahtarı destekler:
  - `--sort`: Taranan toplam dosya sayısına göre azalan çıktıyı sıralar
  - `--top N`: en iyi N sonuçlarını görüntüler (yalnızca belirtilirse `--sort` çalışır)
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1012572-30121022125630"></a>101.25.72 (30.121022.12563.0)

- Linux'ta Uç Nokta için Microsoft Defender artık ABD Kamu müşterileri için önizleme aşamasında kullanıma sunulmuştur. Daha fazla bilgi için bkz. [US Government müşterileri için Uç Nokta için Microsoft Defender](gov.md).
- FUSE dosya sistemlerine sahip sistemlerde Linux üzerinde Uç Nokta için Microsoft Defender kullanımının işletim sisteminin kilitlenmesine neden olduğu bir sorun düzeltildi
- Performans iyileştirmeleri & diğer hata düzeltmeleri

## <a name="1012563-30121022125630"></a>101.25.63 (30.121022.12563.0)

- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1012364-30121021123640"></a>101.23.64 (30.121021.12364.0)

- Virüsten koruma dışlama listesine bağlama noktasının tamamının eklendiği durum için performans iyileştirmesi. Bu sürümden önce, bağlama noktasından kaynaklanan dosya etkinliği yine de ürün tarafından işlendi. Bu sürümden başlayarak, dışlanan bağlama noktaları için dosya etkinliği gizlenerek daha iyi ürün performansına yol açar
- Son isteğe bağlı tarama hakkındaki bilgileri görüntülemek için komut satırı aracına yeni bir seçenek eklendi. Son isteğe bağlı tarama hakkındaki bilgileri görüntülemek için `mdatp health --details antivirus`
- Hata düzeltmeleri & diğer performans iyileştirmeleri

## <a name="1011853"></a>101.18.53

- Linux için EDR genel [kullanıma sunuldu](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/edr-for-linux-is-now-is-generally-available/ba-p/2048539)
- Özel taramalar sırasında AV dışlamalarını yoksaymak için yeni bir komut satırı anahtarı`--ignore-exclusions` () eklendi (`mdatp scan custom`)
- Tanılama günlüklerinin farklı bir dizine kaydedilmesini sağlayan yeni bir parametre (`--path [directory]`) ile genişletilmiş `mdatp diagnostic create`
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1011299"></a>101.12.99

- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1010476"></a>101.04.76

- Hata düzeltmeleri

## <a name="1010348"></a>101.03.48

- Hata düzeltmeleri

## <a name="1010255"></a>101.02.55

- Ürünün bazen yeniden başlatma / yükseltmeyi takip etmeye başlamaması sorunu düzeltildi
- Ara sunucu ayarlarının ürün yükseltmelerinde kalıcı olmaması sorunu düzeltildi

## <a name="1010075"></a>101.00.75

- Aşağıdaki dosya sistemi türleri için destek eklendi: , , , , , `nfs`, , `overlay`, `reiserfs``ramfs``udf`ve `jfs``fuseblk``fuse``ecryptfs``vfat`
- [Komut satırı aracı](linux-resources.md#configure-from-the-command-line) için yeni söz dizimi.
- Performans iyileştirmeleri & hata düzeltmeleri

## <a name="1009070"></a>100.90.70

> [!WARNING]
> Yüklü paketi 100.90.70'ten önceki bir ürün sürümünden yükseltirken, güncelleştirme Red Hat tabanlı ve SLES dağıtımlarında başarısız olabilir. Bunun nedeni dosya yolundaki önemli bir değişikliktir. Geçici bir çözüm, eski paketi kaldırmak ve daha sonra yenisini yüklemektir. Bu sorun daha yeni sürümlerde mevcut değildir.

- Virüsten [koruma dışlamaları artık joker karakterleri destekliyor](linux-exclusions.md#supported-exclusion-types)
- Komut satırı aracı aracılığıyla `mdatp` [performans sorunlarını giderme](linux-support-perf.md) özelliği eklendi
- Paket yüklemesini daha sağlam hale getirmek için geliştirmeler
- Performans iyileştirmeleri & hata düzeltmeleri
