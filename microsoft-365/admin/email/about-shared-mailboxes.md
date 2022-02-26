---
title: Paylaşılan posta kutuları hakkında
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
description: Paylaşılan posta kutuları, aynı posta kutusuna birden çok kişinin erişmesi gereken durumlarda kullanılır. Paylaşılan posta kutusu oluşturmadan önce neleri bilmek zorunda olduğunu öğrenin.
ms.openlocfilehash: 2fbf07fbe71ccb42411f5808aa923d7179d2f13d
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "62973878"
---
# <a name="about-shared-mailboxes"></a>Paylaşılan posta kutuları hakkında

Paylaşılan posta kutuları, birden çok kişinin aynı posta kutusuna, örneğin şirket bilgileri veya e-posta adresi, alma masa veya birden fazla kişi tarafından paylaşılabilen başka bir işleve ulaşması gerektiğinde kullanılır.

Eğer yönetici kullanıcıya bunu yapma yetkisi verdiyse, grup posta kutusu izni olan kullanıcılar posta kutusu adına ya da posta kutusu gibi gönderim yapabilirler. Bu, kullanıcılar "Contoso Desteği" veya "Karşılama Masası Oluşturma" üzerinden e-posta gönderebildiklerinden, yardım ve destek posta kutuları için özellikle yararlıdır.

## <a name="before-you-begin"></a>Başlamadan önce

Paylaşılan [posta kutusunu oluşturmadan önce](create-a-shared-mailbox.md), şunları bilmek gerekir:

- **Lisanslar:** Paylaşılan posta kutunuz, siz lisans atamadan en çok 50 GB veri depolar. Bu alan dolduktan sonra daha fazla veri depolamak için posta kutusuna bir lisans atamanız gerekir. Paylaşılan posta kutusu lisanslama hakkında daha fazla ayrıntı için lütfen Posta Kutusu Exchange Online [bakın](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#StorageLimits). Paylaşılan bir posta kutusu depolama sınırına ulaştığında bir süre e-posta almaya devam edersiniz, ancak yeni e-posta gönderemezsiniz. Bu süre de sona erdiğinde e-posta alamazsınız. Posta kutusuna ileti gönderenler, iletinin teslim edilmediğine ilişkin bir bilgi alır.

- **Kullanıcı izinleri:** Kullanıcılara, paylaşılan posta kutusunu kullanma izinleri (üyelik) verebilirsiniz. Paylaşılan bir posta kutusunu yalnızca kuruluşunuzdaki kişiler kullanabilir.

- **Dış kullanıcılar:** İşletmenizin dışındaki kişilerin (Gmail hesabı olan kişiler gibi) paylaşılan posta kutunuza erişmesine izin verebilirsiniz. Bunu yapmak istediğiniz zaman, daha sonra oluşturmak için grup Outlook göz önünde bulundurarak. Daha fazla bilgi için [bkz. Yönetim Microsoft 365 Grup oluşturma](../create-groups/create-groups.md).

- **Outlook** ile kullanma: Paylaşılan posta kutularına erişmek için Web üzerinde Outlook'i tarayıcınızdan kullanmanın yanı sıra, iOS için Outlook uygulamasını veya Android için Outlook uygulamasını da kullanabilirsiniz. Daha fazla bilgi edinmek için bkz[. Mobil cihazlara paylaşılan Outlook ekleme](https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f). Bir diğer seçenek de paylaşılan posta kutunuz için bir grup oluşturmaktır. Daha fazla bilgi edinmek için bkz. [Grupları Karşılaştırma](../create-groups/compare-groups.md).

- **Şifreleme:** Paylaşılan posta kutusundan gönderilen e-postayı şifreleyesiniz. Bunun nedeni, paylaşılan posta kutusunun kendi güvenlik bağlamı (kullanıcı adı/parola) yoktur ve dolayısıyla bir anahtar atanamaz. Birden fazla kişi üye ise ve kendi anahtarları ile şifrelenmiş e-postalar gönderir/alırsa, e-postanın hangi ortak anahtarla şifrelenen ortak anahtara bağlı olarak diğer üyeler e-postayı okuyabilir ve diğerleri ise okumayabilirsiniz.

- **Posta kutusu dönüştürme:** Kullanıcı posta kutularını paylaşılan posta kutularına dönüştürebilirsiniz. Bkz [. Kullanıcı posta kutusunu paylaşılan posta kutusuna dönüştürme](convert-user-mailbox-to-shared-mailbox.md).

- **Yönetici rolleri:** Genel yönetici veya yönetici Exchange kullanıcılar paylaşılan posta kutuları oluşturabilir.

- **Abonelik gereksinimleri:** Paylaşılan posta kutusu oluşturmak için, e-posta (Microsoft 365 hizmeti) içeren bir iş planına abone Exchange Online gerekir. Bu İş için Microsoft 365 Uygulamaları e-postayı içermez. Microsoft 365 İş Standart e-posta içerir.

- **Oturum açma:** Paylaşılan posta kutusu, ilişkili kullanıcı hesabı tarafından doğrudan oturum açma amaçlı değildir. Paylaşılan posta kutusu hesabı için oturum açma her zaman engellenir ve engellenir.

- **Çok fazla kullanıcı var:** Paylaşılan posta kutusuna eş zamanlı olarak erişecek çok fazla belirlenen kullanıcı olduğunda (25'den fazla önerilmez), bu posta kutusuna ara zaman bağlanamıyorlar veya giden kutusunda yinelenen iletiler gibi tutarsızlıklar olabilir. Bu durumda, kullanıcı sayısını azaltmayı veya Kullanıcı grubu veya Ortak klasör gibi farklı bir iş Microsoft 365 kullanmayı düşünebilirsiniz.

- **İleti silme:** Ne yazık ki, paylaşılan bir posta kutusunda kişilerin iletileri silmeden bunu engelleyemeyebilirsiniz. Bunu tek yol, paylaşılan posta kutusu Microsoft 365 bir posta kutusu oluşturmaktır. E-posta Outlook paylaşılan posta kutusu gibi olur. bu iki grubun karşılaştırması için bkz. [Grupları karşılaştırma](../create-groups/compare-groups.md). Gruplar hakkında daha fazla bilgi edinmek için bkz. [Gruplar hakkında daha fazla bilgi.](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

- **Multi-Geo** Çok coğrafi bir ortamda, paylaşılan posta kutularının aynı kullanıcı posta kutusunun lisanslı olması gibi lisansları da olması gerekir. Coğrafi posta kutusu denetiminin destek olmadığını unutmayın. Örneğin, kullanıcıya farklı bir coğrafi konumdaki paylaşılan posta kutusuna erişim izinleri atanmışsa, o kullanıcı tarafından gerçekleştirilen posta kutusu eylemleri paylaşılan posta kutusunun posta kutusu denetim günlüğüne kaydedilmez. 


> [!NOTE]
> Paylaşılan posta kutusuna erişmek için, kullanıcının bir Exchange Online lisansı olması gerekir, ancak paylaşılan posta kutusu ayrı bir lisans gerektirmez. Her paylaşılan posta kutusunun buna karşılık gelen bir kullanıcı hesabı vardır. Paylaşılan posta kutusunu oluşturulduğunda nasıl parola sağlamanın istenmeyeceğini fark ettiniz mi? Bu hesabın bir parolası var, ancak sistem tarafından oluşturulmuş (bilinmiyor) bir hesap. Paylaşılan posta kutusunda oturum açmak için hesabı kullanmamanız gerekir. Lisans olmadan paylaşılan posta kutuları 50 GB ile sınırlıdır. Boyut sınırını 100 GB'a artırmak için paylaşılan posta kutusuna Plan 2 lisansı Exchange Online gerekir. Bir Exchange Online Eklenti lisansına sahip Exchange Online Arşivleme Plan 1 lisansı yalnızca arşiv posta kutusunun boyutunu artıracaktır. Bu ayrıca ek arşiv depolama kapasitesi için otomatik genişleyen arşivlemeyi etkinleştirmeniz için de olanak sağlar. Benzer şekilde, bir paylaşılan posta kutusunu mahkemeler için yerinde tutmak istemeniz gibi, paylaşılan posta kutusunun bir Exchange Online Plan 2 lisansına veya Exchange Online eklenti lisansına sahip Exchange Online Arşivleme Plan 1 lisansına sahip olması gerekir. Office 365 için Microsoft Defender, Advanced eDiscovery veya otomatik bekletme ilkeleri gibi gelişmiş özellikleri uygulamak için, paylaşılan posta kutusunun bu özellikler için lisanslı olması gerekir.

## <a name="related-content"></a>İlgili içerik

[Paylaşılan posta kutusu oluşturma](create-a-shared-mailbox.md) (makale)\
[Paylaşılan posta kutusunu yapılandırma](configure-a-shared-mailbox.md) (makale)\
[Kullanıcı posta kutusunu paylaşılan posta kutusuna dönüştürme](convert-user-mailbox-to-shared-mailbox.md) (makale)\
[Paylaşılan posta kutusundan lisans kaldırma](remove-license-from-shared-mailbox.md) (makale)\
[Paylaşılan posta kutularıyla ilgili sorunları çözme](resolve-issues-with-shared-mailboxes.md) (makale)
