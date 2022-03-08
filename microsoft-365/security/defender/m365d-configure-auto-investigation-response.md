---
title: Ekip içinde otomatik araştırma ve yanıt özelliklerini Microsoft 365 Defender
description: Yeni ekiplerde otomatik araştırmayı ve yanıtları kendi kendine Microsoft 365 Defender
search.appverid: MET150
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
f1.keywords: CSH
ms.technology: m365d
ms.openlocfilehash: 4ec06a96e345345560a2714fa7e23d91a6f5832f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314228"
---
# <a name="configure-automated-investigation-and-response-capabilities-in-microsoft-365-defender"></a>Ekip içinde otomatik araştırma ve yanıt özelliklerini Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Microsoft 365 Defender, güvenlik [işlemleri ekibinizi çok zaman](m365d-autoir.md) ve çabadan tasarruf edeyleyen güçlü otomatik soruşturma ve yanıt özellikleri içerir. Kendi [kendine güvenen](m365d-autoir.md#how-automated-investigation-and-self-healing-works) bu özellikler, güvenlik analisti tarafından tehditleri araştırmak ve bunlara yanıt vermek için atılacak adımları taklit ediyor, ancak daha hızlı ve ölçeklendirebilme olanağı daha yüksek.

Bu makalede, aşağıdaki adımlarla iş yerinde otomatik araştırma ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> yapılandırıldığı açıklanmıştır:

1. [Önkoşulları gözden geçirin](#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender).
2. [Cihaz gruplarının otomasyon düzeyini gözden geçirme veya değiştirme](#review-or-change-the-automation-level-for-device-groups).
3. [E-posta ve güvenlik ilkelerinizi gözden Office 365](#review-your-security-and-alert-policies-in-office-365).
4. [Bu Microsoft 365 Defender açık olduğundan emin olun](#make-sure-microsoft-365-defender-is-turned-on).

Daha sonra tüm ayarlamaları gerçekleştirdikten sonra İşlem merkezinde [düzeltme eylemlerini görüntüp yönetsiniz](m365d-autoir-actions.md).

## <a name="prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender"></a>Bir ekipte otomatik araştırma ve yanıt için önkoşullar Microsoft 365 Defender

<br>

****

|Gereksinim|Ayrıntılar|
|---|---|
|Abonelik gereksinimleri|Bu aboneliklerden biri: <ul><li>Microsoft 365 E5</li><li>Microsoft 365 A5</li><li>Microsoft 365 E3 Microsoft 365 E5 Güvenlik ile birlikte</li><li>Microsoft 365 A3 güvenlik Microsoft 365 A5 ile birlikte</li><li>Office 365 E5 artı Enterprise Mobility + Security E5 artı Windows E5</li></ul> <p> Lisans [Microsoft 365 Defender bkz](./prerequisites.md#licensing-requirements).|
|Ağ gereksinimleri|<ul><li>[Kimlik için Microsoft Defender etkin](/azure-advanced-threat-protection/what-is-atp)</li><li>[Yapılandırılmış Bulut Uygulamaları için Microsoft Defender](/cloud-app-security/what-is-cloud-app-security)</li><li>[Identity tümleştirmesi için Microsoft Defender](/cloud-app-security/mdi-integration)</li></ul>|
|Windows gereksinimlerini karşıla|<ul><li>Windows 11</li><li>Windows 10, sürüm 1709 veya sonraki bir sürümü yükleme (Bkz[. Windows sürüm bilgileri](/windows/release-information/))</li><li>Aşağıdaki tehdit koruma hizmetleri yapılandırılmıştır:<ul><li>[Uç Nokta için Microsoft Defender](../defender-endpoint/configure-endpoints.md)</li><li>[Microsoft Defender Virüsten Koruma](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features)</li></ul></li></ul>|
|E-posta içeriği ve dosya Office koruma|[Yapılandırılmış bir Office 365 Için Microsoft Defender](/microsoft-365/security/office-365-security/defender-for-office-365#configure-atp-policies)|
|İzinler|Otomatik araştırma ve yanıt özelliklerini yapılandırmak için, genel yönetici () veya Azure Active Directory içinde () veya bu kuruluşta (<https://portal.azure.com> ) Genel Yönetici veya Güvenlik Yöneticisi Microsoft 365 yönetim merkezi.<https://admin.microsoft.com> <p> Otomatik soruşturma ve bekleyen eylemleri gözden geçirme, onaylama veya reddetme gibi yanıt özellikleriyle çalışmak için gereken izinleri almak için bkz. İşlem merkezi görevleri için [gerekli izinler](m365d-action-center.md#required-permissions-for-action-center-tasks).|
|

## <a name="review-or-change-the-automation-level-for-device-groups"></a>Cihaz gruplarının otomasyon düzeyini gözden geçirme veya değiştirme

Otomatik soruşturmaların çalıştırıp çalışmama ve düzeltme eylemlerinin otomatik olarak mı yoksa yalnızca cihazlarınız için onay üzerine mi alınıp alınmayacak, kuruluşun cihaz grup ilkeleri gibi bazı ayarlara bağlıdır. Cihaz grubu ilkeleriniz için yapılandırılmış otomasyon düzeyini gözden geçirme.

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.

2. İzinler **altında Ayarlar** >  **EndpointsDevice** >  **grupları'ne** **gidin**.

3. Cihaz grubu ilkelerinizi gözden geçirme. Özellikle Otomasyon düzeyi **sütununa bakın** . Tam - otomatik **olarak tehditleri düzeltmek için Tam (Tam) kullanmalarını öneririz**.  Istediğiniz otomasyon düzeyini elde etmek için cihaz gruplarınızı oluşturmanız veya düzenlemeniz gerekiyor olabilir. Bu görevle ilgili yardım almak için aşağıdaki makalelere bakın:
   - [Tehditlerin düzeltmesi](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations#how-threats-are-remediated)
   - [Cihaz grupları oluşturma ve yönetme](/windows/security/threat-protection/microsoft-defender-atp/machine-groups)

## <a name="review-your-security-and-alert-policies-in-office-365"></a>E-postada güvenlik ve uyarı ilkelerinizi Office 365

Microsoft, belirli riskleri [belirlemeye yardımcı](../../compliance/alert-policies.md) olan yerleşik uyarı ilkeleri sağlar. Bu riskler arasında Exchange izinlerinin kötüye kullanımı, kötü amaçlı yazılım etkinliği, olası dış ve iç tehditlere ve bilgi yönetimi risklerine yer ve riski vardır. Bazı uyarılar, [e-postada otomatik araştırma ve Office 365](../office-365-security/office-365-air.md). Yeni özellik için [Defender'Office 365](../office-365-security/defender-for-office-365.md) doğru yapılandırıldığından emin olun.

Bazı uyarılar ve güvenlik ilkeleri otomatik soruşturmaları tetikleyse de, *e-posta ve içerik için otomatik olarak hiçbir düzeltme eylemi gerçekleştir alınmaz*. Bunun yerine, İşlem merkezinde güvenlik işlemleri ekibinin e-posta ve e-posta içeriği için tüm düzeltme eylemleri [onay bekliyor](m365d-action-center.md).

E-postanın Office 365 içeriğinin korunmasına yardımcı olacak güvenlik ayarları. Bu ayarları görüntülemek veya değiştirmek için Tehditlere karşı koruma [makalesinde yer alan yönergeleri izleyin](../office-365-security/protect-against-threats.md).

1. Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portalında İlkeler</a> ve **Kurallar & ilkeleri'ne** \> **gidin**.

2. Aşağıdaki ilkelerin hepsinin yapılandırıldığından emin olun. Yardım ve öneriler almak için bkz. [Tehditlere karşı koruma](/microsoft-365/security/office-365-security/protect-against-threats).
   - [Kötü amaçlı yazılımdan koruma](../office-365-security/protect-against-threats.md#part-1---anti-malware-protection-in-eop)
   - [Kimlik avı önleme](../office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
   - [Kasa Ekleri Kaydetme](../office-365-security/protect-against-threats.md#safe-attachments-policies-in-microsoft-defender-for-office-365)
   - [Güvenli Bağlantılar](../office-365-security/protect-against-threats.md#safe-links-policies-in-microsoft-defender-for-office-365)
   - [İstenmeyen posta önleme](../office-365-security/protect-against-threats.md#part-3---anti-spam-protection-in-eop)

3. [E-Kasa, SharePoint OneDrive için eklerin Microsoft Teams](../office-365-security/mdo-for-spo-odb-and-teams.md) açık olduğundan emin olun.

4. Tüm iş [yeriz için Sıfır saatlik otomatik temizleme (ZAP) Exchange Online](../office-365-security/zero-hour-auto-purge.md) emin olun.

5. (Bu adım isteğe bağlıdır.) İlke [Office 365 uyarı ilkelerinizi](../../compliance/alert-policies.md) gözden Microsoft 365 uyumluluk merkezi.[https://compliance.microsoft.com/compliancepolicies](https://compliance.microsoft.com/compliancepolicies) Çeşitli varsayılan uyarı ilkeleri Tehdit yönetimi kategorisinde yer almaktadır. Bu uyarılardan bazıları otomatik araştırmayı ve yanıtı tetikler. Daha fazla bilgi edinmek için Varsayılan [uyarı ilkeleri'ne bakın](../../compliance/alert-policies.md#default-alert-policies).

## <a name="make-sure-microsoft-365-defender-is-turned-on"></a>Microsoft 365 Defender'in açık olduğundan emin olun

:::image type="content" source="../../media/mtp-enable/mtp-on.png" alt-text="Etkinleştirmenin etkin olduğundan Microsoft 365 Defender emin olun." lightbox="../../media/mtp-enable/mtp-on.png":::

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalında oturum açma</a>

2. Gezinti bölmesinde, önceki resimde **gösterildiği gibi & Uyarıları****,** Ekinlik **ve İşlem** merkezini kullanarak Olaylar'ı seçin.
   - UyarıLarda **, & ve İşlem merkezinde** **Olaylar'i görüyorsanız** Microsoft 365 Defender açık demektir. Bu [makalenin Cihaz grupları için otomasyon düzeyini gözden geçirme veya](#review-or-change-the-automation-level-for-device-groups) değiştirme bölümüne bakın.
   - Olaylar, *İşlem* merkezi **veya Avlama'Microsoft 365 Defender** Veya Arama'ya bağlı olarak görmüyorsanız, bu Microsoft 365 Defender açık değildir.  Bu durumda İşlem [merkezini ziyaret edin](m365d-action-center.md).

> [!TIP]
> Yardıma mı ihtiyacınız var? Bkz[. E-Microsoft 365 Defender](m365d-enable.md).

## <a name="next-steps"></a>Sonraki adımlar

- [Düzeltme eylemleri Microsoft 365 Defender](m365d-remediation-actions.md)
- [İşlem merkezini ziyaret edin](m365d-action-center.md)
