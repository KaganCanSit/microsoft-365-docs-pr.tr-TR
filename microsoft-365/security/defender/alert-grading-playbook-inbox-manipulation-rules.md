---
title: Şüpheli gelen kutusu işleme kuralları için uyarı notlama
description: Uyarıları gözden geçirmek ve saldırıyı düzeltmek ve ağın korunması için önerilen eylemleri yapmak için şüpheli gelen kutusu işleme kurallarına uyarı notlama.
keywords: olaylar, uyarılar, araştırma, çözümleme, yanıt, korelasyon, saldırı, makineler, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, microsoft, m365
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
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: 89d068feb5051a72e7592b7ea365b2e253e35115
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63325985"
---
# <a name="alert-grading-for-suspicious-inbox-manipulation-rules"></a>Şüpheli gelen kutusu işleme kuralları için uyarı notlama

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Tehditle tehdit, kullanıcının gelen kutusunda e-postaları okuma, e-postaları dış hesaplara iletme, izlemeleri silme ve kimlik avı postaları gönderme gibi birçok kötü amaçlı amaçlı kullanıcı hesaplarını kullanabilir. İş e-posta güvenliği (BEC) ve kimlik avı kampanyaları sırasında kötü amaçlı gelen kutusu kuralları yaygındır ve bunları tutarlı bir şekilde izlemek önemlidir. 

Bu çalışma kitabı, saldırganlar tarafından yapılandırılan şüpheli gelen kutusu işleme kurallarıyla ilgili herhangi bir olayı araştırmanıza ve saldırıyı düzeltmek ve ağnızı korumak için önerilen eylemler uygulamanıza yardımcı olur. Bu çalışma kitabı, güvenlik işlemleri merkezi (SOC) analistleri ve uyarıları gözden geçiren, ince alan ve not alan IT yöneticileri de dahil olmak üzere güvenlik ekiplerine yöneliktir. Uyarıları hızlı bir şekilde Doğru Pozitif (TP) veya Hatalı Pozitif (TP) olarak sınıflandırabilirsiniz ve saldırıyı düzeltmek için TP uyarıları için önerilen eylemleri gerçekleştirin. 

Bu playbook'un kullanımı sonuçları:

- Gelen kutusu işleme kurallarıyla ilişkilendirilmiş uyarıları kötü amaçlı (TP) veya skp (FP) etkinlikleri olarak belirlediniz.

  Kötü amaçlı ise, kötü amaçlı gelen kutusu işleme kurallarını kaldırılmış demektir.

- E-postalar kötü amaçlı bir e-posta adresine iletirse gerekli eylemi benimseyebilirsiniz.

## <a name="inbox-manipulation-rules"></a>Gelen kutusu işleme kuralları

Gelen kutusu kuralları, önceden tanımlanmış ölçütlere göre e-posta iletilerini otomatik olarak yönetecek şekilde ayarlanır. Örneğin, yöneticinizden gelen tüm iletileri başka bir klasöre taşımak veya gelen iletileri başka bir e-posta adresine iletecek bir gelen kutusu kuralı oluşturabilirsiniz.

### <a name="malicious-inbox-manipulation-rules"></a>Kötü amaçlı gelen kutusu işleme kuralları

Saldırganlar, kötü amaçlı etkinliklerini kullanıcıdan gizlemek üzere güvenliği tehlikeye konan kullanıcı posta kutusunda gelen e-postaları gizlemek için e-posta kuralları ayarlamış olabilir. Ayrıca güvenliği tehlikeye atılmış kullanıcı posta kutusunda e-postaları silmek, e-postaları daha az fark edilebilir bir klasöre (RSS gibi) taşımak veya postalarınızı bir dış hesaba iletmek için de kurallar ayarlanabilir. Bazı kurallar tüm e-postaları başka bir klasöre taşımak ve bunları "okundu" olarak işaretlemek için, bazı kurallar ise yalnızca e-posta iletisinde veya konu iletisinde belirli anahtar sözcükleri içeren postaları hareket ettirebilirsiniz. 

Örneğin, gelen kutusu kuralı "fatura", "kimlik avı", "yanıt vermedi", "şüpheli e-posta" veya "istenmeyen posta" gibi anahtar sözcükleri başkaları arasında arama yapacak şekilde ayarlanmış olabilir ve bunları bir dış e-posta hesabına taşı. Saldırganlar ayrıca güvenliği tehlikeye atılmış kullanıcı posta kutusunu istenmeyen posta, kimlik avı e-postaları veya kötü amaçlı yazılım dağıtmak için de kullanabilir. 

## <a name="workflow"></a>İş Akışı

İşte, şüpheli gelen kutusu işleme kuralı etkinliklerini belirlemeye yönelik iş akışı.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-workflow.png" alt-text="Gelen kutusu işleme kuralları için uyarı soruşturma iş akışı" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-workflow.png":::


## <a name="investigation-steps"></a>İnceleme adımları

Bu bölüm, olayı yanıtlamaya ve organizasyonlarınızı daha fazla saldırıya karşı korumak için önerilen adımları atılacak ayrıntılı adım adım kılavuzu içerir.

### <a name="1-review-the-alerts"></a>1. Uyarıları gözden geçirme

İşte, uyarı kuyruğunda gelen kutusu işleme kuralı uyarısı örneği.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-queue.png" alt-text="Gelen kutusu işleme kuralı örneği" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-queue.png":::

İşte, kötü amaçlı gelen kutusu işleme kuralı tarafından tetiklenen uyarının ayrıntılarına bir örnek.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-description.png" alt-text="Kötü amaçlı gelen kutusu işleme kuralı tarafından tetiklenen uyarının ayrıntıları" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-description.png":::


### <a name="2-investigate-inbox-manipulation-rule-parameters"></a>2. Gelen kutusu işleme kuralı parametrelerini araştır 

Kuralların aşağıdaki kural parametrelerine veya ölçütlerine göre şüpheli olup olmadığını belirleme:

- Anahtar Sözcükler

   Saldırgan, işleme kuralını yalnızca belirli sözcükleri içeren e-postalara uygulayabilir. Bu anahtar sözcükleri, şu tür öznitelikler altında bulabilirsiniz: "BodyContainsWords", "SubjectContainsWords" veya "SubjectOrContainsWords". 

   Anahtar sözcüklere göre filtre uygulama varsa, o zaman anahtar sözcüklerin size şüpheli görünip görünmeyip şüpheli olmadığını kontrol edin (yaygın senaryolar, "kimlik avı", "istenmeyen posta", "yanıt vermedik" gibi saldırgan etkinlikleriyle ilgili e-postaları filtrelemektir).

   Hiç filtre yoksa, bu da şüpheli olabilir.

- Hedef klasör

   Güvenlik algılamayı kaldırmak için, saldırgan e-postaları daha az fark edilebilir bir klasöre hareket ettirebilir ve e-postaları okundu olarak işaretlenebilir (örneğin, "RSS" klasörü). Saldırgan "MoveToFolder" ve "MarkAsRead" eylemlerini uygularsa, hedef klasörün bir şekilde kuralda yer alan anahtar sözcüklerle ilgili olup olmadığını kontrol edin ve şüpheli görünür mü yoksa şüpheli mi olduğuna karar verin. 

- Hepsini sil

   Bazı saldırganlar etkinliklerini gizlemek için gelen tüm e-postaları silebilir. Çoğunlukla, anahtar sözcüklerle filtrelemeden "tüm gelen e-postaları sil" kuralı kötü amaçlı etkinliklerin bir göstergesidir. 
 
Burada, ilgili olay günlüğünün "tüm gelen e-postaları sil" kural yapılandırmasına (RawEventData.Parameters'de olduğu gibi) bir örnek verilmektedir. 

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-delete-log.png" alt-text="Tüm gelen e-posta kuralı yapılandırmasını silme örneği" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-delete-log.png":::


### <a name="3-investigate-the-ip-address"></a>3. IP adresini araştır

Kural oluşturmayla ilgili olayı gerçekleştiren IP adresinin özniteliklerini gözden geçirme:

- Kiracıda aynı IP'den kaynaklanan diğer şüpheli bulut etkinliklerini arama. Örneğin, şüpheli etkinlikler birden fazla başarısız oturum açma girişimi olabilir. 
- ISS, bu kullanıcı için yaygın ve mantıklı mı?
- Konum, bu kullanıcı için genel ve mantıklı mı?

### <a name="4-investigate-suspicious-activity-by-the-user-prior-to-creating-the-rules"></a>4. Kuralları oluşturmadan önce kullanıcının şüpheli etkinliğini araştırma

Kurallar oluşturulmadan önce tüm kullanıcı etkinliklerini gözden geçirmeyi, ödün göstergelerini denetlemeyi ve şüpheli görünen kullanıcı eylemlerini araştırabilirsiniz. 

Örneğin, birden çok başarısız oturum açma işlemi için şunları incele: 

- Oturum açma etkinliği 

   Kural oluşturmadan önce oturum açma etkinliğinin şüpheli olmadığını doğrulama. (ortak konum / ISS / kullanıcı-aracısı). 

- Uyarılar

   Kuralları oluşturmadan önce kullanıcının uyarı almış olup olmadığını kontrol edin. Bu, kullanıcı hesabının güvenliği ihlal edilmiş olabileceğini gösteriyor olabilir. Örneğin, olanaksız seyahat uyarısı, sık kullanılmayan bir ülke, birkaç başarısız oturum açma gibi.)

- Olay

   Uyarının, bir olayı gösteren diğer uyarılarla ilişkilendirilip ilişkilendirilip ilişkilendiril olmadığını kontrol edin. Öyleyse, olayın başka pozitif uyarılar içerdiğini kontrol edin.

## <a name="advanced-hunting-queries"></a>Gelişmiş arama sorguları

[Gelişmiş Av](advanced-hunting-overview.md) , ağ'daki etkinlikleri incelemenize ve tehdit göstergelerini bulamanıza olanak sağlayan sorgu tabanlı bir tehdit arama aracıdır. 

Belirli bir zaman penceresi sırasında tüm yeni gelen kutusu kuralı olaylarını bulmak için bu sorguyu kullanın.  

```kusto
let start_date = now(-10h); 
let end_date = now();
let user_id = ""; // enter here the user id
CloudAppEvents
| where Timestamp between (start_date .. end_date)
| where AccountObjectId == user_id
| where Application == @"Microsoft Exchange Online"
| where ActionType in ("Set-Mailbox", "New-InboxRule", "Set-InboxRule") //set new inbox rule related operations
| project Timestamp, ActionType, CountryCode, City, ISP, IPAddress, RuleConfig = RawEventData.Parameters, RawEventData
```

*RuleConfig sütunu* yeni gelen kutusu kuralı yapılandırmasını sağlar.

Kullanıcının geçmişine bakarak ISS'nin kullanıcı için ortak olup olmadığını kontrol etmek için bu sorguyu kullanın.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 60d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by ISP 
```

Kullanıcının geçmişine bakarak, ülkenin kullanıcı için ortak olup olmadığını kontrol etmek üzere bu sorguyu kullanın.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 60d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by CountryCode
```

Kullanıcı geçmişine bakarak kullanıcı aracısının kullanıcı için ortak olup olmadığını kontrol etmek için bu sorguyu kullanın.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 60d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by UserAgent
```

## <a name="recommended-actions"></a>Önerilen eylemler

1. Kötü amaçlı gelen kutusu kuralını devre dışı bırakma.
2. Kullanıcı hesabının kimlik bilgilerini sıfırlayın. Ayrıca, Bulut Uygulamaları için Microsoft Defender'la kullanıcı hesabının güvenliğinin ihlal edilmiş olup olduğunu doğruabilirsiniz ve bu da Azure Active Directory (Azure AD) Identity Protection'dan güvenlik sinyallerini alır.
3. Etkiyi alan kullanıcı hesabı tarafından gerçekleştirilen diğer kötü amaçlı etkinlikleri arama.
4. Güvenliği tehlikeye atılmış diğer kullanıcı hesaplarını bulmak için, kiracıda aynı IP'den veya aynı ISS'den (ISS az görülen) gelen diğer şüpheli etkinlikleri bulun.

## <a name="see-also"></a>Ayrıca bkz.

- [Uyarı notlamaya genel bakış](alert-grading-playbooks.md)
- [Şüpheli e-posta iletme etkinliği](alert-grading-playbook-email-forwarding.md)
- [Şüpheli gelen kutusu iletme kuralları](alert-grading-playbook-inbox-forwarding-rules.md)
- [Uyarıları araştırma](investigate-alerts.md)
