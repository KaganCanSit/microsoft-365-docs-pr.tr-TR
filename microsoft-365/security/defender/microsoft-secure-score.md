---
title: Microsoft Güvenlik Puanı
description: Microsoft 365 Defender portalında Microsoft Güvenli Puanını, güvenlik duruşunuzu nasıl iyileştirebileceğinizi ve güvenlik yöneticilerinin neler bekleyebileceğinizi açıklar.
keywords: microsoft güvenli puanı, güvenli puan, office 365 güvenli puanı, microsoft güvenlik puanı, Microsoft 365 Defender portalı, iyileştirme eylemleri
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
- Adm_TOC
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.technology: m365d
ms.openlocfilehash: 33e4ae46c6ec75d615cf64efe93d7b5bd8a77905
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/05/2022
ms.locfileid: "66617038"
---
# <a name="microsoft-secure-score"></a>Microsoft Güvenlik Puanı

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Microsoft Güvenli Puan, bir kuruluşun güvenlik duruşunun ölçümüdür ve daha yüksek bir sayı daha fazla geliştirme eylemi gerçekleştirildiğini gösterir. [Microsoft 365 Defender portalında](microsoft-365-defender-portal.md) bulunabilirhttps://security.microsoft.com/securescore.

Güvenli Puan önerilerini takip edin, kuruluşunuzu tehditlere karşı koruyabilirsiniz. kuruluşlar, Microsoft 365 Defender portalındaki merkezi bir panodan Microsoft 365 kimlikleri, uygulamaları ve cihazlarının güvenliğini izleyebilir ve üzerinde çalışabilir.

Güvenli Puan kuruluşlara yardımcı olur:  

* Kuruluşun güvenlik duruşunun geçerli durumunu rapor edin.
* Bulunabilirlik, görünürlük, rehberlik ve denetim sağlayarak güvenlik duruşlarını geliştirin.  
* Karşılaştırmalarla karşılaştırın ve ana performans göstergelerini (KPI' ler) oluşturun.

Güvenli puana hızlı bir genel bakış için bu videoyu izleyin.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWUPrP]

Kuruluşlar ölçümlerin ve eğilimlerin sağlam görselleştirmelerine, diğer Microsoft ürünleriyle tümleştirmeye, benzer kuruluşlarla puan karşılaştırmasına ve çok daha fazlasına erişim elde eder. Puan, üçüncü taraf çözümlerin önerilen eylemleri ele aldığı zamanları da yansıtabilir.

:::image type="content" source="../../media/secure-score/secure-score-home-page.png" alt-text="Microsoft 365 Defender portalındaki Microsoft Güvenli Puan giriş sayfası" lightbox="../../media/secure-score/secure-score-home-page.png":::

## <a name="how-it-works"></a>Nasıl çalışır?

Aşağıdaki eylemler için size puan verilir:

- Önerilen güvenlik özelliklerini yapılandırma
- Güvenlikle ilgili görevleri gerçekleştirme
- İyileştirme eylemini üçüncü taraf bir uygulama veya yazılımla veya alternatif bir risk azaltmayla ele alma

Bazı iyileştirme eylemleri yalnızca tam olarak tamamlandığında puan verir. Bazı cihazlar veya kullanıcılar için tamamlandıysa bazıları kısmi puan verir. İyileştirme eylemlerinden birini gerçekleştiremiyor veya uygulamak istemiyorsanız riski veya kalan riski kabul etmeyi seçebilirsiniz.

Desteklenen Microsoft ürünlerinden biri için lisansınız varsa bu ürünlerle ilgili önerileri görürsünüz. Lisans sürümü, abonelik veya plandan bağımsız olarak bir ürün için tüm olası iyileştirmeleri gösteririz. Bu şekilde en iyi güvenlik uygulamalarını anlayabilir ve puanınızı geliştirebilirsiniz. Güvenli Puan ile temsil edilen mutlak güvenlik duruşunuz, kuruluşunuzun belirli bir ürün için sahip olduğu lisanslar ne olursa olsun aynı kalır. Güvenliğin kullanılabilirlik ile dengelenmesi gerektiğini ve her önerinin ortamınızda çalışamadığını unutmayın.

Puanınız, görselleştirmeler ve iyileştirme eylem sayfalarında sunulan bilgileri yansıtacak şekilde gerçek zamanlı olarak güncelleştirilir. Güvenli Puan ayrıca her eylem için elde edilen puanlarınızla ilgili sistem verilerini almak için günlük olarak eşitlenir.

### <a name="key-scenarios"></a>Önemli senaryolar

- [Geçerli puanınızı denetleyin](microsoft-secure-score-improvement-actions.md#check-your-current-score)
- [Puanınızı sizinki gibi kuruluşlarla karşılaştırın](microsoft-secure-score-history-metrics-trends.md#compare-your-score-to-organizations-like-yours)
- [İyileştirme eylemlerini görüntüleme ve eylem planına karar verme](microsoft-secure-score-improvement-actions.md#take-action-to-improve-your-score)
- [Araştırmak veya uygulamak için iş akışları başlatma](microsoft-secure-score-improvement-actions.md#view-improvement-action-details)

### <a name="how-improvement-actions-are-scored"></a>İyileştirme eylemleri nasıl puanlanmıştır?

Her iyileştirme eylemi 10 puan veya daha azdır ve çoğu ikili bir şekilde puanlanır. Yeni bir ilke oluşturma veya belirli bir ayarı açma gibi iyileştirme eylemini uygularsanız, noktaların %100'lerini alırsınız. Diğer iyileştirme eylemleri için puanlar toplam yapılandırmanın yüzdesi olarak verilir.

Örneğin, bir geliştirme eylemi, çok faktörlü kimlik doğrulaması ile tüm kullanıcılarınızı koruyarak 10 puan elde ettiğinizi belirtir. Toplam 100 kullanıcıdan yalnızca 50'sini koruduğunuz için 5 puanlık kısmi puan alırsınız (50 korumalı / 100 toplam * 10 maksimum pts = 5 pt).

### <a name="products-included-in-secure-score"></a>Güvenli Puana dahil olan ürünler

Şu anda aşağıdaki ürünler için öneriler vardır:

- Microsoft 365 (Exchange Online dahil)
- Azure Active Directory
- Uç Nokta için Microsoft Defender
- Kimlik için Microsoft Defender
- Bulut Uygulamaları için Defender
- Microsoft Teams

Diğer güvenlik ürünlerine yönelik öneriler yakında sunulacaktır. Öneriler, her ürünle ilişkili tüm saldırı yüzeylerini kapsamaz, ancak iyi bir temeldir. Ayrıca, geliştirme eylemlerini üçüncü taraf veya alternatif risk azaltma kapsamında olarak işaretleyebilirsiniz.

### <a name="security-defaults"></a>Güvenlik varsayılanları

Microsoft Güvenli Puan, [Azure Active Directory'de güvenlik varsayılanlarını](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults) destekleyecek şekilde iyileştirme eylemlerini güncelleştirdi ve bu da yaygın saldırılar için önceden yapılandırılmış güvenlik ayarlarıyla kuruluşunuzun korunmasına yardımcı olmasını kolaylaştırdı.

Güvenlik varsayılanlarını açarsanız, aşağıdaki iyileştirme eylemleri için tam puan alırsınız:

- Tüm kullanıcıların güvenli erişim için çok faktörlü kimlik doğrulamasını tamamlayabildiğine emin olun (9 nokta)
- Yönetim rolleri için MFA gerektir (10 nokta)
- Eski kimlik doğrulamasını engellemek için ilkeyi etkinleştirme (7 nokta)

>[!IMPORTANT]
>Güvenlik varsayılanları, "oturum açma riski ilkesi" ve "kullanıcı riski ilkesi" geliştirme eylemlerine benzer güvenlik özellikleri içerir. Bu ilkeleri güvenlik varsayılanlarının üzerine ayarlamak yerine durumlarını "Alternatif risk azaltma yoluyla çözümlendi" olarak güncelleştirmenizi öneririz.

## <a name="required-permissions"></a>Gerekli izinler

Microsoft Güvenli Puanı'na erişim iznine sahip olmak için Azure Active Directory'de aşağıdaki rollerden birine atanmış olmanız gerekir.

### <a name="read-and-write-roles"></a>Rolleri okuma ve yazma

Okuma ve yazma erişimiyle değişiklik yapabilir ve Güvenli Puan ile doğrudan etkileşim kurabilirsiniz. Diğer kullanıcılara da salt okunur erişim atayabilirsiniz.

* Genel yönetici
* Güvenlik yöneticisi
* Exchange yöneticisi
* SharePoint yöneticisi

### <a name="read-only-roles"></a>Salt okunur roller

Salt okunur erişim sayesinde, bir iyileştirme eyleminin durumunu veya notlarını düzenleyemez, puan bölgelerini düzenleyemez veya özel karşılaştırmaları düzenleyemezsiniz.

* Yardım masası yöneticisi
* Kullanıcı yöneticisi
* Hizmet destek yöneticisi
* Güvenlik gözetmeni
* Güvenlik operatörü
* Genel gözetmen

## <a name="risk-awareness"></a>Risk farkındalığı

Microsoft Güvenli Puan, sistem yapılandırmalarına, kullanıcı davranışına ve güvenlikle ilgili diğer ölçümlere göre güvenlik duruşunuzun sayısal bir özetidir. Sisteminizin veya verilerinizin ihlal edilme olasılığının mutlak ölçümü değildir. Bunun yerine, Microsoft ortamınızda ihlal edilme riskini dengelemeye yardımcı olabilecek güvenlik denetimlerini benimsediğiniz kapsamı temsil eder. Hiçbir çevrimiçi hizmetin güvenlik ihlallerinden etkilenmez ve güvenlik puanı hiçbir şekilde güvenlik ihlaline karşı bir garanti olarak yorumlanamaz.

## <a name="we-want-to-hear-from-you"></a>Sizden haber almak istiyoruz

Herhangi bir sorununuz varsa [Güvenlik, Gizlilik & Uyumluluk](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) topluluğuna göndererek bize bildirin. Topluluğu izliyoruz ve yardım sağlayacağız.

## <a name="related-resources"></a>İlgili kaynaklar

- [Güvenlik duruşlarınızı değerlendirin](microsoft-secure-score-improvement-actions.md)
- [Microsoft Güvenli Puan geçmişinizi izleme ve hedefleri karşılama](microsoft-secure-score-history-metrics-trends.md)
- [Yapılacak yenilikler](microsoft-secure-score-whats-coming.md)
- [Yenilikler](microsoft-secure-score-whats-new.md)
