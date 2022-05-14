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
description: Cihazlarla kullanmak üzere gruplara lisans atamayı öğrenin.
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
- okr_SMB
search.appverid: MET150
ms.date: 05/12/2022
ms.openlocfilehash: 5603fd947abdfbc6bede01fe7545a5a0fa99a67d
ms.sourcegitcommit: 4e7ff69f4d7d27c2d419f763cfcb069e3b0d0d9f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2022
ms.locfileid: "65403282"
---
# <a name="manage-licenses-for-devices"></a>Cihazlar için lisansları yönetme

Eğitim için Kurumlar için Microsoft 365 Uygulamaları (cihaz) veya Microsoft 365 Uygulamaları (cihaz) varsa, Azure AD grupları kullanarak cihazlara lisans atayabilirsiniz. Bir cihazın lisansı olduğunda, bu cihazı kullanan herkes Kurumlar için Microsoft 365 Uygulamaları kullanabilir (daha önce Office 365 ProPlus olarak adlandırılmıştır). Örneğin, kuruluşunuzdaki kişiler tarafından kullanılan 20 dizüstü bilgisayarınız ve tabletiniz olduğunu varsayalım. Her cihaza bir lisans atadığınızda, cihazlardan birinde oturum açan her kişi kendi lisansına gerek kalmadan Kurumlar için Microsoft 365 Uygulamaları kullanır.

> [!IMPORTANT]
> Kurumlar için Microsoft 365 Uygulamaları için cihaz tabanlı lisanslama, yalnızca bazı ticari müşteriler ve bazı eğitim müşterileri için eklenti lisansı olarak kullanılabilir. Ticari müşteriler için lisans *Kurumlar için Microsoft 365 Uygulamaları (cihaz)* ve yalnızca Kurumsal Anlaşma/Kurumsal Anlaşma Aboneliği aracılığıyla kullanılabilir. Eğitim müşterileri *için lisans Eğitim için Microsoft 365 Uygulamaları (cihaz)* ve yalnızca Eğitim için Kayıt Çözümleri (EES) aracılığıyla kullanılabilir. Daha fazla bilgi için [eğitim kullanılabilirliği](https://educationblog.microsoft.com/2019/08/attention-it-administrators-announcing-office-365-proplus-device-based-subscription-for-education) hakkındaki blog gönderisini okuyun. Ticari kullanılabilirlik için Microsoft hesabı temsilcinize başvurun.

Başlamak için, Azure Active Directory yönetim merkezinde bir grup oluşturun ve ardından cihazları gruba atayın. Cihaz gereksinimleri, hangi grup türlerini kullanabileceğiniz ve Kurumlar için Microsoft 365 Uygulamaları cihaz lisansını kullanmak üzere nasıl yapılandırabileceğiniz de dahil olmak üzere cihaz lisanslama hakkında daha fazla bilgi edinmek için bkz. [Kurumlar için Microsoft 365 Uygulamaları için cihaz tabanlı lisanslama](/deployoffice/device-based-licensing).

> [!IMPORTANT]
> Bu makaledeki görevleri tamamlamak için Genel yönetici olmanız gerekir.

## <a name="assign-licenses-to-devices"></a>Cihazlara lisans atama

Bir gruba lisans atadığınızda, grup içindeki tüm cihazlara lisans atarsınız. Tek bir gruba yalnızca bir abonelik atayabilirsiniz.

1. Microsoft 365 yönetim merkezi **Faturalama** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Lisansları</a> sayfasına gidin.
2. **Lisanslar** sayfasında **Eğitim için Microsoft 365 Uygulamaları (cihaz)** veya **Kurumlar için Microsoft 365 Uygulamaları (cihaz)** seçeneğini belirleyin.
3. Sonraki sayfada bir abonelik seçin ve ardından **Lisans ata'yı** seçin.
4. **Gruba lisans atayın** bölmesinde bir grup adı yazmaya başlayın ve ardından sonuçlar arasından seçerek listeye ekleyin.
5. **Ata'yı** ve ardından **Kapat'ı** seçin.

## <a name="unassign-licenses-from-devices"></a>Cihazlardan lisans atamalarını kaldırma

Bir gruptaki lisansların atamasını kaldırdığınızda, lisansları gruptaki tüm cihazlardan kaldırırsınız. Ardından tüm uygulamalar ve ilişkili veriler salt okunur olur.

1. Yönetim merkezinde <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">BillingLicenses</a>  >  sayfasına gidin.
2. **Lisanslar** sayfasında **Eğitim için Microsoft 365 Uygulamaları (cihaz)** veya **Kurumlar için Microsoft 365 Uygulamaları (cihaz)** seçeneğini belirleyin.
3. Sonraki sayfada bir abonelik seçin, üç noktayı (daha fazla eylem) seçin ve ardından **Lisansların atamasını kaldır'ı** seçin.
4. **Lisansların Atamasını Kaldır** iletişim kutusunda Atamayı **Kaldır'ı** seçin.
