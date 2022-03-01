---
title: Ayarlar Grupları ile Microsoft 365 arasındaki etkileşimleri SharePoint
ms.reviewer: mmclean
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
description: Gruplar ve Grup grupları arasındaki Microsoft 365 etkileşimleri hakkında bilgi SharePoint
ms.openlocfilehash: 76f3772685dbf67e61d68a47373f514ab2dabfbc
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2021
ms.locfileid: "63005419"
---
# <a name="settings-interactions-between-microsoft-365-groups-and-sharepoint"></a>Ayarlar Grupları ile Microsoft 365 arasındaki etkileşimleri SharePoint

Grup Gruplarında Microsoft 365 ayarları SharePoint, Microsoft 365 paylaşma ve grup ve ekip sitesi oluşturmayla ilgili ayarlar birbiriyle çakışır. Bu makalede, bu etkileşimlerin açıklamaları ve bu ayarlarla nasıl çalışıla ilgili en iyi yöntemler yer almaktadır.

![Venn diyagramında SharePoint, Yammer özellikleri vardır.](../media/groups-sharepoint-venn.png)

## <a name="the-effects-of-sharepoint-settings-on-microsoft-365-groups"></a>Gruplarda SharePoint ayarlarının Microsoft 365.

|SharePoint ayarı|Açıklama|Grupların Microsoft 365 efekti|Öneri|
|:-----------------|:----------|:-----------------------------|:-------------|
|Kuruluş ve site için dış paylaşım|Sitelerin, dosyaların ve klasörlerin kuruluş dışındaki kişilerle paylaş verip paylaşılanamay olacağını belirler.|Grup SharePoint ayarları eşleşmezse, gruptaki konukların siteye erişimi engellenmiş olabilir veya grupta değil de, sitede dış erişim olabilir.|Paylaşım ayarlarını değiştirirken, hem Grup ayarlarını hem de SharePoint ekip siteleri için site ayarlarını kontrol edin.<br><br>Bkz [. Sitede konuklarla işbirliği yapma](./collaborate-in-site.md).|
|Etki alanı izin verme/engelleme|Belirtilen etki alanlarıyla içeriğin paylaşılmasını izin verir veya önler.|Gruplar izin listeleri veya SharePoint tanımaz. E-posta izin verilmeyen etki SharePoint kullanıcılar, grup aracılığıyla SharePoint erişim elde edeylem.|Azure AD için etki alanı izinlistelerini veya engellemelerini yönetin ve SharePoint birlikte yönetin. Etki alanlarına izin verme ve engelleme işlemleri için kuruluş genelinde bir yönetim süreci oluşturun.<br><br>Etki [SharePoint ve](/sharepoint/restricted-domains-sharing) [Azure AD etki alanı ayarlarını değiştirme](/azure/active-directory/b2b/allow-deny-list)|
|Yalnızca belirli güvenlik gruplarında yer alan kullanıcıların dışarıdan paylaşımda  olmasına izin verme|Siteleri, klasörleri ve dosyaları dışarıdan paylaşan güvenlik gruplarını belirtir.|Bu ayar, grup sahiplerinin grupları harici olarak paylaşmalarını etkilemez. Grup konukları, ilişkili sitenin SharePoint erişim iznine sahip olabilir.||
|SharePoint paylaşımı ayarlarını değiştirme|Siteyi grup üyeliğinin dışında doğrudan kimlerin paylaştıranı belirler. Bu, grup veya site sahibi tarafından yapılandırılır.|Bu ayar grubu doğrudan etkilemez, ancak kullanıcıların bir siteye eklenmelerine ve diğer grup kaynaklarına erişimleri izin vermez|Sitenin paylaşımını doğrudan sınırlamak ve grup aracılığıyla site erişimini yönetmek için bu ayarı kullanmayı düşünebilirsiniz.|
|Kullanıcıların ilk sayfadan ve son SharePoint site oluşturmasına izin OneDrive|Kullanıcıların yeni site oluştura olup SharePoint belirtir.|Bu ayar kapalı durumda olursa, kullanıcılar yine de grup oluşturarak grup bağlantılı ekip siteleri oluşturabilir.||

## <a name="the-effects-of-microsoft-365-groups-setting-on-sharepoint"></a>Çalışma Microsoft 365 grupları ayarının SharePoint

|Microsoft 365 grupları ayarını ayarlama|Açıklama|Efektin SharePoint|Öneri|
|:---------------------------|:----------|:-------------------|:-------------|
|Adlandırma ilkeleri|Grup adı öneklerini ve soneklerini ve grup oluşturma için engellenen sözcükleri belirtir|İlkeler, grup bağlantılı ekip siteleri oluşturan kullanıcılar için zorunludur ancak diğer şablonlarla iletişim siteleri veya siteler oluşturmaz.|Gerekirse iletişim siteleri için ayrı adlandırma kılavuzu oluşturun.|
|Grup konuk erişimi|Kuruluş dışındaki kişilerin gruplara eklen olup olacağını belirtir.|Grup SharePoint ayarları eşleşmezse, gruptaki konukların siteye erişimi engellenmiş olabilir veya grupta değil de, sitede dış erişim olabilir.|Paylaşım ayarlarını değiştirirken, hem Grup ayarlarını hem de SharePoint ekip siteleri için site ayarlarını kontrol edin.<br><br>Bkz [. Sitede konuklarla işbirliği yapma](./collaborate-in-site.md)|
|Güvenlik grubuna göre grup oluşturma|Gruplar yalnızca belirli bir güvenlik grubunun üyeleri tarafından oluşturulabilir.|Güvenlik grubunun üyesi olmayan kullanıcılar grup bağlantılı bir ekip sitesi oluşturabilecektir.|Grup isteğinde bulunan işlemde site talepe ilişkin yönergeler olduğundan emin olun.|
|Grup süre sonu ilkesi|Etkin olarak kullanılmadan grupların otomatik olarak silinecek olduğu bir zaman dönemini belirtir.|Grup silindiğinde, ilişkili SharePoint site de silinir. Bekletme ilkeleri tarafından korunan içerikler korunur.|Kullanılmayan grup ve sitelerden kaçınmak için süre sonu ilkelerini kullanın.|

## <a name="related-topics"></a>İlgili konular

[İşbirliği yönetim planlaması önerileri](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[İşbirliği yönetim planınızı oluşturma](collaboration-governance-first.md)

[Kuruluş dışındaki çalışanlarla işbirliği](./collaborate-with-people-outside-your-organization.md)

[Web sitesinde site SharePoint](/sharepoint/manage-site-creation)