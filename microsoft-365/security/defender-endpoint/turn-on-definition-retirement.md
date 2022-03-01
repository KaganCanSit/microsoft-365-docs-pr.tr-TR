---
title: Emeklilik için tanımın sonlarını Microsoft Defender Virüsten Koruma
description: Emeklilik için tanımın sonlarını Microsoft Defender Virüsten Koruma.
keywords: Microsoft Defender Virüsten Koruma, kötü amaçlı yazılımdan koruma, güvenlik, defender, tanım emeklilik
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.date: 06/10/2021
ms.reviewer: ''
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.collection: m365-security-compliance
ms.openlocfilehash: dd9cd313dec962547acef85c6da326d3b6e5c58f
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997486"
---
# <a name="turn-on-definition-retirement"></a>Tanımın sonlarını kapatma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Grup İlkesi'yi kullanarak tanımın emeklilikni yapılandırsanız. Tanımın emeklilik, bilgisayarın belirli bir güvenlik açığına karşı korunması için gerekli güvenlik güncelleştirmelerine sahip olup olduğunu denetler. Sistem, bir tanım tarafından algılanan açıktan yararlanmaya açık değilse, bu tanım "kaldırıldı" olur. Verilen protokolün tüm güvenlik zekası kaldırıldısa, bu protokol artık ayrıştırıcı olmaz. Bu özelliğin etkinleştirilmesi, performansı artırmaya yardımcı olur. En son güvenlik güncelleştirmelerinin hepsiyle birlikte güncel olan bir bilgisayarda, ağ korumasının ağ performansı üzerinde hiçbir etkisi olmaz.

## <a name="use-group-policy-to-configure-definition-retirement"></a>Kullanımdan kullanımdan kullanım tanımını yapılandırmak için Grup İlkesi kullanma

1. Grup İlkesi yönetim uç noktanız üzerinde, Grup İlkesi [Yönetim Konsolu'nu açın](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Ağ İnceleme **Sistemi için** \> **Bilgisayar Yapılandırması Windows** \> **Bileşenleri** **Microsoft Defender Virüsten Koruma'e** \> \> gidin.

3. Tanımın **emeklilik için aç'ı seçin**. Varsayılan olarak, bu ilke etkindir. Yapılandırılmadı **olarak ayarlanırsa**, tanımın emeklilik etkinleştirilir.

4. İlkeyi düzenlemek için, ilke **ayarını düzenle bağlantısını** seçin.

5. **Etkin'i** ve sonra Tamam'ı **seçin**.

6. Güncelleştirilmiş Grup İlkesi Nesnenizi dağıtın. Bkz [. Grup İlkesi Yönetim Konsolu](/windows/win32/srvnodes/group-policy).

> [!TIP]
> Şirket içinde Grup İlkesi Nesneleri mi kullanıyorsunuz? Buluttaki çevirinin nasıl olduğunu öğrenin. [Grup İlkesi çözümlemesini kullanarak şirket içi grup ilkesi nesnelerinizi Çözümleme - Microsoft Endpoint Manager.](/mem/intune/configuration/group-policy-analytics)
