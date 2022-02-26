---
title: Office 2013 ve Office 2016 istemci uygulamaları için modern kimlik doğrulama nasıl çalışır?
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/1/2017
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- MED150
- GMA150
- GPA150
- GEA150
- BCS160
ms.assetid: e4c45989-4b1a-462e-a81b-2a13191cf517
ms.collection:
- M365-security-compliance
description: Modern kimlik Microsoft 365 özellikleri, 2013 ve 2016 istemci Office farklı nasıl çalışır? öğrenin.
ms.openlocfilehash: c3586029a3c1ea73dae30696c74011e3dd22400d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973719"
---
# <a name="how-modern-authentication-works-for-office-2013-office-2016-and-office-2019-client-apps"></a>Office 2013, Office 2016 ve Office 2019 istemci uygulamaları için modern kimlik doğrulama nasıl çalışır?

*Bu makale hem diğer Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Office 2013, Office 2016 ve Office 2019 istemci uygulamalarının Exchange Online, SharePoint Online için Microsoft 365 kiracısında kimlik doğrulama yapılandırmasına bağlı olarak modern kimlik doğrulama özelliklerini nasıl kullanabileceğini öğrenmek için bu makaleyi okuyun ve Skype Kurumsal Online.

> [!NOTE]
> Office 2010 ve Office Mac 2011 gibi eski istemci uygulamaları modern kimlik doğrulamayı desteklemez ve yalnızca temel kimlik doğrulamasıyla kullanılabilir.

## <a name="availability-of-modern-authentication-for-microsoft-365-services"></a>Microsoft 365 hizmetleri için modern kimlik doğrulamanın kullanılabilirliği

Modern Microsoft 365 için, modern kimlik doğrulamanın varsayılan durumu:

- Varsayılan **olarak** Exchange Online açıktır. Bu [özelliği kapatmak veya açmak için bkz. Exchange Online'de modern](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) kimlik doğrulamayı etkinleştirme veya devre dışı bırakma.

- SharePoint  Online için varsayılan olarak açıktır.

- Skype Kurumsal  Online için varsayılan olarak açıktır. Açmak [veya Skype Kurumsal için modern kimlik doğrulaması için bkz. Skype Kurumsal Online'da](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx) etkinleştirme.

> [!NOTE]
> 1 Ağustos 2017'den önce oluşturulan kiracılarda, Exchange Online Skype Kurumsal Online için modern kimlik  doğrulama varsayılan olarak kapalıdır.

## <a name="sign-in-behavior-of-office-client-apps"></a>İstemci uygulamalarının oturum Office davranışı

Office 2013 istemci uygulamaları varsayılan olarak eski kimlik doğrulamasını destekler. Eski, Microsoft Online Oturum Açma Yardımcısı'nın veya temel kimlik doğrulamasını desteklemeleri anlamına gelir. Bu istemcilerin modern kimlik doğrulama özelliklerini kullanamaları için, Windows defteri anahtarlarının ayarlanmış olması gerekir. Yönergeler için bkz. [Mobil cihazlarda Office 2013 için Modern Kimlik Windows etkinleştirme](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).

Windows çalıştıran ve Microsoft Office 2013'ün yüklü olduğu herhangi bir cihazda (örneğin, dizüstü bilgisayar veya tablet) modern kimlik doğrulamayı etkinleştirmek için, aşağıdaki kayıt defteri anahtarlarını ayarlamanız gerekir. Bu anahtarlar, modern kimlik doğrulamayı etkinleştirmek istediğiniz her cihazda ayarlanmalıdır.

|**Kayıt defteri anahtarı**|**Tür**|**Değer** |
|:-------|:------:|--------:|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL  |REG_DWORD  |1  |
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version |REG_DWORD |1 |

Diğer [öğrencilerle nasıl çalıştığını öğrenmek için Skype Kurumsal'da Modern Kimlik Doğrulama (ADAL)](./hybrid-modern-auth-overview.md) kullanma Skype Kurumsal.

Office 2016 ve Office 2019 istemcileri, modern kimlik doğrulamayı varsayılan olarak destekler ve istemcinin bu yeni akışları kullanmak için herhangi bir eyleme gerek yoktur. Ancak, eski kimlik doğrulamasının kullanılaması için açık bir eylem gereklidir.

Office 2013, Office 2016 ve Office 2019 istemci kimlik doğrulamasının, modern kimlik doğrulamanın açık olup olmadığını bağlı olarak Microsoft 365 hizmetleriyle nasıl çalıştığını görmek için aşağıdaki bağlantılara tıklayın.

- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)

- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)

- [Skype Kurumsal Çevrimiçi Sürüm](modern-auth-for-office-2013-and-2016.md#BK_SFBO)

<a name="BK_EchangeOnline"> </a>
### <a name="exchange-online"></a>Exchange Online

Aşağıdaki tabloda, Office 2013, Office 2016 ve Office 2019 istemci uygulamaları Exchange Online'e modern kimlik doğrulama açık veya ücretsiz olarak bağlanıyor.

|Office istemci uygulaması sürümü****|Kayıt defteri anahtarı var?****|Modern kimlik doğrulamada?****|Kiracı için modern kimlik doğrulaması açıkken kimlik doğrulama davranışı (varsayılan)****|Kiracı için modern kimlik doğrulaması kapalıken kimlik doğrulama davranışı****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Hayır, <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Evet  <br/> |2013, 2016 veya 2019'da modern kimlik doğrulamayı Outlook gerektirir. <br/> [Daha fazla bilgi](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Yeni istemci içinde modern kimlik Outlook gerektirir.<br/> |
|Office 2019  <br/> |Hayır veya EnableADAL = 1  <br/> |Evet  <br/> |Önce modern kimlik doğrulama denenir. Sunucu modern kimlik doğrulama bağlantısını reddederse, temel kimlik doğrulaması kullanılır. Kiracı etkin değilken, sunucu modern kimlik doğrulamayı reddeder.  <br/> |Önce modern kimlik doğrulama denenir. Sunucu modern kimlik doğrulama bağlantısını reddederse, temel kimlik doğrulaması kullanılır. Kiracı etkin değilken, sunucu modern kimlik doğrulamayı reddeder.  <br/> |
|Office 2019  <br/> |Evet, EnableADAL = 1  <br/> |Evet  <br/> |Önce modern kimlik doğrulama denenir. Sunucu modern kimlik doğrulama bağlantısını reddederse, temel kimlik doğrulaması kullanılır. Kiracı etkin değilken, sunucu modern kimlik doğrulamayı reddeder.  <br/> |Önce modern kimlik doğrulama denenir. Sunucu modern kimlik doğrulama bağlantısını reddederse, temel kimlik doğrulaması kullanılır. Kiracı etkin değilken, sunucu modern kimlik doğrulamayı reddeder.  <br/> |
|Office 2019  <br/> |Evet, EnableADAL=0  <br/> |Hayır  <br/> |Temel kimlik doğrulaması  <br/> |Temel kimlik doğrulaması  <br/> |
|Office 2016  <br/> |Hayır, <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Evet  <br/> |2013, 2016 veya 2019'da modern kimlik doğrulamayı gerektirir. <br/> [Daha fazla bilgi](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Yeni istemci içinde modern kimlik Outlook gerektirir.<br/> |
|Office 2016  <br/> |Hayır veya EnableADAL = 1  <br/> |Evet  <br/> |Önce modern kimlik doğrulama denenir. Sunucu modern kimlik doğrulama bağlantısını reddederse, temel kimlik doğrulaması kullanılır. Kiracı etkin değilken, sunucu modern kimlik doğrulamayı reddeder.  <br/> |Önce modern kimlik doğrulama denenir. Sunucu modern kimlik doğrulama bağlantısını reddederse, temel kimlik doğrulaması kullanılır. Kiracı etkin değilken, sunucu modern kimlik doğrulamayı reddeder.  <br/> |
|Office 2016  <br/> |Evet, EnableADAL = 1  <br/> |Evet  <br/> |Önce modern kimlik doğrulama denenir. Sunucu modern kimlik doğrulama bağlantısını reddederse, temel kimlik doğrulaması kullanılır. Kiracı etkin değilken, sunucu modern kimlik doğrulamayı reddeder.  <br/> |Önce modern kimlik doğrulama denenir. Sunucu modern kimlik doğrulama bağlantısını reddederse, temel kimlik doğrulaması kullanılır. Kiracı etkin değilken, sunucu modern kimlik doğrulamayı reddeder.  <br/> |
|Office 2016  <br/> |Evet, EnableADAL=0  <br/> |Hayır  <br/> |Temel kimlik doğrulaması  <br/> |Temel kimlik doğrulaması  <br/> |
|Office 2013  <br/> |Hayır  <br/> |Hayır  <br/> |Temel kimlik doğrulaması  <br/> |Temel kimlik doğrulaması  <br/> |
|Office 2013  <br/> |Evet, EnableADAL = 1  <br/> |Evet  <br/> |Önce modern kimlik doğrulama denenir. Sunucu modern kimlik doğrulama bağlantısını reddederse, temel kimlik doğrulaması kullanılır. Kiracı etkin değilken, sunucu modern kimlik doğrulamayı reddeder.  <br/> |Önce modern kimlik doğrulama denenir. Sunucu modern kimlik doğrulama bağlantısını reddederse, temel kimlik doğrulaması kullanılır. Kiracı etkin değilken, sunucu modern kimlik doğrulamayı reddeder.  <br/> |

<a name="BK_SharePointOnline"> </a>
### <a name="sharepoint-online"></a>SharePoint Online

Aşağıdaki tabloda, Office Online'a modern kimlik doğrulama açık veya modern kimlik doğrulama açık ve açık bir şekilde bağlanarak Office 2013, Office 2016 ve SharePoint Office 2019 istemci uygulamaları için kimlik doğrulama davranışı açık almaktadır.

|Office istemci uygulaması sürümü****|Kayıt defteri anahtarı var?****|Modern kimlik doğrulamada?****|Kiracı için modern kimlik doğrulaması açıkken kimlik doğrulama davranışı (varsayılan)****|Kiracı için modern kimlik doğrulaması kapalıken kimlik doğrulama davranışı****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Hayır veya EnableADAL = 1  <br/> |Evet  <br/> |Yalnızca modern kimlik doğrulaması.  <br/> |Bağlantı kuramaz.  <br/> |
|Office 2019  <br/> |Evet, EnableADAL = 1  <br/> |Evet  <br/> |Yalnızca modern kimlik doğrulaması.  <br/> |Bağlantı kuramaz.  <br/> |
|Office 2019  <br/> |Evet, EnableADAL = 0  <br/> |Hayır  <br/> |Yalnızca Microsoft Online Oturum Açma Yardımcısı.  <br/> |Yalnızca Microsoft Online Oturum Açma Yardımcısı.  <br/> |
|Office 2016  <br/> |Hayır veya EnableADAL = 1  <br/> |Evet  <br/> |Yalnızca modern kimlik doğrulaması.  <br/> |Bağlantı kuramaz.  <br/> |
|Office 2016  <br/> |Evet, EnableADAL = 1  <br/> |Evet  <br/> |Yalnızca modern kimlik doğrulaması.  <br/> |Bağlantı kuramaz.  <br/> |
|Office 2016  <br/> |Evet, EnableADAL = 0  <br/> |Hayır  <br/> |Yalnızca Microsoft Online Oturum Açma Yardımcısı.  <br/> |Yalnızca Microsoft Online Oturum Açma Yardımcısı.  <br/> |
|Office 2013  <br/> |Hayır  <br/> |Hayır  <br/> |Yalnızca Microsoft Online Oturum Açma Yardımcısı.  <br/> |Yalnızca Microsoft Online Oturum Açma Yardımcısı.  <br/> |
|Office 2013  <br/> |Evet, EnableADAL = 1  <br/> |Evet  <br/> |Yalnızca modern kimlik doğrulaması.  <br/> |Bağlantı kuramaz.  <br/> |

### <a name="skype-for-business-online"></a>Skype Kurumsal Çevrimiçi
<a name="BK_SFBO"> </a>

Aşağıdaki tablo, Office Online'a modern kimlik doğrulama açık veya modern kimlik doğrulama açık veya açık bir şekilde bağlanarak Office 2013, Office 2016 ve Skype Kurumsal Office 2019 istemci uygulamaları için kimlik doğrulama davranışını açıklar.

|Office istemci uygulaması sürümü****|Kayıt defteri anahtarı var?****|Modern kimlik doğrulamada?****|Kiracı için modern kimlik doğrulaması açıkken kimlik doğrulama davranışı****|Kiracı için modern kimlik doğrulaması kapalı olan kimlik doğrulama davranışı (varsayılan)****|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Hayır veya EnableADAL = 1  <br/> |Evet  <br/> |Önce modern kimlik doğrulama denenir. Sunucu modern kimlik doğrulama bağlantısını reddederse, Microsoft Online Oturum Açma Yardımcısı kullanılır. Skype Kurumsal Online kiracıları etkin değilken, sunucu modern kimlik doğrulamayı reddeder.  <br/> |Önce modern kimlik doğrulama denenir. Sunucu modern kimlik doğrulama bağlantısını reddederse, Microsoft Online Oturum Açma Yardımcısı kullanılır. Skype Kurumsal Online kiracıları etkin değilken, sunucu modern kimlik doğrulamayı reddeder.  <br/> |
|Office 2019  <br/> |Evet, EnableADAL = 1  <br/> |Evet  <br/> |Önce modern kimlik doğrulama denenir. Sunucu modern kimlik doğrulama bağlantısını reddederse, Microsoft Online Oturum Açma Yardımcısı kullanılır. Skype Kurumsal Online kiracıları etkin değilken, sunucu modern kimlik doğrulamayı reddeder.  <br/> |Önce modern kimlik doğrulama denenir. Sunucu modern kimlik doğrulama bağlantısını reddederse, Microsoft Online Oturum Açma Yardımcısı kullanılır. Skype Kurumsal Online kiracıları etkin değilken, sunucu modern kimlik doğrulamayı reddeder.  <br/> |
|Office 2019  <br/> |Evet, EnableADAL = 0  <br/> |Hayır  <br/> |Yalnızca Microsoft Online Oturum Açma Yardımcısı.  <br/> |Yalnızca Microsoft Online Oturum Açma Yardımcısı.  <br/> |
|Office 2016  <br/> |Hayır veya EnableADAL = 1  <br/> |Evet  <br/> |Önce modern kimlik doğrulama denenir. Sunucu modern kimlik doğrulama bağlantısını reddederse, Microsoft Online Oturum Açma Yardımcısı kullanılır. Skype Kurumsal Online kiracıları etkin değilken, sunucu modern kimlik doğrulamayı reddeder.  <br/> |Önce modern kimlik doğrulama denenir. Sunucu modern kimlik doğrulama bağlantısını reddederse, Microsoft Online Oturum Açma Yardımcısı kullanılır. Çevrimiçi kiracılar etkin değilken, Skype Kurumsal modern kimlik doğrulamayı reddeder.  <br/> |
|Office 2016  <br/> |Evet, EnableADAL = 1  <br/> |Evet  <br/> |Önce modern kimlik doğrulama denenir. Sunucu modern kimlik doğrulama bağlantısını reddederse, Microsoft Online Oturum Açma Yardımcısı kullanılır. Çevrimiçi kiracılar etkin değilken, Skype Kurumsal modern kimlik doğrulamayı reddeder.  <br/> |Önce modern kimlik doğrulama denenir. Sunucu modern kimlik doğrulama bağlantısını reddederse, Microsoft Online Oturum Açma Yardımcısı kullanılır. Çevrimiçi kiracılar etkin değilken, Skype Kurumsal modern kimlik doğrulamayı reddeder.  <br/> |
|Office 2016  <br/> |Evet, EnableADAL = 0  <br/> |Hayır  <br/> |Yalnızca Microsoft Online Oturum Açma Yardımcısı.  <br/> |Yalnızca Microsoft Online Oturum Açma Yardımcısı.  <br/> |
|Office 2013  <br/> |Hayır  <br/> |Hayır  <br/> |Yalnızca Microsoft Online Oturum Açma Yardımcısı.  <br/> |Yalnızca Microsoft Online Oturum Açma Yardımcısı.  <br/> |
|Office 2013  <br/> |Evet, EnableADAL = 1  <br/> |Evet  <br/> |Önce modern kimlik doğrulama denenir. Sunucu modern kimlik doğrulama bağlantısını reddederse, Microsoft Online Oturum Açma Yardımcısı kullanılır. Çevrimiçi kiracılar etkin değilken, Skype Kurumsal modern kimlik doğrulamayı reddeder.  <br/> |Yalnızca Microsoft Online Oturum Açma Yardımcısı.  <br/> |

## <a name="see-also"></a>Ayrıca bkz.

[Windows cihazlarında Office 2013 için Modern Kimlik Doğrulamasını etkinleştirme](../admin/security-and-compliance/enable-modern-authentication.md)

[Etki için çok faktörlü kimlik Microsoft 365](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md)

[Multi-Factor Authentication Microsoft 365 oturum açma](https://support.microsoft.com/office/sign-in-to-microsoft-365-with-multi-factor-authentication-2b856342-170a-438e-9a4f-3c092394d3cb)

[Microsoft 365 Kurumsal genel bakış](microsoft-365-overview.md)