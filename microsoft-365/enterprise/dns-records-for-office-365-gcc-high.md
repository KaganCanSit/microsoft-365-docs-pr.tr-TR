---
title: Office 365 GCC High için DNS kayıtları
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: 'Özet: Office 365 GCC High için DNS kayıtları'
hideEdit: true
ms.openlocfilehash: 80c1a5d4473af0877e67b6bc9e14a9ffd890e3ba
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019527"
---
# <a name="dns-records-for-office-365-gcc-high"></a>Office 365 GCC High için DNS kayıtları

*Bu makale Office 365 GCC High ve Microsoft 365 GCC için geçerlidir*

Office 365 GCC High'ye eklemenin bir parçası olarak, SMTP ve SIP etki alanlarınızı Online Services kiracınıza eklemeniz gerekir.  Bunu, Azure AD PowerShell'New-MsolDomain veya [Azure Government Portal'ı](https://portal.azure.us) kullanarak etki alanını ekleme ve sahipliği onaylama işlemini başlatmak için kullanacağız.

Etki alanlarınızı kiracınıza ekleyen ve doğrulayan olduktan sonra, aşağıdaki hizmetler için uygun DNS kayıtlarını eklemek üzere aşağıdaki kılavuzu kullanın.  Aşağıdaki tabloyu, gelen MX kayıtlarına veya var olan Otomatik Bulma kayıtlarına göre kuruluş ihtiyaçlarını karşılamak Exchange değiştirmeniz gerekir.  Kesintileri veya e-postaların yanlış teslimini önlemek için, bu DNS kayıtlarını mesajlaşma ekibimizle birlikte koordine öneririz.

## <a name="exchange-online"></a>Exchange Online

| Tür | Öncelik | Ana bilgisayar adı | Adrese veya değere göre | TTL |
| --- | --- | --- | --- | --- |
| MX | 0 | @ | *tenant.mail.protection.office365.us* (diğer ayrıntılar için aşağıya bakın) | Bir Saat |
| TXT | - | @ | v=spf1 include:spf.protection.office365.us -all | Bir Saat |
| CNAME | - | autodiscover | autodiscover.office365.us | Bir Saat |

### <a name="exchange-autodiscover-record"></a>Exchange Bulma kaydı

Şirket içinde Exchange Server varsa, geçiş işlemini tamamlayana kadar var olan kaydınızı yerinde bırakmanızı ve Exchange Online tamamlandıktan sonra bu kaydı güncelleştirmenizi öneririz. 

### <a name="exchange-online-mx-record"></a>Exchange Online MX Kaydı

Kabul edilen etki alanlarınız için MX kayıt değeri, yukarıda belirtildiği gibi standart bir biçime sahiptir: *tenant.mail.protection.office365.us*, kiracıyı varsayılan  kiracı adının ilk bölümüyle değiştirir.

Örneğin, kiracı adınız contoso.onmicrosoft.us, MX kaydınız için **contoso.mail.protection.office365.us** ad kullanırsanız.

## <a name="skype-for-business-online"></a>Skype Kurumsal Çevrimiçi

### <a name="cname-records"></a>CNAME kayıtları

| Tür | Ana bilgisayar adı | Adrese veya değere göre | TTL |
| --- | --- | --- | --- |
| CNAME | sip | sipdir.online.gov.skypeforbusiness.us | Bir Saat |
| CNAME | lyncdiscover | webdir.online.gov.skypeforbusiness.us | Bir Saat |

### <a name="srv-records"></a>SRV kayıtları

| Tür | Hizmet | Protokol | Bağlantı noktası | Ağırlık | Öncelik | Name | Hedef | TTL |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SRV | \_sip | \_tls | 443 | 1 | 100 | @ | sipdir.online.gov.skypeforbusiness.us | Bir Saat |
| SRV | \_sipfederationtls | \_tcp | 5061 | 1 | 100 | @ | sipfed.online.gov.skypeforbusiness.us | Bir Saat |

## <a name="other-dns-records"></a>Diğer DNS kayıtları

> [!IMPORTANT]
> DNS bölgesinde *msoid* CNAME kaydınız varsa, şu anda **kaydı** DNS'den kaldırmanız gerekir.  msoid kaydı, Microsoft 365 Kurumsal Uygulamaları *(Office 365 ProPlus)* ile uyumlu değildir ve etkinleştirmenin başarılı olmasını önler.
