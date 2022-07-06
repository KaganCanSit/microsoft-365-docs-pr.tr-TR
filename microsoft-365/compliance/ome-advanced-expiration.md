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
ms.openlocfilehash: b93aad4f217f956561b686b1415c64456a4360db
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635161"
---
# <a name="set-an-expiration-date-for-email-encrypted-by-microsoft-purview-advanced-message-encryption"></a>Microsoft Purview Gelişmiş İleti Şifreleme tarafından şifrelenen e-posta için bir son geçerlilik tarihi belirleme

Microsoft Purview Gelişmiş İleti Şifrelemesi [Microsoft 365 Kurumsal E5, Office 365 E5](https://www.microsoft.com/microsoft-365/enterprise/home), Microsoft 365 E5 (Kar Amacı Gütmeyen Personel Fiyatlandırması), Office 365 Kurumsal E5 (Kar Amacı Gütmeyen Personel Fiyatlandırması) ve Office 365 Eğitim A5. Microsoft 365 E3, Microsoft 365 E3 (Kar Amacı Gütmeyen Personel Fiyatlandırması) için SKU eklentisini veya Microsoft 365 E3 için Office 365 Gelişmiş Uyumluluk SKU eklentisini Microsoft 365 E5 Uyumluluk , Microsoft 365 E3 (Kar Amacı Gütmeyen Personel Fiyatlandırması) veya SKU'ları Office 365.

Kuruluşunuzun Microsoft Purview Gelişmiş İleti Şifrelemesi içermeyen bir aboneliği varsa, Microsoft 365 E3, Microsoft 365 E3 (Kar Amacı Gütmeyen Personel Fiyatlandırması) için Microsoft 365 E5 Uyumluluk SKU eklentisiyle veya Microsoft 365 E3, Microsoft 365 E3 (Kar Amacı Gütmeyen Personel Fiyatlandırması) veya SKU'ları Office 365 için SKU eklentisini Office 365 Gelişmiş Uyumluluk.

Kullanıcılarınızın şifrelenmiş e-postalara erişmek için OME Portalını kullanan dış alıcılara gönderdiği e-postalarda ileti süre sonunu kullanabilirsiniz. PowerShell'de son kullanma tarihini belirten özel markalı bir şablon kullanarak kuruluşunuz tarafından gönderilen şifrelenmiş e-postaları görüntülemek ve yanıtlamak için alıcıları OME portalını kullanmaya zorlarsınız.

Office 365 genel yöneticisi olarak, kuruluşunuzun e-posta iletilerinin görünümünü özelleştirmek için şirket markanızı uyguladığınızda, bu e-posta iletileri için bir süre sonu da belirtebilirsiniz. Microsoft Purview Gelişmiş İleti Şifrelemesi ile, kuruluşunuzdan kaynaklanan şifrelenmiş e-postalar için birden çok şablon oluşturabilirsiniz. Şablon kullanarak, alıcıların kullanıcılarınız tarafından gönderilen postalara ne kadar süreyle erişebileceğini denetleyebilirsiniz.

Son kullanıcı, son kullanma tarihi ayarlanmış bir posta aldığında, sarmalayıcı e-postasında son kullanma tarihini görür. Kullanıcı süresi dolan bir postayı açmaya çalışırsa, OME portalında bir hata görüntülenir.

Yalnızca dış alıcılara e-postalar için son kullanma tarihleri ayarlayabilirsiniz.

Microsoft Purview Gelişmiş İleti Şifrelemesi ile özel markalama uyguladığınızda, Office 365 sarmalayıcıyı şablonu uyguladığınız posta akışı kuralına uyan e-postaya uygular. Ayrıca, süre sonunu yalnızca özel markalama kullanıyorsanız kullanabilirsiniz.

## <a name="create-a-custom-branding-template-to-force-mail-expiration-by-using-powershell"></a>PowerShell kullanarak posta süre sonunu zorlamak için özel bir marka şablonu oluşturma

1. Kuruluşunuzda genel yönetici izinlerine sahip bir hesapla [Exchange Online PowerShell'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

2. New-OMEConfiguration cmdlet'ini çalıştırın.

    ```powershell
    New-OMEConfiguration -Identity "Expire in 7 days" -ExternalMailExpiryInDays 7
    ```

Konum:

- `Identity` özel şablonun adıdır.

- `ExternalMailExpiryInDays` , alıcıların süresi dolmadan önce postaları tutabilecekleri gün sayısını tanımlar. 1-730 gün arasındaki herhangi bir değeri kullanabilirsiniz.

## <a name="more-information-about-microsoft-purview-advanced-message-encryption"></a>Microsoft Purview Gelişmiş İleti Şifrelemesi hakkında daha fazla bilgi

- [Gelişmiş İleti Şifrelemesi](ome-advanced-message-encryption.md)

- [Microsoft Purview Gelişmiş İleti Şifreleme tarafından şifrelenen e-postayı iptal etme](revoke-ome-encrypted-mail.md)

- [İleti ilkesi ve uyumluluk hizmeti açıklaması](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)
