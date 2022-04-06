---
title: Office 365 ve güvenlik için Microsoft Defender dahil Office 365 Güvenliği Exchange Online Protection
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 07/21/2021
audience: Admin
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Güvenlik Office 365 ve 2 için EOP'den Office 365 Defender'a, Standart ile Katı güvenlik yapılandırmaları ve daha fazlası. Sahip olduğunuz özellikleri ve özelliklerinizin nasıl güvenli olduğunu anlıyoruz.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 31eaa1c2ae44799c15a782d121ad2068eaa40c25
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681116"
---
# <a name="microsoft-defender-for-office-365-security-overview"></a>Güvenlik için Microsoft Defender Office 365 a genel bakış

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)

Bu makalede size Buluttaki güvenlik özelliklerini nasıl Office 365 Microsoft Defender'ı tanıtacak. Bir Güvenlik İşlemleri Merkezi'nde yer alan bir Güvenlik Yöneticisi de olabilir veya bilgi tazelemeniz gerekir. Haydi işe bakalım.

> [!CAUTION]
> **Outlook.com**, **Microsoft 365 Aile** veya **Microsoft 365 Bireysel** kullanıyorsanız ve Kasa Bağlantıları veya *Kasa* Ekleri bilgilerine ihtiyacınız ***varsa, şu*** bağlantıya tıklayın:  Gelişmiş [Outlook.com güvenliği Microsoft 365 aboneleri](https://support.microsoft.com/office/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2).

## <a name="what-is-defender-for-office-365-security"></a>Güvenlik için Defender Office 365 nedir

Her Office 365 abonelik, güvenlik özellikleriyle gelir. Gerçekleştirebilirsiniz hedefler ve işlemler, bu farklı aboneliklerin odağındadır. Güvenlik Office 365, abonelik türünüzle ilgili üç ana güvenlik hizmeti (veya ürünü) vardır:

1. Exchange Online Protection (EOP)
1. Office 365 için Microsoft Defender Plan 1 (Office P1 için Defender)
1. Office 365 için Microsoft Defender Plan 2 (Office P2 için Defender)

> [!NOTE]
> Aboneliğinizi satın aldıysanız ve şu anda güvenlik özelliklerini dışarıyınız *varsa* Tehditlere Karşı Koru [makalesinde yer alan adımlara geçin](protect-against-threats.md) . Aboneliğinizi yeni yeni başladıysanız ve başlamadan önce lisansınızı bilmek için faturanızı kontrol edin ve aşağıdaki > [Ürünleriniz'e Microsoft 365 yönetim merkezi](https://admin.microsoft.com/AdminPortal/#/homepage).

Office 365 EOP tarafından sunulan temel korumalar üzerinde güvenlik derlemelerini de sağlar. EOP, posta kutularının bulunab Exchange Online tüm aboneliklerde kullanılabilir (burada ele alınan tüm güvenlik ürünlerinin Bulut tabanlı olduğunu unutmayın).

Bu şekilde ele alınan bu üç bileşeni görmeye alışık olabilirsiniz:

|EOP|Office 365 P1 için Microsoft Defender|Office 365 P2 için Microsoft Defender|
|---|---|---|
|Geniş, toplu tabanlı, bilinen saldırılar önler.|E-postayı ve işbirliğini sıfır günlük kötü amaçlı yazılımlardan, kimlik avından ve iş e-postalarından ödün vermeden korur.|İhlal sonrası araştırma, arama ve yanıt eklerinin yanı sıra otomasyon ve benzetim (eğitim için) ekler.|

Ancak mimari açısından, her parçanın her biri bir güvenlik vurgusu olan kümülatif güvenlik katmanları olarak düşünerek başlayalım. Şöyle ki:

:::image type="content" source="../../media/tp_GraphicEOPATPP1P2_2.png" alt-text="EOP ve Microsoft Defender for Office 365 and their relationships with service emphasis, including a note for email authentication.":::

Bu hizmetlerden her biri Koruma, Algılama, Araştırma ve Yanıtla ile ilgili bir hedefi vurgulasa da, ***all** _ hizmetler koruma, algılama, araştırma ve yanıtlama hedeflerinin *__any_**'lerini gerçekleştirmektedir.

Güvenliğin temel Office 365 EOP korumasıdır. P1 için Microsoft Defender Office 365 içinde EOP içerir. P2 içeren Office 365 Defender P1 ve EOP. Yapı kümülatiftir. İşte bu nedenle, bu ürünü yapılandırıyorken EOP ile başlamalı ve destek için Defender'Office 365.

Genel DNS'te e-posta kimlik doğrulaması yapılandırması devam etse de kimlik doğrulamasına karşı savunmaya yardımcı olmak için bu özelliği yapılandırmak önemlidir. *EOP'niz varsa,* ***e-posta kimlik [doğrulamasını yapılandırmanız gerekir](email-validation-and-authentication.md)***.

EOP'niz varsa Office 365 E3, ancak yükseltme aracılığıyla Office 365 P1 için tek başına Defender satın alma seçeneğiniz vardır. Office 365 E5, P2 için Defender'ı zaten Office 365.

> [!TIP]
> Aboneliğiniz E5'Office 365 E3 de bağlı değilse, Office 365 P1 için Microsoft Defender'a yükseltme seçeneğiniz olup Office 365 kontrol edebilirsiniz. Bu web sayfası ilginizi çekiyorsa[, bu](https://www.microsoft.com/microsoft-365/exchange/advance-threat-protection#coreui-contentrichblock-x07wids) web sayfasında P1 için Microsoft Defender yükseltmesi için Office 365 abonelikler liste bulabilirsiniz (ince baskı için sayfanın sonuna bakın).

## <a name="the-office-365-security-ladder-from-eop-to-microsoft-defender-for-office-365"></a>EOP Office 365 den Iş için Microsoft Defender'a kadar her güvenlik Office 365

> [!IMPORTANT]
> Şu sayfalarda ayrıntıları öğrenin: [Exchange Online Protection](exchange-online-protection-overview.md) ve Office 365 [için Defender](defender-for-office-365.md).

Uygulama planları için Microsoft Defender Office 365 eklemenin tek bir EOP tehdit yönetimi avantajını ilk bakışta anması zor olabilir. Bir yükseltme yolunun kuruma uygun olup olduğunu sıralamanıza yardımcı olmak için, her ürünün şu özelliklerle ilgili özelliklerine göz atabilirsiniz:

- tehditleri önleme ve algılama
- araştırılıyor
- yanıt verme

Exchange Online Protection **:**
<p>

|Engelleme/Algılama|Araştır|Yanıtla|
|---|---|---|
|Teknolojiler şunlardır:<ul><li>istenmeyen posta</li><li>kimlik avı</li><li>kötü amaçlı yazılım</li><li>toplu posta</li><li>akıllı ifade</li><li>kimliğe bürünme algılama</li><li>Yönetici Karantinası</li><li>Yönetici ve kullanıcı Hatalı Pozitif ve Yanlış Negatif gönderileri</li><li>URL'ler ve Dosyalar için İzin Ver/Engelle</li><li>Raporlar</li></ul>|<li>Denetim günlüğü araması</li><li>İleti İzleme</li>|<li>Sıfır saatlik otomatik temizleme (ZAP)</li><li>İzin Ver ve Engelle listelerini iyileştirme ve sınama</li>|

EOP'de daha fazla bilgi almak için bu **[makaleye atlayın](exchange-online-protection-overview.md)**.

Bu ürünler kümülatif olduğundan, Office 365 için Microsoft Defender'ı değerlendirir ve abone olmayı karar verirsiniz, bu özellikleri eklersiniz.

1. **Plan'da (Office 365 için Defender ile** Kazançlar:
<p>

|Engelleme/Algılama|Araştır|Yanıtla|
|---|---|---|
|Teknolojiler EOP'nin içinde yer alan her şeyi ve şunları içerir:<ul><li>Kasa ekleme</li><li>Kasa bağlantıları<li>İş yükleri için Office 365 Koruması için Microsoft Defender (örneğin. SharePoint Online, Teams, OneDrive İş)</li><li>E-postada, istemcilerde ve diğer Office tıklama süresi koruması Teams</li><li>Office 365 için Defender'da kimlik avı önleme</li><li>Kullanıcı ve etki alanı kimliğe bürünme koruması</li><li>Uyarılar ve uyarılar için SIEM tümleştirme API'si</li>|<li>Algılamalar için SIEM tümleştirme API'si</li><li>**Gerçek zamanlı algılamalar aracı**</li><li>URL izleme</li>|<li>Aynı</li></ul>

Bu nedenle, Office 365 için Microsoft Defender P1 **evin *engelleme** _ tarafında genişler ve fazladan _*_detection** formları_ ekler.

P1 için Microsoft Defender Office 365, **araştırmalarda gerçek zamanlı algılamaları** da ekler. Bu tehdit arama aracının adı kalın yazıyla gösterilir, çünkü bu, Office 365 P1  için Defender'a sahip olduğunu öğrenmenin Office 365 anlamına gelir. Office 365 P2 için Defender'da görünmez.

**2. Plan'da (Office 365 için Defender ile** Kazançlar:
<p>

|Engelleme/Algılama|Araştır|Yanıtla|
|---|---|---|
|Teknolojiler EOP'de yer alan her şeyi ve Office 365 için Microsoft Defender'ı içerir:<ul><li>Aynı</li>|<li>**Tehdit Gezgini**</li><li>Tehdit İzleyicileri</li><li>Kampanya görünümleri</li>|<li>Otomatik Araştırma ve Yanıt (AIR)</li><li>Threat Explorer'dan AIR</li><li>Güvenliği ihlal edilmiş kullanıcılar için AIR</li><li>Otomatik soruşturmalar için SIEM Tümleştirme API'si</li>

Bu nedenle, Office 365 için Microsoft Defender P2 evin araştırma ve yanıt tarafında  genişler ve yeni bir av gücü ekler. Otomasyon.

P2 için Microsoft Defender Office 365 ta birincil arama aracı **Gerçek zamanlı** algılamalar yerine Tehdit Gezgini olarak an çağrılır. Microsoft 365 Defender portalına gitmek için Tehdit Gezgini'ni görüyorsanız, Office 365 P2 için Microsoft Defender'dasınız.

Office 365 P1 ve P2 için Microsoft Defender ile ilgili ayrıntılara almak için **[bu makaleye geçin](defender-for-office-365.md)**.

> [!TIP]
> Son kullanıcılar söz konusu Office 365 EOP ve Microsoft Defender de farklıdır. Office 365 P1 için EOP ve Defender'da odak noktası farkındalıktır ve dolayısıyla bu iki hizmet, kullanıcıların daha fazla çözümleme yapmak amacıyla şüpheli bulunan *e-postaları* bildirsin için Rapor iletisi Outlook eklentisini içerir. <p> Office 365 P2 için Defender'da (EOP ve P1'de bulunan her şeyi içerir), odak son kullanıcılar için daha  fazla eğitime kayıyor; dolayısıyla Güvenlik İşlemleri Merkezi güçlü bir *Tehdit* Araç aracına ve sağladığı son kullanıcı ölçümlerine erişim sağlar.

## <a name="microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet"></a>Office 365 için Microsoft Defender Plan 1 - Plan 2 hile sayfası

Bu hızlı başvuru özelliği, her bir Microsoft Defender aboneliği için hangi özellikleri Office 365 yardımcı olur. EOP özellikleri bilginiz ile bir araya geldiğinde, işletme karar vericilerinin ihtiyaçları için hangi Microsoft Defender Office 365 olduğunu belirlemesine yardımcı olabilir.

|Office 365 için Defender Plan 1|Office 365 için Defender Plan 2|
|---|---|
|Yapılandırma, koruma ve algılama özellikleri: <ul><li>[Kasa Ekleri Kaydetme](safe-attachments.md)</li><li>[Güvenli Bağlantılar](safe-links.md)</li><li>[Kasa, Bağlantı SharePoint OneDrive için Ekleri Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Kimlik avı için Defender'da kimlik avı koruması Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Gerçek zamanlı algılamalar](threat-explorer.md)</li></ul>|Plan 1 Office 365 için Defender <p> --- artı --- <p> Otomasyon, araştırma, düzeltme ve eğitim özellikleri: <ul><li>[Tehdit İzleyicileri](threat-trackers.md)</li><li>[Tehdit Gezgini](threat-explorer.md)</li><li>[Otomatik araştırma ve yanıt](office-365-air.md)</li><li>[Saldırı benzetimi eğitimi](attack-simulation-training.md)</li><li>[E-Microsoft 365 Defender'de gelişmiş avla tehditlere karşı önceden Microsoft 365 Defender](../defender/advanced-hunting-overview.md)</li><li>[E-Microsoft 365 Defender'de olayları araştır](../defender/investigate-incidents.md)</li><li>[E-postada uyarıları Microsoft 365 Defender](../defender/investigate-alerts.md)</li></ul>|

- Office 365 için Microsoft Defender Plan 2 Office 365 E5, Office 365 A5 ve Microsoft 365 E5.

- Plan 1 Office 365 için Microsoft Defender çevrimiçi Microsoft 365 İş Ekstra.

- Office 365 için Microsoft Defender Plan 1 ve Office 365 Için Defender Plan 2'nin her biri, belirli abonelikler için bir eklenti olarak kullanılabilir. Daha fazla bilgi edinmek için, bu planlar için [Microsoft Defender genelindeki Özellik kullanılabilirliği Office 365 vardır](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- Belgeler [Kasa özelliği](safe-docs.md) yalnızca lisans sahibi veya Microsoft 365 E5 Microsoft 365 E5 Güvenlik (Office 365 planları için Microsoft Defender'a dahil değildir) kullanıcılar tarafından kullanılabilir.

- Geçerli aboneliğiniz Office 365 için Microsoft Defender'ı dahil etmek istemiyorsanız[,](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html) denemeyi başlatmak için satışla iletişime geçin ve Office 365 için Microsoft Defender'ın nasıl çalışacı olduğunu öğrenin.

- Office 365 P2 için Microsoft Defender müşterilerinin Microsoft 365 Defender ve uyarıları etkili bir şekilde  algılamak, gözden geçirmek ve yanıtlamak için Microsoft 365 Defender tümleştirmelerine erişimi vardır.

> [!TIP]
> ***Insider tip** _. İçindekiler tablosunda EOP docs.microsoft.com Microsoft Defender hakkında bilgi edinmek için bu tabloyu Office 365. Bu sayfaya geri gidin ve [Office 365 Genel](index.yml) Bakış'a gidin; yan çubukta içindekiler tablosu kuruluş ifadesinin yer alır. Dağıtımla (geçiş dahil) başlar ve önleme, algılama, soruşturma ve yanıt için devam eder. <p> Bu yapı, _Security Administration* *konularının Güvenlik* İşlemleri konuları tarafından takip edilecek **şekilde bölünmüştir** . İş rollerinin yeni bir üyesiyseniz, alanı öğrenmenize yardımcı olması için bu ipucunda yer alan bağlantıyı ve içindekiler tablosu bilginizi kullanın. Geri bildirim bağlantılarını *kullanmayı ve makaleleri* *sonuç olarak* değerlendirmeyi unutmayın. Geri bildirim, size sunduğumuz hizmeti geliştirmemıza yardımcı olur.

## <a name="where-to-go-next"></a>Sıradaki yer

Güvenlik Yöneticisiyseniz, postanız için DKIM veya DMARC yapılandırmanız gerekir. Öncelik kullanıcılarınız için 'Katı' güvenlik önayarları almak veya ürünle ilgili nelerin yeni olduğunu görmek istiyor da olabilir. Veya Güvenlik İşlemleri kullanıyorsanız, Saldırı Saldırı ile son kullanıcı algılamasını araştırmak ve yanıtlamak veya eğitmek için Gerçek zamanlı algılamaları veya Tehdit Gezgini'ni kullanırsanız. Her iki şekilde de, bundan sonra nelere bakıla ilgili bazı ek önerileri burada veser.

[SPF, DKIM ve DMARC dahil olmak üzere E-posta Kimlik Doğrulaması (bunların üçünün de kurulumunun bağlantılarıyla)](email-validation-and-authentication.md)

[Önerilen belirli 'golden' yapılandırmalarına bakın ve](recommended-settings-for-eop-and-office365.md) güvenlik ilkelerini [hızla yapılandırmak için önerilen ön ayarları kullanın](preset-security-policies.md)

EOP [gelişmeleri dahil olmak üzere, Windows için Microsoft Defender'Office 365 neler olduğunu takip etme](whats-new-in-defender-for-office-365.md)

[Tehdit Gezgini'ni veya Gerçek zamanlı algılamaları kullanma](threat-explorer.md)

Saldırı [benzetimi eğitimlerini kullanın](attack-simulation-training.md)
