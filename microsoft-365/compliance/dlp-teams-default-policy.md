---
title: E-postada (önizleme) varsayılan veri Microsoft Teams ilkesi hakkında bilgi
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: E-postada varsayılan veri kaybı önleme Microsoft Teams
ms.openlocfilehash: 61a1ea22362d9e75d605660d29116140f6708003
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990602"
---
# <a name="learn-about-the-default-data-loss-prevention-policy-in-microsoft-teams-preview"></a>E-postada (önizleme) varsayılan veri Microsoft Teams ilkesi hakkında bilgi

[Veri kaybı](dlp-learn-about-dlp.md) önleme özellikleri, özel kanal iletileri dahil olmak Microsoft Teams sohbet ve kanal iletilerini de içerecek şekilde genişletildi. Bu sürümün bir parçası olarak, ilk kez gelen müşteriler için Microsoft Teams varsayılan bir DLP ilkesi <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a>.

## <a name="applies-to"></a>Geçerli olduğu yer:

Aşağıdaki lisanslardan biri veya birden fazlası ile lisanslı olan ve etkin kullanıcı Teams.
 
- ME5, 
- MA5, 
- E5/A5 Uyumluluğu 
- IP+G tuşlarına bas 
- OE5 
- O365 Gelişmiş Uyumluluk 
- EMS E5


## <a name="what-does-the-default-policy-do"></a>Varsayılan ilke ne işe geliyor?

Kuruluş için varsayılan DLP Teams, kuruluş içinde ve dışında paylaşılan tüm kredi kartı numaralarını izler. Bu ilke, kiracının tüm kullanıcıları için varsayılan olarak açıktır. Son kullanıcılar için herhangi bir ilke ipucu oluşturmaz, ancak bir Uyarı olayı üretir ve ayrıca yöneticiye düşük önem düzeyi olan bir e-postayı tetikler (ilkeye eklenmiştir). Yönetici, Uyumluluk merkezi'nde oturum açmakla etkinlikleri  görüntüleyemez ve ilke ayrıntılarını düzenleyebilir.

Yöneticiler bu ilkeyi, Veri Kaybı [önleme ilkeleri](https://compliance.microsoft.com/compliancesettings) > Uyumluluk Merkezi'nde görebilirsiniz.


> [!div class="mx-imgBorder"]
> ![varsayılan Teams DLP ilkesidir.](../media/default-teams-dlp-policy.png)

## <a name="edit-or-delete-the-default-policy"></a>Varsayılan ilkeyi düzenleme veya silme

Daha [iyi performans için varsayılan ilkeyi düzenlemek veya silmek için](create-test-tune-dlp-policy.md#tune-a-dlp-policy), DLP Uyumluluk Yönetimi izinlerine **sahip bir hesap kullanın** . Daha fazla bilgi için bkz. [İzinler](create-test-tune-dlp-policy.md#permissions).

