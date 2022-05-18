---
title: cihazları Intune ile yönetme
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
description: Uzak çalışanlar için koruma oluştururken fidye yazılımlarına karşı koruma sağlayarak uç nokta cihazlarınızı Sıfır Güven güvenlik mimarinizin bir parçası olarak Microsoft Intune kaydedin.
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-overview
ms.custom: ''
keywords: ''
ms.openlocfilehash: 218ffa6ba9b2e7a4eb5fcd2f042b77b207ab8594
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65468052"
---
# <a name="manage-devices-with-intune-overview"></a>Intune Genel Bakış ile cihazları yönetme

Kurumsal düzeyde güvenliğin temel bileşenlerinden biri, cihazları yönetmeyi ve korumayı içerir. Sıfır Güven bir güvenlik mimarisi oluştururken, ortamınızı fidye yazılımlarına karşı sağlamlaştırırken veya uzak çalışanları desteklemek için korumalar oluştururken, cihazları yönetmek stratejinin bir parçasıdır.
Microsoft 365, cihazları yönetmeye ve korumaya yönelik çeşitli araçlar ve yöntemler içerirken, bu kılavuz Microsoft Intune kullanarak Microsoft'un önerilerinde yol gösterir. Aşağıdakiler sizin için doğru yoldur:

- Azure AD Join (Karma Azure AD Join dahil) aracılığıyla cihazları Intune kaydetmeyi planlayın.
- Cihazları el ile Intune kaydetmeyi planlayın.
- Uygulamalar ve veriler için koruma uygulama ve/veya bu cihazları Intune kaydetme planlarına sahip KCG cihazlarına izin verin.

Öte yandan, ortamınız Microsoft Endpoint Configuration Manager de dahil olmak üzere ortak yönetim planları içeriyorsa, kuruluşunuz için en iyi yolu geliştirmek için [ortak yönetim belgelerine](/mem/configmgr/comanage/) bakın. Ortamınız Windows 365 Bulut PC planları içeriyorsa, kuruluşunuz için en iyi yolu geliştirmek için [Windows 365 Enterprise belgelerine](/windows-365/enterprise/) bakın.

Dağıtım işlemine genel bir bakış için bu videoyu izleyin.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4F1af]

## <a name="why-manage-endpoints"></a>Uç noktaları neden yönetebilirsiniz?

Modern kuruluş, verilerine erişen inanılmaz çeşitli uç noktalara sahiptir. Bu kurulum çok büyük bir saldırı yüzeyi oluşturur ve sonuç olarak uç noktalar kolayca Sıfır Güven güvenlik stratejinizdeki en zayıf bağlantı haline gelebilir.

Dünya uzak veya hibrit bir iş modeline geçtikten sonra çoğunlukla ihtiyaçlara göre hareket eden kullanıcılar, her yerden, herhangi bir cihazdan, tarihteki her zamankinden daha fazla çalışıyor. Saldırganlar bu değişikliklerden yararlanmak için taktiklerini hızlı bir şekilde ayarlıyor. Birçok kuruluş, bu yeni iş güçlüklerinde gezinirken kısıtlanmış kaynaklarla karşı karşıya kalır. Neredeyse bir gecede şirketler dijital dönüşümü hızlandırdı. Basitçe belirtmek gerekirse, insanların çalışma şekli değişti; artık çok sayıda şirket kaynağına yalnızca ofisten ve şirkete ait cihazlardan erişmeyi beklemiyoruz.

Şirket kaynaklarınıza erişen uç noktaların görünürlüğünü elde etmek, Sıfır Güven cihaz stratejinizin ilk adımıdır. Genellikle şirketler bilgisayarları güvenlik açıklarına ve saldırılara karşı korurken mobil cihazlar genellikle izlenmeyen ve korumasız kalır. Verilerinizi riske atmadığınızdan emin olmak için her uç noktayı risklere karşı izlememiz ve kuruluş ilkesine göre uygun erişim düzeyini sağlamak için ayrıntılı erişim denetimleri kullanmamız gerekir. Örneğin, kişisel bir cihazın jailbreak uygulanmışsa, kurumsal uygulamaların bilinen güvenlik açıklarına maruz kalmadığından emin olmak için erişimi engelleyebilirsiniz.

Bu makale serisi, kaynaklarınıza erişen cihazları yönetmek için önerilen bir işlemde yol gösterir. Önerilen adımları izlerseniz, kuruluşunuz cihazlarınız ve erişecekleri kaynaklar için çok gelişmiş koruma elde eder.

## <a name="implementing-the-layers-of-protection-on-and-for-devices"></a>Cihazlar için ve üzerinde koruma katmanlarını uygulama

Cihazlarda ve cihazlardaki verileri ve uygulamaları korumak çok katmanlı bir işlemdir. Yönetilmeyen cihazlarda kazanabileceğiniz bazı korumalar vardır. Cihazları yönetime kaydettikten sonra daha gelişmiş denetimler uygulayabilirsiniz. Tehdit koruması uç noktalarınıza dağıtıldığında daha da fazla içgörü elde eder ve bazı saldırıları otomatik olarak düzeltme olanağı elde edebilirsiniz. Son olarak, kuruluşunuz hassas verileri tanımlama, sınıflandırma ve etiketler uygulama ve Microsoft Purview veri kaybı önleme ilkelerini yapılandırma işini yerine getirdiyse, uç noktalarınızdaki veriler için daha ayrıntılı koruma elde edebilirsiniz.

Aşağıdaki diyagramda, bu ortama tanıttığınız Microsoft 365 ve diğer SaaS uygulamaları için Sıfır Güven bir güvenlik duruşu elde etmek için yapı taşları gösterilmektedir. Cihazlarla ilgili öğeler 1 ile 7 arasında numaralandırılır. Bunlar, cihaz yöneticilerinin gerçekleştirmek için diğer yöneticilerle koordine edeceği koruma katmanlarıdır.

![Microsoft 365 Sıfır Güven dağıtım yığını](../media/devices/m365-zero-trust-deployment-stack-devices.png#lightbox)

Bu çizimde:

|&nbsp;|Adım|Açıklama|Lisans gereksinimleri|
|---|---|---|---|
|1|Başlangıç noktası Sıfır Güven kimlik ve cihaz erişim ilkelerini yapılandırma|[**Düzey 2 Uygulama Koruma İlkeleri (APP) veri korumasını uygulamak**](manage-devices-with-intune-app-protection.md) için kimlik yöneticinizle birlikte çalışın. Bu ilkeler, cihazları yönetmenizi gerektirmez. uygulama ilkelerini Intune yapılandırabilirsiniz. Kimlik yöneticiniz, onaylı uygulamalar gerektirecek şekilde bir Koşullu Erişim ilkesi yapılandırıyor.|E3, E5, F1, F3, F5|
|2|Cihazları Intune kaydetme|Bu görevin uygulanması için daha fazla planlama ve zaman gerekir. Microsoft, cihazları kaydetmek için Intune kullanılmasını önerir çünkü bu araç en iyi tümleştirmeyi sağlar. Platforma bağlı olarak cihazları kaydetmek için çeşitli seçenekler vardır. Örneğin, Windows cihazlar Azure AD Join veya Autopilot kullanılarak kaydedilebilir. Her platform için seçenekleri gözden geçirmeniz ve ortamınız için en uygun kayıt seçeneğini belirlemeniz gerekir. Bkz [**. 2. Adım. Daha fazla bilgi için cihazları Intune kaydedin**](manage-devices-with-intune-enroll.md).|E3, E5, F1, F3, F5|
|3|Uyumluluk ilkelerini yapılandırma|Uygulamalarınıza ve verilerinize erişen cihazların en düşük gereksinimleri karşıladığından emin olmak istiyorsunuz; örneğin cihazlar parola veya pin korumalıdır ve işletim sistemi günceldir. Uyumluluk ilkeleri, cihazların karşılaması gereken gereksinimleri tanımlamanın yoludur. [**3. Adım. Uyumluluk ilkelerini ayarlama**](manage-devices-with-intune-compliance-policies.md) , bu ilkeleri yapılandırmanıza yardımcı olur.|E3, E5, F3, F5|
|4|kimlik ve cihaz erişim ilkelerini Sıfır Güven Enterprise (önerilen) yapılandırma|Cihazlarınız kaydedildikten sonra, [**koşullu erişim ilkelerini sağlıklı ve uyumlu cihazlar gerektirecek şekilde ayarlamak için**](manage-devices-with-intune-require-compliance.md) kimlik yöneticinizle birlikte çalışabilirsiniz.|E3, E5, F3, F5|
|5|Yapılandırma profillerini dağıtma|Yapılandırma profilleri, bir cihazı yalnızca uyumlu olarak işaretleyen veya yapılandırdığınız ölçütlere göre olmayan cihaz uyumluluk ilkelerinin aksine, aslında bir cihazdaki ayarların yapılandırmasını değiştirir. Cihazları siber tehditlere karşı sağlamlaştırmak için yapılandırma ilkelerini kullanabilirsiniz. Bkz [**. 5. Adım. Yapılandırma profillerini dağıtma**](manage-devices-with-intune-configuration-profiles.md).|E3, E5, F3, F5|
|6|Cihaz riskini ve güvenlik temelleriyle uyumluluğu izleme|Bu adımda, Intune Uç Nokta için Microsoft Defender bağlarsınız. Bu tümleştirmeyle cihaz riskini erişim koşulu olarak izleyebilirsiniz. Riskli durumda olduğu belirlenen cihazlar engellenir. Güvenlik temelleriyle uyumluluğu da izleyebilirsiniz. Bkz [**. 6. Adım. Cihaz riskini ve güvenlik temellerine uyumluluğunu izleyin**](manage-devices-with-intune-monitor-risk.md).|E5, F5|
|7|Bilgi koruma yetenekleriyle veri kaybı önleme (DLP) uygulayın|Kuruluşunuz hassas verileri tanımlamak ve belgeleri etiketlemek için çalışmayı kullandıysa, [**cihazlarınızdaki hassas bilgileri ve belgeleri korumak**](manage-devices-with-intune-dlp-mip.md) için bilgi koruma yöneticinizle birlikte çalışabilirsiniz.|E5, F5 uyumluluk eklentisi|

## <a name="coordinating-endpoint-management-with-zero-trust-identity-and-device-access-policies"></a>Uç nokta yönetimini Sıfır Güven kimlik ve cihaz erişim ilkeleriyle koordine etme

Bu kılavuz, önerilen [**Sıfır Güven kimlik ve cihaz erişim ilkeleriyle**](../security/office-365-security/microsoft-365-policies-configurations.md) sıkı bir şekilde koordine edilir. Intune ile yapılandırdığınız korumayı Azure AD'daki Koşullu Erişim ilkelerine taşımak için kimlik ekibinizle birlikte çalışacaksınız.

aşağıda, Intune/MEM'de yapacağınız çalışma için adım açıklama balonları içeren önerilen ilke kümesinin ve Azure AD'de koordine olmanıza yardımcı olacağınız ilgili Koşullu Erişim ilkelerinin bir çizimi verilmiştir.

[![kimlik ve cihaz erişim ilkelerini Sıfır Güven](../media/devices/identity-device-overview-steps.png#lightbox)](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/media/devices/identity-device-overview-steps.png)

Bu çizimde:

- 1. Adım, [**Düzey 2 Uygulama Koruma İlkelerini Uygulama (APP)**](manage-devices-with-intune-app-protection.md) bölümünde, APP ilkeleriyle önerilen veri koruma düzeyini yapılandırabilirsiniz. Ardından ilgili Koşullu Erişim kuralını bu korumanın kullanılmasını gerektirecek şekilde yapılandırmak için kimlik ekibinizle birlikte çalışırsınız.
- 2., 3. ve 4. Adımlarda cihazları Intune ile yönetime kaydeder, cihaz uyumluluk ilkeleri tanımlarsınız ve ardından kimlik ekibinizle koordine olarak ilgili Koşullu Erişim kuralını yalnızca uyumlu cihazlara erişime izin verecek şekilde yapılandırırsınız.

<!---
## Managing change with users
--->

## <a name="enrolling-devices-vs-onboarding-devices"></a>Cihazları kaydetme ve cihazları ekleme karşılaştırması

Bu yönergeleri izlerseniz, cihazları Intune kullanarak yönetime kaydedersiniz ve aşağıdaki Microsoft 365 özellikleri için cihazları eklersiniz:

- Uç Nokta için Microsoft Defender
- Microsoft Purview (uç nokta veri kaybı önleme (DLP) için) 

Aşağıdaki çizimde bunun Intune kullanılarak nasıl çalıştığı ayrıntılı olarak gösterilmiştir.

![Cihazları kaydetme ve ekleme işlemi](../media/devices/devices-enroll-onboard-process.png#lightbox)

Çizimde:

1. Intune ile cihazları yönetime kaydetme.
2. Uç Nokta için Defender'a cihaz eklemek için Intune kullanın.
3. Uç Nokta için Defender'a eklenen cihazlar, Uç Nokta DLP de dahil olmak üzere Microsoft Purview özellikler için de eklenir.
 
Cihazları yalnızca Intune yönettiğini unutmayın. Ekleme, bir cihazın belirli bir hizmetle bilgi paylaşma özelliğini ifade eder. Aşağıdaki tabloda, cihazları yönetime kaydetme ve belirli bir hizmet için cihazları ekleme arasındaki farklar özetlenmektedir.


|         |Kayıt     |Onboard  |
|---------|---------|---------|
|Açıklama     |  Kayıt, cihazları yönetmek için geçerlidir. Cihazlar Intune veya Configuration Manager ile yönetim için kaydedilir.        | Ekleme, bir cihazı Microsoft 365'daki belirli bir özellik kümesiyle çalışacak şekilde yapılandırıyor. Şu anda ekleme, Uç Nokta için Microsoft Defender ve Microsoft uyumluluk özellikleri için geçerlidir. <br><br>Windows cihazlarda ekleme, Windows Defender'da Defender'ın çevrimiçi hizmete bağlanmasına ve cihaza uygulanan ilkeleri kabul etmesine olanak tanıyan bir ayar eklemeyi içerir.        |
|Kapsam     | Bu cihaz yönetimi araçları, cihazı güvenlik gibi belirli hedeflere uyacak şekilde yapılandırmak da dahil olmak üzere tüm cihazı yönetir.        |Ekleme yalnızca geçerli hizmetleri etkiler.     |
|Önerilen yöntem     | Azure Active Directory birleştirme, cihazları otomatik olarak Intune kaydeder.        | Intune, uç nokta için Windows Defender cihazlar eklemek ve dolayısıyla özellikleri Microsoft Purview için tercih edilen yöntemdir.<br><br>Diğer yöntemler kullanılarak Microsoft Purview özelliklerine eklenen cihazların Uç Nokta için Defender'a otomatik olarak kaydedilmediğini unutmayın.        |
|Diğer yöntemler     |   Diğer kayıt yöntemleri, cihazın platformuna ve KCG olup olmadığına veya kuruluşunuz tarafından yönetilip yönetilmediğine bağlıdır.      | Cihaz eklemeye yönelik diğer yöntemler şunlardır:<br><li>Yapılandırma Yöneticisi<li>Diğer mobil cihaz yönetim aracı (cihaz bir tarafından yönetiliyorsa)<li>Yerel betik<li>Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarını eklemeye yönelik VDI yapılandırma paketi<li>Grup İlkesi|
| | |     |

Cihazları yalnızca Intune yönettiğini unutmayın. Ekleme, bir cihazın belirli bir hizmet özelliğiyle bilgi paylaşma özelliğini ifade eder. Aşağıdaki tabloda, belirli bir özellik için cihazları yönetime kaydetme ve cihazları ekleme arasındaki farklar özetlenmektedir.

|&nbsp;|Kayıt|Onboard|
|---|---|---|
|Açıklama|Kayıt, cihazları yönetmek için geçerlidir. Cihazlar Intune veya Configuration Manager ile yönetim için kaydedilir.|Ekleme, bir cihazı Microsoft 365'daki belirli bir özellik kümesiyle çalışacak şekilde yapılandırıyor. Şu anda ekleme, Uç Nokta için Microsoft Defender ve Microsoft uyumluluk özellikleri için geçerlidir. <br/><br/> Windows cihazlarda ekleme, Windows Defender'da Defender'ın çevrimiçi hizmete bağlanmasına ve cihaza uygulanan ilkeleri kabul etmesine olanak tanıyan bir ayar eklemeyi içerir.|
|Kapsam|Bu cihaz yönetimi araçları, cihazı güvenlik gibi belirli hedeflere uyacak şekilde yapılandırmak da dahil olmak üzere tüm cihazı yönetir.|Ekleme yalnızca geçerli olan özellikleri etkiler.|
|Önerilen yöntem|Azure Active Directory birleştirme, cihazları otomatik olarak Intune kaydeder.|Intune, uç nokta için Windows Defender cihazlar eklemek ve dolayısıyla özellikleri Microsoft Purview için tercih edilen yöntemdir. <br/><br/> Diğer yöntemler kullanılarak Microsoft Purview özelliklerine eklenen cihazların Uç Nokta için Defender'a otomatik olarak kaydedilmediğini unutmayın.|
|Diğer yöntemler|Diğer kayıt yöntemleri, cihazın platformuna ve KCG olup olmadığına veya kuruluşunuz tarafından yönetilip yönetilmediğine bağlıdır.|Cihaz eklemeye yönelik diğer yöntemler şunlardır: <ul><li>Yapılandırma Yöneticisi</li><li>Diğer mobil cihaz yönetim aracı (cihaz bir tarafından yönetiliyorsa)</li><li>Yerel betik</li><li>Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarını eklemeye yönelik VDI yapılandırma paketi</li><li>Grup İlkesi</li></ul>|

## <a name="learning-for-administrators"></a>Yöneticiler için Learning

Aşağıdaki kaynaklar yöneticilerin MEM ve Intune kullanma hakkındaki kavramları öğrenmesine yardımcı olur.

[Microsoft Endpoint Manager Açıklama ile cihaz yönetimini basitleştirme](/learn/modules/simplify-device-management-with-microsoft-endpoint-manager/): Modern yönetim, Microsoft Endpoint Manager ve Microsoft 365'deki iş yönetimi araçlarının tüm cihazlarınızın yönetimini nasıl kolaylaştırabileceği hakkında bilgi edinin.

[Microsoft Intune Açıklamayı Ayarlama](/learn/modules/set-up-microsoft-intune/): Microsoft Endpoint Manager bir parçası olan Microsoft Intune, kuruluşunuzdaki kişilerin üretken olmak için kullandığı cihazları, uygulamaları ve verileri korumanıza yardımcı olur. Bu modülü tamamladıktan sonra Microsoft Intune ayarlamış olacaksınız. Kurulum, desteklenen yapılandırmaları gözden geçirmeyi, Intune kaydolmayı, kullanıcı ve grup eklemeyi, kullanıcılara lisans atamayı, yönetici izinleri vermeyi ve MDM yetkilisini ayarlamayı içerir.
