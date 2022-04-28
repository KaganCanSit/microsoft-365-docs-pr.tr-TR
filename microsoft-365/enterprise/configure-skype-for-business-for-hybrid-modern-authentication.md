---
title: Şirket içi Skype Kurumsal Karma Modern Kimlik Doğrulaması kullanacak şekilde yapılandırma
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Daha güvenli kullanıcı kimlik doğrulaması ve yetkilendirmesi sunarak şirket içi Skype Kurumsal Karma Modern Kimlik Doğrulaması (HMA) kullanacak şekilde yapılandırmayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7f5e48905416f84ed1a4c48f7e6f1a4b6477f73e
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093492"
---
# <a name="how-to-configure-skype-for-business-on-premises-to-use-hybrid-modern-authentication"></a>Şirket içi Skype Kurumsal Karma Modern Kimlik Doğrulaması kullanacak şekilde yapılandırma

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Daha güvenli kullanıcı kimlik doğrulaması ve yetkilendirmesi sunan bir kimlik yönetimi yöntemi olan Modern Kimlik Doğrulaması, şirket içi Skype Kurumsal sunucu ve şirket içi Exchange sunucu ile karmalar Skype Kurumsal bölünmüş etki alanı için kullanılabilir.

> [!IMPORTANT]
> Modern Kimlik Doğrulaması (MA) hakkında daha fazla bilgi edinmek ve bunu neden şirketinizde veya kuruluşunuzda kullanmayı tercih edebileceğinizi öğrenmek ister misiniz? Genel bakış için [bu belgeyi](hybrid-modern-auth-overview.md) denetleyin. MA ile hangi Skype Kurumsal topolojilerinin desteklendiğini bilmeniz gerekiyorsa, burada belgelenmiştir!

**Başlamadan önce** şu terimleri kullanıyorum:

- Modern Kimlik Doğrulaması (MA)

- Karma Modern Kimlik Doğrulaması (HMA)

- şirket içi (EXCH) Exchange

- Exchange Online (EXO)

- şirket içi (SFB) Skype Kurumsal

- Skype Kurumsal Online (SFBO)

Ayrıca, bu makaledeki bir grafik gri veya soluk bir nesneye sahipse, gri olarak gösterilen öğenin MA'ya özgü yapılandırmaya dahil **olmadığı** anlamına gelir.

## <a name="read-the-summary"></a>Özeti okuyun

Bu özet, işlemi yürütme sırasında kaybolabilecek adımlara böler ve işlemin neresinde olduğunuzu izlemek için genel bir denetim listesi için iyidir.

1. İlk olarak, tüm önkoşulları karşıladığınızdan emin olun.

1. Hem Skype Kurumsal hem de Exchange için birçok **önkoşul** yaygın olduğundan, [giriş öncesi denetim listenize yönelik genel bakış makalesine bakın](hybrid-modern-auth-overview.md). Bu makaledeki adımlardan herhangi birine başlamadan  *önce*  bunu yapın.

1. Bir dosyada veya OneNote ihtiyacınız olacak HMA'ya özgü bilgileri toplayın.

1. EXO için Modern Kimlik Doğrulaması'nı açın (henüz açık değilse).

1. SFBO için Modern Kimlik Doğrulaması'nı aç (henüz açık değilse).

1. Şirket içi Exchange için Karma Modern Kimlik Doğrulaması'nı AÇIN.

1. Şirket içi Skype Kurumsal için Karma Modern Kimlik Doğrulaması'nı AÇIN.

Bu adımlar SFB, SFBO, EXCH ve EXO için MA'yı açar. Yani, SFB ve SFBO'nun HMA yapılandırmasına katılabilen tüm ürünler (EXCH/EXO bağımlılıkları dahil). Başka bir deyişle, kullanıcılarınız Karma'nın herhangi bir bölümünde (EXO + SFBO, EXO + SFB, EXCH + SFBO veya EXCH + SFB) posta kutuları oluşturulduysa, tamamlanmış ürününüz şu şekilde görünür:

![İş için Karma 6 Skype HMA topolojisi, olası dört konumda da MA'ya sahiptir.](../media/ab89cdf2-160b-49ac-9b71-0160800acfc8.png)

Gördüğünüz gibi MA'yi açmak için dört farklı yer var! En iyi kullanıcı deneyimi için bu konumların dördünde de MA'yı açmanızı öneririz. Tüm bu konumlarda MA'yı açamıyorsanız, yalnızca ortamınız için gerekli olan konumlarda MA'yı açmak için adımları ayarlayın.

Desteklenen topolojiler [için MA ile Skype Kurumsal için Desteklenebilirlik konusuna](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported) bakın.

> [!IMPORTANT]
> Başlamadan önce tüm önkoşulları karşıladığınızdan bir kez daha kontrol edin. Bu bilgileri [Karma modern kimlik doğrulamasına genel bakış ve önkoşullar](hybrid-modern-auth-overview.md) bölümünde bulabilirsiniz.

## <a name="collect-all-hma-specific-info-youll-need"></a>İhtiyacınız olan tüm HMA'ya özgü bilgileri toplayın

Modern Kimlik Doğrulaması'nı kullanmak için [önkoşulları](hybrid-modern-auth-overview.md) karşılayıp karşılamadığını bir kez daha denetledikten sonra (yukarıdaki nota bakın), sonraki adımlarda HMA'yi yapılandırmak için ihtiyacınız olacak bilgileri tutmak için bir dosya oluşturmanız gerekir. Bu makalede kullanılan örnekler:

- **SIP/SMTP etki alanı**

  - Örn. contoso.com (Office 365 ile birleştirilir)

- **Kiracı Kimliği**

  - Office 365 kiracınızı temsil eden GUID (contoso.onmicrosoft.com oturum açma sırasında).

- **SFB 2015 CU5 Web Hizmeti URL'leri**

Dağıtılan tüm SfB 2015 havuzları için iç ve dış web hizmeti URL'lerine ihtiyacınız olacaktır. Bunları edinmek için Skype Kurumsal Yönetim Kabuğu'ndan aşağıdakileri çalıştırın:

```powershell
Get-CsService -WebServer | Select-Object PoolFqdn, InternalFqdn, ExternalFqdn | FL
```

- Örn. Iç: https://lyncwebint01.contoso.com

- Örn. Dış: https://lyncwebext01.contoso.com

Standard Sürümü sunucusu kullanıyorsanız iç URL boş olur. Bu durumda, iç URL için havuz fqdn'sini kullanın.

## <a name="turn-on-modern-authentication-for-exo"></a>EXO için Modern Kimlik Doğrulaması'nı açma

Buradaki yönergeleri izleyin: [Exchange Online: Kiracınızı modern kimlik doğrulaması için etkinleştirme.](https://social.technet.microsoft.com/wiki/contents/articles/32711.exchange-online-how-to-enable-your-tenant-for-modern-authentication.aspx)

## <a name="turn-on-modern-authentication-for-sfbo"></a>SFBO için Modern Kimlik Doğrulaması'nı açma

Buradaki yönergeleri izleyin: [çevrimiçi Skype Kurumsal: Kiracınızı modern kimlik doğrulaması için etkinleştirme](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).

## <a name="turn-on-hybrid-modern-authentication-for-exchange-on-premises"></a>Şirket içi Exchange için Karma Modern Kimlik Doğrulaması'nı açma

Buradaki yönergeleri izleyin: [Şirket içi Exchange Server Karma Modern Kimlik Doğrulaması kullanacak şekilde yapılandırma](configure-exchange-server-for-hybrid-modern-authentication.md).

## <a name="turn-on-hybrid-modern-authentication-for-skype-for-business-on-premises"></a>Şirket içi Skype Kurumsal için Karma Modern Kimlik Doğrulaması'nı açma

### <a name="add-on-premises-web-service-urls-as-spns-in-azure-active-directory"></a>Azure Active Directory'da SPN olarak şirket içi web hizmeti URL'leri ekleme

Şimdi URL'leri (daha önce toplanan) SFBO'da Hizmet Sorumluları olarak eklemek için komutları çalıştırmanız gerekir.

> [!NOTE]
> Hizmet sorumlusu adları (SPN) web hizmetlerini tanımlar ve hizmetin yetkili bir kullanıcı adına hareket edebilmesi için bunları bir güvenlik sorumlusuyla (hesap adı veya grup gibi) ilişkilendirir. Bir sunucuda kimlik doğrulaması yapılan istemciler, SPN'lerde bulunan bilgileri kullanır.

1. İlk olarak[, bu yönergelerle](/powershell/azure/active-directory/overview) Azure Active Directory 'a (Azure AD) bağlanın.

2. SFB web hizmeti URL'lerinin listesini almak için bu komutu şirket içinde çalıştırın.

   AppPrincipalId değerinin ile `00000004`başladığını unutmayın. Bu, Skype Kurumsal Online'a karşılık gelir.

   Bir SE ve WS URL'sini içerecek ancak çoğunlukla ile `00000004-0000-0ff1-ce00-000000000000/`başlayan SPN'lerden oluşan bu komutun çıkışını (ve daha sonra karşılaştırma için ekran görüntüsünü) not alın.

   ```powershell
   Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 | Select -ExpandProperty ServicePrincipalNames
   ```

3. Şirket içinden gelen iç **veya** dış SFB URL'leri eksikse (örneğin, https://lyncwebint01.contoso.com https://lyncwebext01.contoso.com) bu belirli kayıtları bu listeye eklememiz gerekir).

    Aşağıdaki  *örnek URL'leri* Ekle komutlarındaki gerçek URL'lerinizle değiştirmeyi unutmayın!

    ```powershell
    $x= Get-MsolServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000
    $x.ServicePrincipalnames.Add("https://lyncwebint01.contoso.com/")
    $x.ServicePrincipalnames.Add("https://lyncwebext01.contoso.com/")
    Set-MSOLServicePrincipal -AppPrincipalId 00000004-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
    ```

4. 2. adımdaki **Get-MsolServicePrincipal** komutunu yeniden çalıştırıp çıkışa bakarak yeni kayıtlarınızın eklendiğini doğrulayın. Önceki listeyi veya ekran görüntüsünü yeni SPN listesiyle karşılaştırın. Ayrıca, kayıtlarınızın yeni listesinin ekran görüntüsünü de görüntüleyebilirsiniz. Başarılıysanız, listede iki yeni URL görürsünüz. Örneğimize göre, SPN'lerin listesi artık belirli URL'leri https://lyncwebint01.contoso.com ve https://lyncwebext01.contoso.com/içerecektir.

### <a name="create-the-evosts-auth-server-object"></a>EvoSTS Kimlik Doğrulama Sunucusu Nesnesi Oluşturma

Skype Kurumsal Yönetim Kabuğu'nda aşağıdaki komutu çalıştırın.

```powershell
New-CsOAuthServer -Identity evoSTS -MetadataURL https://login.windows.net/common/FederationMetadata/2007-06/FederationMetadata.xml -AcceptSecurityIdentifierInformation $true -Type AzureAD
```

### <a name="enable-hybrid-modern-authentication"></a>Karma Modern Kimlik Doğrulamasını Etkinleştirme

Bu aslında MA'yi açan adımdır. Önceki adımların tümü, istemci kimlik doğrulama akışını değiştirmeden önceden çalıştırılabilir. Kimlik doğrulama akışını değiştirmeye hazır olduğunuzda, Skype Kurumsal Yönetim Kabuğu'nda bu komutu çalıştırın.

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity evoSTS
```

## <a name="verify"></a>Doğrulamak

HMA'yı etkinleştirdiğinizde, istemcinin bir sonraki oturum açma bilgileri yeni kimlik doğrulama akışını kullanır. HMA'nın yalnızca etkinleştirilmesi herhangi bir istemci için yeniden kimlik doğrulaması tetiklemez. İstemciler, sahip oldukları kimlik doğrulama belirteçlerinin ve/veya sertifikaların kullanım ömrüne göre yeniden kimlik doğrulamasından geçer.

Etkinleştirdikten sonra HMA'nın çalıştığını test etmek için test SFB Windows istemcisini kapatın ve 'kimlik bilgilerimi sil'e tıkladığınızdan emin olun. Yeniden oturum açın. İstemci artık Modern Kimlik Doğrulama akışını kullanmalıdır ve oturum açma bilgileriniz artık istemci sunucuyla iletişim kurar ve oturum açmadan hemen önce görülen bir **Office 365** 'İş veya okul' hesabı istemi içerir.

'OAuth Yetkilisi' için Skype Kurumsal İstemcileri için 'Yapılandırma Bilgileri'ni de denetlemeniz gerekir. Bunu istemci bilgisayarınızda yapmak için, CTRL tuşunu basılı tutarak Windows Bildirim tepsisindeki Skype Kurumsal Simgesine sağ tıklayın. Görüntülenen menüde **Yapılandırma Bilgileri'ne** tıklayın. Masaüstünde görünecek olan 'Skype Kurumsal Yapılandırma Bilgileri' penceresinde aşağıdakileri arayın:

:::image type="content" alt-text="Modern Kimlik Doğrulaması kullanan bir Skype Kurumsal İstemcisinin Yapılandırma bilgileri, lync ve EWS OAUTH Yetkili URL'sini https://login.windows.net/common/oauth2/authorizegösterir." source="../media/4e54edf5-c8f8-4e7f-b032-5d413b0232de.png":::

Ayrıca, Outlook istemcisinin simgesine (Windows Bildirimler tepsisinde de) sağ tıklayıp 'Bağlantı Durumu'na tıkladığınızda da CTRL tuşunu basılı tutmalısınız. İstemcinin SMTP adresini OAuth'da kullanılan taşıyıcı belirtecini temsil eden 'Taşıyıcı\*' AuthN türünde arayın.

## <a name="related-articles"></a>İlgili makaleler

[Modern Kimlik Doğrulamasına genel bakış bağlantısı](hybrid-modern-auth-overview.md).

Skype Kurumsal istemcileriniz için Modern Kimlik Doğrulaması'nın nasıl kullanılacağını bilmeniz gerekiyor mu? Burada adımlar var: [Karma modern kimlik doğrulamasına genel bakış ve bunu şirket içi Skype Kurumsal ve Exchange sunucularla kullanmak için önkoşullar](./hybrid-modern-auth-overview.md).
