---
title: Office 365 için Microsoft Defender'da adım adım tehdit koruması Office 365
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
description: Gelen bir iletinin yolunu, iş için Microsoft Defender'daki tehdit filtreleme yığını Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 62d7ac9f13f59fce3b635f6d1dace2f22ee7f503
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683833"
---
# <a name="step-by-step-threat-protection-in-microsoft-defender-for-office-365"></a>Microsoft Defender'da güvenlik tehditlerini adım adım Office 365

Koruma veya filtreleme Office 365 için Microsoft Defender, bu makaledeki gibi 4 aşamaya ya da 4 aşamaya kadar tamamlanır. Genel olarak, gelen posta teslimden önce tüm bu aşamalardan geçer, ancak asıl yol e-postası e-postanın gerçek yolu, e-posta yapılandırması için Office 365 bağlıdır.

> [!TIP]
> Uygulama koruması için Defender'ın 4 aşamasının birleşik grafiği  için bu makalenin sonuna kadar Office 365 devam edin!

## <a name="phase-1---edge-protection"></a>Aşama 1 - Kenar Koruması

Ne yazık ki, bir zamanlar kritik olan *Edge blokları* , artık yenilecek kötü bir temel için görece daha basittir. Burada zaman içinde daha az trafik engellenir, ancak yığının önemli bir parçası olarak kalır.  

Kenar blokları otomatik olarak tasarlanmıştır. Hatalı pozitif sonuçlar olması durumunda gönderenlere bu durum bildirilecek ve sorunu nasıl ele amayacakları anlatıldı. Sınırlı saygınlığı olan güvenilir iş ortaklarından gelen bağlayıcılar teslim edilebilirlik sağlar veya yeni uç noktalar eklemeye devam etmek için geçici geçersiz kılmalar kullanılabilir.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase1.png" alt-text="Uygulama için Defender'da filtrelemenin 1. Office 365 Edge Koruması'dır.":::

1. **Ağ azaltma,** belirli bir Office 365 altyapısı tarafından göndereb üzere ileti sayısını sınırlayın, bu altyapıyı ve müşterileri Hizmet Engelleme (DOS) saldırılarından korur.

2. **IP itibarı ve azaltma,** IP adreslerinin bilinen hatalı bağlantılarından gelen iletilerin engellenmiş olduğunu sağlar. Belirli bir IP kısa bir süre içinde çok sayıda ileti gönderirse, bu kısıtlar.

3. **Etki alanı itibarı** , bilinen kötü bir etki alanındaki tüm iletileri engellemektedir.

4. **Dizin tabanlı kenar filtreleme blokları** SMTP aracılığıyla kuruluşun dizin bilgilerini toplamaya çalışır.

5. **Geri yaslama algılaması** , kuruluşun geçersiz teslim edilemedi raporları (NDR) aracılığıyla saldırıya neden olmasını önler.

6. **Bağlayıcılar için iyileştirilmiş filtreleme**, trafik başka bir cihazdan geçse bile kimlik doğrulama bilgilerini daha önce Office 365. Bu, karmaşık veya karma yönlendirme senaryolarında bile, heuristic kümeleme, kimlik sahtesi önleme ve kimlik avı önleme makine öğrenme modelleri de içinde olmak üzere filtreleme yığınının doğruluğunu geliştirmektedir.

## <a name="phase-2---sender-intelligence"></a>Aşama 2 - Gönderen Zekası

Gönderen zekası özellikleri istenmeyen postaları, toplu iletileri, kimliğe bürünme ve yetkisiz kimlik sahtesi iletilerini yakalamak için kritik öneme sahiptir ve ayrıca kimlik avı algılamaya faktör sağlar. Bu özelliklerin çoğu tek tek yapılandırılabilir.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase2.png" alt-text="Office 365 için Defender'da filtrelemenin 2. aşaması Sender Intelligence'tir.":::

1. **Hesap ödünle tutarlı** olan anormal davranışlara sahip olduğunda hesap güvenliği algılama tetikleyicileri ve uyarıları yükseltildi. Bazı durumlarda, kullanıcı hesabı engellenir ve kuruluşun güvenlik işlemleri ekibi tarafından sorun çözülene kadar başka e-posta iletileri göndermesi engellenir.

2. **E-posta** Kimlik Doğrulaması, gönderenlerin yetkili ve güvenilir posta gönderenlerden emin olması amacıyla, müşterinin Bulutta ayarlanmış yöntemlerini ve yöntemlerini içerir. Bu yöntemler kimlik doğrulamalarına karşı karşı koyar.
    - **SPF** , IP adreslerinin ve kuruluşun adına posta göndermesine izin verilen sunucuların liste bulunduğu DNS TXT kayıtlarına bağlı olarak postaları reddedebilirsiniz.
    - **DKIM** , gönderenin kimliğini doğru sağlayan şifreli bir imza sağlar.
    - **DMARC** , yöneticilerin etki alanında SPF ve DKIM'yi gerekli olarak işaretlemesine olanak sağlar ve bu iki teknolojinin sonuçları arasında hizalamayı zorunlu bırakır.
    - **ARC** müşteri yapılandırılmaz, ancak posta listelerinde iletmeyle çalışırken bir kimlik doğrulama zinciri kaydederken DMARC'yi temeller.

3. **Sahte adresli** ifade, kurumsal veya bilinen dış etki alanlarını taklit eden kötü niyetli gönderenlerden "sahte adres" (başka bir ifadeyle başka bir hesap adına posta gönderenler veya posta listesi için iletme) izin verilenleri filtreleyebilirsiniz. Yasal olarak 'adına' postayı, istenmeyen posta ve kimlik avı iletilerini teslim etmek için kimlik sahtesi yapan gönderenlerden ayırıyor.

    **Kuruluş içi kullanıcı hesabı, kuruluş** içindeki bir etki alanında yapılanma girişimleri tespit eder ve engeller.

4. **Etki alanı arası bilgi hesabı, kuruluş** dışındaki bir etki alanında yapılan kullanıcı hesabı girişimlerini algılar ve engeller.

5. **Toplu filtreleme,** yöneticilerin iletinin bir toplu gönderenden gönderip gönderilme olmadığını gösteren bir toplu güven düzeyi (BCL) yapılandırmasını sağlar. Yöneticiler istenmeyen posta olarak hangi toplu posta düzeyine karar vermek için Posta Önleme ilkesinde Toplu Kaydırıcı'yı kullanabilirler.

6. **Posta kutusu zekası** , standart kullanıcı e-posta davranışlarından öğrenir. Gönderenin yalnızca, kullanıcının çoğunlukla iletişimde olduğu ama aslında kötü amaçlı bir kişi olduğunu algılayan bir kullanıcının iletişim grafiğinden yararlanan bir grafiktir. Bu yöntem kimliğe bürünme algılar.

7. **Posta kutusu zekası kimliğe** bürünme, her kullanıcının tek tek gönderen haritasına dayalı olarak geliştirilmiş kimliğe bürünme sonuçlarını etkinleştiren veya devre dışı bırakarak. Etkinleştirildiğinde, bu özellik kimliğe bürünme özelliğini tanımlamanıza yardımcı olur.

8. **Kullanıcı kimliğe bürünme** , yöneticinin kimliğine bürünülme olasılığı yüksek değerli hedeflerden bir liste oluşturmasını sağlar. Gönderenin yalnızca korumalı yüksek değerli hesabın adıyla ve adresiyle aynı görünen bir posta geldiğinde, posta işaretlenir veya etiketlenir. (Örneğin, *trα cye@contoso.com* *tracye@contoso.com).*

9. **Etki alanı kimliğe** bürünme, alıcının etki alanına benzeyen ve bir iç etki alanı gibi etmeye çalışan etki alanlarını algılar. Örneğin, bu kimliğe *bürünme tracye@liw α re.com* *kimliğine tracye@litware.com*.

## <a name="phase-3---content-filtering"></a>Aşama 3 - İçerik Filtreleme

Bu aşamada, filtreleme yığını postanın köprüleri ve ekleri de içinde olmak üzere belirli içeriğini işlemeye başlar.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase3.png" alt-text="MDO'da filtrelemenin aşama 3'ü İçerik Filtrelemedir.":::

1. **Aktarım kuralları** (posta akış kuralları veya aynı Exchange aktarım kuralları olarak da bilinir), bir ileti için eşit geniş bir koşullar karşı geldiğinde yöneticinin çok çeşitli eylemler gerçekleştiremelerine olanak sağlar. Etkin posta akış kurallarına /aktarım kurallarına göre, tüm kuruluşlarınız tarafından akan iletiler değerlendirilir.

2. **Microsoft Defender Virüsten Koruma** iki üçüncü *taraf Virüsten* Koruma altyapısı, eklerde bilinen tüm kötü amaçlı yazılımları algılamak için kullanılır.

3. Virüsten koruma (AV) altyapıları da tüm ekleri doğru olarak yazarak, Tür engellemenin yönetici tarafından  belirtilen tüm tür eklerini engelleyiğine kadar kullanılır.

4. Office 365 için Microsoft Defender kötü amaçlı bir ek, dosyanın karması ve etkin içeriğinin karma olduğunu her algılasa, Exchange Online Protection (EOP) itibarına eklenir. **Eklerin itibarını** engellemesi, MSAV bulut çağrıları aracılığıyla tüm Office 365 ve uç noktalarda bu dosyayı engelleecektir.

5. **Heuristic kümeleme** , teslim davranışlarına dayalı olarak dosyanın şüpheli olduğunu belirler. Şüpheli bir ek bulunursa, kampanyanın tamamı duraklatılır ve dosya korumalı olarak bulunur. Dosya kötü amaçlı olarak bulunursa, kampanyanın tamamı engellenir.

6. **Makine öğrenme modelleri** kimlik avı girişimlerini algılamak için iletinin üst bilgi, gövde içeriği ve URL'leri üzerinde çalışır.

7. Microsoft, BILINEN kötü amaçlı URL'lere sahip her iletiyi engellemek için, URL korumalı alandan gelen bir itibarın yanı sıra URL itibarını engelleyen üçüncü taraf akışlarından gelen **URL** itibarını da kullanır.

8. **İçerik tamamları,** makine öğrenme modelleri kullanarak ileti gövdesi içindeki yapı ve sözcük sıklığına dayalı olarak şüpheli iletileri algılanabilir.

9. **Kasa, önceden** asla görülmeyilen tehditleri tespit etmek için dinamik çözümleme kullanarak Office 365 Defender'ın tüm eklerini korumalı alanlara ekler.

10. **Bağlantılı içerik detonasyonu** , e-postada bir dosyaya bağlanan her URL'yi ek olarak, teslim sırasında dosyayı zaman uyumsuz olarak korumalı alan olarak kabul edin.

11. **Akışta kimlik avı** önleme teknolojisi şüpheli bir ileti veya URL bulduğunda URL Detonation gerçekleşir. URL detonation sandboxes the URL'ler in the message time time.

## <a name="phase-4---post-delivery-protection"></a>Aşama 4 - Teslim Sonrası Koruması

Son aşama, posta veya dosya teslimi sonrasında, çeşitli posta kutuları ve posta kutuları gibi istemcilerde görünen dosya ve bağlantılarda olan posta üzerinde Microsoft Teams.

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase4.png" alt-text="Yayın için Defender'da filtrelemenin 4. Office 365 Teslim sonrası korumasıdır.":::

1. **Kasa Bağlantıları**, Office 365 tıklama süresi koruması için Defender'dır. Her iletide yer alan her URL, Microsoft posta bağlantıları sunucularına işaret Kasa kaydırılmış. URL'ye tıklendiğinde, kullanıcı hedef siteye yönlendirmeden önce en son itibarına göre denetlenir. URL, itibarını güncelleştirmek için zaman uyumsuz korumalı alandır.

2. **Kimlik avı için sıfır saatlik otomatik temizleme (ZAP),** önceden bu posta kutularına teslim edilen kötü amaçlı kimlik avı iletilerini geriye dönük olarak algılar ve Exchange Online olur.

3. **Kötü amaçlı yazılım için ZAP**, önceden bu posta kutularına teslim edilen kötü amaçlı kötü amaçlı yazılım iletilerini geriye dönük olarak algılar Exchange Online eder.

4. **spam için ZAP**, önceden bu posta kutularına teslim edilen kötü amaçlı istenmeyen posta iletilerini geriye dönük olarak algılar Exchange Online devre dışı bırakılır.

5. **Kampanya Görünümleri** yöneticilerin, herhangi bir ekibin otomasyon olmadan gerçekleştirebileceklerine göre bir saldırının büyük resmini, daha hızlı ve daha tamamen görmelerini sağlar. Microsoft, kampanyaları tanımlamaya yardımcı olmak için tüm hizmet genelinde çok miktarda kimlik avı önleme, istenmeyen posta önleme ve kötü amaçlı yazılımdan koruma verilerinden faydalanarak yöneticilerin, indirilebilir bir kampanyada da bulunan hedefler, etkiler ve akışlar dahil olmak üzere bunları baştan sona incelemelerine olanak sağlar.

6. **İletiYi Bildir eklentileri** , kişilerin hatalı pozitif sonuçları (iyi e-posta, yanlışlıkla kötü olarak işaretlenen *) veya* hatalı negatifleri (iyi olarak işaretlenmiş kötü e-posta *)* Microsoft'a daha fazla çözümleme yapmak için kolayca bildirmelerini sağlar.

7. **Kasa Office** istemcileri için bağlantılar aynı Kasa Word, PowerPoint ve Office istemcilerinin içinde yerel olarak tıklama süresi koruması Excel.

8. **OneDrive, SharePoint ve Teams** için Koruma, OneDrive, SharePoint ve Microsoft Teams'de yerel olarak kötü amaçlı dosyalara karşı aynı Kasa Ekleri koruması sunar.

9. Teslim sonrası bir dosyayı gösteren bir URL seçildiğinde, bağlantılı içerik **detonasyonu** dosyanın korumalı alanı tamamlandıktan ve URL'nin güvenli olduğu bulunana kadar bir uyarı sayfası görüntüler.

## <a name="the-filtering-stack-diagram"></a>Filtre yığını diyagramı

Diyagramı oluşturmanın tüm kısımlarında olduğu gibi son diyagram da ürün büyüdükçe ve gelişiyor. Güncelleştirmelerden sonra **sormanız gerekirse** , bu sayfaya yer işareti ekleyin ve altta bulunan geri bildirim seçeneğini kullanın. Kayıtlarınız için bu, tüm aşamaları sırayla yığınla gösterir:

:::image type="content" source="../../media/mdo-filtering-stack/mdo-filter-stack-phase5.png" alt-text="1'den 4'e kadar olmak Office 365 için Defender'da filtrelemenin tüm aşamaları.":::

## <a name="more-information"></a>Daha fazla bilgi

şu anda * için Microsoft Defender'ı Office 365 **gerekir** _? Organizasyonlarınızı korumaya _now adım adım bu adım bu yığını [kullanın](protect-against-threats.md) (_now*).

*Bu içerik için MSFTTracyP'den ve Giulian Garruba'ya belge yazma ekibinden özel teşekkürler.*
