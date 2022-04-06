---
title: Daha fazla güvenlik için Microsoft 365 kiracınızı yapılandırma
f1.keywords:
- NOCSH
ms.author: bcarter
author: BrendaCarter
manager: laurawi
ms.date: 10/11/2018
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
description: Bu konu başlığı, kiracı ortamının güvenliğini etkileyen kiracı genelindeki ayarlar için önerilen Microsoft 365 gösterir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 96f31d0fb9eb3ef9d6eaec396fdac8fe96b96c3d
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476367"
---
# <a name="configure-your-microsoft-365-tenant-for-increased-security"></a>Daha fazla güvenlik için Microsoft 365 kiracınızı yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Bu konu başlığı, kiracı ortamının güvenliğini etkileyen kiracı genelindeki ayarlar için önerilen Microsoft 365 gösterir. Güvenlik ihtiyaçları daha fazla veya daha az güvenlik gerekli olabilir. Bu önerileri başlangıç noktası olarak kullanın.

## <a name="check-office-365-secure-score"></a>Güvenli Office 365'i denetleme

Office 365 Puanı, normal etkinliklerinize ve güvenlik ayarlarınıza göre kuruluş güvenliklerini analiz eder ve bir puan atar. Geçerli puanınızı not alarak başlama. Kiracı genelinde bazı ayarların ayarlanması, puanınızı artıracaktır. Amaç maksimum puanı elde etmek değil, kullanıcılarınız için üretkenliği olumsuz etkilemeyen ortamınızı koruma fırsatlarını da takip etmektir. [Bkz. Microsoft Güvenli Puan](../defender/microsoft-secure-score.md).

## <a name="tune-threat-management-policies-in-the-microsoft-365-defender-portal"></a>Güvenlik portalında tehdit yönetimi ilkelerini Microsoft 365 Defender ayarlama

Bu Microsoft 365 Defender, ortamınızı koruyan özellikler içerir. Ayrıca, izlemek ve önlem almak için kullanabileceğiniz raporları ve panoları da içerir. Bazı alanlar varsayılan ilke yapılandırmaları içerir. Bazı alanlar varsayılan ilkeleri veya kuralları içermemektedir. E-posta ve işbirliği **& bu ilkeleri ziyaret** \> **& kuralları** \> Tehdit ilkeleri **,** daha güvenli bir ortam için tehdit yönetimi ayarlarını ayarlamak için tehdit ilkelerini kullanır.

|Alan|Varsayılan ilke?|Öneri|
|---|---|---|
|**Kimlik avı önleme**|Evet|Varsayılan kimlik avı koruma ilkesi burada açıklandığı gibi yapılandırma: [EOP ve Kimlik](protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365) avından korunma ayarlarını Office 365 için Defender. <p> Daha fazla bilgi: <ul><li>[E-postada kimlik avı önleme Microsoft 365](set-up-anti-phishing-policies.md)</li><li>[E-postada önerilen kimlik avı önleme ilkesi Office 365 için Microsoft Defender](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365)</li><li> [Kimliğe bürünme içgörü](impersonation-insight.md)</li><li>[EOP'de akıllı Spoof Intelligence içgörü](learn-about-spoof-intelligence.md)</li><li>[Kiracı İzin Ver/Engelleme Listesi'ne tıklayın](tenant-allow-block-list.md).</li></ul>|
|**Kötü Amaçlı Yazılımdan Koruma Altyapısı**|Evet|Varsayılan kötü amaçlı yazılımdan koruma ilkesi burada açıklandığı gibi yapılandırma: [EOP'de kötü amaçlı yazılımdan koruma ayarlarını yapılandırma](protect-against-threats.md#part-1---anti-malware-protection-in-eop). <p> Daha fazla bilgi: <ul><li>[Kötü amaçlı yazılımdan koruma](anti-malware-protection.md)</li><li>[Kötü amaçlı yazılımdan koruma ilkesi ayarları](recommended-settings-for-eop-and-office365.md#eop-anti-malware-policy-settings)</li><li>[Kötü amaçlı yazılımdan koruma ilkelerini yapılandırma](configure-anti-malware-policies.md)</li></ul>|
|**Kasa'de Ekleri Office 365 için Defender**|Hayır|Ekler için genel ayarları Kasa ve burada açıklandığı gibi Kasa Ekleri ilkesi oluşturun: Kasa'de [Ekleri Yapılandırma Office 365 için Microsoft Defender](protect-against-threats.md#safe-attachments-policies-in-microsoft-defender-for-office-365). <p> Daha fazla bilgi: <ul><li>[Ekleri Kasa ayarları için önerilenler](recommended-settings-for-eop-and-office365.md#safe-attachments-settings)</li><li>[Kasa'de Ekleri Office 365 için Microsoft Defender](safe-attachments.md)</li><li>[Ekleri Kasa ilkelerini ayarlama](set-up-safe-attachments-policies.md)</li><li>[Kasa, Bağlantı SharePoint OneDrive için Ekleri Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Microsoft 365 E5 aboneliğinde Güvenli Belgeler](safe-docs.md)</li></ul>|
|**Kasa'daki Bağlantıları Office 365 için Microsoft Defender**|Hayır|Bağlantılar'ın genel ayarlarını Kasa ve burada açıklandığı gibi Kasa Bağlantıları ilkesi oluşturun: bağlantıların Kasa ayarlarını [Office 365 için Microsoft Defender](protect-against-threats.md#safe-links-policies-in-microsoft-defender-for-office-365). <p> Daha fazla bilgi: <ul><li>[Önerilen Kasa Bağlantıları ayarları](recommended-settings-for-eop-and-office365.md#safe-links-settings)</li><li>[Bağlantılar Kasa ayarlama](set-up-safe-links-policies.md)</li><li>[Kasa'daki Bağlantıları Office 365 için Microsoft Defender](safe-links.md)</li><li>[Web'de Bağlantıları Kasa genel ayarlarını Office 365 için Microsoft Defender](configure-global-settings-for-safe-links.md)</li></ul>|
|**İstenmeyen posta önleme (posta filtreleme)**|Evet|Varsayılan istenmeyen posta önleme ilkesi burada açıklandığı gibi yapılandırma: [EOP'de istenmeyen posta önleme ayarlarını yapılandırma](protect-against-threats.md#part-3---anti-spam-protection-in-eop) <p> Daha fazla bilgi: <ul><li>[İstenmeyen posta önleme ilkesi ayarları](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)</li><li>[EOP'de istenmeyen posta önleme koruması](anti-spam-protection.md)</li><li>[EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md)</li></ul>|
|***E-posta Kimlik Doğrulaması***|Evet|E-posta kimlik doğrulaması, e-posta iletilerine ileti kaynağı ve gönderen hakkında doğrulanabilir bilgiler eklemek için DNS kayıtlarını kullanır. Microsoft 365 varsayılan etki alanı için e-posta kimlik doğrulamasını otomatik olarak yapılandırıyor (onmicrosoft.com), ancak Microsoft 365 yöneticileri de özel etki alanları için e-posta kimlik doğrulamasını yapılandırabilirsiniz. Üç kimlik doğrulama yöntemi kullanılır: <ul><li>Sender Policy Framework (veya SPF).</li><ul><li>Kurulum için bkz[. SPF'yi Microsoft 365 SPF'yi ayarlama.](set-up-spf-in-office-365-to-help-prevent-spoofing.md)</li></ul> <li>DomainKeys Identified Mail (DKIM).</li><ul><li>Bkz [. Özel etki alanınıza gönderilen giden e-postayı doğrulamak için DKIM kullanma](use-dkim-to-validate-outbound-email.md).</li><li>DKIM'yi yapılandırdıktan sonra, dkIM'yi Microsoft 365 Defender etkinleştirin.</li></ul><li>Etki Alanı Tabanlı İleti Kimlik Doğrulaması, Raporlama ve Uyumluluk (DMARC).</li><ul><li>DMARC kurulumu için [DMARC kullanarak e-postayı doğrula ve Microsoft 365](use-dmarc-to-validate-email.md).</li></ul></ul>|

> [!NOTE]
> SPF'nin standart dışı dağıtımları, karma dağıtımları ve sorun giderme için: Microsoft 365, birlikte kullanma işlemi[, spoofing'i önlemek için Sender Policy Framework'i (SPF) kullanır](how-office-365-uses-spf-to-prevent-spoofing.md).

## <a name="view-dashboards-and-reports-in-the-microsoft-365-defender-portal"></a>Panoları ve raporları portalda Microsoft 365 Defender görüntüleme

Ortamının durumu hakkında daha fazla bilgi edinmek için bu raporları ve panoları ziyaret edin. Bu raporlarda yer alan veriler, organizasyonunız sizin için önemli hizmetleri kullandığı Office 365 hale gelecektir. Şimdilik hangi monitör ve işlem hakkında bilgi sahibi olasiniz.

|Pano|Açıklama|
|---|---|
|E-posta güvenlik raporları|Bu raporlar tüm Exchange Online Protection. Daha fazla bilgi için bkz[. Microsoft 365 Defender portalında e-posta Microsoft 365 Defender görüntüleme](view-email-security-reports.md).|
|Office 365 için Defender raporları|Raporlar yalnızca tüm Office 365 için Defender. Daha fazla bilgi için [bkz. Office 365 için Defender portalında raporları görüntüleme Microsoft 365 Defender.](view-reports-for-mdo.md)|
|Posta akışı raporları ve içgörüleri|Bu raporlar ve içgörüler, yönetim Exchange (EAC) içinde yer almaktadır. Daha fazla bilgi için bkz [. Posta akışı raporları](/exchange/monitoring/mail-flow-reports/mail-flow-reports) ve [Posta akışı içgörüleri](/exchange/monitoring/mail-flow-insights/mail-flow-insights).|
|[Tehdit Gezgini (veya gerçek zamanlı algılamalar)](threat-explorer.md)|Kiracınızı araştırıyorsanız veya kiracınıza yönelik bir saldırıyla karşılaşıyorsanız tehditleri çözümlemek için Explorer'ı (veya gerçek zamanlı algılamaları) kullanın. Gezgin (ve gerçek zamanlı algılamalar raporu), size zaman içinde saldırı hacmini gösterir ve tehdit aileleri, altyapı ve daha fazlasını kullanarak bu verileri analiz edersiniz. Ayrıca, Olaylar listesi için tüm şüpheli e-postaları işaretebilirsiniz.|

## <a name="configure-additional-exchange-online-tenant-wide-settings"></a>Kiracı genelindeki Exchange Online ayarları yapılandırma

Önerilen birkaç ek ayara buradan bakabilirsiniz.

|Alan|Öneri|
|---|---|
|**Posta akış kuralları** (aktarım kuralları olarak da bilinir)|Yürütülebilir dosya türlerini ve makro içeren dosya türlerini engelleyerek fidye yazılımlarına karşı Office için posta akış kuralı ekleyin. Daha fazla bilgi için bkz[. Kendi dosyalarında ileti eklerini incelemek için posta Exchange Online](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments). <p> Aşağıdaki ek konulara bakın: <ul><li>[Fidye yazılımlarına karşı koruma](../../admin/security-and-compliance/secure-your-business-data.md#5-protect-against-ransomware)</li><li>[Yazılım ve Yazılıma Karşı Kötü Amaçlı Yazılım ve Fidye Yazılımına karşı Microsoft 365](/compliance/assurance/assurance-malware-and-ransomware-protection)</li><li>[bir fidye yazılımı saldırılarından kurtar'Office 365](recover-from-ransomware.md)</li></ul> <p> E-postanın dış etki alanlarına otomatik olarak iletimsini önlemek için bir posta akışı kuralı oluşturun. Daha fazla bilgi için bkz [. Güvenli Puanla İstemci Dış Yönlendirme Kurallarını Azaltma](/archive/blogs/office365security/mitigating-client-external-forwarding-rules-with-secure-score). <p> Daha fazla bilgi: [Posta akış kuralları (aktarım kuralları) Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)|
|**Modern kimlik doğrulama**|Modern kimlik doğrulaması, multi-factor authentication (MFA) kullanmanın önkoşullarıdır. E-posta dahil bulut kaynaklarına erişimin güvenliğini sağlamak için MFA'nın kullanılması önerilir. <p> Şu konulara bakın: <ul><li>[2010'da modern kimlik doğrulamayı etkinleştirme veya devre dışı Exchange Online](/Exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online)</li><li>[Skype Kurumsal Online: Kiracınızı modern kimlik doğrulaması için etkinleştirme](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)</li></ul> <p> Modern kimlik doğrulama Office 2016 istemcileri, SharePoint Online ve OneDrive İş. <p> Daha fazla bilgi: [modern kimlik doğrulama Office 2013 ve Office 2016 istemci uygulamaları için nasıl çalışır?](../../enterprise/modern-auth-for-office-2013-and-2016.md)|

## <a name="configure-tenant-wide-sharing-policies-in-sharepoint-admin-center"></a>Yönetim merkezinde kiracı genelinde paylaşım SharePoint yapılandırma

Taban çizgisi korumasıyla başlayarak SharePoint sitelerini daha yüksek koruma düzeylerinde yapılandırmaya yönelik Microsoft önerileri. Daha fazla bilgi için bkz[. Site ve dosyaların güvenliğini SharePoint ilke önerileri](sharepoint-file-access-policies.md).

SharePoint düzeyinde yapılandırılan ekip siteleri, anonim erişim bağlantıları kullanarak dış kullanıcılarla dosya paylaşımına olanak sağlar. Dosyaları e-postayla göndermek yerine bu yaklaşımın kullanılması önerilir.

Taban çizgisi korumasının hedeflerini desteklemek için, burada önerilen şekilde kiracı genelindeki paylaşım ilkelerini yapılandırın. Tek tek sitelerin paylaşım ayarları bu kiracı genelindeki ilkeye göre daha kısıtlayıcı olabilir, ancak izinli olmaz.

|Alan|Varsayılan ilke içerir|Öneri|
|---|---|---|
|**Paylaşım** (SharePoint Online ve OneDrive İş)|Evet|Dış paylaşım varsayılan olarak etkinleştirilmiştir. Bu ayarların kullanılması önerilir: <ul><li>Kimliği doğrulanmış dış kullanıcılarla paylaşıma ve anonim erişim bağlantıları kullanmaya izin ver (varsayılan ayar).</li><li>Anonim erişim bağlantılarının süresi bu kadar gün içinde dolar. İsterseniz, 30 gün gibi bir sayı girin.</li><li>Varsayılan bağlantı türü: İç 'i (yalnızca kuruluşta yer alan kişiler) seçin. Anonim bağlantıları kullanarak paylaşmak isteyen kullanıcıların paylaşım menüsünden bu seçeneği tercihleri gerekir.</li></ul> <p> Daha fazla bilgi: [Dış paylaşıma genel bakış](/sharepoint/external-sharing-overview)|

SharePoint merkezi ve OneDrive İş merkezi aynı ayarları içerir. Yönetim merkezinde her iki ayar da geçerlidir.

## <a name="configure-settings-in-azure-active-directory"></a>E-postada ayarları Azure Active Directory

Daha güvenli ortamlar için kiracı genelinde kurulumu tamamlamak Azure Active Directory bu iki alanı ziyaret edin.

### <a name="configure-named-locations-under-conditional-access"></a>Adlandırılmış konumları yapılandırma (koşullu erişim altında)

Organizasyonda güvenli ağ erişimi olan ofisler varsa, güvenilir IP adresi aralıklarını adlandırılmış Azure Active Directory olarak ekleyin. Bu özellik, oturum açma riski olayları için bildirilen hatalı pozitiflerin sayısını azaltmaya yardımcı olur.

Bkz. [Azure Active Directory'de adlandırılmış konumlar](/azure/active-directory/active-directory-named-locations)

### <a name="block-apps-that-dont-support-modern-authentication"></a>Modern kimlik doğrulamasını desteklemeen uygulamaları engelleme

Çok faktörlü kimlik doğrulaması için modern kimlik doğrulamayı destekleyen uygulamalar gerekir. Modern kimlik doğrulamasını desteklemez uygulamalar, koşullu erişim kuralları kullanılarak engel olamaz.

Güvenli ortamlar için, modern kimlik doğrulamasını desteklemeen uygulamalarda kimlik doğrulamayı devre dışı bırakarak emin olun. Bunu, yakın zamanda Azure Active Directory bir denetimle aynı anda ve bu denetimle de yapabiliriz.

Bu arada, bu görevi SharePoint Online ve iş başka bir OneDrive İş:

- PowerShell kullanın, bkz [. Modern kimlik doğrulaması kullanmayan uygulamaları engelleme](/mem/intune/protect/app-modern-authentication-block).
- Bunu" SharePoint "<a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank"></a>Cihaz erişimi" sayfasındaki "Modern kimlik doğrulama kullanmayan uygulamalardan erişimi denetleme" altında bulabilirsiniz. Engelle'yi seçin.

## <a name="get-started-with-defender-for-cloud-apps-or-office-365-cloud-app-security"></a>Kullanmaya başlayın Uygulamaları Bulut için Defender ile Office 365 Bulut Uygulamaları Güvenliği

Bu Office 365 Bulut Uygulamaları Güvenliği riski değerlendirmek, şüpheli etkinliklere karşı uyarı yapmak ve otomatik olarak işlem yapmak için kullanın. Plan Office 365 E5 gerekir.

Erişim verildikten Microsoft Defender for Cloud Apps, kapsamlı denetimler ve gelişmiş koruma da dahil olmak üzere tüm bulut uygulamalarınız için daha derin bir görünürlük elde etmek için Office 365.

Bu çözüm EMS E5 planını öneren bir uygulama olduğundan, Bulut için Defender Uygulamaları ile başlamanızı ve böylelikle ortamınızı diğer SaaS uygulamalarıyla kullanabileceğinizi öneririz. Varsayılan ilkeler ve ayarlarla çalışmaya başlama.

Daha fazla bilgi:

- [Uygulama Bulut için Defender dağıtma](/cloud-app-security/getting-started-with-cloud-app-security)
- [Daha fazla bilgi Microsoft Defender for Cloud Apps](https://www.microsoft.com/cloud-platform/cloud-app-security)
- [Uygulamalar Bulut için Defender nedir?](/cloud-app-security/what-is-cloud-app-security)

:::image type="content" source="../../media/1fb2aa65-54b8-4746-9f5e-c187d339e9f5.png" alt-text="Bulut için Defender Apps panosu" lightbox="../../media/1fb2aa65-54b8-4746-9f5e-c187d339e9f5.png":::

## <a name="additional-resources"></a>Ek kaynaklar

Bu makaleler ve kılavuzlar, güvenlik güvenlik altına almak için ek Microsoft 365 sağlar:

- [Kampanyalar, kar](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) amacı gütmeyen kuruluşlar ve diğer çevik kuruluşlar için Microsoft güvenlik kılavuzu (bu önerileri özellikle yalnızca bulut ortamlarında herhangi bir ortamda kullanabilirsiniz)

- [Kimlikler ve cihazlar için önerilen güvenlik ilkeleri ve yapılandırmalar](microsoft-365-policies-configurations.md) (bu öneriler AD FS ortamları için yardım içerir)
