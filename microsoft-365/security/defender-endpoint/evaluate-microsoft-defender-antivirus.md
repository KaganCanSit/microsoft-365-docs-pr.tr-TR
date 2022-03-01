---
title: Değerlendirme Microsoft Defender Virüsten Koruma
description: Her boyuttaki işletmeler, bu kılavuzu kullanarak işletmeniz tarafından sunulan korumayı Microsoft Defender Virüsten Koruma test Windows.
keywords: Microsoft Defender Virüsten Koruma, bulut koruması, bulut, kötü amaçlı yazılımdan koruma, güvenlik, defender, değerlendirme, test, koruma, karşılaştırma, gerçek zamanlı koruma
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 4dd25a599f144a60bfd2ebeb3e9bb8b1876bd3c6
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015219"
---
# <a name="evaluate-microsoft-defender-antivirus"></a>Değerlendirme Microsoft Defender Virüsten Koruma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

Virüslere, kötü amaçlı yazılımlara Microsoft Defender Virüsten Koruma ve istenmeyen uygulamalara karşı ne kadar iyi koruma olduğunu belirlemek için bu kılavuzu kullanın.

> [!TIP]
>Ayrıca aşağıdaki özelliklerin çalıştığını onaylamak ve nasıl çalıştığını görmek için [demo.wd.microsoft.com'de](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) Uç nokta için Microsoft Defender tanıtım web sitesini ziyaret edebilirsiniz:
>
> - Bulut teslimi koruma
> - Hızlı öğrenme (ilk görüşte engelle dahil)
> - İstenmeyen bir uygulama engellemesi olabilir

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

Hem küçük hem de büyük işletmeler için Microsoft Defender Virüsten Koruma yeni nesil koruma özelliklerinin ve bunların ağ üzerinde kötü amaçlı yazılım algılama ve korumayı nasıl artıracaklarını açıklar.

Her ayarı bağımsız olarak veya hepsini bir kerede yapılandırmayı ve değerlendirmeyi seçebilirsiniz. Genel değerlendirme senaryolarına dayalı olarak benzer ayarları gruplamız ve ayarları etkinleştirmek için PowerShell kullanma yönergelerini içeririz.

Kılavuz, çevrimdışı görüntüleme için PDF biçimindedir:

- [Kılavuzu PDF biçiminde indirin](https://www.microsoft.com/download/details.aspx?id=54795)

Ayrıca, kılavuzda açıklanan tüm ayarları otomatik olarak etkinleştirecek bir PowerShell de indirebilirsiniz. Yukarıdaki PDF indirmesi ile birlikte betiği veya powershell galerisinden tek tek edinebilirsiniz:

- [Ayarları otomatik olarak yapılandırmak için PowerShell betiği indirme](https://www.powershellgallery.com/packages/WindowsDefender_InternalEvaluationSettings)

> [!IMPORTANT]
> Kılavuz şu anda değerlendirmenin tek makineyle değerlendirilmesi için Microsoft Defender Virüsten Koruma. Bu kılavuzda yer alan tüm ayarların etkinleştirilmesi, gerçek zamanlı dağıtım için uygun değildir.
>
> Ağ üzerinde gerçek zamanlı dağıtım ve uygulamaları izlemeyle ilgili en Microsoft Defender Virüsten Koruma için bkz. [Microsoft Defender Virüsten Koruma.](deploy-manage-report-microsoft-defender-antivirus.md)

## <a name="related-topics"></a>İlgili konular

- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Dağıtım Microsoft Defender Virüsten Koruma](deploy-manage-report-microsoft-defender-antivirus.md)