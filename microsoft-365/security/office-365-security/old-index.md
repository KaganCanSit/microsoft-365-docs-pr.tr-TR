---
title: Office 365 genel bakış, Office 365 için Microsoft Defender, EOP, MSDO
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 08/13/2020
audience: Admin
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: EOP Office 365 den Proje Planları 1 Office 365 için Defender 2'ye, Standart ile Katı güvenlik yapılandırmaları ve daha fazlası için güvenlik. Sahip olduğunuz özellikleri anlama ve özelliklerinizin güvenliğini sağlamayı öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d75ed9a3b01a7a16e283ce007f7c4a5b50cdab09
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467499"
---
# <a name="office-365-security"></a>Office 365 güvenliği


**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)


Bu makale size Buluttaki yeni güvenlik özelliklerinizi tanıtacak. Bir Güvenlik İşlemleri Merkezi'nde yer alan bir Güvenlik Yöneticisi de olabilir veya bilgi tazelemeniz gerekir. Haydi işe bakalım.

> [!CAUTION]
> **Outlook.com**, **Microsoft 365 Aile** veya **Microsoft 365 Bireysel** kullanıyorsanız ve Kasa Bağlantıları veya *Kasa* Ekleri bilgilerine ihtiyacınız ***varsa, şu*** bağlantıya tıklayın:  Gelişmiş [Outlook.com güvenliği Microsoft 365 aboneleri](https://support.microsoft.com/office/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2).

## <a name="office-365-security-spelled-out"></a>Office 365 yazılmış güvenlik

Her Office 365 abonelik, güvenlik özellikleriyle gelir. Gerçekleştirebilirsiniz hedefler ve işlemler, bu farklı aboneliklerin odağındadır. Güvenlik Office 365, abonelik türünüzle ilgili üç ana güvenlik hizmeti (veya ürünü) vardır:

1. Exchange Online Protection (EOP)
1. Office 365 için Microsoft Defender Plan 1 (Office P1 için Defender)
1. Office 365 için Microsoft Defender Plan 2 (Office P2 için Defender)

> [!NOTE]
> Aboneliğinizi satın aldıysanız ve şu anda güvenlik özelliklerini dışarıyınız *varsa* Tehditlere Karşı Koru [makalesinde yer alan adımlara geçin](protect-against-threats.md) . Aboneliğinizi yeni yeni başladıysanız ve başlamadan önce lisansınızı bilmek için faturanızı kontrol edin ve aşağıdaki > [Ürünleriniz'e Microsoft 365 yönetim merkezi](https://admin.microsoft.com/AdminPortal/#/homepage).

Office 365 EOP tarafından sunulan temel korumalar üzerinde güvenlik derlemelerini de sağlar. EOP, posta kutularının bulunab Exchange Online tüm aboneliklerde kullanılabilir (burada ele alınan tüm güvenlik ürünlerinin Bulut tabanlı olduğunu unutmayın).

Bu şekilde ele alınan bu üç bileşeni görmeye alışık olabilirsiniz:

|EOP|Office 365 için Microsoft Defender P1|Office 365 için Microsoft Defender P2|
|---|---|---|
|Geniş, toplu tabanlı, bilinen saldırılar önler.|E-postayı ve işbirliğini sıfır günlük kötü amaçlı yazılımlardan, kimlik avından ve iş e-postalarından ödün vermeden korur.|İhlal sonrası araştırma, arama ve yanıt eklerinin yanı sıra otomasyon ve benzetim (eğitim için) ekler.|

Ancak mimari açısından, her parçanın her biri bir güvenlik vurgusu olan kümülatif güvenlik katmanları olarak düşünerek başlayalım. Şöyle ki:

<!--:::image type="content" source="../../media/tp-EOPATPStack.PNG" alt-text="Placeholder graphic.":::-->

:::image type="content" source="../../media/tp_GraphicEOPATPP1P2_2.png" alt-text="EOP ve Office 365 için Microsoft Defender-posta kimlik doğrulaması notu da dahil olmak üzere, hizmet vurgulu olarak EOP ve Kimlik Doğrulama ve aralarındaki ilişkiler" lightbox="../../media/tp_GraphicEOPATPP1P2_2.png":::

Bu hizmetlerden her biri Koruma, Algılama, Araştırma ve Yanıtla ile ilgili bir hedefi vurgulasa da, ***all** _ hizmetler koruma, algılama, araştırma ve yanıtlama hedeflerinin *__any_**'lerini gerçekleştirmektedir.

Güvenliğin temel Office 365 EOP korumasıdır. Office 365 için Microsoft Defender P1 içinde EOP içerir. Office 365 için Defender P2 P1 ve EOP içerir. Yapı kümülatiftir. İşte bu nedenle, bu ürünü yapılandırarak çalışmaya EOP ile başlamalı ve Office 365 için Defender.

Genel DNS'te e-posta kimlik doğrulaması yapılandırması devam etse de kimlik doğrulamasına karşı savunmaya yardımcı olmak için bu özelliği yapılandırmak önemlidir. *EOP'niz varsa,* ***e-posta kimlik [doğrulamasını yapılandırmanız gerekir](email-validation-and-authentication.md)***.

EOP'niz varsa Office 365 E3 sürümüne sahipsinizdir ancak yükseltme aracılığıyla P1'den bağımsız Office 365 için Defender seçeneğiyle kullanabilirsiniz. P2'Office 365 E5 zaten Office 365 için Defender var.

> [!TIP]
> Aboneliğiniz E5'Office 365 E3 de bağlı değilse, P1'e yükseltme seçeneğiniz olup Office 365 için Microsoft Defender bakabilirsiniz. Bu web sayfası ilginizi çekiyorsa[, bu](https://www.microsoft.com/microsoft-365/exchange/advance-threat-protection#coreui-contentrichblock-x07wids) web sayfası Office 365 için Microsoft Defender P1 yükseltmesi için uygun abonelikleri listeler (ince yazdırma için sayfanın sonuna bakın).

## <a name="the-office-365-security-ladder-from-eop-to-microsoft-defender-for-office-365"></a>EOP'Office 365 güvenlik Office 365 için Microsoft Defender

![EOP ve Office 365 için Microsoft Defender vurgusu için, Koru ve Algıla'dan Araştır ve Yanıtla'ya kadar olan bir vurgu verir. EOP ve up için E-posta Kimlik Doğrulaması yapılandırması (en az DKIM ve DMARC) ayar olmalı.](../../media/tp_EOPATPP1P2Take6.gif#lightbox)

> [!IMPORTANT]
> Bu sayfalarda ayrıntıları öğrenin: [Exchange Online Protection](exchange-online-protection-overview.md) [ve Office 365 için Defender](defender-for-office-365.md).

Plan eklemenin Office 365 için Microsoft Defender, yalnızca EOP tehdit yönetiminin avantajını ilk bakışta söylemek zor olabilir. Bir yükseltme yolunun kuruma uygun olup olduğunu sıralamanıza yardımcı olmak için, her ürünün şu özelliklerle ilgili özelliklerine göz atabilirsiniz:

- tehditleri önleme ve algılama
- araştırılıyor
- yanıt verme

Exchange Online Protection **:**
<p>

|Engelleme/Algılama|Araştır|Yanıtla|
|---|---|---|
|Teknolojiler şunlardır:<ul><li>istenmeyen posta</li><li>kimlik avı</li><li>kötü amaçlı yazılım</li><li>toplu posta</li><li>akıllı ifade</li><li>kimliğe bürünme algılama</li><li>Yönetici Karantinası</li><li>Yönetici ve kullanıcı Hatalı Pozitif ve Yanlış Negatif gönderileri</li><li>URL'ler ve Dosyalar için İzin Ver/Engelle</li><li>Raporlar</li></ul>|<li>Denetim günlüğü araması</li><li>İleti İzleme</li>|<li>Sıfır saatlik otomatik temizleme (ZAP)</li><li>İzin Ver ve Engelle listelerini iyileştirme ve sınama</li>|

EOP'de daha fazla bilgi almak için bu **[makaleye atlayın](exchange-online-protection-overview.md)**.

Bu ürünler kümülatif olduğundan, Office 365 için Microsoft Defender P1'i değerlendirir ve abone olmayı karar verirsiniz, bu özellikleri eklersiniz.

Gelirler ve **Office 365 için Defender, Plan 1** (bugüne kadar):
<p>

|Engelleme/Algılama|Araştır|Yanıtla|
|---|---|---|
|Teknolojiler EOP'nin içinde yer alan her şeyi ve şunları içerir:<ul><li>Kasa ekleme</li><li>Kasa bağlantıları<li>Office 365 için Microsoft Defender iş yüklerinin korumasını sağlar (örneğin. SharePoint Online, Teams, OneDrive İş)</li><li>E-postada, istemcilerde ve diğer Office tıklama süresi koruması Teams</li><li>Office 365 için Defender'te kimlik avı önleme</li><li>Kullanıcı ve etki alanı kimliğe bürünme koruması</li><li>Uyarılar ve uyarılar için SIEM tümleştirme API'si</li>|<li>Algılamalar için SIEM tümleştirme API'si</li><li>**Gerçek zamanlı algılamalar aracı**</li><li>URL izleme</li>|<li>Aynı</li></ul>

Bu Office 365 için Microsoft Defender P1, **evin *engelleme** _ tarafında genişler ve fazladan _*algılama** _formları_ ekler.

Office 365 için Microsoft Defender P1, **soruşturmalar için Gerçek zamanlı algılamaları** da ekler. Bu tehdit arama aracının adı kalın yazıyla gösterilir, çünkü böyle bir P1 *e-Office 365 için Defender* açıktır. P2'de Office 365 için Defender.

Çıkışlar, **Office 365 için Defender 2 (bugüne** kadar):
<p>

|Engelleme/Algılama|Araştır|Yanıtla|
|---|---|---|
|Teknolojiler EOP'de yer alan her şeyi ve P1 Office 365 için Microsoft Defender içerir:<ul><li>Aynı</li>|<li>**Tehdit Gezgini**</li><li>Tehdit İzleyiciler</li><li>Kampanya görünümleri</li>|<li>Otomatik Araştırma ve Yanıt (AIR)</li><li>Threat Explorer'dan AIR</li><li>Güvenliği ihlal edilmiş kullanıcılar için AIR</li><li>Otomatik soruşturmalar için SIEM Tümleştirme API'si</li>

Office 365 için Microsoft Defender P2, evin araştırma ve yanıt tarafında genişler ve  yeni bir av gücü ekler. Otomasyon.

Office 365 için Microsoft Defender P2'de birincil av aracı, Gerçek zamanlı **algılamalar** yerine Tehdit Gezgini olarak adlandırılan araçtır. Bulut için Defender'a gitmek için Tehdit Gezgini'ni görüyorsanız, Office 365 için Microsoft Defender P2'desiniz.

P1 ve P2 Office 365 için Microsoft Defender ayrıntılarına almak için **[bu makaleye geçin](defender-for-office-365.md)**.

> [!TIP]
> EOP ve Office 365 için Microsoft Defender son kullanıcılara göre de farklıdır. EOP ve Office 365 için Defender P1'de odak noktası farkındalıktır ve dolayısıyla bu iki hizmet, kullanıcıların daha fazla çözümleme yapmak amacıyla şüpheli bulunan *e-postaları* bildirsin için Rapor Outlook iletisi eklentisinde yer alır. <p> Office 365 için Defender P2'de (EOP ve P1'de bulunan her şeyi içerir), odak son kullanıcılar için daha  fazla eğitime kayıyor; dolayısıyla Güvenlik İşlemleri Merkezi güçlü bir *Tehdit* Araç'larına ve sağladığı son kullanıcı ölçümlerine erişim sağlar.

## <a name="microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet"></a>Office 365 için Microsoft Defender Plan 1 - Plan 2 hile sayfası

Bu hızlı başvuru özelliği, her abonelikle birlikte hangi becerilerin Office 365 için Microsoft Defender yardımcı olur. EOP özellikleri bilginiz ile bir araya geldiğinde, işletme karar vericilerinin ihtiyaçlarına en uygun Office 365 için Microsoft Defender karar vermelerine yardımcı olabilir.

|Office 365 için Defender Plan 1|Office 365 için Defender Plan 2|
|---|---|
|Yapılandırma, koruma ve algılama özellikleri: <ul><li>[Kasa Ekleri Kaydetme](safe-attachments.md)</li><li>[Güvenli Bağlantılar](safe-links.md)</li><li>[Kasa, Bağlantı SharePoint OneDrive için Ekleri Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[E-posta'da kimlik avına karşı koruma Office 365 için Defender](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Gerçek zamanlı algılamalar](threat-explorer.md)</li></ul>|Office 365 için Defender Plan 1 özellikleri <p> --- artı --- <p> Otomasyon, araştırma, düzeltme ve eğitim özellikleri: <ul><li>[Tehdit İzleyiciler](threat-trackers.md)</li><li>[Tehdit Gezgini](threat-explorer.md)</li><li>[Otomatik araştırma ve yanıt](office-365-air.md)</li><li>[Attack Simulator](attack-simulator.md)</li></ul>|

- Office 365 için Microsoft Defender Plan 2 iş, Office 365 E5, Office 365 A5 ve Microsoft 365 E5.

- Office 365 için Microsoft Defender Plan 1 yeni bir Microsoft 365 İş Ekstra.

- Office 365 için Microsoft Defender Plan 1 Office 365 için Defender Plan 2'nin her biri belirli abonelikler için eklenti olarak kullanılabilir. Daha fazla bilgi edinmek için, bu planlar arasında özellik [kullanılabilirliği Office 365 için Microsoft Defender bağlantısıdır](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- Belge [Kasa özelliği](safe-docs.md) yalnızca Lisans veya Lisans Microsoft 365 E5 (Microsoft 365 E5 Güvenlik planlara dahil değildir) sahip Office 365 için Microsoft Defender tarafından kullanılabilir.

- Geçerli aboneliğiniz yeni abonelik [Office 365 için Microsoft Defender, deneme](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html) sürümü başlatmak için satışla iletişime geçin ve aboneliğinizin Office 365 için Microsoft Defender yardımcı olduğunu öğrenin.

> [!TIP]
> ***Insider tip** _. EOP ve docs.microsoft.com hakkında bilgi edinmek için tablo içindekiler Office 365 için Microsoft Defender. Bu sayfaya geri gidin ve [Office 365 Genel](index.yml) Bakış'a gidin; yan çubukta içindekiler tablosu kuruluş ifadesinin yer alır. Dağıtımla (geçiş dahil) başlar ve önleme, algılama, soruşturma ve yanıt için devam eder. <p> Bu yapı, _Security Administration* *konularının Güvenlik* İşlemleri konuları tarafından takip edilecek **şekilde bölünmüştir** . İş rollerinin yeni bir üyesiyseniz, alanı öğrenmenize yardımcı olması için bu ipucunda yer alan bağlantıyı ve içindekiler tablosu bilginizi kullanın. Geri bildirim bağlantılarını *kullanmayı ve makaleleri* *sonuç olarak* değerlendirmeyi unutmayın. Geri bildirim, size sunduğumuz hizmeti geliştirmemıza yardımcı olur.

## <a name="where-to-go-next"></a>Sıradaki yer

Güvenlik Yöneticisiyseniz, postanız için DKIM veya DMARC yapılandırmanız gerekir. Öncelik kullanıcılarınız için 'Katı' güvenlik önayarları almak veya ürünle ilgili nelerin yeni olduğunu görmek istiyor da olabilir. Veya Güvenlik İşlemleri kullanıyorsanız, Saldırı Saldırı ile son kullanıcı algılamasını araştırmak ve yanıtlamak veya eğitmek için Gerçek zamanlı algılamaları veya Tehdit Gezgini'ni kullanırsanız. Her iki şekilde de, bundan sonra nelere bakıla ilgili bazı ek önerileri burada veser.

[SPF, DKIM ve DMARC dahil olmak üzere E-posta Kimlik Doğrulaması (bunların üçünün de kurulumunun bağlantılarıyla)](email-validation-and-authentication.md)

[Önerilen belirli 'golden' yapılandırmalarına bakın ve](recommended-settings-for-eop-and-office365.md) güvenlik ilkelerini [hızla yapılandırmak için önerilen ön ayarları kullanın](preset-security-policies.md)

EOP [gelişmeleri dahil olmak üzere Office 365 için Microsoft Defender hakkında daha fazla şey](whats-new-in-defender-for-office-365.md)

[Tehdit Gezgini'ni veya Gerçek zamanlı algılamaları kullanma](threat-explorer.md)

Saldırı [Slanı'Office 365 için Microsoft Defender](attack-simulator.md)
