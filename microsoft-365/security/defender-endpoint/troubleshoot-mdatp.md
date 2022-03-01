---
title: Uç nokta hizmet sorunları için Microsoft Defender'da sorun giderme
description: Hizmete erişmeye çalışırken sunucu hataları gibi bilinen sorunlar için çözüm ve geçici çözümler bulun.
keywords: uç nokta için Microsoft Defender sorunlarını giderme, sunucu hatası, erişim reddedildi, geçersiz kimlik bilgileri, veri yok, pano portalı, izin ver, olay görüntüleyicisi
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
ms.topic: troubleshooting
ms.technology: mde
ms.openlocfilehash: e9a0fdb1bd10d734da95ba88c459ec665635f40e
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998192"
---
# <a name="troubleshoot-service-issues"></a>Hizmet sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

Bu bölüm, Uç nokta için Microsoft Defender hizmetini kullanırken ortaya çıkabilecek sorunları ele almaktadır.

## <a name="server-error---access-is-denied-due-to-invalid-credentials"></a>Sunucu hatası - Geçersiz kimlik bilgileri nedeniyle erişim reddedildi

Hizmete erişmeye çalışırken bir sunucu hatasıyla karşılaşırsanız, tarayıcı tanımlama bilgisi ayarlarını değiştirebilirsiniz.
Tarayıcınızı tanımlama bilgilerine izin verecek şekilde yapılandırabilirsiniz.

## <a name="elements-or-data-missing-on-the-portal"></a>Portalda öğeler veya veriler eksik

Bazı öğeler veya veriler Microsoft 365 Defender ara sunucu ayarlarının bunu engelliyor olabilir.

Proxy izin listesine `*.security.microsoft.com` bu listeye dahil olduğundan emin olun.

> [!NOTE]
> Aşağıdaki uç noktaları eklerken HTTPS protokolünü kullanabilirsiniz.

## <a name="microsoft-defender-for-endpoint-service-shows-event-or-error-logs-in-the-event-viewer"></a>Uç Nokta hizmeti için Microsoft Defender Olay Görüntüleyicisi'nde olay veya hata günlüklerini gösteriyor

Uç [Nokta için Microsoft Defender hizmeti tarafından bildirilen](event-error-codes.md) olay kimliklerinin listesi için bkz. Olay Görüntüleyicisi'ni kullanarak olayları ve hataları gözden geçirme. Bu makalede olay hatalarına neden olan sorun giderme adımları da yerlanmıştır.

## <a name="microsoft-defender-for-endpoint-service-fails-to-start-after-a-reboot-and-shows-error-577"></a>Uç Nokta hizmeti için Microsoft Defender yeniden başlatmadan sonra başlatıla görüntüden başarısız oldu ve 577 hatasını gösteriyor

Ekleme cihazları başarıyla tamamlanırsa, ancak yeniden başlatma sonrasında Uç Nokta için Microsoft Defender başlayacı yoksa ve 577 hatası gösteriyorsa, Windows Defender'ın bir ilke tarafından devre dışı bırakılamaıp devre dışı olmadığını kontrol edin.

Daha fazla bilgi için bkz[. İlke tarafından Microsoft Defender Virüsten Koruma devre dışı bırakıldıktan emin olmak.](troubleshoot-onboarding.md#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)

## <a name="known-issues-with-regional-formats"></a>Bölgesel biçimlerle ilgili bilinen sorunlar

### <a name="date-and-time-formats"></a>Tarih ve saat biçimleri

Saat ve tarih biçimleriyle ilgili bilinen bazı sorunlar vardır.

Aşağıdaki tarih biçimleri desteklemektedir:

- AA/2/yyyy
- lar/AA/yyyy

Aşağıdaki tarih ve saat biçimleri şu anda desteklenmiyor:

- Tarih biçimi yyyy/AA/d
- Tarih biçimi d/AA/yy
- yy ile tarih biçimi. Yalnızca yyyy gösterir.
- Zaman biçimi SS:dd:ss desteklenmiyor (12 saat AM/PM biçimi desteklenmiyor). Yalnızca 24 saatlik biçim desteklemektedir.

### <a name="use-of-comma-to-indicate-thousand"></a>Bini belirtmek için virgül kullanımı

Sayılarda ayırıcı olarak virgül kullanımını desteklemez. Bin sayısını belirtmek üzere virgülle ayrılmış bölgeler, ayırıcı olarak yalnızca bir noktanın kullanımını görebilir. Örneğin, 15,5K 15,5K olarak görüntülenir.

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-troubleshoot-belowfoldlink)

## <a name="microsoft-defender-for-endpoint-tenant-was-automatically-created-in-europe"></a>Avrupa'da Uç Nokta kiracısı için Microsoft Defender otomatik olarak oluşturuldu

Sunucuları izlemek için Bulut için Microsoft Defender'ı kullanırken, uç nokta kiracısı için Microsoft Defender otomatik olarak oluşturulur. Uç nokta verileri için Microsoft Defender varsayılan olarak Avrupa'da depolanır.

## <a name="related-topics"></a>İlgili konular

- [Uç nokta ekleme sorunları için Microsoft Defender'da sorun giderme](troubleshoot-onboarding.md)
- [Olay Görüntüleyicisi'ni kullanarak olayları ve hataları gözden geçirme](event-error-codes.md)
