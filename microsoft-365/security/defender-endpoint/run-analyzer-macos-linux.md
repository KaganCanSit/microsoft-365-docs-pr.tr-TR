---
title: macOS veya Linux'ta istemci çözümleyicisini çalıştırın
description: macOS veya Linux'ta Uç Nokta İstemcisi Çözümleyicisi için Microsoft Defender'ı çalıştırmayı öğrenin
keywords: istemci çözümleyicisi, algılayıcı, çözümleyici, mdeanalyzer, macos, linux, mdeanalyzer sorunlarını giderme
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
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: f6767b1a788129266bff713a6608277a2450598c
ms.sourcegitcommit: 9c8eca862a2f0fdca7a66c641e382e37fcaefa10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2022
ms.locfileid: "63775906"
---
# <a name="run-the-client-analyzer-on-macos-and-linux"></a>macOS ve Linux'ta istemci çözümleyicisini çalıştırın


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="running-the-analyzer-through-gui-scenario"></a>Çözümleyiciyi GUI senaryosu aracılığıyla çalıştırma

1. [Araştırmaniz gereken macOS veya](https://aka.ms/XMDEClientAnalyzer) Linux makinesine XMDE İstemci Çözümleyicisi aracını indirin.

   > [!NOTE]
   > Yukarıdaki bağlantıdan indirilen geçerli SHA256 karması 'XMDEClientAnalyzer.zip' karması: 'A9BF065DE3F2608A309BC4F5295548BB9931F107BF2F01DC42A789C5527C1308'.

2. Makinede XMDEClientAnalyzer.zip içeriğini ayıkla.

3. Bir terminal oturumu açın, dizini ayıklanan konuma seçin ve çalıştırın:

   `./mde_support_tool.sh -d`

   > [!NOTE]
   > Linux'ta, betiğin yürütme izinleri yoksa önce çalıştırmanız gerekir:
   >
   > `chmod a+x mde_support_tool.sh`

## <a name="running-the-analyzer-using-a-terminal-or-ssh-scenario"></a>Çözümleyiciyi terminal veya SSH senaryosu kullanarak çalıştırma

İlgili makinede bir terminal veya SSH açın ve aşağıdaki komutları çalıştırın:

1. `wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer`

2. `unzip -q XMDEClientAnalyzer.zip`

3. `cd XMDEClientAnalyzer`

4. `chmod +x mde_support_tool.sh`

3. Gerekli pip ve lxml'i yüklemek için kök olmayan kullanım olarak çalıştırın; hangi bileşenler: `./mde_support_tool.sh`

4. Gerçek tanılama paketini toplamak ve sonuç arşiv dosyasını oluşturmak için yeniden kök olarak çalıştırın: `./mde_support_tool.sh -d`

> [!NOTE]
> - Linux için, çözümleyici sonuç çıktısını oluşturmak için 'lxml' gerektirir. Yüklü değilse, çözümleyici aşağıdaki python paketleri için resmi depodan getirmeyi dener: <https://files.pythonhosted.org/packages/\*/lxml\*.whl>
> 
> - Buna ek olarak, araç şu anda Python sürüm 3 veya daha sonraki bir sürümünün de yüklü olması gerekir.
>
> - Python 3'ü kullana almayan veya lxml bileşenini getiren bir makinede çalışıyorsanız, hiçbir gereklilik belirt almayan çözümleyicinin ikili tabanlı sürümünü indirebilirsiniz: [XMDE İstemci](https://aka.ms/XMDEClientAnalyzerBinary) Çözümleyicisi İkilisi
>
> - Cihazınız bir proxy arkasında ise, proxy sunucusunu mde_support_tool.sh betiğine ortam değişkeni olarak kolayca geçebilirsiniz. Örneğin: `https_proxy=https://myproxy.contoso.com:8080 ./mde_support_tool.sh"`

Örneğin:

![Komut satırı örneği görüntüsü.](images/4ca188f6c457e335abe3c9ad3eddda26.png)

Ek söz dizimi yardımı:

**-h** \# Yardım<br>
\# Yardım iletisi göster

**performans** \# Performans<br>
\# Bir performans sorunu üzerinde isteğe bağlı olarak yeniden üretilebilir çözümlemesi için kapsamlı izleme toplar. Karşılaştırma `--length=<seconds>` süresini belirtmek için kullanma.

**-o** \# Çıktı<br>
\# Sonuç dosyasının hedef yolunu belirtme

**-nz** \# No-Zip<br>
\# Ayarlanırsa, sonuçta elde edilen bir arşiv dosyası yerine bir dizin oluşturulur

**-f** \# Kuvvet<br>
\# Çıktı hedef yolda zaten varsa üzerine yaz

## <a name="result-package-contents-on-macos-and-linux"></a>macOS ve Linux'ta sonuç paketi içeriği

- report.html

  Açıklama: Çözümleyici betiği tarafından makinede çalıştırılarak  çalıştırınan bulguları ve kılavuzu içeren ana HTML çıkış dosyası.

- mde_diagnostic.zip

  Açıklama: Her iki macOS'ta da *mdatp tanılama aracı oluşturulurken oluşturulan* aynı [tanılama çıktısı](/windows/security/threat-protection/microsoft-defender-atp/mac-resources#collecting-diagnostic-information)

  veya

  [Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-resources#collect-diagnostic-information)

- mde.xml

  Açıklama: Çalışırken oluşturulan VE HTML rapor dosyasını oluşturmak için kullanılan XML çıktısı.

- Processes_information.txt

  Açıklama: Sistemde uç nokta ile ilgili işlemler için çalışan Microsoft Defender'ın ayrıntılarını içerir.

- Log.txt

  Açıklama: Veri toplama sırasında ekranda yazılan günlük iletilerinin aynısını içerir.

- Health.txt

  Açıklama: Mdatp health komutu çalıştırlarda gösterilen *aynı temel durum çıktısı* .

- Events.xml

  Açıklama: HTML raporu oluşturmak için çözümleyici tarafından kullanılan ek XML dosyası.

- Auditd_info.txt

  Açıklama: Denetlenen hizmet ve Linux işletim sistemiyle ilgili bileşenler [hakkında](/windows/security/threat-protection/microsoft-defender-atp/linux-support-events) ayrıntılar

- perf_benchmark.tar.gz

  Açıklama: Performans testi raporları. Bunu yalnızca performans parametresini kullanıyorsanız görebilirsiniz.
