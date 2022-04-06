---
title: E-posta iletileriyle ilgili sorunları ve hata iletilerini Microsoft 365 Lighthouse
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
description: Yönetilen Servis Sağlayıcıları (MSP) Microsoft 365 Lighthouse, hata iletilerini ve sorunlarını giderme konusunda yardım alır.
ms.openlocfilehash: e39eea66222852d8f331aa6bc68b386bea3da763
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2022
ms.locfileid: "63705442"
---
# <a name="troubleshoot-and-resolve-problems-and-error-messages-in-microsoft-365-lighthouse"></a>E-posta iletileriyle ilgili sorunları ve hata iletilerini Microsoft 365 Lighthouse

Bu makalede, E-posta iletileri kullanılırken karşılaşabilirsiniz hata iletileri ve Microsoft 365 Lighthouse sorunları çözmek için atılması gereken sorun giderme adımları ve sağlar.

## <a name="partner-onboarding"></a>İş ortağı ekleme

### <a name="message-when-trying-to-access-lighthouse-microsoft-365-lighthouse-doesnt-support-indirect-providers-at-this-time-you-must-be-an-indirect-reseller-or-direct-bill-partner-to-use-this-service"></a>Deniz Feneri'ne erişmeye çalışırken ileti: "Microsoft 365 Lighthouse şu anda dolaylı sağlayıcıları desteklememektedir, bu hizmeti kullanmak için dolaylı bir satıcı veya doğrudan fatura ortağı olmak gerekir"

**Neden:** Deniz Feneri'ne dolaylı fatura iş ortağı olarak erişmeye çalıştınız. Şu anda, Deniz Feneri yalnızca dolaylı satıcıları ve doğrudan fatura ortaklarını desteklemektedir.

**Çözüm:** Nitelikleri ve gereksinimlerin tam listesi için bkz. Sistem [Microsoft 365 Lighthouse](m365-lighthouse-requirements.md). Dolaylı sağlayıcı değilsanız ve bu iletiyi hatayla aldıklarını inanıyorsanız, Destek'e başvurun. Daha fazla bilgi için bkz[. Destek almak için Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="message-when-trying-to-access-lighthouse-you-must-be-an-indirect-reseller-or-direct-bill-partner-to-use-this-service"></a>Deniz Feneri'ne erişmeye çalışırken ileti: "Bu hizmeti kullanmak için dolaylı bir satıcı veya doğrudan fatura ortağınız olmalı"

**Neden:** Deniz Feneri'ne erişmeye çalıştınız ve Microsoft iş ortağı değilsiniz. Deniz Feneri'i kullanmak Bulut Çözümü Sağlayıcısı kurumsal (CSP) programına dolaylı bayi veya doğrudan fatura ortağı olarak kaydolmanız gerekir.

**Çözüm:** Nitelikleri ve gereksinimlerin tam listesi için bkz. Sistem [Microsoft 365 Lighthouse](m365-lighthouse-requirements.md). Deniz Feneri'ne erişmek için uygunsanız ve bu iletiyi hatayla aldıklarını inanıyorsanız, Destek'e başvurun. Daha fazla bilgi için bkz[. Destek almak için Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="message-when-signing-in-to-lighthouse-accept-the-partner-amendment"></a>Deniz Feneri'nde oturum aken ileti: "İş Ortağı Değişikliğini Kabul Et"

**Neden:** İş ortağı kiracısı genel yöneticisi iş ortağı değişikliğini imzalamadan önce Deniz Feneri'ne erişmeye çalıştınız.

**Çözüm:** Bir Genel yöneticinin, Deniz Feneri'ne erişmek ve burada çalışmak için önce Deniz Feneri'nde oturum açması ve iş ortağı değişikliğini kabul etmiş olması gerekir. Genel yönetici düzeltmeyi imzaladikten sonra hata devam ederse Destek'e başvurun. Daha fazla bilgi için bkz[. Destek almak için Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="customer-tenant-onboarding"></a>Müşteri kiracısı ekleme  

### <a name="customer-tenants-show-a-status-other-than-active-in-the-tenant-list"></a>Müşteri kiracıları, kiracı listesinde "Etkin" dışında bir durum gösterir  

**Neden:** Müşteri kiracınız aşağıdaki ölçütlere uygun değil:

  - Yönetilen Hizmet Sağlayıcısı (MSP) için temsilci (DAP) veya ayrıntılı temsilcili (GDAP) yönetici ayrıcalıklarının ayarlanmış olması gerekir
  - En az bir kullanıcı veya Microsoft 365 İş Ekstra lisansına Microsoft 365 E3 gerekir
  - 1000'den fazla lisanslı kullanıcıya sahip olmalı 

**Çözüm:** Aşağıdaki tabloda, eylem gerektiren farklı kiracı durumları açıkladığı gibi, bunları nasıl çözeceklerini de açıklar.<br><br>

| Durum | Açıklama | Çözüm |
|--|--|--|
| Etkin değil | Kiracı MSP'nin isteği üzerine çıkarıldı ve artık Deniz Feneri'nde yönetilmiyor. | Kiracıyı yeniden etkinleştirmeniz gerekir. Kiracılar **sayfasında** , yeniden etkinleştirmek istediğiniz kiracının yanındaki üç noktayı (diğer eylemler) seçin ve sonra da Kiracıyı **etkinleştir'i seçin**. İlk müşteri verilerinizin Deniz Feneri'nde görünmesi 24-48 saat sürebilir. |
| Uygun değil - DAP veya GDAP ayarlanmaz | Kiracıyla ayarlanmış OLAN DAP veya GDAP yönetici ayrıcalıklarınız yoktur ve bu, Deniz Feneri için gereklidir. | Microsoft İş Ortağı Merkezi'nde DAP veya GDAP yönetici ayrıcalıklarını ayarlayın. |
| Uygun değil - Gerekli lisans eksik | Kiracının gerekli bir lisansı yok. En az bir kullanıcı veya Microsoft 365 İş Ekstra lisansı Microsoft 365 E3 gerekir. | Kiracının en az bir kullanıcı veya Microsoft 365 İş Ekstra lisans Microsoft 365 E3 emin olun. |
| Uygun değil - Kullanıcı sayısı aşıldı | Kiracı, Deniz Feneri tarafından izin verilen en fazla 1000 lisanslı kullanıcıya sahip. | Kiracının 1000'den fazla lisanslı kullanıcısı olmadığını doğrulayın. |
| Uygun değil - Coğrafi denetim başarısız oldu | Siz ve müşteriniz, Deniz Feneri'nin ihtiyaç olduğu coğrafi bölgede ikamet yok. | Müşterinin coğrafi bölgenize yerdığını doğrulayın. Yönete değil, o zaman Deniz Feneri'nde kiracıyı yönete değildir. |
| İşlemde | Deniz Feneri kiracıyı keşfetti ancak hala kiracıyı ekleme sürecinde. | Deniz Feneri'nin kiracıyı ekleme işlemini tamamlamasına 48 saat izin ver. |

Müşteri kiracının işe ekleme ölçütlerine uygun olduğunu onaylarsanız ve kiracınız Hala Deniz Feneri'nde **Etkin** olarak görünmüyorsa, Destek'e başvurun. Daha fazla bilgi için bkz[. Destek almak için Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="access-and-permissions"></a>Erişim ve izinler

### <a name="message-when-trying-to-access-lighthouse-not-authorized-or-insufficient-privileges-or-access-restriction-insufficient-or-lack-of-permissions-is-causing-access-restriction"></a>Deniz Feneri'ne erişmeye çalışırken ileti: "Yetkili Değil" veya "Yetersiz ayrıcalıklar" veya "Erişim Kısıtlaması: İzinlerin yetersiz olması veya olmaması erişim kısıtlamasına neden oluyor" 

**Neden:** Azure AD'de doğru güvenlik grubuna üyesi değilsiniz veya Deniz Feneri'ne erişim için İş Ortağı Merkezi'nde size doğru rol atanmamış.

**Çözüm:** İş ortağı kiracınıza uygun izinlere sahip bir yöneticinin sizi Azure AD'de doğru GDAP güvenlik grubuna atadığı ve İş Ortağı Merkezi'nde size doğru rolü atadığından emin olun. Ayrıca, Deniz Feneri'nde bazı işlemlerin Genel yönetici olmak zorunda olduğunu unutmayın. GDAP rolleri ve her rolün neler yapılası hakkında daha fazla bilgi edinmek için Portal [güvenliğini Microsoft 365 Lighthouse bakın](m365-lighthouse-configure-portal-security.md). Tüm Azure AD yerleşik rollerinin ve GDAP izinlerinin ayrıntılı açıklaması için bkz. [Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference).

DAP ilişkileri olan müşteriler için, iş ortağı yöneticisinin sizi İş Ortağı Merkezi'nde Yönetici temsilcisine veya Yardım masası aracısı rolüne ataması gerekir. Tüm İş Ortağı Merkezi rollerinin ve izinlerinin ayrıntılı açıklaması için bkz. [Kullanıcılara rol ve izin atama](/partner-center/permissions-overview).

### <a name="i-dont-see-complete-data-in-certain-areas-of-lighthouse-or-i-cant-perform-certain-tasks-or-i-cant-access-certain-tenants"></a>Deniz Feneri'nin belirli alanlarında tam veriler göremiyorum veya bazı görevleri gerçekleştir göremiyorum veya belirli kiracılara erişe bilmiyorum

**Neden:** Var olan Azure AD güvenlik grubuna atanan rollere bağlı olarak, sınırlı bir GDAP erişiminiz var.

**Çözüm:** İş ortağı kiracınıza uygun izinlere sahip bir yöneticinin sizi Azure AD'de doğru GDAP güvenlik grubuna ata olduğundan emin olun. Ayrıca, Deniz Feneri'nde bazı işlemlerin Genel yönetici olmak zorunda olduğunu unutmayın. GDAP rolleri ve her rolün neler yapılası hakkında daha fazla bilgi edinmek için Portal [güvenliğini Microsoft 365 Lighthouse bakın](m365-lighthouse-configure-portal-security.md). Tüm Azure AD yerleşik rollerinin ve GDAP izinlerinin ayrıntılı açıklaması için bkz. [Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference).

## <a name="customer-tenant-management"></a>Müşteri kiracı yönetimi  

### <a name="customer-tenant-has-no-data-showing-in-lighthouse"></a>Deniz Feneri'nde müşteri kiracısı hiçbir veri gösteremdi

**Neden:** Kiracı ekleme işlemi tamamlamadan önce Deniz Feneri'nde verileri görüntülemeye çalışabilirsiniz.

**Çözüm:** İlk müşteri verilerinizin Deniz Feneri'nde görünmesi 24-48 saat sürebilir. Kiracıyı eklemenin bu yana 48 saati geçen bir süredir devam ediyor ve kiracı verilerini görüntüemiyor veya yükleyemiyorsanız ya da daha önce mümkün olan verileri görüntüleyemiyor veya yükleyemiyorsanız, Destek'e başvurun. Daha fazla bilgi için bkz[. Destek almak için Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md). İlgili ağ günlüklerini ve değiştirilmiş olan seçeneklerin listesini sağlamak için hazır olun.

### <a name="customer-tenant-data-isnt-updating-after-making-changes-in-the-customer-tenant"></a>Müşteri kiracıda değişiklik sonrasında müşteri kiracı verileri güncelleştiriliyor

**Neden:** Müşteri kiracısı içinde yaptığınız değişikliklerin Deniz Feneri'nde müşteri kiracı verileriyle eşitlenmesi 4 saat kadar sürebilir.

**Çözüm:** 4 saati geçse ve Deniz Feneri'nde müşteri kiracı verileri hala güncelleştirilmediyse, Destek'e başvurun. Daha fazla bilgi için bkz[. Destek almak için Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md). Müşteri kiracı bilgilerini sağlamak için hazır olun.

### <a name="message-when-applying-a-baseline-to-a-customer-tenant-process-error-occurred"></a>Müşteri kiracısına taban çizgisi uygularken şu ileti: "süreç hatası oluştu"  

**Neden:** Müşteri kiracısı içindeki kullanıcı yapılandırmayı Microsoft Intune tamamlamadınız.

**Çözüm:** Müşteri kiracısı içinde Intune için temel yapılandırma adımlarını tamamlamış olduğunu doğrulayın. Intune yapılandırmasının müşteri kiracısı için tamamlandıktan sonra sorun devam ederse Destek'e başvurun. Daha fazla bilgi için bkz[. Destek almak için Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

### <a name="cant-access-partner-tenant-data-in-lighthouse"></a>Deniz Feneri'nde iş ortağı kiracı verilerine erişlanamıyor

**Neden**: Deniz Feneri, yalnızca müşteri kiracılarını *görüntülemeyi ve* yönetmeyi destekler. Şu anda iş ortağı kiracıları görüntülemeyi ve *yönetmeyi* desteklemez.

**Çözüm:** İş ortağı kiracınızı görüntülemek ve yönetmek için hangi yöntemi kullanıyor olursanız olun kullanmaya devam olun.

## <a name="device-and-threat-management"></a>Cihaz ve tehdit yönetimi 

### <a name="i-dont-see-any-customer-tenant-data-on-the-device-compliance-and-threat-management-pages-of-lighthouse"></a>Deniz Feneri'nin Cihaz uyumluluğu ve Tehdit yönetimi sayfalarında müşteri kiracısı verilerini göremiyorum

**Neden 1:** Müşteri kiracısı Intune'a eklemeyi henüz tamamlamış değil. Müşteri kiracısı Intune'a eklemeyi tamamlayana kadar Deniz Feneri'nin Cihaz uyumluluğu veya Tehdit yönetimi sayfalarında müşteri kiracı verileri kullanılamaz.

**Çözüm:** Verilerini görüntülemeye çalışırken müşteri kiracısını Intune'a eklemenin tamamlandıktan sonra olduğunu doğrulayın. Intune'da ekleme işlemi tamamlandıktan sonra, Deniz Feneri'nde cihaz verileri için 4 saat bekleyin.

**Neden 2:** Müşteri kiracısı kısa süre önce Deniz Feneri'ne alındı ve veriler Deniz Feneri'ne yükleniyor.

**Çözüm:** Bir müşteri kiracısı Deniz Feneri'ne alındıktan sonra ilk müşteri verilerinizin görünmesi için 24-48 saat izin kullanın.

**Neden 3:** Müşteri kiracı cihazı yenidir ve cihaz verileri hala Deniz Feneri'ne yükleniyor.

**Çözüm:** Bir kiracı cihazı ekli olduğunda, deniz fenerinde cihaz verilerin görünmesi için 4 saat izin kullanın.

Çözüm yönergelerini takipdikten sonra Cihaz uyumluluğu ve Tehdit yönetimi sayfalarında veriler hala görünmüyorsa, Destek'e başvurun. Daha fazla bilgi için bkz[. Destek almak için Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md).

## <a name="related-content"></a>İlgili içerik

[Dosyanın bilinen Microsoft 365 Lighthouse](m365-lighthouse-known-issues.md) sorunları (makale)\
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)\
[Destek almak için yardım ve Microsoft 365 Lighthouse](m365-lighthouse-get-help-and-support.md) (makale)