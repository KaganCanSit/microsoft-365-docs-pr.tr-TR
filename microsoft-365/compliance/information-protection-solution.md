---
title: Microsoft Purview ile bilgi koruma çözümü dağıtma
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ms.collection:
- m365solution-overview
- m365solution-mip
- m365initiative-compliance
description: Kuruluşunuz için Microsoft Purview Bilgi Koruması dağıtmaya yönelik açıklayıcı kılavuz.
ms.openlocfilehash: 3b62cf6165447288275a7a8c02a64ab27b41d607
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635271"
---
# <a name="deploy-an-information-protection-solution-with-microsoft-purview"></a>Microsoft Purview ile bilgi koruma çözümü dağıtma

>*[Microsoft 365 Güvenlik & Uyumluluğu için Lisanslama](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Bilgi koruma stratejiniz iş gereksinimlerinize göre oluşturulur. Birçok kuruluş düzenlemelere, yasalara ve iş uygulamalarına uymalıdır. Ayrıca kuruluşların belirli projelere ait veriler gibi özel bilgileri de koruması gerekir.

Microsoft Purview Bilgi Koruması (eski adıyla Microsoft Bilgi Koruması), belirli iş hedeflerinizi gerçekleştirmek için kullanabileceğiniz bir çerçeve, süreç ve özellikler sağlar. 

## <a name="microsoft-purview-information-protection-framework"></a>Microsoft Purview Bilgi Koruması çerçevesi

Microsoft Purview Bilgi Koruması kullanarak hassas bilgileri nerede yaşarsa yaşasın, nereye giderse gitsin keşfetmenize, sınıflandırmanıza, korumanıza ve yönetmenize yardımcı olun.

![Microsoft Purview Bilgi Koruması çözümüne genel bakış](../media/mip-solution-overview-extended.png)

Bu özelliklerin birbirini nasıl desteklediğini ve birbirleri üzerinde nasıl derlediğini görmek için aşağıdaki Ignite oturumunu izleyin: [verilerinizi bilin, verilerinizi koruyun ve Microsoft Bilgi Koruması ile veri kaybını önleyin](https://myignite.microsoft.com/archives/IG20-OD273).

Veri idaresi için bkz. [Microsoft Purview ile veri idaresi çözümü dağıtma](data-governance-solution.md).

## <a name="licensing"></a>Lisanslama

Microsoft Purview Bilgi Koruması özellikleri Microsoft Purview'a dahildir. Lisanslama gereksinimleri, yapılandırma seçeneklerine bağlı olarak özellikler içinde bile farklılık gösterebilir. Lisanslama gereksinimlerini ve seçeneklerini belirlemek [için bkz. Güvenlik & uyumluluğu için Microsoft 365 kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="know-your-data"></a>Verileriniz hakkında bilgi edinme

![Microsoft Purview Bilgi Koruması çözüme genel bakış için verilerinizi öğrenme](../media/knowyourdata-mipsolution.png)

Hassas verilerinizin nerede olduğunu bilmek çoğu kuruluş için en büyük zorluktır. Microsoft Purview Bilgi Koruması veri sınıflandırması, kuruluşunuzun oluşturduğu her geçen gün artan miktarda veriyi keşfetmenize ve doğru bir şekilde sınıflandırmanıza yardımcı olur. Grafik gösterimler, bu verileri korumak ve yönetmek için ilkeler ayarlayıp izleyebilmek için bu verilere ilişkin içgörüler elde etmenize yardımcı olur.


|Adım|Açıklama|Daha fazla bilgi|
|:---|:----------|:---------------|
|1| Korumak istediğiniz hassas bilgi kategorilerini açıklayın. <br /><br /> Kuruluşunuz için en değerli olan ve olmayan bilgi türleri hakkında zaten bir fikriniz var. Başlangıç noktanız olan bu kategorileri açıklamak için paydaşlarla birlikte çalışın. | [Hassas bilgi türleri hakkında daha fazla bilgi edinme](sensitive-information-type-learn-about.md) <p> [Eğitilebilir sınıflandırıcılar hakkında daha fazla bilgi edinme](classifier-learn-about.md)|
|2| Hassas verileri bulma ve sınıflandırma. <br /><br /> Öğelerdeki hassas veriler, varsayılan DLP ilkeleri, kullanıcılar tarafından el ile etiketleme ve hassas bilgi türleri veya makine öğrenmesi kullanılarak otomatik desen tanıma gibi birçok farklı yöntem kullanılarak bulunabilir. | [Veri sınıflandırması hakkında daha fazla bilgi edinme](data-classification-overview.md) <p> [Video: Uyumluluk merkezinde veri sınıflandırması](https://www.microsoft.com/videoplayer/embed/RE4vx8x)|
|3| Hassas öğelerinizi görüntüleyin.  <br /><br /> Hassas öğelerin ve kullanıcıların bu öğeler üzerinde yaptığı eylemlerin daha ayrıntılı bir analizi için içerik gezginini ve etkinlik gezginini kullanın.| [İçerik gezginini kullanmaya başlama](data-classification-content-explorer.md) <p> [Etkinlik gezginini kullanmaya başlama](data-classification-activity-explorer.md)|

## <a name="protect-your-data"></a>Verilerinizi koruma

![Microsoft Purview Bilgi Koruması çözüme genel bakış için verilerinizi koruma](../media/protect-mipsolution.png)

Hassas verilerinizi daha verimli bir şekilde korumanıza yardımcı olmak için hassas verilerinizin bulunduğu yeri bilme bilgilerini kullanın. Ancak beklemenize gerek yoktur; verilerinizi el ile, varsayılan ve otomatik etiketlemenin bir bileşimiyle hemen korumaya başlayabilirsiniz. Ardından, hangi öğelerin etiketlendiğini ve etiketlerinizin nasıl kullanıldığını onaylamak için önceki bölümde yer alan [içerik gezginini](data-classification-content-explorer.md) ve [etkinlik gezginini](data-classification-activity-explorer.md) kullanın.

|Adım|Açıklama|Daha fazla bilgi|
|:---|-----------|:---------------|
| 1|Kuruluşunuzun verilerini koruyacak [duyarlılık etiketlerinizi](sensitivity-labels.md) ve ilkelerinizi tanımlayın. <br /><br />Bu etiketler, içeriğin duyarlılığını tanımlamanın yanı sıra üst bilgiler, alt bilgiler, filigranlar ve şifreleme gibi koruma eylemleri de uygulayabilir. | [Hassasiyet etiketlerini kullanmaya başlama](get-started-with-sensitivity-labels.md) <br /><br /> [Duyarlılık etiketleri ve ilkeleri oluşturma ve yapılandırma](create-sensitivity-labels.md) <br /><br /> [Şifreleme uygulamak için hassasiyet etiketleri kullanarak içeriğe erişimi kısıtlama](encryption-sensitivity-labels.md) |
| 2|Microsoft 365 uygulamaları ve hizmetleri için öğeleri etiketleyip koruyun. <br /><br />Duyarlılık etiketleri Microsoft 365 Word, Excel, PowerPoint, Outlook ve SharePoint ve OneDrive siteleri ile Microsoft 365 gruplarını içeren kapsayıcılar için desteklenir. El ile etiketleme, otomatik etiketleme, varsayılan etiket ve zorunlu etiketleme gibi etiketleme yöntemlerinin bir bileşimini kullanın.| [Office uygulamalarında duyarlılık etiketlerini yönetme](sensitivity-labels-office-apps.md) <br /><br /> [SharePoint ve OneDrive'daki Office dosyaları için hassasiyet etiketlerini etkinleştirme](sensitivity-labels-sharepoint-onedrive-files.md) <br /><br /> [Duyarlılık etiketleriyle şifrelenmiş dosyalar için birlikte yazmayı etkinleştirme](sensitivity-labels-coauthoring.md) <br /><br /> [İçeriğe otomatik olarak bir hassasiyet etiketi uygulama](apply-sensitivity-label-automatically.md) <br /><br /> [Microsoft Teams, Microsoft 365 grupları ve SharePoint siteleriyle duyarlılık etiketlerini kullanma](sensitivity-labels-teams-groups-sites.md) <br /><br /> [SharePoint ve OneDrive'da siteler ve belgeler için varsayılan paylaşım bağlantısını ayarlamak için duyarlılık etiketlerini kullanma](sensitivity-labels-default-sharing-link.md) <br /><br /> [Microsoft SharePoint Syntex'da modele duyarlılık etiketi uygulama](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model) <br /><br /> [Power BI'da duyarlılık etiketleri](/power-bi/admin/service-security-sensitivity-label-overview) |
|3|Duyarlılık etiketlerinizle [Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security) kullanarak buluttaki veri depolarında bulunan hassas öğeleri keşfedin, etiketleyin ve koruyun.| [Bulutta depolanan düzenlenmiş ve hassas verileri bulma, sınıflandırma, etiketleme ve koruma](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|4|[Azure Information Protection birleşik etiketleme tarayıcısını](/azure/information-protection/deploy-aip-scanner) duyarlılık etiketlerinizle dağıtarak şirket içindeki veri depolarında bulunan hassas öğeleri keşfedin, etiketleyin ve koruyun.| [Azure Information Protection birleşik etiketleme tarayıcısını yapılandırma ve yükleme](/azure/information-protection/deploy-aip-scanner-configure-install)|
|5|Azure Blob Depolama, Azure dosyaları, Azure Data Lake Storage 1. Nesil ve [Azure Data Lake Storage](/azure/purview/overview) öğelerini bulmak ve etiketlemek için Microsoft Purview Veri Eşlemesi kullanarak duyarlılık etiketlerinizi Azure'a genişletin 12. Nesil. | [Microsoft Purview Veri Eşlemesi'de etiketleme](/azure/purview/create-sensitivity-label)|

Duyarlılık etiketlerini iş kolu uygulamalarına veya üçüncü taraf SaaS uygulamalarına genişletmek isteyen bir geliştiriciyseniz bkz. [Microsoft Bilgi Koruması (MIP) SDK kurulumu ve yapılandırması](/information-protection/develop/setup-configure-mip). 

### <a name="additional-protection-capabilities"></a>Ek koruma özellikleri

Microsoft Purview, verilerin korunmasına yardımcı olacak ek özellikler içerir. Her müşterinin bu özelliklere ihtiyacı olmaz ve bazılarının yerini daha yeni sürümler alabilir.

Koruma özelliklerinin tam listesi için [Verilerinizi Microsoft Purview ile koruyun](information-protection.md) sayfasını kullanın.

## <a name="prevent-data-loss"></a>Veri kaybını önleme

![Microsoft Purview Bilgi Koruması çözümü için veri kaybını önlemeye genel bakış](../media/dlp-mipsolution.png)

Uygulamalar ve hizmetler arasında hassas verilerin uygunsuz şekilde paylaşılmasını, aktarılmasını veya kullanılmasını engellemek için Microsoft Purview Veri Kaybı Önleme (DLP) ilkelerini dağıtın. Bu ilkeler kullanıcıların hassas verileri kullanırken doğru kararları almasına ve doğru eylemleri gerçekleştirmesine yardımcı olur.

|Adım|Açıklama|Daha fazla bilgi|
|:---|:----------|:---------------|
|1|DLP hakkında bilgi edinin. <br /><br /> Kuruluşların denetimi altında finansal veriler, özel veriler, kredi kartı numaraları, sağlık kayıtları veya sosyal güvenlik numaraları gibi hassas bilgiler bulunur. Bu hassas verilerin korunmasına ve riskin azaltılmasına yardımcı olmak için, kullanıcılarının bunları sahip olmaması gereken kişilerle uygunsuz bir şekilde paylaşmasını önlemek için bir yönteme ihtiyaçları vardır. Bu uygulamaya veri kaybı önleme (DLP) adı verilir.| [Veri kaybı önleme hakkında daha fazla bilgi edinme](dlp-learn-about-dlp.md)|
|2|DLP uygulamanızı planlayın. <br /><br /> Her kuruluşun iş gereksinimleri, hedefleri, kaynakları ve durumu kendilerine özel olduğundan, her kuruluş veri kaybı önlemeyi (DLP) farklı şekilde planlar ve uygular. Ancak, tüm başarılı DLP uygulamaları için ortak olan öğeler vardır. | [Veri kaybı önleme planı](dlp-overview-plan-for-dlp.md)|
|3|Bir DLP ilkesi tasarlayıp oluşturun. <br /><br /> Veri kaybı önleme (DLP) ilkesi oluşturmak hızlı ve kolaydır, ancak çok fazla ayarlama yapmanız gerekiyorsa istenen sonuçları elde etmek için bir ilke almak zaman alabilir. İlkeyi uygulamadan önce tasarlamaya zaman ayırarak, yalnızca deneme ve hataya göre ayarlamaya kıyasla istediğiniz sonuçlara daha hızlı ve daha az istenmeyen sorunla ulaşabilirsiniz.| [Bir DLP ilkesi tasarlama](dlp-policy-design.md) <p> [DLP ilkesi başvurusu](dlp-policy-reference.md) <p>[Bir DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md)|
|4|DLP ilkelerinizi ayarlayın. <br /><br /> Bir DLP ilkesini dağıttığınızda amaçlanan amaca ne kadar uygun olduğunu göreceksiniz. Daha iyi performans için ilke ayarlarınızı ayarlamak için bu bilgileri kullanın. | [Bir DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md)|


## <a name="training-resources"></a>Eğitim kaynakları

Danışmanlar ve yöneticiler için öğrenme modülleri:

- [Microsoft Purview'da bilgi koruma ve veri yaşam döngüsü yönetimine giriş](/learn/modules/m365-compliance-information-governance)
- [Verileri koruma ve idare için sınıflandırma](/learn/modules/m365-compliance-information-classify-data)
- [Microsoft Purview'da bilgileri koruma](/learn/modules/m365-compliance-information-protect-information)
- [Microsoft Purview'da veri kaybını önleme](/learn/modules/m365-compliance-information-prevent-data-loss)

Kullanıcılarınızı kendileri için yapılandırdığınız duyarlılık etiketlerini uygulama ve kullanma konusunda eğitmeye yardımcı olmak için [duyarlılık etiketleri için son kullanıcı belgelerine](get-started-with-sensitivity-labels.md#end-user-documentation-for-sensitivity-labels) bakın.

Teams için veri kaybı önleme ilkelerini dağıttığınızda, bu teknolojiye giriş olarak aşağıdaki son kullanıcı kılavuzunu, görebileceği bazı olası iletilerle yararlı bulabilirsiniz: [Veri kaybını önleme (DLP) ve iletişim uyumluluk ilkeleriyle ilgili Teams iletileri ](https://support.microsoft.com/office/teams-messages-about-data-loss-prevention-dlp-and-communication-compliance-policies-c5631c3f-f61b-4306-a6ac-6603d9fc5ff0).
