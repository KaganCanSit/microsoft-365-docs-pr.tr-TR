---
title: Şirket içi Exchange Server Karma Modern Kimlik Doğrulaması kullanacak şekilde yapılandırma
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/27/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: cef3044d-d4cb-4586-8e82-ee97bd3b14ad
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: Size daha güvenli kullanıcı kimlik doğrulaması ve yetkilendirmesi sunan Karma Modern Kimlik Doğrulaması (HMA) kullanmak için şirket içi Exchange Server yapılandırmayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 2ee190a541fdf3e4e77a251e040f2cb69416088c
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65095762"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>Şirket içi Exchange Server Karma Modern Kimlik Doğrulaması kullanacak şekilde yapılandırma

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Karma Modern Kimlik Doğrulaması (HMA), daha güvenli kullanıcı kimlik doğrulaması ve yetkilendirmesi sunan bir kimlik yönetimi yöntemidir ve Exchange sunucu şirket içi karma dağıtımları için kullanılabilir.

## <a name="definitions"></a>Tanımlar

Başlamadan önce bazı tanımlar hakkında bilgi sahibi olmanız gerekir:

- Karma Modern Kimlik Doğrulaması \> HMA

- Şirket içi \> Exchange DÖVİZ KURLARI

- \> exo Exchange Online

Ayrıca *, bu makaledeki bir grafikte 'gri gösterilmiş' veya 'soluk' bir nesne varsa, gri olarak gösterilen öğenin HMA'ya özgü yapılandırmaya dahil edilmediği anlamına gelir*.

## <a name="enabling-hybrid-modern-authentication"></a>Karma Modern Kimlik Doğrulamasını Etkinleştirme

HMA'nın etkinleştirilmesi şu anlama gelir:

1. Başlamadan önce önkoşullarla karşılaştığından emin olmak.

1. Hem Skype Kurumsal hem de Exchange için birçok **önkoşul** yaygın olduğundan [, Karma Modern Kimlik Doğrulamasına genel bakış ve bunu şirket içi Skype Kurumsal ve Exchange sunucularla kullanmak için önkoşullar](hybrid-modern-auth-overview.md). Bu makaledeki adımlardan herhangi birine başlamadan önce bunu yapın.
Eklenecek bağlantılı posta kutularıyla ilgili gereksinimler.

1. Azure AD'de **Hizmet Asıl Adları (SPN)** olarak şirket içi web hizmeti URL'leri ekleme. EXCH'nin **birden çok kiracıyla** karma olması durumunda, bu şirket içi web hizmeti URL'leri, EXCH ile karma olan tüm kiracıların Azure AD'sine SPN'ler olarak eklenmelidir.

1. HMA için tüm Sanal Dizinlerin etkinleştirildiğinden emin olun

1. EvoSTS Kimlik Doğrulama Sunucusu nesnesi denetleniyor

1. EXCH'te HMA'nın etkinleştirilmesi.

> [!NOTE]
> Office sürümünüz MA'Office destekliyor mu? Bkz[. Office 2013 ve Office 2016 istemci uygulamaları için modern kimlik doğrulaması nasıl çalışır](modern-auth-for-office-2013-and-2016.md)?

## <a name="make-sure-you-meet-all-the-prerequisites"></a>Tüm önkoşulları karşıladığınızdan emin olun

Hem Skype Kurumsal hem de Exchange için birçok önkoşul yaygın olduğundan, [karma modern kimlik doğrulamasına genel bakış ve bunu şirket içi Skype Kurumsal ve Exchange sunucularla kullanmak için önkoşulları](hybrid-modern-auth-overview.md) gözden geçirin. Bu makaledeki adımlardan herhangi birine başlamadan  *önce*  bunu yapın.

> [!NOTE]
> Outlook Web App ve Exchange Denetim Masası karma Modern Kimlik Doğrulaması ile çalışmaz.

## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Azure AD'de SPN olarak şirket içi web hizmeti URL'leri ekleme

Şirket içi web hizmeti URL'lerinizi Azure AD SPN'leri olarak atayan komutları çalıştırın. SPN'ler, kimlik doğrulaması ve yetkilendirme sırasında istemci makineleri ve cihazlar tarafından kullanılır. Şirket içinden Azure Active Directory 'a (Azure AD) bağlanmak için kullanılabilecek tüm URL'lerin Azure AD'ye kaydedilmesi gerekir (bu hem iç hem de dış ad alanlarını içerir).

İlk olarak, AAD eklemeniz gereken tüm URL'leri toplayın. Şirket içinde şu komutları çalıştırın:

```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ClientAccessServer | fl Name, AutodiscoverServiceInternalUri
Get-OABVirtualDirectory | FL server,*url*
Get-AutodiscoverVirtualDirectory | FL server,*url*
Get-OutlookAnywhere | FL server,*hostname*
```

İstemcilerin bağlanabileceği URL'lerin AAD HTTPS hizmet sorumlusu adları olarak listelenmiş olduğundan emin olun. EXCH'nin **birden çok kiracıyla** karma olması durumunda, bu HTTPS SPN'leri EXCH ile karma olarak tüm kiracıların AAD eklenmelidir.

1. İlk olarak[, bu yönergelerle](connect-to-microsoft-365-powershell.md) AAD bağlanın.

    > [!NOTE]
    > Aşağıdaki komutu kullanabilmek için bu sayfadaki _Bağlan-MsolService_ seçeneğini kullanmanız gerekir.

2. Exchange ilgili URL'leriniz için aşağıdaki komutu yazın:

   ```powershell
   Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
   ```

   Ve URL'sini içermesi `https://*autodiscover.yourdomain.com*` `https://*mail.yourdomain.com*` gereken ancak çoğunlukla ile `00000002-0000-0ff1-ce00-000000000000/`başlayan SPN'lerden oluşan bu komutun çıkışını not edin (ve daha sonra karşılaştırma için ekran görüntüsü). Şirket içi ortamınızdan eksik URL'ler varsa `https://` , bu belirli kayıtlar bu listeye eklenmelidir.

3. İç ve dış MAPI/HTTP, EWS, ActiveSync, OAB ve Otomatik Bulma kayıtlarınızı bu listede görmüyorsanız, bunları aşağıdaki komutu kullanarak eklemeniz gerekir (örnek URL'ler ve'dir `mail.corp.contoso.com` `owa.contoso.com`, ancak **örnek URL'leri kendi URL'nizle değiştirirsiniz**):

   ```powershell
   $x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000
   $x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
   $x.ServicePrincipalnames.Add("https://owa.contoso.com/")
   Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
   ```

4. 2. adımdaki komutu yeniden çalıştırıp çıkışa `Get-MsolServicePrincipal` bakarak yeni kayıtlarınızın eklendiğini doğrulayın. Önceki listeyi / ekran görüntüsünü yeni SPN listesiyle karşılaştırın. Ayrıca, kayıtlarınız için yeni listenin ekran görüntüsünü de çekebilirsiniz. Başarılıysanız, listede iki yeni URL görürsünüz. Örneğimize göre, SPN'lerin listesi artık belirli URL'leri `https://mail.corp.contoso.com` ve `https://owa.contoso.com`içerecektir.

## <a name="verify-virtual-directories-are-properly-configured"></a>Sanal Dizinlerin Düzgün Yapılandırıldığını Doğrulama

Şimdi aşağıdaki komutları çalıştırarak Outlook tüm Sanal Dizinlerde Exchange OAuth'un düzgün etkinleştirildiğini doğrulayın:

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth*
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

Bu VDir'lerin her birinde **OAuth'un** etkinleştirildiğinden emin olmak için çıktıyı denetleyin; şuna benzer olacaktır (ve bakılacak önemli şey 'OAuth'):

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*

Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```

Herhangi bir sunucuda ve dört sanal dizinden herhangi birinde OAuth eksikse, devam etmeden önce ilgili komutları kullanarak eklemeniz gerekir ([Set-MapiVirtualDirectory](/powershell/module/exchange/set-mapivirtualdirectory), [Set-WebServicesVirtualDirectory](/powershell/module/exchange/set-webservicesvirtualdirectory), [Set-OABVirtualDirectory](/powershell/module/exchange/set-oabvirtualdirectory) ve [Set-AutodiscoverVirtualDirectory](/powershell/module/exchange/set-autodiscovervirtualdirectory)).

## <a name="confirm-the-evosts-auth-server-object-is-present"></a>EvoSTS Kimlik Doğrulama Sunucusu Nesnesinin Mevcut Olduğunu Onaylayın

Bu son komut için şirket içi Exchange Yönetim Kabuğu'na dönün. Artık şirket içi ortamınızda evoSTS kimlik doğrulama sağlayıcısı için bir giriş olduğunu doğrulayabilirsiniz:

```powershell
Get-AuthServer | where {$_.Name -like "EvoSts*"} | ft name,enabled
```

Çıkışınızın GUID'i olan EvoSts Adında bir AuthServer göstermesi ve 'Etkin' durumunun True olması gerekir. Bunu görmüyorsanız Karma Yapılandırma Sihirbazı'nın en son sürümünü indirip çalıştırmanız gerekir.

> [!NOTE]
> EXCH'nin **birden çok kiracıyla** karma olması durumunda, çıkışınız EXCH ile karma olan her kiracı için Ad'ın `EvoSts - {GUID}` bir AuthServer'ını göstermelidir ve **Bu** AuthServer nesnelerinin tümü için Etkin durumu True olmalıdır.

> [!IMPORTANT]
> Ortamınızda Exchange 2010 çalıştırıyorsanız EvoSTS kimlik doğrulama sağlayıcısı oluşturulmaz.

## <a name="enable-hma"></a>HMA'yı etkinleştirme

Şirket içi Exchange Yönetim Kabuğu'nda aşağıdaki komutu çalıştırın ve komut satırında değerini ortamınızdaki dizeyle değiştirin\<GUID\>:

```powershell
Set-AuthServer -Identity "EvoSTS - <GUID>" -IsDefaultAuthorizationEndpoint $true
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```

> [!NOTE]
> Karma Yapılandırma Sihirbazı'nın eski sürümlerinde EvoSts AuthServer, GUID ekli olmadan evoSTS olarak adlandırıldı. Yapmanız gereken bir eylem yoktur, komutun GUID bölümünü kaldırarak yukarıdaki komut satırını bunu yansıtacak şekilde değiştirmeniz yeterlidir:
>
> ```powershell
> Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true
> ```

EXCH sürümü Exchange 2016 (CU18 veya üzeri) veya Exchange 2019 (CU7 veya üzeri) ise ve karma Eylül 2020'de indirilen HCW ile yapılandırılmışsa, şirket içi Exchange Yönetim Kabuğu'nda aşağıdaki komutu çalıştırın:

```powershell
Set-AuthServer -Identity "EvoSTS - {GUID}" -DomainName "Tenant Domain" -IsDefaultAuthorizationEndpoint $true
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```

> [!NOTE]
> EXCH'nin **birden çok kiracıyla** karma olması durumunda, EXCH'de her kiracıya karşılık gelen etki alanlarıyla birlikte birden çok AuthServer nesnesi vardır.  Bu AuthServer nesnelerinden herhangi biri için **IsDefaultAuthorizationEndpoint** bayrağı true ( **IsDefaultAuthorizationEndpoint** cmdlet'i kullanılarak) olarak ayarlanmalıdır. Bu bayrak tüm Authserver nesneleri için true olarak ayarlanamaz ve bu AuthServer nesnelerinden birinin **IsDefaultAuthorizationEndpoint** bayrağı true olarak ayarlansa bile HMA etkinleştirilir.
> 
> **DomainName** parametresi için genellikle biçimindeki `contoso.onmicrosoft.com`kiracı etki alanı değerini kullanın.

## <a name="verify"></a>Doğrulamak

HMA'yı etkinleştirdiğinizde, istemcinin bir sonraki oturum açma bilgileri yeni kimlik doğrulama akışını kullanır. HMA'yı açmanın herhangi bir istemci için yeniden kimlik doğrulaması tetiklemeyeceğini ve Exchange yeni ayarları almasının biraz zaman alabileceğini unutmayın.

Ayrıca, Outlook istemcisinin simgesine (Windows Bildirimler tepsisinde de) sağ tıklayıp 'Bağlantı Durumu'na tıkladığınızda da CTRL tuşunu basılı tutmalısınız. İstemcinin SMTP adresini, **OAuth'da** kullanılan taşıyıcı belirtecini temsil eden Authn türünde `Bearer\*`arayın.

> [!NOTE]
> HMA ile Skype Kurumsal yapılandırmanız mı gerekiyor? İki makaleniz olması gerekir: [Biri desteklenen topolojileri](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported) listeler, diğeri de [yapılandırmayı nasıl yapacağınızı](configure-skype-for-business-for-hybrid-modern-authentication.md) gösterir.

## <a name="using-hybrid-modern-authentication-with-outlook-for-ios-and-android"></a>iOS ve Android için Outlook ile karma Modern Kimlik Doğrulaması kullanma

TCP 443'te Exchange sunucusu kullanan bir şirket içi müşteriyseniz, aşağıdaki IP aralıklarından gelen ağ trafiğine izin verin:

```console
52.125.128.0/20
52.127.96.0/23
```

Bu IP adresi aralıkları, [Office 365 IP Adresi ve URL Web hizmetine dahil olmayan ek uç noktalar](/microsoft-365/enterprise/additional-office365-ip-addresses-and-urls) bölümünde de belgelenmiştir.

## <a name="related-topics"></a>İlgili konular

[Office 365 ayrılmış/ITAR'dan vNext'e geçiş için Modern Kimlik Doğrulama yapılandırma gereksinimleri](/exchange/troubleshoot/modern-authentication/modern-authentication-configuration)
