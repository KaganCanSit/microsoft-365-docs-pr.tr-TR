---
title: Ayarlar Grupları, grupları Microsoft 365 ve grup Teams etkileşimlerini SharePoint
ms.reviewer: ''
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Grup, Grup ve Grup Microsoft 365 arasındaki Teams etkileşimleri SharePoint
ms.openlocfilehash: 64f00fcb5ace9e2f2f4a6630def6beb0a51d40bf
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2021
ms.locfileid: "63005417"
---
# <a name="settings-interactions-between-microsoft-365-groups-teams-and-sharepoint"></a>Ayarlar Grupları, grupları Microsoft 365 ve grup Teams etkileşimlerini SharePoint

Microsoft 365'da Microsoft 365 grupları, Microsoft Teams ve SharePoint için, özellikle paylaşım ve grup/ekip ve SharePoint oluşturma ile ilgili bazı ayarlar birbiriyle örtüşüyor. Bu makalede, bu etkileşimlerin açıklamaları ve bu ayarlarla nasıl çalışıla ilgili en iyi yöntemler yer almaktadır.

![Venn diyagramında SharePoint, Teams ve grup özellikleri vardır.](../media/teams-groups-sharepoint-venn.png)

## <a name="the-effects-of-sharepoint-settings-on-groups-and-teams"></a>Ekipler ve SharePoint ayarlarının etkileri

|SharePoint ayarı|Açıklama|Grup ve Microsoft 365 üzerinde Teams|Öneri|
|:-----------------|:----------|:---------------------------------------|:-------------|
|Kuruluş ve site için dış paylaşım|Sitelerin, dosyaların ve klasörlerin kuruluş dışındaki kişilerle paylaş verip paylaşılanamay olacağını belirler.|Yeni SharePoint, gruplar ve Teams ayarları eşleşmezse, ekipten konukların siteye erişimi engellenmiş olabilir veya beklenmedik dış erişim olabilir.|Paylaşım ayarlarını değiştirirken Grup ayarlarını, grup Teams ve grup bağlantılı ekip SharePoint site ayarlarını değiştirin.<br><br> Bkz [. Ekipte konuklarla işbirliği yapma](./collaborate-as-team.md)|
|Etki alanı izin verme/engelleme|Belirtilen etki alanlarıyla içeriğin paylaşılmasını izin verir veya önler.|Gruplar ve Teams izin listesine SharePoint listeleri tanımaz. E-postada izin verilmeyen etki SharePoint, ekip aracılığıyla SharePoint sitelere veya içeriğe erişim elde edemleri.|Azure AD için etki alanı izinlistelerini veya engellemelerini yönetin ve SharePoint birlikte yönetin. Etki alanlarına izin verme ve engelleme işlemleri için kuruluş genelinde bir yönetim süreci oluşturun.<br><br>Etki [SharePoint ve](/sharepoint/restricted-domains-sharing) [Azure AD etki alanı ayarlarını değiştirme](/azure/active-directory/b2b/allow-deny-list)|
|Yalnızca belirli güvenlik gruplarında yer alan kullanıcıların dışarıdan paylaşımda  olmasına izin verme|Dış site, klasör ve SharePoint paylaşabilirsiniz güvenlik gruplarını belirtir.|Bu ayar, ekip sahiplerinin ekipleri dışarıdan paylaşmasını engellemez. Ekip konukları, ilişkili ekip sitesine SharePoint sahip olabilir.||
|SharePoint paylaşımı ayarlarını değiştirme|Siteyi kimlerin doğrudan ekip üyeliğinin dışında paylaşa bir ortak olduğunu belirler. Bu, ekip veya site sahibi tarafından yapılandırılır.|Bu ayar ekibi doğrudan etkilemez, ancak kullanıcıların bir siteye eklenmelerine ve ekibin kendisine veya diğer ekip kaynaklarına erişim Teams sağlar|Sitenin doğrudan paylaşımını sınırlamak ve ekip aracılığıyla site erişimini yönetmek için bu ayarı kullanmayı göz önünde bulundurabilirsiniz.|
|Kullanıcıların ilk sayfadan ve son SharePoint site oluşturmasına izin OneDrive|Kullanıcıların yeni site oluştura olup SharePoint belirtir.|Bu ayar kapalı durumda olursa, kullanıcılar yine de ekip oluşturarak grup bağlantılı ekip siteleri oluşturabilir.||

## <a name="the-effects-of-groups-settings-on-teams"></a>Ekipler üzerinde grup ayarlarının etkileri

|Microsoft 365 grupları ayarını ayarlama|Açıklama|Efekt Teams|Öneri|
|:---------------------------|:----------|:--------------|:-------------|
|Adlandırma ilkeleri|Grup adı öneklerini ve soneklerini ve grup oluşturma için engellenen sözcükleri belirtir|İlkeler, ekip oluşturan kullanıcılar için zorunlu kılındı.||
|Grup konuk erişimi|Kuruluş dışındaki kişilerin gruplara eklen olup olacağını belirtir.|Grup veya konuk Teams ayarları kapalı olursa, ekip konuklarla paylaşılamaz.|Konuk paylaşımı ayarlarını değiştirirken ekiple ilişkilendirilmiş Teams, Gruplar ve SharePoint sitenin ayarlarını kontrol edin.<br><br> Bkz [. Ekipte konuklarla işbirliği yapma](./collaborate-as-team.md)|
|Güvenlik grubuna göre grup oluşturma|Gruplar yalnızca belirli bir güvenlik grubunun üyeleri tarafından oluşturulabilir.|Güvenlik grubunun üyesi olan kullanıcılar ekip oluşturabilecektir.|Grup isteğinde bulunan sürecinizin, ekip veya ekip sitesi talep SharePoint emin olun.|
|Grup süre sonu ilkesi|Etkin olarak kullanılmadan grupların otomatik olarak silinecek olduğu bir zaman dönemini belirtir.|Grup silindiğinde, ekip ve ilişkili SharePoint site de silinir. Bekletme ilkeleri tarafından korunan içerikler korunur.|Kullanılmayan ekip, grup ve sitelerden kaçınmak için süre sonu ilkelerini kullanın.|

## <a name="related-topics"></a>İlgili konular

[İşbirliği yönetim planlaması önerileri](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[İşbirliği yönetim planınızı oluşturma](collaboration-governance-first.md)

[Kuruluş dışındaki çalışanlarla işbirliği](./collaborate-with-people-outside-your-organization.md)

[Web sitesinde site SharePoint](/sharepoint/manage-site-creation)