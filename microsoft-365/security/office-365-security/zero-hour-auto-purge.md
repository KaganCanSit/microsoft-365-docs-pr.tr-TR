---
title: Office 365 için Microsoft Defender'de sıfır saatlik otomatik temizleme
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MBS150
- MET150
ms.assetid: 96deb75f-64e8-4c10-b570-84c99c674e15
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Sıfır saatlik otomatik temizleme (ZAP), Exchange Online posta kutusundaki teslim edilen iletileri gereksiz e-posta klasörüne veya istenmeyen posta, kimlik avı veya teslimden sonra kötü amaçlı yazılım içeren karantinaya alır.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bd9bb3f231e42c625c87669417210281d1d5a3df
ms.sourcegitcommit: a8fbaf4b441b5325004f7a2dacd9429ec9d80534
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2022
ms.locfileid: "65739471"
---
# <a name="zero-hour-auto-purge-zap-in-exchange-online"></a>Exchange Online'de sıfır saatlik otomatik temizleme (ZAP)

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

## <a name="zero-hour-auto-purge-zap-basics"></a>Sıfır saatlik otomatik temizleme (ZAP) temel bilgileri

Exchange Online'da posta kutuları olan Microsoft 365 kuruluşlarda, sıfır saat otomatik temizleme (ZAP), Exchange Online posta kutularına zaten teslim edilmiş kötü amaçlı kimlik avı, istenmeyen posta veya kötü amaçlı yazılım iletilerini geçmişe dönük olarak algılayan ve etkisiz hale getiren bir e-posta koruma özelliğidir.

ZAP, şirket içi Exchange posta kutularını koruyan tek başına Exchange Online Protection (EOP) ortamlarında çalışmaz.

## <a name="how-zap-works"></a>ZAP nasıl çalışır?

İstenmeyen posta ve kötü amaçlı yazılım imzaları hizmette gerçek zamanlı olarak günlük olarak güncelleştirilir. Ancak kullanıcılar, içeriğin kullanıcılara teslim edildikten sonra silah haline getirilip getirilmediğini de içeren çeşitli nedenlerle kötü amaçlı iletiler almaya devam edebilir. ZAP, hizmetteki istenmeyen posta ve kötü amaçlı yazılım imzalarına yönelik güncelleştirmeleri sürekli izleyerek bu sorunu giderir. ZAP, kullanıcının posta kutusunda zaten bulunan iletileri bulabilir ve kaldırabilir.

ZAP eylemi kullanıcı için sorunsuzdur; bir ileti algılandığında ve taşındığında bildirim gönderilmez.

[Kasa gönderen listeleri](create-safe-sender-lists-in-office-365.md), posta akışı kuralları (taşıma kuralları olarak da bilinir), Gelen Kutusu kuralları veya ek filtreler ZAP'a göre önceliklidir. Posta akışında gerçekleşenlere benzer şekilde, hizmet teslim edilen iletinin ZAP'a ihtiyacı olduğunu belirlese bile, iletinin güvenilir gönderenler yapılandırması nedeniyle üzerinde işlem yapılmadığı anlamına gelir. Bu, iletileri filtrelemeyi atlayacak şekilde yapılandırma konusunda dikkatli olmak için başka bir nedendir.

Office 365 için Microsoft Defender'da ZAP'ın e-postadaki tehditleri otomatik olarak nasıl algılayıp etkisiz hale getirildiğini öğrenmek için bu kısa videoyu izleyin. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGrLg]

### <a name="zero-hour-auto-purge-zap-for-malware"></a>Kötü amaçlı yazılım için sıfır saatlik otomatik temizleme (ZAP)

Teslimden sonra kötü amaçlı yazılım içerdiği bulunan **okunmuş veya okunmamış iletiler** için ZAP, kötü amaçlı yazılım ekini içeren iletiyi karantinaya alır. Varsayılan olarak, karantinaya alınan kötü amaçlı yazılım iletilerini yalnızca yöneticiler görüntüleyebilir ve yönetebilir. Ancak yöneticiler, kullanıcıların kötü amaçlı yazılım olarak _karantinaya_ alınan iletilere ne yapmalarına izin verildiğini tanımlamak için karantina ilkeleri oluşturabilir ve kullanabilir. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md).

Kötü amaçlı yazılımdan koruma ilkelerinde kötü amaçlı yazılımlara yönelik ZAP varsayılan olarak etkindir. Daha fazla bilgi için bkz. [EOP'de kötü amaçlı yazılımdan koruma ilkelerini yapılandırma](configure-anti-malware-policies.md).

### <a name="zero-hour-auto-purge-zap-for-phishing"></a>Kimlik avı için sıfır saatlik otomatik temizleme (ZAP)

Teslimden sonra kimlik avı olarak tanımlanan **okunmuş veya okunmamış iletiler** için ZAP sonucu, geçerli istenmeyen posta önleme ilkesinde **kimlik avı e-posta** filtreleme kararı için yapılandırılan eyleme bağlıdır. Kimlik avı için kullanılabilir filtreleme kararı eylemleri ve olası ZAP sonuçları aşağıdaki listede açıklanmıştır:

- **Metin içeren X-Header**, **Prepend konu satırı** ekleme, **İletiyi e-posta adresine yeniden yönlendirme**, **İletiyi silme**: ZAP ileti üzerinde hiçbir işlem gerçekleştirmez.

- **İletiyi Gereksiz E-posta'ya taşıma**: ZAP, iletiyi Gereksiz E-posta klasörüne taşır. Daha fazla bilgi için bkz[. Microsoft 365'da Exchange Online posta kutularında gereksiz e-posta ayarlarını yapılandırma](configure-junk-email-settings-on-exo-mailboxes.md).

- **Karantina iletisi**: ZAP, iletiyi karantinaya alır.

Varsayılan olarak, kimlik avı için ZAP istenmeyen posta önleme ilkelerinde etkinleştirilir ve **Kimlik avı e-posta** filtreleme kararının varsayılan eylemi **Karantina iletisidir**; bu da kimlik avı için ZAP'in iletiyi varsayılan olarak karantinaya aldığı anlamına gelir.

İstenmeyen posta filtreleme kararlarını yapılandırma hakkında daha fazla bilgi için bkz[. Microsoft 365'da istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

### <a name="zero-hour-auto-purge-zap-for-high-confidence-phishing"></a>Yüksek güvenilirlikli kimlik avı için sıfır saatlik otomatik temizleme (ZAP)

Teslimden sonra yüksek güvenilirlikli kimlik avı olarak tanımlanan **okunmuş veya okunmamış iletiler** için ZAP, iletiyi karantinaya alır. Varsayılan olarak, karantinaya alınan yüksek güvenilirlikli kimlik avı iletilerini yalnızca yöneticiler görüntüleyebilir ve yönetebilir. Ancak yöneticiler, kullanıcıların yüksek güvenilirlikli kimlik avı olarak _karantinaya_ alınan iletilere neler yapabileceğini tanımlamak için karantina ilkeleri oluşturabilir ve kullanabilir. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md)

Yüksek güvenilirlikli kimlik avı için ZAP varsayılan olarak etkindir. Daha fazla bilgi için bkz[. Office 365'da Varsayılan Olarak Güvenli](secure-by-default.md).

### <a name="zero-hour-auto-purge-zap-for-spam"></a>İstenmeyen postalar için sıfır saatlik otomatik temizleme (ZAP)

Teslimden sonra istenmeyen posta olarak tanımlanan **okunmamış iletiler** için ZAP sonucu, ilgili istenmeyen posta önleme ilkesindeki **İstenmeyen posta** filtreleme kararı için yapılandırılan eyleme bağlıdır. İstenmeyen postalar ve olası ZAP sonuçları için kullanılabilir filtreleme kararı eylemleri aşağıdaki listede açıklanmıştır:

- **Metin içeren X-Header**, **Prepend konu satırı** ekleme, **İletiyi e-posta adresine yeniden yönlendirme**, **İletiyi silme**: ZAP ileti üzerinde hiçbir işlem gerçekleştirmez.

- **İletiyi Gereksiz E-posta'ya taşıma**: ZAP, iletiyi Gereksiz E-posta klasörüne taşır. Daha fazla bilgi için bkz[. Microsoft 365'da Exchange Online posta kutularında gereksiz e-posta ayarlarını yapılandırma](configure-junk-email-settings-on-exo-mailboxes.md).

- **Karantina iletisi**: ZAP, iletiyi karantinaya alır. Varsayılan olarak, son kullanıcılar alıcı oldukları durumlarda karantinaya alınan istenmeyen posta iletilerini görüntüleyebilir ve yönetebilir. Ancak yöneticiler, _kullanıcıların istenmeyen posta olarak karantinaya_ alınan iletilere ne yapmalarına izin verildiğini tanımlamak için karantina ilkeleri oluşturabilir ve kullanabilir. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md)

İstenmeyen posta önleme ilkelerinde istenmeyen posta ZAP varsayılan olarak etkindir ve **İstenmeyen posta** filtreleme kararının varsayılan eylemi **İletiyi Gereksiz E-posta klasörüne taşı'dır**; bu da istenmeyen posta ZAP'sinin **okunmamış** iletileri varsayılan olarak Gereksiz E-posta klasörüne taşıması anlamına gelir.

İstenmeyen posta filtreleme kararlarını yapılandırma hakkında daha fazla bilgi için bkz[. Microsoft 365'da istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

### <a name="zero-hour-auto-purge-zap-considerations-for-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender için sıfır saatlik otomatik temizleme (ZAP) konuları

ZAP, Kasa Ekler ilkesi taramasında [Dinamik Teslim](safe-attachments.md#dynamic-delivery-in-safe-attachments-policies) sürecinde olan veya EOP kötü amaçlı yazılım filtrelemesinin eki **Zaten Kötü Amaçlı Yazılım Uyarısı Text.txt** dosyasıyla değiştirdiği hiçbir iletiyi karantinaya almayacaktır. Bu tür iletiler için kimlik avı veya istenmeyen posta sinyali alınırsa ve istenmeyen posta önleme ilkesindeki filtreleme kararı iletide bazı eylemler gerçekleştirecek şekilde ayarlanırsa (Gereksiz Öğeye Taşı, Yeniden Yönlendir, Sil veya Karantinaya Al) ZAP varsayılan olarak bir 'Gereksize Taşı' eylemine ayarlanır.

## <a name="how-to-see-if-zap-moved-your-message"></a>ZAP'ın iletinizi taşıyıp taşımadığını görme

ZAP'ın iletinizi taşıyıp taşımadığını belirlemek için aşağıdaki seçeneklere sahipsiniz:

- **İleti sayısı**: Belirtilen tarih aralığı için ZAP'ı etkileyen iletilerin sayısını görmek için [Posta akışı durum raporundaki Posta Akışı görünümünü](view-email-security-reports.md#mailflow-view-for-the-mailflow-status-report) kullanın.
- **İleti ayrıntıları**: **Tüm e-posta** olaylarını **Ek eylem** sütunu için **ZAP** değerine göre filtrelemek için [Tehdit Gezgini'ni (ve gerçek zamanlı algılamaları)](threat-explorer.md) kullanın.

> [!NOTE]
> ZAP, Exchange posta kutusu denetim günlüklerine sistem eylemi olarak kaydedilmez.

## <a name="zero-hour-auto-purge-zap-faq"></a>Sıfır saatlik otomatik temizleme (ZAP) SSS

### <a name="what-happens-if-a-legitimate-message-is-moved-to-the-junk-email-folder"></a>Geçerli bir ileti Gereksiz E-posta klasörüne taşınırsa ne olur?

[Hatalı pozitifler](report-junk-email-messages-to-microsoft.md) için normal raporlama işlemini izlemeniz gerekir. İletinin Gelen Kutusu'ndan Gereksiz E-posta klasörüne taşınmasının tek nedeni hizmetin iletinin istenmeyen posta veya kötü amaçlı olduğunu belirlemesi olabilir.

### <a name="what-if-i-use-the-quarantine-folder-instead-of-the-junk-mail-folder"></a>Gereksiz Posta klasörü yerine Karantina klasörünü kullanırsam ne olur?

ZAP, bu makalenin önceki bölümlerinde açıklandığı gibi istenmeyen posta önleme ilkelerinizin yapılandırmasına bağlı olarak bir ileti üzerinde işlem gerçekleştirir.

### <a name="what-if-im-using-safe-senders-mail-flow-rules-or-allowedblocked-sender-lists"></a>Güvenilir gönderenler, posta akışı kuralları veya izin verilen/engellenen gönderen listeleri kullanıyorsam ne olur?

Kasa gönderenler, posta akışı kuralları veya kuruluş ayarlarını engelleme ve izin verme önceliklidir. Hizmet, yapılandırdığınız işlemi gerçekleştirdiğinden bu iletiler ZAP'ın dışında tutulur. Bu, iletileri filtrelemeyi atlayacak şekilde yapılandırma konusunda dikkatli olmak için başka bir nedendir.

### <a name="what-are-the-licensing-requirements-for-zero-hour-auto-purge-zap-to-work"></a>Sıfır saatlik otomatik temizlemenin (ZAP) çalışması için lisans gereksinimleri nelerdir?

Lisanslarda herhangi bir sınırlama yoktur. ZAP, Exchange çevrimiçi ortamda barındırılan tüm posta kutularında çalışır. ZAP, şirket içi Exchange posta kutularını koruyan tek başına Exchange Online Protection (EOP) ortamlarında çalışmaz.

### <a name="what-if-a-message-is-moved-to-another-folder-eg-inbox-rules"></a>İleti başka bir klasöre taşınırsa (örneğin, Gelen Kutusu kuralları) ne olur?

Sıfır saatlik otomatik temizleme, ileti silinmediği veya aynı veya daha güçlü olduğu sürece eylem henüz uygulanmadığı sürece çalışmaya devam eder. Örneğin, kimlik avı önleme ilkesi karantinaya alınmışsa ve ileti zaten Gereksiz E-posta'daysa, ZAP iletiyi karantinaya almak için işlem yapacaktır.

### <a name="how-does-zap-affect-mailboxes-on-hold"></a>ZAP beklemedeki posta kutularını nasıl etkiler?

Sıfır saatlik otomatik temizleme, beklemedeki posta kutularından gelen iletileri karantinaya alır. ZAP, istenmeyen posta önleme ilkelerinde istenmeyen posta veya kimlik avı kararı için yapılandırılan eyleme bağlı olarak iletileri Gereksiz E-posta klasörüne taşıyabilir.

Exchange Online ayrı tutmalar hakkında daha fazla bilgi için bkz. [Yerinde Saklama ve Exchange Online'de Dava Tutma](/Exchange/security-and-compliance/in-place-and-litigation-holds).
