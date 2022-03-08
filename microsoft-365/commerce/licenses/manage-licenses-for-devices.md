---
title: Cihazlar için lisansları yönetme
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: shegu, nicholak
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
description: Cihazlarla kullanım için gruplara lisans atamayı öğrenin.
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
- okr_SMB
search.appverid: MET150
ms.date: 08/27/2021
ms.openlocfilehash: fd452cb52a1c65a59e478fb80438ac95a57e8bf6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63311795"
---
# <a name="manage-licenses-for-devices"></a>Cihazlar için lisansları yönetme

Eğitim için Kurumlar için Microsoft 365 Uygulamaları (cihaz) veya Microsoft 365 Uygulamaları varsa, Azure AD gruplarını kullanarak cihazlara lisans atabilirsiniz. Bir cihazın lisansı olduğunda, o cihazı kullanan herkes Kullanıcı Adı (Kurumlar için Microsoft 365 Uygulamaları olarak adlandırılmıştır) Office 365 ProPlus. Örneğin, 20 dizüstü bilgisayarınız ve tabletiniz olduğunu ve bu dizüstü bilgisayarın kurum daki kişiler tarafından kullanıla olduğunu varsayalın. Her cihaza bir lisans atadığınız zaman, cihazlardan birini kullanarak oturum Kurumlar için Microsoft 365 Uygulamaları gerek kalmadan oturum atayabilirsiniz.

> [!IMPORTANT]
> Mobil cihaz tabanlı lisanslama Kurumlar için Microsoft 365 Uygulamaları sadece bazı ticari müşteriler ve bazı eğitim müşterileri için eklenti lisansı olarak kullanılabilir. Ticari müşteriler için bu lisans Kurumlar için Microsoft 365 Uygulamaları *(cihaz)* ile kullanılabilir ve yalnızca Kurumsal Anlaşma/Kurumsal Anlaşma aracılığıyla kullanılabilir. Eğitim müşterileri için lisans, Microsoft 365 Uygulamaları (cihaz *) için mevcuttur* ve yalnızca Eğitim için Kayıt Çözümleri (EES) aracılığıyla kullanılabilir. Daha fazla bilgi için, eğitim kullanılabilirliği ile ilgili blog [gönderilerini okuyun](https://educationblog.microsoft.com/2019/08/attention-it-administrators-announcing-office-365-proplus-device-based-subscription-for-education). Ticari kullanılabilirlik için Microsoft hesap temsilcinize başvurun.

İlk olarak, yönetim merkezinde bir Azure Active Directory oluşturun ve ardından cihazları gruba atsın. Cihaz lisanslama hakkında, cihaz gereksinimleri, kullanabileceğiniz grup türleri ve cihaz lisanslama Kurumlar için Microsoft 365 Uygulamaları için yapılandırma gibi daha fazla bilgi için bkz. Kurumlar için Microsoft 365 Uygulamaları için cihaz [tabanlı lisanslama](/deployoffice/device-based-licensing).

> [!IMPORTANT]
> Bu makaledeki görevleri tamamlamak için Genel yönetici olmak gerekir.

## <a name="assign-licenses-to-devices"></a>Cihazlara lisans atama

Bir gruba lisans atadığınız zaman, lisansları gruptaki tüm cihazlara atarsiniz. Herhangi bir tek gruba yalnızca bir abonelik atabilirsiniz.

1. Faturalar Microsoft 365 yönetim merkezi **,** <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">BillingLicenses</a> >  sayfasına gidin.
2. Lisanslar **sayfasında Eğitim** için Microsoft 365 Uygulamaları **(cihaz) veya Lisans (Kurumlar için Microsoft 365 Uygulamaları)** **seçin**.
3. Sonraki sayfada abonelik seçin ve ardından Lisans **ata'ya tıklayın**.
4. Bir **gruba lisans ata bölmesinde** , bir grup adı yazmaya başlayın ve sonuçlardan bunu listeye eklemek için seçin.
5. **Ata'ya ve** ardından Kapat'a **seçin**.

## <a name="unassign-licenses-from-devices"></a>Cihazlardan lisans atamalarını iptal et

Bir gruptan lisans atamalarını kaldırabilirsiniz, gruptaki tüm cihazlardan lisansları kaldırmış oluruz. Tüm uygulamalar ve ilişkili verileri daha sonra salt okunur olur.

1. Yönetim merkezinde <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">BillingLicenses</a>  >  sayfasına gidin.
2. Lisanslar **sayfasında Eğitim** için Microsoft 365 Uygulamaları **(cihaz) veya Lisans (Kurumlar için Microsoft 365 Uygulamaları)** **seçin**.
3. Sonraki sayfada bir abonelik seçin, üç noktayı (diğer eylemler) ve sonra Lisansları **atamayı iptal et'i seçin**.
4. Lisans **atamasını iptal et iletişim** kutusunda Atamayı **Aç'ı seçin**.
