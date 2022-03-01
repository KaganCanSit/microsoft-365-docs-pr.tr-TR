---
title: Şirket içi posta ve şirket içi sunucularla kullanmak için karma Modern Kimlik Skype Kurumsal genel Exchange önkoşulları
ms.author: kvice
ms.reviewer: smithre4
author: kelleyvice-msft
manager: laurawi
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
description: Bu makalede, Karma Modern Kimlik Doğrulama hakkında bilgi edinecek ve şirket içi kimlik doğrulaması ve sunucularında Skype Kurumsal önkoşulları Exchange olacak.
ms.openlocfilehash: f0abb01b7a03405f576a12766b21b3c36113004d
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015206"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>Karma modern kimlik doğrulamasına genel bakış ve bunu şirket içi şirket içi sunucularla ve şirket içi sunucularla Skype Kurumsal için Exchange önkoşullar

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

_Modern Kimlik_ Doğrulama, daha güvenli kullanıcı kimlik doğrulaması ve yetkilendirme sunan bir kimlik yönetimi yöntemidir. Karma dağıtımlarda, Office 365 sunucu şirket için Skype Kurumsal sunucu ve Exchange karma dağıtımları için Skype Kurumsal kullanılabilir. Bu makalede önkoşullar, modern kimlik doğrulamayı ayarlama/devre dışı bırakma ve ilgili istemcilerden bazılarının (örneğin, Outlook ve Skype) bilgilerini içerir.

- [Modern kimlik doğrulama nedir?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
- [Modern kimlik doğrulamayı kullanıca hangi değişiklikler olur?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
- [Şirket içi ortamınız için modern kimlik doğrulama durumunu denetleme](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
- [Modern kimlik doğrulama önkoşullarını karşııyor musunuz?](#do-you-meet-modern-authentication-prerequisites)
- [Başlamadan önce başka ne bil ihtiyacım var?](hybrid-modern-auth-overview.md#BKMK_Whatelse)

## <a name="what-is-modern-authentication"></a>Modern kimlik doğrulama nedir?
<a name="BKMK_WhatisModAuth"> </a>

Modern kimlik doğrulama, bir istemciyle (örneğin, dizüstü bilgisayarınız veya telefonunuz) bir sunucu arasında kimlik doğrulama ve yetkilendirme yöntemlerinin bir bileşimini ve ayrıca zaten bildiğiniz erişim ilkelerine güvenen bazı güvenlik önlemlerini bir arada bulunduran genel bir terimdir. İçindekiler:

- **Kimlik doğrulama yöntemleri**: Çok faktörlü kimlik doğrulaması (MFA); akıllı kart kimlik doğrulaması; istemci sertifika tabanlı kimlik doğrulaması
- **Yetkilendirme yöntemleri**: Microsoft'un Açık Yetkilendirme (OAuth) uygulamasını uygulama
- **Koşullu erişim ilkeleri**: Mobil Uygulama Yönetimi (MAM) ve Azure Active Directory (Azure AD) Koşullu Erişimi

Modern kimlik doğrulamasıyla kullanıcı kimliklerinin yönetilmesi yöneticilerin kaynakların güvenliğini sağlama konusunda birçok farklı araç kullanmalarını sağlar ve hem şirket içi (Exchange hem de Skype Kurumsal), Exchange karma ve Skype Kurumsal karma/bölünmüş etki alanı senaryolarına daha güvenli kimlik yönetimi yöntemleri sunar.

Kullanıcı Skype Kurumsal kimlik bilgileriyle Exchange olduğundan, istemci Skype Kurumsal oturum açma davranışı kullanıcı kimlik doğrulamasının modern kimlik doğrulaması durumundan Exchange. Her iki konumda da yer alan kullanıcılarla Skype Kurumsal Skype Kurumsal Online'a  ve Skype Kurumsal şirket içinde sahip olduğunuz bir bölünmüş etki alanı karma mimarisine sahip olursanız, bu da geçerlidir.

Bu uygulamada modern kimlik doğrulama hakkında daha fazla Office 365 için bkz[. Office 365 İstemci Uygulaması Desteği - Multi-Factor Authentication](microsoft-365-client-support-multi-factor-authentication.md).

> [!IMPORTANT]
> Ağustos 2017'den itibaren, Office 365 Skype Kurumsal online ve Exchange içeren tüm yeni kiracılar modern kimlik doğrulamayı varsayılan olarak etkinleştirecek. Önceden var olan kiracıların varsayılan MA durumlarında bir değişiklik olmayacaktır, ama tüm yeni kiracılar yukarıda listelenen, genişletilmiş kimlik özellikleri kümelerini otomatik olarak destekler. MA'nizin durumunu kontrol etmek [için, Şirket içi ortamının modern kimlik doğrulama durumunu denetleme bölümüne](hybrid-modern-auth-overview.md#BKMK_CheckStatus) bakın.

## <a name="what-changes-when-i-use-modern-authentication"></a>Modern kimlik doğrulamayı kullanıca hangi değişiklikler olur?
<a name="BKMK_WhatChanges"> </a>

Şirket içi Skype Kurumsal veya Exchange sunucusuyla modern kimlik doğrulama kullanırken, hala şirket içi kullanıcıların kimlik doğrulamasını yaptığınız ama kaynaklara (dosyalar veya e-postalar gibi) erişimlerini yetkilendirme yazıları  değişir. İşte bu nedenle modern kimlik doğrulama istemci ve sunucu iletişimiyle ilgili olsa da, MA'nın yapılandırılması sırasında atılan adımlar evoSTS'nin (Azure AD tarafından kullanılan Güvenlik Belirteci Hizmeti) Skype Kurumsal ve Exchange sunucusu için Auth Server olarak ayarlanmış şirket içi olmasıyla sonuç verir.

EvoSTS'ye yapılan değişiklik, şirket içi sunucularının istemcilerinizi yetkilendirmek için OAuth'dan (belirteç verme verme) yararlanmasını sağlar ve ayrıca şirket içinizin bulutta ortak olan güvenlik yöntemlerini (Multi-Factor Authentication gibi) kullanmasını sağlar. Buna ek olarak, kullanıcıların isteğin bir parçası olarak parolalarını vermeden kaynaklara erişim isteğinda  olmasına olanak sağlayan evoSTS sorun belirteçleri. Kullanıcılarınızı nerede barındırıyor olursanız olun (çevrimiçi veya şirket içinde), ve gereken kaynağı barındıran konum ne olursa olsun, Modern kimlik doğrulama yapılandırıldığında EvoSTS kullanıcıların ve istemcilerin yetkilendirmenin temel kaynağı haline gelecektir.

Örneğin, bir Skype Kurumsal kullanıcı adına takvim bilgilerini almak için Exchange sunucusuna erişmesi gerekirse, bu işlemi yapmak için Microsoft Kimlik Doğrulama Kitaplığı'nın (MSAL) kullanır. MSAL, dizininizin güvenlik kaynaklarını OAuth güvenlik belirteçleri kullanılarak istemci uygulamalarına kullanılabilir hale yapacak şekilde tasarlanmış bir kod kitaplığıdır. MSAL, kullanıcıya kaynak erişimi vermek için, talepleri doğrulamak ve belirteçleri (parolalar yerine) takas etmek için OAuth ile birlikte çalışır. Geçmişte, buna benzer bir işlemde (kullanıcı taleplerini nasıl doğrulayanın ve gerekli belirteçlerin nasıl çıkarı olduğunu bilen sunucu) şirket içinde bir Güvenlik Belirteci Hizmeti, hatta Active Directory Federasyon Hizmetleri bile olabilir. Bununla birlikte, modern kimlik doğrulama Azure AD kullanarak bu yetkiyi merkezi hale verir.

Bu aynı zamanda Exchange sunucunuz ve Skype Kurumsal ortamlarınız tamamen şirket içi olsa bile, yetkili sunucunun çevrimiçi olması ve şirket içi ortamının Bulutta (ve aboneliğinizin dizin olarak kullandığı Azure AD örneğinde) Office 365 aboneliğiniz için bir bağlantı oluşturabilme ve bu aboneliğe sahip olması gerekir.

Neler değişmiyor? Bölünmüş etki alanı karma kullanıyor veya şirket içi Skype Kurumsal Exchange sunucu kullanıyor olun, ilk olarak tüm kullanıcıların şirket içinde kimlik *doğrulaması yapmaları gerekir*. Modern kimlik doğrulamanın karma bir uygulamasında, _Lyncdiscover ve_ Otomatik Bulma'nın her _ikisi_ de şirket içi sunucuyu gösterir.

> [!IMPORTANT]
> MA tarafından desteklenen belirli Skype Kurumsal hakkında bilginiz varsa, bu belge [burada belgelenmiş olur](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported).

## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>Şirket içi ortamınız için modern kimlik doğrulama durumunu denetleme
<a name="BKMK_CheckStatus"> </a>

Modern kimlik doğrulama, hizmetler OAuth/S2S uygulanırken kullanılan yetkilendirme sunucusunu değiştirir çünkü, şirket içi kimlik doğrulama ve ortamlar için modern kimlik doğrulamanın etkinleştirildiğinde veya devre dışı bırak Skype Kurumsal Exchange gerekir. Aşağıdaki PowerShell komutunu çalıştırarak Exchange sunucular tablodaki durumu kontrol edin:

```powershell
Get-OrganizationConfig | ft OAuth*
```

_OAuth2ClientProfileEnabled özelliğinin_ değeri **False** ise, modern kimlik doğrulama devre dışı bırakılır.

[Get-OrganizationConfig](/powershell/module/exchange/get-organizationconfig) Get-OrganizationConfig daha fazla bilgi için bkz.

Skype Kurumsal sunucularınızı kontrol etmek için aşağıdaki PowerShell komutunu çalıştırabilirsiniz:

```powershell
Get-CSOAuthConfiguration
```

Komut boş bir _OAuthServers_ özelliği döndürürse veya _ClientADALAuthOverride_ özelliğinin değeri **İzin** Verilmiyorsa, modern kimlik doğrulama devre dışı bırakılır.

Cmdlet'ini Get-CsOAuthConfiguration için bkz. [Get-CsOAuthConfiguration](/powershell/module/skype/get-csoauthconfiguration).

## <a name="do-you-meet-modern-authentication-prerequisites"></a>Modern kimlik doğrulama önkoşullarını karşııyor musunuz?

Devam etmek için önce bu öğeleri doğrulayın ve listenizi kapatın:

- **Skype Kurumsal belirli**
  - Tüm sunucuların 2015 veya sonraki son güncelleştirmeleri için Mayıs 2017 toplu güncelleştirmesi (CU5) Skype Kurumsal Sunucu gerekir
    - **Özel** Durum - Ölçeklenebilirlik Dalı Cihazı (SBA) geçerli sürümde olabilir (Lync 2013'e bağlı olarak)
  - SIP etki alanınız, başka bir Office 365
  - Tüm SFB Ön Uçlarının, Office 365 URL'leri ve IP adresi aralıkları 'Microsoft 365 Ortak ve Office Office 365' bölümündeki Satır 56 ve 125'te listelenen, Office 365 Kimlik Doğrulama URL'leri (TCP 443) ve iyi bilinen sertifika kök [CRL'leri](urls-and-ip-address-ranges.md) (TCP 80) için İnternet'e giden bağlantıları olması gerekir.

- **Skype Kurumsal karma bir çalışma ortamında Office 365 olabilir**
  - 2019 Skype Kurumsal Sunucu da çalışan tüm sunucuların olduğu, Skype Kurumsal Sunucu bir dağıtım.
  - 2015 Skype Kurumsal Sunucu te çalışan tüm sunucuların olduğu bir Skype Kurumsal Sunucu 2015 dağıtımı.
  - Aşağıda listelenmiş olarak en fazla iki farklı sunucu sürümüne sahip bir dağıtım:
    - Skype Kurumsal Sunucu 2015
    - Skype Kurumsal Sunucu 2019
  - Tüm Skype Kurumsal en son toplu güncelleştirmelerin yüklenmiş olması gerekir. Tüm kullanılabilir [güncelleştirmeleri](/skypeforbusiness/sfb-server-updates) bulmak Skype Kurumsal Sunucu yönetmek için bkz. En son toplu güncelleştirmeleri yükleme.
  - Karma ortamda Lync Server 2010 veya 2013 yoktur.

>[!NOTE]
>Skype Kurumsal ön uç sunucularınız İnternet erişimi için bir proxy sunucusu kullanıyorsa, kullanılan ara sunucu IP'si ve Bağlantı Noktası numarası her ön uç için web.config dosyasının yapılandırma bölümüne girilir.

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
> Gerekli URL'lerin en son [listeleriyle güncel Office 365](urls-and-ip-address-ranges.md) için RSS akışına abone Office 365 URL'leri ve IP adresi aralıklarını takip edebilirsiniz.

- **Exchange Server özel**
  - Exchange sunucusu 2013 CU19 ve yukarı, Exchange sunucusu 2016 CU8 ve Exchange Server 2019 CU1 ve daha yenilerini kullanasınız.
  - Ortamda Exchange Server 2010 yoktur.
  - SSL Offloading yapılandırılmadı. SSL sonlandırma ve yeniden şifreleme de desteklenir.
  - Ortamınız sunucuların İnternet'e bağlanmasına izin vermek için bir ara sunucu altyapısı kullanıyorsa, tüm Exchange sunucularının [InternetWebProxy](/powershell/module/exchange/set-exchangeserver) özelliğinde tanımlanmış bir ara sunucuya sahip olduğundan emin olun.

- **Exchange Server bir karma karma ortam içinde Office 365 olabilir**

  - Exchange Server 2013 kullanıyorsanız, en az bir sunucunun Posta Kutusu ve İstemci Erişimi sunucu rolleri yüklü olması gerekir. Posta Kutusu ve İstemci Erişimi rollerini ayrı sunuculara yüklemek mümkün olduğu gibi, daha fazla güvenilirlik ve gelişmiş performans sağlamak için her iki rolü de aynı sunucuya yüklemenizi kesinlikle öneririz.
  - Exchange Server 2016 veya sonraki bir sürümünü kullanıyorsanız, en az bir sunucunun Posta kutusu sunucu rolü yüklü olması gerekir.
  - Karma Exchange 2007 veya 2010 hiçbir sunucu yok.
  - Tüm Exchange en son toplu güncelleştirmelerin yüklenmiş olması gerekir. Tüm kullanılabilir [güncelleştirmeleri](/exchange/plan-and-deploy/install-cumulative-updates) bulmak ve yönetmek için bkz. Exchange Toplu Güncelleştirmeleri en son Toplu Güncelleştirmelere yükseltme.

- **Exchange istemci ve protokol gereksinimlerini karşılama**

    Modern kimlik doğrulamanın kullanılabilirliği istemcinin, protokolün ve yapılandırmanın bileşimine göre belirlenir. Modern kimlik doğrulama istemci, protokol ve/veya yapılandırma tarafından desteklenmiyorsa, istemci eski kimlik doğrulamayı kullanmaya devam eder.
  
    Aşağıdaki istemciler ve protokoller, ortamda modern kimlik Exchange etkinleştirildiğinde şirket içi kimlik doğrulamasıyla modern kimlik doğrulamayı destekler:

  |**İstemciler**|**Birincil Protokol**|**Notlar**|
  |:-----|:-----|:-----|
  |Outlook 2013 ve sonrası  <br/> |HTTP üzerinden MAPI  <br/> |Bu istemcilerle modern kimlik doğrulamasının (Exchange 2013 Service Pack 1 ve üzerinin yeni yüklemeleri için etkin veya True) kullanılam için HTTP üzerinden MAPI'nin Exchange içinde etkinleştirilmesi gerekir; daha fazla bilgi için bkz. [Office 2013 ve Office 2016](modern-auth-for-office-2013-and-2016.md) istemci uygulamaları için modern kimlik doğrulama nasıl çalışır?  <br/> Office 365 için gereken en düşük derlemeyi Outlook bkz. Outlook [Installer (MSI) kullanan Windows sürümleri için güncelleştirmeler](/officeupdates/outlook-updates-msi).  <br/> |
  |Mac için Outlook 2016 ve sonrası  <br/> |Exchange Web Hizmetleri  <br/> |  <br/> |
  |iOS Outlook Android için uygulama  <br/> | Microsoft eşitleme teknolojisi <br/> |Daha [fazla bilgi için bkz. iOS ve Android Outlook Kimlik Doğrulama ile karma Modern](/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) Kimlik Doğrulamayı kullanma.  <br/> |
  |Exchange ActiveSync (örneğin, iOS11 Posta)  <br/> |Exchange ActiveSync  <br/> |Modern Exchange ActiveSync destekleyen diğer istemcilerde, temel kimlik doğrulamadan modern kimlik doğrulamaya geçiş yapmak için profili yeniden oluşturmanız gerekir.  <br/> |

    Listelenmiyor istemciler ve/veya protokoller (örneğin, POP3) şirket içi kimlik doğrulamayı desteklemez Exchange ortamda modern kimlik doğrulama etkinleştirilse bile eski kimlik doğrulama mekanizmalarını kullanmaya devam eder.

- **Genel önkoşullar**
  - Kaynak ormanı senaryoları, karma modern kimlik doğrulama istekleri sırasında doğru SID aramalarının gerçekleştirilir olması için hesap ormanıyla iki yollı bir güven gerektirir. 
  - AD FS kullanıyorsanız, federasyon için Windows 2012 R2 AD FS 3.0 ve üstü gerekir.
  - Kimlik yapılandırmaları, azure ad Bağlan tarafından desteklenen parola karması eşitlemesi, geçişli kimlik doğrulaması ve şirket içi STS gibi kullanıcı tarafından desteklenen türlerden Office 365.
  - Kullanıcı çoğaltması ve Bağlan için yapılandırılmış ve işlevli Azure AD bağlantınız var.
  - Karmanın, şirket içi ve Exchange ortamınız arasında Klasik Karma Topoloji modu kullanılarak yapılandırıldığından Office 365 var. Karma karma için resmi Exchange CU veya mevcut CU - 1 olması gerektiğini söylüyor.
    > [!NOTE]
    > Karma modern kimlik doğrulaması, Karma [Aracı'da desteklenmiyor](/exchange/hybrid-deployment/hybrid-agent).

  - Hem şirket içi test kullanıcısını hem de Office 365'te oturum alıkan karma bir test kullanıcısını (Skype Kurumsal Skype ile modern kimlik doğrulamayı kullanmak için) ve Microsoft Outlook'te (Exchange ile modern kimlik doğrulamayı kullanmak istiyorsanız) oturum aça olduğundan emin olun.

## <a name="what-else-do-i-need-to-know-before-i-begin"></a>Başlamadan önce başka ne bil ihtiyacım var?
<a name="BKMK_Whatelse"> </a>

- Şirket içi sunucuların tüm senaryoları, modern kimlik doğrulamasını şirket içinde ayarlamayı içerir (aslında Skype Kurumsal'te desteklenen topolojilerin listesi vardır) dolayısıyla kimlik doğrulama ve yetkilendirmeden sorumlu olan sunucu Microsoft Bulut'ta ('evoSTS' olarak adlandırılan Azure AD'nin güvenlik belirteci hizmeti) ve şirket içi yüklemeniz tarafından kullanılan URL'ler veya ad alanları hakkında Azure AD'nin güncelleştirilsini içerir Skype Kurumsal veya Exchange. Bu nedenle, şirket içi sunucular Microsoft Bulut bağımlılığına sahip olur. Bu eylemin gerçek olması 'karma kimlik doğrulaması'nın yapılandırılması düşünülebilir.
- Bu makale, desteklenen modern kimlik doğrulama topolojilerini (yalnızca Skype Kurumsal için gereklidir) seçmenize yardımcı olacak diğer bağlantıları ve kurulum adımlarını veya şirket içi ve şirket içi Exchange için modern kimlik doğrulamayı devre dışı bırakma adımlarını içeren nasıl Skype Kurumsal makalelerine yöneliktir. Sunucu ortamınıza modern kimlik doğrulamayı kullanmak için bir giriş sayfası gerekirse tarayıcınızda bu sayfayı sık kullanılanlara ekleyin.

## <a name="related-topics"></a>İlgili Konular
<a name="BKMK_URLListforMA"> </a>

- [Şirket içinde Exchange Server Modern Kimlik Doğrulamayı kullanmak üzere yapılandırma](configure-exchange-server-for-hybrid-modern-authentication.md)
- [Skype Kurumsal Kimlik Doğrulama ile desteklenen topolojiler](/skypeforbusiness/plan-your-deployment/modern-authentication/topologies-supported)
- [Şirket içinde Skype Kurumsal Modern Kimlik Doğrulamayı kullanmak üzere yapılandırma](configure-skype-for-business-for-hybrid-modern-authentication.md)
- [Karma Modern Kimlik Doğrulama'nın dosya ve ağ bağlantılarından Skype Kurumsal veya devre dışı Exchange](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
