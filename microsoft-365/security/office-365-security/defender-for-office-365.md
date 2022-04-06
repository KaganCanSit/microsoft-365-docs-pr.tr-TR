---
title: Office 365 için Microsoft Defender - CSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.localizationpriority: high
search.appverid:
- MET150
- MOE150
ms.assetid: e100fe7c-f2a1-4b7d-9e08-622330b83653
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
- intro-overview
description: Office 365 için Microsoft Defender Kasa, Kasa Bağlantılar, gelişmiş kimlik avı önleme araçları, raporlama araçları ve tehdit zekası özellikleri içerir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b8041962ca1a696146f9a5828c66b1a6800c4b01
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683745"
---
# <a name="microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Bu makale, Microsoft [Defender'a sahip iş müşterileri için Office 365](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description). Outlook.com, Microsoft 365 Aile veya Microsoft 365 Bireysel kullanıyorsanız ve Outlook'te Kasa Bağlantıları veya Kasa Ekleri hakkında bilgi arıyorsanız bkz. gelişmiş [Outlook.com güvenliği Microsoft 365 aboneleri](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Güvenlik için Microsoft Defender Office 365 e-posta iletileri, bağlantılar (URL'ler) ve işbirliği araçları tarafından tehditlere karşı kuruluşu korur. Defender for Office 365 şunları içerir:

- **[Tehdit koruması ilkeleri](#configure-microsoft-defender-for-office-365-policies)**: Organizasyonunız için uygun koruma düzeyini ayarlamak üzere tehdit koruması ilkelerini tanımlayın.

- **[Raporlar](#view-microsoft-defender-for-office-365-reports)**: Defender'ı izlemek ve Office 365 performansını izlemek için gerçek zamanlı raporları görüntüleniyor.

- **[Tehdit soruşturması ve yanıt özellikleri](#use-threat-investigation-and-response-capabilities)**: Tehditleri araştırmak, anlamak, benzetmek ve engellemek için önde gelen araçları kullanın.

- **[Otomatik araştırma ve yanıt özellikleri](office-365-air.md)**: Zaman ve çabadan tasarruf etmek için araştırma ve tehditleri azaltmaya yönelik çabalar gerekir.

## <a name="interactive-guide-to-microsoft-defender-for-office-365"></a>Microsoft Defender for Office 365 için etkileşimli Office 365

Bu etkileşimli kılavuzda, iş için Microsoft Defender ile organizasyonlarınızı korumayı Office 365. Güvenlik ilkeleri için Defender'ın Office 365 ilkeleri tanımlamanıza, kuruma yönelik tehditleri çözümlemenize ve saldırılara yanıt vermenize nasıl yardımcı olduğunu görebilir.

[Etkileşimli kılavuza göz atabilirsiniz](https://aka.ms/MSDO-IG)

## <a name="getting-started"></a>Başlarken

Office 365 için Microsoft Defender'ı ilk kez kullanıyorsanız veya en iyi şekilde bunu yaparak iyi bir çalışma deneyimine sahip olursanız *, bu* makaleyi başvuru olarak kullanarak Office 365 yapılandırmasının bazı parçalara ayrılarak incelenmesini ve raporları görüntülemesini s avantajından yararlanabilirsiniz. Mantıksal erken yapılandırma öbekleri:

- Adı 'anti' *olan her* şeyi yapılandır.
  - kötü amaçlı yazılımdan koruma
  - kimlik avı önleme
  - istenmeyen posta önleme
- Adı 'kasa' *olacak şekilde* her şeyi ayarlayın.
  - Güvenli Bağlantılar
  - Kasa Ekleri Kaydetme
- İş yüklerini savunma (örneğin. SharePoint Online, OneDrive ve Teams)
- Sıfır saatlik otomatik temizleme (ZAP) ile koruyun.

Yaparak öğrenmek için bu [bağlantıya tıklayın](protect-against-threats.md).

> [!NOTE]
> Windows için Microsoft Defender Office 365 iki farklı Plan türüyle gelir. Plan **1'e** sahip olup değilken "Gerçek Zamanlı Algılamalar" varsa Plan 2'ye, Tehdit Gezgini'ne sahip olupsanız Plan **2'ye** sahip olup ola bakabilirsiniz. Göreceğiniz araçları Sizin Planınız etkiler, bu nedenle öğrenirken Planınız hakkında bilginiz olduğunu bilin.

## <a name="microsoft-defender-for-office-365-plan-1-and-plan-2"></a>Plan 1 ve Plan 2 Office 365 için Microsoft Defender

Aşağıdaki tabloda her plana nelerin dahil olduğu özetlenmiştir.

|Office 365 için Defender Plan 1|Office 365 için Defender Plan 2|
|---|---|
|Yapılandırma, koruma ve algılama özellikleri: <ul><li>[Kasa Ekleri Kaydetme](safe-attachments.md)</li><li>[Güvenli Bağlantılar](safe-links.md)</li><li>[Kasa, Bağlantı SharePoint OneDrive için Ekleri Microsoft Teams](mdo-for-spo-odb-and-teams.md)</li><li>[Kimlik avı için Defender'da kimlik avı koruması Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Gerçek zamanlı algılamalar](threat-explorer.md)</li></ul>|Plan 1 Office 365 için Defender <p> --- artı --- <p> Otomasyon, araştırma, düzeltme ve eğitim özellikleri: <ul><li>[Tehdit İzleyicileri](threat-trackers.md)</li><li>[Tehdit Gezgini](threat-explorer.md)</li><li>[Otomatik araştırma ve yanıt](office-365-air.md)</li><li>[Saldırı benzetimi eğitimi](attack-simulation-training.md)</li><li>[E-Microsoft 365 Defender'de gelişmiş avla tehditlere karşı önceden Microsoft 365 Defender](../defender/advanced-hunting-overview.md)</li><li>[E-Microsoft 365 Defender'de olayları araştır](../defender/investigate-incidents.md)</li><li>[E-postada uyarıları Microsoft 365 Defender](../defender/investigate-alerts.md)</li></ul>|

- Office 365 için Microsoft Defender Plan 2 Office 365 E5, Office 365 A5 ve Microsoft 365 E5.

- Plan 1 Office 365 için Microsoft Defender çevrimiçi Microsoft 365 İş Ekstra.

- Office 365 için Microsoft Defender Plan 1 ve Office 365 Için Defender Plan 2'nin her biri, belirli abonelikler için bir eklenti olarak kullanılabilir. Daha fazla bilgi edinmek için, bu planlar için [Microsoft Defender genelindeki Özellik kullanılabilirliği Office 365 vardır](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- Belgeler [Kasa özelliği](safe-docs.md) yalnızca lisans sahibi veya Microsoft 365 E5 Microsoft 365 E5 Güvenlik (Office 365 planları için Microsoft Defender'a dahil değildir) kullanıcılar tarafından kullanılabilir.

- Geçerli aboneliğiniz Office 365 için Microsoft Defender'ı dahil etmek istemiyorsanız[,](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html) denemeyi başlatmak için satışla iletişime geçin ve Office 365 için Microsoft Defender'ın nasıl çalışacı olduğunu öğrenin.

- Office 365 P2 için Microsoft Defender müşterilerinin Microsoft 365 Defender ve uyarıları etkili bir şekilde  algılamak, gözden geçirmek ve yanıtlamak için Microsoft 365 Defender tümleştirmelerine erişimi vardır.

## <a name="configure-microsoft-defender-for-office-365-policies"></a>Microsoft Defender'ı Office 365 yapılandırma

Office 365 için Microsoft Defender ile, Microsoft 365 Defender portalında  \>  \> <https://security.microsoft.com> E-posta ve işbirliği İlkeleri'nin altında yer alan & kuralları Tehdit ilkeleri'& ilkeleri tanımlayarak korumayı **yapılandırabilirsiniz**. Bunun yerine, 'ı kullanarak doğrudan **Tehdit ilkeleri** sayfasına da gidebilirsiniz <https://security.microsoft.com/threatpolicy>.

Daha fazla bilgi edinmek için [bu videoyu izleyin](https://www.youtube.com/watch?v=vivvTmWJ_3c).

> [!TIP]
> Tanımlanacak ilkelerin hızlı bir listesi için bkz. [Tehditlere karşı koruma](protect-against-threats.md).

## <a name="defender-for-office-365-policies"></a>Office 365 İlkeleri için Defender

Önceden tanımlanmış tehditlere yönelik davranış ve koruma düzeyi, sizin için tanımlanan ilkeler tarafından belirler. İlke seçenekleri aşırı esnektir. Örneğin, kuruluş güvenlik ekibi kullanıcı, kuruluş, alıcı ve etki alanı düzeyinde geniş geniş bir tehdit koruması kurabilirsiniz. Yeni tehditlerin ve zorlukların günlük olarak ortaya çıkması nedeniyle ilkelerinizi düzenli olarak gözden geçirmek önemlidir.

- **[Kasa: E-posta](safe-attachments.md)** eklerini kötü amaçlı içeriklere karşı kontrol ederek ileti sistemini korumak için sıfır günlük koruma sağlar. Virüs/kötü amaçlı yazılım imzasız tüm iletileri ve ekleri özel bir ortama yönlendiriyor ve sonra da kötü amaçlı amacı saptamak için makine öğrenme ve çözümleme tekniklerini kullanır. Hiçbir şüpheli etkinlik bulunursa, ileti posta kutusuna iletlenir. Daha fazla bilgi için bkz[. Ek İlkelerini Kasa ayarlama](set-up-safe-attachments-policies.md).

- **[Kasa Bağlantıları](safe-links.md)**: E-posta iletisinde ve dosyalarda olduğu gibi URL'ler için tıklamayla doğrulama Office sağlar. Koruma sürekli olarak mesajlaşma ve uygulama ortamınız genelinde Office uygulanır. Bağlantılar her tıklama için taranır: Güvenli bağlantılar erişilebilir kalır ve kötü amaçlı bağlantılar dinamik olarak engellenir. Daha fazla bilgi edinmek için bkz[. Bağlantı Kasa ayarlama](set-up-safe-links-policies.md).

- **[Kasa. SharePoint, OneDrive ve Microsoft Teams](mdo-for-spo-odb-and-teams.md)** ekleri: Ekip sitelerinde ve belge kitaplıklarında kötü amaçlı dosyaları tanımleyerek ve engelleyerek, kullanıcılar dosyalarda işbirliği ve paylaşımda bulundurarak, organizasyonlarınızı korur. Daha fazla bilgi edinmek için bkz[. SharePoint, OneDrive ve Office 365 için Defender'ı Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).

- **[Kimlik avı için Defender'daki Kimlik avı koruması](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)** Office 365: Kullanıcılarınızı ve iç veya özel etki alanlarınızı kimliğe bürünme girişimleri algılar. Kimlik avı saldırılarını tersine çeviren makine öğrenme modellerini ve gelişmiş kimliğe bürünme algılama algoritmalarını uygular. Daha fazla bilgi edinmek için bkz[. Kimlik avı için Microsoft Defender'da kimlik avı Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="view-microsoft-defender-for-office-365-reports"></a>Yeni raporlar için Microsoft Defender Office 365 görüntüleme

Office 365 için Microsoft Defender, destek [için](view-reports-for-mdo.md) Defender'ı izlemek Office 365. Raporlara Microsoft 365 Defender portalında <https://security.microsoft.com>  \> Raporlar **E-posta** ve işbirliği &-posta \> ve **işbirliği & erişebilirsiniz**. Veya doğrudan 'ı kullanarak E-posta **ve işbirliği raporları sayfasına** gidebilirsiniz <https://security.microsoft.com/securityreports>.

Raporlar gerçek zamanlı olarak güncelleştirmesi, size en yeni bilgileri sağlar. Ayrıca bu raporlar size yakın tehditlere karşı öneriler sağlar ve sizi uyarıyor. Önceden tanımlanmış raporlar aşağıdakileri içerir:

- [Tehdit Gezgini (veya gerçek zamanlı algılamalar)](threat-explorer.md)
- [Tehdit koruması durum raporu](view-reports-for-mdo.md#threat-protection-status-report)
- ... ve birkaç kişi daha.

## <a name="use-threat-investigation-and-response-capabilities"></a>Tehdit araştırma ve yanıt özelliklerini kullanma

Office 365 için Microsoft Defender Plan 2, kuruluş güvenlik ekibinin kötü amaçlı saldırılarla ilgili tahminde ve anlamaya ve engellemeye olanak sağlayan en iyi sınıf tehdit soruşturması ve yanıt araçları içerir.[](office-365-ti.md)

- **[Tehdit izleyicileri](threat-trackers.md)** en son siber güvenlik sorunları konusunda en son zekayı sağlar. Örneğin, en son kötü amaçlı yazılımla ilgili bilgileri  görüntüp, bunun organizasyonunız için gerçek bir tehdit haline gelmeden önce önlem almalarını sebilirsiniz. Kullanılabilir izleyiciler [Şunlardır: Dikkat çekici izleyiciler](threat-trackers.md#noteworthy-trackers), Popüler [izleyiciler](threat-trackers.md#trending-trackers), [İzlanan sorgular](threat-trackers.md#tracked-queries) [ve Kaydedilmiş sorgular](threat-trackers.md#saved-queries).

- **[Tehdit Gezgini (veya gerçek zamanlı algılamalar)](threat-explorer.md)** (Gezgin olarak da adlandırılır) son tehditleri tanımlamanıza ve çözümlemenıza olanak sağlayan gerçek zamanlı bir rapordır. Gezgin'i özel dönemlere göre verileri gösterecek şekilde yapılandırabilirsiniz.

- **[Saldırı benzetimi eğitimi](attack-simulation-training.md)** , güvenlik açıklarını tanımlamak için organizasyonu gerçekçi saldırı senaryolarını çalıştırmanıza olanak sağlar. Kimlik avı kimlik bilgisi toplama ve ek saldırılarının, parola parola saldırılarının ve parola saldırılarının da içinde olduğu mevcut saldırı türlerinin benzetimleri gerçektir.

## <a name="save-time-with-automated-investigation-and-response"></a>Otomatik araştırma ve yanıtla zaman kazanmak

(**Yenİ!**) Olası bir siber saldırıları araştırıyorken, zaman özünü belirlemektedir. Tehditleri ne kadar çabuk tespit edebilir ve ne kadar kısa sürede azaltmak için, kuruluşta o kadar iyi bir seçim olmayacaktır. [Otomatik araştırma](office-365-air.md) ve yanıt (AIR) özellikleri, bir uyarının tetiklendiğinde veya el ile, örneğin Explorer'daki bir görünümden başlatıldığı durumlarda otomatik olarak başlatılabilir bir dizi güvenlik çalışma kitabı içerir. AIR, güvenlik işlemleriniz için ekip zaman ve çabadan tasarruf etmek için tehditleri etkili ve verimli bir şekilde azaltmaya yardımcı olur. Daha fazla bilgi edinmek için [bkz. Office 365](office-365-air.md).

## <a name="permissions-required-to-use-microsoft-defender-for-office-365-features"></a>Office 365 özellikleri için Microsoft Defender'ı kullanmak Office 365 izinleri

Microsoft Defender for Office 365 erişmek için, size uygun bir rol atanacak. Aşağıdaki tabloda bazı örnekler verilmiştir:

|Rol veya rol grubu|Daha fazla bilgi edinmek için kaynaklar|
|---|---|
|genel yönetici (Kuruluş Yönetimi)|Bu rolü Azure Active Directory portalında veya Microsoft 365 Defender atabilirsiniz. Daha fazla bilgi için bkz[. Microsoft 365 Defender portalına.](permissions-microsoft-365-security-center.md)|
|Güvenlik Yöneticisi|Bu rolü Azure Active Directory portalında veya Microsoft 365 Defender atabilirsiniz. Daha fazla bilgi için bkz[. Microsoft 365 Defender portalına.](permissions-microsoft-365-security-center.md)|
|Kuruluş Yönetimi Exchange Online|[Web'de Exchange Online](/exchange/permissions-exo/permissions-exo) <p> [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell)|
|Arama ve Temizleme|Bu rol yalnızca Microsoft 365 Defender portalında veya Microsoft 365 uyumluluk merkezi. Daha fazla bilgi için bkz. [Site portalında Microsoft 365 Defender ve](permissions-microsoft-365-security-center.md) [Sitenin İzinleri Microsoft 365 uyumluluk merkezi](../../compliance/microsoft-365-compliance-center-permissions.md).|
|||

## <a name="get-microsoft-defender-for-office-365"></a>Microsoft Defender'ı Office 365

Office 365 için Microsoft Defender, abonelikler, abonelikler, Microsoft 365 E5, Office 365 E5 ve Office 365 A5 gibi Microsoft 365 İş Ekstra. Aboneliğiniz Office 365 için Defender'ı eklese bile bazı aboneliklere eklenti olarak Office 365 Plan 1 veya Office 365 için Defender satın alabilirsiniz. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Abonelikler için Office 365 Için Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#office-365-advanced-threat-protection-atp-availability) içeren aboneliklerin listesi için Microsoft Defender'ın kullanılabilir Office 365 vardır.

- [Plan 1 ve 2'de bulunan Office 365 listesi](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans) için Microsoft Defender genelinde özellik kullanılabilirliği.

- [Planları karşılaştırmak ve satın almak için Office 365 Microsoft Defender](https://products.office.com/exchange/advance-threat-protection#pmg-allup-content) for Office 365.

- [Ücretsiz denemeyi başlatma](https://go.microsoft.com/fwlink/p/?LinkID=698279)

## <a name="new-features-in-microsoft-defender-for-office-365"></a>Windows için Microsoft Defender'daki yeni Office 365

Microsoft Defender'a sürekli yeni özellikler Office 365 eklendi. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Microsoft 365 Haritası](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=Microsoft%2CDefender%2Cfor%2COffice%2C365) geliştirme ve düzenlemeyle ilgili yeni özelliklerin bir listesini sağlar.

- [Office 365 için Microsoft Defender Hizmet Açıklaması](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#whats-new-in-office-365-advanced-threat-protection-atp), bu planlar için Defender genelindeki özellikleri ve Office 365 açıklamayı açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)
- [Web'de otomatik araştırma ve yanıt (AIR) Microsoft 365 Defender](../defender/m365d-autoir.md)
