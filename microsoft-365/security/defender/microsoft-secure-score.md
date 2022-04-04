---
title: Microsoft Güvenlik Puanı
description: Güvenlik portalında Microsoft Güvenli Puanı Microsoft 365 Defender, güvenlik nedenlerinizi nasıl geliştirin ve güvenlik yöneticilerinin neler beklemesi olduğunu açıklar.
keywords: microsoft güvenli puan, güvenli puan, office 365 güvenli puanı, microsoft güvenlik puanı, Microsoft 365 Defender portalı, geliştirme eylemleri
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
ms.openlocfilehash: ed80d57d25fea2f3c19b6fe6363f993569c68a92
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499458"
---
# <a name="microsoft-secure-score"></a>Microsoft Güvenlik Puanı

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Microsoft Güvenli Puanı, kuruluşun güvenlik mezralarının bir ölçümüdür ve yapılan daha fazla geliştirme eylemine işaret eden daha yüksek bir sayıdır. Microsoft 365 Defender https://security.microsoft.com/securescore [portalında bulunabilir](microsoft-365-defender.md#the-microsoft-365-defender-portal).

Güvenli Puan önerilerine göre, kuruluş tehditlere karşı koruma suz. Kuruluşlar, Microsoft 365 Defender portalında yer alan merkezi bir panodan kimliklerinin, uygulamalarının ve cihazlarının güvenliğini Microsoft 365 ve üzerinde çalışır.

Güvenli Puan kuruluşlara yardımcı olur:  

* Kuruluşun güvenlik durumunu raporla.
* Keşfederlik, görünürlük, rehberlik ve denetim sağlayarak güvenlik sorumluluklarını geliştirin.  
* Karşılaştırmalar ile karşılaştırın ve ana performans göstergeleri (KPY) ortayayın.

Güvenli puan'a hızlı bir genel bakış için bu videoyu izleyin.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWUPrP]

Kuruluşlar, ölçümlerin ve eğilimlerin güçlü görselleştirmelerine, diğer Microsoft ürünleriyle tümleştirmeye, benzer kuruluşlarla puan karşılaştırmalarına ve daha birçok öğeye erişim elde etmektedir. Puan, üçüncü taraf çözümlerinin önerilen eylemleri çözümlediğiniz durumlarını da yansıtabilirsiniz.

:::image type="content" source="../../media/secure-score/secure-score-home-page.png" alt-text="Web portalının Microsoft Güvenli Puanı Microsoft 365 Defender sayfası" lightbox="../../media/secure-score/secure-score-home-page.png":::

## <a name="how-it-works"></a>Nasıl çalışır?

Aşağıdaki eylemler için size puan verilir:

- Önerilen güvenlik özelliklerini yapılandırma
- Güvenlikle ilgili görevler yapma
- Üçüncü taraf bir uygulama veya yazılım ya da alternatif bir azaltma ile iyileştirme eylemlerini ele

Bazı geliştirme eylemleri yalnızca tümüyle tamamlandığında puanlar sağlar. Bazı cihazlarda veya kullanıcılarda tamamlanan kısmi puanlar vardır. Geliştirme eylemlerinden birini gerçekleştiremenizi ya da üzerinde işlem yapmak istemenizi istemiyorsanız, riski veya kalan riski kabul etmeye seçebilirsiniz.

Desteklenen Microsoft ürünlerinden biri için lisansınız varsa, o ürünler için önerilere bakın. Lisans sürümü, aboneliği veya planına bakılmaksızın, bir ürün için tüm olası iyileştirmeleri gösteririz. Bu şekilde, güvenlikle ilgili en iyi uygulamaları anlıyoruz ve puanınızı geliştireceğiz. Güvenli Puan ile temsil edilen mutlak güvenlik nedenniz, belirli bir ürün için kuruma ait lisanslar ne olursa olsun aynı kalır. Güvenliğin kullanılabilirlik ile dengelenmeleri gerektiğini ve her önerinin ortamınıza uygun olmadığını unutmayın.

Puanınız, görsel öğelerde ve geliştirme eylem sayfalarında sunulan bilgileri yansıtacak şekilde gerçek zamanlı olarak güncelleştirilir. Güvenli Puan, her eylem için elde edilen puanlar hakkında sistem verilerini almak için de günlük olarak eşitler.

### <a name="key-scenarios"></a>Önemli senaryolar

- [Geçerli puanınızı denetleme](microsoft-secure-score-improvement-actions.md#check-your-current-score)
- [Puanınızı sizinki gibi kuruluşlarla karşılaştırma](microsoft-secure-score-history-metrics-trends.md#compare-your-score-to-organizations-like-yours)
- [Geliştirme eylemlerini görüntüleme ve eylem planına karar verme](microsoft-secure-score-improvement-actions.md#take-action-to-improve-your-score)
- [Araştırma veya uygulama için iş akışlarını başlatma](microsoft-secure-score-improvement-actions.md#view-improvement-action-details)

### <a name="how-improvement-actions-are-scored"></a>Geliştirme eylemleri nasıl puanlandı

Her geliştirme eylemi 10 puana veya daha kısa sürede değerindedir ve bunların çoğu ikili biçimde puanlandı. Yeni ilke oluşturma veya belirli bir ayarı açma gibi geliştirme eylemlerini gerçekleştirseniz, puanların %100'ını elde etmiş sayılırsınız. Diğer geliştirme eylemleri için puanlar toplam yapılandırmanın yüzdesi olarak verilir.

Örneğin, geliştirme amaçlı bir eylem, tüm kullanıcılarınızı çok faktörlü kimlik doğrulamasıyla koruyarak 10 puan alasınız. Toplam 100 kullanıcıdan yalnızca 50'sinde korumalısınız, bu nedenle 5 puanlık (50 korumalı / 100 toplam * 10 max pts = 5 pts) kısmi puan alırsınız.

### <a name="products-included-in-secure-score"></a>Güvenli Puan'a dahil edilen ürünler

Şu anda aşağıdaki ürünlerle ilgili öneriler vardır:

- Microsoft 365 (diğer Exchange Online)
- Azure Active Directory
- Uç Nokta için Microsoft Defender
- Kimlik için Microsoft Defender
- Bulut Uygulamaları için Defender
- Microsoft Teams

Öneriler güvenlik ürünleri için ürünler yakında hazır olacak. Öneriler, her ürünle ilişkili tüm saldırı yüzeylerini kaplamaz, ancak iyi bir taban çizgisidir. Ayrıca, geliştirme eylemlerini üçüncü taraf veya alternatif bir azaltma kapsamında olarak işaretabilirsiniz.

### <a name="security-defaults"></a>Güvenlik varsayılanları

Microsoft Güvenli Puanı'nın, Azure Active Directory'de [](/azure/active-directory/fundamentals/concept-fundamentals-security-defaults)güvenlik varsayılanlarını desteklemeye yönelik güncelleştirilmiş geliştirme eylemleri vardır ve bu da yaygın saldırılar için önceden yapılandırılmış güvenlik ayarlarıyla organizasyonu korumaya yardımcı olur.

Güvenlik varsayılanlarını kullanırsanız, aşağıdaki geliştirme eylemleri için size tam puan verilecektir:

- Tüm kullanıcıların, güvenli erişim için çok faktörlü kimlik doğrulamasını tamamlayama (9 nokta)
- Yönetim rolleri için MFA gerektir (10 puan)
- Eski kimlik doğrulamayı engellemek için ilkeyi etkinleştir (7 puan)

>[!IMPORTANT]
>Güvenlik varsayılanları, "oturum açma riski ilkesi" ve "kullanıcı risk ilkesi" geliştirme eylemlerine benzer güvenlik özellikleri içerir. Bu ilkeleri güvenlik varsayılanları yerine "Alternatif etki azaltma yoluyla çözümlendi" durumuna güncelleştirmenizi öneririz.

## <a name="required-permissions"></a>Gerekli izinler

Microsoft Secure Score'a erişim iznine sahip olmak için bu puanlar için size aşağıdaki Azure Active Directory.

### <a name="read-and-write-roles"></a>Rolleri okuma ve yazma

Okuma ve yazma erişimiyle, değişiklik yapabilirsiniz ve Güvenli Puan ile doğrudan etkileşim kurabilirsiniz. Ayrıca, diğer kullanıcılara salt okunur erişim de atabilirsiniz.

* Genel yönetici
* Güvenlik yöneticisi
* Exchange yöneticisi
* SharePoint yöneticisi

### <a name="read-only-roles"></a>Salt okunur roller

Salt okunur erişimle, iyileştirme eylemi, puan bölgeleri düzenleme veya özel karşılaştırmaları düzenleme durumlarını veya notları düzenleyemezsiniz.

* Yardım masası yöneticisi
* Kullanıcı yöneticisi
* Hizmet destek yöneticisi
* Güvenlik gözetmeni
* Güvenlik operatörü
* Genel okuyucu

## <a name="risk-awareness"></a>Risk farkındalığı

Microsoft Güvenli Puanı; sistem yapılandırmalarına, kullanıcı davranışına ve güvenlikle ilgili diğer ölçümlere dayalı olarak güvenlik nedennizin sayısal bir özetidir. Bu, sistem veya verilerinizin ihlal olma ihtimalinin mutlak bir ölçümü değildir. Bunun yerine, Microsoft ortamında ihlal olma riskini dengelemeye yardımcı olacak güvenlik denetimlerine sahip olma kapsamınızı temsil eder. Hiçbir çevrimiçi hizmet güvenlik ihlallerinden uzak değildir ve güvenlik puanı herhangi bir şekilde güvenlik ihlallerine karşı bir garanti olarak yorumlanmayacaktır.

## <a name="we-want-to-hear-from-you"></a>Bize haber almak için

Herhangi bir sorun varsa, Güvenlik, Gizlilik ve Uyumluluk topluluğuna [göndererek & sağlayın](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) . Topluluğu izliyoruz ve yardım sağacağız.

## <a name="related-resources"></a>İlgili kaynaklar

- [Güvenlik duruşlarınızı değerlendirin](microsoft-secure-score-improvement-actions.md)
- [Microsoft Güvenli Puan geçmişinizi izleme ve hedefleri karşılama](microsoft-secure-score-history-metrics-trends.md)
- [Yapılacak yenilikler](microsoft-secure-score-whats-coming.md)
- [Yeni gelenler](microsoft-secure-score-whats-new.md)
