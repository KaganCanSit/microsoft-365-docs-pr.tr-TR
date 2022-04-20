---
title: güvenlik ayarlarınızı İş için Microsoft Defender görüntüleme ve düzenleme
description: İş için Microsoft Defender'de güvenlik ilkelerinizi yapılandırma
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/18/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 22c2de998f4d4cfadb0262ccedf04decc01ce226
ms.sourcegitcommit: dc415d784226c77549ba246601f34324c4f94e73
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64916303"
---
# <a name="view-and-edit-your-security-policies-and-settings-in-microsoft-defender-for-business"></a>güvenlik ilkelerinizi ve ayarlarınızı İş için Microsoft Defender görüntüleme ve düzenleme

> [!NOTE]
> İş için Microsoft Defender artık [Microsoft 365 İş Ekstra](../../business-premium/index.md) dahil edilir. 

## <a name="overview"></a>Genel bakış

Şirketinizin cihazlarını İş için Microsoft Defender ekledikten sonra, sonraki adımınız güvenlik ilkelerinizi gözden geçirmektir. Gerekirse güvenlik ilkelerinizi ve ayarlarınızı düzenleyebilirsiniz. 

> [!TIP]
> İş için Defender, önerilen ayarları kullanan önceden yapılandırılmış güvenlik ilkeleri içerir. Ancak, ayarlarınızı iş gereksinimlerinize uyacak şekilde düzenleyebilirsiniz.

Gözden geçirilip yapılandırılan güvenlik ilkeleri şunlardır:

- Şirketinizin cihazları için virüsten koruma ve kötü amaçlı yazılımdan korumayı belirleyen **[yeni nesil koruma ilkeleri](#view-or-edit-your-next-generation-protection-policies)**
- Şirketinizin cihazlarına hangi ağ trafiğinin akışına izin verileceğini belirleyen **[güvenlik duvarı koruması ve kuralları](#view-or-edit-your-firewall-policies-and-custom-rules)**
- Kullanıcıların yetişkinlere **[yönelik içerik](#set-up-web-content-filtering)** veya yasal sorumluluk gibi kategorilere göre belirli web sitelerini (URL' ler) ziyaret etmesini engelleyen web içeriği filtreleme.
- Otomatik araştırma ve yanıt gibi **[gelişmiş özellikler](#review-settings-for-advanced-features)** ve blok modunda uç noktada algılama ve yanıtlama (EDR).

İş için Defender'da güvenlik ilkeleri cihaz [grupları](mdb-create-edit-device-groups.md#what-is-a-device-group) aracılığıyla cihazlara uygulanır. 

Güvenlik ilkelerinize ek olarak, Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com) ) hangi saat diliminin kullanılacağı ve önizleme özelliklerinin kullanıma sunulduklarında alınıp alınmayacağı gibi [ayarları görüntüleyebilir ve düzenleyebilirsiniz](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal).

Güvenlik ilkelerinizi ve ayarlarınızı yönetmek için bu makaleyi kılavuz olarak kullanın.

## <a name="what-to-do"></a>Yapılması gerekenler

1. [Güvenlik ilkelerinizi ve cihazlarınızı yöneteceğiniz yeri seçin](#choose-where-to-manage-security-policies-and-devices).

2. [Yeni nesil koruma ilkelerinizi görüntüleyin veya düzenleyin](#view-or-edit-your-next-generation-protection-policies).

3. [Güvenlik duvarı ilkelerinizi ve özel kurallarınızı görüntüleyin veya düzenleyin](#view-or-edit-your-firewall-policies-and-custom-rules).

4. [Web içeriği filtrelemeyi ayarlayın](#set-up-web-content-filtering).

5. [Gelişmiş özellikler için ayarları gözden geçirin](#review-settings-for-advanced-features).

6. [Microsoft 365 Defender portalında diğer ayarları görüntüleyin ve düzenleyin](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal). 

7. [Sonraki adımlarınıza geçin](#next-steps).

>
> **Bir dakikan var mı?**
> Lütfen <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">güvenlikle ilgili kısa anketimize</a> katılın. Sizden haber almak isteriz!
>

## <a name="choose-where-to-manage-security-policies-and-devices"></a>Güvenlik ilkelerinin ve cihazların nerede yönetileceğini seçme

İş için Defender, kurulum ve [yapılandırma sürecini](mdb-simplified-configuration.md) kolaylaştırmaya yardımcı olan basitleştirilmiş bir yapılandırma işlemine sahiptir. Basitleştirilmiş yapılandırma işlemini seçerseniz güvenlik ilkelerinizi Microsoft 365 Defender portalında ([https://security.microsoft.com/](https://security.microsoft.com/) ) görüntüleyebilir ve yönetebilirsiniz. Ancak, bu seçenekle sınırlı değilsiniz. Microsoft Endpoint Manager (Microsoft Intune dahil) kullanıyorsanız Endpoint Manager kullanmaya devam edebilirsiniz.

Aşağıdaki tablo, güvenlik ilkelerinizi ve cihazlarınızı yöneteceğiniz yeri seçmenize yardımcı olabilir. <br/><br/>

| Seçeneği | Açıklama |
|:---|:---|
| **Microsoft 365 Defender portalını kullanma** (*önerilen*) | Microsoft 365 Defender portalı ([https://security.microsoft.com/](https://security.microsoft.com/)) şirketinizin cihazlarını, güvenlik ilkelerini ve güvenlik ayarlarını yönetmek için tek durağınız olabilir. Güvenlik ilkelerinize ve ayarlarınıza erişebilir, [Tehdit & Güvenlik Açığı Yönetimi panonuzu](mdb-view-tvm-dashboard.md) kullanabilir ve olayları tek bir yerden [görüntüleyebilir ve yönetebilirsiniz](mdb-view-manage-incidents.md) . <br/><br/>Microsoft Endpoint Manager kullanıyorsanız, İş için Defender'a eklediğiniz cihazlar ve güvenlik ilkeleriniz Endpoint Manager görünür. Daha fazla bilgi edinmek için aşağıdaki makalelere bakın:<br/>- [İş için Defender varsayılan ayarları ve Microsoft Endpoint Manager](mdb-next-gen-configuration-settings.md#defender-for-business-default-settings-and-microsoft-endpoint-manager)<br/>- [İş için Microsoft Defender'de güvenlik duvarı](mdb-firewall.md)   |
| **Microsoft Endpoint Manager kullanma** | Şirketiniz güvenlik ilkelerini yönetmek için zaten Endpoint Manager (Microsoft Intune içerir) kullanıyorsa cihazları ve güvenlik ilkelerini yönetmek için Endpoint Manager kullanmaya devam edebilirsiniz. Daha fazla bilgi için bkz. [Microsoft Intune'da uç nokta güvenlik ilkeleriyle cihaz güvenliğini yönetme](/mem/intune/protect/endpoint-security-policy). <br/><br/>[İş için Defender'da basitleştirilmiş yapılandırma işlemine](mdb-simplified-configuration.md) geçmeye karar verirseniz, daha sonra ilke [çakışmalarını](mdb-troubleshooting.yml) önlemek için Endpoint Manager'deki mevcut güvenlik ilkelerini silmeniz istenir. |

> [!IMPORTANT]
> Microsoft 365 Defender portalında güvenlik ilkelerini yönetiyorsanız, bu ilkeleri Virüsten Koruma veya Güvenlik Duvarı ilkeleri olarak listelenen Endpoint Manager *görüntüleyebilirsiniz*. Güvenlik duvarı ilkelerinizi Endpoint Manager görüntülediğinizde iki ilke listelenir: biri güvenlik duvarı korumanız için, diğeri özel kurallar için.

## <a name="view-or-edit-your-next-generation-protection-policies"></a>Yeni nesil koruma ilkelerinizi görüntüleme veya düzenleme

Yeni nesil koruma ilkelerinizi yönetmek için Microsoft 365 Defender portalını mı yoksa Microsoft Endpoint Manager mi kullandığınıza bağlı olarak, aşağıdaki tabloda yer alan yordamlardan birini kullanın:

| Portal | Yordam |
|:---|:---|
| Microsoft 365 Defender portalı ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com) ) gidin ve oturum açın. <br/><br/>2. Gezinti bölmesinde **Cihaz yapılandırması'nı** seçin. İlkeler işletim sistemine ve ilke türüne göre düzenlenir.<br/><br/>3. bir işletim sistemi sekmesi seçin (örneğin **, Windows istemcileri**).<br/><br/>4. İlke listenizi görüntülemek için **Yeni nesil korumayı** genişletin.<br/><br/>5. İlke hakkında daha fazla ayrıntı görüntülemek için bir ilke seçin. Değişiklik yapmak veya ilke ayarları hakkında daha fazla bilgi edinmek için aşağıdaki makalelere bakın: <br/>- [Cihaz ilkelerini görüntüleme veya düzenleme](mdb-view-edit-policies.md)<br/>- [Yeni nesil yapılandırma ayarlarını anlama](mdb-next-gen-configuration-settings.md)  |
| Microsoft Endpoint Manager yönetim merkezi ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Adresine gidin [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ve oturum açın. Artık Microsoft Endpoint Manager yönetim merkezindesiniz.<br/><br/>2. **Uç nokta güvenliği'ne** tıklayın.<br/><br/>3. İlkelerinizi bu kategoride görüntülemek için **Virüsten Koruma'ya** tıklayın. <br/><br/>Microsoft Endpoint Manager'da güvenlik ayarlarınızı yönetme konusunda yardım almak için [Microsoft Intune'de uç nokta güvenliğini yönetme](/mem/intune/protect/endpoint-security) ile başlayın. |

## <a name="view-or-edit-your-firewall-policies-and-custom-rules"></a>Güvenlik duvarı ilkelerinizi ve özel kurallarınızı görüntüleme veya düzenleme

Güvenlik duvarı korumanızı yönetmek için Microsoft 365 Defender portalını mı yoksa Microsoft Endpoint Manager mi kullandığınıza bağlı olarak, aşağıdaki tabloda yer alan yordamlardan birini kullanın:

| Portal | Yordam |
|:---|:---|
| Microsoft 365 Defender portalı ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com) ) gidin ve oturum açın. <br/><br/>2. Gezinti bölmesinde **Cihaz yapılandırması'nı** seçin. İlkeler işletim sistemine ve ilke türüne göre düzenlenir.<br/><br/>3. bir işletim sistemi sekmesi seçin (örneğin **, Windows istemcileri**).<br/><br/>4. İlke listenizi görüntülemek için **Güvenlik Duvarı'nı** genişletin.<br/><br/>5. İlke hakkında daha fazla ayrıntı görüntülemek için bir ilke seçin. Değişiklik yapmak veya ilke ayarları hakkında daha fazla bilgi edinmek için aşağıdaki makalelere bakın: <br/>- [Cihaz ilkelerini görüntüleme veya düzenleme](mdb-view-edit-policies.md)<br/>- [Güvenlik duvarı ayarları](mdb-firewall.md)<br/>- [Güvenlik duvarı ilkeleri için özel kurallarınızı yönetme](mdb-custom-rules-firewall.md)  |
| Microsoft Endpoint Manager yönetim merkezi ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Adresine gidin [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ve oturum açın. Artık Microsoft Endpoint Manager yönetim merkezindesiniz.<br/><br/>2. **Uç nokta güvenliği'ne** tıklayın.<br/><br/>3. İlkelerinizi bu kategoride görüntülemek için **Güvenlik Duvarı'nı** seçin. Güvenlik duvarı koruması için tanımlanan özel kurallar ayrı ilkeler olarak listelenir.<br/><br/>Microsoft Endpoint Manager'da güvenlik ayarlarınızı yönetme konusunda yardım almak için [Microsoft Intune'de uç nokta güvenliğini yönetme](/mem/intune/protect/endpoint-security) ile başlayın. |

## <a name="set-up-web-content-filtering"></a>Web içeriği filtrelemeyi ayarlama

Web içeriği filtreleme, güvenlik ekibinizin web sitelerine erişimi aşağıdaki gibi içerik kategorilerine göre izlemesine ve düzenlemesine olanak tanır:

- Yetişkin içeriği: Tarikatlar, kumar, çıplaklık, pornografi, cinsel içerikli malzeme veya şiddet ile ilgili siteler
- Yüksek bant genişliği: Siteleri, görüntü paylaşım sitelerini veya eşler arası konakları indirme
- Yasal sorumluluk: Çocuk istismarı görüntülerini içeren, yasa dışı etkinlikleri teşvik eden, intihal veya okul dolandırıcılığına teşvik eden veya zararlı etkinlikleri teşvik eden siteler
- Boş zaman: Web tabanlı sohbet odaları, çevrimiçi oyun, web tabanlı e-posta veya sosyal ağ sağlayan siteler
- Kategorilere ayrılmamış: İçeriği olmayan veya yeni kaydedilen siteler

Bu kategorilerdeki web sitelerinin tümü kötü amaçlı değildir, ancak uyumluluk düzenlemeleri, bant genişliği kullanımı veya diğer endişeler nedeniyle şirketiniz için sorunlu olabilir. Ayrıca, güvenlik ekibinizin herhangi bir web sitesi kategorisini engellemesi gerekip gerekmediğini daha iyi anlamak için yalnızca denetim ilkesi oluşturabilirsiniz.

Web içeriği filtreleme, Windows Defender SmartScreen (Microsoft Edge) ve Ağ Koruması (Chrome, Firefox, Brave ve Opera) tarafından gerçekleştirilen bloklarla büyük web tarayıcılarında kullanılabilir. Daha fazla bilgi için bkz. [Web içeriği filtreleme önkoşulları](../defender-endpoint/web-content-filtering.md#prerequisites).

### <a name="to-set-up-web-content-filtering"></a>Web içeriği filtrelemeyi ayarlamak için

1. Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com) ) **Ayarlar** >  **Web içerik filtreleme** > **+ İlke ekle'yi** seçin.

2. İlkeniz için bir ad ve açıklama belirtin.

3. Engelleyecek kategorileri seçin. Her üst kategoriyi tamamen genişletmek ve belirli web içeriği kategorilerini seçmek için genişlet simgesini kullanın.

   Hiçbir web sitesini engellemeyen yalnızca denetim ilkesi ayarlamak için hiçbir kategori seçmeyin.

   **Kategorilere Ayrılmamış'ı** seçmeyin.

4. İlkeyi uygulamak için cihaz gruplarını seçerek ilke kapsamını belirtin. Yalnızca seçili cihaz gruplarındaki cihazların seçilen kategorilerdeki web sitelerine erişmesi engellenir.

5. Özeti gözden geçirin ve ilkeyi kaydedin. İlke yenilemesinin seçili cihazlarınıza uygulanması 2 saat kadar sürebilir.

> [!TIP]
> Web içeriği filtreleme hakkında daha fazla bilgi edinmek için bkz. [Web içeriği filtreleme](../defender-endpoint/web-content-filtering.md).

## <a name="review-settings-for-advanced-features"></a>Gelişmiş özellikler için ayarları gözden geçirme

Yeni nesil koruma, güvenlik duvarı ve web içeriği filtreleme ilkelerine ek olarak, İş için Defender gelişmiş güvenlik özellikleri içerir. Bu özellikler önerilen ayarlar kullanılarak önceden yapılandırılmış; ancak bunları gözden geçirebilir ve gerekirse ayarları iş gereksinimlerinize uyacak şekilde düzenleyebilirsiniz.

Gelişmiş özelliklerin ayarlarına erişmek için Microsoft 365 Defender portalında ([https://security.microsoft.com](https://security.microsoft.com) ) **Ayarlar** >  EndpointsGeneralAdvanced >  >  **özellikler'e** gidin.

Aşağıdaki tabloda gelişmiş özelliklerin ayarları açıklanmaktadır:

| Ayar | Açıklama |
|:---|:---|
| Otomatik Araştırma <br/>(varsayılan olarak açıktır) | Uyarılar oluşturuldukçe otomatik araştırma yapılabilir. Her otomatik araştırma, algılanan bir tehdidin eylem gerektirip gerektirmediğini belirler ve ardından düzeltme eylemleri (karantinaya dosya gönderme, işlemi durdurma, cihazı yalıtma veya URL'yi engelleme gibi) gerçekleştirir (veya önerir). Bir araştırma çalışırken, ortaya çıkan diğer ilgili uyarılar tamamlanana kadar araştırmaya eklenir. Etkilenen bir varlık başka bir yerde görülürse, otomatik araştırma kapsamını bu varlığı içerecek şekilde genişletir ve araştırma işlemi yinelenir.<br/><br/>Araştırmalara **Olaylar** sayfasından bakabilirsiniz. Bir olay seçin ve ardından **Araştırmalar** sekmesini seçin.<br/><br/>[Otomatik araştırma hakkında daha fazla bilgi edinin](../defender-endpoint/automated-investigations.md).   |
| Canlı Yanıt  | İş için Defender aşağıdaki el ile yanıt eylemi türlerini içerir: <br/>- Virüsten koruma taraması çalıştırma<br/>- Cihazı yalıtma<br/>- Dosyayı durdurma ve karantinaya al<br/>- Bir dosyayı engellemek veya dosyaya izin vermek için gösterge ekleme <br/><br/>[Yanıt eylemleri hakkında daha fazla bilgi edinin](../defender-endpoint/respond-machine-alerts.md). |
| Sunucular için Canlı Yanıt | (Bu ayar şu anda İş için Defender'da kullanılamıyor)   |
| Canlı Yanıt imzasız betik yürütme | (Bu ayar şu anda İş için Defender'da kullanılamıyor)  | 
| Blok modunda EDR etkinleştirme<br/>(varsayılan olarak açıktır) | Microsoft Defender Virüsten Koruma birincil virüsten koruma ürünü olmadığında ve bir cihazda pasif modda çalıştığında kötü amaçlı yapıtlara karşı ek koruma sağlar. Blok modundaki EDR, EDR özellikleri tarafından algılanan kötü amaçlı yapıtları düzeltmek için arka planda çalışır. Bu tür yapıtlar birincil, Microsoft dışı virüsten koruma ürünü tarafından kaçırılmış olabilir. Microsoft Defender Virüsten Koruma birincil virüsten koruma yazılımı olarak çalıştıran cihazlar için blok modundaki EDR, Microsoft Defender Virüsten Koruma ihlal sonrası, davranışsal EDR algılamalarında otomatik eylemler gerçekleştirmesine izin vererek ek bir savunma katmanı sağlar.<br/><br/>[Blok modunda EDR hakkında daha fazla bilgi edinin](../defender-endpoint/edr-in-block-mode.md). |
| Dosyaya izin verme veya dosyayı engelleme <br/>(varsayılan olarak açıktır) | [Göstergeleri](../defender-endpoint/indicator-file.md) kullanarak bir dosyaya izin vermenizi veya dosyayı engellemenizi sağlar. Bu özellik, Microsoft Defender Virüsten Koruma etkin modda olmasını ve [bulut korumasının](../defender-endpoint/cloud-protection-microsoft-defender-antivirus.md) açılmasını gerektirir.<br/><br/>Bir dosyanın engellenmesi, dosyanın kuruluşunuzdaki cihazlarda okunmasını, yazılmasını veya yürütülmesini engeller. <br/><br/>[Dosyalar için göstergeler hakkında daha fazla bilgi edinin](../defender-endpoint/indicator-file.md).  |
| Özel ağ göstergeleri<br/>(varsayılan olarak açıktır) | [Ağ göstergelerini](../defender-endpoint/indicator-ip-domain.md) kullanarak BIR IP adresine, URL'ye veya etki alanına izin vermenizi veya engellemenizi sağlar. Bu özellik, Microsoft Defender Virüsten Koruma etkin modda olmasını ve [ağ korumasının](../defender-endpoint/enable-network-protection.md) açılmasını gerektirir.<br/><br/>Kendi tehdit bilgilerinize göre IP'lere, URL'lere veya etki alanlarına izin verebilir veya bunları engelleyebilirsiniz. Riskli bir uygulama açtıklarında kullanıcıları bir istemle de uyarabilirsiniz. İstem, uygulamayı kullanmalarını engellemez, ancak kullanıcılar için bir uyarı sağlayabilirsiniz.<br/><br/>[Ağ koruması hakkında daha fazla bilgi edinin](../defender-endpoint/network-protection.md). |
| Kurcalama koruması<br/>(bu ayarı açmanızı öneririz) | Kurcalama koruması, kötü amaçlı uygulamaların aşağıdaki gibi eylemler gerçekleştirmesini önler:<br/>- Virüs ve tehdit korumasını devre dışı bırakma<br/>- Gerçek zamanlı korumayı devre dışı bırakma<br/>- Davranış izlemeyi kapatma<br/>- Bulut korumasını devre dışı bırakma<br/>- Güvenlik bilgileri güncelleştirmelerini kaldırma<br/>- Algılanan tehditlerde otomatik eylemleri devre dışı bırakma<br/><br/>Kurcalama koruması temelde Microsoft Defender Virüsten Koruma güvenli, varsayılan değerlerine kilitler ve güvenlik ayarlarınızın uygulamalar ve yetkisiz yöntemler tarafından değiştirilmesini önler. <br/><br/>[Kurcalama koruması hakkında daha fazla bilgi edinin](../defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection.md).  |
| Kullanıcı ayrıntılarını göster<br/>(varsayılan olarak açıktır) | Kuruluşunuzdaki kişilerin çalışanların resmi, adı, unvanı ve departmanı gibi ayrıntıları görmesini sağlar. Bu ayrıntılar Azure Active Directory (Azure AD) içinde depolanır.<br/><br/>[Azure AD'de kullanıcı profilleri hakkında daha fazla bilgi edinin](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).  |
| Skype Kurumsal tümleştirmesi<br/>(varsayılan olarak açıktır) | Skype Kurumsal Temmuz 2021'de kullanımdan kaldırıldı. Henüz Microsoft Teams taşınmadıysanız bkz. [Küçük işletmenizde Microsoft Teams ayarlama](/microsoftteams/deploy-small-business). <br/><br/>Microsoft Teams (veya eski Skype Kurumsal) ile tümleştirme, işletmenizdeki kişiler arasında tek tıklamayla iletişime olanak tanır.   |
| Web içeriği filtreleme<br/>(varsayılan olarak açıktır) | İstenmeyen içerik içeren web sitelerine erişimi engelleyin ve tüm etki alanlarındaki web etkinliğini izleyin. Bkz. [Web içeriği filtrelemeyi ayarlama](#set-up-web-content-filtering). |
| Microsoft Intune bağlantısı<br/>(Intune varsa bu ayarı açmanızı öneririz) | Kuruluşunuzun aboneliği Microsoft Intune (Microsoft Endpoint Manager parçası ve [Microsoft 365 İş Ekstra](../../business/index.yml) dahil) içeriyorsa, bu ayar İş için Defender'ın cihazlar hakkındaki bilgileri Intune ile paylaşmasını sağlar.  |
| cihaz keşfi<br/>(varsayılan olarak açıktır) | Güvenlik ekibinizin şirket ağınıza bağlı yönetilmeyen cihazları bulmasını sağlar. Bilinmeyen ve yönetilmeyen cihazlar ağınıza önemli riskler getirir. Bu, eşleşmeyen bir yazıcı, zayıf güvenlik yapılandırmalarına sahip ağ cihazları veya güvenlik denetimleri olmayan bir sunucu olabilir. <br/><br/>Cihaz bulma, yönetilmeyen cihazları bulmak için eklenen cihazları kullanır, böylece güvenlik ekibiniz yönetilmeyen cihazları ekleyebilir ve güvenlik açığınızı azaltabilir. <br/><br/>[Cihaz bulma hakkında daha fazla bilgi edinin](../defender-endpoint/device-discovery.md).    |
| Özellikleri önizleyin | Microsoft, yeni özellik geliştirmeleri ve özellikleri dahil etmek için İş için Defender gibi hizmetleri sürekli güncelleştirmektedir. Önizleme özelliklerini almayı kabul ederseniz, önizleme deneyiminde yaklaşan özellikleri ilk deneyenler arasında yer alırsınız. <br/><br/>[Önizleme özellikleri hakkında daha fazla bilgi edinin](../defender-endpoint/preview.md).  |


## <a name="view-and-edit-other-settings-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında diğer ayarları görüntüleme ve düzenleme

Cihazlara uygulanan güvenlik ilkelerine ek olarak, İş için Defender'da görüntüleyebileceğiniz ve düzenleyebileceğiniz başka ayarlar da vardır. Örneğin, kullanılacak saat dilimini belirtirsiniz ve cihazları ekleyebilir (veya devre dışı bırakabilirsiniz). 

> [!NOTE]
> Kiracınızda bu makalede listelenenden daha fazla ayar görebilirsiniz. Bu makalede, İş için Defender'da gözden geçirmeniz gereken en önemli ayarlar vurgulanır.

### <a name="settings-to-review-for-defender-for-business"></a>İş için Defender'ı gözden geçirmek Ayarlar

Aşağıdaki tabloda, İş için Defender'da görüntüleme (ve gerekirse düzenleme) ayarları açıklanmaktadır:

| Kategori | Ayar | Açıklama |
|:---|:---|:---|
| **Güvenlik merkezi** | **Saat dilimi** | Olaylarda görüntülenen tarihler ve saatler, algılanan tehditler ve otomatik araştırma & düzeltme için kullanılacak saat dilimini seçin. UTC veya yerel saat diliminizi kullanabilirsiniz (*önerilir*).  |
| **Microsoft 365 Defender** | **Hesabı** | Verilerinizin depolandığı yer, kiracı kimliğiniz ve kuruluşunuzun (kuruluş) kimliği gibi ayrıntıları görüntüleyin. |
| **Microsoft 365 Defender**  | **Özellikleri önizleyin**  | Yaklaşan özellikleri ve yeni özellikleri denemek için önizleme özelliklerini açın. Yeni özellikleri ilk önizleyip geri bildirim sağlayanlar arasında olabilirsiniz. |
| **Bitiş noktası**  | **E-posta bildirimleri** | E-posta bildirim kurallarınızı ayarlayın veya düzenleyin. Güvenlik açıkları algılandığında veya bir uyarı oluşturulduğunda, e-posta bildirim kurallarınızda belirtilen alıcılar bir e-posta alır. [E-posta bildirimleri hakkında daha fazla bilgi edinin](mdb-email-notifications.md). |
| **Bitiş noktası**   | **Cihaz yönetimi** >  **Ekleme** | İndirilebilir bir betik kullanarak cihazları İş için Defender'a ekleyin. Daha fazla bilgi edinmek için bkz[. Cihazları İş için Microsoft Defender ekleme](mdb-onboard-devices.md).   |  
| **Bitiş noktası**  |  **Cihaz yönetimi** >  **Çıkarma** | Cihazları İş için Defender'dan çıkarın (kaldırın). Bir cihazı kullanıma aldığınızda, bu cihaz artık İş için Defender'a veri göndermez, ancak kullanıma alınmadan önce alınan veriler korunur. Daha fazla bilgi için bkz. [Cihazı çıkarma](mdb-offboard-devices.md).  |

### <a name="access-your-settings-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında ayarlarınıza erişme

1. Microsoft 365 Defender portalına ()[https://security.microsoft.com/](https://security.microsoft.com/) gidin ve oturum açın.

2. **Ayarlar'ı** seçin ve ardından bir kategori (**Güvenlik merkezi**, **Microsoft 365 Defender** veya **Uç Noktalar** gibi) seçin.

3. Ayarlar listesinde, görüntülemek veya düzenlemek için bir öğe seçin.

## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki görevlerden birine veya daha fazlasına geçin:

- [İş için Microsoft Defender kullanarak Kullanmaya başlayın](mdb-get-started.md)
- [İş için Microsoft Defender'de cihazları yönetme](mdb-manage-devices.md)
- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md)
- [İş için Microsoft Defender'de ilkeleri görüntüleme veya düzenleme](mdb-view-edit-policies.md)
