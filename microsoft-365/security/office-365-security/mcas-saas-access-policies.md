---
title: SaaS Microsoft Defender for Cloud Apps için önerilen ilkeler - Microsoft 365 Kurumsal | Microsoft Docs
description: MICROSOFT DEFENDER FOR CLOUD APPS ile tümleştirme için önerilen ilkeler açık Microsoft Defender for Cloud Apps.
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
ms.openlocfilehash: 7cda1669b4f8441d13f92b09d7390e31f4add529
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472297"
---
# <a name="recommended-microsoft-defender-for-cloud-apps-policies-for-saas-apps"></a>SaaS Microsoft Defender for Cloud Apps önerilen güvenlik ilkeleri

Microsoft Defender for Cloud Apps engelleme, karşıya yüklemeler, kopyalama ve yapıştırma ve yazdırma gibi SaaS uygulamalarıyla gerçek zamanlı olarak gerçek zamanlı izleme ve denetime olanak sağlayan Azure AD koşullu erişim ilkelerine yönelik bir yapıya sahip olur. Bu özellik, kurumsal kaynaklara yönetim dışı cihazlardan veya konuk kullanıcılar tarafından erişilma gibi yapısal risk taşıyan oturumlara güvenlik ekler.

Bulut için Defender Uygulamalar aynı zamanda Microsoft Bilgi Koruması ile yerel olarak tümleştirilmiştir, hassas bilgi türleri ve duyarlılık etiketlerine dayalı hassas verileri bulmak ve uygun önlemleri almak için gerçek zamanlı içerik incelemesi sağlar.

Bu kılavuz, bu senaryolara yönelik öneriler içerir:

- SaaS uygulamalarını IT yönetimine getirme
- Belirli SaaS uygulamaları için korumayı ayarlama
- Veri koruma düzenlemelerine uymaya yardımcı olmak için veri kaybı önleme (DLP) ayarlarını yapılandırma

## <a name="bring-saas-apps-into-it-management"></a>SaaS uygulamalarını IT yönetimine getirme

SaaS uygulamalarını yönetmek Bulut için Defender Uygulamaları'nın kullanımında ilk adım bunları keşfetmek ve ardından bunları Azure AD kiracınıza eklemektir. Keşifle ilgili yardıma ihtiyacınız varsa bkz [. Ağda SaaS uygulamalarını keşfetme ve yönetme](/cloud-app-security/tutorial-shadow-it). Uygulamaları budikten sonra, [bunları Azure AD kiracınıza ekleyin](/azure/active-directory/manage-apps/add-application-portal).

Aşağıdakini yaparak bunları yönetmeye başlayabilirsiniz:

1. İlk olarak, Azure AD'de yeni bir koşullu erişim ilkesi oluşturun ve bunu "Koşullu Erişim Uygulama Denetimi Kullan" olarak yapılandırın. Bu, isteği Diğer Uygulamalar'a Bulut için Defender yönlendirmektir. Tek bir ilke oluşturabilir ve tüm SaaS uygulamalarını bu ilkeye  eklersiniz.
1. Ardından, Bulut için Defender Uygulamaları'nın içinde oturum ilkeleri oluşturun. Uygulamak istediğiniz her denetim için bir ilke oluşturun.

SaaS uygulamalarına izinler normalde uygulamaya erişim için iş ihtiyacı temel a dayalıdır. Bu izinler son derece dinamik olabilir. Bulut için Defender uygulamalarının kullanılması, kullanıcıların başlangıç noktası, kurumsal veya özel güvenlik korumasıyla ilişkilendirilmiş bir Azure AD grubuna atanmış olup olmadığı bakılmaksızın, uygulama verilerine koruma sağlar.

SaaS uygulamaları koleksiyonunuz genelinde verileri korumak için, aşağıdaki diyagramda gerekli Azure AD koşullu erişim ilkesiyle birlikte, Farklı Uygulamalar'da oluşturabilirsiniz önerilen ilkeler Bulut için Defender yer almaktadır. Bu örnekte, Uygulamalar'da Bulut için Defender ilkeler yönetmekte olduğu tüm SaaS uygulamaları için geçerlidir. Bu denetimler, cihazların yönetil olup olmadığının yanı sıra dosyalara zaten uygulanmış olan duyarlılık etiketlerine bağlı olarak uygun denetimleri uygulamak üzere tasarlanmıştır.

:::image type="content" source="../../media/microsoft-365-policies-configurations/mcas-manage-saas-apps-2.png" alt-text="Bulut için Defender Apps'te SaaS uygulamalarını yönetme ilkeleri" lightbox="../../media/microsoft-365-policies-configurations/mcas-manage-saas-apps-2.png":::

Aşağıdaki tabloda, Azure AD'de oluşturmanız gereken yeni koşullu erişim ilkesi listeledir.

|Koruma düzeyi|İlke|Daha fazla bilgi|
|---|---|---|
|Tüm koruma düzeyleri|[Koşullu Erişim Uygulama Denetimi'Bulut için Defender kullanma](/cloud-app-security/proxy-deployment-aad#configure-integration-with-azure-ad)|Bu, IdP'nizi (Azure AD) uygulama uygulamalarıyla çalışacak Bulut için Defender yapılandırıyor.|
||||

Sonraki tabloda, yukarıda gösterilen ve tüm SaaS uygulamalarını korumak için oluşturabilirsiniz örnek ilkeleri listelemektedir. Kendi iş, güvenlik ve uyumluluk hedeflerinizi değerlendirmeye ve ardından ortamınıza en uygun korumayı sağlayan ilkeler oluşturmanıza emin olun.

|Koruma düzeyi|İlke|
|---|---|
|Başlangıç noktası|Unmanaged cihazlarından gelen trafiği izleme <p> Unmanaged cihazlarından dosya indirmeleri için koruma ekleme|
|Enterprise|Hassas ya da sınıflandırılmış cihazlarla etiketlenmiş dosyaların indir olmasını engelleme (bu, yalnızca tarayıcı erişimi sağlar)|
|Özel güvenlik|Tüm cihazlardan sınıflandırılmış dosya indirmeyi engelle (bu, yalnızca tarayıcı erişimi sağlar)|
|||

Koşullu Erişim Uygulama Denetimi'yi ayarlamaya ilişkin son yönergeler için bkz. Öne çıkan uygulamalar için [Koşullu Erişim Uygulama Denetimi'ne Dağıtma](/cloud-app-security/proxy-deployment-aad). Bu makale, Azure AD'de gerekli koşullu erişim ilkesi oluşturma ve SaaS uygulamalarınızı test etme sürecinde size yol sunar.

Daha fazla bilgi için bkz[. Koşullu Erişim Uygulama denetimi Microsoft Defender for Cloud Apps uygulamaları koruma](/cloud-app-security/proxy-intro-aad).

## <a name="tune-protection-for-specific-saas-apps"></a>Belirli SaaS uygulamaları için korumayı ayarlama

Ortamınıza belirli SaaS uygulamalarına ek izleme ve denetimler uygulamak iyi bir uygulama olabilir. Bulut için Defender uygulamaları bunu gerçekleştirmene olanak sağlar. Örneğin Box gibi bir uygulama ortamınıza yoğun bir şekilde kullanılıyorsa, ek denetimler uygulamak mantıklı olur. Hukuk veya finans departmanınız hassas iş verileri için belirli bir SaaS uygulaması kullanıyorsa, bu uygulamalara fazladan koruma hedeflebilirsiniz.

Örneğin, bu tür yerleşik anormal algılama ilkesi şablonlarıyla Box ortamınızı koruyabilirsiniz:

- Anonim IP adreslerinden etkinlik
- Sık kullanılmayan ülkenin etkinliği
- Şüpheli IP adreslerinden etkinlik
- Olanaksız seyahat
- Son kullanıcı tarafından gerçekleştirilen etkinlik (IdP AAD gerekir)
- Kötü amaçlı yazılım algılama
- Birden çok başarısız oturum açma denemesi
- Fidye yazılımı etkinliği
- Risky Oauth Uygulaması
- Olağan dışı dosya paylaşım etkinliği

Bunlar örneklerdir. Ek ilke şablonları düzenli olarak eklenir. Belirli uygulamalara ek koruma uygulama örnekleri için bkz [. Bağlı uygulamaları koruma](/cloud-app-security/protect-connected-apps).

[Uygulama Bulut için Defender, Box](/cloud-app-security/protect-box) ortamınızı korumaya nasıl yardımcı olur? Box'ta ve diğer uygulamalarda hassas verilerle iş verilerinizi korumanıza yardımcı olacak denetim türlerini gösterir.

## <a name="configure-data-loss-prevention-dlp-to-help-comply-with-data-protection-regulations"></a>Veri koruma düzenlemelerine uymaya yardımcı olmak için veri kaybı önleme (DLP) ayarlarını yapılandırma

Bulut için Defender Uygulamaları uyumluluk düzenlemelerine karşı korumayı yapılandırmak için değerli bir araç olabilir. Bu durumda, bir düzenlemenin uygulandığı belirli verileri aramanız ve her ilkeyi uygun önlemleri alacak şekilde yapılandırmanız için belirli ilkeler oluşturabilirsiniz.

Aşağıdaki çizimde ve tabloda, Genel Veri Koruma Yönetmeliğine (GDPR) uymak üzere yapılandırılan ilkelere çeşitli örnekler verilmiştir. Bu örneklerde, ilkeler belirli verileri aramada kullanılır. Verilerin duyarlılığına bağlı olarak, her ilke uygun önlemleri alacak şekilde yapılandırılır.

:::image type="content" source="../../media/microsoft-365-policies-configurations/mcas-dlp.png" alt-text="Veri Bulut için Defender önleme sayfası için en iyi uygulama ilkeleri" lightbox="../../media/microsoft-365-policies-configurations/mcas-dlp.png":::

|Koruma düzeyi|Örnek ilkeler|
|---|---|
|Başlangıç noktası|Bu hassas bilgi türünü içeren dosyalar ("Kredi Kartı Numarası") kuruluşun dışında paylaşılırken uyarı <p> >Bu hassas bilgi türünü içeren dosyaların indirilmelerini engelle ("Kredi kartı numarası"), yani devre dışı bırakıldı cihazlara|
|Enterprise|Yönetilen cihazlara bu hassas bilgi türünü ("Kredi kartı numarası") içeren dosya indirmelerini koruma <p> Bu hassas bilgi türünü içeren dosyaların indirilmelerini engelle ("Kredi kartı numarası"), tarafından engellenen cihazlara <p> Bu etiketlerle ilgili bir dosya Posta Kutusu veya Box'a OneDrive İş uyarı (Müşteri verileri, İnsan Kaynakları: Maaş Verileri, İnsan Kaynakları, Çalışan verileri)|
|Özel güvenlik|Bu etikete sahip dosyaların ("Çok fazla sınıflandırılmış") yönetilen cihazlara indirildikten sonra uyarı <p> Bu etiketle dosyaların indirilmelerini engelle ("Çok fazla sınıflandırılmış") ve işlenemeyen cihazlara|
|||

## <a name="next-steps"></a>Sonraki adımlar

Bulut için Defender Uygulamalarını kullanma hakkında daha fazla bilgi için bkz[. Microsoft Defender for Cloud Apps bakın](//cloud-app-security/).
