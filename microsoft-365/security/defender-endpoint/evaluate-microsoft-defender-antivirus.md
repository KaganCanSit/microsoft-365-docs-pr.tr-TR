---
title: Microsoft Defender Virüsten Koruma’yı değerlendirin
description: Her büyüklükteki işletmeler, Windows'da Microsoft Defender Virüsten Koruma tarafından sunulan korumayı değerlendirmek ve test etmek için bu kılavuzu kullanabilir.
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
ms.openlocfilehash: da13d621b350955a7de93d5abe2ee3f4c0c1b27a
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416068"
---
# <a name="evaluate-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma’yı değerlendirin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**

- Microsoft Defender Virüsten Koruma
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)

**Platform**
- Windows

Microsoft Defender Virüsten Koruma sizi virüslerden, kötü amaçlı yazılımlardan ve istenmeyebilecek uygulamalardan ne kadar iyi koruyup korumadığını belirlemek için bu kılavuzu kullanın.

> [!TIP]
>Ayrıca, aşağıdaki özelliklerin çalıştığını onaylamak ve nasıl çalıştıklarını görmek için [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) Uç Nokta için Microsoft Defender tanıtım web sitesini ziyaret edebilirsiniz:
>
> - Bulut tabanlı koruma
> - Hızlı öğrenme (ilk bakışta engelle dahil)
> - İstenmeyebilecek uygulama engelleme

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

Hem küçük hem de büyük kuruluşlar için kullanılabilen Microsoft Defender Virüsten Koruma önemli yeni nesil koruma özelliklerini ve ağınızda kötü amaçlı yazılım algılama ve korumayı nasıl artırdıklarını açıklar.

Her ayarı bağımsız olarak veya tümünü aynı anda yapılandırmayı ve değerlendirmeyi seçebilirsiniz. Benzer ayarları tipik değerlendirme senaryolarına göre gruplandırdık ve ayarları etkinleştirmek için PowerShell kullanma yönergelerini de dahil ettik.

Kılavuz, çevrimdışı görüntüleme için PDF biçiminde kullanılabilir:

- [Kılavuzu PDF biçiminde indirme](https://www.microsoft.com/download/details.aspx?id=54795)

Ayrıca kılavuzda açıklanan tüm ayarları otomatik olarak etkinleştirecek bir PowerShell indirebilirsiniz. Betiği yukarıdaki PDF indirme işleminin yanı sıra veya PowerShell Galerisi'dan tek tek edinebilirsiniz:

- [Ayarları otomatik olarak yapılandırmak için PowerShell betiğini indirin](https://www.powershellgallery.com/packages/WindowsDefender_InternalEvaluationSettings)

> [!IMPORTANT]
> Kılavuz şu anda Microsoft Defender Virüsten Koruma tek makineli değerlendirmeye yöneliktir. Bu kılavuzdaki tüm ayarların etkinleştirilmesi gerçek dünya dağıtımı için uygun olmayabilir.
>
> Ağ üzerinden Microsoft Defender Virüsten Koruma gerçek dünya dağıtımı ve izlemesine yönelik en son öneriler için bkz[. Dağıtım Microsoft Defender Virüsten Koruma](deploy-manage-report-microsoft-defender-antivirus.md).

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)

## <a name="related-topics"></a>İlgili konular

- [Windows 10'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
- [Microsoft Defender Virüsten Koruma dağıtma](deploy-manage-report-microsoft-defender-antivirus.md)