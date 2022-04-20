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
description: Office 365 için Microsoft Defender Kasa Ekleri, Kasa Bağlantıları, gelişmiş kimlik avı önleme araçları, raporlama araçları ve tehdit bilgileri özelliklerini içerir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a181f8ef6bb7ca018fb9ddf0f0adc4fe565b73e1
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941555"
---
# <a name="microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Bu makale, [Office 365 için Microsoft Defender](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description) sahip iş müşterilerine yöneliktir. Outlook.com, Microsoft 365 Aile veya Microsoft 365 Bireysel kullanıyorsanız ve Outlook Kasa Bağlantıları veya Kasa Ekleri hakkında bilgi arıyorsanız bkz. [Gelişmiş Outlook.com güvenliği aboneleri Microsoft 365](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Office 365 için Microsoft Defender, kuruluşunuzu e-posta iletileri, bağlantılar (URL'ler) ve işbirliği araçları tarafından ortaya konan kötü amaçlı tehditlere karşı korur. Office 365 için Defender şunları içerir:

- **[Tehdit koruma ilkeleri](#configure-microsoft-defender-for-office-365-policies)**: Kuruluşunuz için uygun koruma düzeyini ayarlamak için tehdit koruma ilkeleri tanımlayın.

- **[Raporlar](#view-microsoft-defender-for-office-365-reports)**: Kuruluşunuzdaki Office 365 için Defender performansını izlemek için gerçek zamanlı raporları görüntüleyin.

- **[Tehdit araştırma ve yanıt özellikleri: Tehditleri](#use-threat-investigation-and-response-capabilities)** araştırmak, anlamak, benzetimini yapmak ve önlemek için önde gelen araçları kullanın.

- **[Otomatik araştırma ve yanıt özellikleri: Tehditleri](office-365-air.md)** araştırmak ve azaltmak için zaman ve çabadan tasarruf edin.

## <a name="interactive-guide-to-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender için etkileşimli kılavuz

Bu etkileşimli kılavuzda, Office 365 için Microsoft Defender ile kuruluşunuzu korumayı öğreneceksiniz. Office 365 için Defender koruma ilkeleri tanımlamanıza, kuruluşunuza yönelik tehditleri analiz etmeye ve saldırılara yanıt vermenize nasıl yardımcı olabileceğini göreceksiniz.

[Etkileşimli kılavuza göz atın](https://aka.ms/MSDO-IG)

## <a name="getting-started"></a>Başlarken

Office 365 için Microsoft Defender yeniyseniz veya *bunu yaparak* en iyi şekilde öğrenmek istiyorsanız, başvuru olarak bu makaleyi kullanarak ilk Office 365 için Defender yapılandırmasının öbeklere bölünmesinden, araştırılmasından ve raporların görüntülenmesinden yararlanabilirsiniz. Mantıksal erken yapılandırma öbekleri şunlardır:

- Adında '*anti*' ile her şeyi yapılandırın.
  - kötü amaçlı yazılımdan koruma
  - kimlik avı önleme
  - Antispam
- Adında "*güvenli*" olan her şeyi ayarlayın.
  - Güvenli Bağlantılar
  - ekleri Kasa
- İş yüklerini savunma (ör. SharePoint Online, OneDrive ve Teams)
- Sıfır saatlik otomatik temizleme (ZAP) ile koruyun.

Bunu yaparak öğrenmek için [bu bağlantıya tıklayın](protect-against-threats.md).

> [!NOTE]
> Office 365 için Microsoft Defender iki farklı Plan türünde gelir. **'** Gerçek Zamanlı Algılamalar' ve Tehdit Gezgini'niz varsa **Plan 1'iniz** olup olmadığını anlayabilirsiniz. Sahip olduğunuz Plan, göreceğiniz araçları etkiler, bu nedenle öğrenirken Planınızın farkında olduğunuzdan emin olun.

## <a name="microsoft-defender-for-office-365-plan-1-and-plan-2"></a>Office 365 için Microsoft Defender Plan 1 ve Plan 2

Aşağıdaki tabloda her plana neler dahil olduğu özetlenmiştir.

|Office 365 için Defender Plan 1|Office 365 için Defender Plan 2|
|---|---|
|Yapılandırma, koruma ve algılama özellikleri: <ul><li>[Güvenli Ekleri Kaydetme](safe-attachments.md)</li><li>[Güvenli Bağlantılar](safe-links.md)</li><li>[SharePoint, OneDrive ve Microsoft Teams için Güvenli Ekler](mdo-for-spo-odb-and-teams.md)</li><li>[Office 365 için Defender'da kimlik avına karşı koruma](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)</li><li>[Gerçek zamanlı algılamalar](threat-explorer.md)</li></ul>|Office 365 için Defender Plan 1 özellikleri <p> --- artı --- <p> Otomasyon, araştırma, düzeltme ve eğitim özellikleri: <ul><li>[Tehdit İzleyiciler](threat-trackers.md)</li><li>[Tehdit Gezgini](threat-explorer.md)</li><li>[Otomatik araştırma ve yanıt](office-365-air.md)</li><li>[Saldırı simülasyonu eğitimi](attack-simulation-training.md)</li><li>[Microsoft 365 Defender'da gelişmiş arama ile tehditleri proaktif olarak avlama](../defender/advanced-hunting-overview.md)</li><li>[Microsoft 365 Defender'daki olayları araştırma](../defender/investigate-incidents.md)</li><li>[Microsoft 365 Defender'da uyarıları araştırma](../defender/investigate-alerts.md)</li></ul>|

- Office 365 için Microsoft Defender Plan 2, Office 365 E5, Office 365 A5 ve Microsoft 365 E5'e dahildir.

- Office 365 için Microsoft Defender Plan 1, Microsoft 365 İş Ekstra'ya dahildir.

- Office 365 için Microsoft Defender Plan 1 ve Office 365 için Defender Plan 2, belirli abonelikler için eklenti olarak kullanılabilir. Daha fazla bilgi edinmek için, [Office 365 planları için Microsoft Defender genelinde Özellik kullanılabilirliği](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans) bağlantısını burada bulabilirsiniz.

- [Güvenli Belgeler](safe-docs.md) özelliği yalnızca Microsoft 365 E5 veya Microsoft 365 E5 Güvenlik lisanslarına sahip kullanıcılar tarafından kullanılabilir (Office 365 için Microsoft Defender planlarına dahil değildir).

- Mevcut aboneliğiniz Office 365 için Microsoft Defender'ı içermiyorsa ve bunu istiyorsanız, [bir deneme başlatmak için satış ekibiyle iletişime geçin](https://info.microsoft.com/ww-landing-M365SMB-web-contact.html) ve Office 365 için Microsoft Defender'ın kuruluşunuzda nasıl çalışabileceğini öğrenin.

- Office 365 için Microsoft Defender P2 müşterileri, olayları ve uyarıları verimli bir şekilde algılamak, gözden geçirmek ve yanıtlamak için **Microsoft 365 Defender tümleştirmesine** erişebilir.

## <a name="configure-microsoft-defender-for-office-365-policies"></a>Office 365 için Microsoft Defender ilkelerini yapılandırma

kuruluşunuzun güvenlik ekibi, Office 365 için Microsoft Defender ile **e-posta & işbirliği** \> **İlkeleri'ndeki** Microsoft 365 Defender portalında <https://security.microsoft.com> ilkeleri tanımlayarak korumayı yapılandırabilir & **Tehdit ilkelerini** kurallar\>. Veya kullanarak <https://security.microsoft.com/threatpolicy>doğrudan **Tehdit ilkeleri** sayfasına gidebilirsiniz.

[Bu videoyu](https://www.youtube.com/watch?v=vivvTmWJ_3c) izleyerek daha fazla bilgi edinin.

> [!TIP]
> Tanımlanacağı ilkelerin hızlı listesi için bkz. [Tehditlere karşı koruma](protect-against-threats.md).

## <a name="defender-for-office-365-policies"></a>Office 365 için Defender İlkeleri

Kuruluşunuz için tanımlanan ilkeler, önceden tanımlanmış tehditler için davranış ve koruma düzeyini belirler. İlke seçenekleri son derece esnek. Örneğin, kuruluşunuzun güvenlik ekibi kullanıcı, kuruluş, alıcı ve etki alanı düzeyinde ayrıntılı tehdit koruması ayarlayabilir. Her gün yeni tehditler ve zorluklar ortaya çıktığı için ilkelerinizi düzenli olarak gözden geçirmeniz önemlidir.

- **[Kasa Ekler](safe-attachments.md)**: Kötü amaçlı içerik için e-posta eklerini denetleyerek mesajlaşma sisteminizi korumak için sıfır gün koruma sağlar. Virüs/kötü amaçlı yazılım imzası olmayan tüm iletileri ve ekleri özel bir ortama yönlendirir ve ardından kötü amaçlı amacı algılamak için makine öğrenmesi ve analiz tekniklerini kullanır. Şüpheli etkinlik bulunmazsa, ileti posta kutusuna iletilir. Daha fazla bilgi için bkz. [Kasa Ekler ilkelerini ayarlama](set-up-safe-attachments-policies.md).

- **[Kasa Bağlantıları](safe-links.md)**: URL'lerin tıklama zamanı doğrulaması sağlar; örneğin, e-posta iletilerinde ve Office dosyalarında. Koruma devam eder ve mesajlaşma ve Office ortamınız genelinde geçerlidir. Bağlantılar her tıklama için taranır: güvenli bağlantılar erişilebilir kalır ve kötü amaçlı bağlantılar dinamik olarak engellenir. Daha fazla bilgi için bkz. [Kasa Bağlantıları ilkelerini ayarlama](set-up-safe-links-policies.md).

- **[SharePoint, OneDrive ve Microsoft Teams için ekleri Kasa](mdo-for-spo-odb-and-teams.md)**: Ekip sitelerindeki ve belge kitaplıklarındaki kötü amaçlı dosyaları tanımlayıp engelleyerek, kullanıcılar işbirliği yaparken ve dosya paylaştığında kuruluşunuzu korur. Daha fazla bilgi edinmek için bkz[. SharePoint, OneDrive ve Microsoft Teams için Office 365 için Defender açma](turn-on-mdo-for-spo-odb-and-teams.md).

- **[Office 365 için Defender'de kimlik avı koruması](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)**: Kullanıcılarınızın ve iç veya özel etki alanlarınızın kimliğine bürünme girişimlerini algılar. Kimlik avı saldırılarını önlemeye yönelik makine öğrenmesi modellerini ve gelişmiş kimliğe bürünme algılama algoritmalarını uygular. Daha fazla bilgi için bkz. [Office 365 için Microsoft Defender'da kimlik avı önleme ilkelerini yapılandırma](configure-mdo-anti-phishing-policies.md).

## <a name="view-microsoft-defender-for-office-365-reports"></a>Office 365 için Microsoft Defender raporlarını görüntüleme

Office 365 için Microsoft Defender, Office 365 için Defender izlemek için [raporlar](view-reports-for-mdo.md) içerir. Raporlara Microsoft 365 Defender portalında <https://security.microsoft.com> **Raporlar** \> **E-posta & işbirliği** \> **E-posta & işbirliği raporları** bölümünden erişebilirsiniz. İsterseniz, kullanarak <https://security.microsoft.com/securityreports>doğrudan **E-posta ve işbirliği raporları** sayfasına gidebilirsiniz.

Raporlar gerçek zamanlı olarak güncelleştirilerek size en son içgörüleri sağlar. Bu raporlar ayrıca öneriler sağlar ve sizi yakın tehditler konusunda uyarır. Önceden tanımlanmış raporlar aşağıdakileri içerir:

- [Tehdit Gezgini (veya gerçek zamanlı algılamalar)](threat-explorer.md)
- [Tehdit koruması durum raporu](view-reports-for-mdo.md#threat-protection-status-report)
- ... ve birkaçı daha.

## <a name="use-threat-investigation-and-response-capabilities"></a>Tehdit araştırması ve yanıt özelliklerini kullanma

Office 365 için Microsoft Defender Plan 2, kuruluşunuzun güvenlik ekibinin kötü amaçlı saldırıları tahmin etmesini, anlamasını ve engellemesini sağlayan sınıfının en iyisi [tehdit araştırmasını ve yanıt araçlarını](office-365-ti.md) içerir.

- **[Tehdit izleyicileri](threat-trackers.md)** , geçerli siber güvenlik sorunlarıyla ilgili en son bilgileri sağlar. Örneğin, en son kötü amaçlı yazılım hakkındaki bilgileri görüntüleyebilir ve kuruluşunuz için gerçek bir tehdit haline gelmeden önce karşı önlemler alabilirsiniz. Kullanılabilir izleyiciler [arasında Dikkat çekici izleyiciler](threat-trackers.md#noteworthy-trackers), [Popüler izleyiciler](threat-trackers.md#trending-trackers), [İzlenen sorgular](threat-trackers.md#tracked-queries) ve [Kaydedilen sorgular](threat-trackers.md#saved-queries) bulunur.

- **[Tehdit Gezgini (veya gerçek zamanlı algılamalar)](threat-explorer.md)** (Gezgin olarak da adlandırılır) son tehditleri tanımlamanıza ve analiz etmenizi sağlayan gerçek zamanlı bir rapordur. Gezgin'i özel dönemlere ait verileri gösterecek şekilde yapılandırabilirsiniz.

- **[Saldırı simülasyonu eğitimi](attack-simulation-training.md)** , kuruluşunuzda güvenlik açıklarını tanımlamak için gerçekçi saldırı senaryoları çalıştırmanızı sağlar. Zıpkınla kimlik avı kimlik bilgileri toplama ve ek saldırıları, parola spreyi ve deneme yanılma parola saldırıları dahil olmak üzere mevcut saldırı türlerinin simülasyonları mevcuttur.

## <a name="save-time-with-automated-investigation-and-response"></a>Otomatik araştırma ve yanıt ile zaman kazanın

(**YENİ!**) Olası bir siber saldırıyı araştırırken, zaman esastır. Tehditleri ne kadar erken tanımlayıp hafifletebilirseniz kuruluşunuz o kadar iyi olur. [Otomatik araştırma ve yanıt](office-365-air.md) (AIR) özellikleri, bir uyarı tetiklendiğinde veya Gezgin'deki bir görünümde olduğu gibi el ile otomatik olarak başlatilebilen bir dizi güvenlik playbook'u içerir. AIR, güvenlik operasyonları ekibinize tehditleri etkili ve verimli bir şekilde azaltmaya yönelik zaman ve çaba tasarrufu sağlayabilir. Daha fazla bilgi için bkz. [Office 365'da AIR](office-365-air.md).

## <a name="permissions-required-to-use-microsoft-defender-for-office-365-features"></a>Office 365 için Microsoft Defender özelliklerini kullanmak için gereken izinler

Office 365 için Microsoft Defender özelliklere erişmek için size uygun bir rol atanmalıdır. Aşağıdaki tabloda bazı örnekler verilmiştir:

|Rol veya rol grubu|Daha fazla bilgi edinmek için kaynaklar|
|---|---|
|genel yönetici (Kuruluş Yönetimi)|Bu rolü Azure Active Directory veya Microsoft 365 Defender portalında atayabilirsiniz. Daha fazla bilgi için bkz. [Microsoft 365 Defender portalında İzinler](permissions-microsoft-365-security-center.md).|
|Güvenlik Yöneticisi|Bu rolü Azure Active Directory veya Microsoft 365 Defender portalında atayabilirsiniz. Daha fazla bilgi için bkz. [Microsoft 365 Defender portalında İzinler](permissions-microsoft-365-security-center.md).|
|Exchange Online'da Kuruluş Yönetimi|[Exchange Online'de izinler](/exchange/permissions-exo/permissions-exo) <p> [PowerShell'i Exchange Online](/powershell/exchange/exchange-online-powershell)|
|Arama ve Temizleme|Bu rol yalnızca Microsoft 365 Defender portalında veya Microsoft Purview uyumluluk portalında kullanılabilir. Daha fazla bilgi için bkz. [Microsoft 365 Defender portalındaki](permissions-microsoft-365-security-center.md) [İzinler ve Microsoft Purview uyumluluk portalındaki İzinler](../../compliance/microsoft-365-compliance-center-permissions.md).|
|||

## <a name="get-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender alma

Office 365 için Microsoft Defender Microsoft 365 E5, Office 365 E5, Office 365 A5 ve Microsoft 365 İş Ekstra gibi belirli aboneliklere dahildir. Aboneliğiniz Office 365 için Defender içermiyorsa, Office 365 için Defender Plan 1 veya Office 365 için Defender Plan 2'yi belirli aboneliklere eklenti olarak satın alabilirsiniz. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- Office 365 için Defender planları içeren aboneliklerin listesi için [kullanılabilirliği](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#office-365-advanced-threat-protection-atp-availability) Office 365 için Microsoft Defender.

- Plan 1 ve 2'ye dahil edilen özelliklerin listesi için [Office 365 için Microsoft Defender planlarında özellik kullanılabilirliği](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability-across-advanced-threat-protection-atp-plans).

- Planları karşılaştırmak ve Office 365 için Defender satın almak için [doğru Office 365 için Microsoft Defender alın](https://products.office.com/exchange/advance-threat-protection#pmg-allup-content).

- [Ücretsiz deneme başlatın](https://go.microsoft.com/fwlink/p/?LinkID=698279)

## <a name="new-features-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'deki yeni özellikler

Office 365 için Microsoft Defender sürekli olarak yeni özellikler eklenir. Daha fazla bilgi edinmek için aşağıdaki kaynaklara bakın:

- [Microsoft 365 Yol Haritası](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=Microsoft%2CDefender%2Cfor%2COffice%2C365), geliştirme ve dağıtım aşamasındaki yeni özelliklerin bir listesini sağlar.

- [Office 365 için Microsoft Defender Hizmet Açıklaması](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#whats-new-in-office-365-advanced-threat-protection-atp), Office 365 için Defender planlardaki özellikleri ve kullanılabilirliği açıklar.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)
- [Microsoft 365 Defender'de otomatik araştırma ve yanıt (AIR)](../defender/m365d-autoir.md)
