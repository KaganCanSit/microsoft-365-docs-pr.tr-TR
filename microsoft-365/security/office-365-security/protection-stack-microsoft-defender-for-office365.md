---
title: Office 365 için Microsoft Defender'da adım adım tehdit koruma yığını
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 04/05/2021
ms.reviewer: gigarrub
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
description: Office 365 için Microsoft Defender'daki tehdit filtreleme yığını aracılığıyla gelen iletinin yolunu izleyin.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 4548beaf8d3071006114a65fd95c16b06e8a875d
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648183"
---
# <a name="step-by-step-threat-protection-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'da adım adım tehdit koruması

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Şunlar için geçerlidir:**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Office 365 için Microsoft Defender koruma veya filtreleme yığını, bu makalede olduğu gibi 4 aşamaya ayrılabilir. Genel olarak, gelen posta teslimden önce tüm bu aşamalardan geçer, ancak e-postanın aldığı gerçek yol kuruluşun Office 365 için Defender yapılandırmasına tabidir.

> [!TIP]
> Office 365 için Defender korumanın 4 aşamasının tümünün *birleşik* grafiği için bu makalenin sonuna kadar bizi takip edin!

## <a name="phase-1---edge-protection"></a>1. Aşama - Edge Koruması

Ne yazık ki, bir zamanlar *kritik* olan Edge blokları artık kötü aktörlerin üstesinden gelmek için nispeten basittir. Zaman içinde burada daha az trafik engellenir ancak yığının önemli bir parçası olmaya devam eder.  

Kenar blokları otomatik olacak şekilde tasarlanmıştır. Hatalı pozitif olması durumunda, gönderenlere bildirim gönderilir ve sorunlarının nasıl giderileceği bildirilir. Saygınlığı sınırlı olan güvenilir iş ortaklarının bağlayıcıları, yeni uç noktalar eklerken teslim edilebilirlik sağlayabilir veya geçici geçersiz kılmalar uygulanabilir.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase1.png" alt-text="Office 365 için Defender'de 1. Aşama filtrelemesi" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase1.png":::

1. **Ağ azaltma**, belirli bir altyapı kümesi tarafından gönderilebilen ileti sayısını sınırlayarak Office 365 altyapıyı ve müşterileri Hizmet Reddi (DOS) saldırılarına karşı korur.

2. **IP saygınlığı ve azaltma** , bilinen hatalı bağlantı IP adreslerinden ileti gönderilmesini engeller. Belirli bir IP kısa bir süre içinde çok sayıda ileti gönderirse, bunlar kısıtlanır.

3. **Etki alanı saygınlığı** bilinen bir kötü etki alanından gönderilen iletileri engeller.

4. **Dizin tabanlı kenar filtreleme** , SMTP aracılığıyla kuruluşun dizin bilgilerini toplama girişimlerini engeller.

5. **Backscatter algılama** , bir kuruluşun geçersiz teslim edilmeyen raporlar (NDR) aracılığıyla saldırıya uğramasını önler.

6. **Bağlayıcılar için gelişmiş filtreleme**, trafik Office 365 ulaşmadan önce başka bir cihazdan geçtiğinde bile kimlik doğrulama bilgilerini korur. Bu, karmaşık veya karma yönlendirme senaryolarında bile buluşsal kümeleme, kimlik sahtekarlığı önleme ve kimlik avı önleme makine öğrenmesi modelleri dahil olmak üzere filtreleme yığını doğruluğunu geliştirir.

## <a name="phase-2---sender-intelligence"></a>2. Aşama - Gönderen Bilgileri

Gönderen bilgilerindeki özellikler istenmeyen posta, toplu, kimliğe bürünme ve yetkisiz kimlik sahtekarlığı iletilerini yakalamak için kritik öneme sahiptir ve kimlik avı algılamayı da dikkate alır. Bu özelliklerin çoğu tek tek yapılandırılabilir.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase2.png" alt-text="Office 365 için Defender'da filtrelemenin 2. aşaması Gönderen zekası" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase2.png":::

1. **Hesap güvenliğinin aşılmasına yönelik algılama** tetikleyicileri ve uyarılar, bir hesabın anormal davranışı olduğunda ve gizliliğin tehlikeye girerek tutarlı olması durumunda tetiklenir. Bazı durumlarda, kullanıcı hesabı engellenir ve sorun kuruluşun güvenlik operasyonları ekibi tarafından çözülene kadar başka e-posta iletileri göndermesi engellenir.

2. **E-posta Kimlik Doğrulaması** , hem müşterinin yapılandırmış olduğu yöntemleri hem de gönderenlerin yetkili, gerçek posta gönderenler olduğundan emin olmak için Bulutta ayarlanan yöntemleri içerir. Bu yöntemler sahtekarlık için direnmektedir.
    - **SPF** , KURULUŞ adına posta göndermesine izin verilen IP adreslerini ve sunucuları listeleyen DNS TXT kayıtlarına göre postaları reddedebilir.
    - **DKIM** , gönderenin kimliğini doğrulayan şifreli bir imza sağlar.
    - **DMARC** , yöneticilerin etki alanında SPF ve DKIM'i gerekli olarak işaretlemesine olanak tanır ve bu iki teknolojinin sonuçları arasında hizalamayı zorlar.
    - **ARC** müşteri tarafından yapılandırılmaz, ancak kimlik doğrulama zincirini kaydederken posta listelerinde iletme ile çalışmak için DMARC'yi derler.

3. **Kimlik sahtekarlık zekası** , kuruluş veya bilinen dış etki alanlarını taklit eden kötü amaçlı gönderenlerden 'kimlik sahtekarlığına' izin verilenleri (başka bir hesap adına posta gönderenler veya posta listesi için iletilenler) filtrelenebilir. Yasal "adına" postaları istenmeyen posta ve kimlik avı iletileri göndermek için sahtekarlık yapan gönderenlerden ayırır.

    **Kuruluş içi kimlik sahtekarı zekası** , kuruluş içindeki bir etki alanından gelen kimlik sahtekarlık girişimlerini algılar ve engeller.

4. **Etki alanları arası kimlik sahtekarı zekası** , kuruluş dışındaki bir etki alanından gelen kimlik sahtekarlık girişimlerini algılar ve engeller.

5. **Toplu filtreleme, yöneticilerin** iletinin toplu gönderenden gönderilip gönderilmediğini belirten bir toplu güvenilirlik düzeyi (BCL) yapılandırmasına olanak tanır. Yöneticiler, istenmeyen posta olarak davranacak toplu posta düzeyine karar vermek için Antispam ilkesindeki Toplu Kaydırıcıyı kullanabilir.

6. **Posta kutusu zekası** standart kullanıcı e-posta davranışlarından öğrenir. Bir gönderenin yalnızca kullanıcının genellikle iletişim kuracağı, ancak aslında kötü amaçlı olduğu bir kişi olduğunu algılamak için kullanıcının iletişim grafiğinden yararlanıyor. Bu yöntem kimliğe bürünme algılar.

7. **Posta kutusu zekası kimliğe bürünme** özelliği, her kullanıcının tek tek gönderen eşlemesini temel alarak gelişmiş kimliğe bürünme sonuçlarını etkinleştirir veya devre dışı bırakır. Bu özellik etkinleştirildiğinde kimliğe bürünme tanımlamaya yardımcı olur.

8. **Kullanıcı kimliğe bürünme** , bir yöneticinin kimliğine bürünülmesi muhtemel yüksek değerli hedeflerin listesini oluşturmasına olanak tanır. Gönderenin yalnızca korumalı yüksek değerli hesapla aynı ada ve adrese sahip olduğu bir posta gelirse, posta işaretlenir veya etiketlenir. (Örneğin, *tracye@contoso.com* için *trα cye@contoso.com*).

9. **Etki alanı kimliğe bürünme** , alıcının etki alanına benzeyen ve bir iç etki alanı gibi görünmeye çalışan etki alanlarını algılar. Örneğin, bu kimliğe bürünme tracye@litware.com *için* *tracye@liw α re.com*.

## <a name="phase-3---content-filtering"></a>3. Aşama - İçerik Filtreleme

Bu aşamada filtreleme yığını, köprüleri ve ekleri de dahil olmak üzere postanın belirli içeriğini işlemeye başlar.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase3.png" alt-text="MDO'da 3. Aşama filtrelemesi İçerik Filtreleme'dir" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase3.png":::

1. **Aktarım kuralları** (posta akışı kuralları veya Exchange aktarım kuralları olarak da bilinir), bir yöneticinin bir ileti için eşit derecede geniş bir koşul aralığı karşılandığında çok çeşitli eylemler gerçekleştirmesine olanak tanır. Kuruluşunuzda akan tüm iletiler, etkin posta akışı kuralları/aktarım kurallarıyla değerlendirilir.

2. **eklerdeki** bilinen tüm kötü amaçlı yazılımları algılamak için Microsoft Defender Virüsten Koruma ve iki *üçüncü taraf Virüsten Koruma altyapısı* kullanılır.

3. Virüsten koruma (AV) altyapıları tüm ekleri doğru yazmak için de kullanılır, böylece **Tür engelleme** , yöneticinin belirttiği türlerdeki tüm ekleri engelleyebilir.

4. Office 365 için Microsoft Defender kötü amaçlı bir ek algılandığında, dosyanın karması ve etkin içeriğinin karması Exchange Online Protection (EOP) itibarına eklenir. **Ek itibarını engelleme**, MSAV bulut çağrıları aracılığıyla tüm Office 365 ve uç noktalarda bu dosyayı engeller.

5. **Buluşsal kümeleme** , teslim buluşsal yöntemlerine göre bir dosyanın şüpheli olduğunu belirleyebilir. Şüpheli bir ek bulunduğunda kampanyanın tamamı duraklatılır ve dosya korumalı olur. Dosyanın kötü amaçlı olduğu tespit edilirse kampanyanın tamamı engellenir.

6. **Makine öğrenmesi modelleri** , kimlik avı girişimlerini algılamak için iletinin üst bilgisine, gövde içeriğine ve URL'lerine göre hareket eder.

7. Microsoft, bilinen bir kötü amaçlı URL'ye sahip tüm iletileri engellemek için URL korumalı alanının yanı sıra **URL saygınlığının yanı sıra URL itibarını engelleyen** üçüncü taraf akışlarından gelen URL itibarını belirler.

8. **İçerik buluşsal yöntemleri** , makine öğrenmesi modellerini kullanarak iletinin gövdesindeki yapıya ve sözcük sıklığına göre şüpheli iletileri algılayabilir.

9. **Kasa Ekler**, daha önce hiç görülmemiş tehditleri algılamak için dinamik analiz kullanarak Office 365 için Defender müşteriler için her eki korumalı alanlara ekler.

10. **Bağlantılı içerik patlama** , e-postadaki bir dosyaya bağlanan her URL'yi ek olarak ele alır ve teslim sırasında dosyayı zaman uyumsuz olarak korumalı alana alır.

11. **Url Detonation** upstream anti-phishing teknolojisi şüpheli bir ileti veya URL bulduğunda oluşur. URL patlama, teslim sırasında iletideki URL'leri korumalı alanlara ekler.

## <a name="phase-4---post-delivery-protection"></a>4. Aşama - Teslim Sonrası Koruma

Son aşama, posta veya dosya tesliminin ardından, çeşitli posta kutularında ve dosyalarda ve Microsoft Teams gibi istemcilerde görünen bağlantılarda bulunan postalar üzerinde hareket ederek gerçekleşir.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase4.png" alt-text="Office 365 için Defender'da 4. Aşama filtrelemesi teslim sonrası korumadır" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase4.png":::

1. **Kasa Bağlantıları**, Office 365 için Defender tıklama zamanı korumasıdır. Her iletideki her URL, Microsoft Kasa Bağlantıları sunucularına işaret etmek için sarmalanır. Bir URL'ye tıklandığında, kullanıcı hedef siteye yeniden yönlendirilmeden önce en son saygınlığa karşı denetlenebilir. URL, itibarını güncelleştirmek için zaman uyumsuz olarak korumalıdır.

2. **Kimlik avı için sıfır saatlik otomatik temizleme (ZAP),** zaten Exchange Online posta kutularına teslim edilmiş kötü amaçlı kimlik avı iletilerini geriye dönük olarak algılar ve etkisiz hale getirmektedir.

3. **Kötü amaçlı yazılım için ZAP**, daha önce Exchange Online posta kutularına teslim edilmiş kötü amaçlı yazılım iletilerini geçmişe dönük olarak algılar ve nötrleştirir.

4. **İstenmeyen postalar için ZAP**, önceden Exchange Online posta kutularına teslim edilmiş olan kötü amaçlı istenmeyen posta iletilerini geriye dönük olarak algılar ve etkisiz hale getirmektedir.

5. **Kampanya Görünümleri** , yöneticilerin herhangi bir ekibin otomasyon olmadan görebileceğinden daha hızlı ve tamamen bir saldırının büyük resmini görmesine olanak sağlar. Microsoft, kampanyaların tanımlanmasına yardımcı olmak için hizmetin tamamında çok miktarda kimlik avı, istenmeyen posta önleme ve kötü amaçlı yazılımdan koruma verilerinden yararlanır ve ardından yöneticilerin bunları baştan sona araştırmasına olanak tanır( hedefler, etkiler ve akışlar da dahil olmak üzere) indirilebilir kampanya yazma işlemlerinde de kullanılabilir.

6. **Rapor İletisi eklentileri** , daha fazla analiz için kişilerin hatalı pozitifleri (iyi e-posta, yanlışlıkla *kötü* olarak işaretlenmiş) veya hatalı negatifleri ( *iyi* olarak işaretlenmiş hatalı e-postalar) kolayca Microsoft'a bildirmesini sağlar.

7. **Office istemcileri için Kasa Bağlantıları**, Word, PowerPoint ve Excel gibi Office istemcilerin içinde yerel olarak aynı Kasa Bağlantılar tıklama zamanı koruması sunar.

8. **OneDrive, SharePoint ve Teams için** koruma, OneDrive, SharePoint ve Microsoft Teams içinde, yerel olarak kötü amaçlı dosyalara karşı aynı Kasa Ekler koruması sunar.

9. Teslim sonrasında dosyaya işaret eden bir URL seçildiğinde, dosyanın korumalı alanı tamamlanana ve URL'nin güvenli olduğu bulunana kadar **bağlantılı içerik patlama** bir uyarı sayfası görüntüler.

## <a name="the-filtering-stack-diagram"></a>Filtreleme yığını diyagramı

Son diyagram (diyagramı oluşturan diyagramın tüm bölümlerinde olduğu gibi) *ürün büyüdükçe ve geliştikçe değiştirilebilir*. Bu sayfaya yer işareti ekleyin ve güncelleştirmelerin ardından sormanız gerekirse en altta bulabileceğiniz **geri bildirim** seçeneğini kullanın. Kayıtlarınız için bu, tüm aşamaların sırasıyla yer alan yığındır:

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase5.png" alt-text="1 ile 4 Office 365 için Defender sıralı filtrelemenin tüm aşamaları" lightbox="../../media/mdo-filtering-stack/mdo-filter-stack-phase5.png":::

## <a name="more-information"></a>Daha fazla bilgi

***şu anda** _ Office 365 için Microsoft Defender ayarlamanız gerekiyor mu? Kuruluşunuzu korumaya başlamak için bu _now* yığınını [bu adım adım](protect-against-threats.md) kullanarak kullanın.

*MSFTTracyP ve belge yazma ekibinden Giulian Garruba'ya bu içerik için özel teşekkür ederiz*.
