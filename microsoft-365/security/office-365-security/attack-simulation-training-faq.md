---
title: Saldırı simülasyonu eğitimi dağıtımıyla ilgili dikkat edilmesi gerekenler ve SSS
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection: m365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, Microsoft 365 E5 Office 365 için Microsoft Defender veya Plan 2 kuruluşlarında saldırı simülasyonu ve eğitimiyle ilgili dağıtım konuları ve sık sorulan sorular hakkında bilgi edinebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4145dcd073ec97c43ac64eecdbd25c48612a9b83
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65649031"
---
# <a name="attack-simulation-training-deployment-considerations-and-faq"></a>Saldırı simülasyonu eğitimi dağıtımıyla ilgili dikkat edilmesi gerekenler ve SSS

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Office 365 için Microsoft Defender plan 2](defender-for-office-365.md)

Saldırı simülasyonu eğitimi, Microsoft 365 E5 veya Office 365 için Microsoft Defender Plan 2 kuruluşlarının gerçek dünya, silah dışı kimlik avı yükleri tarafından desteklenen kimlik avı simülasyonlarının oluşturulmasına ve yönetilmesine izin vererek sosyal mühendislik riskini ölçmesine ve yönetmesine olanak tanır. Terranova güvenliğiyle ortaklaşa sunulan hiper hedefli eğitim, bilginin geliştirilmesine ve çalışan davranışının değiştirilmesine yardımcı olur.

Saldırı simülasyonu eğitimine başlama hakkında daha fazla bilgi için bkz. [Saldırı simülasyonu eğitimini kullanma Kullanmaya başlayın](attack-simulation-training-get-started.md).

Simülasyon oluşturma ve zamanlama deneyiminin tamamı serbest akışlı ve sorunsuz olacak şekilde tasarlanmış olsa da, simülasyonların kurumsal ölçekte çalıştırılması genellikle planlama gerektirir. Bu makale, müşterilerimiz simülasyonları kendi ortamlarında çalıştırırken gördüğümüz belirli zorlukların giderilmesine yardımcı olur.

## <a name="issues-with-end-user-experiences"></a>Son kullanıcı deneyimleriyle ilgili sorunlar

### <a name="phishing-simulation-urls-blocked-by-google-safe-browsing"></a>Google Kasa Gözatma tarafından engellenen kimlik avı simülasyonu URL'leri

URL saygınlığı hizmeti, Saldırı simülasyonu eğitimi tarafından güvenli olmayan url'ler olarak kullanılan bir veya daha fazla URL'yi tanımlayabilir. Google Chrome'da Google Kasa Gözatma, **yanıltıcı bir site ileri** iletisiyle sanal kimlik avı URL'lerinden bazılarını engeller. Simülasyon URL'lerimize her zaman izin vermek için birçok URL saygınlığı satıcısıyla çalışsak da, her zaman tam kapsamlı bir kapsamımız yoktur.

:::image type="content" source="../../media/attack-sim-training-faq-chrome-deceptive-site-message.png" alt-text="Google Chrome'da yanıltıcı site ileri uyarısı" lightbox="../../media/attack-sim-training-faq-chrome-deceptive-site-message.png":::

Bu sorunun Microsoft Edge etkilemediğini unutmayın.

Planlama aşamasının bir parçası olarak, URL'yi bir kimlik avı kampanyasında kullanmadan önce desteklenen web tarayıcılarınızda URL'nin kullanılabilirliğini denetlemeyi unutmayın. URL'ler Google Kasa Gözatma tarafından engelleniyorsa, URL'lere erişime izin vermek için Google'ın [bu yönergelerini izleyin](https://support.google.com/chrome/a/answer/7532419).

Şu anda Saldırı simülasyonu eğitimi tarafından kullanılan URL'lerin listesi için Saldırı [simülasyonu eğitimini kullanarak Kullanmaya başlayın](attack-simulation-training-get-started.md) bakın.

### <a name="phishing-simulation-and-admin-urls-blocked-by-network-proxy-solutions-and-filter-drivers"></a>Ağ ara sunucusu çözümleri ve filtre sürücüleri tarafından engellenen kimlik avı simülasyonu ve yönetici URL'leri

Hem kimlik avı simülasyonu URL'leri hem de yönetici URL'leri, ara güvenlik cihazlarınız veya filtreleriniz tarafından engellenebilir veya bırakılabilir. Örneğin:

- Güvenlik duvar -ları
- Web Uygulaması Güvenlik Duvarı (WAF) çözümleri
- Üçüncü taraf filtre sürücüleri (örneğin, çekirdek modu filtreleri)

Bu katmanda birkaç müşterinin engellendiğini gördük ancak bu gerçekleşir. Sorunlarla karşılaşırsanız, güvenlik cihazlarınız veya filtreleriniz tarafından taramayı atlamak için aşağıdaki URL'leri gerektiği gibi yapılandırmayı göz önünde bulundurun:

- [Saldırı simülasyonu eğitimi kullanılarak Kullanmaya başlayın'da](attack-simulation-training-get-started.md) açıklandığı gibi sanal kimlik avı URL'leri.
- <https://security.microsoft.com/attacksimulator>
- <https://security.microsoft.com/attacksimulationreport>
- <https://security.microsoft.com/trainingassignments>

### <a name="simulation-messages-not-delivered-to-all-targeted-users"></a>Simülasyon iletileri tüm hedeflenen kullanıcılara teslim edilmedi

Simülasyon e-posta iletilerini gerçekten alan kullanıcı sayısının simülasyon tarafından hedeflenen kullanıcı sayısından az olması mümkündür. Aşağıdaki kullanıcı türleri, hedef doğrulama kapsamında dışlanır:

- Geçersiz alıcı e-posta adresleri.
- Konuk kullanıcılar.
- artık Azure Active Directory (Azure AD) etkin olmayan kullanıcılar.

Simülasyonlara yalnızca geçerli, geçerli posta kutusu olan konuk olmayan kullanıcılar dahil edilecek. Kullanıcıları hedeflemek için dağıtım grupları veya posta etkin güvenlik grupları kullanıyorsanız, dağıtım grubu üyelerini görüntülemek ve doğrulamak için [Exchange Online PowerShell'de](/powershell/exchange/connect-to-exchange-online-powershell) [Get-DistributionGroupMember](/powershell/module/exchange/get-distributiongroupmember) cmdlet'ini kullanabilirsiniz.

## <a name="issues-with-attack-simulation-training-reporting"></a>Saldırı simülasyonu eğitim raporlamasıyla ilgili sorunlar

### <a name="attack-simulation-training-reports-do-not-contain-any-activity-details"></a>Saldırı simülasyonu eğitim raporları herhangi bir etkinlik ayrıntısı içermiyor

Saldırı simülasyonu eğitimi, çalışanlarınızın tehdit hazırlığı ilerleme durumu hakkında sizi bilgilendiren zengin ve eyleme dönüştürülebilir içgörülerle birlikte gelir. Saldırı simülasyonu eğitim raporları verilerle doldurulmazsa, kuruluşunuzda denetim günlüğü aramanın açık olduğunu doğrulayın (varsayılan olarak açıktır).

Olayların yakalanabilmesi, kaydedilebilmesi ve okunabilmesi için Saldırı benzetimi eğitimi için denetim günlüğü araması gereklidir. Denetim günlüğü aramasını kapatmak, Saldırı simülasyonu eğitimi için aşağıdaki sonuçlara neden olur:

- Raporlama verileri tüm raporlarda kullanılamaz. Raporlar boş görünür.
- Veriler kullanılamadığından eğitim atamaları engellenir.

Denetim günlüğü aramasını açmak için bkz [. Denetim günlüğü aramasını açma veya kapatma](../../compliance/turn-audit-log-search-on-or-off.md).

> [!NOTE]
> Boş etkinlik ayrıntıları, kullanıcılara E5 lisansı atanmadığından da kaynaklanabilir. Raporlama olaylarının yakalanıp kaydedildiğinden emin olmak için etkin bir kullanıcıya en az bir E5 lisansı atandığını doğrulayın.

### <a name="simulation-reports-are-not-updated-immediately"></a>Simülasyon raporları hemen güncelleştirilmez

Ayrıntılı simülasyon raporları, bir kampanya başlattıktan hemen sonra güncelleştirilmez. Endişelenmeyin; bu davranış beklenir.

Her simülasyon kampanyasının bir yaşam döngüsü vardır. İlk oluşturulduğunda simülasyon **Zamanlanmış** durumunda olur. Simülasyon başlatıldığında Devam ediyor durumuna geçiş **yapılır** . Tamamlandığında, simülasyon **Tamamlandı** durumuna geçiş yapılır.

Bir simülasyon **Zamanlanmış** durumundayken, simülasyon raporları çoğunlukla boş olur. Bu aşamada simülasyon altyapısı hedef kullanıcı e-posta adreslerini çözümleme, dağıtım gruplarını genişletme, konuk kullanıcıları listeden kaldırma gibi işlemleri tamamlar:

:::image type="content" source="../../media/attack-sim-training-faq-scheduled-state.png" alt-text="Simülasyonu Zamanlanmış durumda gösteren simülasyon ayrıntıları" lightbox="../../media/attack-sim-training-faq-scheduled-state.png":::

Simülasyon **Devam Ediyor** aşamasına girdikten sonra, bilgilerin raporlamaya girmeye başladığını fark edeceksiniz:

:::image type="content" source="../../media/attack-sim-training-faq-in-progress-state.png" alt-text="Simülasyonu Sürüyor durumunda gösteren simülasyon ayrıntıları" lightbox="../../media/attack-sim-training-faq-in-progress-state.png":::

Devam **ediyor** durumuna geçiş sonrasında tek tek simülasyon raporlarının güncelleştirilmiş olması 30 dakika kadar sürebilir. Simülasyon **Tamamlandı** durumuna ulaşana kadar rapor verileri dermeye devam eder. Raporlama güncelleştirmeleri aşağıdaki aralıklarla gerçekleşir:

- İlk 60 dakika boyunca her 10 dakikada bir.
- 2 güne kadar 60 dakika sonra 15 dakikada bir.
- 2 günden 7 güne kadar 30 dakikada bir.
- 7 günden sonra 60 dakikada bir.

**Genel Bakış** sayfasındaki pencere öğeleri, kuruluşunuzun simülasyon tabanlı güvenlik duruşunun zaman içinde hızlı bir anlık görüntüsünü sağlar. Bu pencere öğeleri genel güvenlik duruşunuzu ve zaman içindeki yolculuğunuzu yansıttığı için her simülasyon kampanyası tamamlandıktan sonra güncelleştirilir.

> [!NOTE]
> Verileri ayıklamak için çeşitli raporlama sayfalarında **Dışarı Aktar** seçeneğini kullanabilirsiniz.

### <a name="messages-reported-as-phishing-by-users-arent-appearing-in-simulation-reports"></a>Kullanıcılar tarafından kimlik avı olarak bildirilen iletiler simülasyon raporlarında görünmüyor

Saldırı simülatörü eğitimindeki simülasyon raporları, kullanıcı etkinliğiyle ilgili ayrıntıları sağlar. Örneğin:

- İletideki bağlantıya tıklayan kullanıcılar.
- Kimlik bilgilerini veren kullanıcılar.
- İletiyi kimlik avı olarak bildiren kullanıcılar.

Kullanıcıların kimlik avı olarak bildirdiği iletiler Saldırı simülasyonu eğitim simülasyonu raporlarında yakalanmazsa, bildirilen iletilerin Microsoft'a teslimini engelleyen bir Exchange posta akışı kuralı (aktarım kuralı olarak da bilinir) olabilir. Posta akışı kurallarının aşağıdaki e-posta adreslerine teslimi engellemediğini doğrulayın:

- junk@office365.microsoft.com
- abuse@messaging.microsoft.com
- phish@office365.microsoft.com
- değil\_ junk@office365.microsoft.com

## <a name="other-frequently-asked-questions"></a>Sık sorulan diğer sorular

### <a name="q-what-is-the-recommended-method-to-target-users-for-simulation-campaigns"></a>S: Simülasyon kampanyaları için kullanıcıları hedeflemek için önerilen yöntem nedir?

Y: Hedef kullanıcılar için çeşitli seçenekler mevcuttur:

- Tüm kullanıcıları dahil edin (şu anda 40.000'den az kullanıcısı olan kuruluşlar tarafından kullanılabilir).
- Belirli kullanıcıları seçin.
- Csv dosyasından kullanıcıları seçin (satır başına bir e-posta adresi).
- Grup tabanlı hedeflemeyi Azure AD.

Hedeflenen kullanıcıların Azure AD grupları tarafından tanımlandığı kampanyaların genel olarak daha kolay yönetildiğini tespit ettik.

### <a name="q-are-there-any-limits-in-targeting-users-while-importing-from-a-csv-or-adding-users"></a>S: CSV'den içeri aktarma veya kullanıcı ekleme sırasında kullanıcıları hedefleme konusunda herhangi bir sınır var mı?

Y: Alıcıları CSV dosyasından içeri aktarma veya simülasyona tek tek alıcı ekleme sınırı 40.000'dir.

Alıcı tek bir kullanıcı veya grup olabilir. Bir grup yüzlerce veya binlerce alıcı içerebilir, bu nedenle tek tek kullanıcı sayısına gerçek bir sınır uygulanmaz.

Büyük bir CSV dosyasını yönetmek veya çok sayıda alıcı eklemek zahmetli olabilir. Azure AD gruplarının kullanılması simülasyonun genel yönetimini basitleştirir.

### <a name="q-does-microsoft-provide-payloads-in-other-languages"></a>S: Microsoft başka dillerde yük sağlar mı?

Y: Şu anda 10'dan fazla dilde 40'dan fazla yerelleştirilmiş yük mevcuttur: Çince (Basitleştirilmiş), Çince (Geleneksel), İngilizce, Fransızca, Almanca, İtalyanca, Japonca, Korece, Portekizce, Rusça, İspanyolca ve Felemenkçe. Mevcut yüklerin diğer dillere doğrudan veya makine çevirilerinin yanlışlığa ve ilginin azalmasına yol açacağını fark ettik.

Bunun yanı sıra, özel yük yazma deneyimini kullanarak istediğiniz dilde kendi yükünüzü oluşturabilirsiniz. Ayrıca belirli bir coğrafyadaki kullanıcıları hedeflemek için kullanılan mevcut yükleri toplamanızı kesinlikle öneririz. Başka bir deyişle, saldırganların içeriği sizin için yerelleştirmesine izin verin.

### <a name="q-how-can-i-switch-to-other-languages-for-my-admin-portal-and-training-experience"></a>S: Yönetici portalım ve eğitim deneyimim için diğer dillere nasıl geçiş yapabilirim?

Y: Microsoft 365 veya Office 365 dil yapılandırması her kullanıcı hesabı için özel ve merkezidir. Dil ayarınızı değiştirme yönergeleri için bkz. [İş için Microsoft 365'da görüntüleme dilinizi ve saat diliminizi değiştirme](https://support.microsoft.com/office/6f238bff-5252-441e-b32b-655d5d85d15b).

Yapılandırma değişikliğinin tüm hizmetler arasında eşitlenmesi 30 dakika kadar sürebilir.

### <a name="q-can-i-trigger-a-test-simulation-to-understand-what-it-looks-like-prior-to-launching-a-full-fledged-campaign"></a>S: Tam kapsamlı bir kampanya başlatmadan önce nasıl göründüğünü anlamak için bir test simülasyonu tetikleyebilir miyim?

Y: Evet yapabilirsiniz! Yeni bir simülasyon oluşturmak için sihirbazın en son **Simülasyonu Gözden Geçir** sayfasında **Test gönder** seçeneği vardır. Bu seçenek, şu anda oturum açmış olan kullanıcıya örnek bir kimlik avı benzetimi iletisi gönderir. Gelen Kutunuzda kimlik avı iletisini doğruladıktan sonra simülasyonu gönderebilirsiniz.

:::image type="content" source="../../media/attack-sim-training-simulations-review-simulation.png" alt-text="Simülasyonu gözden geçir sayfasındaki Test gönder düğmesi" lightbox="../../media/attack-sim-training-simulations-review-simulation.png":::

### <a name="q-can-i-target-users-that-belong-to-a-different-tenant-as-part-of-the-same-simulation-campaign"></a>S: Aynı simülasyon kampanyasının bir parçası olarak farklı bir kiracıya ait kullanıcıları hedefleyebilir miyim?

C: Hayır. Şu anda kiracılar arası simülasyonlar desteklenmemektedir. Hedeflenen tüm kullanıcılarınızın aynı kiracıda olduğunu doğrulayın. Tüm kiracılar arası kullanıcılar veya konuk kullanıcılar simülasyon kampanyasının dışında tutulur.

### <a name="q-how-does-region-aware-delivery-work"></a>S: Bölge tanımalı teslim nasıl çalışır?

Y: Bölge algılamalı teslim, iletinin ne zaman teslim edileceğini belirlemek için hedeflenen kullanıcının posta kutusunun TimeZone özniteliğini ve 'önce değil' mantığını kullanır. Örneğin, aşağıdaki senaryoyu göz önünde bulundurun:

- Pasifik saat diliminde (UTC-8) saat 07:00'de bir yönetici bir kampanya oluşturur ve aynı gün saat 09:00'da başlayacak şekilde zamanlar.
- UserA, Doğu saat diliminde (UTC-5) yer alır.
- UserB aynı zamanda Pasifik saat dilimindedir.

Aynı gün saat 09:00'da simülasyon iletisi UserB'ye gönderilir. Bölgeye duyarlı teslimde, 09:00 Pasifik saati Doğu saatiyle 23:00 olduğundan ileti aynı gün UserA'ya gönderilmez. Bunun yerine, ileti bir sonraki gün Doğu saatiyle 09:00'da UserA'ya gönderilir.

Bu nedenle, bölgeye duyarlı teslimin etkinleştirildiği bir kampanyanın ilk çalıştırmasında simülasyon iletisinin yalnızca belirli bir saat dilimindeki kullanıcılara gönderildiği görünebilir. Ancak, zaman geçtikçe ve daha fazla kullanıcı kapsama girdikçe, hedeflenen kullanıcılar artar.
