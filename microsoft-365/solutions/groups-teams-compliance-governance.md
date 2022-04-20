---
title: Microsoft 365 grupları, Teams ve SharePoint işbirliği için uyumluluk seçenekleri
ms.reviewer: ''
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Microsoft 365 grupları, Teams ve SharePoint işbirliği için uyumluluk seçenekleri hakkında bilgi edinin.
ms.openlocfilehash: afbbc6e507d613e028f65dbc157ec2222414af8c
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939136"
---
# <a name="compliance-options-for-microsoft-365-groups-teams-and-sharepoint-collaboration"></a>Microsoft 365 grupları, Teams ve SharePoint işbirliği için uyumluluk seçenekleri

Microsoft 365, kullanıcılarınız işbirliği yaptıklarında uyumluluğu korumak için eksiksiz bir araç paketi sunar. Bu seçenekleri gözden geçirin ve bunların iş gereksinimlerinizle nasıl eşlendiğini, verilerinizin duyarlılığını ve kullanıcılarınızın işbirliği yapması gereken kişilerin kapsamını göz önünde bulundurun.

Aşağıdaki tabloda, Microsoft 365'de kullanılabilen uyumluluk denetimleri için hızlı bir başvuru sağlanır. Aşağıdaki bölümlerde daha fazla bilgi verilmiştir.

|Kategori|Açıklama|Başvuru|
|:-------|:----------|:--------|
|Bilgi saklama|||
||Grupların postalarını ve SharePoint içeriğini saklama|[SharePoint ve OneDrive için bekletme ilkeleri hakkında bilgi edinin](../compliance/retention-policies-sharepoint.md)|
||Sohbeti ve iletileri saklama|[Microsoft Teams için bekletme ilkeleri hakkında bilgi edinin](../compliance/retention-policies-teams.md)|
|Bilgi sınıflandırması|||
||Grupları ve ekipleri sınıflandırma|[Microsoft Teams, Microsoft 365 grupları ve SharePoint sitelerindeki içeriği korumak için duyarlılık etiketlerini kullanma](../compliance/sensitivity-labels-teams-groups-sites.md)|
||Hassas içeriği otomatik olarak sınıflandırma|[İçeriğe otomatik olarak bir hassasiyet etiketi uygulama](../compliance/apply-sensitivity-label-automatically.md)|
||Hassas içeriği şifreleme|[Şifreleme uygulamak için hassasiyet etiketleri kullanarak içeriğe erişimi kısıtlama](../compliance/encryption-sensitivity-labels.md)|
|Bilgi koruması|||
||Hassas bilgilerin kaybını önleme|[Microsoft Purview Veri Kaybı Önleme hakkında bilgi edinin](../compliance/dlp-learn-about-dlp.md)|
||Sohbetteki hassas bilgileri koruyun.|[Microsoft Purview Veri kaybı önleme ve Microsoft Teams](../compliance/dlp-microsoft-teams.md)|
||Kuruluşunuzun hassas bilgilerini tanımlama|[Özel hassas bilgi türleri](../compliance/sensitive-information-type-learn-about.md)|
|Kullanıcı segmentasyonu|||
||Kullanıcı kesimleri arasındaki iletişimi kısıtlama|[Bilgi engelleri](../compliance/information-barriers.md)|
|Veri yerleşimi|||
||Verileri belirli coğrafi konumlarda depolama|[Microsoft 365 Multi-Geo](/microsoft-365/enterprise/microsoft-365-multi-geo)|

## <a name="information-retention"></a>Bilgi saklama

Bekletme ilkeleri; dosyalar, iletiler ve postalar dahil olmak üzere gruplarda ve ekiplerde işbirliği için kullanılan öğeleri korumak veya silmek için kullanılabilir. İlkeler tutulacak ve silinecek, yalnızca korunacak veya yalnızca silinecek şekilde ayarlanabilir. Bekletme ilkesi kapsamındaki bilgiler, grubun veya ekibin süresinin dolması veya başka bir şekilde silinmesi durumunda korunur.

Microsoft 365 Grupları için bekletme ilkesi yapılandırmak, grup posta kutusunu ve ilişkili SharePoint sitesini ve dosyalarını kapsar.

- [SharePoint ve OneDrive için bekletme ilkeleri hakkında bilgi edinin](../compliance/retention-policies-sharepoint.md)

Teams için bekletme ilkeleri sohbet ve kanal iletilerini korur. Sohbet ve kanal iletileri Exchange posta kutularında depolanırken, Exchange saklama ilkelerinden etkilenmez. Bekletme ilkelerinizi Teams sohbetlere ve Teams kanal iletilerine uygulanacak şekilde ayarlamanız gerekir. 

Kullanıcı hesabı silinse bile kullanıcı sohbetleri süresiz olarak korunur. Bu verileri süresiz olarak saklamak istemiyorsanız, belirli bir süre sonra kullanıcı sohbetlerini silmek için bir bekletme ilkesi kullanmayı veya bu silme işlemini kullanıcı silme işleminize eklemeyi göz önünde bulundurun.

- [Microsoft Teams için bekletme ilkeleri hakkında bilgi edinin](../compliance/retention-policies-teams.md)

- [Microsoft Teams bekletme ilkeleri](/microsoftteams/retention-policies)

Tek bir bekletme ilkesi, Teams sohbet ve Teams kanal iletilerine uygulanacak şekilde ayarlanabilir. 

Ek kaynaklar:

- [Bekletme ilkeleri hakkında bilgi edinin](../compliance/retention.md)

- [Exchange'de bekletme etiketleri ve bekletme ilkeleri](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies)

## <a name="information-classification"></a>Bilgi sınıflandırması

Konuk erişimini, grup ve ekip gizliliğini yönetmek ve gruplar ve ekipler için yönetilmeyen cihazlara erişimi yönetmek için duyarlılık etiketlerini kullanabilirsiniz. Etiket uygulandığında, bu ayarlar etiket ayarları tarafından belirtilen şekilde otomatik olarak yapılandırılır.

- [Microsoft Teams, Microsoft 365 grupları ve SharePoint sitelerindeki içeriği korumak için duyarlılık etiketlerini kullanma](../compliance/sensitivity-labels-teams-groups-sites.md)

Hassas bilgi türlerini algılama veya eğitilebilir sınıflandırıcılarla desen eşleştirme dahil olmak üzere, belirttiğiniz ölçütlere göre dosyalara ve e-postalara duyarlılık etiketlerini otomatik olarak uygulamak için Microsoft 365 yapılandırabilirsiniz.

- [İçeriğe otomatik olarak bir hassasiyet etiketi uygulama](../compliance/apply-sensitivity-label-automatically.md)

Duyarlılık etiketlerini kullanarak dosyaları şifreleyebilir, böylece yalnızca şifresini çözme ve okuma izni olan kişilere izin vekleyebilirsiniz.

- [Şifreleme uygulamak için hassasiyet etiketleri kullanarak içeriğe erişimi kısıtlama](../compliance/encryption-sensitivity-labels.md)

- [Güvenlik yalıtımıyla bir ekibi yapılandırın](./secure-teams-security-isolation.md)

Ek kaynaklar:

- [Duyarlılık etiketleri hakkında bilgi edinin](../compliance/sensitivity-labels.md)


## <a name="information-protection"></a>Bilgi koruması

DLP ilkeleri hassas bilgilerin SharePoint, Exchange ve Teams arasında yanlışlıkla paylaşılmasını önleyebilir. Bir dizi kurala göre yapılması gereken eylemleri (erişimi engelleme gibi) belirten ilkeler oluşturabilirsiniz.

- [Veri kaybı önleme hakkında daha fazla bilgi edinme](../compliance/dlp-learn-about-dlp.md)

Teams'da DLP, hassas bilgiler içeren iletileri silerek sohbet ve kanal iletileri Teams hassas bilgilerin korunmasına yardımcı olabilir.

- [Veri kaybı önleme ve Microsoft Teams](../compliance/dlp-microsoft-teams.md)

Proje kodu adları gibi kuruluşunuza özgü hassas bilgileriniz varsa, kendi hassas bilgi türlerinizi oluşturabilir ve gruplar, ekipler ve SharePoint içeriği korumak için bunları DLP ilkelerine uygulayabilirsiniz.

- [Özel hassas bilgi türleri](../compliance/sensitive-information-type-learn-about.md)

## <a name="user-segmentation"></a>Kullanıcı segmentasyonu

Bilgi engelleriyle, gruplar arasındaki istenmeyen iletişimi ve işbirliğini kısıtlamak ve kuruluşunuzdaki çıkar çakışmalarını önlemek için verilerinizi ve kullanıcılarınızı segmentlere ayırabilirsiniz. Bilgi engelleri, kuruluşunuzdaki kişi grupları arasında dosya işbirliğine, sohbete, aramaya veya toplantı davetlerine izin veren veya engelleyen ilkeler oluşturmanıza olanak tanır.

- [Bilgi engelleri](../compliance/information-barriers.md)

- [Microsoft Teams'da bilgi engelleri](/microsoftteams/information-barriers-in-teams)

- [SharePoint ile bilgi engellerini kullanma](/sharepoint/information-barriers)

## <a name="data-residency"></a>Veri yerleşimi

Microsoft 365 Multi-Geo ile bekleyen verileri, veri yerleşimi gereksinimlerini karşılamak için seçtiğiniz coğrafi konumlarda sağlayabilir ve depolayabilirsiniz. Multi-Geo ortamında, Microsoft 365 kiracınız merkezi bir konumdan (Microsoft 365 aboneliğinizin ilk sağlandığı yerde) ve verileri depolayabileceğiniz bir veya daha fazla uydu konumundan oluşur.

- [Microsoft 365 Multi-Geo](/microsoft-365/enterprise/microsoft-365-multi-geo)

- [multi-geo Microsoft 365 için planlama](/microsoft-365/enterprise/plan-for-multi-geo)

## <a name="related-topics"></a>İlgili konular

[İşbirliği idaresi planlama önerileri](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[İşbirliği idare planınızı oluşturma](collaboration-governance-first.md)

[Exchange Online için güvenlik ve uyumluluk](/exchange/security-and-compliance/security-and-compliance)

[Bilgileri koruma](../compliance/information-protection.md)
