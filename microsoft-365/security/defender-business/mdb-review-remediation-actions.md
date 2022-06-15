---
title: İş için Microsoft Defender'de düzeltme eylemlerini gözden geçirme
description: İş için Defender ile algılanan tehditlere karşı alınan düzeltmeleri görüntüleyin. eylemleri Microsoft 365 Defender portalındaki İşlem merkezinde görüntüleyebilirsiniz.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 5c73b840b127770c4581dda4d03b3c95066df515
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66089538"
---
# <a name="review-remediation-actions-in-the-action-center"></a>İşlem merkezindeki düzeltme eylemlerini gözden geçirme

Tehditler algılandıkçe düzeltme eylemleri devreye girer. Belirli bir tehdide ve güvenlik ayarlarınızın nasıl yapılandırıldığına bağlı olarak, düzeltme eylemleri otomatik olarak veya yalnızca onaylandığında gerçekleştirilebilir. Karantinaya dosya gönderme, işlemin çalışmasını durdurma ve zamanlanmış görevi kaldırma gibi düzeltme eylemlerine örnek olarak verilebilir. Tüm düzeltme eylemleri İşlem merkezinde izlenir.

:::image type="content" source="../../media/defender-business/mdb-actioncenter.png" alt-text="İşlem merkezinin ekran görüntüsü":::

**Bu makalede şunlar açıklanmaktadır**:

- [İşlem merkezini kullanma](#how-to-use-the-action-center)
- [Düzeltme eylemleri](#remediation-actions)


## <a name="how-to-use-the-action-center"></a>İşlem merkezini kullanma

1. Microsoft 365 Defender portalına ()[https://security.microsoft.com](https://security.microsoft.com) gidin ve oturum açın.

2. Gezinti bölmesinde **İşlem merkezi'ni** seçin.

3. Bekleyen eylemleri görüntülemek ve onaylamak (veya reddetmek) için **Beklemede** sekmesini seçin. Bu tür eylemler virüsten koruma/kötü amaçlı yazılımdan koruma, otomatik araştırma, el ile yanıt etkinlikleri veya canlı yanıt oturumlarından kaynaklanabilir.

4. Tamamlanan eylemlerin listesini görüntülemek için **Geçmiş** sekmesini seçin. 

## <a name="remediation-actions"></a>Düzeltme eylemleri

İş için Microsoft Defender çeşitli düzeltme eylemleri içerir. Bu eylemler el ile yanıt eylemlerini, otomatik araştırmadan sonraki eylemleri ve canlı yanıt eylemlerini içerir.

Aşağıdaki tabloda, kullanılabilen düzeltme eylemleri listelenir:

| Kaynak  | Eylem  |
|---------|---------|
| [Otomatik araştırma](../defender-endpoint/automated-investigations.md)      | - Dosyayı karantinaya al <br/>- Kayıt defteri anahtarını kaldırma <br/>- Bir işlemi sonlandırma <br/>- Hizmeti durdurma <br/>- Sürücüyü devre dışı bırakma <br/>- Zamanlanmış görevi kaldırma        |
| [El ile yanıt eylemleri](../defender-endpoint/respond-machine-alerts.md)   | - Virüsten koruma taraması çalıştırma <br/>- Cihazı yalıtma <br/>- Durdurma ve karantinaya al <br/>- Bir dosyayı engellemek veya dosyaya izin vermek için gösterge ekleme       |
| [Canlı yanıt](../defender-endpoint/live-response.md)   | - Adli veri toplama <br/>- Bir dosyayı analiz etme <br/>- Betik çalıştırma <br/>- Şüpheli bir varlığı analiz için Microsoft'a gönderme <br/>- Dosyayı düzeltme <br/>- Tehditleri proaktif olarak avlama         |

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender'da tehditlere yanıt verme ve tehditleri azaltma](mdb-respond-mitigate-threats.md)
- [İş için Microsoft Defender'de cihazları yönetme](mdb-manage-devices.md)