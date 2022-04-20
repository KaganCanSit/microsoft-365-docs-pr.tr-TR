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
description: kuruluşunuzun SIEM sunucusunu Office 365 Etkinlik Yönetimi API'sindeki Office 365 ve ilgili tehdit olayları için Microsoft Defender ile tümleştirin.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e53fe703637ba4b33fd9658b2ec53b2c8c57db0f
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972595"
---
# <a name="siem-integration-with-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender ile SIEM tümleştirmesi

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

Kuruluşunuz bir güvenlik bilgileri ve olay yönetimi (SIEM) sunucusu kullanıyorsa, Office 365 için Microsoft Defender'ı SIEM sunucunuzla tümleştirebilirsiniz. Office 365 [Etkinlik Yönetimi API'sini](/office/office-365-management-api/office-365-management-activity-api-reference) kullanarak bu tümleştirmeyi ayarlayabilirsiniz.

SIEM tümleştirmesi, Office 365 için Microsoft Defender tarafından algılanan kötü amaçlı yazılım veya kimlik avı gibi bilgileri SIEM sunucu raporlarınızda görüntülemenizi sağlar.

- Office 365 için Microsoft Defender ile SIEM tümleştirmesinin bir örneğini görmek için [bkz. Teknik Community blogu: Office 365 için Defender ve O365 Yönetim API'siyle SOC'nizin Verimliliğini Artırma](https://techcommunity.microsoft.com/t5/microsoft-security-and/improve-the-effectiveness-of-your-soc-with-office-365-atp-and/ba-p/1525185).
- Office 365 Yönetim API'leri hakkında daha fazla bilgi edinmek için bkz. [Office 365 Yönetim API'lerine genel bakış](/office/office-365-management-api/office-365-management-apis-overview).

## <a name="how-siem-integration-works"></a>SIEM tümleştirmesi nasıl çalışır?

Office 365 Etkinlik Yönetimi API'si, kuruluşunuzun Microsoft 365 ve Azure Active Directory etkinlik günlüklerinden kullanıcı, yönetici, sistem ve ilke eylemleri ve olayları hakkındaki bilgileri alır. Kuruluşunuzda Office 365 Plan 1 veya 2 için Microsoft Defender veya Office 365 E5 varsa, [Office 365 için Microsoft Defender şemasını](/office/office-365-management-api/office-365-management-activity-api-schema#office-365-advanced-threat-protection-and-threat-investigation-and-response-schema) kullanabilirsiniz.

Kısa süre önce, [Office 365 Plan 2 için Microsoft Defender'daki](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) otomatik araştırma ve yanıt özelliklerinden gelen olaylar Office 365 Yönetim Etkinliği API'sine eklendi. API, kimlik, ad ve durum gibi temel araştırma ayrıntılarıyla ilgili verileri eklemenin yanı sıra araştırma eylemleri ve varlıkları hakkında üst düzey bilgiler de içerir.

SIEM sunucusu veya diğer benzer sistem algılama olaylarına erişmek için **audit.general** iş yükünü yoklar. Daha fazla bilgi için bkz. [Office 365 Yönetim API'leriyle Kullanmaya başlayın](/office/office-365-management-api/get-started-with-office-365-management-apis).

## <a name="enum-auditlogrecordtype---type-edmint32"></a>Enum: AuditLogRecordType - Tür: Edm.Int32

### <a name="auditlogrecordtype"></a>AuditLogRecordType

Aşağıdaki tabloda, Office 365 olayları için Microsoft Defender ile ilgili **AuditLogRecordType** değerleri özetlenir:<br/><br/>

| Değer | Üye adı | Açıklama |
|---|---|---|
| 28| ThreatIntelligence | Exchange Online Protection ve Office 365 için Microsoft Defender'dan kimlik avı ve kötü amaçlı yazılım olayları. |
| 41| ThreatIntelligenceUrl | Kasa Office 365 için Microsoft Defender'dan engelleme ve engelleme geçersiz kılma olaylarını bağlar. |
| 47| ThreatIntelligenceAtpContent | Office 365 için Microsoft Defender'dan SharePoint Online, OneDrive İş ve Microsoft Teams dosyaları için kimlik avı ve kötü amaçlı yazılım olayları. |
| 64| AirInvestigation | Office 365 Plan 2 için Microsoft Defender'dan araştırma ayrıntıları ve ilgili yapıtlar gibi otomatik araştırma ve yanıt olayları. |

> [!IMPORTANT]
> Office 365 için Microsoft Defender ile SIEM tümleştirmesini ayarlamak için Microsoft 365 Defender portalında genel yönetici veya Güvenlik Yöneticisi rolü atanmış olmalıdır. Daha fazla bilgi için bkz. [Microsoft 365 Defender portalında İzinler](permissions-microsoft-365-security-center.md).
>
> Microsoft 365 ortamınız için denetim günlüğü açık olmalıdır. Bu konuda yardım almak için bkz. [Denetim günlüğü aramasını açma veya kapatma](../../compliance/turn-audit-log-search-on-or-off.md).

## <a name="see-also"></a>Ayrıca bkz.

[Office 365 tehdit araştırması ve yanıtı](office-365-ti.md)

[Office 365'de otomatik araştırma ve yanıt (AIR)](automated-investigation-response-office.md)