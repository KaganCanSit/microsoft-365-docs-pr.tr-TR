---
title: Cihazları tek bir Intune
ms.author: bcarter
author: brendacarter
f1.keywords:
- enroll devices into Intune
- manage device endpoints
- zero trust deployment stack
- device management with zero trust
manager: dougeby
audience: ITPro
ms.topic: article
description: Uç nokta cihazlarınızı Microsoft Intune ve güvenlik mimarisinin bir parçası olarak Sıfır Güven ve uzak çalışanlar için koruma sağlarken fidye yazılımlarına karşı koruma sağlar.
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-overview
ms.custom: ''
keywords: ''
ms.openlocfilehash: 2ca980a3f4f66b1b2d0a838f16c6ac7f138bc979
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64570095"
---
# <a name="manage-devices-with-intune-overview"></a>Hızlı Genel Bakış ile Intune yönetme

Kurumsal düzeyde güvenliğin temel bileşenleri arasında cihazları yönetme ve koruma vardır. İster güvenlik mimarisi Sıfır Güven, fidye yazılımlarına karşı ortamınızı bağlantılara açıklaştırın veya uzak çalışanları desteklemek için korumalar inşa ediyor olun, cihazları yönetmek stratejinin bir parçasıdır.
Microsoft 365 cihazları yönetmeye ve korumaya yönelik çeşitli araçlar ve metodolojiler içerir ama bu kılavuz Microsoft'un Cihaz Yönetimi'ne yönelik önerilerini Microsoft Intune. Aşağıdakiler sizin için doğru kılavuz olur:

- Cihazları Azure AD Join (Karma Azure AD Intune dahil) aracılığıyla Intune'e kaydetmeyi plan edin.
- Cihazları el ile mobil cihaza Intune.
- Uygulamalar ve veriler için koruma uygulama planları olan BYOD cihazlarına izin verin ve/veya bu cihazları yönetime kaydettirin.

Öte yandan, ortamınız birlikte yönetim planları (örneğin, proje Microsoft Endpoint Configuration Manager) varsa, bkz[.](/mem/configmgr/comanage/) Organizasyonunıza en uygun yolu geliştirmek için birlikte yönetim belgeleri. Ortamınıza proje planları Windows 365 Bulut PC, Windows 365 Enterprise [için](/windows-365/enterprise/) belgelerinize bakın.

## <a name="why-manage-endpoints"></a>Uç noktaları neden yönetebilirsiniz?

Modern kuruluş, verilerine erişen inanılmaz çeşitli uç noktalara sahiptir. Bu kurulum muazzam bir saldırı yüzeyi oluşturur ve bunun sonucunda uç noktalar sizin güvenlik stratejinizin en zayıf Sıfır Güven olabilir.

Çoğunlukla, dünya uzak veya karma bir iş modeline kayarak gerekli olarak hareket ediyor ve kullanıcılar her yerden, her cihazdan, tarihe göre daha çok çalışıyor. Saldırganlar bu değişiklikden yararlanmak için taktiklerini hızlı bir şekilde ayariyor. Birçok kuruluş, bu yeni iş zorluklarında ilerlerken kısıtlanmış kaynakla karşılaşmaktadır. Neredeyse gece, şirketler dijital dönüşümü hızlandırmıştır. Basitçe ifade etmek gerekirse, kişilerin çalışma yolu değişmiştir; artık şirket kaynakları genel kaynaklarına yalnızca ofisten ve şirkete ait cihazlardan erişmeyi beklemeyeceksiniz.

Şirket kaynaklarınıza erişen uç noktalara görünürlük kazanmak, cihaz stratejinizin ilk Sıfır Güven adımıdır. Mobil cihazlar çoğunlukla izlemez ve koruma olmadan devam ederken şirketler bilgisayarları güvenlik açıklarından ve saldırılardan önceden korur. Verilerinizi risklere karşı açık durumuna getirmemenizi sağlamak için, kuruluş ilkesine göre uygun erişim düzeyini sağlamak için her uç noktayı riskler için izlememiz ve ayrıntılı erişim denetimleri ihtiyacımız vardır. Örneğin, kişisel bir cihazın güvenliği engellenirse, kurumsal uygulamaların bilinen güvenlik açıklarına açık kalmaması için erişimi engelleyebilirsiniz.

Bu makale dizisi, kaynaklarınıza erişen cihazları yönetmek için önerilen bir süreçte yol sunar. Önerilen adımları izlediğinizde, organizasyonunız cihazlarınız ve erişim sağlandık kaynaklar için çok gelişmiş koruma elde eder.

## <a name="implementing-the-layers-of-protection-on-and-for-devices"></a>Cihazlara ve cihazlara koruma katmanları uygulama

Cihazlar ve cihazlara yönelik verileri ve uygulamaları korumak çok katmanlı bir işlemdir. Unmanaged cihazlarda kazanabilirsiniz bazı korumalar vardır. Cihazları yönetime kaydettikten sonra, daha gelişmiş denetimler gerçekleştirebilirsiniz. Uç noktalarınıza tehdit koruması dağıtıldığında, daha da fazla içgörü ve bazı saldırıları otomatik olarak düzeltme olanağı elde edersiniz. Son olarak, organizasyonunız hassas verileri tanımlama, sınıflandırma ve etiketler uygulama ve veri kaybı önleme ilkelerini yapılandırma çalışmalarını başlattısa, uç noktalarınız üzerinde veriler için daha da ayrıntılı koruma elde edinebilirsiniz.

Aşağıdaki diyagramda, bu ortama Sıfır Güven SaaS uygulamalarının ve Microsoft 365 yüksek güvenlik Microsoft 365 için yapı taşlarını gösteren yapı taşları yer almaktadır. Cihazlarla ilgili öğeler 1'den 7'ye kadar numara olur. Bunlar, koruma cihazı yöneticilerinin başaracakları diğer yöneticilerle eşgüdüm altına alınan katmanlardır.

![Microsoft 365 Sıfır Güven yığını](../media/devices/m365-zero-trust-deployment-stack-devices.png#lightbox)

Bu şekilde:

|&nbsp;|Adım|Açıklama|Lisans gereksinimleri|
|---|---|---|---|
|1|Kimlik ve cihaz erişim Sıfır Güven başlangıç noktası ilkelerini yapılandırma|Düzey 2 Uygulama Koruma [İlkeleri (UYGULAMA) veri korumasını uygulamak için kimlik yöneticinizle birlikte çalışma](manage-devices-with-intune-app-protection.md). Bu ilkeler cihazları yönetmenizi gerektirmez. UYGULAMA ilkelerini aşağıdaki Intune. Kimlik yöneticiniz onaylı uygulamalar gerektiren bir Koşullu Erişim ilkesi yapılandırıyor.|E3, E5, F1, F3, F5|
|2|Cihazları yönetime kaydedin|Bu görevin uygulanması için daha fazla planlama ve zaman gerekir. Bu araç en iyi Intune tümleştirme sağladığı için Microsoft, cihazları kaydetmek için Intune kullanılması önerilir. Platforma bağlı olarak, cihazları kaydetmek için birkaç seçenek vardır. Örneğin, Windows cihazları Azure AD Join kullanılarak veya AutoPilot kullanılarak kaydedebilirsiniz. Her bir platforma yönelik seçenekleri gözden geçirmeniz ve ortamınıza en uygun kayıt seçeneğinin hangisi olduğuna karar vermeniz gerekir. Daha [fazla bilgi için bkz. 3. Adım: Cihazları yönetime](manage-devices-with-intune-enroll.md) kaydetme.|E3, E5, F1, F3, F5|
|3|Uyumluluk ilkelerini yapılandırma|Uygulamalarınıza ve verilerinize erişen cihazların en düşük gereksinimleri (örneğin, cihazlar parola veya pin korumalı) karşı olduğundan ve işletim sisteminin güncel olduğundan emin olmak istiyor olun. Uyumluluk ilkeleri, cihazların karşılaması gereken gereksinimleri tanımlamanın yoludur. [3. Adım. Uyumluluk ilkeleri ayarlamak, bu](manage-devices-with-intune-compliance-policies.md) ilkeleri yapılandırmanıza yardımcı olur.|E3, E5, F3, F5|
|4|Kimlik Enterprise cihaz erişim ilkelerini Sıfır Güven (önerilen) bir kimlik ve cihaz erişimi ilkelerini yapılandırma|Cihazlarınız kaydedilene kadar, kimlik yöneticinizle birlikte çalışarak koşullu Erişim ilkelerini sağlıklı ve uyumlu cihazlar gerektirecek [şekilde ayarlamaları sebilirsiniz](manage-devices-with-intune-require-compliance.md).|E3, E5, F3, F5|
|5|Yapılandırma profillerini dağıtma|Bir cihazı yalnızca uyumlu olarak işaret eden veya yapılandırılan ölçütlere dayalı olmayan cihaz uyumluluk ilkelerinin aksine, yapılandırma profilleri aslında cihaz ayarlarının yapılandırmasını değiştirir. Siber tehditlere karşı cihazlara yönelik yapılandırma ilkelerini kullanabilirsiniz. Bkz [. Adım 5. Yapılandırma profillerini dağıtın](manage-devices-with-intune-configuration-profiles.md).|E3, E5, F3, F5|
|6|Cihaz riskini ve güvenlik taban çizgileriyle uyumluluğu izleme|Bu adımda, diğer Intune bağlan Uç Nokta için Microsoft Defender. Bu tümleştirmeyle, cihaz riskini erişim koşulu olarak izleyebilirsiniz. Riskli durumda bulunan cihazlar engellenir. Ayrıca, güvenlik taban çizgileriyle uyumluluğu da izleyebilirsiniz. Bkz [. Adım 6. Cihaz riskini ve güvenlik taban çizgilerine uyumluluğu takip edin](manage-devices-with-intune-monitor-risk.md).|E5, F5|
|7|Bilgi koruma yetenekleriyle veri kaybı önleme (DLP) uygulayın|Organizasyonunız hassas verileri tanımlama ve belgeleri etiketleme çalışmalarını başlattısa, cihazlarınız üzerinde hassas bilgileri ve belgeleri korumak için bilgi koruma [yöneticinizle birlikte çalışabilirsiniz](manage-devices-with-intune-dlp-mip.md).|E5, F5 uyumluluk eklentisi|

## <a name="coordinating-endpoint-management-with-zero-trust-identity-and-device-access-policies"></a>Kimlik ve cihaz erişimi ilkeleriyle Sıfır Güven uç nokta yönetimini birlikte uygulama

Bu kılavuz, kimlik ve cihaz erişim Sıfır Güven [önerilen kılavuzlarla sıkı bir şekilde eşgüdüm sağlar](../security/office-365-security/microsoft-365-policies-configurations.md). Kimlik ekibimizle birlikte çalışarak, Azure AD'de Koşullu Erişim Intune'te yapılandırmış olacağınız korumayı gerçekleştireceksiniz.

Aşağıda, Intune/MEM'de yapacaksınız çalışmayla ilgili adım açıklamalı olarak ayarlanmış önerilen ilkeyi ve Azure AD'de eşgüdümlü olarak yardım edecek ilgili Koşullu Erişim ilkelerinin bir çizimi ve ve hazır bir şekilde gösterilmiştir.

[![Sıfır Güven ve cihaz erişimi ilkelerini doğrulama](../media/devices/identity-device-overview-steps.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-overview-steps.png)

Bu şekilde:

- 1. Adım'da Düzey 2 Uygulama Koruma İlkelerini [(UYGULAMA)](manage-devices-with-intune-app-protection.md) uygulama ilkeleriyle birlikte önerilen veri koruma düzeyini yapılandırabilirsiniz. Daha sonra, ilgili Koşullu Erişim kuralını bu korumanın kullanımını gerektirecek şekilde yapılandırmak için kimlik ekibiyle birlikte çalışırsanız.
- 2, 3 ve 4'lerde, cihazları Intune/MEM ile yönetime kaydettir, cihaz uyumluluk ilkeleri tanımlar ve sonra ilgili Koşullu Erişim kuralını yalnızca uyumlu cihazlara erişim izni verecek şekilde yapılandırmak için kimlik ekibimizle birlikte çalışırsanız.

<!---
## Managing change with users
--->

## <a name="enrolling-devices-vs-onboarding-devices"></a>Cihazları kaydetme ve cihaz ekleme

Bu kılavuza uyarsanız, cihazları yönetime kaydetmek için Intune (veya başka bir araç) kullandıracak ve cihazları iki hizmet için kullanıyabilirsiniz:

- Uç Nokta için Defender
- Uç nokta DLP

Aşağıdaki çizimde, bu iki tablo Intune.

![Kaydolma ve cihaz ekleme işlemi](../media/devices/devices-enroll-onboard-process.png#lightbox)

Çizimde:

1. Diğer cihazlarla cihazları yönetime Intune.
2. Uç Intune Defender'a cihaz ekleme için Cihaz Ekleme'ye kullanın.
3. Uç nokta için Defender'a dahil olan cihazlar, Uç nokta DLP dahil olmak Microsoft 365 uyumluluk özellikleri için de ekli olarak kullanılır.

Yalnızca diğer Intune cihazların yönetiminde olduğunu unutmayın. Ekleme, bir cihazın belirli bir hizmetle bilgi paylaşabilme özelliği anlamına gelir. Aşağıdaki tabloda, cihazları yönetime kaydetme ile belirli bir hizmet için cihazları ekleme arasındaki farklar özetlenmiştir.

|&nbsp;|Kaydol|Onboard|
|---|---|---|
|Açıklama|Kayıt, cihazları yönetmek için geçerlidir. Cihazlar, cihaz yönetimi için Intune veya Configuration Manager.|Ekleme, bir cihazı özellikler kümesi üzerinde belirli bir özelliklerle çalışacak şekilde Microsoft 365. Şu anda ekleme, yazılım Uç Nokta için Microsoft Defender Microsoft uyumluluk özellikleri için geçerlidir. <br/><br/> Diğer Windows, ekleme işlemi Defender'ın çevrimiçi hizmete bağlanmasına ve cihaza uygulanacak ilkeleri kabul etmesinde izin veren Windows Defender'da bir ayarın bağlanması içerir.|
|Kapsam|Bu cihaz yönetim araçları, cihazı güvenlik gibi belirli hedefleri karşılayacak şekilde yapılandırma da dahil olmak üzere tüm cihazı yönetir.|Ekleme, yalnızca geçerli olan hizmetleri etkiler.|
|Önerilen yöntem|Azure Active Directory katıl, cihazları otomatik olarak Intune.|Intune uç nokta için cihaz ekleme için tercih edilen yöntem Windows Defender ve sonuç olarak uyumluluk Microsoft 365 tercih edilir. <br/><br/> Diğer yöntemleri kullanarak uyumluluk özelliklerini Microsoft 365 cihazlar, Uç Nokta için Defender'a otomatik olarak kaydolmaz.|
|Diğer yöntemler|Diğer kayıt yöntemleri cihazın platformuna ve byOD olup olmadığını veya kuruluş tarafından yönetil olup olmadığını bağlıdır.|Cihaz ekleme için diğer yöntemler, önerilen sırada şunlardır: <ul><li>Yapılandırma Yöneticisi</li><li>Diğer mobil cihaz yönetim aracı (cihaz tek bir cihaz tarafından yönetiliyorsa)</li><li>Yerel betik</li><li>Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarını eklemeye uygun VDI yapılandırma paketi</li><li>Grup İlkesi</li></ul>|

## <a name="learning-for-administrators"></a>Learning için sistem yöneticisi

Aşağıdaki kaynaklar yöneticilerin MEM ve MEM'nin kullanımıyla ilgili kavramları öğrenmesi için yardımcı Intune.

[Microsoft Endpoint Manager](/learn/modules/simplify-device-management-with-microsoft-endpoint-manager/) ile cihaz yönetimini basitleştirme Açıklama: Modern yönetim Microsoft Endpoint Manager ve Microsoft 365'daki işletme yönetim araçlarının tüm cihazlarınızı yönetimini nasıl basitleştirebilirsiniz hakkında bilgi edinebilirsiniz.

[Microsoft Intune](/learn/modules/set-up-microsoft-intune/) Ayarlama: Microsoft Intune bir parçası olan Microsoft Endpoint Manager, verimli olmak için kuruluşta çalışan kişilerin cihaz, uygulama ve verileri korumanıza yardımcı olur. Bu modülü tamamladıktan sonra, çalışma Microsoft Intune. Ayarlama; desteklenen yapılandırmaları gözden geçirmeyi, Intune'e kaydolmayı, kullanıcıları ve grupları eklemeyi, kullanıcılara lisans atamayı, yönetici izinlerini atamayı ve MDM yetkilisini ayarlamayı içerir.
