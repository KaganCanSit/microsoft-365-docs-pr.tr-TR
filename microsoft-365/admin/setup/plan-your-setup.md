---
title: İş için Microsoft 365 kurulumunuzu planlama
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
- Adm_O365_Setup
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- adminvideo
search.appverid:
- MET150
- MOE150
ms.assetid: eb926624-018b-4486-bf11-5fba6ee4d645
description: İş için Microsoft 365'e geçiş yapma gereksinimleri ve dikkat edilmesi gerekenler hakkında bilgi edinin.
ms.openlocfilehash: 356d4cc1f696c871badcdceeb392c74b510cb49c
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66601168"
---
# <a name="plan-your-setup-of-microsoft-365-for-business"></a>İş için Microsoft 365 kurulumunuzu planlama

YouTube'da [Microsoft 365 küçük işletme yardımına](https://go.microsoft.com/fwlink/?linkid=2197659) göz atın.

Bu makale, iş için Microsoft 365 planına abone olan kişilere yöneliktir.
  
Kuruluşunuzu Microsoft 365'e taşımadan önce karşılamanız gereken gereksinimler, elinizde olması gereken bilgiler ve vermeniz gereken kararlar vardır.

## <a name="overview-of-microsoft-365-for-business-setup"></a>İş için Microsoft 365 kurulumuna genel bakış

[YouTube kanalımızda](https://go.microsoft.com/fwlink/?linkid=2197910) bu videoya ve diğer videolara göz atın.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Vjso?autoplay=false]

Microsoft 365 ile işletmenizi buluta taşıma kararınız için tebrikler! İşletmenizde bir kişi veya 20 kişi olsun, küçük bir planlama yapmak, microsoft 365 İş'i en iyi şekilde kullanmanıza yardımcı olur.

## <a name="info-to-have-on-hand-before-you-run-the-setup-wizard"></a>Kurulum sihirbazını çalıştırmadan önce elinizde olması gereken bilgiler

Kurulum sihirbazını çalıştırmaya ve etki alanınızı Microsoft 365'e taşımaya hazır olduğunuzda, elinizde olması gereken bilgiler şunlardır:
  
- Microsoft 365'e eklemek istediğiniz kişilerin listesi. Bunları Zaten Microsoft 365'e eklemiş olsanız bile, etki alanı bilgilerinizi güncelleştiriyorsanız, bunların adlarını buraya girmeniz gerekir.

- Oturum açabilmeleri için çalışanlarınıza kullanıcı kimliklerini ve parolalarını nasıl bildireceksiniz? Bilgileri çalışanlarınızı arayarak mı bildireceksiniz? Yoksa kişisel e-posta adreslerine mi göndereceksiniz? E-postalarına erişemezler, bu nedenle bunu kullanamazsınız.

- Kuruluşunuz için bir etki alanı adınız varsa (contoso.com gibi) **ve** Microsoft e-postasını kullanmayı planlıyorsanız, etki alanınızın nereye kaydedildiğini bilmeniz ve oturum açma bilgilerine sahip olmanız gerekir.

## <a name="what-happens-when-you-run-the-microsoft-365-setup-wizard"></a>Microsoft 365 kurulum sihirbazını çalıştırdığınızda ne olur?

Kurulum sihirbazı, Microsoft 365 uygulamalarını bilgisayarınıza yükleme, etki alanınızı ekleme ve doğrulama, kullanıcılar ekleme ve lisans atama ve etki alanınızı bağlama konusunda size yol gösterir.

> [!NOTE]
> İş [için Microsoft 365'te yönetici rollerini](../add-users/assign-admin-roles.md) sihirbazda eklediğiniz kullanıcılara atamanız gerekiyorsa, bunu daha sonra **Kullanıcılar** sayfasında yapabilirsiniz. 
  
Kurulum sihirbazını tamamlamazsanız, kurulum görevlerini istediğiniz zaman [yönetim merkezi](https://go.microsoft.com/fwlink/p/?linkid=2024339) > **Kurulum'dan** tamamlayabilirsiniz. Buradan e-postayı ve kişileri başka bir e-posta hizmetinden geçirebilir, yönetici hesabınızın etki alanını değiştirebilir, fatura bilgilerinizi yönetebilir, kullanıcı ekleyebilir veya kaldırabilir, parolaları sıfırlayabilir ve diğer iş işlevlerini gerçekleştirebilirsiniz. Kurulum sihirbazı ile **Kurulum** sayfası arasındaki farklar hakkında daha fazla bilgi için bkz. [Microsoft 365 kurulum sihirbazı ile Kurulum sayfası arasındaki farklar](o365-setup-wizard-and-setup-page.md).

Herhangi bir noktada takılırsanız bizi arayın. [Yardımcı olmak için buradayız!](../../business-video/get-help-support.md).
  
## <a name="when-not-to-use-the-setup-wizard-active-directory-synchronization-and-hybrid-environments"></a>Kurulum sihirbazı hangi durumlarda kullanılmaz? Active Directory eşitlemesi ve karma ortamlar

Verileri veya kullanıcıları şirket içi ortamlardan geçirmeyi veya dizin eşitlemesi içeren bir karma sistem ayarlamayı içeren birkaç senaryo vardır. Herhangi bir kategorideyseniz şu makalelerdeki yönergeleri izleyin:
  
- şirket içi Active Directory dizin eşitlemesini ayarlamak için bkz. [Microsoft 365 için dizin eşitlemesini ayarlama ve Microsoft 365'teki](../../enterprise/set-up-directory-synchronization.md) farklı kimlik modellerini anlamak [için Microsoft 365 için kimlik altyapınızı dağıtma makalesini](../../enterprise/deploy-identity-solution-overview.md) okuyun.

- Exchange karmasını ayarlamak için, karma exchange ayarlamanın (DNS kayıtlarını ayarlama dahil) tüm farklı yollarında size yol gösteren yönergelerin tamamı burada bulunabilir: [Exchange Server Dağıtım Yardımcısı](/exchange/exchange-deployment-assistant)

- SharePoint karma ayarlaması, özellikle de karma arama ve site özellikleri için, bkz. [SharePoint'te Karma Arama](/SharePoint/hybrid/hybrid-search-in-sharepoint).

## <a name="move-to-microsoft-365-all-at-once-or-in-stages"></a>Microsoft 365'e bir kerede veya aşamalı olarak gitme

- **Kuruluşunuzun tümünü aynı anda Microsoft 365'e taşımak istiyor musunuz?** Öyleyse, etki alanınızı hemen Microsoft 365'e taşımayı planlayın. Microsoft 365 kurulum sihirbazını çalıştırarak başlayın; etki alanınızı ayarlamanızı ister.

- **Microsoft 365'e aşamalı olarak geçmek istiyor musunuz?** Microsoft 365'e aşamalı olarak geçmek istiyorsanız Microsoft 365 kurulum sihirbazını çalıştırmayı atlayın ve Microsoft 365 özelliklerini aşağıdaki sırayla benimsemeyi göz önünde bulundurun:

    1. Office uygulamalarını indirip yükleyebilmeleri [için çalışanlarınızı Microsoft 365'e ekleyin](../add-users/add-users.md).

    2. Word, Excel ve PowerPoint'i bilgisayarınızda ve cihazlarınızda kullanmak için [Office uygulamalarını indirin ve yükleyin](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658).

    3. [Toplantılarınızda kullanmak üzere Microsoft Teams'i ayarlayın](#plan-for-teams) .

    4. [İçeriğinizi Microsoft 365 bulut depolama alanına](set-up-file-storage-and-sharing.md) (OneDrive veya SharePoint ekip siteleri) taşıyın.

    5. Hazır olduğunuzda, [yönetim merkezinde](https://go.microsoft.com/fwlink/p/?linkid=2024339) sol gezinti bölmesinde **Kurulum'u** seçin ve [etki alanınızı ve e-postanızı taşımak](add-domain.md) için **Kurulum** sayfasını kullanın.

## <a name="check-that-your-devices-meet-system-requirements"></a>Cihazlarınızın sistem gereksinimlerini karşılayıp karşılamadığını denetleyin.

Kuruluşunuzdaki her kişi Office 2016 uygulama paketini (Word, Excel, PowerPoint vb.) en fazla beş pc ve Mac bilgisayara yükleyebilir. İş için [Office 2016 paketlerini](https://go.microsoft.com/fwlink/?LinkId=534827) yüklemeye yönelik işletim sistemi ve bilgisayar gereksinimlerine göz atın.
  
Mobil uygulamalar iOS, Android ve Windows cihazlarına yüklenebilir. [Office için sistem gereksinimleri](https://go.microsoft.com/fwlink/?LinkId=534827) konusunda, mobil cihaz ve tarayıcı desteği hakkında bilgi edinebilirsiniz.
  
## <a name="plan-for-email"></a>E-postayı planlama

Mevcut bir e-posta hizmetinden Microsoft 365'e geçmeyi planlıyorsanız, geçişin yapılması genellikle iki gün sürer.
  
### <a name="plan-for-email-downtime"></a>E-postanın kapalı kalma süresini planlama
  
E-postanız için Microsoft 365 kullanacaksanız:
  
- İş e-posta adresinizi (örneğin *, rob\@contoso.com*) başka bir e-posta hizmetinden Microsoft 365'e taşımak için postanızı yeni Microsoft 365 posta kutunuza teslim edilecek şekilde yönlendirmeniz gerekir. Bunu, etki alanı konağınızda yapmanız gereken güncelleştirmelerde adım adım size yol gösterdiğimiz **Kurulum** sayfasında **Kullanıcılarınızın verilerini geçir'i** seçerek yaparsınız.

- Alan adı sağlayıcınızı güncelleştirdikten sonra değişikliklerin uygulanması genellikle bir veya iki saat sürer. Ancak değişikliklerin İnternet üzerinden güncelleştirilebilir olması bazen 72 saate kadar sürebilir.

- E-posta kapalı kalma süreniz olabileceği için, daha az e-posta aldığınızda bir akşam veya hafta sonunda Microsoft e-postasına geçmeyi planlamanızı öneririz.

### <a name="plan-to-move-your-existing-email-contacts-and-calendar"></a>Mevcut e-postanızı, kişilerinizi ve takviminizi taşımayı planlayın
  
E-posta hesabınız için Microsoft 365'i kullanacaksanız, mevcut e-postanızı, kişilerinizi ve takviminizi yanınızda getirebilirsiniz. **Kurulum** sayfası, çoğu senaryo için mevcut e-postanızı ve kişilerinizi taşımanıza yardımcı olur. Ayrıca bir veya daha fazla posta kutusunu taşımak için, adım adım kılavuzlarımız mevcutttur.
  
|**Kaç tane posta kutusu geçirilecek?**|**Öneri**|
|:-----|:-----|
|Yalnızca birkaç  <br/> |Posta kutularını geçirmek için **Kurulum** sayfasını kullanmak istemiyorsanız, posta kutusu sahiplerinin kendi e-postalarını ve kişilerini geçirmelerine izin vekleyebilirsiniz. Bkz [. E-postayı ve kişileri İş için Microsoft 365'e geçirme](migrate-email-and-contacts-admin.md).  <br/> |
|Birden çok  <br/> |Gmail'den geçiş gerçekleştiriyorsanız bkz. [G Suite posta kutularını Microsoft 365'e geçirme](/Exchange/mailbox-migration/migrating-imap-mailboxes/migrate-g-suite-mailboxes).  <br/> Exchange de dahil olmak üzere başka bir e-posta sağlayıcısından geçiş gerçekleştiriyorsanız bkz. [Birden çok e-posta hesabını Microsoft 365'e geçirmenin yolları](/Exchange/mailbox-migration/mailbox-migration).  <br/> |

## <a name="plan-for-file-storage-and-migration"></a>Dosya depolaması ve geçişini planlama

Microsoft 365 bireyler, küçük kuruluşlar ve kuruluşlar için bulut depolama alanı sağlar. Nerede depolayabileceğiniz konusunda rehberlik için bkz. [Microsoft 365'te belgeleri nerede depolayabilirsiniz](https://support.microsoft.com/office/d18d21a0-1f9f-4f6c-ac45-d52afa0a4a2e)?
  
- **Yüzlerce dosyayı** [OneDrive'a](https://support.microsoft.com/office/45114744-6D42-45CD-8975-F9617819BDEB) veya [bir SharePoint ekip sitesine](https://support.microsoft.com/office/da549fb1-1fcb-4167-87d0-4693e93cb7a0#__toc384119242) taşıyabilirsiniz. Tek seferde en fazla 100 dosya yükleyebilirsiniz. Varsayılan en yüksek dosya boyutu olan 2 GB'tan büyük dosyalar yüklemekten kaçının.
  
- **Birkaç bin dosyayı** Microsoft 365 depolama alanına taşımak istiyorsanız [SharePoint Online Sınırları'nı](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits) gözden geçirin. Geçiş işleminde yardımcı olması için bir geçiş aracı kullanmanızı veya [iş ortağıyla](https://go.microsoft.com/fwlink/?linkid=391089) çalışmanızı öneririz. Çok sayıda dosya geçirme hakkında bilgi edinmek için [SharePoint Online ve OneDrive Geçişi Kullanıcı Kılavuzu](/sharepointmigration/upload-on-premises-content-to-sharepoint-online-using-powershell-cmdlets)'na göz atın.
  
## <a name="plan-for-teams"></a>Teams için planlama

Microsoft Teams'i kullanarak kuruluşunuzdaki aboneliğinizdeki diğer kişilere çağrı yapabilirsiniz. Örneğin, kuruluşunuzda 10 kişi varsa, özel bir kurulum yapmadan Teams'i kullanarak birbirinizi arayabilir ve anlık ileti alabilirsiniz. Daha fazla bilgi için bkz. [Microsoft Teams'i kullanmaya başlama](/MicrosoftTeams/get-started-with-teams-quick-start).

Daha büyük kuruluşlar için veya Skype Kurumsal, şirket içi veya karma dağıtımlardan başlıyorsanız bkz. [Microsoft Teams'i dağıtma](/MicrosoftTeams/how-to-roll-out-teams).
  
## <a name="plan-for-integration-with-active-directory-or-other-software"></a>Active Directory veya başka bir yazılımla tümleştirmeyi planlama

- **Şirket içi Active Directory'nizi tümleştirmek istiyor musunuz?** Azure Active Directory Connect kullanarak şirket içi Active Directory Microsoft 365 ile tümleştirebilirsiniz. Yönergeler için bkz. [Microsoft 365 için dizin eşitlemesini ayarlama](../../enterprise/set-up-directory-synchronization.md).
  
- **Microsoft 365'i diğer şirketler tarafından üretilen yazılımlarla tümleştirmek istiyor musunuz?** Microsoft 365'i kuruluşunuzdaki diğer yazılımlarla tümleştirmeniz gerekiyorsa, dağıtımınızda size yardımcı olması için [bir iş ortağı işe](https://go.microsoft.com/fwlink/?linkid=391089) almayı düşünmenizi öneririz.
  
## <a name="do-you-want-someone-to-help-you-set-up-microsoft-365"></a>Birinin Microsoft 365'i kurmanıza yardımcı olmasını istiyor musunuz?

- **50'den daha az çalışanınız varsa:**

  - **Yardım isteyin, sizi ararız**. Microsoft 365'i satın aldıktan sonra yönetim merkezine erişebilirsiniz (buna ulaşmak için kurulumu çalıştırmanız gerekmez). Yönetim merkezinin alt kısmında **Yardım mı gerekiyor?** öğesini seçin. Sorununuzu açıklayın, sizi ararız. 
  - **Sorularınız [için Microsoft 365 İş Desteği'ne](../../business-video/get-help-support.md) başvurun**. We're here to help! 
  - **Bir [Microsoft iş ortağıyla](https://go.microsoft.com/fwlink/?linkid=391089)** çalışmayı düşünün. Zaman yetersizse veya gelişmiş gereksinimleriniz varsa (binlerce dosyayı Microsoft 365 bulut depolama alanına taşıma veya diğer yazılımlarla tümleştirme gibi) deneyimli bir iş ortağı büyük yardım sağlayabilir. 

- **50'den daha fazla çalışanınız varsa** dağıtımınıza yardımcı olmak üzere [FastTrack Ekleme Merkezi](https://go.microsoft.com/fwlink/?LinkId=517115)'ni kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

[İş için Microsoft 365 planlarının güvenliğini sağlamaya yönelik en iyi yöntemler](../security-and-compliance/secure-your-business-data.md)
