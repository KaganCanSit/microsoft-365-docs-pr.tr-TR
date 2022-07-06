---
title: Microsoft Teams'de varsayılan DLP ilkesi hakkında bilgi edinin (önizleme)
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
description: Microsoft Teams'de varsayılan veri kaybı önleme ilkesi hakkında bilgi edinin
ms.openlocfilehash: 5c3a5a116da90a41abcc459808e83176dc750fe1
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624233"
---
# <a name="learn-about-the-default-data-loss-prevention-policy-in-microsoft-teams-preview"></a>Microsoft Teams'teki varsayılan veri kaybı önleme ilkesi hakkında daha fazla bilgi edinme (önizleme)

[Microsoft Purview Veri Kaybı Önleme](dlp-learn-about-dlp.md) özellikleri Microsoft Teams sohbeti ve özel kanal iletileri dahil olmak üzere kanal iletilerini içerecek şekilde genişletilmiştir. Bu sürümün bir parçası olarak, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalı</a> ilk kez çalışan müşteriler için Microsoft Teams için varsayılan bir DLP ilkesi oluşturduk.

## <a name="licensing"></a>Lisanslama

Microsoft Teams'de DLP için tam lisans bilgileri için bkz[. Information Protection: Teams için Veri Kaybı Önleme](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-teams).

## <a name="what-does-the-default-policy-do"></a>Varsayılan ilke ne yapar?

Teams için varsayılan DLP ilkesi, kuruluş içinde ve dışında paylaşılan tüm kredi kartı numaralarını izler. Bu ilke, kiracının tüm kullanıcıları için varsayılan olarak açıktır. Son kullanıcılar için herhangi bir ilke ipucu oluşturmaz, bir Uyarı olayı oluşturur ve ayrıca yöneticiye düşük önem derecesinde bir e-posta tetikler (ilkeye eklenir). Yönetici, Uyumluluk merkezinde oturum açarak etkinlikleri görüntüleyebilir ve ilke ayrıntılarını düzenleyebilir.

Yöneticiler bu ilkeyi [Microsoft Purview uyumluluk portalı >](https://compliance.microsoft.com/compliancesettings) Veri Kaybı önleme ilkeleri sayfasında görüntüleyebilir.


> [!div class="mx-imgBorder"]
> ![varsayılan Teams DLP ilkesi.](../media/default-teams-dlp-policy.png)

## <a name="edit-or-delete-the-default-policy"></a>Varsayılan ilkeyi düzenleme veya silme

[Daha iyi performans için varsayılan ilkeyi düzenlemek veya silmek için](create-test-tune-dlp-policy.md#tune-a-dlp-policy) **DLP Uyumluluk Yönetimi** izinlerine sahip bir hesap kullanmanız yeterlidir. Daha fazla bilgi için bkz. [İzinler](create-test-tune-dlp-policy.md#permissions).

