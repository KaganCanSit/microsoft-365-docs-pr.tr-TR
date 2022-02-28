---
title: Gizlilik uygulamalarıyla veri gizliliği düzenlemelerine uygun bilgi Microsoft 365
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/22/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-overview
ms.custom: admindeeplinkCOMPLIANCE
description: MICROSOFT TEAMS, Microsoft 365 SharePoint ve e-posta da içinde olmak üzere GDPR ve California Tüketici Gizliliği Yasası (CCPA) gibi veri gizliliği düzenlemelerine yönelik Microsoft Teams korumayı yapılandırabilirsiniz.
ms.openlocfilehash: 92314529cf6ca3ec318b181eb367bab81b9b81a0
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990599"
---
# <a name="deploy-information-protection-for-data-privacy-regulations-with-microsoft-365"></a>Gizlilik uygulamalarıyla veri gizliliği düzenlemelerine uygun bilgi Microsoft 365

Organizasyonunız, hem şirket içi hem de bulutta olmak üzere, IT altyapıda depolanan kişisel bilgileri korumanızı, yönetmenizi ve bu bilgiler üzerinde denetim sağlamanızı gerektiren bölgesel veri gizliliği düzenlemelerine tabi olabilir. Veri gizlilik yönetmeliğinin en iyi örneği, Avrupa Birliği Genel Veri Koruma Yönetmeliğidir (GDPR). Veri gizliliği düzenlemelerine uyulmamalıdır ve önemli ölçüde ince bilgiler ortaya çıkan olabilir.

Bu çalışma sayfalarındaki veri türlerine örnek olarak Microsoft 365'da sohbet oturumları, Microsoft Teams Exchange'te e Exchange ve SharePoint dosyaları OneDrive. Bu çözüm, risk değerlendirmesi ve kişisel verileri aynı ağ ağlarında korumak için uygun önlemlerin nasıl Microsoft 365. Bu, veri gizliliği olaylarını korumak, yönetmek ve yanıtlamak için kişisel bilgilerin belirlenmesini içerir.

![Veri gizliliği düzenlemelerine ilişkin bilgi koruması nedir?](../media/information-protection-deploy/information-protection-data-privacy-regulations-overview.png#lightbox)

Ayrıca, veri gizliliğinize yönelik kimlik, Microsoft 365 ve tehdit koruması denetimlerinin kullanımı hakkında ek bilgiler de sağlanır.

Dağıtım sürecine genel bir bakış için bu videoyu izleyin.
<br>
<br>
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4NHCQ]

Bu Microsoft 365 özellikleri ve özellikleri, bilgileri koruma ölçütlerine karşılamanıza yardımcı olur.

| Özellik veya özellik | Açıklama | Lisanslama |
|:-------|:-----|:-------|
| Uyumluluk Yöneticisi | Mevzuat uyumluluğu etkinliklerini yönetin, geçerli uyumluluk yapılandırmanız hakkında genel bir puan elde edin ve iyileştirme önerileri bulun. Bu, çalışma sayfalarındaki iş akışı tabanlı bir risk değerlendirme Microsoft 365 uyumluluk merkezi. | Microsoft 365 E3 ve E5 |
| Office 365 için Microsoft Defender | E Microsoft 365 iletileri, belgeler ve işbirliği araçları gibi Office ve işbirliği araçlarınızı saldırıya karşı koruyun. | Microsoft 365 E3 ve E5 |
| Duyarlılık etiketleri | Kullanıcıların üretkenliğini ve işbirliği yapma becerisini engellemeden, organizasyon verilerinizi sınıflandırarak ve koruyabilirsiniz. E-postaya, dosyalara veya sitelere çeşitli koruma düzeyleri içeren etiketler yer alın. | Microsoft 365 E3 ve E5 |
| Veri Kaybına Karşı Koruma (DLP) | Kişisel bilgileri içeren verilerin hem şirket içinde hem de dışında riskli, istemeden veya uygunsuz paylaşımı algıla, uyarma ve engelleme. | Microsoft 365 E3 ve E5 |
| Veri bekletme etiketleri ve ilkeleri | Bilgi yönetimi denetimlerini uygulama. Bunlar, verilerinizin (müşterilerle ilgili kişisel veriler gibi) ne kadar süreyle tutularak kuruluş ilkelerine ve veri düzenlemelerine uygun tutula tutula güncel olduğunu belirlemeyi içerebilir. | Microsoft 365 E3 ve E5 |
| E-posta şifreleme | Kuruluş içindeki ve dışındaki kişiler arasında şifreli e-posta iletileri göndererek ve alarak kişisel verilerinizi koruyun. | Microsoft 365 E3 ve E5 |
||||

## <a name="organization-of-the-guidance-in-this-solution"></a>Bu çözümde yol gösterici kuruluşun

Gizlilikle ilgili bir Microsoft 365 karşılamanıza yardımcı olacak en iyi araçları anlamanıza yardımcı olmak için, bu kılavuz bölümler halinde düzenlenmiştir.

![Veri gizliliği düzenlemeleri için bilgi korumayı uygulama adımları.](../media/information-protection-deploy/information-protection-data-privacy-regulations-steps.png)

Bu bölümlerden her biri bu çözümde ayrı bir makaleye karşılık karşılık almaktadır.

> [!NOTE]
> Veri gizliliği yükümlülüklerinizi zaten biliyorsanız ve var olan bir plan üzerinde yürütmeye devam ediyorsanız, Engelle, Koru, Koru, Ve Araştır kılavuzuna odaklanmanız iyi olabilir.

> [!IMPORTANT]
> Bu kılavuzun ardından, özellikle özellikler bağlamı dışında gerekli adımların sayısı dikkate alınarak, herhangi bir veri gizlilik düzenlemesi ile uyumlu hale gelmezsiniz. Uyumluluk sağlanmasından ve yasal ve uyumluluk ekiplerinize danışmak ya da uyumluluk konusunda özelleştirilmiş üçüncü tarafların yol gösterici ve tavsiyelerini almak sizin sorumluluğundadır.

## <a name="plan-assess-data-privacy-risks-and-identify-sensitive-items"></a>Plan: Veri gizlilik risklerini değerlendirme ve hassas öğeleri belirleme

Verilerinizin tabi olduğu veri gizliliği düzenlemelerini ve risklerini değerlendirmek, bu düzenlemelere yönelik özellikleri yapılandırma da dahil olmak üzere iyileştirmeleri uygulamaya başlamadan önce at gereken temel Microsoft 365. Bu çalışma, bir bütün olarak hazırlık değerlendirmesini veya düzenleme denetimlerine tabi olan belirli hassas bilgi türlerinin tanımlanmasını içerebilir. Buna uyulmalıdır.

Daha fazla bilgi için bkz [. Veri gizliliği risklerini değerlendirme ve hassas öğeleri belirleme](information-protection-deploy-assess.md).

## <a name="track-run-risk-assessments-and-check-your-compliance-score"></a>Takip et: Risk değerlendirmeleri çalıştırın ve uyumluluk puanınızı kontrol edin

<a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a> Uyumluluk Yöneticisi, size genel olarak iyileştirme eylemlerini ve size uygun birden çok veri gizliliği düzenlemesi ile ilgili geliştirme eylemlerini izleme ve yönetmeye yönelik yerleşik bir yetenek sağlar.

Seçilen her değerlendirme şablonu için eylem öğelerini takip etmek, belirli mevzuat denetimlerini görüntülemek ve bunları belirli eylemlerle ilişkilendirmek üzere, her düzenlemeye özgü yerleşik değerlendirme şablonlarını kullanabilirsiniz.

Daha fazla bilgi için bkz [. Geliştirme eylemlerini yönetmek için Uyumluluk Yöneticisi'ni kullanma](information-protection-deploy-compliance.md).

## <a name="prevent-protect-personal-data"></a>Engelleme: Kişisel verileri koruma

Microsoft 365 gizlilik düzenleme uyumluluğuna uyumlu olmak için kullanabileceğiniz kimlik, cihaz ve tehdit koruması özellikleri sağlar.

Daha fazla bilgi için bkz [. Veri gizliliği düzenlemesi için kimlik, cihaz ve tehdit koruması kullanma](information-protection-deploy-identity-device-threat.md).

Bu makalede, veri gizliliği düzenlemelerinin bu alanlarda genel olarak neleri araylarıları kısaca açıklanmıştır ve ilgili Microsoft 365 çözümlerinin bir listesini sunar ve uygulama gereksinimleriyle ilgili olarak size yardımcı olacak ek bilgilerin bağlantılarını içerir.

## <a name="protect-information-subject-to-data-privacy-regulation"></a>Veri gizliliği düzenlemeye tabi bilgileri koruma

Veri gizliliği yönetmelikleri, örnek GDPR, California Tüketici Koruma Yasası (CCPA), HIPAA-HITECH (ABD sağlık hizmetleri gizlilik yasası) ve Brezilya Veri Koruma Yasası (LGPD) örnek kümemizde yer alan dörtten fazla veri gizliliği düzenlemesinde yer alan bilgileri korumak için 40'dan fazla denetim dahil olmak üzere ortamınıza dahil olmak üzere bir dizi kişisel bilgi koruma denetimi dikte eder.

Daha fazla bilgi için bkz [. Bilgileri, kurumda veri gizlilik düzenlemesi konularını konu alan koruma](information-protection-deploy-protect-information.md).

Bu makalede, kurumda veri gizliliği için bilgi koruma  ihtiyaçlarını karşılamak üzere kullanılmaktadır.

## <a name="retain-govern-information-subject-to-data-privacy-regulation"></a>Koruma: Veri gizlilik yönetmeliğine tabi bilgileri yönetme

Veri gizliliği düzenlemeleri, örnek GDPR, CCPA, HIPAA-HITECH ve LGPD kümemizde yer alan dört veri gizliliği düzenlemesinde yer alan 24'den fazla denetim dahil olmak üzere ortamınıza dahil olmak üzere kişisel bilgi idaresi denetimleri arar.

Daha fazla bilgi için bkz [. Kuruluşlarınız için veri gizlilik düzenlemesi konularını yönetme](information-protection-deploy-govern.md).

&mdash;&mdash;Veri gizliliği düzenlemeleri, bilgi idaresi ile ilgili belirsiz belirsiz olabilir, ancak bu makaleyi silmek ve arşivlemek, kurum içinde veri gizliliği için bilgi idaresi gereksinimlerine uygun olarak kullanabileceğiniz birincil denetim düzenlerini hazırlar.

## <a name="investigate-monitor-investigate-and-respond-to-data-privacy-incidents"></a>Araştır: Veri gizlilik olaylarını izleme, araştırma ve yanıtlama

İlişkili Microsoft 365 faaliyete ettiyken, kuruluşta veri gizliliği olaylarını izlemenize, araştırmanıza ve yanıtlamanıza yardımcı olacak birçok özellik vardır.

Bu özellikleri kullanmaya ilişkin süreçlere, yordamlara ve diğer belgelere sahip olmak, mevzuat gövdelerine uyumluluğu göstermek açısından önemli olabilir.

Daha fazla bilgi için bkz [. Kurumda veri gizliliği olaylarını izleme ve yanıtlama](information-protection-deploy-monitor-respond.md).

## <a name="training-for-administrators"></a>Yöneticiler için eğitim

Microsoft Learn'den alınan bu eğitim modülleri, bilgi koruması için önemli olan özellikleri öğrenmeniz için size yardımcı olabilir.


#### <a name="information-protection"></a>Bilgi koruması

|Eğitim:|Kurumsal bilgileri iş yerleriyle Microsoft 365|
|:---|:---|
|![Teams koruma eğitimi simgesini seçin.](../media/protect-enterprise-information-microsoft-365.svg)|Kuruluş bilgilerini korumak ve güvenliğini sağlamak her zaman olduğu kadar zor olabilir. Microsoft 365 ile kurumsal bilgileri koruma yolu, hassas verilerinizi yanlışlıkla yanlış şekilde ortaya çıkarma veya yanlış kullanımlara karşı koruma, verileri keşfetme ve sınıflandırma, duyarlılık etiketleriyle koruma ve hassas bilgilerini hem izleme hem de çözümleme konularını ele almaktadır. Bu öğrenme yolu, Destek Sertifikalı: Güvenlik Microsoft 365 İş ortağı ve güvenlik Microsoft 365: Enterprise Sertifikalarını hazırlamanıza yardımcı olabilir.<br><br>1 sa - Learning Yolu - 5 Modül|

> [!div class="nextstepaction"]
> [Başlangıç >](/learn/modules/m365-security-info-overview/introduction/)

#### <a name="identity-and-access"></a>Kimlik ve erişim

|Eğitim:|Kimlik ve erişimi diğer Azure Active Directory|
|:---|:---|
|![Kimlik ve erişim eğitimi simgesi.](../media/protect-identity-and-access-with-microsoft-365.svg)|Identity ve Access öğrenme yolu en son kimlik ve erişim teknolojilerini, kimlik doğrulamayı güçlendirme araçlarını ve kuruluş içinde kimlik koruması konusunda yol gösterici bilgileri kapsar. Microsoft erişim ve kimlik teknolojileri, ister şirket içinde ister bulutta olsun, kuruluş kimliğinizin güvenliğini sağlamanızı ve kullanıcılarınızı herhangi bir konumdan güvenli bir şekilde çalışmalarını sağlamanızı sağlar. Bu öğrenme yolu, Eğitim Sertifikalı: Güvenlik Microsoft 365 İş ortağı ve eğitim Microsoft 365: Enterprise Uzman sertifikalarına hazırlanmanıza yardımcı olabilir.<br><br>2 sa 52 dak . Learning Yol - 6 Modüller|

> [!div class="nextstepaction"]
> [Başlangıç >](/learn/modules/m365-identity-overview/introduction/)