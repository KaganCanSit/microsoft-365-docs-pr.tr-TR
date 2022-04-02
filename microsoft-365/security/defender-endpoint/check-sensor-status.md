---
title: Algılayıcının Uç Nokta için Microsoft Defender'da algılayıcının durumunu Uç Nokta için Microsoft Defender
description: Yanlış yapılandırılmış, etkin olmayan veya algılayıcı verilerini raporlamamış olan cihazları belirlemek için cihazlarda algılayıcıların durumunu kontrol edin.
keywords: algılayıcı, algılayıcı durumu, hatalı yapılandırılmış, etkin olmayan, algılayıcı verisi yok, algılayıcı verileri, engelli iletişimler, iletişim
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
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: bba5fde870b2916501f4154c6ff628a0d2e3ff1f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465482"
---
# <a name="check-sensor-health-state-at-microsoft-defender-for-endpoint"></a>Algılayıcıların durumuna göz atarak Uç Nokta için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-checksensor-abovefoldlink)

Algılayıcı **sorunu olan cihazlar kutucuğu** Güvenlik İşlemleri panosunda bulunur. Bu kutucuk, ayrı ayrı cihazın algılayıcı verilerini sağlayabilme ve Uç nokta için Defender hizmetiyle iletişim kurma özelliği hakkında bilgi sağlar. Bu rapor, kaç cihazla dikkat gerektir olduğunu rapor etmektedir ve sorunlu cihazları tanımları ve bilinen sorunları düzeltmeye yardımcı olur.

Kutucukta, hizmete düzgün bir şekilde rapor olmayan cihaz sayısı hakkında bilgi sağlayan iki durum göstergesi vardır:

- **Hatalı Yapılandırılmış - Bu** cihazlar kısmen uç nokta için Defender hizmetine algılayıcı verilerini bildiriyor olabilir ve düzeltilmesi gereken yapılandırma hataları olabilir.
- **Etkin Değil** - Son ay içinde yediden fazla gün boyunca Uç Nokta için Defender hizmetine bildirmeyi durduran cihazlar.

Gruplardan herhangi birini tıklatmak sizi **tercihe bağlı** olarak filtrelenmiş Cihazlar listesine yönlendirmektedir.

:::image type="content" source="images/atp-devices-with-sensor-issues-tile.png" alt-text="Algılayıcı sorunları kutucuğu bulunan cihazlar" lightbox="images/atp-devices-with-sensor-issues-tile.png":::

Cihazlar **listesinde**, durum listesini aşağıdaki durum durumuna göre filtre yapabilirsiniz:

- **Etkin** - Uç nokta için Defender hizmetine etkin olarak rapor yapan cihazlar.
- **Hatalı Yapılandırılmış - Bu** cihazlar kısmen uç nokta için Defender hizmetine algılayıcı verilerini bildiriyor olabilir, ancak düzeltilmesi gereken yapılandırma hataları olabilir. Yanlış yapılandırılmış cihazlar aşağıdaki sorunlardan birini veya bir birleşimine sahip olabilir:
  - **Algılayıcı verisi yok** - Cihazlar algılayıcı verilerini göndermeyi durdurdu. Cihazdan sınırlı uyarılar tetiklenir.
  - **İletişim engelli -** Cihazla iletişim kurma yeteneği engellidir. Daha derin çözümleme yapmak, dosyaları engellemek, cihazı ağdan ve cihazla iletişim gerektiren diğer eylemlerden göndermek işe yaramadı.
- **Etkin Değil** - Uç nokta için Defender hizmetine bildirmeyi durduran cihazlar.

Dışarı Aktar özelliğini kullanarak listenin tamamını CSV biçiminde **de indirebilirsiniz.** Filtreler hakkında daha fazla bilgi için bkz [. Cihazlar listesini görüntüleme ve düzenleme](machines-view-overview.md).

> [!NOTE]
> Filtrelenmemiş verileri görüntülemek için listeyi CSV biçiminde dışarı aktarın. CSV dosyası, görünümde uygulanan herhangi bir filtreye bakılmaksızın kuruluşta tüm cihazları içerir ve kuruluşun ne kadar büyük olduğuna bağlı olarak indirmesi çok uzun zaman almalıdır.

:::image type="content" source="images/atp-devices-list-page.png" alt-text="Cihaz listesi sayfasında Dışarı Aktar sekmesi" lightbox="images/atp-devices-list-page.png":::

Yanlış yapılandırılmış veya etkin olmayan bir cihaza tıklarken cihaz ayrıntılarını görüntüebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Uç Nokta için Defender'da uygun olmayan algılayıcıları düzeltme](fix-unhealthy-sensors.md)
- [İstemci çözümleyicisi genel bakış](overview-client-analyzer.md)
- [İstemci çözümleyicisini indirme ve çalıştırma](download-client-analyzer.md)
- [İstemci çözümleyicisini çözümleyiciyi çalışma Windows](run-analyzer-windows.md)
- [macOS veya Linux'ta istemci çözümleyicisini çalıştırın](run-analyzer-macos-linux.md)
- [Windows'da gelişmiş sorun giderme için veri Windows](data-collection-analyzer.md)
