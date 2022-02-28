---
title: Veri gizliliği düzenlemesi için kimlik, cihaz ve tehdit koruması kullanma
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/09/2020
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: ''
description: Verilerinizin kimlik, cihaz ve tehdit koruması hizmetleriyle kişisel veri ihlallerini Microsoft 365.
ms.openlocfilehash: a5aa97637b0d44b762d1a1146effdefb932ab47d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988582"
---
# <a name="use-identity-device-and-threat-protection-for-data-privacy-regulation"></a>Veri gizliliği düzenlemesi için kimlik, cihaz ve tehdit koruması kullanma

Microsoft 365, kuruluşların veri gizliliğiyle ilgili uyumluluk düzenlemelerine uymaya yardımcı olmak için çalıştıracakları bir dizi kimlik, cihaz ve tehdit koruması özelliği sağlar. Bu makalede, bu alanlarda veri gizliliği düzenlemelerinin neleri gerekli k olduğu açıklanmıştır ve uygulama gereksinimlerini karşılamanıza yardımcı olacak ek bilgilerin bağlantılarını içeren ilgili Microsoft 365 özellikleri ve hizmetlerinin bir listesini sağlar.

## <a name="how-identity-device-and-threat-protection-relate-to-data-privacy-regulation"></a>Kimlik, cihaz ve tehdit korumasının veri gizliliği düzenlemesi ile ilişkili

Veri gizliliği yasal düzenlemelerinin özgülükleri farklılık gösterse de, çağırıldıklarının özünü GDPR'nin aşağıdaki durumuna ilişkin Madde 5(1)(f) ile kabartmalı olarak ifade eder:

- Kişisel veriler, yetkisiz veya yasa dışı işlemeye karşı ve yanlışlıkla kayıp, zarar görme veya zarara karşı uygun teknik veya kurumsal ölçüler ('bütünlük ve gizlilik') kullanılarak, kişisel verilerin uygun güvenliğini sağlayan bir şekilde işlenir.

Kişisel veri ihlallerine genellikle yönetim veya son kullanıcı hesabının güvenliği tehlikeye ve kötü amaçlı sistem erişimi neden olur. Örneğin, bir yönetici hesabının ele eleması, müşteri kredi kartı numaralarının veya diğer kişisel bilgilerin sızıntısını neden olabilir. Genel olarak yardımcı olabilecek kimlik, cihaz ve tehdit korumasının Microsoft 365, uyumluluk Yöneticisi'nde bulunan uyumluluk puanınıza yansıtılabilir ve bu şekilde uygulanma olasılığı vardır.

## <a name="using-the-results-of-your-assessment-work-and-compliance-manager"></a>Değerlendirme çalışmanızı ve Uyumluluk Yöneticisi'ni sonuçları kullanma

Uyumluluk Yöneticisi şu kategorileri kullanarak kimlik, cihaz ve tehdit koruması içerir:

- Kimlik, Denetim Erişimi **kategorisine karşılık** gelen
- Cihaz, Cihazları Yönet **kategorisine** karşılık gelen
- Tehdit koruması Tehditlere Karşı **Koruma kategorisine karşılık** geldi
 
Bunlar dört ana veri gizliliği düzenlemesi örnek kümemizde seçilmişse, Uyumluluk Yöneticisi 90 geliştirme eylemi belirtir ve bunların çoğu "27" olarak puanlandı. Bu tür büyük bir sayı bu kategoriler için Uyumluluk Yöneticisi tarafından belirtilmiş olduğu için, yaygın kullanılanlardan bazıları başvuru için burada listelenmiştir.

Kimlik [Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/) ve **Denetim Erişimi** kategorisini kullanın; şunları da kullanabilirsiniz:

- Yeniden yürütmeye karşı karşı kimlik doğrulaması uygulama ("Ortadaki adam" saldırılarını önlemek için)
- Eski kimlik doğrulamayı engelin.
- Kullanıcı riski ve kullanıcı oturum açma risk ilkelerini yapılandırma.
- Yöneticiler ve yönetici olmayanlar için Koşullu Erişim'i ve çok faktörlü kimlik doğrulamasını (MFA) etkinleştirin.
- Parola ilkelerini yapılandırarak ve zorunlu kılın.
- Azure AD ile ayrıcalıklı hesaplara erişimi Privileged Identity Management.
- Sonlandırmayla birlikte erişimi devre dışı bırak.
- Kullanıcı hesaplarını ve durum değişikliklerini denetleme.
- Rol grubunu ve yönetim değişikliklerini gözden geçirin.

Cihazlar [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager) ve **Cihazları Yönet kategorisini** kullanın; şunları da kullanabilirsiniz:

- Kökleri bozuk ve kökleri olan mobil cihazları engelle.
- Intune'i mobil cihaz yönetimi için yapılandırma.
- Android, iOS, macOS ve Windows için uyumluluk Windows oluşturun.
- Android, iOS, macOS ve diğer cihazlar için bir cihaz Windows oluşturun.
- iOS ve güvenlik ilkeleri için uygulama koruma Windows.
- Kilit ekranı ile bilgileri gizleyin.
- Mobil cihazlar için parola ilkeleri uygulama.
- Mobil cihazların çalışmama sırasında kilitlenmesini gerektirme.
- Birden çok oturum açma hatasının mobil cihazlarda temize ulaşamalarını gerekli olarak kontrol edin.

[Tehditlere Exchange Online Protection kategorisi için Office 365 Microsoft Defender](../security/office-365-security/defender-for-office-365.md) **for Microsoft** Defender'ı kullanın; şu bilgileri kullanabilirsiniz:

- Gönderen kimlik doğrulamasını (SPF, DMARC ve DKIM) etkinleştirin.
- Kimlik avı önleme ilkelerini Office 365 için Microsoft Defender'ı ayarlayın.
- Ekleri Kasa uygulama.
- Bağlantı Kasa gerçekleştirin.
- Kötü amaçlı yazılım algılama ve yanıt ilkeleri uygulama.
- Giden ve gelen istenmeyen posta ilkeleri uygulama.

### <a name="references"></a>Başvurular:

- [Ortak kimlik ve cihaz erişimi ilkeleri](../security/office-365-security/identity-access-policies.md)
- [Güvenlik tehditlerine karşı Office 365](https://support.office.com/article/protect-against-threats-in-office-365-b10023f6-f30f-45d3-b3ad-b71aa4aa0d58)
- [Kasa Ekleri Kaydetme](../security/office-365-security/safe-attachments.md)
- [Güvenli Bağlantılar](../security/office-365-security/safe-links.md)
- [Güvenli Belgeler](../security/office-365-security/safe-docs.md)
