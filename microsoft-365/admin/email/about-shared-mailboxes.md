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
description: Paylaşılan posta kutuları, birden çok kişinin aynı posta kutusuna erişmesi gerektiğinde kullanılır. Paylaşılan posta kutusu oluşturmadan önce bilmeniz gerekenleri öğrenin.
ms.openlocfilehash: a384440b64b84618831b8065bd40d89200ea47d0
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971549"
---
# <a name="about-shared-mailboxes"></a>Paylaşılan posta kutuları hakkında

Paylaşılan posta kutuları, birden çok kişinin aynı posta kutusuna, örneğin şirket bilgileri veya e-posta adresi, alma masa veya birden fazla kişi tarafından paylaşılabilen başka bir işleve ulaşması gerektiğinde kullanılır.

Eğer yönetici kullanıcıya bunu yapma yetkisi verdiyse, grup posta kutusu izni olan kullanıcılar posta kutusu adına ya da posta kutusu gibi gönderim yapabilirler. Bu, kullanıcılar "Contoso Desteği" veya "Karşılama Masası Oluşturma" üzerinden e-posta gönderebildiklerinden, yardım ve destek posta kutuları için özellikle yararlıdır.

## <a name="before-you-begin"></a>Başlamadan önce

[Paylaşılan posta kutusu oluşturmadan](create-a-shared-mailbox.md) önce bilmeniz gereken bazı şeyler şunlardır:

- **Lisans:** Paylaşılan posta kutunuza lisans atamadan en fazla 50 GB veri depolayabilir. Bu alan dolduktan sonra daha fazla veri depolamak için posta kutusuna bir lisans atamanız gerekir. Paylaşılan posta kutusu lisanslama hakkında daha fazla bilgi için bkz. [Exchange Online Sınırları](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#StorageLimits). Paylaşılan bir posta kutusu depolama sınırına ulaştığında bir süre e-posta almaya devam edersiniz, ancak yeni e-posta gönderemezsiniz. Bu süre de sona erdiğinde e-posta alamazsınız. Posta kutusuna ileti gönderenler, iletinin teslim edilmediğine ilişkin bir bilgi alır.

- **Kullanıcı izinleri:** Kullanıcılara paylaşılan posta kutusunu kullanma izinleri (üyelik) vermeniz gerekir. Paylaşılan bir posta kutusunu yalnızca kuruluşunuzdaki kişiler kullanabilir.

- **Dış kullanıcılar:** İşletmenizin dışındaki kişilere (Gmail hesabı olan kişiler gibi) paylaşılan posta kutunuza erişim veremezsiniz. Bunu yapmak istiyorsanız, bunun yerine Outlook için bir grup oluşturmayı göz önünde bulundurun. Daha fazla bilgi için bkz. [Yönetim merkezinde Microsoft 365 grubu oluşturma](../create-groups/create-groups.md).

- **Outlook ile kullanma:** Paylaşılan posta kutularına erişmek için tarayıcınızdan Web üzerinde Outlook kullanmanın yanı sıra, iOS uygulaması için Outlook veya Android uygulaması için Outlook de kullanabilirsiniz. Daha fazla bilgi için bkz. [Outlook mobil cihazlara paylaşılan posta kutusu ekleme](https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f). Bir diğer seçenek de paylaşılan posta kutunuz için bir grup oluşturmaktır. Daha fazla bilgi için bkz. [Grupları Karşılaştırma](../create-groups/compare-groups.md).

- **Şifreleme:** Paylaşılan posta kutusundan gönderilen e-postaları şifreleyemezsiniz. Bunun nedeni, paylaşılan posta kutusunun kendi güvenlik bağlamı (kullanıcı adı/parola) olmamasından dolayı bir anahtar atanamamasıdır. Birden fazla kişi üyeyse ve kendi anahtarlarıyla şifreledikleri e-postaları gönderiyor/alıyorsa, e-postanın şifrelendiği ortak anahtara bağlı olarak diğer üyeler e-postayı okuyabilir ve diğerleri okuyamayabilir.

- **Posta kutusu dönüştürme:** Kullanıcı posta kutularını paylaşılan posta kutularına dönüştürebilirsiniz. Bkz [. Kullanıcı posta kutusunu paylaşılan posta kutusuna dönüştürme](convert-user-mailbox-to-shared-mailbox.md).

- **Yönetici rolleri:** Genel yönetici veya Exchange yönetici rolüne sahip kullanıcılar paylaşılan posta kutuları oluşturabilir.

- **Abonelik gereksinimleri:** Paylaşılan posta kutusu oluşturmak için e-posta (Exchange Online hizmeti) içeren bir iş için Microsoft 365 planına abone olmanız gerekir. İş için Microsoft 365 Uygulamaları aboneliği e-posta içermez. Microsoft 365 İş Standart e-posta içerir.

- **Oturum açma:** Paylaşılan posta kutusu, ilişkili kullanıcı hesabı tarafından doğrudan oturum açmaya yönelik değildir. Paylaşılan posta kutusu hesabı için oturum açmayı her zaman engellemeniz ve engellenmiş durumda tutmanız gerekir.

- **Çok fazla kullanıcı:** Paylaşılan bir posta kutusuna eşzamanlı olarak erişen çok fazla sayıda belirlenmiş kullanıcı olduğunda (en fazla 25 kullanıcı önerilir), bu posta kutusuna zaman zaman bağlanamayabilir veya giden kutusunda yinelenen iletiler gibi tutarsızlıklar olabilir. Bu durumda, kullanıcı sayısını azaltmayı veya Microsoft 365 grubu veya Ortak klasör gibi farklı bir iş yükü kullanmayı düşünebilirsiniz.

- **İleti silme:** Ne yazık ki, kişilerin paylaşılan posta kutusundaki iletileri silmesini önleyemezsiniz. Bunun tek yolu, paylaşılan posta kutusu yerine [bir Microsoft 365 grubu oluşturmaktır](/microsoft-365/admin/create-groups/create-groups). Outlook'daki bir grup paylaşılan posta kutusu gibidir. İkisinin karşılaştırması için bkz. [Grupları karşılaştırma](../create-groups/compare-groups.md). Gruplar hakkında daha fazla bilgi edinmek için bkz. [Microsoft 365 grupları hakkında bilgi edinin](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2).

- **Multi-Geo** Çok coğrafi bir ortamda, paylaşılan posta kutularının kullanıcı posta kutusunun lisanslanmasıyla aynı şekilde lisanslanması gerekir. Coğrafi bölgeler arası posta kutusu denetiminin desteklenmediğini unutmayın. Örneğin, kullanıcıya farklı bir coğrafi konumdaki paylaşılan posta kutusuna erişim izinleri atanmışsa, bu kullanıcı tarafından gerçekleştirilen posta kutusu eylemleri paylaşılan posta kutusunun posta kutusu denetim günlüğüne kaydedilmez. 


> [!NOTE]
> Paylaşılan posta kutusuna erişmek için kullanıcının Exchange Online lisansı olması gerekir, ancak paylaşılan posta kutusu ayrı bir lisans gerektirmez. Her paylaşılan posta kutusunun karşılık gelen bir kullanıcı hesabı vardır. Paylaşılan posta kutusunu oluştururken parola girmenizin nasıl istendiğini fark ettin mi? Hesabın parolası var, ancak sistem tarafından oluşturulmuş (bilinmiyor). Paylaşılan posta kutusunda oturum açmak için hesabı kullanmamalısınız. Lisans olmadan paylaşılan posta kutuları 50 GB ile sınırlıdır. Boyut sınırını 100 GB'a yükseltmek için paylaşılan posta kutusuna Exchange Online Plan 2 lisansı atanmalıdır. Exchange Online Arşivleme eklenti lisansına sahip Exchange Online Plan 1 lisansı yalnızca arşiv posta kutusunun boyutunu artırır. Bu, ek arşiv depolama kapasitesi için otomatik genişletme arşivlemeyi etkinleştirmenize de olanak tanır. Benzer şekilde, paylaşılan posta kutusunu dava ayrı tutmaya yerleştirmek istiyorsanız, paylaşılan posta kutusunun Exchange Online Plan 2 lisansına veya Exchange Online Arşivleme eklenti lisansına sahip bir Exchange Online Plan 1 lisansına sahip olması gerekir. Office 365 için Microsoft Defender, eBulma (Premium) veya otomatik saklama ilkeleri gibi gelişmiş özellikleri uygulamak istiyorsanız, paylaşılan posta kutusunun bu özellikler için lisanslanması gerekir.

## <a name="related-content"></a>İlgili içerik

[Paylaşılan posta kutusu oluşturma](create-a-shared-mailbox.md) (makale)\
[Paylaşılan posta kutusunu yapılandırma](configure-a-shared-mailbox.md) (makale)\
[Kullanıcı posta kutusunu paylaşılan posta kutusuna dönüştürme](convert-user-mailbox-to-shared-mailbox.md) (makale)\
[Paylaşılan posta kutusundan lisans kaldırma](remove-license-from-shared-mailbox.md) (makale)\
[Paylaşılan posta kutularıyla ilgili sorunları çözme](resolve-issues-with-shared-mailboxes.md) (makale)
