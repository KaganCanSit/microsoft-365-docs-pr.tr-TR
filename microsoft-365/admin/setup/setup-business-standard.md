---
title: Yeni Microsoft 365 İş Standart var olan bir etki alanıyla etki alanı ayarlama
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
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
- admindeeplinkMAC
- admindeeplinkEXCHANGE
search.appverid:
- MET150
- MOE150
- BEA160
description: E-Microsoft 365 İş Standart satın alırken, sahip olduğunuz bir etki alanını kullanma veya kayıt sırasında bir etki alanı satın alma seçeneğiniz vardır.
ms.openlocfilehash: 791f719f50809f2aa178ca2ab72471aea534e111
ms.sourcegitcommit: 7aa2441c1f2cc5b4b5495d6fdb993e563f86647f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64638037"
---
# <a name="set-up-microsoft-365-business-standard-with-a-new-or-existing-domain"></a>Yeni Microsoft 365 İş Standart var olan bir etki alanıyla etki alanı ayarlama

Yeni bir Microsoft 365 İş Standart, sahip olduğu bir etki alanını ekleme veya satın alma seçeneğiniz vardır. Yeni bir [abonelik için kaydolma Microsoft 365 İş Standart göz atabilirsiniz](../simplified-signup/signup-business-standard.md).

Bu makalede, size zaten sahip olduğunuz mevcut bir etki alanını ekleme veya yeni etki alanı satın alma adımlarında yoleceğiz. Kayıt olurken yeni bir etki alanı satın aldısanız, etki alanınız ayarlanır ve Kullanıcı ekleme ve lisans [atama'ya geçebilirsiniz](#add-users-and-assign-licenses).

## <a name="set-up-microsoft-365-for-business"></a>İşletmeler Microsoft 365 ayarlama

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE471FJ]

## <a name="before-you-begin"></a>Başlamadan önce

Etki alanlarını eklemek, değiştirmek veya kaldırmak için genel yönetici olasınız. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../add-users/about-admin-roles.md).

> [!IMPORTANT]
> İş için İş'e Microsoft 365 (genellikle işletme sahibi) otomatik olarak kuruluşun teknik yöneticisi olur. Diğer kişilerinizi yönetici olarak ekleyebilir ve hizmetlerinizi yönetmede yardım Microsoft 365 edin. Daha fazla [bilgi için Yönetici rolleri](../add-users/assign-admin-roles.md) atama'ya bakın.

## <a name="watch-add-an-existing-domain-to-your-microsoft-365-business-standard-subscription"></a>İzle: Microsoft 365 İş Standart aboneliğinize mevcut bir etki Microsoft 365 İş Standart ekleme

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxApu]

## <a name="steps-add-an-existing-domain-to-your-microsoft-365-business-standard-subscription"></a>Adımlar: Microsoft 365 İş Standart aboneliğinize mevcut bir etki Microsoft 365 İş Standart ekleme

1. Oturum açma **sayfasındaki Oturum açma adresinizden**, Microsoft 365 İş Standart e-posta **hesabı oluştur (gelişmiş)'i seçin**.

2. **Office uygulamalarınızı** yükleyin sayfasında, isteğe bağlı olarak uygulamaları kendi bilgisayarınıza yükleyebilirsiniz.

3. Etki alanı **ekle adımlarında** , kullanmak istediğiniz etki alanı adını girin (örneğin, contoso.com.

    > [!IMPORTANT]
    > Kayıt sırasında etki alanı satın yaptıysanız, burada Etki alanı adımı **ekle'yi** görmeyebilirsiniz. Bunun yerine Kullanıcı [ekle'ye](#add-users-and-assign-licenses) gidin.

4. Etki alanının size [ait olduğunu doğrulayana kadar, herhangi bir DNS barındırma Office 365](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) DNS kayıtları oluşturma adımlarını izleyin. Etki alanı barındırmanızı biliyorsanız, bkz. Etki alanına [etki alanı Microsoft 365](/microsoft-365/admin/setup/add-domain).

    Barındırma sağlayıcınız GoDaddy veya etki alanı bağlantısı özelliği etkinleştirilmiş başka bir ana bilgisayarsa [, işlem](/office365/admin/get-help-with-domains/domain-connect) kolaydır ve otomatik olarak oturum açmalı ve Microsoft'un sizin adına kimlik doğrulamasına izin vermelisiniz.

    ![GoDaddy Erişimi Onayla sayfasında Yetkilendir'i seçin.](../../media/godaddyauth.png)

## <a name="add-users-and-assign-licenses"></a>Kullanıcı ekleme ve lisans atama

Kullanıcıları şimdi ekleyebilirsiniz, ancak kullanıcıları [daha sonra yönetim merkezinden](../add-users/add-users.md) de eklemeniz de gerekir.

Her kullanıcıya otomatik olarak bir lisans Microsoft 365 İş Standart atanır.

1. Yeni Microsoft 365 İş Standart mevcut kullanıcılarınız varsa, bu kullanıcılara şimdi lisans atama seçeneği elde edebilirsiniz. Bu kullanıcılara da lisans ekleyerek işleme devam edin.

2. Kullanıcıları ekledikten sonra, kimlik bilgilerini kendi ekledikten sonra yeni kullanıcılarla paylaşma seçeneğiniz de olur. Bunları yazdırabilir, e-posta ile gönderebilir veya indirebilirsiniz.

## <a name="connect-your-domain"></a>Etki alanınızı bağlama
  
Hizmetleri ayarlamak için, DNS ana 2 veya etki alanı kayıt şirketinde kayıtları güncelleştirmeniz gerekir.
  
1. Kurulum sihirbazı, genellikle kayıt şirketinizi algılar ve kayıt şirketinin web sitesinde NS kayıtlarınızı güncelleştirmek için adım adım yönergelere ulaşabileceğiniz bir bağlantı verir. Bu şekilde ayarlanamazsa, [ad sunucularını değiştirarak herhangi bir etki Office 365 alanı kayıt şirketiyle bağlantı kurabilirsiniz](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md).

    - Mevcut DNS kayıtlarınız, örneğin var olan bir web siteniz varsa, ancak DNS barındırma hizmetiniz etki alanı bağlantısı için etkinleştirilmişse [, Kayıtları](/office365/admin/get-help-with-domains/domain-connect) benim için **ekle'yi seçin**. Etki **alanlarınızı seçin çevrimiçi hizmetler** varsayılanları kabul edin ve Sonraki'yi seçin ve DNS barındırma hizmet barındırması sayfasında Yetkilendir'i seçin.
    - Diğer DNS ana bilgisayarlarında mevcut DNS kayıtlarınız varsa (etki alanı bağlantısı için etkin değil), var olan hizmetlerin bağlı kalacağından emin olmak için kendi DNS kayıtlarınızı yönetmek istemeniz gerekir. Daha [fazla bilgi için etki alanı](/office365/admin/get-help-with-domains/dns-basics) temel bilgilerine bakın.

2. Sihirbazda adımları izleyin; sizin için e-posta ve diğer hizmetler ayarlanır.

    Kayıt işlemi tamamlandığında yönetim merkezine yönlendirilen yönetim merkezine yönlendirildiniz. Burada Office uygulamalarını yüklemek, etki alanlarınızı eklemek, kullanıcıları eklemek ve lisansları atamak için sihirbazı takip edersiniz. İlk kurulumu tamamlandıktan sonra, yönetim merkezinde bulunan Kurulum sayfasını  kullanarak abonelikleri ile birlikte gelen hizmetleri ayarlamaya ve yapılandırmaya devam edebilirsiniz.

    Kurulum sihirbazı ve yönetim merkezi Kurulum sayfası hakkında daha fazla **bilgi** için bkz. Kurulum sihirbazı [ile Kurulum sayfası arasındaki fark.](o365-setup-wizard-and-setup-page.md)

## <a name="watch-set-up-business-email-with-a-new-domain"></a>İzle: Yeni bir etki alanıyla iş e-postası ayarlama

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyVVA]

## <a name="steps-set-up-business-email-with-a-new-domain"></a>Adımlar: yeni bir etki alanıyla iş e-postası ayarlama

1. Oturum açma **sayfasındaki Oturum açma adresinizden**, Microsoft 365 İş Standart e-posta **hesabı oluştur (gelişmiş)'i seçin**.

2. Yeni bir etki alanı satın almak için adımları izleyin ve kullanmak istediğiniz etki alanı adını (örneğin, contoso.com). Etki alanınızı satın almayı tamamlandıktan sonra, kullanıcıları [ve](../add-users/add-users.md) lisansları ekleyebilir ve Office yönetim merkezinde lisans uygulamalarınızı yükleyebilirsiniz.

## <a name="finish-setting-up"></a>Ayarlamayı bitir

Web sitenizi, e-Outlook, Teams OneDrive için aşağıdaki adımları izleyin.

### <a name="step-set-up-outlook-for-email"></a>Adım: E-posta Outlook e-postayı ayarlama

1. Arama Windows Başlat menüsü, arama Outlook ve seçin.

    (Mac kullanıyorsanız, araç çubuğundan Outlook veya Bulici'yi kullanarak mac'i bulun.)

    Yeni bir e-Outlook, Hoş Geldiniz sayfasında Sonraki'yi **seçin**.

2. Dosya **Bilgileri Hesap** \> **Ekle'yi** \> seçin.

3. Microsoft e-posta adresinizi girin ve **Posta'Bağlan**.

## <a name="watch-set-up-outlook-for-email"></a>İzle: E-posta Outlook ayarlama

> [!VIDEO https://www.microsoft.com/videoplayer/embed/9fe86884-8a83-42cc-bca9-61a12e6dad31?autoplay=false]
  
E-posta [için E-Outlook'i ayarlama'da daha fazla bilgi edinebilirsiniz](https://support.microsoft.com/office/f5bf0cd1-e1f3-4b0d-a022-ecab17efe86f).
  
### <a name="import-email"></a>E-posta içe aktarma

Outlook başka bir e-posta hesabıyla kullanıyorsanız önceki e-posta, takvim ve kişilerinizi yeni Microsoft hesabınıza aktarabilirsiniz.
  
1. **Eski e-postanızı dışarı aktarma**

    In Outlook, choose **File** \> **Open &amp; Export** \> **Import/Export**.

    Dosyaya **Dışarı Aktar'ı seçin** ve ardından dosyanızı Veri Dosyası (.pst) Outlook alt klasörleri dışarı aktarma adımlarını izleyin.

2. **Eski e-postanızı içeri aktarma**

    Dosya Outlook Dışarı **AktarmaYı Aç'ı** \> **&amp; İçeri/Dışarı Aktarma** \> seçin.

    Bu kez, Başka **bir program veya dosyadan** içeri aktar'ı seçin ve eski e-postanızı dışarı aktararak oluşturduğunuz yedek dosyasını içeri aktarma adımlarını izleyin.

## <a name="watch-import-and-redirect-email"></a>İzle: E-postayı içeri aktarma ve yeniden yönlendirme

> [!VIDEO https://www.microsoft.com/videoplayer/embed/40f7df36-9e24-44e5-8791-e9ed0dd8fd21?autoplay=false]
  
Daha fazla bilgi [için E-postayı birlikte Outlook](https://support.microsoft.com/office/6a3771d4-4c1d-4a25-92a6-0b8e476335de).

Ayrıca, yönetim merkezini <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange e-postasını</a> içeri aktarmayı da kullanabilirsiniz. Daha fazla bilgi için bkz. [Birden çok e-posta hesabını geçirme](/Exchange/mailbox-migration/mailbox-migration).

## <a name="set-up-microsoft-teams-and-onedrive-for-business"></a>İşletmeler Microsoft Teams OneDrive ayarlama

Görev OneDrive bir bulut simgesi seçin ve dosyalarınızı yeni dosya klasörünüze taşımak için OneDrive İş izleyin. Bir **sonrakini** ayarlamak için Sonraki'Microsoft Teams.

1. İş Microsoft Teams, profil simgenizi seçin ve sonra İş **veya okul hesabı ekle'yi seçin**. Hesabınıza yeni hesap eklemek için adımları Teams.

## <a name="use-a-public-website"></a>Genel web sitesi kullanma

Microsoft 365, işletmeniz için bir genel web sitesi içermemektedir. Bir iş ortağı ayarlamak için GoDaddy veya WIX gibi bir Microsoft iş ortağını kullanabilirsiniz.
  
1. Yönetim merkezinde Kaynaklar'a gidin **ve ardından** Genel web **sitesi'ni seçin**.

2. **Seçeneklerden birinin** altında Daha fazla bilgi'yi seçin, ardından bir web sitesi iş ortağına kaydolarak kendi araçlarını kullanarak sitenizi ayarlayın ve tasarlar.

## <a name="watch-create-your-business-website"></a>İzle: İş web sitenizi oluşturma

> [!VIDEO https://www.microsoft.com/videoplayer/embed/4839abc6-9323-4cbf-a79d-2907235f9ebb]

## <a name="invite-users-to-join-your-subscription-and-organization"></a>Kullanıcıları aboneliğinize ve organizasyonunıza katılmaya davet etme

Organizasyonlarınızı bir kez ayar verdiktan sonra diğer kullanıcıları kurumsal aboneliğinize katılmaya Microsoft 365 davet edebilirsiniz. Aboneliğin tüm özelliklerine erişim elde etmelerini sağlarlar.

[Aboneliğime kullanıcıları davet et](../simplified-signup/admin-invite-business-standard.md)

Kullanıcılarınıza, organizasyonunıza ve aboneliğinize katılmak için aşağıdaki makalelerde yer alan adımları takip edeceklerini haber verme.

- [E-posta davetini kabul etme](../simplified-signup/user-invite-business-standard.md)

- [E-posta davetini e-posta Outlook, Yahoo, Gmail veya başka bir hesabı kullanarak kabul etme (Kullanıcı)](../simplified-signup/user-invite-msa-nodomain-join.md)

## <a name="related-topics"></a>İlgili konular

[Verileri Microsoft 365 İş Standart aboneliğime geçirme](../simplified-signup/migrate-data-business-standard.md)
