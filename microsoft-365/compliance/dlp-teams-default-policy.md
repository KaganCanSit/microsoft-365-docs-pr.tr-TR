---
title: Microsoft Teams'teki varsayılan veri kaybı önleme ilkesi hakkında daha fazla bilgi edinme (önizleme)
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
ms.openlocfilehash: 61443cdfdc116e9c25d9dad24c968876ae5d0349
ms.sourcegitcommit: db2ed146b46ade9ea62eed9cb8efff5fea7a35e6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2022
ms.locfileid: "64481374"
---
# <a name="learn-about-the-default-data-loss-prevention-policy-in-microsoft-teams-preview"></a>Microsoft Teams'teki varsayılan veri kaybı önleme ilkesi hakkında daha fazla bilgi edinme (önizleme)

[Veri kaybı](dlp-learn-about-dlp.md) önleme özellikleri, özel kanal iletileri dahil olmak Microsoft Teams sohbet ve kanal iletilerini de içerecek şekilde genişletildi. Bu sürümün bir parçası olarak, ilk kez gelen müşteriler için Microsoft Teams varsayılan bir DLP ilkesi <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a>.

## <a name="licensing"></a>Lisanslama

DLP'nin tüm lisans bilgilerini Microsoft Teams için bkz[. Information Protection: Lisanslama için Veri Kaybı Önleme Teams](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-teams).

## <a name="what-does-the-default-policy-do"></a>Varsayılan ilke ne işe geliyor?

Kuruluş için varsayılan DLP Teams, kuruluş içinde ve dışında paylaşılan tüm kredi kartı numaralarını izler. Bu ilke, kiracının tüm kullanıcıları için varsayılan olarak açıktır. Son kullanıcılar için herhangi bir ilke ipucu oluşturmaz, ancak bir Uyarı olayı üretir ve ayrıca yöneticiye düşük önem düzeyi olan bir e-postayı tetikler (ilkeye eklenmiştir). Yönetici, Uyumluluk merkezi'nde oturum açmakla etkinlikleri  görüntüleyemez ve ilke ayrıntılarını düzenleyebilir.

Yöneticiler bu ilkeyi, Veri Kaybı [önleme ilkeleri](https://compliance.microsoft.com/compliancesettings) > Uyumluluk Merkezi'nde görebilirsiniz.


> [!div class="mx-imgBorder"]
> ![varsayılan Teams DLP ilkesidir.](../media/default-teams-dlp-policy.png)

## <a name="edit-or-delete-the-default-policy"></a>Varsayılan ilkeyi düzenleme veya silme

Daha [iyi performans için varsayılan ilkeyi düzenlemek veya silmek için](create-test-tune-dlp-policy.md#tune-a-dlp-policy), DLP Uyumluluk Yönetimi izinlerine **sahip bir hesap kullanın** . Daha fazla bilgi için bkz. [İzinler](create-test-tune-dlp-policy.md#permissions).

