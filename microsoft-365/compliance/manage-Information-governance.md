---
title: Microsoft 365'de Microsoft Bilgi Yönetimi
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.collection: m365-security-compliance
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
recommendations: false
description: Verilerinizi uyumluluk veya mevzuat gereksinimleri için yönetmek için Microsoft Bilgi Yönetimi özelliklerini uygulama.
ms.openlocfilehash: b99d073817dc0ef899f448fb6a21619b08806759
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63009986"
---
# <a name="microsoft-information-governance-in-microsoft-365"></a>Microsoft 365'de Microsoft Bilgi Yönetimi

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Verilerinizi uyumluluk veya mevzuat gereksinimlerine göre yönetmek için Microsoft Bilgi Yönetimi (bazen MIG ile kısaltılmış) özelliklerini kullanın.

Lisanslama [açısından bakıldığında](#licensing-requirements), bilgi yönetimi, kayıt yönetimi ve veri bağlayıcıları arasında önemli ölçüde çakışma olabilir. Bu üç alandan üçü de verilerin elde tutulmasını ve silinmesini Microsoft 365. Bağlayıcılar, bilgi yönetimi ve kayıt yönetimi dışında uyumluluk çözümleri tarafından kullanılır. 

Uyumluluk merkezinde her biri kendi düğümü bulunan bu üç farklı çözümün ana yapılandırılabilir bileşenlerini tanımlamanıza yardımcı olacak aşağıdaki grafiği kullanın:

![Microsoft Information Goevernance için yönetecek ana bileşenler.](../media/information-governance-components.png)

Verilerinizi korumaya mı bakabilirsiniz? Bkz[. Microsoft Bilgi Koruması'da Microsoft 365](information-protection.md).

## <a name="information-governance"></a>Bilgi yönetimi

Size gerekenleri tutmak ve size gerek tutmayanları silmek için:
 
|Özellik|Hangi sorunları çözer?|Kullanmaya başlayın|
|:------|:------------|:--------------------|:-----------------------------|
|[özel durumlar için bekletme etiketleri Microsoft 365 iş yükleri için bekletme ilkeleri](retention.md) | E-posta, belgeler, e-posta ve posta iletileri için ilke yönetimiyle Teams veya Yammer silme | [Bekletme ilkeleri oluşturma ve yapılandırma](create-retention-policies.md) <br /><br /> [Bekletme ilkeleriniz için özel durumlar için bekletme etiketleri oluşturma](create-retention-labels-information-governance.md)|
|[Posta kutularını arşivleme](archive-mailboxes.md)| Kullanıcılara ek posta kutusu depolama alanı sağlar | [Arşiv posta kutularını etkinleştirme](enable-archive-mailboxes.md) |
|[Etkin olmayan posta kutuları](inactive-mailboxes-in-office-365.md)| Çalışanlar kuruluşdan ayrıldıktan sonra posta kutusu içeriğini koruyarak bu içeriğin yöneticiler, uyumluluk görevlileri ve kayıt yöneticileri tarafından erişilebilir kalmasını sağlar | [Etkin olmayan posta kutuları oluşturma ve yönetme](create-and-manage-inactive-mailboxes.md)|
|[PST dosyaları için hizmeti içeri aktarma](importing-pst-files-to-office-365.md)| Uyumluluk veya mevzuat gereksinimleri için e-Exchange Online iletilerini tutmak ve aramak için PST dosyalarını bu posta kutularına toplu olarak içeri aktarma | [Ağ karşıya yükleme kullanarak, kuruluş PST dosyalarını başka bir Microsoft 365](use-network-upload-to-import-pst-files.md)|

## <a name="records-management"></a>Kayıt yönetimi

Yasal, iş veya mevzuat yükümlülükleri için yüksek değerli öğelerin yaşam döngüsü yönetimi:

|Özellik|Hangi sorunları çözer?|Kullanmaya başlayın|
|:------|:------------|---------------------|:----------------------------|
|[Kayıt yönetimi](records-management.md)| Kayıt bildirimi ve gerektiğinde karşıtlıklı ifadeyle içeriğinizin tüm yaşam döngüsünü desteklemek için esnek bekletme ve silme zamanlamaları ve gereksinimleri içeren e-posta ve belgeler için tek bir çözüm |[Kayıt yönetimiyle çalışmaya başlama](get-started-with-records-management.md) |

## <a name="connectors-for-third-party-data"></a>Üçüncü taraf verileri için bağlayıcılar

Uyumluluk araçlarınızı sosyal medya platformlarından, anlık ileti platformlarından ve belge işbirliği platformlarından gelen üçüncü taraf verilerini içe ve arşive doğru genişletebilirsiniz:

|Özellik|Hangi sorunları çözer?|Kullanmaya başlayın|
|:------|:------------|:--------------------|:-----------------------------|
|[Veri bağlayıcıları](archiving-third-party-data.md)| Sosyal medya platformlarından, anlık ileti platformlarından ve belge işbirliği platformlarından üçüncü taraf verilerini içeri aktarma, arşivleme ve bu verilere uyumluluk çözümleri uygulama| [Üçüncü taraf bağlayıcılar](archiving-third-party-data.md#third-party-data-connectors)|

## <a name="licensing-requirements"></a>Lisans gereksinimleri

Microsoft Bilgi Yönetimi lisans gereksinimleri, bu sayfada listelenen her beceri için lisans gereksinimleri ayarlamak yerine kullandığınız senaryolara ve özelliklere bağlıdır. Lisans gereksinimlerinizi ve seçeneklerinizi anlamak için, Lisanslama belgelerinizin Microsoft 365 [bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance): 
- [Bilgi Yönetimi](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-governance) 
- [Kayıt Yönetimi](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#records-management) 
- [Veri bağlayıcıları](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#data-connectors)

Ek lisans gereksinimleri, belge yönergelerine dahil edilecektir. Örneğin, posta kutularını yönetmeye özgü lisanslama için posta kutularının lisansları Exchange Online.

