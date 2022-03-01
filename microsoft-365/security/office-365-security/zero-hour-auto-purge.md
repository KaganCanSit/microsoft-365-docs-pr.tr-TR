---
title: Office 365 için Microsoft Defender'da sıfır saatlik otomatik Office 365
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
description: Sıfır saatlik otomatik temizleme (ZAP) bir Exchange Online posta kutusunda bulunan teslim edilen iletileri istenmeyen posta, kimlik avı veya teslimden sonra kötü amaçlı yazılım içeren karantinaya taşır.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a48f5eb1d45af16ab275c16d2965dc9a578d9312
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "63010157"
---
# <a name="zero-hour-auto-purge-zap-in-exchange-online"></a>Exchange Online'te sıfır saatlik otomatik temizleme (ZAP)

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

## <a name="zero-hour-auto-purge-zap-basics"></a>Sıfır saatlik otomatik temizleme (ZAP) temel bilgileri

Exchange Online'ta posta kutuları olan Microsoft 365 kuruluşlarına, sıfır saatlik otomatik temizleme (ZAP), önceden Exchange Online posta kutularına teslim edilen kötü amaçlı kimlik avı, istenmeyen posta veya kötü amaçlı yazılım iletilerini geriye dönük olarak algılayan ve devre dışı olarak algılayan bir e-posta koruması özelliğidir.

ZAP, şirket içi veya Exchange Online Protection posta kutularını koruyan tek başına Exchange ortamlarında çalışmıyor.

## <a name="how-zap-works"></a>ZAP nasıl çalışır?

İstenmeyen posta ve kötü amaçlı yazılım imzaları hizmette gerçek zamanlı olarak günlük olarak güncelleştirilir. Bununla birlikte, kullanıcılar kullanıcılara teslim edildikten sonra içeriğin teslim edildikten sonra yine de olması gibi çeşitli nedenlerle kötü amaçlı iletileri almaya devam ediyor. ZAP, hizmette istenmeyen posta ve kötü amaçlı yazılım imzalarında yapılan güncelleştirmeleri sürekli olarak izerek bu sorunu gidermektedir. ZAP, kullanıcının posta kutusunda zaten olan iletileri bulabilir ve kaldırabilir.

ZAP eylemi kullanıcı için sorunsuz olur; ileti algılandığında ve taşındığında bu iletiyle ilgili bir iletiyle ilgili olarak bu iletiye haber velanmaz.

[Kasa listeleri, posta](create-safe-sender-lists-in-office-365.md) akış kuralları (aktarım kuralları olarak da bilinir), Gelen Kutusu kuralları veya ek filtreler ZAP'den önce gelir. Posta akışında yapılana benzer şekilde, hizmet teslim edilen iletinin ZAP gerektiğini belirlerse bile, güvenli gönderenlerin yapılandırması nedeniyle ileti üzerinde eyleme geç olmaz. Bu, iletileri filtrelemeyi at edecek şekilde yapılandırma konusunda dikkatli olmak için bir başka nedendir.

### <a name="zero-hour-auto-purge-zap-for-malware"></a>Kötü amaçlı yazılım için sıfır saatlik otomatik temizleme (ZAP)

**Teslimden sonra kötü amaçlı yazılım** içerdiği bulunan okundu veya okunmadı iletileri için, ZAP kötü amaçlı yazılım ekin bulunduğu iletiyi karantinaya alır. Varsayılan olarak, karantinaya alınmış kötü amaçlı yazılım iletilerini yalnızca yöneticiler  görüntüp yönetebilir. Ancak yöneticiler, kullanıcılara kötü amaçlı yazılım olarak _karantinaya_ alınmış iletilerde ne yapma izni verilmiyorsa, karantina ilkeleri oluşturabilir ve kullanabilir. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).

Kötü amaçlı yazılımdan koruma ilkelerde kötü amaçlı yazılım için ZAP varsayılan olarak etkindir. Daha fazla bilgi için bkz. [EOP'de kötü amaçlı yazılımdan koruma ilkelerini yapılandırma](configure-anti-malware-policies.md).

### <a name="zero-hour-auto-purge-zap-for-phishing"></a>Kimlik avı için sıfır saatlik otomatik temizleme (ZAP)

**Teslimden** sonra kimlik avı olarak tanımlanan okundu veya okunmamış iletiler için ZAP sonucu, ilgili istenmeyen posta önleme ilkesinde Kimlik avı e-posta filtreleme  kararı için yapılandırılan eyleme bağlıdır. Kimlik avı için kullanılabilir filtreleme karar eylemleri ve bunların olası ZAP sonuçları aşağıdaki listede açıklanmıştır:

- **X Üstbilgisi Ekle**, **Konu satırına** metin **ekle,** İletiyi e-posta adresine **yönlendir,** İletiyi sil: ZAP ileti üzerinde hiçbir eylem atz.

- **İletiyi Gereksiz E-posta'ya** taşı: ZAP iletiyi Gereksiz E-posta klasörüne taşır. Daha fazla bilgi için bkz[. Posta kutularında veya posta Exchange Online gereksiz e-posta Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **İletiyi karantinaya** alın: ZAP iletiyi karantinaya alır.

Varsayılan olarak, kimlik avı için ZAP istenmeyen posta önleme ilkelerde etkindir ve Kimlik avı e-posta filtreleme  kararının varsayılan eylemi Karantina iletisidir; yani kimlik avı için ZAP varsayılan olarak iletiyi karantinaya alır.

İstenmeyen posta filtreleme kararlarını yapılandırma hakkında daha fazla bilgi için bkz. Gelişmiş [Sistem'de istenmeyen posta ilkelerini Microsoft 365](configure-your-spam-filter-policies.md).

### <a name="zero-hour-auto-purge-zap-for-high-confidence-phishing"></a>Yüksek güveni olan kimlik avı için sıfır saatlik otomatik temizleme (ZAP)

**Teslimden sonra yüksek güven güveni** olan kimlik avı olarak tanımlanan okundu veya okunmamış iletiler için, ZAP iletiyi karantinaya alır. Varsayılan olarak, karantinaya alınan yüksek güvene sahip kimlik avı iletilerini yalnızca yöneticiler sınr ve yönetebilir. Ancak yöneticiler, kullanıcıların yüksek güvenlikli kimlik  avı olarak karantinaya alınmış iletilerde ne yapmalarına izin verilmiyor olarak karantina ilkelerini oluşturabilir ve kullanabilir. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md)

Yüksek güvenlikli kimlik avı için ZAP varsayılan olarak etkinleştirilmiştir. Daha fazla bilgi için bkz[. Office 365](secure-by-default.md).

### <a name="zero-hour-auto-purge-zap-for-spam"></a>İstenmeyen posta için sıfır saatlik otomatik temizleme (ZAP)

**Teslimden** sonra istenmeyen posta olarak tanımlanan okunmamış iletiler için ZAP sonucu, ilgili istenmeyen posta önleme ilkesinde İstenmeyen posta filtreleme kararı  için yapılandırılan eyleme bağlıdır. İstenmeyen posta için kullanılabilir filtreleme karar eylemleri ve bunların olası ZAP sonuçları aşağıdaki listede açıklanmıştır:

- **X Üstbilgisi Ekle**, **Konu satırına** metin **ekle,** İletiyi e-posta adresine **yönlendir,** İletiyi sil: ZAP ileti üzerinde hiçbir eylem atz.

- **İletiyi Gereksiz E-posta'ya** taşı: ZAP iletiyi Gereksiz E-posta klasörüne taşır. Daha fazla bilgi için bkz[. Posta kutularında veya posta Exchange Online gereksiz e-posta Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **İletiyi karantinaya** alın: ZAP iletiyi karantinaya alır. Varsayılan olarak, son kullanıcılar alıcısı olan istenmeyen posta karantinasına alınmış iletileri iletiyi sınar ve yönetebilir. Ancak yöneticiler, kullanıcıların istenmeyen posta olarak _karantinaya_ alınmış iletilerde neler yapmalarına izin verilmiyorsa, karantina ilkeleri oluşturabilir ve kullanabilir. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md)

Varsayılan olarak, istenmeyen posta ZAP istenmeyen posta önleme ilkelerde etkindir ve İstenmeyen posta filtreleme  kararının varsayılan eylemi İletiyi Gereksiz E-posta klasörüne taşıdır **; bu** da, istenmeyen posta ZAP'ın okunmamış iletileri varsayılan olarak Gereksiz E-posta klasörüne taşı olduğu anlamına gelir.

İstenmeyen posta filtreleme kararlarını yapılandırma hakkında daha fazla bilgi için bkz. Gelişmiş [Sistem'de istenmeyen posta ilkelerini Microsoft 365](configure-your-spam-filter-policies.md).

### <a name="zero-hour-auto-purge-zap-considerations-for-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'da sıfır saatlik otomatik temizleme (ZAP) Office 365

ZAP, Kasa Ekleri ilkesinde tarama sırasındaki Dinamik Teslim sırasındaki veya EOP kötü amaçlı yazılım filtrelemenin eki zaten Kötü Amaçlı Yazılım Uyarısı Text.txtdeğiştir olduğu iletilerden birini **karantinaya Text.txt**.[](safe-attachments.md#dynamic-delivery-in-safe-attachments-policies) Bu tür iletiler için kimlik avı veya istenmeyen posta sinyali alınırsa ve istenmeyen posta önleme ilkesinde filtreleme kararı bir eyleme yönelik olarak ayarlanırsa (Gereksiz'e Taşı, Yeniden Yönlendir, Sil veya Karantinaya Taşı) zap varsayılan olarak bir 'Gereksiz'e Taşı' eylemine ayarlar.

## <a name="how-to-see-if-zap-moved-your-message"></a>ZAP'ın iletinizi taşıdıklarını görme

ZAP'in iletinizi taşıdı olup olmadığını belirlemek için aşağıdaki seçenekleriniz vardır:

- **İleti sayısı**: Belirtilen tarih aralığı [](view-email-security-reports.md#mailflow-view-for-the-mailflow-status-report) için ZAP'den etkilenen iletilerin sayısını görmek için Posta Akışı durumu raporuna posta akışı görünümünü kullanın.
- **İleti ayrıntıları**: [Tüm e-posta olaylarını](threat-explorer.md) Ek eylem sütunu için ZAP değerine  göre filtrelemek için **Threat** Explorer 'ı (ve gerçek zamanlı **algılamaları**) kullanın.

**Not**: ZAP, posta kutusu denetim günlüklerinde Exchange eylemi olarak günlüğe kaydedilmez.

## <a name="zero-hour-auto-purge-zap-faq"></a>Sıfır saatlik otomatik temizleme (ZAP) SSS

### <a name="what-happens-if-a-legitimate-message-is-moved-to-the-junk-email-folder"></a>Geçerli bir ileti Gereksiz E-posta klasörüne taşınırsa ne olur?

Hatalı pozitif sonuçlar için normal raporlama işlemini [izleyelisiniz](report-junk-email-messages-to-microsoft.md). İletinin Gelen Kutusu'dan Gereksiz E-posta klasörüne taşınma nedeni hizmetin iletinin istenmeyen posta veya kötü amaçlı olduğunu belirlediğinden olabilir.

### <a name="what-if-i-use-the-quarantine-folder-instead-of-the-junk-mail-folder"></a>Gereksiz Posta klasörü yerine Karantina klasörünü kullanırsanız ne olur?

ZAP, bir iletide, bu makalenin önceki sürümlerinde açıklandığı gibi istenmeyen posta önleme ilkelerinizin yapılandırmasına bağlı olarak işlem gösterir.

### <a name="what-if-im-using-safe-senders-mail-flow-rules-or-allowedblocked-sender-lists"></a>Güvenilir gönderenler, posta akış kuralları veya izin verilen/engellenen gönderenler listelerini kullanıyorum?

Kasa gönderenleri, posta akış kurallarını engelp kurumsal ayarları engelleme ve buna izin verme. Hizmet, yapmak üzere yapılandırmış olduğunu yaptığı için bu iletiler ZAP'den çıkarılacaktır. Bu, iletileri filtrelemeyi at edecek şekilde yapılandırma konusunda dikkatli olmak için bir başka nedendir.

### <a name="what-are-the-licensing-requirements-for-zero-hour-auto-purge-zap-to-work"></a>Sıfır saatlik otomatik temizleme (ZAP) için lisans gereksinimleri nelerdir?

Lisanslarda sınırlama yoktur. ZAP, çevrimiçi bir alanda barındırılan tüm posta Exchange çalışır. ZAP, şirket içi veya Exchange Online Protection posta kutularını koruyan tek başına Exchange ortamlarında çalışmıyor.

### <a name="what-if-a-message-is-moved-to-another-folder-eg-inbox-rules"></a>İleti başka bir klasöre taşınırsa (örn. Gelen Kutusu kuralları) ne olur?

Sıfır saatlik otomatik temizleme, ileti silinmemiş ya da aynı ya da daha güçlü olduğu sürece eylem henüz uygulanmamış olduğu sürece çalışır. Örneğin, kimlik avı önleme ilkesi karantinaya alınacak şekilde ayarlanmışsa ve ileti zaten Gereksiz E-posta'da ise, ZAP iletiyi karantinaya almak için bir işlem alır.

### <a name="how-does-zap-affect-mailboxes-on-hold"></a>ZAP, basılı posta kutularını nasıl etkiler?

Sıfır saatlik otomatik temizleme, iletileri tutulan posta kutularından karantinaya asın. ZAP, istenmeyen posta veya kimlik avı kararı için yapılandırılan eyleme bağlı olarak iletileri Gereksiz E-posta klasörüne taşıyabiliyor.

Aynı anda tutma hakkında daha fazla Exchange Online için bkz. Aynı Anda Yerinde Tutma ve [Exchange Online](/Exchange/security-and-compliance/in-place-and-litigation-holds).
