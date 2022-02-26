---
title: Microsoft 365 kiracılar arası işbirliği
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Kiracılar Microsoft 365 kuruluşlar arasında işbirliğinin nasıl çalıştığını ve farklı kuruluşların güvenli bir şekilde birlikte çalışmasına olanak sağlamayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 9cb91b6bcaac212eeaf0ef4051f466751d8dbbd9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973569"
---
# <a name="microsoft-365-inter-tenant-collaboration"></a>Microsoft 365 kiracılar arası işbirliği

Fabrikam ve Contoso adlı iki kuruluşun, işletme kiracısı Microsoft 365 olduğunu ve bazıları sınırlı bir süre devam eden, bazıları ise devam eden çeşitli projelerde birlikte çalışmak olduğunu varsayalım. Fabrikam ve Contoso, kişi ve ekiplerinin farklı kiracıları üzerinde güvenli bir şekilde daha etkili Microsoft 365 bir şekilde işbirliği yapmalarını nasıl sağlar? Microsoft 365(Azure AD) Azure Active Directory B2B işbirliğiyle birlikte çeşitli seçenekler sağlar. Bu makalede, Fabrikam'ın ve Contoso'nın dikkate alıy etkide bulunayy adlı birkaç önemli senaryo açıklanmıştır.

Microsoft 365 kiracılar arası işbirliği seçenekleri arasında dosyalar ve konuşmalar için merkezi bir konum kullanma, takvimleri paylaşma, iletişim için IM, sesli/görüntülü aramalar kullanma ve kaynaklarla uygulamalara erişimi güvenlik altına alma vardır. Çözümleri seçmek ve daha fazla bilgi edinmek için aşağıdaki tabloları kullanın.

## <a name="exchange-online-collaboration-options"></a>Exchange Online işbirliği seçenekleri

| Paylaşım hedefi | Yönetim eylemi | Nasıl bilgi |
|:-----|:-----|:-----|
|Başka bir kuruluşla takvim Microsoft 365 paylaşma |Yöneticiler, Exchange Online'te işletmelerle işbirliği yapma ve kullanıcıların zamanlamaları (serbest/meşgul bilgileri) başkalarıyla paylaşmasına olanak vermek için Exchange Online'de takvim erişimi için farklı düzeyler ayarlamalarını sağlar. | <ul><li>[Paylaşım](/exchange/sharing/sharing) </li><li> [Kuruluş ilişkileri](/exchange/sharing/organization-relationships/organization-relationships) </li><li> [Kuruluş ilişkisi oluşturma](/exchange/sharing/organization-relationships/create-an-organization-relationship) </li><li> [Kuruluş ilişkisini değiştirme](/exchange/sharing/organization-relationships/modify-an-organization-relationship) </li><li> [Kuruluş ilişkisini kaldırma](/exchange/sharing/organization-relationships/remove-an-organization-relationship) </li><li> [Dış kullanıcılarla takvimleri paylaşma](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) </li></ul> |
|Kullanıcıların takvimlerini kuruluş dışındaki kullanıcılarla nasıl paylaştır olduğunu denetleme | Yöneticiler, kullanıcıların posta kutularına kimlerle paylaş uygulanabileceklerini ve verilen erişim düzeyini kontrol etmek için bu posta kutularına paylaşım ilkeleri uygulama |  <ul><li> [Paylaşım ilkeleri](/exchange/sharing/sharing-policies/sharing-policies) </li><li> [Paylaşım ilkesi oluşturma](/exchange/sharing/sharing-policies/create-a-sharing-policy) </li><li> [Posta kutularına paylaşım ilkesi uygulama](/exchange/sharing/sharing-policies/apply-a-sharing-policy) </li><li> [Paylaşım ilkesi değiştirme, devre dışı bırakma veya kaldırma](/exchange/sharing/sharing-policies/modify-a-sharing-policy) </li></ul> |
|İş ortağı kuruluşlarla güvenli e-posta kanalları yapılandırma ve posta akışını denetleme | Yöneticiler, iş ortağı bir kuruluşla veya servis sağlayıcıyla yapılan posta alışverişlerine güvenlik uygulamak için bağlayıcılar oluşturabilir. Bağlayıcılar aktarım katmanı güvenliği (TLS) üzerinden şifrelemeyi zorunlu olduğu gibi, iş ortaklarının e-posta gönderirken kullanılan etki alanı adları veya IP adresi aralıkları üzerinde kısıtlamalara da olanak sağlar. |  <ul><li> [E-Exchange Online bağlantılarının güvenliğini sağlamak için TLS'yi nasıl kullanır?](../compliance/exchange-online-uses-tls-to-secure-email-connections.md) </li><li> [Bağlayıcıları kullanarak posta akışını yapılandırma](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) </li><li> [Uzak etki alanları](/exchange/mail-flow-best-practices/remote-domains/remote-domains) </li><li> [İş ortağı kuruluşla güvenli posta akışı için bağlayıcıyı ayarlama](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner) </li><li> [Posta akışıyla ilgili en iyi yöntemler (genel bakış)](/exchange/mail-flow-best-practices/mail-flow-best-practices) </li></ul> |

## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>SharePoint Online ve OneDrive İş işbirliği seçeneklerini ayarlama

| Paylaşım hedefleri | Yönetim eylemi | Nasıl bilgi |
|:-----|:-----|:-----|
|Dış kullanıcılarla siteleri ve belgeleri paylaşma | Yöneticiler, kimliği doğrulanmış Microsoft hesabı, kimliği doğrulanmış iş veya okul hesabı veya konuk hesapları için kiracı veya site koleksiyonu düzeyinde paylaşımı yapılandırıyor |  <ul><li> [SharePoint Online ortamınız için dış paylaşımı yönetme](https://support.office.com/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) </li><li> [Etki alanına göre SharePoint ve OneDrive paylaşımını kısıtlama](/sharepoint/restricted-domains-sharing) </li><li> [İşletmeler SharePoint (B2B) extranet çözümü olarak SharePoint Online'i kullanma](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) </li></ul> |
|Son kullanıcılar için dış paylaşımı izleme ve denetleme | OneDrive İş sahiplerini ve SharePoint Online son kullanıcılarının site ve belge paylaşımını yapılandırmalarını ve paylaşımı izlemek için bildirimler oluşturmalarını sağlar |  <ul><li> [Dış paylaşım için bildirimleri yapılandırma OneDrive İş](https://support.office.com/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) </li><li> [Dosya SharePoint klasör paylaşma](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) </li></ul> |

## <a name="skype-for-business-collaboration-options"></a>Skype Kurumsal işbirliği seçeneklerini ayarlama

| Paylaşım hedefi | Yönetim eylemi | Nasıl bilgi |
|:-----|:-----|:-----|
|Skype Kurumsal Online - Diğer kullanıcılarla IM, aramalar ve Skype Kurumsal iletişim durumu | Yöneticiler kendi Skype Kurumsal Online kullanıcılarının başka bir kiracıda IM çağrısı yapmalarını, sesli/görüntülü aramalar yapmalarını ve bu kullanıcılarla iletişim Microsoft 365 görebilirler. | [Kullanıcıların kuruluş dışındaki Skype Kurumsal kullanıcılarıyla bağlantı kurmasına izin verme](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94)|
|Skype Kurumsal Online - Diğer kullanıcılarla (tüketici) IM Skype ve iletişim durumu | Yöneticiler kendi Skype Kurumsal Online kullanıcılarının kendi kullanıcılarıyla IM (tüketici) kullanıcılarıyla IM Skype ve iletişim durumlarını görmelerini etkinleştirebilirsiniz. | [Kullanıcıların Skype Kurumsal kişi eklemesine Skype verme](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460)|

## <a name="azure-ad-b2b-collaboration-options"></a>Azure AD B2B İşbirliği seçenekleri

| Paylaşım hedefi | Yönetim eylemi | Nasıl bilgi |
|:-----|:-----|:-----|
|Azure AD B2B işbirliği - Kuruluş dizininde bir gruba dış kullanıcılar ekleyerek içerik paylaşımı | **Bir Azure AD DC** **yöneticisi, Güvenlik** **Yöneticisi, Kullanıcı** **Yöneticisi, Bulut** Uygulama Yöneticisi veya bir  Microsoft 365 kiracısı için Genel yönetici başka bir Microsoft 365 kiracısına verilen kişileri kendi dizinine katılmaya davet ekleyebilir, söz konusu dış kullanıcıları bir gruba ekleyebilir ve grup için SharePoint siteleri ve kitaplıkları gibi içeriğe erişim izni veebilir. |  <ul><li> [Azure AD B2B işbirliği önizlemesi nedir?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) </li><li> [Azure AD B2B: Yeni güncelleştirmeler işletmeler arası iş bir arası işi kolaylaştırır](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) </li><li> [Dış paylaşım ve Azure Active Directory B2B işbirliğini destekle](/azure/active-directory/active-directory-b2b-o365-external-user) </li><li> [Azure Active Directory B2B işbirliği API'si ve özelleştirmesi](/azure/active-directory/active-directory-b2b-api) </li><li> [Azure AD ve Kimlik Gösterisi: Azure AD B2B İşbirliği (İşletmeler Için)](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) </li></ul> |

## <a name="microsoft-365-collaboration-options"></a>Microsoft 365 işbirliği seçenekleri

| Paylaşım hedefi | Yönetim eylemi | Nasıl bilgi |
|:-----|:-----|:-----|
|Microsoft 365- E-posta, takvim, OneNote ve paylaşılan dosyalar merkezi bir yerde | Gruplar İş Temel İş, İş Premium, Eğitim ve E1, E3 ve E5 planlarında Enterprise desteklenen gruplardır. Bir kiracının Microsoft 365 grup oluşturabilir ve başka bir kiracıya konuk kullanıcı Microsoft 365 kişileri davet etme. Bu, Dynamics CRM için de geçerlidir. |  <ul><li> [Grupların nasıl Microsoft 365 öğrenin](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) </li><li> [Microsoft 365 Gruplarında konuk erişimi](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) </li><li> [Gruplarda Microsoft 365 dağıtma](/previous-versions/dynamicscrm-2016/administering-dynamics-365/dn896591(v=crm.8)) </li></ul> |

## <a name="yammer-collaboration-options"></a>Yammer işbirliği seçeneklerini ayarlama

| Paylaşım hedefi | Yönetim eylemi | Nasıl bilgi |
|:-----|:-----|:-----|
|Yammer - Kurumsal sosyal medya üzerinden işbirliği | Yammer yöneticisi dış grup oluşturma özelliği devre dışı bırakılamadıkça, kullanıcılar Yammer'te konuşmalar, gönderileri takip etme ve takip etme, dosyaları paylaşma ve çevrimiçi sohbet etme özelliği aracılığıyla işbirliği yapmak için dış gruplar oluşturabilir. | [Yammer'da dış grupları oluşturma ve yönetme](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a)|

## <a name="teams-collaboration-options"></a>Teams işbirliği seçenekleri

|Paylaşım hedefi|Yönetim eylemi|Nasıl bilgi|
|:-----|:-----|:-----|
|Kuruluş dışından Teams kullanıcılarla işbirliği yapma | Davet **eden kullanıcı için** bir **Kullanıcı Yöneticisi** veya genel yönetici Microsoft 365 bu kiracıda dış işbirliğini etkinleştirmesi Teams. Genel yöneticiler ve ekip sahipleri artık e-posta adresi olan herkesi iş birliği için davet Teams.  <br/> Yöneticiler ayrıca kiracılarında mevcut olan Konukları yönetebilir ve düzenleyebilir. |  <ul><li> [Konuk Erişimine Yetki Ver](/microsoftteams/teams-dependencies) </li><li> [Konuk Erişimini Aç veya Kapat'Teams](/microsoftteams/set-up-guests) </li><li> [Konuk Erişimini kontrol etmek için PowerShell kullanma](/microsoftteams/guest-access-powershell) </li><li> [Konuk Erişimi Denetim Listesi](/microsoftteams/guest-access-checklist) </li><li> [Konuk Kullanıcıları Görüntüleme](/microsoftteams/view-guests) </li><li> [Konuk kullanıcı bilgilerini düzenleme](/microsoftteams/edit-guests-information) </li></ul> |
|Ekip sahipleri, konukların ekipleri içinde nasıl işbirliği yaptıklarına davet etmek ve yönetmek için davet veya daveti yönetebilir.  |Ekip sahiplerinin, konukların ekipleri içinde neler yaptıklarıyla ilgili ek denetimler vardır. |  <ul><li> [Konuk Ekleme](https://support.office.com/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) </li><li> [Ek ekiplere konuk ekleme](/microsoftteams/add-guests) </li><li> [Aynı Ağ Üzerinden Konuk Erişimini Teams](/microsoftteams/manage-guests) </li><li> [Bir Ekipte veya Kanalda kimlerin olduğunu görme](https://support.office.com/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) </li></ul> |
|Diğer kiracılardan gelen konuklar e-Teams içindekileri layabilir ve diğer üyelerle işbirliği | Yok. | [Konuk erişimi deneyimi](/microsoftteams/guest-experience)|

## <a name="power-bi-collaboration-options"></a>Power BI işbirliği seçeneklerini ayarlama

| Paylaşım hedefi | Yönetim eylemi | Nasıl bilgi |
|:-----|:-----|:-----|
|Power BI konuk kullanıcıların bağlantılarla onlara paylaşılan içeriği tüketmelerine olanak sağlar. Bu, kuruluşta yer alan kullanıcıların, içeriklerini kuruluşlar arasında güvenli bir şekilde dağıtmalarını sağlar.<br/> | Genel Power BI, kullanıcıların kuruluş içindeki içeriği görüntülemek için dış kullanıcıları davet edip ete bir denetimde olabilir.| [Dış Power BI Azure AD B2B ile dış konuk kullanıcılara diğer içerikleri dağıtma](/power-bi/service-admin-azure-ad-b2b) |

## <a name="points-to-be-aware-of-about-microsoft-365-inter-tenant-collaboration"></a>Kiracılar arası işbirliği hakkında Microsoft 365 noktaları

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>Kullanıcı hesaplarını, lisansları, abonelikleri ve depolama alanını paylaşma

Her kuruluş kendi kullanıcı hesaplarını, kimliklerini, güvenlik gruplarını, aboneliklerini, lisanslarını ve depolama alanını bakımını sağlar. Kişiler gerekli bilgilere erişim sağlarken şirket varlıklarının Microsoft 365 için paylaşım ilkeleri ve güvenlik ayarlarıyla birlikte şirket iş birliği özelliklerini kullanır.

- **Kullanıcı hesapları:** Hesaplar, şirket içi Active Directory Etki Alanı Hizmetleri'nin kiracıları veya bölümleri arasında paylaşılamaz veya çoğaltılamaz.

- **Lisanslar &amp; abonelikleri:** Microsoft 365'te, lisans planlarından (SKU'lar veya Microsoft 365 planları olarak da adlandırılan) gelen lisanslar, kullanıcılara bu planlar için tanımlanmış Microsoft 365 hizmetleri için erişim sağlar.

- **Depolama:** Microsoft 365 lisans planlarında, SharePoint Online için yazılım sınırları ve sınırlamaları posta kutusu depolama sınırlarından ayrı yönetilir. Posta kutusu depolama sınırları, posta kutusu kullanılarak ayarlanır ve Exchange Online. Her iki senaryoda da, depolama alanı kiracılar arasında paylaşılamaz.

### <a name="can-we-share-domain-namespaces-across-microsoft-365-tenants"></a>Etki alanı ad alanlarını bu kiracılar arasında Microsoft 365 paylaşabilir miyiz?

Hayır. Kuruluş etki alanı adları (fabrikam.com veya tailspintoys.com, tek bir kiracıyla ilişkilendiril kullanılabilir ve Microsoft 365 kullanılabilir. Her kiracının kendi ad alanı olması gerekir. UPN, SMTP ve SIP ad alanları kiracılar arasında paylaşılamaz.

### <a name="what-about-hybrid-components-and-microsoft-365-inter-tenant-collaboration"></a>Karma bileşenler ve kiracılar Microsoft 365 nasıl kullanılır?

Exchange kuruluşu ve Azure AD Bağlan gibi şirket içi karma bileşenleri, birden çok kiracıya bölünamaz.
