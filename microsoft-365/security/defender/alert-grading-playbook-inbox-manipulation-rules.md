---
title: Şüpheli gelen kutusu işleme kuralları için uyarı notlama
description: Uyarıları gözden geçirmek ve saldırıyı düzeltmek ve ağınızı korumak için önerilen eylemleri uygulamak için şüpheli gelen kutusu işleme kuralları için uyarı notlama.
keywords: olaylar, uyarılar, araştırma, analiz etme, yanıt, bağıntı, saldırı, makineler, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, Microsoft, m365
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
ms.openlocfilehash: e663d02037633599b9dffc19e1ebbd174aa279e1
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663192"
---
# <a name="alert-grading-for-suspicious-inbox-manipulation-rules"></a>Şüpheli gelen kutusu işleme kuralları için uyarı notlama

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- Microsoft 365 Defender

Tehdit aktörleri, bir kullanıcının gelen kutusundaki e-postaları okuma, e-postaları dış hesaplara iletmek için gelen kutusu kuralları oluşturma, izlemeleri silme ve kimlik avı postaları gönderme gibi birçok kötü amaçlı amaçla güvenliği aşılmış kullanıcı hesaplarını kullanabilir. Kötü amaçlı gelen kutusu kuralları, iş e-posta güvenliğinin aşılması (BEC) ve kimlik avı kampanyaları sırasında yaygındır ve bunları tutarlı bir şekilde izlemek önemlidir.

Bu playbook, saldırganlar tarafından yapılandırılan şüpheli gelen kutusu işleme kurallarıyla ilgili tüm olayları araştırmanıza ve saldırıyı düzeltmek ve ağınızı korumak için önerilen eylemleri gerçekleştirmenize yardımcı olur. Bu playbook, güvenlik operasyonları merkezi (SOC) analistleri ve uyarıları inceleyen, araştıran ve not veren BT yöneticileri de dahil olmak üzere güvenlik ekiplerine yöneliktir. Uyarıları hızlı bir şekilde Doğru Pozitif (TP) veya Hatalı Pozitif (TP) olarak notlayabilir ve TP uyarılarının saldırıyı düzeltmesi için önerilen eylemleri gerçekleştirebilirsiniz.

Bu playbook'u kullanmanın sonuçları şunlardır:

- Gelen kutusu işleme kurallarıyla ilişkili uyarıları kötü amaçlı (TP) veya zararsız (FP) etkinlikler olarak tanımladiniz.

  Kötü amaçlıysa, kötü amaçlı gelen kutusu işleme kurallarını kaldırmış olursunuz.

- E-postalar kötü amaçlı bir e-posta adresine iletildiyse gerekli eylemi yapmışsınızdır.

## <a name="inbox-manipulation-rules"></a>Gelen kutusu işleme kuralları

Gelen kutusu kuralları, önceden tanımlanmış ölçütlere göre e-posta iletilerini otomatik olarak yönetecek şekilde ayarlanır. Örneğin, yöneticinizden gelen tüm iletileri başka bir klasöre taşımak veya aldığınız iletileri başka bir e-posta adresine iletmek için bir gelen kutusu kuralı oluşturabilirsiniz.

### <a name="malicious-inbox-manipulation-rules"></a>Kötü amaçlı gelen kutusu işleme kuralları

Saldırganlar, kullanıcıdan gelen kötü amaçlı etkinliklerini gizlemek için güvenliği aşılmış kullanıcı posta kutusundaki gelen e-postaları gizlemek için e-posta kuralları ayarlayabilir. Ayrıca, güvenliği aşılmış kullanıcı posta kutusunda e-postaları silmek, e-postaları daha az fark edilebilir başka bir klasöre (RSS gibi) taşımak veya postaları bir dış hesaba iletmek için kurallar ayarlayabilir. Bazı kurallar tüm e-postaları başka bir klasöre taşıyabilir ve bunları "okundu" olarak işaretleyebilirken, bazı kurallar yalnızca e-posta iletisinde veya konuda belirli anahtar sözcükler içeren postaları taşıyabilir.

Örneğin, gelen kutusu kuralı diğerleri arasında "fatura", "kimlik avı", "yanıtlama", "şüpheli e-posta" veya "istenmeyen posta" gibi anahtar sözcükleri aramak ve bunları bir dış e-posta hesabına taşımak için ayarlanabilir. Saldırganlar istenmeyen postaları, kimlik avı e-postalarını veya kötü amaçlı yazılımları dağıtmak için güvenliği aşılmış kullanıcı posta kutusunu da kullanabilir.

## <a name="workflow"></a>Iş akışı

Şüpheli gelen kutusu işleme kuralı etkinliklerini tanımlamaya yönelik iş akışı aşağıdadır.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-workflow.png" alt-text="Gelen kutusu işleme kuralları için uyarı araştırma iş akışı" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-workflow.png":::

## <a name="investigation-steps"></a>Araştırma adımları

Bu bölüm, olaya yanıt vermek ve kuruluşunuzu başka saldırılara karşı korumak için önerilen adımları uygulamak için ayrıntılı adım adım yönergeler içerir.

### <a name="1-review-the-alerts"></a>1. Uyarıları gözden geçirin

Aşağıda, uyarı kuyruğundaki gelen kutusu işleme kuralı uyarısının bir örneği verilmiş.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-queue.png" alt-text="Gelen kutusu işleme kuralı örneği" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-queue.png":::

Burada, kötü amaçlı gelen kutusu işleme kuralı tarafından tetiklenen bir uyarının ayrıntılarına bir örnek verilmiştir.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-description.png" alt-text="Kötü amaçlı gelen kutusu işleme kuralı tarafından tetiklenen uyarının ayrıntıları" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-alert-description.png":::

### <a name="2-investigate-inbox-manipulation-rule-parameters"></a>2. Gelen kutusu işleme kuralı parametrelerini araştırma

Kuralların aşağıdaki kural parametrelerine veya ölçütlerine göre şüpheli görünerek görünmediğini belirleyin:

- Anahtar kelime -ler

   Saldırgan, düzenleme kuralını yalnızca belirli sözcükleri içeren e-postalara uygulayabilir. Bu anahtar sözcükleri şu gibi bazı öznitelikler altında bulabilirsiniz: "BodyContainsWords", "SubjectContainsWords" veya "SubjectOrBodyContainsWords".

   Anahtar sözcüklere göre filtreleme varsa, anahtar sözcüklerin size şüpheli görünip görünmediğini denetleyin (yaygın senaryolar, saldırgan etkinlikleriyle ilgili "kimlik avı", "istenmeyen posta", "yanıtlama" gibi e-postaları filtrelemektir).

   Hiç filtre yoksa, bu da şüpheli olabilir.

- Hedef klasör

   Saldırgan, güvenlik algılamasını azaltmak için e-postaları daha az fark edilebilir bir klasöre taşıyabilir ve e-postaları okundu olarak işaretleyebilir (örneğin, "RSS" klasörü). Saldırgan "MoveToFolder" ve "MarkAsRead" eylemi uygularsa, şüpheli görünip görünmediğine karar vermek için hedef klasörün kuraldaki anahtar sözcüklerle bir şekilde ilişkili olup olmadığını denetleyin.

- Tümünü sil

   Bazı saldırganlar etkinliklerini gizlemek için yalnızca gelen tüm e-postaları siler. Çoğunlukla, anahtar sözcüklerle filtrelemeden "tüm gelen e-postaları sil" kuralı kötü amaçlı etkinliklerin bir göstergesidir.

aşağıda, ilgili olay günlüğünün "tüm gelen e-postaları sil" kural yapılandırmasına (RawEventData.Parameters'da görüldüğü gibi) bir örnek verilmiştir.

:::image type="content" source="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-delete-log.png" alt-text="Tüm gelen e-postaları silme kuralı yapılandırması örneği" lightbox="../../media/alert-grading-playbook-inbox-manipulation-rules/alert-grading-playbook-inbox-manipulation-rules-delete-log.png":::

### <a name="3-investigate-the-ip-address"></a>3. IP adresini araştırma

Kural oluşturma işleminin ilgili olayını gerçekleştiren IP adresinin özniteliklerini gözden geçirin:

- Kiracıda aynı IP'den kaynaklanan diğer şüpheli bulut etkinliklerini arayın. Örneğin, şüpheli etkinlik birden çok başarısız oturum açma girişimi olabilir.
- ISS bu kullanıcı için ortak ve makul mü?
- Konum bu kullanıcı için ortak ve makul mü?

### <a name="4-investigate-suspicious-activity-by-the-user-prior-to-creating-the-rules"></a>4. Kuralları oluşturmadan önce kullanıcının şüpheli etkinliğini araştırma

Kurallar oluşturulmadan önce tüm kullanıcı etkinliklerini gözden geçirebilir, risk göstergelerini denetleyebilir ve şüpheli görünen kullanıcı eylemlerini araştırabilirsiniz.

Örneğin, birden çok başarısız oturum açma için şunları inceleyin:

- Oturum açma etkinliği

   Kural oluşturmadan önceki oturum açma etkinliğinin şüpheli olmadığını doğrulayın. (ortak konum / ISS / kullanıcı aracısı).

- Uyarılar

   Kuralları oluşturmadan önce kullanıcının uyarı alıp almadığını denetleyin. Bu, kullanıcı hesabının gizliliğinin tehlikeye girmiş olabileceğini gösterebilir. Örneğin, imkansız seyahat uyarısı, seyrek ülke, diğerleri arasında birden fazla başarısız oturum açma.)

- Olay

   Uyarının bir olayı gösteren diğer uyarılarla ilişkili olup olmadığını denetleyin. Öyleyse, olayın diğer gerçek pozitif uyarılar içerip içermediğini denetleyin.

## <a name="advanced-hunting-queries"></a>Gelişmiş tehdit avcılığı sorguları

[Gelişmiş Tehdit Avcılığı](advanced-hunting-overview.md) , tehdit göstergelerini bulmak için ağınızdaki olayları incelemenize olanak tanıyan sorgu tabanlı bir tehdit avcılığı aracıdır.

Belirli bir zaman penceresindeki tüm yeni gelen kutusu kuralı olaylarını bulmak için bu sorguyu kullanın.

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

*RuleConfig* sütunu yeni gelen kutusu kuralı yapılandırmasını sağlar.

Kullanıcının geçmişine bakarak ISS'nin kullanıcı için ortak olup olmadığını denetlemek için bu sorguyu kullanın.

```kusto
let alert_date = now(); //enter alert date
let timeback = 60d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by ISP
```

Kullanıcının geçmişine bakarak ülkenin kullanıcı için ortak olup olmadığını denetlemek için bu sorguyu kullanın.

```kusto
let alert_date = now(); //enter alert date
let timeback = 60d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by CountryCode
```

Kullanıcının geçmişine bakarak kullanıcı aracısının kullanıcı için ortak olup olmadığını denetlemek için bu sorguyu kullanın.

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

1. Kötü amaçlı gelen kutusu kuralını devre dışı bırakın.
2. Kullanıcı hesabının kimlik bilgilerini sıfırlayın. Ayrıca, Azure Active Directory (Azure AD) Kimlik Koruması'ndan güvenlik sinyalleri alan Microsoft Defender for Cloud Apps kullanıcı hesabının gizliliğinin ihlal edildiğini de doğrulayabilirsiniz.
3. Etkilenen kullanıcı hesabı tarafından gerçekleştirilen diğer kötü amaçlı etkinlikleri arayın.
4. Diğer güvenliği aşılmış kullanıcı hesaplarını bulmak için kiracıda aynı IP'den veya aynı ISS'den (ISS yaygın değilse) kaynaklanan diğer şüpheli etkinlikleri denetleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Uyarı notlama genel bakış](alert-grading-playbooks.md)
- [Şüpheli e-posta iletme etkinliği](alert-grading-playbook-email-forwarding.md)
- [Şüpheli gelen kutusu iletme kuralları](alert-grading-playbook-inbox-forwarding-rules.md)
- [Uyarıları araştırın](investigate-alerts.md)
