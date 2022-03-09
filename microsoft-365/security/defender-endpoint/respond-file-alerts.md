---
title: Uç Nokta için Microsoft Defender'da dosya üzerinde yanıt eylemleri gerçekleştirin
description: Bir dosyayı durdurarak ve kullanarak ya da dosyayı engelleyerek ve etkinlik ayrıntılarını kontrol ederek dosyayla ilgili uyarılarda yanıt eylemleri gerçekleştirin.
keywords: Yanıtlama, durdurma ve karantinaya al, dosyayı engelleme, derin çözümleme
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
ms.openlocfilehash: 0e7253993a1c05bd25e6dd13865826c42dd7603a
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63400258"
---
# <a name="take-response-actions-on-a-file"></a>Dosyada yanıt eylemleri gerçekleştirin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

[!include[Prerelease information](../../includes/prerelease.md)]

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-responddile-abovefoldlink)

Dosyaları durdurarak ve kullanarak veya bir dosyayı engelleyerek algılanan saldırılara hızlı bir şekilde yanıt verin. Dosyalar üzerinde işlem yapıldıktan sonra, İşlem merkezi'nde etkinlik ayrıntılarını kontrol edin.

Yanıt eylemleri, dosyanın ayrıntılı profil sayfasında kullanılabilir. Bu sayfaya başladıktan sonra, yeni Dosya sayfasını kapatarak yeni ve eski sayfa düzenleri **arasında geçişebilirsiniz**. Bu makalenin kalan kalanında daha yeni olan sayfa düzeni açıklanmıştır.

Yanıt eylemleri dosya sayfasının en üstünde görüntülenir ve şunları içerir:

- Dosyayı Durdur ve Karantinaya Alın
- Gösterge Ekle
- Dosyayı indir
- Tehdit uzmanına danışın
- İşlem merkezi

Ayrıca, dosyayı güvenli bir bulut korumalı alanda çalıştırmak için dosyaları derinlemesine çözümlemeye gönderebilirsiniz. Çözümleme tamamlandığında, dosyanın davranışı hakkında bilgi sağlayan ayrıntılı bir rapor elde edinebilirsiniz. Derin çözümleme sekmesini seçerek dosyaları daha derin çözümleme için gönderebilirsiniz ve geçmiş **raporları okuyabilirsiniz** . Dosya bilgileri kartlarında yer almaktadır.

Bazı eylemler için belirli izinler gerekir. Aşağıdaki tabloda, taşınabilir yürütülebilir (PE) ve PE olmayan dosyalar üzerinde belirli izinlerin gerçekleştirebilirleri eylem açık almaktadır:

<br>

****

|İzin|PE dosyaları|Pe olmayan dosyalar|
|---|:---:|:---:|
|Verileri görüntüleme|X|X|
|Uyarı soruşturması|&#x2611;|X|
|Canlı yanıt temel|X|X|
|Canlı yanıt gelişmiş|&#x2611;|&#x2611;|
|

Roller hakkında daha fazla bilgi için bkz [. Rol tabanlı erişim denetimi için roller oluşturma ve yönetme](user-roles.md).

## <a name="stop-and-quarantine-files-in-your-network"></a>Ağ içinde dosyaları durdurma ve karantinaya alın

Kötü amaçlı işlemi durdurarak ve gözlemlenen dosyayı kullanarak saldırılar bulundurabilirsiniz.

> [!IMPORTANT]
> Bu eylemi yalnızca şu durumla karşı  gerekir:
>
> - Üzerinde eyleme geçen cihaz, 1703 veya Windows 10 sürüm 11'de veya Windows çalışıyor
> - Dosya güvenilir üçüncü taraf yayıncılara ait değildir veya Microsoft tarafından imzalanmıştır
> - Microsoft Defender Virüsten Koruma Pasif modunda çalışıyor olması gerekir. Daha fazla bilgi için uyumluluk [Microsoft Defender Virüsten Koruma bakın](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility).

Dosyayı **Durdur ve Karantinaya** Al eylemi, işlemleri çalıştırmayı durdurmayı, dosyaları başka bir şekilde çalıştırmayı ve kayıt defteri anahtarları gibi kalıcı verileri silmeyi içerir.

Bu eylem, dosyanın son 30 gün içinde Windows 10, sürüm 1703 veya Windows 11'i olan cihazlarda geçerli olur.

> [!NOTE]
> Her zaman dosyayı karantinadan geri yükleyebilirsiniz.

### <a name="stop-and-quarantine-files"></a>Dosyaları durdurma ve karantinaya alın

1. Durdurmak istediğiniz dosyayı seçin ve karantinaya alın. Aşağıdaki görünümlerden herhangi biri için dosya seçerek veya Arama kutusunu kullanabilirsiniz:

   - **Uyarılar** - Uyarı Anlatı zaman çizelgesinde Açıklama veya Ayrıntılar'daki ilgili bağlantılara tıklayın
   - **Arama kutusu** - **açılan** menüden Dosya'ı seçin ve dosya adını girin

   > [!NOTE]
   > Dosya durdurma ve karantina eylemi en çok 1000 cihazla sınırlıdır. Dosyayı çok sayıda cihazlarda durdurmak için bkz. Dosyayı engellemek [veya buna izin vermek için gösterge ekleme](#add-indicator-to-block-or-allow-a-file).

2. Üst çıtaya gidip Dosyayı Durdur **ve Karantinaya Bırak'ı seçin**.

   ![Dosya durdurma ve karantina eyleminin resmi.](images/atp-stop-quarantine-file.png)

3. Bir neden belirtin, ardından **Onayla'ya seçin**.

   ![Dosya kalıcı olarak durdurma ve karantinaya alın penceresinin resmi.](images/atp-stop-quarantine.png)

   İşlem merkezi, gönderim bilgilerini gösterir:

   ![Dosya durdurma ve karantinaya alındı işlem merkezi görüntüsü.](images/atp-stopnquarantine-file.png)

   - **Gönderme süresi** - Eylemin ne zaman gönder olduğunu gösterir.
   - **Başarı** - Dosyanın durdurularak karantinaya alındığı cihaz sayısını gösterir.
   - **Başarısız** - Eylemin başarısız olduğu cihaz sayısını ve hatayla ilgili ayrıntıları gösterir.
   - **Beklemede** - Dosyanın durdurulma ve karantinaya alındığı cihazların sayısını gösterir. Bu durum, cihazın çevrimdışı olduğu veya ağa bağlı olmadığının durumlar için zaman al götürebilirsiniz.

4. Eylem hakkında daha fazla bilgi görüntülemek için durum göstergelerini seçin. Örneğin, eylemin **başarısız olduğu** yeri görmek için Başarısız'ı seçin.

#### <a name="notification-on-device-userf"></a>Cihaz kullanıcı bildirimi

Dosya bir cihazdan kaldırıldığı zaman aşağıdaki bildirim gösterilir:

![Cihaz kullanıcısı bildiriminin resmi.](images/atp-notification-file.png)

Cihaz zaman çizelgesinde, dosyanın durdurulmuş ve karantinaya alınmış olduğu her cihaz için yeni bir olay eklenir.

Kuruluş genelinde yaygın olarak kullanılan dosyalar için eylem uygulanmadan önce bir uyarı gösterilir. Bunun amacı, bu işlemi yapmak olduğunu doğrulamaktır.

## <a name="restore-file-from-quarantine"></a>Dosyayı karantinadan geri yükleme

Bir incelemeden sonra temiz olduğunu belirlediysanız, dosyayı geri alın ve karantinadan kaldırabilirsiniz. Dosya karantinaya alınmış her cihazda aşağıdaki komutu çalıştırın.

1. Cihazda yükseltilmiş komut satırı istemini açın:

   1. **Başlat'a gidin** ve _cmd yazın_.

   1. Komut istemi'ne **sağ tıklayın ve** Yönetici olarak **çalıştır'ı seçin**.

2. Aşağıdaki komutu girin ve Enter tuşuna **basın**:

   ```dos
   "%ProgramFiles%\Windows Defender\MpCmdRun.exe" -Restore -Name EUS:Win32/CustomEnterpriseBlock -All
   ```

   > [!NOTE]
   > Bazı senaryolarda **ThreatName** şöyle görünebilir: EUS:Win32/CustomEnterpriseBlock!cl.
   >
   > Uç Nokta için Defender, son 30 gün içinde bu cihazda karantinaya alınmış olan tüm özel engellenen dosyaları geri yükleyebilir.

> [!IMPORTANT]
> Olası ağ tehditi olarak karantinaya alınmış bir dosya kurtarılamaz olabilir. Kullanıcı karantinadan sonra dosyayı geri yükleme girişiminde olursa, bu dosyaya erişilemez. Bunun nedeni sistemin artık dosyaya erişmek için ağ kimlik bilgilerine sahip olması olabilir. Normalde, bu durum sistem veya paylaşılan klasörde geçici olarak oturum açmanın sonucudur ve erişim belirteçlerinin süresi dolar.

## <a name="download-or-collect-file"></a>Dosya indirme veya toplama

Yanıt **eylemlerinden Dosyayı** indir'i seçmek, dosyanızı içeren yerel, parola korumalı bir .zip arşiv indirmenize olanak sağlar. Dosyayı indirme nedeni kaydederek bir parola ayar İlkeyi ayarlayabiliyorsanız, bir çıkış görüntülenir.

Varsayılan olarak, karantinada olan dosyaları indirebilirsiniz.

![Dosya indirme eyleminin resmi.](images/atp-download-file-action.png)

### <a name="download-quarantined-files"></a>Karantinaya alınmış dosyaları indirme

Posta dosyaları veya güvenlik Microsoft Defender Virüsten Koruma tarafından karantinaya alınan dosyalar, örnek gönderim yapılandırmalarına göre [uyumlu bir şekilde kaydedilir](enable-cloud-protection-microsoft-defender-antivirus.md). Güvenlik ekipleri "Dosyayı indir" düğmesi aracılığıyla dosyaları doğrudan dosyanın ayrıntı sayfasından indirebilir. **Bu önizleme özelliği varsayılan olarak 'Açık' durumdadır**.

Konum, kuruluş ayarlarına (AB, İngiltere veya ABD) bağlıdır. Karantinaya alınmış bir dosya, kuruluş başına yalnızca bir kez toplanır. Hizmet Güveni Portalı'nda Microsoft'un veri koruması hakkında daha fazla bilgi edinmek için:https://aka.ms/STP

Bu ayarın açık olması, güvenlik ekiplerinin kötü olabilecek dosyaları incelemelerine ve olayları daha hızlı ve daha az riskli bir yolla incelemelerine yardımcı olabilir. Bununla birlikte, bu ayarı  kapatmanız gerekirse, Gelişmiş Uç **Noktalar** \>  \> \> Ayarlar Karantinaya alınmış dosyaları **indir'e** gidip ayarı ayarlayın. [Gelişmiş özellikler hakkında daha fazla bilgi](advanced-features.md)

#### <a name="backing-up-quarantined-files"></a>Karantinaya alınmış dosyaları geri yükleme

Örnek gönderim yapılandırmanıza bağlı olarak, kullanıcılardan karantinaya alınmış dosyayı geri yüklemeden önce açık bir izin [sağlamaları istenebilirsiniz](enable-cloud-protection-microsoft-defender-antivirus.md#use-group-policy-to-turn-on-cloud-protection).

Örnek gönderme kapalı ise bu özellik çalışmaz. Otomatik örnek gönderimi kullanıcıdan izin istenecek şekilde ayarlanırsa, yalnızca kullanıcının göndermeyi kabulladığı örnekler toplanır.

> [!IMPORTANT]
> Karantinaya alınmış dosya gereksinimlerini karşıdan yükleme:
>
> - Organizasyonun etkin Microsoft Defender Virüsten Koruma kullanıcı kullanıyor
> - Virüsten koruma altyapısı sürümü 1.1.17300.4 veya sonraki bir sürümdür. Aylık [platform ve altyapı sürümlerine bakın](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions)
> - Bulut tabanlı koruma etkinleştirilir. Bkz [. Buluta teslim edilen korumayı açma](enable-cloud-protection-microsoft-defender-antivirus.md)
> - Örnek gönderme açık
> - Cihazların Windows 10 1703 veya sonraki bir sürümü, Windows server 2016 veya 2019 ya da Windows Server 2022 veya Windows 11'i vardır

### <a name="collect-files"></a>Dosyaları toplama

Dosya henüz Uç Nokta için Microsoft Defender tarafından depolanıyorsa, dosyayı indirebilirsiniz. Bunun yerine, aynı konumda **Bir Dosya topla** düğmesi görüyoruz. Son 30 gün içinde kuruluşta hiç dosya görülmemişse, Dosya **topla devre dışı** bırakılır.
> [!Important]
> Olası ağ tehditi olarak karantinaya alınmış bir dosya kurtarılamaz olabilir. Kullanıcı karantinadan sonra dosyayı geri yükleme girişiminde olursa, bu dosyaya erişilemez. Bunun nedeni sistemin artık dosyaya erişmek için ağ kimlik bilgilerine sahip olması olabilir. Normalde, bu durum sistem veya paylaşılan klasörde geçici olarak oturum açmanın sonucudur ve erişim belirteçlerinin süresi dolar.

## <a name="add-indicator-to-block-or-allow-a-file"></a>Dosyayı engellemek veya dosyaya izin vermek için gösterge ekleme

Olası kötü amaçlı dosyaları veya kötü amaçlı yazılımdan şüpheleniyorlar tarafından engellenebilir ve saldırının organizasyona daha fazla yayılmasını önle. Kötü amaçlı olabilecek bir taşınabilir yürütülebilir (PE) dosyası biliyorsanız, dosyayı engelleyebilirsiniz. Bu işlem, okunmalarını, yazıldıklarını veya organizasyonlar üzerinde yürütüleceklerini önler.

> [!IMPORTANT]
>
> - Bu özellik, bulut teslimi korumasının Microsoft Defender Virüsten Koruma tarafından etkinleştirildiğinde kullanılabilir. Daha fazla bilgi için bkz [. Bulut teslimi korumasını yönetme](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus).
>
> - Kötü amaçlı yazılımdan koruma istemci sürümü 4.18.1901.x veya sonraki bir sürümde olabilir.
> - Bu özellik kötü amaçlı yazılımdan (veya kötü amaçlı olabilecek dosyalardan) şüphelenilen dosyaların Web'den indirilmalarını önlemek için tasarlanmıştır. Şu anda dosya dosyaları ve yürütülebilir dosyalar da dahil olmak üzere taşınabilir _yürütülebilir (PE_ ) _.exe.dll_ destekler. Kapsam zaman içinde uzatılacaktır.
> - Bu yanıt eylemi 11. Windows 10, sürüm 1703 veya daha sonraki sürümler Windows kullanılabilir.
> - İzin verme veya engelleme eylemi öncesinde dosyanın sınıflandırması cihazın önbelleği üzerinde bulunuyorsa, izin ver veya engelle işlevi dosyalar üzerinde yapılamaz.

> [!NOTE]
> Bu eylemi benim için PE dosyasının cihaz zaman çizelgesinde olması gerekir.
>
> Eylemin gerçek dosyayla alınması arasında birkaç dakika gecikme süresi olabilir.

### <a name="enable-the-block-file-feature"></a>Dosyayı engelleme özelliğini etkinleştirme

Dosyaları engellemeye başlamak için önce Dosya [bloğunda Engelle **veya izin** ver özelliğini Ayarlar](advanced-features.md).

### <a name="allow-or-block-file"></a>Dosyaya izin verme veya dosyayı engelleme

Dosya için bir gösterge karması eklerken, bir uyarı bırakmayı ve kuruluşta bir cihaz bu karmayı çalıştırmayı her çalıştırsa dosyayı engellemeyi seçebilirsiniz.

Otomatik olarak bir gösterge tarafından engellenen dosyalar dosyanın İşlem merkezinde görünmez, ancak uyarılar Uyarılar sırasında görünmeye devam eder.

[Dosyalarda uyarı engelleme ve](manage-indicators.md) yükseltmeyle ilgili daha fazla ayrıntı için göstergeleri yönetme'ye bakın.

Dosyanın engellenmesini durdurmak için göstergeyi kaldırın. Bunu, dosyanın **profil sayfasındaki** Göstergeyi Düzenle eylemiyle de yapabiliriz. Bu eylem, göstergeyi eklemeden önce **Gösterge** Ekle eylemiyle aynı konumda görünür.

Ayrıca, Yeni Sayfa sayfasındaki Kurallar **Ayarlar** **göstergelerini düzenleyebilirsiniz**\>. Göstergeler bu alanda dosyanın karma değerine göre listelenir.

## <a name="consult-a-threat-expert"></a>Tehdit uzmanına danışın

Güvenliği tehlikeye atılmış olabilecek cihazlar veya zaten güvenliği tehlikeye atılmış cihazlar hakkında daha fazla bilgi için Bir Microsoft tehdit uzmanına danışın. Microsoft Tehdit Uzmanları ve doğru yanıt için Microsoft 365 Defender portalında doğrudan meşgul olur. Uzmanlar güvenliği tehlikeye atabilecek bir cihaz hakkında içgörüler sağlar ve karmaşık tehditleri ve hedefli saldırı bildirimlerini anlamanıza yardımcı olur. Ayrıca, portal panoda gördüğünüz uyarılar veya tehdit İstihbaratı bağlamı hakkında da bilgi sağlayabilecektir.

Ayrıntılar [için Bkz. Microsoft Tehdit Uzmanına](/microsoft-365/security/defender-endpoint/configure-microsoft-threat-experts#consult-a-microsoft-threat-expert-about-suspicious-cybersecurity-activities-in-your-organization) Danışma.

## <a name="check-activity-details-in-action-center"></a>İşlem merkezinde etkinlik ayrıntılarını denetleme

İşlem **merkezi** , bir cihaz veya dosya üzerinde yapılan işlemlerle ilgili bilgi sağlar. Aşağıdaki ayrıntıları görüntüebilirsiniz:

- Araştırma paketi koleksiyonu
- Virüsten koruma taraması
- Uygulama kısıtlaması
- Cihaz yalıtlığı

Gönderme tarihi/saati, gönderilen kullanıcı ve eylem başarılı olursa ya da başarısız olursa diğer tüm ilgili ayrıntılar da gösterilir.

![Bilgili işlem merkezi görüntüsü.](images/action-center-details.png)

## <a name="deep-analysis"></a>Derin çözümleme

Siber güvenlik soruşturmaları normalde bir uyarı tarafından tetiklenir. Uyarılar çoğunlukla yeni veya bilinmeyen gözlenen bir veya birden çok dosyayla ilgilidir. Dosya seçerek, dosyanın meta verilerini görüntülebilirsiniz. Dosyayla ilgili verileri zenginleştirmek için, dosyayı derinlemesine çözümlemek için gönderebilirsiniz.

Derin çözümleme özelliği, dosyayı güvenli, tam araçlı bir bulut ortamında yürütür. Derin çözümleme sonuçları, dosyanın etkinliklerini, gözlemlenen davranışları ve bırakılan dosyalar, kayıt defteri değişiklikleri ve IP'lerle iletişim gibi ilişkili yapıları gösterir.
Derin çözümleme şu anda taşınabilir yürütülebilir (PE) dosyalarının (yürütülebilir dosya ve dosya _.exe_ ) kapsamlı _.dll_ desteklemektedir.

Dosyanın derin çözümlemesi birkaç dakika sürer. Dosya çözümlemesi tamamlandıktan sonra Derin Çözümleme sekmesi, eldeki en son sonuçların özetini ve tarih ve saati görüntüleyebilirsiniz.

Derin çözümleme özeti, bazıları kötü amaçlı etkinlikleri ve diskte oluşturulan iletişimlenmiş IP'ler ve dosyalar da dahil olmak üzere gözlenen davranışların listesini içerir. Hiçbir şey bulunamazsa, bu bölümlerde kısa bir ileti görüntülenir.

Derin çözümleme sonuçları tehdit zekası ile eştir ve tüm eşleşmeler uygun uyarılar üretir.

Herhangi bir dosyanın ayrıntılarını, genellikle bir uyarının araştırılması sırasında veya kötü amaçlı davranış şüphesi olan başka bir nedenle araştırmak için derin çözümleme özelliğini kullanın. Bu özellik, derin **çözümleme** sekmesinde, dosyanın profil sayfasında yer alan kullanılabilir.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4aAYy?rel=0]

**Derin çözümleme için** gönder, dosya Uç Nokta arka uç örnek koleksiyonunda dosya kullanılabilir durumda olduğunda veya bu dosya derinlemesine çözümlemeye göndermeyi destekleyen bir Windows 10 cihazda gözlemlendiyse etkinleştirilir.

> [!NOTE]
> Yalnızca Windows 10 ve Windows 11 dosyaları otomatik olarak toplanabilir.

Ayrıca, dosya bir Windows 10 cihazında ([](https://www.microsoft.com/security/portal/submission/submit.aspx)veya Windows 11'de) gözlemlenmedi ise ve daha derin çözümleme düğmesinin kullanılabilir olması için Gönder düğmesinin kullanılabilir olması için Microsoft Güvenlik Merkezi Portalı'nden  bir örnek gönderebilirsiniz.

> [!NOTE]
> Microsoft Güvenlik Merkezi Portalı'daki arka uç işleme akışları nedeniyle, dosya gönderimi ve Uç Nokta için Defender'daki derin çözümleme özelliğinin kullanılabilirliği arasında 10 dakikaya kadar gecikme olabilir.

### <a name="submit-files-for-deep-analysis"></a>Daha derin çözümleme yapmak için dosyaları gönderme

1. Derin çözümleme yapmak için göndermek istediğiniz dosyayı seçin. Aşağıdaki görünümlerin herhangi birini seçerek veya bu dosyada arama yapabilirsiniz:

    - **Uyarılar** - Uyarı Hikaye zaman çizelgesinde **Açıklama'dan** **veya Ayrıntılar'dan** dosya bağlantılarını seçin
    - **Cihazlar listesi** - Kuruluşta cihaz bölümündeki **Açıklama** **veya Ayrıntılar** **bölümünden dosya bağlantılarını** seçin
    - **Arama kutusu** - **açılan** menüden Dosya'ı seçin ve dosya adını girin

2. Dosya **görünümünün Derin** çözümleme sekmesinde Gönder'i **seçin**.

   ![Pe dosyalarını yalnızca dosya ayrıntıları bölümünde gönderebilirsiniz.](images/submit-file.png)

   > [!NOTE]
   > DOSYA VE TİPİ dosyaları da _dahil olmak.exe_ _PE.dll_ destekler.

   İlerleme çubuğu görüntülenir ve çözümlemenin farklı aşamaları hakkında bilgi sağlar. Çözümleme bittiğinde raporu görüntüebilirsiniz.

> [!NOTE]
> Cihazın kullanılabilirlik durumuna bağlı olarak, örnek toplama süresi değişiklik gösterebilir. Örnek koleksiyon için 3 saatlik bir zaman aşımı vardır. Koleksiyon başarısız olur ve bu sırada çevrimiçi bir cihaz (veya 11 Windows 10 11) bildirimi yoksa Windows durdurulacak. Dosya hakkında en yeni verileri elde etmek için, daha derin çözümlemeler yapmak için dosyaları yeniden gönderebilirsiniz.

### <a name="view-deep-analysis-reports"></a>Derin çözümleme raporlarını görüntüleme

Gönderilen dosya hakkında daha ayrıntılı içgörüler görmek için, sağlanan ayrıntılı çözümleme raporunu görüntüye alın. Bu özellik, dosya görünümü bağlamında kullanılabilir.

Aşağıdaki bölümlerde ayrıntılar sağlayan kapsamlı raporu görüntüebilirsiniz:

- Davranışlar
- Gözlenebilirler

Verilen ayrıntılar olası bir saldırının göstergesi varsa araştırmanıza yardımcı olabilir.

1. Daha derin çözümleme yapmak için dosyayı seçin.
2. Derin çözümleme **sekmesini** seçin. Daha önce rapor varsa, rapor özeti bu sekmede görüntülenir.

    ![Ayrıntılı çözümleme raporu, bir dizi kategori arasında ayrıntılı bilgi gösterir.](images/analysis-results-nothing500.png)

#### <a name="troubleshoot-deep-analysis"></a>Derin çözümleme sorunlarını giderme

Dosya göndermek için çalışırken bir sorun oluşursa, aşağıdaki sorun giderme adımlarının her birini deneyin.

1. Söz konusu dosyanın PE dosyası olduğundan emin olun. PE dosyaları genellikle _yürütülebilir.exe_ ya _da.dll_ (yürütülebilir programlar veya uygulamalar) içerir.

2. Hizmetin dosyaya erişimi olduğundan, dosyanın hala var olduğundan ve hiç bozuk veya değiştirilmemiş olduğundan emin olun.

3. Kısa bir süre bekleyin ve dosyayı yeniden göndermeyi deneyin. Kuyruk dolu olabilir veya geçici bir bağlantı veya iletişim hatası olabilir.

4. Örnek koleksiyon ilkesi yapılandırılmamışsa, varsayılan davranış örnek koleksiyona izin vermektir. Yapılandırılmışsa, dosyayı yeniden göndermeden önce örnek toplamaya izin veren ilke ayarının doğrula. Örnek koleksiyon yapılandırıldığında, aşağıdaki kayıt defteri değerini kontrol edin:

    ```text
    Path: HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection
    Name: AllowSampleCollection
    Type: DWORD
    Hexadecimal value :
      Value = 0 - block sample collection
      Value = 1 - allow sample collection
    ```

5. Grup İlkesi aracılığıyla kuruluş birimini değiştirme. Daha fazla bilgi için bkz [. Grup İlkesiyle Yapılandırma](configure-endpoints-gp.md).

6. Bu adımlar sorunu çözmezse, destan ile iletişime geçin.

## <a name="related-topics"></a>İlgili konular

- [Cihazda yanıt eylemleri gerçekleştirin](respond-machine-alerts.md)
- [Dosyaları araştırma](investigate-files.md)
- [Uç Nokta Planı 1 için Microsoft Defender'da el ile yanıt eylemleri](defender-endpoint-plan-1.md#manual-response-actions)
