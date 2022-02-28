---
title: Yöneticiler için Microsoft 365 Gruplarına genel bakış
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
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
description: Grup Microsoft 365 kullanarak, bir grup kişinin paylaşılan kaynaklar koleksiyonuna erişmesi Microsoft 365 ekip çalışması boyunca ekip çalışmasına yolabilirsiniz.
ms.openlocfilehash: 5aaf7598f3591efb330618f0be98ea3376816eca
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983980"
---
# <a name="overview-of-microsoft-365-groups-for-administrators"></a>Yöneticiler için Microsoft 365 Gruplarına genel bakış

Microsoft 365 Grupları, farklı ekip çalışması boyunca tüm ekip çalışmasına yol alan temel Microsoft 365. En Microsoft 365 gruplarıyla, bir grup kişinin bir paylaşılan kaynak koleksiyonuna erişme izni veebilirsiniz. Bu kaynaklar şunlardır:

- Paylaşılan bir Outlook kutusu
- Paylaşılan takvim
- SharePoint belge kitaplığı
- Bir Planner
- OneNote not defteri
- Power BI
- Yammer (grup başka bir gruptan Yammer)
- Ekip (grup bir ekip üyesinden Teams)
- Yol Haritası (web Project varsa)
- Stream

Grup Microsoft 365, bu kaynakların her biri için izinleri el ile atamanız gerekmez. Gruba kişi eklemek, onlara gereken izinleri otomatik olarak verir.

Grup oluşturma belirli bir kişi grubuyla [sınırlandırmadıkça, tüm kullanıcılar grup oluşturabilir](../../solutions/manage-creation-of-groups.md). Grup oluşturma işleminizi sınırlandırdıysanız grup oluşturamazsanız, grup oluşturamaz olan kullanıcılar SharePoint siteleri, Planner'lar, ekipler, Outlook grup takvimleri, Akış grupları, Yammer grupları, OneDrive'daki paylaşılan kitaplıklar veya paylaşılan Power BI çalışma alanları oluşturamaz. Bu hizmetler, onları oluşturan kişilerin grup oluşturamalarını gerektirir. Grubun üyesi olan kullanıcılar, Planner'da görev oluşturma veya Teams sohbeti kullanma gibi grup etkinliklerine yine katılabilir.

Grupların rolleri şöyledir:

- **Sahipler** - Grup sahipleri üye ekleyebilir veya kaldırabilir ve paylaşılan gelen kutusundan konuşmaları silme veya grupla ilgili farklı ayarları değiştirme gibi benzersiz izinlere sahip olabilir. Grup sahipleri grubu yeniden adlandırarak açıklamayı veya resmi güncelleştirer ve daha fazlasını ister.
- **Üyeler** - Üyeler gruptaki her şeye erişim sağlar ancak grup ayarlarını değiştiremezler. Varsayılan olarak grup üyeleri konukları grubunuza katılmaya davetlayabilir, ancak bu [ayarı değiştirebilirsiniz](manage-guest-access-in-groups.md).
- **Konuklar** - Grup konukları, kurum dışından gelen üyelerdir.

Yalnızca genel yöneticiler, kullanıcı yöneticileri ve grup yöneticileri aynı grupta grup oluşturabilir ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">Microsoft 365 yönetim merkezi</a>. Yönetici temsilcisi olamazsınız (örneğin, başka birinin adına yönetici olan bir danışman).

Yönetici olarak şunları şunları ssunuz:

- [Kimlerin grup oluştura kişi oluştura kişilerini belirtme](../../solutions/manage-creation-of-groups.md)
- [Kuruluşta gruplar için adlandırma ilkesi oluşturma](../../solutions/groups-naming-policy.md)
- [Grup oluştururken hangi etki alanını kullanıcaz?](../../solutions/choose-domain-to-create-groups.md)
- [Gruplara konuk erişimini yönetme](manage-guest-access-in-groups.md)
- [Silinen grubu kurtarma](restore-deleted-group.md) (silme işleminin son 30 günü içinde)

Gruplarınızı yaşam döngüsünü yönetmek için daha otomatik bir yol Microsoft 365, grupların süresinin belirli bir zaman aralığında dolması için süre sonu ilkelerini kullanabilirsiniz. Grubun sahipleri, grubun süresi dolmadan 30, 15 ve 1 gün önce bir e-posta alırlar ve bu e-posta hala gerekirse grubun yenilenmesine olanak sağlar. Bkz. [Microsoft 365 Süre Sonu İlkesi](../../solutions/microsoft-365-groups-expiration-policy.md).

Gruplarınızı gruplardan veya Microsoft 365 yönetim merkezi [PowerShell kullanarak yönetabilirsiniz](../../enterprise/manage-microsoft-365-groups-with-powershell.md).

Büyük bir şirket veya kuruluş gibi çok sayıda kullanıcınız varsa, çeşitli amaçlarla grup oluşturan birçok kullanıcınız olabilir. En iyi uygulamalar için gruplarda [yönetim planı'Microsoft 365 gözden](../../solutions/collaboration-governance-overview.md) geçirmenizi kesinlikle öneririz.

## <a name="group-limits"></a>Grup sınırları

Kullanıcı Grupları için aşağıdaki Microsoft 365 geçerlidir:

|En fazla...|Değer|
|:---------|:----|
|Grup başına sahipler|100|
|Bir kullanıcının oluştura etki alanı oluşturması|250|
|Bir yöneticinin oluştur olduğu gruplar|Varsayılan kiracı sınırı olan 500 K'ye kadar|
|Üye sayısı|1.000'den fazla, ancak yalnızca 1.000 eşzamanlı olarak Grup konuşmalarına erişim sağlar. <br>Kullanıcılar, grup gruplarında yer alan büyük gruplarda takvim ve konuşmalara erişirken gecikmeler Outlook.|
|Bir kullanıcının üyesi olduğu Grup sayısı|7,000|
|Dosya depolama|Abone olan kullanıcı başına 1 Terabayt + 10 GB + satın alınan diğer depolama alanı. Sınırsız miktarda ek depolama alanı satın alabilirsiniz.|
|Grup Posta Kutusu boyutu|50 GB|

Bir kuruluşun sahip Microsoft 365 grup sayısı için varsayılan üst sayı 500.000'tir. Varsayılan sınırı aşan bir sınıra gitmek için Microsoft Desteği'ne başvurun. Gruplar sınırlarının nasıl Microsoft 365 için bkz. [Gruplar - Microsoft 365 yardımı](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2).

Grup kullanımı hakkında işlem Microsoft 365 olduğunda, grup gruplarınızı daha etkili bir şekilde yönetebilirsiniz. Rapor Microsoft 365 yönetim merkezi, depolama kullanımını, sahip olduğu etkin grupları ve kullanıcıların grupları nasıl kullananları görmenizi sağlayan bir raporlama aracı vardır. Daha [Microsoft 365 için Bkz. Yönetim merkezinde Raporlar'a](../activity-reports/office-365-groups.md) bakın.

## <a name="sensitivity-labels"></a>Duyarlılık etiketleri

Bir kullanıcı grubu oluşturduklarında, kuruluşta yer alan kullanıcıların ayarlarından duyarlılık Microsoft 365 oluşturabilirsiniz. Duyarlılık etiketleriyle şunları yapılandırabilirsiniz: 

- Gizlilik (genel veya özel)
- Dış kullanıcılara erişim
- Unmanaged device access

Örneğin, Çok Gizli adlı bir etiket oluşturabilir ve  bu etiketle oluşturulan her grubun özel olacağını ve dış kullanıcılara izin ver vermeyeceğini belirtebilirsiniz. Kuruluşta kullanıcılar grup oluşturma sırasında bu etiketi seçerken, grup özel olarak ayarlanır ve grup üyelerinin gruba dış kullanıcı eklemesine izin verilmez.

> [!IMPORTANT]
> Şu anda sınıflandırma etiketleri kullanıyorsanız, duyarlılık etiketleri etkinleştirildikten sonra grup oluşturan kullanıcılar artık bu etiketleri kullanmayacak. 

Duyarlılık etiketlerini oluşturma, yönetme ve kullanma hakkında bilgi için bkz. Microsoft Teams, Microsoft 365 grupları ve sitelerde içeriği korumak [için SharePoint kullanma](../../compliance/sensitivity-labels-teams-groups-sites.md).

## <a name="which-microsoft-365-plans-include-groups"></a>Hangi Microsoft 365 grupları içerir?

Exchange Online Online Microsoft 365 tüm SharePoint grupları destekleyecektir. Buna İş Temel Bilgiler ve İş Plan Premium ve E1, E3 Enterprise E5 planları dahildir. Grup, grubu oluşturan kişinin lisansını alır (grubun "düzenleyicisi" olarak da bilinir). Düzenleyici, grubun sahip olması istediğiniz özellikler için uygun lisansa sahip olduğu sürece, bu lisans gruba iletecek.

> [!NOTE]
> Hizmet aileleri ve planları Microsoft 365 daha ayrıntılı bilgi için bkz. [Microsoft 365 seçeneklerine bakın](/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options).

Yalnızca Exchange bir planınız varsa, Outlook'te grupların paylaşılan gelen kutusu ve paylaşılan takvim özelliklerine yine de sahip olursanız, belge kitaplığı, Planner veya diğer özelliklerden herhangi birini elde etmeyebilirsiniz.

Microsoft 365 gruplar gruplarla birlikte Azure Active Directory. Edinilen grup özellikleri, hangi Azure Active Directory sahip olduğunu ve grubun düzenleyicisine hangi lisansların atandığına bağlıdır.

> [!IMPORTANT]
> Tüm grup özellikleri için, Azure AD Premium aboneliğiniz varsa, kullanıcılar onlara atanmış bir AAD P1 lisansına sahip olsalar da gruba katılabilirler. Lisans zorunlu kılınmaz.
> Düzenli aralıklarla, hangi kullanıcıların lisansın eksik olduğunu ve lisans gereksinimlerine uyumlu olması için onlara bir lisans atanmamış olması gerektiren kullanım raporları oluşturacağız. Örneğin, bir kullanıcının lisansı olmadığını ve adlandırma ilkesi zorunlu kılınan bir gruba ekli olduğunu kabul etmek var. Rapor, lisansa ihtiyaç olduğunu size bayrakla haber veerer.

## <a name="related-content"></a>İlgili içerik

[Gruplar hakkında bilgi Microsoft 365 (](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)makale)\
[Dağıtım listelerini Gruplara yükseltme Microsoft 365 (](../manage/upgrade-distribution-lists.md)makale)\
[PowerShell Microsoft 365 Grupları Yönetme](../../enterprise/manage-microsoft-365-groups-with-powershell.md) (makale)\
[SharePoint Çevrimiçi Sınırlar](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits) (makale)\
[Microsoft Stream'de grupları ve kanalları düzenleme](/stream/groups-channels-organization) (makale)
