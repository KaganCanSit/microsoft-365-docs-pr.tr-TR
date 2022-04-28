---
title: Şirket içi Skype Kurumsal ve Exchange sunucularıyla kullanım için Karma Modern Kimlik Doğrulamasına genel bakış ve önkoşullar
ms.author: kvice
ms.reviewer: smithre4
author: kelleyvice-msft
manager: scotv
ms.date: 12/03/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
description: Bu makalede Karma Modern Kimlik Doğrulaması ve şirket içi Skype Kurumsal ve Exchange sunucularıyla kullanım önkoşulları hakkında bilgi edineceksiniz.
ms.openlocfilehash: c161f205aba1222f39811155bef5c6be6da613d0
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093404"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>Karma modern kimlik doğrulamasına genel bakış ve şirket içi Skype Kurumsal ve Exchange sunucularla kullanmak için önkoşullar

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

_Modern Kimlik Doğrulaması_ , daha güvenli kullanıcı kimlik doğrulaması ve yetkilendirmesi sunan bir kimlik yönetimi yöntemidir. Şirket içi Skype Kurumsal sunucu ile şirket içi Exchange sunucunun Office 365 karma dağıtımları ve karma Skype Kurumsal bölünmüş etki alanı için kullanılabilir. Bu makale önkoşullar, modern kimlik doğrulamayı ayarlama/devre dışı bırakma ile ilgili belgelere ve ilgili istemcilerden bazılarına (ör. Outlook ve Skype istemcileri) bilgileri.

- [Modern kimlik doğrulaması nedir?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
- [Modern kimlik doğrulaması kullandığımda ne değişir?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
- [Şirket içi ortamınızın modern kimlik doğrulama durumunu denetleme](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
- [Modern kimlik doğrulaması önkoşullarını karşılıyor musunuz?](#do-you-meet-modern-authentication-prerequisites)
- [Başlamadan önce bilmem gereken başka ne var?](hybrid-modern-auth-overview.md#BKMK_Whatelse)

## <a name="what-is-modern-authentication"></a>Modern kimlik doğrulaması nedir?
<a name="BKMK_WhatisModAuth"> </a>

Modern kimlik doğrulaması, bir istemci (örneğin, dizüstü bilgisayarınız veya telefonunuz) ile bir sunucu arasındaki kimlik doğrulama ve yetkilendirme yöntemlerinin yanı sıra zaten aşina olabileceğiniz erişim ilkelerine dayanan bazı güvenlik önlemlerinin birleşimi için kullanılan bir terimdir. İçindekiler:

- **Kimlik doğrulama yöntemleri**: Çok faktörlü kimlik doğrulaması (MFA); akıllı kart kimlik doğrulaması; istemci sertifikası tabanlı kimlik doğrulaması
- **Yetkilendirme yöntemleri**: Microsoft'un Açık Yetkilendirme (OAuth) uygulamasını
- **Koşullu erişim ilkeleri**: Mobil Uygulama Yönetimi (MAM) ve Azure Active Directory (Azure AD) Koşullu Erişim

Modern kimlik doğrulaması ile kullanıcı kimliklerini yönetmek, yöneticilerin kaynakların güvenliğini sağlamak için kullanabileceği birçok farklı araç sağlar ve hem şirket içi (Exchange hem de Skype Kurumsal), karma Exchange ve karma/bölünmüş etki alanı senaryolarına Skype Kurumsal daha güvenli kimlik yönetimi yöntemleri sunar.

Skype Kurumsal Exchange ile yakından çalıştığından, istemci kullanıcıların Skype Kurumsal oturum açma davranışı Exchange modern kimlik doğrulama durumundan etkilenir. Ayrıca, hem Çevrimiçi hem de şirket içinde Skype Kurumsal Skype Kurumsal Skype Kurumsal _bölünmüş etki alanı_ karma mimariniz varsa ve kullanıcılar her iki konumda da barındırılıyorsa geçerlidir.

Office 365 modern kimlik doğrulaması hakkında daha fazla bilgi için bkz. [Office 365 İstemci Uygulaması Desteği - Çok faktörlü kimlik doğrulaması](microsoft-365-client-support-multi-factor-authentication.md).

> [!IMPORTANT]
> Ağustos 2017 itibarıyla, çevrimiçi ve Exchange Skype Kurumsal içeren tüm yeni Office 365 kiracıları varsayılan olarak modern kimlik doğrulamayı etkinleştirecektir. Önceden var olan kiracıların varsayılan MA durumunda bir değişiklik olmaz, ancak tüm yeni kiracılar yukarıda listelenen genişletilmiş kimlik özellikleri kümesini otomatik olarak destekler. MA durumunuzu denetlemek için [Şirket içi ortamınızın modern kimlik doğrulama durumunu denetleme](hybrid-modern-auth-overview.md#BKMK_CheckStatus) bölümüne bakın.

## <a name="what-changes-when-i-use-modern-authentication"></a>Modern kimlik doğrulaması kullandığımda ne değişir?
<a name="BKMK_WhatChanges"> </a>

Şirket içi Skype Kurumsal veya Exchange sunucusuyla modern kimlik doğrulaması kullanırken, şirket içi kullanıcıların *kimliğini* doğrulamaya devam edebilirsiniz, ancak kaynaklara (dosyalar veya e-postalar gibi) *erişimlerini yetkilendirme* hikayesi değişir. Bu nedenle modern kimlik doğrulaması istemci ve sunucu iletişimi hakkında olsa da MA yapılandırması sırasında atılan adımlar evoSTS'nin (Azure AD tarafından kullanılan bir Güvenlik Belirteci Hizmeti) şirket içi Skype Kurumsal ve Exchange sunucusu için Kimlik Doğrulama Sunucusu olarak ayarlanmasına neden olur.

evoSTS'ye yapılan değişiklik, şirket içi sunucularınızın istemcilerinizi yetkilendirmek için OAuth'dan (belirteç verme) yararlanmasına ve ayrıca şirket içi sunucularınızın bulutta ortak olan güvenlik yöntemlerini (Multi-factor Authentication gibi) kullanmasına olanak tanır. Buna ek olarak, evoSTS kullanıcıların istek kapsamında parolalarını sağlamadan kaynaklara erişim istemesine olanak sağlayan belirteçler verir. Kullanıcılarınızın nerede barındırıldığı (çevrimiçi veya şirket içi) ve gerekli kaynağı hangi konumda barındırdığı fark etmez, modern kimlik doğrulaması yapılandırıldıktan sonra EvoSTS kullanıcıları ve istemcileri yetkilendirmenin çekirdeği haline gelir.

Örneğin, bir Skype Kurumsal istemcisinin kullanıcı adına takvim bilgilerini almak için Exchange sunucusuna erişmesi gerekiyorsa, bunu yapmak için Microsoft Kimlik Doğrulama Kitaplığı'nı (MSAL) kullanır. MSAL, dizininizdeki güvenli kaynakları OAuth güvenlik belirteçlerini kullanarak istemci uygulamaları için kullanılabilir hale getirmek için tasarlanmış bir kod kitaplığıdır. MSAL, bir kullanıcıya kaynağa erişim izni vermek için talepleri doğrulamak ve belirteçleri (parolalar yerine) değiştirmek için OAuth ile birlikte çalışır. Geçmişte, bunun gibi bir işlemdeki yetkili (kullanıcı taleplerini doğrulamayı ve gerekli belirteçleri vermeyi bilen sunucu) şirket içi bir Güvenlik Belirteci Hizmeti, hatta Active Directory Federasyon Hizmetleri (AD FS) olabilir. Ancak modern kimlik doğrulaması, Azure AD kullanarak bu yetkiyi merkezileştirir.

Bu ayrıca, Exchange sunucunuz ve Skype Kurumsal ortamlarınız tamamen şirket içinde olsa da, yetkilendirme sunucusunun çevrimiçi olacağı ve şirket içi ortamınızın Bulutta Office 365 aboneliğinize (ve aboneliğinizin dizini olarak kullandığı Azure AD örneğine) bağlantı oluşturup sürdürebilmesi gerektiği anlamına gelir.

Ne değişmez? İster bölünmüş etki alanı karmasında olun, ister şirket içinde Skype Kurumsal ve Exchange sunucusu kullanıyor olun, tüm kullanıcıların önce *şirket içinde* kimlik doğrulaması yapması gerekir. _Lyncdiscovery_ ve _Autodiscovery_, modern kimlik doğrulamasının karma bir uygulamasında şirket içi sunucunuza işaret eder.

> [!IMPORTANT]
> MA ile desteklenen belirli Skype Kurumsal topolojilerini bilmeniz gerekiyorsa, bunlar [burada belgelenmiştir](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported).

## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>Şirket içi ortamınızın modern kimlik doğrulama durumunu denetleme
<a name="BKMK_CheckStatus"> </a>

Modern kimlik doğrulaması, hizmetler OAuth/S2S uygularken kullanılan yetkilendirme sunucusunu değiştirdiğinden, şirket içi Skype Kurumsal ve Exchange ortamlarınız için modern kimlik doğrulamasının etkinleştirilip etkinleştirilmediğini veya devre dışı bırakılıp bırakılmadiğini bilmeniz gerekir. Aşağıdaki PowerShell komutunu çalıştırarak Exchange sunucularınızdaki durumu de kontrol edebilirsiniz:

```powershell
Get-OrganizationConfig | ft OAuth*
```

_OAuth2ClientProfileEnabled_ özelliğinin değeri **False** ise modern kimlik doğrulaması devre dışı bırakılır.

Get-OrganizationConfig cmdlet'i hakkında daha fazla bilgi için bkz. [Get-OrganizationConfig](/powershell/module/exchange/get-organizationconfig).

Aşağıdaki PowerShell komutunu çalıştırarak Skype Kurumsal sunucularınızı de kontrol edebilirsiniz:

```powershell
Get-CSOAuthConfiguration
```

Komut boş bir _OAuthServers_ özelliği döndürürse veya _ClientADALAuthOverride_ özelliğinin değeri **İzin Verilmezse** modern kimlik doğrulaması devre dışı bırakılır.

Get-CsOAuthConfiguration cmdlet'i hakkında daha fazla bilgi için bkz. [Get-CsOAuthConfiguration](/powershell/module/skype/get-csoauthconfiguration).

## <a name="do-you-meet-modern-authentication-prerequisites"></a>Modern kimlik doğrulaması önkoşullarını karşılıyor musunuz?

Devam etmeden önce bu öğeleri doğrulayın ve listenizden denetleyin:

- **belirli Skype Kurumsal**
  - Skype Kurumsal Sunucu 2015 veya üzeri için tüm sunucuların Mayıs 2017 toplu güncelleştirmesi (CU5) olmalıdır
    - **Özel Durum** - Survivability Branch Appliance (SBA) geçerli sürümde olabilir (Lync 2013 tabanlı)
  - SIP etki alanınız Office 365'de Federasyon etki alanı olarak eklenir
  - Tüm SFB Ön Uçları, Office 365 URL'leri ve [IP adresi aralıklarının](urls-and-ip-address-ranges.md) 'Microsoft 365 Ortak ve Office' bölümünün 56. ve 125. Satırlarında listelenen kimlik doğrulama URL'lerini (TCP 443) ve iyi bilinen sertifika kök CRL'lerini (TCP 80) Office 365 için İnternet'e giden bağlantılara sahip olmalıdır.

- **Karma Office 365 ortamında şirket içi Skype Kurumsal**
  - Skype Kurumsal Sunucu 2019 çalıştıran tüm sunucularla Skype Kurumsal Sunucu 2019 dağıtımı.
  - Skype Kurumsal Sunucu 2015 çalıştıran tüm sunucularla Skype Kurumsal Sunucu 2015 dağıtımı.
  - Aşağıda listelenen en fazla iki farklı sunucu sürümüne sahip bir dağıtım:
    - Skype Kurumsal Sunucu 2015
    - Skype Kurumsal Sunucu 2019
  - Tüm Skype Kurumsal sunucularında en son toplu güncelleştirmelerin yüklü olması gerekir. Kullanılabilir tüm güncelleştirmeleri bulmak ve yönetmek için [güncelleştirmeleri Skype Kurumsal Sunucu](/skypeforbusiness/sfb-server-updates).
  - Karma ortamda Lync Server 2010 veya 2013 yoktur.

>[!NOTE]
>Skype Kurumsal ön uç sunucularınız İnternet erişimi için bir ara sunucu kullanıyorsa, kullanılan ara sunucu IP'si ve Bağlantı noktası numarası her ön uç için web.config dosyasının yapılandırma bölümüne girilmelidir.

- C:\Program Files\Skype Kurumsal Sunucu 2015\Web Components\Web ticket\int\web.config
- C:\Program Files\Skype Kurumsal Sunucu 2015\Web Components\Web ticket\ext\web.config

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="https://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</configuration>
```

> [!IMPORTANT]
> Gerekli URL'lerin en son listeleriyle güncel kalmak için [Office 365 URL'ler ve IP adresi aralıkları](urls-and-ip-address-ranges.md) için RSS akışına abone olun.

- **belirli Exchange Server**
  - Exchange server 2013 CU19 ve üzeri, sunucu 2016 CU8 ve üzeri Exchange ya da 2019 CU1 ve üzeri Exchange Server kullanıyorsunuz.
  - Ortamda Exchange sunucu 2010 yok.
  - SSL Boşaltma yapılandırılmadı. SSL sonlandırma ve yeniden şifreleme desteklenir.
  - Ortamınızın sunucuların İnternet'e bağlanmasına izin vermek için bir proxy sunucu altyapısı kullanması durumunda, tüm Exchange sunucuların [InternetWebProxy](/powershell/module/exchange/set-exchangeserver) özelliğinde tanımlanan proxy sunucusuna sahip olduğundan emin olun.

- **Karma Office 365 ortamında şirket içi Exchange Server**

  - Exchange Server 2013 kullanıyorsanız, en az bir sunucuda Posta Kutusu ve İstemci Erişimi sunucu rolleri yüklü olmalıdır. Posta Kutusu ve İstemci Erişimi rollerini ayrı sunuculara yüklemek mümkün olsa da, daha fazla güvenilirlik ve gelişmiş performans sağlamak için her iki rolü de aynı sunucuya yüklemenizi kesinlikle öneririz.
  - Exchange server 2016 veya sonraki bir sürümünü kullanıyorsanız, en az bir sunucuda Posta Kutusu sunucusu rolü yüklü olmalıdır.
  - Karma ortamda Exchange sunucusu 2007 veya 2010 yoktur.
  - Tüm Exchange sunucularında en son toplu güncelleştirmelerin yüklü olması gerekir. Kullanılabilir tüm güncelleştirmeleri bulmak ve yönetmek için bkz. [Exchange en son Toplu Güncelleştirmelere yükseltme](/exchange/plan-and-deploy/install-cumulative-updates).

- **İstemci ve protokol gereksinimlerini Exchange**

    Modern kimlik doğrulamasının kullanılabilirliği istemci, protokol ve yapılandırma birleşimine göre belirlenir. Modern kimlik doğrulaması istemci, protokol ve/veya yapılandırma tarafından desteklenmiyorsa, istemci eski kimlik doğrulamasını kullanmaya devam eder.
  
    Aşağıdaki istemciler ve protokoller, ortamda modern kimlik doğrulaması etkinleştirildiğinde şirket içi Exchange modern kimlik doğrulamasını destekler:

  |**Istemci**|**Birincil Protokol**|**Notlar**|
  |:-----|:-----|:-----|
  |Outlook 2013 ve üzeri  <br/> |HTTP üzerinden MAPI  <br/> |Bu istemcilerle modern kimlik doğrulaması kullanmak için http üzerinden MAPI Exchange içinde etkinleştirilmelidir (Exchange 2013 Service Pack 1 ve üzeri yeni yüklemeler için etkin veya True); daha fazla bilgi için bkz. [Office 2013 ve Office 2016 istemci uygulamaları için modern kimlik doğrulaması nasıl çalışır](modern-auth-for-office-2013-and-2016.md)?  <br/> gereken en düşük Outlook derlemesini çalıştırdığınızdan emin olun; bkz. [Windows Yükleyicisi (MSI) kullanan Outlook sürümleri için en son güncelleştirmeler](/officeupdates/outlook-updates-msi).  <br/> |
  |Mac için Outlook 2016 ve üzeri  <br/> |Exchange Web Hizmetleri  <br/> |  <br/> |
  |iOS ve Android için Outlook  <br/> | Microsoft eşitleme teknolojisi <br/> |Daha fazla bilgi için bkz. [iOS ve Android için Outlook ile karma Modern Kimlik Doğrulaması kullanma](/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth).  <br/> |
  |Exchange ActiveSync istemcileri (örneğin, iOS11 Posta)  <br/> |Exchange ActiveSync  <br/> |Modern kimlik doğrulamasını destekleyen Exchange ActiveSync istemciler için, temel kimlik doğrulamasından modern kimlik doğrulamasına geçmek için profili yeniden oluşturmanız gerekir.  <br/> |

    Listelenmeyen istemciler ve/veya protokoller (örneğin, POP3), şirket içi Exchange modern kimlik doğrulamasını desteklemez ve ortamda modern kimlik doğrulaması etkinleştirildikten sonra bile eski kimlik doğrulama mekanizmalarını kullanmaya devam eder.

- **Genel önkoşullar**
  - Kaynak ormanı senaryoları, karma modern kimlik doğrulama istekleri sırasında doğru SID aramalarının gerçekleştirildiğinden emin olmak için hesap ormanıyla iki yönlü güven gerektirir. 
  - AD FS kullanıyorsanız federasyon için Windows 2012 R2 AD FS 3.0 ve üstü olmalıdır.
  - Kimlik yapılandırmalarınız Parola karması eşitleme, doğrudan kimlik doğrulaması ve Office 365 tarafından desteklenen şirket içi STS gibi Azure AD Bağlan tarafından desteklenen türlerden herhangi biridir.
  - Azure AD Bağlan kullanıcı çoğaltması ve eşitlemesi için yapılandırılmış ve çalışır.
  - Karmanın, şirket içi ve Office 365 ortamınız arasında Klasik Karma Topoloji modu Exchange kullanılarak yapılandırıldığını doğruladınız. Exchange karma için resmi destek bildirimi, mevcut CU veya geçerli CU - 1'e sahip olmanız gerektiğini söylüyor.
    > [!NOTE]
    > Karma modern kimlik doğrulaması [Karma Aracı](/exchange/hybrid-deployment/hybrid-agent) ile desteklenmez.

  - Hem şirket içi test kullanıcısının hem de Office 365'de bulunan karma test kullanıcısının Skype Kurumsal masaüstü istemcisinde (Skype ile modern kimlik doğrulaması kullanmak istiyorsanız) ve Microsoft Outlook (Exchange ile modern kimlik doğrulaması kullanmak istiyorsanız) oturum açaadığından emin olun.
  - Microsoft Office'daki SignInOptions ayarının en kısıtlayıcı ayarıyla yapılandırılmadığından emin olun. Daha fazla bilgi için bkz[. Office İnternet'e bağlanmasına izin verme](/office365/troubleshoot/access-management/office-feature-disabled).

## <a name="what-else-do-i-need-to-know-before-i-begin"></a>Başlamadan önce bilmem gereken başka ne var?
<a name="BKMK_Whatelse"> </a>

- Şirket içi sunuculara yönelik tüm senaryolar, kimlik doğrulaması ve yetkilendirmeden sorumlu sunucunun Microsoft Bulut'ta (Azure AD'nin 'evoSTS' olarak adlandırılan güvenlik belirteci hizmeti) olması için şirket içi modern kimlik doğrulamasını ayarlamayı (aslında Skype Kurumsal desteklenen topolojilerin listesi vardır) ve şirket içi yüklemeniz tarafından kullanılan URL'ler veya ad alanları hakkında Azure AD'yi güncelleştirmeyi içerir Skype Kurumsal veya Exchange. Bu nedenle, şirket içi sunucular bir Microsoft Bulut bağımlılığı alır. Bu eylemin gerçeklenmesi 'karma kimlik doğrulaması' yapılandırması olarak düşünülebilir.
- Bu makalede, desteklenen modern kimlik doğrulama topolojilerini (yalnızca Skype Kurumsal için gereklidir) seçmenize yardımcı olacak diğer kişilere ve şirket içi ve şirket içi Skype Kurumsal Exchange için kurulum adımlarını veya modern kimlik doğrulamayı devre dışı bırakma adımlarını özetleyen nasıl yapılır makaleleri yer alır. Sunucu ortamınızda modern kimlik doğrulaması kullanmak için bir giriş tabanına ihtiyacınız olacaksa, tarayıcınızda bu sayfayı sık kullanılanlara ekleyin.

## <a name="related-topics"></a>İlgili Konular
<a name="BKMK_URLListforMA"> </a>

- [Şirket içi Exchange Server Modern Kimlik Doğrulaması kullanacak şekilde yapılandırma](configure-exchange-server-for-hybrid-modern-authentication.md)
- [Modern Kimlik Doğrulaması ile desteklenen Skype Kurumsal topolojileri](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)
- [Şirket içi Skype Kurumsal Modern Kimlik Doğrulaması kullanacak şekilde yapılandırma](configure-skype-for-business-for-hybrid-modern-authentication.md)
- [karma modern kimlik doğrulamasını Skype Kurumsal ve Exchange kaldırma veya devre dışı bırakma](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
