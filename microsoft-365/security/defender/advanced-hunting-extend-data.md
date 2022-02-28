---
title: Doğru ayarlarla gelişmiş arama kapsamı genişletme
description: Gelişmiş aramada en kapsamlı Windows elde etmeye yardımcı olmak için cihazlarında ve diğer ayarlarda denetim ayarlarını denetleme
keywords: gelişmiş av, olay, özet, varlık, denetim ayarları, kullanıcı hesabı yönetimi, güvenlik grubu yönetimi, tehdit avı, siber tehdit araması, arama, sorgu, telemetri, Microsoft 365, Microsoft 365 Defender
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: dd61fa434eaf2130f0fcb0f28df9a20d696e04ec
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989970"
---
# <a name="extend-advanced-hunting-coverage-with-the-right-settings"></a>Doğru ayarlarla gelişmiş arama kapsamı genişletme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender

[Gelişmiş av](advanced-hunting-overview.md), cihazlarınız, çalışma alanınız, Azure AD ve Identity için Microsoft Defender gibi Office 365 çeşitli kaynaklardan gelen verilere dayandır. Mümkün olan en kapsamlı verileri elde etmek için, ilgili veri kaynaklarında doğru ayarların olduğundan emin olun.

## <a name="advanced-security-auditing-on-windows-devices"></a>Mobil cihazlarda gelişmiş Windows denetimi
Cihazlarınız üzerinde yerel hesap yönetimi, yerel güvenlik grubu yönetimi ve hizmet oluşturma gibi etkinliklerle ilgili veri almak için bu gelişmiş denetim ayarlarını açın.

| Veri | Açıklama | Şema tablosu | Yapılandırma |
| --- | --- | --- | --- |
| Hesap yönetimi | Yerel hesap oluşturma, `ActionType` silme ve hesapla ilgili diğer etkinlikleri gösteren çeşitli değerler olarak yakalanan olaylar | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - Gelişmiş güvenlik denetim ilkesi dağıtma: [Kullanıcı Hesabı Yönetimini Denetleme](/windows/security/threat-protection/auditing/audit-user-account-management)<br> - [Gelişmiş güvenlik denetim ilkeleri hakkında bilgi](/windows/security/threat-protection/auditing/advanced-security-auditing) |
| Güvenlik grubu yönetimi | Yerel güvenlik grubu oluşturma `ActionType` ve diğer yerel grup yönetimi etkinliklerini gösteren çeşitli değerler olarak yakalanan olaylar | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - Gelişmiş güvenlik denetim ilkesi dağıtma: [Denetim Güvenliği Grup Yönetimi](/windows/security/threat-protection/auditing/audit-security-group-management)<br> - [Gelişmiş güvenlik denetim ilkeleri hakkında bilgi](/windows/security/threat-protection/auditing/advanced-security-auditing) |
| Hizmet yüklemesi | Değeri ile bir `ActionType` hizmet `ServiceInstalled`oluşturulmuş olduğunu belirten , yakalanan olaylar | [DeviceEvents](advanced-hunting-deviceevents-table.md) | - Gelişmiş güvenlik denetim ilkesi dağıtma: [Denetim Güvenlik Sistemi Uzantısı](/windows/security/threat-protection/auditing/audit-security-system-extension)<br> - [Gelişmiş güvenlik denetim ilkeleri hakkında bilgi](/windows/security/threat-protection/auditing/advanced-security-auditing) |

## <a name="microsoft-defender-for-identity-sensor-on-the-domain-controller"></a>Etki alanı denetleyicisinde Kimlik algılayıcısı için Microsoft Defender
Şirket içinde Active Directory çalıştırıyorsanız, Identity için Microsoft Defender verileri almak için etki alanı denetleyicisine Identity için Microsoft Defender algılayıcısı'nın yüklemesi gerekir. Bu veriler yüklendikten ve düzgün yapılandırıldığında, aynı zamanda Identity için Microsoft Defender aracılığıyla gelişmiş ava da akış verir ve ağ bağlantınız için kimlik bilgileriyle olaylarının daha holek bir resmini sağlar. Ayrıca bu veriler, gelişmiş avlama kapsamındaki ilgili uyarıları oluşturmak için Kimlik için Microsoft Defender'ın da bu özelliği geliştirmektedir. 

| Veri | Açıklama | Şema tablosu | Yapılandırma |
| --- | --- | --- | --- |
| Etki alanı denetleyicisi | Şirket içi Active Directory'den Identity için Microsoft Defender'a gönderilen veriler, hesap ayrıntıları, oturum açma etkinliği ve Active Directory sorguları gibi kimlikle ilgili bilgileri zenginleştirme | [IdentityInfo](advanced-hunting-identityinfo-table.md), [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md) ve [IdentityQueryEvents gibi birden çok tablo](advanced-hunting-identityqueryevents-table.md)  | - [Kimlik algılayıcısı için Microsoft Defender'ı yükleme](/azure-advanced-threat-protection/install-atp-step4)<br>- [İlgili etkinlik Windows açma](/azure-advanced-threat-protection/configure-event-collection) |

>[!NOTE]
>Bu makaledeki bazı tablolar Uç Nokta için Microsoft Defender'da kullanılamıyor olabilir. [Daha fazla Microsoft 365 Defender](m365d-enable.md) kullanarak tehdit yakalamak için çok daha fazla kaynağı açabilirsiniz. Gelişmiş av iş akışlarınızı Uç Nokta için Microsoft Defender'dan Microsoft 365 Defender için [Microsoft Defender'dan gelişmiş arama sorgularını geçirme makalesinde](advanced-hunting-migrate-from-mde.md) yer alan adımları takip edebilirsiniz.

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)