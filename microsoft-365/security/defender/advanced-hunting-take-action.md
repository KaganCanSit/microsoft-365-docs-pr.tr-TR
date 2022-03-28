---
title: Web'de gelişmiş arama sorgusu sonuçları için Microsoft 365 Defender
description: Gelişmiş arama sorgusu sonuçlarınıza yönelik tehditlere ve etkilenen varlıklara hızlı bir şekilde neden olun
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, önlem alma
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: eb881611ad4b983eb80d028dfe3dee20c3ed6216
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754674"
---
# <a name="take-action-on-advanced-hunting-query-results"></a>Gelişmiş arama sorgusu sonuçları üzerinde eyleme geç

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Güçlü ve kapsamlı eylem seçeneklerini kullanarak gelişmiş avda bulunan [tehditlere](advanced-hunting-overview.md) hızla yer ve tehditlere karşı adres bulabilirsiniz. Bu seçeneklerle şunları yapabilirsiniz:

- Cihazlarda çeşitli eylemler gerçekleştirin
- Dosyaları karantinaya alın

## <a name="required-permissions"></a>Gerekli izinler
Gelişmiş arama yoluyla işlem yapmak için cihazlarda düzeltme eylemleri gönderme izinleri olan Uç nokta için Microsoft Defender'da [bir role sahip olmak gerekir](/windows/security/threat-protection/microsoft-defender-atp/user-roles#permission-options). Bir işlem gerçekleştire değilseniz, aşağıdaki izni almak için genel yöneticiye başvurun:

*Tehdit ve Tehdide > düzeltme eylemleri güvenlik açığı yönetimi - Düzeltme işleme*

## <a name="take-various-actions-on-devices"></a>Cihazlarda çeşitli eylemler gerçekleştirin
Sorgu sonuçları hücresinde sütun tarafından tanımlanan cihazlarda `DeviceId` aşağıdaki eylemleri gerçekleştirebilirsiniz:

- Etkilenen cihazları bulaşmak için yalıtmak veya saldırının sonradan ilerlemesini önlemek
- Daha fazla bilgi elde etmek için araştırma paketi topla
- En son güvenlik zekası güncelleştirmelerini kullanarak tehdit bulmak ve kaldırmak için virüsten koruma taraması çalıştırın
- Cihazda ve büyük olasılıkla etkilenen diğer cihazları kontrol etmek ve düzeltmek için otomatik bir araştırma başlatma
- Uygulama yürütmeyi yalnızca Microsoft imzalı yürütülebilir dosyalarla kısıtlama; kötü amaçlı yazılım veya güvenilmeyen diğer yürütülebilir dosyalar aracılığıyla sonraki tehdit etkinliğini önleme

Bu yanıt eylemlerinin Uç Nokta için Microsoft Defender aracılığıyla nasıl gerçekleştirilecekleri hakkında daha fazla bilgi edinmek için, [cihazlardaki yanıt eylemleri hakkında bilgi edinebilirsiniz](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts).
   
## <a name="quarantine-files"></a>Dosyaları karantinaya alın
Dosyalarda karantina *eylemlerini* dağıtarak, karşılaşıldıklarda otomatik olarak karantinaya alınmalarını sabilirsiniz. Bu eylemi seçerseniz, aşağıdaki sütunlar arasında seçim yapabilirsiniz ve sorgu sonuçlarınız içinde karantinaya alınacak dosyaları tanımlayabilirsiniz:

- `SHA1`: Bu sütun, gelişmiş av tablolarının çoğunda kayıtlı eylemden etkilenen dosyanın SHA-1'ini ifade eder. Örneğin, bir dosya kopyalanmışsa, etkilenen bu dosya kopyalanan dosya olur.
- `InitiatingProcessSHA1`: Gelişmiş arama tablolarının çoğunda, bu sütun kayıtlı eylemin başlatılamadan sorumlu olan dosyayı gösterir. Örneğin, bir çocuk işlemi başlatıldısa, bu başlatıcı dosyası üst işlemin bir parçası olur. 
- `SHA256`: Bu sütun, sütunda tanımlanan dosyanın SHA-256 eşdeğeridir `SHA1` .
- `InitiatingProcessSHA256`: Bu sütun, sütunda tanımlanan dosyanın SHA-256 eşdeğeridir `InitiatingProcessSHA1` .

Karantina eylemlerinin nasıl gerçekleştir alındığı ve dosyaların nasıl geri yüklenebilir olduğu hakkında daha fazla bilgi edinmek için, [dosyalarda yanıt eylemleri makalesini okuyun](/windows/security/threat-protection/microsoft-defender-atp/respond-file-alerts).

>[!NOTE]
>Dosyaları bulmak ve karantinaya almak için, sorgu sonuçları cihaz tanımlayıcıları `DeviceId` olarak değerleri de içermeli.  

## <a name="take-action"></a>Harekete geç
Açıklanan eylemlerin herhangi birini yapmak için, sorgu sonuçlarınıza bir veya birden çok kayıt seçin ve sonra da Eylemleri **gerçekleştir'i seçin**. Tercih ettiğiniz eylemleri seçme ve sonra gönderme işlemi boyunca bir sihirbaz size yol sağlar.

:::image type="content" source="../../media/take-action-multiple.png" alt-text="Web portalında Eylemlere Microsoft 365 Defender seçeneği" lightbox="../../media/take-action-multiple.png":::

## <a name="review-actions-taken"></a>Yapılan eylemleri gözden geçirme
Her eylem, ayrı ayrı İşlem merkeziHistory (Tarih **)** >  **altında** [işlem merkezine security.microsoft.com/action-center/history](https://security.microsoft.com/action-center/history).[](m365d-action-center.md) Her eylemin durumunu kontrol etmek için işlem merkezine gidin.
 
>[!NOTE]
>Bu makaledeki bazı tablolar Uç Nokta için Microsoft Defender'da kullanılamıyor olabilir. [Daha fazla Microsoft 365 Defender](m365d-enable.md) kullanarak tehdit yakalamak için çok daha fazla kaynağı açabilirsiniz. Gelişmiş av iş akışlarınızı Uç Nokta için Microsoft Defender'dan Microsoft 365 Defender için [Microsoft Defender'dan gelişmiş arama sorgularını geçirme makalesinde](advanced-hunting-migrate-from-mde.md) yer alan adımları takip edebilirsiniz.

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenin](advanced-hunting-query-language.md)
- [Sorgu sonuçlarıyla çalışın](advanced-hunting-query-results.md)
- [Şemayı anlayın](advanced-hunting-schema-tables.md)
- [İşlem merkezine genel bakış](m365d-action-center.md)
