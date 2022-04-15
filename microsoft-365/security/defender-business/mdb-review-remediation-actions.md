---
title: İş için Microsoft Defender'de düzeltme eylemlerini gözden geçirme
description: otomatik olarak alınan veya İşlem merkezinde onay bekleyen düzeltmeleri görüntüleme
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 15a64491f6e97137d1e919aa126d4bf134c47999
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862224"
---
# <a name="review-remediation-actions-in-the-action-center"></a>İşlem merkezindeki düzeltme eylemlerini gözden geçirme

> [!NOTE]
> İş için Microsoft Defender artık [Microsoft 365 İş Ekstra](../../business-premium/index.md) dahil edilir. 

Tehditler algılandıkçe düzeltme eylemleri devreye girer. Belirli bir tehdide ve güvenlik ayarlarınızın nasıl yapılandırıldığına bağlı olarak, düzeltme eylemleri otomatik olarak veya yalnızca onaylandığında gerçekleştirilebilir. Karantinaya dosya gönderme, işlemin çalışmasını durdurma ve zamanlanmış görevi kaldırma gibi düzeltme eylemlerine örnek olarak verilebilir. Tüm düzeltme eylemleri İşlem merkezinde izlenir.

:::image type="content" source="../../media/defender-business/mdb-actioncenter.png" alt-text="İşlem merkezinin ekran görüntüsü":::

**Bu makalede şunlar açıklanmaktadır**:

- [İşlem merkezini kullanma](#how-to-use-the-action-center)
- [Düzeltme eylemleri](#remediation-actions)

>
> **Bir dakikan var mı?**
> Lütfen <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">güvenlikle ilgili kısa anketimize</a> katılın. Sizden haber almak isteriz!
>

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