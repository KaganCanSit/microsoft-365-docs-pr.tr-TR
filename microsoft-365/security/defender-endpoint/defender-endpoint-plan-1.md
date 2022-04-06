---
title: Uç Nokta için Microsoft Defender Plan 1'e genel bakış
description: Uç Nokta Için Defender Plan 1'e genel bir bakış edinin. Bu uç nokta koruma aboneliğine dahil edilen özellikler ve özellikler hakkında bilgi edinin.
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
ms.openlocfilehash: 774d54aee080fbe3d6f5576fb29c85d887717b70
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663522"
---
# <a name="overview-of-microsoft-defender-for-endpoint-plan-1"></a>Uç Nokta için Microsoft Defender Plan 1'e genel bakış

**Uygulandığı öğe**

- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Uç Nokta için Microsoft Defender, sizinki gibi kuruluşların gelişmiş tehditleri önlemesine, algılamasına, araştırmasına ve yanıtlamasına yardımcı olmak için tasarlanmış bir kurumsal uç nokta güvenlik platformudur. Uç Nokta için Defender'ın iki planda kullanıma sunulduğunu duyurmaktan mutluluk duyuyoruz: 

- Bu makalede açıklanan **Uç Nokta Için Defender Plan 1**; Ve 
- Genel kullanıma sunulan ve daha önce **[Uç Nokta için Defender](microsoft-defender-endpoint.md)** olarak bilinen [Uç Nokta için Defender](microsoft-defender-endpoint.md) Plan 2.

Aşağıdaki görüntüdeki yeşil kutular, Uç Nokta için Defender Plan 1'e nelerin dahil olduğunu gösterir:

:::image type="content" source="../../media/mde-p1/mde-p1-overview-diagram.png" alt-text="Uç Nokta için Defender Plan 1 ile ilgili olanlar" lightbox="../../media/mde-p1/mde-p1-overview-diagram.png":::

Aşağıdakiler için bu kılavuzu kullanın:

- [Uç Nokta Için Defender Plan 1'e neler dahil olduğu hakkında genel bakış edinin](#defender-for-endpoint-plan-1-capabilities)
- [Uç Nokta için Defender Plan 1’i Plan 2 ile karşılaştırın](defender-endpoint-plan-1-2.md)
- [Uç Nokta Planı 1 için Defender'ı ayarlamayı ve yapılandırmayı öğrenin](mde-p1-setup-configuration.md)
- [olayları ve uyarıları görüntüleyebileceğiniz, cihazları yönetebileceğiniz ve algılanan tehditlerle ilgili raporları kullanabileceğiniz Microsoft 365 Defender portalını kullanarak Kullanmaya başlayın](mde-plan1-getting-started.md)
- [Bakım ve işlemlere genel bakış elde edin](mde-p1-maintenance-operations.md)

> [!TIP]
> [Uç Nokta için Defender Plan 1 ile Plan 2 arasındaki farklar hakkında daha fazla bilgi edinin](defender-endpoint-plan-1-2.md).

## <a name="defender-for-endpoint-plan-1-capabilities"></a>Uç Nokta Için Defender Plan 1 özellikleri

Uç Nokta Planı 1 için Defender aşağıdaki özellikleri içerir:

- Sektör lideri, sağlam kötü amaçlı yazılımdan koruma ve virüsten koruma içeren **[yeni nesil](#next-generation-protection)** koruma
- Tehditler algılandığında güvenlik ekibinizin cihazlarda veya dosyalarda gerçekleştirebileceği karantinaya dosya gönderme gibi **[el ile yanıt eylemleri](#manual-response-actions)**
- Cihazları güçlendiren, sıfır gün saldırılarını önleyen ve uç nokta erişimi ve davranışları üzerinde ayrıntılı denetim sunan **[saldırı yüzeyi azaltma özellikleri](#attack-surface-reduction)**
- Microsoft 365 Defender portalı ile **[merkezi yapılandırma ve yönetim](#centralized-management)** ve Microsoft Endpoint Manager ile tümleştirme
- Windows, macOS, iOS ve Android cihazları dahil olmak üzere **[çeşitli platformlar için koruma](#cross-platform-support)**

Aşağıdaki bölümlerde bu özellikler hakkında daha fazla ayrıntı sağlanır. 

## <a name="next-generation-protection"></a>Yeni nesil koruma

Yeni nesil koruma, sağlam virüsten koruma ve kötü amaçlı yazılımdan koruma içerir. Yeni nesil koruma ile şunları elde edersiniz: 

- Davranış tabanlı, buluşsal ve gerçek zamanlı virüsten koruma 
- Yeni ve yeni tehditleri neredeyse anında algılamayı ve engellemeyi içeren bulut tabanlı koruma 
- Microsoft Defender Virüsten Koruma ile ilgili güncelleştirmeler de dahil olmak üzere ayrılmış koruma ve ürün güncelleştirmeleri 

Daha fazla bilgi için bkz. [Yeni nesil korumaya genel bakış](next-generation-protection.md).

## <a name="manual-response-actions"></a>El ile yanıt eylemleri

El ile yanıt eylemleri, güvenlik ekibinizin uç noktalarda veya dosyalarda tehdit algılandığında gerçekleştirebileceği eylemlerdir. Uç Nokta için Defender, gizliliği tehlikeye girmiş veya şüpheli içerik olduğu algılanan [bir cihazda gerçekleştirilebilecek bazı el ile yanıt eylemlerini](respond-machine-alerts.md) içerir. Tehdit olarak algılanan [dosyalarda yanıt eylemlerini](respond-file-alerts.md) de çalıştırabilirsiniz. Aşağıdaki tabloda, Uç Nokta için Defender Plan 1'de kullanılabilen el ile yanıt eylemleri özetlenir. <br/><br/>

| Dosya/Cihaz | Eylem | Açıklama |
|:---|:---|:---|
| Cihaz | Antivirüs taraması başlat | Virüsten koruma taraması başlatır. Cihazda herhangi bir tehdit algılanırsa, bu tehditler genellikle virüsten koruma taraması sırasında ele alınmaktadır. |
| Cihaz | Cihazı yalıtma | Uç Nokta için Defender bağlantısını korurken bir cihazın kuruluşunuzun ağıyla bağlantısını keser. Bu eylem, cihazı izlemenize ve gerekirse başka işlem yapmanıza olanak tanır. |
| Dosya | Durdurma ve karantinaya al |İşlemlerin çalışmasını durdurur ve ilişkili dosyaları karantinaya alır. |
| Dosya | Bir dosyayı engellemek veya dosyaya izin vermek için gösterge ekleme | Blok göstergeleri taşınabilir yürütülebilir dosyaların cihazlarda okunmasını, yazılmasını veya yürütülmesini engeller. <p>İzin verme göstergeleri, dosyaların engellenmesini veya düzeltilmesini engeller. |

Daha fazla bilgi edinmek için aşağıdaki makalelere bakın:

- [Cihazlarda yanıt eylemleri gerçekleştirme](respond-machine-alerts.md) 
- [Dosyalarda yanıt eylemleri gerçekleştirme](respond-file-alerts.md)

## <a name="attack-surface-reduction"></a>Saldırı yüzeyini azaltma

Kuruluşunuzun saldırı yüzeyleri, siber saldırılara karşı savunmasız olduğunuz yerlerdir. Uç Nokta için Defender Plan 1 ile kuruluşunuzun kullandığı cihazları ve uygulamaları koruyarak saldırı yüzeylerinizi azaltabilirsiniz. Uç Nokta Planı 1 için Defender'a dahil edilen saldırı yüzeyi azaltma özellikleri aşağıdaki bölümlerde açıklanmıştır.

- [Saldırı yüzeyini azaltma kuralları](#attack-surface-reduction-rules)
- [Fidye yazılımı azaltma](#ransomware-mitigation)
- [Cihaz denetimi](#device-control)
- [Web koruması](#web-protection)
- [Ağ koruması](#web-protection)
- [Ağ güvenlik duvarı](#network-firewall)
- [Uygulama denetimi](#application-control)

Uç Nokta için Defender'daki saldırı yüzeyi azaltma özellikleri hakkında daha fazla bilgi edinmek için bkz. [Saldırı yüzeyi azaltmaya genel bakış](overview-attack-surface-reduction.md).

### <a name="attack-surface-reduction-rules"></a>Saldırı yüzeyini azaltma kuralları

Saldırı yüzeyi azaltma kuralları, riskli olarak kabul edilen belirli yazılım davranışlarını hedefler. Bu tür davranışlar şunlardır:

- Diğer dosyaları indirmeye veya çalıştırmaya çalışan yürütülebilir dosyaları ve betikleri başlatma
- Karartılmış veya başka bir şekilde şüpheli betikleri çalıştırma
- Normal çalışma sırasında uygulamaların genellikle başlatmayabilecekleri davranışları başlatma

Meşru iş uygulamaları bu tür yazılım davranışları sergileyebilir; ancak bu davranışlar genellikle kötü amaçlı yazılım aracılığıyla saldırganlar tarafından yaygın olarak kötüye kullanıldıklarından riskli olarak kabul edilir. Saldırı yüzeyi azaltma kuralları riskli davranışları kısıtlayabilir ve kuruluşunuzun güvende kalmasına yardımcı olabilir.

Daha fazla bilgi edinmek için bkz. [Kötü amaçlı yazılım bulaşmasını önlemek için saldırı yüzeyi azaltma kurallarını kullanma](attack-surface-reduction.md).

### <a name="ransomware-mitigation"></a>Fidye yazılımı azaltma

Denetimli klasör erişimiyle fidye yazılımı risk azaltması elde edersiniz. Denetimli klasör erişimi, yalnızca güvenilen uygulamaların uç noktalarınızdaki korumalı klasörlere erişmesine izin verir. Uygulamalar, yaygınlıklarına ve saygınlığına göre güvenilen uygulamalar listesine eklenir. Güvenlik operasyonları ekibiniz de güvenilen uygulamalar listesine uygulama ekleyebilir veya bu listeden uygulama kaldırabilir.

Daha fazla bilgi edinmek için bkz [. Önemli klasörleri denetimli klasör erişimiyle koruma](controlled-folders.md).

### <a name="device-control"></a>Cihaz denetimi

Bazen kuruluşunuzun cihazlarına yönelik tehditler, USB sürücüler gibi çıkarılabilir sürücülerde dosya biçiminde gelir. Uç Nokta için Defender, yetkisiz çevre birimlerinden gelen tehditlerin cihazlarınızı tehlikeye atmasını önlemeye yardımcı olan özellikler içerir. Uç Nokta için Defender'ı çıkarılabilir cihazlardaki çıkarılabilir cihazları ve dosyaları engelleyecek veya izin verecek şekilde yapılandırabilirsiniz. 

Daha fazla bilgi için bkz. [USB cihazlarını ve çıkarılabilir medyayı denetleme](control-usb-devices-using-intune.md).

### <a name="web-protection"></a>Web koruması

Web koruması ile kuruluşunuzun cihazlarını web tehditlerine ve istenmeyen içeriğe karşı koruyabilirsiniz. Web koruması, web tehdit koruması ve web içeriği filtrelemeyi içerir.

- [Web tehdit koruması](web-threat-protection.md) kimlik avı sitelerine, kötü amaçlı yazılım vektörlerine, güvenlik açığından yararlanma sitelerine, güvenilmeyen veya saygınlığı düşük sitelere ve açıkça engellediğiniz sitelere erişimi engeller.
- [Web içeriği filtreleme,](web-content-filtering.md) kategorilerine göre belirli sitelere erişimi engeller. Kategoriler yetişkin içeriği, boş zaman siteleri, yasal sorumluluk siteleri ve daha fazlasını içerebilir.

Daha fazla bilgi için bkz. [web koruması](web-protection-overview.md).

### <a name="network-protection"></a>Ağ koruması

Ağ koruması sayesinde, kuruluşunuzun İnternet'te kimlik avı dolandırıcılığı, açıklardan yararlanma ve diğer kötü amaçlı içerikleri barındırabilecek tehlikeli etki alanlarına erişmesini engelleyebilirsiniz. 

Daha fazla bilgi için bkz. [Ağınızı koruma](network-protection.md).

### <a name="network-firewall"></a>Ağ güvenlik duvarı

Ağ güvenlik duvarı koruması ile, hangi ağ trafiğinin kuruluşunuzun cihazlarına veya cihazlarına akışına izin verilebileceğini belirleyen kurallar ayarlayabilirsiniz. Uç Nokta için Defender ile elde ettiğiniz ağ güvenlik duvarı ve gelişmiş güvenlik ile şunları yapabilirsiniz:

- Ağ güvenlik tehditleri riskini azaltma
- Hassas verileri ve fikri mülkiyeti koruma
- Güvenlik yatırımınızı genişletme

Daha fazla bilgi edinmek için bkz[. Gelişmiş güvenlikle Windows Defender Güvenlik Duvarı](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security).

### <a name="application-control"></a>Uygulama denetimi

Uygulama denetimi, sistem çekirdeğinde (çekirdek) yalnızca güvenilen uygulamaları ve kodu çalıştırarak Windows uç noktalarınızı korur. Güvenlik ekibiniz, birlikte tasarlama sertifikaları, saygınlığı, başlatma işlemi ve daha fazlası gibi uygulamanın özniteliklerini dikkate alan uygulama denetim kuralları tanımlayabilir. Uygulama denetimi Windows 10 veya sonraki sürümlerde kullanılabilir.

Daha fazla bilgi için bkz. [Windows için uygulama denetimi](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control).

## <a name="centralized-management"></a>Merkezi yönetim

Uç Nokta Için Defender Plan 1, güvenlik ekibinizin algılanan tehditler hakkındaki güncel bilgileri görüntülemesine, tehditleri azaltmak için uygun eylemleri gerçekleştirmesine ve kuruluşunuzun tehdit koruma ayarlarını merkezi olarak yönetmesine olanak tanıyan Microsoft 365 Defender portalını içerir.

Daha fazla bilgi için bkz. [Microsoft 365 Defender portala genel bakış](portal-overview.md).

### <a name="role-based-access-control"></a>Rol tabanlı erişim denetimi

Güvenlik yöneticiniz rol tabanlı erişim denetimini (RBAC) kullanarak Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com) ) uygun erişimi vermek için roller ve gruplar oluşturabilir. RBAC ile, Bulut için Defender kimlerin erişebileceği ve ne görüp yapabilecekleri üzerinde ayrıntılı denetime sahip olursunuz. 

Daha fazla bilgi edinmek için bkz. [Rol tabanlı erişim denetimini kullanarak portal erişimini yönetme](rbac.md).

### <a name="reporting"></a>Raporlama

Microsoft 365 Defender portalı ([https://security.microsoft.com](https://security.microsoft.com)) algılanan tehditler ve bu tehditleri ele almak için eylemler hakkındaki bilgilere kolay erişim sağlar. 

- **Giriş** sayfası, hangi kullanıcıların veya cihazların risk altında olduğunu, kaç tehdit algılandığını ve hangi uyarıların/olayların oluşturulduğunu bir bakışta gösteren kartlar içerir.
- **Olaylar & uyarıları** bölümünde, tetiklenen uyarılar sonucunda oluşturulan tüm olaylar listelenir. Cihazlar arasında tehdit algılandığında uyarılar ve olaylar oluşturulur.
- **İşlem merkezi**, gerçekleştirilen düzeltme eylemlerini listeler. Örneğin, bir dosya karantinaya gönderilirse veya bir URL engellenirse, her eylem **Geçmiş** sekmesindeki İşlem merkezinde listelenir.
- **Raporlar** bölümünde algılanan tehditleri ve bunların durumunu gösteren raporlar yer alır. 

Daha fazla bilgi edinmek için bkz. [Uç Nokta için Microsoft Defender Plan 1 ile Kullanmaya başlayın](mde-plan1-getting-started.md).

### <a name="apis"></a>Apı 'leri

Uç Nokta için Defender API'leri ile iş akışlarını otomatikleştirebilir ve kuruluşunuzun özel çözümleriyle tümleştirebilirsiniz. 

Daha fazla bilgi için bkz [. Uç Nokta için Defender API'leri](management-apis.md). 

## <a name="cross-platform-support"></a>Platformlar arası destek

Çoğu kuruluş çeşitli cihazlar ve işletim sistemleri kullanır. Şu anda, Uç Nokta Için Defender Plan 1 aşağıdaki işletim sistemlerini destekler:

- Windows 7 (ESU gereklidir)
- Windows 8.1
- Windows 10, sürüm 1709 veya üzeri
- macOS: 11.5 (Big Sur), 10.15.7 (Catalina) veya 10.14.6 (Mojave)
- iOS
- Android işletim sistemi

## <a name="next-steps"></a>Sonraki adımlar

- [Uç Nokta için Microsoft Defender Plan 1 ile Plan 2 karşılaştırması](defender-endpoint-plan-1-2.md)
- [Uç Nokta için Defender Planı 1’i ayarlama ve yapılandırın](mde-p1-setup-configuration.md)
- [Uç Nokta için Defender Plan 1 ile Kullanmaya başlayın](mde-plan1-getting-started.md)
- [Uç Nokta Için Defender Plan 1'i yönetme](mde-p1-maintenance-operations.md)
