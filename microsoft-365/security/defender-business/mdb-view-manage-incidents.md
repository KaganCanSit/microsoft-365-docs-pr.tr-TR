---
title: İş için Microsoft Defender'da olayları görüntüleme ve yönetme
description: Uyarıları görüntülemeyi & yönetmeyi, tehditlere yanıt vermeyi, cihazları yönetmeyi ve düzeltme eylemlerini gözden geçirmeyi öğrenin
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
ms.openlocfilehash: ec1d85b72cfbe17e182d3aed573476e4fadfdef6
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64861454"
---
# <a name="view-and-manage-incidents-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'da olayları görüntüleme ve yönetme

> [!NOTE]
> İş için Microsoft Defender artık [Microsoft 365 İş Ekstra](../../business-premium/index.md) dahil edilir. 

Tehditler algılandığında ve uyarılar tetiklendiğinde olaylar oluşturulur. Şirketinizin güvenlik ekibi olayları Microsoft 365 Defender portalında görüntüleyebilir ve yönetebilir.

**Bu makale şunları içerir**:

- [Olaylarınızı ve uyarılarınızı izleme](#monitor-your-incidents--alerts)
- [Uyarı önem derecesi](#alert-severity)
- [Sonraki adımlar](#next-steps)

>
> **Bir dakikan var mı?**
> Lütfen <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">güvenlikle ilgili kısa anketimize</a> katılın. Sizden haber almak isteriz!
>

## <a name="monitor-your-incidents--alerts"></a>Olaylarınızı & uyarılarınızı izleme

1. Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com) ) gezinti bölmesinde **Olaylar'ı** seçin. Oluşturulan tüm olaylar sayfada listelenir.

   :::image type="content" source="../../media/defender-business/mdb-incidents-list.png" alt-text="Olaylar listesinin ekran görüntüsü":::

2. Uyarı hakkında daha fazla bilgi edinebileceğiniz açılır pencere bölmesini açmak için bir uyarı seçin. 

   :::image type="content" source="../../media/defender-business/mdb-incident-flyout.png" alt-text="Açılır öğe açıkken seçilen olayın ekran görüntüsü":::

3. Açılır bölmede uyarı başlığını görebilir, etkilenen varlıkların (uç noktalar veya kullanıcı hesapları gibi) listesini görüntüleyebilir, kullanılabilir eylemler gerçekleştirebilir ve daha fazla bilgi görüntülemek ve hatta seçili uyarının ayrıntılar sayfasını açmak için bağlantıları kullanabilirsiniz. 

> [!TIP]
> İş için Microsoft Defender, önerilen eylemleri sunarak algılanan tehditleri gidermenize yardımcı olmak için tasarlanmıştır. Bir uyarıyı görüntülediğinizde, yapılması önerilen eylemleri arayın. Ayrıca, yalnızca tehdit önem derecesine değil, aynı zamanda şirketiniz için risk düzeyine göre belirlenen uyarı önem derecesini de not edin. 

## <a name="alert-severity"></a>Uyarı önem derecesi

Microsoft Defender Virüsten Koruma algılanan tehdidin (kötü amaçlı yazılım) mutlak önem derecesine ve tek bir uç noktaya (virüs bulaşmışsa) olası riski temel alan bir uyarı önem derecesi atadığında.
İş için Microsoft Defender algılanan davranışın önem derecesine, bir uç noktaya (cihaza) gerçek risk ve daha da önemlisi şirketiniz için olası risk temelinde bir uyarı önem derecesi atar. Aşağıdaki tabloda birkaç örnek verilmiştir:

| Senaryo | Uyarı önem derecesi | Neden |
|:---|:---|:---|
| Microsoft Defender Virüsten Koruma herhangi bir hasara neden olmadan önce bir tehdidi algılar ve durdurur. | Bilgi | Herhangi bir hasar verilmeden önce tehdit durduruldu. |
| Microsoft Defender Virüsten Koruma, şirketinizde yürütülen kötü amaçlı yazılımları algılar. Kötü amaçlı yazılım durduruldu ve düzeltildi. | Düşük | Tek bir uç noktaya zarar verilmiş olsa da, kötü amaçlı yazılım artık şirketiniz için bir tehdit oluşturmaz. |
| Yürütülen kötü amaçlı yazılımlar İş için Microsoft Defender tarafından algılanır. Kötü amaçlı yazılım neredeyse hemen engellenir. | Orta veya Yüksek | Kötü amaçlı yazılım, tek tek uç noktalar ve şirketiniz için bir tehdit oluşturur. |
| Şüpheli davranış algılanır ancak henüz düzeltme işlemi yapılmaz. | Düşük, Orta veya Yüksek | Önem derecesi, davranışın şirketiniz için tehdit oluşturma derecesine bağlıdır. |

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender'da tehditlere yanıt verme ve tehditleri azaltma](mdb-respond-mitigate-threats.md)
- [İşlem merkezindeki düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)
- [İş için Microsoft Defender'de cihaz ilkelerini görüntüleme veya düzenleme](mdb-view-edit-policies.md)