---
title: Karma Modern Skype Kurumsal kullanmak için şirket içinde nasıl yapılandırılan?
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 522d5cec-4e1b-4cc3-937f-293570717bc6
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: Şirket içinde karma kimlik Skype Kurumsal kullanarak, size daha güvenli kullanıcı kimlik doğrulaması ve yetkilendirme sunan Karma Modern Kimlik Doğrulama'yı (HMA) kullanmayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: dd42aa6befdbb646217a9829dd59c0821fbd29d3
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996529"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>Karma Modern Skype Kurumsal kullanmak için şirket içinde nasıl yapılandırılan?

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Modern Kimlik Doğrulama, daha güvenli kullanıcı kimlik doğrulaması ve yetkilendirme sunan bir kimlik yönetimi yöntemidir; şirket içi Skype Kurumsal ve Exchange sunucusu ile bölünmüş etki alanı karmaları için Skype Kurumsal kullanılabilir.

> [!IMPORTANT]
> Modern Kimlik Doğrulama (MA) hakkında daha fazla bilgi sahibi olmak ister misiniz ve bunu şirket veya kuruluşta neden kullanmayı tercih edersiniz? Genel [bir bakış için](hybrid-modern-auth-overview.md) bu belgeye bakın. MA tarafından desteklenen Skype Kurumsal bilmek zorundaysanız, burada belgelenmiş olur!

**Başlamadan önce** şu terimleri kullanıyoruz:

- Modern Kimlik Doğrulama (MA)

- Karma Modern Kimlik Doğrulaması (HMA)

- Exchange (EXCH)

- Exchange Online (EXO)

- Skype Kurumsal (SFB)

- Skype Kurumsal Online (SFBO)

Ayrıca, bu makaledeki grafikte gri veya soluk gösterilen bir nesne varsa, gri olarak gösterilen öğe MA'ya özgü yapılandırmaya dahil değildir.

## <a name="read-the-summary"></a>Özeti okuma

Bu özet, işlemi yürütme sırasında kaybolabilecek adımlara göre kırar ve genel denetim listesinin, işlemde neredenizi takip etmek için iyi bir uygulamadır.

1. İlk olarak, tüm önkoşullara uygun olduğundan emin olun.

1. Birçok **önkokolun** yaygın Skype Kurumsal iki Exchange, önkoşullar denetim listenizin [genel bakış makalesine bakın](hybrid-modern-auth-overview.md). Bu  *makaledeki*  adımlardan herhangi birini başlamadan önce bunu uygulayın.

1. Bir dosyada veya başka bir dosyada ihtiyacınız olacak HMA'ya özgü OneNote.

1. EXO için Modern Kimlik Doğrulama'ya (henüz açık değilse) açık olarak seçin.

1. SFBO için Modern Kimlik Doğrulamayı AÇ (henüz açık değilse).

1. Şirket içi kimlik doğrulaması için karma modern Exchange açma.

1. Şirket içi kimlik doğrulaması için karma modern Skype Kurumsal açma.

Bu adımlar SFB, SFBO, EXCH ve EXO için MA'yı, yani SFB ve SFBO'nun HMA yapılandırmasına (EXCH/EXO bağımlılıkları da dahil) katılabilirsiniz. Başka bir deyişle, kullanıcılarınız karmanın herhangi bir bölümünde (EXO + SFBO, EXO + SFB, EXCH + SFBO veya EXCH + SFB) oluşturulmuş posta kutuları varsa, ürününüz aşağıdaki gibi olur:

![Her dört olası Skype, iş HMA topolojisi için Karma 6 matris vardır.](../media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)

Gördüğünüz gibi, MA'da aç yalnızca dört farklı yer vardır! En iyi kullanıcı deneyimini yaşamak için bu konumların dörtsinde de MA'ı açmanizi öneririz. MA'ı bu konumların tümsinde açamazsanız, ma'ı yalnızca ortamınız için gereken konumlarda açacak şekilde adımları ayarlayın.

Desteklenen [topolojiler için ma ile Skype Kurumsal](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported) için Desteklanabilirlik başlığına bakın.

> [!IMPORTANT]
> Başlamadan önce önkoşulların tamamını karşıp karşılamıştınız bir kez daha kontrol edin. Bu bilgiyi Karma modern kimlik doğrulamasına [genel bakış ve önkoşullarda bulabilirsiniz](hybrid-modern-auth-overview.md).

## <a name="collect-all-hma-specific-info-youll-need"></a>HMA'ya özgü gereken tüm bilgileri toplayın

Modern Kimlik Doğrulama'yı kullanmak için önkoşullara uygun olduğunu iki kez kontrol ettikten sonra (yukarıdaki nota bakın), ileriki adımlarda HMA'yı yapılandırmak için ihtiyacınız olacak bilgileri tutmak üzere bir dosya oluşturmanız gerekir.[](hybrid-modern-auth-overview.md) Bu makalede kullanılan örnekler:

- **SIP/SMTP etki alanı**

  - Örn. contoso.com (diğerleriyle federasyon Office 365)

- **Kiracı Kimliği**

  - Kiracınızı temsil eden GUID Office 365 (kullanıcı oturum açma contoso.onmicrosoft.com.

- **SFB 2015 CU5 Web Hizmeti URL'leri**

Dağıtılan tüm SfB 2015 havuzları için iç ve dış web hizmeti URL'leri gerekir. Bunları almak için, Yönetim Kabuğu'Skype Kurumsal çalıştırın:

```powershell
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- Örn. İç: https://lyncwebint01.contoso.com

- Örn. Dış: https://lyncwebext01.contoso.com

Standard Sürümü sunucusu kullanıyorsanız iç URL boş olacaktır. Bu durumda, iç URL için havuz fqdn'sini kullanın.

## <a name="turn-on-modern-authentication-for-exo"></a>EXO için Modern Kimlik Doğrulama'ı açma

Buradaki yönergeleri izleyin: [Exchange Online: Kiracınızı modern kimlik doğrulama için etkinleştirme.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)

## <a name="turn-on-modern-authentication-for-sfbo"></a>SFBO için Modern Kimlik Doğrulama'yu açma

Buradaki yönergeleri izleyin: [Skype Kurumsal Online: Modern kimlik doğrulama için kiracınızı etkinleştirin](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).

## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>Şirket içi kimlik doğrulaması için Exchange Modern Kimlik Doğrulama'ya

Buradaki yönergeleri izleyin: [Şirket içinde Exchange Server Karma Modern Kimlik Doğrulama'nın kullanımı için yapılandırma](configure-exchange-server-for-hybrid-modern-authentication.md).

## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>Şirket içi kimlik doğrulaması için Skype Kurumsal Modern Kimlik Doğrulamayı açma

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-active-directory"></a>Şirket içi web hizmeti URL'lerini POSTA'ya SPN olarak Azure Active Directory

Şimdi, SFBO'da Hizmet Sorumluları olarak URL'leri (daha önce toplanan) eklemek için komutları çalıştırmalısınız.

> [!NOTE]
> Hizmet sorumlusu adları (SPN) web hizmetlerini tanımlayabilir ve yetkili bir kullanıcı adına hareket etmek için bunları bir güvenlik sorumlusuyla (hesap adı veya grup gibi) ilişkilendirme. Sunucuya kimlik doğrulayıcılar SPN'lerde yer alan bilgileri kullanır.

1. İlk olarak, bu yönergeleri Azure Active Directory Azure AD)'[ye bağlanın](/powershell/azure/active-directory/overview).

2. SFB web hizmeti URL'lerinin listesini almak için bu şirket içi komutu çalıştırın.

   AppPrincipalId ile başladığını unutmayın `00000004`. Bu, Skype Kurumsal Online'a karşılıkdır.

   Bu komutun çıktısını (ve daha sonraki karşılaştırmalar için ekran görüntüsünü) not alın. Bu komutun çıktısı SE WS URL'sini içerir, ancak çoğunlukla ile başlayan SPN'lerden oluşur`00000004-0000-0ff1-ce00-000000000000/`.

   ```powershell
   Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
   ```

3. Şirket içi **veya** dış SFB URL'leri eksikse (örneğin, https://lyncwebint01.contoso.com https://lyncwebext01.contoso.com) bu belirli kayıtları bu listeye eklememiz gerekir).

    Aşağıdaki örnek  *URL'leri, Ekle* komutlarında gerçek URL'leri ile değiştir

    ```powershell
    $x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
    $x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
    $x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
    Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
    ```

4. **Get-MsolServicePrincipal** komutunu yeniden 2. adımda çalıştırarak ve çıktıya bakarak yeni kayıtlarınızı eklenmiştir. Önceki listeyi veya ekran görüntüsünü yeni SPN'ler listesiyle karşılaştırın. Kayıtlarınız için yeni listenin ekran görüntüsü de ekleyebilirsiniz. Başarılı olursanız, listede iki yeni URL'ye sahip olursanız. Örneğimize göre, SPN'ler listesi artık belirli URL'leri ve .https://lyncwebint01.contoso.com https://lyncwebext01.contoso.com/

### <a name="create-the-evosts-auth-server-object"></a>EvoSTS Auth Server Nesnesi Oluşturma

Dış Yönetim Kabuğu'Skype Kurumsal aşağıdaki komutu çalıştırın.

```powershell
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```

### <a name="enable-hybrid-modern-authentication"></a>Karma Modern Kimlik Doğrulamayı Etkinleştirme

Bu, ASLıNDA MA'ya dönüşen adımdır. Önceki adımların hepsi, istemci kimlik doğrulaması akışı değişmeden 44 saat çalıştırabilirsiniz. Kimlik doğrulama akışını değiştirmeye hazırsanız, Yönetim Kabuğu'na bu Skype Kurumsal çalıştırın.

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```

## <a name="verify"></a>Doğrula

HMA'yı etkinleştiren bir istemcinin bir sonraki oturum açması yeni kimlik doğrulama akışını kullanır. Yalnızca HMA'yı açmanın hiçbir istemci için yeniden kimlik doğrulaması tetiklenene olmadığını unutmayın. İstemciler, sahip olduğu kimlik doğrulama belirteçlerinin yaşam süresine ve/veya sertifikalarına göre yeniden yazar.

Etkinleştirdikten sonra HMA'nın çalıştığını test etmek için, test SFB Windows istemcisinde oturumları kesin ve 'Kimlik bilgilerimi sil'e tıklamayı seçin. Yeniden oturum açma. İstemci artık Modern Kimlik Doğrulaması akışını kullansın. Oturum açma isteminde, istemci sunucuyla  bağlantı Office 365 oturum açmadan hemen önce görülen 'İş veya okul' hesabı istenir.

Ayrıca, 'OAuth Authority' için İstemciler Skype Kurumsal'ı da denetlemelisiniz. Bunu istemci bilgisayarınızda yapmak için, Bildirim tepsisinde Sağ Ok simgesine sağ Skype Kurumsal CTRL Windows basılı tutun. Görüntülenen **menüde Yapılandırma** Bilgileri'ne tıklayın. Masaüstünde Skype Kurumsal 'Yapılandırma Bilgileri' penceresinde, şunları bakın:

:::image type="content" alt-text="Modern Kimlik Doğrulaması kullanan bir Skype Kurumsal İstemcisi'nin Yapılandırma bilgileri' içinde bir Lync ve EWS OAUTH Authority URL'si gösterirhttps://login.windows.net/common/oauth2/authorize." source="../media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png":::

Ayrıca, Outlook istemcisinin simgesine sağ tıklarken (Windows Bildirimleri tepsisinde) CTRL tuşunu basılı tutarak da 'Bağlantı Durumu' öğesini tıklatabilirsiniz. İstemcinin SMTP adresini, OAuth'ta kullanılan taşıyıcı belirtecinin temsil ettiği '\*Taşıyıcı' türünde bir AuthN türüne göre bakın.

## <a name="related-articles"></a>İlgili makaleler

[Modern Kimlik Doğrulamaya genel bakış bağlantısına geri dönebilirsiniz](hybrid-modern-auth-overview.md).

Modern Kimlik Doğrulama'nın istemcilerinizi nasıl kullanabileceğini Skype Kurumsal gerekiyor? Burada bazı adımlar var: Karma modern kimlik doğrulamaya genel bakış ve bunu şirket içi şirket içi posta ve sunucularla [Skype Kurumsal için Exchange önkoşullar](./hybrid-modern-auth-overview.md).
