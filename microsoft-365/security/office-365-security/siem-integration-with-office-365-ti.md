---
title: Office 365 için Microsoft Defender ile SIEM tümleştirmesi
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: ''
search.appverid:
- MET150
- MOE150
ms.assetid: eb56b69b-3170-4086-82cf-ba40a530fa1b
ms.date: 08/21/2020
ms.collection:
- M365-security-compliance
description: Etkinlik Yönetimi API'sinde işlerinizi ve ilgili tehdit olaylarını Office 365 için Office 365 SIEM sunucusunu Microsoft Defender ile tümleştirin.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3dbb175ba169c9bb8f4d7240d59d9886391167c3
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984431"
---
# <a name="siem-integration-with-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender ile SIEM tümleştirmesi

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Kuruluş bir güvenlik bilgileri ve olay yönetimi (SIEM) sunucusu kullanıyorsa, Office 365 için Microsoft Defender'ı SIEM sunucunuzla tümleştirebilirsiniz. Bu tümleştirmeyi en son Etkinlik Yönetimi [API'sini Office 365 kurabilirsiniz](/office/office-365-management-api/office-365-management-activity-api-reference).

SIEM tümleştirmesi, SIEM sunucu raporlarınıza kötü amaçlı yazılım veya Microsoft Defender tarafından Office 365 kimlik avı gibi bilgileri görüntülemenize olanak sağlar.

- Office 365 için Microsoft Defender ile SIEM tümleştirmesi örneği için bkz[. Teknik Community blogu: Office 365 için Defender ile SOC'nizin etkinliğini geliştirme ve O365 Yönetim API'si](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185).
- Yeni Yönetim API'leri hakkında daha Office 365 için bkz. [Yönetim API'Office 365 genel bakış](/office/office-365-management-api/office-365-management-apis-overview).

## <a name="how-siem-integration-works"></a>SIEM tümleştirmesi nasıl çalışır?

Office 365 Yönetimi API'si, kullanıcı, yönetici, sistem ve ilke eylemleri ile etkinlikleriyle ilgili bilgileri, Microsoft 365 günlükleri Azure Active Directory sağlar. 1 veya 2 için Microsoft Defender Office 365 veya Office 365 E5 varsa, bu şema için [Microsoft Defender'ı Office 365 kullanabilirsiniz](/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema).

Yakın zamanda, Plan [2 için Microsoft Defender'daki otomatik soruşturma ve yanıt Office 365](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) etkinlikler Office 365 API'nize eklenmiştir. API, kimlik, ad ve durum gibi temel soruşturma ayrıntılarıyla ilgili verileri eklemeye ek olarak, soruşturma eylemleri ve varlıkları hakkında üst düzey bilgiler de içerir.

SIEM sunucusu veya diğer benzer sistem, algılama olaylarına **erişmek için audit.general** iş yükünü yoklar. Daha fazla bilgi edinmek için bkz[. Yönetim API'lerini Office 365 başlama](/office/office-365-management-api/get-started-with-office-365-management-apis).

## <a name="enum-auditlogrecordtype---type-edmint32"></a>Enum: AuditLogRecordType - Tür: Edm.Int32

### <a name="auditlogrecordtype"></a>AuditLogRecordType

Aşağıdaki tabloda, bu olaylar için Microsoft Defender **ile ilgili AuditLogRecordType** değerleri Office 365 özetlenmiştir:<br/><br/>

| Değer | Üye adı | Açıklama |
|---|---|---|
| 28| ThreatIntelligence | Exchange Online Protection için Microsoft Defender'dan kimlik avı ve kötü amaçlı yazılım Office 365. |
| 41| ThreatIntelligenceUrl | Kasa bağlantılar engelleme süresi ve bu olayları engellemek için Microsoft Defender'dan Office 365. |
| 47| ThreatIntelligenceAtpContent | Office 365 için Microsoft Defender'dan SharePoint Online, OneDrive İş ve Microsoft Teams'daki dosyalar için kimlik avı ve kötü amaçlı yazılım Office 365. |
| 64| AirInvestigation | Plan 2 için Microsoft Defender'dan, soruşturma ayrıntıları ve ilgili yapılar gibi otomatik Office 365 olayları. |

> [!IMPORTANT]
> İş için Microsoft Defender ile SIEM tümleştirmesini ayarlamak üzere Microsoft 365 Defender portalında genel yönetici veya Güvenlik Yöneticisi rolünün Office 365. Daha fazla bilgi için bkz[. Microsoft 365 Defender portalına.](permissions-microsoft-365-security-center.md)
>
> Denetim günlüğünün kayıt ortamınız için Microsoft 365 gerekir. Bu konuda yardım almak için bkz [. Denetim günlüğü aramalarını açma veya kapatma](../../compliance/turn-audit-log-search-on-or-off.md).

## <a name="see-also"></a>Ayrıca bkz.

[Office 365 soruşturma ve yanıt](office-365-ti.md)

[Web'de otomatik araştırma ve yanıt (AIR) Office 365](automated-investigation-response-office.md)