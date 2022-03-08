---
title: Cihaz profillerini anlama
description: Yöneticilerin cihazlara atay erişim izinlerini alan çeşitli profiller
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: d12a197db8dbcb6356882082c212754fef726d4e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320837"
---
# <a name="device-profiles"></a>Cihaz profilleri

Cihaz profillerini, cihaz yapılandırma seçenekleri hiyerarşisinin bir parçası olarak düşünebilirsiniz.

:::image type="content" source="../../media/mmd-profile-options-heirarchy.png" alt-text="Piramit olarak gösterilen cihaz yapılandırmaları. Açıklama şöyledir:":::

| Cihaz yapılandırma seçenekleri | Açıklama
| ----- | ----- |
| Yapılandırmanız | En üstte, ağ ayrıntıları veya uygulamalar gibi kendi yapılandırmanız vardır. Bir cihaz, Microsoft Yönetilen Masaüstü tarafından yönetil olmayan veya engellenmiş herhangi bir sayıda yapılandırmaya sahip olabilir. |
| Özelleştirmeler | Bir sonraki üst düzey ise ek [özelleştirmelerdir](customizing.md). Her cihazda bir veya birden çok (veya hiç) özelleştirmesi olabilir. Özelleştirmeler alt düzey katmanı değiştirebilir (Cihaz profilleri veya temel yapılandırma) ya da standart yapılandırmanın en üstünde katmanda yer alan tamamen yeni bir istek olabilir. |
| Cihaz profilleri | Her Microsoft Yönetilen Masaüstü cihazına bir profil atanmış olmalı ve bu cihazdan yalnızca biri atanmıştır. Yöneticiler bir cihazın atandığı profili seçer.<br><br>Cihazlara farklı önceden ayarlanmış profiller atabilirsiniz. Her profil belirli kullanıcı türlerinin ihtiyaçlarına göre en iyi duruma getirilmiş. Üç cihaz profili vardır:<ul><li>Standard</li><li>Hassas Veriler</li><li>Güçlü kullanıcı</li> |
| Foundation | Temel olarak, her Microsoft Yönetilen Masaüstü cihazı için şunları içeren bir temel vardır:<br><ul><li>Standart güvenlik temeli</li><li>Uyumluluk ilkeleri</li><li>Windows Güncelleştirme ayarları</li><li>Gruplar</li></ul><br>Microsoft Yönetilen Masaüstü ile çalışmak için, her cihaz bu öğelerin hepsini içermeli. Bu öğeler yöneticiler tarafından değiştirilemez. Microsoft Yönetilen Masaüstü'ne bir istek göndermeniz gerekir. |

## <a name="device-profile-details"></a>Cihaz profili ayrıntıları

Aşağıdaki tabloda, cihaz profilleri tarafından yapılandırılan her ayar için ayarlar ve bunların varsayılan değerleri özetlenmiştir. Sahne gerisinde, bu ayarlar tek bir OMA-URIs Profilinde Özel Yapılandırma Profilleri kullanılarak Microsoft Endpoint Manager.

<br>

****

| Özellik | Hassas Veriler | Son Kullanıcı | Standard |
| ----- | :-----: | :-----: | :-----: |
|**Dış Engelleme Depolama**| Evet | Evet | Hayır |
|**[Bulut Blok Düzeyi](/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel)**| Yüksek | Yüksek | Yüksek |
|**Microsoft Hesaplarını devre dışı bırakma**| Evet | Evet | Hayır |
|**Kişisel bilgileri devre OneDrive**| Evet | Evet | Hayır |
|**[Yükseltme için güvenli masaüstüne geçiş](/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-useraccountcontrol-switchtothesecuredesktopwhenpromptingforelevation)**| Hayır | Evet | Hayır |
|**Uç Nokta Cihaz Etiketi için Microsoft Defender**| M365Managed-SensitiveData | M365Managed-PowerUser | M365Managed-Standard |
|**Cihazda yönetici misiniz?**| Hayır | Evet | Hayır |
|**AutoPilot Profili**| MMD Standard | MMD Güç Kullanıcısı | MMD Standard |
|**AppLocker**| Evet | Hayır | Hayır |
|**Genel Mağazayı Engelle**| Evet | Evet | Hayır |
|

Her cihaz profili de şu öğeleri içerir:

- Bir cihaz Azure Active Directory dinamik üyeliktir.
- Statik üyelik Azure Active Directory grubu.
- Bir Microsoft Endpoint Manager Profili.

> [!IMPORTANT]
> Bu grupların üyeliğini doğrudan değiştirmeyin. Profilleri yeniden atama konusunda [açıklandığı gibi arabirimi kullanın](../working-with-managed-desktop/change-device-profile.md).

## <a name="limitations"></a>Sınırlamalar

Cihaz profilleri ve ayrıntılarıyla ilgili diğer ilkelerde olduğu gibi özel durumlar talep edebilirsiniz.

Bir kuruluşta ("kiracı") yer alan ve her bir cihaz profili Azure Active Directory olduğunu unutmayın. Örneğin, Hassas veri cihazı profilinin AppLocker'ı yalnızca bazı kullanıcılarınız için devre dışı bırakmasını talep edebilirsiniz. Hassas veri cihazı profiline sahip tüm cihazların yapılandırması aynı olmalı.

Her cihazda yalnızca bir profil olabilir. Verilen cihaz birden çok kullanıcı tarafından kullanılıyorsa, o cihaza sahip tüm kullanıcılar aynı yapılandırmaya sahip olur.
