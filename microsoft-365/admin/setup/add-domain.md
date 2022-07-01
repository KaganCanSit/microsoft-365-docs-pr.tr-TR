---
title: Microsoft 365'e etki alanı ekleme
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
- Adm_O365_Setup
- Adm_O365
- Adm_TOC
ms.custom:
- adminvideo
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
description: DNS ana bilgisayarınızda bir DNS kaydı ekleyerek etki alanınızı Microsoft 365 yönetim merkezi Microsoft 365'e eklemek için kurulum sihirbazını kullanın.
ms.openlocfilehash: be72f10727a5d4ed168740d80eb04078584137d9
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66602910"
---
# <a name="add-a-domain-to-microsoft-365"></a>Microsoft 365'e etki alanı ekleme

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](domains-faq.yml)**.

YouTube'da [Microsoft 365 küçük işletme yardımına](https://go.microsoft.com/fwlink/?linkid=2197659) göz atın.
  
## <a name="before-you-begin"></a>Başlamadan önce

Etki alanlarını eklemek, değiştirmek veya kaldırmak için, bir [işletme veya kurumsal planın](https://products.office.com/business/office) **Etki Alanı Adı Yöneticisi** veya **Genel Yöneticisi** **olmanız gerekir**. Bu değişiklikler kiracının tamamını etkiler; *Özelleştirilmiş yöneticiler* veya *normal kullanıcılar* bu değişiklikleri yapamaz.

> [!TIP]
> Bu konuda verilen adımlarla ilgili yardıma ihtiyacınız varsa[bir Microsoft küçük işletme uzmanıyla çalışmayı](https://go.microsoft.com/fwlink/?linkid=2186871) göz önünde bulundurun. İşletme Yardımı ile, işletmenizi büyütürken katılımdan gündelik kullanıma kadar her aşamada siz ve çalışanlarınız günün 24 saati küçük işletme uzmanlarına erişebilirsiniz.

## <a name="watch-add-a-domain"></a>İzleyin: Etki alanı ekleme

[YouTube kanalımızda](https://go.microsoft.com/fwlink/?linkid=2198213) bu videoya ve diğer videolara göz atın.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4dN8c?autoplay=false]

Şirketinizin farklı amaçlar için birden çok etki alanı adına ihtiyacı olabilir. Örneğin, müşteriler zaten kullandığından ve iletişimleri size ulaşamadığından, şirketinizin adının farklı bir yazımını eklemek isteyebilirsiniz.

1. Microsoft 365 yönetim merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**Kurulum'u**</a> seçin.
1. **Özel etki alanınızı ayarlayın'ın altında**,**Etki alanı ekle'yi** **Yönet'i** >  >  seçin.
1. Eklemek istediğiniz yeni etki alanı adını girin ve **İleri'yi** seçin.
1. Etki alanı kayıt şirketinizde oturum açın ve **İleri'yi** seçin.
1. Yeni etki alanınız için hizmetleri seçin.
1. **Sonrakini Yetkile** >  **İleri'yi** >  ve ardından **Son'u** seçin. Yeni etki alanınız eklendi.

## <a name="add-a-domain"></a>Etki alanı ekleme

Etki alanı eklemek, ayarlamak veya ayarlamaya devam etmek için bu adımları izleyin. 

::: moniker range="o365-worldwide"

1. Şuradan yönetim merkezine gidin: <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Şuradan yönetim merkezine gidin: <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end
    
2. **Ayarlar** > **Etki Alanları** sayfasına gidin. 

3. **Etki alanı ekle'yi** seçin.
    
4. Eklemek istediğiniz etki alanının adını girin ve **İleri'yi** seçin.
    
5. Etki alanının sahibi olduğunuzu nasıl doğrulamak istediğinizi seçin.
    
    1. Etki alanı kayıt şirketiniz [Domain Connect](#domain-connect-registrars-integrating-with-microsoft-365) kullanıyorsa, Microsoft kayıt şirketinizde oturum açmanızı ve Microsoft 365 bağlantısını onaylamanızı sağlayarak [kayıtlarınızı otomatik olarak ayarlar](../get-help-with-domains/domain-connect.md) . Yönetim merkezine geri dönersiniz ve Microsoft etki alanınızı otomatik olarak doğrular.
    2. Etki alanınızı bir TXT kaydı kullanarak doğrulayabilirsiniz. Bu DNS kaydını kayıt şirketinizin web sitesine ekleme yönergelerini görmek için bunu seçin ve **İleri'yi** seçin. Bu, kaydı ekledikten sonra doğrulanması 30 dakika kadar sürebilir. 
    3. Etki alanınızın web sitesine bir metin dosyası ekleyebilirsiniz. Kurulum sihirbazından .txt dosyasını seçip indirin, ardından dosyayı web sitenizin en üst düzey klasörüne yükleyin. Dosyanın yolu şuna benzer olmalıdır: `http://mydomain.com/ms39978200.txt`. Web sitenizde dosyayı bularak etki alanının sahibi olduğunuzu onaylarız.
    
6. Microsoft'un etki alanınızı kullanması için gereken DNS değişikliklerini nasıl yapmak istediğinizi seçin.
    
    1. Kayıt şirketiniz [Domain Connect'i](#domain-connect-registrars-integrating-with-microsoft-365) destekliyorsa **DNS kayıtlarını benim için ekle'yi** seçin; Microsoft kayıt şirketinizde oturum açıp Microsoft 365 bağlantısını onaylamanızı sağlayarak [kayıtlarınızı otomatik olarak ayarlar](../get-help-with-domains/domain-connect.md).
    2. Etki alanınıza yalnızca belirli Microsoft 365 hizmetlerini eklemek istiyorsanız veya bunu şimdilik atlayıp daha sonra yapmak istiyorsanız **DNS kayıtlarını kendim ekleyeceğim'i** seçin. **Bu seçeneği, tam olarak ne yaptığınızı biliyorsanız kullanın.**

7. *DNS kayıtlarını kendiniz eklemeyi* seçtiyseniz **, İleri'yi** seçtiğinizde etki alanınızı ayarlamak için kayıt şirketleri web sitenize eklemeniz gereken tüm kayıtları içeren bir sayfa görürsünüz. 

    Portal kayıt şirketinizi tanımazsa [bu genel yönergeleri izleyebilirsiniz.](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md)
    
    Etki alanınızın DNS barındırma sağlayıcısını veya etki alanı kayıt şirketini bilmiyorsanız, bkz. [Etki alanı kayıt yetkilinizi veya DNS barındırma hizmet sağlayıcınızı bulma](../get-help-with-domains/find-your-domain-registrar.md)
    
    Daha sonrasını beklemek istiyorsanız, tüm hizmetlerin seçimini kaldırın ve **Devam'a** tıklayın veya önceki etki alanı bağlantısı adımında **Diğer Seçenekler'i** ve **şimdilik bunu atla'yı** seçin.
    
8. **Son'u** seçin- işiniz bitti!

## <a name="add-or-edit-custom-dns-records"></a>Özel DNS kayıtlarını ekleme veya düzenleme

Bir web sitesi veya üçüncü taraf hizmeti için özel kayıt eklemek için aşağıdaki adımları izleyin.

1. adresinden Microsoft yönetim merkezinde <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>oturum açın.

2. **Ayarlar**  > **Etki Alanları** sayfasına gidin.

3. **Etki Alanları** sayfasında bir etki alanı seçin. 
    
4. **DNS ayarları'nın** altında **Özel Kayıtlar'ı** seçin; ardından **Yeni özel kayıt'ı** seçin.

5. Eklemek istediğiniz DNS kaydı türünü seçin ve yeni kaydın bilgilerini yazın.
    
6. **Kaydet**'i seçin.

## <a name="registrars-with-domain-connect"></a>Domain Connect ile kayıt şirketleri

[Domain Connect](https://www.domainconnect.org/) özellikli kayıt şirketleri, dakikalar süren üç adımlı bir işlemle etki alanınızı Microsoft 365'e eklemenize olanak sağlar. 
  
Sihirbazda yalnızca etki alanının sahibi olduğunuzu onaylayacak ve ardından etki alanınızın kayıtlarını otomatik olarak ayarlayacağız, böylece e-posta Microsoft 365'e ve Teams gibi diğer Microsoft 365 hizmetlerine gelir ve etki alanınızla çalışır.
  
> [!NOTE]
> Kurulum sihirbazını başlatmadan önce tarayıcınızda tüm açılır pencere engelleyicilerini devre dışı bırakın.
  
### <a name="domain-connect-registrars-integrating-with-microsoft-365"></a>Microsoft 365 ile tümleştiren Domain Connect kayıt şirketleri

- [1&amp;1 IONOS](https://www.1and1.com/)
- [EuroDNS](https://www.eurodns.com/)
- [Cloudflare](https://www.cloudflare.com/)
- [Godaddy](https://www.godaddy.com/)
- [WordPress.com](https://wordpress.com/)
- [Plesk](https://www.plesk.com/)
- [MediaTemple](https://mediatemple.net/)
- SecureServer veya WildWestDomains (SecureServer DNS barındırma kullanan GoDaddy kurumsal bayileri)
    - Örnekler:
        - [DomainsPricedRight](https://www.domainspricedright.com/products/domain-registration)
        - [DomainRightNow](https://www.domainrightnow.com/)

### <a name="what-happens-to-my-email-and-website"></a>E-postama ve web siteme ne olur?

Kurulumu tamamladıktan sonra, etki alanınızın MX kaydı Microsoft 365'e işaret edecek şekilde güncelleştirilir ve etki alanınızın tüm e-postaları Microsoft 365'e gelmeye başlar. Etki alanınızda e-posta alan herkes için Microsoft 365'te kullanıcı eklediğinizden ve posta kutularını ayarladığınızdan emin olun!
  
İş için kullandığınız bir web siteniz varsa, bu site bulunduğu yerde çalışmaya devam eder. Etki Alanı Bağlantısı kurulum adımları web sitenizi etkilemez.

### <a name="add-an-onmicrosoftcom-domain"></a>onmicrosoft.com etki alanı ekleme

Her Microsoft 365 kuruluşunda en fazla beş onmicrosoft.com etki alanı olabilir.

> [!NOTE]
> Etki alanı eklemek için Genel yönetici veya Etki Alanı Adı yöneticisi olmanız gerekir.
> Ek bir .onmicrosoft etki alanı oluşturmak ve bunu varsayılan olarak kullanmak SharePoint Online için yeniden adlandırma yapmaz. .onmicrosoft SharePoint etki alanınızda değişiklik yapmak için [SharePoint etki alanı yeniden adlandırma önizlemesini](/sharepoint/change-your-sharepoint-domain-name) kullanmanız gerekir (şu anda 1.000'den az sitesi olan tüm kiracılarda kullanılabilir).
> Microsoft 365 posta hizmetlerini kullanıyorsanız, ilk .onmicrosoft etki alanınızın kaldırılması desteklenmez.


onmicrosoft.com etki alanı eklemek için:

1. Microsoft 365 yönetim merkezi **Ayarlar'ı** ve ardından **Etki Alanları'nı** seçin.

2. Mevcut bir *.onmicrosoft.com* etki alanını seçin.

    ![Etki alanları sayfası.](../../media/onmicrosoft-domains.png)
  

3. **Genel Bakış** sekmesinde **onmicrosoft.com etki alanı ekle'yi** seçin.

    ![Etki alanı özelliklerinin ekran görüntüsü.](../../media/add-onmicrosoft-domain-link.png)

4. **Onmicrosoft etki alanı ekle** sayfasındaki **Etki alanı adı** kutusuna yeni onmicrosoft.com etki alanınızın adını girin. 

    ![Onmicrosoft etki alanı ekle'nin ekran görüntüsü.](../../media/add-an-onmicrosoftcom-domain-page.png)

    > [!NOTE]
    > Girdiğiniz etki alanı adının yazım ve doğruluğunu doğruladığınızdan emin olun. Beş onmicrosoft.com etki alanıyla sınırlısınız ve şu anda oluşturulduktan sonra silinemezler.     

5. **Etki alanı ekle'yi** seçin. Başarıyla eklendiğinde bunu belirten bir ileti görürsünüz. 
    
    ![Başarıyla eklenen etki alanının ekran görüntüsü.](../../media/domain-added.png)

Sahip olduğunuz herhangi bir etki alanını varsayılan etki alanınız olarak ayarlayabilirsiniz. 

onmicrosoft.com etki alanı ekleme hakkında daha fazla bilgi için bkz. [onmicrosoft.com etki alanınızı ekleme veya değiştirme](add-or-replace-your-onmicrosoftcom-domain.md).

## <a name="related-content"></a>İlgili içerik

[Etki alanları hakkında SSS](domains-faq.yml) (makale)</br>
[Etki alanı nedir?](../get-help-with-domains/what-is-a-domain.md) (makale)</br>
[Microsoft 365'te etki alanı adı satın alma](../get-help-with-domains/buy-a-domain-name.md) (makale)</br>
[Etki alanınıza bağlanmak için DNS kayıtları ekleme](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) (makale)</br>
[Microsoft 365'i herhangi bir etki alanı kayıt şirketiyle ayarlamak için ad sunucularını değiştirme](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md) (makale)
