---
title: Uç nokta için Microsoft Defender ile Office 365 için Microsoft Defender'ı kullanma
f1.keywords:
- NOCSH
keywords: integrate, Microsoft Defender, Endpoint için Microsoft Defender
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
description: Cihazlarınıza ve e-Office 365 yönelik tehditlerle ilgili daha ayrıntılı bilgi almak için Microsoft Defender for Endpoint ile birlikte Microsoft Defender'ı kullanın.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 67406984e73f39858f4a7329a8c8520fcd35ac5c
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027482"
---
# <a name="use-microsoft-defender-for-office-365-together-with-microsoft-defender-for-endpoint"></a>Uç nokta için Microsoft Defender ile Office 365 için Microsoft Defender'ı kullanma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


[Uygulama için Microsoft Defender Office 365](defender-for-office-365.md) Uç Nokta için [Microsoft Defender ile çalışacak şekilde yalıtıldı](/windows/security/threat-protection).

Mobil cihazlar için Microsoft Defender Office 365 uç nokta için Microsoft Defender ile tümleştirin, güvenlik işlemleri ekibinin, kullanıcıların cihazları risk altında olduğu zaman hızlı bir şekilde izlemesi ve önlem almalarına yardımcı olabilir. Örneğin, tümleştirme etkinleştirildikten sonra, güvenlik işlemleri takımınız algılanan e-posta iletisiden etkilenme olasılığı olan cihazları ve uç nokta için Microsoft Defender'da bu cihazlar için ne kadar yeni uyarı üretlendiğini görebilir.

Aşağıdaki resimde, Uç nokta tümleştirmesi **için** Microsoft Defender etkinleştirildiğinde Cihazlar sekmesinin nasıl göründüğünü görebilirsiniz:

![Uç Nokta için Microsoft Defender etkinleştirildiğinde, uyarılara sahip cihazların listesini seçebilirsiniz.](../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG)

Bu örnekte, algılanan e-posta iletisi alıcılarının dört cihazı olduğunu ve birinin de uyarı olduğunu görüyoruz. Bir cihazın bağlantısına tıklarsanız, cihaz sayfası Microsoft 365 Defender [açılır](/microsoft-365/security/defender/microsoft-365-defender).

> [!TIP]
> Portal Microsoft 365 Defender, yeni portalın Microsoft Defender Güvenlik Merkezi. Bkz. [Microsoft 365 Defender'de Uç Nokta için Microsoft Defender](../defender/microsoft-365-security-center-mde.md).

## <a name="requirements"></a>Gereksinimler

- Kuruluşta Kimlik Için Microsoft Defender (veya Office 365) ve Uç Office 365 E5 için Microsoft Defender olmalıdır.

- Bu kuruluşta ya genel yönetici veya güvenlik yöneticisi rolünün atanmış Microsoft 365. Daha fazla bilgi için bkz[. Microsoft 365 Defender portalına.](permissions-microsoft-365-security-center.md)

- Gezgin'e [erişiminiz (veya gerçek zamanlı algılamalar) olması gerekir](threat-explorer.md).

## <a name="to-integrate-microsoft-defender-for-office-365-with-microsoft-defender-for-endpoint"></a>Microsoft Defender for Endpoint ile Office 365 için Microsoft Defender'ı tümleştirin

Windows için Microsoft Defender'Office 365 Uç Nokta için Microsoft Defender ile tümleştirme, hem Uç Nokta için Defender'da hem de Uç Nokta için Defender'da Office 365.

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.

2. E-posta **ve & Gezgini'ne** \> **gidin**. 

3. Gezgin **sayfasında**, ekranın sağ üst köşesinde **MDE Arama Çubuğu'Ayarlar**.

3. Görüntülenen Uç Nokta **bağlantısı için Microsoft Defender** açılır öğesini, Uç Nokta Bağlan **Için Microsoft Defender'ı** açıp![](../../media/scc-toggle-on.png) Kapat'ı **seçin**.

    :::image type="content" source="../../media/explorer-mdeconnection-dialognew.png" alt-text="MDE Bağlantısı.":::

4. Gezinti bölmesinde, **Tamam'ı Ayarlar**. Sayfa Son **Ayarlar** Uç **Noktalar'ı seçin**

5. Açılan **Uç Noktalar** sayfasında Gelişmiş özellikler'i **seçin**.

6. Tehdit İstihbaratı **Office 365'e** kadar aşağı kaydırın ve bu bağlantıyı açık olarak seçin (![Aç/kapat).](../../media/scc-toggle-on.png)

   Bitirdikten sonra, Kaydetme **tercihleri'ne tıklayın**.

## <a name="see-also"></a>Ayrıca bkz.

[Yeni bir tehdit soruşturması ve yanıt Office 365](office-365-ti.md)

[Office 365 için Microsoft Defender](defender-for-office-365.md)

[Uç Nokta için Microsoft Defender](/windows/security/threat-protection)
