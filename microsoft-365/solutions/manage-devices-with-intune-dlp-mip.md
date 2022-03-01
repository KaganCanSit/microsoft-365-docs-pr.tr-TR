---
title: Adım 7. Bilgi koruma özellikleriyle veri kaybı önleme (DLP) uygulama
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
description: Kuruluş için DLP ilkeleri oluşturmak için bilgi koruma ve yönetim ekibimizle birlikte çalışarak Uç Nokta DLP'nizi uygulama.
ms.openlocfilehash: c38171d790ffd376c7886da0547345cf7e74e36c
ms.sourcegitcommit: bcea69bacd1b48827bd60af2880909593a1609a4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010780"
---
# <a name="step-7-implement-data-loss-prevention-dlp-with-information-protection-capabilities"></a>Adım 7. Bilgi koruma özellikleriyle veri kaybı önleme (DLP) uygulama


Organizasyonunız verilerinizi anlamak, veri duyarlılığı şeması geliştirmek ve şemayı uygulamak için zaman kaybettiyse, veri kaybı önleme (DLP) ilkelerini kullanarak bu şemanın öğelerini uç noktalara genişletmeye hazır olabilirsiniz. 

Microsoft Uç Nokta veri kaybı önleme (Uç Nokta DLP) şu anda aşağıdakiler için geçerlidir:
- Windows 10, Windows 11
- macOS

DLP ilkeleri, bilgi koruma ve yönetim ekibiniz tarafından oluşturulur. Her DLP ilkesi, veri kümesi içinde hangi öğelerin (hassas bilgi türleri veya etiketler gibi) bakıla hazır olacağını ve bu verilerin nasıl korunmasını tanımlar. 

Örneğin, DLP ilkesi pasaport numarası gibi kişisel veriler için bakabilirsiniz. DLP ilkesi, pasaport numarasının kuruluş dışındaki kişilerle paylaşılması gibi, ilkeyi hareketeecek bir koşul içerir. İlkenin 2013'e bağlı olduğu eylem de yalıtıldı. Seçenekler, yalnızca eylemi yöneticilere bildirmeden, kullanıcıları uyarıp hatta verilerin paylaşılmasını engellemeye kadar geniş bir aralıktadır.

DLP ilkesi ayrıca e-posta adresi ve posta siteleri gibi ilkenin Exchange konumu da SharePoint belirtir. Yöneticiler tarafından kullanılabilen konumlardan biri de cihazlardır. Cihazlar seçiliyse, ilkenin hangi kullanıcılara ve kullanıcı gruplarına uygulan etki alanıyla ilgili olduğunu belirtebilirsiniz. Ayrıca, ilkenin dışında tutulacak kullanıcıları ve kullanıcı gruplarını da belirtebilirsiniz.

Bilgi koruma ve yönetim ekibiniz DLP ilkelerini uç noktalara genişletmeye hazırsa, Uç Nokta DLP için cihazları etkinleştirmek, DLP ilkelerini test etmek ve ayarlamak, kullanıcıları eğitmek ve sonuçları izlemek için onlarla birlikte çalışmanız gerekir. 

![Cihaz yöneticisi için uç nokta DLP adımları](../media/devices/endpoint-dlp-steps.png#lightbox)

[2. Adımı tamamladıysanız. Cihazları yönetime ve](manage-devices-with-intune-enroll.md) [6. Adıma kaydettirin. Cihaz riskini ve güvenlik taban çizgilerine uyumluluğu](manage-devices-with-intune-monitor-risk.md) izlemek için cihazları Uç Nokta için Defender'a kaydettirin; cihazlarınız Uç Nokta DLP için zaten etkinleştirilmiştir. 


Bilgi koruma ekibimizle çalışmak için aşağıdaki adımları kullanın.


|Adım  |Açıklama  |
|---------|---------|
|1     |  [Uç nokta Microsoft 365 kaybı önleme hakkında bilgi öğrenin](../compliance/endpoint-dlp-learn-about.md).        |
|2     | Uç Nokta DLP için cihazları etkinleştirin. Uç nokta için Microsoft Defender'a cihazlarınız varsa, cihazlarınız Uç Nokta DLP için zaten etkinleştirilmiş durumdadır. Cihazlarınız Uç Nokta için Defender'a eklemediyebilirsiniz, yönergeler için [bkz. Uç nokta veri kaybı önleme ile çalışmaya](../compliance/endpoint-dlp-getting-started.md) başlama.|
|3     |   İlkeleri tanımlamak, test etmek ve ayarlamak için bilgi koruma ve yönetim ekibimizle birlikte çalışma. Bu, sonuçların izlenmesini de içerir. Bu kaynaklara bakın:<br>- [Uç nokta veri kaybını önlemeyi kullanma](../compliance/endpoint-dlp-using.md)<br>- [Veri kaybını önleme raporlarını görüntüleme](../compliance/view-the-dlp-reports.md)      |
|     |         |