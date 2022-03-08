---
title: Adım 4. Cihazları koruma
author: dansimp
f1.keywords:
- NOCSH
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- ransomware
- m365solution-ransomware
ms.custom: seo-marvel-jun2020
keywords: fidye yazılımı, insan tarafından işletilen fidye yazılımı, insan tarafından işletilen fidye yazılımı, HumOR, extortion saldırısı, fidye yazılımı saldırı, şifreleme, cryptovirology, sıfır güven
description: MDA Windows MAM sağlayıcısı olarak Intune'i kullanın ve Windows 10 kaynaklarınızı fidye yazılımlarına karşı korumak için Microsoft 365 özelliklerini kullanın.
ms.openlocfilehash: 0d7b9a5e125c3f0478948340dce5677a3ae65395
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318081"
---
# <a name="step-4-protect-devices"></a>Adım 4. Cihazları koruma

Cihazları (uç noktaları) fidye yazılımı saldırılarının ilk erişim parçasına karşı korumaya yardımcı olmak için:

- [Intune'u](/mem/intune/fundamentals/what-is-intune) cihazlarınız için mobil cihaz yönetimi (MDM) ve mobil uygulama yönetimi (MAM) sağlayıcısı olarak dağıtın ve kuruluşa ait cihazlarınızı kaydettirin.
- Kullanıcı hesabı [kimlik bilgilerini doğrulamak, cihaz sistem](/microsoft-365/security/office-365-security/identity-access-policies) durumu ve uyumluluk gereksinimlerini zorunlu etmek için Ortak kimlik ve cihaz erişimi ilkelerini uygulama.
- Uç [Nokta ve Güvenlik](/microsoft-365/security/defender-endpoint/network-protection) Özellikleri için Microsoft Defender'da Ağ Microsoft 365 Defender.
- Site [ve indirme denetimi ile uygulama](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings) [ve dosya denetimi Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings) engellemek veya uyarmak için yapılandırma.
- [İndirilen Microsoft Defender Virüsten Koruma ekleri](/microsoft-365/security/defender-endpoint/configure-advanced-scan-types-microsoft-defender-antivirus) taramayı etkinleştirme.
- Uç **Nokta ve Güvenlik Için** Microsoft Defender'da Uzak Masaüstü güvenlik düzeyini **TLS** Microsoft 365 Defender.

## <a name="windows-11-or-10-devices"></a>Windows 11 veya 10 cihaz

11 veya 10 cihazdan bir saldırının uz Windows korunmasına yardımcı olmak için:

- [Microsoft Defender Güvenlik Duvarı'nı açma](https://support.microsoft.com/windows/turn-microsoft-defender-firewall-on-or-off-ec0844f7-aebd-0583-67fe-601ecf5d774f).
- [Tüm Microsoft Defender Virüsten Koruma güncelleştirin](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus).

Saldırının etkisini azaltmak için:

- Saldırı [yüzeyini azaltma kurallarını ve fidye yazılımlarına karşı gelişmiş korumayı kullanın](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-reference#use-advanced-protection-against-ransomware).

Güvenlik savunmalarınızı ele alan bir saldırgandan korunmaya yardımcı olmak için:

- Bulut [teslimi korumasını açık](/microsoft-365/security/defender-endpoint/enable-cloud-protection-microsoft-defender-antivirus) Microsoft Defender Virüsten Koruma şekilde korumayı koruma.
- Gerçek Microsoft Defender Virüsten Koruma [izlemenin açık olduğunu](/microsoft-365/security/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus) unutmayın.
- Gerçek [zamanlı korumayı açma](/microsoft-365/security/defender-endpoint/configure-real-time-protection-microsoft-defender-antivirus).
- Güvenlik ayarlarında [kötü amaçlı değişiklikleri önlemek için Uç Nokta için Microsoft Defender'da](/microsoft-365/security/defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection) değişiklik korumasını açma.

Saldırının bir parçası olarak kodu yürüten bir saldırgana karşı korunmaya yardımcı olmak için:

- [Aç'Microsoft Defender Virüsten Koruma](/mem/intune/user-help/turn-on-defender-windows).
- [Bu makrolardan Win32 API Office engelin](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules#block-win32-api-calls-from-office-macros).
- Bu işlemi kullanarak, 4.0 Excel tüm eski çalışma kitaplarını güncelleştirilmiş VBA makro [biçimine geçirebilirsiniz](https://www.microsoft.com/microsoft-365/blog/2010/02/16/migrating-excel-4-macros-to-vba/).
- [Imzalanmamış makroların kullanımını devre dışı bırakma](https://support.microsoft.com/topic/enable-or-disable-macros-in-office-files-12b036fd-d140-4e74-b45e-16fed1a7e5c6). Bilinmeyen makroların ortamınıza çalışmayy olduğundan emin olmak için, [](/deployoffice/security/designate-trusted-locations-for-files-in-office) işle ilgili gerekli tüm iç makroların imzalanmıştır ve güvenilir konumdan yararlanarak çalışmanızı sağlar.
- Kötü amaçlı XLM veya VBA makrolarını, Kötü amaçlı yazılımdan Koruma Tarama [Arabirimi (](https://www.microsoft.com/security/blog/2021/03/03/xlm-amsi-new-runtime-defense-against-excel-4-0-macro-malware/) AMSI) ile çalışma zamanı makro taramasını durdurarak durdurun. Makro Çalıştırma Süresi Tarama Kapsamı için Grup İlkesi ayarı Tüm Dosyalar için Etkinleştir veya Düşük  Güveni Olan Dosyalar için Etkinleştir olarak ayarlanmışsa bu özellik (varsayılan olarak **etkindir) açıktır**. En son grup ilkesi şablon dosyalarını al.

## <a name="impact-on-users-and-change-management"></a>Kullanıcılar üzerindeki etkisi ve değişiklik yönetimi

Bu korumaları uygulayan siz, aşağıdakiler için değişiklik yönetimi yapın:

- Yaygın [Sıfır Güven kimliği ve cihaz erişim ilkeleri](/microsoft-365/security/office-365-security/identity-access-policies) , uyumlu olmayan cihazlara sahip kullanıcılara erişimi reddedebilir.
- Dosyaları indirmek, indirme öncesinde kullanıcıları uyarmış veya engellenmiş olabilir.
- Bazı Office, Excel 4.0, XLM veya VBA makroları artık çalışmay olabilir.

## <a name="resulting-configuration"></a>Sonuçta elde edilen yapılandırma

kiracınız için 1.ve 4. adımlar için fidye yazılımı koruması ve bu korumayı edin.

![4. Adımdan sonra Microsoft 365 kiracınız için fidye yazılımı koruması](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step4.png)

## <a name="next-step"></a>Sonraki adım

[![Yazılımla fidye yazılımına karşı 5. Microsoft 365](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-step5.png)](ransomware-protection-microsoft-365-information.md)

Kiracınıza [bilgileri korumak için 5](ransomware-protection-microsoft-365-information.md). Adıma Microsoft 365 geçin. 
