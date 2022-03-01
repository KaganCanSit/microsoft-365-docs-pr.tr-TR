---
title: Negatif sonuçlarda hatalı pozitif ve yanlış negatif Outlook
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
description: Rapor İletisi özelliğini kullanarak pozitif ve yanlış negatif Outlook rapor etmeyi öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e5539525b6d752223c4895fc62ff49a90768a5b5
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/29/2021
ms.locfileid: "62997067"
---
# <a name="report-false-positives-and-false-negatives-in-outlook"></a>Negatif sonuçlarda hatalı pozitif ve yanlış negatif Outlook

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Posta kutuları olan bir Microsoft 365 kuruluşunda Exchange Online iseniz, Microsoft 365 Defender portalında Gönderiler sayfasını kullanmanızı öneririz. Daha fazla bilgi için bkz [. Gönderimler portalını kullanarak şüpheli istenmeyen posta, kimlik avı, URL'ler ve dosyaları Microsoft'a gönderme](admin-submission.md).

Karma modern kimlik doğrulaması kullanarak Exchange Online'ta veya şirket içi posta kutularında posta kutusu olan Microsoft 365 kuruluşlarında, hatalı pozitif sonuçlar (engellenen veya gereksiz posta klasörüne gönderilen iyi bir e-posta) ve hatalı negatif sonuçlar (gelen kutusuna teslim edilen istenmeyen e-posta veya kimlik avı) Exchange Online Protection'Exchange Online Protection (EOP) gönderebilirsiniz.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- En iyi kullanıcı gönderimi deneyimi için, Rapor İletisi eklentisinde veya Rapor Kimlik Avı eklentisinde kullanın.

- Tüm platformlarda Web üzerinde Outlook (Outlook, iOS, Android ve Masaüstü) Rapor İletisi ve Rapor Kimlik Avı eklentisini kullanabilirsiniz.

- Posta kutuları olan bir kuruluşun yöneticisiyseniz, Exchange Online portalında Gönderiler Microsoft 365 Defender kullanın. Daha fazla bilgi için bkz. Yönetici Gönderimi'ni kullanarak şüpheli istenmeyen posta, kimlik avı [, URL'ler ve dosyaları Microsoft'a gönderme](admin-submission.md).

- İletileri doğrudan Microsoft'a, belirttiğiniz bir posta kutusuna veya her iki posta kutusuna da gönderecek şekilde yapılandırabilirsiniz. Daha fazla bilgi için bkz [. Kullanıcı gönderimleri ilkeleri](user-submission.md).

- Rapor İletisi'nin veya Rapor Kimlik Avından Korunma eklentilerini nasıl edinerek etkinleştirebilirsiniz hakkında daha fazla bilgi için bkz. Rapor İletisi'ne veya Rapor Kimlik Avı [eklentilerini etkinleştirme](enable-the-report-message-add-in.md).

- İletileri Microsoft'a bildirme hakkında daha fazla bilgi için bkz [. İletileri ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md).

### <a name="turn-off-the-built-in-reporting-experience"></a>Yerleşik raporlama deneyimini kapatma

Outlook'de yerleşik raporlama deneyimini önerilmez, çünkü kullanıcı gönderim ilkesi [kullanamaz](./user-submission.md). Bunun yerine Rapor İletisi eklentinizi veya Rapor Kimlik Avı eklentinizi öneririz.

Bu cmdlet'i çalıştırabilirsiniz. Kurumda herhangi bir cmdlet'i veya parametreyi çalıştırmak için gereken izinleri bulmak için bkz. [Herhangi bir cmdlet'i çalıştırmak için Exchange bulma](/powershell/exchange/find-exchange-cmdlet-permissions).

Aşağıdaki PowerShell komutunu çalıştırarak, aşağıdaki tabloda yerleşik raporlama deneyimini devre dışı Web üzerinde Outlook:

```powershell
Set-OwaMailboxPolicy -Identity OwaMailboxPolicy-Default -ReportJunkEmailEnabled $false
```


## <a name="use-the-report-message-feature"></a>İletiYi Bildir özelliğini kullanma

### <a name="report-junk-and-phishing-messages"></a>Gereksiz ve kimlik avı iletilerini bildirme

Gelen Kutusu'daki veya Önemsiz E-posta dışındaki başka herhangi bir e-posta klasöründeki iletiler için, istenmeyen posta ve kimlik avı iletilerini bildirme için aşağıdaki yöntemi kullanın:

1. Seçili **iletinin sağ** üst köşesinde Diğer eylemler üç nokta öğesini seçin, açılan menüden İletiyi bildir'i seçin ve sonra da Gereksiz veya Kimlik  **Avı'ı** **seçin**.

   ![İletiyi Bildir - Diğer eylemler.](../../media/report-message-more-actions.png)

   ![Rapor İletisi - Gereksiz ve Kimlik Avı.](../../media/report-message-junk-phishing.png)

2. Seçilen iletiler analiz için Microsoft'a gönderilir ve:
   - İstenmeyen posta olarak bildirildiyse Önemsiz E-posta klasörüne taşındı.
   - Kimlik avı olarak bildirildiklerinden silindi.

### <a name="report-messages-that-are-not-junk"></a>Gereksiz iletileri bildirme

1. Seçili **iletinin sağ** üst köşesinde Diğer eylemler üç nokta öğesini seçin, açılan menüden İletiyi bildir'i seçin ve sonra da Gereksiz **Değil'i seçin**.

   ![İletiyi Bildir - Diğer eylemler.](../../media/report-message-more-actions.png)

   ![İletiyi Bildir - Gereksiz değil.](../../media/report-message-not-junk.png)

2. Seçili ileti çözümleme için Microsoft'a gönderilir ve Gelen Kutusu'na veya belirtilen başka herhangi bir klasöre taşınır.

## <a name="view-and-review-reported-messages"></a>Bildirilen iletileri görüntüleme ve gözden geçirme

Kullanıcıların Microsoft'a rapor  çekmek için şu seçenekleri kullanabilirsiniz:

- Portalda **Gönderiler** sayfasını Microsoft 365 Defender kullanın. Daha fazla bilgi için bkz [. Microsoft'a kullanıcı gönderimlerini görüntüleme](admin-submission.md#view-user-submissions-to-microsoft).
- Bildirilen iletilerin kopyalarını göndermek için bir posta akışı kuralı (aktarım kuralı olarak da bilinir) oluşturun. Yönergeler için bkz [. Kullanıcıların Microsoft'a ne bildirimini görmek için posta akışı kurallarını kullanma](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft).
