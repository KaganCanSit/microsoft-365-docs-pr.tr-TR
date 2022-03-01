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
ms.openlocfilehash: 0b2bf3b0b4912d9e9b25c38b06262efb696f0cf2
ms.sourcegitcommit: a6651b841f111ea2776cab88bf2c80f805fa8e09
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2022
ms.locfileid: "63027275"
---
# <a name="device-profiles"></a>Cihaz profilleri

Cihazlara, her biri belirli tür kullanıcıların ihtiyaçları için iyileştirilmiş farklı önceden ayarlanmış yapılandırmalar ("cihaz profilleri") atabilirsiniz. Üç cihaz profili vardır:

- Standard
- Hassas Veriler
- Güçlü kullanıcı

Cihaz profillerini, cihaz yapılandırma seçenekleri hiyerarşisinin bir parçası olarak düşünebilirsiniz.

:::image type="content" source="../../media/mmd-profile-options-heirarchy.png" alt-text="Piramit olarak gösterilen cihaz yapılandırmaları. Açıklama şöyledir:":::

Temel olarak, her Microsoft Yönetilen Masaüstü cihazı standart bir güvenlik temeli, uyumluluk ilkeleri, Güncelleştirme ayarları ve grupları Windows bir temele sahip olur. Microsoft Yönetilen Masaüstü ile çalışmak için, her cihazda yöneticiler tarafından Microsoft Yönetilen Masaüstü'ne istek olmadan değiştiril türlü türlü bu öğelerin hepsi yer alamayacak tüm öğeler gerekir.

Cihaz profilleri bir sonraki üst düzeyde görünür. Her Microsoft Yönetilen Masaüstü cihazına bir (ve yalnızca bir) profil atanmış olması gerekir. Yöneticiler bir cihazın atandığı profili seçebilir.

Hala daha yüksek bir düzeyde ek [özelleştirmeler vardır](customizing.md). Her cihazda bir veya birden çok (veya hiç) özelleştirmesi olabilir. Alt düzey katmanı (Cihaz profilleri veya temel yapılandırma) değiştirebilir ya da standart yapılandırmanın en üstünde katmanda yer alan tamamen yeni bir istek olabilir.

En üstte, ağ ayrıntıları veya uygulamalar gibi kendi değişiklikleriniz vardır. Bir cihaz, Microsoft Yönetilen Masaüstü tarafından yönetil olmayan veya engellenmiş herhangi bir sayıda değişiklike sahip olabilir.


## <a name="device-profile-details"></a>Cihaz profili ayrıntıları

Aşağıdaki tabloda, cihaz profilleri tarafından yapılandırılan her ayar için ayarlar ve bunların varsayılan değerleri özetlenmiştir. (Sahne gerisinde, bu ayarlar OMA-URIs'de Özel Yapılandırma Profilleri kullanılarak Microsoft Endpoint Manager.)

<br>

****

|Özellik|Hassas Veriler|Son Kullanıcı|Standard|
|---|:---:|:---:|:---:|
|**Dış Engelleme Depolama**|Evet|Evet|Hayır|
|**[Bulut Blok Düzeyi](/windows/client-management/mdm/policy-csp-defender#defender-cloudblocklevel)**|Yüksek|Yüksek|Yüksek|
|**Microsoft Hesaplarını devre dışı bırakma**|Evet|Evet|Hayır|
|**Kişisel bilgileri devre OneDrive**|Evet|Evet|Hayır|
|**[Yükseltme için güvenli masaüstüne geçiş](/windows/client-management/mdm/policy-csp-localpoliciessecurityoptions#localpoliciessecurityoptions-useraccountcontrol-switchtothesecuredesktopwhenpromptingforelevation)**|Hayır|Evet|Hayır|
|**Uç Nokta Cihaz Etiketi için Microsoft Defender**|M365Managed-SensitiveData|M365Managed-PowerUser|M365Managed-Standard|
|**Cihazda yönetici misiniz?**|Hayır|Evet|Hayır|
|**AutoPilot Profili**|MMD Standard|MMD Güç Kullanıcısı|MMD Standard|
|**AppLocker**|Evet|Hayır|Hayır|
|**Genel Mağazayı Engelle**|Evet|Evet|Hayır|
|

Her cihaz profili de şu öğeleri içerir:

- Dinamik üyelik Azure Active Directory (AAD) cihaz grubu
- Statik üyelik AAD grubu
- A Microsoft Endpoint Manager Configuration profile

> [!IMPORTANT]
> Bu grupların üyeliğini doğrudan değiştirmeyin. Profilleri yeniden atama konusunda [açıklandığı gibi arabirimi kullanın](../working-with-managed-desktop/change-device-profile.md).

## <a name="limitations"></a>Sınırlamalar

Cihaz profilleri ve ayrıntılarıyla ilgili diğer ilkelerde olduğu gibi özel durumlar talep edebilirsiniz. Bir kuruluşta ("kiracı") yer alan ve her bir cihaz profili Azure Active Directory olduğunu unutmayın. Örneğin, Hassas veri cihazı profilinin AppLocker'ı yalnızca bazı kullanıcılarınız için devre dışı bırakmasını talep edebilirsiniz. Hassas veri profiline sahip tüm cihazlar aynı yapılandırmaya sahip olmalı.

Her cihazda yalnızca bir profil olabilir. Verilen cihaz birden çok kullanıcı tarafından kullanılıyorsa, o cihaza sahip tüm kullanıcılar aynı yapılandırmaya sahip olur.
