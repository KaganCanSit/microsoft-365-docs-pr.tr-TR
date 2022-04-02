---
title: Windows’da Microsoft Defender Virüsten Koruma
description: Kötü amaçlı yazılımlardan ve virüslerden koruyan yerleşik Microsoft Defender Virüsten Koruma’yı yönetmeyi, yapılandırmayı ve kullanmayı öğrenin.
keywords: Microsoft Defender Virüsten Koruma, windows defender, kötü amaçlı yazılımdan koruma, scep, system center endpoint protection, system center configuration manager, virüs, kötü amaçlı yazılım, tehdit, algılama, koruma, güvenlik
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: high
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: b6eabc3527742b6cc7f06d23207db813b827e5f5
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63009990"
---
# <a name="microsoft-defender-antivirus-in-windows"></a>Windows’da Microsoft Defender Virüsten Koruma

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

Microsoft Defender Virüsten Koruma; Windows 10, Windows 11 ve Windows Sunucusu sürümlerinde kullanılabilir.

Microsoft Defender Virüsten Koruma, Uç Nokta için Microsoft Defender’da yeni nesil korumanın önemli bir bileşenidir. Bu koruma, makine öğrenimi, büyük veri çözümlemesi, ayrıntılı tehdit direnci araştırması ve Microsoft bulut altyapısını bir araya getirerek kuruluşunuzdaki cihazları (veya uç noktaları) korur. Microsoft Defender Virüsten Koruma, Windows'da yerleşik olarak bulunur ve Uç Nokta için Microsoft Defender ile birlikte çalışarak cihazınızda ve bulutta koruma sağlar.

## <a name="compatibility-with-other-antivirus-products"></a>Diğer virüsten koruma ürünleriyle uyumluluk

Aygıtınızda Microsoft dışı virüsten koruma/kötü amaçlı yazılımlardan koruma ürünü kullanıyorsanız, Microsoft Defender Virüsten Koruma’yı, Microsoft dışı virüsten koruma çözümüyle birlikte pasif modda çalıştırmanız mümkün olabilir. Bu, kullanılan işletim sistemine ve cihazınıza Uç Nokta için Defender eklenip eklenmediğine bağlıdır. Daha fazla bilgi edinmek için [Microsoft Defender Virüsten Koruma uyumluluğuna](microsoft-defender-antivirus-compatibility.md) bakın.

## <a name="comparing-active-mode-passive-mode-and-disabled-mode"></a>Etkin, pasif ve devre dışı modlarını karşılaştırma

Aşağıdaki tabloda, Microsoft Defender Virüsten Koruma etkin, pasif veya devre dışı modda olduğunda neler beklenebileceği açıklanmıştır.

<br/><br/>

| Mod | Neler olur? |
|---|---|
| Etkin mod | Etkin modda, Microsoft Defender Virüsten Koruma, cihazda virüsten birincil koruma uygulaması olarak kullanılır. Dosyalar taranır, tehditler düzeltilir ve algılanan tehditler, kuruluşunuzun güvenlik raporlarında ve Windows Güvenliği uygulamanıza listelenir. |
| Pasif mod | Pasif modda, Microsoft Defender Virüsten Koruma, cihazda virüsten birincil koruma uygulaması olarak kullanılamaz. Dosyalar taranır ve algılanan tehditler rapor edilir ancak tehditler Microsoft Defender Virüsten Koruma ile düzeltilmez. <br/><br/> **ÖNEMLİ**: Microsoft Defender Virüsten Koruma, pasif modda sadece Uç Nokta için Microsoft Defender’a eklenmiş uç noktalarda çalıştırılabilir. [Microsoft Defender Virüsten Koruma’nın pasif modda çalıştırılması için gereksinimlere](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode) bakın. |
| Devre dışı bırakılmış veya kaldırılmış | Microsoft Defender Virüsten Koruma, devre dışı bırakıldığında veya kaldırıldığında kullanılmaz. Dosyalar taranmaz, tehditler düzeltilmez. Genel olarak, Microsoft Defender Virüsten Koruma’yı devre dışı bırakmanızı veya kaldırmanızı önermeyiz. |

Daha fazla bilgi edinmek için [Microsoft Defender Virüsten Koruma uyumluluğuna](microsoft-defender-antivirus-compatibility.md) bakın.

## <a name="check-the-state-of-microsoft-defender-antivirus-on-your-device"></a>Cihazınızın Microsoft Defender Virüsten Koruma durumunu kontrol etme

Cihazınızın Microsoft Defender Virüsten Koruma durumunu kontrol etmek için Windows Güvenliği uygulaması veya Windows PowerShell gibi çeşitli yöntemlerden birini kullanabilirsiniz.

### <a name="use-the-windows-security-app-to-check-status-of-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma durumunu kontrol etmek için Windows Güvenliği uygulamasını kullanma

1. Windows cihazınızda Başlat menüsü seçip yazmaya başlayın`Security`. Ardından, sonuçlarda Windows Güvenliği uygulamasını açın.

2. **Virüs ve tehdit koruması**’nı seçin.

3. **Virüs ve tehdit koruması ayarları**’nda **Ayarları yönet**’i seçin.

Ayarlar sayfasında virüsten koruma/kötü amaçlı yazılımdan koruma çözümünün adını görürsünüz.

### <a name="use-powershell-to-check-status-of-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma durumunu kontrol etmek için PowerShell’i kullanma

1. Başlat menüsünü seçip yazmaya başlayın`PowerShell`. Ardından, sonuçlarda Windows PowerShell’i açın.

2. `Get-MpComputerStatus` yazın.

3. Sonuç listesinde **AMRunningMode** satırına bakın.

   - **Normal**, Microsoft Defender Virüsten Koruma’nın etkin modda çalıştığı anlamına gelir.

   - **Pasif mod**, Microsoft Defender Virüsten Koruma’nın çalıştığı ancak cihazınızda virüsten birincil koruma/kötü amaçlı yazılımdan koruma ürünü olmadığı anlamına gelir. Pasif mod, yalnızca Uç Nokta için Microsoft Defender'a eklenen ve belirli gereksinimleri karşılayan cihazlar için kullanılabilir. Daha fazla bilgi edinmek için [Microsoft Defender Virüsten Koruma’nın pasif modda çalıştırılması gereksinimlere](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode) bakın.

   - **EDR Engelleme Modu**, Microsoft Defender Virüsten Koruma'nın çalıştığı ve Uç Nokta için Microsoft Defender’in bir özelliği olan [Uç nokta algılama ve yanıt’ın (EDR) engelleme modunda](edr-in-block-mode.md) etkinleştirildiği anlamına gelir.

   - **SxS Pasif Modu**, Microsoft Defender Virüsten Koruma’nın başka bir virüsten koruma/kötü amaçlı yazılımdan koruma ürünüyle birlikte çalıştığı ve [sınırlı düzenli taramanın kullanıldığı anlamına gelir](limited-periodic-scanning-microsoft-defender-antivirus.md).

> [!TIP]
> Get-MpComputerStatus PowerShell cmdlet hakkında daha fazla bilgi edinmek için [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus) başvuru makalesine bakın.

## <a name="get-your-antivirusantimalware-platform-updates"></a>Virüsten koruma/kötü amaçlı yazılımdan koruma platform güncellemelerinizi alın

Microsoft Defender Virüsten Koruma programını ve tüm virüsten koruma/kötü amaçlı yazılımdan koruma çözümlerini güncel tutmanız önemlidir. Microsoft, cihazlarınızın kötü amaçlı yeni yazılımlara ve saldırı tekniklerine karşı korunması için en son teknolojiye sahip olmalarını sağlamak amacıyla düzenli güncelleştirmeler yayımlar. Daha fazla bilgi için [Microsoft Defender Virüsten Koruma güncelleştirmelerine bakın ve temelleri uygulayın](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Defender Virüsten Koruma yönetimi ve yapılandırması](configuration-management-reference-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma değerlendirmesi](evaluate-microsoft-defender-antivirus.md)
