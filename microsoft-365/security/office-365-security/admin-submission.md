---
title: Gönderileri yönetme
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
description: Yöneticiler yenidencanlama için şüpheli e-postalar, şüpheli kimlik avı postaları, istenmeyen postalar ve diğer zararlı olabilecek iletiler, URL'ler ve e-posta ekleri göndermek için Microsoft 365 Defender portalında Gönderimler portalını kullanmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 34d608a6ea114fff8005069f3dc2ddc79c4be45e
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682647"
---
# <a name="use-the-submissions-portal-to-submit-suspected-spam-phish-urls-and-files-to-microsoft"></a>Gönderimler portalını kullanarak şüpheli istenmeyen posta, kimlik avı, URL'ler ve dosyaları Microsoft'a gönderme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)


Microsoft 365 posta kutuları Exchange Online kuruluşlarda, yöneticiler tarama yapmak üzere Microsoft'a e-posta iletileri, URL'ler ve ekleri göndermek için Microsoft 365 Defender portalında Gönderiler portalını kullanabilirler.

Çözümleme için bir e-posta iletisi gönderdiğinizde şunları alırsınız:

- **E-posta kimlik** doğrulaması denetimi: E-posta kimlik doğrulamasının teslim edilirken geçirip geçiri olmadığıyla ilgili ayrıntılar.
- **İlke isabetleri**: Hizmet filtresi kararlarını geçersiz kılma yoluyla gelen e-postaya kiracınıza izin etmiş veya bunu engellemış olan tüm ilkeler hakkında bilgiler.
- **Itibar/detonasyonu yükü**: İletide url'leri ve ekleri içeren güncel bir sorun vardır.
- **Noter çözümlemesi**: İletilerin kötü amaçlı olup olmadığını onaylamak için insan noterleri tarafından yapılan incelemeleri gözden geçirebilirsiniz.

> [!IMPORTANT]
> Tüm kiracılarda itibar/detonasyonu ve notlayıcı çözümlemesi yapılmaz. Verilerin uyumluluk amacıyla kiracı sınırını terkması gerekirken, bilgilerin kuruluş dışından olması engellenir.

Microsoft'a e-posta iletileri, URL'ler ve ekleri göndermenin diğer yolları için bkz. İletileri [ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com/>. Doğrudan Gönderiler **sayfasına gitmek için** kullanın <https://security.microsoft.com/reportsubmission>.

- Microsoft'a ileti ve dosya göndermek için, aşağıdaki rollerden biri gerekir:
  - **Güvenlik Yöneticisi** veya **Güvenlik Okuyucusu'Microsoft 365 Defender** [seçin](permissions-microsoft-365-security-center.md).
  
    Bu makalenin devamlarında açıklandığı gibi, özel posta kutusuna kullanıcı gönderimlerini görüntüleme için [bu](#view-user-submissions-to-microsoft) rollerden birinin gerekli olduğunu unutmayın.

- Yöneticiler, posta kutusunda hala kullanılabilir ve kullanıcı veya başka bir yönetici tarafından temizlen iletileri yine sağlanacaksa, 30 günlük olarak gönderebilirsiniz.

- Yönetici gönderimleri aşağıdaki fiyatlarda kısıtlandı:
  - Herhangi 15 dakika içerisinde en fazla gönderim: 150 gönderi
  - 24 saat içerisinde aynı gönderiler: 3 gönderi
  - 15 dakikalık bir dönemde aynı gönderiler: 1 gönderi
  
- Kullanıcıların Microsoft'a ileti ve dosya gönderme hakkında daha fazla bilgi için bkz [. İletileri ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md).

## <a name="report-suspicious-content-to-microsoft"></a>Şüpheli içeriği Microsoft'a bildirme

1. Microsoft 365 Defender portalında, <https://security.microsoft.com>Eylemler ve **Gönderiler'de** **Gönderiler &** \> **gidin**. Doğrudan Gönderiler **sayfasına gitmek için** kullanın <https://security.microsoft.com/reportsubmission>.

2. Gönderiler **sayfasında**, rapor etmek istediğiniz içeriğin türüne göre  E-posta veya E-posta ekleri veya **URL'ler** ![sekmesinin seçili olduğunu doğrulayın ve ardından çözümleme simgesi için Microsoft'a Gönder'e tıklayın.](../../media/m365-cc-sc-create-icon.png) **Çözümleme için Microsoft'a gönderin**.

3. Aşağıdaki bölümlerde **açıklandığı gibi** ilgili içerik türünü (e-posta, URL veya e-posta eki) göndermek üzere görüntülenen çözümleme açılır için Microsoft'a Gönder açılır eklentisini kullanın.

   > [!NOTE]
   > Dosya ve URL gönderimleri bulutlarda kullanılamaz ve verilerin ortamdan ayrılmasına izin vermez. Dosya veya URL'yi seçme özelliği gri olur.

### <a name="notify-users-from-within-the-portal"></a>Kullanıcıları portalın içinde bilgilendirin

1. Microsoft 365 Defender portalında, E-posta <https://security.microsoft.com>ve **işbirliği** Gönderileri'nin **Gönderiler &** \> **gidin**. Doğrudan Gönderiler **sayfasına gitmek için** kullanın <https://security.microsoft.com/reportsubmission>.

2. Gönderiler **sayfasında** Kullanıcı tarafından **bildirilen iletiler sekmesine** tıklayın, ardından işaretlemek ve bildirmek istediğiniz iletiyi seçin.

3. Farklı işaretle **ve bildir açılan liste'yi** seçin ve ardından Tehdit bulunamadı Kimlik avı **veya Gereksiz** \> **öğesini** **seçin**.

   :::image type="content" alt-text="Portaldan ileti gönderin." source="../../media/unified-submission-user-reported-message.png" lightbox="../../media/unified-submission-user-reported-message.png":::

Bildirilen ileti, hatalı pozitif veya hatalı negatif olarak işaretlenir. Portal içerisinden iletiyi bildiren kullanıcıya otomatik olarak bir e-posta bildirimi gönderilir.

### <a name="submit-a-questionable-email-to-microsoft"></a>Microsoft'a şüpheli bir e-posta gönderme

1. Gönderim **türünü seçin kutusunda**, açılan listede E-posta'nın seçili olduğunu doğrulayın.

2. Ağ **iletisi kimliğini ekleme veya e-posta dosyasını karşıya yükleme** bölümünde, aşağıdaki seçeneklerden birini kullanın:
   - **E-posta** ağ iletisi kimliğini ekleyin: Bu, iletide veya karantinaya alınan iletilerde **X-MS-Exchange-Organization-Network-Message-Id** üst bilgisinde veya **X-MS-Office365-Filtering-Correlation-Id** üst bilgisinde kullanılabilen bir GUID değeridir.
   - **Upload-posta dosyasını (.msg veya .eml) tıklatın**: Dosyalara **gözat'a tıklayın**. Açılan iletişim kutusunda .eml veya .msg dosyasını bulup seçin ve aç'a **tıklayın**.

3. Sorunu **olan bir alıcı seçin kutusunda** , ilke denetimi çalıştırmak istediğiniz alıcıyı belirtin. İlke denetimi, kullanıcı veya kuruluş ilkeleri nedeniyle e-postanın taramayı atlayarak atlayarak belirleme.

4. **Microsoft'a gönderme nedenini seçin bölümünde**, aşağıdaki seçeneklerden birini belirleyin:
   - **Engellenmiş olmalı (Hatalı pozitif)**
   - **Engellenmiş olmalı (** Yanlış negatif): E-posta görünen  bölüm olarak kategorilere ayrılmış olmalı bölümünde, aşağıdaki değerlerden birini seçin (emin değilsanız, en iyi kararlarınızı kullanın):
     - **Kimlik avı**
     - **Kötü amaçlı yazılım**
     - **İstenmeyen posta**

5. Bitirdikten sonra Gönder'e **tıklayın**.

    > [!div class="mx-imgBorder"]
    > ![Yeni URL gönderim örneği.](../../media/submission-flyout-email.png)

### <a name="send-a-suspect-url-to-microsoft"></a>Şüpheli bir URL'yi Microsoft'a gönderme

1. Gönderim **türünü seçin kutusunda** , açılan **listeden URL'yi** seçin.

2. Görüntülenen **URL** kutusuna tam URL'yi girin (örneğin, `https://www.fabrikam.com/marketing.html`).

3. **Microsoft'a gönderme nedenini seçin bölümünde**, aşağıdaki seçeneklerden birini belirleyin:
   - **Engellenmiş olmalı (Hatalı pozitif)**
   - **Engellenmiş olmalıdır (** Yanlış negatif): Bu **URL** görünen bölüm olarak kategorilere ayrılmış olmalıdır, aşağıdaki değerlerden birini seçin (emin değilsanız, en iyi kararlarınızı kullanın):
     - **Kimlik avı**
     - **Kötü amaçlı yazılım**

4. Bitirdikten sonra Gönder'e **tıklayın**.

    > [!div class="mx-imgBorder"]
    > ![Yeni E-posta gönderim örneği.](../../media/submission-url-flyout.png)

### <a name="submit-a-suspected-email-attachment-to-microsoft"></a>Şüpheli bir e-posta eklerini Microsoft'a gönderme

1. Gönderim türünü **seçin kutusunda,** açılan listeden Eki **e-posta** ile gönder'i seçin.

2. Görüntülenen Dosya **bölümünde** Dosyalara **gözat'a tıklayın**. Açılan iletişim kutusunda dosyayı bulup seçin ve Aç'a **tıklayın**.

3. **Microsoft'a gönderme nedenini seçin bölümünde**, aşağıdaki seçeneklerden birini belirleyin:
   - **Engellenmiş olmalı (Hatalı pozitif)**
   - **Engellenmiş olmalı (** Yanlış negatif): Bu dosya görünen bölüm  olarak kategorilere ayrılmış olmalı bölümünde, aşağıdaki değerlerden birini seçin (emin değilsanız, en iyi kararlarınızı kullanın):
     - **Kimlik avı**
     - **Kötü amaçlı yazılım**

4. Bitirdikten sonra Gönder'e **tıklayın**.

    > [!div class="mx-imgBorder"]
    > ![Yeni Ek gönderme örneği.](../../media/submit-email-attachment-for-analysis.png)

> [!NOTE]
> Kötü amaçlı yazılım filtrelemesi ileti eklerini Kötü Amaçlı Yazılım Uyarısı Text.txt dosyasıyla değiştirirse, özgün iletiyi özgün ekleri içeren karantinadan göndermeniz gerekir. İletileri karantinaya almak ve kötü amaçlı yazılım hatalı pozitif sonuçlarla serbest bırakmak hakkında daha fazla bilgi için bkz. Karantinaya alınmış [iletileri ve dosyaları yönetici olarak yönetme](manage-quarantined-messages-and-files.md).

## <a name="view-admin-submissions-to-microsoft"></a>Microsoft'a yapılan yönetici gönderimlerini görüntüleme

1. Microsoft 365 Defender portalında, <https://security.microsoft.com>Eylemler ve **Gönderiler'de** **Gönderiler &** \> **gidin**. Doğrudan Gönderiler **sayfasına gitmek için** kullanın <https://security.microsoft.com/reportsubmission>.

2. Gönderiler **sayfasında**, E-postalar, **URL** **veya E-posta** eki **sekmesinin seçili** olduğunu doğrulayın.

   - Kullanılabilir bir sütun başlığına tıklayarak girişleri sıraabilirsiniz. En **çok yedi sütun** göstermek için Sütunları özelleştir'e tıklayın. Varsayılan değerler yıldız işaretiyle () işaretlenir<sup>\*</sup>:
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
     - **Ağ İleti Kimliği/Nesne Kimliği**
     - **Yön**
     - **Gönderen IP'si**
     - **Toplu uyumlu düzey (BCL)**
     - **Hedef**
     - **İlke eylemi**
     - **Gönderilen**
     - **Kimlik avı benzetimi**
     - **Etiketler**<sup>\*</sup>
     - **İzin ver**

     Bitirdikten sonra Uygula'ya **tıklayın**.

     > [!div class="mx-imgBorder"]
     > ![Yönetici gönderileri için Yeni Sütun özelleştirme seçenekleri.](../../media/submit-admin-submissios-customize-columns.png)

   - Girdileri filtrelemek için Filtre'ye **tıklayın**. Kullanılabilir filtreler:
     - **Gönderilme tarihi**: **Başlangıç tarihi ve** **Bitiş tarihi**.
     - **Gönderim Kimliği**: Her gönderiye atanan GUID değeri.
     - **Ağ İletisi Kimliği**
     - **Gönderen**
     - **Alıcı**
     - **Ad**
     - **Gönderilen**
     - **Gönderme nedeni**
     - **Durum**
     - **Etiketler**

     Bitirdikten sonra Uygula'ya **tıklayın**.

     > [!div class="mx-imgBorder"]
     > ![Yönetici gönderimleri için yeni Filtre seçenekleri.](../../media/submit-admin-submissions-view-filters.png)

   - Girdileri gruplay etmek için **, Grup'a** tıklayın ve açılan listeden aşağıdaki değerlerden birini seçin:
     - **Yok**
     - **Tür**
     - **Neden**
     - **Durum**
     - **Sonuç**
     - **Etiketler**

   - Girdileri dışarı aktarma için Dışarı Aktar'a **tıklayın**. Görüntülenen iletişim kutusunda, dosyanın .csv kaydedin.

### <a name="admin-submission-result-details"></a>Yönetici gönderimi sonuç ayrıntıları

Yönetici gönderimleri içinde gönderilen iletiler gözden geçir gösterilir ve gönderilerin ayrıntı uç iletisinde sonuçları gösterilir:

- Teslim sırasında gönderenin e-posta kimlik doğrulamasında hata olup olmadığı.
- İletiyle ilgili kararı etkilemiş veya geçersiz kılmış olabilecek bir ilke eşleşmesi hakkında bilgi.
- İletide yer alan URL’lerin veya dosyaların kötü amaçlı olup olmadığını görmek için geçerli etkisizleştirme sonuçları.
- Noterlerin geri bildirimi.

Geçersiz kılma bulunursa, sonuç birkaç dakika içinde kullanılabilir olur. E-posta kimlik doğrulaması veya teslimte sorun yoksa ve teslim geçersiz kılmadan etkilenmezse, noterlerin geri bildirimleri bir gün kadar zaman alsa bile.

## <a name="view-user-submissions-to-microsoft"></a>Microsoft'a kullanıcı gönderimlerini görüntüleme

Rapor İletisi eklentisinde [, Rapor](enable-the-report-message-add-in.md) Kimlik Avında Rapor eklentisinde veya [](enable-the-report-phish-add-in.md)kullanıcılar [Web üzerinde Outlook'te](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md) yerleşik raporlamayı kullanıyorsa, Kullanıcı tarafından bildirilen ileti sekmesinde kullanıcıların nelerin rapor **yaptığını görebilirsiniz.**

1. Microsoft 365 Defender portalında, <https://security.microsoft.com>Eylemler ve **Gönderiler'de** **Gönderiler &** \> **gidin**. Doğrudan Gönderiler **sayfasına gitmek için** kullanın <https://security.microsoft.com/reportsubmission>.

2. Gönderiler **sayfasında** Kullanıcı tarafından bildirilen **iletiler sekmesini** seçin.

   - Kullanılabilir bir sütun başlığına tıklayarak girişleri sıraabilirsiniz. Seçenekleri **göstermek için Sütunları** özelleştir'e tıklayın. Varsayılan değerler yıldız işaretiyle () işaretlenir<sup>\*</sup>:

     - **E-posta konusu**<sup>\*</sup>
     - **Rapor**<sup>\*</sup>
     - **Bildirilen tarih**<sup>\*</sup>
     - **Gönderen**<sup>\*</sup>
     - **Bildirilen neden**<sup>\*</sup>
     - **Sonuç**<sup>\*</sup>
     - **İleti bildirilen kimlik**
     - **Ağ İletisi Kimliği**
     - **Gönderen IP'si**
     - **Raporlandığı yer**
     - **Kimlik avı benzetimi**
     - **Yönetici gönderime dönüştürülen**
     - **Etiketler**<sup>\*</sup>
     - **Farklı işaretlenmiş**<sup>\*</sup>
     - **İşaretlenen**
     - **İşaretlenen tarih**

     Bitirdikten sonra Uygula'ya **tıklayın**.

   - Girdileri filtrelemek için Filtre'ye **tıklayın**. Kullanılabilir filtreler:
     - **Bildirilen tarih**: **Başlangıç tarihi** ve **Bitiş tarihi**.
     - **Rapor**
     - **E-posta konusu**
     - **İleti bildirilen kimlik**
     - **Ağ İletisi Kimliği**
     - **Gönderen**
     - **Bildirilen neden**: **Gereksiz**, Kimlik **avı veya İstenmeyen** **posta değil**
     - **Şu kişi** tarafından bildirildi: **Microsoft eklenti** **veya Üçüncü taraf eklenti**
     - **Kimlik avı benzetimi**: **Evet** veya **Hayır**
     - **Yönetici gönderime dönüştürülen**: **Evet** veya **Hayır**
     - **Etiketler**

     Bitirdikten sonra Uygula'ya **tıklayın**.

     > [!div class="mx-imgBorder"]
     > ![Kullanıcı gönderimleri için yeni Filtre seçenekleri.](../../media/submit-user-submissions-view-filters.png)

   - Girdileri gruplay etmek için **, Grup'a** tıklayın ve açılan listeden aşağıdaki değerlerden birini seçin:
     - **Yok**
     - **Neden**
     - **Gönderen**
     - **Rapor**
     - **Sonuç**
     - **Raporlandığı yer**
     - **Kimlik avı benzetimi**
     - **Yönetici gönderime dönüştürülen**
     - **Etiketler**
   
   - Girdileri dışarı aktarma için Dışarı Aktar'a **tıklayın**. Görüntülenen iletişim kutusunda, dosyanın .csv kaydedin.

> [!NOTE]
> Kuruluşlar kullanıcıya bildirilen iletileri yalnızca özel posta kutusuna gönderecek şekilde yapılandırılmışsa, bildirilen iletiler yeniden gönderme için gönderilmez ve **Kullanıcı** tarafından bildirilen ileti sonuçları her zaman boş olur.

### <a name="undo-user-submissions"></a>Kullanıcı gönderimlerini geri alma

Kullanıcı özel posta kutusuna şüpheli bir e-posta gönderdi mi, kullanıcı ve yöneticinin gönderiyi geri alma seçeneği yoktur. Kullanıcı e-postayı kurtarmak isterse, Silinmiş Öğeler veya Gereksiz E-posta klasörlerini kullanarak kurtarılabilir.

### <a name="converting-user-reported-messages-from-the-custom-mailbox-into-an-admin-submission"></a>Kullanıcı, özel posta kutusundan yönetici gönderisine ileti bildirdi 

Özel posta kutusunu, kullanıcı tarafından bildirilen iletileri Microsoft'a göndermeden kesişim noktası olarak yapılandırdısanız, çözümleme için belirli iletileri bulabilir ve Microsoft'a gönderebilirsiniz.

Kullanıcı tarafından **bildirilen iletiler** sekmesinde, listeden bir ileti seçin, çözümleme için **Microsoft'a** Gönder'e tıklayın ve sonra açılan listeden aşağıdaki değerlerden birini seçin:

- **Rapor temizleme**
- **Kimlik avını bildirme**
- **Kötü amaçlı yazılım bildir**
- **İstenmeyen posta bildir**
- **Tetik araştırma**

> [!div class="mx-imgBorder"]
> ![Eylem düğmesi üzerinde Yeni Seçenekler.](../../media/admin-submission-main-action-button.png)
