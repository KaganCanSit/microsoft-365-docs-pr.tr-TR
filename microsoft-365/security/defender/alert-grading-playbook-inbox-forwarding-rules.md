---
title: Şüpheli gelen kutusu iletme kuralları için uyarı notları
description: Uyarıları gözden geçirmek ve saldırıyı düzeltmek ve ağınızı korumak için önerilen eylemleri uygulamak için şüpheli gelen kutusu iletme kuralları için uyarı notlama.
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
ms.openlocfilehash: dca305b88e6e8db25e0a798c4361086bd7cb1e8b
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666030"
---
# <a name="alert-grading-for-suspicious-inbox-forwarding-rules"></a>Şüpheli gelen kutusu iletme kuralları için uyarı notları

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- Microsoft 365 Defender

Tehdit aktörleri, güvenliği aşılmış kullanıcı hesaplarını kullanıcının gelen kutusundaki e-postaları okuma, e-postaları dış hesaplara iletmek için gelen kutusu kuralları oluşturma, kimlik avı postaları gönderme gibi çeşitli kötü amaçlı amaçlar için kullanabilir. Kötü amaçlı gelen kutusu kuralları, iş e-posta güvenliğinin aşılması (BEC) ve kimlik avı kampanyaları sırasında yaygın olarak görülür ve bunları tutarlı bir şekilde izlemek önemlidir.

Bu playbook, şüpheli gelen kutusu iletme kurallarıyla ilgili uyarıları araştırmanıza ve bunları Doğru Pozitif (TP) veya Hatalı Pozitif (TP) olarak hızla notlamanıza yardımcı olur. Ardından, saldırıyı düzeltmek için TP uyarıları için önerilen eylemleri gerçekleştirebilirsiniz.

Office 365 için Microsoft Defender ve Microsoft Defender for Cloud Apps için uyarı not verme konusuna genel bakış için [giriş makalesine](alert-grading-playbooks.md) bakın.

Bu playbook'u kullanmanın sonuçları şunlardır:

- Gelen kutusu iletme kurallarıyla ilişkili uyarıları kötü amaçlı (TP) veya zararsız (FP) etkinlikler olarak tanımlamışsınız.

  Kötü amaçlıysa, kötü amaçlı gelen kutusu iletme kurallarını kaldırmış olursunuz.

- E-postalar kötü amaçlı bir e-posta adresine iletildiyse gerekli eylemi yapmışsınızdır.

## <a name="inbox-forwarding-rules"></a>Gelen kutusu iletme kuralları

Önceden tanımlanmış ölçütlere göre e-posta iletilerini otomatik olarak yönetmek için gelen kutusu kurallarını yapılandırabilirsiniz. Örneğin, yöneticinizden gelen tüm iletileri başka bir klasöre taşımak veya aldığınız iletileri başka bir e-posta adresine iletmek için bir gelen kutusu kuralı oluşturabilirsiniz.

### <a name="suspicious-inbox-forwarding-rules"></a>Şüpheli gelen kutusu iletme kuralları

Kullanıcıların posta kutularına erişim elde ettikten sonra saldırganlar genellikle hassas verileri dış e-posta adresine çıkarmalarına ve kötü amaçlı olarak kullanmalarına olanak tanıyan bir gelen kutusu kuralı oluşturur.

Kötü amaçlı gelen kutusu kuralları sızdırma işlemini otomatikleştirir. Belirli kurallarla, hedef kullanıcının gelen kutusundaki kural ölçütleriyle eşleşen her e-posta saldırganın posta kutusuna iletilir. Örneğin, bir saldırgan finansla ilgili hassas verileri toplamak isteyebilir. Konu veya ileti gövdesinde 'finans' ve 'fatura' gibi anahtar sözcükler içeren tüm e-postaları posta kutularına iletmek için bir gelen kutusu kuralı oluştururlar.

Gelen kutusu kurallarının bakımı kullanıcılar tarafından yapılan yaygın bir görev olduğundan şüpheli gelen kutusu iletme kurallarının algılanması çok zor olabilir. Bu nedenle, uyarıları izlemek önemlidir.

## <a name="workflow"></a>Iş akışı

Şüpheli e-posta iletme kurallarını tanımlamaya yönelik iş akışı aşağıdadır.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-workflow.png" alt-text="Gelen kutusu iletme kuralları için uyarı araştırma iş akışı" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-workflow.png":::

## <a name="investigation-steps"></a>Araştırma adımları

Bu bölüm, olaya yanıt vermek ve kuruluşunuzu başka saldırılara karşı korumak için önerilen adımları uygulamak için ayrıntılı adım adım yönergeler içerir.

### <a name="review-generated-alerts"></a>Oluşturulan uyarıları gözden geçirme

Aşağıda, uyarı kuyruğundaki gelen kutusu iletme kuralı uyarısının bir örneği verilmiş.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-queue.png" alt-text="Uyarı kuyruğundaki bildirim örneği" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-queue.png":::

Burada, kötü amaçlı bir gelen kutusu iletme kuralı tarafından tetiklenen uyarının ayrıntılarına bir örnek verilmiştir.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-description.png" alt-text="Kötü amaçlı gelen kutusu iletme kuralı tarafından tetiklenen uyarının ayrıntıları" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-description.png":::

### <a name="investigate-rule-parameters"></a>Kural parametrelerini araştırma

Bu aşamanın amacı, kuralların belirli ölçütlere göre şüpheli görünerek görünmediğini belirlemektir:

İletme kuralının alıcıları:

- Hedef e-posta adresinin aynı kullanıcıya ait ek bir posta kutusu olmadığını doğrulayın (kullanıcının kişisel posta kutuları arasında e-postaları kendi kendine ilettiği durumlardan kaçının).
- Hedef e-posta adresinin şirkete ait bir iç adres veya alt etki alanı olmadığını doğrulayın.

Filtre:

- Gelen kutusu kuralı, e-postanın konusu veya gövdesinde belirli anahtar sözcükleri arayan filtreler içeriyorsa finans, kimlik bilgileri ve ağ gibi sağlanan anahtar sözcüklerin kötü amaçlı etkinliklerle ilgili olup olmadığını denetleyin. Bu filtreleri şu özniteliklerin altında bulabilirsiniz (event RawEventData sütununda gösterilir): "BodyContainsWords", "SubjectContainsWords" veya "SubjectOrBodyContainsWords"
- Saldırgan postalara filtre ayarlamamayı seçerse ve bunun yerine gelen kutusu kuralı tüm posta kutusu öğelerini saldırganın posta kutusuna iletirse, bu davranış da şüphelidir.

### <a name="investigate-ip-address"></a>IP adresini araştırma

Kural oluşturma işleminin ilgili olayını gerçekleştiren IP adresiyle ilgili öznitelikleri gözden geçirin:

1. Kiracıda aynı IP'den kaynaklanan diğer şüpheli bulut etkinliklerini arayın. Örneğin, şüpheli etkinlik birden çok başarısız oturum açma girişimi olabilir.
2. ISS bu kullanıcı için ortak ve makul mü?
3. Konum bu kullanıcı için ortak ve makul mü?

### <a name="investigate-any-suspicious-activity-with-the-user-inbox-before-creating-rules"></a>Kural oluşturmadan önce kullanıcı gelen kutusuyla şüpheli etkinlikleri araştırma

Kural oluşturmadan önce tüm kullanıcı etkinliklerini gözden geçirebilir, risk göstergelerini denetleyebilir ve şüpheli görünen kullanıcı eylemlerini araştırabilirsiniz. Örneğin, birden çok başarısız oturum açma.

- Oturum açma işlemleri:

  Kural oluşturma olayından önceki oturum açma etkinliğinin şüpheli olmadığını doğrulayın (ortak konum, ISS veya kullanıcı aracısı gibi).

- Diğer uyarılar veya olaylar
  - Kural oluşturmadan önce kullanıcı için diğer uyarılar tetiklendiğinde. Öyleyse, bu durum kullanıcının gizliliğinin tehlikeye girdiğini gösterebilir.
  - Uyarı bir olayı göstermek için diğer uyarılarla bağıntılıysa, olay başka gerçek pozitif uyarılar içeriyor mu?

## <a name="advanced-hunting-queries"></a>Gelişmiş tehdit avcılığı sorguları

[Gelişmiş Tehdit Avcılığı](advanced-hunting-overview.md) , ağınızdaki olayları incelemenize ve tehdit göstergelerini bulmanıza olanak tanıyan sorgu tabanlı bir tehdit avcılığı aracıdır.

Belirli bir zaman penceresindeki tüm yeni gelen kutusu kuralı olaylarını bulmak için bu sorguyu çalıştırın.

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

*RuleConfig* , kural yapılandırmasını içerir.

Kullanıcının geçmişine bakarak ISS'nin kullanıcı için ortak olup olmadığını denetlemek için bu sorguyu çalıştırın.

```kusto
let alert_date = now(); //enter alert date
let timeback = 30d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by ISP
```

Kullanıcının geçmişine bakarak ülkenin kullanıcı için ortak olup olmadığını denetlemek için bu sorguyu çalıştırın.

```kusto
let alert_date = now(); //enter alert date
let timeback = 30d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by CountryCode
```

Kullanıcının geçmişine bakarak kullanıcı aracısının kullanıcı için ortak olup olmadığını denetlemek için bu sorguyu çalıştırın.

```kusto
let alert_date = now(); //enter alert date
let timeback = 30d;
let userid = ""; //enter here user id
CloudAppEvents
| where Timestamp between ((alert_date-timeback)..(alert_date-1h))
| where AccountObjectId == userid
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by UserAgent
```

Diğer kullanıcıların aynı hedefe iletme kuralı oluşturup oluşturmadığını denetlemek için bu sorguyu çalıştırın (diğer kullanıcıların da güvenliğinin aşıldığını gösterebilir).

```kusto
let start_date = now(-10h);
let end_date = now();
let dest_email = ""; // enter here destination email as seen in the alert
CloudAppEvents
| where Timestamp between (start_date .. end_date)
| where ActionType in ("Set-Mailbox", "New-InboxRule", "Set-InboxRule") //set new inbox rule related operations
| project Timestamp, ActionType, CountryCode, City, ISP, IPAddress, RuleConfig = RawEventData.Parameters, RawEventData
| where RuleConfig has dest_email
```

## <a name="recommended-actions"></a>Önerilen eylemler

1. Kötü amaçlı gelen kutusu kuralını devre dışı bırakın.
2. Kullanıcının hesap kimlik bilgilerini sıfırlayın. Ayrıca, Azure Active Directory (Azure AD) Kimlik Koruması'ndan güvenlik sinyalleri alan Microsoft Defender for Cloud Apps kullanıcı hesabının gizliliğinin ihlal edildiğini de doğrulayabilirsiniz.
3. Etkilenen kullanıcı tarafından gerçekleştirilen diğer kötü amaçlı etkinlikleri arayın.
4. Diğer güvenliği aşılmış kullanıcıları bulmak için kiracıdaki aynı IP'den veya aynı ISS'den (ISS yaygın değilse) kaynaklanan diğer şüpheli etkinlikleri denetleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Uyarı notlama genel bakış](alert-grading-playbooks.md)
- [Şüpheli e-posta iletme etkinliği](alert-grading-playbook-email-forwarding.md)
- [Şüpheli gelen kutusu işleme kuralları](alert-grading-playbook-inbox-manipulation-rules.md)
- [Uyarıları araştırın](investigate-alerts.md)
