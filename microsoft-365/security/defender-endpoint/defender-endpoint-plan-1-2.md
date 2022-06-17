---
title: Uç Nokta için Microsoft Defender planlarını karşılaştırma
description: Uç Nokta Planı 1 için Defender'ı Plan 2 ile karşılaştırın. Planlar arasındaki farklar hakkında bilgi edinin ve kuruluşunuzun gereksinimlerine uygun planı seçin.
keywords: Uç Nokta için Defender, gelişmiş tehdit koruması, uç nokta koruması
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 06/17/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: shlomi, efratka
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 00db46643d3f2b49003194075c44970a20ba83e9
ms.sourcegitcommit: 7ac54e1952383d5cd5f084c6a9d247eb747d4904
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66139441"
---
# <a name="compare-microsoft-defender-for-endpoint-plans"></a>Uç Nokta için Microsoft Defender planlarını karşılaştırma

Uç Nokta için Microsoft Defender, kurumsal ağların gelişmiş tehditleri engellemesine, algılamasına, araştırmasına ve yanıtlamasına yardımcı olmak için tasarlanmış bir kurumsal uç nokta güvenlik platformudur. Uç Nokta için Defender, merkezi yönetim ve raporlama ile birlikte virüsten koruma, kötü amaçlı yazılımdan koruma, fidye yazılımı risk azaltma ve daha fazlasını içeren gelişmiş tehdit koruması sağlar. Uç Nokta için Microsoft Defender için aşağıdaki seçenekler arasından seçim yapabilirsiniz:

- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender Güvenlik Açığı Yönetimi](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Uç Nokta Planı 1 için Defender, Uç Nokta Plan 2 için Defender ve yeni Defender Güvenlik Açığı Yönetimi eklentisinde sağlanan farklı özelliklerin hangi korumayı sağladığını netleştirmeye yardımcı olması için bu makaleyi kullanabilirsiniz.

## <a name="compare-defender-for-endpoint-plans"></a>Uç Nokta için Defender planlarını karşılaştırın

Aşağıdaki tabloda her Uç Nokta için Defender planına nelerin dahil olduğu özetlenmiştir.

| Plan | Dahil olanlar |
|:---|:---|
| [Uç Nokta için Defender Plan 1](defender-endpoint-plan-1.md) | <ul><li>[Yeni nesil koruma](defender-endpoint-plan-1.md#next-generation-protection) (kötü amaçlı yazılımdan koruma ve virüsten koruma içerir)</li><li>[Saldırı yüzeyini azaltma](defender-endpoint-plan-1.md#attack-surface-reduction)</li><li> [El ile yanıt eylemleri](defender-endpoint-plan-1.md#manual-response-actions)</li><li>[Merkezi yönetim](defender-endpoint-plan-1.md#centralized-management)</li><li>[Güvenlik raporları](defender-endpoint-plan-1.md#reporting)</li><li>[Apı 'leri](defender-endpoint-plan-1.md#apis)</li><li>[Windows 10, iOS, Android işletim sistemi ve macOS cihazları için destek](defender-endpoint-plan-1.md#cross-platform-support)</li></ul>|
| [Uç Nokta için Defender Plan 2](microsoft-defender-endpoint.md) | Uç Nokta için Defender Plan 1 özelliklerinin tümüne ek olarak:<ul><li>[cihaz keşfi](device-discovery.md)</li><li>[Cihaz envanteri](machines-view-overview.md)</li><li>[Core Defender Güvenlik Açığı Yönetimi özellikleri](../defender-vulnerability-management/defender-vulnerability-management-capabilities.md)</li><li>[Tehdit Analizi](threat-analytics.md)</li><li>[Otomatik araştırma ve yanıt](automated-investigations.md)</li><li>[Gelişmiş avcılık örneği](advanced-hunting-overview.md)</li><li>[Uç nokta algılama ve yanıt](overview-endpoint-detection-response.md)</li><li>[Microsoft Tehdit Uzmanları](microsoft-threat-experts.md)</li><li>[Windows](configure-endpoints.md) (istemci ve sunucu) ve [Windows olmayan platformlar (macOS](configure-endpoints-non-windows.md), iOS, Android ve Linux) desteği</li></ul> |
| [Defender Güvenlik Açığı Yönetimi eklentisi](../defender-vulnerability-management/defender-vulnerability-management-capabilities.md) | Uç Nokta Için Defender Plan 2 için Ek Defender Güvenlik Açığı Yönetimi:<ul><li>[Güvenlik temelleri değerlendirmesi](../defender-vulnerability-management/tvm-security-baselines.md)</li><li>[Güvenlik açığı bulunan uygulamaları engelleyin](../defender-vulnerability-management/tvm-block-vuln-apps.md)</li><li>[Tarayıcı uzantıları](../defender-vulnerability-management/tvm-browser-extensions.md)</li><li>[Dijital sertifika değerlendirmesi](../defender-vulnerability-management/tvm-certificate-inventory.md)</li><li>[Ağ paylaşımı analizi](../defender-vulnerability-management/tvm-network-share-assessment.md)</li><li>[Windows](configure-endpoints.md) (istemci ve sunucu) ve [Windows olmayan platformlar (macOS](configure-endpoints-non-windows.md), iOS, Android ve Linux) desteği</li></ul> |

## <a name="mixed-licensing-scenarios"></a>Karma lisanslama senaryoları

Kuruluşunuzun Uç Nokta Için Defender Plan 1 ve Uç Nokta Için Defender Plan 2 gibi Microsoft uç nokta güvenlik aboneliklerinin bir karışımını kullandığını varsayalım. **Şu anda en yüksek işlevsel Microsoft uç nokta güvenlik aboneliği kiracınızın deneyimini ayarlar**. Bu örnekte kiracı deneyiminiz tüm kullanıcılar için Uç Nokta Planı 2 için Defender olacaktır.

Ancak, **destek birimine başvurabilir ve kiracı deneyiminiz için geçersiz kılma isteğinde bulunabilirsiniz**. Diğer bir ifadeyle, tüm kullanıcılar için Uç Nokta Planı 1 için Defender deneyimini korumak için bir geçersiz kılma isteyebilirsiniz. 

- Lisanslar ve ürün koşulları hakkında ayrıntılı bilgi için bkz[. Microsoft 365 abonelikler için lisanslama ve ürün koşulları](https://www.microsoft.com/licensing/terms/productoffering/Microsoft365/MCA).
- Desteğe başvurma hakkında bilgi için bkz. [Destek Uç Nokta için Microsoft Defender başvurun](contact-support.md).

> [!TIP]
> Kuruluşunuz küçük veya orta ölçekli bir işletmeyse aşağıdaki makalelere bakın:
> - [İş için Microsoft Defender nedir?](../defender-business/mdb-overview.md)
> - [Küçük ve orta ölçekli işletmeler için Microsoft 365 planlarındaki güvenlik özelliklerini karşılaştırın](../defender-business/compare-mdb-m365-plans.md).

## <a name="start-a-trial"></a>Deneme sürümü başlatma

- Uç Nokta Için Defender Plan 1'i denemek için adresini ziyaret edin [https://aka.ms/mdep1trial](https://aka.ms/mdep1trial).
- Uç Nokta Için Defender Plan 2'yi denemek için adresini ziyaret edin [https://aka.ms/MDEp2OpenTrial](https://aka.ms/MDEp2OpenTrial).
- Microsoft Defender Güvenlik Açığı Yönetimi eklentisini denemek için adresini ziyaret edin[https://aka.ms/AddonPreviewTrial](https://aka.ms/AddonPreviewTrial). 

## <a name="see-also"></a>Ayrıca bkz.

- [İş için Microsoft Defender](../defender-business/mdb-overview.md) (küçük ve orta ölçekli işletmeler için uç nokta koruması)