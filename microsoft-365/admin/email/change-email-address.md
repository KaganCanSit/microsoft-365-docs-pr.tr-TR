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
description: Bir etki alanı adı satın alıp Microsoft 365'e ekleyerek e-posta adresinizi tom@fourthcoffee.com gibi kolay bir e-posta adresiyle değiştirin.
ms.openlocfilehash: 2c6085ee9c951b9afb3d44460bfd613b63375986
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66602436"
---
# <a name="change-your-microsoft-365-email-address-to-use-your-custom-domain"></a>Microsoft 365 e-posta adresinizi özel etki alanınızı kullanacak şekilde değiştirme

YouTube'da [Microsoft 365 küçük işletme yardımına](https://go.microsoft.com/fwlink/?linkid=2197659) göz atın.

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**. 
  
::: moniker range="o365-worldwide"

Microsoft 365'teki ilk e-posta adresiniz tom@fourthcoffee.onmicrosoft.com gibi .onmicrosoft.com içerir. Bunu tom@fourthcoffee.com gibi daha kolay anlaşılır bir adrese dönüştürebilirsiniz. İlk olarak, fourthcoffee.com gibi kendi etki alanı adınız gerekir. Buna zaten sahip olmanız harika olur! Sahip değilseniz, [etki alanı kayıt şirketinden satın almayı](../get-help-with-domains/buy-a-domain-name.md) öğrenebilirsiniz.

::: moniker-end

::: moniker range="o365-21vianet"

21Vianet tarafından sağlanan Office 365'deki ilk e-posta adresiniz, tom@fourthcoffee.partner.onmschina.cn gibi partner.onmschina.cn içerir. Bunu tom@fourthcoffee.cn gibi daha kolay bir adresle değiştirebilirsiniz. Önce fourthcoffee.cn gibi kendi etki alanı adınız gerekir. Buna zaten sahip olmanız harika olur! Sahip değilseniz, [etki alanı kayıt şirketinden satın almayı](../get-help-with-domains/buy-a-domain-name.md) öğrenebilirsiniz.

::: moniker-end

Kurulum sırasında etki alanınızın MX kaydını güncelleştirerek etki alanınızın e-postasını Microsoft 365'e gelecek şekilde değiştirdiğinizde, bu etki alanına gönderilen TÜM e-postalar Microsoft 365'e gelmeye başlar. MX kaydını değiştirmeden önce etki alanınızda e-postası olan herkes için Microsoft 365'te kullanıcı eklediğinizden ve posta kutuları oluşturduğunuzdan emin olun. Etki alanınızdaki herkesin e-postasını Microsoft 365'e taşımak istemiyor musunuz? [Bunun yerine yalnızca birkaç e-posta adresiyle Microsoft 365'e pilot uygulama adımlarını](../misc/pilot-microsoft-365-from-my-custom-domain.md) uygulayabilirsiniz.
  
## <a name="set-up-business-email-with-a-new-domain"></a>Yeni etki alanıyla iş e-postası ayarlama

[YouTube kanalımızda](https://go.microsoft.com/fwlink/?linkid=2198215) bu videoya ve diğer videolara göz atın.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyVVA?autoplay=false]

E-posta adresiniz için yeni bir etki alanı adı satın alın ve Microsoft 365 ile e-posta adreslerini ayarlayın.

1. Yeni etki alanı adı için iletişim bilgilerinizi sağlayarak, ödeme yönteminizi seçerek ve ardından siparişinizi vererek e-posta adresiniz için yeni bir etki alanı adı satın alın.
1. Adresin ilk bölümünü değiştirin (@ işaretinden önce) veya olduğu gibi bırakın. 
1. Microsoft 365 oturumunu kapatın ve yeni e-posta adresinizle yeniden oturum açın. Çalışan e-posta adresleriniz yeni etki alanıyla güncelleştirilir. 

## <a name="set-up-business-email-with-an-existing-domain"></a>Var olan bir etki alanıyla iş e-postası ayarlama

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxApu?autoplay=false]

İster bir web sitesi adresi için ister başka bir sağlayıcıdaki e-posta adresi için kullanıyor olun, sahip olduğunuz bir etki alanı adını kullanın.

1. Etki alanınızı barındıran web sitesinde oturum açın. Otomatik olarak doğrulamak veya etki alanını el ile güncelleştirmek için bir düğmeye tıklayın. 
1. E-posta adresini özelleştirin veya olduğu gibi bırakın.
1. Microsoft 365 oturumunu kapatın ve yeni e-posta adresinizle yeniden oturum açın. Çalışan e-posta adresleriniz yeni etki alanıyla güncelleştirilir.

## <a name="change-your-email-address-to-use-your-custom-domain-using-the-microsoft-365-admin-center"></a>Microsoft 365 yönetim merkezi kullanarak e-posta adresinizi özel etki alanınızı kullanacak şekilde değiştirme

Bu adımları gerçekleştirmek için genel yönetici olmanız gerekir.

::: moniker range="o365-worldwide"

1. Şuradan yönetim merkezine gidin: <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. konumundaki <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank"> https://portal.partner.microsoftonline.cn</a>yönetim merkezine gidin.

::: moniker-end

2. **Kurulum** > **Etki Alanları** sayfasına gidin.

3. **Etki alanları** sayfasında **Etki alanı ekle'yi** seçin.

4. Etki alanınızın sahibi olduğunuzu onaylamak için adımları izleyin. Microsoft 365'te etki alanınızla ilgili her şeyin doğru şekilde ayarlanması için size yol gösterecektir.

5. **Etkin Kullanıcılar'a** >  gidin.

6. Kullanıcı adını düzenlemek ve yeni eklediğiniz etki alanıyla değiştirmek için bir kullanıcı seçin.

> [!NOTE]
> Exchange lisansı kullanmıyorsanız, Microsoft 365 kiracısından e-posta göndermek veya almak için etki alanını kullanamazsınız.
  
## <a name="related-content"></a>İlgili içerik

[Microsoft 365 kullanarak özel etki alanı satın alma](../get-help-with-domains/buy-a-domain-name.md) (makale)\
[Etki alanlarını yönetme](/admin) (bağlantı sayfası)\
[Etki alanları hakkında SSS](../setup/domains-faq.yml) (makale)