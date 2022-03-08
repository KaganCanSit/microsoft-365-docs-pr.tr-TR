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
ms.openlocfilehash: 112bfd63a5f3667b22378790b62f3e33fba784d6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320305"
---
# <a name="example-of-a-phishing-email-attack"></a>Kimlik avı e-posta saldırısı örneği

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Microsoft 365 Defender e-postayla teslim edilen kötü amaçlı ekleri algılamaya yardımcı olabilir. Güvenlik [Office 365 Uyumluluk](https://protection.office.com/) Merkezi Microsoft 365 Defender ile tümleştirilerinden, güvenlik analistleri e-posta ekleri gibi Office 365'ten gelen tehditlere karşı görünürlük sağlar.

Örneğin, bir analiste çok aşamalı bir olay atanmıştır.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-incident.png" alt-text="Çok aşamalı bir olay örneği."::: 

Olayın **Uyarılar sekmesinde**, Office 365 için Defender ve Bulut Uygulamaları için Microsoft Defender uyarıları görüntülenir. Analist, e-posta iletileri uyarılarını seçerek Office 365 Defender hakkında detaya gitmenizi sağlar. Uyarının ayrıntıları yan bölmede görüntülenir.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-alerts.png" alt-text="E-posta uyarısı örneği.":::
 
Daha fazla bilgi ekranı aşağı kaydırarak, kötü amaçlı dosyalar ve etkileniyor olan kullanıcı gösterilir.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-impact.png" alt-text="Kullanıcı ve e-posta uyarısının dosya üzerindeki etkisi örneği.":::
  
Uyarı sayfasını **aç'ı** seçmek, bağlantıyı seçerek sizi çeşitli bilgilerin daha ayrıntılı görüntül olduğu belirli bir uyarıya alır. Asıl e-posta iletisi, panelin alt kısmında **Gezgin'de iletileri** görüntüle seçerek ekleyebilirsiniz.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-event-explorer.png" alt-text="Uyarının ayrıntıları örneği."::: 

Bu, analisti E-posta Konusu, Alıcı, Gönderen ve diğer bilgilerin görüntülendiğinde Tehdit Yönetimi sayfasına alır. **Özel** Eylemler **altındaki** ZAP, analiste Sıfır saatlik otomatik temizleme özelliğinin uygulanmasını söyler. ZAP, kuruluş genelindeki posta kutularında yer alan kötü amaçlı ve istenmeyen iletileri otomatik olarak algılar ve kaldırır. Daha fazla bilgi için bkz[. Saat içinde Sıfır saatlik otomatik temizleme (ZAP) Exchange Online](../office-365-security/zero-hour-auto-purge.md).

Eylemler seçerek belirli iletiler üzerinde başka eylemler de **gerçekleştirebilirsiniz**. 
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-actions.png" alt-text="E-posta iletisinde diğer eylemlerin örneği."::: 

## <a name="next-step"></a>Sonraki adım

Kimlik tabanlı [saldırı araştırma yoluna](first-incident-path-identity.md) bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Olaylara genel bakış](incidents-overview.md)
- [Olayları araştırma](investigate-incidents.md)
- [Olayları yönetme](manage-incidents.md)
