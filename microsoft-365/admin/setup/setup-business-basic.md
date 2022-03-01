---
title: Ayarlama Microsoft 365 İş Temel
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
- TRN_SMB
ms.custom:
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
- MOE150
- BEA160
description: Microsoft 365 İş Temel aboneliğinizi nasıl ayarlay Microsoft 365 İş Temel öğrenin.
ms.openlocfilehash: e7c616936f045bc4266c24b65342451ffeff43ef
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "62996152"
---
# <a name="set-up-microsoft-365-business-basic"></a>Ayarlama Microsoft 365 İş Temel

## <a name="watch-set-up-microsoft-365-business-basic"></a>İzle: E-Microsoft 365 İş Temel

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vk3W]

Bu videoyu faydalı bulduysanız, [küçük işletmelere ve Microsoft 365’i ilk kez kullananlara yönelik eğitim serisinin tamamına göz atın](../../business-video/index.yml).

## <a name="add-your-domain-to-personalize-sign-in"></a>Oturum açmanızı kişiselleştirmek için etki alanınızı ekleme

E-Microsoft 365 İş Temel satın alırken, sahip olduğunuz bir etki alanını kullanma veya kayıt sırasında bir etki alanı satın alma seçeneğiniz vardır.

- Kayıt olurken yeni bir etki alanı satın aldısanız, etki alanınız ayarlanır ve Kullanıcı ekleme ve lisans [atama'ya geçebilirsiniz](#add-users-and-assign-licenses).

 ::: moniker range="o365-worldwide"

1. yönetim merkezine gidin <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. yönetim merkezine gidin <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end 

2. Sihirbazı **başlatmak için Kuruluma** git'i seçin.
    
3. Etki alanı **ekle adımlarında** , kullanmak istediğiniz etki alanı adını girin (örneğin, contoso.com.

    > [!IMPORTANT]
    > Kayıt sırasında etki alanı satın yaptıysanız, burada Etki alanı adımı **ekle'yi** görmeyebilirsiniz. Bunun yerine Kullanıcı [ekle'ye](#add-users-and-assign-licenses) gidin.

    
4. Etki alanının size ait olduğunu [doğrulayanın, herhangi bir DNS](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) barındırma sağlayıcısında DNS Office 365 için sihirbazda yer alan adımları izleyin. Etki alanı barındırmanızı biliyorsanız, bkz. Etki alanına [etki alanı Microsoft 365](/microsoft-365/admin/setup/add-domain).

    Barındırma sağlayıcınız GoDaddy veya etki alanı bağlantısı özelliği etkinleştirilmiş başka bir ana bilgisayarsa [, işlem](/office365/admin/get-help-with-domains/domain-connect) kolaydır ve otomatik olarak oturum açmalı ve Microsoft'un sizin adına kimlik doğrulamasına izin vermelisiniz.

    ![GoDaddy Erişimi Onayla sayfasında Yetkilendir'i seçin.](../../media/godaddyauth.png)

## <a name="add-users-and-assign-licenses"></a>Kullanıcı ekleme ve lisans atama

Sihirbaza kullanıcı eklemekle birlikte, kullanıcıları daha sonra [yönetim merkezinden](../add-users/add-users.md) de ebilirsiniz. Buna ek olarak, yerel bir etki alanı denetleyiciniz varsa[, Azure AD etki alanı denetleyicisi olan kullanıcıları Bağlan](/azure/active-directory/hybrid/how-to-connect-install-express).

## <a name="add-users-in-the-wizard"></a>Sihirbaza kullanıcı ekleme

Sihirbaza ekley istediğiniz kullanıcılara otomatik olarak lisans Microsoft 365 İş Temel atanır.

1. Microsoft 365 İş Temel aboneliğinizin mevcut kullanıcıları varsa (örneğin, Azure AD Bağlan kullandıysanız), bu kullanıcılara şimdi lisans atama seçeneğiniz olur. Bu kullanıcılara da lisans ekleyerek işleme devam edin.

2. Kullanıcıları ekledikten sonra, kimlik bilgilerini kendi ekledikten sonra yeni kullanıcılarla paylaşma seçeneğiniz de olur. Bunları yazdırabilir, e-posta ile gönderebilir veya indirebilirsiniz.

## <a name="connect-your-domain"></a>Etki alanınızı bağlama

> [!NOTE]
> Kullanıcıları ayarlamak için .onmicrosoft etki alanını kullanmayı Bağlan Azure AD Bağlan kullandıysanız, bu adımı görmeyebilirsiniz.
  
Hizmetleri ayarlamak için DNS ana bilgisayarınızda veya etki alanı kayıt şirketinizde bazı kayıtları güncelleştirmeniz gerekir.
  
1. Kurulum sihirbazı, genellikle kayıt şirketinizi algılar ve kayıt şirketinin web sitesinde NS kayıtlarınızı güncelleştirmek için adım adım yönergelere ulaşabileceğiniz bir bağlantı verir. Bu şekilde ayarlanamazsa, [ad sunucularını değiştirarak herhangi bir etki Office 365 alanı kayıt şirketiyle bağlantı kurabilirsiniz](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md). 

    - Mevcut DNS kayıtlarınız, örneğin var olan bir web siteniz varsa, ancak DNS barındırma hizmetiniz etki alanı bağlantısı için etkinleştirilmişse [, Kayıtları](/office365/admin/get-help-with-domains/domain-connect) benim için **ekle'yi seçin**. Çevrimiçi **hizmetlerinizi seçin sayfasında**, tüm varsayılanları kabul edin ve Sonraki'yi seçin ve DNS barındırma hizmet  barındırması sayfasında Yetkilendir'i seçin.
    - Diğer DNS ana bilgisayarlarında mevcut DNS kayıtlarınız varsa (etki alanı bağlantısı için etkin değil), var olan hizmetlerin bağlı kalacağından emin olmak için kendi DNS kayıtlarınızı yönetmek istemeniz gerekir. Daha [fazla bilgi için etki alanı](/office365/admin/get-help-with-domains/dns-basics) temel bilgilerine bakın.

2. Sihirbazda adımları izleyin; sizin için e-posta ve diğer hizmetler ayarlanır.

    Kayıt işlemi tamamlandığında, kullanıcıları ekp lisansları ataydığınız yönetim merkezine yönlendirildiniz. İlk kurulumu tamamlandıktan sonra, yönetim merkezinde bulunan Kurulum sayfasını  kullanarak abonelikleri ile birlikte gelen hizmetleri ayarlamaya ve yapılandırmaya devam edebilirsiniz.

    Kurulum sihirbazı ve yönetim merkezi Kurulum sayfası hakkında daha fazla **bilgi** için bkz. Kurulum sihirbazı [ile Kurulum sayfası arasındaki fark.](o365-setup-wizard-and-setup-page.md)