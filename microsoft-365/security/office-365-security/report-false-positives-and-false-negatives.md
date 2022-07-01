---
title: Outlook'ta yanlış pozitifleri ve yanlış negatifleri bildirme
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
description: Rapor İletisi özelliğini kullanarak Outlook'ta hatalı pozitif ve hatalı negatifleri bildirmeyi öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 60f9a9eff9694752630170991b7a800f52a2952d
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66602148"
---
# <a name="report-false-positives-and-false-negatives-in-outlook"></a>Outlook'ta yanlış pozitifleri ve yanlış negatifleri bildirme

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Exchange Online posta kutuları olan bir Microsoft 365 kuruluşunda yöneticiyseniz, Microsoft 365 Defender portalındaki **Gönderimler** sayfasını kullanmanızı öneririz. Daha fazla bilgi için bkz [. Şüpheli istenmeyen postaları, kimlik avı, URL'leri ve dosyaları Microsoft'a göndermek için Gönderimler portalını kullanma](admin-submission.md).

Karma modern kimlik doğrulaması kullanarak Exchange Online veya şirket içi posta kutularında posta kutuları olan Microsoft 365 kuruluşlarında, hatalı pozitifler (engellenmiş veya gereksiz klasöre gönderilmiş iyi e-postalar) ve hatalı negatifler (gelen kutusuna teslim edilen istenmeyen e-posta veya kimlik avı) Exchange Online Protection (EOP) adresine gönderebilirsiniz.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- En iyi kullanıcı gönderimi deneyimi için Rapor İletisi eklentisini veya Rapor Kimlik Avı eklentisini kullanın.

- Rapor İletisi eklentisi ve Rapor Kimlik Avı eklentisi tüm platformlarda (Web üzerinde Outlook, iOS, Android ve Masaüstü) Outlook için çalışır.

- Exchange Online posta kutuları olan bir kuruluşta yöneticiyseniz Microsoft 365 Defender portalındaki Gönderimler portalını kullanın. Daha fazla bilgi için bkz. [Microsoft'a şüpheli istenmeyen posta, kimlik avı, URL'ler ve dosyalar göndermek için Yönetici Gönderimini kullanma](admin-submission.md).

- İletileri doğrudan Microsoft'a, belirttiğiniz bir posta kutusuna veya her ikisine birden gönderecek şekilde yapılandırabilirsiniz. Daha fazla bilgi için bkz. [Kullanıcı gönderim ilkeleri](user-submission.md).

- Rapor İletisi veya Rapor Kimlik Avı eklentilerini alma ve etkinleştirme hakkında daha fazla bilgi için bkz. [Rapor İletisini veya Rapor Kimlik Avı eklentilerini etkinleştirme](enable-the-report-message-add-in.md).

- İletileri Microsoft'a bildirme hakkında daha fazla bilgi için bkz. [İletileri ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md).

bir iletinin içeriğini belirlemek için kullanıcı gönderimlerini kolayca araştırmak ve uygun düzeltme eylemini uygulayarak gönderime yanıt vermek için Office 365 için Microsoft Defender nasıl kullanabileceğinizi öğrenmek için bu kısa videoyu izleyin. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWBHof]

## <a name="use-the-report-message-feature"></a>Rapor İletisi özelliğini kullanma

### <a name="report-junk-and-phishing-messages"></a>Gereksiz iletileri ve kimlik avı iletilerini bildirme

Gelen Kutusu'ndaki iletiler veya Gereksiz E-posta dışındaki herhangi bir e-posta klasöründe istenmeyen posta ve kimlik avı iletilerini bildirmek için aşağıdaki yöntemi kullanın:

1. Seçili iletinin sağ üst köşesindeki **Diğer eylemler** üç nokta'yı seçin, açılan menüden **Rapor iletisi'ni** ve ardından **Gereksiz** veya **Kimlik Avı'nı** seçin.

   :::image type="content" source="../../media/report-message-more-actions.png" alt-text="Diğer eylemler simgesi" lightbox="../../media/report-message-more-actions.png":::

   :::image type="content" source="../../media/report-message-junk-phishing.png" alt-text="Rapor İletisi bölmesinde gereksiz ve kimlik avı seçeneği" lightbox="../../media/report-message-junk-phishing.png":::

2. Seçilen iletiler analiz için Microsoft'a gönderilir ve:
   - İstenmeyen posta olarak bildirildiyse Gereksiz E-posta klasörüne taşındı.
   - Kimlik avı olarak bildirildiyse silindi.

### <a name="report-messages-that-are-not-junk"></a>Gereksiz olmayan iletileri bildirme

1. Seçili iletinin sağ üst köşesindeki **Diğer eylemler** üç nokta'yı seçin, açılan menüden **Rapor iletisi'ni** ve ardından **Gereksiz Değil'i** seçin.

   :::image type="content" source="../../media/report-message-more-actions.png" alt-text="Daha fazla eylem sağlayan simge" lightbox="../../media/report-message-more-actions.png":::

   :::image type="content" source="../../media/report-message-not-junk.png" alt-text="Rapor İletisi bölmesinin altındaki Gereksiz Değil seçeneği" lightbox="../../media/report-message-not-junk.png":::

2. Seçilen ileti analiz için Microsoft'a gönderilir ve Gelen Kutusu'na veya belirtilen başka bir klasöre taşınır.

## <a name="view-and-review-reported-messages"></a>Bildirilen iletileri görüntüleme ve gözden geçirme

Kullanıcıların Microsoft'a bildirmiş olduğu iletileri gözden geçirmek için şu seçeneklere sahipsiniz:

- Microsoft 365 Defender portalındaki **Gönderimler** sayfasını kullanın. Daha fazla bilgi için bkz. [Microsoft'a kullanıcı gönderimlerini görüntüleme](admin-submission.md#view-user-submissions-to-microsoft).
- Bildirilen iletilerin kopyalarını göndermek için bir posta akışı kuralı (taşıma kuralı olarak da bilinir) oluşturun. Yönergeler için bkz. [Kullanıcıların Microsoft'a bildirdiğini görmek için posta akışı kurallarını kullanma](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-see-what-users-are-reporting-to-microsoft).
