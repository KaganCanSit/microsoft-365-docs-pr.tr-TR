---
title: Microsoft 365 ile veri gizliliği düzenlemeleri için bilgi koruma dağıtma
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
description: Microsoft Teams, SharePoint ve e-posta da dahil olmak üzere GDPR ve California Tüketici Gizliliği Yasası (CCPA) gibi veri gizliliği düzenlemeleri için Microsoft 365 bilgi korumasını yapılandırın.
ms.openlocfilehash: ece8483773d3e2f5cdafe90bd93e11c52e2ba838
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939026"
---
# <a name="deploy-information-protection-for-data-privacy-regulations-with-microsoft-365"></a>Microsoft 365 ile veri gizliliği düzenlemeleri için bilgi koruma dağıtma

Kuruluşunuz hem şirket içinde hem de bulutta olmak üzere BT altyapınızda depolanan kişisel bilgileri korumanızı, yönetmenizi ve bunlar üzerinde hak ve denetim sağlamanızı gerektiren bölgesel veri gizliliği düzenlemelerine tabi olabilir. Veri gizliliği düzenlemesinin en iyi örneği, Avrupa Birliği Genel Veri Koruma Yönetmeliği'dir (GDPR). Veri gizliliği düzenlemelerine uyulmaması önemli para cezalarına neden olabilir.

Microsoft 365'daki veri türlerine örnek olarak Microsoft Teams sohbet oturumları, Exchange e-postalar ve SharePoint ile OneDrive'deki dosyalar verilebilir. Bu çözüm, riskleri değerlendirme ve Microsoft 365 kişisel verileri korumak için uygun eylemleri gerçekleştirme konusunda rehberlik sağlar. Bu, veri gizliliği olaylarını koruyabilmeniz, yönetebilmeniz ve yanıt verebilmeniz için kişisel bilgileri tanımlamayı içerir.

![Veri gizliliği düzenlemeleri için bilgi koruması nedir?](../media/information-protection-deploy/information-protection-data-privacy-regulations-overview.png#lightbox)

Veri gizliliği gereksinimleriniz için Microsoft 365 kimlik, cihaz ve tehdit koruma denetimlerinin kullanımı hakkında ek bilgiler de sağlanır.

Dağıtım işlemine genel bir bakış için bu videoyu izleyin.
<br>
<br>
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4NHCQ]

Bu Microsoft 365 özellikleri ve özellikleri, bilgileri korumaya yönelik ölçütleri karşılamanıza yardımcı olur.

| Yetenek veya özellik | Açıklama | Lisanslama |
|:-------|:-----|:-------|
| Uyumluluk Yöneticisi | Mevzuat uyumluluğu etkinliklerini yönetin, geçerli uyumluluk yapılandırmanızın genel puanını alın ve iyileştirme önerileri bulun. Bu, Microsoft Purview uyumluluk portalındaki iş akışı tabanlı bir risk değerlendirme aracıdır. | Microsoft 365 E3 ve E5 |
| Office 365 için Microsoft Defender | Microsoft 365 uygulamalarınızı ve e-posta iletileri, Office belgeleri ve işbirliği araçları gibi verilerinizi saldırılara karşı koruyun. | Microsoft 365 E3 ve E5 |
| Duyarlılık etiketleri | Kullanıcıların üretkenliğini ve işbirliği yapma becerilerini engellemeden kuruluşunuzun verilerini sınıflandırın ve koruyun. E-postaya, dosyalara veya sitelere çeşitli koruma düzeylerine sahip etiketler yerleştirin. | Microsoft 365 E3 ve E5 |
| Veri Kaybı Koruması (DLP) | Hem şirket içinde hem de dışarıdan kişisel bilgiler içeren verilerin riskli, yanlışlıkla veya uygunsuz bir şekilde paylaşılması algılayın, uyarın ve engelleyin. | Microsoft 365 E3 ve E5 |
| Veri saklama etiketleri ve ilkeleri | Bilgi idaresi denetimleri uygulayın. Bunlar, verilerinizin (müşterilerle ilgili kişisel veriler gibi) kuruluşunuzun ilkelerine veya veri düzenlemelerine uyması için ne kadar süre tutulabileceğini belirlemeyi içerebilir. | Microsoft 365 E3 ve E5 |
| E-posta şifreleme | Kuruluşunuzun içindeki ve dışındaki kişiler arasında şifreli e-posta iletileri göndererek ve alarak kişisel verileri koruyun. | Microsoft 365 E3 ve E5 |
||||

## <a name="organization-of-the-guidance-in-this-solution"></a>Bu çözümdeki kılavuzun düzenlenmesi

Gizlilikle ilgili bir veya daha fazla düzenlemeyi karşılamanıza yardımcı olacak Microsoft 365 araçlarını anlamanıza yardımcı olmak için bu kılavuz bölümler halinde düzenlenmiştir.

![Veri gizliliği düzenlemeleri için bilgi koruma uygulama adımları.](../media/information-protection-deploy/information-protection-data-privacy-regulations-steps.png)

Bu bölümlerin her biri, bu çözümdeki ayrı bir makaleye karşılık gelir.

> [!NOTE]
> Veri gizliliği yükümlülüklerinizi zaten biliyorsanız ve mevcut bir plana göre yürütülüyorsanız Önleme, Koruma, Saklama ve Araştırma kılavuzuna odaklanmak isteyebilirsiniz.

> [!IMPORTANT]
> Bu kılavuzun izlenmesi, özellikle özelliklerin bağlamının dışında olan gerekli adım sayısını göz önünde bulundurarak sizi herhangi bir veri gizliliği düzenlemesiyle uyumlu hale getirmeyecektir. Uyumluluğunuzu sağlamaktan ve yasal ve uyumluluk ekiplerinize danışmaktan veya uyumluluk konusunda uzman üçüncü taraflardan rehberlik ve tavsiye almaktan sorumlusunuz.

## <a name="plan-assess-data-privacy-risks-and-identify-sensitive-items"></a>Plan: Veri gizliliği risklerini değerlendirme ve hassas öğeleri belirleme

Kuruluşunuzun tabi olduğu veri gizliliği düzenlemelerini ve risklerini değerlendirmek, Microsoft 365 özelliklerini yapılandırma da dahil olmak üzere iyileştirmeleri uygulamaya başlamadan önce atılması gereken önemli bir ilk adımdır. Bu çalışma, genel hazırlık değerlendirmesi veya kuruluşunuzun uyması gereken yasal denetimlere tabi olan belirli hassas bilgi türlerinin tanımlanmasını içerebilir.

Daha fazla bilgi için bkz [. Veri gizliliği risklerini değerlendirme ve hassas öğeleri tanımlama](information-protection-deploy-assess.md).

## <a name="track-run-risk-assessments-and-check-your-compliance-score"></a>İzleme: Risk değerlendirmeleri çalıştırma ve uyumluluk puanınızı denetleme

<a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalında</a> bulunan Uyumluluk Yöneticisi, geliştirme eylemlerini ve sizin için geçerli olan birden çok veri gizliliği düzenlemesiyle ilgili olanları izlemenizi ve yönetmenizi sağlayan yerleşik bir özellik sunar.

Her düzenlemeye özgü yerleşik değerlendirme şablonlarını kullanabilir, burada seçilen her değerlendirme şablonu için eylem öğelerini izleyebilir, ayrıca belirli mevzuat denetimlerini görüntüleyebilir ve bunları belirli eylemlerle ilişkilendirebilirsiniz.

Daha fazla bilgi için bkz [. Geliştirme eylemlerini yönetmek için Uyumluluk Yöneticisi'ni kullanma](information-protection-deploy-compliance.md).

## <a name="prevent-protect-personal-data"></a>Engelle: Kişisel verileri koruma

Microsoft 365, veri gizliliği mevzuat uyumluluğuna uymaya yardımcı olmak için kullanabileceğiniz kimlik, cihaz ve tehdit koruma özellikleri sağlar.

Daha fazla bilgi için bkz. [Veri gizliliği düzenlemesi için kimlik, cihaz ve tehdit koruma](information-protection-deploy-identity-device-threat.md) kullanma.

Bu makalede, veri gizliliği düzenlemelerinin bu alanlarda genel olarak nelere çağrıldığı kısaca açıklanır ve uygulama gereksinimlerini karşılamanıza yardımcı olacak daha fazla bilgi için bağlantılar içeren ilgili Microsoft 365 çözümlerinin bir listesi sağlanır.

## <a name="protect-information-subject-to-data-privacy-regulation"></a>Veri gizliliği düzenlemesine tabi bilgileri koruma

Veri gizliliği düzenlemeleri, GDPR, California Tüketici Koruma Yasası (CCPA), HIPAA-HITECH (Birleşik Devletler sağlık hizmetleri gizlilik yasası) ve Brezilya Veri Koruma Yasası (LGPD) örnek kümemizdeki dört veri gizliliği düzenlemesinde bilgileri korumaya yönelik 40'tan fazla denetim de dahil olmak üzere, ortamınızda kullanılabilecek bir dizi kişisel bilgi koruma denetimi belirler.

Daha fazla bilgi için bkz [. Kuruluşunuzdaki veri gizliliği düzenlemesine tabi bilgileri koruma](information-protection-deploy-protect-information.md).

Bu makalede, kuruluşunuzda veri gizliliğine yönelik bilgi koruma gereksinimlerini karşılamak için kullanılabilecek ana denetim şemaları ele alınıyor.

## <a name="retain-govern-information-subject-to-data-privacy-regulation"></a>Saklama: Veri gizliliği düzenlemesine tabi bilgileri idare etme

Veri gizliliği düzenlemeleri, GDPR, CCPA, HIPAA-HITECH ve LGPD örnek kümemizdeki dört veri gizliliği düzenlemesinde 24'ten fazla denetim de dahil olmak üzere ortamınızda kullanılabilecek kişisel bilgi idare denetimleri için çağrıda bulunur.

Daha fazla bilgi için bkz. [Kuruluşunuzdaki veri gizliliği düzenlemesine tabi olan bilgileri yönetme](information-protection-deploy-govern.md).

Veri gizliliği düzenlemeleri, bilgi idareleriyle&mdash; ilgili belirsiz olabilir, ancak bu makalenin silinmesi ve arşivlenmesi&mdash;, kuruluşunuzda veri gizliliği için adres bilgileri idaresi gereksinimlerini kullanabileceğiniz birincil denetim şemalarını düzenler.

## <a name="investigate-monitor-investigate-and-respond-to-data-privacy-incidents"></a>Araştırma: Veri gizliliği olaylarını izleme, araştırma ve yanıtlama

kuruluşunuzdaki veri gizliliği olaylarını izlemenize, araştırmanıza ve yanıtlamanıza yardımcı olacak Microsoft 365 özellik vardır.

Bu özelliklerin kullanımına yönelik süreçlere, yordamlara ve diğer belgelere sahip olmak, düzenleyici kurumlara uyumluluğu göstermek için önemli olabilir.

Daha fazla bilgi için bkz. [Kuruluşunuzdaki veri gizliliği olaylarını izleme ve yanıtlama](information-protection-deploy-monitor-respond.md).

## <a name="training-for-administrators"></a>Yöneticiler için eğitim

Microsoft Learn'den alınan bu eğitim modülleri, bilgi koruması için önemli olan özellikleri öğrenmenize yardımcı olabilir.


#### <a name="information-protection"></a>Bilgi koruması

|Eğitim:|Kurumsal bilgileri Microsoft 365 ile koruma|
|:---|:---|
|![Teams bilgi koruma eğitimi simgesi.](../media/protect-enterprise-information-microsoft-365.svg)|Kuruluşunuzun bilgilerini korumak ve güvenliğini sağlamak her zamankinden daha zordur. Kurumsal bilgileri Microsoft 365 ile koruma öğrenme yolu, hassas bilgilerinizi yanlışlıkla aşırı paylaşıma veya kötüye kullanmaya karşı korumayı, verileri bulmayı ve sınıflandırmayı, duyarlılık etiketleriyle korumayı ve kaybına karşı koruma sağlamak için hassas bilgilerinizi hem izleme hem de analiz etme konularını açıklar. Bu öğrenme yolu, Microsoft 365 Sertifikalı: Güvenlik Yöneticisi İş Ortağı ve Microsoft 365 Sertifikalı: Enterprise Yönetim Uzmanı sertifikaları için hazırlanmanıza yardımcı olabilir.<br><br>1 sa - Learning Yolu - 5 Modül|

> [!div class="nextstepaction"]
> [Başlangıç >](/learn/modules/m365-security-info-overview/introduction/)

#### <a name="identity-and-access"></a>Kimlik ve erişim

|Eğitim:|Azure Active Directory ile kimliği ve erişimi koruma|
|:---|:---|
|![Kimlik ve erişim eğitimi simgesi.](../media/protect-identity-and-access-with-microsoft-365.svg)|Kimlik ve Erişim öğrenme yolu, en son kimlik ve erişim teknolojilerini, kimlik doğrulamasını güçlendirmeye yönelik araçları ve kuruluşunuzdaki kimlik korumasına yönelik yönergeleri kapsar. Microsoft erişim ve kimlik teknolojileri, ister şirket içinde ister bulutta olsun kuruluşunuzun kimliğinin güvenliğini sağlamanızı ve kullanıcılarınızın herhangi bir konumdan güvenli bir şekilde çalışmasını sağlamanızı sağlar. Bu öğrenme yolu, Microsoft 365 Sertifikalı: Güvenlik Yöneticisi İş Ortağı ve Microsoft 365 Sertifikalı: Enterprise Yönetim Uzmanı sertifikalarına hazırlanmanıza yardımcı olabilir.<br><br>2 sa 52 dk - Learning Yolu - 6 Modül|

> [!div class="nextstepaction"]
> [Başlangıç >](/learn/modules/m365-identity-overview/introduction/)