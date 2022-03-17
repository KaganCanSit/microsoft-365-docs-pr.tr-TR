---
title: Bulut için Microsoft Defender ile tümleştirme
description: Bulut için Microsoft Defender ile Uç Nokta Tümleştirmesi için Microsoft Defender hakkında bilgi
keywords: integration, server, azure, 2012r2, 2016, 2019, sunucu ekleme, cihaz yönetimi, Uç nokta sunucuları için Microsoft Defender'ı yapılandırma, Uç nokta sunucuları için Microsoft Defender'ı ekleme, Uç nokta sunucuları için Microsoft Defender'ı ekleme
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
ms.author: macapara
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 2ed9d25336cd7e8162849aa5d1d1a3e3382063fc
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526684"
---
# <a name="integration-with-microsoft-defender-for-cloud"></a>Bulut için Microsoft Defender ile tümleştirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Bulut için Microsoft Defender

Uç Nokta için Microsoft Defender Bulut için Microsoft Defender ile tümleştirin, kapsamlı bir sunucu Windows çözümü sağlar. Bu tümleştirmeyle, Bulut için Microsoft Defender Gelişmiş Sunucularda gelişmiş tehdit algılaması sağlamak üzere Uç Nokta için Defender'ın Windows kullanabilir.

Bu tümleştirmede aşağıdaki özellikler yer almaktadır:

- Otomatik ekleme - Uç nokta algılayıcısı için Defender, Bulut için Microsoft Defender'a Windows Sunucularda otomatik olarak etkinleştirilir. Bulut için Microsoft Defender ekleme hakkında daha fazla bilgi için bkz [. Uç nokta için tümleşik Microsoft Defender lisansını kullanma](/azure/security-center/security-center-wdatp).

    > [!NOTE]
    > Sunucular için Microsoft Defender ile Uç Nokta için Microsoft Defender arasındaki tümleştirme, [Windows Server 2019 ve Windows Virtual Desktop'u (WVD) destekleyecek şekilde genişletildi](/azure/security-center/release-notes#microsoft-defender-for-endpoint-integration-with-azure-defender-now-supports-windows-server-2019-and-windows-10-virtual-desktop-wvd-in-preview).

- Windows için Microsoft Defender tarafından izlenen sunuculara, Uç Nokta için Defender - Bulut için Microsoft Defender uç nokta kiracısı üzerinden sorunsuz bir şekilde bağlanarak, istemciler ve sunucular arasında tek bir görünüm sağlar.  Ayrıca, Bulut konsolu için Microsoft Defender'da Uç nokta uyarıları için Defender kullanılabilir.
- Sunucu soruşturması - Bulut müşterileri için Microsoft Defender Microsoft 365 Defender portalına erişarak olası ihlal kapsamını ortaya çıkarmak için ayrıntılı incelemeler gerçekleştirebilirsiniz.

> [!IMPORTANT]
> - Sunucuları izlemek için Bulut için Microsoft Defender'ı kullanıyorken, otomatik olarak uç nokta kiracısı için bir Defender oluşturulur (ABD kullanıcılarının ABD'de, Avrupa ve İngiltere kullanıcıları için AB'de).<br>
Uç Nokta için Defender tarafından toplanan veriler, sağlama sırasında tanımlandığı gibi kiracının coğrafi konumda depolanır.
> - Bulut için Microsoft Defender'ı kullanmadan önce Uç Nokta için Defender'ı kullanırsanız, daha sonra Bulut için Microsoft Defender ile tümleştirin, kiracınızı oluşturulduğunda verileriniz belirttiğiniz konumda depolanır.
> - Yapılandırıldığında, verilerinizin depolandığı konumu değiştiremezsiniz. Verilerinizi başka bir konuma taşımanız gerekirse, kiracıyı sıfırlamak için Microsoft Desteği'ne başvurun. <br>
Bu tümleştirmeyi kullanan sunucu uç noktası izlemesi, bu Office 365 GCC devre dışı bırakılmıştır.



## <a name="related-topics"></a>İlgili konular
- [Windows'un önceki sürümlerini ekleme](onboard-downlevel.md)
- [Onboard Windows Server 2012 R2, 2016, SAC sürüm 1803 ve 2019](configure-server-endpoints.md)
