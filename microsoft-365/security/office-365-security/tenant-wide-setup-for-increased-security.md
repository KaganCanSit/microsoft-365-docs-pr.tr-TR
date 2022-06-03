---
title: Daha fazla güvenlik için Microsoft 365 kiracınızı yapılandırma
f1.keywords:
- NOCSH
ms.author: bcarter
author: BrendaCarter
manager: laurawi
ms.date: 04/06/2022
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_IP
- M365-security-compliance
search.appverid: MET150
ms.assetid: 8d274fe3-db51-4107-ba64-865e7155b355
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
description: Bu konu, Microsoft 365 ortamınızın güvenliğini etkileyen kiracı genelindeki ayarlar için önerilen yapılandırmada size yol gösterir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a1a9b7e6a006eb63078f237ce1078d6aa825fa14
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65872373"
---
# <a name="configure-your-microsoft-365-tenant-for-increased-security"></a>Daha fazla güvenlik için Microsoft 365 kiracınızı yapılandırma

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Bu konu, Microsoft 365 ortamınızın güvenliğini etkileyen kiracı genelindeki ayarlar için önerilen yapılandırmada size yol gösterir. Güvenlik gereksinimleriniz daha fazla veya daha az güvenlik gerektirebilir. Başlangıç noktası olarak bu önerileri kullanın.

## <a name="check-office-365-secure-score"></a>Güvenli Puan Office 365 Denetleyin

Office 365 Güvenli Puan, kuruluşunuzun güvenliğini normal etkinliklerinize ve güvenlik ayarlarınıza göre analiz eder ve bir puan atar. Geçerli puanınızı not alarak başlayın. Kiracı genelinde bazı ayarların ayarlanması puanınızı artırır. Amaç, maksimum puanı elde etmek değil, ortamınızı korumak ve kullanıcılarınız için üretkenliği olumsuz etkilemeyen fırsatların farkında olmaktır. Bkz. [Microsoft Güvenli Puanı](../defender/microsoft-secure-score.md).

## <a name="tune-threat-management-policies-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında tehdit yönetimi ilkelerini ayarlama

Microsoft 365 Defender portalı, ortamınızı koruyan özellikler içerir. Ayrıca izlemek ve eyleme geçmek için kullanabileceğiniz raporlar ve panolar da içerir. Bazı alanlar varsayılan ilke yapılandırmalarıyla birlikte gelir. Bazı alanlar varsayılan ilkeler veya kurallar içermez. **E-posta & işbirliği** \> **İlkeleri altında** bu ilkeleri ziyaret edin & daha güvenli bir ortam için tehdit yönetimi ayarlarını ayarlamak için tehdit **ilkelerine** kurallar \> uygulayın.

|Alan|Varsayılan ilke?|Öneri|
|---|---|---|
|**Kimlik avına karşı koruma**|Evet|Burada açıklandığı gibi varsayılan kimlik avı önleme ilkesini yapılandırın: [EOP ve Office 365 için Defender kimlik avı koruması ayarlarını yapılandırın](protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365). <p> Daha fazla bilgi: <ul><li>[Microsoft 365'de kimlik avı önleme ilkeleri](set-up-anti-phishing-policies.md)</li><li>[Office 365 için Microsoft Defender'de önerilen kimlik avı önleme ilkesi ayarları](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365)</li><li> [Kimliğe bürünme içgörüleri](impersonation-insight.md)</li><li>[EOP'de sahte zeka içgörüleri](learn-about-spoof-intelligence.md)</li><li>[Kiracı İzin Ver/Engelle Listesini yönet](tenant-allow-block-list.md).</li></ul>|
|**Kötü Amaçlı Yazılımdan Koruma Altyapısı**|Evet|Burada açıklandığı gibi varsayılan kötü amaçlı yazılımdan koruma ilkesini yapılandırın: [EOP'de kötü amaçlı yazılımdan koruma ayarlarını yapılandırın](protect-against-threats.md#part-1---anti-malware-protection-in-eop). <p> Daha fazla bilgi: <ul><li>[Kötü amaçlı yazılımdan koruma](anti-malware-protection.md)</li><li>[Önerilen kötü amaçlı yazılımdan koruma ilkesi ayarları](recommended-settings-for-eop-and-office365.md#eop-anti-malware-policy-settings)</li><li>[Kötü amaçlı yazılımdan koruma ilkelerini yapılandırma](configure-anti-malware-policies.md)</li></ul>|
|**Office 365 için Defender'da Güvenli Ekler**|Hayır|Kasa Ekleri için genel ayarları yapılandırın ve burada açıklandığı gibi bir Kasa Ekler ilkesi oluşturun: [Office 365 için Microsoft Defender Kasa Ekler ayarlarını yapılandırın](protect-against-threats.md#safe-attachments-policies-in-microsoft-defender-for-office-365). <p> Daha fazla bilgi: <ul><li>[Önerilen Kasa Ekler ayarları](recommended-settings-for-eop-and-office365.md#safe-attachments-settings)</li><li>[Office 365 için Microsoft Defender'da Ekleri Kasa](safe-attachments.md)</li><li>[Kasa Ek ilkelerini ayarlama](set-up-safe-attachments-policies.md)</li><li>[SharePoint, OneDrive ve Microsoft Teams için Güvenli Ekler](mdo-for-spo-odb-and-teams.md)</li><li>[Microsoft 365 E5 aboneliğinde Güvenli Belgeler](safe-docs.md)</li></ul>|
|**Office 365 için Microsoft Defender'da bağlantıları Kasa**|Hayır|Kasa Bağlantıları için genel ayarları yapılandırın ve burada açıklandığı gibi bir Kasa Bağlantıları ilkesi oluşturun: [Office 365 için Microsoft Defender'da Kasa Bağlantıları ayarlarını yapılandırın](protect-against-threats.md#safe-links-policies-in-microsoft-defender-for-office-365). <p> Daha fazla bilgi: <ul><li>[Önerilen Kasa Bağlantıları ayarları](recommended-settings-for-eop-and-office365.md#safe-links-settings)</li><li>[Kasa Bağlantıları ilkelerini ayarlama](set-up-safe-links-policies.md)</li><li>[Office 365 için Microsoft Defender'da bağlantıları Kasa](safe-links.md)</li><li>[Office 365 için Microsoft Defender'da Kasa Bağlantıları için genel ayarları yapılandırma](configure-global-settings-for-safe-links.md)</li></ul>|
|**İstenmeyen posta önleme (posta filtreleme)**|Evet|Burada açıklandığı gibi varsayılan istenmeyen posta önleme ilkesini yapılandırın: [EOP'de istenmeyen posta önleme koruma ayarlarını yapılandırma](protect-against-threats.md#part-3---anti-spam-protection-in-eop) <p> Daha fazla bilgi: <ul><li>[Önerilen istenmeyen posta önleme ilkesi ayarları](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)</li><li>[EOP'de istenmeyen posta önleme koruması](anti-spam-protection.md)</li><li>[EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md)</li></ul>|
|***E-posta Kimlik Doğrulaması***|Evet|E-posta kimlik doğrulaması, ileti kaynağı ve gönderen hakkındaki e-posta iletilerine doğrulanabilir bilgiler eklemek için DNS kayıtlarını kullanır. Microsoft 365, varsayılan etki alanı (onmicrosoft.com) için e-posta kimlik doğrulamasını otomatik olarak yapılandırabilir, ancak Microsoft 365 yöneticileri özel etki alanları için e-posta kimlik doğrulamasını da yapılandırabilir. Üç kimlik doğrulama yöntemi kullanılır: <ul><li>Gönderen İlkesi Çerçevesi (veya SPF).</li><ul><li>Kurulum için, kimlik [sahtekarlıklarını önlemeye yardımcı olmak için bkz. Microsoft 365'de SPF'yi ayarlama](set-up-spf-in-office-365-to-help-prevent-spoofing.md).</li></ul> <li>DomainKeys Tanımlanan Posta (DKIM).</li><ul><li>Bkz. [Özel etki alanınızdan gönderilen giden e-postayı doğrulamak için DKIM kullanma](use-dkim-to-validate-outbound-email.md).</li><li>DKIM'i yapılandırdıktan sonra Microsoft 365 Defender portalında etkinleştirin.</li></ul><li>Etki Alanı Tabanlı İleti Kimlik Doğrulaması, Raporlama ve Uyumluluk (DMARC).</li><ul><li>DMARC kurulumu için [Microsoft 365'da e-postayı doğrulamak için DMARC kullanın](use-dmarc-to-validate-email.md).</li></ul></ul>|

> [!NOTE]
> SPF' nin standart olmayan dağıtımları, karma dağıtımları ve sorun giderme için: [Microsoft 365 sahtekarlık önlemek için Sender Policy Framework'ün (SPF) nasıl kullanıldığı](how-office-365-uses-spf-to-prevent-spoofing.md).

## <a name="view-dashboards-and-reports-in-the-microsoft-365-defender-portal"></a>panoları ve raporları Microsoft 365 Defender portalında görüntüleme

Ortamınızın durumu hakkında daha fazla bilgi edinmek için bu raporları ve panoları ziyaret edin. Kuruluşunuz Office 365 hizmetlerini kullandığından bu raporlardaki veriler daha zengin hale gelir. Şimdilik izleyebileceğiniz ve üzerinde işlem yapabileceğiniz şeyler hakkında bilgi sahibi olun.

|Pano|Açıklama|
|---|---|
|E-posta güvenlik raporları|Bu raporlar Exchange Online Protection'de kullanılabilir. Daha fazla bilgi için bkz. [Microsoft 365 Defender portalında e-posta güvenlik raporlarını görüntüleme](view-email-security-reports.md).|
|raporları Office 365 için Defender|Raporlar yalnızca Office 365 için Defender'de kullanılabilir. Daha fazla bilgi için bkz. [Microsoft 365 Defender portalında Office 365 için Defender raporlarını görüntüleme](view-reports-for-mdo.md).|
|Posta akışı raporları ve içgörüleri|Bu raporlar ve içgörüler Exchange yönetim merkezinde (EAC) kullanılabilir. Daha fazla bilgi için bkz [. Posta akışı raporları](/exchange/monitoring/mail-flow-reports/mail-flow-reports) ve [Posta akışı içgörüleri](/exchange/monitoring/mail-flow-insights/mail-flow-insights).|
|[Tehdit Gezgini (veya gerçek zamanlı algılamalar)](threat-explorer.md)|Kiracınıza yönelik bir saldırıyı araştırıyorsanız veya yaşıyorsanız, tehditleri analiz etmek için Gezgin'i (veya gerçek zamanlı algılamaları) kullanın. Explorer (ve gerçek zamanlı algılama raporu) size zaman içindeki saldırı hacmini gösterir ve bu verileri tehdit aileleri, saldırgan altyapısı ve daha fazlası tarafından analiz edebilirsiniz. Ayrıca, Olaylar listesi için herhangi bir şüpheli e-postayı işaretleyebilirsiniz.|

## <a name="configure-additional-exchange-online-tenant-wide-settings"></a>Kiracı genelinde ek Exchange Online ayarlarını yapılandırma

Aşağıda önerilen ek ayarlardan birkaçı yer alır.

|Alan|Öneri|
|---|---|
|**Posta akışı kuralları** (taşıma kuralları olarak da bilinir)|Yürütülebilir dosya türlerini engelleyerek ve makro içeren dosya türlerini Office fidye yazılımlarına karşı korunmaya yardımcı olmak için bir posta akışı kuralı ekleyin. Daha fazla bilgi için bkz. [Exchange Online ileti eklerini incelemek için posta akışı kurallarını kullanma](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments). <p> Şu ek konulara bakın: <ul><li>[Fidye yazılımlarından koruma](../../admin/security-and-compliance/secure-your-business-data.md)</li><li>[Microsoft 365'de Kötü Amaçlı Yazılım ve Fidye Yazılımı Koruması](/compliance/assurance/assurance-malware-and-ransomware-protection)</li><li>[Office 365'da fidye yazılımı saldırısından kurtarma](recover-from-ransomware.md)</li></ul> <p> E-postanın dış etki alanlarına otomatik olarak iletilmesini önlemek için bir posta akışı kuralı oluşturun. Daha fazla bilgi için bkz. [Güvenli Puan ile İstemci Dış İletme Kurallarını Azaltma](/archive/blogs/office365security/mitigating-client-external-forwarding-rules-with-secure-score). <p> Daha fazla bilgi: [Exchange Online'de posta akışı kuralları (aktarım kuralları)](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)|
|**Modern kimlik doğrulaması**|Modern kimlik doğrulaması, çok faktörlü kimlik doğrulaması (MFA) kullanmak için bir önkoşuldur. E-posta da dahil olmak üzere bulut kaynaklarına erişimin güvenliğini sağlamak için MFA önerilir. <p> Şu konulara bakın: <ul><li>[Exchange Online'de modern kimlik doğrulamasını etkinleştirme veya devre dışı bırakma](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online)</li><li>[Skype Kurumsal Online: Kiracınızı modern kimlik doğrulaması için etkinleştirme](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)</li></ul> <p> Modern kimlik doğrulaması Office 2016 istemcileri, SharePoint Online ve OneDrive İş için varsayılan olarak etkindir. <p> Daha fazla bilgi: [modern kimlik doğrulaması Office 2013 ve Office 2016 istemci uygulamalarında nasıl çalışır](../../enterprise/modern-auth-for-office-2013-and-2016.md)?|

## <a name="configure-tenant-wide-sharing-policies-in-sharepoint-admin-center"></a>SharePoint yönetim merkezinde kiracı genelinde paylaşım ilkelerini yapılandırma

Temel korumadan başlayarak SharePoint ekip sitelerini artan koruma düzeylerinde yapılandırmaya yönelik Microsoft önerileri. Daha fazla bilgi için bkz. [SharePoint sitelerin ve dosyaların güvenliğini sağlamaya yönelik ilke önerileri](sharepoint-file-access-policies.md).

Temel düzeyde yapılandırılmış SharePoint ekip siteleri, anonim erişim bağlantılarını kullanarak dış kullanıcılarla dosya paylaşımına izin verir. Bu yaklaşım, dosyaları e-postayla göndermek yerine önerilir.

Temel koruma hedeflerini desteklemek için kiracı genelinde paylaşım ilkelerini burada önerilen şekilde yapılandırın. Tek tek sitelerin paylaşım ayarları bu kiracı genelindeki ilkeden daha kısıtlayıcı olabilir, ancak daha izin vermez.

|Alan|Varsayılan ilkeyi içerir|Öneri|
|---|---|---|
|**Paylaşım** (çevrimiçi ve OneDrive İş SharePoint)|Evet|Dış paylaşım varsayılan olarak etkindir. Bu ayarlar önerilir: <ul><li>Kimliği doğrulanmış dış kullanıcılara paylaşıma izin ver ve anonim erişim bağlantılarını kullan (varsayılan ayar).</li><li>Anonim erişim bağlantılarının süresi bu kadar gün içinde dolar. İsterseniz 30 gün gibi bir sayı girin.</li><li>Varsayılan bağlantı türü — İç 'i seçin (yalnızca kuruluştaki kişiler). Anonim bağlantıları kullanarak paylaşmak isteyen kullanıcıların paylaşım menüsünden bu seçeneği belirlemesi gerekir.</li></ul> <p> Daha fazla bilgi: [Dış paylaşıma genel bakış](/sharepoint/external-sharing-overview)|

SharePoint yönetim merkezi ve OneDrive İş yönetim merkezi aynı ayarları içerir. Her iki yönetim merkezindeki ayarlar her ikisi için de geçerlidir.

## <a name="configure-settings-in-azure-active-directory"></a>Azure Active Directory ayarları yapılandırma

Daha güvenli ortamlar için kiracı genelinde kurulumu tamamlamak için Azure Active Directory bu iki alanı ziyaret edin.

### <a name="configure-named-locations-under-conditional-access"></a>Adlandırılmış konumları yapılandırma (koşullu erişim altında)

Kuruluşunuz güvenli ağ erişimine sahip ofisler içeriyorsa, güvenilen IP adresi aralıklarını adlandırılmış konumlar olarak Azure Active Directory ekleyin. Bu özellik, oturum açma riski olayları için bildirilen hatalı pozitif sonuçların sayısını azaltmaya yardımcı olur.

Bkz. [Azure Active Directory'de adlandırılmış konumlar](/azure/active-directory/conditional-access/location-condition)

### <a name="block-apps-that-dont-support-modern-authentication"></a>Modern kimlik doğrulamayı desteklemeyen uygulamaları engelleme

Çok faktörlü kimlik doğrulaması, modern kimlik doğrulamasını destekleyen uygulamalar gerektirir. Modern kimlik doğrulamayı desteklemeyen uygulamalar koşullu erişim kuralları kullanılarak engellenemez.

Güvenli ortamlar için modern kimlik doğrulamasını desteklemeyen uygulamalar için kimlik doğrulamasını devre dışı bırakmayı unutmayın. Bunu Azure Active Directory'da yakında sunulacak bir denetimle yapabilirsiniz.

Bu arada, SharePoint Online ve OneDrive İş için bunu gerçekleştirmek için aşağıdaki yöntemlerden birini kullanın:

- PowerShell kullanma, bkz [. Modern kimlik doğrulaması kullanmayan uygulamaları engelleme](/mem/intune/protect/app-modern-authentication-block).
- Bunu "cihaz erişimi" sayfasındaki <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint yönetim merkezinde</a> yapılandırın— "Modern kimlik doğrulaması kullanmayan uygulamalardan erişimi denetleme." Engelle'yi seçin.

## <a name="get-started-with-defender-for-cloud-apps-or-office-365-cloud-app-security"></a>Bulut için Defender Uygulamaları veya Office 365 Bulut Uygulamaları Güvenliği ile Kullanmaya başlayın

Riski değerlendirmek, şüpheli etkinlikle ilgili uyarı vermek ve otomatik olarak eyleme geçmek için Office 365 Bulut Uygulamaları Güvenliği kullanın. Office 365 E5 plan gerektirir.

Microsoft Defender for Cloud Apps kullanarak erişim verildikten sonra bile daha derin görünürlük, kapsamlı denetimler ve Office 365 dahil olmak üzere tüm bulut uygulamalarınız için geliştirilmiş koruma elde edebilirsiniz.

Bu çözüm EMS E5 planını önerdiğinden, ortamınızdaki diğer SaaS uygulamalarıyla kullanabilmeniz için Bulut için Defender Uygulamaları ile başlamanızı öneririz. Varsayılan ilkeler ve ayarlarla başlayın.

Daha fazla bilgi:

- [Bulut için Defender Uygulamaları Dağıtma](/cloud-app-security/getting-started-with-cloud-app-security)
- [Microsoft Defender for Cloud Apps hakkında daha fazla bilgi](https://www.microsoft.com/cloud-platform/cloud-app-security)
- [Bulut için Defender Uygulamaları nedir?](/cloud-app-security/what-is-cloud-app-security)

:::image type="content" source="../../media/1fb2aa65-54b8-4746-9f5e-c187d339e9f5.png" alt-text="Bulut için Defender Uygulamaları panosu" lightbox="../../media/1fb2aa65-54b8-4746-9f5e-c187d339e9f5.png":::

## <a name="additional-resources"></a>Ek kaynaklar

Bu makaleler ve kılavuzlar, Microsoft 365 ortamınızın güvenliğini sağlamaya yönelik ek açıklayıcı bilgiler sağlar:

- [Siyasi kampanyalar, kar amacı gütmeyen kuruluşlar ve diğer çevik kuruluşlar için Microsoft güvenlik kılavuzu](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) (bu öneriyi her ortamda, özellikle de yalnızca bulut ortamlarında kullanabilirsiniz)

- [Kimlikler ve cihazlar için önerilen güvenlik ilkeleri ve yapılandırmaları](microsoft-365-policies-configurations.md) (bu öneriler AD FS ortamları için yardım içerir)
