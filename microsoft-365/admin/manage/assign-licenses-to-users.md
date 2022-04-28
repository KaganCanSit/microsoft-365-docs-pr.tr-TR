---
title: Kullanıcılara lisans atama
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: sinakassaw, nicholak
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- commerce_licensing
- AdminSurgePortfolio
- TopSMBIssues
- SaRA
- business_assist
- okr_SMB
- manage_licenses
- AdminTemplateSet
search.appverid: MET150
description: Belirli kullanıcılara ürün lisansları atamak veya belirli bir ürüne kullanıcı lisansları atamak isteyip istemediğinize bağlı olarak lisans atayın.
ms.date: 04/22/2022
ms.openlocfilehash: 32c91c82388cdb87b0dd6b980b51b888d1cec521
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092635"
---
# <a name="assign-licenses-to-users"></a>Kullanıcılara lisans atama

**Kullanıcılara, Etkin kullanıcılar** sayfasında veya **Lisanslar sayfasında lisans** atayabilirsiniz. Kullandığınız yöntem, belirli kullanıcılara ürün lisansları atamak mı yoksa belirli bir ürüne kullanıcı lisansları atamak mı istediğinize bağlıdır.

> [!NOTE]
> 
> - Yönetici olarak, kuruluşunuzdaki bir kullanıcı tarafından satın alınan self servis satın alma aboneliği için lisans atayamaz veya lisansı kaldıramazsınız. [Self servis satın alma aboneliğini devralabilir](../../commerce/subscriptions/manage-self-service-purchases-admins.md#take-over-a-self-service-purchase-subscription) ve lisansları atayabilir veya atamasını kaldırabilirsiniz.
> - Bazı abonelikler için yalnızca aboneliğinizi satın aldıktan veya yeniledikten sonra sınırlı bir süre içinde iptal edebilirsiniz. İptal penceresi geçtiyse, süresi sonunda aboneliği iptal etmek için yinelenen ödemeyi kapatın.

[Aynı anda kullanıcı eklemeyi ve lisans atamayı öğrenin](../add-users/add-users.md).

> [!TIP]
> Bu konuda verilen adımlarla ilgili yardıma ihtiyacınız varsa[bir Microsoft küçük işletme uzmanıyla çalışmayı](https://go.microsoft.com/fwlink/?linkid=2186871) göz önünde bulundurun. İşletme Yardımı ile, işletmenizi büyütürken katılımdan gündelik kullanıma kadar her aşamada siz ve çalışanlarınız günün 24 saati küçük işletme uzmanlarına erişebilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

- Lisansları atamak için Genel, Lisans veya Kullanıcı yöneticisi olmanız gerekir. Daha fazla bilgi için bkz. [Microsoft 365 yönetici rolleri hakkında](../add-users/about-admin-roles.md).
- [PowerShell ile kullanıcı hesaplarına Microsoft 365 lisans atayabilirsiniz](../../enterprise/assign-licenses-to-user-accounts-with-microsoft-365-powershell.md).
- Grup tabanlı lisanslama kullanmak için bkz. [Azure Active Directory'de kullanıcılara grup üyeliğine göre lisans atama](/azure/active-directory/users-groups-roles/licensing-groups-assign)
- Sway gibi bazı hizmetler, kullanıcılara otomatik olarak atanır ve tek tek atanması gerekmez.


## <a name="use-the-licenses-page-to-assign-licenses-to-users"></a>Kullanıcılara lisans atamak için Lisanslar sayfasını kullanma

Lisansları atamak için **Lisanslar** sayfasını kullandığınızda, belirli bir ürünün lisanslarını en fazla 20 kullanıcıya atarsınız. **Lisanslar** sayfasında, abonelikleriniz olan tüm ürünlerin listesini görürsünüz. Ayrıca her ürün için toplam lisans sayısını, kaç lisansın atandığı ve kaç tane kullanılabilir olduğunu da görürsünüz.

::: moniker range="o365-worldwide"

1. Yönetim merkezinde **Faturalama** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Lisansları</a> sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim merkezinde **Faturalama** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank">Lisansları</a> sayfasına gidin.

::: moniker-end

2. Bir ürün seçin.

3. Ürün ayrıntıları sayfasında **Lisans ata'yı** seçin.

4. **Kullanıcılara lisans ata** bölmesinde bir ad yazmaya başlayın ve ardından sonuçlar arasından seçerek listeye ekleyin. Tek seferde en fazla 20 kullanıcı ekleyebilirsiniz.

4. Belirli öğelere erişim atamak veya kaldırmak için **Uygulamaları ve hizmetleri aç veya kapat'ı** seçin.

6. İşiniz bittiğinde **Ata'yı** ve ardından **Kapat'ı** seçin.

Bir çakışma varsa, bir ileti görüntülenir, sorunun ne olduğunu size söyler ve nasıl düzelteceğinizi söyler. Örneğin, çakışan hizmetler içeren lisansları seçtiyseniz, hata iletisinde her lisansa dahil edilen hizmetleri gözden geçirmeniz ve yeniden denemeniz gerekir.

## <a name="change-the-apps-and-services-a-user-has-access-to"></a>Kullanıcının erişimi olan uygulamaları ve hizmetleri değiştirme

::: moniker range="o365-worldwide"

1. Yönetim merkezinde **Faturalama** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">Lisansları</a> sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim merkezinde **Faturalama** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank">Lisansları</a> sayfasına gidin.

::: moniker-end

2. **Lisanslar** sayfasında belirli bir kullanıcının satırını seçin.

3. Sağ bölmede, erişim vermek veya erişimini kaldırmak istediğiniz uygulamaları ve hizmetleri seçin veya seçimini kaldırın.

4. İşiniz bittiğinde **Kaydet'i** ve ardından **Kapat'ı** seçin.

## <a name="use-the-active-users-page-to-assign-licenses"></a>Lisans atamak için Etkin kullanıcılar sayfasını kullanma

Lisans atamak için **Etkin kullanıcılar** sayfasını kullandığınızda, ürünlere kullanıcı lisansları atarsınız.

### <a name="assign-licenses-to-multiple-users"></a>Birden çok kullanıcıya lisans atama

::: moniker range="o365-worldwide"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

2. Lisans atamak istediğiniz kullanıcıların adlarının yanındaki daireleri seçin.

3. Üst kısımda **Ürün lisanslarını yönet'i** seçin.

4. **Ürün lisanslarını yönet** bölmesinde **Daha fazla ata: Mevcut lisansları koru ve daha fazlasını** \> ata **İleri'yi** seçin.

5. **Lisanslar'ın** altında, seçili kullanıcıların sahip olmasını istediğiniz lisansların kutusunu seçin.\
    Varsayılan olarak, bu lisanslarla ilişkili tüm hizmetler kullanıcılara otomatik olarak atanır. Kullanıcıların kullanabileceği hizmetleri sınırlayabilirsiniz. Kullanıcıların sahip olmasını istemediğiniz hizmetlerin kutularının seçimini kaldırın.

6. Bölmenin en altında **Değişiklikleri kaydet'i** seçin.  
    Herkes için yeterli lisansınız yoksa ek lisans satın almanız gerekebilir.

> [!NOTE]
> Çok sayıda kullanıcı için lisans atamak istiyorsanız, [Azure Active Directory'de Kullanıcılara grup üyeliğine göre lisans atama'yı](/azure/active-directory/enterprise-users/licensing-groups-assign) kullanın

### <a name="assign-licenses-to-one-user"></a>Bir kullanıcıya lisans atama

::: moniker range="o365-worldwide"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

2. Lisans atamak istediğiniz kullanıcının satırını seçin.

3. Sağ bölmede, **Lisanslar ve Uygulamalar**'ı seçin.

4. **Lisanslar** bölümünü genişletin, atamak istediğiniz lisansların kutularını seçin ve ardından **Değişiklikleri kaydet** öğesini seçin.

## <a name="assign-a-license-to-a-guest-user"></a>Konuk kullanıcıya lisans atama

Konuk kullanıcıları Azure Active Directory yönetim merkezinde kuruluşunuzla işbirliği yapmaya davet edebilirsiniz. Konuk kullanıcılar hakkında bilgi edinmek için bkz. [Azure Active Directory B2B'de konuk kullanıcı erişimi nedir?](/azure/active-directory/external-identities/what-is-b2b). Konuk kullanıcılarınız yoksa bkz[. Hızlı Başlangıç: Azure portal dizininize konuk kullanıcı ekleme](/azure/active-directory/external-identities/b2b-quickstart-add-guest-users-portal).

> [!IMPORTANT]
> Bu adımları gerçekleştirmek için Genel yönetici olmanız gerekir.

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2067268" target="_blank">Azure Active Directory yönetim merkezine</a> gidin.

2. Gezinti bölmesinde **Kullanıcılar'ı** seçin.

3. **Kullanıcılar | Tüm Kullanıcılar (Önizleme)** sayfasında **Filtre ekle'yi** seçin.

4. **Alan seçin** menüsünde **Kullanıcı türü'nü** ve ardından **Uygula'yı** seçin.

5. Sonraki menüde **Konuk'a** tıklayın.

6. Sonuç listesinde lisansa ihtiyacı olan kullanıcıyı seçin.

7. **Yönet'in** altında **Lisanslar'ı** seçin.

8. **Ödevler'i** seçin.

9. **Lisans atamalarını güncelleştir** sayfasında, lisans atamak istediğiniz ürünü seçin.

10. Sağ tarafta, konuk kullanıcının erişmesini istemediğiniz hizmetlerin onay kutularını temizleyin.

11. **Kaydet**'i seçin.

## <a name="next-steps"></a>Sonraki adımlar

Kullanıcılarınızın henüz Office uygulamaları yüklü değilse, [pc veya Mac'te Microsoft 365 veya Office 2019'u indirip yükleme ve](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) [mobil cihazda Office uygulamaları ve e-postayı ayarlama](https://support.microsoft.com/office/7dabb6cb-0046-40b6-81fe-767e0b1f014f) gibi ayarlamaları için [Çalışan hızlı başlangıç kılavuzunu](../setup/employee-quick-setup.md) kullanıcılarınızla paylaşabilirsiniz.

## <a name="related-content"></a>İlgili içerik

[Abonelikleri ve lisansları anlama](../../commerce/licenses/subscriptions-and-licenses.md) (makale)\
[Kullanıcılardan lisans atamalarını kaldırma](remove-licenses-from-users.md) (makale)\
[Aboneliğiniz için lisans satın alma veya kaldırma](../../commerce/licenses/buy-licenses.md) (makale)
