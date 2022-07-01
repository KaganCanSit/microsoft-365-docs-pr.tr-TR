---
title: Microsoft 365 yönetim merkezi'deki yenilikler ne?
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
search.appverid:
- MET150
- MOE150
- FRP150
ms.custom:
- MACDashWhatsNew
- AdminSurgePortfolio
- admindeeplinkMAC
description: Microsoft 365 yönetim merkezi - Bu ay eklenen özellikler hakkında bilgi edinin.
ms.openlocfilehash: fe801e913e227239b53eb7f1166a3f802f4217ce
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66602590"
---
# <a name="whats-new-in-the-microsoft-365-admin-center"></a>Microsoft 365 yönetim merkezi'deki yenilikler

::: moniker range="o365-21vianet"

> [!NOTE]
> Bu makaledeki bilgilerin bazıları 21Vianet tarafından sağlanan Office 365 için geçerli olmayabilir.

::: moniker-end

[Microsoft 365 yönetim merkezi](Microsoft 365 yönetim merkezi Genel Bakış](admin-overview/admin-center-overview.md) öğesine sürekli yeni özellikler ekliyoruz, öğrendiğimiz sorunları düzeltiyoruz ve geri bildiriminize göre değişiklikler yapıyoruz. Bazı özellikler müşterilerimiz için farklı hızlarda kullanıma sunulur. Henüz bir özellik görmüyorsanız, [kendinizi hedeflenen sürüme eklemeyi deneyin](manage/release-options-in-office-365.md).

Diğer Microsoft bulut hizmetleriyle ilgili yeni şeyleri öğrenmek isterseniz:

- [Azure Active Directory'deki yenilikler](/azure/active-directory/fundamentals/whats-new)
- [Exchange yönetim merkezindeki yenilikler](/Exchange/whats-new)
- [Microsoft Intune'deki yenilikler](/mem/intune/fundamentals/whats-new)
- [Microsoft Purview uyumluluk portalı'deki yenilikler](/Office365/SecurityCompliance/whats-new)
- [Microsoft 365 Defender'daki yenilikler](../security/mtp/whats-new.md)
- [SharePoint yönetim merkezindeki yenilikler](/sharepoint/what-s-new-in-admin-center)
- [Office güncelleştirmeleri](/OfficeUpdates/)
- [Windows sürüm durumunu denetleme](/windows/deployment/update/check-release-health)

## <a name="may-2022"></a>Mayıs 2022

### <a name="role-based-access-controls-rbac"></a>Rol tabanlı erişim denetimleri (RBAC)

özel güvenlik özniteliklerinin yönetimi için Microsoft 365 yönetim merkezi dört yeni rol vardır. Bu roller, **roller** altındaki Microsoft 365 yönetim merkezi herkes tarafından kullanılabilir.

- **Öznitelik Atama Yöneticisi**   Desteklenen Azure AD nesnelerine özel güvenlik öznitelik anahtarları ve değerleri atayın.

- **Öznitelik Atama Okuyucusu**   Desteklenen Azure AD nesneleri için özel güvenlik özniteliği anahtarlarını ve değerlerini okur.

- **Öznitelik Tanımı Yöneticisi**   Özel güvenlik özniteliklerinin tanımını tanımlayın ve yönetin.

- **Öznitelik Tanımı Okuyucusu**   Özel güvenlik özniteliklerinin tanımını okur.

Ayrıca, yöneticilere yalnızca Sanal Ziyaretleri yönetmek için ihtiyaç duydukları erişimi vermenizi sağlayan yeni bir rol vardır.

- **Sanal ZiyaretLer Yöneticisi**   Yönetim merkezlerinden veya Sanal Ziyaretler uygulamasından Sanal Ziyaretler bilgilerini ve ölçümlerini yönetin ve paylaşın.

Bu roller hakkında daha fazla bilgi için bkz. [yerleşik roller Azure AD](/azure/active-directory/roles/permissions-reference).

### <a name="quick-assist"></a>Hızlı Yardım

Uygulamanın performansını ve güvenliğini artırmak için Hızlı Yardım Windows Mağazası'na taşıdık. Windows Hızlı Yardım uygulaması, sizin ve son kullanıcılarınızın uzak bağlantı üzerinden bilgisayar yardımı almanıza veya sağlamanıza olanak tanır.

Yeni Hızlı Yardım Store uygulamasıyla geçiş kodu oluşturma sürelerinde önemli bir iyileştirme ve uygulama hatalarında azalma görmeniz gerekir.

Daha fazla bilgi için bkz. [Uzak bağlantı üzerinden bilgisayar sorunlarını çözme](https://support.microsoft.com/windows/solve-pc-problems-over-a-remote-connection-b077e31a-16f4-2529-1a47-21f6a9040bf3) ve [Yükleme Hızlı Yardım](https://support.microsoft.com/windows/install-quick-assist-c17479b7-a49d-4d12-938c-dbfb97c88bca)

## <a name="april-2022"></a>Nisan 2022

### <a name="nps-sentiment-insights"></a>NPS Yaklaşım İçgörüleri

NPS anket içgörüleri, Microsoft 365 yönetim merkezi yapay zeka temelli bir panodur.

Yönetim merkezinde **Sistem Sağlığı** > **Ürünü geri bildirimi** > **NPS anket içgörüleri'ne** gidin.

Bu özellik, sizin gibi yöneticilerin kullanıcılarınızın yanıt verdiği Microsoft NPS anketlerinden türetilen eyleme dönüştürülebilir içgörüler elde etmenize yardımcı olur. [Kuruluşunuz için Microsoft ürünü NPS geri bildirimi ve içgörüleri](manage/manage-feedback-product-insights.md) makalesinde daha fazla bilgi edinin.

Geri bildirimlerinize dayanarak, kullanıcılarınızın Microsoft 365 ürünleriyle ilgili neler hissettiğini öğrenebilmeniz için her NPS ayrıntılı geri bildiriminin yaklaşımını tanımlayan yeni bir özellik sunuyoruz. **NPS** ayrıntılı geri bildirimine Pozitif, **Negatif** ve **Diğer** gibi yaklaşım etiketleri atanır.

:::image type="content" source="../media/product-feedback-nps-verbatims.png" alt-text="Ekran görüntüsü: NPS anket içgörüleri sekmesinde ürün geri bildirim panosu":::

NPS anket içgörüleri panosundaki yaklaşım özelliğiyle şunları yapabileceksiniz:

- NPS ayrıntılı geri bildirimine göre son 12 ayın yaklaşım eğilimini görselleştirin.

- Uygulama ve platform başına yaklaşımı belirleme.

Üç yaklaşım mevcuttur:

:::image type="content" source="../media/sentiment-examples.png" alt-text="Ekran görüntüsü: Yaklaşım örnekleri ve açıklamaları":::

NPS anket içgörü panosunu kullanarak size daha iyi bir deneyim sunmak için aşağıdaki öğeleri denetlemenizi öneririz:

- Kullanıcılarınızı geri bildirim göndermeye teşvik edin.

- [Ürün içi anket ilkelerinin](https://config.office.com) etkinleştirildiğini onaylayın.

- [Windows Hata Bildirimi](/windows/win32/wer/windows-error-reporting) etkinleştirerek tanınabilirliği geliştirin.

> [!NOTE]
> Kurumsal bir müşteriyseniz ve tasarım oturumlarımıza katılmak istiyorsanız bize şu adreste bir e-posta gönderin: prosight@microsoft.com

### <a name="microsoft-365-admin-center-search"></a>Microsoft 365 yönetim merkezi arama

Artık genel arama'da arama yapıp **Enter'ı** seçerek tüm arama sonuçlarını ayrı bir tarayıcı sayfasında görüntüleyebilirsiniz.

Yeni ayrı arama sonuçları sayfamızla daha kapsamlı bir sonuç listesini keşfedebilir ve daha verimli bir arama deneyimi için tarayıcı sayfasına kolayca dönebilirsiniz.

:::image type="content" source="../media/whats-new-search-page.png" alt-text="Ekran görüntüsü: Yeni Microsoft 365 yönetim merkezi tarayıcı arama sayfası":::

### <a name="search-in-distribution-lists-to-add-priority-accounts"></a>Öncelik Hesapları eklemek için dağıtım listelerinde arama

Daha önce, öncelik hesaplarını yalnızca kişinin adını, e-posta adresini veya iş unvanını kullanarak arayabilirsiniz. Bu güncelleştirmeyle, artık dağıtım listesindeki öncelik hesaplarına eklenecek kişileri arayabilirsiniz. Bu, kişileri verimli bir şekilde toplu olarak eklemenize olanak tanır ve kuruluşunuzdaki tek tek kişileri etiketlemek için gereken süreyi azaltır.

:::image type="content" source="../media/search-by-distribution-list-priority-accounts.png" alt-text="Ekran görüntüsü: Dağıtım listesi kullanarak eklenecek öncelik hesaplarını arama":::

- Bir dağıtım listesinden en fazla 50 kullanıcıyı tek bir eylemde öncelik hesapları olarak etiketleyebilirsiniz.

- Kullanıcı hakkında departman ve iş unvanı gibi ek bilgiler Öncelik Hesapları sayfasında sunulmuştur.

- Yalnızca dağıtım listelerinde kullanıcı hesaplarını etiketleyebilir, listenin kendisini etiketleyemezsiniz. Zaten etiketlenmiş kullanıcılar dağıtım listesi aramanızda gösterilmez.

## <a name="march-2022"></a>Mart 2022

### <a name="microsoft-365-lighthouse-ga"></a>Microsoft 365 Lighthouse GA

Küçük ve orta ölçekli işletmeler, BT ortamlarını yönetmek için genellikle güvenilir BT iş ortaklarına güvenir. Yönetilen Hizmet Sağlayıcıları (MSP' ler) için çok kiracılı bir yönetim portalı olan [Microsoft 365 Lighthouse](https://aka.ms/March1SMBPartnerBlog) genel kullanılabilirliğiyle iş ortaklarının müşterileri uygun ölçekte güvenli hale getirmesini kolaylaştırıyoruz. Microsoft 365 Lighthouse, iş ortaklarını tehditleri, anormal oturum açma işlemlerini ve cihaz uyumluluk uyarılarını güvende tutmak için hızla tanımlama ve bunlarla ilgili işlem yapma gücü vererek müşterilere eksiksiz bir deneyim sağlar.

:::image type="content" source="../media/lighthouse.png" alt-text="Ekran görüntüsü: Microsoft 365 Lighthouse panosu":::

Microsoft 365 Lighthouse yalnızca bir BT iş ortağı hizmetidir ve Bulut Çözümü Sağlayıcısı (CSP) programına kayıtlı olan ve Microsoft 365 İş Ekstra, Microsoft 365 E3 veya Microsoft 365 İş Ekstra sahip en fazla 1000 lisanslı kullanıcısı olan müşterileri yöneten iş ortakları tarafından kullanılabilir İş için Microsoft Defender (önizlemede) abonelikler. Microsoft CSP'ye kayıtlı bir BT İş Ortağıysanız Microsoft 365 Lighthouse kuruluşunuz için hiçbir ücret ödemeden kullanılabilir ve iş ölçeğinize ve büyümenize yardımcı olacak şekilde tasarlanmıştır. Daha fazla bilgi için [Microsoft 365 Lighthouse yardım kitaplığına](../lighthouse/m365-lighthouse-overview.md) göz atın.

Microsoft 365 Lighthouse kullanmaya başlamak için bkz. [Microsoft 365 Lighthouse kaydolma](../lighthouse/m365-lighthouse-sign-up.md). Microsoft 365 Lighthouse, İş için Defender ve Microsoft 365 İş Ekstra hakkında daha fazla bilgi edinmek [için İş Ortağı web semineri serimizde bize katılın](https://aka.ms/M365MDBSeries).

## <a name="february-2022"></a>Şubat 2022

### <a name="net-promoter-score-nps-survey-insights"></a>Net promoter score (NPS) anket içgörüleri

Artık Microsoft 365 yönetim merkezi kullanıcılarınızın NPS anket verilerini ve içgörülerini görüntüleyebilirsiniz. Bu yeni özellik ile son kullanıcılarınızdan gelen NPS anket yanıtlarından eyleme dönüştürülebilir içgörüler elde edebilir ve tüm sorunları ve endişeleri gidererek daha yüksek son kullanıcı zevki elde edebilirsiniz.

Yönetim merkezinde **Sistem Sağlığı** > **Ürünü geri bildirimi** > **NPS anket içgörüleri'ne** gidin.

:::image type="content" source="../media/feedback-whatsnew.png" alt-text="Ekran görüntüsü: Microsoft 365 yönetim merkezi Geri Bildirim sayfasını gösterme":::

Kullanıcı geri bildirimlerinden ortak temaları belirledik. Ardından, veri kümelerini eğitmek ve geri bildirimleri otomatik olarak En Önemli Konulara düzenlemek için makine öğrenmesi modelleri tekniklerini kullandık.

Dokuz konu başlığı mevcuttur. Gelecek güncelleştirmelerde daha fazla konuya dikkat edin.

:::image type="content" source="../media/feedback-nine-topics.png" alt-text="Ekran görüntüsü: 9 yeni geri bildirim konusu gösteriliyor":::

NPS anket içgörü panosu şu üç yeni raporu ve özeti de içerir:

- Son 12 ay için aylık NPS eğilim hacmi
- Pasifleri, teşvik edicileri ve detraktörleri tanımlayabilmek
- Platform ve uygulama başına NPS birimi

NPS anket içgörü panosunu kullanarak size daha iyi bir deneyim sunmak için:

- Son kullanıcılarınızı geri bildirim göndermeye teşvik etme
- Ürün içi anket ilkelerinin etkinleştirildiğini onaylayın
- Windows Hata Bildirimi açarak tanılamayı geliştirme

[Kuruluşunuz için Microsoft ürünü NPS geri bildirimi ve içgörüleri](manage/manage-feedback-product-insights.md) makalesinde daha fazla bilgi edinin.  

> [!NOTE]
> Tasarım oturumlarımıza katılmak istiyorsanız bize şu adreste bir e-posta gönderin: prosight@microsoft.com

### <a name="microsoft-365-admin-center-video-training"></a>Microsoft 365 yönetim merkezi video eğitimi

Microsoft 365 yönetim merkezi video eğitimimizi güncelleştirdik. İşletmeniz için Microsoft 365'i ayarlamayı ve yönetmeyi öğrenmek için [Yönetici eğitim video kitaplığı](https://go.microsoft.com/fwlink/?linkid=2197659) sayfasına gidin.

:::image type="content" source="../media/admin-library-vid-training.png" alt-text="Ekran görüntüsü: Yönetim merkezi video eğitim kitaplığını gösterme":::

## <a name="july-2021"></a>Temmuz 2021

### <a name="microsoft-365-admin-center-search"></a>Microsoft 365 yönetim merkezi arama

Artık <a href="https://go.microsoft.com/fwlink/p/?linkid=2091030" target="_blank">Microsoft 365 yönetim merkezi</a> olay kimliklerini arayabilirsiniz. Mevcut olaylar hakkında sosyal medya, sektör yayınları veya diğer yöneticilerden bilgi edinebilirsiniz. Olay hakkında daha fazla ayrıntı aramak ve kuruluşunuz üzerindeki etkisini anlamak için artık yönetim merkezine gidebilirsiniz. Yönetim merkezinde olay kimliği için arama yapın.

:::image type="content" source="../media/incident-id.png" alt-text="Ekran görüntüsü: Yönetim merkezinde olay kimliğini arama":::

### <a name="support-ticket-insight-for-premier-organizations"></a>Premier kuruluşlar için destek bileti içgörüleri

Destek hacminiz hakkında görsel içgörüler sağlamak için **Ürüne göre Birim eğilimi ve Birim eğilimi** adlı 2 grafik ekledik.

**Birim eğilimi** sekmesinin altındaki çizgi grafik, kuruluşunuz için aylar içinde destek vakalarının artması veya azalması durumunda eğilimi vurgular. Her ay oluşturulan destek olaylarının sayısını denetlemek için grafiğin üzerine gelebilirsiniz.

:::image type="content" source="../media/SuppInsight-voltrnd.PNG" alt-text="Ekran görüntüsü: Kuruluşunuzda aylar içinde destek vakaları artıyorsa veya azalıyorsa eğilimi vurgulayan grafik":::

**Ürüne göre hacim eğilimi** grafiği, her ayın en yüksek destek talebine sahip ilk 3 ürününü gösterir. Tabloda filtrelemeyi etkinleştirdik ve artık sonuçları **Product**, **Severity** ve **Date'e** göre filtreleyebilirsiniz.

:::image type="content" source="../media/SuppInsight-voltrndproduct.PNG" alt-text="Ekran görüntüsü: Graph, her ayın en yüksek destek talebine sahip ilk 3 ürününü gösterir":::

Ayrıca, biletleriniz hakkında daha fazla içgörü sağlamak için **Hizmet İsteğini Görüntüle** tablosuna **Önem Derecesi** ve **Kapalı Tarih** olmak üzere 2 yeni alan ekledik.

:::image type="content" source="../media/SuppInsight-date-sev.PNG" alt-text="Ekran görüntüsü: Önem derecesine ve tarihe göre destek bileti sıralamasını gösteren tablo.":::

<a href="https://go.microsoft.com/fwlink/p/?linkid=2166757" target="_blank">Microsoft 365 yönetim merkezi'da</a> bu güncelleştirmeleri gözden geçirin. Sol gezinti bölmesinde **Destek** > **Görünümü Hizmeti istekleri'ne** gidin.

## <a name="june-2021"></a>Haziran 2021

### <a name="microsoft-365-admin-center-search"></a>Microsoft 365 yönetim merkezi arama

Arama işlevine birkaç yeni kategori ekledik.

- Artık genel arama'da Microsoft 365 yönetici rollerini arayabilir ve herhangi bir sayfadan rol atamalarını hızlı bir şekilde görüntüleyebilir ve yönetebilirsiniz. Örneğin, **Intune yöneticisini** arayın.

- Artık genel arama aracılığıyla basitleştirilmiş kurulum deneyimlerini bulabilirsiniz. Bu, sizin ve ekibinizin yeni özellikleri kullanmaya hızlı bir şekilde başlamanıza yardımcı olabilir. Örneğin, **parolayı süresi hiç dolmak üzere ayarlama** için arama.

Yönetim merkezinde arama hakkında daha fazla bilgi edinmek için Microsoft 365 yönetim merkezi arama [bölümüne](manage/search-in-the-mac.md) bakın.
