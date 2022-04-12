---
title: Kötü amaçlı yazılımları saniyeler içinde algılamak için ilk bakışta engellemeyi etkinleştirme
description: Kötü amaçlı yazılımları saniyeler içinde algılamak ve engellemek için ilk bakışta engelleme özelliğini açın.
keywords: tarama, ilk bakışta engelle, kötü amaçlı yazılım, ilk görüş, bulut, defender, virüsten koruma
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
ms.openlocfilehash: 071bd6fe59a7200e1d16cf94633b0d7b3cb688c5
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788116"
---
# <a name="turn-on-block-at-first-sight"></a>İlk görüşte engellemeyi etkinleştirin

**Şunlar için geçerlidir:**

- [Pertahanan Microsoft untuk Titik Akhir Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma 

**Platform**
- Windows

Bu makalede "ilk bakışta engelle" olarak bilinen bir virüsten koruma/kötü amaçlı yazılımdan koruma özelliği açıklanır ve kuruluşunuz için ilk bakışta engellemenin nasıl etkinleştirileceği açıklanır.

> [!TIP]
> Bu makale, kuruluşlar için güvenlik ayarlarını yöneten kuruluş yöneticilerine ve BT Uzmanlarına yöneliktir. Enteprise yöneticisi veya BT Pro değilseniz ancak ilk bakışta engellemeyle ilgili sorularınız varsa [Kurumsal yönetici değil veya BT Pro?](#not-an-enterprise-admin-or-it-pro) bölümüne bakın.

## <a name="what-is-block-at-first-sight"></a>"İlk görüşte blok" nedir?

İlk bakışta engelle yeni nesil korumanın yeni kötü amaçlı yazılımları algılayan ve saniyeler içinde engelleyen bir tehdit koruması özelliğidir. Belirli güvenlik ayarları etkinleştirildiğinde ilk bakışta engelle etkinleştirilir. Bu ayarlar şunlardır:

- Bulut tabanlı koruma;
- Belirtilen örnek gönderim zaman aşımı (50 saniye gibi); Ve
- Dosya engelleme düzeyi yüksek.

Çoğu kurumsal kuruluşta, ilk bakışta engellemeyi etkinleştirmek için gereken ayarlar Microsoft Defender Virüsten Koruma dağıtımlarla yapılandırılır.

## <a name="how-it-works"></a>Nasıl çalışır?

Microsoft Defender Virüsten Koruma şüpheli ancak algılanmamış bir dosyayla karşılaştığında bulut koruma arka ucumuzu sorgular. Bulut arka ucu, dosyaların kötü amaçlı olup olmadığını belirlemek için buluşsal yöntemler, makine öğrenmesi ve dosyanın otomatik analizini uygular.

Microsoft Defender Virüsten Koruma doğru, akıllı ve gerçek zamanlı koruma sağlamak için birden çok algılama ve önleme teknolojisi kullanır.

:::image type="content" source="images/microsoft-defender-atp-next-generation-protection-engines.png" alt-text="Microsoft Defender AV altyapılarının listesi" lightbox="images/microsoft-defender-atp-next-generation-protection-engines.png":::

> [!TIP]
> Daha fazla bilgi edinmek için bkz. [(Blog) yeni nesil korumanın Pertahanan Microsoft untuk Titik Akhir temelindeki gelişmiş teknolojileri tanıma](https://www.microsoft.com/security/blog/2019/06/24/inside-out-get-to-know-the-advanced-technologies-at-the-core-of-microsoft-defender-atp-next-generation-protection/).

## <a name="a-few-things-to-know-about-block-at-first-sight"></a>İlk bakışta blok hakkında bilmeniz gereken birkaç şey

- Windows 10, sürüm 1803 veya sonraki sürümlerde, ilk bakışta engelle taşınabilir olmayan yürütülebilir dosyaları (JS, VBS veya makrolar gibi) ve yürütülebilir dosyaları engelleyebilir.

- Engelle ilk bakışta yalnızca yürütülebilir dosyalar ve İnternet'ten indirilen veya İnternet bölgesinden gelen taşınabilir olmayan yürütülebilir dosyalar için bulut koruma arka ucu kullanır. .exe dosyasının karma değeri, bulut arka ucu üzerinden denetlenerek dosyanın önceden algılanmamış bir dosya olup olmadığını belirler.

- Bulut arka ucu bir belirleme yapamazsa Microsoft Defender Virüsten Koruma dosyayı kilitler ve bir kopyasını buluta yükler. Bulut, dosyanın kötü amaçlı olup olmadığını belirleyip belirlemediğine bağlı olarak dosyanın sonraki tüm karşılaşmalarda çalıştırılmasına veya engellenmesine izin vermeden önce bir belirlemeye ulaşmak için daha fazla analiz gerçekleştirir.

- Çoğu durumda, bu işlem yeni kötü amaçlı yazılımların yanıt süresini saatlerden saniyelere düşürebilir.

- Bulut tabanlı koruma hizmeti dosyayı analiz ederken [bir dosyanın ne kadar süreyle çalışmasının engelleneceğini belirtebilirsiniz](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md) . Ayrıca, bir dosya engellendiğinde [kullanıcıların masaüstünde görüntülenen iletiyi özelleştirebilirsiniz](/windows/security/threat-protection/windows-defender-security-center/wdsc-customize-contact-information) . Şirket adını, kişi bilgilerini ve ileti URL'sini değiştirebilirsiniz.

## <a name="turn-on-block-at-first-sight-with-microsoft-intune"></a>Microsoft Intune ile ilk bakışta bloğu açma

> [!TIP]
> Microsoft Intune artık Microsoft Endpoint Manager bir parçasıdır.

1. Microsoft Endpoint Manager yönetim merkezinde (<https://endpoint.microsoft.com> ) **Cihazlar** \> **Yapılandırma profilleri'ne** gidin.

2. **Cihaz kısıtlamaları** profil türünü kullanarak bir profil seçin veya oluşturun.

3. Cihaz kısıtlamaları profilinin **Yapılandırma ayarları** bölümünde, **Microsoft Defender Virüsten Koruma** altında aşağıdaki ayarları ayarlayın veya onaylayın:

   - **Bulut tabanlı koruma**: Etkin
   - **Dosya Engelleme Düzeyi**: Yüksek
   - **Bulut tarafından dosya taraması için zaman uzantısı**: 50
   - **Örnek göndermeden önce kullanıcılara sor**: Tüm verileri sormadan gönderme

   :::image type="content" source="../../media/intune-block-at-first-sight.png" alt-text="İlk bakışta yapılandırma bloğunu Intune" lightbox="../../media/intune-block-at-first-sight.png":::

4. Ayarlarınızı kaydedin.

> [!TIP]
>
> - Dosya engelleme **düzeyinin Yüksek** olarak ayarlanması güçlü bir algılama düzeyi uygular. Dosya engellemenin meşru dosyaların hatalı pozitif algılanmasına neden olması olası olmayan bir durumda, güvenlik operasyonları ekibiniz [karantinaya alınan dosyaları geri yükleyebilir](./restore-quarantined-files-microsoft-defender-antivirus.md).
> - Intune'da Microsoft Defender Virüsten Koruma cihaz kısıtlamalarını yapılandırma hakkında daha fazla bilgi için bkz[. Microsoft Intune'de cihaz kısıtlama ayarlarını yapılandırma](/intune/device-restrictions-configure).
> - Intune'daki Microsoft Defender Virüsten Koruma cihaz kısıtlamalarının listesi için bkz. [Intune'de Windows 10 (ve daha yeni) ayarlar için cihaz kısıtlaması](/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

## <a name="turn-on-block-at-first-sight-with-microsoft-endpoint-manager"></a>Microsoft Endpoint Manager ile ilk bakışta bloğu açma

> [!TIP]
> Microsoft Endpoint Configuration Manager arıyorsanız, artık Microsoft Endpoint Manager bir parçasıdır.

1. Microsoft Endpoint Manager()<https://endpoint.microsoft.com> içinde **Endpoint security** \> **Virüsten Koruma'ya** gidin.

2. Mevcut bir ilkeyi seçin veya **Microsoft Defender Virüsten Koruma** profil türünü kullanarak yeni bir ilke oluşturun.

3. Aşağıdaki yapılandırma ayarlarını yapın veya onaylayın:

   - **Bulut tabanlı korumayı açma**: Evet
   - **Bulut tabanlı koruma düzeyi**: Yüksek
   - **saniyeler içinde genişletilmiş zaman aşımı Microsoft Defender Virüsten Koruma**: 50

   :::image type="content" source="images/endpointmgr-antivirus-cloudprotection.png" alt-text="Microsoft Endpoint Manager portalında ilk görüş ayarlarında engelle" lightbox="images/endpointmgr-antivirus-cloudprotection.png":::

4. Microsoft Defender Virüsten Koruma profilini **Tüm kullanıcılar**, **Tüm cihazlar** veya **Tüm kullanıcılar ve cihazlar** gibi bir gruba uygulayın.

## <a name="turn-on-block-at-first-sight-with-group-policy"></a>grup ilkesi ile ilk bakışta bloğu açma

> [!NOTE]
> bloğu ilk bakışta açmak için Intune veya Microsoft Endpoint Manager kullanmanızı öneririz.

1. grup ilkesi yönetim bilgisayarınızda [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **Düzenle'yi** seçin.

2. **grup ilkesi Yönetim Düzenleyicisi'ni** kullanarak **Bilgisayar yapılandırması** \> **Yönetim şablonları** \> **Windows Bileşenler** \> **Microsoft Defender Virüsten Koruma** \> **MAPS'e** gidin.

3. MAPS bölümünde **, 'İlk Bakışta Engelle' özelliğini yapılandır'a** çift tıklayın ve **Etkin** olarak ayarlayın ve **ardından Tamam'ı** seçin.

    > [!IMPORTANT]
    > **Her zaman istem (0)** ayarı cihazın koruma durumunu düşürür. **Hiçbir zaman gönderme (2)** ayarı, ilk görüşte bloğun çalışmayacağı anlamına gelir.

4. MAPS bölümünde, **daha fazla analiz gerektiğinde Dosya örnekleri gönder'e** çift tıklayın ve **Etkin** olarak ayarlayın. Daha **fazla analiz gerektiğinde dosya örnekleri gönder'in** altında **Tüm örnekleri gönder'i** ve ardından **Tamam'ı** seçin.

5. grup ilkesi Nesnenizi genellikle yaptığınız gibi ağınız genelinde yeniden dağıtabilirsiniz.

## <a name="confirm-block-at-first-sight-is-enabled-on-individual-client-devices"></a>Tek tek istemci cihazlarında ilk bakışta bloğun etkinleştirildiğini onaylayın

Windows Güvenliği uygulamasını kullanarak ilk bakışta bloğun tek tek istemci cihazlarda etkinleştirildiğini onaylayabilirsiniz. **Bulut tabanlı koruma** ve **Otomatik örnek gönderimi** açık olduğu sürece ilk bakışta engelle özelliği otomatik olarak etkinleştirilir.

1. Windows Güvenliği uygulamasını açın.

2. **Virüs & tehdit koruması'nı** seçin ve ardından **Virüs & tehdit koruması ayarları'nın** altında **Ayarlar yönet'i** seçin.

   :::image type="content" source="../../media/wdav-protection-settings-wdsc.png" alt-text="Windows Güvenliği uygulamasında Virüs & tehdit koruması ayarları etiketi" lightbox="../../media/wdav-protection-settings-wdsc.png":::

3. **Bulut tabanlı korumanın** ve **Otomatik örnek gönderimi'nin** her ikisinin de açık olduğunu onaylayın.

> [!NOTE]
>
> - Önkoşul ayarları grup ilkesi kullanılarak yapılandırılır ve dağıtılırsa, bu bölümde açıklanan ayarlar gri görünür ve tek tek uç noktalarda kullanılamaz.
> - grup ilkesi Nesnesi aracılığıyla yapılan değişikliklerin, ayarın Windows Ayarlar güncelleştirilmeden önce tek tek uç noktalara dağıtılması gerekir.

## <a name="validate-block-at-first-sight-is-working"></a>İlk bakışta bloğun çalıştığını doğrulama

Özelliğin çalıştığını doğrulamak için [ilk bakışta engelle örnek dosyasını](https://demo.wd.microsoft.com/Page/BAFS) indirin. Dosyayı indirmek için Azure AD'de Güvenlik Yöneticisi veya Genel Yönetici rolü atanmış bir hesaba ihtiyacınız olacaktır.

Bulut özellikli korumanın çalıştığını doğrulamak için [Ağınızla bulut arasındaki bağlantıları doğrulama bölümünde yer alan](configure-network-connections-microsoft-defender-antivirus.md#validate-connections-between-your-network-and-the-cloud) yönergeleri izleyin.

> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

## <a name="turn-off-block-at-first-sight"></a>İlk görüşte bloğu kapat

> [!CAUTION]
> İlk bakışta bloğu kapatmak, cihazınızın veya ağınızın koruma durumunu düşürür.

Ön koşul ayarlarını ilk görüşte engelleme koruması kullanmadan korumak istiyorsanız ilk görüşte engellemeyi devre dışı bırakabilirsiniz. Bu özelliğin ağınızı nasıl etkilediğini görmek için ilk bakışta bloğu geçici olarak kapatabilirsiniz. Ancak, ilk görüş korumasında bloğun kalıcı olarak devre dışı bırakılması önerilmez.

### <a name="turn-off-block-at-first-sight-with-microsoft-endpoint-manager"></a>Microsoft Endpoint Manager ile ilk görüşte bloğu kapatma

1. Microsoft Endpoint Manager yönetim merkezine (<https://endpoint.microsoft.com>) gidin ve oturum açın.

2. **Endpoint security** \> **Virüsten Koruma'ya** gidin ve Microsoft Defender Virüsten Koruma ilkenizi seçin.

3. **Yönet'in** altında **Özellikler'i** seçin.

4. **Yapılandırma ayarları'nın** yanında **Düzenle'yi** seçin.

5. Aşağıdaki ayarlardan birini veya daha fazlasını değiştirin:

   - **Bulut tabanlı korumayı aç'ı** **Hayır** veya **Yapılandırılmadı olarak** ayarlayın.
   - **Bulut tabanlı koruma düzeyini** **Yapılandırılmadı olarak** ayarlayın.
   - **Saniyeler Microsoft Defender Virüsten Koruma Genişletilmiş Zaman Aşımı** onay kutusunu temizleyin.

6. Ayarlarınızı gözden geçirin ve kaydedin.

### <a name="turn-off-block-at-first-sight-with-group-policy"></a>grup ilkesi ile ilk görüşte bloğu kapatma

1. grup ilkesi yönetim bilgisayarınızda [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve düzenle'yi seçin.

2. **grup ilkesi Yönetim Düzenleyicisi'ni** kullanarak **Bilgisayar yapılandırması'na** gidin ve **Yönetim şablonları'nı** seçin.

3. **MAPS** **Microsoft Defender Virüsten Koruma Windows bileşenleri** \>  \> aracılığıyla ağacı genişletin.

4. **'İlk Bakışta Engelle' özelliğini yapılandır'a** çift tıklayın ve seçeneği **Devre Dışı** olarak ayarlayın.

    > [!NOTE]
    > İlk bakışta bloğun devre dışı bırakılması önkoşul grubu ilkelerini devre dışı bırakmaz veya değiştirmez.

## <a name="not-an-enterprise-admin-or-it-pro"></a>Kuruluş yöneticisi veya BT Pro değil misiniz?

Kuruluş yöneticisi veya BT Pro değilseniz ancak ilk bakışta engelleme hakkında sorularınız varsa, bu bölüm tam size göredir. İlk bakışta engelle, kötü amaçlı yazılımları saniyeler içinde algılayan ve engelleyen bir tehdit koruması özelliğidir. "İlk bakışta engelle" adlı belirli bir ayar olmasa da, cihazınızda belirli ayarlar yapılandırıldığında özellik etkinleştirilir.

### <a name="how-to-manage-block-at-first-sight-on-or-off-on-your-own-device"></a>Blokları ilk görüşte kendi cihazınızda veya kapalı olarak yönetme

Bir kuruluş tarafından yönetilmeyen kişisel bir cihazınız varsa, ilk görüşte engellemeyi nasıl açabileceğinizi veya kapatabileceğinizi merak ediyor olabilirsiniz. İlk bakışta bloğu yönetmek için Windows Güvenliği uygulamasını kullanabilirsiniz.

1. Windows 10 veya Windows 11 bilgisayarınızda Windows Güvenliği uygulamasını açın.

2. **Virüs ve tehdit koruması**’nı seçin.

3. **Virüs & tehdit koruması ayarları'nın** altında **Ayarları yönet'i** seçin.

4. Aşağıdaki adımlardan birini uygulayın:

   - İlk bakışta engellemeyi etkinleştirmek için hem **Bulut tabanlı korumanın** hem de **Otomatik örnek gönderimi'nin** her ikisinin de açık olduğundan emin olun.

   - Engellemeyi ilk bakışta devre dışı bırakmak için **Bulut tabanlı korumayı** veya **Otomatik örnek gönderimini** kapatın.

     > [!CAUTION]
     > İlk bakışta bloğu kapatmak, cihazınızın koruma düzeyini düşürür. İlk bakışta bloğun kalıcı olarak devre dışı bırakılması önerilmez.

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [macOS'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender Virüsten Koruma macOS Virüsten Koruma ilkesi ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android'de Uç Nokta için Defender özelliklerini yapılandırma](android-configure.md)
> - [iOS özelliklerinde Pertahanan Microsoft untuk Titik Akhir yapılandırma](ios-configure-features.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Windows 10'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
- [Bulut tabanlı korumayı etkinleştirme](enable-cloud-protection-microsoft-defender-antivirus.md)
- [Windows Güvenliği ile korunmaya devam edin](https://support.microsoft.com/windows/stay-protected-with-windows-security-2ae0363d-0ada-c064-8b56-6a39afb6a963)
