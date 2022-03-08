---
title: Şüpheli gelen kutusu iletme kuralları için uyarı notlama
description: Uyarıları gözden geçirmek ve saldırıyı düzeltmek ve ağın korunması için önerilen eylemleri yapmak için şüpheli gelen kutusu iletme kurallarına uyarı notlama.
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
ms.openlocfilehash: 08178a1672e3bdd5b124138f698b42be8181373a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63325509"
---
# <a name="alert-grading-for-suspicious-inbox-forwarding-rules"></a>Şüpheli gelen kutusu iletme kuralları için uyarı notlama

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Tehdit ile ilgili tehdit, bir kullanıcının gelen kutusunda e-postaları okuma, e-postaları dış hesaplara iletme, kimlik avı e-postaları gönderme gibi çeşitli kötü amaçlı amaçlar için güvenliği tehlikeye atılmış kullanıcı hesaplarını kullanabilir. Kötü amaçlı gelen kutusu kuralları, iş e-posta güvenliği (BEC) ve kimlik avı kampanyaları sırasında yaygın yaygındır ve bunları tutarlı bir şekilde izlemek önemlidir.

Bu çalışma kitabı şüpheli gelen kutusu iletme kurallarına yönelik uyarıları araştırmanıza ve bunları hızlı bir şekilde Doğru Pozitif (TP) veya Hatalı Pozitif (TP) olarak notlamanıza yardımcı olur. Ardından, saldırıyı düzeltmek için TP uyarıları için önerilen eylemleri gerçekleştirabilirsiniz. 

Office 365 için Microsoft Defender ve Bulut Uygulamaları için Microsoft Defender uyarı notlama hakkında genel bilgi için giriş [makalesine bakın](alert-grading-playbooks.md).

Bu playbook'un kullanımı sonuçları:

- Gelen kutusu iletme kurallarıyla ilişkilendirilmiş uyarıları kötü amaçlı (TP) veya skp (FP) etkinlikleri olarak belirlediniz.

  Kötü amaçlı ise, kötü amaçlı gelen kutusu iletme kurallarını kaldırılmış demektir.

- E-postalar kötü amaçlı bir e-posta adresine iletirse gerekli eylemi benimseyebilirsiniz.

## <a name="inbox-forwarding-rules"></a>Gelen kutusu iletme kuralları

E-posta iletilerini önceden tanımlanmış ölçütlere göre otomatik olarak yönetmek için gelen kutusu kurallarını yapılandırabilirsiniz. Örneğin, yöneticinizden gelen tüm iletileri başka bir klasöre taşımak veya gelen iletileri başka bir e-posta adresine iletecek bir gelen kutusu kuralı oluşturabilirsiniz.

### <a name="suspicious-inbox-forwarding-rules"></a>Şüpheli gelen kutusu iletme kuralları

Kullanıcıların posta kutularına erişim elde edildikten sonra, saldırganlar çoğunlukla hassas verileri bir dış e-posta adresine dosyalamalarına ve kötü amaçlı amaçlarla kullanmalarına olanak sağlayan bir gelen kutusu kuralı oluştur. 

Kötü amaçlı gelen kutusu kuralları, filtreleme işlemini otomatik hale gelir. Belirli kurallarla, hedef kullanıcının gelen kutusunda kural ölçütlerine uyan tüm e-postalar saldırgan posta kutusuna ilet edilir. Örneğin, bir saldırgan finans ile ilgili hassas verileri toplamak istiyor olabilir. Konu veya ileti gövdesinde 'finans' ve 'fatura' gibi anahtar sözcükleri içeren tüm e-postaları posta kutularına iletmeleri için bir gelen kutusu kuralı oluşturdukları anlamına gelir.

Gelen kutusu kurallarının bakımı kullanıcılar tarafından yapılan yaygın bir görev olduğundan, şüpheli gelen kutusu iletme kurallarını algılamak çok zor olabilir. Bu nedenle uyarıları izlemek önemlidir. 

## <a name="workflow"></a>İş Akışı

İşte, şüpheli e-posta iletme kurallarını belirlemeye yardımcı olacak iş akışı.
 
:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-workflow.png" alt-text="Gelen kutusu iletme kuralları için uyarı soruşturma iş akışı" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-workflow.png":::

## <a name="investigation-steps"></a>İnceleme adımları

Bu bölüm, olayı yanıtlamaya ve organizasyonlarınızı daha fazla saldırıya karşı korumak için önerilen adımları atılacak ayrıntılı adım adım kılavuzu içerir.

### <a name="review-generated-alerts"></a>Oluşturulan uyarıları gözden geçirme

İşte, uyarı kuyruğunda gelen kutusu iletme kuralı uyarısı örneği.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-queue.png" alt-text="Uyarı kuyruğunda bildirim örneği" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-queue.png":::

İşte, kötü amaçlı gelen kutusu iletme kuralı tarafından tetiklenen uyarının ayrıntıları örneği.

:::image type="content" source="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-description.png" alt-text="Kötü amaçlı gelen kutusu iletme kuralı tarafından tetiklenen uyarının ayrıntıları" lightbox="../../media/alert-grading-playbook-inbox-forwarding-rules/alert-grading-playbook-inbox-forwarding-rules-alert-description.png":::

### <a name="investigate-rule-parameters"></a>Kural parametrelerini araştırma 

Bu aşamanın amacı, belirli ölçütlere göre kuralların şüpheli olup olmadığını belirlemektir:

Yönlendirme kuralının alıcıları:

- Hedef e-posta adresinin, aynı kullanıcıya ait ek bir posta kutusu olmadığını doğrulama (kullanıcının e-postaları kişisel posta kutuları arasında kendi kendine iletmesi gibi durumlardan kaçınma). 
- Hedef e-posta adresinin şirkete ait bir iç adres veya alt etki alanı olmadığını doğrulama.

Filtreler:
 
- Gelen kutusu kuralı, e-postanın konusunda veya gövdesinde belirli anahtar sözcükleri araten filtreler içeriyorsa, sağlanan anahtar sözcüklerin (finans, kimlik bilgileri ve ağ gibi) yanı sıra kötü amaçlı etkinliklerle ilgili olup olmadığını kontrol edin. Bu filtreleri, şu özniteliklerin altında bulabilirsiniz (olay RawEventData sütununda görüntülenir): "BodyContainsWords", "SubjectContainsWords" veya "SubjectOrContainsWords"
- Saldırgan postalara herhangi bir filtre ayarlamayı seçmezse ve gelen kutusu kuralı tüm posta kutusu öğelerini saldırgan'ın posta kutusuna iletirse, bu davranış da şüphelidir. 

### <a name="investigate-ip-address"></a>IP adresini araştır

Kural oluşturmayla ilgili olayı gerçekleştiren IP adresiyle ilgili öznitelikleri gözden geçirme:

1. Kiracıda aynı IP'den kaynaklanan diğer şüpheli bulut etkinliklerini arama. Örneğin, şüpheli etkinlik birden çok başarısız oturum açma girişimi olabilir. 
2. ISS, bu kullanıcı için yaygın ve mantıklı mı?
3. Konum, bu kullanıcı için genel ve mantıklı mı?

### <a name="investigate-any-suspicious-activity-with-the-user-inbox-before-creating-rules"></a>Kural oluşturmadan önce kullanıcı gelen kutusuyla ilgili şüpheli etkinlikleri araştırma

Kural oluşturmadan önce tüm kullanıcı etkinliklerini gözden geçirerek, ödün göstergelerine bakarak ve şüpheli görünen kullanıcı eylemlerini araştırabilirsiniz. Örneğin, birden çok başarısız oturum açma işlemi.  

- Oturum açma: 

  Kural oluşturma olayından önce oturum açma etkinliğinin şüpheli olmadığını doğrulama (ortak konum, ISS veya kullanıcı aracısı gibi). 

- Diğer uyarılar veya olaylar 

   - Kural oluşturmadan önce kullanıcı için başka uyarılar tetikledi mi? Bu durumda, güvenliğin ihlal edilmiş olduğu belirtilebilir. 

   - Uyarı bir olayı belirtmek için diğer uyarılarla bağlantılıysa, o zaman olay başka doğru pozitif uyarılar içeriyor mu? 

## <a name="advanced-hunting-queries"></a>Gelişmiş arama sorguları

[Gelişmiş Av](advanced-hunting-overview.md) , ağ'daki olayları incelemenize ve tehdit göstergelerini bulamanıza olanak sağlayan sorgu tabanlı bir tehdit arama aracıdır. 

Belirli bir zaman penceresinde tüm yeni gelen kutusu kuralı olaylarını bulmak için bu sorguyu çalıştırın.  

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

Kullanıcının geçmişine bakarak ISS'nin kullanıcı için ortak olup olmadığını kontrol etmek için bu sorguyu çalıştırın.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 30d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by ISP 
```

Kullanıcının geçmişine bakarak, ülkenin kullanıcı için ortak olup olmadığını kontrol etmek için bu sorguyu çalıştırın.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 30d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by CountryCode
```

Kullanıcının geçmişine bakarak, kullanıcı aracısı arasında ortak olup olmadığını kontrol etmek için bu sorguyu çalıştırın.

```kusto
let alert_date = now(); //enter alert date 
let timeback = 30d; 
let userid = ""; //enter here user id 
CloudAppEvents 
| where Timestamp between ((alert_date-timeback)..(alert_date-1h)) 
| where AccountObjectId == userid 
| make-series ActivityCount = count() default = 0 on Timestamp  from (alert_date-timeback) to (alert_date-1h) step 12h by UserAgent
```

Bu sorguyu çalıştırarak diğer kullanıcıların aynı hedefe iletme kuralı oluşturan diğer kullanıcıların da güvenliği ihlal edilmiş olup olduğunu kontrol edin.

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

1. Kötü amaçlı gelen kutusu kuralını devre dışı bırakma. 
2. Kullanıcının hesap kimlik bilgilerini sıfırlayın. Ayrıca, Bulut Uygulamaları için Microsoft Defender'la kullanıcı hesabının güvenliğinin ihlal edilmiş olup olduğunu doğruabilirsiniz ve bu da Azure Active Directory (Azure AD) Identity Protection'dan güvenlik sinyallerini alır.
3. Etkiyi alan kullanıcı tarafından gerçekleştirilen diğer kötü amaçlı etkinlikleri arama.
4. Kiracıda, güvenliği tehlikeye atılmış diğer kullanıcıları bulmak için aynı IP'den veya aynı ISS'den (ISS seyrek ortaya çıktı ise) gelen diğer şüpheli etkinlikleri denetleme.

## <a name="see-also"></a>Ayrıca bkz.

- [Uyarı notlamaya genel bakış](alert-grading-playbooks.md)
- [Şüpheli e-posta iletme etkinliği](alert-grading-playbook-email-forwarding.md)
- [Şüpheli gelen kutusu işleme kuralları](alert-grading-playbook-inbox-manipulation-rules.md)
- [Uyarıları araştırma](investigate-alerts.md)
