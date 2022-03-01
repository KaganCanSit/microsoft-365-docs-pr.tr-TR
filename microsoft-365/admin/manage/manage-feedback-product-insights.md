---
title: Microsoft ürün NPS geri bildirimleri ve kuruluşları için içgörüler
f1.keywords:
- NOCSH
ms.author: Kwekua
author: Kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: Microsoft ürünleri ve hizmetleriyle ilgili olarak nasıl olduklarını görmek için son kullanıcılarından Net promoter scores (NPS) kullanın.
ms.openlocfilehash: 230225edf924a418a65055a2527f9f7ded28ba61
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63016668"
---
# <a name="microsoft-product-nps-feedback-and-insights-for-your-organization"></a>Microsoft ürün NPS geri bildirimleri ve kuruluşları için içgörüler

Bir kuruluşta yönetici olarak Microsoft 365 Microsoft tarafından gönderilen NPS ürün anketlerine erişerek içgörüler elde edinebilirsiniz.  

Net Promoter Score (NPS) anketleri kullanıcı geri bildirimlerini toplar ve kullanıcıların ne kadar büyük bir olasılıkla ürün ve hizmetleri arkadaşlara ve iş arkadaşlarınıza öner aldıklarını ölçün. Bu veriler, ürün ve hizmetlerinizin benimsenmesi ve yaygınlıkını belirlemede Microsoft 365 için kullanılabilir.

Microsoft ürünleri ve hizmetleriyle ilgili öngörüler sunmak için NPS anketlerini ve son kullanıcılarından gelen geri bildirimleri kullanırız. Bu bilgiler, kurumunuzu son kullanan ürün ve hizmetleri bulmanızı ve sorunları tanımlamanıza ve hızlı bir şekilde çözmenize yardımcı olabilir. Bu bilgilerle şunları sebilirsiniz:

- Kullanıcıların tartıştığı en önemli temalara erişin.
- Mutlu kullanıcıları belirleme.
- Memnun olan kullanıcıların şikayetlerini ele alın.
- İşletim sisteminin veya platform kullananların hangileri olduğunu görme.
- Ürüne, platforma, kanala göre filtre uygulama veya anahtar sözcükler kullanarak arama.
- En çok karşılaşılan ürünler ve sorunlar hakkında son kullanıcı açıklamalarını görmek.
- Geri bildirimi ve anket bilgilerini CSV dosyasına aktarın.

## <a name="before-you-begin"></a>Başlamadan önce

Anket raporlarını görüntülemek ve [okumak](../add-users/about-admin-roles.md) için yönetici olmak gerekir. Kuruluşta, anket raporlarını görüntülemek ve okumak için geri bildirim anketlerin açık olması gerekir. Daha fazla [bilgi edinmek için, Microsoft geri bildirimlerini kurum için](manage-feedback-ms-org.md) yönetme makalelerini ziyaret edin.

## <a name="nps-survey-insights"></a>NPS anketi içgörüleri

1. Yönetim merkezinde HealthProduct  > **feedbackNPS anket öngörüleri'ne** >  gidin.
2. **NPS anket öngörüleri sayfasında**, sayfada gezinebilirsiniz ve kuruluşun NPS ile ilgili anket öngörülerini görebilirsiniz.

:::image type="content" source="../../media/product-feedback-main-page.png" alt-text="Ekran görüntüsü: Net Promoter Score (NPS) ana grafiği":::

### <a name="top-topic-filters"></a>En önemli konu filtreleri

Kullanıcı geri bildirimlerinden yaygın temaları belirledik. Daha sonra veri kümelerini eğiten ve geri bildirimleri En İyi Konular olarak otomatik olarak düzenleyen makine öğrenme **modellerini kullandık**. Bundan sonra, en yüksek verbatim geri bildirimi hacmine sahip en iyi beş konu tanımlayabilirsiniz.  

:::image type="content" source="../../media/top-topics-filter.png" alt-text="Ekran görüntüsü: En çok tartışılan geri bildirime sahip ilk beş konu":::

> [!NOTE]
> Akıllı bir konuyu, yalnızca konuyla ilgili uzmanlarla ortaklık içinde minimum kalite çıtası bir araya getirmeden yayımlarız. Duyarlık ve geri çekme ölçümleri aynıyı belirlemek için kullanılır.

**Verbatim duyarlılığı** , bu konuda sınıflandırılmış bir verbatim'in doğru olma olasılığıdır.

**Verbatim Recall** , bu konuyla ilgili bir indirimin bu konuda sınıflandırılma olasılığıdır.

Şu anda kullanılabilir olan konular şunlardır:

**Değişiklik Yönetimi** ; güncelleştirme işlemi, sık kullanılan uygulamaların nasıl kullanımı ve tasarım değişiklikleri gibi güncelleştirilmiş deneyimlerle ilgili müşteri açıklamalarını ifade eder.

- Verbatim Precision- %82
- Verbatim Geri Çekme- %81

**İşbirliği** , kullanıcıların Microsoft uygulamalarını kullanarak işbirliğini ne kadar kolay bulmaları anlamına gelir.

- Verbatim Precision- %92
- Verbatim Recall-91%

**Karmaşıklık** , uygulamaların karmaşık mı yoksa kullanımı kolay mı olduğunu hissetmeleri konusunda müşteri geri bildirimlerine başvurur.

- Verbatim Precision- %92
- Verbatim Recall- 89%

**Genel Takdir** açıklaması, pozitif bir duyguları olan ve diğer konuya uyması olmayan müşterilerin açıklamalarını ifade eder.

- Verbatim Precision- %93
- Verbatim Recall- 98%

**Güvenilirlik,** uygulama ve sistem davranışı ile ilgili olarak beklenmeyen sonlandırmaya neden olan müşteri yorumlarını içerir.

- Verbatim Precision- %97
- Verbatim Recall- 94%

**Gezinti** , uygulama gezintisi ve kullanılabilirlik hakkında müşteri yorumlarını içerir.  

- Verbatim Precision- %93
- Verbatim Recall- 98%

**Performans** , bir Microsoft ürünü kullanırken bir kullanıcının deneyimleladığı işlemlerin algılanma hızıyla ilgili sorunları ele alan müşteri açıklamalarını ifade eder. Bu konu, kilitlenme alanlarını veya daha geniş güvenilirlik sorunlarını kapsamıyor.

- Verbatim Precision- %92
- Verbatim Recall- 98%

**Güvenilirlik,** müşteri yorumlarını uygulama ve sistem davranışı hakkında beklenmeyen sonlandırma ile sonuçlandırarak ifade eder.  

Verbatim Precision- 97% Verbatim Geri Çekme- %94

**Kullanıcı Eğitimi** , yardım belgeleri, öğreticiler, kılavuzlar ve diğer ürün içi veya çevrimiçi öğrenme içeriğiyle ilgili müşteri yorumlardan oluşur.

- Verbatim Precision- %83
- Verbatim Recall- 87%

**Değer** , fiyatlandırma ve ödeme tercihleri gibi konularla ilgili müşteri tercihlerine başvurur.  

- Verbatim Precision- %86
- Verbatim Geri Çekme- %100

### <a name="chart-information"></a>Grafik bilgileri

**Toplam geri** bildirim, son kullanıcılar tarafından gönderilen toplam NPS geri bildirim yanıtı sayısını gösterir, yorumlara NPS geri bildirimi eksner ve yorum olmadan da gösterir.

**Açıklamalar** , son kullanıcı tarafından gönderilen ve açıklama içeren toplam NPS geri bildirim yanıtı sayısını gösterir.

**Uygulamaya göre yanıt hacmi** uygulamaya göre TOPLAM NPS geri bildirim yanıtı ses düzeyini gösterir.

**Platforma göre yanıt hacmi** , platforma göre NPS geri bildirim yanıtının toplam sayısını gösterir.

**Aya göre geri bildirim hacmi** , son on iki ayın toplam NPS geri bildirim yanıtı ses düzeyini gösterir.

:::image type="content" source="../../media/response-details.png" alt-text="Ekran görüntüsü: Yanıt hacmi ve aya göre yanıt hacmi":::

Grafikler aşağıdaki gibi NPS derecelendirmesi ile filtrelenebilir:

- Yükleniciler, sizin ürün veya hizmetinizi öneren memnun değilim müşterilerdir.
- Pasifler hizmetten memnun olan, ancak ürün veya hizmetinizi öneren müşterilerdir.
- Yükseltenler- Sadık, sadık ve sadık olan ve ürün veya hizmetinizi öneren mutlu müşteriler.

:::image type="content" source="../../media/how-likely-recommend.png" alt-text="Ekran görüntüsü: Bir uygulamayı bir arkadaşınıza veya meslektaşına önerilme olasılığınız ile ilgili grafik":::

### <a name="export-to-csv-and-search"></a>CSV ve Arama'ya aktarma

CSV'ye Aktar işlevini kullanarak ham verileri daha fazla çözümlemek için dışarı aktarabilirsiniz. Geri bildirim alanına karşılık gelen açıklama bölümünde anahtar sözcükler için arama yapabilirsiniz.

:::image type="content" source="../../media/export-to-csv.png" alt-text="Ekran görüntüsü: CSV'ye dışarı aktar için seçin":::

> [!NOTE]
> Ham veriler, NPS geri bildirimleri de içinde olmak üzere tüm geri bildirim türlerini içerir.

### <a name="filters"></a>Filtreler

Kanallar, Ürünler, **Platformlar** **ve Geri** Bildirim **Türlerine** göre **filtre uygulama.**

**Kanallar**, kuruluşların belirli bir süre için özellik güncelleştirmelerini ne sıklıkta edin olduklarını seçmeleri için Office. Daha fazla bilgi için [bkz. Yayın için güncelleştirme kanallarına Microsoft 365 Uygulamaları](/deployoffice/overview-update-channels). Bu filtre, belirli bir kanalda kullanıcıdan gönderilen geri bildirime kadar filtrelemenizi sağlar.

Geri bildirim Android, iOS, **Mac ve Diğer** Platformlar'a Windows. Bu filtre, geri bildirimi gönderildikten sonra gönderilen platforma göre filtrelemenizi sağlar.

İş ürünleri **Microsoft 365 çoğunluğu bu** filtre altında bulunabilir. Geri bildirim gönderilen ürünleri seçmek için bu filtreyi kullanın.

Topladığımız **geri bildirimleri filtrelemek** için Geri Bildirim Türlerini (yalnızca NPS geri bildirim türlerine ayarlanmış) kullanın.

:::image type="content" source="../../media/feedback-filters.png" alt-text="Ekran görüntüsü: Geri bildirim türlerini gösteren grafik":::

### <a name="we-want-to-hear-from-you"></a>Bize haber almak için

NPS anketi içgörü panosu hakkındaki düşüncelerinizi ve bu panoyu nasıl geliştir fikirlerinizi paylaşabilirsiniz. Ürünler ve hizmetlerde Geri Bildirim bölümlerini kullanın. Bize e-postayla da e-posta prosight@microsoft.com
