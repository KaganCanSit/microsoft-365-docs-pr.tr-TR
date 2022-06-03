---
title: SaaS uygulamaları için önerilen Microsoft Defender for Cloud Apps ilkeleri - Microsoft 365 Kurumsal | Microsoft Docs
description: Microsoft Defender for Cloud Apps ile tümleştirme için önerilen ilkeleri açıklar.
author: BrendaCarter
manager: laurawi
ms.topic: article
audience: Admin
ms.author: bcarter
ms.date: 03/22/2021
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
ms.prod: m365-security
ms.openlocfilehash: 8386b01da6d0db5703d74d96f4e22de18b1f7d70
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65873632"
---
# <a name="recommended-microsoft-defender-for-cloud-apps-policies-for-saas-apps"></a>SaaS uygulamaları için önerilen Microsoft Defender for Cloud Apps ilkeleri

Microsoft Defender for Cloud Apps, indirmeleri engelleme, karşıya yüklemeler, kopyalama ve yapıştırma ve yazdırma gibi Ayrıntılı eylemleri SaaS uygulamalarıyla gerçek zamanlı izleme ve denetlemeye olanak tanımak için Azure AD koşullu erişim ilkelerine dayalıdır. Bu özellik, şirket kaynaklarına yönetilmeyen cihazlardan veya konuk kullanıcılar tarafından erişildiğinde olduğu gibi doğal risk taşıyan oturumlara güvenlik ekler.

Bulut için Defender Uygulamaları ayrıca Microsoft Purview Bilgi Koruması ile yerel olarak tümleştirerek hassas bilgi türlerine ve duyarlılık etiketlerine göre hassas verileri bulmak ve uygun işlemleri yapmak için gerçek zamanlı içerik denetimi sağlar.

Bu kılavuz şu senaryolar için öneriler içerir:

- SaaS uygulamalarını BT yönetimine getirme
- Belirli SaaS uygulamaları için korumayı ayarlama
- Veri koruma düzenlemelerine uymaya yardımcı olmak için Microsoft Purview veri kaybı önlemeyi (DLP) yapılandırma

## <a name="bring-saas-apps-into-it-management"></a>SaaS uygulamalarını BT yönetimine getirme

SaaS uygulamalarını yönetmek için Bulut için Defender Uygulamalarını kullanmanın ilk adımı, bunları bulmak ve ardından bunları Azure AD kiracınıza eklemektir. Bulma konusunda yardıma ihtiyacınız varsa bkz. [Ağınızdaki SaaS uygulamalarını bulma ve yönetme](/cloud-app-security/tutorial-shadow-it). Uygulamaları keşfettikten sonra [bunları Azure AD kiracınıza ekleyin](/azure/active-directory/manage-apps/add-application-portal).

Aşağıdakileri yaparak bunları yönetmeye başlayabilirsiniz:

1. İlk olarak, Azure AD yeni bir koşullu erişim ilkesi oluşturun ve bunu "Koşullu Erişim Uygulama Denetimi Kullan" olarak yapılandırın. Bu, isteği Bulut için Defender Uygulamalarına yönlendirir. Bir ilke oluşturabilir ve tüm SaaS uygulamalarını bu ilkeye ekleyebilirsiniz.
1. Ardından, Bulut için Defender Uygulamalar'da oturum ilkeleri oluşturun. Uygulamak istediğiniz her denetim için bir ilke oluşturun.

SaaS uygulamalarına yönelik izinler genellikle uygulamaya erişim için iş gereksinimini temel alır. Bu izinler son derece dinamik olabilir. Bulut için Defender Uygulamaları ilkelerinin kullanılması, kullanıcıların başlangıç noktası, kuruluş veya özel güvenlik korumasıyla ilişkili bir Azure AD grubuna atanmasından bağımsız olarak uygulama verilerine koruma sağlar.

SaaS uygulamaları koleksiyonunuz genelinde verileri korumak için, aşağıdaki diyagramda gerekli Azure AD koşullu erişim ilkesi ve Bulut için Defender Uygulamalarında oluşturabileceğiniz önerilen ilkeler gösterilmektedir. Bu örnekte, Bulut için Defender Uygulamalarında oluşturulan ilkeler yönettiğiniz tüm SaaS uygulamaları için geçerlidir. Bunlar, cihazların yönetilip yönetilmediğine ve dosyalara zaten uygulanmış olan duyarlılık etiketlerine göre uygun denetimleri uygulamak için tasarlanmıştır.

:::image type="content" source="../../media/microsoft-365-policies-configurations/mcas-manage-saas-apps-2.png" alt-text="Bulut için Defender Uygulamalarında SaaS uygulamalarını yönetme ilkeleri" lightbox="../../media/microsoft-365-policies-configurations/mcas-manage-saas-apps-2.png":::

Aşağıdaki tabloda, Azure AD'de oluşturmanız gereken yeni koşullu erişim ilkesi listelenir.

|Koruma düzeyi|Ilkesi|Daha fazla bilgi|
|---|---|---|
|Tüm koruma düzeyleri|[Bulut için Defender Uygulamalarında Koşullu Erişim Uygulama Denetimini Kullanma](/cloud-app-security/proxy-deployment-aad#configure-integration-with-azure-ad)|Bu, IdP'nizi (Azure AD) Bulut için Defender Uygulamaları ile çalışacak şekilde yapılandırılır.|
||||

Bu sonraki tabloda, tüm SaaS uygulamalarını korumak için oluşturabileceğiniz yukarıda gösterilen örnek ilkeler listelenir. Kendi iş, güvenlik ve uyumluluk hedeflerinizi değerlendirip ortamınız için en uygun korumayı sağlayan ilkeler oluşturduğunuzdan emin olun.

|Koruma düzeyi|Ilkesi|
|---|---|
|Başlangıç noktası|Yönetilmeyen cihazlardan gelen trafiği izleme <p> Yönetilmeyen cihazlardan dosya indirmelerine koruma ekleme|
|Enterprise|Hassas veya yönetilmeyen cihazlardan sınıflandırılmış olarak etiketlenmiş dosyaların indirilmesini engelle (bu yalnızca tarayıcı erişimi sağlar)|
|Özel güvenlik|Tüm cihazlardan sınıflandırılmış olarak etiketlenmiş dosyaların indirilmesini engelle (bu yalnızca tarayıcı erişimi sağlar)|
|||

Koşullu Erişim Uygulama Denetimi'ni ayarlamaya yönelik uçtan uca yönergeler için bkz. [Öne çıkan uygulamalar için Koşullu Erişim Uygulama Denetimi Dağıtma](/cloud-app-security/proxy-deployment-aad). Bu makale, Azure AD gerekli koşullu erişim ilkesini oluşturma ve SaaS uygulamalarınızı test etme işleminde size yol gösterir.

Daha fazla bilgi için bkz. [Microsoft Defender for Cloud Apps Koşullu Erişim Uygulama Denetimi ile uygulamaları koruma](/cloud-app-security/proxy-intro-aad).

## <a name="tune-protection-for-specific-saas-apps"></a>Belirli SaaS uygulamaları için korumayı ayarlama

Ortamınızdaki belirli SaaS uygulamalarına ek izleme ve denetimler uygulamak isteyebilirsiniz. Bulut için Defender Uygulamaları bunu gerçekleştirmenize olanak tanır. Örneğin, ortamınızda Box gibi bir uygulama yoğun bir şekilde kullanılıyorsa ek denetimler uygulamak mantıklıdır. Öte yandan hukuk veya finans departmanınız hassas iş verileri için belirli bir SaaS uygulaması kullanıyorsa bu uygulamalara ek koruma hedefleyebilirsiniz.

Örneğin, Box ortamınızı şu yerleşik anomali algılama ilkesi şablonlarıyla koruyabilirsiniz:

- Anonim IP adreslerinden etkinlik
- Seyrek görülen ülkeden etkinlik
- Şüpheli IP adreslerinden etkinlik
- İmkansız seyahat
- Sonlandırılan kullanıcı tarafından gerçekleştirilen etkinlik (IdP olarak AAD gerektirir)
- Kötü amaçlı yazılım algılama
- Birden çok başarısız oturum açma girişimi
- Fidye yazılımı etkinliği
- Riskli Oauth Uygulaması
- Olağan dışı dosya paylaşımı etkinliği

Bunlar örnektir. Düzenli olarak ek ilke şablonları eklenir. Belirli uygulamalara ek koruma uygulama örnekleri için bkz. [Bağlı uygulamaları koruma](/cloud-app-security/protect-connected-apps).

[Bulut için Defender Uygulamaları, Box ortamınızın korunmasına nasıl yardımcı olur](/cloud-app-security/protect-box)? Box'ta ve diğer uygulamalarda hassas verilerle iş verilerinizi korumanıza yardımcı olabilecek denetim türlerini gösterir.

## <a name="configure-data-loss-prevention-dlp-to-help-comply-with-data-protection-regulations"></a>Veri koruma düzenlemelerine uymaya yardımcı olmak için veri kaybı önlemeyi (DLP) yapılandırma

Bulut için Defender Uygulamalar, uyumluluk düzenlemeleri için koruma yapılandırmaya yönelik değerli bir araç olabilir. Bu durumda, bir düzenlemenin geçerli olduğu belirli verileri aramak için belirli ilkeler oluşturur ve her ilkeyi uygun eylemi gerçekleştirecek şekilde yapılandırabilirsiniz.

Aşağıdaki çizim ve tablo, Genel Veri Koruma Yönetmeliği'ne (GDPR) uymaya yardımcı olmak için yapılandırılabilir ilke örnekleri sağlar. Bu örneklerde ilkeler belirli verileri arar. Verilerin duyarlılığına bağlı olarak, her ilke uygun eylemi gerçekleştirecek şekilde yapılandırılır.

:::image type="content" source="../../media/microsoft-365-policies-configurations/mcas-dlp.png" alt-text="Veri kaybı önleme için Bulut için Defender Uygulamaları ilkeleri sayfası" lightbox="../../media/microsoft-365-policies-configurations/mcas-dlp.png":::

|Koruma düzeyi|Örnek ilkeler|
|---|---|
|Başlangıç noktası|Bu hassas bilgi türünü ("Kredi Kartı Numarası") içeren dosyalar kuruluş dışında paylaşıldığında uyarı <p> >Bu hassas bilgi türünü ("Kredi kartı numarası") içeren dosyaların yönetilmeyen cihazlara indirilmelerini engelle|
|Enterprise|Bu hassas bilgi türünü ("Kredi kartı numarası") içeren dosyaların yönetilen cihazlara indirilmelerini koruma <p> Bu hassas bilgi türünü ("Kredi kartı numarası") içeren dosyaların yönetilmeyen cihazlara indirilmelerini engelle <p> Bu etiketlerin üzerinde bulunan bir dosya OneDrive İş veya Box'a yüklendiğinde uyarı (Müşteri verileri, İnsan Kaynakları: Maaş Verileri,İnsan Kaynakları, Çalışan verileri)|
|Özel güvenlik|Bu etikete ("Yüksek oranda sınıflandırılmış") sahip dosyalar yönetilen cihazlara indirildiğinde uyarı verme <p> Yönetilmeyen cihazlara bu etikete ("Yüksek oranda sınıflandırılmış") sahip dosyaların indirilmelerini engelle|
|||

## <a name="next-steps"></a>Sonraki adımlar

Bulut için Defender Uygulamalarını kullanma hakkında daha fazla bilgi [için Microsoft Defender for Cloud Apps belgelerine bakın](/defender-cloud-apps/).
