---
title: Microsoft 365 yol haritası - En önemli öncelikler
f1.keywords:
- NOCSH
ms.author: bcarter
author: BrendaCarter
manager: laurawi
ms.date: 08/20/2021
audience: Admin
ms.topic: conceptual
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
ms.assetid: 28c86a1c-e4dd-4aad-a2a6-c768a21cb352
description: En çok, Microsoft'un siber güvenlik ekibinin güvenlik özelliklerini uygulama ve güvenlik ortamınızı korumaya Microsoft 365 öneriler.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9edfda495e1359ac5af74f86f65d33661a2f7059
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "62999130"
---
# <a name="security-roadmap---top-priorities-for-the-first-30-days-90-days-and-beyond"></a>Güvenlik yol haritası - İlk 30 gün, son 90 gün ve daha sonra için en önemli öncelikler

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Bu makale, Microsoft'un siber güvenlik ekibinin güvenlik özelliklerini Microsoft 365 içerir. Bu makale Microsoft Ignite oturumundan uyarlanmıştır: Microsoft 365 güven güveni uzmanı gibi[: İlk 30 gün, 90](https://www.youtube.com/watch?v=luignzNyR-o) gün ve daha üstü için en yüksek öncelik. Bu oturum Mark Simos ve Matt Kemelhar tarafından ve Cybersecurity Architects Enterprise geliştirildi ve sunuldu.

Bu makalede:

- [Yol Haritası sonuçları](security-roadmap.md#Roadmap)
- [30 gün — güçlü hızlı kazançlar](security-roadmap.md#Thirdaydays)
- [90 gün — gelişmiş korumalar](security-roadmap.md#Ninetydays)
- [Beyond](security-roadmap.md#Beyond)

## <a name="roadmap-outcomes"></a>Yol Haritası sonuçları
<a name="Roadmap"> </a>

Bu yol haritası önerileri, aşağıdaki hedefler ile üç aşama arasında mantıksal bir düzende aşamalıdır.

****

|Zaman çerçevesi|Sonuçlar|
|---|---|
|30 gün|Hızlı yapılandırma: <ul><li>Temel yönetici korumaları.</li><li>Günlüğe kaydetme ve çözümleme.</li><li>Temel kimlik korumaları.</li></ul> <p> Kiracı yapılandırması. <p> Paydaşları hazırlama.|
|90 gün|Gelişmiş korumalar: <ul><li>Yönetici hesapları.</li><li>Veriler ve kullanıcı hesapları.</li></ul> <p> Uyumluluk, tehdit ve kullanıcı  ihtiyaçlarının görünürlüğü. <p> Varsayılan ilkeleri ve korumaları uyarlama ve uygulama.|
|Beyond|Önemli ilkeleri ve denetimleri ayarlayın ve geliştirin. <p> Korumaları şirket içi bağımlılıklara kadar genişletme. <p> İş ve güvenlik süreçleriyle tümleştirin (yasal, insider tehdit, vb.).|
|

## <a name="30-days--powerful-quick-wins"></a>30 gün — güçlü hızlı kazançlar
<a name="Thirdaydays"> </a>

Bu görevler hızla yerine gelir ve kullanıcılar üzerinde düşük bir etki sağlar.

****

|Alan|Görevler|
|---|---|
|Güvenlik yönetimi|<ul><li>Güvenli Puanı kontrol edin ve geçerli puanınızı () not edin<https://security.microsoft.com/securescore>.</li><li>Denetim günlüğünü bu kayıt için Office 365. Bkz[. Denetim günlüğünde arama.](../../compliance/search-the-audit-log-in-security-and-compliance.md)</li><li>[Güvenliği Microsoft 365 için yapılandırma](tenant-wide-setup-for-increased-security.md).</li><li>Portalda ve Bulut Uygulamaları için Defender'da Microsoft 365 Defender panoları ve raporları düzenli olarak gözden geçirebilirsiniz.</li></ul>|
|Tehdit koruması|[Bağlan Microsoft 365 anormal davranışlar için varsayılan](/cloud-app-security/connect-office-365-to-microsoft-cloud-app-security) tehdit algılama ilkelerini kullanmaya başlamak üzere Bulut Uygulamaları için Microsoft Defender'a yardımcı olun. Anormal algılama için temel oluşturmak yedi gün sürer. <p>  Yönetici hesapları için koruma uygulama:<ul><li>Yönetici etkinliği için ayrılmış yönetici hesapları kullanın.</li><li>Yönetici hesapları için çok faktörlü kimlik doğrulamasını (MFA) zorunlu kılın.</li><li>Yönetici etkinliği [için yüksek Windows bir cihaz](/windows-hardware/design/device-experiences/oem-highly-secure) kullanın.</li></ul>|
|Kimlik ve erişim yönetimi|<ul><li>[Kimlik Azure Active Directory'yi etkinleştirin](/azure/active-directory/active-directory-identityprotection-enable).</li><li>Federasyon kimlik ortamları için, hesap güvenliğini zorunlu kılın (parola uzunluğu, yaş, karmaşıklık, vb.).</li></ul>|
|Bilgi koruması|Örnek bilgi koruma önerilerini gözden geçirebilirsiniz. Bilgi koruması, kurum genelinde koordinasyon gerektirir. Bu kaynaklarla çalışmaya başlayın:<ul><li>[Office 365 GDPR için Bilgi Koruması](/compliance/regulatory/gdpr)</li><li>[Verileri Teams koruma katmanıyla yapılandırabilirsiniz](../../solutions/configure-teams-three-tiers-protection.md) (paylaşım, sınıflandırma, veri kaybını önleme ve Azure Information Protection içerir)</li></ul>|
|

## <a name="90-days--enhanced-protections"></a>90 gün — gelişmiş korumalar
<a name="Ninetydays"> </a>

Bu görevlerin plan yapmak ve uygulamak için biraz daha zaman gerekir, ancak güvenlik nedenlerinizi büyük ölçüde artırabilirsiniz.

****

|Alan|Görev|
|---|---|
|Güvenlik yönetimi|<ul><li>Ortamınız için önerilen eylemler için Güvenli Puan'a () göz atabilirsiniz<https://security.microsoft.com/securescore>.</li><li>Bulut portalı, Bulut Uygulamaları için Defender ve SIEM Microsoft 365 Defender panoları ve raporları düzenli olarak gözden geçirmeye devam edin.</li><li>Yazılım güncelleştirmelerini bakın ve gerçekleştirin.</li><li>Saldırı benzetimi eğitimini [(Office 365](attack-simulation-training.md) Threat Intelligence ile birlikte) kullanarak güvenli kimlik avı, parola-bilgi ve güvenlikli parola saldırılarına yönelik [saldırı benzetimleri yürütebilirsiniz](office-365-ti.md).</li><li>Bulut Uygulamaları için Defender'da (Araştır sekmesinde) yerleşik raporları gözden geçirerek paylaşım riski için arama yapın.</li><li>Uyumluluk [Yöneticisi'ni](../../compliance/compliance-manager.md) kontrol edin ve organizasyonunıza uygun düzenlemelerin (GDPR, NIST 800-171 gibi) durumunu gözden geçirin.</li></ul>|
|Tehdit koruması|Yönetici hesapları için gelişmiş korumalar uygulama: <ul><li>Yönetici [etkinliği için Ayrıcalıklı Erişim İş istasyonlarını](/security/compass/privileged-access-devices) (PAWs) yapılandırarak.</li><li>[Azure AD etki Privileged Identity Management](/azure/active-directory/active-directory-privileged-identity-management-configure).</li><li>Office 365'tan, Bulut Uygulamaları için Defender'dan ve AD FS gibi diğer hizmetlerden günlük verilerini toplamak için bir güvenlik bilgileri ve olay yönetimi (SIEM) aracı yapılandırabilirsiniz. Denetim günlüğü, yalnızca 90 günlük verileri depolar. Bu verileri SIEM aracında yakalama, daha uzun süre depolayarak verilerinizi depolamaya olanak sağlar.</li></ul>|
|Kimlik ve erişim yönetimi|<ul><li>Tüm kullanıcılar için MFA'yi etkinleştirin ve zorunlu kılın.</li><li>Koşullu erişim ve [ilgili ilkeler kümesi uygulama](microsoft-365-policies-configurations.md).</li></ul>|
|Bilgi koruması| Bilgi koruma ilkelerini uyarlama ve uygulama. Bu kaynaklara bazı örnekler verilmiştir: <ul><li>[Office 365 GDPR için Bilgi Koruması](/compliance/regulatory/gdpr)</li><li>[Dört Teams koruma katmanıyla yapılandırma](../../solutions/configure-teams-three-tiers-protection.md)</li></ul> <p> Bulutta depolanan veriler için (Bulut Uygulamaları için Defender Microsoft 365 yerine) Microsoft 365 önleme ilkelerini ve izleme araçlarını kullanın. <p> Gelişmiş uyarı özellikleri (veri kaybı Microsoft 365 dışında) özelliğiyle Bulut Uygulamaları için Defender'ı kullanın.|
|

## <a name="beyond"></a>Beyond
<a name="Beyond"> </a>

Bunlar, önceki çalışmalara yönelik önemli güvenlik önlemleridir.

****

|Alan|Görev|
|---|---|
|Güvenlik yönetimi|<ul><li>Güvenli Puan() kullanarak sonraki eylemleri planlamaya devam.<https://security.microsoft.com/securescore></li><li>Bulut portalı, Bulut Uygulamaları için Defender ve SIEM Microsoft 365 Defender panoları ve raporları düzenli olarak gözden geçirmeye devam edin.</li><li>Yazılım güncelleştirmelerini uygulamaya ve uygulamaya devam edin.</li><li>eKbulma'ı yasal ve tehdit yanıt süreçlerinize tümleştirin.</li></ul>|
|Tehdit koruması|<ul><li>Şirket [içi kimlik bileşenleri](/windows-server/identity/securing-privileged-access/securing-privileged-access) (AD, AD FS) için Güvenli Ayrıcalıklı Erişim (SPA) uygulama.</li><li>Insider tehditlerini izlemek için Bulut Uygulamaları için Defender'ı kullanın.</li><li>Bulut uygulamaları için Defender'ı kullanarak GÖLGE IT SaaS kullanımını keşfedin.</li></ul>|
|Kimlik ve erişim yönetimi|<ul><li>İlkeleri ve işlem işlemlerini geliştirin.</li><li>Insider tehditlerini belirlemek için Azure AD Identity Protection'i kullanın.</li></ul>|
|Bilgi koruması|Bilgi koruma ilkelerini geliştirme: <ul><li>Microsoft 365 etiketlerini Office 365 veri kaybını önleme (DLP) veya Azure Information Protection bilgilerini ekleme ve değiştirme.</li><li>Bulut Uygulamaları ilkeleri ve uyarıları için Defender.</li></ul>|
|

Ayrıca bkz [: Petya ve WannaCrypt](https://cloudblogs.microsoft.com/microsoftsecure/2018/02/21/how-to-mitigate-rapid-cyberattacks-such-as-petya-and-wannacrypt/) gibi hızlı siber saldırıların azaltmak.
