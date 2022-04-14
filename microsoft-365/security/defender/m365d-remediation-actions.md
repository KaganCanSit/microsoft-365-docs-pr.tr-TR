---
title: Microsoft 365 Defender'de düzeltme eylemleri
description: Microsoft 365 Defender'de otomatik araştırmalardan sonra kullanılabilecek düzeltme eylemlerine genel bakış elde edin
keywords: otomatik, araştırma, uyarı, tetikleyici, eylem, düzeltme
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.custom: autoir
ms.reviewer: evaldm, isco
ms.technology: m365d
ms.openlocfilehash: 5605678a1fcc30719d7f838a16452ba527c554b7
ms.sourcegitcommit: a7e1d155939e862337271fbe38bf26f62bd49bdd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/14/2022
ms.locfileid: "64847059"
---
# <a name="remediation-actions-in-microsoft-365-defender"></a>Microsoft 365 Defender'de düzeltme eylemleri

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- Microsoft 365 Defender

Microsoft 365 Defender'da otomatik bir araştırma sırasında ve sonrasında, kötü amaçlı veya şüpheli öğeler için düzeltme eylemleri tanımlanır. Uç nokta olarak da adlandırılan cihazlarda bazı düzeltme eylemleri gerçekleştirilen işlemlerdir. Kimlikler, hesaplar ve e-posta içeriğinde diğer düzeltme eylemleri gerçekleştirilen işlemlerdir. Düzeltme eylemleri alındıktan, onaylandıktan veya reddedildikten sonra otomatik araştırmalar tamamlanmıştır.

> [!IMPORTANT]
> Düzeltme eylemlerinin otomatik olarak mı yoksa yalnızca onay üzerine mi gerçekleştirildiği otomasyon düzeyleri gibi belirli ayarlara bağlıdır. Daha fazla bilgi edinmek için aşağıdaki makalelere bakın:
>
> - [Microsoft 365 Defender'de otomatik araştırma ve yanıt özelliklerinizi yapılandırma](m365d-configure-auto-investigation-response.md)
> - [Kimlik için Microsoft Defender'de eylem hesaplarını yapılandırma](/defender-for-identity/manage-action-accounts)
> - [Cihazlarda tehditler nasıl düzeltilir?](../defender-endpoint/automated-investigations.md)
> - [E-posta & işbirliği içeriğindeki tehditler ve düzeltme eylemleri](../office-365-security/air-remediation-actions.md#threats-and-remediation-actions)

Aşağıdaki tabloda, şu anda Microsoft 365 Defender'de desteklenen düzeltme eylemleri özetlenmektedir.

|Cihaz (uç nokta) düzeltme eylemleri  |E-posta düzeltme eylemleri  |Kullanıcılar (hesaplar)  |
|:---------|:---------|----------|
|- Araştırma paketini toplama <br/>- Cihazı yalıt (bu eylem geri alınabilir)<br/>- Çıkarma makinesi <br/>- Sürüm kodu yürütme <br/>- Karantinadan serbest bırakma <br/>- İstek örneği <br/>- Kod yürütmeyi kısıtla (bu eylem geri alınabilir) <br/>- Virüsten koruma taraması çalıştırma <br/>- Durdurma ve karantinaya al      |- URL'yi engelle (tıklama zamanı)<br/>- E-posta iletilerini veya kümelerini geçici silme<br/>- Karantina e-postası<br/>- E-posta eklerini karantinaya alma<br/>- Dış posta iletmeyi kapatma          |- Kullanıcıyı devre dışı bırakma<br />- Kullanıcı parolasını sıfırlama<br />- Kullanıcının güvenliğinin aşıldığını onaylayın          |

Onay bekleniyor veya zaten tamamlandı olsun düzeltme eylemleri [İşlem merkezinde](m365d-action-center.md) görüntülenebilir.

## <a name="remediation-actions-that-follow-automated-investigations"></a>Otomatik araştırmalardan sonra gelen düzeltme eylemleri

Otomatik bir araştırma tamamlandığında, ilgili her kanıt için bir karara ulaşılır. Karara bağlı olarak düzeltme eylemleri tanımlanır. Bazı durumlarda düzeltme eylemleri otomatik olarak gerçekleştirilen; diğer durumlarda düzeltme eylemleri onay bekler. Her şey [otomatik araştırma ve yanıtın nasıl yapılandırıldığına](m365d-configure-auto-investigation-response.md) bağlıdır.

Aşağıdaki tabloda olası karar ve sonuçlar listelemektedir:

| Karar    | Etkilenen varlıklar    | Sonuç -ları|
|------|------|------|
| Kötü amaçlı    | Cihazlar (uç noktalar)    | Düzeltme eylemleri otomatik olarak yapılır (kuruluşunuzun [cihaz gruplarının](m365d-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups) Tam olarak ayarlandığı varsayılarak **- tehditleri otomatik olarak düzeltin**)|
| Tehlikeye | Kullanıcılar | Düzeltme eylemleri otomatik olarak gerçekleştirilen |
| Kötü amaçlı    | E-posta içeriği (URL'ler veya ekler) | Önerilen düzeltme eylemleri onay bekliyor|
| Şüpheli    | Cihazlar veya e-posta içeriği | Önerilen düzeltme eylemleri onay bekliyor|
| Tehdit bulunamadı    | Cihazlar veya e-posta içeriği    | Hiçbir düzeltme eylemi gerekmez|

## <a name="remediation-actions-that-are-taken-manually"></a>El ile gerçekleştirilen düzeltme eylemleri

Otomatik araştırmalardan sonra kullanılabilecek düzeltme eylemlerine ek olarak, güvenlik operasyonları ekibiniz belirli düzeltme eylemlerini el ile gerçekleştirebilir. Bunlar şunları içerir:

- Cihaz yalıtımı veya dosya karantinası gibi el ile cihaz eylemi
- E-posta iletilerini geçici silme gibi el ile e-posta eylemi
- Kullanıcı parolasını devre dışı bırakma veya sıfırlama gibi el ile kullanıcı eylemi
- Cihazlarda, kullanıcılarda veya e-postada [gelişmiş tehdit avcılığı](../defender-endpoint/advanced-hunting-overview.md) eylemi
- E-postayı gereksiz e-postaya taşıma, e-postayı geçici silme veya e-postayı sabit silme gibi e-posta içeriğinde [Gezgin](../office-365-security/threat-explorer.md) eylemi
- Bir dosyayı silme, işlemi durdurma ve zamanlanmış görevi kaldırma gibi el ile [canlı yanıt](/windows/security/threat-protection/microsoft-defender-atp/live-response) eylemi
- Cihazı yalıtma, virüsten koruma taraması çalıştırma ve dosya hakkında bilgi alma gibi [Uç Nokta için Microsoft Defender API'leriyle](../defender-endpoint/management-apis.md#microsoft-defender-for-endpoint-apis) canlı yanıt eylemi

## <a name="next-steps"></a>Sonraki adımlar

- [İşlem merkezini ziyaret edin](m365d-action-center.md)
- [Düzeltme eylemlerini görüntüleyin ve yönetin](m365d-autoir-actions.md)
- [Hatalı pozitif sonuçları veya hatalı negatifleri ele alın](m365d-autoir-report-false-positives-negatives.md)
