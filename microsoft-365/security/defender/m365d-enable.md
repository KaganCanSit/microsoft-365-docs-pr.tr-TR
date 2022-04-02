---
title: Microsoft 365 Defender’ı açın
description: Güvenliği etkinleştirmeyi ve Microsoft 365 Defender olayla yanıtını tümleştirmeye başlamayı öğrenin.
keywords: çalışmaya başlama, Microsoft 365 Defender, Microsoft 365 Defender, M365, güvenlik, veri konumu, gerekli izinler, lisansa uygunluk, ayarlar sayfası
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 2a99dbaf50b582df4203fc9c8e1d04e0a3f6d807
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64498666"
---
# <a name="turn-on-microsoft-365-defender"></a>Microsoft 365 Defender’ı açın

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

[Microsoft 365 Defender](microsoft-365-defender.md) özelliklerini şirket içinde veya şirket genelinde tümleştirerek Uç Nokta için Microsoft Defender yanıt Office 365 için Microsoft Defender. Microsoft Defender for Cloud Apps ve Kimlik için Microsoft Defender. Bu birleşik deneyim, portalda erişebilirsiniz güçlü Microsoft 365 Defender ekler.

Microsoft 365 Defender izinleri olan uygun müşteriler portalını ziyaret edinse otomatik olarak Microsoft 365 Defender. Çeşitli önkoşulları ve bu önkoşulların nasıl Microsoft 365 Defender için bu makaleyi okuyun.

## <a name="check-license-eligibility-and-required-permissions"></a>Lisans uygunluğunu ve gerekli izinleri denetleme

Bir güvenlik ürününün Microsoft 365, genel olarak bu ürünü ek lisans Microsoft 365 Defender olmadan kullanma hakkı size sağlar. Desteklenen tüm hizmetlere erişim sağlayan Microsoft 365 E5, E5 Güvenlik, A5 veya A5 Güvenlik lisansı ya da geçerli bir lisans birleşimi almalarını öneririz.

Ayrıntılı lisans bilgileri için [lisans gereksinimlerini okuyun](prerequisites.md#licensing-requirements).

### <a name="check-your-role"></a>Rollerinizi kontrol edin

Bir sonraki rolü açmak için aşağıdaki rollerden biri Microsoft 365 Defender:

- Genel Yönetici
- Güvenlik Yöneticisi
- Güvenlik İşleci
- Genel Okuyucu
- Güvenlik Okuyucu
- Uyumluluk Yöneticisi
- Uyumluluk Veri Yöneticisi
- Uygulama Yöneticisi
- Bulut Uygulama Yöneticisi

[Rollerinizi Azure AD'de görüntüleme](/azure/active-directory/users-groups-roles/directory-manage-roles-portal)

## <a name="supported-services"></a>Desteklenen hizmetler

Microsoft 365 Defender, zaten dağıtmış olduğunuz desteklenen çeşitli hizmetlerden verileri bir araya toplar. Yeni içgörüleri tanımlamak ve merkezi yanıt iş akışlarını mümkün hale etmek için verileri merkezi olarak işler ve depolar. Bunu, tümleşik hizmetlerle ilişkilendirilmiş dağıtımları, ayarları veya verileri etkilemeden yapar.

En iyi korumayı elde etmek ve Microsoft 365 Defender için, ağ üzerinde tüm geçerli desteklenen hizmetleri dağıtmanızı öneririz. Daha fazla bilgi [için, desteklenen hizmetlerin dağıtımı hakkında bilgi okuyun](deploy-supported-services.md).

## <a name="onboard-to-the-service"></a>Hizmete ekleme
Kullanıcı Microsoft 365 Defender basit bir işlemdir. Gezinti menüsünden, ekleme işlemini başlatmak için Olay &**,** Atla **, İşlem** merkezi veya Tehdit analizi gibi herhangi bir öğeyi seçin. 

### <a name="data-center-location"></a>Veri merkezi konumu

Microsoft 365 Defender verileri, kullanıcı tarafından kullanılan [konumda depolar ve Uç Nokta için Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy). Veri merkezi konumunuz Uç Nokta için Microsoft Defender, güvenlik hizmetlerinin etkin olduğu konuma bağlı olarak yeni bir Microsoft 365 seçilir. Seçili veri merkezi konumu ekranda gösterilir.

Farklı **bir veri merkezi** Microsoft 365 Defender sağlama konusunda Microsoft desteğine Microsoft 365 Defender için Yardım mı gerekiyor? öğesini seçin.

> [!NOTE]
> Geçmişte, Uç Nokta için Microsoft Defender aracılığıyla açık olduğunda Avrupa Birliği (AB) veri merkezlerinde otomatik olarak Bulut için Microsoft Defender. Microsoft 365 Defender geçmişte bu şekilde Uç Nokta için Defender hazır bulunduran müşteriler için otomatik olarak aynı AB veri merkezinde sağacaktır.

### <a name="confirm-that-the-service-is-on"></a>Hizmetin şu şekilde olduğunu onaylayın

Hizmet sağlandıktan sonra, şunları ekler:

- [Olay yönetimi](incidents-overview.md)
- [Uyarılar sırası](investigate-alerts.md)
- Otomatik araştırma ve yanıtı [yönetmek için işlem merkezi](m365d-autoir.md)
- [Gelişmiş av](advanced-hunting-overview.md) özellikleri
- Tehdit analizi

:::image type="content" source="../../media/overview-incident.png" alt-text="Microsoft 365 Defender portalında Microsoft 365 Defender bölmesi" lightbox="../../media/overview-incident.png":::
*Microsoft 365 Defender yönetimi ve diğer özellikleri olan en iyi portal*

### <a name="getting-microsoft-defender-for-identity-data"></a>Veri Kimlik için Microsoft Defender alma 
Microsoft Defender for Cloud Apps ile tümleştirmeyi etkinleştirmek için, kullanıcıda en az Microsoft Defender for Cloud Apps oturum aç gerekir.

## <a name="get-assistance"></a>Yardım al

SSS bölümünü açma konusunda en sık sorulan soruların yanıtlarını Microsoft 365 Defender [SSS bölümünü okuyun](m365d-enable-faq.md).

Microsoft destek personeli, kiracınız üzerinde hizmetin ve ilgili kaynakların sağlanmasına veya yeniden kararlaştırmasına yardımcı olabilir. Yardım için portalda **Yardım mı gerekiyor?** Microsoft 365 Defender seçin. De destek ile iletişime geçerek iletişim Microsoft 365 Defender.

## <a name="related-topics"></a>İlgili konular

- [Sık sorulan sorular](m365d-enable-faq.md)
- [Lisans gereksinimleri ve diğer önkoşullar](prerequisites.md)
- [Desteklenen hizmetleri dağıtın](deploy-supported-services.md)
- [Microsoft 365 Defender genel bakış](microsoft-365-defender.md)
- [Uç Nokta için Microsoft Defender genel bakış](../defender-endpoint/microsoft-defender-endpoint.md)
- [Office 365 için Defender genel bakış](../office-365-security/defender-for-office-365.md)
- [Microsoft Defender for Cloud Apps genel bakış](/cloud-app-security/what-is-cloud-app-security)
- [Kimlik için Microsoft Defender genel bakış](/azure-advanced-threat-protection/what-is-atp)
- [Uç Nokta için Microsoft Defender depolamayı](../defender-endpoint/data-storage-privacy.md)
