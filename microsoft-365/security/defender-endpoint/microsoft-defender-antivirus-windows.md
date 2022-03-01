---
title: Microsoft Defender Virüsten Koruma'da Windows
description: Yeni, yerleşik kötü amaçlı yazılım ve virüsten koruma Microsoft Defender Virüsten Koruma yönetmeyi, yapılandırmayı ve kullanmayı öğrenin.
keywords: Microsoft Defender Virüsten Koruma, windows defender, kötü amaçlı yazılımdan koruma, scep, sistem merkezi uç nokta koruması, sistem merkezi yapılandırma yöneticisi, virüs, kötü amaçlı yazılım, tehdit, algılama, koruma, güvenlik
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
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63009990"
---
# <a name="microsoft-defender-antivirus-in-windows"></a>Microsoft Defender Virüsten Koruma'da Windows

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

Microsoft Defender Virüsten Koruma, Windows 10 Windows 11'de ve Windows Server sürümlerinde kullanılabilir.

Microsoft Defender Virüsten Koruma, Uç Nokta için Microsoft Defender'da yeni nesil korumanın önemli bir bileşenidir. Bu koruma, makine öğrenimi, büyük veri çözümlemesi, derinlikli tehdit direnci araştırması ve organizasyonlu cihazları (veya uç noktaları) korumak için Microsoft bulut altyapısını bir araya getirir. Microsoft Defender Virüsten Koruma, Windows'de yerleşik olarak çalışır ve aygıtınızda ve bulutta koruma sağlamak için Uç Nokta için Microsoft Defender ile çalışır.

## <a name="compatibility-with-other-antivirus-products"></a>Diğer virüsten koruma ürünleriyle uyumluluk

Aygıtınızda Microsoft'a karşı virüsten koruma/kötü amaçlı yazılımlardan koruma ürünü kullanıyorsanız, Microsoft dışı virüsten koruma çözümünün yanı sıra pasif modunda Microsoft Defender Virüsten Koruma çalıştırabilirsiniz. Kullanılan işletim sistemine ve cihazınızın Uç Nokta için Defender'a olup olmadığınıza bağlıdır. Daha fazla bilgi edinmek için uyumluluk [Microsoft Defender Virüsten Koruma bakın](microsoft-defender-antivirus-compatibility.md).

## <a name="comparing-active-mode-passive-mode-and-disabled-mode"></a>Etkin modu, pasif modunu ve devre dışı modunu karşılaştırma

Aşağıdaki tabloda, etkin modda, pasif Microsoft Defender Virüsten Koruma devre dışı bırakılmıştır.

<br/><br/>

| Mod | Ne olur? |
|---|---|
| Etkin mod | Etkin modda, Microsoft Defender Virüsten Koruma, cihazda birincil virüsten koruma uygulaması olarak kullanılır. Dosyalar taranır, tehditlere yönelik düzeltmeler yapıldı ve algılanan tehditler, kuruluş güvenlik raporlarında ve Windows Güvenliği uygulamanıza listelenir. |
| Pasif modu | Pasif modunda, Microsoft Defender Virüsten Koruma, cihazda birincil virüsten koruma uygulaması olarak kullanılamaz. Dosyalar taranır ve algılanan tehditlere rapor edilir, ancak tehditler diğer belgeler veya Microsoft Defender Virüsten Koruma. <br/><br/> **ÖNEMLİ**: Microsoft Defender Virüsten Koruma edilgen modda yalnızca Uç Nokta için Microsoft Defender'a ekli uç noktalarda çalıştırabilirsiniz. [Edilgen modda Microsoft Defender Virüsten Koruma için gereksinimler'e bakın](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode). |
| Devre dışı bırakıldı veya kaldırıldı | Devre dışı bırakılacak veya Microsoft Defender Virüsten Koruma kaldırılamaz. Dosyalar taranmaz ve tehditlere düzeltme olmaz. Genelde devre dışı bırakmanızı veya kaldırmanızı Microsoft Defender Virüsten Koruma. |

Daha fazla bilgi edinmek için uyumluluk [Microsoft Defender Virüsten Koruma bakın](microsoft-defender-antivirus-compatibility.md).

## <a name="check-the-state-of-microsoft-defender-antivirus-on-your-device"></a>Cihazınızın Microsoft Defender Virüsten Koruma durumunu denetleme

Cihazınızın durumlarını Microsoft Defender Virüsten Koruma, Windows Güvenliği uygulaması veya posta kutusu gibi çeşitli yöntemlerden birini Windows PowerShell.

### <a name="use-the-windows-security-app-to-check-status-of-microsoft-defender-antivirus"></a>Windows Güvenliği durumunu kontrol etmek için Microsoft Defender Virüsten Koruma

1. Windows başlat'ı Başlat menüsü yazmaya başlayın`Security`. Sonuçlarda Windows Güvenliği'i açın.

2. Virüs **ve tehdit &'yi seçin**.

3. Virüs **koruması & ayarları'nın altında** Ayarları **yönet'i seçin**.

Ayarlar sayfasında virüsten koruma/kötü amaçlı yazılımdan koruma çözümünün adını görebilirsiniz.

### <a name="use-powershell-to-check-status-of-microsoft-defender-antivirus"></a>PowerShell kullanarak postanın durumunu Microsoft Defender Virüsten Koruma

1. Metni Başlat menüsü ve yazmaya başlayın`PowerShell`. Daha sonra Windows PowerShell bir arama açın.

2. `Get-MpComputerStatus` yazın.

3. Sonuç listesinde **AMRunningMode satırına** bakın.

   - **Normal**, Microsoft Defender Virüsten Koruma modda çalıştır çalıştırıı olduğu anlamına gelir.

   - **Pasif modu** Microsoft Defender Virüsten Koruma anlamına gelir, ancak aygıtınızda birincil virüsten koruma/kötü amaçlı yazılımdan koruma ürünü değildir. Pasif modu yalnızca Uç Nokta için Microsoft Defender'a ekli olan ve belirli gereksinimleri karşı bulunan cihazlar için kullanılabilir. Daha fazla bilgi edinmek için [pasif Microsoft Defender Virüsten Koruma için gereksinimler' bakın](microsoft-defender-antivirus-compatibility.md#requirements-for-microsoft-defender-antivirus-to-run-in-passive-mode).

   - **EDR Modu,** Microsoft Defender Virüsten Koruma için kullanılabilir olduğu ve Engelleme modunda Uç nokta algılama ve yanıt [(EDR)](edr-in-block-mode.md) özelliğinin etkinleştirildiğinde Uç nokta için Microsoft Defender'da bir özelliğin etkin olduğu anlamına gelir.

   - **SxS Pasif Modu**, Microsoft Defender Virüsten Koruma başka bir virüsten koruma/kötü amaçlı yazılımdan koruma ürünüyle birlikte çalıştır anlamına gelir ve düzenli aralıklarla [tarama kullanılmaktadır](limited-periodic-scanning-microsoft-defender-antivirus.md).

> [!TIP]
> PowerShell cmdlet'i Get-MpComputerStatus daha fazla bilgi edinmek için [Get-MpCompkomStatus başvuru makalesine bakın](/powershell/module/defender/get-mpcomputerstatus).

## <a name="get-your-antivirusantimalware-platform-updates"></a>Virüsten koruma/kötü amaçlı yazılımdan koruma platform güncelleştirmelerini alın

Güncel e-Microsoft Defender Virüsten Koruma veya virüsten koruma/kötü amaçlı yazılımdan koruma çözümlerini korumanız önemlidir. Microsoft, cihazlarınızı yeni kötü amaçlı yazılımlara ve saldırı tekniklerine karşı korumak için en son teknolojiye sahip olduğundan emin olmak için düzenli güncelleştirmeler yayımlar. Daha fazla bilgi için bkz[. Güncelleştirmeleri Microsoft Defender Virüsten Koruma ve taban çizgilerini uygulama](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Defender Virüsten Koruma yönetimi ve yapılandırması](configuration-management-reference-microsoft-defender-antivirus.md)
- [Veri Microsoft Defender Virüsten Koruma değerlendirme](evaluate-microsoft-defender-antivirus.md)
