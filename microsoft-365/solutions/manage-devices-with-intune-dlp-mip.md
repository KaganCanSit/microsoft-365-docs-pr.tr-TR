---
title: 7. Adım. Bilgi koruma yetenekleriyle veri kaybı önleme (DLP) uygulayın
ms.author: bcarter
author: brendacarter
f1.keywords:
- Endpoint dlp
- data loss prevention
- dlp policies
manager: dougeby
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- endpoint dlp
- data loss prevention
- dlp policies
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
description: Kuruluşunuz için DLP ilkeleri oluşturmak üzere bilgi koruma ve idare ekibinizle birlikte çalışarak Uç Nokta DLP'sini uygulayın.
ms.openlocfilehash: 605923c377aca77f84861116b38b6ef07f95ca4f
ms.sourcegitcommit: a06bb81fbd727a790a8fe6a3746b8a3cf62a6b24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/05/2022
ms.locfileid: "64651311"
---
# <a name="step-7-implement-data-loss-prevention-dlp-with-information-protection-capabilities"></a>7. Adım. Bilgi koruma yetenekleriyle veri kaybı önleme (DLP) uygulayın


Kuruluşunuz verilerinizi anlamak, veri duyarlılığı şeması geliştirmek ve şemayı uygulamak için zaten zaman ayırmışsa, veri kaybı önleme (DLP) ilkelerini kullanarak bu şemanın öğelerini uç noktalara genişletmeye hazır olabilirsiniz. 

Microsoft Endpoint veri kaybı önleme (Endpoint DLP) şu anda şunlar için geçerlidir:
- Windows 10, Windows 11
- macOS

DLP ilkeleri, bilgi koruma ve idare ekibiniz tarafından oluşturulur. Her DLP ilkesi, hassas bilgi türleri veya etiketler gibi bir veri kümesi içindeki hangi öğelerin aranacağını ve bu verilerin nasıl korunacağını tanımlar. 

Örneğin, DLP ilkesi pasaport numarası gibi kişisel verileri arayabilir. DLP ilkesi, bir pasaport numarasının kuruluşunuz dışındaki kişilerle paylaşılması gibi, ilkenin eyleme geçmelerini tetikleyen bir koşul içerir. İlkenin gerçekleştirilen eylemi de yapılandırılabilir. Seçenekler yalnızca eylemi yöneticilere raporlama, kullanıcıları uyarma ve hatta verilerin paylaşılmasını engelleme arasında değişir.

DLP ilkesi, e-posta ve Exchange SharePoint siteleri gibi ilkenin uygulanacağı konumu da belirtir. Yöneticilerin kullanabileceği konumlardan biri cihazlardır. Cihazlar seçiliyse, ilkenin hangi kullanıcılara ve kullanıcı gruplarına uygulanacağını belirtebilirsiniz. İlkenin dışında tutulacak kullanıcıları ve kullanıcı gruplarını da belirtebilirsiniz.

Bilgi koruma ve idare ekibiniz DLP ilkelerini uç noktalara genişletmeye hazırsa, Uç Nokta DLP için cihazları etkinleştirmek, DLP ilkelerini test etmek ve ayarlamak, kullanıcıları eğitmek ve sonuçları izlemek için onlarla koordine olmanız gerekir. 

![Cihaz yöneticisi için uç nokta DLP adımları](../media/devices/endpoint-dlp-steps.png#lightbox)

[2. Adımı tamamladıysanız. Cihazları Intune](manage-devices-with-intune-enroll.md) ve [6. Adım'a kaydedin. Cihaz riskini ve güvenlik temellerine uyumluluğu izlemek için cihazları Uç Nokta için Defender'a kaydedin](manage-devices-with-intune-monitor-risk.md); cihazlarınız Uç Nokta DLP için zaten etkinleştirilmiştir. 


Bilgi koruma ekibinizle çalışmak için aşağıdaki adımları kullanın.


|Adım  |Açıklama  |
|---------|---------|
|1     |  [uç nokta veri kaybını önleme Microsoft 365 hakkında bilgi edinin](../compliance/endpoint-dlp-learn-about.md).        |
|2     | Uç Nokta DLP için cihazları etkinleştirin. Cihazlarınızı Uç Nokta için Microsoft Defender'a eklerseniz, cihazlarınız Uç Nokta DLP için zaten etkindir. Cihazlarınız Uç Nokta için Defender'a eklenmemişse yönergeler için [bkz. Uç nokta veri kaybı önleme ile Kullanmaya başlayın](../compliance/endpoint-dlp-getting-started.md).|
|3     |   İlkeleri tanımlamak, test etmek ve ayarlamak için bilgi koruma ve idare ekibinizle birlikte çalışın. Bu, sonuçları izlemeyi içerir. Şu kaynaklara bakın:<br>- [Uç nokta veri kaybı önlemeyi kullanma](../compliance/endpoint-dlp-using.md)<br>- [Veri kaybı önleme raporlarını görüntüleme](../compliance/view-the-dlp-reports.md)      |
|     |         |