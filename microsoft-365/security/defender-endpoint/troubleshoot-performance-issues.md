---
title: Performans sorunlarını giderin
description: Uç Nokta için Microsoft Defender'daki gerçek zamanlı koruma hizmetiyle ilgili yüksek CPU kullanımı sorunlarını giderme.
keywords: sorun giderme, performans, yüksek CPU kullanımı, yüksek CPU kullanımı, hata, düzeltme, güncelleştirme uyumluluğu, oms, izleme, rapor, Microsoft Defender Virüsten Koruma
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
ms.date: 10/19/2021
audience: ITPro
ms.topic: troubleshooting
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 01db84f3ddd4eae79cae2fa97400f4d3d78ba8da
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419758"
---
# <a name="troubleshoot-performance-issues-related-to-real-time-protection"></a>Gerçek zamanlı korumayla ilgili performans sorunlarını giderin


[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Sisteminizde Uç Nokta için Microsoft Defender'da gerçek zamanlı koruma hizmetiyle ilgili yüksek CPU kullanımı veya performans sorunları varsa Microsoft desteğine bir bilet gönderebilirsiniz. [tanılama verilerini Microsoft Defender Virüsten Koruma toplama](collect-diagnostic-data.md) başlığındaki adımları izleyin.

Yönetici olarak, bu sorunları kendi başınıza da giderebilirsiniz.

İlk olarak, sorunun başka bir yazılımdan kaynaklenip kaynaklanmadığını denetlemek isteyebilirsiniz. [Virüsten koruma dışlamaları için satıcıya danışın](#check-with-vendor-for-antivirus-exclusions).

Aksi takdirde, [Microsoft Koruma Günlüğünü Analiz](#analyze-the-microsoft-protection-log) Etme'deki adımları izleyerek tanımlanan performans sorunuyla hangi yazılımın ilişkili olduğunu belirleyebilirsiniz.

Ayrıca, aşağıdaki adımları izleyerek Microsoft desteğine gönderiminize ek günlükler de sağlayabilirsiniz:

- [İşlem İzleyicisi'yi kullanarak işlem günlüklerini yakalama](#capture-process-logs-using-process-monitor)
- [Windows Performans Kaydedicisi'yi kullanarak performans günlüklerini yakalama](#capture-performance-logs-using-windows-performance-recorder)

## <a name="check-with-vendor-for-antivirus-exclusions"></a>Virüsten koruma dışlamaları için satıcıya başvurun

Sistem performansını etkileyen yazılımı kolayca belirleyebiliyorsanız yazılım satıcısının bilgi bankası veya destek merkezine gidin. Virüsten koruma dışlamalarıyla ilgili önerileri olup olmadığını arayın. Satıcının web sitesinde yoksa, onlarla birlikte bir destek bileti açabilir ve onlardan bir destek bileti yayımlamasını isteyebilirsiniz.

Yazılım satıcılarının [hatalı pozitif sonuçları en aza indirmek için sektörle iş ortaklığındaki çeşitli yönergeleri izlemelerini](https://www.microsoft.com/security/blog/2018/08/16/partnering-with-the-industry-to-minimize-false-positives/) öneririz. Satıcı, [yazılımlarını Microsoft Güvenlik Zekası portalı](https://www.microsoft.com/wdsi/filesubmission?persona=SoftwareDeveloper) üzerinden gönderebilir.

## <a name="analyze-the-microsoft-protection-log"></a>Microsoft Koruma Günlüğünü Analiz Etme

**MPLog-xxxxxxxx-xxxxxx.log** dosyasında, yazılımı *EstimatedImpact* olarak çalıştırmanın tahmini performans etkisi bilgilerini bulabilirsiniz:

`Per-process counts:ProcessImageName: smsswd.exe, TotalTime: 6597, Count: 1406, MaxTime: 609, MaxTimeFile: \Device\HarddiskVolume3\_SMSTaskSequence\Packages\WQ1008E9\Files\FramePkg.exe, EstimatedImpact: 65%`

<br>

****

|Alan adı|Açıklama|
|---|---|
|ProcessImageName|İşlem görüntüsü adı|
|TotalTime|Bu işlem tarafından erişilen dosyaların taranmalarında harcanan milisaniye cinsinden kümülatif süre|
|Sayısı|Bu işlem tarafından erişilen taranan dosyaların sayısı|
|MaxTime|Bu işlem tarafından erişilen bir dosyanın en uzun tek taramasında milisaniye cinsinden süre|
|MaxTimeFile|Sürenin en uzun taramasının `MaxTime` kaydedildiği bu işlem tarafından erişilen dosyanın yolu|
|EstimatedImpact|Bu işlemin tarama etkinliği yaşadığı sürenin dışında bu işlem tarafından erişilen dosyalar için taramalarda harcanan zaman yüzdesi|
|

Performans etkisi yüksekse, Microsoft Defender Virüsten Koruma [taramaları için dışlamaları yapılandırma ve doğrulama](collect-diagnostic-data.md) makalesindeki adımları izleyerek işlemi Yol/İşlem dışlamalarına eklemeyi deneyin.

Önceki adım sorunu çözmezse, aşağıdaki bölümlerde [İşlem İzleyicisi](#capture-process-logs-using-process-monitor) veya [Windows Performans Kaydedicisi](#capture-performance-logs-using-windows-performance-recorder) aracılığıyla daha fazla bilgi toplayabilirsiniz.

## <a name="capture-process-logs-using-process-monitor"></a>İşlem İzleyicisi'yi kullanarak işlem günlüklerini yakalama

İşlem İzleyicisi (ProcMon), gerçek zamanlı işlemleri gösterebilen gelişmiş bir izleme aracıdır. Performans sorununu oluşurken yakalamak için bunu kullanabilirsiniz.

1. [İşlem İzleyicisi v3.60'ı](/sysinternals/downloads/procmon) gibi `C:\temp`bir klasöre indirin.

2. Dosyanın web işaretini kaldırmak için:
    1. **ProcessMonitor.zip** sağ tıklayın ve **Özellikler'i** seçin.
    1. *Genel* sekmesinin altında *Güvenlik'i* arayın.
    1. **Engellemeyi Kaldır'ın** yanındaki kutuyu işaretleyin.
    1. **Uygula'yı** seçin.

    :::image type="content" source="images/procmon-motw.png" alt-text="MOTW'yi Kaldır sayfası" lightbox="images/procmon-motw.png":::

3. Klasör yolunun olması `C:\temp\ProcessMonitor`için dosyasının `C:\temp` sıkıştırmasını açın.

4. **ProcMon.exe** sorun giderdiğiniz Windows istemcisine veya Windows sunucusuna kopyalayın.

5. ProcMon'ı çalıştırmadan önce, yüksek CPU kullanımı sorunuyla ilgili olmayan diğer tüm uygulamaların kapatıldığından emin olun. Bunu yaptığınızda denetlenecek işlem sayısı en aza indirgenecektir.

6. ProcMon'ı iki şekilde başlatabilirsiniz.
    1. **ProcMon.exe** sağ tıklayın ve **Yönetici olarak çalıştır'ı** seçin.

        Günlük otomatik olarak başladığından, geçerli yakalamayı durdurmak için büyüteç simgesini seçin veya **Ctrl+E** klavye kısayolunu kullanın.

        :::image type="content" source="images/procmon-magglass.png" alt-text="Büyüteç simgesi" lightbox="images/procmon-magglass.png":::

        Yakalamayı durdurduğunuz doğrulamak için büyüteç simgesinin artık kırmızı X ile görünüp görünmediğini denetleyin.

        :::image type="content" source="images/procmon-magglass-stop.png" alt-text="Kırmızı eğik çizgi" lightbox="images/procmon-magglass-stop.png":::

        Ardından, önceki yakalamayı temizlemek için silgi simgesini seçin.

        :::image type="content" source="images/procmon-eraser-clear.png" alt-text="Temizle simgesi" lightbox="images/procmon-eraser-clear.png":::

        Alternatif olarak **Ctrl+X** klavye kısayolunu da kullanabilirsiniz.

    2. İkinci yol, **komut satırını** yönetici olarak çalıştırmak ve ardından İşlem İzleyicisi yolundan çalıştırmaktır:

       :::image type="content" source="images/cmd-procmon.png" alt-text="Cmd procmon" lightbox="images/cmd-procmon.png":::

        ```console
        Procmon.exe /AcceptEula /Noconnect /Profiling
        ```

        > [!TIP]
        > İzlemeyi kolayca başlatıp durdurabilmeniz için verileri yakalarken ProcMon penceresini mümkün olduğunca küçük hale getirin.
        >
        > :::image type="content" source="images/procmon-minimize.png" alt-text="Simge durumuna küçült Procmon'un görüntülendiği sayfa" lightbox="images/procmon-minimize.png":::

7. 6. adımdaki yordamlardan birini takip ettikten sonra filtre ayarlama seçeneğini göreceksiniz. **Tamam**'ı seçin. Yakalama tamamlandıktan sonra sonuçları istediğiniz zaman filtreleyebilirsiniz.

   :::image type="content" source="images/procmon-filter-options.png" alt-text="Filtre Uygulama İşlem Adı olarak Sistem Dışlama'nın seçildiği sayfa" lightbox="images/procmon-filter-options.png":::

8. Yakalamayı başlatmak için büyüteç simgesini yeniden seçin.

9. Sorunu yeniden oluşturun.

    > [!TIP]
    > Sorunun tamamen yeniden üretilmesi için bekleyin, ardından izlemenin başladığı zaman damgasını not alın.

10. Yüksek CPU kullanım koşulu sırasında iki-dört dakikalık işlem etkinliğine sahip olduğunuzda büyüteç simgesini seçerek yakalamayı durdurun.

11. Yakalamayı benzersiz bir adla ve .pml biçiminde kaydetmek için **Dosya'yı** ve ardından **Kaydet...'i** seçin. **Tüm olaylar** ve **Yerel İşlem İzleyicisi Biçimi (PML)** radyo düğmelerini seçtiğinizden emin olun.

    :::image type="content" source="images/procmon-savesettings1.png" alt-text="Ayarları kaydet sayfası" lightbox="images/procmon-savesettings1.png":::

12. Daha iyi izleme için varsayılan yolu şu şekilde `C:\temp\ProcessMonitor\LogFile.PML` `C:\temp\ProcessMonitor\%ComputerName%_LogFile_MMDDYEAR_Repro_of_issue.PML` değiştirin:
    - `%ComputerName%` cihaz adıdır
    - `MMDDYEAR` ay, gün ve yıldır
    - `Repro_of_issue` yeniden oluşturmaya çalıştığınız sorunun adıdır

    > [!TIP]
    > Çalışma sisteminiz varsa karşılaştırmak için örnek bir günlük almak isteyebilirsiniz.

13. .pml dosyasını sıkıştırın ve Microsoft desteğine gönderin.

## <a name="capture-performance-logs-using-windows-performance-recorder"></a>Windows Performans Kaydedicisi'yi kullanarak performans günlüklerini yakalama

Microsoft desteğine göndermenize ek bilgiler eklemek için Windows Performans Kaydedicisi'ni (WPR) kullanabilirsiniz. WPR, Windows kayıtlar için Olay İzleme oluşturan güçlü bir kayıt aracıdır.

WPR, Windows Değerlendirme ve Dağıtım Seti'nin (Windows ADK) bir parçasıdır ve [Windows ADK'yi indirip yükleyebilir](/windows-hardware/get-started/adk-install). Ayrıca Windows 10 [SDK'da](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) Windows 10 Yazılım Geliştirme Seti'nin bir parçası olarak indirebilirsiniz.

WPR kullanıcı arabirimini, [WPR kullanıcı arabirimini kullanarak performans günlüklerini yakalama makalesindeki](#capture-performance-logs-using-the-wpr-ui) adımları izleyerek kullanabilirsiniz.

Alternatif olarak, [WPR CLI kullanarak performans günlüklerini yakalama](#capture-performance-logs-using-the-wpr-cli) başlığı ** altında verilen adımları izleyerek Windows 8 ve sonraki sürümlerde kullanılabilenwpr.exekomut satırı aracını da kullanabilirsiniz.

### <a name="capture-performance-logs-using-the-wpr-ui"></a>WPR kullanıcı arabirimini kullanarak performans günlüklerini yakalama

> [!TIP]
> Bu sorunla birden çok cihazda karşılaşılıyorsa, en çok RAM'e sahip olanı kullanın.

1. WPR'yi indirip yükleyin.

2. *Windows Setleri'nin* altında **Windows Performans Kaydedicisi'ne** sağ tıklayın.

   :::image type="content" source="images/wpr-01.png" alt-text="Başlat menüsü" lightbox="images/wpr-01.png":::

    **Diğer'i** seçin. **Yönetici olarak çalıştır'ı** seçin.

3. Kullanıcı Hesabı Denetimi iletişim kutusu görüntülendiğinde **Evet'i** seçin.

   :::image type="content" source="images/wpt-yes.png" alt-text="UAC sayfası" lightbox="images/wpt-yes.png":::

4. Ardından[, Uç Nokta için Microsoft Defender çözümleme](https://github.com/YongRhee-MDE/Scripts/blob/master/MDAV.wprp) profilini indirin ve gibi `C:\temp`bir klasöre kaydedin`MDAV.wprp`.

5. WPR iletişim kutusunda **Diğer seçenekler'i** seçin.

   :::image type="content" source="images/wpr-03.png" alt-text="Daha fazla seçenek belirleyebileceğiniz sayfa" lightbox="images/wpr-03.png":::


6. **Profil Ekle...** öğesini seçin ve dosyanın yoluna `MDAV.wprp` gidin.

7. Bundan sonra, *Özel ölçümler* altında altında *Uç Nokta için Microsoft Defender analizi* adlı yeni bir profil kümesi görmeniz gerekir.

   :::image type="content" source="images/wpr-infile.png" alt-text="Dosya içi" lightbox="images/wpr-infile.png":::

    > [!WARNING]
    > Windows Sunucunuzda 64 GB veya daha fazla RAM varsa yerine özel ölçümü `Microsoft Defender for Endpoint analysis for large servers` `Microsoft Defender for Endpoint analysis`kullanın. Aksi takdirde, sisteminiz yüksek miktarda disk belleği olmayan havuz belleği veya arabellek tüketebilir ve bu da sistem kararlılığının oluşmasına neden olabilir. **Kaynak Analizi'ni** genişleterek hangi profillerin ekleneceğini seçebilirsiniz.
    Bu özel profil, ayrıntılı performans analizi için gerekli bağlamı sağlar.

8. WPR kullanıcı arabiriminde özel ölçüm Uç Nokta için Microsoft Defender ayrıntılı analiz profilini kullanmak için:

    1. *İlk düzey önceliklendirme*, *Kaynak Analizi* ve *Senaryo Analizi* grupları altında hiçbir profilin seçilmediğinden emin olun.
    2. **Özel ölçümler'i** seçin.
    3. **analiz Uç Nokta için Microsoft Defender'ı** seçin.
    4. *Ayrıntı* düzeyi'nin altında **Ayrıntılı'ya** tıklayın.
    5. Günlük modu altında **Dosya** veya **Bellek'i** seçin.

    > [!IMPORTANT]
    > Performans sorunu doğrudan kullanıcı tarafından yeniden oluşturulabiliyorsa dosya günlüğü modunu kullanmak için *Dosya'ya* tıklayın. Sorunların çoğu bu kategoriye girer. Ancak, kullanıcı sorunu doğrudan yeniden oluşturamıyorsa ancak sorun oluştuğunda kolayca fark edebilirse, bellek günlüğü modunu kullanmak için *Bellek'i* seçmesi gerekir. Bu, izleme günlüğünün uzun çalışma süresi nedeniyle aşırı şişmemesini sağlar.

9. Artık veri toplamaya hazırsınız. Performans sorununun yeniden üretilmesiyle ilgili olmayan tüm uygulamalardan çıkın. WPR penceresinin kapladığı alanı küçük tutmak için **Seçenekleri gizle'yi** seçebilirsiniz.

   :::image type="content" source="images/wpr-08.png" alt-text="Gizle seçenekleri" lightbox="images/wpr-08.png":::

    > [!TIP]
    > İzlemeyi tam sayı saniye olarak başlatmayı deneyin. Örneğin, 01:30:00. Bu, verileri çözümlemeyi kolaylaştırır. Ayrıca sorunun tam olarak ne zaman yeniden üretildiğinde zaman damgasını izlemeye çalışın.

10. **Başlat**'ı seçin.

    :::image type="content" source="images/wpr-09.png" alt-text="Kayıt sistemi bilgileri sayfası" lightbox="images/wpr-09.png":::

11. Sorunu yeniden oluşturun.

    > [!TIP]
    > Veri toplamayı en fazla beş dakika tutun. Çok fazla veri toplandığı için iki ila üç dakika iyi bir aralıktır.

12. **Kaydet**'i seçin.

    :::image type="content" source="images/wpr-10.png" alt-text="Kaydet seçeneği" lightbox="images/wpr-10.png":::

13. **Sorunun ayrıntılı açıklamasını yazın: sorun** hakkında bilgi ve sorunu nasıl yeniden oluşturduğunuzu belirtin.

    :::image type="content" source="images/wpr-12.png" alt-text="Doldurduğunuz bölme" lightbox="images/wpr-12.png":::

    1. İzleme dosyanızın kaydedileceği yeri belirlemek için **Dosya Adı:** öğesini seçin. Varsayılan olarak, öğesine `%user%\Documents\WPR Files\`kaydedilir.
    1. **Kaydet**'i seçin.

14. İzleme birleştirilirken bekleyin.

    :::image type="content" source="images/wpr-13.png" alt-text="WPR genel izleme toplama" lightbox="images/wpr-13.png":::

15. İzleme kaydedildikten sonra **Klasörü aç'ı** seçin.

    :::image type="content" source="images/wpr-14.png" alt-text="WPR izlemesinin kaydedildiği bildirimini görüntüleyen sayfa" lightbox="images/wpr-14.png":::

    Hem dosyayı hem de klasörü Microsoft Desteği göndermenize ekleyin.

    :::image type="content" source="images/wpr-15.png" alt-text="Dosyanın ve klasörün ayrıntıları" lightbox="images/wpr-15.png":::

### <a name="capture-performance-logs-using-the-wpr-cli"></a>WPR CLI kullanarak performans günlüklerini yakalama

komut satırı aracı *wpr.exe*, Windows 8 ile başlayan işletim sisteminin bir parçasıdır. Komut satırı aracını kullanarak WPR izlemesini toplamak için wpr.exe:

1. gibi `C:\traces`bir yerel dizinde adlı `MDAV.wprp` dosyaya performans izlemeleri için **[Uç Nokta için Microsoft Defender analiz](https://github.com/YongRhee-MDE/Scripts/blob/master/MDAV.wprp)** profilini indirin.

2. **Başlat Menüsü** simgesine sağ tıklayın ve yönetici komut istemi penceresini açmak için **Windows PowerShell (Yönetici)** veya **Komut İstemi 'ni (Yönetici)** seçin.

3. Kullanıcı Hesabı Denetimi iletişim kutusu görüntülendiğinde **Evet'i** seçin.

4. Yükseltilmiş komut isteminde aşağıdaki komutu çalıştırarak Uç Nokta için Microsoft Defender performans izlemesini başlatın:

    ```console
    wpr.exe -start C:\traces\MDAV.wprp!WD.Verbose -filemode
    ```

    > [!WARNING]
    > Windows Sunucunuzda 64 GB veya RAM veya daha fazla ram varsa, sırasıyla ve yerine profilleri `WD.Light` `WD.Verbose`kullanın `WDForLargeServers.Light` `WDForLargeServers.Verbose`. Aksi takdirde, sisteminiz yüksek miktarda disk belleği olmayan havuz belleği veya arabellek tüketebilir ve bu da sistem kararlılığının oluşmasına neden olabilir.

5. Sorunu yeniden oluşturun.

    > [!TIP]
    > Veri toplamayı en fazla beş dakika tutun. Senaryoya bağlı olarak, çok fazla veri toplandığı için iki ila üç dakika iyi bir aralıktır.

6. Yükseltilmiş istemde aşağıdaki komutu çalıştırarak performans izlemesini durdurun ve sorun ve sorunu nasıl yeniden oluşturduğunuz hakkında bilgi sağladığından emin olun:

    ```console
    wpr.exe -stop merged.etl "Timestamp when the issue was reproduced, in HH:MM:SS format" "Description of the issue" "Any error that popped up"
    ```

7. İzleme birleştirilene kadar bekleyin.

8. Hem dosyayı hem de klasörü Microsoft desteğine gönderin.

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Defender Virüsten Koruma tanılama verilerini toplama](collect-diagnostic-data.md)
- [Microsoft Defender Virüsten Koruma taramaları için dışlamaları yapılandırma ve doğrulama](configure-exclusions-microsoft-defender-antivirus.md)
