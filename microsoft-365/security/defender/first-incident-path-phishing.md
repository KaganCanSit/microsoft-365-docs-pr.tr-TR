---
title: Kimlik avı e-posta saldırısı örneği
description: Kimlik avı saldırısının örnek çözümlemesinde adım adım ilerler.
keywords: olaylar, uyarılar, araştırma, korelasyon, saldırı, makineler, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, microsoft, m365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 413c4fadcc6de3527643be712713d37a1e2c346c
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64501145"
---
# <a name="example-of-a-phishing-email-attack"></a>Kimlik avı e-posta saldırısı örneği

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Microsoft 365 Defender e-postayla teslim edilen kötü amaçlı ekleri algılamaya yardımcı olabilir. Güvenlik [Office 365 Uyumluluk](https://protection.office.com/) Merkezi Microsoft 365 Defender ile tümleştirilerinden, güvenlik analistleri e-posta ekleri gibi Office 365'ten gelen tehditlere karşı görünürlük sağlar.

Örneğin, bir analiste çok aşamalı bir olay atanmıştır.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-incident.png" alt-text="Çok aşamalı bir olay" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-incident.png":::

Olayın **Uyarılar** sekmesinde, Posta ve Posta Office 365 için Defender Microsoft Defender for Cloud Apps görüntülenir. Analist, e-posta iletileri Office 365 için Defender seçerek en son uyarıların ayrıntıya iner. Uyarının ayrıntıları yan bölmede görüntülenir.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-alerts.png" alt-text="E-posta uyarısı" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-alerts.png":::
 
Daha fazla bilgi ekranı aşağı kaydırarak, kötü amaçlı dosyalar ve etkileniyor olan kullanıcı gösterilir.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-impact.png" alt-text="E-posta uyarısının kullanıcı ve dosya üzerindeki etkisi" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-impact.png":::
  
Uyarı sayfasını **aç'ı** seçmek, bağlantıyı seçerek sizi çeşitli bilgilerin daha ayrıntılı görüntül olduğu belirli bir uyarıya alır. Asıl e-posta iletisi, panelin alt kısmında **Gezgin'de iletileri** görüntüle seçerek ekleyebilirsiniz.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-event-explorer.png" alt-text="Uyarının ayrıntıları" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-event-explorer.png"::: 

Bu, analisti E-posta Konusu, Alıcı, Gönderen ve diğer bilgilerin görüntülendiğinde Tehdit Yönetimi sayfasına alır. **Özel** Eylemler **altındaki** ZAP, analiste Sıfır saatlik otomatik temizleme özelliğinin uygulanmasını söyler. ZAP, kuruluş genelindeki posta kutularında yer alan kötü amaçlı ve istenmeyen iletileri otomatik olarak algılar ve kaldırır. Daha fazla bilgi için bkz[. Saat içinde Sıfır saatlik otomatik temizleme (ZAP) Exchange Online](../office-365-security/zero-hour-auto-purge.md).

Eylemler seçerek belirli iletiler üzerinde başka eylemler de **gerçekleştirebilirsiniz**. 
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-actions.png" alt-text="E-posta iletileri üzerinde 7/2" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-actions.png"::: 

## <a name="next-step"></a>Sonraki adım

Kimlik tabanlı [saldırı araştırma yoluna](first-incident-path-identity.md) bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Olaylara genel bakış](incidents-overview.md)
- [Olayları araştırın](investigate-incidents.md)
- [Olayları yönetin](manage-incidents.md)
