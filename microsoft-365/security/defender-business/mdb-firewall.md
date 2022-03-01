---
title: İş için Microsoft Defender'da Güvenlik Duvarı (önizleme)
description: Microsoft Defender Windows Defender'da (önizleme) yapılandırma ayarları da içinde olmak üzere Güvenlik Duvarı hakkında bilgi
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: d3fbaa66dd29c0c5ff3dcc2a420d1d05e789bd33
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027498"
---
# <a name="firewall-in-microsoft-defender-for-business-preview"></a>İş için Microsoft Defender'da Güvenlik Duvarı (önizleme)

> [!IMPORTANT]
> İş için Microsoft Defender şu anda önizlemede ve istekte etmek için buraya kaydolan müşterilere ve IT [İş Ortaklarına aşamalı](https://aka.ms/mdb-preview) olarak aşamalı olarak aşamalı olarak sunulmaktadır. Önümüzdeki haftalarda bir ilk müşteri ve iş ortağı kümesi sunuyoruz ve genel kullanılabilirlik durumuna kadar önizlemeyi genişleteceğiz. Önizlemenin bir dizi ilk [senaryoyla başlat olacağını](mdb-tutorials.md#try-these-preview-scenarios) ve düzenli olarak özellikler ekley olacacaz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

İş için Microsoft Defender (önizleme), Güvenlik Duvarı'nı kullanarak güvenlik [Windows Defender içerir](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). Güvenlik duvarı koruması, hangi ağ trafiğinin cihazlara girişine veya cihazlarından akışına izin verildiğini belirleyen kurallarla cihazların güvenliğini sağlar. 

Çeşitli konumlarda cihazlarda bağlantılara izin veriip engellenmezseniz, güvenlik duvarı korumasını kullanabilirsiniz. Örneğin, güvenlik duvarı ayarlarınız, cihazınızın iç ağına bağlı cihazlarda gelen bağlantılara izin verir, ancak cihaz güvenilmeyen cihazlarla bir ağ üzerinde olduğunda bu bağlantıları önler.

**Bu makalede şu açıklanmıştır**:

- [İş için Defender'da (önizleme) varsayılan güvenlik duvarı ayarları](#default-firewall-settings-in-defender-for-business)
- [İş için Defender'da (önizleme) yapılandırabilirsiniz güvenlik duvarı ayarları](#firewall-settings-you-can-configure-in-defender-for-business)

## <a name="default-firewall-settings-in-defender-for-business"></a>İş için Defender'da varsayılan güvenlik duvarı ayarları

İş için Microsoft Defender (önizleme), kuruluş cihazlarınızı ilk günden korumaya yardımcı olmak için varsayılan güvenlik duvarı ilkelerini ve ayarlarını içerir. Kuruluş cihazları İş için Microsoft Defender'a (önizleme) ekli olduğu anda, varsayılan güvenlik duvarı ilkeniz aşağıdaki gibi çalışır:

- Konumdan bağımsız olarak, cihazlardan giden bağlantılara varsayılan olarak izin verilir.
- Cihazlar kuruluş ağınıza bağlandığında, tüm gelen bağlantılar varsayılan olarak engellenir.
- Cihazlar bir ortak ağa veya özel ağa bağlandığında, tüm gelen bağlantılar varsayılan olarak engellenir.

İş için Microsoft Defender'da (önizleme), gelen bağlantıları engellemek veya buna izin vermek için özel durumlar tanımlayabilirsiniz. Özel kurallar oluşturarak bu özel durumları tanımlayabilirsiniz. Bkz [. Güvenlik duvarı ilkeleri için özel kuralları yönetme](mdb-custom-rules-firewall.md).

## <a name="firewall-settings-you-can-configure-in-defender-for-business"></a>İş için Defender'da yapılandırabilirsiniz güvenlik duvarı ayarları

İş için Microsoft Defender (önizleme), Güvenlik Duvarı aracılığıyla güvenlik Windows Defender içerir. Aşağıdaki tabloda, Microsoft Defender İş'te (önizleme) güvenlik duvarı koruması için yapılandırılan ayarlar listelemiştir. <br/><br/>

| Ayar | Açıklama |
|--|--|
| **Etki alanı ağı** | Etki alanı ağ profili, kuruluş ağınız için geçerlidir. Etki alanı ağ için güvenlik duvarı ayarları, aynı ağ üzerinde olan diğer cihazlarda başlatılan gelen bağlantılara uygulanır. Varsayılan olarak, gelen bağlantılar Tüm bağlantıları engelle **olarak ayarlanır**.  |
| **Genel ağ** | Genel ağ profili, kafe veya havaalanında gibi genel bir konumda kullanabileceğiniz bir ağa uygulanır. Ortak ağların güvenlik duvarı ayarları, aynı ağ üzerinde olan diğer cihazlarda başlatılan gelen bağlantılarda geçerlidir. Genel ağ, güvenme olmadığınız cihazlar da içerebilir, çünkü gelen bağlantılar varsayılan olarak hepsini engelle **olarak** ayarlanır.  |
| **Özel ağ** | Özel ağ profili, eviniz gibi özel bir konumdaki ağa uygulanır. Özel ağların güvenlik duvarı ayarları, aynı ağ üzerinde olan diğer cihazlarda başlatılan gelen bağlantılarda geçerlidir. Genel olarak, özel bir ağ üzerinde aynı ağ'daki diğer tüm cihazların güvenilen cihazlar olduğu varsayılır. Bununla birlikte, varsayılan olarak gelen bağlantılar Tüm bağlantıları engelle **olarak ayarlanır**. |
| **Özel kurallar** | [Özel kurallar belirli](mdb-custom-rules-firewall.md) bağlantıları engellemenizi veya izin vermenizi sağlar. Örneğin, bir cihaz üzerinde belirli bir uygulama üzerinden yapılan bağlantılar dışında, özel bir ağa bağlı cihazlardan tüm gelen bağlantıları engellemek istediğiniz varsayalım. Bu durumda, Tüm gelen bağlantıları engellemek **için** Özel ağ'ı ayarladığınız gibi, özel bir kural da ekleyebilir ve bu özel durumu tanımlayabilirsiniz. <br/><br/>Özel kuralları kullanarak belirli dosya veya uygulamalar, İnternet protokolü (IP) adresi veya IP adresi aralığı için özel durumlar tanımlayabilirsiniz. <br/><br/>Oluşturmakta istediğiniz özel kuralın türüne bağlı olarak, aşağıdaki örnek değerleri kullanabilirsiniz: <br/><br/>Uygulama dosyası yolu: `C:\Windows\System\Notepad.exe or %WINDIR%\Notepad.exe` <br/><br/>IP: Geçerli bir IPv4/IPv6 adresi, örneğin `192.168.1.0` : `192.168.1.0/24` <br/><br/>IP: Gibi biçimlendirilmiş geçerli bir IPv4/IPv6 `192.168.1.0-192.168.1.9` adres aralığı (boşluk eklemeden) |

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender'da (önizleme) güvenlik duvarı ayarlarını yönetme](mdb-custom-rules-firewall.md)

- [Güvenlik Duvarı hakkında daha fazla Windows Defender bilgi](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme (önizleme)](mdb-view-manage-incidents.md)

- [Microsoft Defender İş'te (önizleme) tehditlere yanıt verme ve tehditlerini azaltmak](mdb-respond-mitigate-threats.md)

- [İşlem merkezinde düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)