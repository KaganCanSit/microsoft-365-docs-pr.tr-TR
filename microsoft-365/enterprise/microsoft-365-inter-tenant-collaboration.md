---
title: Kiracılar arası işbirliğini Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- M365-subscription-management
- SPO_Content
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
f1.keywords:
- NOCSH
description: Microsoft 365 işbirliğinin kiracılar ve kuruluşlar arasında nasıl çalıştığını ve farklı kuruluşların güvenli bir şekilde birlikte çalışmasını sağlamayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 517e015a463a501ad7b9a295a80531595c650454
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100489"
---
# <a name="microsoft-365-inter-tenant-collaboration"></a>Kiracılar arası işbirliğini Microsoft 365

Fabrikam ve Contoso adlı iki kuruluşun her birinin iş kiracısı için bir Microsoft 365 olduğunu ve bazıları sınırlı bir süre için çalışan ve bazıları devam eden çeşitli projelerde birlikte çalışmak istediklerini varsayalım. Fabrikam ve Contoso, kişilerinin ve ekiplerinin farklı Microsoft 365 kiracıları arasında güvenli bir şekilde daha etkili bir şekilde işbirliği yapmasını nasıl sağlayabilir? Microsoft 365, Azure Active Directory (Azure AD) B2B işbirliğiyle birlikte çeşitli seçenekler sunar. Bu makalede, Fabrikam ve Contoso'nun dikkate alabildiği çeşitli önemli senaryolar açıklanmaktadır.

Microsoft 365 kiracılar arası işbirliği seçenekleri arasında dosyalar ve konuşmalar için merkezi bir konum kullanma, takvimleri paylaşma, iletişim için anlık ileti, sesli/görüntülü aramalar kullanma ve kaynaklara ve uygulamalara erişimin güvenliğini sağlama yer alır. Çözümleri seçmek ve daha fazla bilgi edinmek için aşağıdaki tabloları kullanın.

## <a name="exchange-online-collaboration-options"></a>İşbirliği seçeneklerini Exchange Online

| Paylaşım hedefi | Yönetim eylemi | Nasıl yapılır bilgileri |
|:-----|:-----|:-----|
|Takvimleri başka bir Microsoft 365 kuruluşla paylaşma |Yöneticiler, Exchange Online işletmelerin diğer işletmelerle işbirliği yapmasına ve kullanıcıların zamanlamaları (serbest/meşgul bilgileri) başkalarıyla paylaşmasına izin vermek için farklı takvim erişimi düzeyleri ayarlayabilir. | <ul><li>[Paylaşım](/exchange/sharing/sharing) </li><li> [Kuruluş ilişkileri](/exchange/sharing/organization-relationships/organization-relationships) </li><li> [Kuruluş ilişkisi oluşturma](/exchange/sharing/organization-relationships/create-an-organization-relationship) </li><li> [Kuruluş ilişkisini değiştirme](/exchange/sharing/organization-relationships/modify-an-organization-relationship) </li><li> [Kuruluş ilişkisini kaldırma](/exchange/sharing/organization-relationships/remove-an-organization-relationship) </li><li> [Dış kullanıcılarla takvimleri paylaşma](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) </li></ul> |
|Kullanıcıların takvimlerini kuruluşunuzun dışındaki kişilerle nasıl paylaşacaklarını denetleme | Yöneticiler, kimlerle paylaşılabilir ve erişim düzeyini denetlemek için kullanıcı posta kutularına paylaşım ilkeleri uygular |  <ul><li> [Paylaşım ilkeleri](/exchange/sharing/sharing-policies/sharing-policies) </li><li> [Paylaşım ilkesi oluşturma](/exchange/sharing/sharing-policies/create-a-sharing-policy) </li><li> [Posta kutularına paylaşım ilkesi uygulama](/exchange/sharing/sharing-policies/apply-a-sharing-policy) </li><li> [Paylaşım ilkesini değiştirme, devre dışı bırakma veya kaldırma](/exchange/sharing/sharing-policies/modify-a-sharing-policy) </li></ul> |
|İş ortağı kuruluşlarla güvenli e-posta kanallarını yapılandırma ve posta akışını denetleme | Yöneticiler, iş ortağı kuruluş veya hizmet sağlayıcısıyla posta alışverişlerine güvenlik uygulamak için bağlayıcılar oluşturur. Bağlayıcılar aktarım katmanı güvenliği (TLS) aracılığıyla şifrelemeyi zorunlu kılmanın yanı sıra iş ortaklarınızın e-posta gönderdiği etki alanı adlarında veya IP adresi aralıklarında kısıtlamalara izin verir. |  <ul><li> [Exchange Online, e-posta bağlantılarının güvenliğini sağlamak için TLS'yi nasıl kullanır?](../compliance/exchange-online-uses-tls-to-secure-email-connections.md) </li><li> [Bağlayıcıları kullanarak posta akışını yapılandırma](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) </li><li> [Uzak etki alanları](/exchange/mail-flow-best-practices/remote-domains/remote-domains) </li><li> [İş ortağı kuruluşuyla güvenli posta akışı için bağlayıcı ayarlama](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner) </li><li> [Posta akışı en iyi yöntemleri (genel bakış)](/exchange/mail-flow-best-practices/mail-flow-best-practices) </li></ul> |

## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>çevrimiçi ve OneDrive İş işbirliği seçeneklerini SharePoint

| Hedefleri paylaşma | Yönetim eylemi | Nasıl yapılır bilgileri |
|:-----|:-----|:-----|
|Siteleri ve belgeleri dış kullanıcılarla paylaşma | Yöneticiler, kimliği doğrulanmış Microsoft hesabı, kimliği doğrulanmış iş veya okul hesabı ya da konuk hesapları için kiracı veya site koleksiyonu düzeyinde paylaşımı yapılandırıyor |  <ul><li> [SharePoint Online ortamınız için dış paylaşımı yönetme](https://support.office.com/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) </li><li> [etki alanına göre SharePoint ve OneDrive içeriğinin paylaşımını kısıtlama](/sharepoint/restricted-domains-sharing) </li><li> [SharePoint Online'ı işletmeler arası (B2B) bir extranet çözümü olarak kullanma](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) </li></ul> |
|Son kullanıcılar için dış paylaşımı izleme ve denetleme | OneDrive İş dosya sahipleri ve SharePoint Çevrimiçi son kullanıcılar site ve belge paylaşımını yapılandırıp paylaşımı izlemek için bildirimler oluşturur |  <ul><li> [OneDrive İş için dış paylaşım bildirimlerini yapılandırma](https://support.office.com/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) </li><li> [SharePoint dosya veya klasörleri paylaşma](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) </li></ul> |

## <a name="skype-for-business-collaboration-options"></a>İşbirliği seçeneklerini Skype Kurumsal

| Paylaşım hedefi | Yönetim eylemi | Nasıl yapılır bilgileri |
|:-----|:-----|:-----|
|Skype Kurumsal Online - Diğer Skype Kurumsal kullanıcılarla anlık ileti, aramalar ve iletişim durumu | Yöneticiler, Skype Kurumsal Çevrimiçi kullanıcılarının anlık ileti göndermesini, sesli/görüntülü arama yapmasını ve başka bir Microsoft 365 kiracıdaki kullanıcılarla iletişim durumunu görmesini sağlayabilir. | [Kullanıcıların kuruluş dışındaki Skype Kurumsal kullanıcılarıyla bağlantı kurmasına izin verme](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94)|
|Skype Kurumsal Online - Skype (tüketici) kullanıcılarla anlık ileti, aramalar ve iletişim durumu | Yöneticiler, Skype Kurumsal Çevrimiçi kullanıcılarının anlık ileti göndermesini, arama yapmasını ve Skype (tüketici) kullanıcılarla iletişim durumunu görmesini sağlayabilir. | [kullanıcıların Skype kişi eklemesine izin Skype Kurumsal](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460)|

## <a name="azure-ad-b2b-collaboration-options"></a>Azure AD B2B İşbirliği seçenekleri

| Paylaşım hedefi | Yönetim eylemi | Nasıl yapılır bilgileri |
|:-----|:-----|:-----|
|Azure AD B2B işbirliği - Bir kuruluşun dizinindeki bir gruba dış kullanıcılar ekleyerek içerik paylaşımı | Bir Microsoft 365 kiracısı için **Azure AD DC yöneticisi**, **Güvenlik Yöneticisi**, **Kullanıcı Yöneticisi**, **Bulut Uygulaması Yöneticisi** veya **Genel yönetici**, başka bir Microsoft 365 kiracıdaki kişileri dizinlerine katılmaya davet edebilir, bu dış kullanıcıları bir gruba ekleyebilir ve grubun SharePoint siteleri ve kitaplıkları gibi içeriğe erişim izni verebilir. |  <ul><li> [Azure AD B2B işbirliği önizlemesi nedir?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) </li><li> [Azure AD B2B: Yeni güncelleştirmeler, işletmeler arası işbirliği yapmayı kolaylaştırır](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) </li><li> [Dış paylaşım ve Azure Active Directory B2B işbirliği](/azure/active-directory/active-directory-b2b-o365-external-user) </li><li> [B2B işbirliği API'si ve özelleştirmesi Azure Active Directory](/azure/active-directory/active-directory-b2b-api) </li><li> [Azure AD ve Kimlik Gösterisi: Azure AD B2B İşbirliği (İşletmeden İşletmeye)](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) </li></ul> |

## <a name="microsoft-365-collaboration-options"></a>Microsoft 365 işbirliği seçenekleri

| Paylaşım hedefi | Yönetim eylemi | Nasıl yapılır bilgileri |
|:-----|:-----|:-----|
|Microsoft 365 Grupları - E-posta, takvim, OneNote ve paylaşılan dosyalar merkezi bir yerde | Gruplar Business Essentials, Business Premium, Education ve Enterprise E1, E3 ve E5 planlarında desteklenir. Bir Microsoft 365 kiracıdaki kişiler grup oluşturabilir ve başka bir Microsoft 365 kiracıdaki kişileri konuk kullanıcı olarak davet edebilir. Dynamics CRM için de geçerlidir. |  <ul><li> [Microsoft 365 grupları hakkında bilgi edinin](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) </li><li> [Microsoft 365 Grupları'de konuk erişimi](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) </li><li> [Microsoft 365 Grupları dağıtma](/previous-versions/dynamicscrm-2016/administering-dynamics-365/dn896591(v=crm.8)) </li></ul> |

## <a name="yammer-collaboration-options"></a>İşbirliği seçeneklerini Yammer

| Paylaşım hedefi | Yönetim eylemi | Nasıl yapılır bilgileri |
|:-----|:-----|:-----|
|Yammer - Kurumsal bir sosyal ortam aracılığıyla işbirliği | Dış grup oluşturma özelliği bir Yammer yöneticisi tarafından devre dışı bırakılmadığı sürece, kullanıcılar konuşmalar, gönderileri beğenme ve takip etme, dosya paylaşma ve çevrimiçi sohbet yoluyla Yammer işbirliği yapmak için dış gruplar oluşturabilir. | [Yammer'da dış grupları oluşturma ve yönetme](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a)|

## <a name="teams-collaboration-options"></a>Teams işbirliği seçenekleri

|Paylaşım hedefi|Yönetim eylemi|Nasıl yapılır bilgileri|
|:-----|:-----|:-----|
|Kuruluş dışındaki kullanıcılarla Teams işbirliği yapma | Davet eden Microsoft 365 kiracısının **Kullanıcı Yöneticisi** veya **Genel yöneticisinin** Teams'da dış işbirliğini etkinleştirmesi gerekir. Genel yöneticiler ve ekip sahipleri artık e-posta adresi olan herkesi Teams işbirliğine davet edebilecek.  <br/> Yöneticiler ayrıca kiracılarında zaten mevcut olan Konukları yönetebilir ve düzenleyebilir. |  <ul><li> [Konuk Erişimini Yetkilendirme](/microsoftteams/teams-dependencies) </li><li> [Teams'de Konuk Erişimini Açma veya Kapatma](/microsoftteams/set-up-guests) </li><li> [Konuk Erişimini denetlemek için PowerShell kullanma](/microsoftteams/guest-access-powershell) </li><li> [Konuk Erişimi Denetim Listesi](/microsoftteams/guest-access-checklist) </li><li> [Konuk Kullanıcıları Görüntüle](/microsoftteams/view-guests) </li><li> [Konuk kullanıcı bilgilerini düzenleme](/microsoftteams/edit-guests-information) </li></ul> |
|Ekip sahipleri, konukların ekiplerinde nasıl işbirliği yaptığını davet edebilir ve yönetebilir.  |Ekip sahipleri, konukların ekiplerinde neler yapabilecekleri konusunda ek denetimlere sahiptir. |  <ul><li> [Konuk Ekle](https://support.office.com/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) </li><li> [Ekibİye konuk ekleme](/microsoftteams/add-guests) </li><li> [Teams'de Konuk Erişimini Yönetme](/microsoftteams/manage-guests) </li><li> [Ekipte veya Kanalda kimlerin olduğunu görme](https://support.office.com/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) </li></ul> |
|Diğer kiracılardan gelen konuklar içeriği Teams görüntüleyebilir ve diğer üyelerle işbirliği yapabilir | Hiçbiri. | [Konuk erişim deneyimi](/microsoftteams/guest-experience)|

## <a name="power-bi-collaboration-options"></a>Power BI işbirliği seçenekleri

| Paylaşım hedefi | Yönetim eylemi | Nasıl yapılır bilgileri |
|:-----|:-----|:-----|
|Power BI, dış konuk kullanıcıların kendilerine bağlantılar aracılığıyla paylaşılan içeriği kullanmasına olanak tanır. Bu, kuruluştaki kullanıcıların içeriği kuruluşlar arasında güvenli bir şekilde dağıtmasını sağlar.<br/> | Power BI Yöneticisi, kullanıcıların dış kullanıcıları kuruluş içindeki içeriği görüntülemeye davet edip edemeyeceğini denetleyebilir.| [Azure AD B2B ile Power BI içeriği dış konuk kullanıcılara dağıtma](/power-bi/service-admin-azure-ad-b2b) |

## <a name="points-to-be-aware-of-about-microsoft-365-inter-tenant-collaboration"></a>Kiracılar arası Microsoft 365 işbirliği hakkında dikkat edilmesi gereken noktalar

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>Kullanıcı hesaplarının, lisansların, aboneliklerin ve depolamanın paylaşımı

Her kuruluş kendi kullanıcı hesaplarını, kimliklerini, güvenlik gruplarını, aboneliklerini, lisanslarını ve depolama alanını korur. İnsanlar, şirket varlıklarının denetimini korurken gerekli bilgilere erişim sağlamak için Microsoft 365'daki işbirliği özelliklerini paylaşım ilkeleri ve güvenlik ayarlarıyla birlikte kullanır.

- **Kullanıcı hesapları:** Şirket içi Active Directory Etki Alanı Hizmetleri'ndeki kiracılar veya bölümler arasında hesaplar paylaşılamaz veya çoğaltılamaz.

- **Lisans abonelikleri&amp;:** Microsoft 365 lisans planlarındaki lisanslar (SKU'lar veya Microsoft 365 planları olarak da adlandırılır) kullanıcılara bu planlar için tanımlanan Microsoft 365 hizmetlerine erişim sağlar.

- **Depolama:** Microsoft 365 lisans planlarında, SharePoint Online için yazılım sınırları ve sınırları posta kutusu depolama sınırlarından ayrı olarak yönetilir. Posta kutusu depolama sınırları Exchange Online kullanılarak ayarlanır ve yönetilir. Her iki senaryoda da depolama kiracılar arasında paylaşılamaz.

### <a name="can-we-share-domain-namespaces-across-microsoft-365-tenants"></a>Etki alanı ad alanlarını Microsoft 365 kiracılar arasında paylaşabilir miyiz?

Hayır. fabrikam.com veya tailspintoys.com gibi kuruluş etki alanı adları yalnızca tek bir Microsoft 365 kiracıyla ilişkilendirilebilir ve kullanılabilir. Her kiracının kendi ad alanı olmalıdır. UPN, SMTP ve SIP ad alanları kiracılar arasında paylaşılamaz.

### <a name="what-about-hybrid-components-and-microsoft-365-inter-tenant-collaboration"></a>Karma bileşenler ve Microsoft 365 kiracılar arası işbirliği ne olacak?

bir Exchange kuruluşu ve Azure AD Bağlan gibi şirket içi karma bileşenler birden çok kiracıya bölünemez.
