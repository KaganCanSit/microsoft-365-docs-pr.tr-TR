---
title: Microsoft Purview Gelişmiş İleti Şifreleme tarafından şifrelenen e-posta için bir son geçerlilik tarihi belirleme
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
description: Özel markalı bir şablon aracılığıyla e-postalarda son kullanma tarihi ayarlayarak e-posta güvenliğinizi genişletmek için Microsoft Purview Gelişmiş İleti Şifrelemesi'ni kullanın.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e8689820adc3158ae2a36a4d52ebad0959097b49
ms.sourcegitcommit: 7e0094ddff54bcbe5d691dba58d4c4fb86f8b1a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2022
ms.locfileid: "65188404"
---
# <a name="set-an-expiration-date-for-email-encrypted-by-microsoft-purview-advanced-message-encryption"></a>Microsoft Purview Gelişmiş İleti Şifreleme tarafından şifrelenen e-posta için bir son geçerlilik tarihi belirleme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview Gelişmiş İleti Şifrelemesi [Microsoft 365 Kurumsal E5, Office 365 E5](https://www.microsoft.com/microsoft-365/enterprise/home), Microsoft 365 E5 (Kar Amacı Gütmeyen Personel Fiyatlandırması), Office 365 Kurumsal E5 (Kar Amacı Gütmeyen Personel Fiyatlandırması) ve Office 365 Eğitim A5. Microsoft 365 E3, Microsoft 365 E3 (Kar Amacı Gütmeyen Personel Fiyatlandırması) için SKU eklentisini veya Microsoft 365 E3 için Office 365 Gelişmiş Uyumluluk SKU eklentisini Microsoft 365 E5 Uyumluluk , Microsoft 365 E3 (Kar Amacı Gütmeyen Personel Fiyatlandırması) veya SKU'ları Office 365.

Kuruluşunuzun Microsoft Purview Gelişmiş İleti Şifrelemesi içermeyen bir aboneliği varsa, Microsoft 365 E3, Microsoft 365 E3 (Kar Amacı Gütmeyen Personel Fiyatlandırması) için Microsoft 365 E5 Uyumluluk SKU eklentisiyle veya Microsoft 365 E3, Microsoft 365 E3 (Kar Amacı Gütmeyen Personel Fiyatlandırması) veya SKU'ları Office 365 için SKU eklentisini Office 365 Gelişmiş Uyumluluk.

Kullanıcılarınızın şifrelenmiş e-postalara erişmek için OME Portalını kullanan dış alıcılara gönderdiği e-postalarda ileti süre sonunu kullanabilirsiniz. Windows PowerShell'de son kullanma tarihini belirten özel markalı bir şablon kullanarak kuruluşunuz tarafından gönderilen şifrelenmiş e-postaları görüntülemek ve yanıtlamak için alıcıları OME portalını kullanmaya zorlarsınız.

Office 365 genel yöneticisi olarak, kuruluşunuzun e-posta iletilerinin görünümünü özelleştirmek için şirket markanızı uyguladığınızda, bu e-posta iletileri için bir süre sonu da belirtebilirsiniz. Microsoft Purview Gelişmiş İleti Şifrelemesi ile, kuruluşunuzdan kaynaklanan şifrelenmiş e-postalar için birden çok şablon oluşturabilirsiniz. Şablon kullanarak, alıcıların kullanıcılarınız tarafından gönderilen postalara ne kadar süreyle erişebileceğini denetleyebilirsiniz.

Son kullanıcı, son kullanma tarihi ayarlanmış bir posta aldığında, sarmalayıcı e-postasında son kullanma tarihini görür. Kullanıcı süresi dolan bir postayı açmaya çalışırsa, OME portalında bir hata görüntülenir.

Yalnızca dış alıcılara e-postalar için son kullanma tarihleri ayarlayabilirsiniz.

Microsoft Purview Gelişmiş İleti Şifrelemesi ile özel markalama uyguladığınızda, Office 365 sarmalayıcıyı şablonu uyguladığınız posta akışı kuralına uyan e-postaya uygular. Ayrıca, süre sonunu yalnızca özel markalama kullanıyorsanız kullanabilirsiniz.

## <a name="create-a-custom-branding-template-to-force-mail-expiration-by-using-powershell"></a>PowerShell kullanarak posta süre sonunu zorlamak için özel bir marka şablonu oluşturma

1. [PowerShell'i](/powershell/exchange/connect-to-exchange-online-powershell) kuruluşunuzda genel yönetici izinlerine sahip bir hesapla Exchange Online Bağlan.

2. New-OMEConfiguration cmdlet'ini çalıştırın.

    ```powershell
    New-OMEConfiguration -Identity "Expire in 7 days" -ExternalMailExpiryInDays 7
    ```

Nerede:

- `Identity` özel şablonun adıdır.

- `ExternalMailExpiryInDays` , alıcıların süresi dolmadan önce postaları tutabilecekleri gün sayısını tanımlar. 1-730 gün arasındaki herhangi bir değeri kullanabilirsiniz.

## <a name="more-information-about-microsoft-purview-advanced-message-encryption"></a>Microsoft Purview Gelişmiş İleti Şifrelemesi hakkında daha fazla bilgi

- [Gelişmiş İleti Şifrelemesi](ome-advanced-message-encryption.md)

- [Microsoft Purview Gelişmiş İleti Şifreleme tarafından şifrelenen e-postayı iptal etme](revoke-ome-encrypted-mail.md)

- [İleti ilkesi ve uyumluluk hizmeti açıklaması](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)
