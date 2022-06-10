---
title: İzinler - Güvenlik & Uyumluluk Merkezi
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.AdminRoleGroups
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
description: Yöneticiler, Microsoft 365'daki Güvenlik & Uyumluluk Merkezi'nde bulunan izinler hakkında bilgi edinebilir.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0e8b6fb5e32332a17d0df47222b346b8880c97cb
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66015258"
---
# <a name="permissions-in-the-security--compliance-center"></a>Güvenlik ve Uyumluluk Merkezi’ndeki İzinler

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Güvenlik & Uyumluluk Merkezi, cihaz yönetimi, veri kaybı önleme, eBulma, saklama vb. gibi uyumluluk görevlerini gerçekleştiren kişilere izin vermenizi sağlar. Bu kişiler yalnızca açıkça erişim iznini vediğiniz görevleri gerçekleştirebilir. Güvenlik & Uyumluluk Merkezi'ne erişmek için kullanıcıların genel yönetici veya bir veya daha fazla Güvenlik & Uyumluluk Merkezi rol grubunun üyesi olması gerekir.

Güvenlik & Uyumluluk Merkezi'ndeki izinler rol tabanlı erişim denetimi (RBAC) izin modelini temel alır. RBAC, Exchange tarafından kullanılan izin modeliyle aynıdır, bu nedenle Exchange biliyorsanız, Güvenlik & Uyumluluk Merkezi'nde izinler vermek çok benzer olacaktır. Bununla birlikte, Exchange rol gruplarının ve Güvenlik & Uyumluluk Merkezi rol gruplarının üyelik veya izinleri paylaşmadığını unutmayın. Her ikisinin de bir Kuruluş Yönetimi rol grubu olsa da, aynı değildir. Verdikleri izinler ve rol gruplarının üyeleri farklıdır. Aşağıda Güvenlik & Uyumluluk Merkezi rol gruplarının listesi yer almaktadır.

:::image type="content" source="../../media/992c20ca-e82e-497c-9c8d-6fab212deb80.png" alt-text="Güvenlik & Uyumluluk Merkezi'ndeki İzinler sayfası" lightbox="../../media/992c20ca-e82e-497c-9c8d-6fab212deb80.png":::

## <a name="relationship-of-members-roles-and-role-groups"></a>Üyelerin, rollerin ve rol gruplarının ilişkisi

**Rol**, bir görev kümesi gerçekleştirme izinleri verir; örneğin, Olay Yönetimi rolü kişilerin eBulma servis talepleri ile çalışmasına olanak tanır.

**Rol grubu**, güvenlik & Uyumluluk Merkezi'nde kişilerin işlerini yapmalarına olanak tanıyan bir dizi roldür. Örneğin, Uyumluluk Yöneticisi rol grubu Durum Yönetimi, İçerik Arama ve Kuruluş Yapılandırması rollerini (diğer rollerin yanı sıra) içerir çünkü uyumluluk yöneticisi olan birinin işini yapması için bu görevlerin izinlerine ihtiyacı olur.

Güvenlik & Uyumluluk Merkezi, kişileri atamanız gereken en yaygın görevler ve işlevler için varsayılan rol gruplarını içerir. Varsayılan rol gruplarına tek tek kullanıcıları **üye** olarak eklemenizi öneririz.

:::image type="content" source="../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png" alt-text="Rol gruplarının roller ve üyelerle ilişkisi" lightbox="../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png":::

## <a name="role-groups-in-the-security--compliance-center"></a>Güvenlik & Uyumluluk Merkezi'ndeki rol grupları

Aşağıdaki tabloda Güvenlik & Uyumluluk Merkezi'nde kullanılabilen varsayılan rol grupları ve varsayılan olarak rol gruplarına atanan roller listelenmiştir. Bir kullanıcıya uyumluluk görevi gerçekleştirme izni vermek için, bunları uygun Güvenlik & Uyumluluk Merkezi rol grubuna ekleyin.

Güvenlik & Uyumluluk Merkezi'ndeki izinleri yönetmek, kullanıcılara yalnızca Güvenlik & Uyumluluk Merkezi'nin içinde bulunan uyumluluk özelliklerine erişim sağlar. Exchange posta akışı kuralları (taşıma kuralları olarak da bilinir) gibi Güvenlik & Uyumluluk Merkezi'nde olmayan diğer uyumluluk özelliklerine izin vermek istiyorsanız, Exchange yönetim merkezini (EAC) kullanmanız gerekir. Daha fazla bilgi için bkz. [Exchange Online'de İzinler](/exchange/permissions-exo/permissions-exo).

Güvenlik & Uyumluluk Merkezi'ne erişim izni vermeyi görmek için [Bkz. Kullanıcılara Microsoft Purview yönetim merkezine erişim verme](grant-access-to-the-security-and-compliance-center.md).

> [!NOTE]
> Güvenlik & Uyumluluk Merkezi'nde **İzinler** sekmesini görüntülemek için yönetici olmanız gerekir. Özellikle, **Rol Yönetimi** rolünün atanması gerekir ve bu rol varsayılan olarak yalnızca Güvenlik & Uyumluluk Merkezi'ndeki **Kuruluş Yönetimi** rol grubuna atanır. Ayrıca, **Rol Yönetimi** rolü kullanıcıların rol gruplarını görüntülemesine, oluşturmasına ve değiştirmesine olanak tanır.

|Rol grubu|Açıklama|Varsayılan roller atandı|
|---|---|---|
|**Saldırı Benzetimi Yöneticileri**|Güvenlik & Uyumluluk Merkezi'nde bu rol grubunu kullanmayın. Azure AD'de karşılık gelen rolü kullanın.|Saldırı Simülatörü Yöneticisi|
|**Saldırı Simülatörü Yükü Yazarları**|Güvenlik & Uyumluluk Merkezi'nde bu rol grubunu kullanmayın. Azure AD'de karşılık gelen rolü kullanın.|Saldırı Simülatörü Yükü Yazarı|
|**İletişim Uyumluluğu**|Tüm iletişim uyumluluk rollerine izin verir: yönetici, analist, araştırmacı ve görüntüleyici.|Olay Yönetimi <br/><br/> İletişim Uyumluluğu Yöneticisi <br/><br/> İletişim Uyumluluk Analizi <br/><br/> İletişim Uyumluluğu Durum Yönetimi <br/><br/> İletişim Uyumluluğu Araştırması <br/><br/> İletişim Uyumluluğu Görüntüleyicisi <br/><br/> Veri Sınıflandırması Geri Bildirim Sağlayıcısı <br/><br/> Veri Bağlayıcısı Yöneticisi <br/><br/> View-Only Servis Talebi|
|**İletişim Uyumluluğu Yöneticileri**|İlke oluşturabilen/düzenleyebilen ve genel ayarları tanımlayabilen iletişim uyumluluğu yöneticileri.|İletişim Uyumluluğu Yöneticisi <br/><br/> İletişim Uyumluluğu Durum Yönetimi <br/><br/> Veri Bağlayıcısı Yöneticisi|
|**İletişim Uyumluluğu Analistleri**|İlke eşleşmelerini araştırabilen, ileti meta verilerini görüntüleyebilen ve düzeltme eylemleri gerçekleştirebilen iletişim uyumluluğu analistleri.|İletişim Uyumluluk Analizi <br/><br/> İletişim Uyumluluğu Durum Yönetimi|
|**İletişim Uyumluluğu Araştırmacıları**|İlke eşleşmelerini araştırabilen, ileti içeriğini görüntüleyebilen ve düzeltme eylemleri gerçekleştirebilen iletişim uyumluluğu analistleri.|Olay Yönetimi <br/><br/> İletişim Uyumluluk Analizi <br/><br/> İletişim Uyumluluğu Durum Yönetimi <br/><br/> İletişim Uyumluluğu Araştırması <br/><br/> Veri Sınıflandırması Geri Bildirim Sağlayıcısı <br/><br/> View-Only Servis Talebi|
|**İletişim Uyumluluğu Görüntüleyicileri**|Kullanılabilir raporlara ve pencere öğelerine erişebilen iletişim uyumluluğu görüntüleyicisi.|İletişim Uyumluluğu Durum Yönetimi <br/><br/> İletişim Uyumluluğu Görüntüleyicisi|
|**Uyumluluk Yöneticisi**<sup>1</sup>|Üyeler cihaz yönetimi, veri kaybı önleme, raporlar ve koruma ayarlarını yönetebilir.|Olay Yönetimi <br/><br/> İletişim Uyumluluğu Yöneticisi <br/><br/> İletişim Uyumluluğu Durum Yönetimi <br/><br/> Uyumluluk Yöneticisi <br/><br/> Uyumluluk Araması <br/><br/> Veri Sınıflandırması Geri Bildirim Sağlayıcısı <br/><br/> Veri Sınıflandırma geri bildirimi gözden geçiren <br/><br/> Veri Bağlayıcısı Yöneticisi <br/><br/> Veri Araştırma Yönetimi <br/><br/> Cihaz Yönetimi <br/><br/> Disposition Management <br/><br/> DLP Uyumluluk Yönetimi <br/><br/> Tutun <br/><br/> IB Uyumluluk Yönetimi <br/><br/> Information Protection Yöneticisi <br/><br/> Information Protection Analisti <br/><br/> Information Protection Araştırmacısı <br/><br/> Information Protection Okuyucu <br/><br/> Insider Risk Management Yöneticisi <br/><br/> Uyarıları Yönet <br/><br/> Kuruluş Yapılandırması <br/><br/> RecordManagement <br/><br/> Bekletme Yönetimi <br/><br/> Denetim Günlüklerini View-Only <br/><br/> View-Only Servis Talebi <br/><br/> View-Only Cihaz Yönetimi <br/><br/> View-Only DLP Uyumluluk Yönetimi <br/><br/> View-Only IB Uyumluluk Yönetimi <br/><br/> Uyarıları View-Only Yönetme <br/><br/> alıcıları View-Only <br/><br/> View-Only Kayıt Yönetimi <br/><br/> View-Only Bekletme Yönetimi|
|**Uyumluluk Verileri Yöneticisi**|Üyeler cihaz yönetimi, veri koruma, veri kaybı önleme, raporlar ve koruma ayarlarını yönetebilir.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Araması <br/><br/> Veri Bağlayıcısı Yöneticisi <br/><br/> Cihaz Yönetimi <br/><br/> Disposition Management <br/><br/> DLP Uyumluluk Yönetimi <br/><br/> IB Uyumluluk Yönetimi <br/><br/> Information Protection Yöneticisi <br/><br/> Information Protection Analisti <br/><br/> Information Protection Araştırmacısı <br/><br/> Information Protection Okuyucu <br/><br/> Uyarıları Yönet <br/><br/> Kuruluş Yapılandırması <br/><br/> RecordManagement <br/><br/> Bekletme Yönetimi <br/><br/> Duyarlılık Etiketi Yöneticisi <br/><br/> Denetim Günlüklerini View-Only <br/><br/> View-Only Cihaz Yönetimi <br/><br/> View-Only DLP Uyumluluk Yönetimi <br/><br/> View-Only IB Uyumluluk Yönetimi <br/><br/> Uyarıları View-Only Yönetme <br/><br/> alıcıları View-Only <br/><br/> View-Only Kayıt Yönetimi <br/><br/> View-Only Bekletme Yönetimi|
|**Uyumluluk Yöneticisi Yöneticileri**|Şablon oluşturma ve değiştirme işlemlerini yönetin.|Uyumluluk Yöneticisi Yönetimi <br/><br/> Uyumluluk Yöneticisi Değerlendirmesi <br/><br/> Uyumluluk Yöneticisi Katkısı <br/><br/> Uyumluluk Yöneticisi Okuyucusu <br/><br/> Veri Bağlayıcısı Yöneticisi|
|**Uyumluluk Yöneticisi Değerlendiricileri**|Değerlendirmeler oluşturun, iyileştirme eylemleri uygulayın ve iyileştirme eylemleri için test durumunu güncelleştirin.|Uyumluluk Yöneticisi Değerlendirmesi <br/><br/> Uyumluluk Yöneticisi Katkısı <br/><br/> Uyumluluk Yöneticisi Okuyucusu <br/><br/> Veri Bağlayıcısı Yöneticisi|
|**Uyumluluk Yöneticisi Katkıda Bulunanları**|Değerlendirmeler oluşturun ve iyileştirme eylemlerini uygulamak için çalışma gerçekleştirin.|Uyumluluk Yöneticisi Katkısı <br/><br/> Uyumluluk Yöneticisi Okuyucusu <br/><br/> Veri Bağlayıcısı Yöneticisi|
|**Uyumluluk Yöneticisi Okuyucuları**|Yönetici işlevleri dışındaki tüm Uyumluluk Yöneticisi içeriğini görüntüleyin.|Uyumluluk Yöneticisi Okuyucusu|
|**İçerik Gezgini İçerik Görüntüleyicisi**|İçerik gezgininde içerik dosyalarını görüntüleyin.|Veri Sınıflandırma İçerik Görüntüleyicisi|
|**İçerik Gezgini Liste Görüntüleyicisi**|İçerik gezginindeki tüm öğeleri yalnızca liste biçiminde görüntüleyin.|Veri Sınıflandırma Listesi Görüntüleyicisi|
|**Veri Araştırmacısı**|Posta kutuları, SharePoint Çevrimiçi siteler ve OneDrive İş konumlarında aramalar yapın.|İletişim <br/><br/> Uyumluluk Araması <br/><br/> Veli <br/><br/> Veri Araştırma Yönetimi <br/><br/> Dışarı aktarma <br/><br/> Önizleme <br/><br/> Gözden geçirin <br/><br/> RMS Şifre Çözme <br/><br/> Arama ve Temizleme|
|**eBulma Yöneticisi**|Üyeler posta kutularına, SharePoint Çevrimiçi sitelere ve OneDrive İş konumlarına arama yapabilir ve ayrı tutma gerçekleştirebilir. Üyeler ayrıca eBulma servis taleplerini oluşturup yönetebilir, servis talebine üye ekleyip kaldırabilir, bir servis talebiyle ilişkili İçerik Aramaları oluşturup düzenleyebilir ve eBulma'da (Premium) büyük/küçük harf verilerine erişebilir. <br/><br/> eBulma Yöneticisi, ek izinler atanmış eBulma Yöneticisi rol grubunun bir üyesidir. eBulma Yöneticisi'nin gerçekleştirebileceği görevlere ek olarak, eBulma Yöneticisi şunları yapabilir:<ul><li>Kuruluştaki tüm eBulma servis taleplerini görüntüleyin.</li><li>Kendilerini servis talebine üye olarak ekledikten sonra herhangi bir eBulma servis talebini yönetin.</li></ul> <br/><br/> eBulma Yöneticisi ile eBulma Yöneticisi arasındaki birincil fark, eBulma Yöneticisinin Güvenlik & Uyumluluk Merkezi'ndeki **eBulma servis talepleri** sayfasında listelenen tüm servis taleplerine erişebilmesidir. Bir eBulma yöneticisi yalnızca oluşturdukları servis talebine veya üyesi olduğu servis taleplerine erişebilir. Kullanıcıyı eBulma Yöneticisi yapma hakkında daha fazla bilgi için bkz. [Güvenlik & Uyumluluk Merkezi'nde eBulma izinleri atama](../../compliance/assign-ediscovery-permissions.md).|Olay Yönetimi <br/><br/> İletişim <br/><br/> Uyumluluk Araması <br/><br/> Veli <br/><br/> Dışarı aktarma <br/><br/> Tutun <br/><br/> Önizleme <br/><br/> Gözden geçirin <br/><br/> RMS Şifre Çözme|
|**Genel Okuyucu**|Üyeler raporlara, uyarılara salt okunur erişime sahiptir ve tüm yapılandırma ve ayarları görebilir. <br/><br/> Genel Okuyucu ile Güvenlik Okuyucusu arasındaki temel fark, Genel Okuyucunun **yapılandırmaya ve ayarlara** erişebilmesidir.|Güvenlik Okuyucusu <br/><br/> Duyarlılık Etiketi Okuyucusu <br/><br/> Hizmet Güvencesi Görünümü <br/><br/> Denetim Günlüklerini View-Only <br/><br/> View-Only Cihaz Yönetimi <br/><br/> View-Only DLP Uyumluluk Yönetimi <br/><br/> View-Only IB Uyumluluk Yönetimi <br/><br/> Uyarıları View-Only Yönetme <br/><br/> alıcıları View-Only <br/><br/> View-Only Kayıt Yönetimi <br/><br/> View-Only Bekletme Yönetimi|
|**Information Protection**|Duyarlılık etiketleri ve ilkeleri, DLP, tüm sınıflandırıcı türleri, etkinlik ve içerik gezgini ve tüm ilgili raporlar dahil olmak üzere tüm bilgi koruma özellikleri üzerinde tam denetim.|Veri Sınıflandırma İçerik Görüntüleyicisi <br/><br/> Information Protection Yöneticisi <br/><br/> Information Protection Analisti <br/><br/> Information Protection Araştırmacısı <br/><br/> Information Protection Okuyucu|
|**Information Protection Yöneticileri**|DLP ilkelerini, duyarlılık etiketlerini ve ilkelerini ve tüm sınıflandırıcı türlerini oluşturun, düzenleyin ve silin. Otomatik etiketleme ilkeleri için uç nokta DLP ayarlarını ve simülasyon modunu yönetin.|Information Protection Yöneticisi|
|**Information Protection Analistleri**|DLP uyarılarına ve etkinlik gezginine erişin ve bu uyarıları yönetin. DLP ilkelerine, duyarlılık etiketlerine ve ilkelerine ve tüm sınıflandırıcı türlerine yalnızca görüntüleme erişimi.|Veri Sınıflandırma Listesi Görüntüleyicisi <br/><br/> Information Protection Analisti|
|**Information Protection Araştırmacıları**|DLP uyarılarına, etkinlik gezginine ve içerik gezginine erişin ve bu uyarıları yönetin. DLP ilkelerine, duyarlılık etiketlerine ve ilkelerine ve tüm sınıflandırıcı türlerine yalnızca görüntüleme erişimi.|Veri Sınıflandırma İçerik Görüntüleyicisi <br/><br/> Information Protection Analisti <br/><br/> Information Protection Araştırmacısı|
|**Information Protection Okuyucular**|DLP ilkeleri, duyarlılık etiketleri ve ilkeleri için raporlara yalnızca görüntüleme erişimi.|Information Protection Okuyucu|
|**Insider Risk Management**|Kuruluşunuz için iç risk yönetimini tek bir grupta yönetmek için bu rol grubunu kullanın. Belirlenen yöneticiler, analistler ve araştırmacılar için tüm kullanıcı hesaplarını ekleyerek, içeriden risk yönetimi izinlerini tek bir grupta yapılandırabilirsiniz. Bu rol grubu, tüm insider risk yönetimi izin rollerini içerir. Bu, şirket içi risk yönetimini hızlı bir şekilde kullanmaya başlamanın en kolay yoludur ve ayrı kullanıcı grupları için tanımlanmış ayrı izinlere ihtiyaç duymayan kuruluşlar için uygundur.|Olay Yönetimi <br/><br/> Veri Bağlayıcısı Yöneticisi <br/><br/> Insider Risk Management Yöneticisi <br/><br/> Insider Risk Yönetimi Analizi <br/><br/> Insider Risk Yönetimi Denetimi <br/><br/> Insider Risk Yönetimi Araştırması <br/><br/> Insider Risk Yönetimi Oturumları <br/><br/> View-Only Servis Talebi|
|**Insider Risk Yönetimi Yöneticileri**|Başlangıçta insider risk yönetimini yapılandırmak ve daha sonra insider risk yöneticilerini tanımlı bir gruba ayırmak için bu rol grubunu kullanın. Bu rol grubundaki kullanıcılar insider risk yönetimi ilkelerini, genel ayarları ve rol grubu atamalarını oluşturabilir, okuyabilir, güncelleştirebilir ve silebilir.|Olay Yönetimi <br/><br/> Veri Bağlayıcısı Yöneticisi <br/><br/> Insider Risk Management Yöneticisi <br/><br/> View-Only Servis Talebi|
|**İçeriden Risk Yönetimi Analistleri**|Bu grubu, içeriden risk olayı analisti olarak davranacak kullanıcılara izin atamak için kullanın. Bu rol grubundaki kullanıcılar tüm insider risk yönetimi uyarılarına, olaylarına ve bildirim şablonlarına erişebilir. İç risk İçerik Gezgini'ne erişemezler.|Olay Yönetimi <br/><br/> Insider Risk Yönetimi Analizi <br/><br/> View-Only Servis Talebi|
|**Insider Risk Management Denetçileri**|İç risk yönetimi etkinliklerini denetleyecek kullanıcılara izinler atamak için bu grubu kullanın. Bu rol grubundaki kullanıcılar insider risk denetim günlüğüne erişebilir.|Insider Risk Yönetimi Denetimi|
|**İçeriden Risk Yönetimi Araştırmacıları**|Insider risk veri araştırmacısı olarak davranacak kullanıcılara izin atamak için bu grubu kullanın. Bu rol grubundaki kullanıcılar tüm iç risk yönetimi uyarılarına, servis taleplerine, bildirimler şablonlarına ve tüm durumlar için İçerik Gezgini'ne erişebilir.|Olay Yönetimi <br/><br/> Insider Risk Yönetimi Araştırması <br/><br/> View-Only Servis Talebi|
|**Insider Risk Yönetimi Oturumu Onaylayanları**|Oturum kaydı için grup değişikliği isteklerini yönetin.|Insider Risk Yönetimi Oturumları|
|**IRM Katkıda Bulunanları**|Bu rol grubu görünür, ancak yalnızca arka plan hizmetleri tarafından kullanılır.|Insider Risk Management Kalıcı katkı <br/><br/> Insider Risk Management Geçici katkısı|
|**Bilgi Yöneticileri**|Bilgileri, öğrenmeyi, eğitimleri ve diğer akıllı özellikleri atamayı yapılandırın.|Bilgi Yöneticisi|
|**MailFlow Yöneticisi**|Üyeler, Güvenlik & Uyumluluk Merkezi'nde posta akışı içgörülerini ve raporlarını izleyebilir ve görüntüleyebilir. Genel yöneticiler bu gruba sıradan kullanıcılar ekleyebilir, ancak kullanıcı Exchange Yönetici grubunun üyesi değilse, kullanıcı yöneticiyle ilgili Exchange görevlere erişemez.|alıcıları View-Only|
|**Kuruluş Yönetimi**<sup>1</sup>|Üyeler Güvenlik & Uyumluluk Merkezi'ndeki özelliklere erişim izinlerini denetleyebileceği gibi, cihaz yönetimi, veri kaybı önleme, raporlar ve koruma ayarlarını da yönetebilir. <p> Genel yönetici olmayan kullanıcıların, Microsoft 365 için Basic Mobility ve Security (eski adıyla Mobil Cihaz Yönetimi veya MDM) tarafından yönetilen cihazları görebilmesi ve bu cihazlarda işlem yapması için Exchange yöneticileri olmalıdır. <p> Genel yöneticiler otomatik olarak bu rol grubunun üyesi olarak eklenir, ancak bunları [Güvenlik & Uyumluluk PowerShell'indeki](/powershell/module/exchange/get-rolegroupmember) [Get-RoleGroupMember](/powershell/module/exchange/get-rolegroupmember) cmdlet'in çıktısında görmezsiniz.|Denetim Günlükleri <p><p> Olay Yönetimi <p> İletişim Uyumluluğu Yöneticisi <p> İletişim Uyumluluğu Durum Yönetimi <p> Uyumluluk Yöneticisi <p> Uyumluluk Araması <p> Veri Bağlayıcısı Yöneticisi <p> Cihaz Yönetimi <p> DLP Uyumluluk Yönetimi <p> Tutun <p> IB Uyumluluk Yönetimi <p> Insider Risk Management Yöneticisi <p> Uyarıları Yönet <p> Kuruluş Yapılandırması <p> Karantina <p> RecordManagement <p> Bekletme Yönetimi <p> Rol Yönetimi <p> Arama ve Temizleme <p> Güvenlik Yöneticisi <p> Güvenlik Okuyucusu <p> Duyarlılık Etiketi Yöneticisi <p> Duyarlılık Etiketi Okuyucusu <p> Hizmet Güvencesi Görünümü <p> Etiket Katkıda Bulunanı <p> Etiket Yöneticisi <p> Etiket Okuyucusu <p> Denetim Günlüklerini View-Only <p> View-Only Cihaz Yönetimi <p> View-Only DLP Uyumluluk Yönetimi <p> View-Only IB Uyumluluk Yönetimi <p> View-Only Servis Talebi <p> Uyarıları View-Only Yönetme <p> alıcıları View-Only <p> View-Only Kayıt Yönetimi <p> View-Only Bekletme Yönetimi|
|**Gizlilik Yönetimi**|Microsoft Purview uyumluluk portalında Priva için erişim denetimini yönetin.|Olay Yönetimi <p><p> Veri Sınıflandırma İçerik Görüntüleyicisi <p> Veri Sınıflandırma Listesi Görüntüleyicisi <p> Gizlilik Yönetimi Yöneticisi <p> Gizlilik Yönetimi Analizi <p> Gizlilik Yönetimi Araştırması <p> Gizlilik Yönetimi Kalıcı katkı <p> Gizlilik Yönetimi Geçici katkısı <p> Gizlilik Yönetimi Görüntüleyicisi <p> Konu Hakları İsteği Yöneticisi <p> View-Only Servis Talebi|
|**Gizlilik Yönetimi Yöneticileri**|İlke oluşturabilen/düzenleyebilen ve genel ayarları tanımlayabilen gizlilik yönetimi çözümünün yöneticileri.|Olay Yönetimi <p><p> Gizlilik Yönetimi Yöneticisi <p> View-Only Servis Talebi|
|**Gizlilik Yönetimi Analistleri**|İlke eşleşmelerini araştırabilen, iletilerin meta verilerini görüntüleyebilen ve düzeltme eylemleri gerçekleştirebilen gizlilik yönetimi çözümünün analistleri.|Olay Yönetimi <p><p> Veri Sınıflandırma Listesi Görüntüleyicisi <p> Gizlilik Yönetimi Analizi <p> View-Only Servis Talebi|
|**Gizlilik YönetimiNe Katkıda Bulunanlar**|Gizlilik yönetimi olayları için katkıda bulunan erişimini yönetin.|Gizlilik Yönetimi Kalıcı katkı <p><p> Gizlilik Yönetimi Geçici katkısı|
|**Gizlilik Yönetimi Araştırmacıları**|İlke eşleşmelerini araştırabilen, ileti içeriğini görüntüleyebilen ve düzeltme eylemleri gerçekleştirebilen gizlilik yönetimi çözümünü araştıran araştırmacılar.|Olay Yönetimi <p><p> Veri Sınıflandırma İçerik Görüntüleyicisi <p> Veri Sınıflandırma Listesi Görüntüleyicisi <p> Gizlilik Yönetimi Araştırması <p> View-Only Servis Talebi|
|**Gizlilik Yönetimi Görüntüleyicileri**|Kullanılabilir panolara ve pencere öğelerine erişebilen gizlilik yönetimi çözümünün görüntüleyicisi.|Veri Sınıflandırma Listesi Görüntüleyicisi <p><p> Gizlilik Yönetimi Görüntüleyicisi|
|**Karantina Yöneticisi**|Üyeler tüm Karantina eylemlerine erişebilir. Daha fazla bilgi için bkz. [Karantinaya alınan iletileri ve dosyaları EOP'de yönetici olarak yönetme](manage-quarantined-messages-and-files.md)|Karantina|
|**Kayıt Yönetimi**|Üyeler, bekletme etiketleri ve edat gözden geçirmeleri dahil olmak üzere kayıt yönetiminin tüm yönlerini yapılandırabilir.|Disposition Management <p><p> RecordManagement <p> Bekletme Yönetimi|
|**Inceleme**|Üyeler[, eBulma (Premium)](../../compliance/overview-ediscovery-20.md) olaylarında gözden geçirme kümelerine erişebilir. Bu rol grubunun üyeleri, üyesi oldukları Microsoft Purview uyumluluk portalının **eBulma > Gelişmiş** sayfasında servis taleplerinin listesini görebilir ve açabilir. Kullanıcı bir eBulma (Premium) olayına eriştiğinde, olay verilerine erişmek için **Kümeleri gözden geçir'i** seçebilir. Bu rol, kullanıcının servis talebiyle ilişkili bir koleksiyon aramasının sonuçlarını önizlemesine veya diğer arama veya servis talebi yönetim görevlerini gerçekleştirmesine izin vermez. Bu rol grubunun üyeleri yalnızca bir gözden geçirme kümesindeki verilere erişebilir.|Gözden geçirin|
|**Güvenlik Yöneticisi**|Üyeler Kimlik Koruma Merkezi, Privileged Identity Management, Microsoft 365 Hizmet Durumunu İzleme ve Güvenlik & Uyumluluk Merkezi'nin çeşitli güvenlik özelliklerine erişebilir. <p> Varsayılan olarak, bu rol grubunun herhangi bir üyesi olmayabilir. Ancak, Azure Active Directory güvenlik yöneticisi rolü bu rol grubuna atanır. Bu nedenle, bu rol grubu Güvenlik Yöneticisi rolünün özelliklerini ve üyeliğini Azure Active Directory devralır. <p> İzinleri merkezi olarak yönetmek için Azure Active Directory yönetim merkezine grup üyelerini ekleyin ve kaldırın. Daha fazla bilgi için bkz. [yerleşik rolleri Azure AD](/azure/active-directory/roles/permissions-reference). Bu rol grubunu Güvenlik & Uyumluluk Merkezi'nde (üyelik veya roller) düzenlerseniz, bu değişiklikler diğer hizmetler için değil yalnızca Güvenlik & Uyumluluk Merkezi için geçerlidir. <p> Bu rol grubu, Güvenlik okuyucusu rolünün tüm salt okunur izinlerinin yanı sıra aynı hizmetler için bir dizi ek yönetim izni içerir: Azure Information Protection, Kimlik Koruma Merkezi, Privileged Identity Management, İzleme Microsoft 365  Hizmet Durumu ve Güvenlik & Uyumluluk Merkezi.|Denetim Günlükleri <p><p> Cihaz Yönetimi <p> DLP Uyumluluk Yönetimi <p> IB Uyumluluk Yönetimi <p> Uyarıları Yönet <p> Karantina <p> Güvenlik Yöneticisi <p> Duyarlılık Etiketi Yöneticisi <p> Etiket Katkıda Bulunanı <p> Etiket Yöneticisi <p> Etiket Okuyucusu <p> Denetim Günlüklerini View-Only <p> View-Only Cihaz Yönetimi <p> View-Only DLP Uyumluluk Yönetimi <p> View-Only IB Uyumluluk Yönetimi <p> Uyarıları View-Only Yönetme|
|**Güvenlik İşleci**|Üyeler güvenlik uyarılarını yönetebilir ve ayrıca güvenlik özelliklerinin raporlarını ve ayarlarını görüntüleyebilir.|Uyumluluk Araması <p><p> Uyarıları Yönet <p> Güvenlik Okuyucusu <p> Etiket Katkıda Bulunanı <p> Etiket Okuyucusu <p> Kiracı AllowBlockList Manager <p> Denetim Günlüklerini View-Only <p> View-Only Cihaz Yönetimi <p> View-Only DLP Uyumluluk Yönetimi <p> View-Only IB Uyumluluk Yönetimi <p> Uyarıları View-Only Yönetme|
|**Güvenlik Okuyucusu**|Üyeler Kimlik Koruma Merkezi, Privileged Identity Management, Microsoft 365 Hizmet Durumunu İzleme ve Güvenlik & Uyumluluk Merkezi'nin çeşitli güvenlik özelliklerine salt okunur erişime sahiptir. <p> Varsayılan olarak, bu rol grubunun herhangi bir üyesi olmayabilir. Ancak, Azure Active Directory güvenlik okuyucusu rolü bu rol grubuna atanır. Bu nedenle, bu rol grubu Güvenlik Okuyucusu rolünün özelliklerini ve üyeliğini Azure Active Directory devralır. <p> İzinleri merkezi olarak yönetmek için Azure Active Directory yönetim merkezine grup üyelerini ekleyin ve kaldırın. Daha fazla bilgi için bkz. [yerleşik rolleri Azure AD](/azure/active-directory/roles/permissions-reference). Bu rol grubunu Güvenlik & Uyumluluk Merkezi'nde (üyelik veya roller) düzenlerseniz, bu değişiklikler diğer hizmetler için değil yalnızca Güvenlik & Uyumluluk Merkezi için geçerlidir.|Güvenlik Okuyucusu <p><p> Duyarlılık Etiketi Okuyucusu <p> Etiket Okuyucusu <p> View-Only Cihaz Yönetimi <p> View-Only DLP Uyumluluk Yönetimi <p> View-Only IB Uyumluluk Yönetimi <p> Uyarıları View-Only Yönetme|
|**Hizmet Güvencesi Kullanıcısı**|Üyeler Güvenlik & Uyumluluk Merkezi'ndeki Hizmet güvencesi bölümüne erişebilir. Hizmet güvencesi, Microsoft'un Microsoft 365 depolanan müşteri verilerine yönelik güvenlik uygulamalarını açıklayan raporlar ve belgeler sağlar. Ayrıca Microsoft 365 hakkında bağımsız üçüncü taraf denetim raporları sağlar. Daha fazla bilgi için bkz [. Güvenlik & Uyumluluk Merkezi'nde hizmet güvencesi](../../compliance/service-assurance.md).|Hizmet Güvencesi Görünümü|
|**Konu Hakları İsteği Yöneticileri**|Konu hakları istekleri oluşturun.|Olay Yönetimi <br/><br/> Konu Hakları İsteği Yöneticisi <br/><br/> View-Only Servis Talebi|
|**Gözetmen İncelemesi**|Üyeler, kuruluşta hangi iletişimlerin gözden geçirileceğini tanımlayan ilkeleri oluşturabilir ve yönetebilir. Daha fazla bilgi için bkz [. Kuruluşunuz için iletişim uyumluluk ilkelerini yapılandırma](../../compliance/communication-compliance-configure.md).|Gözetmen Gözden Geçirme Yöneticisi|

> [!NOTE]
> <sup>1</sup> Bu rol grubu, üyelere denetim günlüğünde arama yapmak veya DLP veya Office 365 için Defender raporları gibi Exchange verileri içerebilecek raporları kullanmak için gereken izinleri atamaz. Denetim günlüğünde arama yapmak veya tüm raporları görüntülemek için kullanıcıya Exchange Online'da izinler atanmalıdır. Bunun nedeni, denetim günlüğünde arama yapmak için kullanılan temel cmdlet'in Exchange Online bir cmdlet olmasıdır. Genel yöneticiler denetim günlüğünde arama yapabilir ve tüm raporları görüntüleyebilir çünkü Exchange Online'de Kuruluş Yönetimi rol grubunun üyeleri olarak otomatik olarak eklenirler. Daha fazla bilgi için bkz [. Güvenlik & Uyumluluk Merkezi'nde denetim günlüğünde arama](../../compliance/search-the-audit-log-in-security-and-compliance.md) yapma.

## <a name="roles-in-the-security--compliance-center"></a>Güvenlik & Uyumluluk Merkezi'ndeki roller

Aşağıdaki tabloda, kullanılabilir roller ve varsayılan olarak atandıkları rol grupları listelenmiştir.

Aşağıdaki rollerin varsayılan olarak Kuruluş Yönetimi rol grubuna atanmadığına dikkat edin:

- Saldırı Simülatörü Yöneticisi
- Saldırı Simülatörü Yükü Yazarı
- İletişim
- İletişim Uyumluluk Analizi
- İletişim Uyumluluğu Araştırması
- İletişim Uyumluluğu Görüntüleyicisi
- Uyumluluk Yöneticisi Yönetimi
- Uyumluluk Yöneticisi Değerlendirmesi
- Uyumluluk Yöneticisi Katkısı
- Uyumluluk Yöneticisi Okuyucusu
- Veli
- Veri Sınıflandırma İçerik Görüntüleyicisi
- Veri Sınıflandırması Geri Bildirim Sağlayıcısı
- Veri Sınıflandırma geri bildirimi gözden geçiren
- Veri Sınıflandırma Listesi Görüntüleyicisi
- Veri Araştırma Yönetimi
- Disposition Management
- Dışarı aktarma
- Information Protection Yöneticisi
- Information Protection Analisti
- Information Protection Araştırmacısı
- Information Protection Okuyucu
- Insider Risk Yönetimi Analizi
- Insider Risk Yönetimi Denetimi
- Insider Risk Yönetimi Araştırması
- Insider Risk Management Kalıcı katkı
- Insider Risk Yönetimi Oturumları
- Insider Risk Management Geçici katkısı
- Bilgi Yöneticisi
- Önizleme
- Gizlilik Yönetimi Yöneticisi
- Gizlilik Yönetimi Analizi
- Gizlilik Yönetimi Araştırması
- Gizlilik Yönetimi Kalıcı katkı
- Gizlilik Yönetimi Geçici katkısı
- Gizlilik Yönetimi Görüntüleyicisi
- Gözden geçirin
- RMS Şifre Çözme
- Konu Hakları İsteği Yöneticisi
- Gözetmen Gözden Geçirme Yöneticisi
- Kiracı AllowBlockList Manager

|Rol|Açıklama|Varsayılan rol grubu atamaları|
|---|---|---|
|**Saldırı Simülatörü Yöneticisi**|Bu rolü Güvenlik & Uyumluluk Merkezi'nde kullanmayın. Azure AD'de karşılık gelen rolü kullanın.|Saldırı Simülatörü Yöneticileri|
|**Saldırı Simülatörü Yükü Yazarı**|Bu rolü Güvenlik & Uyumluluk Merkezi'nde kullanmayın. Azure AD'de karşılık gelen rolü kullanın.|Saldırı Simülatörü Yükü Yazarları|
|**Denetim Günlükleri**|Kuruluş için denetimi açın ve yapılandırın, kuruluşun denetim raporlarını görüntüleyin ve ardından bu raporları bir dosyaya aktarın.|Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi|
|**Olay Yönetimi**|eBulma servis talepleri oluşturma, düzenleme, silme ve erişimi denetleme.|İletişim Uyumluluğu <br/><br/> İletişim Uyumluluğu Araştırmacıları <br/><br/> Uyumluluk Yöneticisi <br/><br/> eBulma Yöneticisi <br/><br/> Insider Risk Management <br/><br/> Insider Risk Yönetimi Yöneticileri <br/><br/> İçeriden Risk Yönetimi Analistleri <br/><br/> İçeriden Risk Yönetimi Araştırmacıları <br/><br/> Kuruluş Yönetimi <br/><br/> Gizlilik Yönetimi <br/><br/> Gizlilik Yönetimi Yöneticileri <br/><br/> Gizlilik Yönetimi Analistleri <br/><br/> Gizlilik Yönetimi Araştırmacıları <br/><br/> Konu Hakları İsteği Yöneticileri|
|**İletişim**|Bir eBulma (Premium) olayında tanımlanan koruyucularla tüm iletişimleri yönetin.  Ayrı tutma bildirimleri, tutma anımsatıcıları ve yönetime yükseltmeler oluşturun. Saklama bildirimlerini onaylayan koruyucuyu takip edin ve her koruyucu tarafından koruyucu olarak tanımlandığı durumlarla ilgili iletişimleri izlemek için kullanılan koruyucu portalına erişimi yönetin.|Veri Araştırmacısı <br/><br/> eBulma Yöneticisi|
|**İletişim Uyumluluğu Yöneticisi**|İletişim Uyumluluğu özelliğinde ilkeleri yönetmek için kullanılır.|İletişim Uyumluluğu <br/><br/> İletişim Uyumluluğu Yöneticileri <br/><br/> Uyumluluk Yöneticisi <br/><br/> Kuruluş Yönetimi|
|**İletişim Uyumluluk Analizi**|İletişim Uyumluluğu özelliğindeki ileti ihlallerini araştırmak, düzeltmek için kullanılır. Yalnızca ileti meta verilerini görüntüleyebilir.|İletişim Uyumluluğu <br/><br/> İletişim Uyumluluğu Analistleri <br/><br/> İletişim Uyumluluğu Araştırmacıları|
|**İletişim Uyumluluğu Durum Yönetimi**|İletişim Uyumluluğu durumlarına erişmek için kullanılır.|İletişim Uyumluluğu <br/><br/> İletişim Uyumluluğu Yöneticileri <br/><br/> İletişim Uyumluluğu Analistleri <br/><br/> İletişim Uyumluluğu Araştırmacıları <br/><br/> İletişim Uyumluluğu Görüntüleyicileri <br/><br/> Uyumluluk Yöneticisi <br/><br/> Kuruluş Yönetimi|
|**İletişim Uyumluluğu Araştırması**|İletişim Uyumluluğu özelliğinde inceleme, düzeltme ve ileti ihlallerini gözden geçirmek için kullanılır. İleti meta verilerini ve iletisini görüntüleyebilir.|İletişim Uyumluluğu <br/><br/> İletişim Uyumluluğu Araştırmacıları|
|**İletişim Uyumluluğu Görüntüleyicisi**|İletişim Uyumluluğu özelliğindeki raporlara ve pencere öğelerine erişmek için kullanılır.|İletişim Uyumluluğu <br/><br/> İletişim Uyumluluğu Görüntüleyicileri|
|**Uyumluluk Yöneticisi**|Uyumluluk özellikleri için ayarları ve raporları görüntüleyin ve düzenleyin.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Verileri Yöneticisi <br/><br/> Kuruluş Yönetimi|
|**Uyumluluk Yöneticisi Yönetimi**|Şablon oluşturma ve değiştirme işlemlerini yönetin.|Uyumluluk Yöneticisi Yöneticileri|
|**Uyumluluk Yöneticisi Değerlendirmesi**|Değerlendirmeler oluşturun, iyileştirme eylemleri uygulayın ve iyileştirme eylemleri için test durumunu güncelleştirin.|Uyumluluk Yöneticisi Yöneticileri <br/><br/> Uyumluluk Yöneticisi Değerlendiricileri|
|**Uyumluluk Yöneticisi Katkısı**|Değerlendirmeler oluşturun ve iyileştirme eylemlerini uygulamak için çalışma gerçekleştirin.|Uyumluluk Yöneticisi Yöneticileri <br/><br/> Uyumluluk Yöneticisi Değerlendiricileri <br/><br/> Uyumluluk Yöneticisi Katkıda Bulunanları|
|**Uyumluluk Yöneticisi Okuyucusu**|Yönetici işlevleri dışındaki tüm Uyumluluk Yöneticisi içeriğini görüntüleyin.|Uyumluluk Yöneticisi Yöneticileri <br/><br/> Uyumluluk Yöneticisi Değerlendiricileri <br/><br/> Uyumluluk Yöneticisi Katkıda Bulunanları <br/><br/> Uyumluluk Yöneticisi Okuyucuları|
|**Uyumluluk Araması**|Posta kutuları arasında aramalar yapın ve sonuçların tahminini alın.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Verileri Yöneticisi <br/><br/> Veri Araştırmacısı <br/><br/> eBulma Yöneticisi <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik İşleci|
|**Veli**|eBulma (Premium) olaylarında koruyucuları belirleyin ve yönetin ve koruyucularla ilişkili veri kaynaklarını bulmak için Azure Active Directory ve diğer kaynaklardan gelen bilgileri kullanın. Posta kutuları, SharePoint siteleri ve Teams gibi diğer veri kaynaklarını bir durumda koruyucularla ilişkilendirin.  Bir olay bağlamında içeriği korumak için koruyucularla ilişkili veri kaynaklarına yasal bir saklama yerleştirin.|Veri Araştırmacısı <br/><br/> eBulma Yöneticisi|
|**Veri Sınıflandırma İçerik Görüntüleyicisi**|İçerik gezgininde dosyaların yerinde işlenmesini görüntüleyin.|İçerik Gezgini İçerik Görüntüleyicisi <br/><br/> Information Protection <br/><br/> Information Protection Araştırmacıları <br/><br/> Gizlilik Yönetimi <br/><br/> Gizlilik Yönetimi Araştırmacıları|
|**Veri Sınıflandırması Geri Bildirim Sağlayıcısı**|İçerik gezgininde sınıflandırıcılara geri bildirim sağlamaya izin verir.|İletişim Uyumluluğu <br/><br/> İletişim Uyumluluğu Araştırmacıları <br/><br/> Uyumluluk Yöneticisi|
|**Veri Sınıflandırma geri bildirimi gözden geçiren**|Geri bildirim gezgininde sınıflandırıcılardan gelen geri bildirimlerin gözden geçirilmesine izin verir.|Uyumluluk Yöneticisi|
|**Veri Sınıflandırma Listesi Görüntüleyicisi**|İçerik gezginindeki dosyaların listesini görüntüleyin.|İçerik Gezgini Liste Görüntüleyicisi <br/><br/> Information Protection Analistleri <br/><br/> Gizlilik Yönetimi <br/><br/> Gizlilik Yönetimi Analistleri <br/><br/> Gizlilik Yönetimi Araştırmacıları <br/><br/> Gizlilik Yönetimi Görüntüleyicileri|
|**Veri Bağlayıcısı Yöneticisi**|Microsoft 365'de Microsoft dışı verileri içeri aktarmak ve arşivlemek için bağlayıcılar oluşturun ve yönetin.|İletişim Uyumluluğu <br/><br/> İletişim Uyumluluğu Yöneticileri <br/><br/> Uyumluluk Yöneticisi <br/><br/> Uyumluluk Verileri Yöneticisi <br/><br/> Uyumluluk Yöneticisi Yöneticileri <br/><br/> Uyumluluk Yöneticisi Değerlendiricileri <br/><br/> Uyumluluk Yöneticisi Katkıda Bulunanları <br/><br/> Insider Risk Management <br/><br/> Insider Risk Yönetimi Yöneticileri <br/><br/> Kuruluş Yönetimi|
|**Veri Araştırma Yönetimi**|Veri araştırmasına erişimi oluşturun, düzenleyin, silin ve denetleyin.|Uyumluluk Yöneticisi <br/><br/> Veri Araştırmacısı|
|**Cihaz Yönetimi**|Cihaz yönetimi özellikleri için ayarları ve raporları görüntüleyin ve düzenleyin.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Verileri Yöneticisi <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi|
|**Disposition Management**|Güvenlik & Uyumluluk Merkezi'nde El ile Elden Çıkarma'ya erişim izinlerini denetleyin.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Verileri Yöneticisi <br/><br/> Kayıt Yönetimi|
|**DLP Uyumluluk Yönetimi**|Veri kaybı önleme (DLP) ilkeleri için ayarları ve raporları görüntüleyin ve düzenleyin.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Verileri Yöneticisi <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi|
|**Dışarı aktarma**|Aramalardan döndürülen posta kutusunu ve site içeriğini dışarı aktarın.|Veri Araştırmacısı <br/><br/> eBulma Yöneticisi|
|**Tutun**|İçeriği posta kutularına, sitelere ve ortak klasörlere ayrı tutma. Ayrı tutulduğunda, içeriğin bir kopyası güvenli bir konumda depolanır. İçerik sahipleri özgün içeriği değiştirmeye veya silmeye devam eder.|Uyumluluk Yöneticisi <br/><br/> eBulma Yöneticisi <br/><br/> Kuruluş Yönetimi|
|**IB Uyumluluk Yönetimi**|Bilgi Engeli ilkelerini görüntüleyin, oluşturun, kaldırın, değiştirin ve test edin.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Verileri Yöneticisi <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi|
|**Information Protection Yöneticisi**|DLP ilkelerini, duyarlılık etiketlerini ve ilkelerini ve tüm sınıflandırıcı türlerini oluşturun, düzenleyin ve silin. Otomatik etiketleme ilkeleri için uç nokta DLP ayarlarını ve simülasyon modunu yönetin.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Verileri Yöneticisi <br/><br/> Information Protection <br/><br/> Information Protection Yöneticileri|
|**Information Protection Analisti**|DLP uyarılarına ve etkinlik gezginine erişin ve bu uyarıları yönetin. DLP ilkelerine, duyarlılık etiketlerine ve ilkelerine ve tüm sınıflandırıcı türlerine yalnızca görüntüleme erişimi.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Verileri Yöneticisi <br/><br/> Information Protection <br/><br/> Information Protection Analistleri <br/><br/> Information Protection Araştırmacıları|
|**Information Protection Araştırmacısı**|DLP uyarılarına, etkinlik gezginine ve içerik gezginine erişin ve bu uyarıları yönetin. DLP ilkelerine, duyarlılık etiketlerine ve ilkelerine ve tüm sınıflandırıcı türlerine yalnızca görüntüleme erişimi.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Verileri Yöneticisi <br/><br/> Information Protection <br/><br/> Information Protection Araştırmacıları|
|**Information Protection Okuyucu**|DLP ilkeleri, duyarlılık etiketleri ve ilkeleri için raporlara yalnızca görüntüleme erişimi.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Verileri Yöneticisi <br/><br/> Information Protection <br/><br/> Information Protection Okuyucular|
|**Insider Risk Management Yöneticisi**|Insider Risk Management özelliğine erişimi oluşturun, düzenleyin, silin ve denetleyin.|Uyumluluk Yöneticisi <br/><br/> Insider Risk Management <br/><br/> Insider Risk Yönetimi Yöneticileri <br/><br/> Kuruluş Yönetimi|
|**Insider Risk Yönetimi Analizi**|Tüm insider risk yönetimi uyarılarına, olaylarına ve bildirim şablonlarına erişin.|Insider Risk Management <br/><br/> İçeriden Risk Yönetimi Analistleri|
|**Insider Risk Yönetimi Denetimi**|Insider Risk denetim izlerini görüntülemeye izin verin.|Insider Risk Management <br/><br/> Insider Risk Management Denetçileri|
|**Insider Risk Yönetimi Araştırması**|Tüm iç risk yönetimi uyarılarına, servis taleplerine, bildirimler şablonlarına ve tüm durumlar için İçerik Gezgini'ne erişin.|Insider Risk Management <br/><br/> İçeriden Risk Yönetimi Araştırmacıları|
|**Insider Risk Management Kalıcı katkı**|Bu rol grubu görünür, ancak yalnızca arka plan hizmetleri tarafından kullanılır.|IRM Katkıda Bulunanları|
|**Insider Risk Yönetimi Oturumları**|Oturum kaydı için grup değişikliği isteklerini yönetmeye izin verin.|Insider Risk Management <br/><br/> Insider Risk Yönetimi Oturumu Onaylayanları|
|**Insider Risk Management Geçici katkısı**|Bu rol grubu görünür, ancak yalnızca arka plan hizmetleri tarafından kullanılır.|IRM Katkıda Bulunanları|
|**Bilgi Yöneticisi**|Bilgileri, öğrenmeyi, eğitimleri ve diğer akıllı özellikleri atamayı yapılandırın.|Bilgi Yöneticileri|
|**Uyarıları Yönet**|Uyarılar için ayarları ve raporları görüntüleyin ve düzenleyin.|Uyumluluk Yöneticisi <p><p> Uyumluluk Verileri Yöneticisi <p> Kuruluş Yönetimi <p> Güvenlik Yöneticisi <p> Güvenlik İşleci|
|**Kuruluş Yapılandırması**|Denetim raporlarını çalıştırın, görüntüleyin ve dışarı aktarın ve DLP, cihazlar ve koruma için uyumluluk ilkelerini yönetin.|Uyumluluk Yöneticisi <p><p> Uyumluluk Verileri Yöneticisi <p> Kuruluş Yönetimi|
|**Önizleme**|İçerik aramalarından döndürülen öğelerin listesini görüntüleyin ve içeriğini görüntülemek için listedeki her öğeyi açın.|Veri Araştırmacısı <p><p> eBulma Yöneticisi|
|**Gizlilik Yönetimi Yöneticisi**|Gizlilik Yönetimi'nde ilkeleri yönetin ve çözümün tüm işlevlerine erişime sahiptir.|Gizlilik Yönetimi <p><p> Gizlilik Yönetimi Yöneticileri|
|**Gizlilik Yönetimi Analizi**|Gizlilik Yönetimi'nde ileti ihlallerinin araştırılması ve düzeltilmesi. Yalnızca ileti meta verilerini görüntüleyebilir.|Gizlilik Yönetimi <p> Gizlilik Yönetimi Analistleri|
|**Gizlilik Yönetimi Araştırması**|Gizlilik Yönetimi'nde inceleme, düzeltme ve ileti ihlallerini gözden geçirme. İleti meta verilerini ve iletinin tamamını görüntüleyebilir.|Gizlilik Yönetimi <p><p> Gizlilik Yönetimi Araştırmacıları|
|**Gizlilik Yönetimi Kalıcı katkı**|Kalıcı katkıda bulunan olarak Gizlilik Yönetimi durumlara erişin.|Gizlilik Yönetimi <p><p> Gizlilik YönetimiNe Katkıda Bulunanlar|
|**Gizlilik Yönetimi Geçici katkısı**|Geçici katkıda bulunan olarak Gizlilik Yönetimi olaylarını inceleyin.|Gizlilik Yönetimi <p><p> Gizlilik YönetimiNe Katkıda Bulunanlar|
|**Gizlilik Yönetimi Görüntüleyicisi**|Gizlilik Yönetimi'nde panolara ve pencere öğelerine erişin.|Gizlilik Yönetimi <p><p> Gizlilik Yönetimi Görüntüleyicileri|
|**Karantina**|Karantinaya alınan e-postanın görüntülenmesine ve serbest bırakılmasına izin verir.|Karantina Yöneticisi <p><p> Güvenlik Yöneticisi <p> Kuruluş Yönetimi|
|**RecordManagement**|Kayıt yönetimi özelliğinin yapılandırmasını görüntüleyin ve düzenleyin.|Uyumluluk Yöneticisi <p><p> Uyumluluk Verileri Yöneticisi <p> Kuruluş Yönetimi <p> Kayıt Yönetimi|
|**Bekletme Yönetimi**|Bekletme ilkelerini, bekletme etiketlerini ve bekletme etiketi ilkelerini yönetin.|Uyumluluk Yöneticisi <p><p> Uyumluluk Verileri Yöneticisi <p> Kuruluş Yönetimi <p> Kayıt Yönetimi|
|**Gözden geçirin**|Bu rol, kullanıcıların eBulma (Premium) olaylarında gözden geçirme kümelerine erişmesini sağlar. Bu role atanan kullanıcılar, üyesi oldukları Microsoft Purview uyumluluk portalının **eBulma > Gelişmiş** sayfasında servis taleplerinin listesini görebilir ve açabilir. Kullanıcı bir eBulma (Premium) olayına eriştiğinde, olay verilerine erişmek için **Kümeleri gözden geçir'i** seçebilir. Bu rol, kullanıcının servis talebiyle ilişkili bir koleksiyon aramasının sonuçlarını önizlemesine veya diğer arama veya servis talebi yönetim görevlerini gerçekleştirmesine izin vermez. Bu role sahip kullanıcılar yalnızca bir gözden geçirme kümesindeki verilere erişebilir.|Veri Araştırmacısı <p><p> eBulma Yöneticisi <p> Inceleme|
|**RMS Şifre Çözme**|Arama sonuçlarını dışarı aktarırken RMS korumalı içeriğin şifresini çözme.|Veri Araştırmacısı <p><p> eBulma Yöneticisi|
|**Rol Yönetimi**|Rol grubu üyeliğini yönetin ve özel rol grupları oluşturun veya silin.|Kuruluş Yönetimi|
|**Arama ve Temizleme**|kişilerin içerik arama ölçütlerine uyan verileri toplu olarak kaldırmasına olanak tanır.|Veri Araştırmacısı <br/><br/> Kuruluş Yönetimi|
|**Güvenlik Yöneticisi**|Güvenlik özellikleri için yapılandırmayı ve raporları görüntüleyin ve düzenleyin.|Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi|
|**Güvenlik Okuyucusu**|Güvenlik özellikleri için yapılandırmayı ve raporları görüntüleyin.|Genel Okuyucu <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik İşleci <br/><br/> Güvenlik Okuyucusu|
|**Duyarlılık Etiketi Yöneticisi**|Duyarlılık etiketlerini görüntüleyin, oluşturun, değiştirin ve kaldırın.|Uyumluluk Verileri Yöneticisi <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi|
|**Duyarlılık Etiketi Okuyucusu**|Duyarlılık etiketlerinin yapılandırmasını ve kullanımını görüntüleyin.|Genel Okuyucu <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik Okuyucusu|
|**Hizmet Güvencesi Görünümü**|Hizmet Güvencesi bölümünden kullanılabilir belgeleri indirin. İçerik, yasal uyumluluk ve güvenlik risklerini yönetmek için Microsoft 365 özelliklerini kullanmaya yönelik bağımsız denetim, uyumluluk belgeleri ve güvenle ilgili yönergeleri içerir.|Genel Okuyucu <br/><br/> Kuruluş Yönetimi <br/><br/> Hizmet Güvencesi Kullanıcısı|
|**Gözetmen Gözden Geçirme Yöneticisi**|Hangi iletişimlerin gözden geçirileceğini ve gözden geçirmeyi kimin yapması gerektiğini de içeren denetim gözden geçirme ilkelerini yönetin.|Gözetmen İncelemesi|
|**Etiket Katkıda Bulunanı**|Mevcut kullanıcı etiketlerinin üyeliğini görüntüleyin ve güncelleştirin.|Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi <br/><br/> Güvenlik İşleci|
|**Etiket Yöneticisi**|Kullanıcı etiketlerini görüntüleyin, güncelleştirin, oluşturun ve silin.|Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi|
|**Etiket Okuyucusu**|Mevcut kullanıcı etiketlerine salt okunur erişim.|Güvenlik Okuyucusu|
|**Kiracı AllowBlockList Manager**|Kiracı izin engelleme listesi ayarlarını yönetin.|Güvenlik İşleci|
|**Yalnızca Görüntüleme Denetim Günlükleri**|Denetim raporlarını görüntüleyin ve dışarı aktarın. Bu raporlar hassas bilgiler içerebileceğinden, bu rolü yalnızca bu bilgileri görüntülemesi gereken kişilere atamanız gerekir.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Verileri Yöneticisi <br/><br/> Genel Okuyucu <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi <br/><br/> Güvenlik İşleci|
|**Yalnızca Görüntüle Büyük/Küçük Harf**||İletişim Uyumluluğu <br/><br/> İletişim Uyumluluğu Araştırmacıları <br/><br/> Uyumluluk Yöneticisi <br/><br/> Insider Risk Management <br/><br/> Insider Risk Yönetimi Yöneticileri <br/><br/> İçeriden Risk Yönetimi Analistleri <br/><br/> Insider RiskManagement Araştırmacıları <br/><br/> Kuruluş Yönetimi <br/><br/> Gizlilik Yönetimi <br/><br/> Gizlilik Yönetimi Yöneticileri <br/><br/> Gizlilik Yönetimi Analistleri <br/><br/> Gizlilik Yönetimi Araştırmacıları <br/><br/> Konu Hakları İsteği Yöneticileri|
|**Yalnızca Görüntüleme Cihaz Yönetimi**|Cihaz Yönetimi özelliğinin yapılandırmasını ve raporlarını görüntüleyin.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Verileri Yöneticisi <br/><br/> Genel Okuyucu <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi <br/><br/> Güvenlik İşleci <br/><br/> Güvenlik Okuyucusu|
|**Yalnızca Görüntüleme DLP Uyumluluk Yönetimi**|Veri kaybı önleme (DLP) ilkeleri için ayarları ve raporları görüntüleyin.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Verileri Yöneticisi <br/><br/> Genel Okuyucu <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi <br/><br/> Güvenlik İşleci <br/><br/> Güvenlik Okuyucusu|
|**Salt Görüntüleme IB Uyumluluk Yönetimi**|Bilgi Engelleri özelliğinin yapılandırmasını ve raporlarını görüntüleyin.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Verileri Yöneticisi <br/><br/> Genel Okuyucu <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi <br/><br/> Güvenlik İşleci <br/><br/> Güvenlik Okuyucusu|
|**Yalnızca Görüntüleme Uyarılarını Yönetme**|Uyarıları Yönet özelliğinin yapılandırmasını ve raporlarını görüntüleyin.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Verileri Yöneticisi <br/><br/> Genel Okuyucu <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi <br/><br/> Güvenlik İşleci <br/><br/> Güvenlik Okuyucusu|
|**Yalnızca Görüntüleme Alıcıları**|Kullanıcılar ve gruplar hakkındaki bilgileri görüntüleyin.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Verileri Yöneticisi <br/><br/> Genel Okuyucu <br/><br/> MailFlow Yöneticisi <br/><br/> Kuruluş Yönetimi|
|**Yalnızca Görüntüleme Kaydı Yönetimi**|Kayıt yönetimi özelliğinin yapılandırmasını görüntüleyin.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Verileri Yöneticisi <br/><br/> <br/><br/> Genel Okuyucu <br/><br/> Kuruluş Yönetimi|
|**Yalnızca Görüntüleme Bekletme Yönetimi**|Bekletme ilkelerinin, bekletme etiketlerinin ve bekletme etiketi ilkelerinin yapılandırmasını görüntüleyin.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Verileri Yöneticisi <br/><br/> Genel Yönetici <br/><br/> Kuruluş Yönetimi|
