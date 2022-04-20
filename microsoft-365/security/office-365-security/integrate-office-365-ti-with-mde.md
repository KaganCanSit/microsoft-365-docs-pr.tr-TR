---
title: Office 365 için Microsoft Defender'ın Uç Nokta için Microsoft Defender ile birlikte kullanılması
f1.keywords:
- NOCSH
keywords: integrate, Microsoft Defender, Uç Nokta için Microsoft Defender
ms.author: deniseb
author: denisebmsft
manager: dansimp
ms.date: 12/02/2021
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
description: Cihazlarınıza ve e-posta içeriğinize yönelik tehditler hakkında daha ayrıntılı bilgi edinmek için Office 365 için Microsoft Defender'ı Uç Nokta için Microsoft Defender ile birlikte kullanın.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8df364538e6a799557956a8d624b0561c626e4fd
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971120"
---
# <a name="use-microsoft-defender-for-office-365-together-with-microsoft-defender-for-endpoint"></a>Office 365 için Microsoft Defender'ın Uç Nokta için Microsoft Defender ile birlikte kullanılması

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

[Office 365 için Microsoft Defender, Uç Nokta için Microsoft Defender](defender-for-office-365.md) ile çalışacak şekilde yapılandırılabilir.[](/windows/security/threat-protection)

Office 365 için Microsoft Defender'ı Uç Nokta için Microsoft Defender ile tümleştirmek, güvenlik operasyonları ekibinizin kullanıcıların cihazları risk altındaysa hızlı bir şekilde izlemenize ve harekete geçmenize yardımcı olabilir. Örneğin, tümleştirme etkinleştirildikten sonra güvenlik operasyonları ekibiniz algılanan bir e-posta iletisinden etkilenmiş olabilecek cihazları ve bu cihazlar için Uç Nokta için Microsoft Defender'de oluşturulan son uyarıları görebilir.

Aşağıdaki görüntüde **, Uç Nokta için Microsoft Defender** tümleştirme etkinleştirildiğinde Cihazlar sekmesinin nasıl göründüğü gösterilir:

:::image type="content" source="../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG" alt-text="Uyarı içeren cihazların listesi" lightbox="../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG":::

Bu örnekte, algılanan e-posta iletisinin alıcılarının dört cihazı olduğunu ve birinin uyarı içerdiğini görebilirsiniz. Bir cihazın bağlantısına tıklanması[, Microsoft 365 Defender portalında](/microsoft-365/security/defender/microsoft-365-defender) sayfasını açar.

> [!TIP]
> Microsoft 365 Defender portalı Microsoft Defender Güvenlik Merkezi yerini alır. [bkz. Microsoft 365 Defender'da Uç Nokta için Microsoft Defender](../defender/microsoft-365-security-center-mde.md).

## <a name="requirements"></a>Gereksinimler

- Kuruluşunuzun Office 365 (veya Office 365 E5) ve Uç Nokta için Microsoft Defender için Microsoft Defender'a sahip olması gerekir.

- Microsoft 365'de genel yönetici veya güvenlik yöneticisi rolü atanmış olmalıdır. Daha fazla bilgi için bkz. [Microsoft 365 Defender portalında İzinler](permissions-microsoft-365-security-center.md).

- [Gezgin'e (veya gerçek zamanlı algılamalara)](threat-explorer.md) erişiminiz olmalıdır.

## <a name="to-integrate-microsoft-defender-for-office-365-with-microsoft-defender-for-endpoint"></a>Office 365 için Microsoft Defender'ı Uç Nokta için Microsoft Defender ile tümleştirmek için

Office 365 için Microsoft Defender'ı Uç Nokta için Microsoft Defender ile tümleştirmek hem Uç Nokta için Defender hem de Office 365 için Defender'da ayarlanır.

1. Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com)) gidin ve oturum açın.

2. **E-posta & işbirliği** \> **Gezgini'ne** gidin.

3. **Gezgin** sayfasında, ekranın sağ üst köşesinde **MDE Ayarlar'i** seçin.

3. Görüntülenen **Uç Nokta için Microsoft Defender bağlantı** açılır penceresinde **, Uç Nokta için Microsoft Defender Bağlan** açın (![Aç/kapat](../../media/scc-toggle-on.png))**'ı seçin**.

   :::image type="content" source="../../media/explorer-mdeconnection-dialognew.png" alt-text="MDE Bağlantısı sayfası" lightbox="../../media/explorer-mdeconnection-dialognew.png":::

4. Gezinti bölmesinde **Ayarlar'yi** seçin. **Ayarlar** sayfasında **Uç Noktalar'ı** seçin

5. Açılan **Uç Noktalar** sayfasında **Gelişmiş özellikler'i** seçin.

6. **Office 365 Tehdit Bilgileri bağlantısına** kadar aşağı kaydırın ve açın (![Açık.](../../media/scc-toggle-on.png)).

   İşiniz bittiğinde **Tercihleri kaydet'i** seçin.

## <a name="see-also"></a>Ayrıca bkz.

[Office 365'de tehdit araştırma ve yanıt özellikleri](office-365-ti.md)

[Office 365 için Microsoft Defender](defender-for-office-365.md)

[Uç Nokta için Microsoft Defender](/windows/security/threat-protection)
