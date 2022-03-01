---
title: Saniyeler içinde kötü amaçlı yazılımı algılamak için ilk görüşte engellemeyi etkinleştir
description: Saniyeler içinde kötü amaçlı yazılımları tespit etmek ve engellemek için ilk görüşte blok özelliğini açabilirsiniz.
keywords: tarama, ilk görüşte engelle, kötü amaçlı yazılım, ilk görüş, bulut, defender, virüsten koruma
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: high
author: denisebmsft
ms.author: deniseb
ms.reviewer: marcmcc
manager: dansimp
ms.custom: nextgen
ms.date: 10/18/2021
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: c955ab15640a8c3154e14ba0201946e109f832a9
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63015208"
---
# <a name="turn-on-block-at-first-sight"></a>Bloğu ilk görüşte açma

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Bu makalede, "ilk görüşte engelle" olarak bilinen virüsten koruma/kötü amaçlı yazılımdan koruma özelliği ve kurum için ilk görüşte blok özelliğinin nasıl etkinleştirdiği açıklanmıştır.

> [!TIP]
> Bu makale, kuruluşlar için güvenlik ayarlarını yöneten kuruluş yöneticilerine ve IT Profesyonellerine yöneliktir. Birden çok yönetici değilseniz veya Pro ilk görüşte engelleme hakkında sorularınız varsa Kurumsal yönetici değil veya PRO[? bölümüne](#not-an-enterprise-admin-or-it-pro) bakın.

## <a name="what-is-block-at-first-sight"></a>"İlk görüşte blok" nedir?

İlk görüşte engelle, yeni kötü amaçlı yazılımı algılayan ve saniyeler içinde bunu engelleyen bir yeni nesil koruma özelliğinin tehdit koruması özelliğidir. Bazı güvenlik ayarları etkinleştirildiğinde ilk görüşte engelle etkinleştirilir. Bu ayarlar şunlardır:

- Bulut teslimi koruma;
- Belirtilen bir örnek gönderim zaman aşımı (50 saniye gibi); ve
- Dosya engelleme düzeyi yüksek.

Çoğu kurumsal kuruluşta, ilk görüşte blokları etkinleştirmek için gereken ayarlar en son dağıtımlarda Microsoft Defender Virüsten Koruma yapılandırılır.

## <a name="how-it-works"></a>Nasıl çalışır?

Şüpheli Microsoft Defender Virüsten Koruma ancak algılanmamış bir dosyayla karşılaştığında, bulut koruma arka ucumızı sorgular. Bulut arka ucu, dosyaların kötü amaçlı olup olmadığını belirlemek için dosyanın heuristics, machine learning ve otomatik çözümlemelerini kullanır.

Microsoft Defender Virüsten Koruma, doğru, akıllı ve gerçek zamanlı koruma sağlamak için çeşitli algılama ve önleme teknolojileri kullanır.

![Microsoft Defender AV motorlarının listesi.](images/microsoft-defender-atp-next-generation-protection-engines.png)  

> [!TIP]
> Daha fazla bilgi edinmek için bkz. (Blog) Yeni nesil koruma uç nokta [için Microsoft Defender'ın temel noktasını kullanarak gelişmiş teknolojileri öğrenin](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/).

## <a name="a-few-things-to-know-about-block-at-first-sight"></a>İlk görüşte blok hakkında bilmek gereken birkaç şey

- Dosya Windows 10 1803 veya sonraki sürümlerde, ilk görüşte blok taşınabilir olmayan dosya (JS, VBS veya makrolar gibi) ve yürütülebilir dosyaları engelleyebilir.

- İlk görüşte engelle, yalnızca İnternet'ten indirilen ya da İnternet bölgesinden gelen yürütülebilir dosyalar ve taşınabilir olmayan yürütülebilir dosyalar için bulut koruma arka ucu kullanır. Dosyanın daha önce .exe bir dosya olup olmadığını belirlemek için bulut arka ucu üzerinden dosyanın karma değeri denetlenir.

- Bulut arka ucu belirlemeyi yapamazsa, Microsoft Defender Virüsten Koruma dosyayı kilitler ve bir kopyasını buluta yükler. Bulut, dosyanın kötü amaçlı olup olmadığını kötü amaçlı olarak belirleyip belirlemeyeceğine bağlı olarak, gelecekte karşılaşacak tüm işlemlerde dosyanın çalışmasına izin verilemeden veya engellemeden önce bir karara varacak şekilde daha fazla çözümleme yapar.

- Bu işlem birçok durumda, yeni kötü amaçlı yazılımlar için yanıt süresini saatler'den saniyelere kadar azaltır.

- Bulut [tabanlı koruma hizmeti dosyayı çözümlerken bir](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md) dosyanın ne kadar süreyle çalıştırnması gerektiğini belirtebilirsiniz. Ayrıca, bir [dosya engellendiğinde kullanıcıların masaüstleri](/windows/security/threat-protection/windows-defender-security-center/wdsc-customize-contact-information) üzerinde görüntülenen iletiyi özelleştirebilirsiniz. Şirket adını, iletişim bilgilerini ve ileti URL'sini değiştirebilirsiniz.

## <a name="turn-on-block-at-first-sight-with-microsoft-intune"></a>Engellemeyi ilk görüşte aç Microsoft Intune

> [!TIP]
> Microsoft Intune artık bu yeni Microsoft Endpoint Manager.

1. Cihaz Microsoft Endpoint Manager () merkezinde<https://endpoint.microsoft.com> Cihaz Yapılandırması **profilleri'ne** \> gidin.

2. Cihaz kısıtlamaları profil türünü kullanarak **bir profil seçin veya** oluşturun.

3. Cihaz **kısıtlamaları profilinin** Yapılandırma ayarlarında, Aşağıdaki Ayarları Ayarla'nın altında aşağıdaki ayarları **Microsoft Defender Virüsten Koruma:**

   - **Bulut teslimi koruması**: Etkin
   - **Dosya Engelleme Düzeyi**: Yüksek
   - **Buluta göre dosya tarama için zaman uzantısı**: 50
   - **Örnek göndermeden önce kullanıcılara sor**: Tüm verileri sorulmadan gönder

   :::image type="content" source="../../media/intune-block-at-first-sight.png" alt-text="İlk görüşte Intune config bloğu.":::

4. Ayarlarınızı kaydedin.

> [!TIP]
>
> - Dosya engelleme düzeyini Yüksek olarak **ayarlanması** , güçlü bir algılama düzeyi uygular. Olası bir durumda, dosya engellemenin geçerli dosyaların hatalı olarak algılanmasına neden olması durumunda, güvenlik işlemleri ekipleri karantinaya alınmış dosyaları [geri yükleyebilir](./restore-quarantined-files-microsoft-defender-antivirus.md).
> - Intune'da cihaz Microsoft Defender Virüsten Koruma yapılandırma hakkında daha fazla bilgi için bkz. Intune'da [cihaz kısıtlama ayarlarını Microsoft Intune](/intune/device-restrictions-configure).
> - Intune'Microsoft Defender Virüsten Koruma ilgili cihaz kısıtlamalarının listesi için bkz. [Intune'da Windows 10 ayarları için cihaz kısıtlaması](/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

## <a name="turn-on-block-at-first-sight-with-microsoft-endpoint-manager"></a>Blokları ilk görüşte aç Microsoft Endpoint Manager

> [!TIP]
> Yeni bir Microsoft Endpoint Configuration Manager arıyorsanız, artık bu yeni Microsoft Endpoint Manager.

1. Yeni Microsoft Endpoint Manager ( ),<https://endpoint.microsoft.com> Uç nokta güvenliği **Virüsten Koruma'ya** \> **gidin**.

2. Mevcut bir ilkeyi seçin veya geçerli profil türünü kullanarak **Microsoft Defender Virüsten Koruma** oluşturun.

3. Aşağıdaki yapılandırma ayarlarını ayarlayın veya onaylayın:

   - **Buluta teslim edilen korumayı açma**: Evet
   - **Bulut teslimi koruma düzeyi**: Yüksek
   - **Microsoft Defender Virüsten Koruma Saniye Olarak Uzatılmış Zaman Aşımı**: 50

   :::image type="content" source="images/endpointmgr-antivirus-cloudprotection.png" alt-text="Yeni uygulamanın ilk görme Endpoint Manager.":::

4. Grup Microsoft Defender Virüsten Koruma, Tüm kullanıcılar, Tüm cihazlar veya Tüm **kullanıcılar** **ve cihazlar** gibi **bir gruba kullanıcı profili uygulayabilirsiniz**.

## <a name="turn-on-block-at-first-sight-with-group-policy"></a>Grup İlkesi ile ilk görüşte blokları açma

> [!NOTE]
> Engeli ilk görüşte açmak Microsoft Endpoint Manager Intune veya Başka bir şey kullanmalarını öneririz.

1. Grup İlkesi yönetim bilgisayarınızda Grup İlkesi Yönetim [Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'yi **seçin**.

2.  Grup İlkesi **Yönetim Düzenleyicisi'ni kullanarak**, **HARITALAR'da Bilgisayar yapılandırması** \> \> **Windows Şablonları** \> **Microsoft Defender Virüsten Koruma** \> **gidin**.

3. HARITALAR bölümünde 'İlk Görüşte Engelle **' özelliğini yapılandır'a** çift tıklayın ve bunu Etkin olarak ayarlayın **ve tamam'ı** **seçin**.

    > [!IMPORTANT]
    > Her zaman **sor (0) ayarı** cihazın koruma durumunu düşürecek. Hiçbir zaman **gönderme (2) olarak ayar** yapmak, ilk görüşte engelleme işlevinin çalışmaymayacak anlamına gelir.

4. HARITALAR bölümünde, Daha fazla çözümleme gerektiğinde dosya **örnekleri gönder'e çift tıklayın** ve bunu Etkin olarak **ayarlayın**. Daha **fazla çözümleme gerektiğinde Dosya örnekleri gönder'in altında** Tüm örnekleri **gönder'i ve** sonra Tamam'ı **seçin**.

5. Grup İlkesi Nesnenizi ağ üzerinde her zaman olduğu gibi yeniden sırayın.

## <a name="confirm-block-at-first-sight-is-enabled-on-individual-client-devices"></a>tek tek istemci cihazlarda ilk görüşte engellemenin etkinleştirildiğinden onaylayın

Windows Güvenliği uygulamasını kullanarak, ilk görüşte bloğun tek tek istemci cihazlarda etkinleştir Windows Güvenliği onaylayın. Bulut teslimi koruması ve Otomatik örnek **gönderimi açık** olduğu sürece ilk **görüşte** Engelle otomatik olarak etkinleştirilir.

1. Windows Güvenliği açın.

2. Virüs **ve &'i seçin** ve ardından Virüs koruması altında, & koruma ayarlarını **yönet'i Ayarlar**.

   :::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="Windows Güvenliği uygulamasında virüs koruması & ayarları etiketinin ekran görüntüsü":::

3. Bulut **teslimi korumasının ve Otomatik** örnek **gönderimin her ikisinin** de açık olduğunu onaylayın.

> [!NOTE]
>
> - Önkoşul ayarları Grup İlkesi kullanılarak yapılandırılır ve dağıtılırsa, bu bölümde açıklanan ayarlar gri olur ve uç noktaların tek tek kullanımı için kullanılamaz.
> - Grup İlkesi Nesnesi aracılığıyla yapılan değişikliklerin, ayarın Grup İlkesi Nesnesinde güncelleştirilmeden önce tek tek uç noktalara dağıtılması Windows Ayarlar.

## <a name="validate-block-at-first-sight-is-working"></a>İlk görüşte bloğun çalıştığını doğrulama

Özelliğin çalıştığını doğrulamak için ilk görmede [engelle örnek dosyasını indirin](https://demo.wd.microsoft.com/Page/BAFS). Dosyayı indirmek için Azure AD'de Güvenlik Yöneticisi veya Genel Yönetici rolünün atandığı bir hesaba ihtiyacınız vardır.

Bulut özellikli korumanın çalıştığını doğrulamak için Ağınız ile bulut arasındaki bağlantıları [doğrulama konusunda yer alan yönergeleri izleyin](configure-network-connections-microsoft-defender-antivirus.md#validate-connections-between-your-network-and-the-cloud).

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

## <a name="turn-off-block-at-first-sight"></a>İlk görüşte blokları kapatma

> [!CAUTION]
> İlk görüşte engellemeyi kapatarak cihazlarınızı ve ağlarınızı koruma durumunu düşürebilirsiniz.

önkoşul ayarlarını, aslında ilk görme korumasında blok özelliğini kullanmadan korumak için ilk görmede engellemeyi devre dışı bırakmayı seçebilirsiniz. Bu özelliğin ağın nasıl etkileyeceğini görmek için ilk görüşte engellemeyi geçici olarak kapatabilirsiniz. Ancak, ilk görme koruması için engellemenin kalıcı olarak devre dışı bırakılması önerilmez.

### <a name="turn-off-block-at-first-sight-with-microsoft-endpoint-manager"></a>Görme engeli ilk görüşte Microsoft Endpoint Manager

1. Yönetim Microsoft Endpoint Manager (<https://endpoint.microsoft.com>) gidin ve oturum açma.

2. Uç nokta **güvenliği Virüsten** **Koruma'ya**\> gidin ve sonra Microsoft Defender Virüsten Koruma seçin.

3. **Yönet'in** altında **Özellikler'i seçin**.

4. Yapılandırma **ayarları'nın yanında** Düzenle'yi **seçin**.

5. Aşağıdaki ayarlardan birini veya birden fazlasını değiştirin:

   - Bulut **teslimi korumasını aç'a Hayır** **veya Yapılandırılmadı** **olarak ayarlayın**.
   - Bulut **teslimi koruma düzeyini Yapılandırılmadı** **olarak ayarlayın**.
   - Saniye olarak Uzatılmış Zaman **Microsoft Defender Virüsten Koruma onay kutusunu temizleyin**.

6. Ayarlarınızı gözden geçirin ve kaydedin.

### <a name="turn-off-block-at-first-sight-with-group-policy"></a>Grup İlkesi ile ilk görüşte engellemeyi kapatma

1. Grup İlkesi yönetim bilgisayarınızda Grup İlkesi Yönetim [Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'yi **seçin**.

2. Grup İlkesi **Yönetim Düzenleyicisi'ni kullanarak Bilgisayar** **yapılandırması'ne gidin ve** Yönetim **şablonları'ı seçin**.

3. HARITALAR'da Windows **bileşenleri Microsoft Defender Virüsten Koruma** \>  \> **genişletin**.

4. **'İlk Görüşte Engelle' özelliğini yapılandır'a çift tıklayın ve** seçeneği Devre Dışı olarak **ayarlayın**.

    > [!NOTE]
    > İlk görüşte engellemeyi devre dışı bırakmak, önkoşul grup ilkelerini devre dışı bırakmaz veya değiştirmez.

## <a name="not-an-enterprise-admin-or-it-pro"></a>Kuruluş yöneticisi veya IT yöneticisi Pro?

Kurumsal yönetici veya IT yöneticisi değilseniz Pro ilk görüşte blok hakkında sorularınız varsa, bu bölüm tam size göredir. İlk görüşte engelle, saniyeler içinde kötü amaçlı yazılımları algılayan ve engelleyen bir tehdit koruması özelliğidir. "İlk görüşte engelle" olarak adlandırılan belirli bir ayar olsa da, aygıtınızda bazı ayarlar yapılandırıldığında özellik etkinleştirilir.

### <a name="how-to-manage-block-at-first-sight-on-or-off-on-your-own-device"></a>Kendi cihazınızla ilk görüşte engellemeyi yönetme veya kapatma

Bir kuruluş tarafından yönetilmiyor kişisel cihazınız varsa ilk görüşte engellemeyi nasıl açabilirsiniz veya kapatabilirsiniz. Windows Güvenliği'i ilk görüşte yönetmek için Windows Güvenliği uygulamasını kullanabilirsiniz.

1. Windows 10 veya Windows 11 bilgisayarınızda Windows Güvenliği açın.

2. Virüs **ve tehdit &'yi seçin**.

3. Virüs **koruması & ayarları'nın altında** Ayarları **yönet'i seçin**.

4. Aşağıdaki adımlardan birini uygulayın:

   - Bloğu ilk görüşte etkinleştirmek için, hem Bulut teslimi  korumasının hem de Otomatik  örnek gönderimin açık olduğundan emin olun.

   - Engellemeyi ilk görüşte devre dışı bırakmak için Bulut **teslimi korumasını veya Otomatik** örnek **gönderimi kapatın**.

     > [!CAUTION]
     > İlk görüşte engellemeyi kapatsanız, cihazınız için koruma düzeyi daha düşüktür. İlk görüşte engellemenin kalıcı olarak devre dışı bırakılması önerilmez.


## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Bulut teslimi korumasını etkinleştirme](enable-cloud-protection-microsoft-defender-antivirus.md)
- [Güvenlikle korunmaya Windows Güvenliği](https://support.microsoft.com/windows/stay-protected-with-windows-security-2ae0363d-0ada-c064-8b56-6a39afb6a963)
