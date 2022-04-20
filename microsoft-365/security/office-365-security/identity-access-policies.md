---
title: Yaygın Sıfır Güven kimlik ve cihaz erişim ilkeleri - kurumsal | için Microsoft 365 Microsoft Docs
description: Önerilen yaygın Sıfır Güven kimlik ve cihaz erişim ilkelerini ve yapılandırmalarını açıklar.
ms.author: dansimp
author: dansimp
manager: dansimp
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- remotework
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: 0c7facc2ac5a20b21a6862b115b62c576ebaeb1f
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972199"
---
# <a name="common-zero-trust-identity-and-device-access-policies"></a>Yaygın Sıfır Güven kimlik ve cihaz erişim ilkeleri

Bu makalede, Azure Active Directory (Azure AD) Uygulama Ara Sunucusu ile yayımlanan şirket içi uygulamalar da dahil olmak üzere Microsoft 365 bulut hizmetlerine erişimin güvenliğini sağlamak için önerilen yaygın Sıfır Güven kimlik ve cihaz erişim ilkeleri açıklanmaktadır.

Bu kılavuzda, önerilen ilkelerin yeni sağlanan bir ortamda nasıl dağıtılacağı açıklanır. Bu ilkeleri ayrı bir laboratuvar ortamında ayarlamak, dağıtımı üretim öncesi ve üretim ortamlarınıza hazırlamadan önce önerilen ilkeleri anlamanıza ve değerlendirmenize olanak tanır. Yeni sağlanan ortamınız, değerlendirme gereksinimlerinizi yansıtacak şekilde yalnızca bulut veya karma olabilir.

## <a name="policy-set"></a>İlke kümesi

Aşağıdaki diyagramda önerilen ilke kümesi gösterilmektedir. Her ilkenin hangi koruma katmanı için geçerli olduğunu ve ilkelerin bilgisayarlar, telefonlar ve tabletler ya da her iki cihaz kategorisi için de geçerli olup olmadığını gösterir. Ayrıca bu ilkeleri nerede yapılandırdığınız da gösterilir.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-policies-byplan.png" alt-text="Sıfır Güven kimliği ve cihaz erişimini yapılandırmaya yönelik yaygın ilkeler." lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-policies-byplan.png":::

<!--

Here's a one-page PDF summary:

[![Thumb image for the Zero Trust identity and device protection for Microsoft 365 handout.](../../media/microsoft-365-policies-configurations/zero-trust-id-device-protection-model-handout-thumbnail.png)](../../downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf) <br> [View as a PDF](../../downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf) \| [Download as a PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf)

-->

Bu makalenin geri kalanında bu ilkelerin nasıl yapılandırıldığı açıklanmaktadır.

> [!NOTE]
> Cihazın istenen kullanıcıya sahip olduğundan emin olmak için cihazları Intune'a kaydetmeden önce çok faktörlü kimlik doğrulamasının (MFA) kullanılmasının zorunlu olması önerilir. Cihaz uyumluluk ilkelerini zorunlu kılmadan önce cihazları Intune'a kaydetmeniz gerekir.

Bu görevleri yerine getirmeniz için size zaman vermek için başlangıç noktası ilkelerini bu tabloda listelenen sırayla uygulamanızı öneririz. Ancak, kurumsal ve özel güvenlik koruma düzeyleri için MFA ilkeleri her zaman uygulanabilir.

|Koruma düzeyi|İlkeler|Daha fazla bilgi|Lisanslama|
|---|---|---|---|
|**Başlangıç noktası**|[Oturum açma riski *orta* veya *yüksek* olduğunda MFA gerektirme](#require-mfa-based-on-sign-in-risk)||E5 Güvenliği eklentisiyle Microsoft 365 E5 veya Microsoft 365 E3|
||[Modern kimlik doğrulamayı desteklemeyen istemcileri engelleme](#block-clients-that-dont-support-multi-factor)|Modern kimlik doğrulaması kullanmayan istemciler Koşullu Erişim ilkelerini atlayabilir, bu nedenle bunları engellemek önemlidir.|Microsoft 365 E3 veya E5|
||[Yüksek riskli kullanıcıların parola değiştirmesi gerekir](#high-risk-users-must-change-password)|Hesapları için yüksek riskli etkinlik algılanırsa, kullanıcıları oturum açarken parolalarını değiştirmeye zorlar.|E5 Güvenliği eklentisiyle Microsoft 365 E5 veya Microsoft 365 E3|
||[Uygulama Koruma İlkeleri (APP) veri korumasını uygulama](#apply-app-data-protection-policies)|Platform başına bir Intune Uygulama Koruması ilkesi (Windows, iOS/iPadOS, Android).|Microsoft 365 E3 veya E5|
||[Onaylı uygulamalar ve uygulama koruması gerektirme](#require-approved-apps-and-app-protection)|iOS, iPadOS veya Android kullanarak telefonlar ve tabletler için mobil uygulama korumasını zorlar.|Microsoft 365 E3 veya E5|
|**Enterprise**|[Oturum açma riski *düşük*, *orta* veya *yüksek* olduğunda MFA gerektirme](#require-mfa-based-on-sign-in-risk)||E5 Güvenliği eklentisiyle Microsoft 365 E5 veya Microsoft 365 E3|
||[Cihaz uyumluluk ilkelerini tanımlama](#define-device-compliance-policies)|Her platform için bir ilke.|Microsoft 365 E3 veya E5|
||[Uyumlu bilgisayarlar ve mobil cihazlar gerektirme](#require-compliant-pcs-and-mobile-devices)|Hem bilgisayarlar (Windows veya macOS) hem de telefonlar veya tabletler (iOS, iPadOS veya Android) için Intune yönetimini zorlar.|Microsoft 365 E3 veya E5|
|**Özel güvenlik**|[*Her zaman* MFA iste](#assigning-policies-to-groups-and-users)||Microsoft 365 E3 veya E5|

## <a name="assigning-policies-to-groups-and-users"></a>Gruplara ve kullanıcılara ilke atama

İlkeleri yapılandırmadan önce, her koruma katmanı için kullandığınız Azure AD gruplarını belirleyin. Genellikle, başlangıç noktası koruması kuruluştaki herkes için geçerlidir. Hem başlangıç noktası hem de kurumsal koruma için dahil edilen bir kullanıcının tüm başlangıç noktası ilkeleri ve kurumsal ilkeler uygulanır. Koruma kümülatiftir ve en kısıtlayıcı ilke uygulanır.

Önerilen bir uygulama, Koşullu Erişim dışlaması için bir Azure AD grubu oluşturmaktır. **Atamalar** bölümündeki **Kullanıcılar ve gruplar** ayarının **Dışla** değerine bu grubu tüm Koşullu Erişim ilkelerinize ekleyin. Bu, siz erişim sorunlarını giderirken kullanıcıya erişim sağlamak için bir yöntem sağlar. Bu yalnızca geçici bir çözüm olarak önerilir. Değişiklikler için bu grubu izleyin ve dışlama grubunun yalnızca amaçlandığı gibi kullanıldığından emin olun.

Aşağıda, MFA gerektirmeye yönelik grup ataması ve dışlama örnekleri verilmiştir.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-policies-assignment.png" alt-text="MFA ilkeleri için Örnek grup ataması ve dışlamaları" lightbox="../../media/microsoft-365-policies-configurations/identity-access-policies-assignment.png":::

Sonuçlar şunlardır:

- Oturum açma riski orta veya yüksek olduğunda tüm kullanıcıların MFA kullanması gerekir.

- Yönetici Personel grubunun üyelerinin oturum açma riski düşük, orta veya yüksek olduğunda MFA kullanmaları gerekir.

  Bu durumda, Yönetim Personeli grubunun üyeleri hem başlangıç noktası hem de kurumsal Koşullu Erişim ilkeleriyle eşleştir. Her iki ilkenin erişim denetimleri birleştirilir ve bu durumda kurumsal Koşullu Erişim ilkesine eşdeğerdir.

- Çok Gizli Project X grubunun üyelerinin her zaman MFA kullanması gerekir

  Bu durumda, Çok Gizli Project X grubunun üyeleri hem başlangıç noktası hem de özel güvenlik Koşullu Erişim ilkeleriyle eşleşer. Her iki ilke için erişim denetimleri birleştirilir. Özelleştirilmiş güvenlik Koşullu Erişim ilkesinin erişim denetimi daha kısıtlayıcı olduğundan kullanılır.

Gruplara ve kullanıcılara daha yüksek koruma düzeyleri uygularken dikkatli olun. Örneğin, Project X için özel güvenlik içeriği üzerinde çalışmasalar bile, Çok Gizli Project X grubunun üyelerinin her oturum açtıklarında MFA kullanmaları gerekir.

Bu önerilerin bir parçası olarak oluşturulan tüm Azure AD gruplarının Microsoft 365 grupları olarak oluşturulması gerekir. Bu, Microsoft Teams ve SharePoint belgelerin güvenliğini sağlarken duyarlılık etiketlerinin dağıtımı için önemlidir.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-AAD-groups.png" alt-text="Microsoft 365 grubu oluşturma" lightbox="../../media/microsoft-365-policies-configurations/identity-device-AAD-groups.png":::

## <a name="require-mfa-based-on-sign-in-risk"></a>Oturum açma riskine göre MFA gerektirme

Kullanıcılarınızın kullanımını gerektirmeden önce MFA'ya kaydolmasını sağlayın. E5 Güvenliği eklentisiyle Microsoft 365 E3 Microsoft 365 E5, EMS E5 ile Office 365 veya tek tek Azure AD Premium P2 lisanslarınız varsa, kullanıcıların MFA'ya kaydolmasını istemek için Azure AD Kimlik Koruması ile MFA kayıt ilkesini kullanabilirsiniz. [Önkoşul çalışması](identity-access-prerequisites.md), tüm kullanıcıları MFA'ya kaydetmeyi içerir.

Kullanıcılarınız kaydedildikten sonra, yeni bir Koşullu Erişim ilkesiyle oturum açmak için MFA gerektirebilirsiniz.

1. [Azure portal](https://portal.azure.com) gidin ve kimlik bilgilerinizle oturum açın.
2. Azure hizmetleri listesinde **Azure Active Directory'yi** seçin.
3. **Yönet** listesinde **Güvenlik'i** ve ardından **Koşullu Erişim'i** seçin.
4. **Yeni ilke'yi** seçin ve yeni ilkenin adını yazın.

Aşağıdaki tablolarda, oturum açma riski temelinde MFA gerektirmek için Koşullu Erişim ilkesi ayarları açıklanmaktadır.

**Atamalar** bölümünde:

|Ayar|Özellikler|Değerler|Notlar|
|---|---|---|---|
|Kullanıcılar ve gruplar|Içerir|**Kullanıcılar ve gruplar > kullanıcıları ve grupları seçin**: Hedeflenen kullanıcı hesaplarını içeren belirli grupları seçin.|Pilot kullanıcı hesaplarını içeren grupla başlayın.|
||Dışlamak|**Kullanıcılar ve gruplar**: Koşullu Erişim özel durum grubunuzu seçin; hizmet hesapları (uygulama kimlikleri).|Üyelik, gerektiğinde geçici olarak değiştirilmelidir.|
|Bulut uygulamaları veya eylemleri|**Dahil > bulut uygulamaları**|**Uygulamaları seçin**: Bu ilkenin uygulanmasını istediğiniz uygulamaları seçin. Örneğin, Exchange Online'ı seçin.||
|Koşul -ları|||Ortamınıza ve gereksinimlerinize özgü koşulları yapılandırın.|
||Oturum açma riski||Aşağıdaki tabloda yer alan kılavuza bakın.|

### <a name="sign-in-risk-condition-settings"></a>Oturum açma riski koşulu ayarları

Risk düzeyi ayarlarını hedeflediğiniz koruma düzeyine göre uygulayın.

|Koruma düzeyi|Gerekli risk düzeyi değerleri|Eylem|
|---|---|---|
|Başlangıç noktası|Yüksek, orta|İkisini de kontrol edin.|
|Enterprise|Yüksek, orta, düşük|Üçünü de kontrol edin.|
|Özel güvenlik||MFA'yı her zaman zorlamak için tüm seçenekleri işaretsiz bırakın.|

**Erişim denetimleri** bölümünde:

|Ayar|Özellikler|Değerler|Eylem|
|---|---|---|---|
|Grant|**Grant access**||Seç|
|||**Çok faktörlü kimlik doğrulaması gerektir**|Çek|
||**Tüm seçili denetimleri gerektir**||Seç|

**İzin ver** ayarlarını kaydetmek için **Seç'i** seçin.

Son olarak **İlkeyi etkinleştir** için **Açık'ı** ve ardından **Oluştur'u** seçin.

Ayrıca ilkeyi test etmek için [Durum](/azure/active-directory/active-directory-conditional-access-whatif) aracını kullanmayı da göz önünde bulundurun.

## <a name="block-clients-that-dont-support-multi-factor"></a>Çok faktörlü desteği olmayan istemcileri engelleme

Çok faktörlü kimlik doğrulamasını desteklemeyen istemcileri engellemek için koşullu erişim ilkesi için bu tablolardaki ayarları kullanın.

çok faktörlü kimlik doğrulamasını destekleyen Microsoft 365 istemcilerin listesi için [bu makaleye](../../enterprise/microsoft-365-client-support-multi-factor-authentication.md) bakın.

**Atamalar** bölümünde:

|Ayar|Özellikler|Değerler|Notlar|
|---|---|---|---|
|Kullanıcılar ve gruplar|Içerir|**Kullanıcılar ve gruplar > kullanıcıları ve grupları seçin**: Hedeflenen kullanıcı hesaplarını içeren belirli grupları seçin.|Pilot kullanıcı hesaplarını içeren grupla başlayın.|
||Dışlamak|**Kullanıcılar ve gruplar**: Koşullu Erişim özel durum grubunuzu seçin; hizmet hesapları (uygulama kimlikleri).|Üyelik, gerektiğinde geçici olarak değiştirilmelidir.|
|Bulut uygulamaları veya eylemleri|**Dahil > bulut uygulamaları**|**Uygulamaları seçin**: Modern kimlik doğrulamasını desteklemeyen istemcilere karşılık gelen uygulamaları seçin.||
|Koşul -ları|**İstemci uygulamaları**|**Yapılandırma için** **Evet'i** seçin <p> **Tarayıcı** ve **Mobil uygulamalar ve masaüstü istemcileri için onay işaretlerini** temizleyin||

**Erişim denetimleri** bölümünde:

|Ayar|Özellikler|Değerler|Eylem|
|---|---|---|---|
|Grant|**Erişimi engelle**||Seç|
||**Tüm seçili denetimleri gerektir**||Seç|

**İzin ver** ayarlarını kaydetmek için **Seç'i** seçin.

Son olarak **İlkeyi etkinleştir** için **Açık'ı** ve ardından **Oluştur'u** seçin.

İlkeyi test etmek için [Durum](/azure/active-directory/active-directory-conditional-access-whatif) aracını kullanmayı göz önünde bulundurun.

Exchange Online için, tüm istemci erişim isteklerini modern kimlik doğrulaması kullanmaya zorlayan [Temel kimlik doğrulamasını devre dışı bırakmak](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online) için kimlik doğrulama ilkelerini kullanabilirsiniz.

## <a name="high-risk-users-must-change-password"></a>Yüksek riskli kullanıcıların parola değiştirmesi gerekir

Tüm yüksek riskli kullanıcıların güvenliği aşılmış hesaplarının oturum açarken parola değişikliği yapmaya zorlandığından emin olmak için aşağıdaki ilkeyi uygulamanız gerekir.

[Microsoft Azure portalında (yönetici kimlik bilgilerinizle)https://portal.azure.com)](https://portal.azure.com/) oturum açın ve ardından **Azure AD Kimlik Koruması > Kullanıcı Risk İlkesi'ne** gidin.

**Atamalar** bölümünde:

|Tür|Özellikler|Değerler|Eylem|
|---|---|---|---|
|Kullanıcılar|Içerir|**Tüm kullanıcılar**|Seç|
|Kullanıcı riski|**Yüksek**||Seç|

İkinci **Ödevler** bölümünde:

|Tür|Özellikler|Değerler|Eylem|
|---|---|---|---|
|Access|**Erişime izin ver**||Seç|
|||**Parola değişikliği gerektir**|Çek|

**Erişim** ayarlarını kaydetmek için **Bitti'yi** seçin.

Son olarak **İlkeyi zorla** için **Açık'ı** ve ardından **Kaydet'i** seçin.

İlkeyi test etmek için [Durum](/azure/active-directory/active-directory-conditional-access-whatif) aracını kullanmayı göz önünde bulundurun.

Bu ilkeyi, bilinen zayıf parolaları ve bunların değişkenlerini ve kuruluşunuza özgü ek zayıf terimleri algılayıp engelleyen [Azure AD parola korumasını yapılandırma](/azure/active-directory/authentication/concept-password-ban-bad) ile birlikte kullanın. Azure AD parola korumasının kullanılması, değiştirilen parolaların güçlü parolalar olmasını sağlar.

## <a name="apply-app-data-protection-policies"></a>APP veri koruma ilkelerini uygulama

APP'ler, izin verilen uygulamaları ve kuruluşunuzun verileriyle gerçekleştirebilecekleri eylemleri tanımlar. APP'te sağlanan seçenekler, kuruluşların korumayı kendi ihtiyaçlarına göre uyarlamasına olanak tanır. Bazıları için, tam bir senaryo uygulamak için hangi ilke ayarlarının gerekli olduğu açık olmayabilir. Microsoft, kuruluşların mobil istemci uç noktasını sağlamlaştırmaya öncelik vermelerine yardımcı olmak için iOS ve Android mobil uygulama yönetimi için APP veri koruma çerçevesi için taksonomi getirmiştir.

APP veri koruma çerçevesi üç farklı yapılandırma düzeyi halinde düzenlenmiştir ve her düzey önceki düzeyin dışında oluşturulur:

- **Düzey 1: Enterprise temel veri koruması**, uygulamaların BIR PIN ile korunmasını ve şifrelenmesini sağlar ve seçmeli temizleme işlemleri gerçekleştirir. Android cihazlar için bu düzey Android cihaz kanıtlamasını doğrular. Bu, Exchange Online posta kutusu ilkelerinde benzer veri koruma denetimi sağlayan ve BT'yi ve kullanıcı popülasyonunu APP'e tanıtır.
- **Düzey 2: gelişmiş Enterprise veri koruması**, UYGULAMA veri sızıntısı önleme mekanizmaları ve en düşük işletim sistemi gereksinimlerini getirir. Bu, iş veya okul verilerine erişen çoğu mobil kullanıcı için geçerli olan yapılandırmadır.
- **Düzey 3: Enterprise yüksek veri koruması** gelişmiş veri koruma mekanizmaları, gelişmiş PIN yapılandırması ve APP Mobile Threat Defense'i tanıtır. Bu yapılandırma, yüksek riskli verilere erişen kullanıcılar için tercih edilir.

Her yapılandırma düzeyine özgü önerileri ve korunması gereken en düşük uygulamaları görmek için [uygulama koruma ilkelerini kullanarak Veri koruma çerçevesi'ni](/mem/intune/apps/app-protection-framework) gözden geçirin.

[Sıfır Güven kimlik ve cihaz erişim yapılandırmalarında](microsoft-365-policies-configurations.md) belirtilen ilkeleri kullanarak Başlangıç noktası ve Enterprise koruma katmanları Düzey 2 kurumsal gelişmiş veri koruma ayarlarıyla yakından eşlenmiştir. Özelleştirilmiş güvenlik koruma katmanı, Düzey 3 kurumsal yüksek veri koruma ayarlarına yakından eşler.

|Koruma düzeyi|Uygulama Koruma İlkesi|Daha fazla bilgi|
|---|---|---|
|Başlangıç noktası|[Düzey 2 gelişmiş veri koruması](/mem/intune/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)|Düzey 2'de zorunlu kılınan ilke ayarları, düzey 1 için önerilen tüm ilke ayarlarını içerir ve yalnızca düzey 1'den daha fazla denetim ve daha karmaşık bir yapılandırma uygulamak için aşağıdaki ilke ayarlarını ekler veya güncelleştirir.|
|Enterprise|[Düzey 2 gelişmiş veri koruması](/mem/intune/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)|Düzey 2'de zorunlu kılınan ilke ayarları, düzey 1 için önerilen tüm ilke ayarlarını içerir ve yalnızca düzey 1'den daha fazla denetim ve daha karmaşık bir yapılandırma uygulamak için aşağıdaki ilke ayarlarını ekler veya güncelleştirir.|
|Özel güvenlik|[Düzey 3 kurumsal yüksek veri koruması](/mem/intune/apps/app-protection-framework#level-3-enterprise-high-data-protection)|Düzey 3'te zorunlu kılınan ilke ayarları, düzey 1 ve 2 için önerilen tüm ilke ayarlarını içerir ve yalnızca düzey 2'den daha fazla denetim ve daha karmaşık bir yapılandırma uygulamak için aşağıdaki ilke ayarlarını ekler veya güncelleştirir.|

Veri koruma çerçevesi ayarlarını kullanarak Microsoft Endpoint Manager içindeki her platform (iOS ve Android) için yeni bir uygulama koruma ilkesi oluşturmak için şunları yapabilirsiniz:

1. [Microsoft Intune ile uygulama koruma ilkeleri oluşturma ve dağıtma](/mem/intune/apps/app-protection-policies) bölümündeki adımları izleyerek ilkeleri el ile oluşturun.
2. Intune'un [PowerShell betikleriyle](https://github.com/microsoftgraph/powershell-intune-samples) örnek [Intune Uygulama Koruma İlkesi Yapılandırma Çerçevesi JSON şablonlarını](https://github.com/microsoft/Intune-Config-Frameworks/tree/master/AppProtectionPolicies) içeri aktarın.

## <a name="require-approved-apps-and-app-protection"></a>Onaylı uygulamalar ve APP koruması gerektirme

Intune'da uyguladığınız Uygulama koruması ilkelerini zorunlu kılmak için, onaylı istemci uygulamalarını ve APP koruma ilkelerinde ayarlanan koşulları zorunlu kılmak için bir Koşullu Erişim ilkesi oluşturmanız gerekir.

Uygulama koruması ilkelerini zorunlu tutma, [Koşullu Erişim ile bulut uygulaması erişimi için uygulama koruma ilkesi gerektirme](/azure/active-directory/conditional-access/app-protection-based-conditional-access) bölümünde açıklanan bir dizi ilke gerektirir. Bu ilkelerin her biri, bu önerilen kimlik ve erişim yapılandırma ilkeleri kümesine dahildir.

Onaylanan uygulamalar ve APP koruması gerektiren Koşullu Erişim ilkesini oluşturmak için, Yalnızca Uygulama koruması ilkeleriyle korunan mobil uygulamalardaki hesapların Microsoft 365 uç noktalarına erişmesine izin veren [Onaylı istemci uygulamaları veya mobil cihazlarla uygulama koruma ilkesi gerektirme](/azure/active-directory/conditional-access/howto-policy-approved-app-or-app-protection#require-approved-client-apps-or-app-protection-policy-with-mobile-devices) bölümündeki adımları izleyin.

   > [!NOTE]
   > Bu ilke, mobil kullanıcıların geçerli uygulamaları kullanarak tüm Microsoft 365 uç noktalarına erişebilmesini sağlar.

Bu ilke, mobil cihazlardaki Exchange ActiveSync istemcilerin Exchange Online bağlanmasını da engeller. Ancak, tüm cihazlarda Exchange ActiveSync işlemek için ayrı bir ilke oluşturabilirsiniz. Daha fazla bilgi için bkz[. Exchange ActiveSync istemcilerinin](secure-email-recommended-policies.md#block-activesync-clients) temel kimlik doğrulamasından yararlanarak Exchange Online bağlanmasını engelleyen ActiveSync istemcilerini engelleme. Bu ilke, bu makalenin üst kısmındaki çizimde resmedilmemiştir. [E-postanın güvenliğini sağlamaya yönelik ilke önerileri](secure-email-recommended-policies.md) bölümünde açıklanmıştır ve resmedilir.

 Bu ilke, [onaylanan istemci uygulamasını gerektir](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-approved-client-app) ve [Uygulama koruma ilkesi gerektir](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-app-protection-policy) onay denetimlerinden yararlanıyor.

Son olarak, iOS ve Android cihazlardaki diğer istemci uygulamaları için eski kimlik doğrulamasını engellemek, bu istemcilerin Koşullu Erişim ilkelerini atlamamasını sağlar. Bu makaledeki yönergeleri izliyorsanız, [modern kimlik doğrulamasını desteklemeyen Blok istemcilerini](#block-clients-that-dont-support-multi-factor) zaten yapılandırmışsınız demektir.

<!---
With Conditional Access, organizations can restrict access to approved (modern authentication capable) iOS and Android client apps with Intune app protection policies applied to them. Several Conditional Access policies are required, with each policy targeting all potential users. Details on creating these policies can be found in [Require app protection policy for cloud app access with Conditional Access](/azure/active-directory/conditional-access/app-protection-based-conditional-access).

1. Follow "Step 1: Configure an Azure AD Conditional Access policy for Microsoft 365" in [Scenario 1: Microsoft 365 apps require approved apps with app protection policies](/azure/active-directory/conditional-access/app-protection-based-conditional-access#scenario-1-office-365-apps-require-approved-apps-with-app-protection-policies), which allows Outlook for iOS and Android, but blocks OAuth capable Exchange ActiveSync clients from connecting to Exchange Online.

   > [!NOTE]
   > This policy ensures mobile users can access all Office endpoints using the applicable apps.

2. If enabling mobile access to Exchange Online, implement [Block ActiveSync clients](secure-email-recommended-policies.md#block-activesync-clients), which prevents Exchange ActiveSync clients leveraging basic authentication from connecting to Exchange Online.

   The above policies leverage the grant controls [Require approved client app](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-approved-client-app) and [Require app protection policy](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-app-protection-policy).

3. Disable legacy authentication for other client apps on iOS and Android devices. For more information, see [Block clients that don't support modern authentication](#block-clients-that-dont-support-modern-authentication).
-->

## <a name="define-device-compliance-policies"></a>Cihaz uyumluluk ilkelerini tanımlama

Cihaz uyumluluk ilkeleri, cihazların uyumlu olarak belirlenmesi için karşılaması gereken gereksinimleri tanımlar. Intune cihaz uyumluluk ilkelerini Microsoft Endpoint Manager yönetim merkezinden oluşturursunuz.

Her bilgisayar, telefon veya tablet platformu için bir ilke oluşturmanız gerekir:

- Android cihaz yöneticisi
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows 8.1 ve üzeri
- Windows 10 ve üzeri

Cihaz uyumluluk ilkeleri oluşturmak için yönetici kimlik bilgilerinizle [Microsoft Endpoint Manager Yönetim Merkezi'nde](https://endpoint.microsoft.com) oturum açın ve ardından **Cihaz** \> **Uyumluluk ilkeleri** **İlkeleri'ne**\> gidin. **İlke Oluştur'u** seçin.

Cihaz uyumluluk ilkelerinin dağıtılabilmesi için kullanıcı gruplarına atanması gerekir. İlkeyi oluşturduktan ve kaydettikten sonra atarsınız. Yönetim merkezinde ilkeyi ve ardından **Atamalar'ı** seçin. İlkeyi almak istediğiniz grupları seçtikten sonra **Kaydet'i** seçerek bu grup atamasını kaydedin ve ilkeyi dağıtın.

Intune'da uyumluluk ilkeleri oluşturmaya ilişkin adım adım yönergeler için Intune [belgelerindeki Microsoft Intune'da uyumluluk ilkesi oluşturma](/mem/intune/protect/create-compliance-policy) bölümüne bakın.

### <a name="recommended-settings-for-ios"></a>iOS için önerilen ayarlar

iOS/iPadOS, ikisi bu altyapının bir parçası olarak ele alınan çeşitli kayıt senaryolarını destekler:

- [Kişisel cihazlar için cihaz kaydı](/mem/intune/enrollment/ios-enroll) – bu cihazlar kişiseldir ve hem iş hem de kişisel kullanım için kullanılır.
- [Şirkete ait cihazlar için denetimli otomatik cihaz kaydı](/mem/intune/enrollment/device-enrollment-program-enroll-ios) – bu cihazlar şirkete aittir, tek bir kullanıcıyla ilişkilendirilir ve kişisel kullanım için değil yalnızca iş için kullanılır.

iOS/iPadOS güvenlik yapılandırma çerçevesi, kişisel ve denetimli cihazlar için rehberlik sağlayan birkaç farklı yapılandırma senaryosu halinde düzenlenmiştir.

Kişisel cihazlar için:

- Temel güvenlik (Düzey 1) – Microsoft, kullanıcıların iş veya okul verilerine eriştiği kişisel cihazlar için en düşük güvenlik yapılandırması olarak bu yapılandırmayı önerir. Bu, parola ilkeleri, cihaz kilidi özellikleri zorunlu hale getirilerek ve belirli cihaz işlevleri (örneğin güvenilmeyen sertifikalar) devre dışı bırakılarak gerçekleştirilir.
- Gelişmiş güvenlik (Düzey 2) – Microsoft, kullanıcıların hassas veya gizli bilgilere eriştiği cihazlar için bu yapılandırmayı önerir. Bu yapılandırma, veri paylaşımı denetimlerini yürürlüğe koyar. Bu yapılandırma, bir cihazdaki iş veya okul verilerine erişen çoğu mobil kullanıcı için geçerlidir.
- Yüksek güvenlik (Düzey 3) – Microsoft, benzersiz olarak yüksek riskli belirli kullanıcılar veya gruplar tarafından kullanılan cihazlar için bu yapılandırmayı önerir (yetkisiz ifşanın kuruluşta önemli ölçüde maddi kayıplara neden olduğu son derece hassas verileri işleyen kullanıcılar). Bu yapılandırma daha güçlü parola ilkeleri uygular, bazı cihaz işlevlerini devre dışı bırakır ve ek veri aktarımı kısıtlamaları uygular.

Denetimli cihazlar için:

- Temel güvenlik (Düzey 1) – Microsoft, kullanıcıların iş veya okul verilerine eriştiği denetimli cihazlar için en düşük güvenlik yapılandırması olarak bu yapılandırmayı önerir. Bu, parola ilkeleri, cihaz kilidi özellikleri zorunlu hale getirilerek ve belirli cihaz işlevleri (örneğin güvenilmeyen sertifikalar) devre dışı bırakılarak gerçekleştirilir.
- Gelişmiş güvenlik (Düzey 2) – Microsoft, kullanıcıların hassas veya gizli bilgilere eriştiği cihazlar için bu yapılandırmayı önerir. Bu yapılandırma, veri paylaşımı denetimlerini yürürlüğe koyar ve USB cihazlarına erişimi engeller. Bu yapılandırma, bir cihazdaki iş veya okul verilerine erişen çoğu mobil kullanıcı için geçerlidir.
- Yüksek güvenlik (Düzey 3) – Microsoft, benzersiz olarak yüksek riskli belirli kullanıcılar veya gruplar tarafından kullanılan cihazlar için bu yapılandırmayı önerir (yetkisiz ifşanın kuruluşta önemli ölçüde maddi kayıplara neden olduğu son derece hassas verileri işleyen kullanıcılar). Bu yapılandırma daha güçlü parola ilkeleri uygular, bazı cihaz işlevlerini devre dışı bırakır, ek veri aktarımı kısıtlamaları uygular ve uygulamaların Apple'ın toplu satın alma programı aracılığıyla yüklenmesini gerektirir.

[Sıfır Güven kimlik ve cihaz erişim yapılandırmalarında](microsoft-365-policies-configurations.md) belirtilen ilkeleri kullanarak Başlangıç noktası ve Enterprise koruma katmanları Düzey 2 gelişmiş güvenlik ayarlarıyla yakından eşlenmiştir. Özelleştirilmiş güvenlik koruma katmanı, Düzey 3 yüksek güvenlik ayarlarına yakından eşler.

|Koruma düzeyi  |Cihaz ilkesi |Daha fazla bilgi  |
|---------|---------|---------|
|Başlangıç noktası     |Gelişmiş güvenlik (Düzey 2)         |Düzey 2'de zorunlu kılınan ilke ayarları, düzey 1 için önerilen tüm ilke ayarlarını içerir ve yalnızca düzey 1'den daha fazla denetim ve daha karmaşık bir yapılandırma uygulamak için aşağıdaki ilke ayarlarını ekler veya güncelleştirir.         |
|Enterprise     |Gelişmiş güvenlik (Düzey 2)         |Düzey 2'de zorunlu kılınan ilke ayarları, düzey 1 için önerilen tüm ilke ayarlarını içerir ve yalnızca düzey 1'den daha fazla denetim ve daha karmaşık bir yapılandırma uygulamak için aşağıdaki ilke ayarlarını ekler veya güncelleştirir.         |
|Özel güvenlik     |Yüksek güvenlik (Düzey 3)         |Düzey 3'te zorunlu kılınan ilke ayarları, düzey 1 ve 2 için önerilen tüm ilke ayarlarını içerir ve yalnızca düzey 2'den daha fazla denetim ve daha karmaşık bir yapılandırma uygulamak için aşağıdaki ilke ayarlarını ekler veya güncelleştirir.         |

Her yapılandırma düzeyi için belirli cihaz uyumluluğu ve cihaz kısıtlama önerilerini görmek için [iOS/iPadOS Güvenlik Yapılandırma Çerçevesi'ni](/mem/intune/enrollment/ios-ipados-configuration-framework) gözden geçirin.

### <a name="recommended-settings-for-android"></a>Android için önerilen ayarlar

Android Enterprise, ikisi bu çerçevenin bir parçası olarak ele alınan çeşitli kayıt senaryolarını destekler:

- [Android Enterprise iş profili](/intune/android-work-profile-enroll) – Bu kayıt modeli genellikle BT'nin iş ve kişisel veriler arasında net bir ayrım sınırı sağlamak istediği kişisel cihazlar için kullanılır. BT tarafından denetlenen ilkeler, iş verilerinin kişisel profile aktarılmamasını sağlar.
- [Android Enterprise tam olarak yönetilen cihazlar](/intune/android-fully-managed-enroll) – bu cihazlar şirkete aittir, tek bir kullanıcıyla ilişkilendirilir ve kişisel kullanım için değil yalnızca iş için kullanılır.

Android Enterprise güvenlik yapılandırma çerçevesi, iş profili ve tam olarak yönetilen senaryolar için rehberlik sağlayan birkaç farklı yapılandırma senaryosu halinde düzenlenmiştir.

Android Enterprise iş profili cihazları için:

- İş profili artırılmış güvenlik (Düzey 2) – Microsoft, kullanıcıların iş veya okul verilerine eriştiği kişisel cihazlar için en düşük güvenlik yapılandırması olarak bu yapılandırmayı önerir. Bu yapılandırma parola gereksinimlerini tanıtır, iş ve kişisel verileri ayırır ve Android cihaz kanıtlamasını doğrular.
- İş profili yüksek güvenlik (Düzey 3) – Microsoft, benzersiz olarak yüksek riskli belirli kullanıcılar veya gruplar tarafından kullanılan cihazlar için bu yapılandırmayı önerir (yetkisiz ifşanın kuruluşta önemli ölçüde maddi kayıplara neden olduğu yüksek oranda hassas verileri işleyen kullanıcılar). Bu yapılandırma mobil tehdit savunmasını veya Uç Nokta için Microsoft Defender tanıtır, en düşük Android sürümünü ayarlar, daha güçlü parola ilkeleri oluşturur ve iş ile kişisel ayrımı daha da kısıtlar.

Android Enterprise tam olarak yönetilen cihazlar için:

- Tam olarak yönetilen temel güvenlik (Düzey 1) – Microsoft bu yapılandırmayı kurumsal bir cihaz için en düşük güvenlik yapılandırması olarak önerir. Bu yapılandırma, iş veya okul verilerine erişen çoğu mobil kullanıcı için geçerlidir. Bu yapılandırma parola gereksinimlerini tanıtır, en düşük Android sürümünü ayarlar ve belirli cihaz kısıtlamalarını belirler.
- Tam olarak yönetilen gelişmiş güvenlik (Düzey 2) – Microsoft, kullanıcıların hassas veya gizli bilgilere eriştiği cihazlar için bu yapılandırmayı önerir. Bu yapılandırma daha güçlü parola ilkeleri oluşturur ve kullanıcı/hesap özelliklerini devre dışı bırakır.
- Tam olarak yönetilen yüksek güvenlik (Düzey 3) - Microsoft, bu yapılandırmayı benzersiz olarak yüksek riskli belirli kullanıcılar veya gruplar tarafından kullanılan cihazlar için önerir (yetkisiz ifşanın kuruluşta önemli ölçüde maddi kayıplara neden olduğu yüksek oranda hassas verileri işleyen kullanıcılar). Bu yapılandırma en düşük Android sürümünü artırır, mobil tehdit savunması veya Uç Nokta için Microsoft Defender ekler ve ek cihaz kısıtlamaları uygular.

[Sıfır Güven kimlik ve cihaz erişim yapılandırmalarında](microsoft-365-policies-configurations.md) belirtilen ilkeleri kullanarak Başlangıç noktası ve Enterprise koruma katmanları, kişisel cihazlar için Düzey 1 temel güvenliği ve tam olarak yönetilen cihazlar için Düzey 2 gelişmiş güvenlik ayarlarıyla yakından eşlenmiştir. Özelleştirilmiş güvenlik koruma katmanı, Düzey 3 yüksek güvenlik ayarlarına yakından eşler.

Android Enterprise iş profili cihazları için:

|Koruma düzeyi  |Cihaz ilkesi |Daha fazla bilgi  |
|---------|---------|---------|
|Başlangıç noktası     |İş Profili: Temel güvenlik (Düzey 1)      |Yok         |
|Enterprise     |İş Profili: Temel güvenlik (Düzey 1)         |Yok         |
|Başlangıç noktası     |Tam Olarak Yönetilen: Gelişmiş Güvenlik (Düzey 2)       |Düzey 2'de zorunlu kılınan ilke ayarları, düzey 1 için önerilen tüm ilke ayarlarını içerir ve yalnızca düzey 1'den daha fazla denetim ve daha karmaşık bir yapılandırma uygulamak için aşağıdaki ilke ayarlarını ekler veya güncelleştirir.         |
|Enterprise     |Tam Olarak Yönetilen: Gelişmiş Güvenlik (Düzey 2)         |Düzey 2'de zorunlu kılınan ilke ayarları, düzey 1 için önerilen tüm ilke ayarlarını içerir ve yalnızca düzey 1'den daha fazla denetim ve daha karmaşık bir yapılandırma uygulamak için aşağıdaki ilke ayarlarını ekler veya güncelleştirir.         |
|Özel güvenlik     |Yüksek güvenlik (Düzey 3)         |Düzey 3'te zorunlu kılınan ilke ayarları, düzey 1 ve 2 için önerilen tüm ilke ayarlarını içerir ve yalnızca düzey 2'den daha fazla denetim ve daha karmaşık bir yapılandırma uygulamak için aşağıdaki ilke ayarlarını ekler veya güncelleştirir.         |

Her yapılandırma düzeyi için belirli cihaz uyumluluğu ve cihaz kısıtlama önerilerini görmek için [Android Enterprise Güvenlik Yapılandırma Çerçevesi'ni](/mem/intune/enrollment/android-configuration-framework) gözden geçirin.

### <a name="recommended-settings-for-windows-10-and-later"></a>Windows 10 ve üzeri için önerilen ayarlar

İlke oluşturma işleminin **2. Adımı: Uyumluluk ayarları** bölümünde yapılandırıldığı gibi, Windows 10 ve üzerini çalıştıran bilgisayarlar için aşağıdaki ayarlar önerilir.

**Cihaz durumu > Windows Sistem Durumu Kanıtlama Hizmeti değerlendirme kuralları** için bu tabloya bakın.

|Özellikler|Değer|Eylem|
|---|---|---|
|BitLocker gerektir|Gerektirir|Seç|
|Cihazda Güvenli Önyükleme'nin etkinleştirilmesini gerektir|Gerektirir|Seç|
|Kod bütünlüğü gerektir|Gerektirir|Seç|

**Cihaz özellikleri** için, BT ve güvenlik ilkelerinize göre işletim sistemi sürümleri için uygun değerleri belirtin.

**Configuration Manager Uyumluluğu** için **Gerekli'yi** seçin.

**Sistem güvenliği** için bu tabloya bakın.

|Tür|Özellikler|Değer|Eylem|
|---|---|---|---|
|Password|Mobil cihazların kilidini açmak için parola iste|Gerektirir|Seç|
||Basit parolalar|Engelle|Seç|
||Parola türü|Cihaz varsayılanı|Seç|
||Minimum parola uzunluğu|6|Tür|
||Parola istenmeden önce işlem yapılmadan geçen en fazla dakika sayısı|15|Tür <p> Bu ayar Android sürüm 4.0 ve üzeri ya da KNOX 4.0 ve üzeri sürümler için desteklenir. iOS cihazları için, iOS 8.0 ve üzeri için desteklenir.|
||Parola süre sonu (gün)|41|Tür|
||Yeniden kullanımı önlemek için önceki parola sayısı|5|Tür|
||Cihaz boşta durumundan geri döndüğünde parola iste (Mobil ve Holografik)|Gerektirir|Windows 10 ve üzeri sürümlerde kullanılabilir|
|Şifreleme|Cihazda veri depolama şifrelemesi|Gerektirir|Seç|
|Cihaz Güvenliği|Güvenlik duvarı|Gerektirir|Seç|
||Antivirus|Gerektirir|Seç|
||Antispyware|Gerektirir|Seç <p> Bu ayar, Windows Güvenliği uygulamasına kayıtlı bir Casus Yazılımdan Koruma çözümü gerektirir.|
|Bulut için Defender|Microsoft Defender Kötü Amaçlı Yazılımdan Koruma|Gerektirir|Seç|
||Microsoft Defender Kötü amaçlı yazılımdan koruma en düşük sürümü||Tür <p> Yalnızca Windows 10 masaüstü için desteklenir. Microsoft, en son sürümden en fazla beş geride kalan sürümleri önerir.|
||Microsoft Defender Kötü Amaçlı Yazılımdan Koruma imzası güncel|Gerektirir|Seç|
||Gerçek zamanlı koruma|Gerektirir|Seç <p> Yalnızca Windows 10 ve üzeri masaüstü için desteklenir|

#### <a name="microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender

|Tür|Özellikler|Değer|Eylem|
|---|---|---|---|
|Microsoft Endpoint Manager yönetim merkezinde kuralları Uç Nokta için Microsoft Defender|[Cihazın makine riski puanında veya altında olmasını gerektir](/mem/intune/protect/advanced-threat-protection-configure#create-and-assign-compliance-policy-to-set-device-risk-level)|Orta|Seç|

<!--
## Require compliant PCs (but not compliant phones and tablets)

Before adding a policy to require compliant PCs, be sure to enroll your devices for management in Intune. Using multi-factor authentication is recommended before enrolling devices into Intune for assurance that the device is in the possession of the intended user.

To require compliant PCs:

1. Go to the [Azure portal](https://portal.azure.com), and sign in with your credentials.
2. In the list of Azure services, choose **Azure Active Directory**.
3. In the **Manage** list, choose **Security**, and then choose **Conditional Access**.
4. Choose **New policy** and type the new policy's name.

5. Under **Assignments**, choose **Users and groups** and include who you want the policy to apply to. Also exclude your Conditional Access exclusion group.

6. Under **Assignments**, choose **Cloud apps or actions**.

7. For **Include**, choose **Select apps > Select**, and then select the desired apps from the **Cloud apps** list. For example, select Office 365. Choose **Select** when done.

8. To require compliant PCs (but not compliant phones and tablets), under **Assignments**, choose **Conditions > Device platforms**. Select **Yes** for **Configure**. Choose  **Select device platforms**, select **Yes** and select **Any device** and under Exclude select **iOS** and **Android**, and then choose **Done**.

9. Under **Access controls**, choose **Grant** .

10. Choose **Grant access** and then check **Require device to be marked as compliant**. For multiple controls, select **Require all the selected controls**. When complete, choose **Select**.

11. Select **On** for **Enable policy**, and then choose **Create**.

> [!NOTE]
> Make sure that your device is compliant before enabling this policy. Otherwise, you could get locked out and will be unable to change this policy until your user account has been added to the Conditional Access exclusion group.

-->

## <a name="require-compliant-pcs-and-mobile-devices"></a>Uyumlu bilgisayarlar ve mobil cihazlar gerektirme

Tüm cihazlar için uyumluluk gerektirmek için:

1. [Azure portal](https://portal.azure.com) gidin ve kimlik bilgilerinizle oturum açın.
2. Azure hizmetleri listesinde **Azure Active Directory'yi** seçin.
3. **Yönet** listesinde **Güvenlik'i** ve ardından **Koşullu Erişim'i** seçin.
4. **Yeni ilke'yi** seçin ve yeni ilkenin adını yazın.

5. **Atamalar'ın** altında **Kullanıcılar ve gruplar'ı** seçin ve ilkenin uygulanmasını istediğiniz kişilere ekleyin. Koşullu Erişim dışlama grubunuzu da hariç tutun.

6. **Ödevler'in** altında **Bulut uygulamaları veya eylemleri'ni** seçin.

7. **Ekle** için **Uygulamaları seçin > Seç'i** seçin ve ardından **Bulut uygulamaları** listesinden istediğiniz uygulamaları seçin. Örneğin, Office 365'ı seçin. İşiniz bittiğinde **Seç'i** seçin.

8. **Erişim denetimleri'nin** altında **Ver'i** seçin.

9. **Erişim ver'i** seçin ve ardından **Cihazın uyumlu olarak işaretlenmesini gerektir'i** işaretleyin. Birden çok denetim için **Tüm seçili denetimleri gerektir'i** seçin. Tamamlandığında **Seç'i** seçin.

10. **İlkeyi etkinleştir** için **Açık'ı** ve ardından **Oluştur'u** seçin.

> [!NOTE]
> Bu ilkeyi etkinleştirmeden önce cihazınızın uyumlu olduğundan emin olun. Aksi takdirde, kilitlenebilir ve kullanıcı hesabınız Koşullu Erişim dışlama grubuna eklenene kadar bu ilkeyi değiştiremezsiniz.

## <a name="next-step"></a>Sonraki adım

[![3. Adım: Konuk ve dış kullanıcılar için ilkeler.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-3.png#lightbox)](identity-access-policies-guest-access.md)

[Konuk ve dış kullanıcılar için ilke önerileri hakkında bilgi edinin](identity-access-policies-guest-access.md)
