---
title: Ortak Sıfır Güven kimliği ve cihaz erişim ilkeleri - Microsoft 365 erişimi için | Microsoft Docs
description: Önerilen Sıfır Güven kimliği ve cihaz erişimi ilkeleri ile yapılandırmalarını açıklar.
ms.author: josephd
author: JoeDavies-MSFT
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
ms.openlocfilehash: 90bdb8dbbb90009b10015591732d0257789884cd
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63009993"
---
# <a name="common-zero-trust-identity-and-device-access-policies"></a>Ortak Sıfır Güven kimliği ve cihaz erişimi ilkeleri

Bu makalede, Azure Active Directory (Azure AD) Uygulama Ara Sunucusu ile yayımlanan şirket içi uygulamalar da dahil olmak üzere, Microsoft 365 bulut hizmetlerine erişimin güvenliğini sağlamak için önerilen Sıfır Güven kimliği ve cihaz erişimi ilkeleri açıklanmaktadır.

Bu kılavuzda, önerilen ilkelerin yeni sağlanan bir ortamda nasıl dağıt dağıtıldıkları açıklandı. Bu ilkeleri ayrı bir laboratuvar ortamında ayarlama, üretim öncesi ve üretim ortamlarında kademeli olarak hazırlamadan önce önerilen ilkeleri anlamanıza ve değerlendirmenize olanak tanır. Yeni sağlanan ortamınız, değerlendirme ihtiyaçlarını yansıtacak şekilde yalnızca bulut veya karma olabilir.

## <a name="policy-set"></a>İlke kümesi

Aşağıdaki diyagramda önerilen ilkeler kümesi çiziliyor. Her ilkenin hangi koruma katmanı için geçerli olduğunu ve ilkelerin pc, telefon ve tabletlere mi yoksa her iki cihaz kategorisine mi uygulanacağı gösterir. Ayrıca, bu ilkeleri nerede yapılandırmış olduğunuz da gösterir.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-policies-byplan.png" alt-text="Sıfır Güven kimliği ve cihaz erişimini yapılandırmak için genel ilkeler." lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-policies-byplan.png":::


<!--

Here's a one-page PDF summary:

[![Thumb image for the Zero Trust identity and device protection for Microsoft 365 handout.](../../media/microsoft-365-policies-configurations/zero-trust-id-device-protection-model-handout-thumbnail.png)](../../downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf) <br> [View as a PDF](../../downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf) \| [Download as a PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/MSFT-cloud-architecture-identity-device-protection-handout.pdf)


--> 

Bu makalenin kalan kalanında bu ilkelerin nasıl yapılandırıldığından emin olun.

> [!NOTE]
> Cihazın hedeflenen kullanıcının sahip olduğundan emin olmak için, Intune'da cihazları kaydetmeden önce Çok faktörlü kimlik doğrulaması (MFA) kullanımının gerekli olması önerilir. Cihaz uyumluluk ilkelerini uygulayamadan önce cihazları Intune'a kaydettirmelisiniz.

Bu görevleri gerçekleştirmeniz için size zaman vermek için, başlangıç noktası ilkelerini bu tabloda listelenen sırayla uygulamanizi öneririz. Bununla birlikte, kurumsal ve özel koruma düzeyleri için MFA ilkeleri her zaman uygulanabilirsiniz.

|Koruma düzeyi|İlkeler|Daha fazla bilgi|Lisanslama|
|---|---|---|---|
|**Başlangıç noktası**|[Oturum açma riski orta veya yüksek olduğunda MFA  *gerektirme*](#require-mfa-based-on-sign-in-risk)||Microsoft 365 E5 E5 Microsoft 365 E3 ile iş veya güvenlik ekleme|
||[Modern kimlik doğrulamasını desteklemez istemcileri engelleme](#block-clients-that-dont-support-multi-factor)|Modern kimlik doğrulaması kullanmayan istemciler Koşullu Erişim ilkelerini atlar, bu nedenle bunları engellemek önemlidir.|Microsoft 365 E3 E5|
||[Yüksek riskli kullanıcıların parolayı değiştirmesi gerekir](#high-risk-users-must-change-password)|Yüksek riskli bir etkinlik algılandığında, kullanıcıların oturum alıkları için parolalarını değiştirmelerini gerekir.|Microsoft 365 E5 E5 Microsoft 365 E3 ile iş veya güvenlik ekleme|
||[Uygulama Koruma İlkeleri (UYGULAMA) veri korumasını uygulama](#apply-app-data-protection-policies)|Platform başına One Intune Uygulama Koruması ilkesi (Windows, iOS/iPadOS, Android).|Microsoft 365 E3 E5|
||[Onaylanan uygulamalar ve uygulama koruması gerektirme](#require-approved-apps-and-app-protection)|iOS, iPadOS veya Android kullanan telefonlar ve tabletler için mobil uygulama korumasını zorunlular.|Microsoft 365 E3 E5|
|**Enterprise**|[Oturum açma riski düşük, orta veya *yüksek olduğunda* MFA *gerektirme*](#require-mfa-based-on-sign-in-risk)||Microsoft 365 E5 E5 Microsoft 365 E3 ile iş veya güvenlik ekleme|
||[Cihaz uyumluluk ilkelerini tanımlama](#define-device-compliance-policies)|Her platform için bir ilke.|Microsoft 365 E3 E5|
||[Uyumlu bilgisayar ve mobil cihaz gerektirme](#require-compliant-pcs-and-mobile-devices)|Hem PC'ler (Windows macOS) hem de telefon veya tabletler (iOS, iPadOS veya Android) için Intune yönetimini zorlar.|Microsoft 365 E3 E5|
|**Özel güvenlik**|[*Her* zaman MFA gerektir](#assigning-policies-to-groups-and-users)||Microsoft 365 E3 E5|
|

## <a name="assigning-policies-to-groups-and-users"></a>Gruplara ve kullanıcılara ilke atama

İlkeleri yapılandırmadan önce, korumanın her katmanı için kullanmakta olduğunu Azure AD gruplarını seçin. Başlangıç noktası koruması normalde kuruluşta herkes için geçerlidir. Hem başlangıç noktası hem de kuruluş korumasına dahil olan bir kullanıcı, uygulanan tüm başlangıç noktası ilkelerini ve kurumsal ilkeleri olur. Koruma kümülatiftir ve en kısıtlayıcı ilke zorunludur.

Önerilen bir yöntem, Koşullu Erişim dışlama için bir Azure AD grubu oluşturmaktır. Atamalar bölümünde, Kullanıcılar ve gruplar ayarının Dışla değeri  bölümünde bu grubu **tüm Koşullu Erişim** **ilkelerinize** ekleyin. Bu size, erişim sorunlarını giderirken kullanıcıya erişim sağlamak için bir yöntem sağlar. Bu yalnızca geçici bir çözüm olarak önerilir. Bu grubu değişiklikler için izle ve dışlama grubunun yalnızca amaçlanan şekilde kullandığından emin olun.

İşte MFA gerektiren grup atamaları ve dışlamalar örneği.

![MFA ilkeleri için örnek grup ataması ve dışlamalar.](../../media/microsoft-365-policies-configurations/identity-access-policies-assignment.png)

Sonuçlar şöyledir:

- Oturum açma riski orta veya yüksek olduğunda, tüm kullanıcıların MFA'ya sahip olması gerekir.

- Oturum açma riski düşük, orta veya yüksek olduğunda Yönetim Personeli grubunun üyeleri MFA'nın kullanımı gereklidir.

  Bu durumda, Yönetim Personeli grubunun üyeleri hem başlangıç noktası hem de kurumsal Koşullu Erişim ilkeleriyle eşler. Her iki ilkenin erişim denetimleri birleştirilmiştir ve bu da kurumsal Koşullu Erişim ilkesiyle eşdeğerdir.

- MFA kullanmak için Project X grubunun üyeleri gerekir

  Bu durumda, Üst Gizli X Project üyeleri hem başlangıç noktası hem de özel güvenlik Koşullu Erişim ilkeleriyle eşler. Her iki ilkenin erişim denetimleri bir araya geldi. Özel güvenlik için erişim denetimi Koşullu Erişim ilkesi daha kısıtlayıcı olduğundan, kullanılır.

Gruplara ve kullanıcılara daha yüksek koruma düzeyleri uygularken dikkatli olun. Örneğin, Çok Gizli Project X grubunun üyeleri, Project X için özel güvenlik içeriği üzerinde çalışmıyor olsalar bile, her oturum aişlerinde MFA'Project gerekir.

Bu önerilerin bir parçası olarak oluşturulan tüm Azure AD grupları, grup olarak Microsoft 365 gerekir. Bu, belgelerde ve satırlarda belgelerin güvenliğini sağlarken duyarlılık etiketlerinin Microsoft Teams SharePoint.

![Yeni grup Microsoft 365 örneği.](../../media/microsoft-365-policies-configurations/identity-device-AAD-groups.png)

## <a name="require-mfa-based-on-sign-in-risk"></a>Oturum açma riski temel alarak MFA gerektirme

Kullanıcılarınızı, MFA'nın kullanımını gerektirmeden önce kaydetmelerini gerekir. Microsoft 365 E5, E5 Güvenlik Microsoft 365 E3, EMS E5 ile Office 365 veya bireysel Azure AD Premium P2 lisansınız varsa, kullanıcıların MFA'ya kaydolmasını gerektirmek için Azure AD Kimlik Koruması ile MFA kayıt ilkesi kullanabilirsiniz. [Önkoşul çalışma](identity-access-prerequisites.md), tüm kullanıcıların MFA'ya kaydını içerir.

Kullanıcılarınız kaydedildikten sonra, yeni bir Koşullu Erişim ilkesiyle MFA'nın oturum açmasını gerekli bulundurabilirsiniz.

1. [Azure portalına gidin](https://portal.azure.com) ve kimlik bilgilerinizle oturum açın.
2. Azure hizmetleri listesinde, Ekle'yi **Azure Active Directory**.
3. Yönet listesinde **Güvenlik'i** **seçin ve** sonra da Koşullu **Erişim'i seçin**.
4. Yeni **ilke'yi** seçin ve yeni ilkenin adını yazın.

Aşağıdaki tablolarda, oturum açma riski temel alarak MFA'nın gerekli olduğu Koşullu Erişim ilkesi ayarları açık almaktadır.

Ödevler **bölümünde** :

|Ayar|Özellikler|Değerler|Notlar|
|---|---|---|---|
|Kullanıcılar ve gruplar|Dahil|**Kullanıcıları ve grupları seçin >: Hedefli** kullanıcı hesaplarını içeren belirli grupları seçin.|Pilot kullanıcı hesaplarını içeren grupla çalışmaya başlama.|
||Dışla|**Kullanıcılar ve gruplar**: Koşullu Erişim özel durum grubunızı seçin; (uygulama kimlikleri) gibi hesaplar.|Üyelik, gerektiği şekilde, geçici olarak değiştirilmelidir.|
|Bulut uygulamaları veya eylemleri|**Bulut uygulamaları > Içerir**|**Uygulamalar'ı** seçin: Bu ilkenin uygulamak istediğiniz uygulamaları seçin. Örneğin, Tamam'ı Exchange Online.||
|Koşullar|||Ortamınıza ve ihtiyaçlarına özel koşulları yapılandırabilirsiniz.|
||Oturum açma riski||Aşağıdaki tabloda yer alan kılavuza bakın.|
|

### <a name="sign-in-risk-condition-settings"></a>Oturum açma riski koşulu ayarları

Hedeflerken koruma düzeyine dayalı olarak risk düzeyi ayarlarını uygulama.

|Koruma düzeyi|Gereken risk düzeyi değerleri|Eylem|
|---|---|---|
|Başlangıç noktası|Yüksek, orta|Her ikisini de kontrol edin.|
|Enterprise|Yüksek, orta, düşük|Bunların üçünü de kontrol edin.|
|Özel güvenlik||MFA'nın her zaman zorunlu kılınması için tüm seçenekleri işaretsiz bırakın.|
|

**Access denetimleri bölümünde**:

|Ayar|Özellikler|Değerler|Eylem|
|---|---|---|---|
|Grant|**Grant access**||Seç|
|||**Çok faktörlü kimlik doğrulaması gerektirme**|Çek|
||**Tüm seçili denetimlere gerektir**||Seç|
|

Ver **ayarlarını kaydetmek** için **Seç'i** seçin.

Son olarak **İlkeyi etkinleştir** **için Etkin seçeneğini,** ardından Oluştur'ı **seçin**.

İlkeyi test [etmek için](/azure/active-directory/active-directory-conditional-access-whatif) Eğer aracına da göz önünde bulundurabilirsiniz.

## <a name="block-clients-that-dont-support-multi-factor"></a>Multi-factor desteği olmayan istemcileri engelleme

Multi-Factor Authentication desteği olmayan istemcileri engellemek üzere koşullu Erişim ilkesi için bu tablolarda yer alan ayarları kullanın.

Çok [faktörlü](../../enterprise/microsoft-365-client-support-multi-factor-authentication.md) kimlik doğrulamasını destekleyen Microsoft 365 istemcilerin listesi için bu makaleye bakın.

Ödevler **bölümünde** :

|Ayar|Özellikler|Değerler|Notlar|
|---|---|---|---|
|Kullanıcılar ve gruplar|Dahil|**Kullanıcıları ve grupları seçin >: Hedefli** kullanıcı hesaplarını içeren belirli grupları seçin.|Pilot kullanıcı hesaplarını içeren grupla çalışmaya başlama.|
||Dışla|**Kullanıcılar ve gruplar**: Koşullu Erişim özel durum grubunızı seçin; (uygulama kimlikleri) gibi hesaplar.|Üyelik, gerektiği şekilde, geçici olarak değiştirilmelidir.|
|Bulut uygulamaları veya eylemleri|**Bulut uygulamaları > Içerir**|**Uygulamaları seçin**: Modern kimlik doğrulamasını desteklemeen istemcilere karşılık gelen uygulamaları seçin.||
|Koşullar|**İstemci uygulamaları**|Yapılandırma **için Evet'i** **seçin** <p> Tarayıcı ve Mobil uygulamalar **ile masaüstü** **istemcilerinin onay işaretlerini temizleme**||
|

**Access denetimleri bölümünde**:

|Ayar|Özellikler|Değerler|Eylem|
|---|---|---|---|
|Grant|**Erişimi engelle**||Seç|
||**Tüm seçili denetimlere gerektir**||Seç|
|

Ver **ayarlarını kaydetmek** için **Seç'i** seçin.

Son olarak **İlkeyi etkinleştir** **için Etkin seçeneğini,** ardından Oluştur'ı **seçin**.

İlkeyi [test etmek için](/azure/active-directory/active-directory-conditional-access-whatif) Eğer aracına göz önünde bulundurabilirsiniz.

Daha fazla Exchange Online için, kimlik doğrulama ilkelerini kullanarak Temel kimlik doğrulamayı devre dışı kullanabilirsiniz [ve bu](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online) da tüm istemci erişimi isteklerini modern kimlik doğrulamayı kullanmaya gerektirir.

## <a name="high-risk-users-must-change-password"></a>Yüksek riskli kullanıcıların parolayı değiştirmesi gerekir

Yüksek riskli tüm kullanıcıların hesaplarında oturum aya alıkan parola değişikliği gerçekleştirmek zorunda olduğundan emin olmak için, aşağıdaki ilkeyi uygulamış olun.

Güvenlik portalında [(Microsoft Azurehttps://portal.azure.com)](https://portal.azure.com/) kimlik bilgilerinizle) oturum açın ve ardından Kullanıcı Riski İlkesi'ne > **Azure AD Kimlik Koruması'ne gidin**.

Ödevler **bölümünde** :

|Tür|Özellikler|Değerler|Eylem|
|---|---|---|---|
|Kullanıcılar|Dahil|**Tüm kullanıcılar**|Seç|
|Kullanıcı riski|**Yüksek**||Seç|
|

İkinci **Ödevler bölümünde** :

|Tür|Özellikler|Değerler|Eylem|
|---|---|---|---|
|Access|**Erişime izin ver**||Seç|
|||**Parola değişikliği gerektirme**|Çek|
|

Access **ayarlarını** kaydetmek için **Bitti'yi** seçin.

Son olarak, **zorunlu ilke için** **On'ı seçin** ve sonra kaydet'i **seçin**.

İlkeyi [test etmek için](/azure/active-directory/active-directory-conditional-access-whatif) Eğer aracına göz önünde bulundurabilirsiniz.

Bu ilkeyi [Azure AD](/azure/active-directory/authentication/concept-password-ban-bad) parola korumasını yapılandırma ile birlikte kullanın. Bu koruma, bilinen zayıf parolaları ve değişkenlerini ve organizasyona özgü diğer zayıf terimleri algılayan ve engelleyen Azure AD parola korumasını kullanır. Azure AD parola korumasının kullanılması, değiştirilen parolaların güçlü parolalar olması için tasarlanmıştır.

## <a name="apply-app-data-protection-policies"></a>UYGULAMA veri koruma ilkelerini uygulama

APP'ler, izin verilen uygulamaları ve bu uygulamaların kuruluş verilerinizle gerçekleştireceği eylemleri tanımlar. UYGULAMA'da kullanılabilen seçenekler, kuruluşların korumayı kendi özel gereksinimlerine göre uyarlamasını sağlar. Bazılarında, tam bir senaryoyu uygulamak için hangi ilke ayarlarının gerekli olduğu belli olabilir. Kuruluşların mobil istemci uç noktasını koruma önceliklerini belirlemelerine yardımcı olmak için, Microsoft iOS ve Android mobil uygulama yönetimine için UYGULAMA veri koruma çerçevesiyle ilgili taksonomi sundu.

UYGULAMA veri koruma çerçevesi, her düzey bir önceki düzeyden yapılandırmaya sahip üç ayrı yapılandırma düzeyi olarak düzenlenmiştir:

- **Düzey 1: Enterprise koruma**, uygulamaların PIN ile korunmasını, şifreli ve seçmeli temizleme işlemlerini gerçekleştirir. Android cihazlarda, bu düzey Android cihaz doğrulamayı doğrular. Bu, posta kutusu ilkeleri içinde benzer bir veri koruma denetimi sağlayan, Exchange Online ve UYGULAMA'ya IT ve kullanıcı popülasyonu sağlayan bir girdi düzeyi yapılandırmasıdır.
- **Düzey 2: Gelişmiş Enterprise koruması**, UYGULAMA veri sızıntısını önleme mekanizmaları ve en düşük işletim sistemi gereksinimlerini ortaya sunmaktadır. Bu, iş veya okul verilerine erişen mobil kullanıcıların çoğu için geçerli olan yapılandırmadır.
- **Düzey 3: Enterprise** koruma, gelişmiş veri koruma mekanizmaları, gelişmiş PIN yapılandırması ve UYGULAMA Mobil Tehdit Savunması'nın tanıtımını sağlar. Bu yapılandırma, yüksek riskli verilere erişen kullanıcılar için tercih edilir.

Her yapılandırma düzeyi için belirli önerileri ve korunması gereken minimum uygulamaları görmek için, uygulama koruma ilkelerini [kullanarak Veri koruma çerçevesi'ne bakın](/mem/intune/apps/app-protection-framework).

Sıfır Güven kimliği ve cihaz erişim yapılandırmalarında belirtilen ilkeler [kullanılarak, Başlangıç](microsoft-365-policies-configurations.md) Enterprise katmanlarını Düzey 2 kurumsal gelişmiş veri koruma ayarlarıyla yakın bir şekilde eşler. Özelleştirilmiş güvenlik koruması katmanı, Düzey 3 kurumsal yüksek veri koruma ayarlarına yakın bir şekilde eşler.

|Koruma düzeyi|Uygulama Koruma İlkesi|Daha fazla bilgi|
|---|---|---|
|Başlangıç noktası|[Düzey 2 geliştirilmiş veri koruması](/mem/intune/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)|Düzey 2'de zorunlu kılınan ilke ayarları, düzey 1 için önerilen tüm ilke ayarlarını içerir ve yalnızca düzey 1'den daha fazla denetim ve daha gelişmiş yapılandırma uygulamak için aşağıdaki ilke ayarlarına ekler veya ayarları günceller.|
|Enterprise|[Düzey 2 geliştirilmiş veri koruması](/mem/intune/apps/app-protection-framework#level-2-enterprise-enhanced-data-protection)|Düzey 2'de zorunlu kılınan ilke ayarları, düzey 1 için önerilen tüm ilke ayarlarını içerir ve yalnızca düzey 1'den daha fazla denetim ve daha gelişmiş yapılandırma uygulamak için aşağıdaki ilke ayarlarına ekler veya ayarları günceller.|
|Özel güvenlik|[Düzey 3 kurumsal yüksek veri koruması](/mem/intune/apps/app-protection-framework#level-3-enterprise-high-data-protection)|Düzey 3'te zorunlu kılınan ilke ayarları, düzey 1 ve 2 için önerilen tüm ilke ayarlarını içerir ve düzey 2'den daha fazla denetim ve daha gelişmiş yapılandırma uygulamak için yalnızca aşağıdaki ilke ayarlarına ekler veya ayarları günceller.|
|

Her platform (iOS ve Android) için veri koruma çerçevesi ayarlarını kullanarak Microsoft Endpoint Manager bir uygulama koruma ilkesi oluşturmak için şunları yapabilirsiniz:

1. İlkeleri el ile oluşturmak için Bu Uygulamayı Koruma ilkeleriyle uygulama [koruma ilkelerini oluşturma ve dağıtma altında Microsoft Intune](/mem/intune/apps/app-protection-policies).
2. [Intune'un PowerShell betikleriyle örnek Intune Uygulama Koruması İlkesi Configuration Framework JSON](https://github.com/microsoft/Intune-Config-Frameworks/tree/master/AppProtectionPolicies) [şablonlarını içeri aktarın](https://github.com/microsoftgraph/powershell-intune-samples).

## <a name="require-approved-apps-and-app-protection"></a>Onaylanan uygulamalar ve UYGULAMA koruması gerektirme

Intune'da uyguladınız Uygulama koruma ilkelerini zorunlu uygulamak için, onaylanmış istemci uygulamalarına ve UYGULAMA koruma ilkeleri içinde ayarlanmış koşulları gerektirecek bir Koşullu Erişim ilkesi oluşturmanız gerekir.

Uygulama koruma ilkelerinin zor olması için, Koşullu Erişimle bulut uygulama erişimi için uygulama koruma [ilkesi gerektirme konusunda açıklanan bir dizi ilke gerekir](/azure/active-directory/conditional-access/app-protection-based-conditional-access). Bu ilkelerin her biri önerilen kimlik ve erişim yapılandırma ilkeleri kümesinde yer almaktadır.

Onaylanmış uygulamalar ve UYGULAMA koruması gerektiren Koşullu Erişim ilkesi oluşturmak için, Mobil cihazlarda onaylı istemci uygulamaları veya [](/azure/active-directory/conditional-access/howto-policy-approved-app-or-app-protection#require-approved-client-apps-or-app-protection-policy-with-mobile-devices)uygulama koruma ilkesi gerektirme altında yer alan ve yalnızca Uygulama koruma ilkeleri tarafından korunan mobil uygulamalar içindeki hesapların Microsoft 365 uç noktalarına izin veren adımları izleyin.

   > [!NOTE]
   > Bu ilke, mobil kullanıcıların tüm kullanıcılarının tüm Microsoft 365 uç noktalarına uygun uygulamaları kullanarak erişmelerini sağlar.

Bu ilke, mobil Exchange ActiveSync istemcilerinin mobil cihaza bağlanmalarını da Exchange Online. Bununla birlikte, tüm cihazlarınız arasında veri işlemeye Exchange ActiveSync ilke oluşturabilirsiniz. Daha fazla bilgi için bkz[. Temel](secure-email-recommended-policies.md#block-activesync-clients) kimlik doğrulamasından yararlanarak Exchange ActiveSync istemcilerinin Exchange Online engelleme. Bu ilke, bu makalenin en başındaki resimde yer alan resim değildir. E-postanın güvenliğini sağlamayla [ilgili ilke önerileri makalesinde açıklanmıştır ve resime bakabilirsiniz](secure-email-recommended-policies.md).

 Bu ilke, Onaylandı istemci uygulaması [gerektirir ve](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-approved-client-app) Uygulama koruma [ilkesi gerektir denetimlerini etkinleştirir](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-app-protection-policy).

Son olarak, iOS ve Android cihazlarda diğer istemci uygulamalarının eski kimlik doğrulamasını engellemek, bu istemcilerin Koşullu Erişim ilkelerini atlaymalarını sağlar. Bu makaledeki rehbere takip ediyorsanız, modern kimlik doğrulamasını desteklemez istemcileri [engelle'yi zaten yapılandırmış durumda olursanız](#block-clients-that-dont-support-multi-factor).

<!---
With Conditional Access, organizations can restrict access to approved (modern authentication capable) iOS and Android client apps with Intune app protection policies applied to them. Several Conditional Access policies are required, with each policy targeting all potential users. Details on creating these policies can be found in [Require app protection policy for cloud app access with Conditional Access](/azure/active-directory/conditional-access/app-protection-based-conditional-access).

1. Follow "Step 1: Configure an Azure AD Conditional Access policy for Microsoft 365" in [Scenario 1: Microsoft 365 apps require approved apps with app protection policies](/azure/active-directory/conditional-access/app-protection-based-conditional-access#scenario-1-office-365-apps-require-approved-apps-with-app-protection-policies), which allows Outlook for iOS and Android, but blocks OAuth capable Exchange ActiveSync clients from connecting to Exchange Online.

   > [!NOTE]
   > This policy ensures mobile users can access all Office endpoints using the applicable apps.

2. If enabling mobile access to Exchange Online, implement [Block ActiveSync clients](secure-email-recommended-policies.md#block-activesync-clients), which prevents Exchange ActiveSync clients leveraging basic authentication from connecting to Exchange Online.

   The above policies leverage the grant controls [Require approved client app](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-approved-client-app) and [Require app protection policy](/azure/active-directory/conditional-access/concept-conditional-access-grant#require-app-protection-policy).

3. Disable legacy authentication for other client apps on iOS and Android devices. For more information, see [Block clients that don't support modern authentication](#block-clients-that-dont-support-modern-authentication).
-->

## <a name="define-device-compliance-policies"></a>Cihaz uyumluluğu ilkelerini tanımlama

Cihaz uyumluluğu ilkeleri, cihazların uyumlu olarak belirlenecek şekilde karşılaması gereken gereksinimleri tanımlar. Intune cihaz uyumluluk ilkelerini, yönetim merkezinden Microsoft Endpoint Manager oluşturabilirsiniz.

Her bir bilgisayar, telefon veya tablet platformu için bir ilke oluşturmanız gerekir:

- Android cihaz yöneticisi
- Android Enterprise
- iOS/iPadOS
- macOS
- Windows 8.1 ve sonrası
- Windows 10 sonra

Cihaz uyumluluk ilkeleri oluşturmak için, Microsoft Endpoint Manager Yönetim Merkezi'nde yönetici kimlik bilgilerinizle oturum açın ve Ardından [](https://endpoint.microsoft.com) Cihazlar Uyumluluk **İlkeleri'ne** \> **gidin**\>. İlke **Oluştur'a seçin**.

Cihaz uyumluluk ilkelerinin dağıtılması için, bunlar kullanıcı gruplarına atanmalıdır. İlkeyi oluşturduk ve kaydeddikten sonra atarsiniz. Yönetim merkezinde ilkeyi ve ardından **Ödevler'i seçin**. İlkeyi almak istediğiniz grupları seçdikten sonra, kaydet'i seçerek grup atamalarını kaydedin ve ilkeyi dağıtın.

Intune'da uyumluluk ilkeleri oluşturmayla ilgili adım adım kılavuz için, Intune belgelerinde yer alan [Microsoft Intune](/mem/intune/protect/create-compliance-policy) ilke oluşturma.

### <a name="recommended-settings-for-ios"></a>iOS için önerilen ayarlar

iOS/iPadOS, ikisi bu altyapının bir parçası olarak ele alınan çeşitli kayıt senaryolarını destekler:

- [Kişisel olarak sahip olunan cihazlar için cihaz](/mem/intune/enrollment/ios-enroll) kaydı – bu cihazlar kişisel olarak kullanım için ve hem iş hem de kişisel kullanım için kullanılır.
- [Şirket sahibi cihazlar için denetlemeli](/mem/intune/enrollment/device-enrollment-program-enroll-ios) otomatik cihaz kaydı – bu cihazlar tek bir kullanıcıyla ilişkilendirilmiş, kurumsal ürüne ait olup kişisel kullanım için değil, iş için özel olarak kullanılır.

iOS/iPadOS güvenlik yapılandırma çerçevesi, kişisel olarak sahip olunan ve denetleme yapılan cihazlar için yol gösterici çeşitli yapılandırma senaryolarında düzenlenmiştir.

Kişisel olarak sahip olunan cihazlar için:

- Temel güvenlik (Düzey 1) – Microsoft, kullanıcıların iş veya okul verilerine erişen kişisel cihazlar için en düşük güvenlik yapılandırması olarak bu yapılandırmayı önermektedir. Bu, parola ilkelerinin, cihaz kilit özelliklerinin zorlanmaları ve bazı cihaz işlevlerinin (örneğin, güvenilmeyen sertifikalar) devre dışı bırakılmasıyla yapılır.
- İyileştirilmiş güvenlik (Düzey 2) – Microsoft kullanıcıların hassas veya gizli bilgilere erişen cihazlar için bu yapılandırmayı öneriyoruz. Bu yapılandırma, veri paylaşımı denetimlerini yürürlüğe koyar. Bu yapılandırma, cihaz üzerinde iş veya okul verilerine erişen mobil kullanıcıların çoğu için geçerlidir.
- Yüksek güvenlik (Düzey 3) – Microsoft benzersiz ölçüde yüksek riskli belirli kullanıcılar veya gruplar tarafından kullanılan cihazlar için bu yapılandırmayı önermektedir (yetkisiz ifşanın kuruluşta önemli ölçüde malzeme kaybına neden olduğu son derece hassas veriler kullanan kullanıcılar). Bu yapılandırma daha güçlü parola ilkeleri gerçekleştirir, bazı cihaz işlevlerini devre dışı kılar ve ek veri aktarımı kısıtlamalarını zorunlu kılar.

Denetlenen cihazlar için:

- Temel güvenlik (Düzey 1) – Microsoft, kullanıcıların iş veya okul verilerine erişen denetlenen cihazlar için en düşük güvenlik yapılandırması olarak bu yapılandırmayı öneriyoruz. Bu, parola ilkelerinin, cihaz kilit özelliklerinin zorlanmaları ve bazı cihaz işlevlerinin (örneğin, güvenilmeyen sertifikalar) devre dışı bırakılmasıyla yapılır.
- İyileştirilmiş güvenlik (Düzey 2) – Microsoft kullanıcıların hassas veya gizli bilgilere erişen cihazlar için bu yapılandırmayı öneriyoruz. Bu yapılandırma, veri paylaşımı denetimlerini yürürlüğe koyar ve USB cihazlarına erişimi engeller. Bu yapılandırma, cihaz üzerinde iş veya okul verilerine erişen mobil kullanıcıların çoğu için geçerlidir.
- Yüksek güvenlik (Düzey 3) – Microsoft benzersiz ölçüde yüksek riskli belirli kullanıcılar veya gruplar tarafından kullanılan cihazlar için bu yapılandırmayı önermektedir (yetkisiz ifşanın kuruluşta önemli ölçüde malzeme kaybına neden olduğu son derece hassas veriler kullanan kullanıcılar). Bu yapılandırma daha güçlü parola ilkeleri gerçekleştirir, bazı cihaz işlevlerini devre dışı kılar, ek veri aktarma kısıtlamalarını zorunlu kılar ve Apple'ın toplu satın alma programı aracılığıyla uygulamaların yüklenmiş olarak uygulanmasını gerektirir.

Sıfır Güven kimliği ve cihaz erişim yapılandırmalarında belirtilen ilkeler [kullanılarak, Başlangıç](microsoft-365-policies-configurations.md) Enterprise katmanı, Düzey 2'nin gelişmiş güvenlik ayarlarıyla yakın bir eşler. Özelleştirilmiş güvenlik koruması katmanı, Düzey 3 yüksek güvenlik ayarlarına yakın bir şekilde eşler.

|Koruma düzeyi  |Cihaz ilkesi |Daha fazla bilgi  |
|---------|---------|---------|
|Başlangıç noktası     |Gelişmiş güvenlik (Düzey 2)         |Düzey 2'de zorunlu kılınan ilke ayarları, düzey 1 için önerilen tüm ilke ayarlarını içerir ve yalnızca düzey 1'den daha fazla denetim ve daha gelişmiş yapılandırma uygulamak için aşağıdaki ilke ayarlarına ekler veya ayarları günceller.         |
|Enterprise     |Gelişmiş güvenlik (Düzey 2)         |Düzey 2'de zorunlu kılınan ilke ayarları, düzey 1 için önerilen tüm ilke ayarlarını içerir ve yalnızca düzey 1'den daha fazla denetim ve daha gelişmiş yapılandırma uygulamak için aşağıdaki ilke ayarlarına ekler veya ayarları günceller.         |
|Özel güvenlik     |Yüksek güvenlik (Düzey 3)         |Düzey 3'te zorunlu kılınan ilke ayarları, düzey 1 ve 2 için önerilen tüm ilke ayarlarını içerir ve düzey 2'den daha fazla denetim ve daha gelişmiş yapılandırma uygulamak için yalnızca aşağıdaki ilke ayarlarına ekler veya ayarları günceller.         |

Her yapılandırma düzeyi için belirli cihaz uyumluluğu ve cihaz kısıtlama önerilerini görmek için [, iOS/iPadOS Security Configuration Framework'u gözden geçirebilirsiniz](/mem/intune/enrollment/ios-ipados-configuration-framework).

### <a name="recommended-settings-for-android"></a>Android için önerilen ayarlar

Android Enterprise, bu çerçeve kapsamında ikisi de ele alan birkaç kayıt senaryosunu destekler:

- [Android Enterprise profili](/intune/android-work-profile-enroll) – Bu kayıt modeli normalde kişisel cihazlar için kullanılır ve IT iş ve kişisel veriler arasında net bir ayırma sınırı sağlamak ister. IT tarafından denetlenen ilkeler, çalışma verilerin kişisel profile aktarılamay olduğundan emin olun.
- [Android Enterprise yönetilen](/intune/android-fully-managed-enroll) cihazlara sahip: Bu cihazlar, tek bir kullanıcıyla ilişkilendirilmiş, kurumsal bir cihazdır ve kişisel kullanım için değil, iş için özel olarak kullanılır.

Android Enterprise yapılandırma çerçevesi, iş profili ve tam olarak yönetilen senaryolar için yol gösterici çeşitli yapılandırma senaryoları olarak düzenlenmiştir.

Android veya Enterprise profili cihazları için:

- İş profilinde artırılmış güvenlik (Düzey 2) – Microsoft, kullanıcıların iş veya okul verilerine erişen kişisel cihazlar için en düşük güvenlik yapılandırması olarak bu yapılandırmayı öneriyoruz. Bu yapılandırma parola gereksinimlerini karşılar, iş ve kişisel verileri birbirinden yorumlar ve Android cihazı doğrulamayı doğrular.
- İş profili yüksek güvenliği (Düzey 3) – Microsoft benzersiz olarak yüksek riskli belirli kullanıcılar veya gruplar tarafından kullanılan cihazlar için bu yapılandırmayı önermektedir (yetkisiz açıklama kuruluşta önemli ölçüde malzeme kaybına neden olduğu, yüksek gizli verileri iş alan kullanıcılar). Bu yapılandırma mobil tehdit savunmasını veya Uç Nokta için Microsoft Defender'ı tanıtıyor, en küçük Android sürümünü ayarıyor, daha güçlü parola ilkeleri oluşturuyor ve iş ile kişisel ayrımı daha fazla kısıtlar.

Android ve Enterprise yönetilen cihazlar için:

- Tümüyle yönetilen temel güvenlik (Düzey 1) – Microsoft, kurumsal bir cihaz için bu yapılandırmayı en düşük güvenlik yapılandırması olarak önermektedir. Bu yapılandırma, iş veya okul verilerine erişen mobil kullanıcıların çoğu için geçerlidir. Bu yapılandırmada parola gereksinimleri vardır, Android'in en düşük sürümünü ayarlar ve bazı cihaz kısıtlamaları geçerli olur.
- Tam olarak yönetilen gelişmiş güvenlik (Düzey 2) – Microsoft kullanıcıların hassas veya gizli bilgilere erişen cihazlar için bu yapılandırmayı öneriyoruz. Bu yapılandırma daha güçlü parola ilkelerine sahip olur ve kullanıcı/hesap özelliklerini devre dışı kılar.
- Tam olarak yönetilen yüksek güvenlik (Düzey 3) - Microsoft, benzersiz olarak yüksek riskli belirli kullanıcılar veya gruplar tarafından kullanılan cihazlar için bu yapılandırmayı önermektedir (yetkisiz açıklama kuruluşta önemli ölçüde malzeme kaybına neden olduğu yüksek hassas verileri işleen kullanıcılar). Bu yapılandırma en düşük Android sürümünü artırır, mobil tehdit savunmasını veya Uç Nokta için Microsoft Defender'ı kullanır ve ek cihaz kısıtlamalarını zorunlu tutar.

Sıfır Güven kimliği ve cihaz erişim yapılandırmalarında belirtilen ilkeler [kullanılarak, Başlangıç](microsoft-365-policies-configurations.md) noktası ve Enterprise koruma katmanları, kişisel olarak sahip olunan cihazlar için Düzey 1 temel güvenliği ve tam olarak yönetilen cihazlar için Düzey 2 gelişmiş güvenlik ayarlarıyla yakın bir şekilde eşler. Özelleştirilmiş güvenlik koruması katmanı, Düzey 3 yüksek güvenlik ayarlarına yakın bir şekilde eşler.

Android veya Enterprise profili cihazları için:

|Koruma düzeyi  |Cihaz ilkesi |Daha fazla bilgi  |
|---------|---------|---------|
|Başlangıç noktası     |İş Profili: Temel güvenlik (Düzey 1)      |Yok         |
|Enterprise     |İş Profili: Temel güvenlik (Düzey 1)         |Yok         |
|Başlangıç noktası     |Tümüyle Yönetilen: Gelişmiş Güvenlik (Düzey 2)       |Düzey 2'de zorunlu kılınan ilke ayarları, düzey 1 için önerilen tüm ilke ayarlarını içerir ve yalnızca düzey 1'den daha fazla denetim ve daha gelişmiş yapılandırma uygulamak için aşağıdaki ilke ayarlarına ekler veya ayarları günceller.         |
|Enterprise     |Tümüyle Yönetilen: Gelişmiş Güvenlik (Düzey 2)         |Düzey 2'de zorunlu kılınan ilke ayarları, düzey 1 için önerilen tüm ilke ayarlarını içerir ve yalnızca düzey 1'den daha fazla denetim ve daha gelişmiş yapılandırma uygulamak için aşağıdaki ilke ayarlarına ekler veya ayarları günceller.         |
|Özel güvenlik     |Yüksek güvenlik (Düzey 3)         |Düzey 3'te zorunlu kılınan ilke ayarları, düzey 1 ve 2 için önerilen tüm ilke ayarlarını içerir ve düzey 2'den daha fazla denetim ve daha gelişmiş yapılandırma uygulamak için yalnızca aşağıdaki ilke ayarlarına ekler veya ayarları günceller.         |

Her yapılandırma düzeyi için belirli cihaz uyumluluğu ve cihaz kısıtlama önerilerini görmek için [Android Güvenlik Enterprise'i gözden geçirebilirsiniz](/mem/intune/enrollment/android-configuration-framework).

### <a name="recommended-settings-for-windows-10-and-later"></a>E-Windows 10 sonrası için önerilen ayarlar

Aşağıdaki ayarlar, 2. Adım **:** İlke oluşturma Windows 10 uyumluluk ayarları'ta yapılandırıldığında ve daha sonraki bir işlemle çalışan bilgisayarlar için önerilir.

Cihaz **durumu ve > Windows Durum Attestation Service değerlendirme kuralları için**, bu tabloya bakın.

|Özellikler|Değer|Eylem|
|---|---|---|
|BitLocker Gerektir|Gerektir|Seç|
|Cihazda Güvenli Önyükleme'nin etkinleştirilmesi gerekir|Gerektir|Seç|
|Kod bütünlüğü gerekli|Gerektir|Seç|
|

Cihaz **özellikleri için**, işletim sistemi sürümleri için uygun değerleri, IT ve güvenlik ilkelerinize göre belirtin.

Yapılandırma **Yöneticisi Uyumluluğu için** Gerektir'i **seçin**.

Sistem **güvenliği için** bu tabloya bakın.

|Tür|Özellikler|Değer|Eylem|
|---|---|---|---|
|Password|Mobil cihazların kilidini açmak için parola gerektirme|Gerektir|Seç|
||Basit parolalar|Engelle|Seç|
||Parola türü|Cihaz varsayılanı|Seç|
||Minimum parola uzunluğu|6|Tür|
||Parola gerekli olmadan önce çalışma dışı en fazla dakika|15|Tür <p> Bu ayar Android'in 4.0 ve üzeri ya da KNOX 4.0 ve üzeri sürümlerinde de kullanılabilir. iOS cihazlarda, iOS 8.0 ve üzeri için desteklemektedir.|
||Parola süre sonu (gün)|41|Tür|
||Yeniden kullanımı önlemek için önceki parola sayısı|5|Tür|
||Cihaz boşta durumuna döndüğünde parola gerektir (Mobil ve Holographic)|Gerektir|Sonraki Windows 10 kullanılabilir|
|Şifreleme|Cihazda veri depolamayı şifreleme|Gerektir|Seç|
|Cihaz Güvenliği|Güvenlik Duvarı|Gerektir|Seç|
||Virüsten koruma|Gerektir|Seç|
||Antiware|Gerektir|Seç <p> Bu ayar için, Windows Güvenliği uygulamasına kaydedilmiş bir Casus Yazılım önleme çözümü gerekir.|
|Bulut için Defender|Microsoft Defender Kötü Amaçlı Yazılımdan Koruma|Gerektir|Seç|
||Microsoft Defender Kötü amaçlı yazılımdan koruma minimum sürümü||Tür <p> Yalnızca masaüstü Windows 10 destekler. Microsoft, en son sürümden beş taneden daha eski sürümleri önerilmez.|
||Microsoft Defender Kötü amaçlı yazılımlardan koruma imzası güncel|Gerektir|Seç|
||Gerçek zamanlı koruma|Gerektir|Seç <p> Yalnızca masaüstü ve Windows 10 için desteklenen|
|

#### <a name="microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender

|Tür|Özellikler|Değer|Eylem|
|---|---|---|---|
|Microsoft Endpoint Manager yönetim merkezinde Uç nokta kuralları için Microsoft Defender|[Cihazın makine risk puanına göre veya altında olması gerekir](/mem/intune/protect/advanced-threat-protection-configure#create-and-assign-compliance-policy-to-set-device-risk-level)|Orta|Seç|
|

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

## <a name="require-compliant-pcs-and-mobile-devices"></a>Uyumlu bilgisayar ve mobil cihaz gerektirme

Tüm cihazlara uyumluluk gerektirmek için:

1. [Azure portalına gidin](https://portal.azure.com) ve kimlik bilgilerinizle oturum açın.
2. Azure hizmetleri listesinde, Ekle'yi **Azure Active Directory**.
3. Yönet listesinde **Güvenlik'i** **seçin ve** sonra da Koşullu **Erişim'i seçin**.
4. Yeni **ilke'yi** seçin ve yeni ilkenin adını yazın.

5. **Ödevler'in** altında **Kullanıcılar ve gruplar'ı** seçin ve ilkenin kimlere başvurmalarını istediğinize dahil seçin. Koşullu Erişim dışlama grubunızı da dışla.

6. **Ödevler'in altında** Bulut **uygulamaları veya eylemleri'ne seçin**.

7. Ekle **için**, **Uygulama seç'> Seç'i** seçin ve ardından Bulut uygulamaları **listesinden istediğiniz uygulamaları** seçin. Örneğin, Tamam'ı Office 365. Bittiğinde **seç'i** seçin.

8. Erişim **denetimleri'nin** altında **Ver'i seçin** .

9. Erişim **ver'i** seçin ve ardından **Cihazın uyumlu olarak işaretlenirken işaretlenir.** Birden çok denetim için Tüm **seçili denetimleri gerektir'i seçin**. Tamamlandığında Seç'i **seçin**.

10. **İlkeyi** etkinleştir **için On'ı** seçin ve sonra da **Oluştur'a seçin**.

> [!NOTE]
> Bu ilkeyi etkinleştirmeden önce cihazınızın uyumlu olduğundan emin olun. Bunu yapamazsanız, kilitlenir ve kullanıcı hesabınız Koşullu Erişim dışlama grubuna eklenene kadar bu ilkeyi değiştiremezsiniz.

## <a name="next-step"></a>Sonraki adım

[![3. Adım: Konuk ve dış kullanıcılar için ilkeler.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-3.png)](identity-access-policies-guest-access.md)

[Konuk ve dış kullanıcılara ilke önerileri hakkında bilgi](identity-access-policies-guest-access.md)
