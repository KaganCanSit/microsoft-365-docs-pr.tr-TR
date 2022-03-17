---
title: Küçük ve orta ölçekli Microsoft 365 kurumsal planlarda güvenlik özelliklerini karşılaştırma
description: İş için Defender ile Uç Nokta için Defender arasındaki farkları anlıyoruz. Her plana nelerin dahil olduğunu bilmek, şirket için bilinçli bir karar ataymanıza yardımcı olabilir.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: reference
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-initiative-defender-business
- m365-security-compliance
ms.openlocfilehash: 793c078621424bca89ccc4c6d88c79054ab059cd
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526034"
---
# <a name="compare-microsoft-defender-for-business-to-microsoft-365-business-premium"></a>İş için Microsoft Defender ile Microsoft 365 İş Ekstra

> [!IMPORTANT]
> İş için Microsoft Defender 1 Mart 2022 [Microsoft 365 İş Ekstra'den](../../business-premium/index.md) itibaren tüm müşterilere sunulmaktadır. Tek başına bir abonelik olarak İş için Defender önizlemededir ve talep etmek için buraya kaydolan müşterilere ve IT İş Ortaklarına [aşamalı](https://aka.ms/mdb-preview) olarak tüm müşterilere aşamalı olarak yayınlatır. Önizleme bir [dizi senaryo içerir ve](mdb-tutorials.md#try-these-preview-scenarios) düzenli olarak özellikler ekleycek.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

Microsoft, küçük ve orta ölçekli işletmeler için çeşitli planlar da dahil olmak üzere çok çeşitli bulut çözümleri ve hizmetleri sunar. Örneğin, [Microsoft 365 İş Ekstra](../../business/microsoft-365-business-overview.md) gibi üretkenlik özelliklerinin yanı sıra güvenlik ve cihaz yönetimi özelliklerini de Office içerir. Bu makale, Microsoft 365 İş Ekstra, İş için Microsoft Defender ve Uç Nokta için Microsoft Defender'a hangi güvenlik özelliklerinin dahil olduğunu netleştirmeye yardımcı olmak üzere tasarlanmıştır.

Microsoft Defender for Business, tek başına bir teklif olarak veya Microsoft 365 İş Ekstra (1 Mart 2022'den itibaren) olarak sunulmaktadır.

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

**Bu makaleyi kullanarak**:

- [İş için Microsoft Defender(tek başına) ile Microsoft 365 İş Ekstra](#compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium)
- [İş için Defender'ı (tek başına) Uç nokta kurumsal teklifleri için Microsoft Defender ile karşılaştırma](#compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2)

**İş için Microsoft Defender'ı Microsoft 365 bir Microsoft 365 aboneliğiniz yok.** microsoft Defender for Business Microsoft 365 İş Ekstra küçük ve orta ölçekli işletmeler için tek başına bir güvenlik çözümü olarak kullanılabilir. Zaten standart veya Microsoft 365 İş Temel varsa, daha fazla tehdit koruması özelliği elde etmek için Microsoft 365 İş Ekstra'e yükseltin veya İş için Microsoft Defender'ı eklemeyi düşünün. 

## <a name="compare-security-features-in-microsoft-defender-for-business-to-microsoft-365-business-premium"></a>İş için Microsoft Defender'daki güvenlik özelliklerini Microsoft 365 İş Ekstra

> [!NOTE]
> Bu makale, İş için Microsoft Defender (tek başına bir plan olarak) ve Microsoft 365 İş Ekstra (İş için Defender'ı içerir) ile birlikte bulunan tehdit koruması özelliklerine üst düzey bir genel bakış sağlamak üzere hazırlanmıştır. Bu makale, hizmet açıklaması veya lisanslama belgesi olarak amaçlanmaz. Daha fazla bilgi için güvenlik [Microsoft 365 uyumluluğu için lisanslama & bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

**1 Mart 2022'den itibaren, İş için Defender yeni bir Microsoft 365 İş Ekstra. Tek başına bir teklif olarak İş için Defender hala önizlemede.**

Aşağıdaki tabloda, İş için Defender'daki (bağımsız) güvenlik özellikleri ve özellikleri ile Microsoft 365 İş Ekstra. 

 <br/><br/>

| Özellik/Özellik | [İş için Microsoft Defender](mdb-overview.md)<br/>(tek başına; şu anda önizlemede) | [Microsoft 365 Business Premium](../../business/microsoft-365-business-overview.md)<br/>(İş için Defender'ı içerir) |
|:---|:---|:---|
| E-posta koruması | Evet <br/>- [Microsoft Defender Virüsten Koruma ile e-posta tarama](../defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus.md) | Evet <br/>- [Exchange Online Protection](../office-365-security/exchange-online-protection-overview.md) <br/>- [Microsoft Defender Virüsten Koruma ile e-posta tarama](../defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus.md) |
| Antispam koruması | Evet <br/>- Cihazlar için | Evet <br/>- Cihazlar için<br/>- İletiler Microsoft 365 ekleri gibi e-posta içeriğini daha fazla bilgi için |
| Kötü amaçlı yazılımlardan koruma | Evet<br/>- Cihazlar için | Evet <br/>- Cihazlar için<br/>- İletiler Microsoft 365 ekleri gibi e-posta içeriğini daha fazla bilgi için |
| [Yeni nesil koruma](../defender-endpoint/microsoft-defender-antivirus-in-windows-10.md) <br/> (virüsten koruma ve kötü amaçlı yazılımlardan koruma) | Evet<br/>- Microsoft Defender Virüsten Koruma ve sonraki Windows 10 dahildir  | Evet <br/>- Microsoft Defender Virüsten Koruma ve sonraki Windows 10 dahildir<br/>- Yerleşik cihazlar için yeni nesil koruma ilkeleri |
| [Saldırı yüzeyini azaltma](../defender-endpoint/overview-attack-surface-reduction.md) <br/>(Güvenlik duvarı koruması veya Windows 10 için ASR kuralları) | Evet  | Evet  |
| [Uç nokta algılama ve yanıt](../defender-endpoint/overview-endpoint-detection-response.md) <br/>(davranış tabanlı algılama ve el ile yanıt eylemleri) | Evet | Evet |
| [Otomatik araştırma ve yanıt](../defender-endpoint/automated-investigations.md) | Evet | Evet |
| [Tehdit & güvenlik açığı yönetimi](../defender-endpoint/tvm-dashboard-insights.md) | Evet | Evet |
| Merkezi yönetim ve raporlama  | Evet  | Evet  |
| [API'ler](../defender-endpoint/apis-intro.md) <br/>(özel uygulamalarla veya raporlama çözümleriyle tümleştirme için)  | Evet | Evet |


## <a name="compare-microsoft-defender-for-business-to-microsoft-defender-for-endpoint-plans-1-and-2"></a>İş için Microsoft Defender ile Uç Nokta Planları 1 ve 2 için Microsoft Defender'ı karşılaştırma

İş için Defender küçük ve orta ölçekli işletmelere Uç Nokta için Defender'ın kurumsal sınıf özellikleri getirir. 

Aşağıdaki tabloda, İş için Defender'daki güvenlik özellikleri ve özellikleri ile Uç Nokta Planları 1 ve 2 için Microsoft Defender karşılaştırıldı. <br/><br/>

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

- [İş için Microsoft Defender gereksinimlerine bakın](mdb-requirements.md)

- [İş için Microsoft Defender'ı almak](get-defender-business.md)

- [İş için Microsoft Defender'ı ayarlamayı ve yapılandırmayı öğrenin](mdb-setup-configuration.md) 
