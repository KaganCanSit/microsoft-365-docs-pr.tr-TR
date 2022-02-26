---
title: Şüpheli e-posta iletme etkinliği için uyarı notlama
description: Uyarıları gözden geçirmek ve saldırıyı düzeltmek ve ağın korunması için önerilen eylemleri yapmak için şüpheli e-posta iletme etkinliğine uyarı notlama.
keywords: olaylar, uyarılar, araştırma, çözümleme, yanıt, korelasyon, saldırı, makineler, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, microsoft, m365
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
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
ms.openlocfilehash: fe4a5e97704cbf1d4851484397e7c4424c099d3c
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/10/2022
ms.locfileid: "62974165"
---
# <a name="alert-grading-for-suspicious-email-forwarding-activity"></a>Şüpheli e-posta iletme etkinliği için uyarı notlama

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Tehdit amaçlı tehdit, kullanıcının gelen kutusunda e-postaları okuma, e-postaları dış alıcılara iletme ve kimlik avı e-postaları gönderme gibi çeşitli kötü amaçlı amaçlar doğrultusunda güvenliği ihlal edilmiş kullanıcı hesaplarını kullanabilir. Hedefli kullanıcı e-postalarının iletil haberini fark e-postayı fark e-postaylamış olabilir. Bu, kullanıcı hesaplarının güvenliği ihlal edilmişken saldırganların kullanmaları için kullanılan çok yaygın bir tactiğidir.

E-postalar el ile veya otomatik olarak iletme kuralları kullanılarak iletilebilir. Otomatik iletme, Gelen Kutusu Kuralları, Aktarım Kuralı (ETR) Exchange SMTP İ iletme gibi çeşitli yöntemlerle uygulanabilirsiniz. El ile iletme işlemi kullanıcılardan doğrudan işlem gerektiriyor ama otomatik iletili e-postaların hepsini fark e-postalarını fark e-postayla gönderemleri gerektir. Yeni Microsoft 365, kullanıcı bir e-postayı otomatik olarak kötü amaçlı olabilecek bir e-posta adresine iletmişsa uyarı yükseltildi.

Bu çalışma kitabı Şüpheli E-posta İ iletme Etkinliği uyarılarını araştırmanıza ve bunları hızlı bir şekilde Doğru Pozitif (TP) veya Hatalı Pozitif (FP) olarak notlamanıza yardımcı olur. Ardından, saldırıyı düzeltmek için TP uyarıları için önerilen eylemleri gerçekleştirabilirsiniz.

Office 365 için Microsoft Defender ve Bulut Uygulamaları için Microsoft Defender uyarı notlama hakkında genel bilgi için giriş [makalesine bakın](alert-grading-playbooks.md).

Bu playbook'un kullanımı sonuçları:

- Otomatik iletili e-postalarla ilişkilendirilmiş uyarıları kötü amaçlı (TP) veya skp (FP) etkinlikleri olarak belirledik.

  Kötü amaçlı ise, etkilenen [posta kutuları için e-posta otomatik](../office-365-security/external-email-forwarding.md) iletmeyi durdurdunız.

- E-postalar kötü amaçlı bir e-posta adresine iletirse gerekli eylemi benimseyebilirsiniz.

## <a name="email-forwarding-rules"></a>E-posta iletme kuralları

E-posta iletme kuralları, kullanıcıların bir kullanıcının posta kutusuna gönderilen e-posta iletilerini kuruluş içinde veya dışında başka bir kullanıcının posta kutusuna iletmesine yönelik bir kural oluşturmasına olanak sağlar. Özellikle birden çok posta kutusu olan bazı e-posta kullanıcıları, işveren e-postalarını özel e-posta hesaplarına taşımak için iletme kurallarını yapılandırıyor. E-posta iletme kullanışlı bir özelliktir, ancak bilgilerin olası açıklanması nedeniyle güvenlik riski de ortaya atabilirsiniz. Saldırganlar bu bilgileri kuruluşa veya iş ortaklarına saldırı yapmak için kullanabilir.

### <a name="suspicious-email-forwarding-activity"></a>Şüpheli e-posta iletme etkinliği

Saldırganlar, kötü amaçlı etkinliklerini kullanıcıdan gizlemek üzere güvenliği tehlikeye konan kullanıcı posta kutusunda gelen e-postaları gizlemek için e-posta kuralları ayarlamış olabilir. Ayrıca güvenliği tehlikeye atılmış kullanıcı posta kutusunda e-postaları silmek, e-postaları RSS klasörü gibi daha az fark edilebilir başka bir klasöre taşımak veya e-postaları bir dış hesaba iletmek için de kurallar ayarlanabilir.  

Bazı kurallar tüm e-postaları başka bir klasöre taşımak ve bunları "okundu" olarak işaretlemek için, bazı kurallar ise yalnızca e-posta iletisinde veya konu iletisinde belirli anahtar sözcükleri içeren postaları hareket ettirebilirsiniz. Örneğin, gelen kutusu kuralı "fatura", "kimlik avı", "yanıt vermedi", "şüpheli e-posta" veya "istenmeyen posta" gibi anahtar sözcükleri başkaları arasında arama yapacak şekilde ayarlanmış olabilir ve bunları bir dış e-posta hesabına taşı. Saldırganlar ayrıca güvenliği tehlikeye atılmış kullanıcı posta kutusunu istenmeyen posta, kimlik avı e-postaları veya kötü amaçlı yazılım dağıtmak için de kullanabilir.
 
e-posta Office 365 için Microsoft Defender şüpheli e-posta iletme kurallarını algılanabilir ve uyararak kaynakta gizli kuralları bulamanıza ve silmenıza olanak sağlar.

Daha fazla bilgi için bu blog gönderileri'ne bakın:

- [İş e-posta güvenliği](https://techcommunity.microsoft.com/t5/microsoft-defender-for-office/business-email-uncompromised-part-one/ba-p/2159900)
- [İş e-postalarının sahne gerisinde güvenliği tehlikeye atma: Büyük bir BEC kampanyasını kesintiye bırakmak için etki alanı arası tehdit verilerini kullanma](https://www.microsoft.com/security/blog/2021/06/14/behind-the-scenes-of-business-email-compromise-using-cross-domain-threat-data-to-disrupt-a-large-bec-infrastructure/)


## <a name="alert-details"></a>Uyarı ayrıntıları

Şüpheli E-posta Iletme Etkinliği uyarılarını gözden geçirmek **için** , Uyarılar sayfasını açıp Etkinlik listesi **bölümünü** açın. İşte bir örnek.
 
:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-list.png" alt-text="Uyarıyla ilgili etkinliklerin listesi" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-list.png":::

Kenar **çubuğunda**  etkinliğin ayrıntılarını görüntülemek için Etkinlik'i seçin. İşte bir örnek.
 
:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-details.png" alt-text="Etkinlik ayrıntıları" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-activity-details.png":::

Neden **alanı** , bu uyarıyla ilgili aşağıdaki bilgileri içerir.

- İ iletme Türü (FT) aşağıdakilerden biridir:

    -  Exchange Aktarım Kuralı (ETR): Aktarım Kuralı kullanılarak Exchange iletildi 

    -  SMTP: Posta Kutusu İletim kullanılarak iletildi

    -  Gelen Kutusu Kuralı: Gelen Kutusu Kuralı kullanılarak iletildi

- İleti İzleme Kimliği (MTI): Bu, bu uyarıyı tetikleyen iletili e-postanın tanımlayıcısıdır (NetworkMessageId). NetworkMessageId, kurum içinde yer alan bir e-postanın benzersiz tanımlayıcısıdır.
- Forwarder (F): Bu e-postayı iletir.
- Şüpheli Alıcı Listesi (SRL): Bu e-postada şüpheli kabul edilen alıcılar listesi.
- Alıcı Listesi (RL): Bu e-postada yer alan tüm alıcıların listesi.

## <a name="investigation-workflow"></a>İnceleme iş akışı

Bu uyarıyı araştırırken şunları belirlemeniz gerekir:

- Kullanıcı hesabı ve posta kutusu güvenliği ihlal edilmiş mi?
- Etkinlikler kötü amaçlı mı?

### <a name="is-the-user-account-and-its-mailbox-compromised"></a>Kullanıcı hesabı ve posta kutusu güvenliği ihlal edilmiş mi?

Gönderenin geçmiş davranışına ve son etkinliklere bakarak, kullanıcının hesabının tehlikeye atılmış olarak kabul edilmiş olup olmadığını belirleyebilirsiniz. Kullanıcı portalında, kullanıcının sayfasından yükseltilmiş uyarı ayrıntılarını Microsoft 365 Defender. 

Etkilenen posta kutusu için şu ek etkinlikleri de çözümebilirsiniz:

- E-postayla ilgili tehditleri anlamak için Tehdit Gezgini'ni kullanma

    - Gönderen tarafından gönderilen en son e-postalardan çoğunun kimlik avı, istenmeyen posta veya kötü amaçlı yazılım olarak algılandığından emin olun.

    - Gönderilen e-postalardan kaç tanesinde hassas bilgi olduğunu gözlemin. 

- Portalda riskli oturum açma davranışını Microsoft Azure.
- Kullanıcının cihazında kötü amaçlı etkinliklerin olup olduğunu kontrol edin.

### <a name="are-the-activities-malicious"></a>Etkinlikler kötü amaçlı mı?

E-posta iletme etkinliğini araştırabilirsiniz. Örneğin, e-postanın türünü, bu e-postanın alıcısı veya e-postanın ilet iş türünü kontrol edin. 

Daha fazla bilgi için aşağıdaki makalelere bakın:

- [Otomatik iletili iletiler içgörü](/microsoft-365/security/office-365-security/mfi-auto-forwarded-messages-report)
- [E-posta içgörülerini iletir yeni kullanıcılar](/microsoft-365/security/office-365-security/mfi-new-users-forwarding-email)
- [Güvenliği Tehlikeye E-posta Hesabını Yanıtla](/microsoft-365/security/office-365-security/responding-to-a-compromised-email-account)
- [Negatif sonuçlarda hatalı pozitif ve yanlış negatif Outlook](/microsoft-365/security/office-365-security/report-false-positives-and-false-negatives)

İşte, şüpheli e-posta iletme etkinliklerini belirlemeye yönelik iş akışı.

:::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-workflow.png" alt-text="E-posta iletme için uyarı soruşturma iş akışı" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-workflow.png":::

Tehdit Gezgini'ni kullanarak veya gelişmiş arama sorguları ile e-posta iletme uyarılarını araştırmanız için, gelişmiş arama portalında Microsoft 365 Defender edebilirsiniz. Gerektiğinde sürecin tamamını veya bir bölümünü izlemeyi seçebilirsiniz.

## <a name="using-threat-explorer"></a>Tehdit Gezgini'ni kullanma

Threat Explorer, bu etkinliğin şüpheli olup olmadığını belirlemek için e-postayla ilgili tehditlere karşı etkileşimli bir soruşturma deneyimi sağlar. Uyarı bilgilerinden aşağıdaki göstergeleri kullanabilirsiniz:

- SRL/RL: Bu ayrıntıları bulmak için (Şüpheli) Alıcılar Listesi'ne (SRL) bakın:
 
    :::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-recipients-list.png" alt-text="Alıcı listesi örneği" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-recipients-list.png":::

    - Who başka e-postaları bu alıcılara iletir mi?

    - Bu alıcılara kaç e-posta iletildi?

    - E-postalar bu alıcılara ne sıklıkta ilet edilir?
 

- MTI: Şu ayrıntıları bulmak için İleti İzleme Kimliği/Ağ İleti Kimliği'ne tıklayın:

    :::image type="content" source="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-network-message-id.png" alt-text="Ağ İletisi Kimliği örneği" lightbox="../../media/alert-grading-playbook-email-forwarding/alert-grading-playbook-email-forwarding-network-message-id.png":::

    - Bu e-posta için hangi ek ayrıntılar kullanılabilir? Örneğin: Konu, dönüş yolu ve zaman damgası.

    - Bu e-postanın kaynağı nedir? Benzer e-postalar var mı?

    - Bu e-posta URL'leri içeriyor mu? URL herhangi bir hassas veriye işaret mi etti?

    - E-posta ek içeriyor mu? Ekler hassas bilgiler içeriyor mu?

    - E-postada hangi eylem ildi? Silinmiş, okundu olarak işaretlenmiş veya başka bir klasöre taşınmış mı?

    - Bu e-postayla ilişkilendirilmiş bir tehdit var mı? Bu e-posta herhangi bir kampanyanın parçası mı?

Bu soruların yanıtlarını temel alarak, bir e-postanın kötü amaçlı mı yoksa kötü amaçlı mı olduğunu belirleyebilirsiniz.

## <a name="advanced-hunting-queries"></a>Gelişmiş arama sorguları

Uyarıyla [ilgili bilgi](advanced-hunting-overview.md) toplamak ve etkinliğin şüpheli olup olmadığını belirlemek için gelişmiş Arama sorgularını kullanmak için, aşağıdaki tablolara erişiminiz olduğundan emin olun:

- EmailEvents - E-posta akışıyla ilgili bilgileri içerir.

- EmailUrlInfo - E-postalarda URL'lerle ilgili bilgileri içerir.

- CloudAppEvents -Kullanıcı etkinliklerinin denetim günlüğünü içerir.

- IdentityLogonEvents - Tüm kullanıcıların oturum açma bilgilerini içerir.

>[!Note]
>Bazı parametreler, sizin veya ağınız için benzersizdir. Bu belirli parametreleri her sorguda olduğu gibi doldurun.
>

Bu alıcılara e-postaları başka kimlerin ilettirmiştir (SRL/RL) bulmak için bu sorguyu çalıştırın.

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| distinct SenderDisplayName, SenderFromAddress, SenderObjectId
```

Bu alıcılara kaç e-posta iletildi bulmak için bu sorguyu çalıştırın.

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| summarize Count=dcount(NetworkMessageId) by RecipientEmailAddress
```

E-postaların bu alıcılara ne sıklıkta iletildiklerini bulmak için bu sorguyu çalıştırın.

```kusto
let srl=pack_array("{SRL}"); //Put values from SRL here.
EmailEvents
| where RecipientEmailAddress in (srl)
| summarize Count=dcount(NetworkMessageId) by RecipientEmailAddress, bin(Timestamp, 1d)
```

E-postada URL olup olduğunu bulmak için bu sorguyu çalıştırın.
 
```kusto
let mti='{MTI}'; //Replace {MTI} with MTI from alert
EmailUrlInfo
| where NetworkMessageId == mti
```

E-postanın ekleri olup olduğunu bulmak için bu sorguyu çalıştırın.

   ```kusto
   let mti='{MTI}'; //Replace {MTI} with MTI from alert
   EmailAttachmentInfo
   | where NetworkMessageId == mti
   ```

Forwarder'ın (gönderen) yeni kurallara sahip olup olduğunu bulmak için bu sorguyu çalıştırın.

```kusto
let sender = "{SENDER}"; //Replace {SENDER} with display name of Forwarder
let action_types = pack_array(
    "New-InboxRule", 
    "UpdateInboxRules", 
    "Set-InboxRule", 
    "Set-Mailbox",    
    "New-TransportRule",
    "Set-TransportRule");
CloudAppEvents
| where AccountDisplayName == sender
| where ActionType in (action_types)
```

Bu kullanıcıdan herhangi bir anormal oturum açma olay bulunarak bu sorguyu çalıştırın. Örneğin: bilinmeyen IP'ler, yeni uygulamalar, yaygın olmayan ülkeler, çoklu Oturum Açma Olayları.

```kusto
let sender = "{SENDER}"; //Replace {SENDER} with email of the Forwarder 
IdentityLogonEvents
| where AccountUpn == sender
```

### <a name="investigating-forwarding-rules"></a>Yönlendirme kurallarını araştırma

Ayrıca, kural türüne (uyarının FT değeri) bağlı olarak, Exchange yönetim merkezini kullanarak şüpheli iletme kurallarını da bulabilirsiniz.

- ETR 

  Exchange aktarım kuralları, Kurallar **bölümünde listelenir**. Tüm kuralların beklendiği gibi olduğunu doğrulayın.

- SMTP

  Gönderenin posta kutusunu seçerek posta kutusu iletme kurallarını, Posta akışı ayarlarını yönet **\> E-posta iletme \> Düzenleme'yi seçebilirsiniz\>**.

- Gelen KutusuRule

  Gelen kutusu kuralları e-posta istemcisiyle yapılandırılır. Kullanıcılar tarafından oluşturulan [gelen kutusu kurallarını liste almak için Get-InboxRule](/powershell/module/exchange/get-inboxrule) PowerShell cmdlet'ini kullanabilirsiniz.

### <a name="additional-investigation"></a>Ek araştırma

Şimdiye kadar keşfedilen kanıtla birlikte, yeni iletme kuralları oluşturulsa bile, bu kuralların oluşturul olup olmadığını da öğrensiniz. Kuralla ilişkilendirilmiş IP adresini araştırabilirsiniz. Bu adresin anormal bir IP adresi olmadığını ve kullanıcı tarafından gerçekleştirilen normal etkinliklerle tutarlı olduğundan emin olun.

## <a name="recommended-actions"></a>Önerilen eylemler

İlişkili etkinliklerin bu uyarıyı Doğru Pozitif durumuna çıkartır olduğunu belirlerken, uyarıyı sınıflandırarak düzeltme için şu eylemleri gerçekleştirin:

1. Gelen kutusu iletme kuralını devre dışı bırakma ve silme.
2. Gelen KutusuRule iletme türü için, kullanıcının hesap kimlik bilgilerini sıfırlayın.
3. SMTP veya ETR iletme türü için, uyarıyı oluşturan kullanıcı hesabının etkinliklerini araştırabilirsiniz.

    - Diğer şüpheli yönetici etkinliklerini araştıryın.

    - Kullanıcı hesabının kimlik bilgilerini sıfırlayın.

4. Etkilenen hesaplardan, IP adreslerinden ve şüpheli gönderenlerden gelen ek etkinliklerin olup kaynaklandığını denetleme.

## <a name="see-also"></a>Ayrıca bkz.

- [Uyarı notlamaya genel bakış](alert-grading-playbooks.md)
- [Şüpheli gelen kutusu iletme kuralları](alert-grading-playbook-inbox-forwarding-rules.md)
- [Şüpheli gelen kutusu işleme kuralları](alert-grading-playbook-inbox-manipulation-rules.md)
- [Uyarıları araştırma](investigate-alerts.md)
