---
title: Microsoft Purview içeriden risk çözümleri
description: Microsoft Purview'da insider risk çözümleriyle kuruluşunuzda riski en aza indirmeye nasıl yardımcı olduğunuzu öğrenin.
keywords: Microsoft 365, Microsoft Purview, insider riskleri, uyumluluk, insider risk yönetimi, iletişim uyumluluğu, bilgi engelleri, ayrıcalıklı erişim yönetimi
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
- m365solution-overview
ms.openlocfilehash: 523aaf14d7eaecf1d69fd24587287aa4c9b89933
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628759"
---
# <a name="microsoft-purview-insider-risk-solutions"></a>Microsoft Purview içeriden risk çözümleri

Insider riskleri, modern çalışma alanında güvenlik ve uyumluluk uzmanlarının en önemli endişelerinden biridir. Sektör çalışmaları, insider risklerinin genellikle belirli kullanıcı olayları veya etkinlikleriyle ilişkili olduğunu göstermiştir. Kuruluşunuzu bu risklere karşı korumak, tanımlanması ve azaltılması zor olabilir. Insider riskleri arasında çeşitli alanlardaki güvenlik açıkları yer alır ve kuruluşunuz için fikri mülkiyet kaybından iş yerinde tacize ve daha fazlasına kadar önemli sorunlara neden olabilir. Aşağıdaki şekilde, yaygın insider riskleri özetlenmiştir:

![Insider risk tehditleri.](../media/ir-solution-threats.png)

Microsoft 365 risk önleme özellikleri, insider risk ürünlerimizin ve çözümlerimizin tasarımı ve yerleşik özellikleridir. Bu çözümler birlikte çalışır ve risk etkinliğini hızla belirlemenize, önceliklendirmenize ve harekete geçirmenize yardımcı olmak için gelişmiş hizmet ve üçüncü taraf göstergelerini kullanır. Çoğu çözüm, veri analistlerinizin ve araştırmacılarınızın bu riskleri hızla harekete geçmek ve en aza indirmek için kullanması için kapsamlı bir algılama, uyarı ve düzeltme iş akışı sunar.

| Risk simgesi | Risk | İletişim uyumluluğu | İçeriden risk yönetimi | Bilgi bariyerleri | Ayrıcalıklı erişim yönetimi |
| :---- | :-------- | :--------------------------- | :-------------------------- |:-------------------------| :--------------------------------|
| ![Veri taşması simgesi.](../media/ir-risk-data-spillage.png)| Veri taşması | ![Destekleniyor](../media/check-mark.png) | ![Destekleniyor](../media/check-mark.png) |  |  |
| ![Gizlilik ihlalleri simgesi.](../media/ir-risk-confidentiality-violations.png)| Gizlilik ihlalleri | ![Destekleniyor](../media/check-mark.png) | ![Destekleniyor](../media/check-mark.png) | ![Destekleniyor](../media/check-mark.png) |  |
| ![IP hırsızlığı simgesi.](../media/ir-risk-ip-theft.png)| IP hırsızlığı | ![Destekleniyor](../media/check-mark.png) | ![Destekleniyor](../media/check-mark.png) | ![Destekleniyor](../media/check-mark.png) |  |
| ![İş yeri şiddet simgesi.](../media/ir-risk-workplace-violence.png)| İş yeri şiddet | ![Destekleniyor](../media/check-mark.png) |  |  |  |
| ![Sahtekarlık/hırsız simgesi.](../media/ir-risk-fraud.png)| Dolandırıcı -lık | ![Destekleniyor](../media/check-mark.png) | ![Destekleniyor](../media/check-mark.png) |  |  |
| ![İlke ihlalleri simgesi.](../media/ir-risk-policy-violations.png)| İlke ihlalleri | ![Destekleniyor](../media/check-mark.png) | ![Destekleniyor](../media/check-mark.png) | ![Destekleniyor](../media/check-mark.png) | ![Destekleniyor](../media/check-mark.png) |
| ![Insider trading/handshake icon.](../media/ir-risk-insider-trading.png)| Insider ticareti | ![Destekleniyor](../media/check-mark.png) |  |  |  |
| ![İlgi çakışmaları simgesi.](../media/ir-risk-conflicts-of-interest.png)| İlgi çakışmaları | ![Destekleniyor](../media/check-mark.png) |  | ![Destekleniyor](../media/check-mark.png) |  |
| ![Hassas veri sızıntıları/cihazlar simgesi.](../media/ir-risk-sensitive-data-leaks.png)| Hassas veri sızıntıları | ![Destekleniyor](../media/check-mark.png) | ![Destekleniyor](../media/check-mark.png) |  |  |
| ![İş yeri tacizi/kişiler simgesi.](../media/ir-risk-workplace-harassment.png)| İş yeri tacizi | ![Destekleniyor](../media/check-mark.png) |  |  |  |
| ![Güvenlik ihlalleri simgesi.](../media/ir-risk-security-violations.png)| Güvenlik ihlalleri |  | ![Destekleniyor](../media/check-mark.png) |  | ![Destekleniyor](../media/check-mark.png) |
| ![Mevzuat uyumluluğu ihlalleri simgesi.](../media/ir-risk-regulatory-compliance-violations.png)| Mevzuat uyumluluğu ihlalleri | ![Destekleniyor](../media/check-mark.png) | ![Destekleniyor](../media/check-mark.png) | ![Destekleniyor](../media/check-mark.png) |  |

## <a name="insider-risk-solutions"></a>İçeriden risk çözümleri

Kuruluşunuzun şirket içi risklere karşı korunmasına yardımcı olmak için bu Microsoft Purview özelliklerini ve özelliklerini kullanın.

### <a name="communication-compliance"></a>İletişim uyumluluğu

[Microsoft Purview İletişim Uyumluluğu](communication-compliance.md), kuruluşunuzdaki uygunsuz iletileri algılamanıza, yakalamanıza ve üzerinde işlem yapmanıza yardımcı olarak iletişim risklerini en aza indirmenize yardımcı olur.

İletişim uyumluluğu aşağıdaki aboneliklerde kullanılabilir:

- Microsoft 365 E5/A5/F5/G5 aboneliği (ücretli veya deneme sürümü)
- Microsoft 365 E3/A3/F3/G5 aboneliği + Microsoft 365 E5/A5/F5/G5 Uyumluluk eklentisi
- Microsoft 365 E3/A3/F3/G5 aboneliği + Microsoft 365 E5/A5/F5/G5 Insider Risk Management eklentisi
- Office 365 Kurumsal E5 aboneliği (ücretli veya deneme sürümü)
- Office 365 A5 aboneliği (ücretli veya deneme sürümü)
- Office 365 Kurumsal E3 aboneliği + Office 365 Gelişmiş Uyumluluk eklentisi (artık yeni aboneliklerde kullanılamaz, nota bakın)

### <a name="insider-risk-management"></a>İçeriden risk yönetimi

[Microsoft Purview İçeriden Risk Yönetimi](insider-risk-management.md), kuruluşunuzdaki kötü amaçlı ve yanlışlıkla etkinlikleri algılamanıza, araştırmanıza ve eyleme geçirmenize olanak tanıyarak iç riskleri en aza indirmenize yardımcı olur.

Insider risk yönetimi aşağıdaki aboneliklerde kullanılabilir:

- Microsoft 365 E5/A5/F5/G5 aboneliği (ücretli veya deneme sürümü)
- Microsoft 365 E3/A3/F3/G3 aboneliği + Microsoft 365 E5/A5/F5/G5 Uyumluluk eklentisi
- Microsoft 365 E3/A3/F3/G3 aboneliği + Microsoft 365 E5/A5/F5/G5 Insider Risk Yönetimi eklentisi
- Office 365 E3 abonelik + Enterprise Mobility ve Security E3 + Microsoft 365 E5 Uyumluluk eklentisi

### <a name="information-barriers"></a>Bilgi engelleri

[Microsoft Purview Bilgi Engelleri](information-barriers.md) , kuruluşunuzda çıkar çatışması oluşmasını önlemek için iki iç grup arasındaki iletişimi ve işbirliğini kısıtlamanıza olanak sağlar.

Bilgi engelleri aşağıdaki aboneliklerde kullanılabilir:

- Microsoft 365 E5/A5 aboneliği (ücretli veya deneme sürümü)
- Office 365 E5/A5/A3/A1 aboneliği (ücretli veya deneme sürümü)
- Office 365 Gelişmiş Uyumluluk eklentisi (artık yeni aboneliklerde kullanılamaz)
- Microsoft 365 E3/A3/A1 aboneliği + Microsoft 365 E5/A5 Uyumluluk eklentisi
- Microsoft 365 E3/A3/A1 aboneliği + Microsoft 365 E5/A5 Insider Risk Management eklentisi

### <a name="privileged-access-management"></a>Ayrıcalıklı erişim yönetimi

[Microsoft Purview Privileged Access Management](privileged-access-management.md), Office 365'daki ayrıcalıklı Exchange Online yönetici görevleri üzerinde ayrıntılı erişim denetimi sağlar. Kuruluşunuzun hassas verilere veya kritik yapılandırma ayarlarına erişimi olan mevcut ayrıcalıklı yönetici hesaplarını kullanan ihlallere karşı korunmasına yardımcı olabilir.

Ayrıcalıklı erişim yönetimi aşağıdaki aboneliklerde kullanılabilir:

- Microsoft 365 E5 aboneliği (ücretli veya deneme sürümü)
- Microsoft 365 A5 aboneliği (ücretli veya deneme sürümü)
- Office 365 Kurumsal E5 aboneliği (ücretli veya deneme sürümü)
- Office 365 A5 aboneliği (ücretli veya deneme sürümü)
- Microsoft 365 E3 abonelik + Microsoft 365 E5 Uyumluluk eklentisi
- Microsoft 365 E3 abonelik + Microsoft 365 E5 Information Protection ve İdare eklentisi
- Microsoft 365 A3 aboneliği + Microsoft 365 A5 Uyumluluğu eklentisi
- Microsoft 365 A3 abonelik + Microsoft 365 A5 Information Protection ve İdare eklentisi

## <a name="deploy-microsoft-purview-insider-risk-solutions"></a>Microsoft Purview insider risk çözümlerini dağıtma

Kuruluşunuzun şirket içi risklere karşı korunmasına yardımcı olmak için aşağıdaki Microsoft Purview çözümlerini ayarlayın ve dağıtın:

![Insider risk çözümü derinlemesine savunma.](../media/ir-solution-defense-in-depth.png)

1. [İletişim uyumluluk ilkelerini](communication-compliance-solution-overview.md) yapılandırma ve oluşturma.
2. [Insider risk yönetimi ilkelerini](insider-risk-management-solution-overview.md) yapılandırın ve oluşturun.
3. İsteğe bağlı: [Bilgi engeli ilkelerini](information-barriers-solution-overview.md) yapılandırın ve oluşturun.
4. İsteğe bağlı: [Ayrıcalıklı erişim yönetimini](privileged-access-management-solution-overview.md) etkinleştirin ve yapılandırın.

## <a name="illustrations-with-examples"></a>Örnekler içeren çizimler

Microsoft Purview insider risk özelliklerini uygulamaya yönelik tümleşik bir strateji planlamanıza yardımcı olmak için *Microsoft 365 bilgi koruma ve uyumluluk özellikleri kümesi çizimlerini* indirin. Insider risk özellikleri için 5-7 arası mimari çizim sayfalarına bakın. Bu çizimleri kendi kullanımınız için uyarlamaktan çekinmeyin.

| Öğe | Açıklama |
|:-----|:------------|
|[![Model posteri: Microsoft 365 bilgi koruma ve uyumluluk özellikleri.](../media/solutions-architecture-center/m365-compliance-illustrations-thumb.png)](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf) <br/> [PDF](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.pdf)  \| olarak indirme [Visio olarak indirme](https://download.microsoft.com/download/3/a/6/3a6ab1a3-feb0-4ee2-8e77-62415a772e53/m365-compliance-illustrations.vsdx) <br/> Ekim 2020 güncelleştirildi|Içerir: <ul><li>  Bilgi koruma ve veri kaybı önleme</li><li>Bekletme ilkeleri ve bekletme etiketleri </li><li>Bilgi engelleri</li><li>İletişim uyumluluğu</li><li>İçeriden risk yönetimi</li><li>Üçüncü taraf veri alımı</li>|

## <a name="training"></a>Eğitim

Yöneticilerinizi ve uyumluluk ekibinizi her iç risk çözümüne yönelik temel bilgilerle eğiterek kuruluşunuzun dağıtım ve uygulama çabalarınıza daha hızlı bir şekilde başlamasını sağlayabilirsiniz.

Microsoft, kuruluşunuzdaki bu kullanıcıları bilgilendirmeye ve eğitmeye yardımcı olmak için aşağıdaki kaynakları sağlar:

| Çözüm/Alan | Kaynaklar |
|:------------------|:--------------|
| Microsoft 365'te insider riskini yönetme |[Öğrenme yolunu tamamlama](/learn/paths/m365-compliance-insider) <br> Bu öğrenme yolu iletişim uyumluluğu, iç risk yönetimi, bilgi engelleri ve ayrıcalıklı erişim yönetimi için tüm bireysel çözüm modüllerini içerir. Tüm modülleri tamamlamak için bu öğrenme yolunu seçin. |
| İletişim uyumluluğu | [Öğrenme modülü: İletişim uyumluluğunu hazırlama](/learn/modules/m365-compliance-insider-prepare-communication-compliance) <br> Bu modül, iletişim uyumluluğu ile davranış kuralları ilkesi ihlallerini tanımlama ve düzeltme hakkında temel bilgileri öğrenmenize, iletişim uyumluluk ilkeleri oluşturmadan önce gereken önkoşulları karşılamanıza ve iletişim uyumluluğunda yerleşik, önceden tanımlanmış ilke şablonları türleri hakkında bilgi edinmenize yardımcı olur. |
| İçeriden risk yönetimi | [Öğrenme modülü: Insider risk yönetimi](/learn/modules/m365-compliance-insider-manage-insider-risk) <br> Bu modül, şirket içi risk yönetiminin bir kuruluştaki iç riskleri önlemeye, algılamaya ve içermeye nasıl yardımcı olabileceğini öğrenmenize, yerleşik, önceden tanımlanmış ilke şablonları türleri hakkında bilgi edinmenize, iç risk ilkeleri oluşturmadan önce gereken temel önkoşulları anlamanıza ve içeriden risk yönetimi olaylarında gerçekleştirebileceğiniz eylem türlerini açıklamanıza yardımcı olur. |
| Bilgi engelleri | [Öğrenme modülü: Bilgi engellerini planlama](/learn/modules/m365-compliance-insider-plan-information-barriers) <br> Bu modül, bilgi engeli ilkelerinin kuruluşunuzun ilgili endüstri standartları ve düzenlemeleriyle uyumluluğu sürdürmesine nasıl yardımcı olabileceğini öğrenmenize, bilgi engellerinin uygulanabileceği durum türlerini listelemenize, bilgi engeli ilkesi oluşturma sürecini açıklamaya ve bilgi engelleri oluştuktan sonra beklenmeyen sorunların nasıl giderileceğine ilişkin açıklamaya yardımcı olur. |
| Ayrıcalıklı erişim yönetimi | [Öğrenme modülü: Ayrıcalıklı erişim yönetimi uygulama](/learn/modules/m365-compliance-insider-implement-privileged-access-management) <br> Bu modül ayrıcalıklı erişim yönetimi ile ayrıcalıklı kimlik yönetimi arasındaki farkı anlamanıza, ayrıcalıklı erişim yönetimi süreci akışını anlamanıza ve ayrıcalıklı erişim yönetimini yapılandırma ve etkinleştirmeyle ilgili temel bilgileri anlamanıza yardımcı olur. |
