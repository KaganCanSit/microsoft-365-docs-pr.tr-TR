---
title: Office 365 için Microsoft Defender ve Exchange Online Protection dahil Office 365 Güvenliği
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 07/21/2021
audience: Admin
ms.topic: conceptual
ms.localizationpriority: high
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Office 365'te güvenlik, EOP’den Office 365 için Defender Plan 1 ve 2’ye, Standart ve Katı güvenlik yapılandırmaları ve daha fazlası. Neye sahip olduğunuzu ve özelliklerinizi nasıl güvence altına alacağınızı anlayın.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 62a8d298c9b3e47acb9ba9af5782624646487677
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65647787"
---
# <a name="microsoft-defender-for-office-365-security-overview"></a>Office 365 için Microsoft Defender güvenliğine genel bakış

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)

Bu makale, Buluttaki Office 365 için Microsoft Defender yeni güvenlik özelliklerini size tanıtacaktır. İster Güvenlik İşlemleri Merkezinin bir parçası olun, ister bu alanda yeni bir Güvenlik Yöneticisi olun veya bir tazeleme istiyorsanız, hadi başlayalım.

> [!CAUTION]
> **Outlook.com**, **Microsoft 365 Aile** veya **Microsoft 365 Bireysel** kullanıyorsanız ve *Güvenli Bağlantılar* veya *Güvenli Ekler* ile ilgili bilgilere ihtiyacınız varsa ***şu bağlantıya tıklayın***: [Microsoft 365 aboneleri için gelişmiş Outlook.com güvenliği](https://support.microsoft.com/office/advanced-outlook-com-security-for-office-365-subscribers-882d2243-eab9-4545-a58a-b36fee4a46e2).

## <a name="what-is-defender-for-office-365-security"></a>Office 365 için Defender güvenliği nedir

Her Office 365 aboneliği güvenlik özellikleriyle birlikte gelir. Yapabileceğiniz hedefler ve eylemler, bu farklı aboneliklerin odağına bağlıdır. Office 365 güvenliğinde abonelik türünüze bağlı olarak üç ana güvenlik hizmeti (veya ürünü) vardır:

1. Exchange Online Protection (EOP)
1. Office 365 için Microsoft Defender Plan 1 (Office için Defender P1)
1. Office 365 için Microsoft Defender Plan 2 (Office için Defender P2)

> [!NOTE]
> Aboneliğinizi satın aldıysanız ve güvenlik özelliklerini *hemen* kullanıma sunmanız gerekiyorsa [Tehditlere Karşı Koruma](protect-against-threats.md) makalesindeki adımlara atlayın. Aboneliğinizde yeniyseniz ve başlamadan önce lisansınızı öğrenmek istiyorsanız, [Microsoft 365 yönetim merkezinde](https://admin.microsoft.com/AdminPortal/#/homepage) Faturalama > Ürünleriniz'e göz atın.

Office 365 güvenliği, EOP tarafından sunulan temel korumaların üzerine inşa edilmiştir. EOP, Exchange Online posta kutularının bulunabileceği tüm aboneliklerde bulunur (burada tartışılan tüm güvenlik ürünlerinin Bulut tabanlı olduğunu unutmayın).

Bu üç bileşenin şu şekilde tartışıldığını görmeye alışmış olabilirsiniz:

|EOP|Office 365 için Microsoft Defender P1|Office 365 için Microsoft Defender P2|
|---|---|---|
|Geniş kapsamlı, birim tabanlı, bilinen saldırıları önler.|E-postayı ve işbirliğini sıfırı gün kötü amaçlı yazılımlarından, kimlik avından ve iş e-postası güvenliğinin tehlikeye atılmasından korur.|İhlal sonrası araştırma, arama ve müdahalenin yanı sıra otomasyon ve simülasyon (eğitim için) ekler.|

Ancak mimari açısından, her bir parçayı, her biri bir güvenlik vurgusu olan kümülatif güvenlik katmanları olarak düşünerek başlayalım. Buna benzer daha fazla:

:::image type="content" source="../../media/tp_GraphicEOPATPP1P2_2.png" alt-text="Office 365 için Microsoft Defender ve EOP, e-posta kimlik doğrulaması için bir not da dahil olmak üzere hizmet vurgusu ile birbirleriyle ilişkileri" lightbox="../../media/tp_GraphicEOPATPP1P2_2.png":::

Bu hizmetlerin her biri, Koruma, Algılama, Araştırma ve Yanıtlama arasından bir hedefi vurgulasa da ***tüm** _ hizmetler, koruma, algılama, araştırma ve yanıt verme hedeflerinden _ *_herhangi biri_** gerçekleştirebilir.

Office 365 güvenliğinin temeli EOP korumasıdır. Office 365 P1 için Microsoft Defender EOP içerir. Office 365 P2 için Defender, P1 ve EOP’yi içerir. Yapı kümülatiftir. Bu nedenle, bu ürünü yapılandırırken EOP ile başlamalı ve Office 365 için Defender ile çalışmalısınız.

E-posta kimlik doğrulaması yapılandırması genel DNS'de gerçekleşse de, kimlik sahtekarlığına karşı savunmaya yardımcı olmak için bu özelliği yapılandırmak önemlidir. *EOP'niz varsa*, ***[e-posta kimlik doğrulamasını yapılandırmalısınız](email-validation-and-authentication.md)***.

Office 365 E3 veya daha düşük bir sürüme sahipseniz, EOP'ye sahipsinizdir, ancak yükseltme yoluyla Office 365 P1 için bağımsız Defender satın alma seçeneğine sahipsiniz. Office 365 E5'iniz varsa, Office 365 P2 için Defender'ınız zaten vardır.

> [!TIP]
> Aboneliğiniz Office 365 E3 veya E5 değilse de Office 365 P1 için Microsoft Defender'a yükseltme seçeneğiniz olup olmadığını kontrol edebilirsiniz. İlgileniyorsanız, [bu web sayfasında](https://www.microsoft.com/microsoft-365/exchange/advance-threat-protection#coreui-contentrichblock-x07wids) Office 365 P1 için Microsoft Defender yükseltmesine uygun abonelikler listelenir (ayrıntılı baskı için sayfanın sonuna bakın).

## <a name="the-office-365-security-ladder-from-eop-to-microsoft-defender-for-office-365"></a>EOP'den Office 365 için Microsoft Defender'a Office 365 güvenlik merdiveni

> [!IMPORTANT]
> Bu sayfalardan ayrıntıları öğrenin: [Exchange Online Protection](exchange-online-protection-overview.md) ve [Office 365 için Defender](defender-for-office-365.md).

Office 365 için Microsoft Defender planlarını saf EOP tehdit yönetimine eklemeyi anlamak ilk bakışta zor olabilir. Kuruluşunuz için bir yükseltme yolunun doğru olup olmadığını belirlemeye yardımcı olması için, şunlar söz konusu olduğunda her bir ürünün özelliklerine göz atabilirsiniz:

- tehditleri önleme ve algılama
- araştırma
- yanıt verme

**Exchange Online Protection** ile başlayarak:
<p>

|Engelleme/Algılama|Araştır|Yanıtla|
|---|---|---|
|Teknolojiler şunlardır:<ul><li>istenmeyen posta</li><li>kimlik avı</li><li>kötü amaçlı yazılım</li><li>toplu posta</li><li>kimlik sahtekarlığı analizi</li><li>kimliğe bürünme algılama</li><li>Yönetici Karantinası</li><li>Yönetici ve kullanıcı Hatalı Pozitif ve Yanlış Negatif gönderileri</li><li>URL’ler ve Dosyalar için İzin Ver/Engelle</li><li>Raporlar</li></ul>|<li>Denetim günlüğü araması</li><li>İleti İzleme</li>|<li>Sıfır anında otomatik temizleme (ZAP)</li><li>İzin Ver ve Engelle listelerini iyileştirme ve sınama</li>|

EOP hakkında daha fazla bilgi almak için **[bu makaleye bakın](exchange-online-protection-overview.md)**.

Bu ürünler kümülatif olduğundan, Office 365 P1 için Microsoft Defender'ı değerlendirir ve buna abone olmaya karar verirseniz, bu özellikleri eklersiniz.

**Office 365 için Defender, Plan 1** ile kazançlar (bugüne kadar):
<p>

|Engelleme/Algılama|Araştır|Yanıtla|
|---|---|---|
|Teknolojiler EOP'nin içinde yer alan her şeyi ve şunları içerir:<ul><li>Güvenli ekler</li><li>Güvenli bağlantılar<li>Office 365 için Microsoft Defender iş yükü koruması (örneğin. SharePoint Online, Teams, OneDrive İş)</li><li>E-posta, Office istemcileri ve Teams'de tıklama süresi koruması</li><li>Office 365 için Defender'da kimlik avı koruması</li><li>Kullanıcı ve etki alanı kimliğine bürünme koruması</li><li>Uyarılar ve uyarılar için SIEM tümleştirme API’si</li>|<li>Algılamalar için SIEM tümleştirme API’si</li><li>**Gerçek zamanlı algılama aracı**</li><li>URL izleme</li>|<li>Aynı</li></ul>

Bu nedenle, Office 365 P1 için Microsoft Defender, evin ***önleme** _ tarafını genişletir ve ekstra _*_algılama_** biçimleri ekler.

Office 365 P1 için Microsoft Defender, araştırmalar için **Gerçek zamanlı algılamalar** da ekler. Office 365 P1 için Defender'a sahip olduğunuzu *bilmenin* açık bir yolu olduğundan, bu tehdit avlama aracının adı kalın yazı ile gösterilir. Office 365 P2 için Defender'da görünmez.

**Office 365 için Defender, Plan 2** ile kazançlar (bugüne kadar):
<p>

|Engelleme/Algılama|Araştır|Yanıtla|
|---|---|---|
|Teknolojiler, EOP’de bulunan her şeyi ve Office 365 P1 için Microsoft Defender'ı ve ayrıca şunları içerir:<ul><li>Aynı</li>|<li>**Tehdit Gezgini**</li><li>Tehdit İzleyiciler</li><li>Kampanya görünümleri</li>|<li>Otomatik Araştırma ve Yanıt (AIR)</li><li>Tehdit Gezgini’nden AIR</li><li>Risk altındaki kullanıcılar için AIR</li><li>Otomatik Araştırmalar için SIEM Tümleştirme API'si</li>

Dolayısıyla, Office 365 için Microsoft Defender P2, evin ***araştırma ve yanıt*** tarafını genişletir ve yeni bir avlanma gücü ekler. Otomasyon.

Office 365 P2 için Microsoft Defender'da birincil arama aracına Gerçek zamanlı algılamalar yerine **Tehdit Gezgini** adı verilir. Microsoft 365 Defender portalına gittiğinizde Tehdit Gezgini'ni görüyorsanız, Office 365 P2 için Microsoft Defender'dasınız demektir.

Office 365 P1 ve P2 için Microsoft Defender'ın ayrıntılarına girmek için **[bu makaleye bakın](defender-for-office-365.md)**.

> [!TIP]
> EOP ve Office 365 için Microsoft Defender, son kullanıcılar söz konusu olduğunda da farklıdır.Office 365 P1 için Defender ve EOP'de odak noktası *farkındalıktır* ve bu nedenle bu iki hizmet, kullanıcıların şüpheli buldukları e-postaları daha fazla analiz için rapor edebilmeleri için *Rapor iletisi Outlook eklentisi*’ni içerir. <p> Office 365 Defender P2'de (EOP ve P1'deki her şeyi içerir), odak son kullanıcılar için *daha fazla eğitime* kayar ve böylece Güvenlik Operasyonları Merkezi, güçlü bir *Tehdit Simülatörü* aracına ve sağladığı son kullanıcı ölçümlerine erişebilir.

## <a name="microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet"></a>Office 365 için Microsoft Defender Plan 1 ve Plan 2 hızlı başvuru kılavuzu

Bu hızlı başvuru, her Office 365 için Microsoft Defender aboneliğiyle hangi özelliklerin geldiğini anlamanıza yardımcı olacaktır. EOP özellikleri hakkındaki bilginizle birleştiğinde, işletme karar alıcılarının hangi Office 365 için Microsoft Defender'ın ihtiyaçları için en iyi olduğunu belirlemesine yardımcı olabilir.

|Office 365 için Defender Plan 1|Office 365 için Defender Plan 2|
|---|---|
|Yapılandırma, koruma ve algılama özellikleri: <ul><li>[Güvenli Ekleri Kaydetme](safe-attachments.md)</li><li>[Güvenli Bağlantılar](safe-links.md)</li><li>[SharePoint, OneDrive ve Microsoft Teams için Güvenli Ekler](mdo-for-spo-odb-and-teams.md)</li><li>[Office 365 için Defender'da kimlik avına karşı koruma](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Gerçek zamanlı algılamalar](threat-explorer.md)</li></ul>|Office 365 için Defender Plan 1 özellikleri <p> --- artı --- <p> Otomasyon, araştırma, düzeltme ve eğitim özellikleri: <ul><li>[Tehdit İzleyiciler](threat-trackers.md)</li><li>[Tehdit Gezgini](threat-explorer.md)</li><li>[Otomatik araştırma ve yanıt](office-365-air.md)</li><li>[Saldırı simülasyonu eğitimi](attack-simulation-training.md)</li><li>[Microsoft 365 Defender'da gelişmiş arama ile tehditleri proaktif olarak avlama](../defender/advanced-hunting-overview.md)</li><li>[Microsoft 365 Defender'daki olayları araştırma](../defender/investigate-incidents.md)</li><li>[Microsoft 365 Defender'da uyarıları araştırma](../defender/investigate-alerts.md)</li></ul>|

- Office 365 için Microsoft Defender Plan 2, Office 365 E5, Office 365 A5 ve Microsoft 365 E5'e dahildir.

- Office 365 için Microsoft Defender Plan 1, Microsoft 365 İş Ekstra'ya dahildir.

- Office 365 için Microsoft Defender Plan 1 ve Office 365 için Defender Plan 2, belirli abonelikler için eklenti olarak kullanılabilir. Daha fazla bilgi edinmek için, [Office 365 planları için Microsoft Defender genelinde Özellik kullanılabilirliği](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans) bağlantısını burada bulabilirsiniz.

- [Güvenli Belgeler](safe-docs.md) özelliği yalnızca Microsoft 365 E5 veya Microsoft 365 E5 Güvenlik lisanslarına sahip kullanıcılar tarafından kullanılabilir (Office 365 için Microsoft Defender planlarına dahil değildir).

- Mevcut aboneliğiniz Office 365 için Microsoft Defender'ı içermiyorsa ve bunu istiyorsanız, [bir deneme başlatmak için satış ekibiyle iletişime geçin](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html) ve Office 365 için Microsoft Defender'ın kuruluşunuzda nasıl çalışabileceğini öğrenin.

- Office 365 için Microsoft Defender P2 müşterileri, olayları ve uyarıları verimli bir şekilde algılamak, gözden geçirmek ve yanıtlamak için **Microsoft 365 Defender tümleştirmesine** erişebilir.

> [!TIP]
> ***Insider ipucu** _. Office 365 için EOP ve Microsoft Defender hakkında bilgi edinmek için docs.microsoft.com içindekiler tablosunu kullanabilirsiniz. [Office 365 Güvenliğine genel bakış](index.yml) sayfasına geri dönün, yan çubukta içindekiler organizasyonunun olduğunu göreceksiniz. Dağıtım (geçiş dahil) ile başlar ve ardından önleme, algılama, araştırma ve yanıt ile devam eder. <p> Bu yapı, _ *Güvenlik Yönetimi** konularını **Güvenlik İşlemleri** konuları takip edecek şekilde bölünmüştür. Her iki iş rolünün de yeni bir üyesiyseniz, alanı öğrenmenize yardımcı olması için bu ipucundaki bağlantıyı ve içindekiler bilginizi kullanın. Gittiğinizde *geri bildirim bağlantılarını* kullanmayı ve *makaleleri derecelendirmeyi* unutmayın. Geri bildirim, size sunduğumuz hizmeti geliştirmemize yardımcı olur.

## <a name="where-to-go-next"></a>Sonra nereye gitmeli

Güvenlik Yöneticisiyseniz, postanız için DKIM veya DMARC'yi yapılandırmanız gerekebilir. Öncelikli kullanıcılarınız için 'Katı' güvenlik ön ayarlarını kullanıma sunmak veya üründeki yeniliklere bakmak isteyebilirsiniz. Veya Güvenlik Operasyonları üyesiyseniz, araştırmak ve yanıt vermek için Gerçek Zamanlı algılamalardan veya Tehdit Gezgini'nden yararlanmak veya Saldırı Simülatörü ile son kullanıcı algılamasını eğitmek isteyebilirsiniz. Her iki durumda da, bir sonraki adımda nelere bakmanız gerektiğine dair bazı ek öneriler burada.

[SPF, DKIM ve DMARC dahil olmak üzere E-posta Kimlik Doğrulaması (üçünün kurulum bağlantılarıyla birlikte)](email-validation-and-authentication.md)

[Önerilen özel 'altın' yapılandırmalara bakın](recommended-settings-for-eop-and-office365.md) ve [güvenlik ilkelerini hızlı bir şekilde yapılandırmak için önerilen ön ayarlarını kullanın](preset-security-policies.md)

[Office 365 için Microsoft Defender'daki yeniliklerden (EOP geliştirmeleri dahil)](whats-new-in-defender-for-office-365.md) haberdar olun

[Tehdit Gezgini veya Gerçek zamanlı algılamaları kullanın](threat-explorer.md)

[Saldırı simülasyonu eğitimini](attack-simulation-training.md) kullanın
