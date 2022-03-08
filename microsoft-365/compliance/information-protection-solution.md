---
title: Microsoft Bilgi Koruması çözümü dağıtma
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
description: (MIP) Microsoft Bilgi Koruması dağıtımı için ön simge kılavuzu.
ms.openlocfilehash: d70f7356909b0aa0ec663a641e1bc76926db72f0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328195"
---
# <a name="deploy-a-microsoft-information-protection-solution"></a>Microsoft Bilgi Koruması çözümü dağıtma

>*[Güvenlik ve Uyumluluk Microsoft 365 lisansı &.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Bilgi koruma stratejiniz iş ihtiyaçlarına göre yönlendirildi. Birçok kuruluş yasal düzenlemelere, yasalara ve iş uygulamalarına uymalıdır. Ayrıca, kuruluşların belirli projeler için veriler gibi özel mülkiyet bilgilerini de korumaları gerekir.

Microsoft Bilgi Koruması (MIP), belirli iş amaçlarınıza yönelik olarak kullanabileceğiniz bir çerçeve, süreç ve özellikler sağlar. 

## <a name="microsoft-information-protection-framework"></a>Microsoft Bilgi Koruması çerçevesi

Gizli Microsoft Bilgi Koruması içinde yer alan veya seyahat her yerde bu bilgileri bu şekilde sınıflandırmanıza, korumanıza ve yönetmeye yardımcı olması için bu bilgileri kullanın.

![MIP çözümüne genel bakış](../media/mip-solution-overview-extended.png)

Bu becerilerin birbirine nasıl destek olduğunu ve birbirlerini nasıl geliştireceklerini görmek için aşağıdaki Ignite oturumunu izleyin: Verilerinizi koruyun, verilerinizi koruyun ve iş yerleriyle birlikte veri [Microsoft Bilgi Koruması](https://myignite.microsoft.com/archives/IG20-OD273).

Verilerinizi yönetme hakkında bilgi için bkz. [Microsoft 365'te Microsoft Bilgi Microsoft 365](manage-Information-governance.md).

## <a name="licensing"></a>Lisanslama

MIP özellikleri, Uyumluluk Uyumluluğu Microsoft 365 dahil edilir. Lisans gereksinimleri, yapılandırma seçeneklerine bağlı olarak özellikler arasında bile değişiklik gösterebilir. Lisans gereksinimlerini ve seçeneklerini belirlemek için, güvenlik [Microsoft 365 uyumluluğuyla ilgili en iyi & bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="know-your-data"></a>Verilerinizi bilebilirsiniz

![MIP çözümü için verilerinizi genel bakış](../media/knowyourdata-mipsolution.png)

Hassas verilerinizin nerede olduğunu bilmek çoğu kuruluş için çoğunlukla en büyük zorlukdur. MIP veri sınıflandırması, kurumda oluşturduğu sürekli artan miktarda verileri keşfetmenize ve doğru şekilde sınıflandırmanıza yardımcı olur. Grafiksel gösterimler, bu verilere yönelik öngörüler kazanmanıza yardımcı olur ve böylelikle ilkeleri korumak ve yönetmek için ilkeler oluşturabilir ve izleyebilirsiniz.


|Adım|Açıklama|Daha fazla bilgi|
|:---|:----------|:---------------|
|1| Korumak istediğiniz hassas bilgi kategorilerini açıkların. <br /><br /> Hangi tür bilgilerin, sizin için en değerli olduğu ve hangi tür bilgilerin değerli olmadığını zaten biliyor siniz. Bu kategorileri açıklamak için proje katılımcıları ile birlikte çalışma çünkü burada sizin başlangıç yeriniz vardır. | [Hassas bilgi türleri hakkında bilgi](sensitive-information-type-learn-about.md) <p> [Eğitilebilir sınıflayıcılar hakkında bilgi](classifier-learn-about.md)|
|2| Hassas verileri keşfedin ve sınıflandırin. <br /><br /> Öğelerdeki hassas veriler, varsayılan DLP ilkelerini, kullanıcılar tarafından el ile etiketlemeyi ve hassas bilgi türlerini veya makine öğrenimini kullanan otomatik desen tanımayı içeren birçok farklı yöntem kullanılarak bulunabilir. | [Veri sınıflandırması hakkında bilgi](data-classification-overview.md) <p> [Video: Uyumluluk merkezinde veri sınıflandırması](https://www.microsoft.com/videoplayer/embed/RE4vx8x)|
|3| Hassas öğelerinizi görüntüleme.  <br /><br /> Hassas öğelerle kullanıcıların bu öğeler üzerinde daha derin çözümlemeler yapmak için içerik gezginini ve etkinlik gezginini kullanın.| [İçerik gezginiyle çalışmaya başlama](data-classification-content-explorer.md) <p> [Etkinlik gezginiyle çalışmaya başlama](data-classification-activity-explorer.md)|

## <a name="protect-your-data"></a>Verilerinizi koruyun

![MIP çözümü için verilerinizi korumaya genel bakış](../media/protect-mipsolution.png)

Daha verimli bir şekilde korumanıza yardımcı olmak için, hassas verilerinizin nerede olduğunu bilmek için bilgileri kullanın. Ama beklemenize gerek yok; el ile, varsayılan ve otomatik etiketlemenin bir bileşimiyle verilerinizi anında korumaya başlayabilirsiniz. Ardından önceki [bölümde yer alan](data-classification-content-explorer.md) [içerik gezginini](data-classification-activity-explorer.md) ve etkinlik gezginini kullanarak hangi öğelerin etiketlenmiş olduğunu ve etiketlerinizin nasıl kullanılıyor olduğunu onaylayın.

|Adım|Açıklama|Daha fazla bilgi|
|:---|-----------|:---------------|
| 1|Duyarlılık [etiketlerinizi ve](sensitivity-labels.md) ilkelerinizi tanımlayarak kurum verilerinizi koruyun. <br /><br />Bu etiketler, içeriğin duyarlılığını tanımlamaya ek olarak üst bilgiler, alt bilgiler, filigranlar ve şifreleme gibi koruma eylemleri de uygulayabilir. | [Duyarlılık etiketleriyle çalışmaya başlama](get-started-with-sensitivity-labels.md) <br /><br /> [Duyarlılık etiketlerini ve onların ilkelerini oluşturma ve yapılandırma](create-sensitivity-labels.md) <br /><br /> [Şifreleme uygulamak için duyarlılık etiketlerini kullanarak içeriğe erişimi kısıtlama](encryption-sensitivity-labels.md) |
| 2|Daha fazla uygulama ve Microsoft 365 için öğeleri etiketle ve koruyun. <br /><br />Duyarlılık etiketleri Word, Microsoft 365, Excel, PowerPoint, Outlook siteleri ve SharePoint OneDrive içeren kapsayıcılar ve Microsoft 365 destekler. El ile etiketleme, otomatik etiketleme, varsayılan etiket ve zorunlu etiketleme gibi etiket yöntemlerinin bir bileşimini kullanın.| [Office uygulamalarında duyarlılık etiketlerini yönetme](sensitivity-labels-office-apps.md) <br /><br /> [SharePoint ve Office dosyaları için duyarlılık OneDrive](sensitivity-labels-sharepoint-onedrive-files.md) <br /><br /> [Duyarlılık etiketleriyle şifrelenmiş dosyalar için birlikte yazma özelliği etkinleştirme](sensitivity-labels-coauthoring.md) <br /><br /> [Otomatik olarak içeriğe duyarlılık etiketi uygulama](apply-sensitivity-label-automatically.md) <br /><br /> [Site oluşturma, Microsoft Teams grupları Microsoft 365 duyarlılık SharePoint kullanma](sensitivity-labels-teams-groups-sites.md) <br /><br /> [Site ve site ve belgeleriniz için varsayılan paylaşım bağlantısını ayarlamak üzere duyarlılık SharePoint OneDrive](sensitivity-labels-default-sharing-link.md) <br /><br /> [Microsoft SharePoint Syntex'da bir modele duyarlılık SharePoint Syntex](/microsoft-365/contentunderstanding/apply-a-sensitivity-label-to-a-model) <br /><br /> [Power BI'de duyarlılık etiketleri](/power-bi/admin/service-security-sensitivity-label-overview) |
|3|Duyarlılık etiketleriniz ile Bulut Uygulamaları için [Microsoft Defender'ı](/cloud-app-security/what-is-cloud-app-security) kullanarak buluttaki veri depolarında bulunan hassas öğeleri keşfedin, etiket edin ve koruyun.| [Bulutta depolanan düzenlemeye tabi ve hassas verileri keşfetme, sınıflandırma, etiketleme ve koruma](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)|
|4|[Azure Information Protection](/azure/information-protection/deploy-aip-scanner) birleştirilmiş etiket tarayıcısını duyarlılık etiketlerinize dağıtarak, şirket içinde bulunan veri depolarında bulunan hassas öğeleri keşfedin, etiket edin ve koruyun.| [Azure Information Protection birleşik etiketleme tarayıcısını yapılandırma ve yükleme](/azure/information-protection/deploy-aip-scanner-configure-install)|
|5|Azure Blob Depolama, Azure dosyaları, Azure Data Lake Depolama Gen1 ve Azure Data Lake ürünlerine yönelik öğeleri keşfetmek ve etiketlemek için Azure [Purview](/azure/purview/overview) kullanarak duyarlılık etiketlerinizi Azure'Depolama genişletme. | [Azure Purview'da etiketleme](/azure/purview/create-sensitivity-label)|

Duyarlılık etiketlerini iş hattı uygulamalarına veya üçüncü taraf SaaS uygulamalarına genişletmek isteyen bir geliştiriciyseniz bkz. [Microsoft Bilgi Koruması SDK kurulumu ve yapılandırması](/information-protection/develop/setup-configure-mip). 

### <a name="additional-protection-capabilities"></a>Ek koruma özellikleri

Microsoft 365 korunmasına yardımcı olmak için ek özellikler içerir. Her müşterinin bu özelliklere ihtiyacı olmaz ve bazıları daha yeni sürümlerden biraz daha fazla şey tarafından edinebilirsiniz.

Koruma [Microsoft Bilgi Koruması tam Microsoft 365](information-protection.md) için sayfa içinde sayfa içinde bu sayfayı kullanın.

## <a name="prevent-data-loss"></a>Veri kaybını önleme

![MIP çözümü için veri kaybını önlemeye genel bakış](../media/dlp-mipsolution.png)

Hassas verilerin uygulamalar ve hizmetler arasında uygunsuz paylaşımını, aktarımını veya kullanımını engellemek için veri kaybı önleme (DLP) ilkelerini dağıtın. Bu ilkeler, kullanıcıların hassas verileri kullanırken doğru kararlar almalarına ve doğru eylemleri yapmalarına yardımcı olur.

|Adım|Açıklama|Daha fazla bilgi|
|:---|:----------|:---------------|
|1|DLP hakkında bilgi edinmek için: <br /><br /> Kuruluşların denetimi altında mali veriler, özel veriler, kredi kartı numaraları, sağlık kayıtları veya sosyal güvenlik numaraları gibi hassas bilgiler vardır. Bu hassas verilerin korunmasına ve riskin azaltılmasına yardımcı olmak için, kullanıcılarının bu verileri uygunsuz bir şekilde kullanmaması gereken kullanıcılarla paylaşmasını önlemenin bir yolu gerekir. Bu uygulama, veri kaybını önleme (DLP) olarak adlandırılan uygulamadır.| [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)|
|2|DLP uygulamanızı planla. <br /><br /> Her kuruluşun iş ihtiyaçları, hedefleri, kaynakları ve durumu benzersiz olduğundan her kuruluş veri kaybı önleme (DLP) önlemeyi (DLP) farklı şekilde planlar ve uygulayamaz. Bununla birlikte, tüm başarılı DLP uygulamaları için ortak olan öğeler vardır. | [Veri kaybını önlemeyi planlama](dlp-overview-plan-for-dlp.md)|
|3|DLP ilkesi tasarlar ve oluşturun. <br /><br /> Veri kaybını önleme (DLP) ilkesi oluşturmak hızlı ve kolaydır, ancak hedeflenen sonuçları almak için bir ilke almak çok fazla ayar yapmak zorundaysanız zaman alıcı olabilir. Bir ilkeyi uygulamaya başlamadan önce tasarlamaya zaman gerek bırakmanız, sizi istenen sonuçlara daha hızlı bir şekilde ve tek başına deneme ve hatayla ayarlamaya göre daha az sayıda ve daha az istenmiş soruna neden olur.| [DLP ilkesi tasarlama](dlp-policy-design.md) <p> [DLP ilkesi başvurusu](dlp-policy-reference.md) <p>[DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md)|
|4|DLP ilkelerinizi ayarlama. <br /><br /> DLP ilkesi dağıttırdikten sonra, ilkenin amaçlanan amaca ne kadar uygun olduğunu yakında göreceğiz. Daha iyi bir performans için ilke ayarlarınızı değiştirmek üzere bu bilgileri kullanın. | [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md)|


## <a name="training-resources"></a>Eğitim kaynakları

Learning ve yöneticiler için diğer modüller:

- [E-Microsoft 365'de bilgi korumasına ve yönetimine Microsoft 365](/learn/modules/m365-compliance-information-governance)
- [Verileri koruma ve yönetim için sınıflandırma](/learn/modules/m365-compliance-information-classify-data)
- [Web'de bilgileri Microsoft 365](/learn/modules/m365-compliance-information-protect-information)
- [Çalışmalarda veri kaybını Microsoft 365](/learn/modules/m365-compliance-information-prevent-data-loss)

Kullanıcılarınızı, bu etiketler için yapılandırılan duyarlılık etiketlerini uygulama ve kullanma konusunda eğitmek için bkz. [Duyarlılık etiketleri için son kullanıcı belgeleri](get-started-with-sensitivity-labels.md#end-user-documentation-for-sensitivity-labels).

Teams için veri kaybı önleme ilkelerini dağıtırken, bu teknolojiye giriş olarak aşağıdaki son kullanıcı kılavuzunda, bu teknolojiye giriş olarak yararlı bulabilir ve bu iletilerin göreceği olası bazı iletileri bulabilirsiniz: veri kaybı önleme [(DLP) ](https://support.microsoft.com/office/teams-messages-about-data-loss-prevention-dlp-and-communication-compliance-policies-c5631c3f-f61b-4306-a6ac-6603d9fc5ff0)ve iletişim uyumluluk ilkeleri hakkında Teams iletileri .
