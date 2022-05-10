---
title: Microsoft Purview Veri Yaşam Döngüsü Yönetimi & Microsoft Purview Kayıt Yönetimi
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
description: Microsoft Purview Veri Yaşam Döngüsü Yönetimi & Microsoft Purview Kayıt Yönetimi'nden gelen özellikleri uygulayarak verilerinizi uyumluluk veya mevzuat gereksinimlerine göre idare edin.
ms.openlocfilehash: c807d2359c9a8c9cb17955b1ad4bf121cab57918
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65286978"
---
# <a name="govern-your-data-with-microsoft-purview"></a>Microsoft Purview ile verilerinizi yönetme

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Verilerinizi uyumluluk veya mevzuat gereksinimlerine göre yönetmek için **Microsoft Purview Veri Yaşam Döngüsü Yönetimi** (eski adıyla Microsoft Information Governance) ve **Microsoft Purview Kayıt Yönetimi** özelliklerini kullanın.

> [!TIP]
> Çoklu bulut ve hizmet olarak yazılım (SaaS) dahil olmak üzere verilerinizi tüm veri varlığınızda eşlemek ve yönetmek mi istiyorsunuz? [Microsoft Purview Veri Haritası, Microsoft Purview Veri Kataloğu ve Microsoft Purview Data Estate Analizler](/azure/purview/overview) kullanın.

[Lisanslama açısından](#licensing-requirements) bakıldığında, veri yaşam döngüsü yönetimi ile kayıt yönetimi arasında önemli bir çakışma olabilir. Her iki çözüm de Microsoft 365 uygulamalar ve hizmetler için verilerin saklanmasını ve silinmesini destekler.

Microsoft Purview uyumluluk portalında her biri kendi yapılandırma alanına sahip olan bu çözümlerin ana yapılandırılabilir bileşenlerini belirlemenize yardımcı olması için aşağıdaki grafiği kullanın:

![Microsoft Purview ile verilerinizi yapılandırmak ve yönetmek için kullanılacak ana bileşenler.](../media/govern-your-data.png)

Verilerinizi korumak mı arıyorsunuz? Bkz [. Microsoft Purview ile verilerinizi koruma](information-protection.md).

## <a name="microsoft-purview-data-lifecycle-management"></a>Microsoft Purview Veri Yaşam Döngüsü Yönetimi

İhtiyacınız olanı korumak ve ihtiyacınız olmayanları silmek için:
 
|Yeteneği|Hangi sorunları çözer?|
|:------|:------------|:----------------|
|[özel durumlar için bekletme etiketleriyle Microsoft 365 iş yükleri için bekletme ilkeleri](retention.md) | E-posta, belgeler, Teams ve Yammer iletileri için ilke yönetimiyle içeriği saklamanıza veya silmenize olanak tanır. |
|[Etkin olmayan posta kutuları](inactive-mailboxes-in-office-365.md)| Çalışanlar kuruluştan ayrıldıktan sonra posta kutusu içeriğini korumanıza olanak tanır, böylece bu içerik yöneticiler, uyumluluk görevlileri ve kayıt yöneticileri tarafından erişilebilir kalır. |
|[Posta kutularını arşivle](archive-mailboxes.md)| Kullanıcılar için ek posta kutusu depolama alanı sağlar.|
|[PST dosyaları için içeri aktarma hizmeti](importing-pst-files-to-office-365.md)| Uyumluluk veya mevzuat gereksinimleri için e-posta iletilerini saklamak ve aramak için posta kutularını Exchange Online PST dosyalarını toplu olarak içeri aktarmayı destekler. |

Daha fazla bilgi edinmek ister misiniz? Bkz. [Veri yaşam döngüsü yönetimi hakkında bilgi edinin](data-lifecycle-management.md).

Bu özelliklerin bazılarını veya tümünü kullanmaya başlamaya hazır mısınız? Bkz. [Veri yaşam döngüsü yönetimiyle Kullanmaya başlayın](get-started-with-data-lifecycle-management.md).


## <a name="microsoft-purview-records-management"></a>Microsoft Purview Kayıt Yönetimi

İş, yasal veya mevzuat kaydı tutma gereksinimleri için yüksek değerli öğeleri yönetin:

|Yeteneği|Hangi sorunları çözer?|
|:---------|:---------------------------|
|[Dosya planı](file-plan-manager.md)| Bekletme etiketlerini etkileşimli olarak oluşturmanıza veya toplu olarak içeri aktarmanıza ve analiz için dışarı aktarmanıza olanak tanır. Etiketler, iş veya mevzuat gereksinimlerini belirlemenize ve izlemenize yardımcı olmak için ek yönetim bilgilerini (isteğe bağlı) destekler. |
|[Tek tek öğeler için bekletme etiketleri, temel saklama için gerekirse bekletme ilkeleri](retention.md)| Etiketler, gerektiğinde kayıt bildirimiyle birlikte el ile veya otomatik olarak uygulanabilen esnek saklama ve silme zamanlamalarını destekler. |
|[Değerlendirme gözden geçirmesi ve değerlendirme kanıtı](disposition.md)| Kalıcı olarak silinmeden önce içeriğin el ile gözden geçirilmesi ve kayıtların kullanım dışı bırakma kanıtı.|

Daha fazla bilgi edinmek ister misiniz? Bkz. [Kayıt yönetimi hakkında bilgi edinin](records-management.md).

Bu özelliklerin bazılarını veya tümünü kullanmaya başlamaya hazır mısınız? Bkz. [kayıt yönetimiyle Kullanmaya başlayın](get-started-with-records-management.md).


## <a name="licensing-requirements"></a>Lisans gereksinimleri

Lisanslama gereksinimlerinizi ve seçeneklerinizi anlamak için [Microsoft 365 lisanslama belgelerindeki aşağıdaki bölümlere bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance): 
- [Microsoft Purview Veri Yaşam Döngüsü Yönetimi](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-data-lifecycle-management)
- [Microsoft Purview Kayıt Yönetimi](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#microsoft-purview-records-management)

Tüm ek lisanslama gereksinimleri belge yönergelerine eklenecektir. Örneğin, posta kutularını yönetmeye özgü lisanslama için Exchange Online lisansları gerekebilir.