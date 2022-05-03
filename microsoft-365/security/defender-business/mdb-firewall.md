---
title: İş için Microsoft Defender'de güvenlik duvarı
description: İş için Defender Windows Defender Güvenlik Duvarı ayarları hakkında bilgi edinin. Güvenlik duvarı, istenmeyen ağ trafiğinin şirket cihazlarınıza akmasını önlemeye yardımcı olabilir.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 9a22af2e1ef047de0deaf98c6eea37cda15dcc5f
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65172678"
---
# <a name="firewall-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'de güvenlik duvarı

İş için Microsoft Defender, [Windows Defender Güvenlik Duvarı ile güvenlik duvarı](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security) özelliklerini içerir. Güvenlik duvarı koruması, hangi ağ trafiğinin cihazlara girmesine veya cihazlardan akmasını sağlayan kurallarla cihazların güvenliğinin korunmasına yardımcı olur. 

Çeşitli konumlardaki cihazlarda bağlantılara izin verilip verilmeyeceğini veya bağlantının engellenip engellenmeyeceğini belirtmek için güvenlik duvarı korumasını kullanabilirsiniz. Örneğin, güvenlik duvarı ayarlarınız şirketinizin iç ağına bağlı cihazlarda gelen bağlantılara izin verebilir, ancak cihaz güvenilmeyen cihazlara sahip bir ağdayken bu bağlantıları engelleyebilir.

**Bu makalede şunlar açıklanmaktadır**:

- [İş için Defender'da varsayılan güvenlik duvarı ayarları](#default-firewall-settings-in-defender-for-business)
- [İş için Defender'da yapılandırabileceğiniz güvenlik duvarı ayarları](#firewall-settings-you-can-configure-in-defender-for-business)

>
> **Bir dakikan var mı?**
> Lütfen <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">güvenlikle ilgili kısa anketimize</a> katılın. Sizden haber almak isteriz!
>

## <a name="default-firewall-settings-in-defender-for-business"></a>İş için Defender'da varsayılan güvenlik duvarı ayarları

İş için Microsoft Defender, şirketinizin cihazlarının ilk günden korunmasına yardımcı olmak için varsayılan güvenlik duvarı ilkelerini ve ayarlarını içerir. Şirketinizin cihazları İş için Microsoft Defender eklenir eklenmez, varsayılan güvenlik duvarı ilkeniz aşağıdaki gibi çalışır:

- Konumdan bağımsız olarak cihazlardan giden bağlantılara varsayılan olarak izin verilir.
- Cihazlar şirketinizin ağına bağlandığında, tüm gelen bağlantılar varsayılan olarak engellenir.
- Cihazlar bir genel ağa veya özel ağa bağlandığında, tüm gelen bağlantılar varsayılan olarak engellenir.

İş için Microsoft Defender'da, gelen bağlantıları engellemek veya izin vermek için özel durumlar tanımlayabilirsiniz. Özel kurallar oluşturarak bu özel durumları tanımlarsınız. Bkz. [Güvenlik duvarı ilkeleri için özel kuralları yönetme](mdb-custom-rules-firewall.md).

## <a name="firewall-settings-you-can-configure-in-defender-for-business"></a>İş için Defender'da yapılandırabileceğiniz güvenlik duvarı ayarları

İş için Microsoft Defender, Windows Defender Güvenlik Duvarı aracılığıyla güvenlik duvarı korumasını içerir. Aşağıdaki tabloda, İş için Microsoft Defender'da güvenlik duvarı koruması için yapılandırılabilir ayarlar listelenir.

| Ayar | Açıklama |
|--|--|
| **Etki alanı ağı** | Etki alanı ağ profili şirketinizin ağı için geçerlidir. Etki alanı ağınız için güvenlik duvarı ayarları, aynı ağdaki diğer cihazlarda başlatılan gelen bağlantılara uygulanır. Varsayılan olarak, gelen bağlantılar **Tümünü engelle** olarak ayarlanır.  |
| **Genel ağ** | Ortak ağ profili, kafe veya havaalanı gibi genel bir konumda kullanabileceğiniz bir ağ için geçerlidir. Ortak ağlar için güvenlik duvarı ayarları, aynı ağdaki diğer cihazlarda başlatılan gelen bağlantılara uygulanır. Ortak ağ, tanımadığınız veya güvenmediğiniz cihazlar içerebileceğinden, gelen bağlantılar varsayılan olarak **Tümünü engelle** olarak ayarlanır.  |
| **Özel ağ** | Özel ağ profili, eviniz gibi özel bir konumdaki bir ağ için geçerlidir. Özel ağlar için güvenlik duvarı ayarları, aynı ağdaki diğer cihazlarda başlatılan gelen bağlantılara uygulanır. Genel olarak, özel bir ağda, aynı ağdaki diğer tüm cihazların güvenilir cihazlar olduğu varsayılır. Ancak, varsayılan olarak gelen bağlantılar **Tümünü engelle** olarak ayarlanır. |
| **Özel kurallar** | [Özel kurallar](mdb-custom-rules-firewall.md) , belirli bağlantıları engellemenize veya izin vermenizi sağlar. Örneğin, bir cihazdaki belirli bir uygulama üzerinden yapılan bağlantılar dışında, özel bir ağa bağlı cihazlardaki tüm gelen bağlantıları engellemek istediğinizi varsayalım. Bu durumda, **Özel ağı** tüm gelen bağlantıları engelleyecek şekilde ayarlar ve ardından özel durumu tanımlamak için özel bir kural eklersiniz. <br/><br/>Belirli dosyalar veya uygulamalar, İnternet protokolü (IP) adresi veya bir IP adresi aralığı için özel durumlar tanımlamak için özel kurallar kullanabilirsiniz. <br/><br/>Oluşturduğunuz özel kuralın türüne bağlı olarak, kullanabileceğiniz bazı örnek değerler şunlardır: <br/><br/>Uygulama dosyası yolu: `C:\Windows\System\Notepad.exe or %WINDIR%\Notepad.exe` <br/><br/>IP: veya gibi `192.168.11.0` geçerli bir IPv4/IPv6 adresi `192.168.1.0/24` <br/><br/>IP: Gibi `192.168.1.0-192.168.1.9` biçimlendirilmiş (boşluk içermeyen) geçerli bir IPv4/IPv6 adres aralığı |

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender'de güvenlik duvarı ayarlarını yönetme](mdb-custom-rules-firewall.md)
- [Windows Defender Güvenlik Duvarı hakkında daha fazla bilgi edinin](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)
- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md)
- [İş için Microsoft Defender'da tehditlere yanıt verme ve tehditleri azaltma](mdb-respond-mitigate-threats.md)
- [İşlem merkezindeki düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)