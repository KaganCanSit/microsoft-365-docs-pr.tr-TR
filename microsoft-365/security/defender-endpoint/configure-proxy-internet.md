---
title: Cihaz ara sunucusu ve İnternet bağlantısı ayarlarını yapılandırma
description: Bulut hizmetiyle iletişimi etkinleştirmek için Uç Nokta için Microsoft Defender proxy ve internet ayarlarını yapılandırın.
keywords: yapılandırma, proxy, internet, internet bağlantısı, ayarlar, proxy ayarları, netsh, winhttp, proxy sunucusu
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 787da143bdbbc2d21610ba14d0fe7c955e4e976d
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64823410"
---
# <a name="configure-device-proxy-and-internet-connectivity-settings"></a>Cihaz ara sunucusu ve İnternet bağlantısı ayarlarını yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimlemek mi istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

Uç Nokta için Defender algılayıcısı, algılayıcı verilerini raporlamak ve Uç Nokta için Defender hizmetiyle iletişim kurmak için Microsoft Windows HTTP (WinHTTP) gerektirir. Ekli Uç Nokta için Defender algılayıcısı LocalSystem hesabını kullanarak sistem bağlamında çalışır. Algılayıcı, Uç Nokta için Defender bulut hizmetiyle iletişimi etkinleştirmek için Microsoft Windows HTTP Hizmetleri'ni (WinHTTP) kullanır.

> [!TIP]
> İleri proxy'leri İnternet'e ağ geçidi olarak kullanan kuruluşlarda, [ileriye doğru ara sunucuların arkasında gerçekleşen bağlantı olaylarını araştırmak](investigate-behind-proxy.md) için ağ korumasını kullanabilirsiniz.

WinHTTP yapılandırma ayarı, Windows İnternet (WinINet) gözatma proxy ayarlarından bağımsızdır (bkz[. WinINet ve WinHTTP](/windows/win32/wininet/wininet-vs-winhttp)). Bir proxy sunucusunu yalnızca aşağıdaki bulma yöntemlerini kullanarak bulabilir:

- Otomatik bulma yöntemleri:

  - Saydam ara sunucu
  
  - Web Proxy Otomatik Bulma Protokolü (WPAD)

    > [!NOTE]
    > Ağ topolojinizde Saydam proxy veya WPAD kullanıyorsanız özel yapılandırma ayarlarına ihtiyacınız yoktur. Ara sunucudaki Uç Nokta için Defender URL dışlamaları hakkında daha fazla bilgi için bkz. [Ara sunucudaki Uç Nokta için Defender hizmeti URL'lerine erişimi etkinleştirme](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)

- El ile statik proxy yapılandırması:

  - Kayıt defteri tabanlı yapılandırma
  
  - Netsh komutu kullanılarak yapılandırılan WinHTTP: Yalnızca kararlı bir topolojideki masaüstleri için uygundur (örneğin: aynı proxy'nin arkasındaki şirket ağında bir masaüstü)

> [!NOTE]
> Defender virüsten koruma ve EDR proxy'leri bağımsız olarak ayarlanabilir.  İzleyen bölümlerde bu ayrımlara dikkat edin.

## <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>Ara sunucuyu kayıt defteri tabanlı statik proxy kullanarak el ile yapılandırma

Bir bilgisayarın İnternet'e bağlanmasına izin verilmiyorsa tanılama verilerini raporlamak ve Uç Nokta için Defender hizmetleriyle iletişim kurmak üzere Uç Nokta için Defender algılama ve yanıt (EDR) algılayıcısı için kayıt defteri tabanlı statik proxy yapılandırın.

> [!NOTE]
> Windows 10, Windows 11 veya Windows Server 2019 veya Windows Server 2022'de bu seçeneği kullanırken, aşağıdaki (veya sonraki) derleme ve toplu güncelleştirme paketine sahip olmanız önerilir:
>
> - Windows 11
> - Windows 10, sürüm 1809 veya Windows Server 2019 veya Windows Server 2022 -<https://support.microsoft.com/kb/5001384>
> - Windows 10, sürüm 1909 -<https://support.microsoft.com/kb/4601380>
> - Windows 10, sürüm 2004 -<https://support.microsoft.com/kb/4601382>
> - Windows 10, sürüm 20H2 -<https://support.microsoft.com/kb/4601382>
>
> Bu güncelleştirmeler CnC (Komut ve Denetim) kanalının bağlantısını ve güvenilirliğini artırır.

Statik ara sunucu, grup ilkesi (GP) aracılığıyla yapılandırılabilir; grup ilkesi değerleri altındaki her iki ayar da EDR kullanmak üzere ara sunucuya yapılandırılmalıdır. Grup ilkesi Yönetim Şablonları'nda kullanılabilir.

- **Yönetim Şablonları > Windows Bileşenleri > Veri Toplama ve Önizleme Derlemeleri > Bağlı Kullanıcı Deneyimi ve Telemetri Hizmeti için Kimliği Doğrulanmış Proxy kullanımını yapılandırın**.

  **Etkin** olarak ayarlayın ve **Kimliği Doğrulanmış Proxy kullanımını devre dışı bırak'ı** seçin.

  :::image type="content" source="images/atp-gpo-proxy1.png" alt-text="grup ilkesi ayarı1 durum bölmesi" lightbox="images/atp-gpo-proxy1.png":::

- **Yönetim Şablonları > Windows Bileşenleri > Veri Toplama ve Önizleme Derlemeleri > Bağlı kullanıcı deneyimlerini ve telemetrisini yapılandırma**:

  Ara sunucuyu yapılandırın.

  :::image type="content" source="images/atp-gpo-proxy2.png" alt-text="grup ilkesi ayarı2 durum bölmesi" lightbox="images/atp-gpo-proxy2.png":::


| Grup İlkesi | Kayıt defteri anahtarı | Kayıt defteri girdisi | Değer |
|:---|:---|:---|:---|
| Bağlı kullanıcı deneyimi ve telemetri hizmeti için kimliği doğrulanmış proxy kullanımını yapılandırma | `HKLM\Software\Policies\Microsoft\Windows\DataCollection` | `DisableEnterpriseAuthProxy` | 1 (REG_DWORD) |
| Bağlı kullanıcı deneyimlerini ve telemetriyi yapılandırma | `HKLM\Software\Policies\Microsoft\Windows\DataCollection` | `TelemetryProxyServer` | ```servername:port or ip:port``` <br> <br> Örneğin: ```10.0.0.6:8080``` (REG_SZ) |

## <a name="configure-a-static-proxy-for-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma için statik proxy yapılandırma

Microsoft Defender Virüsten Koruma [bulut tabanlı koruma](cloud-protection-microsoft-defender-antivirus.md), yeni ve yeni tehditlere karşı neredeyse anında, otomatik koruma sağlar. Defender Virüsten Koruma etkin kötü amaçlı yazılımdan koruma çözümünüz olduğunda [özel göstergeler](manage-indicators.md) için bağlantının gerekli olduğunu unutmayın. [Blok modundaki EDR](edr-in-block-mode.md), Microsoft dışı bir çözüm kullanırken birincil kötü amaçlı yazılımdan koruma çözümüne sahiptir.

Yönetim Şablonları'nda bulunan grup ilkesi kullanarak statik proxy'yi yapılandırın:

1. **Yönetim Şablonları > Windows Bileşenleri > Microsoft Defender Virüsten Koruma > Ağa bağlanmak için ara sunucu tanımlayın**. 

2. **Etkin** olarak ayarlayın ve proxy sunucusunu tanımlayın. URL'nin http:// veya https:// olması gerektiğini unutmayın. https:// için desteklenen sürümler için bkz. [Microsoft Defender Virüsten Koruma güncelleştirmelerini yönetme](manage-updates-baselines-microsoft-defender-antivirus.md).

   :::image type="content" source="images/proxy-server-mdav.png" alt-text="Microsoft Defender Virüsten Koruma için ara sunucu" lightbox="images/proxy-server-mdav.png":::

3. kayıt defteri anahtarı `HKLM\Software\Policies\Microsoft\Windows Defender`altında, ilke kayıt defteri değerini `ProxyServer` REG_SZ olarak ayarlar. 

   Kayıt defteri değeri `ProxyServer` aşağıdaki dize biçimini alır:

    ```text
    <server name or ip>:<port>

    For example: http://10.0.0.6:8080
    ```

> [!NOTE]
>
> Dayanıklılık amacıyla ve bulut tabanlı korumanın gerçek zamanlı yapısı için Microsoft Defender Virüsten Koruma bilinen son çalışan ara sunucuyu önbelleğe alır. Proxy çözümünüzün SSL incelemesi gerçekleştirmediğinden emin olun. Bu, güvenli bulut bağlantısını kesecektir. 
>
> Microsoft Defender Virüsten Koruma, güncelleştirmeleri indirmek üzere Windows Update veya Microsoft Update'e bağlanmak için statik ara sunucuyu kullanmaz. Bunun yerine, Windows Update kullanacak şekilde yapılandırılmışsa sistem genelinde bir ara sunucu veya yapılandırılmış [geri dönüş sırasına](manage-protection-updates-microsoft-defender-antivirus.md) göre yapılandırılmış iç güncelleştirme kaynağı kullanır. 
>
> Gerekirse, ağa bağlanmak için **Yönetim Şablonları > Windows Bileşenleri'ni kullanabilir > Microsoft Defender Virüsten Koruma > Ara sunucu otomatik yapılandırmasını (.pac) tanımlayabilirsiniz**. Birden çok ara sunucuyla gelişmiş yapılandırmalar ayarlamanız gerekiyorsa, proxy sunucusunu atlamak ve Microsoft Defender Virüsten Koruma ara sunucu kullanmasını önlemek **> Microsoft Defender Virüsten Koruma > Adresleri tanımlamak > Microsoft Defender Virüsten Koruma > Yönetim Şablonları > Windows Bileşenleri'ni** kullanın Hedef. 
>
> PowerShell'i cmdlet'iyle `Set-MpPreference` birlikte kullanarak şu seçenekleri yapılandırabilirsiniz: 
>
> - ProxyBypass 
> - ProxyPacUrl 
> - ProxyServer 

> [!NOTE]
> Proxy'yi doğru kullanmak için şu üç farklı ara sunucu ayarlarını yapılandırın:
>  - Uç Nokta için Microsoft Defender (MDE)
>  - AV (Virüsten Koruma)
>  - Uç Nokta Algılama ve Yanıt (EDR)

## <a name="configure-the-proxy-server-manually-using-netsh-command"></a>Netsh komutunu kullanarak ara sunucuyu el ile yapılandırma

Sistem genelinde statik ara sunucuyu yapılandırmak için netsh kullanın.

> [!NOTE]
>
> - Bu, varsayılan proxy ile WinHTTP kullanan Windows hizmetleri de dahil olmak üzere tüm uygulamaları etkiler.</br>
> - Topolojiyi değiştiren dizüstü bilgisayarlar (örneğin: ofisten eve) netsh komutuyla arızalanır. Kayıt defteri tabanlı statik proxy yapılandırmasını kullanın.

1. Yükseltilmiş bir komut satırı açın:
   1. **Başlangıç'a** gidin ve **cmd** yazın.
   1. **Komut istemi'ne** sağ tıklayın ve **Yönetici olarak çalıştır'ı** seçin.

2. Aşağıdaki komutu girin ve **Enter tuşuna** basın:

   ```PowerShell
   netsh winhttp set proxy <proxy>:<port>
   ```

   Örneğin: `netsh winhttp set proxy 10.0.0.6:8080`

Winhttp proxy'yi sıfırlamak için aşağıdaki komutu girin ve **Enter tuşuna** basın:

```PowerShell
netsh winhttp reset proxy
```

Daha fazla bilgi için bkz. [Netsh Komut Söz Dizimi, Bağlamlar ve Biçimlendirme](/windows-server/networking/technologies/netsh/netsh-contexts) .

## <a name="enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server"></a>Ara sunucudaki Uç Nokta için Microsoft Defender hizmet URL'lerine erişimi etkinleştirme

Varsayılan olarak, bir ara sunucu veya güvenlik duvarı tüm trafiği varsayılan olarak engelliyorsa ve yalnızca belirli etki alanlarına izin veriliyorsa, indirilebilir sayfada listelenen etki alanlarını izin verilen etki alanları listesine ekleyin.

Aşağıdaki indirilebilir elektronik tablo, ağınızın bağlanabilmesi gereken hizmetleri ve bunların ilişkili URL'lerini listeler. Bu URL'lere erişimi reddedecek güvenlik duvarı veya ağ filtreleme kuralı olmadığından emin olun. İsteğe bağlı olarak, bunlar için özel olarak bir *izin verme* kuralı oluşturmanız gerekebilir.

<br>

|Etki alanları listesinin elektronik tablosu| Açıklama|
|---|---|
|Ticari müşteriler için Uç Nokta için Microsoft Defender URL listesi| Ticari müşteriler için hizmet konumları, coğrafi konumlar ve işletim sistemi için belirli DNS kayıtlarının elektronik tablosu. <p> [Elektronik tabloyu buradan indirin.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Gov/GCC/DoD için Uç Nokta için Microsoft Defender URL listesi | Gov/GCC/DoD müşterileri için hizmet konumları, coğrafi konumlar ve işletim sistemi için belirli DNS kayıtlarının elektronik tablosu. <p> [Elektronik tabloyu buradan indirin.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

Bir ara sunucuda veya güvenlik duvarında HTTPS taraması (SSL incelemesi) etkinse, yukarıdaki tabloda listelenen etki alanlarını HTTPS taramasının dışında tutun.
Güvenlik duvarınızda coğrafya sütununun WW olduğu tüm URL'leri açın. Coğrafya sütununun WW olmadığı satırlar için, belirli veri konumunuzun URL'lerini açın. Veri konumu ayarınızı doğrulamak için bkz. [Veri depolama konumunu doğrulama ve Uç Nokta için Microsoft Defender için veri saklama ayarlarını güncelleştirme](/microsoft-365/security/defender-endpoint/data-retention-settings).

> [!NOTE]
> Windows sürüm 1803 veya önceki sürümlerle çalışan cihazlar gereksinimleri`settings-win.data.microsoft.com`.  <br>
>
> Bunlara v20 içeren URL'ler yalnızca sürüm 1803 veya üzerini çalıştıran Windows cihazlarınız varsa gereklidir. Örneğin, `us-v20.events.data.microsoft.com` sürüm 1803 veya üzerini çalıştıran ve ABD Veri Depolama bölgesine eklenen bir Windows cihazı için gereklidir.
>

Ara sunucu veya güvenlik duvarı Uç Nokta için Defender algılayıcısı olarak anonim trafiği engelliyorsa ve önceden listelenen URL'lerde anonim trafiğe izin verildiğinden emin olmak için sistem bağlamından bağlanıyorsa.

> [!NOTE]
> Microsoft bir proxy sunucusu sağlamaz. Bu URL'lere yapılandırdığınız proxy sunucusu üzerinden erişilebilir.

### <a name="microsoft-monitoring-agent-mma---proxy-and-firewall-requirements-for-older-versions-of-windows-client-or-windows-server"></a>Microsoft Monitoring Agent (MMA) - Windows istemcisinin veya Windows Server'ın eski sürümleri için ara sunucu ve güvenlik duvarı gereksinimleri

Ara sunucu ve güvenlik duvarı yapılandırma bilgileri listesindeki bilgiler, Windows 7 SP1, Windows 8.1 ve Windows Server 2008 R2* gibi Windows önceki sürümleri için Log Analytics aracısı (genellikle Microsoft Monitoring Agent olarak adlandırılır) ile iletişim kurmak için gereklidir.

<br>

****

|Aracı Kaynağı|Bağlantı Noktaları|Yön|HTTPS denetlemesi atlaması|
|---|---|---|---|
|*.ods.opinsights.azure.com|Bağlantı Noktası 443|Giden|Evet|
|*.oms.opinsights.azure.com|Bağlantı Noktası 443|Giden|Evet|
|*.blob.core.windows.net|Bağlantı Noktası 443|Giden|Evet|
|*.azure-automation.net|Bağlantı Noktası 443|Giden|Evet|

> [!NOTE]
> *Bu bağlantı gereksinimleri, önceki Uç Nokta için Microsoft Defender Windows Server 2016 ve MMA gerektiren Windows Server 2012 R2 için geçerlidir. Bu işletim sistemlerini yeni birleştirilmiş çözümle ekleme yönergeleri[, Windows sunucuları ekleme](configure-server-endpoints.md) veya [Uç Nokta için Microsoft Defender'daki Sunucu geçiş senaryolarında](/microsoft-365/security/defender-endpoint/server-migration) yeni birleşik çözüme geçiş konusunda verilmiştir.

> [!NOTE]
> Bulut tabanlı bir çözüm olarak IP aralığı değişebilir. Dns çözümleme ayarına geçmeniz önerilir.

## <a name="confirm-microsoft-monitoring-agent-mma-service-url-requirements"></a>Microsoft Monitoring Agent (MMA) Hizmet URL'si Gereksinimlerini Onaylayın 

 Windows'in önceki sürümleri için Microsoft Monitoring Agent (MMA) kullanırken ortamınız için joker karakter (*) gereksinimini ortadan kaldırmak için aşağıdaki kılavuza bakın.

1. Uç Nokta için Defender'a Microsoft Monitoring Agent (MMA) içeren önceki bir işletim sistemini ekleme (daha fazla bilgi için bkz. [Uç Nokta için Defender'da Windows önceki sürümlerini](https://go.microsoft.com/fwlink/p/?linkid=2010326) ekleme ve [Windows sunucuları ekleme](configure-server-endpoints.md)).

2. Makinenin Microsoft 365 Defender portalına başarıyla raporlandığından emin olun.

3. Bağlantıyı doğrulamak ve belirli çalışma alanınız için gerekli URL'leri almak için "C:\Program Files\Microsoft Monitoring Agent\Agent" konumundan TestCloudConnection.exe aracını çalıştırın.

4. Bölgeniz için gereksinimlerin tam listesi için Uç Nokta için Microsoft Defender URL'leri listesini denetleyin (Hizmet URL'leri [Elektronik Tablosuna](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx) bakın).

   :::image type="content" source="images/admin-powershell.png" alt-text="Windows PowerShell'deki yönetici" lightbox="images/admin-powershell.png":::

.ods.opinsights.azure.com, \*.oms.opinsights.azure.com ve \*.agentsvc.azure-automation.net URL uç noktalarında \*kullanılan joker karakterler (\*) kendi Çalışma Alanı Kimliğiniz ile değiştirilebilir. Çalışma Alanı Kimliği ortamınıza ve çalışma alanınıza özgüdür. Bu, Microsoft 365 Defender portalındaki kiracınızın Ekleme bölümünde bulunabilir.

\*.blob.core.windows.net URL uç noktası, test sonuçlarının "Güvenlik Duvarı Kuralı: \*.blob.core.windows.net" bölümünde gösterilen URL'lerle değiştirilebilir.

> [!NOTE]
> Bulut için Microsoft Defender aracılığıyla ekleme yapılması durumunda birden çok çalışma alanı kullanılabilir. Her çalışma alanından eklenen makinede TestCloudConnection.exe yordamını gerçekleştirmeniz gerekir (çalışma alanları arasında *.blob.core.windows.net URL'lerinde değişiklik olup olmadığını belirlemek için).

## <a name="verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls"></a>Uç Nokta için Microsoft Defender hizmet URL'lerine istemci bağlantısını doğrulama

Proxy yapılandırmasının başarıyla tamamlandığını doğrulayın. WinHTTP daha sonra ortamınızdaki ara sunucu aracılığıyla bulabilir ve iletişim kurabilir ve ara sunucu Uç Nokta için Defender hizmeti URL'lerine gelen trafiğe izin verir.

1. uç nokta için Defender algılayıcısının çalıştığı bilgisayara [Uç Nokta için Microsoft Defender İstemci Çözümleyicisi aracını](https://aka.ms/mdeanalyzer) indirin. Alt düzey sunucular için en son önizleme sürümünü Uç Nokta için Microsoft Defender [İstemci Çözümleyicisi aracı Beta'yı](https://aka.ms/BetaMDEAnalyzer) indirebilirsiniz.

2. Cihazdaki MDEClientAnalyzer.zip içeriğini ayıklayın.

3. Yükseltilmiş bir komut satırı açın:
   1. **Başlangıç'a** gidin ve **cmd** yazın.
   1. **Komut istemi'ne** sağ tıklayın ve **Yönetici olarak çalıştır'ı** seçin.

4. Aşağıdaki komutu girin ve **Enter tuşuna** basın:

    ```PowerShell
    HardDrivePath\MDEClientAnalyzer.cmd
    ```

    *HardDrivePath'i* MDEClientAnalyzer aracının indirildiği yolla değiştirin. Örneğin:

    ```PowerShell
    C:\Work\tools\MDEClientAnalyzer\MDEClientAnalyzer.cmd
    ```

5. Araç *, HardDrivePath'te* kullanılacak klasörde *MDEClientAnalyzerResult.zip* dosyasını oluşturur ve ayıklar.

6. *MDEClientAnalyzerResult.txt* açın ve sunucu bulmayı ve hizmet URL'lerine erişimi etkinleştirmek için ara sunucu yapılandırma adımlarını gerçekleştirdiğinizden emin olun.

   Araç, Uç Nokta için Defender hizmet URL'lerinin bağlantısını denetler. Uç Nokta için Defender istemcisinin etkileşim kuracak şekilde yapılandırıldığından emin olun. Araç, uç nokta için Defender hizmetleriyle iletişim kurmak için kullanılabilecek her URL için sonuçları *MDEClientAnalyzerResult.txt* dosyasına yazdırır. Örneğin:

   ```text
   Testing URL : https://xxx.microsoft.com/xxx
   1 - Default proxy: Succeeded (200)
   2 - Proxy auto discovery (WPAD): Succeeded (200)
   3 - Proxy disabled: Succeeded (200)
   4 - Named proxy: Doesn't exist
   5 - Command line proxy: Doesn't exist
   ```

Bağlantı seçeneklerinden herhangi biri (200) durumu döndürürse, Uç Nokta için Defender istemcisi bu bağlantı yöntemini kullanarak test edilen URL ile düzgün bir şekilde iletişim kurabilir.

Ancak, bağlantı denetimi sonuçları bir hata gösteriyorsa, bir HTTP hatası görüntülenir (bkz. HTTP Durum Kodları). Ardından [ara sunucudaki Uç Nokta için Defender hizmeti URL'lerine erişimi etkinleştirme bölümünde gösterilen tabloda yer alan URL'leri](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server) kullanabilirsiniz. Kullanılabilir URL'ler, ekleme yordamı sırasında seçilen bölgeye bağlıdır.

> [!NOTE]
> Bağlantı Çözümleyicisi aracının bulut bağlantı denetimleri [, PSExec ve WMI komutlarından kaynaklanan Saldırı Yüzeyi Azaltma kuralı Blok işlemi oluşturma işlemleriyle](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands) uyumlu değildir. Bağlantı aracını çalıştırmak için bu kuralı geçici olarak devre dışı bırakmanız gerekir. Alternatif olarak, çözümleyiciyi çalıştırırken geçici [olarak ASR dışlamaları](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) ekleyebilirsiniz.
>
> TelemetryProxyServer Kayıt Defteri'nde veya grup ilkesi aracılığıyla ayarlandığında Uç Nokta için Defender geri döner ve tanımlanan ara sunucuya erişemiyor.

## <a name="related-articles"></a>İlgili makaleler

- [Microsoft Defender Virüsten Koruma yapılandırmak ve yönetmek için grup ilkesi ayarlarını kullanma](use-group-policy-microsoft-defender-antivirus.md)
- [Windows cihazları ekleme](configure-endpoints.md)
- [Uç Nokta için Microsoft Defender ekleme sorunlarını giderme](troubleshoot-onboarding.md)
