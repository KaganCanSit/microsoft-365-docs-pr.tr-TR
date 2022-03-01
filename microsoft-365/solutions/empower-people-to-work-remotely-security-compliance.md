---
title: '3. Adım: Karma çalışanlar için güvenlik ve uyumluluğu dağıtma'
f1.keywords:
- NOCSH
author: JoeDavies-MSFT
ms.author: josephd
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- m365solution-remotework
- m365solution-scenario
ms.custom: ''
description: Karma Microsoft 365 için uygulamalarınızı, verilerinizi ve cihazlarınızı korumak üzere güvenlik ve uyumluluk hizmetlerini kullanın.
ms.openlocfilehash: 7c898a1ef588ce8eee553490eaa8f5dd452df9e0
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2022
ms.locfileid: "63015347"
---
# <a name="step-3-deploy-security-and-compliance-for-hybrid-workers"></a>3. Adım: Karma çalışanlar için güvenlik ve uyumluluğu dağıtma

Karma çalışanların bazıları ofise hiç gitmeyen veya seyrek olarak gelenler için güvenlik ve uyumluluk, genel çözümün önemli bir bölümüdür. İletişimlerinin tüm iletişimi, bir kuruluş intranet'iyle sınırlı değildir ve İnternet üzerinden  gerçekleşir.

Siz ve çalışanlarınız, siber güvenlik riskini azaltarak ve iç ilkelerinize ve veri düzenlemelerine uyumluluğu koruyarak üretken kalmak için bazı şeyler sürdürebilirsiniz.

Uzaktan çalışma için şu güvenlik ve uyumluluk öğeleri gerekir:

- Örneğin, karma çalışanların kullanabileceği üretkenlik uygulamalarına, örneğin Microsoft Teams
- Sohbet konuşmaları veya paylaşılan dosyalar gibi karma çalışanların oluşturması ve kullanması gereken verilere denetimli erişim ve koruma
- 11 Windows 10 cihazı kötü amaçlı yazılıma ve diğer siber saldırıların türüne karşı koruma
- Duyarlılık ve koruma düzeyleri için tutarlı bir etiketleme ile e-posta, dosya ve sitenin koruması
- Sızdırılmış bilgilerin engellenmesi
- Bölgesel veri düzenlemelerine bağlı kalın

Karma çalışanlar için güvenlik Microsoft 365 uyumluluk hizmetleri sağlayan güvenlik ve uyumluluk hizmetlerinin özellikleri şunlardır.

:::image type="content" source="../media/empower-people-to-work-remotely/remote-workers-security-compliance-grid.png" alt-text="Güvenli Microsoft 365 uyumlu kalmak için bu hizmetlerden kullanın" lightbox="../media/empower-people-to-work-remotely/remote-workers-security-compliance-grid.png":::

## <a name="security"></a>Güvenlik

Uygulamalarınızı ve verilerinizi bu güvenlik özellikleriyle Microsoft 365.

|Özellik veya özellik|Neden gerekiyor?|Lisanslama|
|---|---|---|
|Office 365 için Microsoft Defender|E Microsoft 365 iletileri, belgeler ve işbirliği araçları gibi Office ve işbirliği araçlarınızı saldırıya karşı koruyun. <p> Office 365 için Microsoft Defender, güvenlik risklerini algılamak, soruşturmak ve düzeltme amacıyla uygulamalardan sinyaller toplar ve analiz eder ve e-posta iletileri, bağlantılar (URL'ler) ve işbirliği araçları tarafından tehditlere karşı organizasyonlarınızı korur. Ayrıca, standart ve sıkı güvenlik açıkları için otomatik kiracı yapılandırma değerlendirme ve yapılandırma aracı sağlar.|Microsoft 365 E3 E5|
|Kötü amaçlı yazılıma karşı koruma|Microsoft Defender Virüsten Koruma ve Device Guard cihaz tabanlı kötü amaçlı yazılım koruması sağlar. <p> SharePoint Online, bilinen kötü amaçlı yazılım için dosya karşıya yüklemelerini otomatik olarak tarar. <p> Exchange Online Protection (EOP) bulut posta kutularının güvenliğini sağlar.|Microsoft 365 E3 E5|
|Uç Nokta için Microsoft Defender|Kuruluş cihazlarınız siber tehditlere ve veri ihlallerine karşı koruma sağlar, gelişmiş tehditleri algılar, araştırarak ve yanıtlar.|Microsoft 365 E5|
|Bulut Uygulamaları için Defender|Hem iş hem de diğer SaaS Microsoft 365 bulut tabanlı hizmetlerinizi saldırıya karşı koruyun.|Microsoft 365 E5 uygulamaları için Defender lisansları veya tek bir lisans|
|Azure AD Identity Protection|Kimlik tabanlı riskleri algılamayı ve düzeltmeyi otomatikleştirin. <p>Riskli oturum açmalarda çok faktörlü kimlik doğrulaması (MFA) gerektirecek şekilde risk tabanlı Koşullu Erişim ilkeleri oluşturun.|Microsoft 365 E5 lisansları olan E3 Azure AD Premium P2 E3|
||||

İlk adım, Microsoft Güvenli Puanı'nın nasıl olduğunu ve nasıl [kullanıla olduğunu öğrenmektir](/microsoft-365/security/defender/microsoft-secure-score).

Daha [fazla bilgi için bkz. Güvenlik ekiplerinin evden çalışmayı desteklemesi için en önemli 12](../security/top-security-tasks-for-remote-work.md) görev.

Farklı güvenlik bilgileri için Microsoft 365 için bkz[. Microsoft 365 belgeleme](/microsoft-365/security).

## <a name="compliance"></a>Uyumluluk

Bu uyumluluk özellikleri ile şirket içi ilkelere ve mevzuat gereksinimlerine Microsoft 365.

|Özellik veya özellik|Neden gerekiyor?|Lisanslama|
|---|---|---|
|Duyarlılık etiketleri|E-posta, dosyalar veya sitelere çeşitli koruma düzeylerine sahip etiketler yerleştirerek, kullanıcıların üretkenliğini ve birlikte çalışma yeteneğini engellemeden, kuruluş verilerinizi sınıflandırarak ve koruyabilirsiniz.|Microsoft 365 E3 E5|
|Veri Kaybına Karşı Koruma (DLP)|Kişisel bilgi içeren verilerin hem şirket içinde hem de dışında paylaşımı gibi riskli, istemeden veya uygunsuz paylaşımı algıla, uyarma ve engelleme.|Microsoft 365 E3 E5|
|Koşullu Erişim Uygulama Denetimi|Hassas verilerin kullanıcıların kişisel cihazlarına indirilmiş olmasını önle.|Microsoft 365 E3 E5|
|Veri bekletme etiketleri ve ilkeleri|Verilerinizin ve gereksinimlerinin müşteriler üzerinde kişisel verilerin depolanmasında ne kadar süreyle tutulacakları gibi, bilgilerinizin yönetimiyle ilgili denetimleri, kurum ilkelerine veya veri düzenlemelerine uygun şekilde uygulama.|Microsoft 365 E3 E5|
|Office şifreleme (OME)|Kuruluş içinde ve dışında, düzenlemeye tabi veriler (müşterilere kişisel veriler gibi) içeren kişiler arasında şifrelenmiş e-posta iletileri gönderin ve alın.|Microsoft 365 E3 E5|
|Uyumluluk Yöneticisi|Microsoft Hizmet Güveni Portalı'nın bu iş akışı tabanlı risk değerlendirme aracıyla Microsoft bulut hizmetleriyle ilgili düzenlemelere uyumluluk etkinliklerini yönetin.|Microsoft 365 E3 E5|
|Uyumluluk Yöneticisi|Geçerli uyumluluk yapılandırmanız hakkında genel bir puana ve genel uyumluluk yapılandırmasının iyileştirilmesine yönelik önerilere Microsoft 365 uyumluluk merkezi.|Microsoft 365 E3 E5|
|İletişim Uyumluluğu|İletileri algılama, yakalama ve kuruluşta uygunsuz iletiler için düzeltme eylemleri gerçekleştirin.|Microsoft 365 E5 veya Microsoft 365 E3 Insider Risk Yönetimi eklentilerini güvenlik ya da güvenlikle ilgili olarak değerlendirme|
|Insider Risk Yönetimi|Kuruluşta kötü amaçlı ve yanlışlıkla riski algılayan, araştıran ve bu risklere karşı eylemde bulundurarak. Microsoft 365, yöneticisi olmayan bir cihaz kullanıyor olsa bile bu tür riskleri algılanabilir.|Microsoft 365 E5 veya Microsoft 365 E3 Insider Risk Yönetimi eklentilerini güvenlik ya da güvenlikle ilgili olarak değerlendirme|
||||

Daha [fazla bilgi için bkz. Uyumluluk Microsoft 365 hızlı](../compliance/compliance-quick-tasks.md) görevler.

## <a name="results-of-step-3"></a>Adım 3'in sonuçları

Karma çalışanlarınız için uygulamasına sahipsiniz:

- Güvenlik
  - Karma çalışanların iletişim kurmak ve işbirliği yapmak için kullanabileceği uygulamalara ve verilere denetimli erişim
  - 11 veya 10 cihaz için bulut hizmeti verileri, e-Windows kötü amaçlı yazılım koruması
- Uyumluluk
  - Duyarlılık ve koruma düzeyleri için tutarlı etiketleme
  - Bilgi sızıntısını önleme ilkeleri
  - Bölgesel veri düzenlemelerine bağlı kalın

## <a name="next-step"></a>Sonraki adım

[![4. Adım: Cihazlarınızı, pc'lerinizi ve diğer uç noktaları yönetin.](../media/empower-people-to-work-remotely/remote-workers-step-grid-4.png)](empower-people-to-work-remotely-manage-endpoints.md)

Cihazlarınızı [, bilgisayarlarınızı](empower-people-to-work-remotely-manage-endpoints.md) ve diğer uç noktaları yönetmek için 4. Adımdan devam edin.
