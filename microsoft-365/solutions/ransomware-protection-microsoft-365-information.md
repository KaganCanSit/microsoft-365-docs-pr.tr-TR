---
title: Adım 5. Bilgileri koruma
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
keywords: fidye yazılımı, insan tarafından işletilen fidye yazılımı, insan tarafından işletilen fidye yazılımı, HumOR, extortion saldırısı, fidye yazılımı saldırı, şifreleme, cryptovirology, sıfır güven
description: Denetimli klasör erişimini, MIP, DLP ve Bulut Uygulamaları için Microsoft Defender'ı kullanarak verilerinizi Microsoft 365 koruyun.
ms.openlocfilehash: 0011a3c9fc0d24815818b67906b8f404a191563e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63325103"
---
# <a name="step-5-protect-information"></a>Adım 5. Bilgileri koruma

Fidye yazılımı fidye yazılımları dosyada, veritabanında ve diğer sunucu türlerinde bulunan şirket içi verilerinize de bakacaklarından, bu verileri korumanın en iyi yollarından biri bu verileri Microsoft 365 kiracınıza geçirmektir. Oraya varan sürümleme, geri dönüşüm kutusu ve Dosya Geri Yükleme gibi yerleşik azaltma ve kurtarma [özellikleriyle korunabilirsiniz](ransomware-protection-microsoft-365.md#ransomware-mitigation-and-recovery-capabilities-provided-with-microsoft-365).

Kiracınıza hassas bilgilerin ek korunmasını sağlamak Microsoft 365:

- Hassas bilginizi bulun.
- Katı izinler uygulama ve geniş erişimi ortadan kaldırma (örneğin, çok fazla kullanıcının yazma, düzenleme ve silme özelliklerini değiştirmesini engelleme).
- Hassas bilgilerinizi koruyun.

>[!Note]
>Bir kiracıda bilgi koruması için ayrıntılı dağıtım Microsoft 365 bkz[. Veri gizliliği düzenlemelerine yönelik bilgi korumayı dağıtma](information-protection-deploy.md). Veri gizliliği düzenlemelerine yönelik olsa da, kılavuzun bir çoğu fidye yazılımı koruması için de geçerlidir.
>

## <a name="locate-your-sensitive-information"></a>Hassas bilginizi bulma

İlk görev [kiracınıza, aşağıdaki türlerde yer](/microsoft-365/compliance/information-protection#know-your-data) alan hassas bilgilerin türlerini ve konumlarını belirlemektir:

- Hassas
- Mülkiyet veya fikri mülkiyet
- Düzenlemeye tabi, kişisel olarak tanımlayıcı bilgilerin (PII) korunmasını belirten bu tür bölgesel düzenlemeler
- IT kurtarma planları

Her tür hassas bilgi için, şunları yapın:

- Bilgilerin kuruma kullanımı
- Bu değerin para değerinin tahmin için tutularak yapılan göreli bir ölçüsü (yüksek, orta, düşük gibi)
- Geçerli konumu, örneğin OneDrive SharePoint klasörü veya Microsoft Teams ekibi gibi işbirliği Microsoft Teams.
- Aşağıdakilerden oluşan geçerli izinler:

   - Erişimi olan kullanıcı hesapları

   - Erişimi olan her hesaba izin verilen eylemler 

## <a name="implement-strict-permissions-for-locations-with-sensitive-information"></a>Hassas bilgilerle konumlar için kesin izinler uygulama

Microsoft 365 kiracınız içinde katı izinler uygulamak, Microsoft 365'te genellikle OneDrive klasörleri, siteleri ve klasörleri ve ekipleri olan konumlar ve iletişim yerleri için en SharePoint ayrıcalık ilkesini kullanır. 

Büyük erişime sahip dosya depolama konumları veya ekipler oluşturmak daha kolay (örneğin, kuruluşta herkesin varsayılan ayarı) daha kolay bulunsa da, hassas bilgiler için izin verilen kullanıcı hesapları ve izin verilen eylemler, işbirliği ve iş gereksinimlerini karşılamak için gereken en düşük kümeyle sınırlı tutulsun.

Bir fidye yazılımı kiracınızı ele geçirildiklerinde, kullanıcı hesaplarının kimlik bilgilerini yönetici rol hesapları veya hassas bilgilere erişimi olan kullanıcı hesapları gibi kiracı genelinde daha geniş izin kapsamlarıyla ödün vermeden ayrıcalıklarını yükseltmeye çalışırlar. 

Bu tipik saldırgan davranışına bağlı olarak, saldırgan için iki zorluk düzeyi vardır:

- **Düşük:** Bir saldırgan düşük izinli bir hesap kullanabilir ve kiracınız genelinde geniş erişim nedeniyle hassas bilgilerinizi keşfeder.
- **Daha yüksek:** Bir saldırgan düşük izinli bir hesap kullanamaz ve katı izinler nedeniyle hassas bilginizi keşfeder. Hassas bilgilerle bir konuma erişimi olan bir hesabın kimlik bilgilerini belirleyerek ve bundan sonra ödün vererek izinlerini yükseltmeleri gerekir, ancak bu işlem yalnızca sınırlı bir eylem kümesi gerçekleştirebilirsiniz.

Hassas bilgiler için, zorluk düzeyini mümkün olduğu kadar yüksek bir düzeye taşıyor olması gerekir.

Kiracınız için şu adımlarla kesin izinler sebilirsiniz:

1. Hassas bilgileri bulma [çabalarından,](#locate-your-sensitive-information) hassas bilgilerin konumları için izinleri gözden geçirebilirsiniz. 
2. Hassas bilgiler için sıkı izinler uygulayarak işbirliği ve iş gereksinimlerini karşılar ve bundan etkilenen kullanıcıları bilgilendirin.
3. Hassas bilgiler için gelecekteki konumların kesin izinlerle oluşturulup korunması için kullanıcılarınız için değişiklik yönetimi gerçekleştirin.
4. Kapsamlı izinlerin verilmey olduğundan emin olmak için hassas bilgiler için konumları denetleyin ve takip edin.

Ayrıntılı [kılavuz için bkz. Güvenli dosya paylaşımını Microsoft Teams](setup-secure-collaboration-with-teams.md) işbirliğini ayarlama. Hassas bilgiler için kesin izinlere sahip bir iletişim ve işbirliği merkezi örneği, güvenlik [yalıtlığı olan bir ekiptir](/microsoft-365/solutions/secure-teams-security-isolation).

## <a name="protect-your-sensitive-information"></a>Hassas bilgilerinizi koruyun

Fidye yazılımı yazılımı yazılımına erişim elde etmeleri durumunda hassas bilgilerinizi korumak için:

- Yetkisiz [uygulamaların denetimli](/windows/security/threat-protection/microsoft-defender-atp/controlled-folders) klasörlerdeki verileri değiştirmesini zorlaştıracak şekilde denetimli klasör erişimini kullanın.

- Metin [Microsoft Bilgi Koruması](/microsoft-365/compliance/information-protection) duyarlılık etiketlerini kullanın ve bunları hassas bilgilere uygulayabilirsiniz. Duyarlılık etiketleri, tanımlı kullanıcı hesapları ve izin verilen eylemlerle ek şifreleme ve izinler için ya zamanlandı. Kiracıdan genişletilebilir duyarlılık etiketi türüne sahip bir dosya yalnızca etikette tanımlanmış bir kullanıcı hesabı için kullanılabilir.

- Duyarlılık etiketleri Microsoft 365 dahili ve harici olarak kişisel veya gizli bilgiler içeren riskli, istemeden veya uygunsuz veri paylaşımını tespit etmek, uyarmak ve engellemek için Microsoft 365 Veri Kaybı Önleme [(DLP)](/microsoft-365/compliance/dlp-learn-about-dlp) önlemeyi kullanın.

- Dosyalar [gibi hassas bilgilerin indirilmelerini](/cloud-app-security/what-is-cloud-app-security) engellemek için Bulut Uygulamaları için Microsoft Defender'ı kullanın. Ayrıca, yüksek dosya karşıya [yükleme veya dosya silme](/cloud-app-security/anomaly-detection-policy#ransomware-activity) etkinliklerini algılamak için Bulut Uygulamaları için Defender anormal algılama ilkelerini kullanabilirsiniz.

## <a name="impact-on-users-and-change-management"></a>Kullanıcılar üzerindeki etkisi ve değişiklik yönetimi

Geniş izinlerde yapılan yönetim değişiklikleri, kullanıcıların erişiminin reddedilmiş olması veya bazı eylemlerin yürütülmelerine yol açabilirsiniz.

Buna ek olarak, kullanıcılarınızı aşağıdakiler için Microsoft 365 bilgileri şu şekilde eğitin:

- Katı izinlere (erişim için en az kullanıcı hesabı kümesi ve her hesap için izin verilen en düşük eylem kümesi) sahip iletişim ve işbirliği yerleri oluşturun. 
- Hassas bilgilere düzgün duyarlılık etiketleri uygulayabilirsiniz.
- Denetimli klasör erişimini kullanın.

## <a name="resulting-configuration"></a>Sonuçta elde edilen yapılandırma

İşte, 1-5. adımlar için kiracınız için fidye yazılımı koruması.

![5. Adımdan sonra Microsoft 365 kiracınız için fidye yazılımı koruması](../media/ransomware-protection-microsoft-365/ransomware-protection-microsoft-365-architecture-step5.png)

## <a name="additional-ransomware-resources"></a>Ek fidye yazılımı kaynakları

Microsoft'tan önemli bilgiler:

- [Giderek büyüyen fidye yazılımı tehdidi](https://blogs.microsoft.com/on-the-issues/2021/07/20/the-growing-threat-of-ransomware/) olan Microsoft 20 Temmuz 2021'de Sorunlar blog gönderisi
- [İnsan tarafından işletilen fidye yazılımı](/security/compass/human-operated-ransomware)
- [Fidye yazılımlarına ve ekstörlere karşı hızlı bir şekilde koruma](/security/compass/protect-against-ransomware)
- [2021 Microsoft Dijital Savunma Raporu](https://www.microsoft.com/security/business/microsoft-digital-defense-report) (sayfa 10-19'a bakın)
- [Fidye yazılımı: Microsoft 365 Defender portalında periveive](https://security.microsoft.com/threatanalytics3/05658b6c-dc62-496d-ad3c-c6a795a33c27/overview) ve sürekli tehdit Microsoft 365 Defender raporu
- Microsoft'un Algılama ve Yanıt Ekibi (ATL) fidye yazılımı [yaklaşımı, en iyi yöntemler ve](/security/compass/incident-response-playbook-dart-ransomware-approach) örnek [olay inceleme](/security/compass/dart-ransomware-case-study)

Microsoft 365:

- [Azure ve Microsoft 365 ile Fidye Yazılımı Performansını En Üst Düzeye Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Fidye yazılımı saldırılarından kurtar](/microsoft-365/security/office-365-security/recover-from-ransomware)
- [Kötü amaçlı yazılım ve fidye yazılımına karşı koruma](/compliance/assurance/assurance-malware-and-ransomware-protection)
- [Bilgisayarınızın Windows 10 fidye yazılımlarından koruma](https://support.microsoft.com//windows/protect-your-pc-from-ransomware-08ed68a7-939f-726c-7e84-a72ba92c01c3)
- [SharePoint Online'da fidye yazılımlarını işleme](/sharepoint/troubleshoot/security/handling-ransomware-in-sharepoint-online)
- [Yazılım portalında fidye yazılımı](https://security.microsoft.com/threatanalytics3?page_size=30&filters=tags%3DRansomware&ordering=-lastUpdatedOn&fields=displayName,alertsCount,impactedEntities,reportType,createdOn,lastUpdatedOn,tags,flag) için tehdit Microsoft 365 Defender raporları

Microsoft 365 Defender:

- [Gelişmiş avla fidye yazılımı bulun](/microsoft-365/security/defender/advanced-hunting-find-ransomware)

Microsoft Azure:

- [Fidye Yazılımı Saldırısını Azure Savunma](https://azure.microsoft.com/resources/azure-defenses-for-ransomware-attack/)
- [Azure ve Microsoft 365 ile Fidye Yazılımı Performansını En Üst Düzeye Microsoft 365](https://azure.microsoft.com/resources/maximize-ransomware-resiliency-with-azure-and-microsoft-365/)
- [Fidye yazılımlarına karşı korunmak için planı yedekleme ve geri yükleme](/security/compass/backup-plan-to-protect-against-ransomware)
- [Microsoft Azure Yedekleme ile fidye yazılımlarından korunmaya](https://www.youtube.com/watch?v=VhLOr2_1MCg) yardımcı olun (26 dakikalık video)
- [Sistemsel kimlik güvenliğinden ödün verme](/azure/security/fundamentals/recover-from-identity-compromise)
- [Microsoft Sentinel'de gelişmiş çok amaçlı saldırı algılama](/azure/sentinel/fusion#ransomware)
- [Microsoft Sentinel'de Fidye Yazılımı için Fidye Yazılımı Algılama](https://techcommunity.microsoft.com/t5/azure-sentinel/what-s-new-fusion-detection-for-ransomware/ba-p/2621373)

Bulut Uygulamaları için Microsoft Defender:

-  [Bulut Uygulamaları için Defender'da anormal algılama ilkeleri oluşturma](/cloud-app-security/anomaly-detection-policy)

Microsoft Güvenlik ekibi blog gönderileri:

- [Fidye yazılımlarını önlemeye ve fidye yazılımlarından korunmaya yönelik 3 adım (Eylül 2021)](https://www.microsoft.com/security/blog/2021/09/07/3-steps-to-prevent-and-recover-from-ransomware/)
- [İnsan tarafından işletilen fidye yazılımlarla mücadeleye yardımcı bir kılavuz: Bölüm 1 (Eylül 2021)](https://www.microsoft.com/security/blog/2021/09/20/a-guide-to-combatting-human-operated-ransomware-part-1/)

  Microsoft'un Algılama ve Yanıt Ekibi'nin (YERMİ) fidye yazılımı olayı soruşturmalarını nasıl yönetecekleri ile ilgili önemli adımlar.

- [İnsan tarafından işletilen fidye yazılımıyla mücadeleye kılavuz: Bölüm 2 (Eylül 2021)](https://www.microsoft.com/security/blog/2021/09/27/a-guide-to-combatting-human-operated-ransomware-part-2/)

  Öneriler ve en iyi yöntemler.

- [Siber güvenlik risklerini anlayan giderek daha iyi hale geliyor: Bölüm 4: mevcut tehditlerle gezinme (Mayıs 2021)](https://www.microsoft.com/security/blog/2021/05/26/becoming-resilient-by-understanding-cybersecurity-risks-part-4-navigating-current-threats/)

  Fidye yazılımı **bölümüne** bakın.

- [İnsan tarafından işletilen fidye yazılımı saldırıları: Önlenebilir bir olağanüstü durum (Mart 2020)](https://www.microsoft.com/security/blog/2020/03/05/human-operated-ransomware-attacks-a-preventable-disaster/)

  Gerçek saldırılar için saldırı zinciri çözümlemeleri içerir.

- [Fidye yazılımına yanıt— ödeme yapmak veya ödeme yapmak değil mi? (Aralık 2019)](https://www.microsoft.com/security/blog/2019/12/16/ransomware-response-to-pay-or-not-to-pay/)
- [Norsk 365 Fidye yazılımı saldırılarına saydamlık saldırısıyla yanıt verdi (Aralık 2019)](https://www.microsoft.com/security/blog/2019/12/17/norsk-hydro-ransomware-attack-transparency/)
