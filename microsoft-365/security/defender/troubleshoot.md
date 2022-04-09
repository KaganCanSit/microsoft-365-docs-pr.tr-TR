---
title: Microsoft 365 Defender hizmeti sorunlarını giderme
description: Bilinen Microsoft 365 Defender sorunlarının çözümlerini ve geçici çözümlerini bulma
keywords: sorun giderme Microsoft 365 Defender, sorun giderme, Kimlik için Microsoft Defender, sorunlar, eklenti, ayarlar sayfası
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 656599cf9ec66987119819b2f28f9a8eff1d4e77
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "64731680"
---
# <a name="troubleshoot-microsoft-365-defender-service-issues"></a>Microsoft 365 Defender hizmeti sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- Microsoft 365 Defender

Bu bölümde, Microsoft 365 Defender hizmetini kullanırken ortaya çıkabilecek sorunlar ele alınıyor.

## <a name="i-dont-see-microsoft-365-defender-content"></a>Microsoft 365 Defender içerik görmüyorum

Gezinti bölmesinde portalda Olaylar, İşlem merkezi veya Tehdit Avcılığı gibi özellikleri görmüyorsanız kiracınızın uygun lisanslara sahip olduğunu doğrulamanız gerekir.

Daha fazla bilgi için bkz [. Önkoşullar](prerequisites.md).

## <a name="microsoft-defender-for-identity-alerts-are-not-showing-up-in-the-microsoft-365-defender-incidents"></a>Microsoft 365 Defender olaylarında Kimlik için Microsoft Defender uyarıları gösterilmiyor

Ortamınıza Kimlik için Microsoft Defender dağıttıysanız ancak Microsoft 365 Defender olaylarının bir parçası olarak Kimlik için Defender uyarılarını görmüyorsanız, Microsoft Defender for Cloud Apps  ve Kimlik için Defender tümleştirmesi etkindir.

Daha fazla bilgi için bkz. [Kimlik için Microsoft Defender tümleştirme](/cloud-app-security/mdi-integration).

## <a name="where-is-the-settings-page-for-turning-on-the-service"></a>Hizmeti açmak için ayarlar sayfası nerede?

Microsoft 365 Defender açmak için **Microsoft 365 Defender** portalındaki gezinti bölmesinden Ayarlar erişin. Bu gezinti öğesi yalnızca [önkoşul izinleriniz ve lisanslarınız](m365d-enable.md#check-license-eligibility-and-required-permissions) varsa görünür.

## <a name="how-do-i-create-an-exception-for-my-fileurl"></a>Dosyam/URL'm için özel durum Nasıl yaparım? oluşturulsun mu?

Hatalı pozitif, kötü amaçlı olarak algılanan ancak bir tehdit olmayan bir dosya veya URL'dir. Belirli dosyaların/URL'lerin engellemesini kaldırmak ve izin vermek için göstergeler oluşturabilir ve dışlamalar tanımlayabilirsiniz. Bkz [. Uç Nokta için Defender'da hatalı pozitif/negatifleri adresle](/microsoft-365/security/defender-endpoint/defender-endpoint-false-positives-negatives).
