---
title: Microsoft 365 Defender'de otomatik araştırma ve yanıt özelliklerini yapılandırma
description: Microsoft 365 Defender'de otomatik araştırmayı ve yanıtı kendi kendine düzeltme ile yapılandırma
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
ms.openlocfilehash: 51efeb57c6670f9c798fa254bb0a6242b30c5700
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64944381"
---
# <a name="configure-automated-investigation-and-response-capabilities-in-microsoft-365-defender"></a>Microsoft 365 Defender'de otomatik araştırma ve yanıt özelliklerini yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Microsoft 365 Defender, güvenlik operasyonları ekibinize çok zaman ve çaba kazandırabilecek güçlü [otomatik araştırma ve yanıt özellikleri](m365d-autoir.md) içerir. [Kendi kendini iyileştiren](m365d-autoir.md#how-automated-investigation-and-self-healing-works) bu özellikler, bir güvenlik analistinin tehditleri araştırmak ve yanıtlamak için atacağı adımları taklit eder, yalnızca daha hızlı ve daha fazla ölçeklendirme yeteneği sunar.

Bu makalede, aşağıdaki adımlarla <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender'da</a> otomatik araştırma ve yanıtın nasıl yapılandırıldığı açıklanır:

1. [Önkoşulları gözden geçirin](#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender).
2. [Cihaz grupları için otomasyon düzeyini gözden geçirin veya değiştirin](#review-or-change-the-automation-level-for-device-groups).
3. [Office 365'da güvenlik ve uyarı ilkelerinizi gözden geçirin](#review-your-security-and-alert-policies-in-office-365).
4. [Microsoft 365 Defender açık olduğundan emin olun](#make-sure-microsoft-365-defender-is-turned-on).

Ardından, kurulumu tamamladıktan sonra, [düzeltme eylemlerini İşlem merkezinde görüntüleyebilir ve yönetebilirsiniz](m365d-autoir-actions.md).

## <a name="prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender"></a>Microsoft 365 Defender'de otomatik araştırma ve yanıt önkoşulları

<br>

****

|Gereksinim|Ayrıntılar|
|---|---|
|Abonelik gereksinimleri|Şu aboneliklerden biri: <ul><li>Microsoft 365 E5</li><li>Microsoft 365 A5</li><li>Microsoft 365 E5 Güvenlik eklentisiyle Microsoft 365 E3</li><li>Microsoft 365 A5 Güvenliği eklentisiyle Microsoft 365 A3</li><li>Office 365 E5 artı Enterprise Mobility + Security E5 artı Windows E5</li></ul> <p> Bkz. [lisanslama gereksinimleri Microsoft 365 Defender](./prerequisites.md#licensing-requirements).|
|Ağ gereksinimleri|<ul><li>[Kimlik için Microsoft Defender](/azure-advanced-threat-protection/what-is-atp) etkin</li><li>[Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security) yapılandırıldı</li><li>[Kimlik için Microsoft Defender tümleştirmesi](/cloud-app-security/mdi-integration)</li></ul>|
|cihaz gereksinimlerini Windows|<ul><li>Windows 11</li><li>Windows 10, sürüm 1709 veya üzeri yüklü ([Windows sürüm bilgilerine](/windows/release-information/) bakın)</li><li>Yapılandırılan aşağıdaki tehdit koruma hizmetleri:<ul><li>[Uç Nokta için Microsoft Defender](../defender-endpoint/configure-endpoints.md)</li><li>[Microsoft Defender Virüsten Koruma](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features)</li></ul></li></ul>|
|E-posta içeriği ve Office dosyaları için koruma|[Office 365 için Microsoft Defender](/microsoft-365/security/office-365-security/defender-for-office-365#configure-atp-policies) yapılandırıldı|
|İzinler|Otomatik araştırma ve yanıt özelliklerini yapılandırmak için, Azure Active Directory () veya Microsoft 365 yönetim merkezi (<https://portal.azure.com><https://admin.microsoft.com>) içinde Genel Yönetici veya Güvenlik Yöneticisi rolü atanmış olmalıdır. <p> Bekleyen eylemleri gözden geçirme, onaylama veya reddetme gibi otomatik araştırma ve yanıt özellikleriyle çalışmak için gereken izinleri almak için bkz. [İşlem merkezi görevleri için gerekli izinler](m365d-action-center.md#required-permissions-for-action-center-tasks).|
|

## <a name="review-or-change-the-automation-level-for-device-groups"></a>Cihaz grupları için otomasyon düzeyini gözden geçirme veya değiştirme

Otomatik araştırmaların çalıştırılıp çalıştırılmadığı ve düzeltme eylemlerinin otomatik olarak mı yoksa yalnızca cihazlarınız için onaylandığında mı gerçekleştirildiği kuruluşunuzun cihaz grubu ilkeleri gibi belirli ayarlara bağlıdır. Cihaz grubu ilkeleriniz için yapılandırılmış otomasyon düzeyini gözden geçirin.

1. Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com)) gidin ve oturum açın.

2. **İzinler** altında **Ayarlar** >  **EndpointsCihaz** >  **grupları'na** gidin.

3. Cihaz grubu ilkelerinizi gözden geçirin. Özellikle **Otomasyon düzeyi** sütununa bakın. **Tam - tehditleri otomatik olarak düzeltmenizi** öneririz.  İstediğiniz otomasyon düzeyini elde etmek için cihaz gruplarınızı oluşturmanız veya düzenlemeniz gerekebilir. Bu görevle ilgili yardım almak için aşağıdaki makalelere bakın:
   - [Tehditler nasıl düzeltilir?](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations#how-threats-are-remediated)
   - [Cihaz grupları oluşturun ve yönetin](/windows/security/threat-protection/microsoft-defender-atp/machine-groups)

## <a name="review-your-security-and-alert-policies-in-office-365"></a>Office 365'da güvenlik ve uyarı ilkelerinizi gözden geçirin

Microsoft, belirli riskleri tanımlamaya yardımcı olan yerleşik [uyarı ilkeleri](../../compliance/alert-policies.md) sağlar. Bu riskler Exchange yönetici izinlerinin kötüye kullanılması, kötü amaçlı yazılım etkinliği, olası dış ve iç tehditler ve bilgi idaresi riskleridir. Bazı uyarılar [Office 365 otomatik araştırma ve yanıt](../office-365-security/office-365-air.md) tetikleyebilir. [Office 365 için Defender](../office-365-security/defender-for-office-365.md) özelliklerinizin doğru yapılandırıldığından emin olun.

Bazı uyarılar ve güvenlik ilkeleri otomatik araştırma tetikleyebilse de, *e-posta ve içerik için otomatik olarak düzeltme eylemi yapılmaz*. Bunun yerine, e-posta ve e-posta içeriği için tüm düzeltme eylemleri [, İşlem merkezinde](m365d-action-center.md) güvenlik operasyonları ekibinizin onayını bekler.

Office 365'deki güvenlik ayarları e-postanın ve içeriğin korunmasına yardımcı olur. Bu ayarları görüntülemek veya değiştirmek için [Tehditlere karşı koruma'daki](../office-365-security/protect-against-threats.md) yönergeleri izleyin.

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalında</a> **İlkeler & Kurallar** \> **Tehdit ilkeleri'ne** gidin.

2. Aşağıdaki ilkelerin tümünün yapılandırıldığından emin olun. Yardım ve öneriler almak için bkz. [Tehditlere karşı koruma](/microsoft-365/security/office-365-security/protect-against-threats).
   - [Kötü amaçlı yazılımdan koruma](../office-365-security/protect-against-threats.md#part-1---anti-malware-protection-in-eop)
   - [Kimlik avına karşı koruma](../office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
   - [Güvenli Ekleri Kaydetme](../office-365-security/protect-against-threats.md#safe-attachments-policies-in-microsoft-defender-for-office-365)
   - [Güvenli Bağlantılar](../office-365-security/protect-against-threats.md#safe-links-policies-in-microsoft-defender-for-office-365)
   - [Antispam](../office-365-security/protect-against-threats.md#part-3---anti-spam-protection-in-eop)

3. [SharePoint, OneDrive ve Microsoft Teams için Kasa Eklerinin](../office-365-security/mdo-for-spo-odb-and-teams.md) açık olduğundan emin olun.

4. [Exchange Online'de Sıfır saat otomatik temizlemenin (ZAP)](../office-365-security/zero-hour-auto-purge.md) etkin olduğundan emin olun.

5. (Bu adım isteğe bağlıdır.) Microsoft Purview uyumluluk portalında ([https://compliance.microsoft.com/compliancepolicies](https://compliance.microsoft.com/compliancepolicies) ) [Office 365 uyarı ilkelerinizi](../../compliance/alert-policies.md) gözden geçirin. Çeşitli varsayılan uyarı ilkeleri Tehdit yönetimi kategorisindedir. Bu uyarılardan bazıları otomatik araştırma ve yanıt tetikleyebilir. Daha fazla bilgi için bkz [. Varsayılan uyarı ilkeleri](../../compliance/alert-policies.md#default-alert-policies).

## <a name="make-sure-microsoft-365-defender-is-turned-on"></a>Microsoft 365 Defender açık olduğundan emin olun

:::image type="content" source="../../media/mtp-enable/mtp-on.png" alt-text="Microsoft 365 Defender açıkken Microsoft 365 Defender portalında sol gezinti bölmesi" lightbox="../../media/mtp-enable/mtp-on.png":::

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalında</a> oturum açma

2. Gezinti bölmesinde, önceki görüntüde gösterildiği gibi **Olaylar & Uyarılar**, **Tehdit Avcılığı** ve **İşlem merkezi'ni** arayın.
   - **Olaylar & Uyarılar**, **Tehdit Avcılığı** ve **İşlem merkezi** görüyorsanız Microsoft 365 Defender açıktır. Bu makalenin [Cihaz grupları için otomasyon düzeyini gözden geçirme veya değiştirme](#review-or-change-the-automation-level-for-device-groups) bölümüne bakın.
   - **Olaylar**, **İşlem merkezi** veya **Tehdit Avcılığı'nı** *görmüyorsanız* Microsoft 365 Defender açık olmayabilir. Bu durumda [İşlem merkezini ziyaret edin](m365d-action-center.md).

> [!TIP]
> Yardıma mı ihtiyacınız var? Bkz[. Microsoft 365 Defender açma](m365d-enable.md).

## <a name="next-steps"></a>Sonraki adımlar

- [Microsoft 365 Defender'de düzeltme eylemleri](m365d-remediation-actions.md)
- [İşlem merkezini ziyaret edin](m365d-action-center.md)
