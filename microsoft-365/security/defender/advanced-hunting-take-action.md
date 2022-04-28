---
title: Microsoft 365 Defender gelişmiş tehdit avcılığı sorgu sonuçları üzerinde eylem gerçekleştirme
description: Gelişmiş tehdit avcılığı sorgu sonuçlarınızdaki tehditleri ve etkilenen varlıkları hızla ele alın
keywords: gelişmiş avcılık, tehdit avcılığı, siber tehdit avcılığı, Microsoft 365 Defender, microsoft 365, m365, arama, sorgulama, telemetri, eylem gerçekleştirme
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
ms.openlocfilehash: b7fbe659902bf89023e994f4e1304f25f3934db8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097621"
---
# <a name="take-action-on-advanced-hunting-query-results"></a>Gelişmiş tehdit avcılığı sorgu sonuçları üzerinde eylem gerçekleştirme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Güçlü ve kapsamlı eylem seçeneklerini kullanarak tehditleri hızla içerebilir veya [gelişmiş tehdit avcılığında](advanced-hunting-overview.md) bulduğunuz güvenliği aşılmış varlıkları ele alabilirsiniz. Bu seçeneklerle şunları yapabilirsiniz:

- Cihazlarda çeşitli eylemler gerçekleştirme
- Dosyaları karantinaya al

## <a name="required-permissions"></a>Gerekli izinler
Gelişmiş tehdit avcılığı aracılığıyla cihazlarda işlem yapmak için, Uç Nokta için Microsoft Defender [cihazlarda düzeltme eylemleri gönderme izinlerine](/windows/security/threat-protection/microsoft-defender-atp/user-roles#permission-options) sahip bir role sahip olmanız gerekir. Eylem gerçekleştiremiyorsanız, aşağıdaki izni alma konusunda genel yöneticiye başvurun:

*Tehdit ve güvenlik açığı yönetimi > etkin düzeltme eylemleri - Düzeltme işleme*

Gelişmiş tehdit avcılığı aracılığıyla e-postalar üzerinde işlem yapmak için [e-postaları aramak ve temizlemek](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) için Office 365 için Microsoft Defender bir role sahip olmanız gerekir.

## <a name="take-various-actions-on-devices"></a>Cihazlarda çeşitli eylemler gerçekleştirme
Sorgu sonuçlarınızdaki sütun tarafından `DeviceId` tanımlanan cihazlarda aşağıdaki eylemleri gerçekleştirebilirsiniz:

- Etkilenen cihazları bulaşma içerecek şekilde yalıtma veya saldırıların yaya olarak hareket etmesini önleme
- Daha fazla adli bilgi edinmek için araştırma paketi toplama
- En son güvenlik bilgileri güncelleştirmelerini kullanarak tehditleri bulmak ve kaldırmak için virüsten koruma taraması çalıştırma
- Cihazdaki ve muhtemelen etkilenen diğer cihazlardaki tehditleri denetlemek ve düzeltmek için otomatik bir araştırma başlatın
- Uygulama yürütmeyi yalnızca Microsoft tarafından imzalanan yürütülebilir dosyalarla kısıtlayarak kötü amaçlı yazılım veya diğer güvenilmeyen yürütülebilir dosyalar aracılığıyla sonraki tehdit etkinliğini engelleyin

Bu yanıt eylemlerinin Uç Nokta için Microsoft Defender aracılığıyla nasıl gerçekleştirildiğinden daha fazla bilgi edinmek için [cihazlardaki yanıt eylemleri hakkında bilgi edinin](/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts).
   
### <a name="quarantine-files"></a>Dosyaları karantinaya al
Dosyalara *karantina* eylemini dağıtarak, karşılaşıldığında otomatik olarak karantinaya alınabilmelerini sağlayabilirsiniz. Bu eylemi seçerken, sorgunuzda hangi dosyaların karantinaya alınabileceğini belirlemek için aşağıdaki sütunlar arasında seçim yapabilirsiniz:

- `SHA1`: Çoğu gelişmiş tehdit avcılığı tablosunda, bu sütun kaydedilen eylemden etkilenen dosyanın SHA-1'ine başvurur. Örneğin, bir dosya kopyalanmışsa, etkilenen bu dosya kopyalanan dosya olacaktır.
- `InitiatingProcessSHA1`: Çoğu gelişmiş tehdit avcılığı tablosunda, bu sütun kaydedilen eylemi başlatmadan sorumlu dosyayı ifade eder. Örneğin, bir alt işlem başlatıldıysa, bu başlatıcı dosyası üst işlemin bir parçası olacaktır. 
- `SHA256`: Bu sütun, sütun tarafından tanımlanan dosyanın SHA-256 eşdeğeridir `SHA1` .
- `InitiatingProcessSHA256`: Bu sütun, sütun tarafından tanımlanan dosyanın SHA-256 eşdeğeridir `InitiatingProcessSHA1` .

Karantina eylemlerinin nasıl gerçekleştirildiği ve dosyaların nasıl geri yüklenebileceği hakkında daha fazla bilgi edinmek için [dosyalardaki yanıt eylemleri hakkında bilgi edinin](/windows/security/threat-protection/microsoft-defender-atp/respond-file-alerts).

>[!NOTE]
>Dosyaları bulmak ve karantinaya almak için, sorgu sonuçları cihaz tanımlayıcısı olarak değerleri de içermelidir `DeviceId` .  

Açıklanan eylemlerden herhangi birini yapmak için sorgu sonuçlarınızda bir veya daha fazla kayıt seçin ve ardından **Eylem gerçekleştir'i** seçin. Sihirbaz, tercih ettiğiniz eylemleri seçip gönderme işleminde size yol gösterir.

:::image type="content" source="../../media/take-action-multiple.png" alt-text="Microsoft 365 Defender portalında Eylem gerçekleştir seçeneği" lightbox="../../media/take-action-multiple.png":::


## <a name="take-various-actions-on-emails"></a>E-postalar üzerinde çeşitli eylemler gerçekleştirme
Cihaz odaklı düzeltme adımlarının dışında, sorgu sonuçlarınızdaki e-postalar üzerinde bazı eylemler de gerçekleştirebilirsiniz. Üzerinde işlem yapmak istediğiniz kayıtları seçin, **Eylem gerçekleştir'i** seçin, ardından **Eylemleri seç'in** altında aşağıdakilerden seçiminizi seçin:
- `Move to mailbox folder` - E-posta iletilerini Gereksiz, Gelen Kutusu veya Silinmiş öğeler klasörüne taşımak için bunu seçin

   :::image type="content" source="../../media/advanced-hunting-take-actions-email.png" alt-text="Microsoft 365 Defender portalında Eylem gerçekleştir seçeneği" lightbox="../../media/advanced-hunting-take-actions-email.png":::

- `Delete email` - E-posta iletilerini Silinmiş öğeler klasörüne taşımak (**Geçici silme**) veya kalıcı olarak silmek için bunu seçin (**Sabit silme**)

   :::image type="content" source="../../media/advanced-hunting-take-actions-email-del.png" alt-text="Microsoft 365 Defender portalında Eylem gerçekleştir seçeneği" lightbox="../../media/advanced-hunting-take-actions-email-del.png":::

İşlem merkezi geçmişinde kolayca izlemek için gerçekleştirilen eylemin kısa bir açıklamasını ve düzeltme adını da sağlayabilirsiniz. İşlem merkezinde bu eylemlere filtre uygulamak için Onay Kimliği'ni de kullanabilirsiniz. Bu kimlik sihirbazın sonunda sağlanır:

:::image type="content" source="../../media/choose-email-actions-entities.png" alt-text="varlıklar için eylemleri seçmeyi gösteren eylem gerçekleştirme sihirbazı" lightbox="../../media/choose-email-actions-entities.png":::

Bu e-posta eylemleri [özel algılamalar](custom-detections-overview.md) için de geçerlidir.


## <a name="review-actions-taken"></a>Gerçekleştirilen eylemleri gözden geçirme
Her eylem işlem [merkezine](m365d-action-center.md) **İşlem** **merkeziHistory** >  ([security.microsoft.com/action-center/history](https://security.microsoft.com/action-center/history)) altında tek tek kaydedilir. Her eylemin durumunu denetlemek için işlem merkezine gidin.
 
>[!NOTE]
>Bu makaledeki bazı tablolar Uç Nokta için Microsoft Defender'de kullanılamayabilir. Daha fazla veri kaynağı kullanarak tehditleri avlamak için [Microsoft 365 Defender açın](m365d-enable.md). Gelişmiş avcılık sorgularını Uç Nokta için Microsoft Defender'den geçirme bölümünde yer alan adımları izleyerek [gelişmiş avcılık iş akışlarınızı Uç Nokta için Microsoft Defender'den Microsoft 365 Defender](advanced-hunting-migrate-from-mde.md) taşıyabilirsiniz.

## <a name="related-topics"></a>İlgili konular
- [Gelişmiş avcılığa genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenin](advanced-hunting-query-language.md)
- [Sorgu sonuçlarıyla çalışın](advanced-hunting-query-results.md)
- [Şemayı anlayın](advanced-hunting-schema-tables.md)
- [İşlem merkezine genel bakış](m365d-action-center.md)
