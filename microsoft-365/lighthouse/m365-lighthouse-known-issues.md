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
ms.openlocfilehash: 4d19051de1b4466dabc535446182c7f630ee948b
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2022
ms.locfileid: "63705402"
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
| **Silinmiş ilke görüntülenir** | Intune'dan bir cihaz uyumluluk ilkesi silindikten sonra, geçici olarak Deniz Feneri'nde görünür olmaya devam eder. MSP teknisyenleri silinmiş bir ilke içeren bir ilke karşılaştırması yapmaya çalışsalar, teknisyenler şu hatayı alır: "Bir sorun oluştu. Lütfen sayfayı yenileyin ve yeniden deneyin." | Hatayı çözmek için, silinen ilkeyi ilke karşılaştırmadan silin ve yalnızca var olan ilkeleri karşılaştırın. |

## <a name="threat-management"></a>Tehdit yönetimi

| Sorun | Açıklama | Çözüm |
| ---------------- | ---------------- | ---------------- |
| **Tehdit adı eksik** | MSP teknisyenleri Tehdit Yönetimi sayfasındaki tehdit listesini görüntüleyseler, tehdit adı bazı tehdit olarak eksik olabilir. Bu durum, tehdidin algııldığı cihaz yakın zamanda Intune'dan kaldırıldığı zaman ortaya çıkar. | Sorun 48 saat içinde çözülecek. Ek adım gerekmez. |

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

## <a name="delegated-admin-permissionsdap"></a>Temsili Yönetici İzinleri (DAP)

| Sorun | Açıklama | Çözüm |
| ---------------- | ---------------- | ---------------- |
| **DAP rollerini değiştirirken izinlerin gecikmesi** | MSP teknisyeni Yönetici Temsilcisi veya Yardım masası Aracısı grubuna eklenir veya gruptan kaldırılırsa, Deniz Feneri içindeki uygun izinleri yansıtmada gecikme olabilir. | Sorun 30 dakika içinde çözülecek. Ek adım gerekmez. |

## <a name="granular-delegated-admin-permissionsgdap"></a>Ayrıntılı Temsilci Yönetici İzinleri (GDAP)

> [!NOTE]
> GDAP, iş [ortaklarının](/partner-center/announcements/2022-february#6) GDAP genel olarak kullanıma hazır olmadan önce ayrıntılı izinler atamasına olanak vermek için şu anda teknik önizlemededir.

| Sorun | Açıklama | Çözüm |
| ---------------- | ---------------- | ---------------- |
| **Deniz Feneri'nde çeşitli GDAP izin sorunları** | <ul><li>GDAP Güvenlik Yöneticileri, riskli kullanıcıları görüntüleyemiyor, riskleri yoksayamaz veya risk altında olan kullanıcıları onay yapamaz.</li><li>GDAP Güvenlik Okuyucuları riskli kullanıcıları görüntüdeyemiyor.</li><li>GDAP Genel Yöneticileri, hizmet durumunu görüntülemeye çalışırken bir hata iletisi görmektedir.</li></ul> | GDAP Genel Kullanılabilirliği'ne başlamadan önce, geçici çözüm kullanıcıya bir Genel Yönetici GDAP rolü veya Yönetici Aracısı DAP rolü atamaktır. Genel Yönetici GDAP rolü atama yönergeleri için bkz. Müşteri hizmetini yönetmek için ayrıntılı [yönetici izinlerini alma](/partner-center/gdap-obtain-admin-permissions-to-manage-customer). Yönetici Aracısı DAP rolü atama yönergeleri için bkz. [Kullanıcılara rol ve izin atama](/partner-center/permissions-overview). Lighthouse'da ortak kiracıda belirli rollerin Azure Active Directory gereken eylemlerin listesi için bkz. Portal [Microsoft 365 Lighthouse yapılandırma](/microsoft-365/lighthouse/m365-lighthouse-configure-portal-security).

## <a name="localization"></a>Yerelleştirme

| Sorun | Açıklama | Çözüm |
| ---------------- | ---------------- | ---------------- |
| **Çeviri sorunları** | Tarayıcılarının dili veya Lighthouse'daki dil seçimi İngilizce dışında bir dil seçimi olduğunda, kullanıcılar dil çeviri sorunlarıyla bu sorunu yaşayabilirsiniz. | Deniz Feneri'nde çeviri sorunlarını en aza indirmek için tarayıcının dil seçiminin, Deniz Feneri portalında yer alan dil ayarıyla aynı olduğundan emin olun. Deniz Feneri'nde dil seçimini değiştirmek için, Deniz Feneri'nde oturum açın ve sayfanın üst kısmında bulunan dişli simgesini seçerek Portal ayarları sayfasını açın, Dil **+** bölge'yi seçin ve ardından uygun dil ve bölgesel biçimleri seçin. |

## <a name="related-content"></a>İlgili içerik

[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)\
[E-postada sorunları ve hata iletilerini Microsoft 365 Lighthouse](m365-lighthouse-troubleshoot.md) (makale)\
[Destek almak için yardım ve Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md) (makale)