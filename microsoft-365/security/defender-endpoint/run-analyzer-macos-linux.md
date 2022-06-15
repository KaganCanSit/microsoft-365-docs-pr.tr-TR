---
title: İstemci çözümleyicisini macOS veya Linux'ta çalıştırın
description: macOS veya Linux'ta Uç Nokta için Microsoft Defender İstemci Çözümleyicisi'ni çalıştırmayı öğrenin
keywords: istemci çözümleyicisi, sorun giderme algılayıcısı, çözümleyici, mdeanalyzer, macos, linux, mdeanalyzer
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
ms.openlocfilehash: a4dd7193bed1a22e3b88e6bc9201f5a15ddcd9eb
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66090464"
---
# <a name="run-the-client-analyzer-on-macos-and-linux"></a>İstemci çözümleyicisini macOS ve Linux'ta çalıştırma


**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="running-the-analyzer-through-gui-scenario"></a>GUI senaryosu aracılığıyla çözümleyiciyi çalıştırma

1. [XMDE İstemci Çözümleyicisi](https://aka.ms/XMDEClientAnalyzer) aracını araştırmanız gereken macOS veya Linux makinesine indirin.

   > [!NOTE]
   > Yukarıdaki bağlantıdan indirilen geçerli 'XMDEClientAnalyzer.zip' SHA256 karması: 'AFD674A149F139E80F1AE90E36814DAAC08AAD9E8B0DA20CB1D3FA33B9D0D1AD'.

2. Makinedeki XMDEClientAnalyzer.zip içeriğini ayıklayın.

3. Bir terminal oturumu açın, dizini ayıklanan konuma değiştirin ve çalıştırın:

   `./mde_support_tool.sh -d`

   > [!NOTE]
   > Linux'ta betiğin yürütme izinleri yoksa önce şunu çalıştırmanız gerekir:
   >
   > `chmod a+x mde_support_tool.sh`

## <a name="running-the-analyzer-using-a-terminal-or-ssh-scenario"></a>Terminal veya SSH senaryosu kullanarak çözümleyiciyi çalıştırma

İlgili makinede bir terminal veya SSH açın ve aşağıdaki komutları çalıştırın:

1. `wget --quiet -O XMDEClientAnalyzer.zip https://aka.ms/XMDEClientAnalyzer`

2. `unzip -q XMDEClientAnalyzer.zip`

3. `cd XMDEClientAnalyzer`

4. `chmod +x mde_support_tool.sh`

3. Gerekli pip ve lxml bileşenlerini yüklemek için kök olmayan kullanım olarak çalıştırın: `./mde_support_tool.sh`

4. Gerçek tanılama paketini toplamak ve sonuç arşiv dosyasını oluşturmak için kök olarak yeniden çalıştırın: `./mde_support_tool.sh -d`

> [!NOTE]
> - Linux için çözümleyicinin sonuç çıktısını oluşturması için 'lxml' gerekir. Yüklü değilse çözümleyici aşağıdaki Python paketleri için resmi depodan getirmeye çalışır: <https://pypi.org/search/?q=lxml>
> 
> - Ayrıca aracın şu anda Python sürüm 3 veya üzerinin yüklü olması gerekir.
>
> - Python 3 kullanamayan veya lxml bileşenini getiremeyen bir makinede çalışıyorsanız, çözümleyicinin gereksinimlerinden herhangi birine sahip olmayan ikili tabanlı bir sürümünü indirebilirsiniz: [XMDE İstemci Çözümleyicisi İkili](https://aka.ms/XMDEClientAnalyzerBinary)
>
> - Cihazınız bir ara sunucunun arkasındaysa, proxy sunucusunu mde_support_tool.sh betiğine ortam değişkeni olarak geçirebilirsiniz. Örneğin: `https_proxy=https://myproxy.contoso.com:8080 ./mde_support_tool.sh"`

Örneğin:

:::image type="content" source="images/4ca188f6c457e335abe3c9ad3eddda26.png" alt-text="Komut satırı örneği" lightbox="images/4ca188f6c457e335abe3c9ad3eddda26.png":::

Ek söz dizimi yardımı:

**-h** \# Yardım<br>
\# Yardım iletisini göster

**Performans** \# Performans<br>
\# İsteğe bağlı olarak yeniden oluşturulabilen bir performans sorununun analizi için kapsamlı izleme toplar. Karşılaştırmanın süresini belirtmek için kullanma `--length=<seconds>` .

**-o** \# Çıkış<br>
\# Sonuç dosyası için hedef yolu belirtme

**-nz** \# No-Zip<br>
\# Ayarlanırsa, sonuçta elde edilen arşiv dosyası yerine bir dizin oluşturulur

**-f** \# Kuvvet<br>
\# Çıkış hedef yolda zaten varsa üzerine yaz

## <a name="result-package-contents-on-macos-and-linux"></a>macOS ve Linux'ta sonuç paketi içeriği

- report.html

  Açıklama: Çözümleyici betiğinin makinede çalıştırabileceği bulguları ve yönergeleri içeren ana HTML çıkış dosyası.

- mde_diagnostic.zip

  Açıklama: her [iki macOS](/windows/security/threat-protection/microsoft-defender-atp/mac-resources#collecting-diagnostic-information) *mdatp tanılama oluşturma* çalıştırılırken oluşturulan tanılama çıktısı aynı

  veya

  [Linux](/windows/security/threat-protection/microsoft-defender-atp/linux-resources#collect-diagnostic-information)

- mde.xml

  Açıklama: Çalıştırılırken oluşturulan ve html rapor dosyasını derlemek için kullanılan XML çıkışı.

- Processes_information.txt

  Açıklama: Sistemdeki çalışan Uç Nokta için Microsoft Defender ilgili işlemlerin ayrıntılarını içerir.

- Log.txt

  Açıklama: Veri toplama sırasında ekrana yazılan günlük iletilerinin aynısını içerir.

- Health.txt

  Açıklama: *mdatp* health komutu çalıştırılırken gösterilen temel sistem durumu çıktısının aynısı.

- Events.xml

  Açıklama: ÇÖZÜMleyici tarafından HTML raporu oluştururken kullanılan ek XML dosyası.

- Audited_info.txt

  Açıklama: [Linux](/microsoft-365/security/defender-endpoint/linux-resources) işletim sistemi için denetlenen hizmet ve ilgili bileşenlerle ilgili ayrıntılar

- perf_benchmark.tar.gz

  Açıklama: Performans testi raporları. Bunu yalnızca performans parametresini kullanıyorsanız görürsünüz.
