---
title: Tarafından şifrelenen e-posta için son kullanma tarihi Office 365 Gelişmiş İleti Şifrelemesi
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 10/8/2019
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: E Office 365 Gelişmiş İleti Şifrelemesi markalı bir şablon aracılığıyla e-postalarda son kullanma tarihi ayarerek e-posta güvenliğinizi genişletmek üzere Bu Şablonu kullanın.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1213ecf48ee9bd2e04accdd13aaf3ecd74d3faba
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983228"
---
# <a name="set-an-expiration-date-for-email-encrypted-by-office-365-advanced-message-encryption"></a>Tarafından şifrelenen e-posta için son kullanma tarihi Office 365 Gelişmiş İleti Şifrelemesi

Office 365 Gelişmiş İleti Şifrelemesi [E5, Microsoft 365 Kurumsal, Office 365 E5](https://www.microsoft.com/microsoft-365/enterprise/home) Microsoft 365 E5 (Kar Amacı Gütmeyen Personel Fiyatları) ve diğer Office 365 Kurumsal  E5 (Kar Amacı Gütmeyen Personel Fiyatları) ve A5 Office 365 Eğitim. Organizasyonda herhangi bir aboneliği olmayan bir Office 365 Gelişmiş İleti Şifrelemesi, satın almak için Microsoft 365 E5 Uyumluluk için SKU Microsoft 365 E3, Microsoft 365 E3  (Kar Amacı Gütmeyen Personel Fiyatları) Office 365 Gelişmiş Uyumluluk veya Microsoft 365 E3, Microsoft 365 E3 (Kar Amacı Gütmeyen Personel Fiyatları) veya SKU için SKU Office 365.

Kullanıcılarının şifreli e-postalara erişmek için OME Portalını kullanan dış alıcılara göndertikleri e-postalarda ileti süre sonu kullanabilirsiniz. Alıcıları, son kullanma tarihini belirten özel bir markalı şablon kullanarak, kuruluş tarafından gönderilen şifrelenmiş e-postaları görüntülemek ve yanıtlamak için OME portalını kullanmaya Windows PowerShell.

Bir Office 365 yöneticisi olarak, kuruluş e-posta iletilerinin görünümünü özelleştirmek için şirket markanızı uygulayan bir genel yönetici olarak, bu e-posta iletileri için bir süre sonu da belirtebilirsiniz. Bu Office 365 Gelişmiş İleti Şifrelemesi, kuruluştan gelen şifrelenmiş e-postalar için birden çok şablon oluşturabilirsiniz. Şablon kullanarak, alıcıların kullanıcılarınız tarafından gönderilen postalara ne kadar süreyle erişeni kontrol etmek için kullanabilirsiniz.

Son kullanıcı son kullanma tarihi ayarlanmış bir posta aldığında, kullanıcı kaydıran e-postada son kullanma tarihini görür. Kullanıcı süresi dolmuş bir postayı açmayı deniyorsa, OME portalında bir hata görüntülenir.

Yalnızca dış alıcılara gönderilen e-postalar için son kullanma tarihleri ayarlayabilirsiniz.

Diğer Office 365 Gelişmiş İleti Şifrelemesi ile, özel markalama her uygulamanıza Office 365 şablonun uygulandığı posta akışı kuralına uyan e-postaya kaydırlayıcıyı uygular. Buna ek olarak, yalnızca özel markalama kullanıyorsanız sona ermeyi kullanabilirsiniz.

## <a name="create-a-custom-branding-template-to-force-mail-expiration-by-using-powershell"></a>PowerShell kullanarak postanın süre dolmasını zorlamak için özel bir markalama şablonu oluşturma

1. [Bağlan Exchange Online izinlerine](/powershell/exchange/connect-to-exchange-online-powershell) sahip bir hesap ile PowerShell'i ayarlamayı da sağlar.

2. New-OMEConfiguration cmdlet'ini çalıştırın.

    ```powershell
    New-OMEConfiguration -Identity "Expire in 7 days" -ExternalMailExpiryInDays 7
    ```

Burada:

- `Identity` özel şablonun adıdır.

- `ExternalMailExpiryInDays` alıcıların süresi dolmadan önce postayı saklayacakları gün sayısını tanımlar. 1-730 gün arasında herhangi bir değeri kullanabilirsiniz.

## <a name="more-information-about-office-365-advanced-message-encryption"></a>Daha fazla bilgi Office 365 Gelişmiş İleti Şifrelemesi

- [Office 365 Gelişmiş İleti Şifrelemesi](ome-advanced-message-encryption.md)

- [Kullanıcı tarafından şifrelenen e-postaları iptal Office 365 Gelişmiş İleti Şifrelemesi](revoke-ome-encrypted-mail.md)

- [İleti ilkesi ve uyumluluk hizmeti açıklaması](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)