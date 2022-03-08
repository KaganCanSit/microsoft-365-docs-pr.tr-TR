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
description: Belirli kullanıcılara ürün lisansları atamak veya belirli bir ürüne kullanıcı lisansları atamak istediğinize bağlı olarak lisans atama.
ms.date: 09/16/2021
ms.openlocfilehash: dd0469288ce53ac59663e119022a204130bad3ef
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316709"
---
# <a name="assign-licenses-to-users"></a>Kullanıcılara lisans atama

Kullanıcılara lisansları Etkin kullanıcılar sayfasında **veya** Lisanslar **sayfasında atabilirsiniz** . Kullandığınız yöntem, belirli kullanıcılara ürün lisansları atamak mı yoksa belirli bir ürüne kullanıcı lisansları atamak mı istediğinize bağlıdır.

> [!NOTE]
> 
> - Yönetici olarak, kurumda bir kullanıcı tarafından satın alınan self servis satın alma aboneliği için lisans atayayam veya atamalarını iptal edilemez. Self [servis satın alma aboneliğini üzerine alıp](../../commerce/subscriptions/manage-self-service-purchases-admins.md#take-over-a-self-service-purchase-subscription) lisansları atayın veya atamalarını iptal edin.
> - Bazı abonelikler için, aboneliğinizi satın alıp yeniledikten sonra yalnızca sınırlı bir süre içinde iptal edebilirsiniz. İptal etme penceresi sona ererse, süresi sonunda aboneliği iptal etmek için yinelenen faturalamayı kapatın.

[Aynı anda hem kullanıcı ekleme hem de lisans atama hakkında bilgi alın](../add-users/add-users.md).

> [!TIP]
> Bu konudaki adımlarda yardıma ihtiyacınız varsa, [Microsoft küçük işletme uzmanıyla çalışmayı göz önünde bulundurabilirsiniz](https://go.microsoft.com/fwlink/?linkid=2186871). İş Yardımı ile, işe alımtan günlük kullanıma kadar işlerinizi büyüttükçe siz ve çalışanlarınız küçük işletme uzmanlarına 24 saat erişim elde ediyor.

## <a name="before-you-begin"></a>Başlamadan önce

- Lisansları atamak için Genel, Lisans veya Kullanıcı yöneticisi olmak gerekir. Daha fazla bilgi için bkz[. Microsoft 365 rolleri hakkında](../add-users/about-admin-roles.md).
- [PowerShell ile Microsoft 365 hesaplarına kullanıcı lisansları atabilirsiniz](../../enterprise/assign-licenses-to-user-accounts-with-microsoft-365-powershell.md).
- Grup tabanlı lisanslama kullanmak için bkz. Grup [üyeliğini kullanarak kullanıcılara lisans Azure Active Directory](/azure/active-directory/users-groups-roles/licensing-groups-assign)
- Sway gibi bazı hizmetler, kullanıcılara otomatik olarak atanır ve tek tek atanması gerekmez.


## <a name="use-the-licenses-page-to-assign-licenses-to-users"></a>Kullanıcılara lisans atamak için Lisanslar sayfasını kullanma

Lisans atamak için **Lisanslar** sayfasını kullanırken, belirli bir ürünün lisanslarını en çok 20 kullanıcıya atarsiniz. Lisanslar **sayfasında** , abonelikleriniz olan tüm ürünlerin listesini görebilirsiniz. Ayrıca her ürün için toplam lisans sayısını, kaç lisansın atandığı ve kaç tane kullanılabilir lisans olduğunu da görüyorsunuz.

::: moniker range="o365-worldwide"

1. Yönetim merkezinde Fatura Lisansları **sayfasına** \> gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim merkezinde Fatura Lisansları **sayfasına** \> gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank"></a>

::: moniker-end

2. Bir ürün seçin.

3. Ürün ayrıntıları sayfasında Lisans **ata'ya tıklayın**.

4. Kullanıcılara **lisans ata bölmesinde** , bir ad yazmaya başlayın ve ardından sonuçlardan bu adı listeye ekleyin. Tek seferde en fazla 20 kullanıcı ekleyebilirsiniz.

4. Belirli **öğelere erişim atamak veya kaldırmak için Uygulamaları** ve hizmetleri aç veya kapat'ı seçin.

6. Bitirdikten sonra Ata'ya ve **sonra Kapat'a** **seçin**.

Çakışma olursa, bir ileti görüntülenir, sorunun ne olduğunu ve nasıl düzeltileceklerini size söyler. Örneğin, çakışan hizmetler içeren lisansları seçtiysanız, hata iletisi her lisansta bulunan hizmetleri gözden geçirmeyi ve yeniden denemeyi söylüyor.

## <a name="change-the-apps-and-services-a-user-has-access-to"></a>Kullanıcının erişim izni olan uygulamaları ve hizmetleri değiştirme

::: moniker range="o365-worldwide"

1. Yönetim merkezinde Fatura Lisansları **sayfasına** \> gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim merkezinde Fatura Lisansları **sayfasına** \> gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=850625" target="_blank"></a>

::: moniker-end

2. Lisanslar **sayfasında** , belirli bir kullanıcı için satırı seçin.

3. Sağ bölmede, erişim vermek veya erişimi kaldırmak istediğiniz uygulamaları ve hizmetleri seçin veya seçimleri kaldırın.

4. Bitirdikten sonra Kaydet'i ve **sonra Kapat'ı** **seçin**.

## <a name="use-the-active-users-page-to-assign-licenses"></a>Lisans atamak için Etkin kullanıcılar sayfasını kullanma

Lisans atamak için **Etkin kullanıcılar** sayfasını kullanırken, kullanıcılara ürün lisansları atarsiniz.

### <a name="assign-licenses-to-multiple-users"></a>Birden çok kullanıcıya lisans atama

::: moniker range="o365-worldwide"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

::: moniker-end

2. Lisans atamak istediğiniz kullanıcıların adlarının yanındaki daireleri seçin.

3. Üst kısmında Ürün lisanslarını **yönet'i seçin**.

4. Ürün **lisanslarını yönet bölmesinde Daha** fazla ata **: Mevcut lisansları saklay ve daha fazla lisans ata'ya** \> **tıklayın**.

5. **Lisanslar'ın** altında, seçili kullanıcılara sahip olmak istediğiniz lisansların kutusunu seçin.\
    Varsayılan olarak, bu lisanslarla ilişkili tüm hizmetler kullanıcılara otomatik olarak atanır. Kullanıcıların hangi hizmetleri kullanılabilir olduğunu sınırlandırabilirsiniz. Kullanıcıların sahip istemelerini istemediğiniz hizmetlerin kutularının seçimini kaldırın.

6. Bölmenin en altında Değişiklikleri **kaydet'i seçin**.  
    Herkes için yeterli lisansınız yoksa ek lisans satın almak zorundaysanız.

> [!NOTE]
> Çok fazla sayıda kullanıcıya lisans atamak için, Grup üyeliğini kullanarak kullanıcılara [lisans ata'Azure Active Directory](/azure/active-directory/enterprise-users/licensing-groups-assign)

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

Konuk kullanıcıları, yönetim merkezinden kuruluşla işbirliğine Azure Active Directory davet edin. Konuk kullanıcılar hakkında bilgi edinmek için bkz. [Azure Active Directory B2B'de konuk kullanıcı erişimi nedir?](/azure/active-directory/external-identities/what-is-b2b) Konuk kullanıcınız yoksa bkz. Hızlı Başlangıç [: Azure portalında dizininize konuk kullanıcılar ekleme](/azure/active-directory/external-identities/b2b-quickstart-add-guest-users-portal).

> [!IMPORTANT]
> Bu adımları yapmak için Genel yönetici olmak gerekir.

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2067268" target="_blank">Azure Active Directory yönetim merkezine gidin</a>.

2. Gezinti bölmesinde Kullanıcılar'ı **seçin**.

3. Kullanıcılar **| Tüm Kullanıcılar (Önizleme) sayfasında** Filtre **ekle'yi seçin**.

4. Alan **seçin menüsünde Kullanıcı türü'ne** **ve sonra Uygula'ya** **tıklayın**.

5. Sonraki menüde Konuk'a **tıklayın**.

6. Sonuç listesinde, lisansa ihtiyacı olan kullanıcıyı seçin.

7. **Yönet'in** altında **Lisanslar'ı seçin**.

8. **Ödevler'i seçin**.

9. Lisans **atamalarını güncelleştir** sayfasında, lisans atamak istediğiniz ürünü seçin.

10. Sağlarda, konuk kullanıcının erişmesini istediğiniz hizmetlerin onay kutularını temizleyin.

11. **Kaydet**'i seçin.

## <a name="next-steps"></a>Sonraki adımlar

Kullanıcılarınız henüz Office uygulamalarını yüklememişse, [PC veya Mac bilgisayara Microsoft 365 veya Office 2019'u](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) indirme ve yükleme ve mobil cihazda Office uygulamalarını ve e-postayı ayarlama gibi ayarlamaları yapmak için Çalışan hızlı başlangıç kılavuzunu kullanıcılarınız ile paylaşabilirsiniz[.](https://support.microsoft.com/office/7dabb6cb-0046-40b6-81fe-767e0b1f014f)[](../setup/employee-quick-setup.md)

## <a name="related-content"></a>İlgili içerik

[Abonelikleri ve lisansları anlama](../../commerce/licenses/subscriptions-and-licenses.md) (makale)\
[Kullanıcılardan lisans atamalarını iptal et](remove-licenses-from-users.md) (makale)\
[Aboneliğiniz için lisans satın alma veya kaldırma](../../commerce/licenses/buy-licenses.md) (makale)
