---
title: Office 2013 ve Office 2016 istemci uygulamalarında modern kimlik doğrulaması nasıl çalışır?
ms.author: tracyp
author: MSFTTracyP
manager: scotv
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
description: Microsoft 365 modern kimlik doğrulama özelliklerinin Office 2013 ve 2016 istemci uygulamalarında nasıl farklı çalıştığını öğrenin.
ms.openlocfilehash: 9c4cdc384ceded4ce3bb78ae4e67e0f4c5a503de
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093382"
---
# <a name="how-modern-authentication-works-for-office-2013-office-2016-and-office-2019-client-apps"></a>modern kimlik doğrulaması Office 2013, Office 2016 ve Office 2019 istemci uygulamalarında nasıl çalışır?

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Office 2013, Office 2016 ve Office 2019 istemci uygulamalarının Exchange Online, SharePoint Online ve Microsoft 365 kiracısında kimlik doğrulama yapılandırmasına göre modern kimlik doğrulama özelliklerini nasıl kullandığını öğrenmek için bu makaleyi okuyun çevrimiçi Skype Kurumsal.

> [!NOTE]
> Office 2010 ve Office Mac 2011 gibi eski istemci uygulamaları modern kimlik doğrulamasını desteklemez ve yalnızca temel kimlik doğrulamasıyla kullanılabilir.

## <a name="availability-of-modern-authentication-for-microsoft-365-services"></a>Microsoft 365 hizmetleri için modern kimlik doğrulaması kullanılabilirliği

Microsoft 365 hizmetleri için modern kimlik doğrulamasının varsayılan durumu şunlardır:

- varsayılan olarak Exchange Online için **açıktır**. [Kapatmak veya açmak için bkz. Exchange Online'de modern kimlik doğrulamasını etkinleştirme veya devre dışı bırakma](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662).

- SharePoint Online için varsayılan olarak **açıktır**.

- Skype Kurumsal Online için varsayılan olarak **açıktır**. Kapatmak veya açmak için bkz[. Modern kimlik doğrulaması için Skype Kurumsal Online'ı etkinleştirme](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx).

> [!NOTE]
> 1 Ağustos 2017'den **önce** oluşturulan kiracılar için modern kimlik doğrulaması, Exchange Online ve Skype Kurumsal Online için varsayılan olarak **kapatılır**.

## <a name="sign-in-behavior-of-office-client-apps"></a>Office istemci uygulamalarının oturum açma davranışı

Office 2013 istemci uygulamaları varsayılan olarak eski kimlik doğrulamasını destekler. Eski, Microsoft Çevrimiçi Oturum Açma Yardımcısı'nı veya temel kimlik doğrulamasını desteklediği anlamına gelir. Bu istemcilerin modern kimlik doğrulama özelliklerini kullanabilmesi için Windows istemcisinde kayıt defteri anahtarları ayarlanmış olmalıdır. Yönergeler için bkz[. Windows cihazlarda Office 2013 için Modern Kimlik Doğrulamasını Etkinleştirme](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).

Windows çalıştıran ve Microsoft Office 2013'ün yüklü olduğu herhangi bir cihazda (örneğin, dizüstü bilgisayar veya tablet) modern kimlik doğrulamayı etkinleştirmek için, aşağıdaki kayıt defteri anahtarlarını ayarlamanız gerekir. Bu anahtarlar, modern kimlik doğrulamayı etkinleştirmek istediğiniz her cihazda ayarlanmalıdır.

|**Kayıt defteri anahtarı**|**Tür**|**Değer** |
|:-------|:------:|--------:|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL  |REG_DWORD  |1  |
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version |REG_DWORD |1 |

Skype Kurumsal ile nasıl çalıştığı hakkında bilgi edinmek için [Skype Kurumsal ile Modern Kimlik Doğrulaması (ADAL) kullanma](./hybrid-modern-auth-overview.md) bölümünü okuyun.

Office 2016 ve Office 2019 istemcileri varsayılan olarak modern kimlik doğrulamasını destekler ve istemcinin bu yeni akışları kullanması için hiçbir eylem gerekmez. Ancak, eski kimlik doğrulamasını kullanmak için açık eylem gerekir.

Office 2013, Office 2016 ve Office 2019 istemci kimlik doğrulamasının modern kimlik doğrulamasının açık olup olmamasına bağlı olarak Microsoft 365 hizmetleriyle nasıl çalıştığını görmek için aşağıdaki bağlantılara tıklayın.

- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)

- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)

- [Skype Kurumsal Çevrimiçi Sürüm](modern-auth-for-office-2013-and-2016.md#BK_SFBO)

<a name="BK_EchangeOnline"> </a>
### <a name="exchange-online"></a>Exchange Online

Aşağıdaki tabloda, Office 2013, Office 2016 ve Office 2019 istemci uygulamalarının modern kimlik doğrulamasıyla veya modern kimlik doğrulaması olmadan Exchange Online bağlandığı durumlardaki kimlik doğrulama davranışı açıklanmaktadır.

|Office istemci uygulaması sürümü***|Kayıt defteri anahtarı var mı?***|Modern kimlik doğrulaması açık mı?***|Kiracı için modern kimlik doğrulaması açık kimlik doğrulaması davranışı (varsayılan)***|Kiracı için modern kimlik doğrulaması kapalıyken kimlik doğrulama davranışı***|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |No <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Evet  <br/> |Outlook 2013, 2016 veya 2019'da modern kimlik doğrulamayı zorlar. <br/> [Daha fazla bilgi](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Outlook istemcisi içinde modern kimlik doğrulamasını zorlar.<br/> |
|Office 2019  <br/> |Hayır veya EnableADAL = 1  <br/> |Evet  <br/> |Önce modern kimlik doğrulaması denendi. Sunucu modern kimlik doğrulama bağlantısını reddederse temel kimlik doğrulaması kullanılır. Kiracı etkinleştirilmediğinde sunucu modern kimlik doğrulamasını reddeder.  <br/> |Önce modern kimlik doğrulaması denendi. Sunucu modern kimlik doğrulama bağlantısını reddederse temel kimlik doğrulaması kullanılır. Kiracı etkinleştirilmediğinde sunucu modern kimlik doğrulamasını reddeder.  <br/> |
|Office 2019  <br/> |Evet, EnableADAL = 1  <br/> |Evet  <br/> |Önce modern kimlik doğrulaması denendi. Sunucu modern kimlik doğrulama bağlantısını reddederse temel kimlik doğrulaması kullanılır. Kiracı etkinleştirilmediğinde sunucu modern kimlik doğrulamasını reddeder.  <br/> |Önce modern kimlik doğrulaması denendi. Sunucu modern kimlik doğrulama bağlantısını reddederse temel kimlik doğrulaması kullanılır. Kiracı etkinleştirilmediğinde sunucu modern kimlik doğrulamasını reddeder.  <br/> |
|Office 2019  <br/> |Evet, EnableADAL=0  <br/> |Hayır  <br/> |Temel kimlik doğrulaması  <br/> |Temel kimlik doğrulaması  <br/> |
|Office 2016  <br/> |No <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Evet  <br/> |2013, 2016 veya 2019'da modern kimlik doğrulamayı zorlar. <br/> [Daha fazla bilgi](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Outlook istemcisi içinde modern kimlik doğrulamasını zorlar.<br/> |
|Office 2016  <br/> |Hayır veya EnableADAL = 1  <br/> |Evet  <br/> |Önce modern kimlik doğrulaması denendi. Sunucu modern kimlik doğrulama bağlantısını reddederse temel kimlik doğrulaması kullanılır. Kiracı etkinleştirilmediğinde sunucu modern kimlik doğrulamasını reddeder.  <br/> |Önce modern kimlik doğrulaması denendi. Sunucu modern kimlik doğrulama bağlantısını reddederse temel kimlik doğrulaması kullanılır. Kiracı etkinleştirilmediğinde sunucu modern kimlik doğrulamasını reddeder.  <br/> |
|Office 2016  <br/> |Evet, EnableADAL = 1  <br/> |Evet  <br/> |Önce modern kimlik doğrulaması denendi. Sunucu modern kimlik doğrulama bağlantısını reddederse temel kimlik doğrulaması kullanılır. Kiracı etkinleştirilmediğinde sunucu modern kimlik doğrulamasını reddeder.  <br/> |Önce modern kimlik doğrulaması denendi. Sunucu modern kimlik doğrulama bağlantısını reddederse temel kimlik doğrulaması kullanılır. Kiracı etkinleştirilmediğinde sunucu modern kimlik doğrulamasını reddeder.  <br/> |
|Office 2016  <br/> |Evet, EnableADAL=0  <br/> |Hayır  <br/> |Temel kimlik doğrulaması  <br/> |Temel kimlik doğrulaması  <br/> |
|Office 2013  <br/> |Hayır  <br/> |Hayır  <br/> |Temel kimlik doğrulaması  <br/> |Temel kimlik doğrulaması  <br/> |
|Office 2013  <br/> |Evet, EnableADAL = 1  <br/> |Evet  <br/> |Önce modern kimlik doğrulaması denendi. Sunucu modern kimlik doğrulama bağlantısını reddederse temel kimlik doğrulaması kullanılır. Kiracı etkinleştirilmediğinde sunucu modern kimlik doğrulamasını reddeder.  <br/> |Önce modern kimlik doğrulaması denendi. Sunucu modern kimlik doğrulama bağlantısını reddederse temel kimlik doğrulaması kullanılır. Kiracı etkinleştirilmediğinde sunucu modern kimlik doğrulamasını reddeder.  <br/> |

<a name="BK_SharePointOnline"> </a>
### <a name="sharepoint-online"></a>SharePoint Online

Aşağıdaki tabloda, Office 2013, Office 2016 ve Office 2019 istemci uygulamalarının SharePoint Online'a modern kimlik doğrulamasıyla veya modern kimlik doğrulaması olmadan bağlandığındaki kimlik doğrulama davranışı açıklanmaktadır.

|Office istemci uygulaması sürümü***|Kayıt defteri anahtarı var mı?***|Modern kimlik doğrulaması açık mı?***|Kiracı için modern kimlik doğrulaması açık kimlik doğrulaması davranışı (varsayılan)***|Kiracı için modern kimlik doğrulaması kapalıyken kimlik doğrulama davranışı***|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Hayır veya EnableADAL = 1  <br/> |Evet  <br/> |Yalnızca modern kimlik doğrulaması.  <br/> |Bağlantı kurulamaz.  <br/> |
|Office 2019  <br/> |Evet, EnableADAL = 1  <br/> |Evet  <br/> |Yalnızca modern kimlik doğrulaması.  <br/> |Bağlantı kurulamaz.  <br/> |
|Office 2019  <br/> |Evet, EnableADAL = 0  <br/> |Hayır  <br/> |Yalnızca Microsoft Çevrimiçi Oturum Açma Yardımcısı.  <br/> |Yalnızca Microsoft Çevrimiçi Oturum Açma Yardımcısı.  <br/> |
|Office 2016  <br/> |Hayır veya EnableADAL = 1  <br/> |Evet  <br/> |Yalnızca modern kimlik doğrulaması.  <br/> |Bağlantı kurulamaz.  <br/> |
|Office 2016  <br/> |Evet, EnableADAL = 1  <br/> |Evet  <br/> |Yalnızca modern kimlik doğrulaması.  <br/> |Bağlantı kurulamaz.  <br/> |
|Office 2016  <br/> |Evet, EnableADAL = 0  <br/> |Hayır  <br/> |Yalnızca Microsoft Çevrimiçi Oturum Açma Yardımcısı.  <br/> |Yalnızca Microsoft Çevrimiçi Oturum Açma Yardımcısı.  <br/> |
|Office 2013  <br/> |Hayır  <br/> |Hayır  <br/> |Yalnızca Microsoft Çevrimiçi Oturum Açma Yardımcısı.  <br/> |Yalnızca Microsoft Çevrimiçi Oturum Açma Yardımcısı.  <br/> |
|Office 2013  <br/> |Evet, EnableADAL = 1  <br/> |Evet  <br/> |Yalnızca modern kimlik doğrulaması.  <br/> |Bağlantı kurulamaz.  <br/> |

### <a name="skype-for-business-online"></a>Skype Kurumsal Çevrimiçi
<a name="BK_SFBO"> </a>

Aşağıdaki tabloda, Office 2013, Office 2016 ve Office 2019 istemci uygulamalarının Skype Kurumsal Online'a modern kimlik doğrulamasıyla veya modern kimlik doğrulaması olmadan bağlandığındaki kimlik doğrulama davranışı açıklanmaktadır.

|Office istemci uygulaması sürümü***|Kayıt defteri anahtarı var mı?***|Modern kimlik doğrulaması açık mı?***|Kiracı için modern kimlik doğrulaması açık durumda kimlik doğrulama davranışı***|Kiracı için modern kimlik doğrulaması kapalıyken kimlik doğrulama davranışı (varsayılan)***|
|:-----|:-----|:-----|:-----|:-----|
|Office 2019  <br/> |Hayır veya EnableADAL = 1  <br/> |Evet  <br/> |Önce modern kimlik doğrulaması denendi. Sunucu modern kimlik doğrulama bağlantısını reddederse Microsoft Çevrimiçi Oturum Açma Yardımcısı kullanılır. Skype Kurumsal Çevrimiçi kiracılar etkinleştirilmediğinde sunucu modern kimlik doğrulamayı reddeder.  <br/> |Önce modern kimlik doğrulaması denendi. Sunucu modern kimlik doğrulama bağlantısını reddederse Microsoft Çevrimiçi Oturum Açma Yardımcısı kullanılır. Skype Kurumsal Çevrimiçi kiracılar etkinleştirilmediğinde sunucu modern kimlik doğrulamayı reddeder.  <br/> |
|Office 2019  <br/> |Evet, EnableADAL = 1  <br/> |Evet  <br/> |Önce modern kimlik doğrulaması denendi. Sunucu modern kimlik doğrulama bağlantısını reddederse Microsoft Çevrimiçi Oturum Açma Yardımcısı kullanılır. Skype Kurumsal Çevrimiçi kiracılar etkinleştirilmediğinde sunucu modern kimlik doğrulamayı reddeder.  <br/> |Önce modern kimlik doğrulaması denendi. Sunucu modern kimlik doğrulama bağlantısını reddederse Microsoft Çevrimiçi Oturum Açma Yardımcısı kullanılır. Skype Kurumsal Çevrimiçi kiracılar etkinleştirilmediğinde sunucu modern kimlik doğrulamayı reddeder.  <br/> |
|Office 2019  <br/> |Evet, EnableADAL = 0  <br/> |Hayır  <br/> |Yalnızca Microsoft Çevrimiçi Oturum Açma Yardımcısı.  <br/> |Yalnızca Microsoft Çevrimiçi Oturum Açma Yardımcısı.  <br/> |
|Office 2016  <br/> |Hayır veya EnableADAL = 1  <br/> |Evet  <br/> |Önce modern kimlik doğrulaması denendi. Sunucu modern kimlik doğrulama bağlantısını reddederse Microsoft Çevrimiçi Oturum Açma Yardımcısı kullanılır. Skype Kurumsal Çevrimiçi kiracılar etkinleştirilmediğinde sunucu modern kimlik doğrulamayı reddeder.  <br/> |Önce modern kimlik doğrulaması denendi. Sunucu modern kimlik doğrulama bağlantısını reddederse Microsoft Çevrimiçi Oturum Açma Yardımcısı kullanılır. Skype Kurumsal Çevrimiçi kiracılar etkinleştirilmediğinde sunucu modern kimlik doğrulamayı reddeder.  <br/> |
|Office 2016  <br/> |Evet, EnableADAL = 1  <br/> |Evet  <br/> |Önce modern kimlik doğrulaması denendi. Sunucu modern kimlik doğrulama bağlantısını reddederse Microsoft Çevrimiçi Oturum Açma Yardımcısı kullanılır. Skype Kurumsal Çevrimiçi kiracılar etkinleştirilmediğinde sunucu modern kimlik doğrulamayı reddeder.  <br/> |Önce modern kimlik doğrulaması denendi. Sunucu modern kimlik doğrulama bağlantısını reddederse Microsoft Çevrimiçi Oturum Açma Yardımcısı kullanılır. Skype Kurumsal Çevrimiçi kiracılar etkinleştirilmediğinde sunucu modern kimlik doğrulamayı reddeder.  <br/> |
|Office 2016  <br/> |Evet, EnableADAL = 0  <br/> |Hayır  <br/> |Yalnızca Microsoft Çevrimiçi Oturum Açma Yardımcısı.  <br/> |Yalnızca Microsoft Çevrimiçi Oturum Açma Yardımcısı.  <br/> |
|Office 2013  <br/> |Hayır  <br/> |Hayır  <br/> |Yalnızca Microsoft Çevrimiçi Oturum Açma Yardımcısı.  <br/> |Yalnızca Microsoft Çevrimiçi Oturum Açma Yardımcısı.  <br/> |
|Office 2013  <br/> |Evet, EnableADAL = 1  <br/> |Evet  <br/> |Önce modern kimlik doğrulaması denendi. Sunucu modern kimlik doğrulama bağlantısını reddederse Microsoft Çevrimiçi Oturum Açma Yardımcısı kullanılır. Skype Kurumsal Çevrimiçi kiracılar etkinleştirilmediğinde sunucu modern kimlik doğrulamayı reddeder.  <br/> |Yalnızca Microsoft Çevrimiçi Oturum Açma Yardımcısı.  <br/> |

## <a name="see-also"></a>Ayrıca bkz.

[Windows cihazlarında Office 2013 için Modern Kimlik Doğrulamasını etkinleştirme](../admin/security-and-compliance/enable-modern-authentication.md)

[Microsoft 365 için çok faktörlü kimlik doğrulama](../admin/security-and-compliance/multi-factor-authentication-microsoft-365.md)

[Çok faktörlü kimlik doğrulaması ile Microsoft 365 oturum açma](https://support.microsoft.com/office/sign-in-to-microsoft-365-with-multi-factor-authentication-2b856342-170a-438e-9a4f-3c092394d3cb)

[Microsoft 365 Kurumsal genel bakış](microsoft-365-overview.md)