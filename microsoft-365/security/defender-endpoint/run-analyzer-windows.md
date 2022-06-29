---
title: İstemci çözümleyicisini Windows’da çalıştırın
description: Windows'da Uç Nokta için Microsoft Defender İstemci Çözümleyicisi'ni çalıştırmayı öğrenin.
keywords: istemci çözümleyicisi, sorun giderme algılayıcısı, çözümleyici, mdeanalyzer, windows
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 51eaa6ddcaf50a48ccbd8ffc000a79049c1d9842
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66489480"
---
# <a name="run-the-client-analyzer-on-windows"></a>İstemci çözümleyicisini Windows’da çalıştırın

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

1. [MDE İstemci Çözümleyicisi aracını](https://aka.ms/mdatpanalyzer) araştırmanız gereken Windows makinesine indirin.

2. Makinedeki MDEClientAnalyzer.zip içeriğini ayıklayın.

3. Yükseltilmiş bir komut satırı açın:
    1. **Başlangıç'a** gidin ve **cmd** yazın.
    2. **Komut istemi'ne** sağ tıklayın ve **Yönetici olarak çalıştır'ı** seçin.

4. Aşağıdaki komutu girin ve **Enter tuşuna** basın:

   ```dos
   HardDrivePath\MDEClientAnalyzer.cmd
   ```

   **HardDrivePath'i aracın ayıklandığı yolla değiştirin, örneğin:**

   ```dos
   C:\Work\tools\MDEClientAnalyzer\MDEClientAnalyzer.cmd
   ```

Yukarıdakilere ek olarak, [canlı yanıt kullanarak çözümleyici destek günlüklerini toplama](troubleshoot-collect-support-log.md) seçeneği de vardır..

> [!NOTE]
> modern [birleştirilmiş çözümün](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution) yüklü olduğu Windows 10/11, Windows Server 2019/2022 veya Windows Server 2012R2/2016'da istemci çözümleyicisi betiği, bulut hizmeti URL'lerine bağlantı testlerini çalıştırmak için adlı `MDEClientAnalyzer.exe` yürütülebilir bir dosyayı çağırır.
>
> Windows 8.1, Windows Server 2016 veya ekleme için Microsoft Monitoring Agent'ın (MMA) kullanıldığı herhangi bir işletim sistemi sürümünde istemci çözümleyicisi betiği, Komut ve Denetim (CnC) URL'leri için bağlantı testleri çalıştırmak üzere adlı `MDEClientAnalyzerPreviousVersion.exe` yürütülebilir bir dosyaya çağrı yaparken, Siber Veri kanalı URL'leri için Microsoft Monitoring Agent bağlantı aracına `TestCloudConnection.exe` da çağrıda bulunur.


Çözümleyiciye dahil edilen tüm PowerShell betikleri ve modülleri Microsoft tarafından imzalandı.
Dosyalar herhangi bir şekilde değiştirilmişse çözümleyicinin aşağıdaki hatayla çıkması beklenir:

:::image type="content" source="images/sigerror.png" alt-text="İstemci çözümleyici hatası" lightbox="images/sigerror.png":::


Bu hata gösteriliyorsa, issuerInfo.txt çıkışında bunun neden olduğu ve hangi dosyanın etkilendiği hakkında ayrıntılı bilgiler yer alır:

:::image type="content" source="images/issuerinfo.png" alt-text="Veren bilgileri" lightbox="images/issuerinfo.png":::


MDEClientAnalyzer.ps1 değiştirildikten sonra örnek içerik:

:::image type="content" source="images/modified-ps1.png" alt-text="Değiştirilen ps1 dosyası" lightbox="images/modified-ps1.png":::



## <a name="result-package-contents-on-windows"></a>Windows'ta sonuç paketi içeriği

> [!NOTE]
> Yakalanan dosyaların tam olarak değişmesi, aşağıdakiler gibi faktörlere bağlı olarak değişebilir:
>
> - Çözümleyicinin çalıştırıldığı pencerelerin sürümü.
> - Makinede olay günlüğü kanalı kullanılabilirliği.
> - EDR algılayıcısının başlangıç durumu (Makine henüz eklenmemişse Akıllı durdurulur).
> - Çözümleyici komutuyla gelişmiş bir sorun giderme parametresi kullanıldıysa.

Paketlenmemiş MDEClientAnalyzerResult.zip dosyası varsayılan olarak aşağıdaki öğeleri içerir.

- MDEClientAnalyzer.htm

  Bu, çözümleyici betiğinin makinede çalıştırabileceği bulguları ve yönergeleri içeren ana HTML çıkış dosyasıdır.

- SystemInfoLogs \[Klasörü\]
  - AddRemovePrograms.csv

    Açıklama: Kayıt defterinden toplanan x64 işletim sistemindeki x64 yüklü yazılımların listesi.

  - AddRemoveProgramsWOW64.csv

    Açıklama: Kayıt defterinden toplanan x64 işletim sistemindeki x86 yüklü yazılımların listesi.

    - CertValidate.log

      Açıklama: [CertUtil'e](/windows-server/administration/windows-commands/certutil) çağrılarak yürütülen sertifika iptalinden ayrıntılı sonuç.

    - dsregcmd.txt

      Açıklama: [dsregcmd](/azure/active-directory/devices/troubleshoot-device-dsregcmd) çalıştırılan çıktı. Bu, makinenin Azure AD durumu hakkında ayrıntılar sağlar.

    - IFEO.txt

      Açıklama: Makinede yapılandırılan [Görüntü Dosyası Yürütme Seçeneklerinin](/previous-versions/windows/desktop/xperf/image-file-execution-options) çıkışı

    - MDEClientAnalyzer.txt

      Açıklama: Bu, çözümleyici betiği yürütme ayrıntılarıyla birlikte gösterilen ayrıntılı metin dosyasıdır.

    - MDEClientAnalyzer.xml

      Açıklama: Çözümleyici betik bulgularını içeren XML biçimi.

    - RegOnboardedInfoCurrent.Json

      Açıklama: Kayıt defterinden JSON biçiminde toplanan eklenen makine bilgileri.

  - RegOnboardingInfoPolicy.Json

    Açıklama: Kayıt defterinden JSON biçiminde toplanan ekleme ilkesi yapılandırması.

    - SCHANNEL.txt

      Açıklama: Kayıt defterinden toplanan makineye uygulanan [SCHANNEL yapılandırmasıyla](/windows-server/security/tls/manage-tls) ilgili ayrıntılar.

    - SessionManager.txt

      Açıklama: Oturum Yöneticisi'ne özgü ayarlar kayıt defterinden toplanır.

    - SSL_00010002.txt

      Açıklama: Kayıt defterinden toplanan makineye uygulanan [SSL yapılandırmasıyla](/windows-server/security/tls/manage-tls) ilgili ayrıntılar.

- EventLogs [Klasör]

  - utc.evtx

    Açıklama: DiagTrack olay günlüğünü dışarı aktarma

  - senseIR.evtx

    Açıklama: Otomatik Araştırma olay günlüğünü dışarı aktarma

  - sense.evtx

    Açıklama: Algılayıcı ana olay günlüğünü dışarı aktarma

  - OperationsManager.evtx

    Açıklama: Microsoft Monitoring Agent olay günlüğünü dışarı aktarma




## <a name="see-also"></a>Ayrıca bkz.

- [İstemci çözümleyicisine genel bakış](overview-client-analyzer.md)
- [İstemci çözümleyicisini indirin ve çalıştırın](download-client-analyzer.md)
- [Windows'da gelişmiş sorun giderme için veri toplama](data-collection-analyzer.md)
- [Çözümleyici HTML raporunu inceleyin](analyzer-report.md)
