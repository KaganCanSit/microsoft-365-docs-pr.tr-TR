---
title: Negatif sonuçlarda hatalı pozitif veya yanlış negatif Microsoft 365 Defender
description: Başka bir yerde AIR tarafından bir şey cevapsız veya yanlış Microsoft 365 Defender? Çözümleme için Microsoft'a hatalı pozitif veya yanlış negatif sonuçlar göndermeyi öğrenin.
keywords: otomatik, araştırma, uyarı, düzeltme, hatalı pozitif, hatalı negatif
search.appverid: met150
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
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: how-to
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: 67246d7f7876457e6553818b469987a2b5a59eb0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63321801"
---
# <a name="address-false-positives-or-false-negatives-in-microsoft-365-defender"></a>Negatif sonuçlarda hatalı pozitif veya yanlış negatif Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Herhangi bir tehdit koruması çözümünde hatalı pozitif veya negatif sonuçlar bazen ortaya çıkabilir. Bir [şeyi kaçırılmış veya yanlış algılandığında](m365d-autoir.md) Microsoft 365 Defender araştırma ve yanıt özellikleri otomatik olarak algılanırsa, güvenlik işlemleri ekibimizin benimsey işlemler için atılması gereken adımlar vardır:

- [Microsoft'a hatalı pozitif/negatif bir rapor bildirme](#report-a-false-positivenegative-to-microsoft-for-analysis)
- [Uyarılarınızı ayarlama](#adjust-an-alert-to-prevent-false-positives-from-recurring) (gerekirse)
- [Cihazlarda yapılan düzeltme eylemlerini geri alma](#undo-a-remediation-action-that-was-taken-on-a-device)

Aşağıdaki bölümlerde bu görevlerin nasıl yerine nasıl gerçekleştir olduğu açıklanmaktadır.

## <a name="report-a-false-positivenegative-to-microsoft-for-analysis"></a>Çözümleme için hatalı pozitif/negatif microsoft raporu

|Öğe atlandı veya yanlış algılandı |Hizmet  |Ne yapmalı?  |
|---------|---------|---------|
|- E-posta iletisi <br/>- E-posta eki <br/>- E-posta iletisinde URL<br/>- Office dosyasında URL      |[Office 365 için Microsoft Defender](/microsoft-365/security/office-365-security/defender-for-office-365)        |[Şüpheli istenmeyen posta, kimlik avı, URL'ler ve dosyaları tarama için Microsoft'a gönderme](../office-365-security/admin-submission.md)         |
|Cihazda dosya veya uygulama    |[Uç Nokta için Microsoft Defender](/windows/security/threat-protection)         |[Kötü amaçlı yazılım çözümlemesi yapmak için bir dosyayı Microsoft'a gönderme](https://www.microsoft.com/wdsi/filesubmission)         |

## <a name="adjust-an-alert-to-prevent-false-positives-from-recurring"></a>Hatalı pozitif sonuç yinelemesini önlemek için uyarı ayarlama

|Senaryo |Hizmet |Ne yapmalı? |
|--------|--------|--------|
|- Yasal kullanım uyarılarını tetikler <br/>- Uyarı yanlış    |[Bulut Uygulamaları için Microsoft Defender](/cloud-app-security)<br/> veya <br/>[Azure tehdit koruması](/azure/security/fundamentals/threat-detection)         |[Bulut Uygulamaları için Defender portalında uyarıları yönetme](/cloud-app-security/managing-alerts)         |
|Bir cihaz güvenli olsa bile, bir dosya, IP adresi, URL veya etki alanı kötü amaçlı yazılım olarak kabul edilir|[Uç Nokta için Microsoft Defender](/windows/security/threat-protection) |["İzin Ver" eylemiyle özel bir gösterge oluşturma](/windows/security/threat-protection/microsoft-defender-atp/manage-indicators) |

## <a name="undo-a-remediation-action-that-was-taken-on-a-device"></a>Cihazda yapılan düzeltme eylemlerini geri alma

Bir varlık üzerinde (cihaz veya e-posta iletisi gibi) bir düzeltme eylemi gerçek bir tehdit ise ve etkilenen varlık aslında bir tehdit ise, güvenlik işlemleri takımınız İşlem Merkezi'nde düzeltme eylemini geri [alabilir](m365d-action-center.md).

1. Portala <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender ve</a> oturum açın. 
2. Gezinti bölmesinde İşlem **merkezi'ni seçin**. 
3. Geçmiş **sekmesinde** , geri almak istediğiniz eylemi seçin. Açılır bölmesi açılır.
4. Uçarak çıkış bölmesinde Geri Al'ı **seçin**.

> [!TIP]
> Bkz [. Tamamlanmış eylemleri geri alma](m365d-autoir-actions.md#undo-completed-actions).

## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik bir incelemenin ayrıntılarını ve sonuçlarını görüntüleme](m365d-autoir-results.md)
- [E-Microsoft 365 Defender'de gelişmiş avla tehditlere karşı önceden Microsoft 365 Defender](advanced-hunting-overview.md)
