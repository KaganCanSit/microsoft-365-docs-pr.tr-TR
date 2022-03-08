---
title: Etki alanını kaldırma
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
- AdminSurgePortfolio
- AdminTemplateSet
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: f09696b2-8c29-4588-a08b-b333da19810c
description: Eski bir etki alanını eski etki alanında Microsoft 365 ve kullanıcıları ve grupları başka bir etki alanına taşımayı veya aboneliğinizi iptal etmeyi öğrenin.
ms.openlocfilehash: 3da47275e090296c9b192b4bd60ad19dd8cf4149
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316835"
---
# <a name="remove-a-domain"></a>Etki alanını kaldırma

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**.

Etki alanını farklı bir abonelik planına eklemek istediğiniz için mi Microsoft 365 kaldırabilirsiniz? Yoksa yalnızca aboneliğinizi iptal etmek mi istiyorsunuz? [Planınızı veya aboneliğinizi değiştirebilir](../../commerce/subscriptions/switch-to-a-different-plan.md) veya [aboneliğinizi iptal edebilirsiniz](../../commerce/subscriptions/cancel-your-subscription.md).

> [!TIP]
> Bu konudaki adımlarda yardıma ihtiyacınız varsa, [Microsoft küçük işletme uzmanıyla çalışmayı göz önünde bulundurabilirsiniz](https://go.microsoft.com/fwlink/?linkid=2186871). İş Yardımı ile, işe alımtan günlük kullanıma kadar işlerinizi büyüttükçe siz ve çalışanlarınız küçük işletme uzmanlarına 24 saat erişim elde ediyor.

### <a name="step-1-move-users-to-another-domain"></a>1. Adım: Kullanıcıları başka bir etki alanına taşıma

#### <a name="move-users"></a>Kullanıcıları taşıma

::: moniker range="o365-worldwide"

1. Yönetim merkezine <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">gidin</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim merkezine <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">gidin</a>.

::: moniker-end

2. **KullanıcılarAkaklı** >  **kullanıcılar'ı seçin**.

3. Taşımak istediğiniz tüm kullanıcıların adlarının yanındaki kutuları seçin.

4. Sayfanın üst kısmında Etki alanlarını **değiştir'i seçin**.

5. Etki alanlarını **değiştir bölmesinde** farklı bir etki alanı seçin.

Siz de kaldırmak istediğiniz etki alanındaysanız, bu işlemi kendiniz için de yapmalısınız. Hesabınızın etki alanını düzenlerken, oturumu kapatmalı ve devam etmeyi seçtiğiniz yeni etki alanını kullanarak yeniden oturum açmalısınız.

#### <a name="move-yourself"></a>Kendinizi hareket ettirin

::: moniker range="o365-worldwide"

1. Yönetim merkezine <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">gidin</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim merkezine <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">gidin</a>.

::: moniker-end

2. Kullanıcılar **Etkin** **Kullanıcılar'a**\> gidin ve listeden hesap seçin.

3. Hesap sekmesinde **Kullanıcı** adını **yönet'i seçin** ve sonra da farklı bir etki alanı seçin.

4. Üst kısmından hesap adı'nızı ve ardından OturumLarı **Out'ı seçin**.

5. Yeni etki alanıyla ve aynı parolayla oturum açma.

Kullanıcıları başka bir etki alanına taşımak için PowerShell de kullanabilirsiniz. Daha fazla bilgi için bkz. [Set-MsolUserPrincipalName](/powershell/module/msonline/set-msoluserprincipalname). Varsayılan etki alanını ayarlamak için bkz. [Set-MsolDomain](/powershell/module/msonline/set-msoldomain).

### <a name="step-2-move-groups-to-another-domain"></a>2. Adım: Grupları başka bir etki alanına taşıma

::: moniker range="o365-worldwide"

1. Yönetim merkezinde Gruplar Grupları **sayfasına** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">gidin.</a>

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">merkezinde Gruplar</a> Grupları **sayfasına** > **gidin.**

::: moniker-end

2. Grup adını seçin ve sonra Genel sekmesindeki **E-posta** adresi, **Birincil'in altında** Düzenle'yi **seçin**.

3. Açılan listeyi kullanarak başka bir etki alanı seçin.

4. **Kaydet'i ve** sonra **Kapat'ı seçin**. Kaldırmak istediğiniz etki alanıyla ilişkilendirilmiş tüm gruplar veya dağıtım liseleri için bu işlemi yineleyin.

### <a name="step-3-remove-the-old-domain"></a>3. Adım: Eski etki alanını kaldırma

::: moniker range="o365-worldwide"

> [!NOTE]
> Özel etki alanını kaldıransanız, devam etmeden [önce bkz. Özel etki](#remove-a-custom-domain) alanını kaldırma.

1. Yönetim merkezinde Etki Alanları'Ayarlar  \> gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim merkezinde Kurulum Etki Alanları **sayfasına** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">gidin.</a>

::: moniker-end

2. Etki **Alanları** sayfasında, kaldırmak istediğiniz etki alanını seçin.

3. Sağ bölmede Kaldır'ı **seçin**.

4. Ek bilgi istemlerini izleyin ve ardından Kapat'ı **seçin**.




### <a name="remove-a-custom-domain"></a>Özel etki alanını kaldırma

Aboneliğinizi iptal ediyorsanız ve özel bir etki alanı kullanıyorsanız, aboneliğinizi iptal etmek için önce birkaç ek adım gerekir. 

#### <a name="change-your-domain-nameserver-records-if-needed"></a>Etki alanı ad sunucusu kayıtlarınızı değiştirme (gerekirse)

Özel bir etki alanı ayarsanız, etki alanının diğer hizmetlerle birlikte çalışması için DNS kayıtlarını Microsoft 365 eklediysiniz. Etki alanını kaldırmadan önce, etki alanı MX kaydınız gibi DNS kayıtlarını DNS ana güncelleştirmesi gerekir.

Örneğin, DNS ana  makinenizin MX kaydını değiştirebilirsiniz. Etki alanınıza gönderilen e-posta microsoft adresinize gönderilmez ve bunun yerine yeni e-posta sağlayıcınıza gider. (MX kaydı, etki alanınıza yönlendirilen e-postanın nereye gönderileceğini belirler.)

- Ad sunucusu (NS) kayıtlarınız [Microsoft 365](../../admin/setup/add-domain.md) ad sunucularını işaret ediyorsa, NS kayıtlarınızı yeni DNS ana makinenize işaret edecek şekilde değiştirmeden (bkz. 2. Adım) MX kaydında yapılan değişiklikler etkili olmaz.

- MX kaydını güncelleştirmeden önce, kullanıcılarınıza e-postalarını değiştirmeyi plan istediğiniz tarihi ve kullanmayı planlay istediğiniz yeni e-posta sağlayıcısını haber ve girin. Ayrıca, kullanıcılarınız mevcut Microsoft e-postalarını yeni sağlayıcıya taşımak isteyen kullanıcıların bazı ek adımlar atılması gerekir.

- MX kaydını değiştirdığınız gün, verilerinizi kaydetmeye ve gerekirse MX [kaydını](/microsoft-365/commerce/subscriptions/cancel-your-subscription#save-your-data) [Office emin olun](/microsoft-365/commerce/subscriptions/cancel-your-subscription#uninstall-office-optional).

#### <a name="update-your-domain-mx-and-other-dns-records-if-youre-using-a-custom-domain"></a>Etki alanı MX ve diğer DNS kayıtlarınızı güncelleştirme (özel bir etki alanı kullanıyorsanız)

Etki alanınızı ayarlayacakken ad sunucusu (NS) kayıtlarınızı Microsoft 365'e değiştirdiysiniz, kullanmayı planlasanız DNS ana bilgisayarlarında MX kaydınızı ve diğer DNS kayıtlarınızı ayarlamalı veya güncelleştirmeli ve sonra NS kaydınızı bu DNS ana bilgisayarıyla değiştirmalısınız.

Etki alanınız ayarlanırken NS kayıtlarını değiştirmedıysanız, MX kaydını değiştir adlarını değiştirmiyorsanız postanız hemen yeni adrese çalışmaya başlar.

NS kayıtlarınızı değiştirmek için bkz[. Herhangi bir etki alanı kayıt şirketiyle Microsoft 365 ad sunucularını değiştirme](../../admin/get-help-with-domains/change-nameservers-at-any-domain-registrar.md).



## <a name="how-long-does-it-take-for-a-domain-to-be-removed"></a>Etki alanının kaldırılması ne kadar sürer?

Etki alanına güvenlik grupları, dağıtım listeleri, Microsoft 365 grupları gibi çok fazla yerde başvurulmazsa, etki alanı Microsoft 365 sürebilir. Etki alanını kullanan çok fazla başvuru varsa, etki alanının kaldırılması saatler (bir gün) sürebilir.

Yüzlerce veya binlerce kullanıcınız varsa, PowerShell kullanarak tüm kullanıcıları sorgulayın ve ardından bunları başka bir etki alanına taşıyın. Aksi takdirde, kullanıcı arabiriminde bir grup kullanıcının atlanması mümkündür ve etki alanını kaldırmayı denediğinizde bunu yapamazsınız ve neden kaldırılamadığını anlamazsınız. Daha fazla bilgi için bkz. [Set-MsolUserPrincipalName](/powershell/module/msonline/set-msoluserprincipalname). Varsayılan etki alanını ayarlamak için bkz. [Set-MsolDomain](/powershell/module/msonline/set-msoldomain).

## <a name="still-need-help"></a>Yine de yardım mı gerekiyor?

::: moniker range="o365-worldwide"

> [!NOTE]
> Hesabınızdan [".onmicrosoft.com"](../setup/domains-faq.yml) etki alanını kaldıramazsınız. Etki alanını kaldırsanız bile, kullanıcı hesapları Birincil SMTP/UserprincipalName olarak ".onmicrosoft.com" adresine geri döner.

Hala çalışmıyor mu? Etki alanınızın el ile kaldırılması gerekebilir. [Bize telefon edin](../../business-video/get-help-support.md) ve bununla ilgilenmenize yardım edelim!

::: moniker-end

::: moniker range="o365-21vianet"

> [!NOTE]
> [".partner.onmschina.cn" etki alanını hesabınızdan](../setup/domains-faq.yml) kaldırasınız. Etki alanını kaldırsanız bile, kullanıcı hesapları Birincil SMTP/UserprincipalName olarak ".partner.onmschina.cn" adresine geri döner.

Hala çalışmıyor mu? Etki alanınızın el ile kaldırılması gerekebilir. [Bize telefon edin](../../business-video/get-help-support.md?view=o365-21vianet&preserve-view=true) ve bununla ilgilenmenize yardım edelim!

::: moniker-end

## <a name="related-content"></a>İlgili içerik

[Etki Alanları SSS](../setup/domains-faq.yml) (makale)

[Farklı bir işletmeler için Microsoft 365 planına geçme](../../commerce/subscriptions/switch-to-a-different-plan.md) (makale)

[Aboneliğinizi iptal etme](../../commerce/subscriptions/cancel-your-subscription.md) (makale)
