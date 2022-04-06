---
title: Düzeltme eylemlerini gözden Microsoft 365 İş Ekstra
description: İşlem merkezinde otomatik olarak alınan veya onay bekleyen düzeltmelerin nasıl görüntü gerektirilir
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 160cef2ec7691fbc9debad809b20461a0d3efe23
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705542"
---
# <a name="review-remediation-actions-in-microsoft-365-business-premium"></a>Düzeltme eylemlerini gözden Microsoft 365 İş Ekstra

Tehdit algılandığında düzeltme eylemleri ortaya çıktı. Belirli tehdide ve güvenlik ayarlarınızın nasıl yapılandırılana bağlı olarak, düzeltme eylemleri otomatik olarak veya yalnızca onay üzerine gerçek olabilir. Düzeltme eylemlerine örnek olarak, dosyayı karantinaya gönderme, bir işlemi çalıştırmayı durdurma ve zamanlanmış görevi kaldırma işlemleri örnek olarak verilmiştir. Tüm düzeltme eylemleri, üzerinde yer alan İşlem merkezinde izlenr.[https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)

:::image type="content" source="../media/defender-business/mdb-actioncenter.png" alt-text="M365'te İşlem Merkezi'nin ekran görüntüsü.":::

**Bu makalede şu açıklanmıştır**:

- [İşlem merkezini kullanma](#how-to-use-your-action-center)

- [Düzeltme eylemi türleri](#types-of-remediation-actions)


## <a name="how-to-use-your-action-center"></a>İşlem merkezinizi kullanma

1. Microsoft 365 Defender portalına () gidin[https://security.microsoft.com](https://security.microsoft.com) ve oturum açın.

2. Gezinti bölmesinde İşlem **merkezi'ni seçin**.

3. Bekleyen eylemleri **görüntülemek** ve onaylamak (veya reddetmek) için Beklemede sekmesini seçin. Bu tür eylemler virüsten koruma/kötü amaçlı yazılımlardan koruma, otomatik soruşturmalar, el ile yanıt etkinlikleri veya canlı yanıt oturumlarından oluşabilir.

4. Tamamlanmış **eylemlerin** listesini görüntülemek için Geçmiş sekmesini seçin. 

## <a name="types-of-remediation-actions"></a>Düzeltme eylemi türleri

Aboneliğiniz, algılanan tehditlere yönelik çeşitli düzeltme eylemleri içerir. Bu eylemler, el ile yanıt eylemlerini, otomatik soruşturmayı takip eden eylemleri ve canlı yanıt eylemlerini içerir.

Aşağıdaki tabloda, kullanılabilir düzeltme eylemleri listele:

| Kaynak  | Eylemler  |
|---------|---------|
| [Otomatik soruşturmalar](../security/defender-endpoint/automated-investigations.md)      | - Dosyayı karantinaya alın <br/>- Kayıt defteri anahtarını kaldırma <br/>- Süreci kill <br/>- Hizmeti durdurma <br/>- Sürücüyü devre dışı bırakma <br/>- Zamanlanmış görevi kaldırma        |
| [El ile yanıt eylemleri](../security/defender-endpoint/respond-machine-alerts.md)   | - Virüsten koruma taraması çalıştırma <br/>- Cihazı yalıt <br/>- Durdurma ve karantina <br/>- Dosyayı engellemek veya dosyaya izin vermek için bir gösterge ekleyin       |
| [Canlı yanıt](../security/defender-endpoint/live-response.md)   | - Bilgi toplama <br/>- Dosyayı çözümleme <br/>- Betik çalıştırma <br/>- Çözümleme için Microsoft'a şüpheli bir varlık gönderin <br/>- Dosyayı düzeltme <br/>- Tehditlere karşı önceden önlem almak         |
