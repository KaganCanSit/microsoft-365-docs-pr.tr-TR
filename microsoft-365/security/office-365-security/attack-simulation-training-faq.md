---
title: Saldırı benzetimi eğitimi dağıtımıyla ilgili dikkat edilmesi gereken noktalar ve SSS
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
description: Yöneticiler Plan 2 kuruluşları için Microsoft 365 E5 veya Microsoft Defender'da Saldırı benzetimi ve eğitimiyle ilgili dağıtımla Office 365 hakkında bilgi edinebilirsiniz.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 380241d44f667a845c47f85062d877192e1a7802
ms.sourcegitcommit: 7b83e2605895fee5c73cd1d01f4cd16e1457a69f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2021
ms.locfileid: "62999569"
---
# <a name="attack-simulation-training-deployment-considerations-and-faq"></a>Saldırı benzetimi eğitimi dağıtımıyla ilgili dikkat edilmesi gereken noktalar ve SSS

Saldırı benzetimi eğitimi, Office 365 Plan 2 kuruluşları için Microsoft 365 E5 veya Microsoft Defender'ın, gerçek dünyaya yönelik, kolay kimlik avı yükleri tarafından desteklenen kimlik avı benzetimlerinin oluşturulmasına ve yönetimine izin vererek sosyal mühendislik riskini ölçmesini ve yönetmesini sağlar. Hyper-targeted training, delivered in partnership withNova security, helps improve knowledge and change employee behavior.

Saldırı benzetimi eğitimine başlama hakkında daha fazla bilgi için bkz. [Saldırı benzetimi eğitimlerini kullanmaya başlama](attack-simulation-training-get-started.md).

Benzetim oluşturma ve zamanlama deneyiminin tamamı serbest akışlı ve kusursuz olacak şekilde tasarlasa da, kurumsal ölçekte benzetimler yapmak çoğunlukla planlamayı gerektirir. Bu makale müşterilerimizin kendi ortamlarında benzetimler çalıştırması sayesinde karşılaştığımız belirli güçlüklere yardımcı olur.

## <a name="issues-with-end-user-experiences"></a>Son kullanıcı deneyimleriyle ilgili sorunlar

### <a name="phishing-simulation-urls-blocked-by-google-safe-browsing"></a>Google Kasa Gözatma tarafından engellenen kimlik avı benzetimi URL'leri

URL'nin saygınlığı hizmeti, Saldırı benzetimi eğitimi tarafından kullanılan URL'lerin bir veya daha fazlasını güvenli olmayan olarak tanımlayabilir. Google Kasa Google Chrome'da gezinme, sanal kimlik avı URL'lerinden bazılarını Algısal **bir site devam iletisiyle** engeller. Benzetim URL'lerimize her zaman izin vermek için birçok URL itibari satıcıyla çalışırken, her zaman tam kapsamımız yok.

![Google Chrome'da algısal siteyi ön uyarı.](../../media/attack-sim-training-faq-chrome-deceptive-site-message.png)

Bu sorunun verileri etkilemeyeceğini Microsoft Edge.

Planlama aşamasının bir parçası olarak, kimlik avı kampanyasında URL'yi kullanmadan önce, desteklenen web tarayıcılarında URL'nin kullanılabilirliğini denetlemeye bakın. URL'ler Google Kasa Gözatma tarafından engellenmişse[,](https://support.google.com/chrome/a/answer/7532419) URL'lere erişim izni vermek için Google'ın bu yönergeleri izleyin.

Şu anda [Attack benzetim eğitimi tarafından kullanılan](attack-simulation-training-get-started.md) URL'lerin listesi için Saldırı benzetimi eğitimlerini kullanmaya başlama'ya bakın.

### <a name="phishing-simulation-and-admin-urls-blocked-by-network-proxy-solutions-and-filter-drivers"></a>Ağ ara sunucu çözümleri ve filtre sürücüleri tarafından engellenen kimlik avı benzetimi ve yönetici URL'leri

Hem kimlik avı benzetimi URL'leri hem de yönetici URL'leri ara güvenlik cihazlarınız veya filtreleriniz tarafından engellenmiş veya atmış olabilir. Örneğin:

- Güvenlik duvarları
- Web Uygulaması Güvenlik Duvarı (WAF) çözümleri
- Üçüncü taraf filtre sürücüleri (örneğin, çekirdek modu filtreleri)

Bu katmanda birkaç müşteri engellenmiş olarak görülen bir durumla karşıtlık yaşanır. Sorunlarla karşılaşırsanız, güvenlik cihazlarınız veya filtreleriniz tarafından taramayı atlamak için aşağıdaki URL'leri gerekli şekilde yapılandırmayı düşünebilirsiniz:

- Saldırı benzetimini kullanmaya başlama eğitimi konusunda açıklandığı gibi [benzetimi yapılan kimlik avı URL'leri](attack-simulation-training-get-started.md).
- <https://security.microsoft.com/attacksimulator>
- <https://security.microsoft.com/attacksimulationreport>
- <https://security.microsoft.com/trainingassignments>

### <a name="simulation-messages-not-delivered-to-all-targeted-users"></a>Benzetim iletileri tüm hedeflenen kullanıcılara teslim edilmedi

Benzetim e-posta iletilerini gerçekten alan kullanıcı sayısının, benzetim tarafından hedef alan kullanıcı sayısından daha az olasıdır. Hedef doğrulama kapsamında aşağıdaki kullanıcı türleri hariç tutulacak:

- Geçersiz alıcı e-posta adresleri.
- Konuk kullanıcılar.
- Artık iş yerlerinde (Azure AD) Azure Active Directory kullanıcılar.

Benzetimlere yalnızca geçerli, posta kutusu geçerli olan konuk olmayan kullanıcılar dahildir. Kullanıcıları hedeflemek için dağıtım gruplarını veya posta etkin güvenlik gruplarını kullanıyorsanız, dağıtım grubu üyelerini görüntülemek ve doğrulamak için [Exchange Online PowerShell'de](/powershell/exchange/connect-to-exchange-online-powershell) [Get-DistributionGroupMember](/powershell/module/exchange/get-distributiongroupmember) cmdlet'ini kullanabilirsiniz.

## <a name="issues-with-attack-simulation-training-reporting"></a>Saldırı benzetimi eğitimi raporlama ile ilgili sorunlar

### <a name="attack-simulation-training-reports-do-not-contain-any-activity-details"></a>Saldırı benzetimi eğitim raporları herhangi bir etkinlik ayrıntısı içermemektedir

Saldırı benzetimi eğitimi, çalışanlarınızı tehdit hazırlığı ilerleme durumu hakkında bilgi sahibi tutmak için zengin ve eyleme değiştirilebilir öngörüler ile birlikte gelir. Saldırı benzetimi eğitim raporları verilerle doldurulmazsa, denetim günlüğü aramalarının kuruluşta açık olduğunu doğrulayın (varsayılan olarak açıktır).

Denetim günlüğü araması, Saldırı benzetimi eğitimi tarafından gereklidir; böylece etkinlikler yakalanıp kaydedilebilir ve geri okunabilir. Saldırı benzetimi eğitimi için denetim günlüğü aramalarını kapatmanın sonuçları aşağıdaki şekildedir:

- Raporlama verileri tüm raporlarda kullanılamaz. Raporlar boş görünür.
- Eğitim atamaları engellendi çünkü veriler kullanılamıyor.

Denetim günlüğü aramalarını açmak için bkz [. Denetim günlüğü aramalarını açma veya kapatma](../../compliance/turn-audit-log-search-on-or-off.md).

> [!NOTE]
> Boş etkinlik ayrıntıları, kullanıcılara hiçbir E5 lisansı atanma tarafından da neden olabilir. Raporlama olaylarının yakalanır ve kaydedilirken emin olmak için etkin kullanıcıya en az bir E5 lisansının atanması gerekir.

### <a name="simulation-reports-are-not-updated-immediately"></a>Benzetim raporları hemen güncelleştirilmez

Bir kampanya başlattıktan sonra ayrıntılı benzetim raporları hemen güncelleştirilmez. Endişelenmeyin; beklenen bir davranıştır.

Her benzetim kampanyasının bir yaşam döngüsü vardır. Benzetim ilk oluşturulduğunda, benzetim **Zamanlanmış durumdadır** . Benzetim başladığında Sürüyor **durumuna geçiş** olur. Tamamlandığında, benzetim Tamamlanan durumuna **geçişler** olur.

Benzetim Zamanlanmış **durumdayken** benzetim raporları çoğunlukla boş olacaktır. Bu aşama sırasında benzetim altyapısı hedef kullanıcı e-posta adreslerini çözümliyor, dağıtım gruplarını genişletiyor ve konuk kullanıcıları listeden kaldırıyor.

![Zamanlanan durumdaki benzetimi gösteren benzetim ayrıntıları.](../../media/attack-sim-training-faq-scheduled-state.png)

Benzetim Sürüyor **aşamasına girdikçe** , raporlamaya bilgi girmeye başlayarak bilgi olduğunu fark edin:

![Devam eden durumdaki benzetimi gösteren benzetim ayrıntıları.](../../media/attack-sim-training-faq-in-progress-state.png)

Benzetim raporlarının, geçiş devam ediyor durumuna geçiş sonrasında güncelleştirilsi 30 **dakika kadar** sürebilir. Benzetim Tamamlanan durumuna ulaşana kadar rapor verileri **derlemeye devam** eder. Raporlama güncelleştirmeleri aşağıdaki aralıklarla gerçekleşir:

- İlk 60 dakikada bir, her 10 dakikada bir.
- 60 dakikada bir, 2 gün sonrası her 15 dakikada bir.
- 2 günde bir ile 7 gün arasında her 30 dakikada bir.
- 7 günde bir, 60 dakikada bir.

Genel Bakış sayfasındaki **pencere** öğeleri, kurum un benzetim tabanlı güvenlik durumunun zaman içinde hızlı bir anlık görüntüsünü sağlar. Bu widget'lar zaman içinde genel güvenlik nedenlerinizi ve yolculuğunuz yansıtması nedeniyle, her benzetim kampanyası tamamlandıktan sonra güncelleştirilir.

> [!NOTE]
> Çeşitli raporlama **sayfalarındaki** verileri ayıklamak için Dışarı Aktar seçeneğini kullanabilirsiniz.

### <a name="messages-reported-as-phishing-by-users-arent-appearing-in-simulation-reports"></a>Kullanıcılar tarafından kimlik avı olarak bildirilen iletiler benzetim raporlarında görünmüyor

Saldırı eğitimi ile ilgili benzetim raporları, kullanıcı etkinliğiyle ilgili ayrıntılar sağlar. Örneğin:

- İletinin bağlantısına tık kullanan kullanıcılar.
- Kimlik bilgilerini veren kullanıcılar.
- İletiyi kimlik avı olarak bildirilen kullanıcılar.

Kullanıcıların kimlik avı olarak bildirilen iletiler Saldırı benzetimi eğitim benzetimi raporlarında yakalanzsa, bildirilen iletilerin Microsoft'a teslimsini engelleyen bir Exchange posta akışı kuralı (aktarım kuralı olarak da bilinir) olabilir. Posta akışı kuralları, aşağıdaki e-posta adreslerine teslimi engellemez:

- junk@office365.microsoft.com
- abuse@messaging.microsoft.com
- phish@office365.microsoft.com
- not\_ junk@office365.microsoft.com

## <a name="other-frequently-asked-questions"></a>Sık sorulan diğer sorular

### <a name="q-what-is-the-recommended-method-to-target-users-for-simulation-campaigns"></a>S: Benzetim kampanyaları için kullanıcıları hedeflemek için önerilen yöntem nedir?

A: Hedef kullanıcılar için çeşitli seçenekler vardır:

- Tüm kullanıcıları dahil etmek (şu anda 40.000'den az kullanıcısı olan kuruluşlar tarafından kullanılabilir).
- Belirli kullanıcıları seçin.
- Kullanıcıları bir CSV dosyasından (satır başına bir e-posta adresi) seçin.
- Azure AD grup tabanlı hedefleme.

Hedefli kullanıcıların Azure AD grupları tarafından tanım bulunduğu kampanyaların genel olarak yönetiminin daha kolay olduğunu bulduk.

### <a name="q-are-there-any-limits-in-targeting-users-while-importing-from-a-csv-or-adding-users"></a>S: CSV'den içeri aktarma veya kullanıcı ekleme sırasında kullanıcıları hedeflemede herhangi bir sınırlama var mı?

A: ALıCıLARı BIR CSV dosyasından içeri aktarma veya benzetime tek tek alıcıları ekleme sınırı 40.000'tir.

Alıcı ayrı bir kullanıcı veya grup olabilir. Bir grup yüzlerce veya binlerce alıcı içerebilir, dolayısıyla tek tek kullanıcıların sayısına gerçek bir sınır yerleştiril değildir.

Büyük bir CSV dosyasının yönetilmesi veya birçok alıcıyı tek tek eklemek zahmetli olabilir. Azure AD gruplarının kullanımı benzetimin genel yönetimini basitleştirir.

### <a name="q-does-microsoft-provide-payloads-in-other-languages"></a>S: Microsoft diğer dillerde yüklemeler sağlar mı?

A: Şu anda 10'dan fazla dilde kullanılabilen 40'dan fazla yerelleştirilmiş yük bulunmaktadır: Çince (Basitleştirilmiş), Çince (Geleneksel), İngilizce, Fransızca, Almanca, İtalyanca, Japonca, Korece, Portekizce, Rusça, İspanyolca ve Felemenkçe. Mevcut yüklerin başka dillere doğrudan veya makine çevirisinin yanlışlıklar ve ilgi derecesini azaltacaklarını fark ettik.

Buna göre, özel yük yazma deneyimini kullanarak kendi yüklemenizi istediğiniz dilde oluşturabilirsiniz. Ayrıca belirli bir coğrafyada kullanıcıları hedeflemek için kullanılan mevcut yüklemeleri toplamanız da kesinlikle önerilir. Başka bir deyişle, saldırganların içeriği sizin için yerelleştirmesine izin verme.

### <a name="q-how-can-i-switch-to-other-languages-for-my-admin-portal-and-training-experience"></a>S: Yönetici portalım ve eğitim deneyimim için diğer dillere nasıl geçebilirsiniz?

A: Microsoft 365 veya Office 365, dil yapılandırması her kullanıcı hesabı için özel ve merkezidir. Dil ayarınızı değiştirme yönergeleri için bkz. Microsoft 365 [Kurumsal'da görüntü dilinizi ve saat diliminizi değiştirme](https://support.microsoft.com/office/6f238bff-5252-441e-b32b-655d5d85d15b).

Yapılandırma değişikliğinin tüm hizmetlerde eşitlenmesi 30 dakika kadar sürebilir.

### <a name="q-can-i-trigger-a-test-simulation-to-understand-what-it-looks-like-prior-to-launching-a-full-fledged-campaign"></a>S: Tam teşekküllü bir kampanya başlatmadan önce nasıl göründüğünü anlamak için bir test benzetimini tetikler miyim?

A: Evet, bunu! Yeni bir benzetim **oluşturmak** için sihirbazın en son Benzetimini Gözden Geçir sayfasında Test gönderme **seçeneği vardır**. Bu seçenek, o anda oturum açmış olan kullanıcıya örnek bir kimlik avı benzetimi iletisi gönderir. Gelen Kutunuzda kimlik avı iletisi doğrulandıktan sonra benzetimi gönderebilirsiniz.

![Benzetimi gözden geçir sayfasında bir test gönder düğmesi.](../../media/attack-sim-training-simulations-review-simulation.png)

### <a name="q-can-i-target-users-that-belong-to-a-different-tenant-as-part-of-the-same-simulation-campaign"></a>S: Aynı benzetim kampanyasının bir parçası olarak farklı bir kiracıya ait kullanıcıları hedef adede miyim?

C: Hayır. Şu anda, kiracılar arası benzetimler destekleneme almaktadır. Hedef kullanıcılarının hepsinin aynı kiracıda olduğunu doğrulayın. Kiracılar arası kullanıcılar veya konuk kullanıcılar benzetim kampanyasından çıkarılacaktır.

### <a name="q-how-does-region-aware-delivery-work"></a>S: Bölge bilgisi olan teslim nasıl çalışır?

A: Bölgeyi kullanan teslim, iletiyi ne zaman teslim edeceklerini belirlemek için hedefli kullanıcının posta kutusunun TimeZone özniteliğini ve 'önceden değil' mantığını kullanır. Örneğin, aşağıdaki senaryoyu düşünün:

- Pasifik saat diliminde (UTC-8) saat 07:00'de, yönetici bir kampanya oluşturur ve aynı gün saat 9:00'da başlayacak bir kampanya zamanlar.
- UserA Doğu saat dilimindedir (UTC-5).
- UserB ayrıca Pasifik saat diliminde de yer almaktadır.

Aynı gün saat 9:00'da benzetim mesajı UserB'ye gönderilir. Bölgeyi fark edilen teslimle birlikte, ileti aynı gün UserA'ya gönderilmez, çünkü Pasifik saati 09:00 Doğu saati 12:00'dır. Bunun yerine ileti, ertesi gün Doğu Avrupa saatiyle 09:00'da UserA'ya gönderilir.

Bölgeyi biliyorsanız teslim etkinleştirilen bir kampanyanın ilk çalıştırması sırasında benzetim mesajının yalnızca belirli bir saat diliminde kullanıcılara gönderilmiş gibi görünebilir. Ancak, zaman geçtiğinde ve kapsamda daha fazla kullanıcı ortaya çıktıklarında hedeflenen kullanıcılar artar.
