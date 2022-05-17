---
title: Microsoft 365'da otomatik olarak duyarlılık etiketi uygulama
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
ms.topic: article
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: Duyarlılık etiketi oluşturduğunuzda, dosyalara ve e-postalara otomatik olarak bir etiket atayabilir veya kullanıcılardan önerdiğiniz etiketi seçmelerini isteyebilirsiniz.
ms.openlocfilehash: b1a364fc6053483a05d0ea055000b863b31a94cf
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438037"
---
# <a name="apply-a-sensitivity-label-to-content-automatically"></a>İçeriğe otomatik olarak bir hassasiyet etiketi uygulama

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!TIP]
> Veri eşlemesine otomatik olarak duyarlılık etiketi uygulama hakkında bilgi için bkz. [Microsoft Purview Veri Eşlemesi'nde etiketleme](/azure/purview/create-sensitivity-label).

Duyarlılık etiketi oluşturduğunuzda, belirttiğiniz koşullarla eşleştiğinde bu etiketi dosyalara ve e-postalara otomatik olarak atayabilirsiniz.

İçeriklere duyarlılık etiketlerini otomatik olarak uygulayabilme özelliği önemlidir çünkü:

- Sınıflandırmalarınızın her birini kullanmak için kullanıcılarınızı eğitmek zorunda değilsiniz.

- Tüm içeriği doğru sınıflandırmak için kullanıcılara güvenmeniz gerekmez.

- Kullanıcıların artık ilkeleriniz hakkında bilgi sahibi olması gerekmez; bunun yerine çalışmalarına odaklanabilir.

Microsoft 365 içeriğine otomatik olarak duyarlılık etiketi uygulamak için iki farklı yöntem vardır:

- **Kullanıcılar belgeleri düzenlerken veya e-posta oluştururken (aynı zamanda yanıtlarken veya iletirken) istemci tarafı etiketleme: Dosyalar ve e-postalar** için otomatik etiketleme için yapılandırılmış bir etiket kullanın (Word, Excel, PowerPoint ve Outlook içerir).

    Bu yöntem, kullanıcılara etiket önermeyi ve otomatik olarak etiket uygulamayı destekler. Ancak her iki durumda da kullanıcı, içeriğin doğru etiketlenmesine yardımcı olmak için etiketi kabul etmeye veya reddetmeye karar verir. Belge kaydedilmeden önce bile etiket uygulanabileceğinden, bu istemci tarafı etiketlemesi belgeler için çok az gecikmeye neden olur. Ancak tüm istemci uygulamaları otomatik etiketlemeyi desteklemez. Bu özellik, [Office bazı sürümleriyle](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps) yerleşik etiketleme ve ayrıca Azure Information Protection birleşik etiketleme istemcisi tarafından desteklenir.

    Yapılandırma yönergeleri için bkz. Bu sayfadaki [Office uygulamaları için otomatik etiketlemeyi yapılandırma](#how-to-configure-auto-labeling-for-office-apps).

- **İçerik zaten kaydedildiğinde (SharePoint veya OneDrive) veya e-postayla gönderildiğinde (Exchange Online tarafından işlendiğinde) hizmet tarafı etiketleme**: Otomatik etiketleme ilkesi kullanın.
    
    Bekleyen veriler (SharePoint ve OneDrive belgeler) ve aktarımdaki veriler (Exchange tarafından gönderilen veya alınan e-posta) için otomatik etiketleme olarak adlandırılan bu yöntemi de duyabilirsiniz. Exchange için bekleyen e-postaları (posta kutuları) içermez.
    
    Bu etiketleme uygulamalar yerine hizmetler tarafından uygulandığından, kullanıcıların hangi uygulamalara sahip olduğu ve hangi sürüme sahip olduğu konusunda endişelenmeniz gerekmez. Sonuç olarak, bu özellik kuruluşunuz genelinde hemen kullanılabilir ve büyük ölçekte etiketleme için uygundur. Kullanıcı etiketleme işlemiyle etkileşim kurmadığından otomatik etiketleme ilkeleri önerilen etiketlemeyi desteklemez. Bunun yerine yönetici, etiketi uygulamadan önce içeriğin doğru etiketlenmesine yardımcı olmak için ilkeleri simülasyonda çalıştırır.

    Yapılandırma yönergeleri için bu sayfadaki [SharePoint, OneDrive ve Exchange için otomatik etiketleme ilkelerini yapılandırma](#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) konusuna bakın.
    
    SharePoint ve OneDrive için otomatik etiketlemeye özgü:
    
    - Word (.docx), PowerPoint (.pptx) ve Excel (.xlsx) için Office dosyaları desteklenir.
        - Bu dosyalar, otomatik etiketleme ilkeleri oluşturulmadan önce veya oluşturulduktan sonra bekleyen konumda otomatik olarak etiketlenebilir. Dosyalar açık bir oturumun parçasıysa (dosya açıksa) otomatik olarak etiketlenemez.
        - Şu anda liste öğelerine yönelik ekler desteklenmez ve otomatik olarak etiketlenmez.
    - Kiracınızda günde en fazla 25.000 otomatik olarak etiketlenmiş dosya.
    - Her biri ayrı ayrı belirtildiğinde en fazla 100 siteyi (SharePoint veya OneDrive) hedefleyen kiracı başına en fazla 100 otomatik etiketleme ilkesi. Tüm siteleri de belirtebilirsiniz ve bu yapılandırma en fazla 100 siteden muaf tutulur.
    - Hem simülasyon modu hem de etiketlerin uygulandığı durumlarda, değiştirme, değiştirme ve tarih için mevcut değerler otomatik etiketleme ilkelerinin bir sonucu olarak değiştirilmez.
    - Etiket şifreleme uyguladığında[, Rights Management veren ve Rights Management sahibi](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) dosyayı son değiştiren hesaptır. Bu hesap artık Azure Active Directory içinde değilse, bu değerler ayarlanamadığından etiket uygulanmaz.

    Exchange için otomatik etiketlemeye özgü:
    
    - Office uygulamalarıyla el ile etiketleme veya otomatik etiketlemeden farklı olarak, PDF eklerinin yanı sıra Office ekleri de otomatik etiketleme ilkenizde belirttiğiniz koşullar için taranır. Eşleşme olduğunda, e-posta etiketli olur ancak ek etiketlenmez.
        - PDF dosyaları için, etiket şifreleme uygularsa, kiracınız [PDF ekleri için etkinleştirildiğinde](ome-faq.yml#are-pdf-file-attachments-supported-) bu dosyalar [İleti şifrelemesi](ome.md) kullanılarak şifrelenir.
        - Bu Office dosyaları için Word, PowerPoint ve Excel desteklenir. Etiket şifreleme uygularsa, [bunlar İleti şifrelemesi](ome.md) kullanılarak şifrelenir.
    - IRM şifrelemesi uygulayan Exchange posta akışı kurallarınız veya Microsoft Purview Veri Kaybı Önleme (DLP) ilkeleriniz varsa: İçerik bu kurallar veya ilkeler ve otomatik etiketleme ilkesi tarafından tanımlandığında etiket uygulanır. Bu etiket şifreleme uygularsa, Exchange posta akışı kuralları veya DLP ilkelerindeki IRM ayarları yoksayılır. Ancak bu etiket şifreleme uygulamazsa, etikete ek olarak posta akışı kurallarından veya DLP ilkelerinden gelen IRM ayarları da uygulanır.
    - Etiketi olmayan IRM şifrelemesi olan e-posta, otomatik etiketleme kullanılarak eşleşme olduğunda herhangi bir şifreleme ayarına sahip bir etiketle değiştirilir.
    - Otomatik etiketleme koşullarınızla eşleşme olduğunda gelen e-posta etiketlenmiştir. Bu etiket [şifreleme](encryption-sensitivity-labels.md) için yapılandırılmışsa, gönderen kuruluşunuzdan geldiğinde bu şifreleme her zaman uygulanır. Varsayılan olarak, gönderen kuruluşunuzun dışındayken bu şifreleme uygulanmaz, ancak **e-posta için Ek ayarlar** yapılandırılarak ve bir Rights Management sahibi belirtilerek uygulanabilir.
    - Etiket şifreleme uyguladığında, gönderen kendi kuruluşunuzdan olduğunda e-postayı gönderen kişi Rights Management [veren ve Rights Management sahibidir](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner). Gönderen kuruluşunuzun dışındayken, gelen e-posta için ilkeniz tarafından etiketlenen ve şifrelenen bir Rights Management sahibi belirtebilirsiniz.
    - Etiket [dinamik işaretler](sensitivity-labels-office-apps.md#dynamic-markings-with-variables) uygulamak üzere yapılandırılmışsa, gelen e-posta için bu yapılandırmanın kuruluşunuz dışındaki kişilerin adlarının görüntülenmesine neden olabileceğini unutmayın.

## <a name="compare-auto-labeling-for-office-apps-with-auto-labeling-policies"></a>otomatik etiketleme ilkeleriyle Office uygulamaları için otomatik etiketlemeyi karşılaştırma

İki tamamlayıcı otomatik etiketleme yönteminin davranış farklarını belirlemenize yardımcı olması için aşağıdaki tabloyu kullanın:

|Özellik veya davranış|Etiket ayarı: Dosyalar ve e-postalar için otomatik etiketleme  |İlke: Otomatik etiketleme|
|:-----|:-----|:-----|
|Uygulama bağımlılığı|Evet ([en düşük sürümler](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps)) |No \* |
|Konuma göre kısıtla|Hayır |Evet |
|Koşullar: Eğitilebilir sınıflandırıcılar|Evet |Hayır |
|Koşullar: E-posta için paylaşım seçenekleri ve ek seçenekler|Hayır |Evet |
|Koşullar: Özel Durumlar|Hayır |Evet (yalnızca e-posta) |
|Öneriler, ilke araç ipucu ve kullanıcı geçersiz kılmaları|Evet |Hayır |
|Simülasyon modu|Hayır |Evet |
|Koşullar için denetlenen ekleri Exchange|Hayır | Evet|
|Görsel işaretler uygulama |Evet |Evet (yalnızca e-posta) |
|Etiket olmadan uygulanan IRM şifrelemeyi geçersiz kılma|Evet, kullanıcının dışarı aktarma en düşük kullanım hakkı varsa |Evet (yalnızca e-posta) |
|Gelen e-postayı etiketle|Hayır |Evet|
|Başka bir kuruluştan gönderilen e-postalar için Rights Management sahibi atama |Hayır |Evet|
|E-postalar için, aynı veya daha düşük önceliğe sahip mevcut etiketi değiştirin |Hayır |Evet (yapılandırılabilir)|

\* Arka uç Azure bağımlılığı nedeniyle otomatik etiketleme şu anda tüm bölgelerde kullanılamamaktadır. Kiracınız bu işlevi destekleyemiyorsa **Otomatik etiketleme** sekmesi Microsoft Purview uyumluluk portalı görünmez. Daha fazla bilgi için bkz. [Ülkeye göre Azure bağımlılığı kullanılabilirliği](/troubleshoot/azure/general/dependency-availability-by-country).

## <a name="how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label"></a>Birden çok etikete uygulandığında birden çok koşul nasıl değerlendirilir?

Etiketler, ilkede belirttiğiniz konumlarına göre değerlendirme için sıralanır: önce konumlandırılan etiket en düşük konuma (en az duyarlı) ve en son konumlandırılan etiket en yüksek konuma (en hassas) sahiptir. Öncelik hakkında daha fazla bilgi için bkz. [Etiket önceliği (sipariş konuları)](sensitivity-labels.md#label-priority-order-matters).

## <a name="dont-configure-a-parent-label-to-be-applied-automatically-or-recommended"></a>Bir üst etiketi otomatik olarak uygulanacak veya önerilecek şekilde yapılandırma

İçeriğe üst etiket (alt etiketli bir etiket) uygulayamazsınız. Bir üst etiketi Office uygulamalarda otomatik olarak uygulanacak veya önerilecek şekilde yapılandırmadığınızdan emin olun ve otomatik etiketleme ilkesi için üst etiket seçmeyin. Bunu yaparsanız, üst etiket içeriğe uygulanmaz.

Alt etiketli otomatik etiketlemeyi kullanmak için hem üst etiketi hem de alt etiketi yayımladığınızdan emin olun.

Üst etiketler ve alt etiketler hakkında daha fazla bilgi için bkz. [Alt etiketler (etiketleri gruplandırma).](sensitivity-labels.md#sublabels-grouping-labels)..

## <a name="will-an-existing-label-be-overridden"></a>Mevcut bir etiket geçersiz kılınacak mı?

> [!NOTE]
> E-posta otomatik etiketleme ilkeleri için yeni eklenen bir ayar, eşleşen duyarlılık etiketinin her zaman mevcut etiketi geçersiz kılacağını belirtmenize olanak sağlar.

Otomatik etiketlemenin var olan bir etiketi geçersiz kılıp geçersiz kılmayacağı varsayılan davranış:

- İçerik el ile etiketlendiğinde, bu etiket otomatik etiketleme ile değiştirilmez.

- Otomatik etiketleme, otomatik olarak uygulanan [düşük öncelikli duyarlılık etiketinin](sensitivity-labels.md#label-priority-order-matters) yerini alır, ancak daha yüksek öncelikli bir etiketi değiştirmez.
    
    > [!TIP]
    > Örneğin, Microsoft Purview uyumluluk portalı listenin en üstündeki duyarlılık etiketi 0 sipariş numarasıyla (öncelik) **Genel** olarak, listenin en altındaki duyarlılık etiketi ise sipariş numarası (öncelik 4) ile **Çok Gizli** olarak adlandırılır. **Çok Gizli** etiketi **Genel** etiketi geçersiz kılabilir, ancak tersine geçersiz kılabilir.

Yalnızca e-posta otomatik etiketleme ilkeleri için, nasıl uygulandığından bağımsız olarak mevcut duyarlılık etiketini her zaman geçersiz kılmak için bir ayar seçebilirsiniz.

|Mevcut etiket |Etiket ayarıyla geçersiz kıl: Dosyalar ve e-postalar için otomatik etiketleme  |İlkeyle geçersiz kılma: Otomatik etiketleme|
|:-----|:-----|:-----|
|El ile uygulanan, herhangi bir öncelik|Word, Excel, PowerPoint: Hayır <br /><br> Outlook: Hayır  |SharePoint ve OneDrive: Hayır <br /><br> Exchange: Varsayılan olarak hayır, ancak yapılandırılabilir |
|İlkeden otomatik olarak uygulanan veya varsayılan etiket, düşük öncelikli |Word, Excel, PowerPoint: Evet <br /><br> Outlook: Evet | SharePoint ve OneDrive: Evet <br /><br> Exchange: Evet |
|İlkeden otomatik olarak uygulanan veya varsayılan etiket, daha yüksek öncelik |Word, Excel, PowerPoint: Hayır <br /><br> Outlook: Hayır |SharePoint ve OneDrive: Hayır <br /><br> Exchange: Varsayılan olarak hayır, ancak yapılandırılabilir |

E-posta otomatik etiketleme ilkeleri için yapılandırılabilir ayar, **E-posta için ek ayarlar** sayfasındadır. Bu sayfa, Exchange konumunu içeren otomatik etiketleme ilkesi için duyarlılık etiketi seçtikten sonra görüntülenir.

## <a name="how-to-configure-auto-labeling-for-office-apps"></a>Office uygulamaları için otomatik etiketlemeyi yapılandırma

Office uygulamalarında yerleşik etiketleme için Office uygulamalarda otomatik etiketleme için [gereken en düşük sürümleri](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps) denetleyin.

Azure Information Protection birleşik etiketleme istemcisi yalnızca yerleşik ve özel hassas bilgi türleri için otomatik etiketlemeyi destekler ve Tam Veri Eşleştirme (EDM) veya adlandırılmış varlıkları kullanan eğitilebilir sınıflandırıcıları veya hassas bilgi türlerini desteklemez.

Duyarlılık [etiketi oluşturduğunuzda veya düzenlediğinizde](create-sensitivity-labels.md) Office uygulamalar için otomatik etiketleme ayarları kullanılabilir. Etiketin kapsamı için **Dosyalar & e-postalarının** seçildiğinden emin olun:

![Dosyalar ve e-postalar için duyarlılık etiketi kapsam seçenekleri.](../media/filesandemails-scope-options-sensitivity-label.png)

Yapılandırmada ilerlerken, hassas bilgi türleri veya eğitilebilir sınıflandırıcılar listesinden seçim yapabileceğiniz **Dosyalar ve e-postalar için otomatik etiketleme** sayfasını görürsünüz:

![Office uygulamalarında otomatik etiketleme için etiket koşulları.](../media/sensitivity-labels-conditions.png)

Bu duyarlılık etiketi otomatik olarak uygulandığında, kullanıcı Office uygulaması bir bildirim görür. Örneğin:

![Belgenin otomatik olarak bir etiket uygulandığına ilişkin bildirim.](../media/sensitivity-labels-msg-doc-was-auto-labeled.PNG)

### <a name="configuring-sensitive-info-types-for-a-label"></a>Etiket için hassas bilgi türlerini yapılandırma

**Hassas bilgi türleri** seçeneğini belirlediğinizde, veri kaybı önleme (DLP) ilkesi oluştururken kullandığınız hassas bilgi türlerinin listesini görürsünüz. Bu nedenle, örneğin, kredi kartı numaraları, sosyal güvenlik numaraları veya pasaport numaraları gibi müşterilerin kişisel bilgilerini içeren içeriklere otomatik olarak Çok Gizli etiketi uygulayabilirsiniz:

![Office uygulamalarında otomatik etiketleme için hassas bilgi türleri.](../media/sensitivity-labels-sensitive-info-types.png)

DLP ilkelerini yapılandırdığınıza benzer şekilde, örnek sayısını değiştirip doğruluğu eşleştirerek koşulunuzu iyileştirebilirsiniz. Örneğin:

![Eşleşme doğruluğu ve örnek sayısı seçenekleri.](../media/sit-confidence-level.png)

DLP belgelerinden bu yapılandırma seçenekleri hakkında daha fazla bilgi edinebilirsiniz: [Eşleştirmeyi kolaylaştırmak veya zorlaştırmak için kuralları ayarlama](data-loss-prevention-policies.md#tuning-rules-to-make-them-easier-or-harder-to-match).

> [!IMPORTANT]
> Hassas bilgi türlerinin en fazla benzersiz örnek sayısı parametresini tanımlamanın iki farklı yolu vardır. Daha fazla bilgi edinmek için bkz [. SIT için örnek sayısı desteklenen değerler](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit).

DLP ilkesi yapılandırmasına benzer şekilde, bir koşulun tüm hassas bilgi türlerini mi yoksa yalnızca birini mi algılaması gerektiğini seçebilirsiniz. Koşullarınızı daha esnek veya karmaşık hale getirmek için [gruplar ekleyebilir ve gruplar arasında mantıksal işleçler kullanabilirsiniz](data-loss-prevention-policies.md).

> [!NOTE]
> Özel hassas bilgi türlerini temel alan otomatik etiketleme yalnızca OneDrive ve SharePoint yeni oluşturulan veya değiştirilen içerik için geçerlidir; mevcut içeriğe uygulanmıyor. Bu sınırlama otomatik etiketleme ilkeleri için de geçerlidir.

#### <a name="custom-sensitive-information-types-with-exact-data-match"></a>Tam Veri Eşleşmesi ile özel hassas bilgi türleri

Özel hassas [bilgi türleri için tam veri eşleştirme tabanlı hassas bilgi türlerini](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) kullanmak üzere bir duyarlılık etiketi yapılandırabilirsiniz. Ancak, şu anda EDM kullanmayan en az bir hassas bilgi türü de belirtmeniz gerekir. Örneğin, **Kredi kartı numarası** gibi yerleşik hassas bilgi türlerinden biri.

Hassas bilgi türü koşullarınız için yalnızca EDM ile bir duyarlılık etiketi yapılandırıyorsanız, etiket için otomatik etiketleme ayarı otomatik olarak kapatılır.

### <a name="configuring-trainable-classifiers-for-a-label"></a>Etiket için eğitilebilir sınıflandırıcıları yapılandırma

Bu seçeneği Windows sürüm 2106 veya üzeri için Microsoft 365 Uygulamaları ya da Mac sürüm 16.50 veya üzeri için Microsoft 365 Uygulamaları kullanıyorsanız, kiracınızda otomatik etiketleme ve [hassas bilgi türleri seçeneği](#configuring-sensitive-info-types-for-a-label) için yapılandırılmış en az bir duyarlılık etiketi daha yayımladığınızdan emin olun. Bu platformlarda sonraki sürümleri kullandığınızda bu gereksinim gerekli değildir.

**Eğitilebilir sınıflandırıcılar** seçeneğini belirlediğinizde, önceden eğitilmiş veya özel eğitilebilir sınıflandırıcılardan birini veya daha fazlasını seçin:

![Eğitilebilir sınıflandırıcılar ve duyarlılık etiketleri için seçenekler.](../media/sensitivity-labels-classifers.png)

> [!CAUTION]
> Çok sayıda hatalı pozitif sonuç ürettiğinden **, Rahatsız Edici Dil** önceden eğitilmiş sınıflandırıcıyı kullanım dışı bırakıyoruz. Bu sınıflandırıcıyı kullanmayın ve şu anda kullanıyorsanız iş süreçlerinizi bundan çıkarmanızı ve bunun yerine **Hedeflenen Taciz**, **Küfür** ve **Tehdit** önceden eğitilmiş sınıflandırıcıları kullanmanızı öneririz.

Bu sınıflandırıcılar hakkında daha fazla bilgi için bkz. [Eğitilebilir sınıflandırıcılar hakkında bilgi edinin](classifier-learn-about.md).

### <a name="recommend-that-the-user-applies-a-sensitivity-label"></a>Kullanıcının bir duyarlılık etiketi uygulamasını önerme

İsterseniz, kullanıcılarınıza etiketi uygulamalarını önerebilirsiniz. Bu seçenekle, kullanıcılarınız sınıflandırmayı ve ilişkili korumayı kabul edebilir veya etiket içeriği için uygun değilse öneriyi kapatabilir.

![Kullanıcılara duyarlılık etiketi önerme seçeneği.](../media/Sensitivity-labels-Recommended-label-option.png)

Aşağıda azure Information Protection birleşik etiketleme istemcisinden, özel bir ilke ipucuyla bir etiketi önerilen eylem olarak uygulayacak bir koşul yapılandırdığınızda oluşan bir istem örneği verilmiştir. İlke ipucunda hangi metnin görüntüleneceğini seçebilirsiniz.

![Önerilen etiketi uygulama istemi.](../media/Sensitivity-label-prompt-for-required-label.png)

### <a name="when-automatic-or-recommended-labels-are-applied"></a>Otomatik veya önerilen etiketler uygulandığında

Office uygulamalarında otomatik ve önerilen etiketlemenin uygulanması, Office yerleşik etiketlemeyi mi yoksa Azure Information Protection birleşik etiketleme istemcisini mi kullandığınıza bağlıdır. Ancak her iki durumda da:

- Daha önce el ile etiketlenmiş veya daha önce daha yüksek bir duyarlılıkla otomatik olarak etiketlenmiş belgeler ve e-postalar için otomatik etiketlemeyi kullanamazsınız. Unutmayın, bir belgeye veya e-postaya yalnızca tek bir duyarlılık etiketi uygulayabilirsiniz (tek bir bekletme etiketine ek olarak).

- Daha önce daha yüksek duyarlılıkla etiketlenmiş belgeler veya e-postalar için önerilen etiketlemeyi kullanamazsınız. İçerik daha yüksek bir duyarlılıkla etiketlendiğinde, kullanıcı öneri ve ilke ipucunu içeren istemi görmez.

Yerleşik etiketlemeye özgü:

- Tüm Office uygulamaları otomatik (ve önerilen) etiketlemeyi desteklemez. Daha fazla bilgi için bkz. [Uygulamalarda duyarlılık etiketi özellikleri desteği](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

- Word'ün masaüstü sürümlerinde önerilen etiketler için, öneriyi tetikleyen hassas içerik, kullanıcıların önerilen duyarlılık etiketini uygulamak yerine hassas içeriği gözden geçirip kaldırabilmesi için işaretlenir.

- Bu etiketlerin Office uygulamalarına nasıl uygulandığı, örnek ekran görüntüleri ve hassas bilgilerin nasıl algılandıklarına ilişkin ayrıntılar için bkz. [Office'da dosyalarınıza ve e-postalarınıza duyarlılık etiketlerini otomatik olarak uygulama veya önerme](https://support.microsoft.com/office/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1).

Azure Information Protection birleşik etiketleme istemcisine özgü:

- Otomatik ve önerilen etiketleme, belgeyi kaydettiğinizde Word, Excel ve PowerPoint için ve e-posta gönderdiğinizde Outlook için geçerlidir.

- Outlook önerilen etiketlemeyi desteklemesi için önce [gelişmiş bir ilke ayarı](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#enable-recommended-classification-in-outlook) yapılandırmanız gerekir.

- Belgelerde ve e-postalarda gövde metninde ve üst bilgi ve alt bilgilerde hassas bilgiler algılanabilir, ancak konu satırında veya e-posta eklerinde algılanamaz.

### <a name="convert-your-label-settings-into-an-auto-labeling-policy"></a>Etiket ayarlarınızı otomatik etiketleme ilkesine dönüştürme

> [!NOTE]
> Bu seçenek aşamalı olarak kullanıma sunulacaktır.

Etiket, yapılandırılan koşullar için hassas bilgi türleri içeriyorsa, etiket oluşturma veya düzenleme işleminin sonunda aynı otomatik etiketleme ayarlarını temel alan bir otomatik etiketleme ilkesini otomatik olarak oluşturma seçeneğini görürsünüz.

Otomatik etiketleme ilkeleri eğitilebilir sınıflandırıcıları desteklemediğinden:

- Etiket koşulları yalnızca eğitilebilir sınıflandırıcılar içeriyorsa otomatik olarak bir otomatik etiketleme ilkesi oluşturma seçeneğini görmezsiniz.

- Etiket koşulları eğitilebilir sınıflandırıcılar ve duyarlılık bilgisi türleri içeriyorsa, yalnızca hassas bilgi türleri için bir otomatik etiketleme ilkesi oluşturulur. 

İlkeyi sıfırdan oluşturduysanız el ile seçmeniz gereken değerleri otomatik olarak doldurarak sizin için otomatik olarak bir otomatik etiketleme ilkesi oluşturulsa da, kaydedilmeden önce değerleri görüntülemeye ve düzenlemeye devam edebilirsiniz.

Varsayılan olarak, SharePoint, OneDrive ve Exchange için tüm konumlar otomatik etiket ilkesine dahil edilir ve ilke kaydedildiğinde [simülasyon modunda](#learn-about-simulation-mode) çalışır. otomatik etiketlemenin SharePoint ve OneDrive içindeki içeriğe uygulanması için önkoşullardan biri olan [SharePoint ve OneDrive Office dosyaları için duyarlılık etiketlerini etkinleştirdiğinizden](sensitivity-labels-sharepoint-onedrive-files.md) hiçbir denetim yoktur.

## <a name="how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange"></a>SharePoint, OneDrive ve Exchange için otomatik etiketleme ilkelerini yapılandırma

Otomatik etiketleme ilkelerini yapılandırmadan önce önkoşulların farkında olduğunuzdan emin olun.

### <a name="prerequisites-for-auto-labeling-policies"></a>Otomatik etiketleme ilkeleri için önkoşullar

- Simülasyon modu:
  - Microsoft 365 denetimi açık olmalıdır. Denetimi açmanız gerekiyorsa veya denetimin zaten açık olup olmadığından emin değilseniz bkz. [Denetim günlüğü aramasını açma veya kapatma](turn-audit-log-search-on-or-off.md).
  - Kaynak görünümde dosya veya e-posta içeriğini görüntülemek için, **İçerik Gezgini İçerik Görüntüleyicisi** rol grubuna dahil edilen **Veri Sınıflandırma İçerik Görüntüleyicisi** rolüne veya **Information Protection** ve **Information Protection Araştırmacı rol** gruplarına (şu anda önizleme aşamasındadır) sahip olmanız gerekir. Gerekli rol olmadan, **Eşleşen Öğeler** sekmesinden bir öğe seçtiğinizde önizleme bölmesini görmezsiniz. Genel yöneticiler varsayılan olarak bu role sahip değildir.

- SharePoint ve OneDrive dosyaları otomatik olarak etiketlemek için:
  - [SharePoint ve OneDrive Office dosyaları için duyarlılık etiketlerini etkinleştirdiniz](sensitivity-labels-sharepoint-onedrive-files.md).
  - Otomatik etiketleme ilkesi çalıştırıldığında, dosya başka bir işlem veya kullanıcı tarafından açık olmamalıdır. Düzenleme için kullanıma alınmış bir dosya bu kategoriye girer.

- Yerleşik [duyarlılık türleri yerine özel hassas bilgi türleri](sensitive-information-type-learn-about.md) kullanmayı planlıyorsanız:
  - Özel duyarlılık bilgi türleri yalnızca özel duyarlılık bilgi türleri oluşturulduktan sonra SharePoint veya OneDrive eklenen veya değiştirilen içeriğe uygulanır.
  - Yeni özel hassas bilgi türlerini test etmek için, otomatik etiketleme ilkenizi oluşturmadan önce bunları oluşturun ve ardından test için örnek verilerle yeni belgeler oluşturun.

- Otomatik etiketleme ilkeleriniz için seçebileceğiniz bir veya daha fazla duyarlılık etiketi [oluşturulur ve yayımlanır](create-sensitivity-labels.md) (en az bir kullanıcıya). Bu etiketler için:
  - Office uygulamalar etiket ayarında otomatik etiketlemenin açık veya kapalı olması önemli değildir çünkü bu etiket ayarı, girişte açıklandığı gibi otomatik etiketleme ilkelerini tamamlar.
  - Otomatik etiketleme için kullanmak istediğiniz etiketler görsel işaretler (üst bilgiler, alt bilgiler, filigranlar) kullanacak şekilde yapılandırılmışsa, bunların belgelere uygulanmadığını unutmayın.
  - Etiketler [şifreleme](encryption-sensitivity-labels.md) uyguluyorsa:
    - Otomatik etiketleme ilkesi SharePoint veya OneDrive konumları içerdiğinde, etiketin **İzinleri şimdi ata** ayarı için yapılandırılması gerekir.
    - Otomatik etiketleme ilkesi yalnızca Exchange için olduğunda, etiket **şimdi izinleri ata** veya **Kullanıcıların izin atamasına izin ver** (İletme veya Encrypt-Only seçenekleri için) için yapılandırılabilir.

### <a name="learn-about-simulation-mode"></a>Simülasyon modu hakkında bilgi edinin

Simülasyon modu, otomatik etiketleme ilkelerine özgüdür ve iş akışına dokunmunu sağlar. İlkeniz en az bir benzetimi çalıştırmadan belgeleri ve e-postaları otomatik olarak etiketleyemezsiniz.

Simülasyon modu en fazla 1.000.000 eşleşen dosyayı destekler. Otomatik etiketleme ilkesinden bu sayıdan fazla dosya eşleşiyorsa, etiketleri uygulamak için ilkeyi açamazsınız. Bu durumda, otomatik etiketleme ilkesini daha az dosyanın eşleştirilmesi için yeniden yapılandırmanız ve simülasyonu yeniden çalıştırmanız gerekir. Bu en fazla 1.000.000 eşleşen dosya, duyarlılık etiketlerini uygulamak için zaten açık olan bir otomatik etiketleme ilkesi için değil, yalnızca simülasyon modu için geçerlidir.

Otomatik etiketleme ilkesi için iş akışı:

1. Otomatik etiketleme ilkesi oluşturma ve yapılandırma.

2. İlkeyi simülasyon modunda çalıştırın. Bu işlemin tamamlanması 12 saat sürebilir. Tamamlanan simülasyon, [etkinlik uyarılarını](alert-policies.md) almak üzere yapılandırılan kullanıcıya gönderilen bir e-posta bildirimini tetikler.

3. Sonuçları gözden geçirin ve gerekirse ilkenizi geliştirin. Örneğin, hatalı pozitif sonuçları azaltmak için ilke kurallarını düzenlemeniz veya eşleşen dosya sayısının 1.000.000'i aşmaması için bazı siteleri kaldırmanız gerekebilir. Simülasyon modunu yeniden çalıştırın ve tekrar tamamlanmasını bekleyin.

4. 3. adımı gerektiği gibi yineleyin.

5. Üretimde dağıtın.

Sanal dağıtım, PowerShell için WhatIf parametresi gibi çalışır. Otomatik etiketleme ilkesi, tanımladığınız kuralları kullanarak seçtiğiniz etiketi uygulamış gibi raporlanan sonuçlar görürsünüz. Daha sonra gerekirse kurallarınızı doğruluk açısından daraltabilir ve simülasyonu yeniden çalıştırabilirsiniz. Ancak, Exchange için otomatik etiketleme posta kutularında depolanan e-postalar yerine gönderilen ve alınan e-postalar için geçerli olduğundan, aynı e-posta iletilerini gönderip alamadığınız sürece simülasyondaki e-posta sonuçlarının tutarlı olmasını beklemeyin.

Simülasyon modu, dağıtımdan önce otomatik etiketleme ilkenizin kapsamını aşamalı olarak artırmanıza da olanak tanır. Örneğin, tek bir belge kitaplığıyla SharePoint site gibi tek bir konumla başlayabilirsiniz. Ardından yinelemeli değişikliklerle kapsamı birden çok siteye ve ardından OneDrive gibi başka bir konuma yükseltin.

Son olarak, simülasyon modunu kullanarak otomatik etiketleme ilkenizi çalıştırmak için gereken süreyi yaklaşık olarak belirleyerek simülasyon modu olmadan ne zaman çalıştırabileceğinizi planlayabilir ve zamanlayabilirsiniz.

### <a name="creating-an-auto-labeling-policy"></a>Otomatik etiketleme ilkesi oluşturma

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalı</a> duyarlılık etiketlerine gidin:

    - **Çözümleri** >  **Bilgi koruması**

    Bu seçeneği hemen görmüyorsanız önce **Tümünü göster'i** seçin.

2. **Otomatik etiketleme** sekmesini seçin:

    ![Otomatik etiketleme sekmesi.](../media/auto-labeling-tab.png)

    > [!NOTE]
    > **Otomatik etiketleme** sekmesini görmüyorsanız, arka uç Azure bağımlılığı nedeniyle bu işlev bölgenizde şu anda kullanılamaz. Daha fazla bilgi için bkz. [Ülkeye göre Azure bağımlılığı kullanılabilirliği](/troubleshoot/azure/general/dependency-availability-by-country).

3. **+ Otomatik etiketleme ilkesi oluştur'u** seçin. Bu, Yeni ilke yapılandırmasını başlatır:

    ![Otomatik etiketleme için yeni ilke yapılandırması.](../media/auto-labeling-wizard.png)

4. Bu **etiketin uygulanmasını istediğiniz bilgileri seçin sayfası için**: **Finansal** veya **Gizlilik** gibi şablonlardan birini seçin. Açılan menü **için seçenekleri göster'i** kullanarak aramanızı daraltabilirsiniz. İsterseniz şablonlar gereksinimlerinizi karşılamıyorsa **Özel ilke'yi** de seçebilirsiniz. **İleri**'yi seçin.

5. Otomatik **etiketleme ilkenizi adlandırın** sayfası için: Otomatik olarak uygulanan etiketi, konumları ve etiket içeriğini tanımlayan koşulları tanımlamaya yardımcı olmak için benzersiz bir ad ve isteğe bağlı olarak bir açıklama sağlayın.

6. Etiketi **uygulamak istediğiniz konumları seçin** sayfası için: Exchange, SharePoint ve OneDrive için konumları seçin ve belirtin. Seçtiğiniz konumlar için **tüm** dahil edilenler varsayılanını korumak istemiyorsanız, eklenecek belirli örnekleri seçmek için bağlantıyı seçin veya hariç tutulacak belirli örnekleri seçmek için bağlantıyı seçin. Ardından **İleri'yi** seçin.

    ![Otomatik etiketleme yapılandırması için konumları seçin sayfası.](../media/locations-auto-labeling-wizard.png)
    
    **Dahil** edilen veya **Dışlanan'ı** kullanarak varsayılan ayarları değiştirirseniz:
    
    - **Exchange** konumu için ilke, belirtilen alıcıların gönderen adresine göre uygulanır. Çoğu zaman **Hiçbiri** hariç tutulduğunda **Tümü** dahil seçeneğinin varsayılanını tutmak istersiniz. Bu yapılandırma, kullanıcıların bir alt kümesini test ediyorsanız bile uygundur. Burada kullanıcı alt kümenizi belirtmek yerine, kuruluşunuzdaki alıcıları dahil etmek veya dışlamak üzere koşulları yapılandırmak için sonraki adımda yer alan gelişmiş kuralları kullanın. Aksi takdirde, varsayılan ayarları burada değiştirdiğinizde:
        -  **Tüm** dahil edilenler'in varsayılanını değiştirirseniz ve bunun yerine belirli kullanıcıları veya grupları seçerseniz, kuruluşunuzun dışından gönderilen e-posta ilkeden muaf tutulur. 
        -  **Tüm** dahil edilenler varsayılanını tutar ancak dışlanacak kullanıcıları veya grupları belirtirseniz, dışlanan bu kullanıcıların gönderdiği e-posta ilkeden muaf tutulur, ancak aldıkları e-postalar hariç tutulur.
    
    - OneDrive hesapları için, dahil etmek veya dışlamak üzere tek tek OneDrive hesapları belirtmenize yardımcı olmak için [bkz. Kuruluşunuzdaki tüm kullanıcı OneDrive URL'lerinin listesini alma](/onedrive/list-onedrive-urls).

7. **Ortak veya gelişmiş kuralları ayarlama** sayfası için: Tüm seçtiğiniz konumlarda etiketlenmek üzere içeriği tanımlayan kuralları tanımlamak için **Ortak** kurallar varsayılanını koruyun. Exchange için daha fazla seçenek de dahil olmak üzere konum başına farklı kurallara ihtiyacınız varsa **Gelişmiş kurallar'ı** seçin. Ardından **İleri'yi** seçin.

    Kurallar hassas bilgi türlerini ve paylaşım seçeneklerini içeren koşulları kullanır:
    - Hassas bilgi türleri için hem yerleşik hem de özel hassas bilgi türlerini seçebilirsiniz.
    - Paylaşılan seçenekler için **yalnızca kuruluşumdaki kişilerle veya kuruluşum** **dışındaki kişilerle** seçim yapabilirsiniz.

    Konumunuz **Exchange** ve **Gelişmiş kurallar'ı** seçtiyseniz seçebileceğiniz başka koşullar da vardır:
    - Gönderen IP adresi
    - Alıcı etki alanı
    - Alıcı
    - Ekin dosya uzantısı
    - Ek parola korumalı
    - E-posta eklerinin içeriği taranamadı
    - E-posta eklerinin içeriği taramayı tamamlamadı
    - Üst bilgi desenleri eşleştirir
    - Konu desenleri eşleştirir
    - Alıcı adresi sözcükler içeriyor
    - Alıcı adresi desenleri eşleştirir
    - Gönderen adresi desenleri eşleştirir
    - Gönderen etki alanı
    - Alıcı,
    - Gönderen

    Bu koşulların her biri için özel durumlar belirtebilirsiniz.

8. Önceki seçimlerinize bağlı olarak, artık koşulları ve özel durumları kullanarak yeni kurallar oluşturma fırsatına sahip olacaksınız.

    Hassas bilgi türleri için yapılandırma seçenekleri, Office uygulamalar için otomatik etiketleme için seçtiğiniz seçeneklerle aynıdır. Daha fazla bilgiye ihtiyacınız varsa bkz [. Etiket için hassas bilgi türlerini yapılandırma](#configuring-sensitive-info-types-for-a-label).

    İhtiyacınız olan tüm kuralları tanımlayıp durumlarının açık olduğunu onayladıktan sonra, otomatik uygulanacak etiketi seçmeye devam etmek için **İleri'yi** seçin.

9. **Otomatik uygulanacak bir etiket seçin sayfası için**: **+ Etiket seç'i** seçin, **Duyarlılık etiketi seçin bölmesinden bir etiket seçin** ve ardından **İleri'yi** seçin.

10. İlkeniz Exchange konumu içeriyorsa: **E-posta için ek ayarlar** sayfasında isteğe bağlı yapılandırmaları belirtin:
    
    - **Aynı veya daha düşük önceliğe sahip mevcut etiketleri otomatik olarak değiştirin**: Hem gelen hem de giden e-postalar için geçerlidir, bu ayarı seçtiğinizde her zaman eşleşen bir duyarlılık etiketinin uygulanmasını sağlar. Bu ayarı seçmezseniz, [daha yüksek öncelikli](sensitivity-labels.md#label-priority-order-matters) mevcut duyarlılık etiketine sahip olan veya el ile etiketlenmiş e-postalara eşleşen bir duyarlılık etiketi uygulanmaz.
    
    - **Kuruluşunuzun dışından alınan e-postalara şifreleme uygulama**: Bu seçeneği belirlediğinizde, kuruluşunuzdaki yetkili bir kişinin kuruluşunuzun dışından ve ilke etiketlerinizden şifrelemeyle gönderilen e-postalar için Tam Denetim [kullanım haklarına](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) sahip olduğundan emin olmak için bir [Rights Management sahibi](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) atamanız gerekir. Bu rol daha sonra şifrelemeyi kaldırmak veya kuruluşunuzdaki kullanıcılar için farklı kullanım hakları atamak için gerekebilir.
        
        **Rights Management sahibi atama** için, kuruluşunuza ait bir e-posta adresine göre tek bir kullanıcı belirtin. Bu rol için desteklenmediğinden posta kişisi, paylaşılan posta kutusu veya herhangi bir grup türü belirtmeyin.

10. **İlkeyi şimdi mi yoksa sonraki sürümlerde mi test etmek istediğinize karar verin** sayfası için: Otomatik etiketleme ilkesini şimdi simülasyon modunda çalıştırmaya hazırsanız İlkeyi **simülasyon modunda çalıştır'ı** seçin. Aksi takdirde **İlkeyi kapalı bırak'ı** seçin. **İleri'yi** seçin:

    ![Yapılandırılmış otomatik etiketleme ilkesini test edin.](../media/simulation-mode-auto-labeling-wizard.png)

11. **Özet** sayfası için: Otomatik etiketleme ilkenizin yapılandırmasını gözden geçirin, gerekli değişiklikleri yapın ve yapılandırmayı tamamlayın.

**Şimdi Information** **protectionAuto** >  etiketleme sayfasında, otomatik etiketleme ilkenizi simülasyon modunda çalıştırmayı seçip seçmediğinize bağlı olarak **Simülasyon** veya **Kapalı** bölümünde görürsünüz. Yapılandırmanın ve durumun ayrıntılarını görmek için ilkenizi seçin (örneğin, **İlke benzetimi hala çalışıyor**). Simülasyon modundaki ilkeler için, hangi e-postaların veya belgelerin belirttiğiniz kurallarla eşleşdiğini görmek için **Eşleşen öğeler** sekmesini seçin.

İlkenizi doğrudan bu arabirimden değiştirebilirsiniz:

- **Kapalı** bölümündeki bir ilke için **İlkeyi düzenle** düğmesini seçin.

- **Simülasyon** bölümündeki ilke için, sayfanın üst kısmındaki **İlkeyi düzenle** seçeneğini her iki sekmeden de seçin:

    ![Otomatik etiketleme ilkesi seçeneğini düzenleyin.](../media/auto-labeling-edit.png)

    İlkeyi simülasyon olmadan çalıştırmaya hazır olduğunuzda İlkeyi **aç** seçeneğini belirleyin.

Otomatik etiketleme ilkeleri silinene kadar sürekli olarak çalışır. Örneğin, yeni ve değiştirilmiş dosyalar geçerli ilke ayarlarına eklenir.

### <a name="monitoring-your-auto-labeling-policy"></a>Otomatik etiketleme ilkenizi izleme

Otomatik etiketleme ilkeniz açıldıktan sonra, seçtiğiniz SharePoint ve OneDrive konumlarındaki dosyaların etiketleme ilerleme durumunu görüntüleyebilirsiniz. E-postalar otomatik olarak gönderildikçe etiketlendiğinden etiketleme ilerlemesine dahil değildir.

Etiketleme ilerleme durumu, ilke tarafından etiketlenecek dosyaları, son yedi gün içinde etiketlenen dosyaları ve etiketlenen toplam dosyaları içerir. Günde en fazla 25.000 dosya etiketleme sayısı nedeniyle bu bilgiler, ilkenizin geçerli etiketleme ilerleme durumunu ve etiketlenecek dosya sayısını gösterir.

İlkenizi ilk kez açtığınızda, en son veriler alınana kadar dosyaların etiketlenecekleri 0 değerini görürsünüz. Bu ilerleme bilgileri her 48 saatte bir güncelleştirilir, böylece diğer günlerle ilgili en güncel verileri görmeyi bekleyebilirsiniz. Otomatik etiketleme ilkesini seçtiğinizde, ilk 10 sitenin etiketleme ilerleme durumunu içeren bir açılır pencere bölmesinde ilke hakkında daha fazla ayrıntı görebilirsiniz. Bu açılır bölmedeki bilgiler **, Otomatik etiketleme** ana sayfasında görüntülenen toplu ilke bilgilerinden daha güncel olabilir.

Ayrıca, uygun [izinlere](data-classification-content-explorer.md#permissions) sahip olduğunuzda [içerik gezginini](data-classification-content-explorer.md) kullanarak otomatik etiketleme ilkenizin sonuçlarını da görebilirsiniz:

- **İçerik Gezgini Liste Görüntüleyicisi** rol grubu, dosyanın içeriğini değil, dosyanın etiketini görmenize olanak tanır.
- **İçerik Gezgini İçerik Görüntüleyicisi** rol grubu ve **Information Protection** ve **Information Protection Araştırmacı rol** grupları (şu anda önizleme aşamasındadır) dosyanın içeriğini görmenizi sağlar.

> [!TIP]
> İçerik gezginini, hassas bilgilere sahip belgeleri olan ancak etiketsiz olan konumları belirlemek için de kullanabilirsiniz. Bu bilgileri kullanarak otomatik etiketleme ilkenize bu konumları eklemeyi ve tanımlanan hassas bilgi türlerini kural olarak eklemeyi göz önünde bulundurun.

### <a name="use-powershell-for-auto-labeling-policies"></a>Otomatik etiketleme ilkeleri için PowerShell kullanma

Otomatik etiketleme ilkeleri oluşturmak ve yapılandırmak için [Güvenlik & Uyumluluk Merkezi PowerShell'i](/powershell/exchange/scc-powershell) kullanabilirsiniz. Bu, otomatik etiketleme ilkelerinizin oluşturulmasını ve bakımını tam olarak oluşturabileceğiniz anlamına gelir ve bu da OneDrive ve SharePoint konumlar için birden çok URL belirtmek için daha verimli bir yöntem sağlar.

PowerShell'de komutları çalıştırmadan önce [Güvenlik & Uyumluluk Merkezi PowerShell'e bağlanmanız](/powershell/exchange/connect-to-scc-powershell) gerekir.

Yeni bir otomatik etiketleme ilkesi oluşturmak için:

```powershell
New-AutoSensitivityLabelPolicy -Name <AutoLabelingPolicyName> -SharePointLocation "<SharePointSiteLocation>" -ApplySensitivityLabel <Label> -Mode TestWithoutNotifications
```

Bu komut, belirttiğiniz bir SharePoint sitesi için otomatik etiketleme ilkesi oluşturur. OneDrive bir konum için bunun yerine *OneDriveLocation* parametresini kullanın.

Mevcut otomatik etiketleme ilkesine daha fazla site eklemek için:

```powershell
$spoLocations = @("<SharePointSiteLocation1>","<SharePointSiteLocation2>")
Set-AutoSensitivityLabelPolicy -Identity <AutoLabelingPolicyName> -AddSharePointLocation $spoLocations -ApplySensitivityLabel <Label> -Mode TestWithoutNotifications
```

Bu komut, var olan otomatik etiketleme ilkesine eklenen bir değişkendeki yeni SharePoint URL'lerini belirtir. Bunun yerine OneDrive konum eklemek için *AddOneDriveLocation* parametresini *$OneDriveLocations* gibi farklı bir değişkenle kullanın.

Yeni bir otomatik etiketleme ilkesi kuralı oluşturmak için:

```powershell
New-AutoSensitivityLabelRule -Policy <AutoLabelingPolicyName> -Name <AutoLabelingRuleName> -ContentContainsSensitiveInformation @{"name"= "a44669fe-0d48-453d-a9b1-2cc83f2cba77"; "mincount" = "2"} -Workload SharePoint
```

Mevcut bir otomatik etiketleme ilkesi için bu komut, a44669fe-0d48-453d-a9b1-2cc83f2cba77 varlık kimliğine sahip olan **ABD sosyal güvenlik numarasının (SSN)** hassas bilgi türünü algılamak için yeni bir ilke kuralı oluşturur. Diğer hassas bilgi türlerinin varlık kimliklerini bulmak için [Bkz. Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md).

Otomatik etiketleme ilkelerini destekleyen PowerShell cmdlet'leri, bunların kullanılabilir parametreleri ve bazı örnekler hakkında daha fazla bilgi için aşağıdaki cmdlet yardımına bakın:

- [Get-AutoSensitivityLabelPolicy](/powershell/module/exchange/get-autosensitivitylabelpolicy)
- [New-AutoSensitivityLabelPolicy](/powershell/module/exchange/new-autosensitivitylabelpolicy)
- [New-AutoSensitivityLabelRule](/powershell/module/exchange/new-autosensitivitylabelrule)
- [Remove-AutoSensitivityLabelPolicy](/powershell/module/exchange/remove-autosensitivitylabelpolicy)
- [Remove-AutoSensitivityLabelRule](/powershell/module/exchange/remove-autosensitivitylabelrule)
- [Set-AutoSensitivityLabelPolicy](/powershell/module/exchange/set-autosensitivitylabelpolicy)
- [Set-AutoSensitivityLabelRule](/powershell/module/exchange/set-autosensitivitylabelrule)

## <a name="tips-to-increase-labeling-reach"></a>Etiketleme erişim oranını artırmak için İpuçları

Otomatik etiketleme, kuruluşunuzun sahip olduğu Office dosyaları sınıflandırmanın, etiketlemenin ve korumanın en verimli yollarından biri olsa da, etiketleme erişiminizi artırmak için aşağıdaki yöntemlerden herhangi biriyle tamamlayıp tamamlayamadığını denetleyin:

- SharePoint Syntex ile belge [anlama modeline duyarlılık etiketi uygulayarak](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model) SharePoint kitaplığındaki tanımlanan belgelerin otomatik olarak etiketlenmiş olmasını sağlayabilirsiniz.

- [Azure Information Protection birleşik etiketleme istemcisini](/azure/information-protection/rms-client/aip-clientv2) kullandığınızda:

  - Ağ paylaşımları ve SharePoint Sunucu kitaplıkları gibi şirket içi veri depolarındaki dosyalar için: Bu dosyalardaki hassas bilgileri bulmak ve uygun şekilde etiketlemek için [tarayıcıyı](/azure/information-protection/deploy-aip-scanner) kullanın. Bu dosyaları Microsoft 365'daki SharePoint geçirmeyi veya karşıya yüklemeyi planlıyorsanız, dosyaları buluta taşımadan önce etiketlemek için tarayıcıyı kullanın.

  - Duyarlılık etiketlerini kullanmadan önce başka bir etiketleme çözümü kullandıysanız: Bu çözümlerden [etiketleri yeniden kullanmak için PowerShell ve gelişmiş bir ayar](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#migrate-labels-from-secure-islands-and-other-labeling-solutions) kullanın.

- Kullanıcılara hangi duyarlılık etiketlerinin uygulanacağı konusunda eğitim verdikten sonra [el ile](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) etiketlemeyi teşvik edin. Kullanıcıların hangi etiketin uygulanacağını anlayacağından emin olduğunuzda, [ilke ayarları](sensitivity-labels.md#what-label-policies-can-do) olarak varsayılan bir etiket ve zorunlu etiketleme yapılandırmayı göz önünde bulundurun.

Ayrıca, en az bir DLP ilkesi dosyanın içeriğini tarayana kadar konukların yeni eklenen dosyalara erişmesini önlemek için SharePoint'de yeni dosyaları [varsayılan olarak hassas olarak işaretlemeyi](/sharepoint/sensitive-by-default) göz önünde bulundurun.
