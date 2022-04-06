---
title: İçeriğin içeriğine otomatik olarak duyarlılık Microsoft 365
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
description: Duyarlılık etiketi  oluşturduktan sonra, dosyalara ve e-postalara otomatik olarak bir etiket atayabilirsiniz veya kullanıcılardan önerdiğiniz etiketi seçmelerini istenebilirsiniz.
ms.openlocfilehash: 21ee443ba9bab0ac7071377befee5d6e6143a398
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634635"
---
# <a name="apply-a-sensitivity-label-to-content-automatically"></a>İçeriğe otomatik olarak bir hassasiyet etiketi uygulama

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

> [!NOTE]
> Azure Purview'da otomatik olarak duyarlılık etiketi uygulama hakkında bilgi için bkz. [Azure Purview'da etiketleme](/azure/purview/create-sensitivity-label).

Duyarlılık etiketi  oluşturduktan sonra, belirttiğiniz koşullarla eşleşen dosyalara ve e-postalara otomatik olarak bu etiketi atabilirsiniz.

İçeriklere otomatik olarak duyarlılık etiketleri uygulayabilme özelliği önemlidir çünkü:

- Sınıflandırmalardan her biri için kullanıcılarınızı ne zaman kullanılamayacaklarını eğitmek zorunda değilsiniz.

- Tüm içeriği doğru şekilde sınıflandırmak için kullanıcılara güvenmeniz gerek değildir.

- Kullanıcıların artık ilkelerinizi malıdır; onlar da çalışmalarına odaklanabilirsiniz.

İçerik içeriklerine otomatik olarak duyarlılık etiketi uygulamak için iki farklı yöntem Microsoft 365:

- Kullanıcılar belgeleri düzenlerken veya e-postaları düzenlerken (ayrıca yanıtla veya ilet) istemci tarafı etiketleme: Dosyalar ve e-postalar için (Word, Excel, PowerPoint ve diğer **e-postalar dahil)** otomatik etiketleme için yapılandırılmış bir Outlook.

    Bu yöntem, kullanıcılara etiket önerilerini ve otomatik olarak etiket uygulamayı destekler. Ancak her iki durumda da, içeriği doğru etiketlemeye yardımcı olmak için kullanıcı etiketi kabul etmeye veya reddetmeye karar verir. Belge kaydedmeden önce bile etiketin uygulanama süresi nedeniyle, istemci tarafı etiketlemesi belgelerde çok az gecikmeye neden olur. Bununla birlikte, tüm istemci uygulamaları otomatik etiketlemeyi desteklemez. Bu özellik, bazı Office sürümleriyle yerleşik etiketleme ve aynı zamanda Azure [](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps)birleşik Information Protection istemcisi tarafından da destekler.

    Yapılandırma yönergeleri için, [bu sayfada yer alan uygulamaların otomatik Office yapılandırma](#how-to-configure-auto-labeling-for-office-apps) sayfasına bakın.

- **İçerik önceden kaydedildikten (SharePoint veya OneDrive) veya e-postayla (Exchange Online tarafından işlendiğinde** hizmet tarafı etiketleme: Otomatik etiketleme ilkesi kullanın.
    
    Ayrıca, bu yöntem size gönderilen veriler için otomatik etiketleme (SharePoint ve OneDrive'daki belgeler) ve geçişteki veriler (e-posta, posta ile gönderilen veya alınan) olarak Exchange. Örneğin Exchange e-postaları (posta kutuları) içermez.
    
    Bu etiketleme uygulamalar yerine hizmetlere göre uygulandığından, kullanıcıların hangi uygulamalara sahip olduğu ve hangi sürüme sahip olduğu konusunda endişelenmeniz gerek yok. Sonuç olarak bu özellik, kurum genelinde hemen kullanılabilir ve ölçekte etiketlemeye uygundur. Otomatik etiket ilkeleri etiketlemeyi desteklemez, çünkü kullanıcı etiket işlemiyle etkileşimde bulunmakla etkileşimde bulunmakla ilgili bilgi desteklemez. Bunun yerine, yönetici, etiketi gerçekten uygulamadan önce içeriğin doğru etikete sahip olduğundan emin olmak için ilkeleri benzetim olarak çalıştırır.

    Yapılandırma yönergeleri için, Bu sayfada yer alan SharePoint, OneDrive ve Exchange için [otomatik etiket ilkelerini](#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange) yapılandırma sayfasına bakın.
    
    Etiket ve etiketlerin otomatik olarak SharePoint için OneDrive:
    
    - Office word (.docx), PowerPoint (.pptx) ve Excel (.xlsx) için dosyalar de desteklene.
        - Bu dosyalar, otomatik etiket ilkeleri oluşturulmadan önce veya oluşturulduktan sonra otomatik olarak etiketleniyor olabilir. Dosyalar açık bir oturumun parçası ise (dosya açıksa) otomatik olarak etiketz.
        - Şu anda, liste öğelerine yapılan ekler destek desteklemez ve otomatik olarak etiket olmayacaktır.
    - Kiracınıza günde en fazla 25.000 otomatik etiket eklenir.
    - Kiracı başına 100 adede kadar siteyi (kiracı veya kiracı) tek tek belirtilmiş olarak hedef alan (SharePoint veya OneDrive) başına en çok 100 otomatik etiket ilkeleri. Ayrıca tüm siteleri belirtebilirsiniz ve bu yapılandırma en fazla 100 siteden muaftır.
    - Hem benzetim moduna hem de etiketler uygulandığında, otomatik etiketleme ilkeleri sonucunda değiştirilmiş, değiştiren ve tarihe yönelik mevcut değerler değişmez.
    - Etiket şifrelemeyi uygularken, [Hak Yönetimi verici ve Hak Yönetimi](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) sahibi dosyayı en son değiştiren hesaptır. Bu hesap artık Azure Active Directory, bu değerler ayarlanamaya nedeniyle etiket uygulanmaz.

    Belirli bir etiket için otomatik Exchange:
    
    - OFFICE uygulamalarıyla el ile etiketlemeden veya otomatik etiketlemeden farklı olarak, PDF ekleri Office ekleri de otomatik etiketleme ilkesinde belirttiğiniz koşullar için taranır. Eşleşme olduğunda, e-posta eki etiketli ancak etiketli değildir.
        - PDF dosyaları için, etiket şifreleme uygularsa, kiracınız PDF ekleri için [etkinleştirildiğinde bu dosyalar Office 365 İleti Şifrelemesi (OME)](ome.md) kullanılarak [şifrelenir](ome-faq.yml#are-pdf-file-attachments-supported-).
        - Bu Office için Word, PowerPoint ve Excel dosyaları desteklene. Etiket şifreleme uygularsa, bu etiket İleti Şifrelemesi [(OME) Office 365 kullanılarak şifrelenir](ome.md).
    - IRM şifrelemesi Exchange posta akışı kuralları veya veri kaybı önleme (DLP) ilkeleriniz varsa: İçerik bu kurallar veya ilkeler ve otomatik etiket ilkesiyle tanımsızsız olduğunda, etiket uygulanır. Bu etiket şifreleme uygularsa, ilgili posta akış kuralları veya DLP Exchange IRM ayarları yoksayılır. Ancak bu etiket şifreleme uygulamayacaksa, posta akış kuralları veya DLP ilkelerine yönelik IRM ayarları etikete ek olarak uygulanır.
    - IRM şifrelemesi olmayan e-postaların yerini, otomatik etiketleme kullanılarak bir eşleşme olduğunda ise bir şifreleme ayarlarıyla değiştirirsiniz.
    - Gelen e-posta, otomatik etiketleme koşullarınız ile bir eşleşme olduğunda etiketlenmiş olur. Bu etiket şifreleme için [yapılandırılmışsa](encryption-sensitivity-labels.md), gönderen her zaman kuruluşundan geldiğinde bu şifreleme uygulanır. Varsayılan olarak, gönderen kuruluş dışından olduğunda bu şifreleme uygulanmaz, ancak e-posta için ek ayarlar yapılandırarak ve  Hak Yönetimi sahibi belirterek uygulanabilir.
    - Etiket şifrelemeyi uygularken, [Hak Yönetimi veren ve Hak](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) Yönetimi sahibi, gönderen kendi kuruluşundan geldiğinde e-postayı gönderen kişidir. Gönderen, kurum dışında olduğunda, ilkeniz tarafından etiketlenen ve şifrelenen gelen e-posta için bir Hak Yönetimi sahibi belirtebilirsiniz.
    - Etiket dinamik işaretlemeler uygulamak üzere yapılandırılmışsa [, gelen](sensitivity-labels-office-apps.md#dynamic-markings-with-variables) e-posta için bu yapılandırmanın kurum dışındaki kişilerin adlarını görüntülemeye neden olyabilecektir.

## <a name="compare-auto-labeling-for-office-apps-with-auto-labeling-policies"></a>E-posta uygulamalarının otomatik Office ve otomatik etiket ilkelerini karşılaştırma

Tamamlayıcı iki otomatik etiket yönteminin davranışı farklılıklarını tanımlamanıza yardımcı olması için aşağıdaki tabloyu kullanın:

|Özellik veya davranış|Etiket ayarı: Dosyalar ve e-postalar için otomatik etiketleme  |İlke: Otomatik etiketleme|
|:-----|:-----|:-----|
|Uygulama bağımlılığı|Evet ([en düşük sürümler](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps)) |Hayır \* |
|Konuma göre kısıtla|Hayır |Evet |
|Koşullar: Eğitilebilir sınıflayıcılar|Evet |Hayır |
|Koşullar: Paylaşım seçenekleri ve e-posta için ek seçenekler|Hayır |Evet |
|Koşullar: Özel Durumlar|Hayır |Evet (yalnızca e-posta) |
|Öneriler, ilke araç ipucu ve kullanıcı geçersiz kılmaları|Evet |Hayır |
|Benzetim modu|Hayır |Evet |
|Exchange koşulların denetlenir|Hayır | Evet|
|Görsel işaretler uygulama |Evet |Evet (yalnızca e-posta) |
|IRM şifrelemesi etiket olmadan uygulanırken geçersiz kılma|Kullanıcı Dışarı Aktar minimum kullanım hakkına sahipse Evet |Evet (yalnızca e-posta) |
|Gelen e-postayı etiketleme|Hayır |Evet|
|Başka bir kuruluştan gönderilen e-postalar için Hak Yönetimi sahibi atama |Hayır |Evet|
|E-postalar için, aynı veya daha düşük önceliğe sahip mevcut etiketi değiştirin |Hayır |Evet (yapılandırılabilir)|

\* Arka uç Azure bağımlılığı nedeniyle otomatik etiketleme şu anda tüm bölgelerde kullanılamaz. Kiracınız bu işlevselliği destekleyemeyebilir, Otomatik etiketle  ilgili sekme uyumluluk merkezinde görünmez. Daha fazla bilgi için bkz. [Ülkeye göre Azure bağımlılığı kullanılabilirliği](/troubleshoot/azure/general/dependency-availability-by-country).

## <a name="how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label"></a>Birden fazla etiket için birden fazla etiket geçerli olduğunda birden çok koşullar nasıl değerlendirilir?

Etiketler, ilkede belirttiğiniz konumlarına göre değerlendirme için sıralandı: İlk konum bilgisinde en altta yer alan etiket (en küçük duyarlı) ve en son konum konumundaki etiket en yüksek konuma (en duyarlı) sahip. Öncelik hakkında daha fazla bilgi için bkz. [Etiket önceliği (sipariş konuları)](sensitivity-labels.md#label-priority-order-matters).

## <a name="dont-configure-a-parent-label-to-be-applied-automatically-or-recommended"></a>Üst etiketi otomatik olarak uygulanacak veya önerilen bir etiket olacak şekilde yapılandırma

İçeriğine üst etiket (alt etiketleri olan bir etiket) uygulayamayabileceksiniz. Office uygulamalarına otomatik olarak uygulanacak veya önerilen bir üst etiket yapılandırmama veya bir otomatik etiket ilkesi için üst etiket seçmediğinizden emin olun. Bunu yaparsanız, üst etiket içeriğe uygulanmaz.

Alt etiketle otomatik etiketleme kullanmak için, hem üst etiketi hem de alt etiketi yayımlayın.

Üst etiketler ve alt etiketler hakkında daha fazla bilgi için bkz. [Alt etiketler (gruplama etiketleri)](sensitivity-labels.md#sublabels-grouping-labels).

## <a name="will-an-existing-label-be-overridden"></a>Mevcut bir etiket geçersiz kılınacak mı?

> [!NOTE]
> E-posta otomatik etiketle ilgili ilkeler için eklenen yeni bir ayar, eşleşen bir duyarlılık etiketinin her zaman var olan bir etiketi geçersiz kmayacaklarını belirtmenize izin verir.

Otomatik etiketlemenin varolan bir etiketi geçersiz kıp geçersiz kmayacaklarını varsayılan davranış:

- İçerik el ile etiketlenmiş olduğunda, bu etiket otomatik etiketle değiştirilir.

- Otomatik etiketleme, otomatik olarak [uygulanan daha düşük öncelikli duyarlılık](sensitivity-labels.md#label-priority-order-matters) etiketinin yerini aacaktır, ancak daha yüksek öncelikli bir etiket yerine daha yüksek öncelikli bir etiketle değiştirilir.
    
    > [!TIP]
    > Örneğin, uyumluluk merkezi'nde listenin en üstünde yer alan duyarlılık etiketi Genel olarak 0 sipariş numarası (öncelik) ile ve listenin en altındaki duyarlılık etiketi de sipariş numarasıyla (4 öncelik) Yüksek Gizli olarak adlandırılmıştır. Çok **Gizli etiketi** Ortak etiketi **geçersiz k** ancak bunun başka bir yolu değildir.

Yalnızca e-posta otomatik etiketleme ilkeleri için, nasıl uygulandığına bakılmaksızın, var olan bir duyarlılık etiketini her zaman geçersiz kacak bir ayar seçin.

|Mevcut etiket |Etiket ayarıyla geçersiz kılma: Dosyalar ve e-postalar için otomatik etiketleme  |İlkeyle geçersiz kılma: Otomatik etiketleme|
|:-----|:-----|:-----|
|El ile uygulanır, herhangi bir öncelik|Word, Excel, PowerPoint: Hayır <br /><br> Outlook: Hayır  |SharePoint ve OneDrive: Hayır <br /><br> Exchange: Varsayılan olarak hayır, ancak yapılandırılabilir |
|İlkeden otomatik olarak uygulanan veya varsayılan etiket, düşük öncelikli |Word, Excel, PowerPoint: Evet <br /><br> Outlook: Evet | SharePoint ve OneDrive: Evet <br /><br> Exchange: Evet |
|İlkeden otomatik olarak uygulanan veya varsayılan etiket, yüksek öncelikli |Word, Excel, PowerPoint: Hayır <br /><br> Outlook: Hayır |SharePoint ve OneDrive: Hayır <br /><br> Exchange: Varsayılan olarak hayır, ancak yapılandırılabilir |

E-posta otomatik etiketleme ilkeleri için yapılandırılabilir ayar, E-posta **için ek ayarlar sayfasındadır** . Bu sayfa, duyarlılık konumunu içeren bir otomatik etiket ilkesi için duyarlılık Exchange görüntülenir.

## <a name="how-to-configure-auto-labeling-for-office-apps"></a>Office uygulamaları için otomatik Office yapılandırma

Bir uygulamanın yerleşik etiketlemesi Office için, Office uygulamalarda otomatik etiketleme için gereken [](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps) en düşük Office kontrol edin.

Azure Information Protection birleşik etiketleme istemcisi yalnızca yerleşik ve özel hassas bilgi türlerinde otomatik etiketlemeyi destekler ve Tam Veri Eşleşmesi (EDM) veya adlandırılmış varlıklar kullanan, eğitilebilir sınıflayıcıları veya hassas bilgi türlerini desteklemez.

Bir duyarlılık Office için [otomatik etiket ayarları](create-sensitivity-labels.md) kullanılabilir. Etiketin **kapsamı için &-posta** dosyalarının seçili olduğundan emin olun:

![Dosyalar ve e-postalar için duyarlılık etiketi kapsamı seçenekleri.](../media/filesandemails-scope-options-sensitivity-label.png)

Yapılandırmada ilerlerken, hassas bilgi türleri veya eğitilebilir sınıflayıcılar listesinden seçimnizi tek tek dosyalar ve **e-postalar** için otomatik etiketleme sayfasını görüyorsunuz:

![Office uygulamalarda otomatik etiketleme için Office koşulları.](../media/sensitivity-labels-conditions.png)

Bu duyarlılık etiketi otomatik olarak uygulandığında, kullanıcı kendisinde bir bildirim Office uygulaması. Örneğin:

![Bir belgeye otomatik olarak bir etiket uygulandığını haber verilmesini sağlar.](../media/sensitivity-labels-msg-doc-was-auto-labeled.PNG)

### <a name="configuring-sensitive-info-types-for-a-label"></a>Bir etiket için hassas bilgi türlerini yapılandırma

Hassas bilgi türleri **seçeneğini gördüğünüzde** , veri kaybı önleme (DLP) ilkesi oluşturmayla aynı hassas bilgi türleri listesini görüyorsunuz. Dolayısıyla, örneğin, müşterilerin kredi kartı numaraları, sosyal güvenlik numaraları veya pasaport numaraları gibi kişisel bilgilerini içeren her türlü içeriğe otomatik olarak Çok Gizli etiket uygulayabilirsiniz:

![Office uygulamalarda otomatik etiketleme için Office türleri.](../media/sensitivity-labels-sensitive-info-types.png)

Daha sonra DLP ilkelerini yapılandırmış olacağınız gibi, örnek sayısını ve doğruluğunu değiştirerek koşul bilginizi geliştirebilirsiniz. Örneğin:

![Doğruluk ve örnek sayısı eşleşme seçenekleri.](../media/sit-confidence-level.png)

Bu yapılandırma seçenekleri hakkında daha fazla bilgi edinmek için DLP belgelerine bakın: [Kuralların eşleşmelerini kolaylaştıracak veya zorlaştıracak şekilde ayarlama](data-loss-prevention-policies.md#tuning-rules-to-make-them-easier-or-harder-to-match).

> [!IMPORTANT]
> Hassas bilgi türlerinin en fazla benzersiz örnek sayısı parametresini tanımlamanın iki farklı yolu vardır. Daha fazla bilgi edinmek için bkz [. SIT için örnek sayısı desteklenen değerler](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit).

Ayrıca, DLP ilke yapılandırmasına benzer şekilde, bir koşulun tüm hassas bilgi türlerini mi yoksa yalnızca birini mi algılaması gerektiğini de seçebilirsiniz. Ayrıca, koşullarınızı daha esnek veya karmaşık bir hale getirirken, gruplar ekleyebilir [ve gruplar arasında mantıksal işleçler kullanabilirsiniz](data-loss-prevention-policies.md).

> [!NOTE]
> Özel duyarlı bilgi türlerine dayalı otomatik etiketleme yalnızca OneDrive ve SharePoint'de yeni oluşturulan veya değiştirilen içerik için geçerlidir; var olan içerik için geçerli değildir. Bu sınırlama otomatik etiket ilkeler için de geçerlidir.

#### <a name="custom-sensitive-information-types-with-exact-data-match"></a>Tam Veri Eşleşmesi olan özel hassas bilgi türleri

Özel hassas bilgi türleri için hassas bilgi türlerine göre [tam veri eşleşmesi tabanlı bilgi türlerini kullanmak üzere bir](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) duyarlılık etiketi yapılandırabilirsiniz. Bununla birlikte, şu anda EDM kullanmayan en az bir hassas bilgi türü de belirtebilirsiniz. Örneğin, Kredi kartı numarası gibi yerleşik hassas bilgi **türlerinden biri olabilir**.

Hassas bilgi türü koşullarınız için yalnızca EDM olan bir duyarlılık etiketi yapılandırıyorsanız, etiket için otomatik etiketleme ayarı otomatik olarak kapalıdır.

### <a name="configuring-trainable-classifiers-for-a-label"></a>Bir etiket için eğitilebilir sınıflayıcıları yapılandırma

Windows için Microsoft 365 Uygulamaları sürüm 2106 veya daha düşük ya da Mac için Microsoft 365 Uygulamaları sürüm 16.50 veya daha düşük sürümlerde bu seçeneği kullanırsanız, kiracınıza otomatik etiketleme için yapılandırılmış en az bir duyarlılık etiketi ve hassas bilgi türleri seçeneği daha yayımlamış olduğundan emin [olun.](#configuring-sensitive-info-types-for-a-label) Bu platformlarda daha sonraki sürümleri kullanıyorken bu gereksinim gerekmez.

Eğitilebilir **sınıflandırıcılar seçeneğini belirtin** ; önceden eğitilebilir veya özel eğitime uygun sınıflayıcılardan birini veya daha fazlasını seçin:

![Eğitilebilir sınıflayıcılar ve duyarlılık etiketleri için seçenekler.](../media/sensitivity-labels-classifers.png)

> [!CAUTION]
> Rahatsız Edici Dil ön eğitimcisini, yüksek sayıda yanlış pozitif sonuç üretmiş olduğu için kullanımdandan alıkıyoruz. Bu sınıflandırıcıyı kullanma; şu anda kullanıyorsanız iş işlemlerinizi devre dışı taşımanızı ve bunun yerine Hedefli **Taciz, Küfür** ve **Tehdit** ön eğitimcilerini kullanmanızı öneririz.

Bu sınıflandırıcılar hakkında daha fazla bilgi için bkz[. Eğitilebilir sınıflandırıcılar hakkında bilgi.](classifier-learn-about.md)

### <a name="recommend-that-the-user-applies-a-sensitivity-label"></a>Kullanıcının bir duyarlılık etiketi uygulamalarını önerin

Tercih ederseniz, kullanıcılarınıza etiketi uygulamalarını önerebilirsiniz. Bu seçenekle, kullanıcılarınız sınıflandırmayı ve ilişkili korumayı kabul edilebilir ya da etiketin içeriğine uygun değilse öneriyi reddedebilirsiniz.

![Kullanıcılara duyarlılık etiketi öneri seçeneği.](../media/Sensitivity-labels-Recommended-label-option.png)

Burada, bir etiketi önerilen eylem olarak uygulamak için özel bir ilke ipucuyla bir koşul yapılandırıldığında Azure Information Protection birleşik etiketleme istemcisinde yer alan bir istem örneği ve göstermektedir. İlke ipucunda görüntülenecek metni seçebilirsiniz.

![Önerilen bir etiketi uygulama istemi.](../media/Sensitivity-label-prompt-for-required-label.png)

### <a name="when-automatic-or-recommended-labels-are-applied"></a>Otomatik veya önerilen etiketler uygulandığında

Office uygulamalarına otomatik ve önerilen etiketlemenin uygulanması, Office'de yerleşik olarak yer alan etiketlemeyi mi yoksa Azure Information Protection birleşik etiketleme istemcisini mi kullandığınıza bağlıdır. Bununla birlikte, her iki durumda da:

- Daha önce el ile veya daha önce daha önce daha yüksek bir duyarlılıkla etiketlenmiş belgeler ve e-postalar için otomatik etiketlemeyi kullanasınız. Bir belgeye veya e-postaya (tek bir bekletme etiketine ek olarak) yalnızca tek bir duyarlılık etiketi uygulayabileceksiniz.

- Daha önce daha yüksek bir duyarlılıkla etiketlenmiş belgeler veya e-postalar için önerilen etiketlemeyi kullanasınız. İçerik zaten daha yüksek bir duyarlılıkla etiketlenmiş olduğunda, kullanıcı öneriyi ve ilke ipucunda istemi görmez.

Yerleşik etiketlemeye özgü:

- Diğer tüm Office uygulamaları otomatik (ve önerilen) etiketlemeyi desteklemez. Daha fazla bilgi için bkz [. Uygulamalarda duyarlılık etiketi özellikleri desteği](sensitivity-labels-office-apps.md#support-for-sensitivity-label-capabilities-in-apps).

- Word'in masaüstü sürümlerinde önerilen etiketler için, öneriyi tetikleyen hassas içerik bayrakla işaretlenir; böylelikle kullanıcılar önerilen duyarlılık etiketini uygulamak yerine hassas içeriği gözden geçirebilirsiniz ve kaldırabilirler.

- Bu etiketlerin Office uygulamalarına nasıl uygulandığı, örnek ekran görüntüleri ve ne kadar hassas bilgilerin algılandığından ilgili ayrıntılar için bkz. Office'te dosyalarınıza ve e-postanıza duyarlılık etiketlerinin otomatik olarak [uygulanması veya önerin](https://support.microsoft.com/office/automatically-apply-or-recommend-sensitivity-labels-to-your-files-and-emails-in-office-622e0d9c-f38c-470a-bcdb-9e90b24d71a1).

Azure Information Protection birleşik etiketleme istemcisine özgü:

- Otomatik ve önerilen etiketleme, belgeyi kaydederek Word, Excel ve PowerPoint e-posta gönderirken Outlook için geçerlidir.

- Önerilen Outlook için, önce gelişmiş bir ilke ayarı [yapılandırmalısiniz](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#enable-recommended-classification-in-outlook).

- Belgelerde ve e-postalarda gövde metninde, üst bilgi ve alt bilgilerde hassas bilgiler algılanır, ancak konu satırı veya e-posta ekleri içinde algılanmaz.

## <a name="how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange"></a>SharePoint, ONEDRIVE ve Exchange için otomatik etiketleme ilkeleri Exchange

Otomatik etiket ilkelerini yapılandırmadan önce önkoşulları farkında olun.

### <a name="prerequisites-for-auto-labeling-policies"></a>Otomatik etiket ilkeleri için önkoşullar

- Benzetim modu:
  - Denetim Microsoft 365 açık olması gerekir. Denetimi açmanız gerekirse veya denetimin zaten aç olup olmadığı konusunda emin değilsanız, bkz. [Denetim günlüğü aramalarını açma veya kapatma](turn-audit-log-search-on-or-off.md).
  - Dosya veya e-posta içeriğini kaynak görünümde görüntülemek için, İçerik Gezgini İçerik  Görüntüleyicisi rol grubunda bulunan Veri Sınıflandırma İçerik Görüntüleyicisi rolüne ya da **Information Protection ve Information Protection** **Süreler rol gruplarına** (şu anda önizlemede) sahip olmak gerekir. Gerekli rol olmadan, Eşleşmeli Öğeler sekmesinden bir öğe seçerek önizleme **bölmesini görmeyebilirsiniz** . Genel yöneticiler varsayılan olarak bu role sahip değildir.

- Dosyaları tek tek SharePoint otomatik olarak OneDrive:
  - SharePoint [ve OneDrive'de Office dosyaları için duyarlılık SharePoint etkinleştirmişsiniz](sensitivity-labels-sharepoint-onedrive-files.md).
  - Otomatik etiket ilkesi şu anda çalışıyorken, dosya başka bir işlem veya kullanıcı tarafından açık değil. Düzenleme için kullanıma alınmış bir dosya bu kategoriye girer.

- Yerleşik duyarlılık türleri [yerine özel hassas](sensitive-information-type-learn-about.md) bilgi türlerini kullanmayı planlıyorsanız:
  - Özel duyarlılık bilgi türleri yalnızca özel duyarlılık bilgi türleri oluşturulduktan sonra SharePoint veya OneDrive eklenen veya değiştirilen içeriğe uygulanır.
  - Yeni özel hassas bilgi türlerini test etmek için, otomatik etiketleme ilkenizi oluşturmadan önce bunları oluşturun ve ardından test etmek üzere örnek veriler de olan yeni belgeler oluşturun.

- Otomatik etiket ilkeleriniz için [seçerek yayımladığı](create-sensitivity-labels.md) ve yayımladığı bir veya birden çok duyarlılık etiketi (en az bir kullanıcıya). Bu etiketler için:
  - Girişte anlatıldı gibi söz konusu etiket ayarının Office uygulamaları etiket ayarının açık veya kapalı olması fark etmez, çünkü söz konusu etiket ayarı, otomatik etiket ilkelerini tamamlar.
  - Otomatik etiketleme için kullanmak istediğiniz etiketler görsel işaretler (üst bilgiler, alt bilgiler, filigranlar) kullanmak üzere yapılandırılmışsa, bunların belgelere uygulanmamış olduğunu unutmayın.
  - Etiketler şifreleme [uygulamazsa](encryption-sensitivity-labels.md):
    - Otomatik etiket ilkesi posta veya posta SharePoint OneDrive olduğunda, Şimdi izin ata ayarı için etiketin **yapılandırılması** gerekir.
    - Otomatik etiket ilkesi yalnızca E-posta için Exchange olduğunda, etiket Şimdi izin ata veya Kullanıcıların izin atamasına izin **ver (İ** iletme veya devre dışı bırak seçenekleri için) Encrypt-Only ya da yapılandırabilirsiniz.

### <a name="learn-about-simulation-mode"></a>Benzetim modu hakkında bilgi

Benzetim modu, otomatik etiketleme ilkelerine ve iş akışında yer alan deneyime özgü bir moddur. İlkeniz en az bir benzetim çalıştırana kadar belgeleri ve e-postaları otomatik olarak etiketleyemez.

Benzetim modu 1.000.000'e kadar eşleşmeli dosya destekler. Otomatik etiket ilkesinden bu sayıdan fazla dosya eşlenmişse, etiketleri uygulamak için ilkeyi açabilirsiniz. Bu durumda, daha az dosyanın eşleşmesi için otomatik etiketleme politikasını yeniden yapılandırmanız ve benzetimi yeniden çalıştırmanız gerekir. Bu 1.000.000 eşleşmeli dosya sayısı yalnızca benzetim moduna uygulanır, duyarlılık etiketleri uygulamak için önceden açık olan otomatik etiket ilkesi için geçerli değildir.

Otomatik etiketleme ilkesi için iş akışı:

1. Otomatik etiketleme ilkesi oluşturma ve yapılandırma.

2. Benzetim modunda ilkeyi çalıştırın; bu 12 saat sürebilir. Tamamlanan benzetim, etkinlik uyarılarını alacak şekilde yapılandırılan kullanıcıya gönderilen bir e-posta [bildirimini tetikler](alert-policies.md).

3. Sonuçları gözden geçirme ve gerekirse ilkenizi geliştirme. Örneğin, hatalı pozitif sonuç sayısını azaltmak için ilke kurallarını düzenlemeniz veya bazı siteleri kaldırarak eşleşmeli dosyaların sayısının 1.000.000'i aşmasını azaltmanız gerekiyor olabilir. Benzetim modunu yeniden çalıştırma ve yeniden tamamlamayı bekleyin.

4. 3. adımı gereken şekilde yinelayın.

5. Üretimde dağıtım.

Sanal dağıtım, PowerShell için WhatIf parametresi gibi çalışır. Otomatik etiket ilkesi tanımlandığı kuralları kullanarak seçili etiketinizi uygulama sonuçları olduğunu görüyorsunuz. Daha sonra gerekirse doğruluğu için kurallarınızı geliştirebilir ve benzetimi yeniden çalıştırebilirsiniz. Bununla birlikte, Exchange için otomatik etiketleme posta kutularında depolanan e-postalar yerine gönderilen ve alınan e-postalar için geçerli olduğundan, aynı e-posta iletilerini göndererek alamadıkça benzetimle ilgili sonuçların tutarlı olmasını beklemezsiniz.

Benzetim modu ayrıca dağıtımdan önce otomatik etiketleme ilkenizin kapsamını aşamalı olarak artırmanıza olanak sağlar. Örneğin, tek bir konumla, örneğin tek bir SharePoint kitaplığıyla başlayabilirsiniz. Daha sonra, yinelene değişikliklerle, kapsamı birden çok site için artırarak, sonra da site kapsamını başka bir OneDrive.

Son olarak, benzetim modunu, benzetim modu olmadan ne zaman çalıştıracaklarını planlamanıza ve zamanlamanıza yardımcı olmak üzere otomatik etiketleme ilkenizi çalıştırmak için gereken süre hakkında yaklaşık olarak bilgi sağlamak üzere kullanabilirsiniz.

### <a name="creating-an-auto-labeling-policy"></a>Otomatik etiketleme ilkesi oluşturma

1. İçerik <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a> duyarlılık etiketlerine gidin:

    - **Çözümler** >  **Bilgi koruması**

    Bu seçeneği hemen görmüyorsanız önce Hepsini **göster'i seçin**.

2. Otomatik **etiket sekmesini** seçin:

    ![Otomatik etiket sekmesi.](../media/auto-labeling-tab.png)

    > [!NOTE]
    > Otomatik etiketleme sekmesini görmüyorsanız, arka  uç Azure bağımlılığı nedeniyle bu işlevsellik şu anda bölgenize uygun değildir. Daha fazla bilgi için bkz. [Ülkeye göre Azure bağımlılığı kullanılabilirliği](/troubleshoot/azure/general/dependency-availability-by-country).

3. **+ Otomatik etiketleme ilkesi oluştur'a seçin**. Bu, Yeni ilke yapılandırmasını başlatır:

    ![Otomatik etiketleme için yeni ilke yapılandırması.](../media/auto-labeling-wizard.png)

4. Bu **etiketin uygulanmak istediğiniz bilgileri seçin** sayfası için: Finansal veya Gizlilik gibi **şablonlardan** birini **seçin**. Seçenekleri göster açılan listesinden **aramanızı daraltabilirsiniz** . Şablonlar **gereksinimlerinizi karşılamıyorsa** Özel ilke'yi de seçin. **İleri**'yi seçin.

5. Otomatik etiketleme ilkenizi adla **: Otomatik** olarak uygulanan etiketi, konumları ve koşulları tanımlamak için benzersiz bir ad ve isteğe bağlı olarak bir açıklama girin.

6. Etiketin **uygulanıyor olduğu** konumları seçin sayfası için: Konum, Konum, Konum ve Konum Exchange SharePoint'OneDrive. Seçtiğiniz konumlarda varsayılan olarak Hepsi dahil edilen seçeneğini kullanmak istemiyorsanız, dahil edilecek belirli örnekleri seçmek için bağlantıyı seçin veya hariç tutulacak belirli örnekleri seçmek için bağlantıyı seçin. Sonra Da **Sonraki'yi seçin**.

    ![Otomatik etiketleme yapılandırması için konumlar sayfasını seçin.](../media/locations-auto-labeling-wizard.png)
    
    Varsayılan ayarları, Dahil Edilen veya Dışarıda **Bırakıldı'ya** **göre değiştirirsiniz**:
    
    - Adres **Exchange** ilke, belirtilen alıcıların gönderen adresine göre uygulanır. Çoğu zaman, Hariç Yok ayarında bulunan Tüm **varsayılanı** **tutmanız** gerekir. Bu yapılandırma, kullanıcıların bir alt kümesini test ediyor bile olsa uygundur. Buradaki kullanıcı alt kümenizi belirtmek yerine, bir sonraki adımda gelişmiş kuralları kullanarak organizasyonda alıcıları dahil etmek veya dışarıda tutmak için koşulları yapılandırabilirsiniz. Aksi takdirde, varsayılan ayarları burada değiştirirsiniz:
        -  Varsayılan olarak Tüm dahil'i **değiştirir** ve bunun yerine belirli kullanıcıları veya grupları seçerseniz, kuruluş dışından gönderilen e-posta ilkeden muaf olur. 
        -  Varsayılan olarak **All included (** Dahil edilenler) varsayılanı geçerli olup hariç tutulacak kullanıcıları veya grupları belirtirseniz, bu dışarıda bırakılan kullanıcıların göndermesi gereken e-posta ilkeden muaf olur, ancak almayacakları e-postadan muaf olmaz.
    
    - Daha OneDrive için bkz. Dahil veya dışarıda bırakılacak tek [OneDrive](/onedrive/list-onedrive-urls) hesapları belirtmenize yardımcı olması için, OneDrive kullanıcı url'lerinin listesini elde edin.

7. Ortak veya **gelişmiş kuralları ayarlama** sayfası için: Tüm seçtiğiniz konumlarda etiketilecek  içeriği tanımlayan kurallar tanımlamak için Ortak kurallar'ın varsayılanını kullanın. Konum başına farklı kurallara, örneğin konum başına farklı kurallara ihtiyacınız varsa, Exchange **kurallar'ı seçin**. Sonra Da **Sonraki'yi seçin**.

    Kurallar hassas bilgi türlerini ve paylaşım seçeneklerini içeren koşulları kullanır:
    - Hassas bilgi türleri için, hem yerleşik hem de özel hassas bilgi türlerini seçin.
    - Paylaşılan seçenekler için yalnızca kuruluşum içindeki **veya kuruluşum dışındaki** kişiler **için tercih yapabilirsiniz**.

    Konumunuz Seçili **Exchange** kuralları **seçtiysanız**, seçerek seçerek başka koşullar da ebilirsiniz:
    - Gönderen IP adresi:
    - Alıcı etki alanı:
    - Alıcı
    - Ekin dosya uzantısı
    - Ek parola korumalıdır
    - E-posta eklerinin içeriği taranamadı
    - Herhangi bir e-posta ekin içeriğinin tarama işlemi tamamlanmadı
    - Üst bilgi eşleşme düzenleri
    - Konu eşleşmeleri desenlerini
    - Alıcı adresi sözcükler içeriyor
    - Alıcı adresi desenlere eşler
    - Gönderen adresi desenlere eşler
    - Gönderen etki alanı:
    - Alıcı,
    - Gönderen:

    Bu koşulların her biri için özel durumlar belirtsiniz.

8. Önceki seçimlerinize bağlı olarak, koşulları ve özel durumları kullanarak yeni kurallar oluşturma fırsatınız olacak.

    Hassas bilgi türlerinin yapılandırma seçenekleri, belirli uygulamaların otomatik etiketlerini seçmek için Office aynıdır. Daha fazla bilgi için bkz. [Etiket için hassas bilgi türlerini yapılandırma](#configuring-sensitive-info-types-for-a-label).

    Gereken tüm kuralları tanımlandıktan ve bunların durumunun açık olduğunu onaylarken, otomatik uygulanacak etiketi seçmeye geç için Sonraki'yi seçin.

9. Otomatik **olarak uygulanacak** etiketi seçin sayfası için: **+** Etiket seç'i seçin, Duyarlılık etiketi seçin bölmesinden bir etiket  seçin ve sonra da Sonraki'yi **seçin**.

10. İlkeniz posta konumunu Exchange: E-posta için ek ayarlar sayfasında **isteğe bağlı yapılandırmalar** belirtin:
    
    - **Aynı veya daha düşük önceliğe** sahip mevcut etiketleri otomatik olarak değiştir: Hem gelen hem de giden e-postalarda uygulanabilir, bu ayarı seçerek eşleşen bir duyarlılık etiketinin her zaman uygulanır. Bu ayarı seçmazsanız, daha yüksek önceliğe sahip veya el ile etiketlenmiş mevcut duyarlılık etiketine sahip e-postalara eşleşen bir duyarlılık etiketi uygulanmaz[](sensitivity-labels.md#label-priority-order-matters).
    
    - Şifrelemeyi, kurum dışından alınan e-postalara **uygula: Bu** seçeneği tercih ettiyseniz, [](/azure/information-protection/configure-usage-rights#rights-management-issuer-and-rights-management-owner) kurum dışından gönderilen e-postalar ve şifreleme içeren ilke etiketleriniz için, [](/azure/information-protection/configure-usage-rights#usage-rights-and-descriptions) kuruluş dışındaki yetkili bir kişinin Tam Denetim kullanım haklarına sahip olduğundan emin olmak için, bir Hak Yönetimi sahibi atamanız gerekir. Daha sonra şifrelemeyi kaldırmak veya organizasyonu kullanan kullanıcılara farklı kullanım hakları atamak için bu rol gerekli olabilir.
        
        Hak **Yönetimi sahibi atama için**, kuruluşa ait bir e-posta adresiyle tek bir kullanıcı belirtin. Bir posta kişisi, paylaşılan posta kutusu veya herhangi bir grup türü belirtmeyebilirsiniz, çünkü bunlar bu rolde desteklenmiyor.

10. **İlkeyi** şimdi veya daha sonraki bir sayfada test etmek istediğinize karar verin: Otomatik  etiketleme politikasını benzetim modunda çalıştırmaya hazırsanız benzetim modunda ilkeyi çalıştır'ı seçin. Aksi takdirde **İlkeyi kapalı bırak'ı seçin**. **Sonraki'yi seçin**:

    ![Yapılandırılmış otomatik etiket ilkesi testini kullanın.](../media/simulation-mode-auto-labeling-wizard.png)

11. Özet **sayfası** için: Otomatik etiketleme ilkenizin yapılandırmasını gözden geçirerek gerekli değişiklikleri yapın ve yapılandırmayı tamamlayın.

Bilgi  **korumasıAuto**  >  etiketleme sayfasında, benzetim modunda çalıştırmayı seçip seçmemenize bağlı olarak, benzetim bölümünde otomatik etiketleme ilkenizi görebilirsiniz. Yapılandırma ve durum ayrıntılarını görmek için ilkenizi seçin (örneğin, İlke **benzetimi hala çalışıyor**). Benzetim modundaki ilkeler için, **Hangi e-posta** veya belgelerin belirttiğiniz kurallarla eş olduğunu görmek için Eşlene öğeler sekmesini seçin.

İlkenizi doğrudan bu arabirimden değiştirebilirsiniz:

- Kapalı bölümündeki bir ilke **için** İlkeyi düzenle **düğmesini** seçin.

- Benzetim bölümündeki **ilke** için, sayfanın **üst kısmında yer alan** İlkeyi düzenle seçeneğini iki sekmeden birini seçin:

    ![Otomatik etiketleme ilkesi seçeneğini düzenleyin.](../media/auto-labeling-edit.png)

    Benzetim olmadan ilkeyi çalıştırmaya hazırsanız, **İlkeyi aç seçeneğini** belirleyin.

Otomatik etiketleme ilkeleri, silinene kadar sürekli olarak çalıştırın. Örneğin, yeni ve değiştirilmiş dosyalar geçerli ilke ayarlarına dahil edilir.

### <a name="monitoring-your-auto-labeling-policy"></a>Otomatik etiketleme ilkenizi izleme

Otomatik etiketleme ilkeniz açık olduktan sonra, seçtiğiniz dosya ve klasörlerin etiket ilerleme SharePoint OneDrive görüntüebilirsiniz. E-postalar otomatik olarak gönderildikçe etiketlenirler ve bu e-postalar etiket ilerleme durumuna dahil değildir.

Etiketleme ilerleme durumu, ilkeyle etiketlanacak dosyaları, son yedi gün içinde etiketlenmiş dosyaları ve etiketlenmiş toplam dosyaları içerir. Günde 25.000 dosya etiket en fazla olduğundan, bu bilgiler ilkeniz için geçerli etiketleme ilerleme durumu ve yine de etiketlenmiş olacak dosyaların sayısıyla ilgili görünürlük sağlar.

İlkenizi ilk kez etkinleştirirken, en son veriler alınana kadar dosyaların etiketli olması için başlangıçta 0 değerinin olduğunu görüyorsunuz. Bu ilerleme durumu bilgileri her 48 saatte bir  dolar, böylece her gün hakkında en güncel verileri görmeyi beklersiniz. Otomatik etiketleme ilkesi seçince, bir çıkış bölmesinde ilke hakkında daha fazla ayrıntı görebilirsiniz; bu bölmede en çok 10 sitenin etiket ilerleme durumu da yer almaktadır. Bu çıkış bölmesindeki bilgiler, Otomatik etiket ana sayfasında görüntülenen toplanan ilke **bilgilerinden daha güncel** olabilir.

Ayrıca, uygun izinlere sahipken içerik gezginini kullanarak otomatik etiketleme [ilkenizin](data-classification-content-explorer.md) sonuçlarını [daabilirsiniz](data-classification-content-explorer.md#permissions):

- **İçerik Gezgini Liste Görüntüleyicisi** rol grubu bir dosyanın etiketini görmenizi sağlar, ancak dosyanın içeriğini görmenizi engeller.
- **İçerik Gezgini İçerik Görüntüleyicisi** rol **grubu, Information Protection** **ve Information Protection** Biraları rol grupları (şu anda önizlemede olan) dosyanın içeriğini görmenizi sağlar.

> [!TIP]
> Hassas bilgilerle birlikte belgeleri olan ancak etiketsiz konumları tanımlamak için içerik gezginini de kullanabilirsiniz. Bu bilgileri kullanarak, bu konumları otomatik etiketleme ilkenize eklemeyi ve tanımlanan hassas bilgi türlerini kurallar olarak eklemeyi düşünebilirsiniz.

### <a name="use-powershell-for-auto-labeling-policies"></a>Otomatik etiket ilkeleri için PowerShell kullanma

Otomatik etiketleme ilkeleri [oluşturmak & için PowerShell](/powershell/exchange/scc-powershell) Güvenlik ve Uyumluluk Merkezi PowerShell'i kullanabilirsiniz. Başka bir ifadeyle, otomatik etiketleme ilkelerinizin oluşturulması ve bakımı tamamıyla komut dosyası olarak  yazabilirsiniz. Bu, aynı zamanda grup ve konumlar için birden çok URL OneDrive daha verimli bir SharePoint sağlar.

PowerShell'de komutları çalıştırmadan önce, Güvenlik ve [Uyumluluk Merkezi PowerShell& bağlanın](/powershell/exchange/connect-to-scc-powershell).

Yeni bir otomatik etiketleme ilkesi oluşturmak için:

```powershell
New-AutoSensitivityLabelPolicy -Name <AutoLabelingPolicyName> -SharePointLocation "<SharePointSiteLocation>" -ApplySensitivityLabel <Label> -Mode TestWithoutNotifications
```

Bu komut, belirttiğiniz bir site için SharePoint etiketleme ilkesi oluşturur. Daha fazla OneDrive için bunun yerine *OneDriveLocation* parametresini kullanın.

Var olan otomatik etiketleme ilkesine daha fazla site eklemek için:

```powershell
$spoLocations = @("<SharePointSiteLocation1>","<SharePointSiteLocation2>")
Set-AutoSensitivityLabelPolicy -Identity <AutoLabelingPolicyName> -AddSharePointLocation $spoLocations -ApplySensitivityLabel <Label> -Mode TestWithoutNotifications
```

Bu komut, değişkende yeni SharePoint ve ardından var olan otomatik etiket ilkesine eklenen YENI URL'leri belirtir. Bunun OneDrive konum eklemek için *AddOneDriveLocation* parametresini Farklı bir değişkenle, örneğin *$OneDriveLocations.*

Yeni bir otomatik etiketleme ilkesi kuralı oluşturmak için:

```powershell
New-AutoSensitivityLabelRule -Policy <AutoLabelingPolicyName> -Name <AutoLabelingRuleName> -ContentContainsSensitiveInformation @{"name"= "a44669fe-0d48-453d-a9b1-2cc83f2cba77"; "mincount" = "2"} -Workload SharePoint
```

Var olan bir otomatik etiketleme ilkesi için bu komut, A44669fe-0d48-453d-a9b1-2cc83f2cba77 varlık kimliğine sahip olan ABD sosyal güvenlik numarasının **(SSN)** hassas bilgi türünü algılayan yeni bir ilke kuralı oluşturur. Diğer hassas bilgi türlerinin varlık kimliklerini bulmak için, Hassas bilgi türü varlık [tanımları'ne bakın](sensitive-information-type-entity-definitions.md).

Otomatik etiket ilkelerini destekleyen PowerShell cmdlet'leri, bunların kullanılabilir parametreleri ve bazı örnekleri hakkında daha fazla bilgi için, aşağıdaki cmdlet yardımı bakın:

- [Get-AutoSensitivityLabelPolicy](/powershell/module/exchange/get-autosensitivitylabelpolicy)
- [New-AutoSensitivityLabelPolicy](/powershell/module/exchange/new-autosensitivitylabelpolicy)
- [New-AutoSensitivityLabelRule](/powershell/module/exchange/new-autosensitivitylabelrule)
- [Remove-AutoSensitivityLabelPolicy](/powershell/module/exchange/remove-autosensitivitylabelpolicy)
- [Remove-AutoSensitivityLabelRule](/powershell/module/exchange/remove-autosensitivitylabelrule)
- [Set-AutoSensitivityLabelPolicy](/powershell/module/exchange/set-autosensitivitylabelpolicy)
- [Set-AutoSensitivityLabelRule](/powershell/module/exchange/set-autosensitivitylabelrule)

## <a name="tips-to-increase-labeling-reach"></a>İpuçları ulaşmak için etiketi artırma

Otomatik etiketleme, sahip olduğu Office dosyalarını sınıflandırmanın, etiketlemenin ve korumanın en etkili yollarından biri olsa da, etikete ulaşmanızı artırmak için aşağıdaki yöntemlerden herhangi birini kullanarak bu dosyaları destekleyip destek alamayıp tamamlamayabilirsiniz:

- Daha SharePoint Syntex ile bir belge anlama modeline duyarlılık etiketi [uygulayabilir, böylece](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model) bir kitaplıkta tanımlanan belgeler SharePoint otomatik olarak etiketlenir.

- [Azure Information Protection birleşik etiketleme istemcisini kullanırken](/azure/information-protection/rms-client/aip-clientv2):

  - Ağ paylaşımları ve SharePoint Server kitaplıkları gibi şirket içi veri depolarında bulunan dosyalar için: Bu dosyalarda hassas bilgileri bulmak [](/azure/information-protection/deploy-aip-scanner) ve bunları doğru şekilde etiketlemek için tarayıcıyı kullanın. Bu dosyaları başka bir klasöre geçirmeyi veya SharePoint Microsoft 365, buluta taşımadan önce dosyaları etiketlemek için tarayıcıyı kullanın.

  - Duyarlılık etiketlerini daha önce başka bir etiketleme çözümü kullandıysanız: PowerShell'i ve bu çözümlerden etiketleri yeniden kullanmak için [gelişmiş](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#migrate-labels-from-secure-islands-and-other-labeling-solutions) bir ayarı kullanın.

- [Kullanıcılara hangi duyarlılık etiketlerini](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9) uygulayacaklarını eğitim verdikten sonra el ile etiketlemeyi teşvik edin. Kullanıcıların hangi etiketi uygulayacaklarını an güvenerek, varsayılan bir etiket ve zorunlu etiketlemeyi ilke ayarları olarak [yapılandırmayı göz önünde bulundurabilirsiniz](sensitivity-labels.md#what-label-policies-can-do).

Buna ek olarak, [konukların](/sharepoint/sensitive-by-default) dosyanın içeriğini en az bir DLP ilkesi tarayana kadar SharePoint'te yeni eklenen dosyalara erişmesini önlemek için varsayılan olarak yeni dosyaları hassas olarak işaretlemeyi göz önünde bulundurabilirsiniz.
