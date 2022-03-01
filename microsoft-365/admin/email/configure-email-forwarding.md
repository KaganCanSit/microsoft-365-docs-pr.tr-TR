---
title: E-posta iletmeyi yapılandırma
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: ab5eb117-0f22-4fa7-a662-3a6bdb0add74
description: E-posta iletme, kullanıcı posta kutusuna gönderilen e-Microsoft 365 posta kutusunu kuruluş içindeki veya dışındaki başka bir posta kutusuna iletmenizi sağlar.
ms.openlocfilehash: 5522d9202732ca54d1a395a83e99ae2442b68eb9
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011959"
---
# <a name="configure-email-forwarding-in-microsoft-365"></a>E-posta iletmeyi Microsoft 365

Kuruluşun yöneticisi olarak, kullanıcının posta kutusu için e-posta iletmeyi ayarlamaya şirket gereksinimleriniz olabilir. E-posta iletme, bir kullanıcının posta kutusuna gönderilen e-posta iletilerini, kuruluşun içindeki veya dışındaki başka bir kullanıcının posta kutusuna iletmenizi sağlar.

> [!IMPORTANT]
> Dış alıcılara otomatik iletmeyi kontrol etmek için giden istenmeyen posta filtresi ilkelerini kullanabilirsiniz. Daha fazla bilgi için bkz[. Dış posta iletisinde otomatik dış e-Microsoft 365](/microsoft-365/security/office-365-security/external-email-forwarding#how-the-outbound-spam-filter-policy-settings-work-with-other-automatic-email-forwarding-controls).

> [!TIP]
> Bu konudaki adımlarda yardıma ihtiyacınız varsa, [Microsoft küçük işletme uzmanıyla çalışmayı göz önünde bulundurabilirsiniz](https://go.microsoft.com/fwlink/?linkid=2186871). İş Yardımı ile, işe alımtan günlük kullanıma kadar işlerinizi büyüttükçe siz ve çalışanlarınız küçük işletme uzmanlarına 24 saat erişim elde ediyor.

## <a name="configure-email-forwarding"></a>E-posta iletmeyi yapılandırma

E-posta iletmeyi ayarlamadan önce, aşağıdakilere dikkat edin:

- Uzak etki alanındaki kişilerin otomatik olarak iletillerine izin verme. Ayrıntılar [için bkz. Uzak etki](/exchange/mail-flow-best-practices/remote-domains/manage-remote-domains) alanlarını yönetme.

- E-posta iletmeyi ayar her **zaman, posta** kutusundan gönderilen  *yalnızca yeni e-postalar*  iletebilirsiniz.

- E-posta iletme için  *, from hesabının*  lisansının var olduğu gerekir. Kullanıcı kuruluştan ayrıldığı için e-posta iletmeyi ayarıyorsanız, bir diğer seçenek de posta kutusunu [paylaşılan posta kutusuna dönüştürmektir](convert-user-mailbox-to-shared-mailbox.md). Bu şekilde, birkaç kişi bu postaya erişim iznine sahip olur. Bununla birlikte, paylaşılan bir posta kutusu 50 GB'ın üzerinde olamaz.

Bu adımları Exchange için Exchange Yöneticisi veya Microsoft 365 genel yönetici olmak gerekir. Daha fazla bilgi için Yönetici rolleri hakkında [başlığına bakın](../add-users/about-admin-roles.md).

::: moniker range="o365-worldwide"

1. Yönetim merkezinde Kullanıcılar Etkin kullanıcılar **sayfasına** \> gidin.**[](https://go.microsoft.com/fwlink/p/?linkid=834822)**

2. E-postalarını iletirken kullanmak istediğiniz kullanıcının adını seçin ve özellikler sayfasını açın.

3. Posta sekmesinde **, E-posta** iletmeyi **yönet'i seçin**.

4. E-posta iletme sayfasında Bu posta kutusuna gönderilen tüm e-postaları ilet'i **seçin, iletme** adresini girin ve iletili e-postaların bir kopyasını tutmak isteyip istemediklerini seçin. Bu seçeneği görmüyorsanız kullanıcı hesabına bir lisans atan olduğundan emin olun. Değişiklikleri **kaydet'i seçin**.

    **Birden çok e-posta adresine** iletmek için, kullanıcıdan adreslere iletmesi için Outlook bir kural ayarlamalarını sebilirsiniz. 
    
    1.  Uyarıları **Yönet'i** >  >**>** Outlook **Giriş Kuralları & açma**  
    1. Yeni **Kural Seçin** > **Listenin altına yakın bir yerde bulunan iletide** Kuralı uygula'yı seçin ve Ardından Sonraki'ye **tıklayın**.
    1. Bu **kural** , size gelen her iletiye uygulanacak sorularak Evet'i tıklatın. 
    1. Sonraki listede, eylemler bu grubu **kişiler veya ortak gruba yönlendirecek ve daha** **fazla kural işlemeyi durduracak şekilde seçin**
    1. Pencerenin alt bölümünde altı **çizili kişiler veya ortak** grup ifadesini tıklatın.
    1. **E-posta adresini** yazarak Gönder alanına postayı iletin ve ardından Tamam'a **tıklayın**.
    1. **Son'a**
    

     Veya yönetim merkezinde bir dağıtım grubu [oluşturun, adresleri](../setup/create-distribution-lists.md) buna ekleyin ve [](add-user-or-contact-to-distribution-list.md)sonra iletmeyi bu makaledeki yönergeleri kullanarak DL'ye işaret etmek üzere ayarlayın.

5. E-postayı iletirken kullanıcı hesabını silmeyin veya lisansını kaldırın!  Bunu yaparsanız, e-posta iletme durur.

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim merkezinde Kullanıcılar Etkin kullanıcılar **sayfasına** \> gidin.**[](https://go.microsoft.com/fwlink/p/?linkid=850628)**

2. Özellikler sayfasını açmak için, e-postalarını iletirken kullanmak istediğiniz kullanıcının adını seçin.

3. Posta **ayarlarını genişletin** ve E-posta iletme **bölümünde Düzenle'yi** **seçin**.

4. E-posta iletme sayfasında iki durumlu düğmeyi Açık olarak **ayarlayın, iletme** adresini girin ve iletili e-postaların bir kopyasını tutmak isteyip istemiyorsanız bunu seçin. Bu seçeneği görmüyorsanız kullanıcı hesabına bir lisans atan olduğundan emin olun. **Kaydet**'i seçin.

   **Birden çok e-posta adresine** iletmek için, kullanıcıdan adreslere iletmesi için Outlook bir kural ayarlamalarını sebilirsiniz. Daha fazla bilgi edinmek için bkz [. İletileri otomatik olarak iletmek için kuralları kullanma](https://support.microsoft.com/office/45aa9664-4911-4f96-9663-ece42816d746).

   Veya yönetim merkezinde bir dağıtım grubu [oluşturun, adresleri](../setup/create-distribution-lists.md) buna ekleyin ve [](add-user-or-contact-to-distribution-list.md)sonra iletmeyi bu makaledeki yönergeleri kullanarak DL'ye işaret etmek üzere ayarlayın.

5. E-postayı iletirken kullanıcı hesabını silmeyin veya lisansını kaldırın! Bunu yaparsanız, e-posta iletme durur.

::: moniker-end

## <a name="related-content"></a>İlgili içerik 

[Paylaşılan posta kutusu oluşturma](../email/create-a-shared-mailbox.md) (makale)\
[Farklı bir adresten e-posta gönderme](https://support.microsoft.com/office/ccba89cb-141c-4a36-8c56-6d16a8556d2e) (makale)\
[Kullanıcı adını ve e-posta adresini değiştirme](../add-users/change-a-user-name-and-email-address.md) (makale)\
[Denetim otomatik dış e-posta iletme Microsoft 365](/microsoft-365/security/office-365-security/external-email-forwarding) (makale)


