---
title: Postanıza etki Microsoft 365
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365_Setup
- Adm_O365
- Adm_TOC
ms.custom:
- TopSMBIssues
- SaRA
- MSStore_Link
- okr_smb
- business_assist
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 6383f56d-3d09-4dcb-9b41-b5f5a5efd611
description: Kurulum sihirbazını kullanarak etki alanlarınızı DNS ana Microsoft 365 dns Microsoft 365 yönetim merkezi bir DNS kaydı ekleyerek etki alanına ekleyin.
ms.openlocfilehash: eb58c8fc69a26157aa7dfb323be03efb81ef76bf
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011957"
---
# <a name="add-a-domain-to-microsoft-365"></a>Postanıza etki Microsoft 365

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](domains-faq.yml)**. 
  
## <a name="before-you-begin"></a>Başlamadan önce

Etki alanlarını eklemek, değiştirmek veya kaldırmak için, **Etki** Alanı Adı Yöneticisi  veya bir işletme veya  kuruluş planının Genel [Yöneticisi olun.](https://products.office.com/business/office) Bu değişiklikler kiracının tamamını etkiler; *Özelleştirilmiş yöneticiler* *veya normal* kullanıcılar bu değişiklikleri yapacaktır.

> [!TIP]
> Bu konudaki adımlarda yardıma ihtiyacınız varsa, [Microsoft küçük işletme uzmanıyla çalışmayı göz önünde bulundurabilirsiniz](https://go.microsoft.com/fwlink/?linkid=2186871). İş Yardımı ile, işe alımtan günlük kullanıma kadar işlerinizi büyüttükçe siz ve çalışanlarınız küçük işletme uzmanlarına 24 saat erişim elde ediyor.

## <a name="watch-add-a-domain"></a>İzle: Etki alanı ekleme

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4dN8c?autoplay=false]

Şirketinizin farklı amaçlar doğrultusunda birden çok etki alanı adı olabilir. Örneğin, müşteriler zaten bu adı kullanan ve iletişimleri size ulaşılamadıklarından şirket adınıza farklı bir yazım eklemek istiyor olabilirsiniz.

1. Aşağıdaki Microsoft 365 yönetim merkezi'ı <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**seçin**</a>.
1. Özel **etki alanınızı ayarlayın alanında** **ViewManageAdd** >  etki  > **alanı'ı seçin**.
1. Eklemek istediğiniz yeni etki alanı adını girin ve Ardından Sonraki'yi **seçin**.
1. Etki alanı kayıt şirketisinde oturum açma ve ardından Sonraki'yi **seçin**.
1. Yeni etki alanınız için hizmetleri seçin.
1. NextAuthorizeNext'i  >  > **ve** ardından Son'a **seçin**. Yeni etki alanınız eklendi.

## <a name="add-a-domain"></a>Etki alanı ekleme

Etki alanı eklemek, ayarlamak veya ayarlamaya devam etmek için bu adımları izleyin. 

::: moniker range="o365-worldwide"

1. yönetim merkezine gidin <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. yönetim merkezine gidin <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end
    
2. **Etki Alanları Ayarlar** >  **gidin**. 

3. Etki alanı **ekle'yi seçin**.
    
4. Eklemek istediğiniz etki alanının adını girin ve Ardından Sonraki'yi **seçin**.
    
5. Etki alanının sahibi olduğunu nasıl doğrulamak istediğinize karar seçin.
    
    1. Etki alanı kayıt şirketiniz [Domain Bağlan](#domain-connect-registrars-integrating-with-microsoft-365) kullanıyorsa[, Microsoft kayıt](../get-help-with-domains/domain-connect.md) şirketinde oturum açmanızı ve kayıt şirketiyle bağlantınızı onaylayınarak kayıtlarınızı otomatik olarak Microsoft 365. Yönetim merkezine geri gönderilirsiniz ve Microsoft daha sonra etki alanınızı otomatik olarak doğrular.
    2. Etki alanınızı bir TXT kaydı kullanarak doğrulayabilirsiniz. Bunu seçin ve **bu** DNS kaydının kayıt şirketin web sitesine nasıl eklenileceğinin yönergelerini görmek için Sonraki'ni seçin. Bu doğrulamanın kayıt eklendikten sonra 30 dakika kadar sürebilir. 
    3. Etki alanınıza web sitesine metin dosyası  ekebilirsiniz. Kurulum sihirbazından .txt dosyasını seçin ve indirin, sonra da dosyayı web sitenizin en üst düzey klasörüne yükleyin. Dosyanın yolu şuna benzer: `http://mydomain.com/ms39978200.txt`. Web sitenize ait dosyayı bularak etki alanının sahibi olduğunu doğrulamamız gerekir.
    
6. Microsoft'un etki alanınızı kullanması için gereken DNS değişikliklerini nasıl yapmak istediğinize karar seçin.
    
    1. Etki **Alanı** kayıt şirketiniz Etki Alanı [Bağlan'i](#domain-connect-registrars-integrating-with-microsoft-365) destekliyorsa Dns kayıtlarını benim için ekle'yi seçin [. Microsoft,](../get-help-with-domains/domain-connect.md) kayıt şirketinde oturum açmanızı ve kayıt şirketiyle bağlantınızı onaylayınarak kayıtlarınızı otomatik olarak Microsoft 365.
    2. Etki **alanınıza yalnızca belirli Microsoft 365** hizmetlerini eklemek veya bunu şimdilik atlayıp daha sonra yapmak tercih ediyorsanız DNS kayıtlarını kendim ekeceğim'i seçin. **Bu seçeneği, tam olarak ne yaptığınızı biliyorsanız kullanın.**

7. *DNS* kayıtlarını kendiniz eklemeyi seçtiysanız, Sonraki'yi seçin; etki alanını ayarlamak için kayıt sunucuları web sitenize eklemeniz gereken tüm kayıtların yer olduğu bir sayfa görüntülenir. 

    Portal kayıt şirketinizi tanımazsa [bu genel yönergeleri izleyebilirsiniz.](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md)
    
    Etki alanınızın DNS barındırma sağlayıcısını veya etki alanı kayıt şirketini bilmiyorsanız, bkz. [Etki alanı kayıt yetkilinizi veya DNS barındırma hizmet sağlayıcınızı bulma](../get-help-with-domains/find-your-domain-registrar.md)
    
    Daha sonraya kadar beklemek için, tüm hizmetlerin seçimini kaldırın ve Devam'a tıklayın veya önceki etki alanı bağlantı adımlarında Diğer Seçenekler'i ve şimdilik  bunu **atla'yı seçin**.
    
8. **Son'ı** seçin- hepsi bu kadar!

## <a name="add-or-edit-custom-dns-records"></a>Özel DNS kayıtlarını ekleme veya düzenleme

Bir web sitesi veya üçüncü taraf hizmetine özel kayıt eklemek için aşağıdaki adımları izleyin.

1. Microsoft yönetim merkezinde oturum açma <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>( .

2. **Etki Alanları Ayarlar**  >  **gidin**.

3. **Etki Alanları** sayfasında bir etki alanı seçin. 
    
4. **DNS ayarlarının altında** Özel **Kayıtlar'ı seçin**; ardından Yeni **özel kayıt'ı seçin**.

5. Eklemek istediğiniz DNS kaydının türünü seçin ve yeni kayıt için bilgileri yazın.
    
6. **Kaydet**'i seçin.

## <a name="registrars-with-domain-connect"></a>Etki Alanı Hesabı olan kayıt Bağlan

[Etki Bağlan](https://www.domainconnect.org/) kayıt adları, dakikalar alan üç adımlık bir işlem Microsoft 365 etki alanınıza etki alanı eklemenize izin sağlar. 
  
Sihirbazda, etki alanının sahibi olduğunu doğrular ve ardından e-postanın Teams gibi Microsoft 365'e ve diğer Microsoft 365 hizmetleriyle birlikte etki alanınıza geldiğinde etki alanı kayıtlarınız otomatik olarak ayarlanır.
  
> [!NOTE]
> Kurulum sihirbazını başlatmadan önce tarayıcınızda tüm açılır pencere engelleyicilerini devre dışı bırakın.
  
### <a name="domain-connect-registrars-integrating-with-microsoft-365"></a>Etki Bağlan kayıt şirketleriyle tümleştirmesi Microsoft 365

- [11&amp; IONOS](https://www.1and1.com/)
- [EuroDNS](https://www.eurodns.com/)
- [Cloudflare](https://www.cloudflare.com/)
- [GoDaddy](https://www.godaddy.com/)
- [WordPress.com](https://wordpress.com/)
- [Tiryak](https://www.plesk.com/)
- [MediaTemple](https://mediatemple.net/)
- SecureServer veya WildWestDomains (SecureServer DNS barındırmayı kullanan GoDaddy satıcıları)
    - Örnekler:
        - [DomainsPricedRight](https://www.domainspricedright.com/products/domain-registration)
        - [DomainRightNow](https://www.domainrightnow.com/)

### <a name="what-happens-to-my-email-and-website"></a>E-postama ve web siteme ne olur?

Kurulumu bitirdikten sonra, etki alanınıza göre MX kaydı Microsoft 365'e işaret etmek üzere güncelleştirilir ve etki alanınıza gelen tüm e-posta Microsoft 365. E-postayı etki alanınıza alan herkes için kullanıcı Microsoft 365 ve posta kutularını aynı e-posta kutusunda ayar sayfanız olduğundan emin olun!
  
İş için kullandığınız bir web siteniz varsa, bu site bulunduğu yerde çalışmaya devam eder. Etki Bağlan kurulum adımları web sitenizi etkilemez.

### <a name="add-an-onmicrosoftcom-domain"></a>Etki alanı onmicrosoft.com ekleme

Her Microsoft 365, en fazla üç farklı etki onmicrosoft.com olabilir.

> [!NOTE]
> Etki alanı eklemek için Genel yönetici veya Etki Alanı Adı yöneticisi olun.
> Ek bir .onmicrosoft etki alanı oluşturulur ve varsayılan olarak bu etki alanı kullanılırsa SharePoint Online için yeniden SharePoint. .onmicrosoft SharePoint etki alanınız üzerinde değişiklik yapmak için [SharePoint](/sharepoint/change-your-sharepoint-domain-name) etki alanı yeniden adlandırma önizlemesini (şu anda 1.000'den az sitesi olan tüm kiracılarda kullanılabilir) kullanabilirsiniz.
> E-posta Microsoft 365 kullanıyorsanız, ilk .onmicrosoft etki alanınızı kaldırma işlemi desteklenmiyor.


Etki alanı eklemek onmicrosoft.com:

1. Microsoft yönetim merkezine ve etki **Ayarlar** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**gidin**</a>.

2. Genel Bakış **sekmesinde Etki** alanı için **Ekle'onmicrosoft.com seçin**.

Sahip olduğunuz herhangi bir etki alanını varsayılan etki alanınız olarak değiştirebilirsiniz.

## <a name="related-content"></a>İlgili içerik

[Etki Alanları SSS](domains-faq.yml) (makale)</br>
[Etki alanı nedir?](../get-help-with-domains/what-is-a-domain.md) (makale)</br>
[Microsoft 365'de etki alanı](../get-help-with-domains/buy-a-domain-name.md) adı satın alma (makale)</br>
[Etki alanınıza bağlanmak için DNS kayıtları ekleme](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) (makale)</br>
[Herhangi bir etki alanı kayıt şirketiyle etki Microsoft 365 ayarlamak için ad sunucularını](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md) değiştirme (makale)
