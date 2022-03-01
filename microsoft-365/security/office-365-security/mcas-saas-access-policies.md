---
title: SaaS uygulamaları için Bulut Uygulamaları için Önerilen Microsoft Defender ilkeleri - Microsoft 365 Kurumsal | Microsoft Docs
description: Bulut Uygulamaları için Microsoft Defender ile tümleştirme için önerilen ilkeleri açıklar.
author: BrendaCarter
manager: laurawi
ms.prod: microsoft-365-enterprise
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
ms.openlocfilehash: 8d94207be88bd7c9e070057ac1790845a3be17ca
ms.sourcegitcommit: 07405a81513d1c63071a128b9d5070d3a3bfe1cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006812"
---
# <a name="recommended-microsoft-defender-for-cloud-apps-policies-for-saas-apps"></a>SaaS uygulamaları için Bulut Uygulamaları için Önerilen Microsoft Defender ilkeleri

Bulut Uygulamaları için Microsoft Defender, SaaS uygulamalarıyla indirmeleri engelleme, karşıya yüklemeler, kopyalama ve yapıştırma ve yazdırma gibi gerçek zamanlı olarak gerçek zamanlı izleme ve denetime olanak sağlayan Azure AD koşullu erişim ilkelerine yönelik derlemeler sunar. Bu özellik, kurumsal kaynaklara yönetim dışı cihazlardan veya konuk kullanıcılar tarafından erişilma gibi yapısal risk taşıyan oturumlara güvenlik ekler.

Bulut Uygulamaları için Defender, Microsoft Bilgi Koruması ile yerel olarak tümleştirilmiştir, hassas bilgi türleri ve duyarlılık etiketlerine dayalı hassas verileri bulmak ve uygun önlemleri almak için gerçek zamanlı içerik incelemesi sağlar.

Bu kılavuz, bu senaryolara yönelik öneriler içerir:

- SaaS uygulamalarını IT yönetimine getirme
- Belirli SaaS uygulamaları için korumayı ayarlama
- Veri koruma düzenlemelerine uymaya yardımcı olmak için veri kaybı önleme (DLP) ayarlarını yapılandırma

## <a name="bring-saas-apps-into-it-management"></a>SaaS uygulamalarını IT yönetimine getirme

SaaS uygulamalarını yönetmek için Bulut Uygulamaları için Defender'ı kullanmanın ilk adımı, bunları keşfetmek ve ardından bu uygulamaları Azure AD kiracınıza eklemektir. Keşifle ilgili yardıma ihtiyacınız varsa bkz [. Ağda SaaS uygulamalarını keşfetme ve yönetme](/cloud-app-security/tutorial-shadow-it). Uygulamaları budikten sonra, [bunları Azure AD kiracınıza ekleyin](/azure/active-directory/manage-apps/add-application-portal).

Aşağıdakini yaparak bunları yönetmeye başlayabilirsiniz:

1. İlk olarak, Azure AD'de yeni bir koşullu erişim ilkesi oluşturun ve bunu "Koşullu Erişim Uygulama Denetimi Kullan" olarak yapılandırın. Bu işlem, isteği Bulut Uygulamaları için Defender'a yeniden yönlendirer. Tek bir ilke oluşturabilir ve tüm SaaS uygulamalarını bu ilkeye  eklersiniz.
1. Ardından Bulut Uygulamaları için Defender'da oturum ilkeleri oluşturun. Uygulamak istediğiniz her denetim için bir ilke oluşturun.

SaaS uygulamalarına izinler normalde uygulamaya erişim için iş ihtiyacı temel a dayalıdır. Bu izinler son derece dinamik olabilir. Bulut Uygulamaları için Defender ilkelerinin kullanılması, kullanıcıların başlangıç noktası, kurumsal veya özel güvenlik korumasıyla ilişkilendirilmiş bir Azure AD grubuna atanmış olup olmadığı bakılmaksızın uygulama verilerine koruma sağlar.

SaaS uygulamaları koleksiyonunuz genelindeki verileri korumak için, aşağıdaki diyagramda gerekli Azure AD koşullu erişim ilkesi ile Bulut Uygulamaları için Defender'da oluşturabilirsiniz önerilen ilkeler yer almaktadır. Bu örnekte, Bulut Uygulamaları için Defender'da oluşturulan ilkeler, yönetmekte olduğu tüm SaaS uygulamaları için geçerlidir. Bu denetimler, cihazların yönetil olup olmadığının yanı sıra dosyalara zaten uygulanmış olan duyarlılık etiketlerine bağlı olarak uygun denetimleri uygulamak üzere tasarlanmıştır.

:::image type="content" source="../../media/microsoft-365-policies-configurations/mcas-manage-saas-apps-2.png" alt-text="Bulut Uygulamaları için Defender'da SaaS uygulamalarını yönetmeye yönelik ilkeler." lightbox="../../media/microsoft-365-policies-configurations/mcas-manage-saas-apps-2.png":::

Aşağıdaki tabloda, Azure AD'de oluşturmanız gereken yeni koşullu erişim ilkesi listeledir.

|Koruma düzeyi|İlke|Daha fazla bilgi|
|---|---|---|
|Tüm koruma düzeyleri|[Bulut Uygulamaları için Defender'da Koşullu Erişim Uygulama Denetimi'yi kullanma](/cloud-app-security/proxy-deployment-aad#configure-integration-with-azure-ad)|Bu, IdP'nizi (Azure AD) Bulut Uygulamaları için Defender ile çalışacak şekilde yapılandırıyor.|
||||

Sonraki tabloda, yukarıda gösterilen ve tüm SaaS uygulamalarını korumak için oluşturabilirsiniz örnek ilkeleri listelemektedir. Kendi iş, güvenlik ve uyumluluk hedeflerinizi değerlendirmeye ve ardından ortamınıza en uygun korumayı sağlayan ilkeler oluşturmanıza emin olun.

|Koruma düzeyi|İlke|
|---|---|
|Başlangıç noktası|Unmanaged cihazlarından gelen trafiği izleme <p> Unmanaged cihazlarından dosya indirmeleri için koruma ekleme|
|Enterprise|Hassas ya da sınıflandırılmış cihazlarla etiketlenmiş dosyaların indir olmasını engelleme (bu, yalnızca tarayıcı erişimi sağlar)|
|Özel güvenlik|Tüm cihazlardan sınıflandırılmış dosya indirmeyi engelle (bu, yalnızca tarayıcı erişimi sağlar)|
|||

Koşullu Erişim Uygulama Denetimi'yi ayarlamaya ilişkin son yönergeler için bkz. Öne çıkan uygulamalar için [Koşullu Erişim Uygulama Denetimi'ne Dağıtma](/cloud-app-security/proxy-deployment-aad). Bu makale, Azure AD'de gerekli koşullu erişim ilkesi oluşturma ve SaaS uygulamalarınızı test etme sürecinde size yol sunar.

Daha fazla bilgi için bkz [. Bulut Uygulamaları için Microsoft Defender ile Uygulamaları Koşullu Erişim Uygulama Denetimi ile koruma](/cloud-app-security/proxy-intro-aad).

## <a name="tune-protection-for-specific-saas-apps"></a>Belirli SaaS uygulamaları için korumayı ayarlama

Ortamınıza belirli SaaS uygulamalarına ek izleme ve denetimler uygulamak iyi bir uygulama olabilir. Bulut Uygulamaları için Defender bunu gerçekleştirmeye olanak sağlar. Örneğin Box gibi bir uygulama ortamınıza yoğun bir şekilde kullanılıyorsa, ek denetimler uygulamak mantıklı olur. Hukuk veya finans departmanınız hassas iş verileri için belirli bir SaaS uygulaması kullanıyorsa, bu uygulamalara fazladan koruma hedeflebilirsiniz.

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

[Bulut Uygulamaları için Defender'ın Box](/cloud-app-security/protect-box) ortamınızı korumaya nasıl yardımcı olduğu, Box'ta iş verilerinizi ve hassas verilerle diğer uygulamaları korumanıza yardımcı olacak denetim türlerini gösterir.

## <a name="configure-data-loss-prevention-dlp-to-help-comply-with-data-protection-regulations"></a>Veri koruma düzenlemelerine uymaya yardımcı olmak için veri kaybı önleme (DLP) ayarlarını yapılandırma

Bulut Uygulamaları için Defender, uyumluluk düzenlemelerine ilişkin korumayı yapılandırmak için değerli bir araç olabilir. Bu durumda, bir düzenlemenin uygulandığı belirli verileri aramanız ve her ilkeyi uygun önlemleri alacak şekilde yapılandırmanız için belirli ilkeler oluşturabilirsiniz.

Aşağıdaki çizimde ve tabloda, Genel Veri Koruma Yönetmeliğine (GDPR) uymak üzere yapılandırılan ilkelere çeşitli örnekler verilmiştir. Bu örneklerde, ilkeler belirli verileri aramada kullanılır. Verilerin duyarlılığına bağlı olarak, her ilke uygun önlemleri alacak şekilde yapılandırılır.

:::image type="content" source="../../media/microsoft-365-policies-configurations/mcas-dlp.png" alt-text="Veri kaybını önlemeye yönelik Bulut Uygulamaları için Örnek Defender ilkeleri." lightbox="../../media/microsoft-365-policies-configurations/mcas-dlp.png":::

|Koruma düzeyi|Örnek ilkeler|
|---|---|
|Başlangıç noktası|Bu hassas bilgi türünü içeren dosyalar ("Kredi Kartı Numarası") kuruluşun dışında paylaşılırken uyarı <p> >Bu hassas bilgi türünü içeren dosyaların indirilmelerini engelle ("Kredi kartı numarası"), yani devre dışı bırakıldı cihazlara|
|Enterprise|Yönetilen cihazlara bu hassas bilgi türünü ("Kredi kartı numarası") içeren dosya indirmelerini koruma <p> Bu hassas bilgi türünü içeren dosyaların indirilmelerini engelle ("Kredi kartı numarası"), tarafından engellenen cihazlara <p> Bu etiketlerle ilgili bir dosya Posta Kutusu veya Box'a OneDrive İş uyarı (Müşteri verileri, İnsan Kaynakları: Maaş Verileri, İnsan Kaynakları, Çalışan verileri)|
|Özel güvenlik|Bu etikete sahip dosyaların ("Çok fazla sınıflandırılmış") yönetilen cihazlara indirildikten sonra uyarı <p> Bu etiketle dosyaların indirilmelerini engelle ("Çok fazla sınıflandırılmış") ve işlenemeyen cihazlara|
|||

## <a name="next-steps"></a>Sonraki adımlar

Bulut Uygulamaları için Defender'ı kullanma hakkında daha fazla bilgi için bkz. [Bulut Uygulamaları için Microsoft Defender belgeleri](//cloud-app-security/).
