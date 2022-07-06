---
title: Gönderimleri yönetme
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: seo-marvel-apr2020
description: Yöneticiler, Microsoft 365 Defender portalında Gönderiler portalını kullanarak engellenen, şüpheli e-posta, şüpheli kimlik avı e-postası, istenmeyen posta, diğer zararlı olabilecek iletiler, URL'ler ve e-posta eklerini yeniden keşfetmek üzere Microsoft'a yasal e-posta göndermeyi öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 17083a248e31d5ae1eff3c088497f071bcac643b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66639456"
---
# <a name="use-the-submissions-portal-to-submit-suspected-spam-phish-urls-legitimate-email-getting-blocked-and-email-attachments-to-microsoft"></a>Şüpheli istenmeyen posta, kimlik avı, URL'ler, engellenen meşru e-postalar ve e-posta eklerini Microsoft'a göndermek için Gönderimler portalını kullanın

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)

Exchange Online posta kutularına sahip Microsoft 365 kuruluşlarında, yöneticiler e-posta iletilerini, URL'leri ve ekleri tarama için Microsoft'a göndermek için Microsoft 365 Defender portalındaki Gönderimler portalını kullanabilir.

Analiz için bir e-posta iletisi gönderdiğinizde şunları alırsınız:

- **E-posta kimlik doğrulaması denetimi: E-posta** kimlik doğrulamasının teslim edildiğinde geçirilip geçirilmediğine veya başarısız olmasına ilişkin ayrıntılar.
- **İlke isabetleri**: Hizmet filtresi kararlarımızı geçersiz kılarak kiracınıza gelen e-postaya izin veren veya engelleyen ilkeler hakkında bilgiler.
- **Payload reputation/detonation**: İletideki URL'lerin ve eklerin güncel incelemesi.
- **Not veren analizi**: İletilerin kötü amaçlı olup olmadığını onaylamak için insan not verenler tarafından yapılan gözden geçirme.

> [!IMPORTANT]
> Payload reputation/detonation ve grader analizi tüm kiracılarda yapılmaz. Verilerin uyumluluk amacıyla kiracı sınırından ayrılması gerekmediğinde bilgilerin kuruluş dışına çıkışı engellenir.

E-posta iletilerini, URL'leri ve ekleri Microsoft'a göndermenin diğer yolları için bkz. [İletileri ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md).

Değerlendirme için Microsoft'a ileti göndermek üzere Office 365 için Microsoft Defender'daki yönetici gönderimlerini kullanmayı öğrenmek için bu kısa videoyu izleyin.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWBLPn]

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını adresinde <https://security.microsoft.com/>açarsınız. Doğrudan **Gönderimler** sayfasına gitmek için kullanın <https://security.microsoft.com/reportsubmission>.

- Microsoft'a ileti ve dosya göndermek için aşağıdaki rollerden birine sahip olmanız gerekir:
  - [Microsoft 365 Defender portalında](permissions-microsoft-365-security-center.md) **Güvenlik Yöneticisi** veya **Güvenlik Okuyucusu**.

    Bu rollerden birinin, bu makalenin sonraki bölümlerinde açıklandığı gibi [özel posta kutusuna kullanıcı gönderimlerini görüntülemek için](#view-user-submissions-to-microsoft) gerekli olduğunu unutmayın.

- Posta kutusunda hala kullanılabiliyorsa ve kullanıcı veya başka bir yönetici tarafından temizlenmediyse, yöneticiler 30 gün kadar eski iletiler gönderebilir.

- Yönetici gönderimleri aşağıdaki fiyatlarla kısıtlanır:
  - Herhangi bir 15 dakika içinde en fazla gönderim: 150 gönderim
  - 24 saatlik bir süre içinde aynı gönderimler: 3 gönderim
  - 15 dakikalık bir süre içinde aynı gönderimler: 1 gönderim

- Kullanıcıların iletileri ve dosyaları Microsoft'a nasıl gönderebileceği hakkında daha fazla bilgi için bkz. [İletileri ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md).

## <a name="report-suspicious-content-to-microsoft"></a>Şüpheli içeriği Microsoft'a bildirme

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**Eylemler & Gönderimler sayfasındaki Gönderimler** \> **sayfasına gidin**. Doğrudan **Gönderimler** sayfasına gitmek için kullanın <https://security.microsoft.com/reportsubmission>.

2. **Gönderimler** sayfasında, raporlamak istediğiniz içerik türüne göre **E-postalar** veya **E-posta ekleri** veya **URL'ler** sekmesinin seçili olduğunu doğrulayın ve analiz için Microsoft'a gönder simgesine tıklayın![.](../../media/m365-cc-sc-create-icon.png) **Analiz için Microsoft'a gönderin**.

3. Aşağıdaki bölümlerde açıklandığı gibi ilgili içerik türünü (e-posta, URL veya e-posta eki) göndermek **için görünen Analiz için Microsoft'a gönder** açılır penceresini kullanın.

   > [!NOTE]
   > Verilerin ortamdan ayrılmasına izin verilmeyen bulutlarda dosya ve URL gönderimleri kullanılamaz. Dosya veya URL'yi seçme özelliği gri görünür.

### <a name="notify-users-from-within-the-portal"></a>Portaldan kullanıcılara bildirme

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>**, E-posta & işbirliği** \> **Gönderimleri sayfasındaki Gönderimler** **sayfasına gidin**. Doğrudan **Gönderimler** sayfasına gitmek için kullanın <https://security.microsoft.com/reportsubmission>.

2. **Gönderimler** sayfasında **, Kullanıcı tarafından bildirilen iletiler** sekmesini ve ardından işaretlemek ve bildirmek istediğiniz iletiyi seçin.

3. **Farklı işaretle ve bildir** açılan listesini seçin ve ardından **Tehdit bulunamadı** \> **Kimlik Avı** veya **Gereksiz'i** seçin.

   :::image type="content" source="../../media/unified-submission-user-reported-message.png" alt-text="Gönderimler sayfası" lightbox="../../media/unified-submission-user-reported-message.png":::

Bildirilen ileti hatalı pozitif veya hatalı negatif olarak işaretlenir. Portalın içinden iletiyi bildiren kullanıcıya otomatik olarak bir e-posta bildirimi gönderilir.

### <a name="submit-a-questionable-email-to-microsoft"></a>Microsoft'a sorgulanabilir bir e-posta gönderme

1. **Gönderim türünü seçin** kutusunda, açılan listede **E-posta'nın** seçili olduğunu doğrulayın.

2. **Ağ iletisi kimliğini ekleyin veya e-posta dosyasını karşıya yükleyin** bölümünde aşağıdaki seçeneklerden birini kullanın:
   - **E-posta ağ iletisi kimliğini ekleyin**: Bu, karantinaya alınan iletilerdeki **X-MS-Exchange-Organization-Network-Message-Id** üst bilgisinde veya **X-MS-Office365-Filtering-Correlation-Id** üst bilgisinde bulunan bir GUID değeridir.
   - **E-posta dosyasını (.msg veya .eml) karşıya yükleyin**: **Dosyalara gözat'a** tıklayın. Açılan iletişim kutusunda .eml veya .msg dosyasını bulup seçin ve **aç'a** tıklayın.

3. **Sorun yaşayan bir alıcı seçin** kutusunda, ilke denetimini çalıştırmak istediğiniz alıcıyı belirtin. İlke denetimi, e-postanın kullanıcı veya kuruluş ilkeleri nedeniyle taramayı atlayıp atlamadığını belirler.

4. **Microsoft'a göndermek için bir neden seçin** bölümünde aşağıdaki seçeneklerden birini belirleyin:
   - **Engellenmemesi gerekir (Hatalı pozitif)**
   - **Engellenmiş olmalıdır (Hatalı negatif)**: **E-posta görüntülenen olarak kategorilere ayrılmış olmalıdır** bölümünde aşağıdaki değerlerden birini seçin (emin değilseniz en iyi kararınızı kullanın):
     - **Phish**
     - **Malware**
     - **Spam**

5. İşiniz bittiğinde **Gönder'e** tıklayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/submission-flyout-email.png" alt-text="Yeni URL gönderme işlemi" lightbox="../../media/submission-flyout-email.png":::

### <a name="send-a-suspect-url-to-microsoft"></a>Şüpheli URL'yi Microsoft'a gönderme

1. **Gönderim türünü seçin** kutusunda açılan listeden **URL'yi** seçin.

2. Görüntülenen **URL** kutusuna tam URL'yi girin (örneğin, `https://www.fabrikam.com/marketing.html`).

3. **Microsoft'a göndermek için bir neden seçin** bölümünde aşağıdaki seçeneklerden birini belirleyin:
   - **Engellenmemesi gerekir (Hatalı pozitif)**
   - **Engellenmiş olmalıdır (Hatalı negatif)**: **Bu URL görüntülenen bölüm olarak kategorilere ayrılmış olmalıdır** bölümünde aşağıdaki değerlerden birini seçin (emin değilseniz en iyi kararınızı kullanın):
     - **Phish**
     - **Malware**

4. İşiniz bittiğinde **Gönder'e** tıklayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/submission-url-flyout.png" alt-text="Yeni E-posta gönderme işlemi" lightbox="../../media/submission-url-flyout.png":::

### <a name="submit-a-suspected-email-attachment-to-microsoft"></a>Şüpheli e-posta eklerini Microsoft'a gönderme

1. **Gönderim türünü seçin** kutusunda açılan listeden **E-posta eki'ni** seçin.

2. Görüntülenen **Dosya** bölümünde **Dosyalara gözat'a** tıklayın. Açılan iletişim kutusunda dosyayı bulun ve seçin ve **aç'a** tıklayın.

3. **Microsoft'a göndermek için bir neden seçin** bölümünde aşağıdaki seçeneklerden birini belirleyin:
   - **Engellenmemesi gerekir (Hatalı pozitif)**
   - **Engellenmiş olmalıdır (Hatalı negatif)**: **Bu dosya görüntülenen bölüm olarak kategorilere ayrılmış olmalıdır** bölümünde aşağıdaki değerlerden birini seçin (emin değilseniz en iyi kararınızı kullanın):
     - **Phish**
     - **Malware**

4. İşiniz bittiğinde **Gönder'e** tıklayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/submission-file-flyout.png" alt-text="Yeni Ek gönderme işlemi" lightbox="../../media/submission-file-flyout.png":::

> [!NOTE]
> Kötü amaçlı yazılım filtreleme, ileti eklerini Kötü Amaçlı Yazılım Uyarısı Text.txt dosyasıyla değiştirdiyse, özgün ekleri içeren özgün iletiyi karantinadan göndermeniz gerekir. Karantinaya alma ve kötü amaçlı yazılım hatalı pozitifleri içeren iletilerin nasıl serbest bırakıldığı hakkında daha fazla bilgi için bkz. [Karantinaya alınan iletileri ve dosyaları yönetici olarak yönetme](manage-quarantined-messages-and-files.md).

## <a name="view-email-admin-submissions-to-microsoft"></a>Microsoft'a e-posta yöneticisi gönderimlerini görüntüleme

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**Eylemler & Gönderimler sayfasındaki Gönderimler** \> **sayfasına gidin**. Doğrudan **Gönderimler** sayfasına gitmek için kullanın <https://security.microsoft.com/reportsubmission>.

2. **Gönderimler** sayfasında **E-postalar** sekmesinin seçili olduğunu doğrulayın.

   - Kullanılabilir bir sütun üst bilgisine tıklayarak girişleri sıralayabilirsiniz. İhtiyacınız olan sütunları seçmek için **Sütunları özelleştir'e** tıklayın. Tüm sütunlar seçilebilir ve gönderim kılavuzunda gösterilebilir. Varsayılan değerler yıldız işaretiyle (<sup>\*</sup>):
     - **Gönderim adı**<sup>\*</sup>
     - **Gönderen**<sup>\*</sup>
     - **Alıcı**
     - **Gönderilme tarihi**<sup>\*</sup>
     - **Gönderme nedeni**<sup>\*</sup>
     - **Durum**<sup>\*</sup>
     - **Sonuç**<sup>\*</sup>
     - **Filtre kararı**
     - **Teslim/Engelleme nedeni**
     - **Gönderim Kimliği**
     - **Ağ İletisi Kimliği/Nesne Kimliği**
     - **Yön**
     - **Gönderen IP'i**
     - **Toplu uyumlu düzey (BCL)**
     - **Hedef**
     - **İlke eylemi**
     - **Gönderen**
     - **Kimlik avı benzetimi**
     - **Etiketler**<sup>\*</sup>
     - **İzin ver**

     İşiniz bittiğinde **Uygula'ya** tıklayın.

     > [!div class="mx-imgBorder"]
     > :::image type="content" source="../../media/email-admin-submission-customize-columns.png" alt-text="E-posta yöneticisi gönderimleri için sütun seçeneğini özelleştirin." lightbox="../../media/email-admin-submission-customize-columns.png":::

   - Girişleri filtrelemek için **Filtre'ye** tıklayın. Kullanılabilir filtreler şunlardır:
     - **Gönderilme tarihi**: **Başlangıç tarihi** ve **Bitiş tarihi**.
     - **Gönderme Kimliği**: Her gönderime atanan bir GUID değeri.
     - **Ağ İletisi Kimliği**
     - **Gönderen**
     - **Alıcı**
     - **Ad**
     - **Gönderen**
     - **Gönderme nedeni**
     - **Durum**
     - **Etiketler**

     İşiniz bittiğinde **Uygula'ya** tıklayın.

     > [!div class="mx-imgBorder"]
     > :::image type="content" source="../../media/email-admin-submission-filters.png" alt-text="E-posta yöneticisi gönderimleri için filtre seçenekleri." lightbox="../../media/email-admin-submission-filters.png":::

   - Girişleri gruplandırmak için **Gruplandır'a** tıklayın ve açılan listeden aşağıdaki değerlerden birini seçin:
     - **Yok**
     - **Neden**
     - **Durum**
     - **Sonuç**
     - **Etiketler**

   - Girdileri dışarı aktarmak için **Dışarı Aktar'a** tıklayın. Görüntülenen iletişim kutusunda .csv dosyasını kaydedin.

## <a name="view-email-attachment-admin-submissions-to-microsoft"></a>Microsoft'a e-posta eki yönetici gönderimlerini görüntüleme

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**Eylemler & Gönderimler sayfasındaki Gönderimler** \> **sayfasına gidin**. Doğrudan **Gönderimler** sayfasına gitmek için kullanın <https://security.microsoft.com/reportsubmission>.

2. **Gönderimler** sayfasında **, E-posta ekleri** sekmesinin seçili olduğunu doğrulayın.

   - Kullanılabilir bir sütun üst bilgisine tıklayarak girişleri sıralayabilirsiniz. İhtiyacınız olan sütunları seçmek için **Sütunları özelleştir'e** tıklayın. Tüm sütunlar seçilebilir ve gönderim kılavuzunda gösterilebilir. Varsayılan değerler yıldız işaretiyle (<sup>\*</sup>):
     - **Ek adı**<sup>\*</sup>
     - **Gönderilme tarihi**<sup>\*</sup>
     - **Gönderme nedeni**<sup>\*</sup>
     - **Durum**<sup>\*</sup>
     - **Sonuç**<sup>\*</sup>
     - **Filtre kararı**
     - **Teslim/Engelleme nedeni**
     - **Gönderim Kimliği**
     - **Nesne Kimliği**
     - **İlke eylemi**
     - **Gönderen**
     - **Etiketler**<sup>\*</sup>
     - **İzin ver**

     İşiniz bittiğinde **Uygula'ya** tıklayın.

     :::image type="content" source="../../media/email-attachment-admin-submission-customize-columns.png" alt-text="E-posta eki yönetici gönderimleri için sütun seçeneklerini özelleştirin.":::

   - Girişleri filtrelemek için **Filtre'ye** tıklayın. Kullanılabilir filtreler şunlardır:
     - **Gönderilme tarihi**: **Başlangıç tarihi** ve **Bitiş tarihi**.
     - **Gönderme Kimliği**: Her gönderime atanan bir GUID değeri.
     - **Ek dosya adı**
     - **Gönderen**
     - **Gönderme nedeni**
     - **Durum**
     - **Etiketler**

     İşiniz bittiğinde **Uygula'ya** tıklayın.

     :::image type="content" source="../../media/email-attachment-admin-submission-filters.png" alt-text="E-posta eki yönetici gönderimleri için filtre seçenekleri.":::

   - Girişleri gruplandırmak için **Gruplandır'a** tıklayın ve açılan listeden aşağıdaki değerlerden birini seçin:
     - **Yok**
     - **Neden**
     - **Durum**
     - **Sonuç**
     - **Etiketler**

   - Girdileri dışarı aktarmak için **Dışarı Aktar'a** tıklayın. Görüntülenen iletişim kutusunda .csv dosyasını kaydedin.

## <a name="view-urls-admin-submissions-to-microsoft"></a>Microsoft'a yapılan URL'ler yönetici gönderimlerini görüntüleme

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**Eylemler & Gönderimler sayfasındaki Gönderimler** \> **sayfasına gidin**. Doğrudan **Gönderimler** sayfasına gitmek için kullanın <https://security.microsoft.com/reportsubmission>.

2. **Gönderimler** sayfasında **URL'ler** sekmesinin seçili olduğunu doğrulayın.

   - Kullanılabilir bir sütun üst bilgisine tıklayarak girişleri sıralayabilirsiniz. İhtiyacınız olan sütunları seçmek için **Sütunları özelleştir'e** tıklayın. Tüm sütunlar seçilebilir ve gönderim kılavuzunda gösterilebilir. Varsayılan değerler yıldız işaretiyle (<sup>\*</sup>):
     - **URL**<sup>\*</sup>
     - **Gönderilme tarihi**<sup>\*</sup>
     - **Gönderme nedeni**<sup>\*</sup>
     - **Durum**<sup>\*</sup>
     - **Sonuç**<sup>\*</sup>
     - **Filtre kararı**
     - **Teslim/Engelleme nedeni**
     - **Gönderim Kimliği**
     - **Nesne Kimliği**
     - **İlke eylemi**
     - **Gönderen**
     - **Etiketler**<sup>\*</sup>
     - **İzin ver**

     İşiniz bittiğinde **Uygula'ya** tıklayın.

     :::image type="content" source="../../media/url-admin-submission-customize-columns.png" alt-text="URL yöneticisi gönderimleri için sütun seçeneklerini özelleştirin.":::

   - Girişleri filtrelemek için **Filtre'ye** tıklayın. Kullanılabilir filtreler şunlardır:
     - **Gönderilme tarihi**: **Başlangıç tarihi** ve **Bitiş tarihi**.
     - **Gönderme Kimliği**: Her gönderime atanan bir GUID değeri.
     - **URL**
     - **Gönderen**
     - **Gönderme nedeni**
     - **Durum**
     - **Etiketler**

     İşiniz bittiğinde **Uygula'ya** tıklayın.

     :::image type="content" source="../../media/url-admin-submission-customize-columns.png" alt-text="URL yöneticisi gönderimleri için filtre seçenekleri.":::

   - Girişleri gruplandırmak için **Gruplandır'a** tıklayın ve açılan listeden aşağıdaki değerlerden birini seçin:
     - **Yok**
     - **Neden**
     - **Durum**
     - **Sonuç**
     - **Etiketler**

   - Girdileri dışarı aktarmak için **Dışarı Aktar'a** tıklayın. Görüntülenen iletişim kutusunda .csv dosyasını kaydedin.

### <a name="admin-submission-result-details"></a>gönderim sonucu ayrıntılarını Yönetici

Yönetici gönderimlerinde gönderilen iletiler gözden geçirilir ve sonuçlar gönderim ayrıntıları açılır öğesinde gösterilir:

- Teslim sırasında gönderenin e-posta kimlik doğrulamasında hata olup olmadığı.
- İletiyle ilgili kararı etkilemiş veya geçersiz kılmış olabilecek bir ilke eşleşmesi hakkında bilgi.
- İletide yer alan URL’lerin veya dosyaların kötü amaçlı olup olmadığını görmek için geçerli etkisizleştirme sonuçları.
- Not verenlerden geri bildirim.

Geçersiz kılma bulunduysa, sonucun birkaç dakika içinde kullanılabilir olması gerekir. E-posta kimlik doğrulamasında bir sorun yoksa veya teslim bir geçersiz kılmadan etkilenmediyse, not verenlerin geri bildirimleri bir gün kadar sürebilir.

## <a name="view-user-submissions-to-microsoft"></a>Microsoft'a kullanıcı gönderimlerini görüntüleme

[Rapor İletisi eklentisini](enable-the-report-message-add-in.md), [Rapor Kimlik Avı eklentisini](enable-the-report-phish-add-in.md) dağıttıysanız veya kişiler [Web üzerinde Outlook'da yerleşik raporlamayı](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md) kullanıyorsa, **kullanıcının bildirdiği ileti** sekmesinde kullanıcıların ne bildirdiğini görebilirsiniz.

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**Eylemler & Gönderimler sayfasındaki Gönderimler** \> **sayfasına gidin**. Doğrudan **Gönderimler** sayfasına gitmek için kullanın <https://security.microsoft.com/reportsubmission>.

2. **Gönderimler** sayfasında **Kullanıcı tarafından bildirilen iletiler** sekmesini seçin.

   - Kullanılabilir bir sütun üst bilgisine tıklayarak girişleri sıralayabilirsiniz. Seçenekleri göstermek için **Sütunları özelleştir'e** tıklayın. Varsayılan değerler yıldız işaretiyle (<sup>\*</sup>):

     - **E-posta konusu**<sup>\*</sup>
     - **Rapor eden**<sup>\*</sup>
     - **Bildirilen tarih**<sup>\*</sup>
     - **Gönderen**<sup>\*</sup>
     - **Bildirilen neden**<sup>\*</sup>
     - **Sonuç**<sup>\*</sup>
     - **İleti bildirilen kimlik**
     - **Ağ İletisi Kimliği**
     - **Gönderen IP'i**
     - **Bildirilen kaynak**
     - **Kimlik avı benzetimi**
     - **Yönetici gönderimine dönüştürüldü**
     - **Etiketler**<sup>\*</sup>
     - **olarak işaretlendi**<sup>\*</sup>
     - **İşaretlenen**
     - **İşaretlenen tarih**

     İşiniz bittiğinde **Uygula'ya** tıklayın.

   - Girişleri filtrelemek için **Filtre'ye** tıklayın. Kullanılabilir filtreler şunlardır:
     - **Bildirilen tarih**: **Başlangıç tarihi** ve **Bitiş tarihi**.
     - **Rapor eden**
     - **E-posta konusu**
     - **İleti bildirilen kimlik**
     - **Ağ İletisi Kimliği**
     - **Gönderen**
     - **Bildirilen neden**: **Gereksiz**, **Kimlik Avı** veya **İstenmeyen Posta** değil
     - **Bildirilen kaynak**: **Microsoft eklentisi** veya **Üçüncü taraf eklentisi**
     - **Kimlik avı benzetimi**: **Evet** veya **Hayır**
     - **Yönetici gönderimine dönüştürüldü**: **Evet** veya **Hayır**
     - **Etiketler**

     İşiniz bittiğinde **Uygula'ya** tıklayın.

     > [!div class="mx-imgBorder"]
     > :::image type="content" source="../../media/admin-submission-reported-messages.png" alt-text="Kullanıcı gönderimleri için Yeni Filtre seçenekleri" lightbox="../../media/admin-submission-reported-messages.png":::

   - Girişleri gruplandırmak için **Gruplandır'a** tıklayın ve açılan listeden aşağıdaki değerlerden birini seçin:
     - **Yok**
     - **Neden**
     - **Gönderen**
     - **Rapor eden**
     - **Sonuç**
     - **Bildirilen kaynak**
     - **Kimlik avı benzetimi**
     - **Yönetici gönderimine dönüştürüldü**
     - **Etiketler**

   - Girdileri dışarı aktarmak için **Dışarı Aktar'a** tıklayın. Görüntülenen iletişim kutusunda .csv dosyasını kaydedin.

> [!NOTE]
> Kuruluşlar, kullanıcı tarafından bildirilen iletileri yalnızca özel posta kutusuna gönderecek şekilde yapılandırılmışsa, bildirilen iletiler **Kullanıcı tarafından bildirilen iletiler'de** görünür ancak sonuçları her zaman boş olur (çünkü bunlar yeniden taramazlardı).

## <a name="undo-user-submissions"></a>Kullanıcı gönderimlerini geri alma

Kullanıcı özel posta kutusuna şüpheli bir e-posta gönderdikten sonra, kullanıcı ve yöneticinin gönderimi geri alma seçeneği yoktur. Kullanıcı e-postayı kurtarmak isterse, Silinmiş Öğeler veya Gereksiz E-posta klasörlerinde kurtarma için kullanılabilir.

## <a name="convert-user-reported-messages-from-the-custom-mailbox-into-an-admin-submission"></a>Kullanıcı tarafından bildirilen iletileri özel posta kutusundan yönetici gönderimine dönüştürme

Özel posta kutusunu, iletileri Microsoft'a göndermeden kullanıcı tarafından bildirilen iletileri kesecek şekilde yapılandırdıysanız, analiz için belirli iletileri bulabilir ve Microsoft'a gönderebilirsiniz.

**Kullanıcı tarafından bildirilen iletiler** sekmesinde listeden bir ileti seçin, **analiz için Microsoft'a gönder'e** tıklayın ve açılan listeden aşağıdaki değerlerden birini seçin:

- **Rapor temizleme**
- **Kimlik avı bildirme**
- **Kötü amaçlı yazılımları bildirme**
- **İstenmeyen posta bildirme**
- **Araştırmayı tetikleme**

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/admin-submission-main-action-button.png" alt-text="Eylem düğmesindeki Yeni seçenekler" lightbox="../../media/admin-submission-main-action-button.png":::

İleti Microsoft'a bildirilirse, **Yöneticiye dönüştürülen gönderim** değeri **hayır'dan** **evet'e** dönüşür. İlgili kullanıcı tarafından bildirilen iletinin gönderim açılır öğesi içindeki taşma **menüsünden Dönüştürülmüş yönetici gönderimini görüntüle'ye** tıklayarak doğrudan yönetici gönderimine erişebilirsiniz.

:::image type="content" source="../../media/view-converted-admin-submission.png" alt-text="Kullanıcı tarafından bildirilen bir iletiden oluşturulan yönetici gönderimini görüntüleme seçeneği.":::

## <a name="view-associated-alert-for-user-and-admin-email-submissions"></a>Kullanıcı ve yönetici e-posta gönderimleri için ilişkili uyarıyı görüntüleme

> [!IMPORTANT]
> Bu bölümdeki bilgiler yalnızca plan 2 veya üzeri Office 365 için Defender için geçerlidir.
>
> Şu anda, kullanıcı gönderimleri yalnızca kimlik avı olarak bildirilen iletiler için uyarılar oluşturur.

Bildirilen her kullanıcı için kimlik avı iletisi ve yönetici e-posta gönderimi için ilgili uyarı oluşturulur.

Kullanıcı tarafından bildirilen kimlik avı iletisine karşılık gelen uyarıyı görüntülemek için **, Kullanıcı tarafından bildirilen iletiler** sekmesini seçin ve ardından iletiye çift tıklayarak gönderim açılır öğesini açın. Diğer seçenekler simgesine tıklayın ![.](../../media/m365-cc-sc-more-actions-icon.png) **Diğer seçenekler** ve ardından  **Uyarıyı görüntüle'yi** seçin.

:::image type="content" source="../../media/alert-from-user-submission.png" alt-text="Kullanıcı tarafından bildirilen kimlik avı iletisinden ilgili uyarıyı görüntüleme seçeneği.":::

Yönetici e-posta gönderimlerine karşılık gelen uyarıyı görüntülemek için **E-postalar** sekmesini seçin ve ardından iletiye çift tıklayarak gönderim açılır öğesini açın. **E-posta varlığını aç** seçeneğinde **Uyarıyı görüntüle'yi** seçin.

:::image type="content" source="../../media/alert-from-admin-submission.png" alt-text="Bir yönetici gönderiminden ilgili uyarıyı görüntüleme seçeneği.":::
