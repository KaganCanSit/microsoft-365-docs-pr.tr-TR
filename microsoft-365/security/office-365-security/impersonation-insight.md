---
title: Kimliğe bürünme içgörü
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Yöneticiler kimliğe bürünme içgörüsörü'nin nasıl çalıştığını öğrenebilir. E-posta kimlik doğrulama denetimlerini (SPF, DKIM veya DMARC) geçiremediklerinden, hangi gönderenlerin kuruluşlarına yasal olarak e-posta gönderdiğini hemen tespit ederler.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: dbaf395f10eaac7ff508b03f6f079f94bdd6cebd
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475817"
---
# <a name="impersonation-insight-in-defender-for-office-365"></a>Office 365 için Defender'de kimliğe bürünme içgörü Office 365 için Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Bu makalede açıklanan özellikler Önizleme'dedir, değişebilir ve tüm kuruluşlarda kullanılamaz.

Kimliğe Bürünme, e-posta iletisi gönderenin gerçek veya beklenen bir gönderen e-posta adresine çok benser. Alıcının güveni kazanmak için genellikle kimlik avı veya diğer tür saldırılarda kullanıcı kimliğine bürünülen gönderen e-posta adresleri kullanılır. Temelde iki tür kimliğe bürünme vardır:

- **Etki alanı kimliğe** bürünme: lila@contoso.com, kimliğine bürünülen gönderenin e-posta adresi lila@ćóntoso.com.
- **Kullanıcı kimliğe bürünme**: michelle@contoso.com, kimliğine bürünülen gönderenin e-posta adresi rnichell@contoso.com.

Etki alanı kimliğine bürünme [, etki](anti-spoofing-protection.md) alanı kimlik sahteciliğe göre farklıdır, çünkü kimliğine bürünülen etki alanı normalde gerçek, kayıtlı bir etki alanıdır. Kimliğine bürünülen etki alanındaki gönderenlerden gelen iletiler ve genellikle kimlik sahteciliği girişimlerini (SPF, DKIM ve DMARC) belirleyen normal e-posta kimlik doğrulaması denetimlerini kullanabilir.

Kimliğe Bürünme koruması, kimlik avı koruma ilkesi ayarlarının, kimlik avına özel Office 365 için Microsoft Defender. Bu ayarlar hakkında daha fazla bilgi için bkz. Kimlik avı önleme ilkelerine [yönelik kimliğe bürünme Office 365 için Microsoft Defender](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

Kimliğe bürünülen gönderenlerden veya kimliğe bürünme koruması için yapılandırmış olduğunuz gönderen etki alanlarından gelen iletileri hızla tanımlamak için Microsoft 365 Defender portalında kimliğe bürünme içgörüsteni kullanabilirsiniz.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan Kimlik avı önleme **sayfasına gitmek için** kullanın <https://security.microsoft.com/antiphishing>. Doğrudan Kimliğe Bürünme **içgörü sayfasına** gitmek için, kullanın <https://security.microsoft.com/impersonationinsight>.

- Bu makaledeki yordamları yerine Microsoft 365 Defender portalında izinlerin atanmamış olması gerekir:
  - **Kuruluş Yönetimi**
  - **Güvenlik Yöneticisi**
  - **Güvenlik Okuyucu**
  - **Genel Okuyucu**

  Daha fazla bilgi için bkz[. Microsoft 365 Defender portalına.](permissions-microsoft-365-security-center.md)

  **Not**: Kullanıcı atama Azure Active Directory ilgili kullanıcı rolüne Microsoft 365 yönetim merkezi, kullanıcılara _Microsoft 365 Defender portalında_ gerekli izinleri ve Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).

- Kimlik avı koruma ilkelerinde kimliğe bürünme korumasını etkinleştiriyor ve Office 365 için Microsoft Defender. Kimliğe Bürünme koruması varsayılan olarak etkin değildir. Daha fazla bilgi için bkz[. Kimlik avından korunma ilkelerini Office 365 için Microsoft Defender](configure-mdo-anti-phishing-policies.md).

## <a name="open-the-impersonation-insight-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında kimliğe bürünme içgörü Microsoft 365 Defender açma

1. Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler bölümünde **E-posta &** \> İşbirliği **İlkeleri'ne &** \> \> Kurallar Tehdit ilkeleri **Kimlik** avıyla **mücadele'ye** gidin. Doğrudan Kimlik avı önleme **sayfasına gitmek için** kullanın <https://security.microsoft.com/antiphishing>.

2. Kimlik avı **önleme sayfasında** kimliğe bürünme içgörü şöyle görünür:

   :::image type="content" source="../../media/m365-sc-impersonation-and-spoof-intelligence-insight.png" alt-text="Kimlik avıyla mücadele ilkesi sayfasında kimliğe bürünme içgörü ve kimlik sahteci zekası" lightbox="../../media/m365-sc-impersonation-and-spoof-intelligence-insight.png":::

   Bu içgörüde iki mod vardır:

    - **Bilgi modu**: Kimlik avı önleme ilkelerinde kimliğe bürünme koruması etkin ve yapılandırılmışsa, bu içgörü son yedi gün içinde kimliğine bürünülen etki alanlarından ve kimliğine bürünülen kullanıcılardan (gönderenler) gelen algılanan iletilerin sayısını gösterir. Bu, tüm kimlik avı önleme ilkelerinden kimliğine bürünülen tüm gönderenlerin toplamıdır.
    - Eğer **mod:** Kimliğe bürünme koruması etkin ve kimlik avı önleme ilkeleri arasında yapılandırılmazsa, bu içgörü size son yedi gün içinde kimliğe  bürünme koruma yeteneklerimiz tarafından kaç ileti algılandığından emin olur.

Kimliğe bürünme algılamaları hakkında bilgileri görüntülemek için kimliğe bürünme **bilgisinde** Kimliğe bürünmeleri görüntüle'ye tıklayın.

   > [!NOTE]
   > Bilgi spoof Intelligence içgörü hakkında bilgi için bkz [. EOP'de Spoof Intelligence içgörü](learn-about-spoof-intelligence.md).

## <a name="view-information-about-messages-from-senders-in-impersonated-domains"></a>Kimliğine bürünülen etki alanlarındaki gönderenlerden gelen iletiler hakkında bilgi görüntüleme

Kimliğe **bürünme içgörüs** belgesinde Kimliğe bürünmeleri görüntüle'yi tıklatmaktan sonra görüntülenen Kimliğe Bürünme içgörü sayfasında Etki Alanları sekmesinin **seçili** olduğunu doğrulayın. Etki **Alanları** sekmesi aşağıdaki bilgileri içerir:

- **Gönderen Etki** Alanı: Kimliğe bürünen etki alanı, e-posta iletisi göndermek için kullanılan etki alanıdır.
- **İleti sayısı**: Son 7 gün içinde gönderen etki alanının kimliğine bürünen ileti sayısı.
- **Kimliğe Bürünme** türü: Bu değer kimliğe bürünülen kimliğin algılanan konumunu gösterir (örneğin, **Adreste Etki Alanı**).
- **Kimliğine bürünülen** etki alanı/etki alanı: Kimliğine bürünülen etki alanı, kimlik avı önleme ilkesinde kimliğe bürünme koruması için yapılandırılan etki alanına çok benzer.
- **Etki alanı türü**: Bu değer, iç etki **alanları için Şirket etki** alanı veya özel etki **alanları için Özel** etki alanıdır.
- **İlke**: Kimliğine bürünülen etki alanını algı eden kimlik avı önleme ilkesi.
- **Kimliğe bürünülme** izni verildi: Aşağıdaki değerlerden biri:
  - **Evet**: Etki alanı, kimlik avı önleme ilkesinde güvenilen etki alanı (kimliğe bürünme koruması için bir özel durum) olarak yapılandırılmıştır. Kimliğine bürünülen etki alanındaki gönderenlerden gelen iletiler algılandı, ancak izin verildi.
  - **Hayır**: Etki alanı, kimlik avı önleme ilkesinde kimliğe bürünme koruması için yapılandırılmıştır. Kimliğine bürünülen etki alanındaki gönderenlerden gelen iletiler, kimlik avı önleme ilkesinde kimliğine bürünülen etki alanları için yapılan eyleme dayalı olarak algılandı ve eylem  edildi.

Sonuçları sıralamak için seçili sütun başlıklarına tıkebilirsiniz.

Sonuçları filtrelemek için Arama simgesini ![kullanabilirsiniz.](../../media/m365-cc-sc-search-icon.png) **Sonuçları** filtrelemek için virgülle ayrılmış değer listesi girmek için arama kutusu.

### <a name="view-details-about-messages-from-senders-in-impersonated-domains"></a>Kimliğine bürünülen etki alanlarındaki gönderenlerden gelen iletiler hakkında ayrıntıları görüntüleme

Kimliğe **Bürünme** **içgörü** sayfasındaki Etki Alanları sekmesinde, kullanılabilir kimliğe bürünme algılamalarından birini seçin. Görüntülenen ayrıntılar açılır içeriği, aşağıdaki bilgileri ve özellikleri içerir:

- **Değiştirlenecek kimliğe bürünme** ilkesi: Değiştirmek istediğiniz etkilenen kimlik avı önleme ilkesine seçin. Yalnızca kimliğe bürünülen etki alanının ilkede tanımlandığı ilkeler kullanılabilir. Kimliğe bürünülen etki alanını algılamadan aslında hangi ilkenin sorumlu olduğunu görmek için (büyük olasılıkla alıcıya ve ilkenin önceliğe bağlı olarak) önceki sayfaya bakın.
- **Kimliğe bürünme** izni verilenler listesine ekleyin: Seçtiğiniz kimlik avı önleme ilkesine göre göndereni Güvenilen gönderenler ve etki **alanlarından (** kimliğe bürünme özel durumları) eklemek veya kaldırmak için bu iki durumlu düğmeyi kullanın:
  - Bu **girdinin kimliğine bürünme** değeri Hayır **ise, iki** durumlu düğme kapalıdır. Bu etki alanındaki tüm gönderenlerin kimliğe bürünme korumasıyla değerlendirmesini engellemesini korumak için, iki durumlu düğmeyi Açık: ![Açık olarak kaydırın](../../media/scc-toggle-on.png). Etki alanı, kimlik avı önleme **ilkesine** yönelik kimliğe bürünme koruma ayarlarında Güvenilen etki alanları listesine eklenir.
  - Bu **girdinin kimliğine bürünme** değeri Evet **ise, iki** durumlu düğme açık olur. Bu etki alanındaki tüm gönderenleri kimliğe bürünme korumasıyla değerlendirmeye geri dönmek için, iki durumlu düğmeyi kapalı: ![Kapalı olarak kaydırın](../../media/scc-toggle-off.png). Etki alanı, kimlik avı önleme **ilkesine** bağlı kimliğe bürünme koruma ayarlarında Güvenilen etki alanları listesinden kaldırılır.
- Bunu neden yakaladığımız.
- Ne yapmak gerekir?
- Kimliğine bürünülen etki alanını liste eden bir etki alanı özeti.
- Gönderen hakkında WhoIs verileri.
- Gönderen hakkında ek ayrıntıları [görmek için Threat Explorer'ı](threat-explorer.md) açma bağlantısı.
- Aynı gönderenden gelen ve organizasyona teslim edilen benzer iletiler.

## <a name="view-information-about-messages-from-impersonated-senders"></a>Kimliğine bürünülen gönderenlerden gelen iletiler hakkında bilgi görüntüleme

Kimliğe **bürünme bilgisinde** Kimliğe bürünmeleri  görüntüle'ye tıklarken görüntülenen Kimliğe Bürünme içgörü sayfasında, Kullanıcılar **sekmesine** tıklayın. Kullanıcılar **sekmesi** aşağıdaki bilgileri içerir:

- **Gönderen**: E-posta iletisi gönderen kimliğine bürünen gönderenin e-posta adresi.
- **İleti sayısı**: Son 7 gün içinde kimliğine bürünen gönderenden gelen iletilerin sayısı.
- **Kimliğe bürünme** türü: Bu değer görünen **ad olan Kullanıcı'dır**.
- **Kimliğine bürünülen** kullanıcılar: Kimliğine bürünülen gönderenin e-posta adresi; kimlik avı önleme ilkesinde kimliğe bürünme koruması için yapılandırılan kullanıcıya çok benzer.
- **Kullanıcı türü**: Bu değer, uygulanan koruma türünü gösterir (örneğin, **Korumalı kullanıcı veya Posta Kutusu** **Zekası**).
- **İlke**: Kimliğine bürünülen göndereni algı eden kimlik avı önleme ilkesi.
- **Kimliğe bürünülme** izni verildi: Aşağıdaki değerlerden biri:
  - **Evet**: Gönderen, kimlik avı önleme ilkesinde güvenilen kullanıcı olarak yapılandırıldı (kimliğe bürünme koruması için bir özel durum). Kimliğine bürünülen gönderenden gelen iletiler algılandı, ancak izin verildi.
  - **Hayır**: Gönderen, kimlik avı önleme ilkesinde kimliğe bürünme koruması için yapılandırılmıştır. Kimliğine bürünülen gönderenden gelen iletiler, kimlik avı önleme ilkesinde kimliğine bürünülen kullanıcıların eylemine dayalı olarak algılanır ve üzerinde eylem  edilmiştir.

Sonuçları sıralamak için seçili sütun başlıklarına tıkebilirsiniz.

Sonuçları filtrelemek için, Gönderene filtre uygulama  kutusunu kullanarak sonuçları filtrelemek üzere virgülle ayrılmış bir değer listesi girebilirsiniz.

### <a name="view-details-about-messages-from-impersonated-senders"></a>Kimliğine bürünülen gönderenlerden gelen iletiler hakkında ayrıntıları görüntüleme

Kimliğe **Bürünme** **içgörü** sayfasındaki Kullanıcılar sekmesinde, kullanılabilir kimliğe bürünme algılamalarından birini seçin. Görüntülenen ayrıntılar açılır içeriği, aşağıdaki bilgileri ve özellikleri içerir:

- **Değiştirlenecek kimliğe bürünme** ilkesi: Değiştirmek istediğiniz etkilenen kimlik avı önleme ilkesine seçin. Yalnızca kimliğe bürünülen gönderenin tanımlandığı ilkeler kullanılabilir. Kimliğe bürünülen göndereni algılamaktan aslında hangi ilkenin sorumlu olduğunu görmek için (büyük olasılıkla alıcıya ve ilkenin önceliğe bağlı olarak) önceki sayfaya bakın.
- **Kimliğe bürünme** izni verilenler listesine ekleyin: Seçtiğiniz kimlik avı önleme ilkesine göre göndereni Güvenilen gönderenler ve etki **alanlarından (** kimliğe bürünme özel durumları) eklemek veya kaldırmak için bu iki durumlu düğmeyi kullanın:
  - Bu **girdinin kimliğine bürünme** değeri Hayır **ise, iki** durumlu düğme kapalıdır. Gönderenin kimliğe bürünme korumasıyla değerlendirmesini muaf yapmak için, iki durumlu düğmeyi Açık: ![Açık olarak kaydırın](../../media/scc-toggle-on.png). Gönderen, kimlik avı önleme **ilkesine** yönelik kimliğe bürünme koruma ayarlarında Güvenilen kullanıcılar listesine eklenir.
  - Bu **girdinin kimliğine bürünme** değeri Evet **ise, iki** durumlu düğme açık olur. Göndereni kimliğe bürünme korumasıyla değerlendirmeye geri dönmek için, iki durumlu düğmeyi kapalı: ![Kapalı olarak kaydırın](../../media/scc-toggle-off.png). Gönderen, kimlik avı önleme **ilkesine** yönelik kimliğe bürünme koruma ayarlarında Güvenilen kullanıcılar listesinden kaldırılır.
- Bunu neden yakaladığımız.
- Ne yapmak gerekir?
- Kimliğine bürünülen göndereni liste eden bir gönderen özeti.
- Gönderen hakkında WhoIs verileri.
- Gönderen hakkında ek ayrıntıları [görmek için Threat Explorer'ı](threat-explorer.md) açma bağlantısı.
- Aynı gönderenden gelen ve organizasyona teslim edilen benzer iletiler.
