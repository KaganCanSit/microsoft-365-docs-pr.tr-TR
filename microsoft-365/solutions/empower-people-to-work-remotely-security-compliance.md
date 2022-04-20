---
title: '3. Adım: Karma çalışanlar için güvenlik ve uyumluluk dağıtma'
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
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
description: Karma çalışanlara yönelik uygulamalarınızı, verilerinizi ve cihazlarınızı korumak için Microsoft 365 güvenlik ve uyumluluk hizmetlerini kullanın.
ms.openlocfilehash: 08771de0f9e833405da308fb645b5fb5c906c543
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64937795"
---
# <a name="step-3-deploy-security-and-compliance-for-hybrid-workers"></a>3. Adım: Karma çalışanlar için güvenlik ve uyumluluk dağıtma

Bazıları hiç ofise gitmeyen veya seyrek giden hibrit çalışanlar için güvenlik ve uyumluluk, genel çözümün önemli bir parçasıdır. Tüm iletişimleri bir kuruluş intraneti ile sınırlandırılmak yerine İnternet üzerinden gerçekleşir.

Siz ve çalışanlarınızın siber güvenlik riskini azaltarak iç politikalarınıza ve veri düzenlemelerinize uyumluluğu sürdürürken üretken kalmak için yapabileceğiniz şeyler vardır.

Uzaktan çalışma için şu güvenlik ve uyumluluk öğeleri gerekir:

- Hibrit çalışanlarının kullandığı üretkenlik uygulamalarına denetimli erişim, örneğin Microsoft Teams
- Karma çalışanların oluşturduğu ve kullandığı sohbet konuşmaları veya paylaşılan dosyalar gibi verilere denetimli erişim ve verilerin korunması
- Windows 11 veya 10 cihazın kötü amaçlı yazılımlara ve diğer siber saldırı türlerine karşı korunması
- Duyarlılık ve koruma düzeyleri için tutarlı etiketleme ile e-postanın, dosyaların ve sitenin korunması
- Sızdırılan bilgilerin önlenmesi
- Bölgesel veri düzenlemelerine bağlı kalma

Karma çalışanlar için güvenlik ve uyumluluk hizmetleri sağlayan Microsoft 365 özellikleri aşağıdadır.

:::image type="content" source="../media/empower-people-to-work-remotely/remote-workers-security-compliance-grid.png" alt-text="Güvenli ve uyumlu kalmak için bu Microsoft 365 hizmetlerini kullanın" lightbox="../media/empower-people-to-work-remotely/remote-workers-security-compliance-grid.png":::

## <a name="security"></a>Güvenlik

Uygulamalarınızı ve verilerinizi bu Microsoft 365 güvenlik özellikleriyle koruyun.

|Yetenek veya özellik|Neden ihtiyacım var?|Lisanslama|
|---|---|---|
|Office 365 için Microsoft Defender|Microsoft 365 uygulamalarınızı ve e-posta iletileri, Office belgeleri ve işbirliği araçları gibi verilerinizi saldırılara karşı koruyun. <p> Office 365 için Microsoft Defender, güvenlik risklerini algılamak, araştırmak ve düzeltmek için uygulamalarınızdan gelen sinyalleri toplar ve analiz eder ve kuruluşunuzu e-posta iletileri, bağlantılar (URL' ler) ve işbirliği araçlarının oluşturduğu kötü amaçlı tehditlere karşı korur. Ayrıca standart ve katı güvenlik duruşları için otomatik kiracı yapılandırma değerlendirmesi ve yapılandırma araçları sağlar.|Microsoft 365 E3 veya E5|
|Kötü amaçlı yazılımdan koruma|Microsoft Defender Virüsten Koruma ve Device Guard, cihaz tabanlı kötü amaçlı yazılım koruması sağlar. <p> SharePoint Online, bilinen kötü amaçlı yazılımlar için dosya yüklemelerini otomatik olarak tarar. <p> Exchange Online Protection (EOP), bulut posta kutularının güvenliğini sağlar.|Microsoft 365 E3 veya E5|
|Uç Nokta için Microsoft Defender|Kuruluşunuzun cihazlarını siber tehditlere ve veri ihlallerine karşı koruyun ve gelişmiş tehditleri algılayın, araştırın ve yanıtlayın.|Microsoft 365 E5|
|Bulut Uygulamaları için Defender|Bulut tabanlı hizmetlerinizi (hem Microsoft 365 hem de diğer SaaS uygulamaları) saldırılara karşı koruyun.|Microsoft 365 E5 veya tek tek Bulut için Defender Uygulamaları lisansları|
|Azure AD Kimlik Koruması|Kimlik tabanlı risklerin algılanması ve düzeltilmesi için otomatikleştirme. <p>Riskli oturum açma işlemleri için çok faktörlü kimlik doğrulaması (MFA) gerektirmek için risk tabanlı Koşullu Erişim ilkeleri oluşturun.|Azure AD Premium P2 lisansları olan Microsoft 365 E5 veya E3|
||||

İlk adım [, Microsoft Güvenli Puanı](/microsoft-365/security/defender/microsoft-secure-score) hakkında bilgi edinmek ve kullanmak olmalıdır.

Daha fazla bilgi için bkz. [Güvenlik ekiplerinin evden çalışmayı desteklemesi için en iyi 12 görev](../security/top-security-tasks-for-remote-work.md) .

Microsoft 365 genelinde güvenlik hakkında bilgi için [Microsoft 365 güvenlik belgelerine bakın](/microsoft-365/security).

## <a name="compliance"></a>Uyumluluk

Microsoft 365 bu uyumluluk özellikleriyle iç ilkelere veya mevzuat gereksinimlerine uyun.

|Yetenek veya özellik|Neden ihtiyacım var?|Lisanslama|
|---|---|---|
|Duyarlılık etiketleri|E-postaya, dosyalara veya sitelere çeşitli koruma düzeylerine sahip etiketler yerleştirerek kullanıcıların üretkenliğini ve işbirliği yapma becerilerini engellemeden kuruluşunuzun verilerini sınıflandırın ve koruyun.|Microsoft 365 E3 veya E5|
|Veri Kaybı Koruması (DLP)|Hem şirket içinde hem de dışarıdan kişisel bilgiler içeren verilerin paylaşılması gibi riskli, yanlışlıkla veya uygunsuz paylaşımları algılayın, uyarın ve engelleyin.|Microsoft 365 E3 veya E5|
|Koşullu Erişim Uygulama Denetimi|Hassas verilerin kullanıcıların kişisel cihazlarına indirilmesini önleyin.|Microsoft 365 E3 veya E5|
|Veri saklama etiketleri ve ilkeleri|Kuruluşunuzun ilkelerine veya veri düzenlemelerine uymak için, müşteriler üzerinde kişisel verilerin depolanmasıyla ilgili verilerin ve gereksinimlerin ne kadar süreyle tutulacakları gibi bilgi idare denetimlerini uygulayın.|Microsoft 365 E3 veya E5|
|Microsoft Purview İleti Şifrelemesi|Kuruluşunuzun içindeki ve dışındaki kişiler arasında müşterilerle ilgili kişisel veriler gibi düzenlenmiş veriler içeren şifrelenmiş e-posta iletileri gönderin ve alın.|Microsoft 365 E3 veya E5|
|Uyumluluk Yöneticisi|Microsoft Hizmet Güveni Portalı'ndaki bu iş akışı tabanlı risk değerlendirme aracıyla Microsoft bulut hizmetleriyle ilgili mevzuat uyumluluğu etkinliklerini yönetin.|Microsoft 365 E3 veya E5|
|Uyumluluk Yöneticisi|Microsoft Purview uyumluluk portalında geçerli uyumluluk yapılandırmanızın genel puanını ve iyileştirmeye yönelik önerileri inceleyin.|Microsoft 365 E3 veya E5|
|İletişim Uyumluluğu|Kuruluşunuzdaki uygunsuz iletileri algılama, yakalama ve düzeltme eylemleri gerçekleştirme.|Uyumluluk veya Insider Risk Yönetimi eklentileriyle Microsoft 365 E5 veya Microsoft 365 E3|
|Insider Risk Management|Kuruluşunuzdaki kötü amaçlı ve yanlışlıkla riskleri algılayın, araştırın ve harekete geçin. Microsoft 365, çalışan yönetilmeyen bir cihaz kullanırken bile bu tür riskleri algılayabilir.|Uyumluluk veya Insider Risk Yönetimi eklentileriyle Microsoft 365 E5 veya Microsoft 365 E3|
||||

Daha fazla bilgi için bkz. [Microsoft Purview'u kullanmaya başlamak için hızlı görevler](../compliance/compliance-quick-tasks.md) .

## <a name="results-of-step-3"></a>3. Adımın Sonuçları

Hibrit çalışanlarınız için şunları uyguladınız:

- Güvenlik
  - Karma çalışanların iletişim kurmak ve işbirliği yapmak için kullandığı uygulamalara ve verilere denetimli erişim
  - Bulut hizmeti verileri, e-posta ve Windows 11 veya 10 cihaz için kötü amaçlı yazılım koruması
- Uyumluluk
  - Duyarlılık ve koruma düzeyleri için tutarlı etiketleme
  - Bilgi sızıntısını önleme ilkeleri
  - Bölgesel veri düzenlemelerine bağlı kalma

## <a name="next-step"></a>Sonraki adım

[![4. Adım: Cihazlarınızı, bilgisayarlarınızı ve diğer uç noktalarınızı yönetin.](../media/empower-people-to-work-remotely/remote-workers-step-grid-4.png)](empower-people-to-work-remotely-manage-endpoints.md)

Cihazlarınızı, bilgisayarlarınızı ve diğer uç noktaları yönetmek için [4. Adımla](empower-people-to-work-remotely-manage-endpoints.md) devam edin.
