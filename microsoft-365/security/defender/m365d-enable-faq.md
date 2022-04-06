---
title: Microsoft 365 Defender açarken sık sorulan sorular
description: Lisanslama, izinler, ilk ayarlar ve Microsoft 365 Defender etkinleştirmeyle ilgili diğer ürün ve hizmetler hakkında en sık sorulan soruların yanıtlarını alın
keywords: sık sorulan sorular, SSS, GCC, kullanmaya başlama, Microsoft 365 Defender etkinleştirme, Microsoft 365 Defender, M365, güvenlik, veri konumu, gerekli izinler, lisans uygunluğu, ayarlar sayfası
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
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 73dddcfc1389eb5bb0b0115f0666c413dc7d2a01
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663214"
---
# <a name="frequently-asked-questions-when-turning-on-microsoft-365-defender"></a>Microsoft 365 Defender açarken sık sorulan sorular

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- Microsoft 365 Defender

Gerekli lisanslar ve izinler, destek hizmetlerini dağıtma ve ilk ayarlar dahil olmak üzere [Microsoft 365 Defender](microsoft-365-defender.md) açma hakkında en sık sorulan soruların yanıtlarını okuyun.

Hizmeti açma yönergeleri için [bkz. Microsoft 365 Defender açma](m365d-enable.md).

## <a name="i-dont-have-a-microsoft-365-e5-license-can-i-still-use-microsoft-365-defender"></a>Microsoft 365 E5 lisansım yok. hala Microsoft 365 Defender kullanabilir miyim?

Aşağıdaki E5 dışı lisanslara sahip müşteriler Microsoft 365 Defender kullanabilir:

- Uç Nokta için Microsoft Defender
- Kimlik için Microsoft Defender
- Bulut Uygulamaları için Microsoft Defender
- Office 365 için Defender (Plan 2)

Desteklenen lisansların tam listesi için [lisans gereksinimlerini okuyun](prerequisites.md#licensing-requirements).

## <a name="do-i-need-to-install-or-deploy-anything-to-start-using-microsoft-365-defender"></a>Microsoft 365 Defender kullanmaya başlamak için herhangi bir şey yüklemem veya dağıtmam gerekiyor mu?

Hayır, Microsoft 365 Defender önceden dağıttığınız Microsoft 365 güvenlik hizmetlerindeki verileri birleştirir. Etkinleştirdiğinizde olay, otomasyon ve tehdit avcılığı deneyimleri dağıtılan ürünler kapsamında çalışmaya başlar. Bu ürünlerden hiçbiri düzgün dağıtılmazsa, Microsoft 365 Defender hiçbir veri görüntülemez ve herhangi bir işlem yapamaz.

Microsoft 365 Defender deneyimlerinizi iyileştirmek için desteklenen *tüm* [Microsoft 365 güvenlik ürünlerini ve hizmetlerini](deploy-supported-services.md) dağıtmanızı öneririz.

## <a name="where-does-microsoft-365-defender-process-and-store-my-data"></a>Microsoft 365 Defender verilerimi nerede işler ve depolar?

Microsoft 365 Defender, birleştirilmiş verilerin işlendiği ve depolandığı veri merkezi için otomatik olarak en uygun konumu seçer. Uç Nokta için Microsoft Defender varsa, Uç Nokta için Defender tarafından kullanılan konumu seçer.

>[!NOTE]
>Uç Nokta için Microsoft Defender Bulut için Microsoft Defender aracılığıyla açıldığında Avrupa Birliği (AB) veri merkezlerinde otomatik olarak sağlamalar. Microsoft 365 Defender, Uç Nokta için Microsoft Defender bu şekilde sağlayan müşteriler için aynı AB veri merkezinde otomatik olarak sağlanır.

Veri merkezi konumu, Microsoft 365 Defender (**Ayarlar > Microsoft 365 Defender**) için ayarlar sayfasında hizmet sağlanmadan önce ve sonra gösterilir. Başka bir veri merkezi konumu kullanmayı tercih ediyorsanız, Microsoft desteğine başvurmak için Microsoft 365 Defender portalında **Yardım mı gerekiyor?** öğesini seçin.

## <a name="where-can-i-access-microsoft-365-defender"></a>Microsoft 365 Defender nereden erişebilirim?

Microsoft 365 Defender şu konumda kullanılabilir: <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank"><https://security.microsoft.com></a>.

## <a name="what-permissions-do-i-need-to-access-microsoft-365-defender"></a>Microsoft 365 Defender erişmek için hangi izinlere ihtiyacım var?

Aşağıdaki Azure Active Directory (Azure AD) rollerine atanan hesaplar Microsoft 365 Defender işlevlere ve verilere erişebilir:

- Genel yönetici
- Güvenlik yöneticisi
- Güvenlik İşleci
- Genel Okuyucu
- Güvenlik Okuyucusu
- Uyumluluk Yöneticisi
- Uyumluluk Verileri Yöneticisi
- Uygulama Yöneticisi
- Bulut Uygulaması Yöneticisi


> [!NOTE]
> Uç Nokta için Microsoft Defender'daki rol tabanlı erişim denetimi ayarları verilere erişimi etkiler. Daha fazla bilgi için [Microsoft 365 Defender erişimi yönetme](m365d-permissions.md) hakkında bilgi edinin.

## <a name="what-time-zone-does-microsoft-365-defender-default-to"></a>varsayılan olarak hangi saat dilimine Microsoft 365 Defender?

Varsayılan olarak, Microsoft 365 Defender utc saat diliminde saat bilgilerini görüntüler. Yerel saat diliminizi kullanmak için bu ayarı değiştirebilirsiniz. [Saat dilimini ayarlama hakkında bilgi edinin](m365d-time-zone.md)

## <a name="how-can-i-learn-about-new-microsoft-365-defender-feature-and-ui-updates"></a>Yeni Microsoft 365 Defender özelliği ve kullanıcı arabirimi güncelleştirmeleri hakkında nasıl bilgi edinebilirim?

Microsoft, aşağıdakiler dahil olmak üzere çeşitli kanallar aracılığıyla düzenli olarak bilgi sağlar:

- Microsoft 365 yönetim merkezi'deki [ileti merkezi](../../admin/manage/message-center.md)
- [Microsoft 365 güvenlik & uyumluluk teknoloji topluluğundaki](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/bg-p/securityprivacycompliance) blog gönderileri

[Önizleme özelliklerini](preview.md) açarak herkese açık en son deneyimleri edinin.

## <a name="related-topics"></a>İlgili konular

- [Microsoft 365 Defender genel bakış](microsoft-365-defender.md)
- [Microsoft 365 Defender açın](m365d-enable.md).
- [Lisanslama gereksinimleri ve diğer önkoşullar](prerequisites.md)
- [Desteklenen hizmetleri dağıtın](deploy-supported-services.md)
- [Önizleme özelliklerini açma](preview.md)
