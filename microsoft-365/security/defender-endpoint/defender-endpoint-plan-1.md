---
title: Plan 1 Uç Nokta için Microsoft Defender e genel bakış
description: Uç Nokta Planı 1 için Defender'a genel bir bakış elde olun. Bu uç nokta koruma aboneliğine dahil edilen özellikler ve özellikler hakkında bilgi alın.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 01/19/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.custom: intro-overview
ms.openlocfilehash: d7e7f7d7c22da007187db5df8bd773dca798597c
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466311"
---
# <a name="overview-of-microsoft-defender-for-endpoint-plan-1"></a>Plan 1 Uç Nokta için Microsoft Defender e genel bakış

**Geçerli olduğu yer:**

- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Uç Nokta için Microsoft Defender, sizin gibi kuruluşların gelişmiş tehditlerini önlemeye, algılamaya, araştırmaya ve yanıtlamaya yardımcı olmak için tasarlanmış bir kurumsal uç nokta güvenlik platformudur. Uç nokta için Defender'ın artık iki planla kullanılabilir olduğunu duyurmaktan mutluluk mutluyuz: 

- **Bu makalede açıklanan Uç Nokta Planı 1 için Defender**; ve 
- **[Uç Nokta Plan 2 için Defender](microsoft-defender-endpoint.md)** genel olarak kullanılabilir ve önceden Uç Nokta için [Defender olarak bilinir](microsoft-defender-endpoint.md).

Aşağıdaki resimde yer alan yeşil kutular, Uç Nokta Planı 1 için Defender'a nelerin dahil olduğunu belirtir:

:::image type="content" source="../../media/mde-p1/mde-p1-overview-diagram.png" alt-text="Uç Nokta Planı 1 için Defender ile neler olduğu" lightbox="../../media/mde-p1/mde-p1-overview-diagram.png":::

Bu kılavuzu kullanarak:

- [Uç Nokta Planı 1 için Defender'da bulunanlar hakkında genel bakış](#defender-for-endpoint-plan-1-capabilities)
- [Uç Nokta için Defender Plan 1’i Plan 2 ile karşılaştırın](defender-endpoint-plan-1-2.md)
- [Uç Nokta Planı 1 için Defender'ı ayarlamayı ve yapılandırmayı öğrenin](mde-p1-setup-configuration.md)
- [Kullanmaya başlayın ve uyarıları Microsoft 365 Defender, cihazları yönetebilirsiniz ve algılanan tehditlerle ilgili raporları kullanabileceğiniz Web Sitesi portalını kullanabilirsiniz](mde-plan1-getting-started.md)
- [Bakım ve işlemlere genel bir bakış elde](mde-p1-maintenance-operations.md)

> [!TIP]
> [Uç Nokta Planı 1 için Defender ile Plan 2 arasındaki farklar hakkında daha fazla bilgi öğrenin](defender-endpoint-plan-1-2.md).

## <a name="defender-for-endpoint-plan-1-capabilities"></a>Uç Nokta Plan 1 özellikleri için Defender

Uç Nokta Plan 1 için Defender aşağıdaki özellikleri içerir:

- **[Endüstri lideri, güçlü](#next-generation-protection)** kötü amaçlı yazılımlardan koruma ve virüsten koruma içeren yeni nesil koruma
- **[Güvenlik ekibinin tehdit](#manual-response-actions)** algılandığında cihaz veya dosyalar üzerinde işlem gerçekleştirerek karantinaya gönderme gibi el ile yanıt eylemleri
- **[Cihazlarda saldırı yüzeyini azaltma özellikleri](#attack-surface-reduction)** , sıfır gün saldırılarını önleyen ve uç nokta erişimi ve davranışlar üzerinde ayrıntılı denetim sunan saldırılar
- **[Merkezi yapılandırma ve yönetim merkezi](#centralized-management)** portalıyla Microsoft 365 Defender tümleştirmeyle Microsoft Endpoint Manager
- **[Windows](#cross-platform-support)**, macOS, iOS ve Android cihazları dahil çeşitli platformlara yönelik koruma

Aşağıdaki bölümlerde bu özellikler hakkında daha fazla ayrıntı sağlanmıştır. 

## <a name="next-generation-protection"></a>Yeni nesil koruma

Yeni nesil koruma, güçlü virüsten koruma ve kötü amaçlı yazılımlardan koruma içerir. Yeni nesil korumayla şunları elde olur: 

- Davranış tabanlı, heuristic ve gerçek zamanlı virüsten koruma 
- Neredeyse anında algılamayı ve yeni ve ortaya çıkan tehditleri engellemeyi de içeren bulut teslimi koruması 
- Yazılımla ilgili güncelleştirmeler de dahil olmak üzere, özel koruma Microsoft Defender Virüsten Koruma 

Daha fazla bilgi edinmek için bkz [. Yeni nesil korumaya genel bakış](next-generation-protection.md).

## <a name="manual-response-actions"></a>El ile yanıt eylemleri

El ile yanıt eylemleri, güvenlik ekibinin uç noktalarda veya dosyalarda tehdit algılandığında gerçekleştir eylemleridir. Uç Nokta için Defender güvenliği ihlal [edilmiş veya](respond-machine-alerts.md) şüpheli içeriklere sahip olduğu algılanan bir cihazda gerçekleştirebilecek bazı el ile yanıt eylemleri içerir. Tehdit olarak algılanan [dosyalar üzerinde yanıt](respond-file-alerts.md) eylemleri de çalıştırabilirsiniz. Aşağıdaki tabloda, Uç Nokta Planı 1 için Defender'da bulunan el ile yanıt eylemleri özetlenmiştir. <br/><br/>

| Dosya/Cihaz | Eylem | Açıklama |
|:---|:---|:---|
| Cihaz | Virüsten koruma taraması çalıştırma | Virüsten koruma taraması başlatır. Cihazda herhangi bir tehdit algılanırsa, bu tehditlere genellikle virüsten koruma taraması sırasında yöneliktir. |
| Cihaz | Cihazı yalıt | Uç Nokta için Defender bağlantısını koruyarak cihazın kuruluş ağıyla bağlantısını keser. Bu eylem, cihazı izlemenizi ve gerekirse başka bir işlem İzlemenizi sağlar. |
| Dosya | Durdurma ve karantina |İşlemlerin çalıştır alınmasını ve ilişkili dosyaları karantinaya alınmasını durdurur. |
| Dosya | Dosyayı engellemek veya dosyaya izin vermek için gösterge ekleme | Göstergeleri, taşınabilir yürütülebilir dosyaların cihazlarda okunmalarını, yaz dosyalarını veya yürütülebilir dosyalarını engelleme. <p>Göstergelere izin ver, dosyaların engellenmiş veya düzeltilir. |

Daha fazla bilgi edinmek için aşağıdaki makalelere bakın:

- [Cihazlarda yanıt eylemleri gerçekleştirin](respond-machine-alerts.md) 
- [Dosyalarda yanıt eylemleri gerçekleştirin](respond-file-alerts.md)

## <a name="attack-surface-reduction"></a>Saldırı yüzeyini azaltma

Kuruluşlarının saldırı yüzeyleri siber saldırılara karşı açık olduğunuz tüm yerlerdedir. Uç Nokta Planı 1 için Defender ile, saldırı alanlarınızı, kurumda kullandığı cihazları ve uygulamaları koruyarak azaltabilirsiniz. Uç Nokta Planı 1 için Defender'a dahil edilen saldırı yüzeyini azaltma özellikleri aşağıdaki bölümlerde açıklanmıştır.

- [Saldırı yüzeyini azaltma kuralları](#attack-surface-reduction-rules)
- [Fidye yazılımı azaltma](#ransomware-mitigation)
- [Cihaz denetimi](#device-control)
- [Web koruması](#web-protection)
- [Ağ koruması](#web-protection)
- [Ağ güvenlik duvarı](#network-firewall)
- [Uygulama denetimi](#application-control)

Uç nokta için Defender'daki saldırı yüzeyini azaltma özellikleri hakkında daha fazla bilgi edinmek için saldırı yüzeyini [azaltmaya genel bakış'a bakın](overview-attack-surface-reduction.md).

### <a name="attack-surface-reduction-rules"></a>Saldırı yüzeyini azaltma kuralları

Saldırı yüzeyini azaltma kuralları, riskli olarak kabul edilen bazı yazılım davranışlarını hedefler. Bu tür davranışlar şunlardır:

- Yürütülebilir dosyaları ve başka dosyaları indirmeye veya çalıştırmaya çalışan betikleri başlatma
- Obfuscated veya başka türlü şüpheli betikleri çalıştırma
- Uygulamaların çoğunlukla normal çalışma sırasında başlatmayacakları başlatma davranışları

Yasal iş uygulamaları bu tür yazılım davranışları sergiler; öte yandan, bu davranışlar genellikle kötü amaçlı yazılım yoluyla saldırganlar tarafından kötüye kullanım nedeniyle riskli olarak kabul edilir. Saldırı yüzeyini azaltma kuralları riskli davranışları kısıtlar ve organizasyonlu güvende tutmanıza yardımcı olabilir.

Daha fazla bilgi edinmek için bkz [. Kötü amaçlı yazılım bulaşmasını önlemek için saldırı yüzeyi azaltma kurallarını kullanma](attack-surface-reduction.md).

### <a name="ransomware-mitigation"></a>Fidye yazılımı azaltma

Denetimli klasör erişimiyle fidye yazılımı risklerini azaltabilirsiniz. Denetimli klasör erişimi, yalnızca güvenilen uygulamaların uç noktalarınız üzerinde korumalı klasörlere erişmelerine izin verir. Uygulamalar, yaygınlık ve itibarına bağlı olarak güvenilir uygulamalar listesine eklenir. Güvenlik işlemleri ekipleriniz de güvenilen uygulamalar listesinden uygulama ekleyebilir veya bu listeden uygulamaları kaldırabilir.

Daha fazla bilgi edinmek için [bkz. Denetimli klasör erişimiyle önemli klasörleri koruma](controlled-folders.md).

### <a name="device-control"></a>Cihaz denetimi

Bazen, kuruluş cihazlarına yönelik tehditler USB sürücüleri gibi çıkarılabilir sürücülerde dosya şeklinde gelebilir. Uç nokta için Defender, yetkisiz çevre birimlerinin cihazlarınızı tehlikeye atması engellemeye yardımcı olacak özellikler içerir. Çıkarılabilir cihazlardaki çıkarılabilir cihaz ve dosyaları engellemek veya buna izin vermek üzere Uç Nokta için Defender'ı yapılandırabilirsiniz. 

Daha fazla bilgi için bkz. [USB cihazlarını ve çıkarılabilir medyayı denetleme](control-usb-devices-using-intune.md).

### <a name="web-protection"></a>Web koruması

Web korumasıyla, kuruluş cihazlarınızı web tehditlerine ve istenmeyen içeriğe karşı koruyabilirsiniz. Web koruması, web tehdit koruması ve web içeriği filtrelemesi içerir.

- [Web tehdit koruması](web-threat-protection.md) kimlik avı sitelerine, kötü amaçlı yazılım vektörlerine, açıklarından yararlanma sitelerine, güvenilmeyen veya itibarsız sitelere ve açıkça engellemiş olduğunuz sitelere erişimi engeller.
- [Web içeriği filtreleme,](web-content-filtering.md) kategorilerine göre belirli sitelere erişimi engelleme. Kategoriler yetişkinlere yönelik içerik, boş zaman siteleri, yasal sorumluluk siteleri ve daha fazlasını içerebilir.

Daha fazla bilgi edinmek için [bkz. web koruması](web-protection-overview.md).

### <a name="network-protection"></a>Ağ koruması

Ağ korumasıyla, kuruluşlarının kimlik avı dolandırıcılığı, açıkları açıkları ve diğer zararlı içerikleri barındıran tehlikeli etki alanlarına erişmesini önebilirsiniz. 

Daha fazla bilgi edinmek için bkz [. Ağın koruma](network-protection.md).

### <a name="network-firewall"></a>Ağ güvenlik duvarı

Ağ güvenlik duvarı korumasıyla, hangi ağ trafiğinin kuruluş cihazlarında veya bu cihazlardan akışına izin ver verildiğini belirleyen kurallar kurabilirsiniz. Ağ güvenlik duvarınız ve Uç Nokta için Defender ile sahip olduğunuz gelişmiş güvenlik özellikleriyle şunları kullanabilirsiniz:

- Ağ güvenliği tehditlerini azaltma
- Hassas verileri ve fikri mülkiyeti koruma
- Güvenlik yatırımını genişletme

Daha fazla bilgi edinmek için bkz. [Windows Defender güvenlik duvarına sahip güvenlik duvarı](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security).

### <a name="application-control"></a>Uygulama denetimi

Uygulama denetimi, Windows çekirdek (kernel) içinde yalnızca güvenilir uygulamaları ve kodu çalıştırarak Windows uç noktalarınızı korur. Güvenlik ekipleri, kod atama sertifikaları, itibarı, başlatma süreci gibi bir uygulamanın özniteliklerini göz önünde bulunduran uygulama denetimi kuralları tanımlayabilir. Uygulama denetimi daha sonraki Windows 10 kullanılabilir.

Daha fazla bilgi edinmek için bkz[. Windows](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control).

## <a name="centralized-management"></a>Merkezi yönetim

Uç Nokta Planı 1 için Defender, güvenlik ekibimizin algılanan tehditlerle ilgili güncel bilgileri görüntülemesini, tehditleri azaltmak ve kuruluş tehdit koruması ayarlarını merkezi olarak yönetmesini sağlayan Microsoft 365 Defender portalını içerir.

Daha fazla bilgi edinmek için [portala Microsoft 365 Defender bakın](portal-overview.md).

### <a name="role-based-access-control"></a>Rol tabanlı erişim denetimi

Rol tabanlı erişim denetimi (RBAC) kullanarak, güvenlik yöneticiniz portala uygun erişim için rol ve Microsoft 365 Defender oluşturabilir[https://security.microsoft.com](https://security.microsoft.com). RBAC ile, 2013'e kimlerin eriş, neleri Bulut için Defender neleri göreceği ve neleri göreceği üzerinde ince denetime sahip oluruz. 

Daha fazla bilgi edinmek için [bkz. Rol tabanlı erişim denetimi kullanarak portal erişimini yönetme](rbac.md).

### <a name="reporting"></a>Raporlama

Bu Microsoft 365 Defender portalı ([https://security.microsoft.com](https://security.microsoft.com)), tehditlere karşı algılanan tehditlere ve eylemlere yönelik bilgilere kolay erişim sağlar. 

- Giriş **sayfası** bir bakışta hangi kullanıcıların veya cihazların risk altında olduğunu, kaç tehdit algılandı ve hangi uyarıların/olayların oluşturulmuş olduğunu gösterecek kartlar içerir.
- Olaylar **ve & uyarıları** bölümünde, tetiklenen uyarılar sonucunda oluşturulan tüm olaylar listelenir. Uyarılar ve olaylar, cihazlar genelinde tehdit olarak algılanır.
- İşlem **merkezi** , yapılan düzeltme eylemlerini listeler. Örneğin, bir dosya karantinaya gönderilirse veya BIR URL engellenirse, her eylem Geçmiş sekmesindeki İşlem **merkezinde listelenir.**
- Raporlar **bölümü** , algılanan tehditleri ve bunların durumunu göstermek için raporlar içerir. 

Daha fazla bilgi edinmek için bkz[. Kullanmaya başlayın Plan 1 Uç Nokta için Microsoft Defender planlama](mde-plan1-getting-started.md).

### <a name="apis"></a>API'ler

Uç Nokta API'leri için Defender ile iş akışlarını otomatik hale kullanabilir ve kuruma özel çözümleriyle tümleştirebilirsiniz. 

Daha fazla bilgi edinmek için bkz. [Uç Nokta API'leri için Defender](management-apis.md). 

## <a name="cross-platform-support"></a>Platformlar arası destek

Çoğu kuruluş çeşitli aygıtlar ve işletim sistemleri kullanır. Uç Nokta Planı 1 için Defender şu anda aşağıdaki işletim sistemlerini desteklemektedir:

- Windows 7 (ESU gerekli)
- Windows 8.1
- Windows 10, sürüm 1709 veya sonrası
- macOS: 11.5 (Big Sur), 10.15.7 (Catalina) veya 10.14.6 (Mojave)
- iOS
- Android OS

## <a name="next-steps"></a>Sonraki adımlar

- [Plan 1 Uç Nokta için Microsoft Defender ile Plan 2'nin karşılaştırması](defender-endpoint-plan-1-2.md)
- [Uç Nokta için Defender Planı 1’i ayarlama ve yapılandırın](mde-p1-setup-configuration.md)
- [Kullanmaya başlayın Plan 1 için Defender ile Birlikte Uygulama](mde-plan1-getting-started.md)
- [Uç Nokta Plan 1 için Defender'ı Yönetme](mde-p1-maintenance-operations.md)
