---
title: Microsoft 365 Lighthouse hata iletilerini ve sorunlarını giderme
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
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Microsoft 365 Lighthouse kullanan Yönetilen Hizmet Sağlayıcıları (MSP) için hata iletilerini ve sorunlarını giderme konusunda yardım alın.
ms.openlocfilehash: 939b81344d2957dc005b71d91e27c09a8bca3c96
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174258"
---
# <a name="troubleshoot-error-messages-and-problems-in-microsoft-365-lighthouse"></a>Microsoft 365 Lighthouse hata iletilerini ve sorunlarını giderme

Bu makalede, Microsoft 365 Lighthouse kullanırken karşılaşabileceğiniz hata iletileri ve sorunlar açıklanır ve bunları çözmek için atabileceğiniz sorun giderme adımları sağlanır.

## <a name="partner-onboarding"></a>İş ortağı ekleme

### <a name="message-when-trying-to-access-lighthouse-microsoft-365-lighthouse-doesnt-support-indirect-providers-at-this-time-you-must-be-an-indirect-reseller-or-direct-bill-partner-to-use-this-service"></a>Lighthouse'a erişmeye çalışırken ileti: "Microsoft 365 Lighthouse şu anda dolaylı sağlayıcıları desteklemez, bu hizmeti kullanmak için dolaylı satıcı veya doğrudan fatura iş ortağı olmanız gerekir"

**Neden:** Lighthouse'a dolaylı fatura iş ortağı olarak erişmeye çalıştınız. Şu anda Lighthouse yalnızca dolaylı bayileri ve doğrudan fatura iş ortaklarını destekler.

**Çözünürlük:** Niteliklerin ve gereksinimlerin tam listesi için bkz [. Microsoft 365 Lighthouse gereksinimleri](m365-lighthouse-requirements.md). Dolaylı bir sağlayıcı değilseniz ve bu iletiyi hatayla aldığınıza inanıyorsanız Desteğe başvurun. Daha fazla bilgi için bkz. [Microsoft 365 Lighthouse için yardım ve destek alma](m365-lighthouse-get-help-and-support.md).

### <a name="message-when-trying-to-access-lighthouse-you-must-be-an-indirect-reseller-or-direct-bill-partner-to-use-this-service"></a>Lighthouse'a erişmeye çalışırken ileti: "Bu hizmeti kullanmak için dolaylı bayi veya doğrudan fatura iş ortağı olmanız gerekir"

**Neden:** Lighthouse'a erişmeye çalıştınız ve Bir Microsoft iş ortağı değilsiniz. Lighthouse kullanmak için Bulut Çözümü Sağlayıcısı (CSP) programına dolaylı bayi veya doğrudan fatura iş ortağı olarak kaydolmanız gerekir.

**Çözünürlük:** Niteliklerin ve gereksinimlerin tam listesi için bkz [. Microsoft 365 Lighthouse gereksinimleri](m365-lighthouse-requirements.md). Lighthouse'a erişmeye uygunsanız ve bu iletiyi hatayla aldığınıza inanıyorsanız Desteğe başvurun. Daha fazla bilgi için bkz. [Microsoft 365 Lighthouse için yardım ve destek alma](m365-lighthouse-get-help-and-support.md).

### <a name="message-when-signing-in-to-lighthouse-accept-the-partner-amendment"></a>Lighthouse'da oturum açarken ileti: "İş Ortağı Değişikliğini Kabul Et"

**Neden:** İş ortağı kiracısında genel yönetici iş ortağı değişikliğini imzalamadan önce Lighthouse'a erişmeye çalıştınız.

**Çözünürlük:** Lighthouse'a erişebilmeniz ve lighthouse'da çalışabilmeniz için önce Genel yöneticinin Lighthouse'da oturum açması ve iş ortağı değişikliğini kabul etmesi gerekir. Genel yönetici değişikliği imzaladıktan sonra hata devam ederse Destek'e başvurun. Daha fazla bilgi için bkz. [Microsoft 365 Lighthouse için yardım ve destek alma](m365-lighthouse-get-help-and-support.md).

## <a name="customer-tenant-onboarding"></a>Müşteri kiracısı ekleme  

### <a name="customer-tenants-show-a-status-other-than-active-in-the-tenant-list"></a>Müşteri kiracıları kiracı listesinde "Etkin" dışında bir durum gösteriyor  

**Neden:** Müşteri kiracılarınız aşağıdaki ölçütleri karşılamıyor:

- Müşteri kiracısını yönetebilmek için Yönetilen Hizmet Sağlayıcısı (MSP) için temsilci erişimi ayarlanmış olmalıdır*
- En az bir Microsoft 365 İş Ekstra, Microsoft 365 E3, Windows 365 Business veya İş için Microsoft Defender lisansı olmalıdır
- En fazla 1000 lisanslı kullanıcı olmalıdır 

**Çözünürlük:** Aşağıdaki tabloda eylem gerektiren farklı kiracı durumları ve bunların nasıl çözümlendiği açıklanmaktadır.

*Müşterileri Lighthouse'a eklemek için Temsilci Yönetici Ayrıcalıkları (DAP) gerekir. Daha güvenli temsilci erişimi sağlamak için müşterilerinizle Ayrıntılı Yönetici Ayrıcalıkları (GDAP) oluşturmanızı da öneririz. DAP ve GDAP birlikte bulunurken, her iki modelin de bulunduğu müşteriler için GDAP öncelikli olacaktır. Yakında yalnızca GDAP (ve DAP olmayan) müşteriler Lighthouse'a eklenecek.

| Durum | Açıklama | Çözüm |
|--|--|--|
| Etkin olmayan | Kiracı, MSP'nin isteği üzerine kapatıldı ve artık Lighthouse'da yönetilmedi. | Kiracıyı yeniden etkinleştirmeniz gerekir. **Kiracılar** sayfasında, yeniden etkinleştirmek istediğiniz kiracının yanındaki üç noktayı (daha fazla eylem) seçin ve ardından **Kiracıyı etkinleştir'i** seçin. İlk müşteri verilerinin Lighthouse'da görünmesi 24-48 saat sürebilir. |
| Uygun değil - DAP veya GDAP ayarlanmadı | Lighthouse'un gerektirdiği kiracıyla ayarlanmış DAP veya GDAP yönetici ayrıcalıklarınız yoktur. | Microsoft İş Ortağı Merkezi'nde DAP veya GDAP yönetici ayrıcalıklarını ayarlayın. |
| Uygun değil - Gerekli lisans eksik | Kiracıda gerekli bir lisans eksik. En az bir Microsoft 365 İş Ekstra, Microsoft 365 E3 veya İş için Microsoft Defender lisansı gerekir. | Kiracıya en az bir Microsoft 365 İş Ekstra, Microsoft 365 E3, Windows 365 Business veya İş için Microsoft Defender lisansı atandığından emin olun. |
| Uygun değil - Kullanıcı sayısı aşıldı | Kiracı, Lighthouse tarafından izin verilen en fazla 1000 lisanslı kullanıcıya sahiptir. | Kiracının 1000'den fazla lisanslı kullanıcısı olmadığını doğrulayın. |
| Uygun değil - Coğrafi denetim başarısız oldu | Siz ve müşteriniz Lighthouse'un gerektirdiği aynı coğrafi bölgede ikamet etmezsiniz. | Müşterinin coğrafi bölgenizde bulunduğunu doğrulayın. Aksi takdirde, Lighthouse'da kiracıyı yönetemezsiniz. |
| İşlemde | Lighthouse kiracıyı keşfetti ama hala ekleme aşamasında. | Lighthouse'un kiracıyı ekleme işlemini tamamlaması için 48 saat bekleyin. |

Müşteri kiracınızın ekleme ölçütlerini karşıladığını ve hala Lighthouse'da **Etkin** olarak gösterilmediğini doğruladıysanız Destek'e başvurun. Daha fazla bilgi için bkz. [Microsoft 365 Lighthouse için yardım ve destek alma](m365-lighthouse-get-help-and-support.md).

## <a name="access-and-permissions"></a>Erişim ve izinler

### <a name="message-when-trying-to-access-lighthouse-not-authorized-or-insufficient-privileges-or-access-restriction-insufficient-or-lack-of-permissions-is-causing-access-restriction"></a>Lighthouse'a erişmeye çalışırken ileti: "Yetki yok" veya "Yetersiz ayrıcalıklar" veya "Erişim Kısıtlaması: Erişim kısıtlamasına izin yetersiz veya eksik neden oluyor" 

**Neden:** Azure AD'da doğru güvenlik grubuna ait değilsiniz veya Lighthouse'a erişebilmek için İş Ortağı Merkezi'nde doğru rol size atanmadı.

**Çözünürlük:** İş ortağı kiracınızdan uygun izinlere sahip bir yöneticinin sizi Azure AD'de doğru GDAP güvenlik grubuna atadığından ve size İş Ortağı Merkezi'nde doğru rolü atadığından emin olun. Ayrıca Lighthouse'daki bazı eylemlerin Genel yönetici olmanız gerektiğini unutmayın. GDAP rolleri ve her rolün yapabilecekleri hakkında daha fazla bilgi edinmek için bkz. [Microsoft 365 Lighthouse'de izinlere genel bakış](m365-lighthouse-overview-of-permissions.md). Tüm Azure AD yerleşik rollerin ve GDAP izinlerinin ayrıntılı açıklaması için bkz. [yerleşik roller Azure AD](/azure/active-directory/roles/permissions-reference).

DAP ilişkileri olan müşteriler için, iş ortağı yöneticisinin sizi İş Ortağı Merkezi'ndeki Yönetici aracısı veya Yardım masası aracısı rolüne ataması gerekir. Tüm İş Ortağı Merkezi rollerinin ve izinlerinin ayrıntılı açıklaması için bkz. [Kullanıcılara rol ve izin atama](/partner-center/permissions-overview).

### <a name="i-dont-see-complete-data-in-certain-areas-of-lighthouse-or-i-cant-perform-certain-tasks-or-i-cant-access-certain-tenants"></a>Lighthouse'un belirli alanlarında tam veri görmüyorum veya belirli görevleri gerçekleştiremiyorum veya belirli kiracılara erişemiyorum

**Neden:** GDAP erişiminiz, içinde olduğunuz Azure AD güvenlik grubuna atanan rollere göre sınırlıdır.

**Çözünürlük:** İş ortağı kiracınızdan uygun izinlere sahip bir yöneticinin sizi Azure AD'de doğru GDAP güvenlik grubuna atadığından emin olun. Ayrıca Lighthouse'daki bazı eylemlerin Genel yönetici olmanız gerektiğini unutmayın. GDAP rolleri ve her rolün yapabilecekleri hakkında daha fazla bilgi edinmek için bkz. [Microsoft 365 Lighthouse'de izinlere genel bakış](m365-lighthouse-overview-of-permissions.md). Tüm Azure AD yerleşik rollerin ve GDAP izinlerinin ayrıntılı açıklaması için bkz. [yerleşik roller Azure AD](/azure/active-directory/roles/permissions-reference).

## <a name="customer-tenant-management"></a>Müşteri kiracı yönetimi  

### <a name="customer-tenant-has-no-data-showing-in-lighthouse"></a>Müşteri kiracısında Lighthouse'da gösterilen veri yok

**Neden:** Kiracı ekleme işlemi tamamlanmadan önce Lighthouse'da verileri görüntülemeye çalışıyorsunuz.

**Çözünürlük:** İlk müşteri verilerinin Lighthouse'da görünmesi 24-48 saat sürebilir. Kiracıyı eklemenin üzerinden 48 saatten uzun bir süre geçtiyse ve kiracı verilerini hala görüntüleyemiyor veya yükleyemiyorsanız ya da daha önce görüntüleyemediğiniz veya yükleyemediğiniz durumda Desteğe başvurun. Daha fazla bilgi için bkz. [Microsoft 365 Lighthouse için yardım ve destek alma](m365-lighthouse-get-help-and-support.md). İlgili ağ günlüklerini ve değiştirilmiş olabilecek seçeneklerin listesini sağlamaya hazır olun.

### <a name="customer-tenant-data-isnt-updating-after-making-changes-in-the-customer-tenant"></a>Müşteri kiracısında değişiklik yaptıktan sonra müşteri kiracı verileri güncelleştirilmiyor

**Neden:** Müşteri kiracısında yaptığınız değişikliklerin Lighthouse'daki müşteri kiracı verileriyle eşitlenmesi 4 saat kadar sürebilir.

**Çözünürlük:** 4 saatten uzun bir süre geçtiyse ve müşteri kiracı verileri Lighthouse'da hala güncelleştirilmediyse Destek'e başvurun. Daha fazla bilgi için bkz. [Microsoft 365 Lighthouse için yardım ve destek alma](m365-lighthouse-get-help-and-support.md). Müşteri kiracı bilgilerini sağlamaya hazır olun.

### <a name="message-when-applying-a-baseline-to-a-customer-tenant-process-error-occurred"></a>Müşteri kiracısına temel uygulama iletisi: "İşlem hatası oluştu"  

**Neden:** Müşteri kiracısı içindeki Microsoft Intune yapılandırmasını başarıyla tamamlamadınız.

**Çözünürlük:** Müşteri kiracısı içindeki Intune için temel yapılandırma adımlarını tamamladığınızdan emin olun. Müşteri kiracısı için Intune yapılandırmasının tamamlandığını doğruladıktan sonra sorun devam ederse Destek'e başvurun. Daha fazla bilgi için bkz. [Microsoft 365 Lighthouse için yardım ve destek alma](m365-lighthouse-get-help-and-support.md).

### <a name="cant-access-partner-tenant-data-in-lighthouse"></a>Lighthouse'da iş ortağı kiracı verilerine erişemiyorum

**Neden**: Lighthouse yalnızca *müşteri* kiracılarının görüntülenmesini ve yönetilmesini destekler. Şu anda *iş ortağı* kiracılarının görüntülenmesini ve yönetilmesini desteklememektedir.

**Çözünürlük:** İş ortağı kiracınızı görüntülemek ve yönetmek için kullandığınız yöntemi kullanmaya devam edin.

## <a name="device-and-threat-management"></a>Cihaz ve tehdit yönetimi 

### <a name="i-dont-see-any-customer-tenant-data-on-the-device-compliance-and-threat-management-pages-of-lighthouse"></a>Lighthouse'un Cihaz uyumluluğu ve Tehdit yönetimi sayfalarında müşteri kiracısı verileri görmüyorum

**Neden 1:** Müşteri kiracısı Intune ekleme işlemini tamamlamadı. Müşteri kiracı verileri, müşteri kiracısının Intune ekleme işlemini tamamlayana kadar Lighthouse'un Cihaz uyumluluğu veya Tehdit yönetimi sayfalarında kullanılamaz.

**Çözünürlük:** Verilerini görüntülemeye çalıştığınız müşteri kiracısının Intune ekleme işleminin tamamlandığını doğrulayın. Intune'da ekleme tamamlandıktan sonra, cihaz verilerinin Lighthouse'da görünmesi için 4 saat bekleyin.

**Neden 2:** Müşteri kiracısı kısa süre önce Lighthouse'a eklendi ve veriler Lighthouse'da yüklenmeye devam ediyor.

**Çözünürlük:** Bir müşteri kiracısı Lighthouse'a eklendikten sonra, ilk müşteri verilerinin görünmesi için 24-48 saat bekleyin.

**Neden 3:** Müşteri kiracı cihazı yeni ve cihaz verileri Lighthouse'da yüklenmeye devam ediyor.

**Çözünürlük:** Bir kiracı cihazı eklendiğinde, cihaz verilerinin Lighthouse'da görünmesi için 4 saat bekleyin.

Çözüm yönergelerini takip ettikten sonra veriler Cihaz uyumluluğu ve Tehdit yönetimi sayfalarında görünmeye devam ediyorsa Destek'e başvurun. Daha fazla bilgi için bkz. [Microsoft 365 Lighthouse için yardım ve destek alma](m365-lighthouse-get-help-and-support.md).

## <a name="related-content"></a>İlgili içerik

[Microsoft 365 Lighthouse ile ilgili bilinen sorunlar](m365-lighthouse-known-issues.md) (makale)\
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)\
[Microsoft 365 Lighthouse için yardım ve destek alma](m365-lighthouse-get-help-and-support.md) (makale)
