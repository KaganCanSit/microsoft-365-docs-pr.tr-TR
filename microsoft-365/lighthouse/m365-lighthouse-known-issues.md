---
title: Güvenlikle ilgili bilinen Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthouse
search.appverid: MET150
description: Yönetilen Servis Sağlayıcıları (MSP) Microsoft 365 Lighthouse Özellik alanına göre Deniz Feneri ile ilgili bilinen sorunların bir listesine bakın.
ms.openlocfilehash: 3151937d4552da09c9cfd6808db2bad8bafbbc46
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2022
ms.locfileid: "64594675"
---
# <a name="known-issues-with-microsoft-365-lighthouse"></a>Güvenlikle ilgili bilinen Microsoft 365 Lighthouse

Bu makalede, özellik alanına göre Microsoft 365 Lighthouse sorunları listelemektedir. Deniz Feneri hakkında daha fazla bilgi için bkz. Deniz [Feneri'Microsoft 365 Lighthouse](m365-lighthouse-overview.md).

## <a name="users"></a>Kullanıcılar

| Sorun | Açıklama | Çözüm |
| ---------------- | ---------------- | ---------------- |
| **Yardım masası Aracısı kullanıcı parolasını sıfırlayamıyor** | Yardım masası Aracısı grubunun üyesi olan Yönetilen Hizmet Sağlayıcısı (MSP) teknisyenleri, müşteri kiracılarında yer alan kullanıcıların parolalarını sıfırlayamıyor. Kullanıcı parolasını sıfırlamaya geldiğinde şu hata iletisini alır: "Bunu yapma izniniz yok. [Daha fazla bilgi"](m365-lighthouse-configure-portal-security.md) | İzin sorununa yardımcı olmak için Yardım masası Aracılarının parolaları, kullanıcı kimliklerini veya kimlik Microsoft 365 yönetim merkezi Azure Active Directory. |

## <a name="devices"></a>Cihazlar

| Sorun | Açıklama | Çözüm |
| ---------------- | ---------------- | ---------------- |
| **Silinmiş ilke görüntülenir** | Bir cihaz uyumluluk ilkesi Posta'dan Intune, geçici olarak Deniz Feneri'nde görünmeye devam eder. MSP teknisyenleri silinmiş bir ilke içeren bir ilke karşılaştırması yapmaya çalışsalar, teknisyenler şu hatayı alır: "Bir sorun oluştu. Lütfen sayfayı yenileyin ve yeniden deneyin." | Hatayı çözmek için, silinen ilkeyi ilke karşılaştırmadan silin ve yalnızca var olan ilkeleri karşılaştırın. |

## <a name="threat-management"></a>Tehdit yönetimi

| Sorun | Açıklama | Çözüm |
| ---------------- | ---------------- | ---------------- |
| **Tehdit adı eksik** | MSP teknisyenleri Tehdit Yönetimi sayfasındaki tehdit listesini görüntüleyseler, tehdit adı bazı tehdit olarak eksik olabilir. Tehdit olarak algılanan cihaz yakın zamanda Diğer Kişilerden kaldırıldığı zaman bu Intune. | Sorun 48 saat içinde çözülecek. Ek adım gerekmez. |

## <a name="baselines"></a>Taban çizgisi

| Sorun | Açıklama | Çözüm |
| ---------------- | ---------------- | ---------------- |
| **Eski kimlik doğrulamayı ve MFA dağıtım adımlarını karşılaştırırken çakışan ayarlar** | Bir müşteri kiracısı eski kimlik doğrulamasını ve MFA dağıtım adımlarından birini engelle dağıtmışsa, karşılaştırma testi bu ayarları hatalı bir şekilde çakışan olarak tanımlar. | Geçici bir çözüm gerekmez. Ayarlar aslında çakışmaz ve müşteri kiracısı kullanıcıları etkilenmez. |

## <a name="windows-365"></a>Windows 365

| Sorun | Açıklama | Çözüm |
| ---------------- | ---------------- | ---------------- |
| **Sağlama hatasını yeniden deneme** | MSP teknisyenleri, Bir Bulut Bilgisayarı sağlamayı yeniden denemeye çalışırken "Bunu yapmak için izniniz yok" hata iletisini alır. | Bu sorunu gidermek için, müşteri kiracıda oturum açma ve ardından Microsoft Endpoint Manger yönetim merkezinden Bulut PC'leri yeniden bölüme açma. Yönergeler için bkz [. Bulut bilgisayarı yeniden bölüme yükleme](/windows-365/enterprise/reprovision-cloud-pc). |

## <a name="audit-logs"></a>Denetim günlükleri


| Sorun | Açıklama | Çözüm |
|--|--|--|
| **Denetim günlüklerinde Devre Dışı Bırak ve Yeniden Etkinleştir eylemleri listelenmiyor** | Şu anda Deniz Feneri'nin Denetim günlükleri sayfasında aşağıdaki etkinlikler bildir değildir: <ul><li>Ad: Çıkar eylemi \| : Müşteriyi devre dışı bırakma</li> <li>Ad: resetTenantOnboardingStatus \| Eylemi: Reactive customer</li></ul> | Geçici bir çözüm yok, ancak bir çözüm üzerinde çalışıyoruz. Düzeltme hizmette dağıtıldıktan sonra bu etkinlikler denetim günlüklerinde görüntülenir. |
| **Filtre tüm kullanıcıları göster görünmüyor** | MSP teknisyenleri Başlatan'ı kullanarak filtrelemeye **geldiğinde, denetim** günlükleri oluşturma eylemlerini başlatan teknisyenlerin e-posta kimliklerine karşılık gelen tüm Kullanıcı Asıl Adları (UPN) listesi filtre altında tam olarak görüntülenmez.<br><br>Denetim günlüklerinin kendilerinin tümüyle görüntülendiğinden; Yalnızca Başlatan'ı kullanarak bunları **filtreleme** özelliği etkiler. | Geçici bir çözüm yok, ancak bir çözüm üzerinde çalışıyoruz. Düzeltme hizmette dağıtıldıktan sonra, filtre beklenen davranışa döner (filtreye göre filtre ekleyebilirsiniz UPN'lerin tam listesi görüntülenir). |

## <a name="delegated-admin-privilegesdap"></a>Temsilcili Yönetici Ayrıcalıkları (DAP)

| Sorun | Açıklama | Çözüm |
| ---------------- | ---------------- | ---------------- |
| **DAP rollerini değiştirirken izinlerin gecikmesi** | MSP teknisyeni Yönetici Temsilcisi veya Yardım masası Aracısı grubuna eklenir veya gruptan kaldırılırsa, Deniz Feneri içindeki uygun izinleri yansıtmada gecikme olabilir. | Sorun 30 dakika içinde çözülecek. Ek adım gerekmez. |

## <a name="granular-delegated-admin-privilegesgdap"></a>Ayrıntılı Temsilci Yönetici Ayrıcalıkları (GDAP)

> [!NOTE]
> GDAP, iş [ortaklarının](/partner-center/announcements/2022-february#6) GDAP genel olarak kullanıma hazır olmadan önce ayrıntılı izinler atamasına olanak vermek için şu anda teknik önizlemededir.

Şu anda DAP'nin Deniz Feneri'ne müşterileri eklemesi gerekiyor. Ayrıca daha güvenli, temsilcili erişim sağlamak için müşterilerinizle birlikte GDAP kurmanızı da öneririz. DAP ve GDAP birlikte çalışırken, her iki modelin de bulunduğu müşteriler için GDAP öncelik olacaktır. Kısa süre içinde yalnızca GDAP'ye (ve DAP) sahip olan müşteriler Deniz Feneri'ne yerabilecek.<br><br>

| Sorun | Açıklama | Çözüm |
| ---------------- | ---------------- | ---------------- |
| **Deniz Feneri'nde çeşitli GDAP izin sorunları** | Bazı GDAP rolleri tek bir kiracılı deneyimde olduğu gibi, Deniz Feneri'nde müşteri verilerine erişim düzeyine sahip değildir. Aşağıdaki rollerden herhangi biri MSP teknisyenlerine tek tek atanırsa (bu, diğer GDAP rolleriyle birlikte değil) MSP teknisyenlerine tek tek atanırsa, aşağıdakiler gibi hatalarla karşılaşabilir:<ul><li>GDAP Güvenlik Yöneticileri, Deniz Feneri'nde riskli kullanıcıları görüntüleyemiyor, riskleri yok sayamaz veya risk altında olan kullanıcıları onay yapamaz.</li><li>GDAP Güvenlik Okuyucuları Deniz Feneri'nin içindeki riskli kullanıcıları görüntüde yapamaz.</li><li>GDAP Genel Yöneticileri, Deniz Feneri'nde hizmet durumunu görüntülemeye çalışırken bir hata iletisi görmektedir.</li><li>GDAP Genel Yöneticileri, Deniz Feneri'nde dağıtım planı adımlarını dağıtırken sorun yaşanıyor.</li></ul> | Bunun geçici çözümü, ihtiyaç olan müşteri verilerine erişim düzeyine bağlı olarak MSP teknisyenlerine GDAP rolleri birleşimi atamaktır. Deniz Feneri'nin kullanımı için önerilen GDAP rollerinin listesi için bkz. Deniz [Feneri'nde izinlere Microsoft 365 Lighthouse](m365-lighthouse-overview-of-permissions.md).<br><br>GDAP Genel Yönetici izinlerinin bile Deniz Feneri'nde bir özelliğin kullanımına izin vermeyecek sorunlar için geçici çözüm, müşteriyi yönetmek için müşteri kiracılarından uygun yönetim merkezine erişmektir (örneğin, hizmet durumunu kontrol etmek için Microsoft 365 yönetim merkezi'e müşteri kiracıdan erişin). GDAP ilişkisini değiştirme yönergeleri için bkz. Müşteri hizmetini yönetmek için ayrıntılı yönetici izinleri alma [- İş Ortağı Merkezi](/partner-center/gdap-obtain-admin-permissions-to-manage-customer). |

## <a name="localization"></a>Yerelleştirme

| Sorun | Açıklama | Çözüm |
| ---------------- | ---------------- | ---------------- |
| **Çeviri sorunları** | Tarayıcılarının dili veya Lighthouse'daki dil seçimi İngilizce dışında bir dil seçimi olduğunda, kullanıcılar dil çeviri sorunlarıyla bu sorunu yaşayabilirsiniz. | Deniz Feneri'nde çeviri sorunlarını en aza indirmek için tarayıcının dil seçiminin, Deniz Feneri portalında yer alan dil ayarıyla aynı olduğundan emin olun. Deniz Feneri'nde dil seçimini değiştirmek için, Deniz Feneri'nde oturum açın ve sayfanın üst kısmında bulunan dişli simgesini seçerek Portal ayarları sayfasını açın, Dil **+** bölge'yi seçin ve ardından uygun dil ve bölgesel biçimleri seçin. |

## <a name="related-content"></a>İlgili içerik

[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)\
[E-postada sorunları ve hata iletilerini Microsoft 365 Lighthouse](m365-lighthouse-troubleshoot.md) (makale)\
[Destek almak için yardım ve Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md) (makale)