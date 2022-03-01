---
title: Sertifikalara dayalı göstergeler oluşturma
ms.reviewer: ''
description: Varlıkları algılama, önleme ve dışlamaları tanımlayan sertifikalara dayalı göstergeler oluşturun.
keywords: ioc, sertifika, sertifikalar, yönetme, izin verilen, engellendi, engelle, temiz, kötü amaçlı, dosya karma, ip adresi, url'ler, etki alanı
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 7140b5714dd3660fe8dead37c3b6341d026fbb7c
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998262"
---
# <a name="create-indicators-based-on-certificates"></a>Sertifikalara dayalı göstergeler oluşturma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Sertifikalar için göstergeler oluşturabilirsiniz. Bazı yaygın kullanım örnekleri şunlardır:

- Saldırı yüzeyini azaltma kuralları ve denetimli klasör erişimi gibi engelleme teknolojilerini [](attack-surface-reduction.md) dağıtmanız gereken ancak sertifikayı izin listesine ekleyerek imzalanan uygulamalardan gelen davranışlara izin vermenizi istediğiniz senaryolar.[](controlled-folders.md)
- Kuruluş genelinde belirli bir imzalı uygulama kullanımını engelleme. Uygulamanın sertifikasını engellemek için bir gösterge oluşturarak, Windows Defender AV dosya yürütmelerini (engelleme ve düzeltme) engelleyecek ve Otomatik Araştırma ve Düzeltme aynı şekilde davranır.

## <a name="before-you-begin"></a>Başlamadan önce

Sertifikalar için göstergeler oluşturmadan önce aşağıdaki gereksinimleri anlamak önemlidir:

- Bu özellik, organizasyonunız Veri Tabanlı Windows Defender Virüsten Koruma kullanıyorsa ve Bulut tabanlı koruma etkinleştirildiyse kullanılabilir. Daha fazla bilgi için bkz [. Bulut tabanlı korumayı yönetme](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus).
- Kötü amaçlı yazılımdan koruma istemci sürümü 4.18.1901.x veya sonraki bir sürümde olabilir.
- Windows 10, sürüm 1703 veya sonraki sürümler, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 ve Windows Server 2022 makinelerde desteklenen makinelerde.
    
    >[!NOTE]
    >Windows Server 2016 ve Windows Server 2012 R2 için, bu özelliğin çalışması için [onboard Windows sunucularında](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) verilen yönergeler kullanılarak ekleme gerekiyor. 

- Virüs ve tehdit koruması tanımları güncel olmalıdır.
- Bu özellik şu anda girmeyi destekliyor. CER veya . PEM dosya uzantıları.

> [!IMPORTANT]
>
> - Geçerli yaprak sertifika, geçerli bir sertifika yolu olan ve Microsoft tarafından güvenilen Kök Sertifika Yetkilisi (CA) arasında zincirlemeli olmalıdır. Alternatif olarak, istemci tarafından güvendiği sürece özel (otomatik olarak imzalanan) bir sertifika kullanılabilir (Kök CA sertifikası Yerel Makine 'Güvenilen Kök Sertifika Yetkilileri' altına yüklenir).
> - İzin verme/engelleme sertifikası IOC'lerinin alt veya üstleri IoC izin ver/engelle işlevselliğine dahil değildir; yalnızca yaprak sertifikalar destekler.
> - Microsoft tarafından imzalanan sertifikalar engel kullanılamaz.

## <a name="create-an-indicator-for-certificates-from-the-settings-page"></a>Ayarlar sayfasından sertifikalar için bir gösterge oluşturun:

> [!IMPORTANT]
> Sertifika IoC'si oluşturmak ve kaldırmak 3 saat kadar sürebilir.

1. Gezinti bölmesinde, Uç Noktaları **Ayarlar** \> **Seçin** \> (**Kurallar'ın** **altında**).

2. Gösterge **ekle'yi seçin**.

3. Aşağıdaki ayrıntıları belirtin:
   - Gösterge - Varlık ayrıntılarını belirtin ve göstergenin sona erme tarihini tanımlayın.
   - Eylem - Alınacak eylemi belirtin ve bir açıklama girin.
   - Kapsam - Makine grubunun kapsamını tanımlayın.

4. Özet sekmesinde ayrıntıları gözden geçirin ve Kaydet'e **tıklayın**.

## <a name="related-topics"></a>İlgili konular

- [Gösterge oluşturma](manage-indicators.md)
- [Dosyalar için göstergeler oluşturma](indicator-file.md)
- [URL'ler ve URL'ler/etki alanları için göstergeler oluşturma](indicator-ip-domain.md)
- [Göstergeleri yönetme](indicator-manage.md)
