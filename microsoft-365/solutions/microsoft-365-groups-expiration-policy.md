---
title: Microsoft 365 süresi sonu ilkesi
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
recommendations: false
description: Grup süre sonu Microsoft 365 ilkeleri hakkında bilgi edinin.
ms.openlocfilehash: 1c0ac1aa7e38fddb85bb9b434c46665cacd1ca69
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2021
ms.locfileid: "63005026"
---
# <a name="microsoft-365-group-expiration-policy"></a>Microsoft 365 süresi sonu ilkesi

Grupların ve grupların ve grupların Microsoft 365 artışla Microsoft Teams yöneticilerin ve kullanıcıların kullanılmayan grupları ve ekipleri temizlemenin bir yolu gerekir. Etkin Microsoft 365 süre sonu ilkesi, etkin olmayan grupları sistemden kaldırmaya ve işleri daha temiz hale etmeye yardımcı olabilir.

Bir grubun süresi dolduğunda tüm ilişkili hizmetleri (posta kutusu, Planner, SharePoint sitesi, ekip vb.) de silinir.

Bir grubun süresi dolduğunda "yazılımdan silinir", bu da 30 gün içinde kurtarıl devam anlamına gelir.

Yöneticiler bir sona erme süresi ve bu dönemin sonuna ulaşan ve yenilenmemiş olan etkin olmayan tüm grup silinir. (Arşivlenmiş ekipler buna dahildir.) Son kullanma süresi, grubun oluşturulma tarihi veya son yenileme tarihiyle başlar. Grup sahiplerine süre dolmadan önce otomatik olarak bir e-posta gönderilir ve bu e-posta grubu başka bir son kullanma süresi için yenilemelerine olanak sağlar. Teams kullanıcılar kalıcı bildirimleri e-posta Teams.

Etkin bir şekilde kullanım halinde olan gruplar otomatik olarak yenilenir. Aşağıdaki eylemlerden herhangi biri grubu otomatik olarak yeniler:
- SharePoint: Dosyaları görüntüleme, düzenleme, indirme, taşıma, paylaşma veya karşıya yükleme. (Sayfa SharePoint görüntülemek otomatik yenileme işlemi olarak sayılmaz.)
- Outlook- gruba katılın, gruptaki grup mesajını okuyun veya yazın, bir ileti (grup Web üzerinde Outlook).
- Teams- bir teams kanalını ziyaret ederek.

Otomatik grup Yammer tetikleyen tek etkinlik, bir belgenin topluluk içinde başka bir SharePoint karşıya yüklemek olduğunu unutmayın.

> [!IMPORTANT]
> Süre sonu ilkesini değiştirseniz, hizmet her grubun son kullanma tarihini yeniden hesaplar. Her zaman grubun oluşturulma tarihinden itibaren saymaya başlar ve sonra yeni süre sonu ilkesi uygulanır.

Süre sonu kullanmanın varsayılan olarak kapalı olduğunu bilmek önemlidir. Kullanmak isteyen yöneticilerin, kendi kuruluşları için bu özelliği etkinleştirmesi gerekir.

> [!NOTE]
> Microsoft 365 grupları için süre sonu ilkesi yapılandırmak ve kullanmak, süre sonu ilkesi uygulanan tüm grupların üyelerine Azure AD Premium lisansları atamanız zorunlu değildir. Daha fazla bilgi için bkz[. Azure Active Directory Premium](/azure/active-directory/active-directory-get-started-premium).

## <a name="who-can-configure-and-use-the-microsoft-365-groups-expiration-policy"></a>Who grupları süre sonu Microsoft 365 yapılandırarak kullanabilir misiniz?

|Rol|Ne yapmaları gerekenler|
|---------|---------|
|Office 365 yönetici olarak (Azure'da Şirket yöneticisi), Kullanıcı yöneticisi|Grupların süre sonu ilke ayarlarını oluşturun, Microsoft 365, güncelleştirin veya silin.|
|Kullanıcı|Sahip olduğu [Microsoft 365](/azure/active-directory/users-groups-roles/groups-restore-deleted) grubunu yenileme veya geri yükleme|

## <a name="how-to-set-the-expiration-policy"></a>Süre sonu ilkesi nasıl ayarlanır

Yukarıda da belirtildiği gibi, süre sonu varsayılan olarak kapalıdır. Yöneticinin süre sonu ilkesi etkinleştirmesi ve geçerlilik için özelliklerini ayarlaması gerekir. Etkinleştirmek için, Azure Active Directory  > **GroupsExpiration** >  **seçeneğine gidin**. Burada varsayılan grup yaşam süresini değiştirebilir ve ilk ve ikinci son kullanma süresi bildirimlerinin grup sahibine ne kadar önceden gitmek istediğiniz belirtabilirsiniz.

Grup yaşam süresi gün olarak belirtilir ve sizin belirttiğiniz özel bir değerle veya 180, 365 olarak ayarlanır. Özel değer en az 30 gün öncedir.

Grubun sahibi yoksa, süre sonu e-postaları belirtilen yöneticiye gider.

İlkeyi tüm gruplarınız, yalnızca seçili gruplar (en çok 500) için ayar yapmak veya Yok'ı seçerek tamamen **kapatarak kapatsanız**. Şu anda farklı gruplar için farklı ilkelerin olmadığını unutmayın.

![Grup'ta Gruplar süre sonu ayarlarının Azure Active Directory.](../media/azure-groups-expiration-settings.png)

## <a name="how-expiry-works-with-the-retention-policy"></a>Süre sonu bekletme ilkesiyle nasıl çalışır?

Güvenlik ve Uyumluluk Merkezi'nde gruplar için bir bekletme ilkesi ayardıysanız, süre sonu ilkesi bekletme ilkesiyle sorunsuz çalışır. Grubun kullanım süresi dolduğunda, grubun grup sitesindeki posta kutusu konuşmaları ve dosyaları bekletme ilkesinde tanımlanan belirli sayıda gün boyunca bekletme kapsayıcısinde korunur. Ancak son kullanma tarihinden sonra kullanıcılar grubu veya içeriğini görmez.

## <a name="how-and-when-a-group-owner-learns-if-their-groups-are-going-to-expire"></a>Grup sahibi grupların süresinin dolacak olup olacağını nasıl ve ne zaman öğrenir?

Grup sahiplerine yalnızca e-postayla bilgi gönderilir. Grup Planner, SharePoint veya başka bir uygulama aracılığıyla oluşturuldusa, süre sonu bildirimleri her zaman e-posta yoluyla gönderilir. Grup Grup, Grup Teams aracılığıyla oluşturuldu ise, grup sahibi etkinlik bölümü aracılığıyla yenilenecek bir bildirim alır. Grup sahibinin geçerli bir e-posta adresi yoksa, bir grup için süre sonu ayarını etkinleştirmeniz önerilmez.

Grubun süresi dolmadan 30 gün önce, grup sahipleri (veya sahibi olmadığınız gruplar için belirttiğiniz e-posta adresleri) grubu kolayca yenilemelerine olanak sağlayan bir e-posta alır. Yenilemezse, sona ermeden 15 gün önce bir yenileme e-postası daha alırlar. Aboneliği yine yenilemezse son kullanma tarihinden bir gün önce bir e-posta bildirimi daha alırlar.

Herhangi bir nedenle grup sahiplerinin veya yöneticilerinin hiçbirinin süresi dolmadan önce grubu yenilememesi durumuyla, yönetici süre dolmadan önce grubu 30 gün boyunca geri yükleyebilir. Ayrıntılar için bkz: [Silinmiş bir grup Microsoft 365 geri yükleme](https://support.office.com/article/restore-a-deleted-office-365-group-b7c66b59-657a-4e1a-8aa0-8163b1f4eb54).

## <a name="archiving-group-contents"></a>Grup içeriğini arşivleme

Artık kullanmayı planlamay istediğiniz ancak içeriğini korumak istediğiniz bir grubunuz varsa, farklı grup hizmetlerinden bilgileri dışarı aktarma hakkında bilgi için bkz. [Grupları,](end-life-cycle-groups-teams-sites-yammer.md) ekipleri ve Yammer'i arşivleme.

## <a name="related-topics"></a>İlgili konular

[İşbirliği yönetim planlaması önerileri](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[İşbirliği yönetim planınızı oluşturma](collaboration-governance-first.md)

[Bekletme ilkelerine genel bakış](https://support.office.com/article/5e377752-700d-4870-9b6d-12bfc12d2423)

[Sahipsiz bir gruba yeni sahip atama](https://support.office.com/article/86bb3db6-8857-45d1-95c8-f6d540e45732)

[Grupların Microsoft 365 süresini yapılandırma](/azure/active-directory/active-directory-groups-lifecycle-azure-portal)
