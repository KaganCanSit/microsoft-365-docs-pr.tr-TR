---
title: Karma Modern Kimlik Exchange Server kullanmak üzere şirket içinde nasıl yapılandırılan?
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Şirket içinde karma bir Exchange Server, size daha güvenli kullanıcı kimlik doğrulaması ve yetkilendirme sunan Karma Modern Kimlik Doğrulama'yı (HMA) kullanmak üzere yapılandırmayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: d0889008595717308695c1ad9c5d2a9f1766d1ea
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021770"
---
# <a name="how-to-configure-exchange-server-on-premises-to-use-hybrid-modern-authentication"></a>Karma Modern Kimlik Exchange Server kullanmak üzere şirket içinde nasıl yapılandırılan?

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Karma Modern Kimlik Doğrulama (HMA), daha güvenli kullanıcı kimlik doğrulaması ve yetkilendirme sunan ve Exchange sunucusu şirket içi karma dağıtımlarda kullanılabilen bir kimlik yönetimi yöntemidir.

## <a name="definitions"></a>Tanımlar

Başlamadan önce bazı tanımlara aşina olmak gerekir:

- Karma Modern Kimlik Doğrulama \> HMA

- Exchange şirket içi \> EXCH

- \> Exchange Online EXO

Ayrıca, bu makaledeki grafikte 'gri gri' veya 'soluk' olan bir nesne varsa, gri olarak gösterilen öğe *HMA'ya* özgü yapılandırmaya dahil değildir.

## <a name="enabling-hybrid-modern-authentication"></a>Karma Modern Kimlik Doğrulama'nın etkinleştirilmesi

HMA'yı açma, şu anlama gelir:

1. Başlamadan önce ön hazırlıkları karşılarken emin olmak.

1. Hem şirket **içinde** hem de Skype Kurumsal Exchange birçok önkoşul yaygın olduğu için, Karma Modern Kimlik Doğrulamasına genel bakış ve bunu şirket içi posta ve Skype Kurumsal sunucularla kullanmanın [önkoşulları Exchange vardır](hybrid-modern-auth-overview.md). Bu makaledeki adımlardan herhangi birini başlamadan önce bunu uygulayın.
Eklenecek bağlantılı posta kutularıyla ilgili gereksinimler.

1. Azure AD'de Hizmet Asıl Adları **(SPN)** olarak şirket içi web hizmeti URL'leri ekleme. EXCH'nin birden çok kiracıyla karma olarak olması **durumunda, bu** şirket içi web hizmeti URL'leri EXCH ile karma olarak bulunan tüm kiracıların Azure AD'sinde SPN'ler olarak ek gerekir.

1. HMA için tüm Sanal Dizinlerin etkinleştirildiğinden emin olun

1. EvoSTS Auth Server nesnesini denetleme

1. EXCH'de HMA'yı etkinleştirme.

> [!NOTE]
> Office sürümünüz MA'ya destek oluyor mu? Office [2013 ve Office 2016](modern-auth-for-office-2013-and-2016.md) istemci uygulamaları için bkz. Modern kimlik doğrulama nasıl çalışır?

## <a name="make-sure-you-meet-all-the-prerequisites"></a>Tüm önkoşullara uygun olduğundan emin olun

Birçok önkoşul hem kimlik Skype Kurumsal hem de Exchange yaygın olduğu için, Karma Modern Kimlik Doğrulamaya genel bakış ve bunu şirket içi posta ve Skype Kurumsal sunucularla kullanmak için [önkoşulları Exchange gözden geçirebilirsiniz](hybrid-modern-auth-overview.md). Bu  *makaledeki*  adımlardan herhangi birini başlamadan önce bunu uygulayın.

> [!NOTE]
> Outlook Web App denetim Exchange denetim masası karma Modern Kimlik Doğrulama ile çalışmaz.

## <a name="add-on-premises-web-service-urls-as-spns-in-azure-ad"></a>Şirket içi web hizmeti URL'lerini Azure AD'de SPN'ler olarak ekleme

Şirket içi web hizmeti URL'lerinizi Azure AD SPN'leri olarak ataan komutları çalıştırın. SPN'ler, istemci makineleri ve cihazlar tarafından kimlik doğrulama ve yetkilendirme sırasında kullanılır. Şirket içinden Dış Ad'ye (Azure AD) bağlanmak için Azure Active Directory tüm URL'lerin Azure AD'de kaydedilmiş olması gerekir (bu hem iç hem de dış ad alanlarını içerir).

İlk olarak, bu belgeye eklemeniz gereken tüm URL'leri AAD. Şu komutları şirket içinde çalıştırın:

```powershell
Get-MapiVirtualDirectory | FL server,*url*
Get-WebServicesVirtualDirectory | FL server,*url*
Get-ClientAccessServer | fl Name, AutodiscoverServiceInternalUri
Get-OABVirtualDirectory | FL server,*url*
Get-AutodiscoverVirtualDirectory | FL server,*url*
Get-OutlookAnywhere | FL server,*hostname*
```

BAĞLANTı kurabilirsiniz ve bu istemcilerin URL'ler listesinde HTTPS hizmet sorumlusu adları AAD. EXCH'nin birden çok kiracıyla karma olması **durumunda, bu** HTTPS SPN'leri EXCH ile karma AAD kiracıların genel alanlarına eklenmiştir.

1. İlk olarak, bu yönergeleri AAD [Bilgisayarınıza bağlanin](connect-to-microsoft-365-powershell.md).

    > [!NOTE]
    > Aşağıdaki komutu kullanmak _Bağlan bu sayfadan Bağlan-MsolService_ seçeneğini kullansanız gerekir.

2. İlişkili Exchange URL'leriniz için aşağıdaki komutu yazın:

   ```powershell
   Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 | select -ExpandProperty ServicePrincipalNames
   ```

   Bir ve URL içermesi gereken, ancak çoğunlukla ile başlayan SPN'lerden oluşan bu komutun çıktısını (ve daha sonraki karşılaştırmalar için ekran görüntüsünü) `https://*autodiscover.yourdomain.com*` `https://*mail.yourdomain.com*` not alın `00000002-0000-0ff1-ce00-000000000000/`. Şirket içi `https://` URL'niz eksikse, bu belirli kayıtların bu listeye eklenmiş olması gerekir.

3. İç ve dış MAPI/HTTP, EWS, ActiveSync, OAB ve Otomatik Bulma kayıtlarınızı bu listede görmüyorsanız, aşağıdaki komutu (örnek URL'ler ve ) kullanarak bunları eklemeniz gerekir (`mail.corp.contoso.com``owa.contoso.com`örnek URL'ler ve , ancak örnek URL'leri kendi URL'lerinizi ile **değiştirirsiniz**):

   ```powershell
   $x= Get-MsolServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000
   $x.ServicePrincipalnames.Add("https://mail.corp.contoso.com/")
   $x.ServicePrincipalnames.Add("https://owa.contoso.com/")
   Set-MSOLServicePrincipal -AppPrincipalId 00000002-0000-0ff1-ce00-000000000000 -ServicePrincipalNames $x.ServicePrincipalNames
   ```

4. 2. adımda yer alan komutu çalıştırarak `Get-MsolServicePrincipal` ve çıktıya bakarak yeni kayıtlarınızı eklenmi olduğunu doğrulayın. Önceki listeyi / ekran görüntüsünü yeni SPN'ler listesiyle karşılaştırın. Kayıtlarınız için yeni listenin ekran görüntüsünü de seçebilirsiniz. Başarılı olursanız, listede iki yeni URL'ye bakabilirsiniz. Örneğimize göre, SPN'ler listesi artık belirli URL'leri ve .`https://mail.corp.contoso.com` `https://owa.contoso.com`

## <a name="verify-virtual-directories-are-properly-configured"></a>Sanal Dizinlerin Düzgün Yapılandırıldığından emin olun

Şimdi, OAuth'Exchange aşağıdaki komutları çalıştırarak kullanabileceği tüm Sanal Dizinler Outlook'de düzgün etkinleştirildiğinden emin olun:

```powershell
Get-MapiVirtualDirectory | FL server,*url*,*auth*
Get-WebServicesVirtualDirectory | FL server,*url*,*oauth*
Get-OABVirtualDirectory | FL server,*url*,*oauth*
Get-AutoDiscoverVirtualDirectory | FL server,*oauth*
```

Çıktıyı kontrol edin ve bu VDir'lerin her biri üzerinde **OAuth'ın** etkinleştirildiğinden emin olun; böyle bir görünümde olur (ve bakma gereken önemli nokta 'OAuth'tur):

```powershell
Get-MapiVirtualDirectory | fl server,*url*,*auth*

Server                        : EX1
InternalUrl                   : https://mail.contoso.com/mapi
ExternalUrl                   : https://mail.contoso.com/mapi
IISAuthenticationMethods      : {Ntlm, OAuth, Negotiate}
InternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
ExternalAuthenticationMethods : {Ntlm, OAuth, Negotiate}
```

OAuth hiçbir sunucuda ve dört sanal dizinde yoksa, devam etmeden önce ilgili komutları kullanarak bunu eklemeniz gerekir ([Set-MapiVirtualDirectory](/powershell/module/exchange/set-mapivirtualdirectory), [Set-WebServicesVirtualDirectory](/powershell/module/exchange/set-webservicesvirtualdirectory), [Set-OABVirtualDirectory](/powershell/module/exchange/set-oabvirtualdirectory) ve [Set-AutodiscoverVirtualDirectory](/powershell/module/exchange/set-autodiscovervirtualdirectory)).

## <a name="confirm-the-evosts-auth-server-object-is-present"></a>EvoSTS Auth Server Nesnesi'nin Var Olduğunu Onaylama

Bu son komut için Exchange Yönetim Kabuğu'na dönme. Artık şirket içinizin evoSTS kimlik doğrulama sağlayıcısı için bir girdisi olduğunu doğruabilirsiniz:

```powershell
Get-AuthServer | where {$_.Name -like "EvoSts*"} | ft name,enabled
```

Çıkışta, Name EvoSts'nin GUID'si olan bir AuthServer ve 'Enabled' durumu da True olmalıdır. Bunu görmüyorsanız, Karma Yapılandırma Sihirbazı'nın en son sürümünü indirmeli ve çalıştırabilirsiniz.

> [!NOTE]
> EXCH'nin birden çok kiracıyla karma olması **durumunda,**`EvoSts - {GUID}` çıkışta EXCH ile karma olarak her kiracı için bir Kimlik Doğrulama Sunucusu ve bu AuthServer nesnelerinin tümsinde Etkin durumu True olmalıdır.

> [!IMPORTANT]
> Ortamınız içinde Exchange 2010 çalıştırıyorsanız, EvoSTS kimlik doğrulama sağlayıcısı oluşturulmaz.

## <a name="enable-hma"></a>HMA'yı etkinleştirme

Şirket içi Yönetim Kabuğu Exchange ta aşağıdaki komutu çalıştırın; bunun yerine, \<GUID\> ortamınız içinde komut satırıyla dizeyi kullanın:

```powershell
Set-AuthServer -Identity "EvoSTS - <GUID>" -IsDefaultAuthorizationEndpoint $true
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```

> [!NOTE]
> Karma Yapılandırma Sihirbazı'nın eski sürümlerinde EvoSts AuthServer, GUID ekli olmadan yalnızca EvoSTS olarak adlandırılmıştır. Herhangi bir eyleme gerek yoktur; komutun GUID kısmını kaldırarak yukarıdaki komut satırı üzerinde bunu yansıtacak şekilde değiştirmeniz gerekir:
>
> ```powershell
> Set-AuthServer -Identity EvoSTS -IsDefaultAuthorizationEndpoint $true
> ```

EXCH sürümü Exchange 2016 (CU18 veya sonrası) veya Exchange 2019 (CU7 veya sonrası) ise ve karma Eylül 2020'den sonra HCW ile yapılandırılmışsa, şirket içi Exchange Yönetim Kabuğu'nda aşağıdaki komutu çalıştırın:

```powershell
Set-AuthServer -Identity "EvoSTS - {GUID}" -DomainName "Tenant Domain" -IsDefaultAuthorizationEndpoint $true
Set-OrganizationConfig -OAuth2ClientProfileEnabled $true
```

> [!NOTE]
> EXCH'nin karma olarak birden çok kiracılı olduğu **durumda,** EXCH'de her kiracıya karşılık gelen etki alanlarıyla birlikte birden çok AuthServer nesnesi vardır.  Bu AuthServer nesnelerinden herhangi biri için **IsDefaultAuthorizationEndpoint** bayrağı true olarak ayar olmalıdır ( **IsDefaultAuthorizationEndpoint** cmdlet kullanılarak). Bu bayrak tüm Authserver nesneleri için true olarak ayarlanamaz ve bu AuthServer nesnelerinden birinin **IsDefaultAuthorizationEndpoint** bayrağı true olarak ayarlanmış olsa bile HMA etkinleştirilebilir.
> 
> **DomainName parametresinde**, çoğunlukla formda olan kiracı etki alanı değerini kullanın`contoso.onmicrosoft.com`.

## <a name="verify"></a>Doğrula

HMA'yı etkinleştiren bir istemcinin bir sonraki oturum açması yeni kimlik doğrulama akışını kullanır. Yalnızca HMA'yı açmanın hiçbir istemci için yeniden kimlik doğrulamasına neden olmadığını ve yeni ayarların Exchange için zaman al olabileceğini unutmayın.

Ayrıca, Outlook istemcisinin simgesine sağ tıklarken (Windows Bildirimleri tepsisinde) CTRL tuşunu basılı tutarak da 'Bağlantı Durumu' öğesini tıklatabilirsiniz. İstemcinin SMTP adresini, **OAuth'da** kullanılan taşıyıcı belirtecinin temsil ettiği Authn `Bearer\*`türüne göre bakın.

> [!NOTE]
> HMA ile kimlik Skype Kurumsal mi gerekiyor? size iki makale gerekir: Biri desteklenen [topolojilerin](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported) listeli olduğu gibi, biri de yapılandırmanın [nasıl yapılacaklarını gösterir](configure-skype-for-business-for-hybrid-modern-authentication.md).

## <a name="using-hybrid-modern-authentication-with-outlook-for-ios-and-android"></a>iOS ve Android için Outlook ile karma Modern Kimlik Doğrulama'ı kullanma

TCP 443 üzerinde Exchange sunucusu kullanan şirket içi müşteriysiniz, aşağıdaki IP aralıklarından ağ trafiğine izin ver:

```console
52.125.128.0/20
52.127.96.0/23
```

Bu IP adresi aralıkları, Adres Defteri IP Adresi ve URL Web hizmetine dahil [Office 365 uç noktalar altında da belge edilir](/microsoft-365/enterprise/additional-office365-ip-addresses-and-urls).

## <a name="related-topics"></a>İlgili konular

[Özel bağlantıdan/ITAR'dan vNext'e Office 365 için Modern Kimlik Doğrulama yapılandırma gereksinimleri](/exchange/troubleshoot/modern-authentication/modern-authentication-configuration)
