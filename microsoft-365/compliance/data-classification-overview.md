---
title: Veri sınıflandırması hakkında daha fazla bilgi edinme
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: admindeeplinkDEFENDER
search.appverid:
- MOE150
- MET150
description: Veri sınıflandırma panosu, kuruluşunuzda ne kadar hassas veri bulunduğunu ve sınıflandırıldığını size gösterir.
ms.openlocfilehash: e84205a0357e87f28a77f5186265cf421add1483
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66640774"
---
# <a name="learn-about-data-classification"></a>Veri sınıflandırması hakkında daha fazla bilgi edinme

Microsoft 365 yöneticisi veya uyumluluk yöneticisi olarak, kuruluşunuzdaki içeriği değerlendirip etiketleyebilir, böylece içeriği nerede olursa olsun denetleyebilir, nerede olursa olsun koruyabilir ve kuruluşunuzun ihtiyaçlarına göre korunup silindiğinden emin olabilirsiniz. Bunu [duyarlılık etiketleri](sensitivity-labels.md), [bekletme etiketleri](retention.md#retention-labels) ve hassas bilgi türü sınıflandırması uygulaması aracılığıyla yaparsınız. Bulma, değerlendirme ve etiketlemenin çeşitli yolları vardır, ancak sonuç olarak etiketlenmiş ve bu etiketlerden biriyle veya her ikisiyle de sınıflandırılmış çok sayıda belgeniz ve e-postanız olabilir. Bekletme etiketlerinizi ve duyarlılık etiketlerinizi uyguladıktan sonra, etiketlerin kiracınızda nasıl kullanıldığını ve bu öğelerle ne yapıldığını görmek istersiniz. Veri sınıflandırma sayfası, özellikle de bu içerik gövdesine görünürlük sağlar:

- hassas bilgi türü olarak sınıflandırılmış olan sayı öğeleri ve bu sınıflandırmaların ne olduğu
- Hem Microsoft 365 hem de Azure Information Protection'da en çok uygulanan duyarlılık etiketleri
- en çok uygulanan bekletme etiketleri
- kullanıcıların hassas içeriğinizi ele aldığı etkinliklerin özeti
- hassas ve saklanan verilerinizin konumları

Bu özellikleri veri sınıflandırma sayfasında da yönetirsiniz:

- [eğitilebilir sınıflandırıcılar](classifier-learn-about.md)
- [hassas bilgi türleri](sensitive-information-type-learn-about.md)
- [Tam veri eşleşmesine dayalı hassas bilgi türleri hakkında daha fazla bilgi edinme](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [içerik gezgini](data-classification-content-explorer.md)
- [etkinlik gezgini](data-classification-activity-explorer.md)

Veri sınıflandırmasını <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalı</a> veya <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalı</a> > **Sınıflandırma** > **Veri Sınıflandırması'nda** bulabilirsiniz.

Veri sınıflandırma özelliklerimiz için video turuna katılın.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vx8x]

Veri sınıflandırması, herhangi bir ilke oluşturmadan önce hassas içeriğinizi ve etiketli içeriğinizi tarar. Buna **sıfır değişiklik yönetimi** adı verilir. Bu, ortamınızdaki tüm saklama ve duyarlılık etiketlerinin etkisini görmenizi sağlar ve koruma ve idare ilkesi gereksinimlerinizi değerlendirmeye başlamanızı sağlar.

## <a name="prerequisites"></a>Önkoşullar

### <a name="permissions"></a>İzinler

 Veri sınıflandırma sayfasına erişim elde etmek için, bir hesaba bu rollerden veya rol gruplarından herhangi birinde üyelik atanması gerekir.

**Microsoft 365 rol grupları**

- Genel yönetici
- Uyumluluk yöneticisi
- Güvenlik yöneticisi
- Uyumluluk veri yöneticisi

> [!NOTE]
> En iyi uygulama olarak, Microsoft 365 veri sınıflandırmasına erişim vermek için her zaman en az ayrıcalığı olan rolü kullanın.

#### <a name="roles-and-role-groups-in-preview"></a>Önizlemede Roller ve Rol Grupları

Önizlemede, erişim denetimlerinizde ince ayar yapmak için test yapabileceğiniz roller ve rol grupları vardır.

Aşağıda, önizleme aşamasında olan geçerli rollerin listesi yer alır. Bunlar hakkında daha fazla bilgi edinmek için bkz [. Güvenlik & Uyumluluk Merkezi'ndeki Roller](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Information Protection Yönetici
- Information Protection Analisti
- Information Protection Araştırmacısı
- Information Protection Okuyucu

Aşağıda, önizleme aşamasında olan geçerli rol gruplarının listesi yer alır. Bunlar hakkında daha fazla bilgi edinmek için bkz [. Güvenlik & Uyumluluk Merkezi'ndeki Rol grupları](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Information Protection
- Information Protection Yöneticileri
- Information Protection Analistleri
- Information Protection Araştırmacıları
- Information Protection Okuyucular

## <a name="sensitive-information-types-used-most-in-your-content"></a>İçeriğinizde en çok kullanılan hassas bilgi türleri

Microsoft 365, sosyal güvenlik numarası veya kredi kartı numarası içeren bir öğe gibi hassas bilgi türlerinin birçok tanımıyla birlikte gelir. Hassas bilgi türleri hakkında daha fazla bilgi için bkz [. Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md).

Hassas bilgi türü kartı, kuruluşunuz genelinde bulunan ve etiketlenen en önemli hassas bilgi türlerini gösterir.

![en hassas bilgi türleri.](../media/data-classification-sens-info-types-card.png)

Belirli bir sınıflandırma kategorisinde kaç öğe olduğunu öğrenmek için, kategorinin çubuğunun üzerine gelin.

![en hassas bilgi türleri vurgulama ayrıntısı.](../media/data-classification-sens-info-types-hover.png)

> [!NOTE]
> Kartta "Hassas bilgilerle veri bulunamadı" iletisi görüntüleniyorsa, kuruluşunuzda hassas bilgi türü olarak sınıflandırılmış veya gezinilmiş hiçbir öğe olmadığı anlamına gelir. Etiketleri kullanmaya başlamak için bkz:
>- [Hassasiyet etiketlerini kullanmaya başlama](get-started-with-sensitivity-labels.md)
>- [Kayıt yönetimini kullanmaya başlama](get-started-with-records-management.md)
>- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)

## <a name="top-sensitivity-labels-applied-to-content"></a>İçeriğe en çok uygulanan duyarlılık etiketleri

Microsoft 365 veya Azure Information Protection (AIP) aracılığıyla bir öğeye duyarlılık etiketi uyguladığınızda iki şey gerçekleşir:

- Öğenin kuruluşunuzdaki değerini gösteren etiket belgeye eklenir ve öğenin gittiği her yerde bu etiketi izler.
- Etiketin varlığı, zorunlu filigran veya şifreleme gibi çeşitli koruyucu davranışlara olanak tanır. Uç nokta koruması etkinleştirildiğinde, bir öğenin kuruluş denetiminizden çıkmasını bile engelleyebilirsiniz.

Duyarlılık etiketleri hakkında daha fazla bilgi için bkz. [Duyarlılık etiketleri hakkında bilgi edinin](sensitivity-labels.md)

İlgili verilerin veri sınıflandırma sayfasında gösterilmesi için SharePoint ve OneDrive'daki dosyalar için duyarlılık etiketlerinin etkinleştirilmesi gerekir. Daha fazla bilgi için bkz [. SharePoint ve OneDrive'da Office dosyaları için duyarlılık etiketlerini etkinleştirme](sensitivity-labels-sharepoint-onedrive-files.md).

Duyarlılık etiketi kartı, duyarlılık düzeyine göre öğe sayısını (e-posta veya belge) gösterir.

![duyarlılık etiketi sınıflandırması yer tutucu ekran görüntüsüne göre içeriğin dökümü.](../media/data-classification-top-sensitivity-labels-applied.png)

> [!NOTE]
> Herhangi bir duyarlılık etiketi oluşturmadıysanız veya yayımlamadıysanız veya hiçbir içerikte duyarlılık etiketi uygulanmadıysa, bu kart "Duyarlılık etiketi algılanmadı" iletisini görüntüler. Duyarlılık etiketlerini kullanmaya başlamak için bkz:
>- [Duyarlılık etiketlerini kullanmaya başlama](get-started-with-sensitivity-labels.md) veya AIP için [Azure bilgi koruma ilkesini yapılandırma](/azure/information-protection/configure-policy)

## <a name="top-retention-labels-applied-to-content"></a>İçeriğe en çok uygulanan bekletme etiketleri

Bekletme etiketleri, kuruluşunuzdaki içeriğin saklama ve bırakma işlemlerini yönetmek için kullanılır. Uygulandığında, bir öğenin silinmeden önce ne kadar süre tutulacağını, silinmeden önce gözden geçirilip gözden geçirilmeyeceğini, saklama süresinin ne zaman dolacağını ve kayıt olarak işaretlenip işaretlenmeyeceğini denetlemek için kullanılabilir. Daha fazla bilgi için bkz. [Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinin](retention.md).

En üstteki uygulanan bekletme etiketleri kartı, belirli bir bekletme etiketine sahip olan öğe sayısını gösterir.

![üst uygulanan bekletme etiketleri yer tutucu ekran görüntüsü.](../media/data-classification-top-retention-labels-applied.png)

> [!NOTE]
> Bu kartta "Bekletme etiketi algılanmadı" iletisinin görüntülenmesi, hiçbir bekletme etiketi oluşturmadığınız veya yayımlamadığınız veya hiçbir içeriğin bekletme etiketi uygulanmadığı anlamına gelir. Bekletme etiketlerini kullanmaya başlamak için bkz:
>- [Veri yaşam döngüsü yönetimini kullanmaya başlama](get-started-with-data-lifecycle-management.md)

## <a name="top-activities-detected"></a>En çok kullanılan etkinlikler algılandı

Bu kart, kullanıcıların duyarlılık etiketli öğeler üzerinde gerçekleştirebilecekleri en yaygın eylemlerin hızlı bir özetini sağlar. Microsoft 365'in Windows 10 uç noktalarda bulunan etiketli içerik ve içerik üzerinde izlediği farklı etkinliklerin detayına gitmek için [Etkinlik gezginini](data-classification-activity-explorer.md) kullanabilirsiniz.

> [!NOTE]
> Bu kartta "Etkinlik algılanmadı" iletisi görüntülenirse, dosyalarda etkinlik olmadığı veya kullanıcı ve yönetici denetiminin açık olmadığı anlamına gelir. Denetim günlüklerini açmak için bkz:
>- [Güvenlik & uyumluluk merkezinde denetim günlüğünde arama yapma](search-the-audit-log-in-security-and-compliance.md)

## <a name="sensitivity-and-retention-labeled-data-by-location"></a>Konuma göre etiketlenmiş veriler duyarlılık ve bekletme

Veri sınıflandırma raporlamasının amacı, hangi etikete sahip öğelerin sayısına ve konumlarına görünürlük sağlamaktır. Bu kartlar Exchange, SharePoint ve OneDrive vb.'de etiketlenmiş öğe sayısını size bildirir.

> [!NOTE]
> Bu kartta "Konum algılanmadı, herhangi bir duyarlılık etiketi oluşturmadığınız veya yayımlamadığınız veya hiçbir içeriğin bekletme etiketi uygulanmadığı anlamına gelir. Duyarlılık etiketlerini kullanmaya başlamak için bkz:
>- [Duyarlılık etiketleri](sensitivity-labels.md)

## <a name="public-preview-release-notes"></a>Genel önizleme sürüm notları 

> [!NOTE]
> **Exchange posta kutusu sayısı: Exchange posta kutularının** detayına gittiğiniz zaman küçük bir araç ipucunun göründüğünü fark edeceksiniz. Bu, hassas bilgi türü, duyarlılık etiketi ve bekletme etiketi için görüntülenen toplama sayısının posta kutusunda bulacağınız öğe sayısıyla tam olarak eşleşmeyebileceği gerçeğini ortaya çıkarmaktır. Bunun nedeni, klasördeki detaya gitme işleminin içeriğin sınıflandırılan canlı görünümünü getirmesi ve toplanan sayıyı hesaplamasıdır. Kullanıcının fark etmesi gereken bilgiler

> [!NOTE]
> **Şifrelenmiş belgelerin işlenmesi: Şifrelenmiş** SharePoint, Exchange ve OneDrive dosyaları içerik gezgininde işlenmez. Bu, içerik gezgininde dosya içeriğini görme gereksinimi ile içeriği şifrelenmiş tutma gereksinimi arasında bir denge gerektiren hassas bir sorundur. **İçerik Gezgini Liste Görüntüleyicisi** ve **İçerik Gezgini İçerik Görüntüleyicisi** rol grupları tarafından verilen izinlerle, dosyaların liste görünümünü, dosya meta verilerini ve web istemcisi aracılığıyla içeriğe erişmek için kullanabileceğiniz bir bağlantıyı görürsünüz. Kullanıcının fark etmesi gereken bilgiler

> [!NOTE]
> **SharePoint aramasında bekletme etiketi adlarında desteklenen karakterler: SharePoint** araması, ile `-`veya `_` içinde bekletme etiketi adlarını desteklemez. Örneğin ve `Label-MIP` `Label_MIP` desteklenmez. SharePoint araması, duyarlılık etiketi adlarında ve hassas bilgi türü adlarında bu karakterleri destekler.

> [!NOTE]
> **OneDrive önizleme aşamasında kalır**: Önizleme programımız sırasında OneDrive tümleştirmesi hakkındaki değerli geri bildirimleriniz için teşekkür ederiz. Ayrıntıları incelediğimizde tutarsız veri / akışlarla karşılaşabilirsiniz. Tüm düzeltmeler gerçekleşene kadar OneDrive'ı önizlemede göstermeyi sürdüreceğiz. Devam eden desteğiniz için teşekkür ederiz.

## <a name="see-also"></a>Ayrıca bkz.

- [Etiket etkinliğini görüntüleme](data-classification-activity-explorer.md)
- [Etiketli içeriği görüntüleme](data-classification-content-explorer.md)
- [Duyarlılık etiketleri hakkında bilgi edinin](sensitivity-labels.md)
- [Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinin](retention.md)
- [Hassas bilgi türleri hakkında daha fazla bilgi edinme](sensitive-information-type-learn-about.md)
- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)
- [Eğitilebilir sınıflandırıcılar (önizleme) hakkında bilgi edinin](classifier-learn-about.md)

Veri gizliliği düzenlemelerine uymak için veri sınıflandırmasını kullanmayı öğrenmek için bkz. [Microsoft 365 (aka.ms/m365dataprivacy) ile veri gizliliği düzenlemeleri için bilgi koruması dağıtma](../solutions/information-protection-deploy.md)  .
