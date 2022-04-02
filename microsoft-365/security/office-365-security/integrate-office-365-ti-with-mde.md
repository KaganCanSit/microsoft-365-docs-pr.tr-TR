---
title: Office 365 için Microsoft Defender ile birlikte Uç Nokta için Microsoft Defender
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
description: Cihazlarınıza Office 365 için Microsoft Defender ve e Uç Nokta için Microsoft Defender içeriğinize yönelik tehditlerle ilgili daha ayrıntılı bilgi almak için diğer e-posta adresleriyle birlikte Bu İletişim'i kullanın.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ef1f89a9b218e559855789d0beabad1bc947dad1
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465937"
---
# <a name="use-microsoft-defender-for-office-365-together-with-microsoft-defender-for-endpoint"></a>Office 365 için Microsoft Defender ile birlikte Uç Nokta için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


[Office 365 için Microsoft Defender](defender-for-office-365.md), diğerleriyle birlikte çalışacak şekilde [Uç Nokta için Microsoft Defender](/windows/security/threat-protection).

Kullanıcıların Office 365 için Microsoft Defender risk altında Uç Nokta için Microsoft Defender, güvenlik işlemleri ekibinin izlemesi ve hızlı bir şekilde işlemde yer almalarına yardımcı olabilir. Örneğin, tümleştirme etkinleştirildikten sonra, güvenlik işlemleri ekipleri algılanan bir e-posta iletisiden etkilenme olasılığı olan cihazları ve bu cihazlar için Uç Nokta için Microsoft Defender'te yeni uyarıların oluşturularak bu cihazları görebilir.

Aşağıdaki resimde, tümleştirmeyi **etkinleştirmiş durumdayken** Cihazlar sekmesinin Uç Nokta için Microsoft Defender görünür:

:::image type="content" source="../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG" alt-text="Uyarılı cihazların listesi" lightbox="../../media/fec928ea-8f0c-44d7-80b9-a2e0a8cd4e89.PNG":::

Bu örnekte, algılanan e-posta iletisi alıcılarının dört cihazı olduğunu ve birinin de uyarı olduğunu görüyoruz. Bir cihazın bağlantısına tıklarsanız, cihaz sayfası Microsoft 365 Defender [açılır](/microsoft-365/security/defender/microsoft-365-defender).

> [!TIP]
> Portal Microsoft 365 Defender, yeni portalın Microsoft Defender Güvenlik Merkezi. Bkz[. Uç Nokta için Microsoft Defender'da Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md).

## <a name="requirements"></a>Gereksinimler

- Kuruluş, e-Office 365 için Microsoft Defender (veya Office 365 E5) ve Uç Nokta için Microsoft Defender.

- Bu kuruluşta ya genel yönetici veya güvenlik yöneticisi rolünün atanmış Microsoft 365. Daha fazla bilgi için bkz[. Microsoft 365 Defender portalına.](permissions-microsoft-365-security-center.md)

- Gezgin'e [erişiminiz (veya gerçek zamanlı algılamalar) olması gerekir](threat-explorer.md).

## <a name="to-integrate-microsoft-defender-for-office-365-with-microsoft-defender-for-endpoint"></a>E-Office 365 için Microsoft Defender Uç Nokta için Microsoft Defender

Varsayılan Office 365 için Microsoft Defender Uç Nokta için Microsoft Defender uç nokta için Defender ve Diğer Uç Nokta'da Office 365 için Defender.

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.

2. E-posta **ve & Gezgini'ne** \> **gidin**. 

3. Gezgin **sayfasında**, ekranın sağ üst köşesinde **MDE Arama Çubuğu'Ayarlar**.

3. Görüntülenen **Uç Nokta için Microsoft Defender bağlantı** açılır öğesini seçin, Geçiş Bağlan **Uç Nokta için Microsoft Defender**![](../../media/scc-toggle-on.png)) seçeneğini açıp Kapat'ı **seçin**.

   :::image type="content" source="../../media/explorer-mdeconnection-dialognew.png" alt-text="MDE Bağlantısı sayfası" lightbox="../../media/explorer-mdeconnection-dialognew.png":::

4. Gezinti bölmesinde, **Tamam'ı Ayarlar**. Sayfa Son **Ayarlar** Uç **Noktalar'ı seçin**

5. Açılan **Uç Noktalar** sayfasında Gelişmiş özellikler'i **seçin**.

6. Tehdit İstihbaratı **Office 365'e** kadar aşağı kaydırın ve bu bağlantıyı açık olarak seçin (![Aç/kapat).](../../media/scc-toggle-on.png)

   Bitirdikten sonra, Kaydetme **tercihleri'ne tıklayın**.

## <a name="see-also"></a>Ayrıca bkz.

[Yeni bir tehdit soruşturması ve yanıt Office 365](office-365-ti.md)

[Office 365 için Microsoft Defender](defender-for-office-365.md)

[Uç Nokta için Microsoft Defender](/windows/security/threat-protection)
