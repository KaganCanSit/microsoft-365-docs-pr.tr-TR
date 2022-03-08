---
title: Ayarlama Microsoft 365 İş Ekstra
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
f1.keywords:
- O365E_M365SetupBanner
- BCS365_M365SetupBanner
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- TRN_SMB
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MSB365
- OKR_SMB_M365
- TRN_M365B
- OKR_SMB_Videos
- seo-marvel-mar
- AdminSurgePortfolio
- adminvideo
search.appverid:
- BCS160
- MET150
ms.assetid: 6e7a2dfd-8ec4-4eb7-8390-3ee103e5fece
description: Etki alanı ve kullanıcı ekleme Microsoft 365 İş Ekstra, güvenlik ilkelerini ayarlama ve daha fazlası için kurulum adımlarını keşfedin.
ms.openlocfilehash: b4d12d34e535a58c952a752fca63af6f67e30a61
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63312397"
---
# <a name="set-up-microsoft-365-business-premium-in-the-setup-wizard"></a>Kurulum Microsoft 365 İş Ekstra ayarları

## <a name="watch-overview-of-microsoft-365-setup"></a>İzle: Kuruluma genel Microsoft 365 görünümü

Kurulumla ilgili genel bir bakış için bu Microsoft 365 İş Ekstra izleyin.<br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4jZwg] 

## <a name="watch-set-up-microsoft-365-business-premium"></a>İzle: E-Microsoft 365 İş Ekstra

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE471FJ?autoplay=false]

1. Oturum açma penceresinde oturum <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> Kuruluma **git'i seçin**. Kurulum sihirbazı başlar.
1. Kurulumunuz tamamlandıktan sonra Microsoft yönetim merkezine geri gidin. Yönetim merkezinde Kurulum sayfasında, yönetim ilkeleri, Windows 10 gibi özellikleri ayarlamaya **devam** edebilirsiniz.

## <a name="add-your-domain-users-and-set-up-policies"></a>Etki alanınızı ve kullanıcıları ekleme ve ilkeleri ayarlama

E-Microsoft 365 İş Ekstra satın alırken, sahip olduğunuz bir etki alanını kullanma veya kayıt sırasında bir etki alanı [satın alma seçeneğiniz vardır](../admin-overview/sign-up-for-office-365.md).

- Kayıt olurken yeni bir etki alanı satın aldısanız, etki alanınız ayarlanır ve Kullanıcı ekleme ve lisans [atama'ya geçebilirsiniz](#add-users-and-assign-licenses).

### <a name="add-your-domain-to-personalize-sign-in"></a>Oturum açmanızı kişiselleştirmek için etki alanınızı ekleme

1. Genel yönetici [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) kullanarak oturum açma. 

2. Sihirbazı **başlatmak için Kuruluma** git'i seçin.

    ![Kuruluma git'i seçin.](../../media/gotosetupinadmincenter.png)

3. **Office uygulamalarınızı** yükleyin sayfasında, isteğe bağlı olarak uygulamaları kendi bilgisayarınıza yükleyebilirsiniz.
    
4. Etki alanı **ekle adımlarında** , kullanmak istediğiniz etki alanı adını girin (örneğin, contoso.com.

    > [!IMPORTANT]
    > Kayıt sırasında etki alanı satın yaptıysanız, burada Etki alanı adımı **ekle'yi** görmeyebilirsiniz. Bunun yerine Kullanıcı [ekle'ye](#add-users-and-assign-licenses) gidin.

    ![Oturum açmanızı kişiselleştirin sayfasının ekran görüntüsü.](../../media/adddomain.png)

    
4. Etki alanının size ait olduğunu [doğru yapan herhangi bir DNS barındırma sağlayıcısında DNS](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) Microsoft 365 için sihirbazda yer alan adımları izleyin. Etki alanı barındırmanızı biliyorsanız, bkz. Etki alanına [etki alanı Microsoft 365](/microsoft-365/admin/setup/add-domain).

    Barındırma sağlayıcınız GoDaddy veya etki alanı bağlantısı özelliği etkinleştirilmiş başka bir ana bilgisayarsa [, işlem](/office365/admin/get-help-with-domains/domain-connect) kolaydır ve otomatik olarak oturum açmalı ve Microsoft'un sizin adına kimlik doğrulamasına izin vermelisiniz.

    ![GoDaddy Erişimi Onayla sayfasında Yetkilendir'i seçin.](../../media/godaddyauth.png)

### <a name="add-users-and-assign-licenses"></a>Kullanıcı ekleme ve lisans atama

Sihirbaza kullanıcı eklemekle birlikte, kullanıcıları daha sonra [yönetim merkezinden](../add-users/add-users.md) de ebilirsiniz. Buna ek olarak, yerel bir etki alanı denetleyiciniz varsa[, Azure AD etki alanı denetleyicisi olan kullanıcıları Bağlan](/azure/active-directory/hybrid/how-to-connect-install-express).

#### <a name="add-users-in-the-wizard"></a>Sihirbaza kullanıcı ekleme

Sihirbaza ekley istediğiniz kullanıcılara otomatik olarak lisans Microsoft 365 İş Ekstra atanır.

![Sihirbazda Yeni kullanıcı ekle sayfasının ekran görüntüsü.](../../media/addnewuserspage.png)

1. Microsoft 365 İş Ekstra aboneliğinizin mevcut kullanıcıları varsa (örneğin, Azure AD Bağlan kullandıysanız), bu kullanıcılara şimdi lisans atama seçeneğiniz olur. Bu kullanıcılara da lisans ekleyerek işleme devam edin.

2. Kullanıcıları ekledikten sonra, kimlik bilgilerini kendi ekledikten sonra yeni kullanıcılarla paylaşma seçeneğiniz de olur. Bunları yazdırabilir, e-posta ile gönderebilir veya indirebilirsiniz.

### <a name="connect-your-domain"></a>Etki alanınızı bağlama

> [!NOTE]
> Kullanıcıları ayarlamak için .onmicrosoft etki alanını kullanmayı Bağlan Azure AD Bağlan kullandıysanız, bu adımı görmeyebilirsiniz.
  
Hizmetleri ayarlamak için DNS ana bilgisayarınızda veya etki alanı kayıt şirketinizde bazı kayıtları güncelleştirmeniz gerekir.
  
1. Kurulum sihirbazı, genellikle kayıt şirketinizi algılar ve kayıt şirketinin web sitesinde NS kayıtlarınızı güncelleştirmek için adım adım yönergelere ulaşabileceğiniz bir bağlantı verir. Bunu yoksa, herhangi bir [etki alanı kayıt şirketiyle etki alanı Microsoft 365 ad sunucularını değiştirebilirsiniz](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md). 

    - Mevcut DNS kayıtlarınız, örneğin var olan bir web siteniz varsa, ancak DNS barındırma hizmetiniz etki alanı bağlantısı için etkinleştirilmişse [, Kayıtları](/office365/admin/get-help-with-domains/domain-connect) benim için **ekle'yi seçin**. Çevrimiçi **hizmetlerinizi seçin sayfasında**, tüm varsayılanları kabul edin ve Sonraki'yi seçin ve DNS barındırma hizmet  barındırması sayfasında Yetkilendir'i seçin.
    - Diğer DNS ana bilgisayarlarında mevcut DNS kayıtlarınız varsa (etki alanı bağlantısı için etkin değil), var olan hizmetlerin bağlı kalacağından emin olmak için kendi DNS kayıtlarınızı yönetmek istemeniz gerekir. Daha [fazla bilgi için etki alanı](/office365/admin/get-help-with-domains/dns-basics) temel bilgilerine bakın.

        ![Kayıtları etkinleştirme sayfası.](../../media/activaterecords.png)

2. Sihirbazda adımları izleyin; sizin için e-posta ve diğer hizmetler ayarlanır.

### <a name="protect-your-organization"></a>Organizasyonlarınızı koruma 

Sihirbazda ayar ilkeleri otomatik olarak Tüm Kullanıcılar adında bir [Güvenlik](/office365/admin/create-groups/compare-groups#security-groups) grubuna *uygulanır*. Ayrıca, yönetim merkezinde ilke atamak için ek gruplar da oluşturabilirsiniz.

1. Gelişmiş **siber tehditlere karşı** korumayı artır korumada, Tehdit Koruması'nın Office 365 uygulamalarına yönelik dosyaları ve [](../../security/office-365-security/defender-for-office-365.md) bağlantıları taramasına izin verme varsayılanlarını Office önerilir.

    ![Korumayı artır sayfasının ekran görüntüsü.](../../media/increasetreatprotection.png)


2. Hassas veri **sızıntılarını** önle sayfasında, Office uygulamaları içinde hassas verileri izlemek ve bunların yanlışlıkla kuruluş dışında paylaşımını önlemek için Office 365 Veri Kaybı Önleme 'i (DLP) açmak için varsayılanları kabul edin.

3. Mobil cihazlar **için mobil Office** altında verileri koru sayfasında, mobil uygulama yönetimini açık bırakın, ayarları genişletin ve gözden geçirin ve ardından Mobil uygulama yönetimi **ilkesi oluştur'a tıklayın**.

    ![Mobil için Mobil cihazlar sayfasındaki Office ekran görüntüsü.](../../media/protectdatainmobile.png)


## <a name="secure-windows-10-pcs"></a>Bilgisayarlarda Windows 10 sağlama

Sol gezintide Kurulum'u **seçin ve** oturum açma ve **güvenlik'in** altında Bilgisayar **güvenliği'Windows 10 seçin**. Çalışmaya **başlamak için** Görüntüle'yi seçin. Tüm [yönergeler için Windows 10 bilgisayarlarınızı](secure-win-10-pcs.md) güvenli hale bkz.

## <a name="deploy-office-365-client-apps"></a>Office 365 istemci uygulamalarını dağıtma

Kurulum sırasında Office uygulamalarını otomatik olarak yüklemeyi seçtiysanız, kullanıcılar Windows 10 cihazlarından Azure AD'de iş kimlik bilgileriyle azure ad'de oturum Windows bu uygulamalara yüklenir.

Mobil iOS Office Android cihazlarına kullanıcı yüklemek için bkz. Mobil [cihazları Microsoft 365 İş Ekstra ayarlama](set-up-mobile-devices.md).

Ayrıca e-Office yükleyebilirsiniz. Yönergeler [için Office PC veya Mac bilgisayara yükleme hakkında bilgi](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) edinin.

## <a name="related-content"></a>İlgili içerik

[Microsoft 365 eğitim videoları için giriş](../../business-video/index.yml) (bağlantı sayfası)
