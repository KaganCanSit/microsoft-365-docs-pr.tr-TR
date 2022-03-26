---
title: Kuruluş dışındaki çalışanlarla işbirliği
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-securecollab
- m365solution-scenario
- m365initiative-externalcollab
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: Kuruluş dışından çalışanlarla Microsoft 365 için Teams, OneDrive ve SharePoint uygulamaları yapılandırmayı öğrenin.
ms.openlocfilehash: 65511cbafdc1f5a666c11e1bef7fefd6e6852ee3
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63712798"
---
# <a name="collaborating-with-people-outside-your-organization"></a>Kuruluş dışındaki çalışanlarla işbirliği

Dış paylaşım özellikleri Microsoft 365 iş ortakları, satıcılar, müşteriler ve dizinde hesabı olmadığı diğer kişiler ile işbirliği yapma fırsatı sunar. Ekiplerin, kanalların veya sitelerin tamamını, kuruluş dışındakilerle ya da yalnızca tek tek dosyaları paylaşabilirsiniz.

Kuruluş dışından çalışanlarla işbirliği yapmak şu önemli bileşenlerden oluşur:

- **Paylaşımı etkinleştirme** - Kuruluş için istediğiniz paylaşım düzeyine izin Azure Active Directory, Teams, Microsoft 365 Grupları ve SharePoint genelinde paylaşım denetimlerini yapılandırabilirsiniz.
- **Kuruluş ilişkilerini yapılandırma** - Paylaşılan kanalları kullanıyorsanız, işbirliği yapmak istediğiniz her kuruluşta B2B doğrudan bağlanma erişimine izin vermek için Azure Active Directory'de kiracılar arası erişim ayarlarını yapılandırmanız gerekir. (Bu kuruluşların kiracınız ile kuruluş ilişkilerini de yapılandırmaları gerekir.)
- **Ek güvenliği etkinleştirme** - Temel paylaşım özellikleri, kuruluş dışından kişilerin kimlik doğrulaması yapmalarını gerektirecek şekilde ya da yapılandırılana kadar, Microsoft 365 verilerinizi korumanıza ve dış paylaşım yaparken yönetim ilkelerinizi korumanıza yardımcı olacak birçok ek güvenlik ve uyumluluk özelliği sağlar.

Genel [işbirliği kılavuzunda dış Microsoft 365 bağlı Microsoft Teams bağlı Microsoft 365](/microsoft-365/solutions/setup-secure-collaboration-with-teams) güvenli işbirliğini ayarlama makalesini Microsoft 365 okuyun.

## <a name="enable-sharing"></a>Paylaşımı etkinleştir

Varsayılan olarak, konuk erişimini veya anonim erişimi kullanarak kuruluş dışındaki kullanıcılarla paylaşım özelliği etkinleştirilir, ancak paylaşılan kanalların Azure AD'de kuruluş ilişkileri yapılandırarak etkinleştirilmesi gerekir. Çoğu konuk paylaşımı senaryosu, başka yapılandırmaya gerek kalmadan çalışır. Kullanmakta olduğu senaryonun ayarlarını onaylamak veya yeni bir senaryoyu etkinleştirmek için aşağıdaki seçeneklerden birini belirleyin:

- [Belgeler üzerinde birlikte çalışma](collaborate-on-documents.md) - Dosyaların Microsoft 365 klasörler üzerinde kuruluş dışındaki kullanıcılarla (hem konuklar hem de kimliği doğrulanmamış kullanıcılar) paylaşıma ve işbirliğine izin verecek şekilde belgeleri nasıl yapılandırabilirsiniz?
- [Bir sitede işbirliği yapma](collaborate-in-site.md) - Bir siteyi konukla Microsoft 365 izin SharePoint yapılandırmayı öğrenin.
- [Ekip olarak işbirliği yapma](collaborate-as-team.md) - ekip içinde konuk Microsoft 365 işbirliğini etkinleştirmek için ekibi Teams.
- [Paylaşılan bir kanalda, kuruluşun dışındaki](/microsoft-365/solutions/collaborate-teams-direct-connect) kişiler ile işbirliği yapmak için kanalda dış katılımcılarla işbirliği yapın.

Konuk paylaşım ayarları hakkında ayrıntılı bilgi için Microsoft 365 bkz. [Microsoft 365 göz atabilirsiniz](microsoft-365-guest-settings.md).

## <a name="enable-additional-security"></a>Ek güvenliği etkinleştirme

Kuruluş dışındaki kişilerle paylaşımda kullanmak istediğiniz senaryoyu etkinleştirdikten sonra, içeriğinizi yanlışlıkla veya uygunsuz paylaşıma karşı korumaya yardımcı olacak ek korumalar kullanmayı düşünün.

- [Kimliği doğrulanmamış kullanıcılarla dosya ve klasör paylaşmak için en iyi yöntemler](best-practices-anonymous-sharing.md) - Kimliği doğrulanmamış kullanıcılarla paylaşım için en iyi yöntemler hakkında bilgi edinebilirsiniz.
- [Yanlışlıkla maruz kalma](share-limit-accidental-exposure.md) sayısını sınırla - Önemli içerikleri kuruluş dışındakilerle yanlışlıkla paylaşma riskini azaltmayı öğrenin.
- [Güvenli bir konuk paylaşım](create-secure-guest-sharing-environment.md) ortamı oluşturma - Microsoft 365 dışından çalışanlarla paylaşımın güvenli ve güvenli bir şekilde yapılırken, yönetim gereksinimlerinizi karşılamaya yardımcı olmak için Microsoft 365'de sağlanan araçlar hakkında bilgi edinebilirsiniz.

## <a name="collaborate-with-partner-companies"></a>İş ortağı şirketlerle işbirliği yapma

Başka bir kuruluştan konuk içeren büyük bir proje üzerinde çalışırken paylaşılan kanalları düşünün. Paylaşılan kanallar konuk hesaplarını kullanmamalarından dolayı, diğer kuruluşta yer alan kullanıcılar, kuruluşta ayrı olarak oturum açmak zorunda kalmadan paylaşılan kanala doğrudan erişim sağlar.

Konukların sıklıkla değişmektedir olduğu sürekli bir satıcı ilişkiniz varsa, konuk yönetimini basitleştirmek ve iş ortağı şirketinin bu sorumlulukta paylaşmasına izin vermek için Azure Active Directory'te yetkilendirme yönetimini kullanabilirsiniz. Ayrıntılı [bilgi için bkz. Yönetilen konuklarla B2B extranet](b2b-extranet.md) oluşturma.

## <a name="limit-sharing"></a>Paylaşımı sınırla

Bu konuda yer alan paylaşım özelliklerinden bazıları Microsoft 365 ilkeleriniz ile çakışıyorsa, paylaşımı sınırlama seçenekleri hakkında bilgi edinmek için [Microsoft 365'de](microsoft-365-limit-sharing.md) paylaşımı sınırlama.

## <a name="related-topics"></a>İlgili konular

[İş birliği içinde dosya işbirliğine Microsoft 365](/sharepoint/intro-to-file-collaboration)

[Dosya işbirliğini iş birliği SharePoint birlikte Microsoft 365](/sharepoint/deploy-file-collaboration)
