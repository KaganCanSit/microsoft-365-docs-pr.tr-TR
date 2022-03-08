---
title: E-posta adresinizi özel etki alanınızı kullanacak şekilde değiştirme
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
- adminvideo
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: f4d8cae9-6d06-4c4b-b4e5-6581fd05ea82
description: Bir etki alanı adı satın alıp bunu başka bir tom@fourthcoffee.com e-posta adresi gibi kolay bir e-posta adresiyle Microsoft 365.
ms.openlocfilehash: 4630b3df4719611440e92801235fde20d7bd95f4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316429"
---
# <a name="change-your-email-address-to-use-your-custom-domain"></a>E-posta adresinizi özel etki alanınızı kullanacak şekilde değiştirme

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**. 
  
::: moniker range="o365-worldwide"

E-posta adresiniz Microsoft 365 .onmicrosoft.com içerir, tom@fourthcoffee.onmicrosoft.com. Bunu tom@fourthcoffee.com gibi daha kolay anlaşılır bir adrese dönüştürebilirsiniz. İlk olarak, fourthcoffee.com gibi kendi etki alanı adınız gerekir. Buna zaten sahip olmanız harika olur! Sahip değilseniz, [etki alanı kayıt şirketinden satın almayı](../get-help-with-domains/buy-a-domain-name.md) öğrenebilirsiniz.

::: moniker-end

::: moniker range="o365-21vianet"

21Vianet tarafından Office 365 21Vianet tarafından çalıştırılan ilk e-partner.onmschina.cn e-posta adresiniz, tom@fourthcoffee.partner.onmschina.cn. Bu adresi, daha yakın ve daha tom@fourthcoffee.cn. İlk önce olduğu gibi, kendi etki fourthcoffee.cn gerekir. Buna zaten sahip olmanız harika olur! Sahip değilseniz, [etki alanı kayıt şirketinden satın almayı](../get-help-with-domains/buy-a-domain-name.md) öğrenebilirsiniz.

::: moniker-end

Etki alanı e-postanızı başka bir etki alanına gelecek şekilde Microsoft 365, kurulum sırasında etki alanınıza gönderilen TÜM e-postaların E-postası kurulum sırasında güncelleştirilerek Microsoft 365. MX kaydını değiştirmeden ÖNCE, etki alanınıza e-postası olan herkes için Microsoft 365 kutusunda kullanıcıları ve posta kutularını oluşturduğunuzdan emin olun. Etki alanınız içinde yer alan herkesin e-postalarını başka bir yere taşımak Microsoft 365? Bunun yerine yalnızca birkaç [e-Microsoft 365 e-posta adresiyle pilot uygulama adımlarını atabilirsiniz](../misc/pilot-microsoft-365-from-my-custom-domain.md).
  
## <a name="set-up-business-email-with-a-new-domain"></a>Yeni bir etki alanıyla iş e-postası ayarlama

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyVVA?autoplay=false]

E-posta adresiniz için yeni bir etki alanı adı satın alın ve e-posta adreslerini etki alanı Microsoft 365.

1. Yeni etki alanı adı için iletişim bilgileri sağlayarak, ödeme yönteminizi seçerek ve ardından siparişinizi düzenerek e-posta adresiniz için yeni bir etki alanı adı satın alın.
1. Adresin ilk kısmını (@ işareti öncesi) değiştirme veya olduğu gibi bırakma. 
1. Oturum açma Microsoft 365 ve yeni e-posta adresinizle yeniden oturum açma. Çalışan e-posta adresleriniz yeni etki alanıyla güncelleştirilir. 

## <a name="set-up-business-email-with-an-existing-domain"></a>Var olan bir etki alanıyla iş e-postası ayarlama

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxApu?autoplay=false]

Web sitesi adresi veya başka bir sağlayıcının e-posta adresi için kullanıyor olun, zaten sahip olduğunuz etki alanı adını kullanın.

1. Etki alanınızı barındıran web sitesinde oturum açma. Etki alanını otomatik olarak doğrulamak veya el ile güncelleştirmek için bir düğmeye tıklayın. 
1. E-posta adresini özelleştirin veya olduğu gibi bırakın.
1. Oturum açma Microsoft 365 ve yeni e-posta adresinizle yeniden oturum açma. Çalışan e-posta adresleriniz yeni etki alanıyla güncelleştirilir.

## <a name="change-your-email-address-to-use-your-custom-domain-using-the-microsoft-365-admin-center"></a>E-posta adresinizi, özel etki alanınız olarak değiştirmek için Microsoft 365 yönetim merkezi

Bu adımları gerçekleştirmek için genel yönetici olmak gerekir.

::: moniker range="o365-worldwide"

1. yönetim merkezine gidin <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. yönetim merkezine gidin <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank"> https://portal.partner.microsoftonline.cn</a>.

::: moniker-end

2. **SetupDomains**  >  sayfasına gidin.

3. Etki Alanları **sayfasında Etki** alanı **ekle'yi seçin**.

4. Etki alanının sahibi olduğunu onaylamak için adımları izleyin. Hemen her şeyi, aynı Microsoft 365'de etki alanınız ile doğru şekilde ayarlamak için Microsoft 365.

5. Kullanıcılar Etkin **kullanıcılar'a** >  gidin.

6. Kullanıcı adını düzenlemek ve az önce ekley istediğiniz etki alanıyla değiştirmek için bir kullanıcı seçin.

> [!NOTE]
> Exchange lisansı Exchange, kiracıdan e-posta göndermek veya almak için etki Microsoft 365.
  
## <a name="related-content"></a>İlgili içerik

[Microsoft 365 (makale](../get-help-with-domains/buy-a-domain-name.md))\ kullanarak özel etki alanı satın alma
[Etki alanlarını yönetme](/admin) (bağlantı sayfası)\
[Etki Alanları SSS](../setup/domains-faq.yml) (makale)