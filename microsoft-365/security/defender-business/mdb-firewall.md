---
title: İş için Microsoft Defender'da Güvenlik Duvarı
description: Yapılandırma ayarları Windows Defender İş için Microsoft Defender Güvenlik Duvarı hakkında bilgi
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 92db1711fa5aefb8920c35a8665cf322b3f0f5ef
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63525869"
---
# <a name="firewall-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'da Güvenlik Duvarı

> [!IMPORTANT]
> İş için Microsoft Defender 1 Mart 2022 [Microsoft 365 İş Ekstra'den](../../business-premium/index.md) itibaren tüm müşterilere sunulmaktadır. Tek başına bir abonelik olarak İş için Defender önizlemededir ve istekte etmek için buraya kaydolan müşterilere ve IT İş Ortaklarına [aşamalı](https://aka.ms/mdb-preview) olarak tüm müşterilere aşamalı olarak tüm müşterilere aşamalı olarak ve tek başına bir abonelik sunar. Önizleme bir [dizi senaryo içerir ve](mdb-tutorials.md#try-these-preview-scenarios) düzenli olarak özellikler ekleycek.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

İş için Microsoft Defender, Güvenlik Duvarı'nı Windows Defender [içerir](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). Güvenlik duvarı koruması, hangi ağ trafiğinin cihazlara girişine veya cihazlarından akışına izin verildiğini belirleyen kurallarla cihazların güvenliğini sağlar. 

Çeşitli konumlarda cihazlarda bağlantılara izin veriip engellenmezseniz, güvenlik duvarı korumasını kullanabilirsiniz. Örneğin, güvenlik duvarı ayarlarınız, şirketin iç ağına bağlı cihazlarda gelen bağlantılara izin verir, ancak cihaz güvenilmeyen cihazlarla bir ağ üzerinde olduğunda bu bağlantıları önler.

**Bu makalede şu açıklanmıştır**:

- [İş için Defender'da varsayılan güvenlik duvarı ayarları](#default-firewall-settings-in-defender-for-business)

- [İş için Defender'da yapılandırabilirsiniz güvenlik duvarı ayarları](#firewall-settings-you-can-configure-in-defender-for-business)

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

## <a name="default-firewall-settings-in-defender-for-business"></a>İş için Defender'da varsayılan güvenlik duvarı ayarları

İşletmeler için Microsoft Defender, şirket cihazlarınızı ilk günden korumanıza yardımcı olacak varsayılan güvenlik duvarı ilkelerini ve ayarlarını içerir. Şirketinizin cihazları İş için Microsoft Defender'a ekli olduğu anda, varsayılan güvenlik duvarı ilkeniz aşağıdaki gibi çalışır:

- Konumdan bağımsız olarak, cihazlardan giden bağlantılara varsayılan olarak izin verilir.
- Cihazlar şirketinizin ağına bağlandığında, tüm gelen bağlantılar varsayılan olarak engellenir.
- Cihazlar bir ortak ağa veya özel ağa bağlandığında, tüm gelen bağlantılar varsayılan olarak engellenir.

İş için Microsoft Defender'da gelen bağlantıları engellemek veya buna izin vermek için özel durumlar tanımlayabilirsiniz. Özel kurallar oluşturarak bu özel durumları tanımlayabilirsiniz. Bkz [. Güvenlik duvarı ilkeleri için özel kuralları yönetme](mdb-custom-rules-firewall.md).

## <a name="firewall-settings-you-can-configure-in-defender-for-business"></a>İş için Defender'da yapılandırabilirsiniz güvenlik duvarı ayarları

İş için Microsoft Defender, Güvenlik Duvarı aracılığıyla güvenlik Windows Defender içerir. Aşağıdaki tabloda, İş için Microsoft Defender'da güvenlik duvarı koruması için yapılandırılan ayarlar listeledir. <br/><br/>

| Ayar | Açıklama |
|--|--|
| **Etki alanı ağı** | Etki alanı ağ profili, şirketinizin ağına uygulanır. Etki alanı ağ için güvenlik duvarı ayarları, aynı ağ üzerinde olan diğer cihazlarda başlatılan gelen bağlantılara uygulanır. Varsayılan olarak, gelen bağlantılar Tüm bağlantıları engelle **olarak ayarlanır**.  |
| **Genel ağ** | Genel ağ profili, kafe veya havaalanında gibi genel bir konumda kullanabileceğiniz bir ağa uygulanır. Ortak ağların güvenlik duvarı ayarları, aynı ağ üzerinde olan diğer cihazlarda başlatılan gelen bağlantılarda geçerlidir. Genel ağ, güvenme olmadığınız cihazlar da içerebilir, çünkü gelen bağlantılar varsayılan olarak hepsini engelle **olarak** ayarlanır.  |
| **Özel ağ** | Özel ağ profili, eviniz gibi özel bir konumdaki ağa uygulanır. Özel ağların güvenlik duvarı ayarları, aynı ağ üzerinde olan diğer cihazlarda başlatılan gelen bağlantılarda geçerlidir. Genel olarak, özel bir ağ üzerinde aynı ağ'daki diğer tüm cihazların güvenilen cihazlar olduğu varsayılır. Bununla birlikte, varsayılan olarak gelen bağlantılar Tüm bağlantıları engelle **olarak ayarlanır**. |
| **Özel kurallar** | [Özel kurallar belirli](mdb-custom-rules-firewall.md) bağlantıları engellemenizi veya izin vermenizi sağlar. Örneğin, bir cihaz üzerinde belirli bir uygulama üzerinden yapılan bağlantılar dışında, özel bir ağa bağlı cihazlardan tüm gelen bağlantıları engellemek istediğiniz varsayalım. Bu durumda, Tüm gelen bağlantıları engellemek **için** Özel ağ'ı ayarladığınız gibi, özel bir kural da ekleyebilir ve bu özel durumu tanımlayabilirsiniz. <br/><br/>Özel kuralları kullanarak belirli dosya veya uygulamalar, İnternet protokolü (IP) adresi veya IP adresi aralığı için özel durumlar tanımlayabilirsiniz. <br/><br/>Oluşturmakta istediğiniz özel kuralın türüne bağlı olarak, aşağıdaki örnek değerleri kullanabilirsiniz: <br/><br/>Uygulama dosyası yolu: `C:\Windows\System\Notepad.exe or %WINDIR%\Notepad.exe` <br/><br/>IP: Geçerli bir IPv4/IPv6 adresi, örneğin `192.168.1.0` : `192.168.1.0/24` <br/><br/>IP: Gibi biçimlendirilmiş geçerli bir IPv4/IPv6 `192.168.1.0-192.168.1.9` adres aralığı (boşluk eklemeden) |

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender'da güvenlik duvarı ayarlarını yönetme](mdb-custom-rules-firewall.md)

- [Güvenlik Duvarı hakkında daha fazla Windows Defender bilgi](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md)

- [İş için Microsoft Defender'da tehditleri yanıtlama ve azaltmak](mdb-respond-mitigate-threats.md)

- [İşlem merkezinde düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)