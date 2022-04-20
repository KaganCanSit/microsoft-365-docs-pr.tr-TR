---
title: Adım 5. Bilgileri koruyun
author: dansimp
f1.keywords:
- NOCSH
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- ransomware
- m365solution-ransomware
ms.custom: seo-marvel-jun2020
keywords: fidye yazılımı, insan tarafından çalıştırılan fidye yazılımı, insan tarafından çalıştırılan fidye yazılımı, HumOR, gasp saldırısı, fidye yazılımı saldırısı, şifreleme, kriptoviroloji, sıfır güven
description: Microsoft 365 hassas verilerinizi korumak için denetimli klasör erişimi, Microsoft Purview Information Protection, DLP ve Microsoft Defender for Cloud Apps kullanın.
ms.openlocfilehash: e32c214688adb60fa39fc3c392512f46ec94aecf
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64945141"
---
# <a name="step-5-protect-information"></a>Adım 5. Bilgileri koruyun

Fidye yazılımı saldırganları dosya, veritabanı ve diğer sunucu türlerinde bulunan şirket içi verilerinize de göz atacağından, bu verileri korumanın en iyi yollarından biri, verileri Microsoft 365 kiracınıza geçirmektir. Oraya vardıktan sonra [sürüm oluşturma, geri dönüşüm kutusu ve Dosyalar Geri Yükleme](ransomware-protection-microsoft-365.md#ransomware-mitigation-and-recovery-capabilities-provided-with-microsoft-365) gibi yerleşik azaltma ve kurtarma özellikleriyle korunabilir.

Microsoft 365 kiracınızdaki hassas bilgilerin ek korumasını sağlamak için:

- Hassas bilgilerinizi bulun.
- Katı izinler uygulayın ve geniş erişimi ortadan kaldırarak (örneğin, çok fazla kullanıcının yazma, düzenleme ve silme özelliklerine sahip olmasını engelleyin).
- Hassas bilgilerinizi koruyun.

>[!Note]
>Microsoft 365 kiracıdaki bilgi korumasına yönelik ayrıntılı dağıtım kılavuzu için bkz[. Veri gizliliği düzenlemeleri için bilgi korumasını dağıtma](information-protection-deploy.md). Veri gizliliği düzenlemelerine yönelik olsa da kılavuzun çoğu fidye yazılımı koruması için de geçerlidir.
>

## <a name="locate-your-sensitive-information"></a>Hassas bilgilerinizi bulma

İlk görev, kiracınızdaki hassas bilgilerin [türlerini ve konumlarını belirlemektir ve](/microsoft-365/compliance/information-protection#know-your-data) bu bilgiler aşağıdaki türleri içerebilir:

- Hassas
- Mülkiyet veya fikri mülkiyet
- Düzenlenmiş, kişisel olarak tanımlayıcı bilgilerin (PII) korunmasını belirten bu tür bölgesel düzenlemeler
- BT kurtarma planları

Her hassas bilgi türü için aşağıdakileri belirleyin:

- Bilgilerin kuruluşunuza kullanımı
- Fidye için tutulduysa parasal değerinin göreli ölçüsü (yüksek, orta, düşük gibi)
- OneDrive veya SharePoint klasörü ya da Microsoft Teams ekibi gibi işbirliği yeri gibi geçerli konumu
- Şunlardan oluşan geçerli izinler:

   - Erişimi olan kullanıcı hesapları

   - Erişimi olan her hesaba izin verilen eylemler 

## <a name="implement-strict-permissions-for-locations-with-sensitive-information"></a>Hassas bilgiler içeren konumlar için katı izinler uygulama

Microsoft 365 kiracınızda katı izinler uygulamak, Microsoft 365 genellikle klasörler, SharePoint siteler ve klasörler ve ekipler OneDrive konumlar ve iletişim yerleri için en az ayrıcalık ilkesini kullanır. 

Hassas bilgiler için geniş erişimli (örneğin, kuruluşunuzdaki herkesin varsayılanı) dosya depolama konumları veya ekipler oluşturmak daha kolay olsa da, izin verilen kullanıcı hesapları ve izin verilen eylemler işbirliği ve iş gereksinimlerini karşılamak için gereken minimum kümeyle sınırlandırılmalıdır.

Bir fidye yazılımı saldırganı kiracınıza sızdıktan sonra, kiracınızda yönetici rolü hesapları veya hassas bilgilere erişimi olan kullanıcı hesapları gibi daha geniş kapsamlı izinlere sahip kullanıcı hesaplarının kimlik bilgilerini tehlikeye atarak ayrıcalıklarını yükseltmeye çalışır. 

Bu tipik saldırgan davranışına bağlı olarak, saldırgan için iki zorluk düzeyi vardır:

- **Düşük:** Saldırgan, kiracınız genelinde geniş erişim nedeniyle düşük izinli bir hesap kullanabilir ve hassas bilgilerinizi bulabilir.
- **Yüksek:** Saldırgan, katı izinler nedeniyle düşük izinli bir hesap kullanamaz ve hassas bilgilerinizi bulamıyor. Hassas bilgilere sahip bir konuma erişimi olan bir hesabın kimlik bilgilerini belirleyip tehlikeye atarak izinlerini yükseltmeleri gerekir, ancak bu durumda yalnızca sınırlı bir eylem kümesi gerçekleştirebilir.

Hassas bilgiler için, zorluk düzeyini olabildiğince yüksek yapmalısınız.

Aşağıdaki adımlarla kiracınızda katı izinler sağlayabilirsiniz:

1. [Hassas bilgilerinizi bulma çabasından, hassas bilgilerin](#locate-your-sensitive-information) konumları için izinleri gözden geçirin. 
2. İşbirliği ve iş gereksinimlerini karşılarken hassas bilgiler için katı izinler uygulayın ve etkilenen kullanıcıları bilgilendirin.
3. Hassas bilgiler için gelecekteki konumların katı izinlerle oluşturulması ve korunması için kullanıcılarınız için değişiklik yönetimi gerçekleştirin.
4. Geniş izinlerin verilmediğinden emin olmak için hassas bilgiler için konumları denetleyin ve izleyin.

Ayrıntılı yönergeler için bkz. [Microsoft Teams ile güvenli dosya paylaşımını ve işbirliğini ayarlama](setup-secure-collaboration-with-teams.md). Hassas bilgiler için katı izinlere sahip bir iletişim ve işbirliği mekanına örnek olarak [güvenlik yalıtımına sahip bir ekip gösteriliyor](/microsoft-365/solutions/secure-teams-security-isolation).

## <a name="protect-your-sensitive-information"></a>Hassas bilgilerinizi koruma

Fidye yazılımı saldırganına erişim elde etme ihtimaline karşı hassas bilgilerinizi korumak için:

- Yetkisiz uygulamaların [denetimli klasörlerdeki](/windows/security/threat-protection/microsoft-defender-atp/controlled-folders) verileri değiştirmesini zorlaştırmak için denetimli klasör erişimini kullanın.

- [Microsoft Purview Information Protection](/microsoft-365/compliance/information-protection) ve duyarlılık etiketlerini kullanın ve bunları hassas bilgilere uygulayın. Duyarlılık etiketleri, tanımlı kullanıcı hesapları ve izin verilen eylemlerle ek şifreleme ve izinler için yapılandırılabilir. Kiracınızdan sızan bu tür duyarlılık etiketiyle etiketlenmiş bir dosya yalnızca etikette tanımlanan bir kullanıcı hesabı için kullanılabilir.

- Microsoft Purview [Veri Kaybı Önleme'yi (DLP)](/microsoft-365/compliance/dlp-learn-about-dlp) kullanarak hem şirket içinde hem de dışında duyarlılık etiketlerine dayalı olarak kişisel veya gizli bilgiler içeren verilerin riskli, yanlışlıkla veya uygunsuz bir şekilde paylaşılmalarını algılayın, uyarın ve engelleyin.

- Dosyalar gibi hassas bilgilerin indirilmelerini engellemek için [Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security) kullanın. Yüksek oranda dosya karşıya yükleme veya dosya silme etkinliğini algılamak için [Bulut için Defender Uygulamaları anomali algılama ilkelerini](/cloud-app-security/anomaly-detection-policy#ransomware-activity) de kullanabilirsiniz.

## <a name="impact-on-users-and-change-management"></a>Kullanıcılar ve değişiklik yönetimi üzerindeki etkisi

Geniş izinlerde yapılan yönetim değişiklikleri kullanıcıların erişiminin reddedilmesine veya bazı eylemlerin yürütülememesine neden olabilir.

Ayrıca, Microsoft 365 kiracınızdaki hassas bilgilerin korunması için kullanıcılarınızı şu şekilde eğitin:

- Katı izinlere sahip iletişim ve işbirliği alanları oluşturun (erişim için en az kullanıcı hesabı kümesi ve her hesap için izin verilen minimum eylemler). 
- Hassas bilgilere uygun duyarlılık etiketlerini uygulayın.
- Denetimli klasör erişimini kullanın.

## <a name="resulting-configuration"></a>Sonuçta elde edilen yapılandırma

1-5 arası adımlar için kiracınız için fidye yazılımı koruması aşağıdadır.

![5. Adımdan sonra Microsoft 365 kiracınız için fidye yazılımı koruması](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step5.png)

## <a name="additional-ransomware-resources"></a>Ek fidye yazılımı kaynakları

Microsoft'tan önemli bilgiler:

- [Artan fidye yazılımı tehdidi](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/), Microsoft On the Issues blog gönderisi 20 Temmuz 2021'de
- [İnsan tarafından çalıştırılan fidye yazılımı](/security/compass/human-operated-ransomware)
- [Fidye yazılımı ve gaspa karşı hızla koruma](/security/compass/protect-against-ransomware)
- [2021 Microsoft Dijital Savunma Raporu](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (bkz. sayfa 10-19)
- [Fidye yazılımı: Microsoft 365 Defender portalında sürekli ve sürekli tehdit tehdit](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) analizi raporu
- Microsoft'un Algılama ve Yanıt Ekibi (DART) fidye yazılımı [yaklaşımı ve en iyi yöntemler](/security/compass/incident-response-playbook-dart-ransomware-approach) ve [örnek olay incelemesi](/security/compass/dart-ransomware-case-study)

Microsoft 365:

- [Azure ve Microsoft 365 ile Fidye Yazılımı Dayanıklılığını En Üst Düzeye Çıkarma](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Fidye yazılımı saldırısından kurtarma](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [Kötü amaçlı yazılım ve fidye yazılımı koruması](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Windows 10 bilgisayarınızı fidye yazılımlarından koruma](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [SharePoint Online'da fidye yazılımlarını işleme](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- Microsoft 365 Defender portalında [fidye yazılımı için tehdit analizi raporları](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag)

Microsoft 365 Defender:

- [Gelişmiş avcılık ile fidye yazılımı bulma](/microsoft-365/security/defender/advanced-hunting-find-ransomware)

Microsoft Azure:

- [Fidye Yazılımı Saldırısı için Azure Defenses](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [Azure ve Microsoft 365 ile Fidye Yazılımı Dayanıklılığını En Üst Düzeye Çıkarma](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Fidye yazılımlarına karşı koruma sağlamak için yedekleme ve geri yükleme planı](/security/compass/backup-plan-to-protect-against-ransomware)
- [Microsoft Azure Backup ile fidye yazılımlarından korunmaya yardımcı olun](https://www.youtube.com/watch?v=VhLOr2_1MCg) (26 dakikalık video)
- [Sistemik kimlik güvenliğinin aşılmasından kurtarma](/azure/security/fundamentals/recover-from-identity-compromise)
- [Microsoft Sentinel'de gelişmiş çok aşamalı saldırı algılama](/azure/sentinel/fusion#ransomware)
- [Microsoft Sentinel'de Fidye Yazılımı için Fusion Algılama](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Microsoft Defender for Cloud Apps:

-  [Bulut için Defender Uygulamalarında anomali algılama ilkeleri oluşturma](/cloud-app-security/anomaly-detection-policy)

Microsoft Güvenlik ekibi blog gönderileri:

- [Fidye yazılımlarını önleme ve kurtarma için 3 adım (Eylül 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [İnsan tarafından çalıştırılan fidye yazılımıyla mücadele kılavuzu: Bölüm 1 (Eylül 2021)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  Microsoft'un Algılama ve Yanıt Ekibi'nin (DART) fidye yazılımı olay araştırmalarını nasıl yürüttüğüne ilişkin temel adımlar.

- [İnsan tarafından çalıştırılan fidye yazılımıyla mücadele kılavuzu: Bölüm 2 (Eylül 2021)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  Öneriler ve en iyi yöntemler.

- [Siber güvenlik risklerini anlayarak dayanıklı hale gelme: Bölüm 4— Mevcut tehditlerde gezinme (Mayıs 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  **Fidye yazılımı** bölümüne bakın.

- [İnsan tarafından işletilen fidye yazılımı saldırıları: Önlenebilir bir olağanüstü durum (Mart 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  Gerçek saldırıların saldırı zinciri analizlerini içerir.

- [Fidye yazılımı yanıtı— ödeme yapmak için mi yoksa ödememek için mi? (Aralık 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [Norsk Hydro fidye yazılımı saldırısına şeffaflıkla yanıt veriyor (Aralık 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
