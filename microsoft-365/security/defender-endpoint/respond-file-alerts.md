---
title: Uç Nokta için Microsoft Defender'da bir dosya üzerinde yanıt eylemleri gerçekleştirme
description: Dosyayla ilgili uyarılarda bir dosyayı durdurup quarantinleyerek veya bir dosyayı engelleyerek ve etkinlik ayrıntılarını denetleyerek yanıt eylemleri gerçekleştirin.
keywords: yanıt verme, durdurma ve karantinaya al, dosyayı engelle, derin analiz
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: a70602f9b482196ee949a8f9922f2979b04b3ff4
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669308"
---
# <a name="take-response-actions-on-a-file"></a>Dosyada yanıt eylemleri gerçekleştirin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 1](/microsoft-365/security/defender-endpoint/defender-endpoint-plan-1)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-responddile-abovefoldlink)

Algılanan saldırılara hızlı bir şekilde yanıt vermek için dosyaları durdurup kilitleyin veya bir dosyayı engelleyin. Dosyalar üzerinde işlem yaptıktan sonra İşlem merkezinde etkinlik ayrıntılarını de kontrol edebilirsiniz.

Yanıt eylemleri bir dosyanın ayrıntılı profil sayfasında kullanılabilir. Bu sayfaya geçtikten sonra, yeni **Dosya sayfasını** değiştirerek yeni ve eski sayfa düzenleri arasında geçiş yapabilirsiniz. Bu makalenin geri kalanında daha yeni sayfa düzeni açıklanmaktadır.

Yanıt eylemleri dosya sayfasının üst kısmında çalışır ve şunları içerir:

- Dosyayı Durdur ve Karantinaya Al
- Gösterge Ekle
- Dosyayı indirme
- Tehdit uzmanına danışın
- İşlem merkezi

Dosyayı güvenli bir bulut korumalı alanında çalıştırmak için ayrıntılı analiz için de dosya gönderebilirsiniz. Analiz tamamlandığında, dosyanın davranışı hakkında bilgi sağlayan ayrıntılı bir rapor alırsınız. **Derin** analiz sekmesini seçerek derin analiz için dosya gönderebilir ve geçmiş raporları okuyabilirsiniz. Dosya bilgi kartlarının altında bulunur.

Bazı eylemler belirli izinler gerektirir. Aşağıdaki tabloda, bazı izinlerin taşınabilir yürütülebilir dosyalarda (PE) ve PE olmayan dosyalarda hangi eylemi gerçekleştirebileceği açıklanmaktadır:

|Izni|PE dosyaları|PE olmayan dosyalar|
|---|:---:|:---:|
|Verileri görüntüleme|X|X|
|Uyarı araştırması|&#x2611;|X|
|Canlı yanıt temel|X|X|
|Canlı yanıt gelişmiş|&#x2611;|&#x2611;|

Roller hakkında daha fazla bilgi için bkz. [Rol tabanlı erişim denetimi için rol oluşturma ve yönetme](user-roles.md).

## <a name="stop-and-quarantine-files-in-your-network"></a>Ağ içinde dosyaları durdurun ve karantinaya alın

Kötü amaçlı işlemi durdurarak ve dosyanın gözlemlendiği yerde durarak kuruluşunuzda bir saldırı içerebilirsiniz.

> [!IMPORTANT]
> Bu eylemi yalnızca şu durumda gerçekleştirebilirsiniz:
>
> - Üzerinde işlem yaptığınız cihaz Windows 10, sürüm 1703 veya üzerini çalıştırıyor ve Windows 11
> - Dosya güvenilen üçüncü taraf yayımcılara ait değil veya Microsoft tarafından imzalanmaz
> - Microsoft Defender Virüsten Koruma en azından Pasif modda çalışıyor olmalıdır. Daha fazla bilgi için bkz. [uyumluluk Microsoft Defender Virüsten Koruma](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility).

**Dosyayı Durdur ve Karantinaya Al** eylemi, çalışan işlemleri durdurmayı, dosyaları quarantining'i ve kayıt defteri anahtarları gibi kalıcı verileri silmeyi içerir.

Bu eylem, dosyanın son 30 gün içinde gözlemlendiği Windows 10, sürüm 1703 veya üzeri ve Windows 11 olan cihazlarda geçerli olur.

> [!NOTE]
> Dosyayı istediğiniz zaman karantinadan geri yükleyebilirsiniz.

### <a name="stop-and-quarantine-files"></a>Dosyaları durdurma ve karantinaya al

1. Durdurmak ve karantinaya almak istediğiniz dosyayı seçin. Aşağıdaki görünümlerden herhangi birinden bir dosya seçebilir veya Arama kutusunu kullanabilirsiniz:

   - **Uyarılar** - Uyarı Hikayesi zaman çizelgesindeki Açıklama veya Ayrıntılar'dan ilgili bağlantılara tıklayın
   - **Arama kutusu** - Açılan menüden **Dosya'yı** seçin ve dosya adını girin

   > [!NOTE]
   > Dosya durdurma ve karantinaya al eylemi en fazla 1000 cihazla sınırlıdır. Daha fazla sayıda cihazda bir dosyayı durdurmak için bkz. [Dosyayı engellemek veya dosyaya izin vermek için gösterge ekleme](#add-indicator-to-block-or-allow-a-file).

2. Üst çubuka gidin ve **Durdur ve Dosyayı Karantinaya Al'ı** seçin.

   :::image type="content" source="images/atp-stop-quarantine-file.png" alt-text="Dosya durdurma ve karantinaya al eylemi" lightbox="images/atp-stop-quarantine-file.png":::

3. Bir neden belirtin, ardından **Onayla'yı** seçin.

   :::image type="content" source="images/atp-stop-quarantine.png" alt-text="Durdurma ve karantina dosyası sayfası" lightbox="images/atp-stop-quarantine.png":::

   İşlem merkezi gönderim bilgilerini gösterir:

   :::image type="content" source="images/atp-stopnquarantine-file.png" alt-text="Dosya durdurma ve karantinaya al işlem merkezi" lightbox="images/atp-stopnquarantine-file.png":::

   - **Gönderme zamanı** - Eylemin ne zaman gönderildiğini gösterir.
   - **Başarılı** - Dosyanın durdurulduğu ve karantinaya alındığı cihaz sayısını gösterir.
   - **Başarısız** - Eylemin başarısız olduğu cihaz sayısını ve hatayla ilgili ayrıntıları gösterir.
   - **Beklemede** - Dosyanın henüz durdurulup karantinaya alınacağı cihaz sayısını gösterir. Bu, cihazın çevrimdışı olduğu veya ağa bağlı olmadığı durumlar için zaman alabilir.

4. Eylem hakkında daha fazla bilgi görüntülemek için durum göstergelerinden herhangi birini seçin. Örneğin, eylemin nerede başarısız olduğunu görmek için **Başarısız'ı** seçin.

#### <a name="notification-on-device-userf"></a>Cihaz userf'sinde bildirim

Dosya bir cihazdan kaldırıldığında aşağıdaki bildirim gösterilir:

:::image type="content" source="images/atp-notification-file.png" alt-text="Cihaz kullanıcısının a bildirimi" lightbox="images/atp-notification-file.png":::

Cihaz zaman çizelgesinde, bir dosyanın durdurulduğu ve karantinaya alındığı her cihaz için yeni bir olay eklenir.

Eylem kuruluş genelinde yaygın olarak kullanılan dosyalar için uygulanmadan önce bir uyarı gösterilir. İşlemin amaçlandığını doğrulamak içindir.

## <a name="restore-file-from-quarantine"></a>Dosyayı karantinadan geri yükleyin

Bir araştırmadan sonra temiz olduğunu belirlediyseniz dosyayı geri alabilir ve karantinadan kaldırabilirsiniz. Dosyanın karantinaya alındığı her cihazda aşağıdaki komutu çalıştırın.

1. Cihazda yükseltilmiş bir komut satırı istemi açın:

   1. **Başlangıç'a** gidin ve _cmd_ yazın.

   1. **Komut istemi'ne** sağ tıklayın ve **Yönetici olarak çalıştır'ı** seçin.

2. Aşağıdaki komutu girin ve **Enter tuşuna** basın:

   ```dos
   "%ProgramFiles%\Windows Defender\MpCmdRun.exe" -Restore -Name EUS:Win32/CustomEnterpriseBlock -All
   ```

   > [!NOTE]
   > Bazı senaryolarda **ThreatName** şu şekilde görünebilir: EUS:Win32/CustomEnterpriseBlock!cl.
   >
   > Uç Nokta için Defender, son 30 gün içinde bu cihazda karantinaya alınan tüm özel engellenen dosyaları geri yükler.

> [!IMPORTANT]
> Olası bir ağ tehdidi olarak karantinaya alınan bir dosya kurtarılamayabilir. Kullanıcı karantinadan sonra dosyayı geri yüklemeyi denerse, bu dosyaya erişilemiyor olabilir. Bunun nedeni sistemin artık dosyaya erişmek için ağ kimlik bilgilerine sahip olmaması olabilir. Genellikle bu, bir sistemde veya paylaşılan klasörde geçici oturum açmanın ve erişim belirteçlerinin süresinin dolmasının bir sonucudur.

## <a name="download-or-collect-file"></a>Dosya indirin veya toplayın

Yanıt eylemlerinden **Dosya indir'i** seçtiğinizde dosyanızı içeren yerel, parola korumalı bir .zip arşivi indirebilirsiniz. Dosyayı indirmek için bir neden kaydedebileceğiniz ve bir parola ayarlayabileceğiniz bir açılır pencere görüntülenir.

Varsayılan olarak, karantinadaki dosyaları indirebilmeniz gerekir.

:::image type="content" source="images/atp-download-file-action.png" alt-text="Dosya indirme eylemi" lightbox="images/atp-download-file-action.png":::

### <a name="download-quarantined-files"></a>Karantinaya alınan dosyaları indirme

Microsoft Defender Virüsten Koruma veya güvenlik ekibiniz tarafından karantinaya alınan dosyalar[, örnek gönderim yapılandırmalarınıza](enable-cloud-protection-microsoft-defender-antivirus.md) göre uyumlu bir şekilde kaydedilir. Güvenlik ekibiniz dosyaları doğrudan dosyanın ayrıntı sayfasından "Dosyayı indir" düğmesi aracılığıyla indirebilir. **Bu özellik varsayılan olarak 'Açık'tır**.

Konum, kuruluşunuzun coğrafi ayarlarına (AB, Birleşik Krallık veya ABD) bağlıdır. Karantinaya alınan bir dosya kuruluş başına yalnızca bir kez toplanır. Hizmet Güveni Portalı'ndan https://aka.ms/STPMicrosoft'un veri koruması hakkında daha fazla bilgi edinin.

Bu ayarın açık olması, güvenlik ekiplerinin kötü olabilecek dosyaları incelemesine ve olayları hızlı ve daha az riskli bir şekilde araştırmalarına yardımcı olabilir. Ancak, bu ayarı kapatmanız gerekiyorsa, ayarı ayarlamak için **Ayarlar** \> **Uç Noktalar** \> **Gelişmiş özellikler** \> **Karantinaya alınan dosyaları indir'e** gidin. [Gelişmiş özellikler hakkında daha fazla bilgi edinin](advanced-features.md)

#### <a name="backing-up-quarantined-files"></a>Karantinaya alınan dosyaları yedekleme

[Örnek gönderim yapılandırmanıza](enable-cloud-protection-microsoft-defender-antivirus.md#use-group-policy-to-turn-on-cloud-protection) bağlı olarak, karantinaya alınan dosyayı yedeklemeden önce kullanıcılardan açık onay vermeleri istenebilir.

Örnek gönderim kapatılırsa bu özellik çalışmaz. Otomatik örnek gönderimi kullanıcıdan izin istemek üzere ayarlanırsa, yalnızca kullanıcının göndermeyi kabulladığı örnekler toplanır.

> [!IMPORTANT]
> Karantinaya alınan dosya gereksinimlerini indirin:
>
> - Kuruluşunuz etkin modda Microsoft Defender Virüsten Koruma kullanıyor
> - Virüsten koruma altyapısı sürümü 1.1.17300.4 veya üzeridir. [Bkz. Aylık platform ve altyapı sürümleri](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions)
> - Bulut tabanlı koruma etkindir. Bkz [. Bulut tabanlı korumayı açma](enable-cloud-protection-microsoft-defender-antivirus.md)
> - Örnek gönderim açık
> - Cihazların Windows 10 sürümü 1703 veya üzeri ya da Windows server 2016 veya 2019 ya da Windows Server 2022 veya Windows 11

### <a name="collect-files"></a>Dosyaları toplama

Bir dosya Uç Nokta için Microsoft Defender tarafından depolanmadıysa, dosyayı indiremezsiniz. Bunun yerine, aynı konumda bir **Dosya topla** düğmesi görürsünüz. Son 30 gün içinde kuruluşta bir dosya görülmediyse, **Dosya topla** seçeneği devre dışı bırakılır.
> [!Important]
> Olası bir ağ tehdidi olarak karantinaya alınan bir dosya kurtarılamayabilir. Kullanıcı karantinadan sonra dosyayı geri yüklemeyi denerse, bu dosyaya erişilemiyor olabilir. Bunun nedeni sistemin artık dosyaya erişmek için ağ kimlik bilgilerine sahip olmaması olabilir. Genellikle bu, bir sistemde veya paylaşılan klasörde geçici oturum açmanın ve erişim belirteçlerinin süresinin dolmasının bir sonucudur.

## <a name="add-indicator-to-block-or-allow-a-file"></a>Bir dosyayı engellemek veya dosyaya izin vermek için gösterge ekleme

Kötü amaçlı olabilecek dosyaları veya şüpheli kötü amaçlı yazılımları yasaklayarak kuruluşunuzda bir saldırının daha fazla yayılmasını önleyin. Kötü amaçlı olabilecek bir taşınabilir yürütülebilir dosya (PE) biliyorsanız, dosyayı engelleyebilirsiniz. Bu işlem, kuruluşunuzdaki cihazlarda okunmasını, yazılmasını veya yürütülmesini engeller.

> [!IMPORTANT]
>
> - Kuruluşunuz Microsoft Defender Virüsten Koruma kullanıyorsa ve Bulut tabanlı koruma etkinleştirildiyse bu özellik kullanılabilir. Daha fazla bilgi için bkz. [Bulut tabanlı korumayı yönetme](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus).
>
> - Kötü amaçlı yazılımdan koruma istemcisi sürümü 4.18.1901.x veya üzeri olmalıdır.
> - Bu özellik, şüpheli kötü amaçlı yazılımların (veya kötü amaçlı olabilecek dosyaların) web'den indirilmesini önlemek için tasarlanmıştır. Şu anda _.exeve.dll_ dosyaları da dahil olmak üzere taşınabilir yürütülebilir (PE) __ dosyaları destekler. Kapsam zaman içinde uzatılır.
> - Bu yanıt eylemi Windows 10, sürüm 1703 veya üzeri ve Windows 11 cihazlarda kullanılabilir.
> - İzin ver veya engelle eyleminden önce cihazın önbelleğinde dosya sınıflandırması varsa, izin ver veya engelle işlevi dosyalarda yapılamaz.

> [!NOTE]
> Bu eylemi gerçekleştirebilmek için PE dosyasının cihaz zaman çizelgesinde olması gerekir.
>
> Eylemin gerçekleştirilişiyle gerçek dosyanın engellenmesi arasında birkaç dakika gecikme olabilir.

### <a name="enable-the-block-file-feature"></a>Blok dosyası özelliğini etkinleştirme

Dosyaları engellemeye başlamak için önce Ayarlar'de [**Engelle veya izin ver** özelliğini açmanız](advanced-features.md) gerekir.

### <a name="allow-or-block-file"></a>Dosyaya izin ver veya dosyayı engelle

Bir dosya için gösterge karması eklediğinizde, kuruluşunuzdaki bir cihaz çalıştırmayı denediğinde uyarı oluşturmayı ve dosyayı engellemeyi seçebilirsiniz.

Bir gösterge tarafından otomatik olarak engellenen dosyalar dosyanın İşlem merkezinde gösterilmez, ancak uyarılar Uyarılar kuyruğunda görünmeye devam eder.

Dosyalarda uyarıları engelleme ve tetikleme hakkında daha fazla bilgi için [bkz. göstergeleri yönetme](manage-indicators.md) .

Bir dosyayı engellemeyi durdurmak için göstergeyi kaldırın. Bunu, dosyanın profil sayfasındaki **Göstergeyi Düzenle** eylemi aracılığıyla yapabilirsiniz. Bu eylem, göstergeyi eklemeden önce **Gösterge Ekle** eylemiyle aynı konumda görünür.

Ayrıca, **Ayarlar sayfasından, Kural** \> **Göstergeleri'nin** altında göstergeleri düzenleyebilirsiniz. Göstergeler bu alanda dosya karması tarafından listelenir.

## <a name="consult-a-threat-expert"></a>Tehdit uzmanına danışın

Güvenliği aşılmış olabilecek bir cihaz veya güvenliği aşılmış cihazlar hakkında daha fazla içgörü için bir Microsoft tehdit uzmanına başvurun. Microsoft Tehdit Uzmanları, zamanında ve doğru yanıt için doğrudan Microsoft 365 Defender portalından devreye girer. Uzmanlar, tehlikeye girmiş olabilecek bir cihaz hakkında içgörüler sağlar ve karmaşık tehditleri ve hedeflenen saldırı bildirimlerini anlamanıza yardımcı olur. Ayrıca, portal panonuzda gördüğünüz uyarılar veya tehdit bilgileri bağlamı hakkında bilgi de sağlayabilirler.

Ayrıntılar için bkz. [Microsoft Tehdit Uzmanına Başvurun](/microsoft-365/security/defender-endpoint/configure-microsoft-threat-experts#consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization) .

## <a name="check-activity-details-in-action-center"></a>İşlem merkezinde etkinlik ayrıntılarını denetleyin

**İşlem merkezi**, bir cihazda veya dosyada gerçekleştirilen eylemler hakkında bilgi sağlar. Aşağıdaki ayrıntıları görüntüleyebilirsiniz:

- Araştırma paketi koleksiyonu
- Virüsten koruma taraması
- Uygulama kısıtlaması
- Cihaz yalıtımı

Gönderme tarihi/saati, kullanıcıyı gönderme ve eylemin başarılı veya başarısız olup olmadığını gibi diğer tüm ilgili ayrıntılar da gösterilir.

:::image type="content" source="images/action-center-details.png" alt-text="Bilgi içeren işlem merkezi" lightbox="images/action-center-details.png":::

## <a name="deep-analysis"></a>Derinanaliz

Siber güvenlik araştırmaları genellikle bir uyarı tarafından tetiklenir. Uyarılar, genellikle yeni veya bilinmeyen bir veya daha fazla gözlemlenen dosyayla ilgilidir. Bir dosyayı seçtiğinizde dosyanın meta verilerini görebileceğiniz dosya görünümüne gidebilirsiniz. Dosyayla ilgili verileri zenginleştirmek için dosyayı ayrıntılı analiz için gönderebilirsiniz.

Derin analiz özelliği, güvenli, tam olarak izlenen bir bulut ortamında bir dosya yürütür. Derin analiz sonuçları dosyanın etkinliklerini, gözlemlenen davranışlarını ve bırakılan dosyalar, kayıt defteri değişiklikleri ve IP'lerle iletişim gibi ilişkili yapıtları gösterir.
Derin analiz şu anda taşınabilir yürütülebilir (PE) dosyaların ( _.exe_ ve _.dll_ dosyaları dahil) kapsamlı analizini destekler.

Bir dosyanın derin analizi birkaç dakika sürer. Dosya analizi tamamlandıktan sonra, Derin Çözümleme sekmesi bir özet ve kullanılabilir en son sonuçların tarih ve saatini görüntüleyecek şekilde güncelleştirilir.

Derin analiz özeti, gözlemlenen *davranışların* bir listesini içerir ve bazıları kötü amaçlı etkinlikleri ve diskte oluşturulan ilgili IP'ler ve dosyalar da dahil olmak üzere *gözlemlenebilirleri* gösterebilir. Hiçbir şey bulunamazsa, bu bölümlerde kısa bir ileti görüntülenir.

Derin analizin sonuçları tehdit bilgileriyle eşleştirilir ve tüm eşleşmeler uygun uyarılar oluşturur.

Genellikle bir uyarı araştırması sırasında veya kötü amaçlı davranışlardan şüphelendiğiniz başka herhangi bir nedenle herhangi bir dosyanın ayrıntılarını araştırmak için derin analiz özelliğini kullanın. Bu özellik, dosyanın profil sayfasındaki **Derin analiz** sekmesinde bulunur.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4aAYy?rel=0]

Dosya Uç Nokta için Defender arka uç örnek koleksiyonunda kullanılabilir olduğunda veya **derin analize** göndermeyi destekleyen bir Windows 10 cihazında gözlemlendiğinde derin analiz için gönder seçeneği etkinleştirilir.

> [!NOTE]
> Yalnızca Windows 10 ve Windows 11 dosyaları otomatik olarak toplanabilir.

Ayrıca, dosya Windows 10 cihazda (veya Windows 11) gözlemlenmediyse Microsoft 365 Defender [Portalı](https://www.microsoft.com/security/portal/submission/submit.aspx) üzerinden bir örnek gönderebilir ve **Derin analiz** düğmesinin kullanılabilir duruma gelmesini bekleyebilirsiniz.

> [!NOTE]
> Microsoft 365 Defender Portalı'ndaki arka uç işleme akışları nedeniyle, dosya gönderimi ile Uç Nokta için Defender'daki derin analiz özelliğinin kullanılabilirliği arasında 10 dakikaya kadar gecikme süresi olabilir.

### <a name="submit-files-for-deep-analysis"></a>Ayrıntılı analiz için dosya gönderme

1. Ayrıntılı analiz için göndermek istediğiniz dosyayı seçin. Aşağıdaki görünümlerden herhangi birinden dosya seçebilir veya dosyada arama yapabilirsiniz:

    - **Uyarılar** - Uyarı Hikayesi zaman çizelgesindeki **Açıklama** veya **Ayrıntılar'dan** dosya bağlantılarını seçin
    - **Cihazlar listesi** - **Kuruluştaki cihaz** bölümündeki **Açıklama** veya **Ayrıntılar** bölümünden dosya bağlantılarını seçin
    - **Arama kutusu** - Açılan menüden **Dosya'yı** seçin ve dosya adını girin

2. Dosya görünümünün **Derin analiz** sekmesinde **Gönder'i** seçin.

   :::image type="content" source="images/submit-file.png" alt-text="PE dosyalarını gönder düğmesi" lightbox="images/submit-file.png":::

   > [!NOTE]
   > _.exeve.dll_ dosyaları da dahil olmak üzere yalnızca PE dosyaları desteklenir __.

   bir ilerleme çubuğu görüntülenir ve analizin farklı aşamaları hakkında bilgi sağlar. Daha sonra analiz tamamlandığında raporu görüntüleyebilirsiniz.

> [!NOTE]
> Cihaz kullanılabilirliğine bağlı olarak örnek toplama süresi farklılık gösterebilir. Örnek toplama için 3 saatlik bir zaman aşımı vardır. Koleksiyon başarısız olur ve o anda çevrimiçi Windows 10 cihaz (veya Windows 11) raporlaması yoksa işlem durdurulacaktır. Dosyadaki yeni verileri almak için dosyaları derin analiz için yeniden gönderebilirsiniz.

### <a name="view-deep-analysis-reports"></a>Derin analiz raporlarını görüntüleme

Gönderdiğiniz dosya hakkında daha ayrıntılı içgörüler görmek için sağlanan ayrıntılı analiz raporunu görüntüleyin. Bu özellik dosya görünümü bağlamında kullanılabilir.

Aşağıdaki bölümlerde ayrıntıları sağlayan kapsamlı raporu görüntüleyebilirsiniz:

- Davranış
- Gözlemlenebilir öğeler

Sağlanan ayrıntılar olası bir saldırının göstergesi olup olmadığını araştırmanıza yardımcı olabilir.

1. Ayrıntılı analiz için gönderdiğiniz dosyayı seçin.
2. **Derin analiz** sekmesini seçin. Önceki raporlar varsa, rapor özeti bu sekmede görünür.

   :::image type="content" source="images/analysis-results-nothing500.png" alt-text="Bir dizi kategorideki ayrıntılı bilgileri gösteren derin analiz raporu" lightbox="images/analysis-results-nothing500.png":::

#### <a name="troubleshoot-deep-analysis"></a>Derin analiz sorunlarını giderme

Dosya göndermeye çalışırken bir sorunla karşılaşırsanız aşağıdaki sorun giderme adımlarının her birini deneyin.

1. Söz konusu dosyanın bir PE dosyası olduğundan emin olun. PE dosyaları genellikle _.exe_ veya _.dll_ uzantılarına (yürütülebilir programlar veya uygulamalar) sahiptir.

2. Hizmetin dosyaya erişimi olduğundan, dosyanın hala var olduğundan ve bozulmadığından veya değiştirilmediğinden emin olun.

3. Kısa bir süre bekleyin ve dosyayı yeniden göndermeyi deneyin. Kuyruk dolu olabilir veya geçici bir bağlantı veya iletişim hatası oluştu.

4. Örnek koleksiyon ilkesi yapılandırılmamışsa, varsayılan davranış örnek toplamaya izin vermektir. Yapılandırılmışsa, dosyayı yeniden göndermeden önce ilke ayarının örnek toplamaya izin verdiğinden emin olun. Örnek koleksiyon yapılandırıldığında aşağıdaki kayıt defteri değerini denetleyin:

    ```text
    Path: HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection
    Name: AllowSampleCollection
    Type: DWORD
    Hexadecimal value :
      Value = 0 - block sample collection
      Value = 1 - allow sample collection
    ```

5. grup ilkesi aracılığıyla kuruluş birimini değiştirin. Daha fazla bilgi için bkz[. grup ilkesi ile yapılandırma](configure-endpoints-gp.md).

6. Bu adımlar sorunu çözmezse desteğe başvurun.

## <a name="related-topics"></a>İlgili konular

- [Cihazda yanıt eylemleri gerçekleştirin](respond-machine-alerts.md)
- [Dosyaları araştırın](investigate-files.md)
- [Uç Nokta için Microsoft Defender Plan 1'de el ile yanıt eylemleri](defender-endpoint-plan-1.md#manual-response-actions)
