---
title: Veri sınıflandırması hakkında bilgi
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
description: Veri sınıflandırma panosu, kuruluşta ne kadar hassas verilerin bulunarak sınıflandırılmış olduğunu görebilirsiniz.
ms.openlocfilehash: ac51e20b786b2e21d3bb83bd7900e56fb8fac513
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010853"
---
# <a name="learn-about-data-classification"></a>Veri sınıflandırması hakkında bilgi

Bir Microsoft 365 yöneticisi veya uyumluluk yöneticisi olarak, nereye gittiğini kontrol etmek, nerede olursa olsun korumak ve içeriğin kuruluşlarınıza uygun şekilde korunmasını ve silinmesini sağlamak için, organizasyon içeriği değerlendirebilir ve etiketlebilirsiniz. Bunu duyarlılık etiketleri, bekletme [etiketleri ve hassas bilgi](sensitivity-labels.md) [türü sınıflandırma](retention.md#retention-labels) uygulaması aracılığıyla yapar. Bulma, değerlendirme ve etiketlemenin çeşitli yolları vardır, ancak sonuçta, bu etiketlerin biri veya her ikisi ile etiketlenen ve sınıflandırılmış çok fazla sayıda belgeniz ve e-postanız olabilir. Bekletme etiketlerinizi ve duyarlılık etiketlerinizi verdikten sonra, kiracınız genelinde etiketlerin nasıl kullanılıyor olduğunu ve bu öğelerle nelerin yapılıyor olduğunu görmek iyi olur. Veri sınıflandırma sayfası özellikle şu içerik gövdesinde görünürlük sağlar:

- hassas bir bilgi türü olarak sınıflandırılmış sayı öğeleri ve bu sınıflandırmaların ne olduğu
- hem Azure Information Protection'da hem de Azure Microsoft 365 en yüksek duyarlılık etiketleri
- en çok uygulanan bekletme etiketleri
- kullanıcıların hassas içeriğinizi ele alan etkinliklerin özeti
- hassas ve korunur verilerinizin konumları

Bu özellikleri veri sınıflandırma sayfasında da yönetirsiniz:

- [eğitilebilir sınıflayıcılar](classifier-learn-about.md)
- [hassas bilgi türleri](sensitive-information-type-learn-about.md)
- [Hassas bilgi türlerine dayalı tam veri eşleşmesi hakkında bilgi](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [içerik gezgini](data-classification-content-explorer.md)
- [etkinlik gezgini](data-classification-activity-explorer.md)

Veri sınıflandırmayı **PortalClassificationData** >  Classification <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a> <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">veya Microsoft 365 Defender</a> >  sayfasında **bulabilirsiniz**.

Veri sınıflandırma özelliklerimizi videoyla gezinin.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4vx8x]

Veri sınıflandırması, herhangi bir ilke oluşturmadan önce hassas içeriğinizi ve etiketli içeriğinizi tarar. Buna sıfır **değişiklik yönetimi denir**. Bu, ortamınıza tüm bekletme ve duyarlılık etiketlerinin etkisini görmenizi ve koruma ve yönetim ilkesi  gereklerinizi değerlendirmeye başlamanızı sağlar.

## <a name="prerequisites"></a>Önkoşullar

### <a name="permissions"></a>İzinler

 Veri sınıflandırma sayfasına erişim elde etmek için, bu rollerden veya rol gruplarından herhangi biri için bir hesaba üyelik atanması gerekir.

**Microsoft 365 grupları**

- Genel yönetici
- Uyumluluk yöneticisi
- Güvenlik yöneticisi
- Uyumluluk veri yöneticisi

> [!NOTE]
> En iyi uygulama olarak, rolü her zaman en az ayrıcalıkla kullanarak veri sınıflandırması Microsoft 365 kullanın.

#### <a name="roles-and-role-groups-in-preview"></a>Önizlemede Roller ve Rol Grupları

Önizlemede, erişim denetimlerinize ince ayar yapmak için test etmek için deney erişiminiz olan roller ve rol grupları vardır.

İşte önizlemede olan Microsoft Bilgi Koruması (MIP) rollerinin listesi. Bu roller hakkında daha fazla bilgi edinmek [için Güvenlik ve Uyumluluk Merkezi'& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Bilgi Koruması Yöneticisi
- Bilgi Koruma Analisti
- Bilgi Koruma Koruma Koruma Koruması
- Bilgi Koruma Okuyucusu

Önizlemede olan MIP rol gruplarının listesi burada ve ve şekildedir. Bu gruplar hakkında daha fazla bilgi edinmek [için Güvenlik ve Uyumluluk Merkezi'nde rol & bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Bilgi Koruması
- Bilgi Koruması Yöneticileri
- Bilgi Koruma Analistleri
- Bilgi Koruma Koruma KorumaLarı
- Bilgi Koruma Okuyucuları

## <a name="sensitive-information-types-used-most-in-your-content"></a>İçeriğinizin en çok kullanılan hassas bilgi türleri

Microsoft 365, sosyal güvenlik numarası veya kredi kartı numarası içeren bir öğe gibi hassas bilgi türlerinin birçok tanımıyla gelir. Hassas bilgi türleri hakkında daha fazla bilgi için bkz. [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md).

Hassas bilgi türü kartı, bulunan ve kuruluş genelinde etiketlenmiş en önemli hassas bilgi türlerini gösterir.

![en önemli bilgi türleri.](../media/data-classification-sens-info-types-card.png)

Herhangi bir sınıflandırma kategorisinde kaç öğe olduğunu bulmak için, kategori çubuğunun üzerine gelin.

![en önemli bilgi türleri vurgu ayrıntısı.](../media/data-classification-sens-info-types-hover.png)

> [!NOTE]
> Kartta "Hassas bilgilerle birlikte hiçbir veri bulunamadı" iletisi görüntülenirse, bu, kuruluşta hassas bilgi türü olarak sınıflandırılmış veya gezinilen hiç öğe yok anlamına gelir. Etiketlere başlamak için bkz:
>- [Duyarlılık etiketleriyle çalışmaya başlama](get-started-with-sensitivity-labels.md)
>- [Kayıt yönetimiyle çalışmaya başlama](get-started-with-records-management.md)
>- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)

## <a name="top-sensitivity-labels-applied-to-content"></a>İçeriklere en yüksek duyarlılık etiketleri uygulanmış

Bir öğeye Microsoft 365 Azure Information Protection (AIP) aracılığıyla bir duyarlılık etiketi uygulayabilirsiniz; iki şey olur:

- Öğenin kuruluş değeri gösteren bir etiket belgeye eklidir ve her gittiği yerde bu etiketi takip eder.
- Etiketin varlığı, zorunlu filigran veya şifreleme gibi çeşitli koruyucu davranışlara olanak sağlar. Uç nokta koruması etkin durumda olduğunda, öğenin kuruluş denetiminizi bırakmasını bile önlebilirsiniz.

Duyarlılık etiketleri hakkında daha fazla bilgi için bkz. [Duyarlılık etiketleri hakkında bilgi](sensitivity-labels.md)

Duyarlılık etiketlerinin, ilgili verilerin veri sınıflandırma sayfasında SharePoint OneDrive için metin veya metin olarak yer alan dosyalar için etkinleştirilmesi gerekir. Daha fazla bilgi için bkz[. Dosya ve klasörlerin Office için duyarlılık SharePoint OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

Duyarlılık etiket kartı öğe sayısını (e-posta veya belge) duyarlılık düzeyine göre gösterir.

![Duyarlılık etiketi sınıflandırma yer tutucu ekran görüntüsüne göre içeriğin çözümlemesi.](../media/data-classification-top-sensitivity-labels-applied.png)

> [!NOTE]
> Herhangi bir duyarlılık etiketi oluşturmadınız veya yayımlanmış veya hiç duyarlılık etiketi uygulanmadı ise, bu kart "Duyarlılık etiketi algılanmadı" mesajını görüntüler. Duyarlılık etiketleriyle çalışmaya başlamak için bkz:
>- [Duyarlılık etiketleriyle çalışmaya başlama veya](get-started-with-sensitivity-labels.md) AIP [için Azure bilgi koruma ilkesi yapılandırma](/azure/information-protection/configure-policy)

## <a name="top-retention-labels-applied-to-content"></a>üst bekletme etiketleri içeriğe uygulanır

Bekletme etiketleri, kurumda içeriğin bekletme ve yok tutulmasını yönetmek için kullanılır. Bu uygulama uygulandığında, bir öğenin silinmeden önce ne kadar süreyle tutulacaklarını, silinmeden önce gözden geçirip gözden geçirilemeyeceklerini, bekletme süresinin ne zaman dol olacağını ve kayıt olarak işaretlenir mi olacağını kontrol etmek için kullanılabilirler. Daha fazla bilgi için bkz [. Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinebilirsiniz](retention.md).

En çok uygulanan bekletme etiketleri kartı, belirli bir bekletme etiketine sahip öğe sayısı gösterir.

![üst uygulanmış bekletme etiketleri yer tutucu ekran görüntüsü.](../media/data-classification-top-retention-labels-applied.png)

> [!NOTE]
> Bu kartta "Bekletme etiketi algılanmadı" iletisi görüntülenmişse, hiçbir bekletme etiketi oluşturmadınız veya hiçbir içerik saklama etiketi uygulanmadı demektir. Bekletme etiketleriyle çalışmaya başlamak için bkz:
>- [Bilgi yönetimiyle çalışmaya başlama](get-started-with-information-governance.md)

## <a name="top-activities-detected"></a>Algılanan en önemli etkinlikler

Bu kart, kullanıcıların etiketli öğelere duyarlılıkla ilgili gerçekleştir yaptıkları en yaygın işlemlerin hızlı bir özetini sağlar. Etkinlik gezginini [kullanarak,](data-classification-activity-explorer.md) Microsoft 365 uç noktalarında bulunan etiketli içerik ve içerik üzerinde takip etmek Windows 10 detaya inebilirsiniz.

> [!NOTE]
> Bu kartta "Etkinlik algılanmadı" iletisi görüntülenirse bu, dosyalarda herhangi bir etkinlik olmadığının veya kullanıcının ve yönetici denetiminin açık olmadığını gösterir. Denetim günlüklerini açmak için bkz:
>- [Güvenlik ve uyumluluk merkezinde denetim & arama](search-the-audit-log-in-security-and-compliance.md)

## <a name="sensitivity-and-retention-labeled-data-by-location"></a>Konuma göre etiketlenmiş veriler duyarlılık ve bekletme

Veri sınıflandırma raporlamanın asıl noktası, hem etikete hem de konumlarına sahip öğe sayısına görünürlük sağlamaktır. Bu kartların etiketli kaç öğe olduğunu Exchange SharePoint ve OneDrive vardır.

> [!NOTE]
> Bu kartta "Algılanan konum yok, herhangi bir duyarlılık etiketi oluşturmadınız veya hiçbir içerik saklama etiketi uygulanmadı" iletisi görüntülenir. Duyarlılık etiketleriyle çalışmaya başlamak için bkz:
>- [Duyarlılık etiketleri](sensitivity-labels.md)

## <a name="public-preview-release-notes"></a>Genel önizleme sürüm notları 

> [!NOTE]
> **Exchange kutusu sayısını seçin**: Posta kutuları üzerinde detaya ilerlerken küçük bir araç Exchange görünür. Bunun en önemli konusu, hassas bilgi türü, duyarlılık etiketi ve bekletme etiketi için görüntülenen toplama sayısının, posta kutusunda bu sayıyla tam olarak eşleşmey activede olduğudur. Bunun nedeni, klasörde detaya gitmenin, toplanan sayım hesaplanırken sınıflandırılan canlı içeriği getirmesidir. Kullanıcının fark olması gereken bilgiler (kayakçıda olsa bile)

> [!NOTE]
> **Şifrelenmiş belgelerin işlemesi**: SharePoint, Exchange ve OneDrive dosyalarınız içerik gezgininde işlenmez. Bu, içerik gezgininde dosya içeriğini görme ihtiyacı ile içeriği şifreli tutma arasında denge olmasını gerektiren hassas bir sorundur. İçerik Gezgini Liste **Görüntüleyicisi tarafından** verilen izinler ve İçerik Gezgini  İçerik Görüntüleyicisi rol gruplarıyla, dosyaların liste görünümünü, dosya meta verilerini ve içeriğe web istemcisi üzerinden erişmek için kullanabileceğiniz bir bağlantı görünür. Kullanıcının fark olması gereken bilgiler (kayakçıda olsa bile)

> [!NOTE]
> **Bir aramada bekletme etiketi adlarında SharePoint**: SharePoint `-`arama bekletme etiketi adlarını veya içinde bekletme etiketini desteklemez`_`. Örneğin, `Label-MIP` `Label_MIP` ve desteklenmiyor. SharePoint araması, duyarlılık etiketi adlarında ve hassas bilgi türü adlarında bulunan karakterleri destekler.

> [!NOTE]
> **OneDrive önizlemede kalır: Önizleme** programımız sırasında OneDrive değerli geri bildirimleriniz için teşekkür ederiz. Biz belirli bilgiler üzerinde çalışıyoruz, tutarsız veriler / akışlar ile sonuç oluşturabilirsiniz. Tüm düzeltmeler yerine gelene OneDrive önizlemede sergilemeye devam edeceğiz. Devam eden desteğiniz için teşekkür edersiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Etiket etkinliğini görüntüle](data-classification-activity-explorer.md)
- [Etiketli içeriği görüntüleme](data-classification-content-explorer.md)
- [Duyarlılık etiketleri hakkında bilgi edinin](sensitivity-labels.md)
- [Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi](retention.md)
- [Hassas bilgi türleri hakkında bilgi](sensitive-information-type-learn-about.md)
- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)
- [Eğitilebilir sınıflayıcılar (önizleme) hakkında bilgi](classifier-learn-about.md)

Veri gizliliği düzenlemelerine uygun olarak veri sınıflandırmasını nasıl kullanabileceğinizi öğrenmek için bkz. Gizlilikle ilgili veri gizliliği düzenlemelerine [Microsoft 365 (aka.ms/m365dataprivacy](../solutions/information-protection-deploy.md)).
