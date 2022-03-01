---
title: İş için Microsoft Defender planlarını diğer Microsoft 365 karşılaştırma
description: İş için Defender ile Uç Nokta için Defender arasındaki farkları anlıyoruz. Her plana nelerin dahil olduğunu bilmek, organizasyonunız için bilinçli bir karar ataymanıza yardımcı olabilir.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: reference
ms.date: 02/26/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-initiative-defender-business
- m365-security-compliance
ms.openlocfilehash: 3d8270b2c8424668200e4242cb65e491a2cc6991
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027501"
---
# <a name="compare-microsoft-defender-for-business-preview-to-microsoft-365-business-premium"></a>İş için Microsoft Defender (önizleme) ile Microsoft 365 İş Ekstra

> [!IMPORTANT]
> İş için Microsoft Defender şu anda önizlemede ve istekte etmek için buraya kaydolan müşterilere ve IT [İş Ortaklarına aşamalı](https://aka.ms/mdb-preview) olarak aşamalı olarak aşamalı olarak sunulmaktadır. Önümüzdeki haftalarda bir ilk müşteri ve iş ortağı kümesi sunuyoruz ve genel kullanılabilirlik durumuna kadar önizlemeyi genişleteceğiz. Önizlemenin bir dizi ilk [senaryoyla başlat olacağını](mdb-tutorials.md#try-these-preview-scenarios) ve düzenli olarak özellikler ekley olacacaz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

Microsoft, küçük ve orta ölçekli işletmeler için çeşitli planlar da dahil olmak üzere çok çeşitli bulut çözümleri ve hizmetleri sunar. Örneğin, [Microsoft 365 İş Ekstra](../../business/microsoft-365-business-overview.md) gibi üretkenlik özelliklerinin yanı sıra güvenlik ve cihaz yönetimi özelliklerini de Office içerir. 

**Bu makaleyi kullanarak**:

- [İş için Microsoft Defender (önizleme) ile Microsoft 365 İş Ekstra](#compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium)
- [Uç nokta kurumsal teklifleri için İş için Defender ile Microsoft Defender'ı karşılaştırma](#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2)


**İş için Microsoft Defender (önizleme) satın Microsoft 365 bir abonelik sahibi olmak zorunda değilsiniz.** İş için Microsoft Defender (önizleme), küçük ve orta ölçekli işletmeler için tek başına bir güvenlik çözümüdür. Zaten başka bir aboneliğiniz (Microsoft 365 İş Temel Standart gibi) varsa, daha fazla tehdit koruması özelliği elde etmek için İş için Microsoft Defender'ı eklemeyi göz önünde bulundurabilirsiniz. 

> [!TIP]
> Organizasyonunuz küçük veya orta ölçekli bir işletme ise (300 veya daha az kullanıcı) ve İş için Microsoft Defender önizleme programına kaydolmak için şu sayfayı ziyaret edin [https://aka.ms/MDB-Preview](https://aka.ms/MDB-Preview): . Daha fazla bilgi edinmek için bkz [. İş için Microsoft Defender'ı satın almak](get-defender-business.md).

## <a name="compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium"></a>İş için Microsoft Defender'daki güvenlik özelliklerini Microsoft 365 İş Ekstra

> [!NOTE]
> Bu makale, İş için Microsoft Defender (önizleme) ve Diğer Özellikler'de bulunan tehdit koruma özelliklerine üst düzey bir genel Microsoft 365 İş Ekstra. Bu makale, hizmet açıklaması veya lisanslama belgesi olarak amaçlanmaz. Daha fazla bilgi için güvenlik [Microsoft 365 uyumluluğu için lisanslama & bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

Aşağıdaki tabloda, İş için Defender'daki güvenlik özellikleri ve özellikleri ile Defender Microsoft 365 İş Ekstra önizlemedeyken bu özellikleri karşılaştırabilirsiniz. İş için Defender genel kullanıma uygun olduğunda bu yeni Microsoft 365 İş Ekstra. <br/><br/>

| Özellik/Özellik | [İş için Microsoft Defender](mdb-overview.md) (önizleme) | [Microsoft 365 Business Premium](../../business/microsoft-365-business-overview.md) |
|:---|:---|:---|
| E-posta koruması | Evet ([e-posta tarama](../defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus.md) Microsoft Defender Virüsten Koruma) | Evet ([Exchange Online Protection](../office-365-security/exchange-online-protection-overview.md)) |
| Antispam koruması | Evet (cihazlar için) | Evet (iletiler Microsoft 365 e-posta içeriği gibi e-posta içeriği için) |
| Kötü amaçlı yazılımlardan koruma | Evet (cihazlar için) | Evet (iletiler Microsoft 365 e-posta içeriği gibi e-posta içeriği için) |
| [Yeni nesil koruma](../defender-endpoint/microsoft-defender-antivirus-in-windows-10.md) <br/> (virüsten koruma ve kötü amaçlı yazılımlardan koruma) | Evet (Microsoft Defender Virüsten Koruma sonraki bir Windows 10 dahil edilir)  | Evet (Microsoft Defender Virüsten Koruma sonraki bir Windows 10 dahil edilir) |
| [Saldırı yüzeyini azaltma](../defender-endpoint/overview-attack-surface-reduction.md) <br/>(saldırı yüzeyini azaltma kuralları ve diğer koruma)  | Evet (Saldırı yüzeyini azaltma kuralları dahili Windows 10 ve artı olarak merkezi olarak yönetilen özellikler) | Evet (Saldırı yüzeyini azaltma kuralları dahili Windows 10 sonrası) |
| [Uç nokta algılama ve yanıt](../defender-endpoint/overview-endpoint-detection-response.md) | Evet. Şunları içerir: <br/>- Davranış tabanlı algılama <br/>- El ile yanıt eylemleri <br/>- Canlı yanıt   | Hayır |
| [Otomatik araştırma ve yanıt](../defender-endpoint/automated-investigations.md) | Evet | Hayır |
| [Tehdit & güvenlik açığı yönetimi](../defender-endpoint/tvm-dashboard-insights.md) | Evet | Hayır |
| Merkezi yönetim ve raporlama | Evet. Diğer istemci Windows cihazlarınızı Microsoft 365 Defender portalında ()[https://security.microsoft.com](https://security.microsoft.com) yönetebilir veya cihazları Microsoft Endpoint Manager() üzerinden yönetebilirsiniz[https://endpoint.microsoft.com](https://endpoint.microsoft.com). | Evet. Microsoft 365 yönetim merkezi istemci Windows yönetebilirsiniz[https://admin.microsoft.com](https://admin.microsoft.com). Cihazlar Microsoft Endpoint Manager ()[https://endpoint.microsoft.com](https://endpoint.microsoft.com) Microsoft Endpoint Manager. |
| [API'ler](../defender-endpoint/apis-intro.md) <br/>(özel uygulamalarla veya raporlama çözümleriyle tümleştirin)  | Evet | Evet |



## <a name="compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2"></a>İş için Microsoft Defender ile Uç Nokta Planları 1 ve 2 için Microsoft Defender'ı karşılaştırma

İş için Defender (önizleme), küçük ve orta ölçekli işletmelere Uç Nokta için Defender'ın kurumsal sınıf özellikleri getirir. Aşağıdaki tabloda, İş için Defender'daki (önizleme) güvenlik özellikleri ve özellikleri ile Uç Nokta Planları 1 ve 2 için Microsoft Defender karşılaştırıldı. <br/><br/>

| Özellik/Özellik | [İş için Defender](mdb-overview.md) (önizleme) | [Uç Nokta Plan 1 için Defender](../defender-endpoint/defender-endpoint-plan-1.md) | [Uç Nokta Plan 2 için Defender](../defender-endpoint/microsoft-defender-endpoint.md) |
|:---|:---|:---|
| [Merkezi yönetim](../defender-endpoint/manage-atp-post-migration.md) <sup>[[1](#fn1)]</sup> | Evet | Evet | Evet |
| [Basitleştirilmiş istemci yapılandırması](mdb-simplified-configuration.md) | Evet | Hayır | Hayır |
| [Tehdit & güvenlik açığı yönetimi](../defender-endpoint/next-gen-threat-and-vuln-mgt.md) | Evet | Hayır | Evet |
| [Saldırı yüzeyini azaltma özellikleri](../defender-endpoint/overview-attack-surface-reduction.md) | Evet | Evet | Evet |
| [Yeni nesil koruma](../defender-endpoint/next-generation-protection.md) | Evet | Evet | Evet |
| [Uç nokta algılama ve yanıt](../defender-endpoint/overview-endpoint-detection-response.md) | Evet <sup>[[2](#fn2)]</sup> | Hayır | Evet |
| [Otomatik araştırma ve yanıt](../defender-endpoint/automated-investigations.md) | Evet <sup>[[2](#fn2)]</sup> | Hayır | Evet |
| [Tehdit avı](../defender-endpoint/advanced-hunting-overview.md) ve altı aylık veri bekletme | Hayır | Hayır | Evet |
| [Tehdit analizleri](../defender-endpoint/threat-analytics.md) | Evet <sup>[[2](#fn2)]</sup> | Hayır | Evet |
| [Platformlar arası destek](../defender-endpoint/minimum-requirements.md) <br/>(Windows, macOS, iOS ve Android OS) | Evet <sup>[[3](#fn3)]</sup> | Evet | Evet |
| [Microsoft Tehdit Uzmanları](../defender-endpoint/microsoft-threat-experts.md) | Hayır | Hayır | Evet |
| İş Ortağı API'leri | Evet | Evet | Evet |
| [Microsoft 365 Lighthouse tümleştirmesi](../../lighthouse/m365-lighthouse-overview.md) <br/>(Müşteri kiracıları genelinde güvenlik olaylarını görüntülemek için) | Evet | Hayır | Hayır |

(<a id="fn1">1</a>) Mobil portalda () veya Microsoft 365 Defender aracı ([https://security.microsoft.com](https://security.microsoft.com) )[https://endpoint.microsoft.com](https://endpoint.microsoft.com) gibi başka bir araçla cihazları Microsoft Endpoint Manager.

(<a id="fn2">2</a>) Bu özellikler küçük ve orta ölçekli işletmeler için en iyi duruma getirilmiştir.

(<a id="fn3">3</a>) Önizleme programı Windows, istemci cihazlarının önizleme portalında () Microsoft 365 Defender.[https://security.microsoft.com](https://security.microsoft.com)

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender (önizleme) gereksinimlerine bakın](mdb-requirements.md)

- [İş için Microsoft Defender'ı (önizleme) ayarlamayı ve yapılandırmayı öğrenin](mdb-setup-configuration.md) 