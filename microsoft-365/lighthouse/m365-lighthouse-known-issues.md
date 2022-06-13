---
title: Microsoft 365 Lighthouse ile ilgili bilinen sorunlar
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: crimora
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthous
search.appverid: MET150
description: Microsoft 365 Lighthouse kullanan Yönetilen Hizmet Sağlayıcıları (MSP) için, Özellik alanına göre Lighthouse ile ilgili bilinen sorunların listesine bakın.
ms.openlocfilehash: 7a175d6c14e9b434240ff1a85f901a919ea79dcc
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016734"
---
# <a name="known-issues-with-microsoft-365-lighthouse"></a>Microsoft 365 Lighthouse ile ilgili bilinen sorunlar

Bu makalede, özellik alanına göre Microsoft 365 Lighthouse ile ilgili bilinen sorunlar listelenir. Lighthouse hakkında daha fazla bilgi için bkz. [Microsoft 365 Lighthouse genel bakış](m365-lighthouse-overview.md).

## <a name="users"></a>Kullanıcılar

| Sorun | Açıklama | Çözüm |
| ---------------- | ---------------- | ---------------- |
| **Yardım Masası Aracısı kullanıcı parolasını sıfırlayamıyor** | Yardım Masası Aracısı grubunun üyesi olan Yönetilen Hizmet Sağlayıcısı (MSP) teknisyenleri, müşteri kiracılarındaki kullanıcıların parolalarını sıfırlayamaz. Kullanıcı parolasını sıfırlamaya çalıştığında şu hata iletisini alır: "Bunu yapma izniniz yok. [Daha fazla bilgi edinin](m365-lighthouse-configure-portal-security.md)" | İzin sorununu geçici olarak çözmek için Yardım Masası Aracıları Microsoft 365 yönetim merkezi veya Azure Active Directory kullanarak parolaları sıfırlamalıdır. |

## <a name="devices"></a>Aygıtları

| Sorun | Açıklama | Çözüm |
| ---------------- | ---------------- | ---------------- |
| **Silinen ilke görüntüleniyor** | Cihaz uyumluluk ilkesi Intune silindikten sonra Lighthouse'da geçici olarak görünür olmaya devam eder. MSP teknisyenleri silinmiş bir ilke içeren bir ilke karşılaştırması yapmaya çalışırsa teknisyenler şu hatayı alır: "Bir sorun oluştu. Lütfen sayfayı yenileyin ve yeniden deneyin." | Hatayı çözmek için, ilke karşılaştırmasından silinen ilkeyi temizleyin ve yalnızca mevcut ilkeleri karşılaştırın. |

## <a name="threat-management"></a>Tehdit yönetimi

| Sorun | Açıklama | Çözüm |
| ---------------- | ---------------- | ---------------- |
| **Tehdit adı eksik** | MSP teknisyenleri Tehdit Yönetimi sayfasından tehdit listesini görüntülediğinde, bazı tehditlerde tehdidin adı eksik olabilir. Tehdit algılanan cihaz yakın zamanda Intune'dan kaldırıldığında bu durum ortaya çıkar. | Sorun 48 saat içinde çözülecektir. Ek adım gerekmez. |

## <a name="baselines"></a>Temel

| Sorun | Açıklama | Çözüm |
| ---------------- | ---------------- | ---------------- |
| **Eski kimlik doğrulamasını engelleme ve MFA dağıtım adımlarını karşılaştırırken çakışan ayarlar** | Müşteri kiracısı eski kimlik doğrulamasını engelle ve MFA dağıtım adımlarından birini dağıttıysa, karşılaştırma testi hatalı bir şekilde bu ayarları çakışıyor olarak tanımlar. | Geçici çözüm gerekmez. Ayarlar aslında çakışmaz ve müşteri kiracısında kullanıcılar etkilenmez. |

## <a name="windows-365"></a>Windows 365

| Sorun | Açıklama | Çözüm |
| ---------------- | ---------------- | ---------------- |
| **Sağlamayı yeniden deneme hatası** | MSP teknisyenleri, Bulut bilgisayar sağlamayı yeniden denemeyi denerken "Bunu yapma izniniz yok" hata iletisini alır. | Bu sorunu geçici olarak çözmek için müşteri kiracısında oturum açın ve ardından Microsoft Endpoint Manger yönetim merkezinden Bulut bilgisayarları yeniden sağlayın. Yönergeler için bkz. [Bulut bilgisayarı yeniden sağlama](/windows-365/enterprise/reprovision-cloud-pc). |

## <a name="audit-logs"></a>Denetim günlükleri


| Sorun | Açıklama | Çözüm |
|--|--|--|
| **Devre dışı bırakma ve Yeniden etkinleştirme eylemleri denetim günlüklerinde listelenmiyor** | Aşağıdaki etkinlikler şu anda Lighthouse'un Denetim günlükleri sayfasında bildirilmiyor: <ul><li>Ad: offboardTenant \| Action: Müşteriyi devre dışı bırakma</li> <li>Ad: resetTenantOnboardingStatus \| Action: Reactive customer</li></ul> | Geçici bir çözüm yoktur, ancak bir düzeltme üzerinde çalışıyoruz. Düzeltme hizmete dağıtıldıktan sonra bu etkinlikler denetim günlüklerinde görünür. |
| **Filtre tüm kullanıcıları göstermiyor** | MSP teknisyenleri **Tarafından Başlatılan'ı** kullanarak filtrelemeye çalıştığında, denetim günlükleri oluşturan eylemleri başlatan teknisyenlerin e-posta kimliklerine karşılık gelen tüm Kullanıcı Asıl Adlarının (UPN) listesi filtre altında tam olarak görüntülenmez.<br><br>Denetim günlüklerinin tamamen görüntüleneceğini unutmayın; yalnızca **Tarafından Başlatılarak** filtrelenebilme özelliği etkilenir. | Geçici bir çözüm yoktur, ancak bir düzeltme üzerinde çalışıyoruz. Düzeltme hizmete dağıtıldıktan sonra filtre, filtrelenecek UPN'lerin tam listesini görüntüleyerek beklenen davranışına geri döner. |

## <a name="delegated-admin-privileges-dap"></a>Yönetici Ayrıcalıkları Temsilcisi (DAP)

| Sorun | Açıklama | Çözüm |
| ---------------- | ---------------- | ---------------- |
| **DAP rollerini değiştirirken izin gecikmesi** | Yönetici Aracısı veya Yardım Masası Aracısı grubuna bir MSP teknisyeni eklenirse veya gruptan kaldırılırsa Lighthouse'da uygun izinlerin yansıtılmasında gecikme olabilir. | Sorun 30 dakika içinde çözülecektir. Ek adım gerekmez. |

## <a name="granular-delegated-admin-privileges-gdap"></a>Ayrıntılı Yönetici Ayrıcalıkları (GDAP)

Müşterileri Lighthouse'a eklemek için Ayrıntılı Yönetici Ayrıcalıkları (GDAP) ve dolaylı bayi ilişkisi ya da Temsilci Yönetici Ayrıcalıkları (DAP) ilişkisi gerekir. MÜŞTERI kiracısında DAP ve GDAP birlikte varsa, GDAP özellikli güvenlik gruplarındaki MSP teknisyenleri için GDAP izinleri önceliklidir. Yakında yalnızca GDAP ilişkilerine (dolaylı kurumsal bayi ilişkileri olmadan) sahip müşteriler Lighthouse'a eklenecek.<br><br>

| Sorun | Açıklama | Çözüm |
| ---------------- | ---------------- | ---------------- |
| **Lighthouse genelinde çeşitli GDAP izin sorunları** | Bazı GDAP rolleri, Lighthouse'daki müşteri verilerine tek kiracılı bir deneyimde olduğu gibi aynı düzeyde erişim vermez. Aşağıdaki rollerden herhangi biri MSP teknisyenlerine ayrı ayrı atanırsa (bu, diğer GDAP rolleriyle birlikte değil) aşağıdakiler de dahil olmak üzere hatalarla karşılaşabilir:<ul><li>GDAP Güvenlik Yöneticileri, Lighthouse'da riskli kullanıcıları görüntüleyemiyor, riskleri kapatamıyor veya güvenliği aşılmış kullanıcıları onaylayamıyor.</li><li>GDAP Güvenlik Okuyucuları Lighthouse'da riskli kullanıcıları görüntüleyemez.</li><li>GDAP Genel Yöneticileri Lighthouse'da hizmet durumunu görüntülemeye çalışırken bir hata iletisi görür.</li><li>GDAP Genel Yöneticileri Lighthouse'da dağıtım planı adımlarını dağıtırken sorunlarla karşılaşır.</li></ul> | Geçici çözüm, MSP teknisyenlerine ihtiyaç duydukları müşteri verilerine erişim düzeyine göre GDAP rollerinin bir birleşimini atamaktır. Lighthouse'un kullanılması önerilen GDAP rollerinin listesi için bkz. [Microsoft 365 Lighthouse'de izinlere genel bakış](m365-lighthouse-overview-of-permissions.md).<br><br>GDAP Genel Yönetici izinlerinin bile Lighthouse'da bir özelliğin kullanımına izin vermediği sorunlar için geçici çözüm, müşteriyi yönetmek için müşteri kiracısından uygun yönetim merkezine erişmektir (örneğin, hizmet durumunu denetlemek için müşteri kiracısından Microsoft 365 yönetim merkezi erişin). GDAP ilişkisini değiştirme yönergeleri için bkz. [Müşterinin hizmetini yönetmek için ayrıntılı yönetici izinleri alma - İş Ortağı Merkezi](/partner-center/gdap-obtain-admin-permissions-to-manage-customer). |

## <a name="localization"></a>Yerel -leştirme

| Sorun | Açıklama | Çözüm |
| ---------------- | ---------------- | ---------------- |
| **Çeviri sorunları** | Kullanıcılar, tarayıcılarının dili veya Lighthouse'daki dil seçimleri İngilizce dışında bir şey olduğunda dil çevirisi sorunlarıyla karşılaşabilir. | Lighthouse'da çeviri sorunlarını en aza indirmek için tarayıcının dil seçiminin Lighthouse portalındaki dil ayarıyla eşleştiğinden emin olun. Lighthouse'da dil seçimini değiştirmek için Lighthouse'da oturum açın ve sayfanın üst kısmındaki dişli simgesini seçerek Portal ayarları sayfasını açın, **Dil + bölge'yi** seçin ve ardından uygun dil ve bölgesel biçimleri seçin. |

## <a name="related-content"></a>İlgili içerik

[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)\
[Microsoft 365 Lighthouse hata iletilerini ve sorunlarını giderme](m365-lighthouse-troubleshoot.md) (makale)\
[Microsoft 365 Lighthouse için yardım ve destek alma](m365-lighthouse-get-help-and-support.md) (makale)
