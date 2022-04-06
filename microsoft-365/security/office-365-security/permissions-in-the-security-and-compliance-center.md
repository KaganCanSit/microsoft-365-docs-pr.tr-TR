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
description: Yöneticiler, Güvenlik ve Uyumluluk Merkezi'nde bulunan izinler hakkında & bilgi Microsoft 365.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 79bc6c3e602a24b886fa47971f63e5e4012ff94f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468379"
---
# <a name="permissions-in-the-security--compliance-center"></a>Güvenlik ve Uyumluluk & İzinler

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Güvenlik & Uyumluluk Merkezi, cihaz yönetimi, veri kaybını önleme, eKbulma, bekletme gibi uyumluluk görevlerini gerçekleştiren kullanıcılara izinler vermenizi sağlar. Bu kişiler yalnızca onlara açıkça erişim izni vermekte olduğunuz görevleri gerçekleştirebilir. Güvenlik ve Uyumluluk & erişmek için, kullanıcıların bir veya birden çok Güvenlik ve Uyumluluk Merkezi rol grubunun genel yöneticisi veya & olması gerekir.

Güvenlik ve Uyumluluk &'deki izinler rol tabanlı erişim denetimi (RBAC) izin modelini temel almaktadır. RBAC, Exchange tarafından kullanılan izinlerle aynı izin modelidir, dolayısıyla Exchange'yi biliyorsanız, Güvenlik ve Uyumluluk Merkezi'nde izin & çok benzer olur. Ancak, rol gruplarının ve Güvenlik Exchange uyumluluk merkezi rol gruplarının üyelik veya & paylaşma olmadığını unutmamanız önemlidir. Her ikisinde de Kuruluş Yönetimi rol grubu varken, bunlar aynı değildir. Yaptıkları izinler ve rol gruplarının üyeleri farklıdır. Aşağıda Güvenlik ve Uyumluluk Merkezi & gruplarının listesi verilmiştir.

:::image type="content" source="../../media/992c20ca-e82e-497c-9c8d-6fab212deb80.png" alt-text="Güvenlik ve Uyumluluk Merkezi'nde & sayfası" lightbox="../../media/992c20ca-e82e-497c-9c8d-6fab212deb80.png":::

## <a name="relationship-of-members-roles-and-role-groups"></a>Üyelerin, rollerin ve rol gruplarının ilişkisi

Bir **rol** bir dizi görevi gerçekleştirme iznini, Örneğin, Olay Yönetimi rolü kişilerin eBulma servis servisleriyle çalışmasına olanak sağlar.

Rol **grubu,** kişilerin Güvenlik ve Uyumluluk Merkezi genelinde işlerini yapmalarına olanak sağlayan & kümesidir. Örneğin, Uyumluluk Yöneticisi rol grubu Büyük/Küçük Harf Yönetimi, İçerik Arama ve Kuruluş Yapılandırması rollerini (başka roller arasında) içerir, çünkü uyumluluk yöneticisi olan birinin işini yapmak için bu görevler için izinleri gerekir.

Güvenlik & Merkezi, kişi atamanız gereken en yaygın görevler ve işlevler için varsayılan rol gruplarını içerir. Tek tek kullanıcıları varsayılan rol **gruplarına üye** olarak eklemenizi öneririz.

:::image type="content" source="../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png" alt-text="Rol gruplarının roller ve üyelerle ilişkisi" lightbox="../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png":::

## <a name="role-groups-in-the-security--compliance-center"></a>Güvenlik ve Uyumluluk Merkezi'& rol grupları

Aşağıdaki tabloda, Güvenlik Ayarları Uyumluluk Merkezi'nde & varsayılan rol grupları ve varsayılan olarak rol gruplarına atanan roller listelemaktadır. Kullanıcıya uyumluluk görevi gerçekleştirme izinleri vermek için, onu uygun Güvenlik ve Uyumluluk Merkezi & grubuna ekleyin.

Güvenlik ve Uyumluluk Merkezi'& izinleri yönetme, kullanıcılara yalnızca Güvenlik ve Uyumluluk Merkezi'nin kendi içinde bulunan uyumluluk & verir. Exchange posta akış kuralları (aktarım kuralları olarak da bilinir) gibi, Güvenlik & Uyumluluk Merkezi'nde yer alan diğer uyumluluk özelliklerine izin vermek için Exchange yönetim merkezini (EAC) kullanabilirsiniz. Daha fazla bilgi için bkz. [Exchange Online](/exchange/permissions-exo/permissions-exo).

Güvenlik ve Uyumluluk Merkezi'ne erişim & için Kullanıcıların Uyumluluk Yönetim Merkezi'ne erişme izni [Microsoft 365 göz atabilirsiniz](grant-access-to-the-security-and-compliance-center.md).

> [!NOTE]
> Güvenlik ve **Uyumluluk** Merkezi'nde & görüntülemek için yönetici olmak gerekir. Özel olarak, Rol Yönetimi rolüne atanmış olması  gerekir ve bu rol varsayılan olarak yalnızca Güvenlik ve Uyumluluk Merkezi'nde  Kuruluş & rol grubuna atanır. Ayrıca, Rol **Yönetimi rolü kullanıcıların** rol gruplarını görüntülemesini, oluşturmalarını ve değiştirmelerini sağlar.

|Rol grubu|Açıklama|Atanan varsayılan roller|
|---|---|---|
|**Saldırı Benzetimi Yöneticileri**|Güvenlik ve Uyumluluk Merkezi'nde bu rol & kullanmayın. Azure AD'de ilgili rolü kullanın.|Saldırı Yöneticisi|
|**Saldırı Payload Yazarlarını Saldırı**|Güvenlik ve Uyumluluk Merkezi'nde bu rol & kullanmayın. Azure AD'de ilgili rolü kullanın.|Saldırı Payload Yazar|
|**İletişim Uyumluluğu**|Yönetici, analist, analist ve görüntüleyici gibi tüm iletişim uyumluluk rollerine izinler sağlar.|Vaka Yönetimi <br/><br/> İletişim Uyumluluğu Yöneticisi <br/><br/> İletişim Uyumluluğu Çözümlemesi <br/><br/> İletişim Uyumluluğu Olay Yönetimi <br/><br/> İletişim Uyumluluğu İncelemesi <br/><br/> İletişim Uyumluluğu Görüntüleyicisi <br/><br/> Veri Sınıflandırma Geri Bildirim Sağlayıcısı <br/><br/> Veri Bağlayıcısı Yöneticisi <br/><br/> View-Only Durumu|
|**İletişim Uyumluluğu Yöneticileri**|İlkeleri oluştur/düzenleyebilir ve genel ayarları tanımlayan iletişim uyumluluğu yöneticileri.|İletişim Uyumluluğu Yöneticisi <br/><br/> İletişim Uyumluluğu Olay Yönetimi <br/><br/> Veri Bağlayıcısı Yöneticisi|
|**İletişim Uyumluluğu Analistleri**|İlke eşleşmelerini araştıran, ileti meta verilerini görüntüleyabilen ve düzeltme eylemleri gerçekleştiren iletişim uyumluluğu analistleri.|İletişim Uyumluluğu Çözümlemesi <br/><br/> İletişim Uyumluluğu Olay Yönetimi|
|**İletişim Uyumluluğu Uyumluluk Uyumlulukları**|İlke eşleşmelerini araştıran, ileti içeriğini görüntüleyabilen ve düzeltme eylemleri gerçekleştiren iletişim uyumluluğu analistleri.|Vaka Yönetimi <br/><br/> İletişim Uyumluluğu Çözümlemesi <br/><br/> İletişim Uyumluluğu Olay Yönetimi <br/><br/> İletişim Uyumluluğu İncelemesi <br/><br/> Veri Sınıflandırma Geri Bildirim Sağlayıcısı <br/><br/> View-Only Durumu|
|**İletişim Uyumluluğu Görüntüleyicileri**|Kullanılabilir raporlara ve pencere öğelerine erişen iletişim uyumluluğunu görüntüleyen görüntüleyici.|İletişim Uyumluluğu Olay Yönetimi <br/><br/> İletişim Uyumluluğu Görüntüleyicisi|
|**Uyumluluk Yöneticisi1**<sup></sup>|Üyeler cihaz yönetimi, veri kaybı önleme, raporlar ve saklama ayarlarını yönetebilir.|Vaka Yönetimi <br/><br/> İletişim Uyumluluğu Yöneticisi <br/><br/> İletişim Uyumluluğu Olay Yönetimi <br/><br/> Uyumluluk Yöneticisi <br/><br/> Uyumluluk Araması <br/><br/> Veri Sınıflandırma Geri Bildirim Sağlayıcısı <br/><br/> Veri Sınıflandırma Geri Bildirimi Gözden Geçiren <br/><br/> Veri Bağlayıcısı Yöneticisi <br/><br/> Veri Araştırma Yönetimi <br/><br/> Cihaz Yönetimi <br/><br/> Disposition Management <br/><br/> DLP Uyumluluk Yönetimi <br/><br/> Bekle <br/><br/> IB Uyumluluk Yönetimi <br/><br/> Information Protection Yönetici <br/><br/> Information Protection Analisti <br/><br/> Information Protection Özel Information Protection <br/><br/> Information Protection Okuyucu <br/><br/> Insider Risk Yönetimi Yöneticisi <br/><br/> Uyarıları Yönetme <br/><br/> Kuruluş Yapılandırması <br/><br/> RecordManagement <br/><br/> Bekletme Yönetimi <br/><br/> View-Only Günlüklerini Denetleme <br/><br/> View-Only Durumu <br/><br/> View-Only Cihaz Yönetimi <br/><br/> View-Only DLP Uyumluluk Yönetimi <br/><br/> View-Only IB Uyumluluk Yönetimi <br/><br/> View-Only Yönetme <br/><br/> View-Only'i seçin <br/><br/> View-Only Kaydı Yönetimi <br/><br/> View-Only Bekletme Yönetimi|
|**Uyumluluk Veri Yöneticisi**|Üyeler cihaz yönetimi, veri koruması, veri kaybını önleme, raporlar ve saklama ayarlarını yönetebilir.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Araması <br/><br/> Veri Bağlayıcısı Yöneticisi <br/><br/> Cihaz Yönetimi <br/><br/> Disposition Management <br/><br/> DLP Uyumluluk Yönetimi <br/><br/> IB Uyumluluk Yönetimi <br/><br/> Information Protection Yönetici <br/><br/> Information Protection Analisti <br/><br/> Information Protection Özel Information Protection <br/><br/> Information Protection Okuyucu <br/><br/> Uyarıları Yönetme <br/><br/> Kuruluş Yapılandırması <br/><br/> RecordManagement <br/><br/> Bekletme Yönetimi <br/><br/> Duyarlılık Etiketi Yöneticisi <br/><br/> View-Only Günlüklerini Denetleme <br/><br/> View-Only Cihaz Yönetimi <br/><br/> View-Only DLP Uyumluluk Yönetimi <br/><br/> View-Only IB Uyumluluk Yönetimi <br/><br/> View-Only Yönetme <br/><br/> View-Only'i seçin <br/><br/> View-Only Kaydı Yönetimi <br/><br/> View-Only Bekletme Yönetimi|
|**Uyumluluk Yöneticisi Yöneticileri**|Şablon oluşturma ve değiştirme yönetme.|Uyumluluk Yöneticisi Yönetimi <br/><br/> Uyumluluk Yöneticisi Değerlendirmesi <br/><br/> Uyumluluk Yöneticisi Katkı <br/><br/> Uyumluluk Yöneticisi Okuyucu <br/><br/> Veri Bağlayıcısı Yöneticisi|
|**Uyumluluk Yöneticisi Değerlendirenler**|Değerlendirmeler oluşturun, geliştirme eylemleri gerçekleştirin ve geliştirme eylemleri için test durumunu güncelleştirin.|Uyumluluk Yöneticisi Değerlendirmesi <br/><br/> Uyumluluk Yöneticisi Katkı <br/><br/> Uyumluluk Yöneticisi Okuyucu <br/><br/> Veri Bağlayıcısı Yöneticisi|
|**Uyumluluk Yöneticisi Katkıda Bulunanlar**|Değerlendirmeler oluşturun ve geliştirme eylemleri gerçekleştirmek için çalışma gerçekleştirin.|Uyumluluk Yöneticisi Katkı <br/><br/> Uyumluluk Yöneticisi Okuyucu <br/><br/> Veri Bağlayıcısı Yöneticisi|
|**Uyumluluk Yöneticisi Okuyucuları**|Yönetici işlevleri dışında tüm Uyumluluk Yöneticisi içeriğini görüntüleme.|Uyumluluk Yöneticisi Okuyucu|
|**İçerik Gezgini İçerik Görüntüleyicisi**|İçerik gezgininde içerik dosyalarını görüntüleme.|Veri Sınıflandırma İçerik Görüntüleyicisi|
|**İçerik Gezgini Liste Görüntüleyicisi**|İçerik gezgininde yer alan tüm öğeleri yalnızca liste biçiminde görüntüler.|Veri Sınıflandırma Listesi Görüntüleyicisi|
|**Veri Kaynağı**|Posta kutularında, Çevrimiçi SharePoint ve posta kutularında OneDrive İş gerçekleştirin.|İletişim <br/><br/> Uyumluluk Araması <br/><br/> Custo bire bir <br/><br/> Veri Araştırma Yönetimi <br/><br/> Dışarı aktarma <br/><br/> Önizleme <br/><br/> Gözden geçirin <br/><br/> RMS Şifre Çözme <br/><br/> Arama ve Temizleme|
|**eBulma Yöneticisi**|Üyeler posta kutularında, çevrimiçi sitelerde ve farklı SharePoint yerinde arama ve OneDrive İş gerçekleştirebilirsiniz. Üyeler ayrıca eBulma servis durumlarını oluşturabilir ve yönetebilir, vakaya üye ekp kaldırabilir, vakayla ilişkili İçerik Aramaları oluşturabilir ve düzenleyebilir ve servis e-postalarında servis Advanced eDiscovery. <br/><br/> eBulma Yöneticisi, ek izinlerin atandığı eBulma Yöneticisi rol grubunun üyesidir. eBulma Yöneticisi'nin gerçekleştirebilir olduğu görevlere ek olarak, eBulma Yöneticisi şunları da gerçekleştirebilir:<ul><li>Kuruluşta tüm eBulma servis durumlarını görüntüleme.</li><li>eBulma olaylarını, kendilerini davanın üyesi olarak ekledikten sonra yönetin.</li></ul> <br/><br/> eBulma Yöneticisi ile eBulma Yöneticisi arasındaki en önemli fark, eBulma Yöneticisi'nin Güvenlik ve Uyumluluk Merkezi'nde **eBulma** örnekleri sayfasında listelenen tüm vakalara & sağlamaktır. eBulma yöneticisi yalnızca kendi oluşturduğu vakalara veya üyesi olduğu vakalara erişim sağlar. Bir kullanıcıyı eBulma Yöneticisi yapma hakkında daha fazla bilgi için bkz. Güvenlik ve Uyumluluk Merkezi'nde [eBulma & atama](../../compliance/assign-ediscovery-permissions.md).|Vaka Yönetimi <br/><br/> İletişim <br/><br/> Uyumluluk Araması <br/><br/> Custo bire bir <br/><br/> Dışarı aktarma <br/><br/> Bekle <br/><br/> Önizleme <br/><br/> Gözden geçirin <br/><br/> RMS Şifre Çözme|
|**Genel Okuyucu**|Üyeler raporlara, uyarılara salt okunur erişime sahip olur ve tüm yapılandırma ve ayarları görebilirler. <br/><br/> Genel Okuyucu ile Güvenlik Okuyucu arasındaki temel fark, Genel Okuyucu'nın yapılandırmaya ve **ayarlara erişmesidir**.|Güvenlik Okuyucu <br/><br/> Duyarlılık Etiket Okuyucusu <br/><br/> Hizmet Güvencesi Görünümü <br/><br/> View-Only Günlüklerini Denetleme <br/><br/> View-Only Cihaz Yönetimi <br/><br/> View-Only DLP Uyumluluk Yönetimi <br/><br/> View-Only IB Uyumluluk Yönetimi <br/><br/> View-Only Yönetme <br/><br/> View-Only'i seçin <br/><br/> View-Only Kaydı Yönetimi <br/><br/> View-Only Bekletme Yönetimi|
|**Information Protection**|Duyarlılık etiketleri ve ilkeleri, DLP, tüm sınıflayıcı türleri, etkinlik ve içerik explorer'ları ve tüm ilgili raporlar dahil olmak üzere tüm bilgi koruma özellikleri üzerinde tam denetim.|Veri Sınıflandırma İçerik Görüntüleyicisi <br/><br/> Information Protection Yönetici <br/><br/> Information Protection Analisti <br/><br/> Information Protection Özel Information Protection <br/><br/> Information Protection Okuyucu|
|**Information Protection Yöneticileri**|DLP ilkelerini, duyarlılık etiketlerini ve bunların ilkelerini ve tüm sınıflandırıcı türlerini oluşturun, düzenleyin ve silin. Otomatik etiketleme ilkeleri için uç nokta DLP ayarlarını ve benzetim modunu yönetin.|Information Protection Yönetici|
|**Information Protection Analistleri**|DLP uyarılarına ve etkinlik gezginine erişin ve bu uyarıları yönetin. DLP ilkelerine, duyarlılık etiketlerine ve ilkelerine ve tüm sınıflayıcı türlerine yalnızca görüntüleme erişimi.|Veri Sınıflandırma Listesi Görüntüleyicisi <br/><br/> Information Protection Analisti|
|**Information Protection'lar**|DLP uyarılarına, etkinlik gezginine ve içerik gezginine erişin ve bu uyarıları yönetin. DLP ilkelerine, duyarlılık etiketlerine ve ilkelerine ve tüm sınıflayıcı türlerine yalnızca görüntüleme erişimi.|Veri Sınıflandırma İçerik Görüntüleyicisi <br/><br/> Information Protection Analisti <br/><br/> Information Protection Özel Information Protection|
|**Information Protection Okuyucular**|DLP eğilimleri ve duyarlılık etiketleri ve ilkeleriyle ilgili raporlara yalnızca görüntüleme erişimi.|Information Protection Okuyucu|
|**Insider Risk Yönetimi**|Tek bir grupta, organizasyon için insider risk yönetimini yönetmek üzere bu rol grubunu kullanın. Belirlenen yöneticiler, analistler ve kullanıcı adayları için tüm kullanıcı hesaplarını ekleyerek, insider risk yönetimi izinlerini tek bir grupta yapılandırabilirsiniz. Bu rol grubu tüm Insider risk yönetimi izin rollerini içerir. Insider risk yönetimiyle hızlı bir şekilde çalışmaya başlamanın en kolay yolu budur ve ayrı kullanıcı grupları için tanımlanmış ayrı izinlere ihtiyacı olan kuruluşlara iyi uyum sağlar.|Vaka Yönetimi <br/><br/> Veri Bağlayıcısı Yöneticisi <br/><br/> Insider Risk Yönetimi Yöneticisi <br/><br/> Insider Risk Yönetimi Çözümlemesi <br/><br/> Insider Risk Yönetimi Denetimi <br/><br/> Insider Risk Yönetimi İncelemesi <br/><br/> Insider Risk Yönetimi Oturumları <br/><br/> View-Only Durumu|
|**Insider Risk Yönetimi Yöneticileri**|Başlangıçta Insider risk yönetimini yapılandırmak ve daha sonra insider risk yöneticilerini tanımlı bir grup haline azaltmak için bu rol grubunu kullanın. Bu rol grubunda yer alan kullanıcılar insider risk yönetimi ilkelerini, genel ayarları ve rol grubu atamalarını oluşturabilir, okuyabilir, güncelleştirilebilir ve silebilir.|Vaka Yönetimi <br/><br/> Veri Bağlayıcısı Yöneticisi <br/><br/> Insider Risk Yönetimi Yöneticisi <br/><br/> View-Only Durumu|
|**İçeriden Risk Yönetimi Analistleri**|Insider risk durumu analistleri gibi davranacak kullanıcılara izin atamak için bu grubu kullanın. Bu rol grubunda yer alan kullanıcılar tüm Insider risk yönetimi uyarılarına, vakalarına ve bildirim şablonlarına erişim sağlar. Insider riski olan İçerik Gezgini'ne erişamaz.|Vaka Yönetimi <br/><br/> Insider Risk Yönetimi Çözümlemesi <br/><br/> View-Only Durumu|
|**Insider Risk Yönetimi Denetçileri**|Insider risk yönetimi etkinliklerini denetlenecek kullanıcılara izin atamak için bu grubu kullanın. Bu rol grubunda yer alan kullanıcılar Insider risk denetim günlüğüne erişim sağlar.|Insider Risk Yönetimi Denetimi|
|**İçeriden Risk Yönetimi Araştırmacıları**|Insider risk verisi devam ediyor gibi davranacak kullanıcılara izin atamak için bu grubu kullanın. Bu rol grubunda yer alan kullanıcılar tüm Insider risk yönetimi uyarılarına, olaylarına, bildirim şablonlarına ve tüm durumlarda İçerik Gezgini'ne erişim sağlar.|Vaka Yönetimi <br/><br/> Insider Risk Yönetimi İncelemesi <br/><br/> View-Only Durumu|
|**Insider Risk Yönetimi Oturumu Onaylayanlar**|Oturum kaydı için grup değişikliği isteklerini yönetin.|Insider Risk Yönetimi Oturumları|
|**IRM Katkıda Bulunanları**|Bu rol grubu görünür, ancak yalnızca arka plan hizmetleri tarafından kullanılır.|Insider Risk Yönetimi Kalıcı katılım <br/><br/> Insider Risk Yönetimi Geçici katılım|
|**Bilgi Yöneticileri**|Bilgileri ve öğrenmeyi yapılandırma, eğitimleri ve diğer akıllı özellikleri atama.|Bilgi Yöneticisi|
|**MailFlow Yöneticisi**|Üyeler, Güvenlik ve Uyumluluk Merkezi'nde posta akışı içgörülerini ve raporlarını izleyebilir &  bakabilirsiniz. Genel yöneticiler bu gruba sıradan kullanıcılar ekleyebilir, ancak kullanıcı Exchange Yöneticisi grubunun üyesi değilse, kullanıcı yöneticiyle ilgili diğer görevlere Exchange erişebilirsiniz.|View-Only'i seçin|
|**Kuruluş Yönetimi1**<sup></sup>|Üyeler Güvenlik Ayarları Uyumluluk Merkezi'nde özelliklere erişim izinlerini & ayrıca cihaz yönetimi, veri kaybını önleme, raporlar ve saklama ayarlarını yönetebilir. <br/><br/> Genel yönetici olmadığınız kullanıcıların, Exchange Microsoft 365 (eski adı Mobil mobil cihaz veya MDM) tarafından yönetilen cihazları (eski adı Mobil Cihaz Yönetimi veya MDM) görmek ve bu cihazlarda eylemde yer almaları için yönetici olması gerekir. <br/><br/> Genel yöneticiler otomatik olarak bu rol grubuna üye olarak eklenir, ancak bunları Güvenlik ve Uyumluluk Merkezi PowerShell'in [Get-RoleGroupMember](/powershell/module/exchange/get-rolegroupmember) cmdlet'inin çıktısında [& göresiniz](/powershell/module/exchange/get-rolegroupmember).|Denetim Günlükleri <br/><br/> Vaka Yönetimi <br/><br/> İletişim Uyumluluğu Yöneticisi <br/><br/> İletişim Uyumluluğu Olay Yönetimi <br/><br/> Uyumluluk Yöneticisi <br/><br/> Uyumluluk Araması <br/><br/> Veri Bağlayıcısı Yöneticisi <br/><br/> Cihaz Yönetimi <br/><br/> DLP Uyumluluk Yönetimi <br/><br/> Bekle <br/><br/> IB Uyumluluk Yönetimi <br/><br/> Insider Risk Yönetimi Yöneticisi <br/><br/> Uyarıları Yönetme <br/><br/> Kuruluş Yapılandırması <br/><br/> Karantina <br/><br/> RecordManagement <br/><br/> Bekletme Yönetimi <br/><br/> Rol Yönetimi <br/><br/> Arama ve Temizleme <br/><br/> Güvenlik Yöneticisi <br/><br/> Güvenlik Okuyucu <br/><br/> Duyarlılık Etiketi Yöneticisi <br/><br/> Duyarlılık Etiket Okuyucusu <br/><br/> Hizmet Güvencesi Görünümü <br/><br/> Etiket Katkıda Bulunan <br/><br/> Etiket Yöneticisi <br/><br/> Etiket Okuyucu <br/><br/> View-Only Günlüklerini Denetleme <br/><br/> View-Only Cihaz Yönetimi <br/><br/> View-Only DLP Uyumluluk Yönetimi <br/><br/> View-Only IB Uyumluluk Yönetimi <br/><br/> View-Only Durumu <br/><br/> View-Only Yönetme <br/><br/> View-Only'i seçin <br/><br/> View-Only Kaydı Yönetimi <br/><br/> View-Only Bekletme Yönetimi|
|**Gizlilik Yönetimi**|Aşağıdaki bağlantıda Priva için erişim Microsoft 365 uyumluluk merkezi.|Vaka Yönetimi <br/><br/> Veri Sınıflandırma İçerik Görüntüleyicisi <br/><br/> Veri Sınıflandırma Listesi Görüntüleyicisi <br/><br/> Gizlilik Yönetimi Yöneticisi <br/><br/> Gizlilik Yönetimi Çözümlemesi <br/><br/> Gizlilik Yönetimi İncelemesi <br/><br/> Gizlilik Yönetimi Kalıcı katılım <br/><br/> Gizlilik Yönetimi Geçici katkı <br/><br/> Gizlilik Yönetimi Görüntüleyicisi <br/><br/> Konu Hakları İsteği Yöneticisi <br/><br/> View-Only Durumu|
|**Gizlilik Yönetimi Yöneticileri**|İlkeleri oluştur/düzenleyebilir ve genel ayarları tanımlayan gizlilik yönetimi çözümünün yöneticileri.|Vaka Yönetimi <br/><br/> Gizlilik Yönetimi Yöneticisi <br/><br/> View-Only Durumu|
|**Gizlilik Yönetimi Analistleri**|İlke eşleşmelerini araştıran, iletilerin meta verilerini görüntüleyabilen ve düzeltme eylemleri gerçekleştiren gizlilik yönetimi çözümünün analistleri.|Vaka Yönetimi <br/><br/> Veri Sınıflandırma Listesi Görüntüleyicisi <br/><br/> Gizlilik Yönetimi Çözümlemesi <br/><br/> View-Only Durumu|
|**Gizlilik Yönetimi Katkıda Bulunanlar**|Gizlilik yönetimi davaları için katılımcı erişimini yönetin.|Gizlilik Yönetimi Kalıcı katılım <br/><br/> Gizlilik Yönetimi Geçici katkı|
|**Gizlilik Yönetimi Özel Ekipler**|İlke eşleşmelerini ince alabilen, ileti içeriğini görüntüleyabilen ve düzeltme eylemleri gerçekleştiren bir gizlilik yönetimi çözümüne sahip olan bir sorun.|Vaka Yönetimi <br/><br/> Veri Sınıflandırma İçerik Görüntüleyicisi <br/><br/> Veri Sınıflandırma Listesi Görüntüleyicisi <br/><br/> Gizlilik Yönetimi İncelemesi <br/><br/> View-Only Durumu|
|**Gizlilik Yönetimi Görüntüleyicileri**|Kullanılabilir panolara ve pencere öğelerine erişen gizlilik yönetimi çözümünün görüntüleyicisi.|Veri Sınıflandırma Listesi Görüntüleyicisi <br/><br/> Gizlilik Yönetimi Görüntüleyicisi|
|**Karantina Yöneticisi**|Üyeler tüm Karantina eylemlerine erişim sağlar. Daha fazla bilgi için bkz [. EOP'de yönetici olarak karantinaya alınmış iletileri ve dosyaları yönetme](manage-quarantined-messages-and-files.md)|Karantina|
|**Kayıt Yönetimi**|Üyeler, bekletme etiketleri ve konumlandırma incelemeleri de içinde olmak üzere kayıt yönetimini her açıdan yapılandırabilirsiniz.|Disposition Management <br/><br/> RecordManagement <br/><br/> Bekletme Yönetimi|
|**Gözden geçiren**|Üyeler her durumda gözden geçirme [kümelerine Advanced eDiscovery](../../compliance/overview-ediscovery-20.md) erişin. Bu rol grubunun üyeleri, üyesi olduğu **grup sayfasındaki eBulma >** Gelişmiş sayfasında vakaların listesini Microsoft 365 uyumluluk merkezi ve açabilirler. Kullanıcı çalışma durumuna erişdikten Advanced eDiscovery büyük/harfe erişmek için **Kümeleri gözden geçir'i** seçer. Bu rol, kullanıcının olayla ilişkilendirilmiş koleksiyon aramalarının sonuçlarını önizlemesine veya başka arama ya da olay yönetimi görevleri gerçekleştirmesine izin vermez. Bu rol grubunun üyeleri yalnızca gözden geçirme kümesinde yer alan verilere erişim sağlar.|Gözden geçirin|
|**Güvenlik Yöneticisi**|Üyeler Kimlik Koruma Merkezi, Kimlik Koruma Merkezi, Güvenlik güvenlik özelliklerine Privileged Identity Management, Microsoft 365 Durumunu İzleme ve Uyumluluk Merkezi'& erişim iznine sahiptir. <br/><br/> Varsayılan olarak, bu rol grubunun hiç üyesi yok gibi görünebilir. Bununla birlikte, her Azure Active Directory Güvenlik Yöneticisi rolü bu rol grubuna atanır. Bu nedenle, bu rol grubu Güvenlik Yöneticisi rolünün özelliklerini ve üyeliğini Azure Active Directory. <br/><br/> İzinleri merkezi olarak yönetmek için, yönetim merkezinde grup üyelerini Azure Active Directory kaldırın. Daha fazla bilgi için [bkz. Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference). Bu rol grubunu Güvenlik ve Uyumluluk Merkezi'& (üyelik veya roller) düzenlersanız, bu değişiklikler yalnızca Güvenlik & Uyumluluk Merkezi için geçerli olup diğer hizmetler için geçerli değildir. <br/><br/> Bu rol grubu, Güvenlik okuyucu rolünün tüm salt okunur izinlerini ve ayrıca aynı hizmetler için bir dizi ek yönetim iznini içerir: Azure Information Protection, Kimlik Koruma Merkezi, Privileged Identity Management, İzleme Microsoft 365  Hizmet Durumu ve Güvenlik & Merkezi.|Denetim Günlükleri <br/><br/> Cihaz Yönetimi <br/><br/> DLP Uyumluluk Yönetimi <br/><br/> IB Uyumluluk Yönetimi <br/><br/> Uyarıları Yönetme <br/><br/> Karantina <br/><br/> Güvenlik Yöneticisi <br/><br/> Duyarlılık Etiketi Yöneticisi <br/><br/> Etiket Katkıda Bulunan <br/><br/> Etiket Yöneticisi <br/><br/> Etiket Okuyucu <br/><br/> View-Only Günlüklerini Denetleme <br/><br/> View-Only Cihaz Yönetimi <br/><br/> View-Only DLP Uyumluluk Yönetimi <br/><br/> View-Only IB Uyumluluk Yönetimi <br/><br/> View-Only Yönetme|
|**Güvenlik İşleci**|Üyeler güvenlik uyarılarını yönetebilir ve güvenlik özellikleriyle ilgili raporları ve ayarları  bakabilirsiniz.|Uyumluluk Araması <br/><br/> Uyarıları Yönetme <br/><br/> Güvenlik Okuyucu <br/><br/> Etiket Katkıda Bulunan <br/><br/> Etiket Okuyucu <br/><br/> Tenant AllowBlockList Manager <br/><br/> View-Only Günlüklerini Denetleme <br/><br/> View-Only Cihaz Yönetimi <br/><br/> View-Only DLP Uyumluluk Yönetimi <br/><br/> View-Only IB Uyumluluk Yönetimi <br/><br/> View-Only Yönetme|
|**Güvenlik Okuyucu**|Üyeler Kimlik Koruma Merkezi, Kimlik Koruma Merkezi, Kimlik Doğrulama Merkezi, Güvenlik Privileged Identity Management, Güvenlik Microsoft 365'nin ve Uyumluluk Merkezi'nin bir dizi güvenlik özelliğine & erişim iznine sahiptir. <br/><br/> Varsayılan olarak, bu rol grubunun hiç üyesi yok gibi görünebilir. Ancak, bu rol grubuna Azure Active Directory Okuyucu'dan Güvenlik Okuyucusu rolü atanır. Bu nedenle, bu rol grubu Güvenlik Okuyucusu rolünün özelliklerini ve üyeliğini Azure Active Directory. <br/><br/> İzinleri merkezi olarak yönetmek için, yönetim merkezinde grup üyelerini Azure Active Directory kaldırın. Daha fazla bilgi için [bkz. Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference). Bu rol grubunu Güvenlik ve Uyumluluk Merkezi'& (üyelik veya roller) düzenlersanız, bu değişiklikler yalnızca Güvenlik & Uyumluluk Merkezi için geçerli olup diğer hizmetler için geçerli değildir.|Güvenlik Okuyucu <br/><br/> Duyarlılık Etiket Okuyucusu <br/><br/> Etiket Okuyucu <br/><br/> View-Only Cihaz Yönetimi <br/><br/> View-Only DLP Uyumluluk Yönetimi <br/><br/> View-Only IB Uyumluluk Yönetimi <br/><br/> View-Only Yönetme|
|**Hizmet Güvencesi Kullanıcısı**|Üyeler, Güvenlik ve Uyumluluk Merkezi'nin Hizmet & erişebilirsiniz. Hizmet güvencesi, Microsoft'un müşteri verisinde depolanan müşteri verileriyle ilgili uygulamalarını tanımlayan raporlar ve Microsoft 365. Ayrıca, üçüncü taraf denetim raporlarında bağımsız üçüncü taraf denetim Microsoft 365. Daha fazla bilgi için Güvenlik [ve Uyumluluk Merkezi'nde hizmet & bakın](../../compliance/service-assurance.md).|Hizmet Güvencesi Görünümü|
|**Konu Hakları İsteği Yöneticileri**|Konu hakları istekleri oluşturun.|Vaka Yönetimi <br/><br/> Konu Hakları İsteği Yöneticisi <br/><br/> View-Only Durumu|
|**Gözetmen İncelemesi**|Üyeler, kuruluşta hangi iletişimlerin gözden geçir define ilkelerini oluşturabilir ve yönetebilir. Daha fazla bilgi için bkz [. Organizasyonunız için iletişim uyumluluk ilkelerini yapılandırma](../../compliance/communication-compliance-configure.md).|Gözetmen İnceleme Yöneticisi|

> [!NOTE]
> <sup>1</sup> Bu rol grubu, üyelere denetim günlüğünde arama yapmak veya DLP veya rapor gibi veri Exchange raporları kullanmak için gereken izinleri Office 365 için Defender değil. Denetim günlüğünde arama yapmak veya tüm raporları görüntülemek için, kullanıcıya tüm raporlarda izin Exchange Online. Çünkü, denetim günlüğünde arama yapmak için kullanılan temel cmdlet, bir Exchange Online cmdlet'tir. Genel yöneticiler denetim günlüğünde arama yapın ve tüm raporları sınyınlar, otomatik olarak Denetim Merkezi'nin Kuruluş Yönetimi rol grubuna üye olarak Exchange Online. Daha fazla bilgi için [bkz. Güvenlik ve Uyumluluk Merkezi'nde denetim & arama.](../../compliance/search-the-audit-log-in-security-and-compliance.md)

## <a name="roles-in-the-security--compliance-center"></a>Güvenlik ve Uyumluluk & rolleri

Aşağıdaki tabloda, varsayılan olarak atandığı kullanılabilir roller ve rol grupları listeledir.

Aşağıdaki rollerin varsayılan olarak Kuruluş Yönetimi rol grubuna atanmamış olduğunu unutmayın:

- Saldırı Yöneticisi
- Saldırı Payload Yazar
- İletişim
- İletişim Uyumluluğu Çözümlemesi
- İletişim Uyumluluğu İncelemesi
- İletişim Uyumluluğu Görüntüleyicisi
- Uyumluluk Yöneticisi Yönetimi
- Uyumluluk Yöneticisi Değerlendirmesi
- Uyumluluk Yöneticisi Katkı
- Uyumluluk Yöneticisi Okuyucu
- Custo bire bir
- Veri Sınıflandırma İçerik Görüntüleyicisi
- Veri Sınıflandırma Geri Bildirim Sağlayıcısı
- Veri Sınıflandırma Geri Bildirimi Gözden Geçiren
- Veri Sınıflandırma Listesi Görüntüleyicisi
- Veri Araştırma Yönetimi
- Disposition Management
- Dışarı aktarma
- Information Protection Yönetici
- Information Protection Analisti
- Information Protection Özel Information Protection
- Information Protection Okuyucu
- Insider Risk Yönetimi Çözümlemesi
- Insider Risk Yönetimi Denetimi
- Insider Risk Yönetimi İncelemesi
- Insider Risk Yönetimi Kalıcı katılım
- Insider Risk Yönetimi Oturumları
- Insider Risk Yönetimi Geçici katılım
- Bilgi Yöneticisi
- Önizleme
- Gizlilik Yönetimi Yöneticisi
- Gizlilik Yönetimi Çözümlemesi
- Gizlilik Yönetimi İncelemesi
- Gizlilik Yönetimi Kalıcı katılım
- Gizlilik Yönetimi Geçici katkı
- Gizlilik Yönetimi Görüntüleyicisi
- Gözden geçirin
- RMS Şifre Çözme
- Konu Hakları İsteği Yöneticisi
- Gözetmen İnceleme Yöneticisi
- Tenant AllowBlockList Manager

|Rol|Açıklama|Varsayılan rol grubu atamaları|
|---|---|---|
|**Saldırı Yöneticisi**|Bu rolü Güvenlik ve Uyumluluk Merkezi'& kullanmayın. Azure AD'de ilgili rolü kullanın.|Saldırı Yöneticisi|
|**Saldırı Payload Yazar**|Bu rolü Güvenlik ve Uyumluluk Merkezi'& kullanmayın. Azure AD'de ilgili rolü kullanın.|Saldırı Payload Yazarlarını Saldırı|
|**Denetim Günlükleri**|Kuruluş için denetimi açın ve yapılandırın, kuruluşun denetim raporlarını görüntüden açın ve yapılandırın, sonra da bu raporları bir dosyaya aktarın.|Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi|
|**Vaka Yönetimi**|eBulma olaylarına erişimi oluşturun, düzenleyin, silin ve kontrol altından silin.|İletişim Uyumluluğu <br/><br/> İletişim Uyumluluğu Uyumluluk Uyumlulukları <br/><br/> Uyumluluk Yöneticisi <br/><br/> eBulma Yöneticisi <br/><br/> Insider Risk Yönetimi <br/><br/> Insider Risk Yönetimi Yöneticileri <br/><br/> İçeriden Risk Yönetimi Analistleri <br/><br/> İçeriden Risk Yönetimi Araştırmacıları <br/><br/> Kuruluş Yönetimi <br/><br/> Gizlilik Yönetimi <br/><br/> Gizlilik Yönetimi Yöneticileri <br/><br/> Gizlilik Yönetimi Analistleri <br/><br/> Gizlilik Yönetimi Özel Ekipler <br/><br/> Konu Hakları İsteği Yöneticileri|
|**İletişim**|Bir dava durumunda tanımlanan koruyucularla olan tüm Advanced eDiscovery yönetin.  Tutma bildirimleri, anımsatıcılar tutma ve yönetime yükseltmeler oluşturma. Custo custo custknowledgment of hold notifications and manage access to the custo portal that is used by each custo custo veri portalında to track communications for the cases they were be custo cust.|Veri Kaynağı <br/><br/> eBulma Yöneticisi|
|**İletişim Uyumluluğu Yöneticisi**|İletişim Uyumluluğu özelliğinde ilkeleri yönetmek için kullanılır.|İletişim Uyumluluğu <br/><br/> İletişim Uyumluluğu Yöneticileri <br/><br/> Uyumluluk Yöneticisi <br/><br/> Kuruluş Yönetimi|
|**İletişim Uyumluluğu Çözümlemesi**|İletişim Uyumluluğu özelliğinde ileti ihlallerinin düzeltmesi ve araştırma yapmak için kullanılır. İleti meta verileri yalnızca iletiyi  görüntüde olabilir.|İletişim Uyumluluğu <br/><br/> İletişim Uyumluluğu Analistleri <br/><br/> İletişim Uyumluluğu Uyumluluk Uyumlulukları|
|**İletişim Uyumluluğu Olay Yönetimi**|İletişim Uyumluluğu durumlarına erişmek için kullanılır.|İletişim Uyumluluğu <br/><br/> İletişim Uyumluluğu Yöneticileri <br/><br/> İletişim Uyumluluğu Analistleri <br/><br/> İletişim Uyumluluğu Uyumluluk Uyumlulukları <br/><br/> İletişim Uyumluluğu Görüntüleyicileri <br/><br/> Uyumluluk Yöneticisi <br/><br/> Kuruluş Yönetimi|
|**İletişim Uyumluluğu İncelemesi**|İletişim Uyumluluğu özelliğinde ileti ihlallerini araştırma, düzeltme ve gözden geçirmek için kullanılır. İleti meta verilerini ve iletiyi iletiyi iletiyi  görüntüleme.|İletişim Uyumluluğu <br/><br/> İletişim Uyumluluğu Uyumluluk Uyumlulukları|
|**İletişim Uyumluluğu Görüntüleyicisi**|İletişim Uyumluluğu özelliğinde raporlara ve pencere öğelerine erişmek için kullanılır.|İletişim Uyumluluğu <br/><br/> İletişim Uyumluluğu Görüntüleyicileri|
|**Uyumluluk Yöneticisi**|Uyumluluk özellikleri için ayarları ve raporları görüntüleyemez ve düzenleyebilirsiniz.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Kuruluş Yönetimi|
|**Uyumluluk Yöneticisi Yönetimi**|Şablon oluşturma ve değiştirme yönetme.|Uyumluluk Yöneticisi Yöneticileri|
|**Uyumluluk Yöneticisi Değerlendirmesi**|Değerlendirmeler oluşturun, geliştirme eylemleri gerçekleştirin ve geliştirme eylemleri için test durumunu güncelleştirin.|Uyumluluk Yöneticisi Yöneticileri <br/><br/> Uyumluluk Yöneticisi Değerlendirenler|
|**Uyumluluk Yöneticisi Katkı**|Değerlendirmeler oluşturun ve geliştirme eylemleri gerçekleştirmek için çalışma gerçekleştirin.|Uyumluluk Yöneticisi Yöneticileri <br/><br/> Uyumluluk Yöneticisi Değerlendirenler <br/><br/> Uyumluluk Yöneticisi Katkıda Bulunanlar|
|**Uyumluluk Yöneticisi Okuyucu**|Yönetici işlevleri dışında tüm Uyumluluk Yöneticisi içeriğini görüntüleme.|Uyumluluk Yöneticisi Yöneticileri <br/><br/> Uyumluluk Yöneticisi Değerlendirenler <br/><br/> Uyumluluk Yöneticisi Katkıda Bulunanlar <br/><br/> Uyumluluk Yöneticisi Okuyucuları|
|**Uyumluluk Araması**|Posta kutularında arama gerçekleştirin ve sonuçlar hakkında tahmin alın.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Veri Kaynağı <br/><br/> eBulma Yöneticisi <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik İşleci|
|**Custo bire bir**|Özel durumlar için koruyucuları Advanced eDiscovery yönetin ve koruyucularla ilişkilendirilmiş veri kaynaklarını bulmak için Azure Active Directory ve diğer kaynaklardan gelen bilgileri kullanın. Posta kutuları, posta kutuları ve site SharePoint diğer veri kaynaklarını Teams durumda koruyucularla ilişkilendirme.  Bir dava bağlamında içeriği korumak için koruyucularla ilişkilendirilmiş veri kaynaklarını yasal olarak basılı tutun.|Veri Kaynağı <br/><br/> eBulma Yöneticisi|
|**Veri Sınıflandırma İçerik Görüntüleyicisi**|İçerik Gezgini'nde dosyaların yerinde işlemeyi görüntüleme.|İçerik Gezgini İçerik Görüntüleyicisi <br/><br/> Information Protection <br/><br/> Information Protection'lar <br/><br/> Gizlilik Yönetimi <br/><br/> Gizlilik Yönetimi Özel Ekipler|
|**Veri Sınıflandırma Geri Bildirim Sağlayıcısı**|İçerik gezgininde sınıflayıcılara geri bildirim sağlar.|İletişim Uyumluluğu <br/><br/> İletişim Uyumluluğu Uyumluluk Uyumlulukları <br/><br/> Uyumluluk Yöneticisi|
|**Veri Sınıflandırma Geri Bildirimi Gözden Geçiren**|Geri bildirim gezgininde sınıflayıcılardan gelen geri bildirimleri gözden geçirmeyi sağlar.|Uyumluluk Yöneticisi|
|**Veri Sınıflandırma Listesi Görüntüleyicisi**|İçerik gezgininde dosyaların listesini görüntüleme.|İçerik Gezgini Liste Görüntüleyicisi <br/><br/> Information Protection Analistleri <br/><br/> Gizlilik Yönetimi <br/><br/> Gizlilik Yönetimi Analistleri <br/><br/> Gizlilik Yönetimi Özel Ekipler <br/><br/> Gizlilik Yönetimi Görüntüleyicileri|
|**Veri Bağlayıcısı Yöneticisi**|Microsoft dışı verileri kendi verilerinize aktararak veya arşivlerken bağlayıcıları Microsoft 365.|İletişim Uyumluluğu <br/><br/> İletişim Uyumluluğu Yöneticileri <br/><br/> Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Uyumluluk Yöneticisi Yöneticileri <br/><br/> Uyumluluk Yöneticisi Değerlendirenler <br/><br/> Uyumluluk Yöneticisi Katkıda Bulunanlar <br/><br/> Insider Risk Yönetimi <br/><br/> Insider Risk Yönetimi Yöneticileri <br/><br/> Kuruluş Yönetimi|
|**Veri Araştırma Yönetimi**|Veri araştırması oluşturma, düzenleme, silme ve erişimi denetleme.|Uyumluluk Yöneticisi <br/><br/> Veri Kaynağı|
|**Cihaz Yönetimi**|Cihaz yönetimi özellikleriyle ilgili ayarları ve raporları görüntüleyemez ve düzenleyebilirsiniz.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi|
|**Disposition Management**|Güvenlik ve Uyumluluk Merkezi'nde El ile Disposition'a erişim & denetleyin.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Kayıt Yönetimi|
|**DLP Uyumluluk Yönetimi**|Veri kaybı önleme (DLP) ilkeleriyle ilgili ayarları ve raporları  görüntüleyemez ve düzenleyebilirsiniz.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi|
|**Dışarı aktarma**|Aramalardan döndürülen posta kutusunu ve site içeriğini dışarı aktarın.|Veri Kaynağı <br/><br/> eBulma Yöneticisi|
|**Bekle**|Posta kutularına, sitelere ve ortak klasörlere içerik yerinde tutun. Saklanan içeriğin bir kopyası güvenli bir konumda depolanır. İçerik sahipleri, özgün içeriği değiştirmeye veya silebilir.|Uyumluluk Yöneticisi <br/><br/> eBulma Yöneticisi <br/><br/> Kuruluş Yönetimi|
|**IB Uyumluluk Yönetimi**|Bilgi Engeli ilkelerini görüntüleme, oluşturma, kaldırma, değiştirme ve test edin.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi|
|**Information Protection Yönetici**|DLP ilkelerini, duyarlılık etiketlerini ve bunların ilkelerini ve tüm sınıflandırıcı türlerini oluşturun, düzenleyin ve silin. Otomatik etiketleme ilkeleri için uç nokta DLP ayarlarını ve benzetim modunu yönetin.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Information Protection <br/><br/> Information Protection Yöneticileri|
|**Information Protection Analisti**|DLP uyarılarına ve etkinlik gezginine erişin ve bu uyarıları yönetin. DLP ilkelerine, duyarlılık etiketlerine ve ilkelerine ve tüm sınıflayıcı türlerine yalnızca görüntüleme erişimi.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Information Protection <br/><br/> Information Protection Analistleri <br/><br/> Information Protection'lar|
|**Information Protection Özel Information Protection**|DLP uyarılarına, etkinlik gezginine ve içerik gezginine erişin ve bu uyarıları yönetin. DLP ilkelerine, duyarlılık etiketlerine ve ilkelerine ve tüm sınıflayıcı türlerine yalnızca görüntüleme erişimi.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Information Protection <br/><br/> Information Protection'lar|
|**Information Protection Okuyucu**|DLP ilkeleri ve duyarlılık etiketleri ve bunların ilkeleri için raporlara yalnızca görüntüleme erişimi.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Information Protection <br/><br/> Information Protection Okuyucular|
|**Insider Risk Yönetimi Yöneticisi**|Insider Risk Yönetimi özelliğine erişimi oluşturun, düzenleyin, silin ve kontrol altınain.|Uyumluluk Yöneticisi <br/><br/> Insider Risk Yönetimi <br/><br/> Insider Risk Yönetimi Yöneticileri <br/><br/> Kuruluş Yönetimi|
|**Insider Risk Yönetimi Çözümlemesi**|Tüm Insider risk yönetimi uyarılarına, olaylarına ve bildirim şablonlarına erişin.|Insider Risk Yönetimi <br/><br/> İçeriden Risk Yönetimi Analistleri|
|**Insider Risk Yönetimi Denetimi**|Insider Riski denetim izleri görüntülemeye izin ver.|Insider Risk Yönetimi <br/><br/> Insider Risk Yönetimi Denetçileri|
|**Insider Risk Yönetimi İncelemesi**|Tüm insider risk yönetimi uyarılarına, olaylarına, bildirim şablonlarına ve her durumda İçerik Gezgini'ne erişin.|Insider Risk Yönetimi <br/><br/> İçeriden Risk Yönetimi Araştırmacıları|
|**Insider Risk Yönetimi Kalıcı katılım**|Bu rol grubu görünür, ancak yalnızca arka plan hizmetleri tarafından kullanılır.|IRM Katkıda Bulunanları|
|**Insider Risk Yönetimi Oturumları**|Oturum kaydı için grup değişikliği isteklerini yönetmeye izin ver.|Insider Risk Yönetimi <br/><br/> Insider Risk Yönetimi Oturumu Onaylayanlar|
|**Insider Risk Yönetimi Geçici katılım**|Bu rol grubu görünür, ancak yalnızca arka plan hizmetleri tarafından kullanılır.|IRM Katkıda Bulunanları|
|**Bilgi Yöneticisi**|Bilgileri ve öğrenmeyi yapılandırma, eğitimleri ve diğer akıllı özellikleri atama.|Bilgi Yöneticileri|
|**Uyarıları Yönetme**|Uyarılar için ayarları ve raporları görüntüleme ve düzenleme.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi <br/><br/> Güvenlik İşleci|
|**Kuruluş Yapılandırması**|Denetim raporlarını çalıştırın, görüntüden dışarı aktarın ve DLP, cihazlar ve saklama için uyumluluk ilkelerini yönetin.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Kuruluş Yönetimi|
|**Önizleme**|İçerik aramalarından döndürülen öğelerin listesini görüntüleme ve içeriği görüntülemek için listeden her öğeyi açma.|Veri Kaynağı <br/><br/> eBulma Yöneticisi|
|**Gizlilik Yönetimi Yöneticisi**|Gizlilik Yönetimi'nin ilkelerini yönetin ve çözümün tüm işlevlerine erişim iznine sahip olur.|Gizlilik Yönetimi <br/><br/> Gizlilik Yönetimi Yöneticileri|
|**Gizlilik Yönetimi Çözümlemesi**|Gizlilik Yönetimi'de ileti ihlaliyle ilgili araştırma ve düzeltmeler gerçekleştirin. yalnızca ileti meta verilerini  görüntüler.|Gizlilik Yönetimi <br/><br/> Gizlilik Yönetimi Analistleri|
|**Gizlilik Yönetimi İncelemesi**|Gizlilik Yönetimi'de araştırma, düzeltme ve ileti ihlallerini gözden geçirme. İleti meta verilerini ve tüm iletiyi  görüntüleme.|Gizlilik Yönetimi <br/><br/> Gizlilik Yönetimi Özel Ekipler|
|**Gizlilik Yönetimi Kalıcı katılım**|Kalıcı katılımcı olarak Access Gizlilik Yönetimi davaları.|Gizlilik Yönetimi <br/><br/> Gizlilik Yönetimi Katkıda Bulunanlar|
|**Gizlilik Yönetimi Geçici katkı**|Geçici katılımcı olarak Gizlilik Yönetimi davalarına erişin.|Gizlilik Yönetimi <br/><br/> Gizlilik Yönetimi Katkıda Bulunanlar|
|**Gizlilik Yönetimi Görüntüleyicisi**|Gizlilik Yönetimi'den panolara ve pencere öğelerine erişin.|Gizlilik Yönetimi <br/><br/> Gizlilik Yönetimi Görüntüleyicileri|
|**Karantina**|Karantinaya alınmış e-postaları görüntülemeye ve bırakmaya izin verir.|Karantina Yöneticisi <br/><br/> Güvenlik Yöneticisi <br/><br/> Kuruluş Yönetimi|
|**RecordManagement**|Kayıt yönetimi özelliğinin yapılandırmasını görüntüleme ve düzenleme.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Kuruluş Yönetimi <br/><br/> Kayıt Yönetimi|
|**Bekletme Yönetimi**|Bekletme ilkelerini, bekletme etiketlerini ve bekletme etiketi ilkelerini yönetin.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Kuruluş Yönetimi <br/><br/> Kayıt Yönetimi|
|**Gözden geçirin**|Bu rol, kullanıcıların her durumda gözden geçirme kümelerine erişmesini Advanced eDiscovery sağlar. Bu role atanan kullanıcılar, üyesi olduğu **eBulma sayfasındaki eBulma > Gelişmiş** sayfasında vakaların listesini Microsoft 365 uyumluluk merkezi ve açabilirler. Kullanıcı çalışma durumuna erişdikten Advanced eDiscovery büyük/harfe erişmek için **Kümeleri gözden geçir'i** seçer. Bu rol, kullanıcının olayla ilişkilendirilmiş koleksiyon aramalarının sonuçlarını önizlemesine veya başka arama ya da olay yönetimi görevleri gerçekleştirmesine izin vermez. Bu role sahip kullanıcılar yalnızca gözden geçirme kümesinde yer alan verilere erişim sağlar.|Veri Kaynağı <br/><br/> eBulma Yöneticisi <br/><br/> Gözden geçiren|
|**RMS Şifre Çözme**|Arama sonuçlarını dışarı aktararak RMS korumalı içeriğin şifresini çözme.|Veri Kaynağı <br/><br/> eBulma Yöneticisi|
|**Rol Yönetimi**|Rol grubu üyeliğini yönetin ve özel rol gruplarını oluşturun veya silin.|Kuruluş Yönetimi|
|**Arama ve Temizleme**|Kişilerin içerik arama ölçütlerine uyan verileri toplu olarak kaldırmalarına olanak verir.|Veri Kaynağı <br/><br/> Kuruluş Yönetimi|
|**Güvenlik Yöneticisi**|Güvenlik özellikleri için yapılandırmayı ve raporları görüntüleyemez ve düzenleyebilirsiniz.|Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi|
|**Güvenlik Okuyucu**|Güvenlik özellikleri için yapılandırmayı ve raporları görüntüleme.|Genel Okuyucu <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik İşleci <br/><br/> Güvenlik Okuyucu|
|**Duyarlılık Etiketi Yöneticisi**|Duyarlılık etiketlerini görüntüleme, oluşturma, değiştirme ve kaldırma.|Uyumluluk Veri Yöneticisi <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi|
|**Duyarlılık Etiket Okuyucusu**|Duyarlılık etiketlerinin yapılandırmasını ve kullanımını görüntüleme.|Genel Okuyucu <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik Okuyucu|
|**Hizmet Güvencesi Görünümü**|Hizmet Güvencesi bölümünden kullanılabilir belgeleri indirin. İçerik, yasal düzenlemelere uyumluluk ve güvenlik risklerini yönetmek için bağımsız denetim, uyumluluk Microsoft 365 güvenlik risklerini yönetmek için güvenlikle ilgili rehberlik içerir.|Genel Okuyucu <br/><br/> Kuruluş Yönetimi <br/><br/> Hizmet Güvencesi Kullanıcısı|
|**Gözetmen İnceleme Yöneticisi**|Gözden geçirmesi gereken iletişimler ve incelemeyi kimin yapması gerektiği dahil olmak üzere gözetmen inceleme ilkelerini yönetin.|Gözetmen İncelemesi|
|**Etiket Katkıda Bulunan**|Mevcut kullanıcı etiketlerinin üyeliğini görüntüleme ve güncelleştirme.|Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi <br/><br/> Güvenlik İşleci|
|**Etiket Yöneticisi**|Kullanıcı etiketlerini görüntüleme, güncelleştirme, oluşturma ve silme.|Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi|
|**Etiket Okuyucu**|Var olan kullanıcı etiketlerine salt okunur erişim.|Güvenlik Okuyucu|
|**Tenant AllowBlockList Manager**|Kiracı izin ver engelleme listesi ayarlarını yönetin.|Güvenlik İşleci|
|**Yalnızca görüntülemeli Denetim Günlükleri**|Denetim raporlarını görüntüleme ve dışarı aktarma. Bu raporlarda hassas bilgiler olabileceği için, bu rolü yalnızca bu bilgileri görüntülemesi gereken açık bir kullanıcıya atamanız gerekir.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Genel Okuyucu <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi <br/><br/> Güvenlik İşleci|
|**Yalnızca görüntüleme durumu**||İletişim Uyumluluğu <br/><br/> İletişim Uyumluluğu Uyumluluk Uyumlulukları <br/><br/> Uyumluluk Yöneticisi <br/><br/> Insider Risk Yönetimi <br/><br/> Insider Risk Yönetimi Yöneticileri <br/><br/> İçeriden Risk Yönetimi Analistleri <br/><br/> Insider RiskManagement Esnafları <br/><br/> Kuruluş Yönetimi <br/><br/> Gizlilik Yönetimi <br/><br/> Gizlilik Yönetimi Yöneticileri <br/><br/> Gizlilik Yönetimi Analistleri <br/><br/> Gizlilik Yönetimi Özel Ekipler <br/><br/> Konu Hakları İsteği Yöneticileri|
|**Yalnızca Görüntüleme Cihaz Yönetimi**|Yeni özellik için yapılandırmayı ve Cihaz Yönetimi görüntüleme.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Genel Okuyucu <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi <br/><br/> Güvenlik İşleci <br/><br/> Güvenlik Okuyucu|
|**Yalnızca görüntüleme için DLP Uyumluluk Yönetimi**|Veri kaybı önleme (DLP) ilkeleriyle ilgili ayarları ve raporları görüntüleme.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Genel Okuyucu <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi <br/><br/> Güvenlik İşleci <br/><br/> Güvenlik Okuyucu|
|**Yalnızca görüntüleme için IB Uyumluluk Yönetimi**|Bilgi Engelleri özelliğine ilişkin yapılandırmayı ve raporları görüntüden kaldırabilirsiniz.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Genel Okuyucu <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi <br/><br/> Güvenlik İşleci <br/><br/> Güvenlik Okuyucu|
|**Uyarıları Yalnızca Görüntüleme**|Uyarıları Yönet özelliğiyle ilgili yapılandırmayı ve raporları görüntüleme.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Genel Okuyucu <br/><br/> Kuruluş Yönetimi <br/><br/> Güvenlik Yöneticisi <br/><br/> Güvenlik İşleci <br/><br/> Güvenlik Okuyucu|
|**Yalnızca Görüntüleme Alıcıları**|Kullanıcılar ve gruplar hakkında bilgileri görüntüleme.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Genel Okuyucu <br/><br/> MailFlow Yöneticisi <br/><br/> Kuruluş Yönetimi|
|**Yalnızca Görüntüleme Kaydı Yönetimi**|Kayıt yönetimi özelliğinin yapılandırmasını görüntüleme.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> <br/><br/> Genel Okuyucu <br/><br/> Kuruluş Yönetimi|
|**Yalnızca görüntüleme bekletme yönetimi**|Bekletme ilkelerinin, bekletme etiketlerinin ve bekletme etiketi ilkelerinin yapılandırmasını görüntüleme.|Uyumluluk Yöneticisi <br/><br/> Uyumluluk Veri Yöneticisi <br/><br/> Genel Yönetici <br/><br/> Kuruluş Yönetimi|
