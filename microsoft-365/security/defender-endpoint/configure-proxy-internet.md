---
title: Cihaz ara sunucusunu ve İnternet bağlantısı ayarlarını yapılandırma
description: Bulut hizmetiyle Uç Nokta için Microsoft Defender sağlamak için hızlı ara sunucu ve İnternet ayarlarını yapılandırabilirsiniz.
keywords: configure, proxy, internet, internet bağlantısı, ayarlar, proxy ayarları, netsh, winhttp, proxy server
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
ms.openlocfilehash: cf68afff79a2d719435e9df3d53400584f162618
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507355"
---
# <a name="configure-device-proxy-and-internet-connectivity-settings"></a>Cihaz ara sunucusunu ve İnternet bağlantısı ayarlarını yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-configureendpointsscript-abovefoldlink)

Uç nokta algılayıcısı için Defender, algılayıcı verilerini bildirmesi ve Uç nokta için Defender ile iletişim kurması için MICROSOFT Windows HTTP (WinHTTP) gerektirir. Uç nokta algılayıcısı için ekli Defender LocalSystem hesabını kullanarak sistem bağlamında çalışır. Algılayıcı, Uç nokta bulut Windows Defender ile iletişimi etkinleştirmek için Microsoft http services (WinHTTP) kullanır.

> [!TIP]
> İnternet'e bir ağ geçidi olarak iletme ön sunucularını kullanan kuruluşlarda, ileriye doğru geçişlerin arkasında oluşan bağlantı olaylarını araştırmak için [ağ korumasını kullanabilirsiniz](investigate-behind-proxy.md).

WinHTTP yapılandırma ayarı, Windows Internet (WinINet) gözatma ara sunucusu ayarlarından (bkz. [WinINet ile WinHTTP) bağımsızdır](/windows/win32/wininet/wininet-vs-winhttp). Ara sunucuyu ancak aşağıdaki bulma yöntemlerini kullanarak keşfedebilirsiniz:

- Otomatik Bulma yöntemleri:

  - Saydam ara sunucu
  
  - Web Proxy Otomatik Bulma Protokolü (WPAD)

    > [!NOTE]
    > Ağ topolojinizde Saydam ara sunucu veya WPAD kullanıyorsanız, özel yapılandırma ayarlarına ihtiyacınız yok. Proxy'de Uç Nokta URL dışlamaları için Defender hakkında daha fazla bilgi için bkz. Proxy sunucusunda Uç nokta hizmeti [URL'leri için Defender'a erişimi etkinleştirme](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server)

- El ile statik ara sunucu yapılandırması:

  - Kayıt defteri tabanlı yapılandırma
  
  - WinHTTP netsh komutu kullanılarak yapılandırıldı: Kararlı bir topolojide yalnızca masaüstleri için uygundur (örneğin: aynı proxy'nin arkasındaki bir şirket ağının masaüstü)

> [!NOTE]
> Defender virüsten koruma EDR dizileri birbirinden bağımsız olarak ayarlanır.  Takip eden bölümlerde bu farklara dikkat edin.

## <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>Kayıt defteri tabanlı statik proxy'yi kullanarak proxy sunucusunu el ile yapılandırma

Tanılama verilerini raporunuk ve bir bilgisayarın İnternet'e bağlanmasına izin verilmediğini varsa Uç nokta algılama ve yanıt (EDR) algılayıcısı için Defender için kayıt defteri tabanlı statik ara sunucu yapılandırın.

> [!NOTE]
> Windows 10, Windows 11 ya da Windows Server 2019 veya Windows Server 2022'de bu seçeneği kullanırken, aşağıdaki (veya daha sonraki) derleme ve toplu güncelleştirme toplaması kullanılması önerilir:
>
> - Windows 11
> - Windows 10, sürüm 1809 Veya Windows Server 2019 ya da Windows Server 2022 -<https://support.microsoft.com/kb/5001384>
> - Windows 10, sürüm 1909 -<https://support.microsoft.com/kb/4601380>
> - Windows 10, sürüm 2004 -<https://support.microsoft.com/kb/4601382>
> - Windows 10, sürüm 20H2 -<https://support.microsoft.com/kb/4601382>
>
> Bu güncelleştirmeler, CnC (Komut ve Denetim) kanalının bağlantısını ve güvenilirliğini geliştirmektedir.

Statik ara sunucu grup ilkesi (GP) aracılığıyla yapılandırılabilir, grup ilkesi değerlerinin altındaki ayarların her ikisi de grup ilkesi değerlerinin kullanımı için ara sunucuya EDR. Grup ilkesi Yönetim Şablonları'nda kullanılabilir.

- **Yönetim Şablonları > Windows Kullanıcı Deneyimi > Telemetri Hizmeti için Kimliği Doğrulanmış Ara > Sunucu** kullanımını yapılandırmak için > Veri Toplama ve Önizleme Derlemelerini Yapılandır.

  Etkin olarak ayarlayın **ve Kimliği** Doğrulanmış Proxy **kullanımını devre dışı bırak'ı seçin**.

  :::image type="content" source="images/atp-gpo-proxy1.png" alt-text="Grup ilkesi ayarı1 durum bölmesi" lightbox="images/atp-gpo-proxy1.png":::

- **Yönetim Şablonları > Windows Kullanıcı > Ve Önizleme Yapılarını Yapılandırma > Bağlı kullanıcı deneyimlerini ve telemetrisi yapılandırma**:

  Proxy'yi yapılandırma.

  :::image type="content" source="images/atp-gpo-proxy2.png" alt-text="Grup ilkesi ayar2 durum bölmesi" lightbox="images/atp-gpo-proxy2.png":::


| Grup İlkesi | Kayıt defteri anahtarı | Kayıt defteri girdisi | Değer |
|:---|:---|:---|:---|
| Bağlı kullanıcı deneyimi ve telemetri hizmeti için kimliği doğrulanmış ara sunucu kullanımını yapılandırma | `HKLM\Software\Policies\Microsoft\Windows\DataCollection` | `DisableEnterpriseAuthProxy` | 1 (REG_DWORD) |
| Bağlı kullanıcı deneyimlerini ve telemetriyi yapılandırma | `HKLM\Software\Policies\Microsoft\Windows\DataCollection` | `TelemetryProxyServer` | ```servername:port or ip:port``` <br> <br> Örneğin: ```10.0.0.6:8080``` (REG_SZ) |

## <a name="configure-a-static-proxy-for-microsoft-defender-antivirus"></a>Etki alanı için statik ara sunucu Microsoft Defender Virüsten Koruma

Microsoft Defender Virüsten Koruma [teslim edilen koruma,](cloud-protection-microsoft-defender-antivirus.md) yeni ve ortaya çıkan tehditlere karşı neredeyse anında otomatik koruma sağlar. Defender Virüsten Koruma etkin kötü amaçlı [yazılımdan koruma çözümünüzse](manage-indicators.md) , bağlantının özel göstergeler için gerekli olduğunu unutmayın. Engelleme [EDR, Microsoft dışı](edr-in-block-mode.md) bir çözüm kullanırken birincil kötü amaçlı yazılımdan koruma çözümüne sahip olur.

Yönetim Şablonlarında bulunan grup ilkesi kullanarak statik proxy'yi yapılandırma:

1. **Yönetim > Windows, > Microsoft Defender Virüsten Koruma > bağlanmak için proxy sunucu tanımlamaya karşı Bileşenler Ve Bileşenler'i içerir**. 

2. Etkin olarak **ayarlayın ve** proxy sunucuyu tanımlayın. URL'nin doğru veya yanlış http:// olması gerektiğini https://. Güncelleştirmelerin desteklenen sürümleri için https:// bkz. [Güncelleştirmeleri Microsoft Defender Virüsten Koruma yönetme](manage-updates-baselines-microsoft-defender-antivirus.md).

   :::image type="content" source="images/proxy-server-mdav.png" alt-text="Proxy sunucu Microsoft Defender Virüsten Koruma" lightbox="images/proxy-server-mdav.png":::

3. Kayıt defteri anahtarının altında `HKLM\Software\Policies\Microsoft\Windows Defender`, ilke kayıt defteri değerini Kayıt Defteri REG_SZ `ProxyServer` . 

   Kayıt defteri değeri `ProxyServer` aşağıdaki dize biçimini alır:

    ```text
    <server name or ip>:<port>

    For example: http://10.0.0.6:8080
    ```

> [!NOTE]
>
> Buluta teslim edilen korumanın korumak için ve gerçek zamanlı yapısı için, Microsoft Defender Virüsten Koruma bilinen en son çalışan ara sunucu kullanılır. Ara sunucu çözümünüz SSL denetimi gerçekleştirmez. Bu, güvenli bulut bağlantısını bozacak. 
>
> Microsoft Defender Virüsten Koruma, statik proxy'ye, güncelleştirmeleri indirmek üzere Windows Update Microsoft Update'e bağlanmak için kullanmaz. Bunun yerine, ara sunucu veya yapılandırılmış geri dönüş sırasına göre Windows Update yapılandırılmış iç güncelleştirme kaynağı yapılandırılmışsa, sistem genelinde bir ara sunucu [kullanır](manage-protection-updates-microsoft-defender-antivirus.md). 
>
> Gerekirse, ağa bağlanmak için **Yönetim > Windows Bileşenleri > Microsoft Defender Virüsten Koruma > Ara sunucu otomatik yapılandırmayı tanımla (.pac)** özelliğini kullanabilirsiniz. Birden çok ara sunucuyla gelişmiş yapılandırmalar ayarlamanız gerekirse, proxy sunucuyu atlamak ve Microsoft Defender Virüsten Koruma'nin bu sunucularda ara sunucu kullanmasını önlemek için Yönetim Şablonları **> Windows Bileşenleri > Microsoft Defender Virüsten Koruma >** Adresleri tanımla'ya hedefler. 
>
> Şu seçenekleri yapılandırmak için PowerShell'i `Set-MpPreference` cmdlet ile kullanabilirsiniz: 
>
> - ProxyBypass 
> - ProxyPacUrl 
> - ProxyServer 

> [!NOTE]
> Proxy'yi doğru kullanmak için şu üç farklı ara sunucu ayarlarını yapılandırabilirsiniz:
>  - Uç Nokta için Microsoft Defender (MDE)
>  - AV (Virüsten Koruma)
>  - Uç Nokta Algılama ve Yanıt (EDR)

## <a name="configure-the-proxy-server-manually-using-netsh-command"></a>Netsh komutunu kullanarak proxy sunucusunu el ile yapılandırma

Sistem çapında bir statik ara sunucu yapılandırmak için netsh kullanın.

> [!NOTE]
>
> - Bu da varsayılan ara sunucuyla WinHTTP Windows hizmetleri dahil olmak üzere tüm uygulamaları etkiler.</br>
> - Topolojisi değişen dizüstü bilgisayarlar (örneğin: ofisten ev'e) netsh komutuyla düzgün çalışmayan dizüstü bilgisayarlar. Kayıt defteri tabanlı statik ara sunucu yapılandırmasını kullanın.

1. Yükseltilmiş bir komut satırı açın:
   1. **Başlat'a gidin** ve **cmd yazın**.
   1. Komut istemi'ne **sağ tıklayın ve** Yönetici olarak **çalıştır'ı seçin**.

2. Aşağıdaki komutu girin ve Enter tuşuna **basın**:

   ```PowerShell
   netsh winhttp set proxy <proxy>:<port>
   ```

   Örneğin: `netsh winhttp set proxy 10.0.0.6:8080`

Winhttp proxy'lerini sıfırlamak için aşağıdaki komutu girin ve Enter tuşuna **basın**:

```PowerShell
netsh winhttp reset proxy
```

Daha [fazla bilgi edinmek için bkz. Netsh](/windows-server/networking/technologies/netsh/netsh-contexts) Komut Sözdizimi, Bağlam ve Biçimlendirme.

## <a name="enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server"></a>Proxy sunucusunda Uç Nokta için Microsoft Defender hizmeti URL'lerine erişimi etkinleştirme

Varsayılan olarak, bir ara sunucu veya güvenlik duvarı varsayılan olarak tüm trafiği engelliyor ve yalnızca belirli etki alanlarına izin veriliyorsa, indirilebilir sayfada listelenen etki alanlarını izin verilen etki alanları listesine ekleyin.

Aşağıdaki indirilebilir elektronik tablo, ağ bağlantı kur olması gereken hizmetleri ve bunların ilişkili URL'lerini listeler. Bu URL'lere erişimi reddetmek için güvenlik duvarı veya ağ filtreleme kuralları olmadığını kontrol etme. İsteğe bağlı olarak, özel olarak onlar *için bir izin* kuralı oluşturmanız gerekir.

<br>

|Etki alanı listesinin elektronik tablosu| Açıklama|
|---|---|
|Uç Nokta için Microsoft Defender müşteriler için bir URL listesi| Ticari müşteriler için hizmet konumları, coğrafi konumlar ve işletim sistemi için belirli DNS kayıtlarının elektronik tablosu. <p> [Elektronik tabloyu buradan indirin.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Uç Nokta için Microsoft Defender Gov/GCC/DoD için URL listesi | Gov/GCC/DoD müşterileri için hizmet konumları, coğrafi konumlar ve işletim sistemi için belirli DNS kayıtlarının elektronik tablosu. <p> [Elektronik tabloyu buradan indirin.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

Ara sunucu veya güvenlik duvarı HTTPS tarama (SSL incelemesi) etkinse, yukarıdaki tabloda listelenen etki alanlarını HTTPS tarama dışında tutabilirsiniz.
Güvenlik duvarında, coğrafya sütunu WW olan tüm URL'leri açın. Coğrafya sütununu WW olmayan satırlar için belirli veri konumunuzla ilgili URL'leri açın. Veri konumu ayarınızı doğrulamak için bkz[. Veri depolama konumunu doğrulama ve veri bekletme ayarlarını güncelleştirme Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/data-retention-settings).

> [!NOTE]
> Windows 1803 veya önceki sürümleri ile çalışan cihazları kullanın`settings-win.data.microsoft.com`.  <br>
>
> Url'lerde v20 içeren URL'lerin olması için, Windows 1803 veya sonraki bir sürümü çalıştıran cihazlarınız varsa gereklidir. Örneğin, `us-v20.events.data.microsoft.com` sürüm 1803 veya Windows çalıştıran ve ABD Verileri veri kaynağı bölgesinde bulunan bir Depolama gerekir.
>

Bir ara sunucu veya güvenlik duvarı Uç nokta algılayıcısı için Defender olarak anonim trafiği engelliyorsa ve önceden listelenen URL'lerde anonim trafiğin izin verildiğinden emin olmak için sistem bağlamından bağlanıyorsa.

> [!NOTE]
> Microsoft bir ara sunucu sağlamaz. Bu URL'lere yapılandırılan proxy sunucusu üzerinden erişilebilir.

### <a name="microsoft-monitoring-agent-mma---proxy-and-firewall-requirements-for-older-versions-of-windows-client-or-windows-server"></a>Microsoft Monitoring Agent (MMA) - Windows istemcisinin veya Windows Server'ın eski sürümleri için ara sunucu ve güvenlik Windows gereksinimleri

Proxy ve güvenlik duvarı yapılandırma bilgileri listesinde yer alan bilgiler, Windows'in Windows 7 SP1, Windows 8.1 ve Windows Server 2008 R2 gibi önceki sürümleri için Log Analytics aracısına (genellikle Microsoft Monitoring Agent olarak adlandırılır) ile iletişim kurmak için gereklidir.

<br>

****

|Aracı Kaynağı|Bağlantı Noktaları|Yön|HTTPS denetlemesi atlaması|
|---|---|---|---|
|*.ods.opinsights.azure.com|Bağlantı Noktası 443|Giden|Evet|
|*.oms.opinsights.azure.com|Bağlantı Noktası 443|Giden|Evet|
|*.blob.core.windows.net|Bağlantı Noktası 443|Giden|Evet|
|*.azure-automation.net|Bağlantı Noktası 443|Giden|Evet|

> [!NOTE]
> *Bu bağlantı gereksinimleri, MMA gerektiren Uç Nokta için Microsoft Defender Windows Server 2016 ve R2 Windows Server 2012 için geçerlidir. Yeni birleşik çözümle bu işletim sistemlerini ekleme yönergeleri onboard [Windows sunucularındadır](configure-server-endpoints.md) veya Uç Nokta için Microsoft Defender'te Sunucu geçişi senaryolarında yeni birleşik [çözüme Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/server-migration).

> [!NOTE]
> Bulut tabanlı bir çözüm olarak IP aralığı değişebilir. DNS çözümleme ayarına geçerek bu ayarın kullanılması önerilir.

## <a name="confirm-microsoft-monitoring-agent-mma-service-url-requirements"></a>Hizmet Microsoft Monitoring Agent (MMA) URL Gereksinimlerini Onaylayın 

 Bu güncelleştirmelerin önceki sürümlerinde MMA'yı (MMA) kullanırken belirli ortamınız için joker Microsoft Monitoring Agent (*) gereksinimini ortadan kaldırmak için Windows.

1. Microsoft Monitoring Agent (MMA) ile önceki bir işletim sistemini Uç Nokta için Defender'a ekleme (daha fazla bilgi için bkz. Uç Nokta için [Defender](https://go.microsoft.com/fwlink/p/?linkid=2010326) ve Windows'un önceki sürümlerini ekleme [Windows.](configure-server-endpoints.md)

2. Makinenin portala başarılı bir şekilde rapor Microsoft 365 Defender.

3. Bağlantı TestCloudConnection.exe ve belirli çalışma alanınız için gerekli URL'leri almak için "C:\Program Files\Microsoft Monitoring Agent\Agent" aracından "C:\Program Files\Microsoft Monitoring Agent\Agent" aracından bu aracı çalıştırın.

4. Bölgenizin Uç Nokta için Microsoft Defender tam listesi için URL'ler listesini kontrol edin (Hizmet URL'leri Elektronik Tablosu'ne [bakın](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx)).

   :::image type="content" source="images/admin-powershell.png" alt-text="Yönetici Windows PowerShell" lightbox="images/admin-powershell.png":::

.ods.opinsights.azure.com, .oms.opinsights.azure.com ve \*.agentsvc.azure-automation.net \*URL uç noktalarında kullanılan joker karakterler (\*) \*sizin özel Çalışma Alanı Kimliğiniz ile değiştirilebilir. Çalışma Alanı Kimliği, ortamınıza ve çalışma alanınıza özeldir. Kullanıcı portalı içinde kiracınızı Ekleme Microsoft 365 Defender.

. \*blob.core.windows.net URL uç noktası, test sonuçlarının "Güvenlik Duvarı Kuralı: \*.blob.core.windows.net" bölümünde gösterilen URL'lerle değiştirilebilir.

> [!NOTE]
> Çalışma alanı aracılığıyla ekleme Bulut için Microsoft Defender, birden çok çalışma alanı kullanılabilir. Her çalışma alanında TestCloudConnection.exe makinede kullanıcı yordamını gerçekleştirmeniz gerekir (çalışma alanları arasındaki *.blob.core.windows.net URL'lerde değişiklik olup olmadığını belirlemek için).

## <a name="verify-client-connectivity-to-microsoft-defender-for-endpoint-service-urls"></a>Yeni hizmet URL'leri Uç Nokta için Microsoft Defender bağlantısını doğrulama

Proxy yapılandırmasının başarıyla tamamlanmıştır. Winhttp can then discover and communicate through the proxy server in your environment, and then the proxy server will allow traffic to the Defender for Endpoint service URL'leri.

1. İstemci [Çözümleyicisi Uç Nokta için Microsoft Defender aracını](https://aka.ms/mdeanalyzer), Uç nokta algılayıcısı için Defender'ın açık olduğu bilgisayara indirin. Aşağı düzey sunucular için en son önizleme sürümü, İstemci Çözümleyicisi aracı [Beta Uç Nokta için Microsoft Defender indirilebilir](https://aka.ms/BetaMDEAnalyzer).

2. Cihaz üzerinde MDEClientAnalyzer.zip içeriğini ayıkla.

3. Yükseltilmiş bir komut satırı açın:
   1. **Başlat'a gidin** ve **cmd yazın**.
   1. Komut istemi'ne **sağ tıklayın ve** Yönetici olarak **çalıştır'ı seçin**.

4. Aşağıdaki komutu girin ve Enter tuşuna **basın**:

    ```PowerShell
    HardDrivePath\MDEClientAnalyzer.cmd
    ```

    *HardDrivePath'i* MDEClientAnalyzer aracının indirilmiş olduğu yol ile değiştirin. Örneğin:

    ```PowerShell
    C:\Work\tools\MDEClientAnalyzer\MDEClientAnalyzer.cmd
    ```

5. Araç, klasördeMDEClientAnalyzerResult.zipDosya *dosyasını* *oluşturur ve ayıklar*.

6. Sunucu *MDEClientAnalyzerResult.txt* ve hizmet URL'lerine erişimi etkinleştirmek için sunucu bulma ve erişim için proxy yapılandırma adımlarını gerçekleştirin.

   Araç, Defender'ın Uç nokta hizmeti URL'leri için bağlantısını denetler. Uç Nokta istemcisi için Defender'ın etkileşimde bulunmak üzere yapılandırıldığından emin olun. Araç, uç nokta hizmetleri için Defender *'MDEClientAnalyzerResult.txt* iletişim kurmak için kullanabilecek her URL içinMDEClientAnalyzerResult.txtdosyasındaki sonuçları yazdırır. Örneğin:

   ```text
   Testing URL : https://xxx.microsoft.com/xxx
   1 - Default proxy: Succeeded (200)
   2 - Proxy auto discovery (WPAD): Succeeded (200)
   3 - Proxy disabled: Succeeded (200)
   4 - Named proxy: Doesn't exist
   5 - Command line proxy: Doesn't exist
   ```

Bağlantı seçenekleriden herhangi biri (200) durumu döndürürse, Uç Nokta için Defender istemcisi bu bağlantı yöntemini kullanarak test edilmiş URL'ye düzgün bir şekilde iletişim kurabilir.

Bununla birlikte, bağlantı denetimi sonucunda bir hata olduğu belirtleniyorsa HTTP hatası görüntülenir (bkz. HTTP Durum Kodları). Bundan sonra, proxy sunucusundaki Uç nokta hizmeti URL'leri için Defender'a erişimi etkinleştirme'de gösterilen tabloda [YER alan URL'leri kullanabilirsiniz](#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server). Kullanılabilir URL'ler, ekleme yordamı sırasında seçilen bölgeye bağlıdır.

> [!NOTE]
> Bağlantı Çözümleyicisi aracının bulut bağlantı denetimleri, PSExec ve WMI komutlarından kaynaklanan Saldırı Surface Azaltma kuralı Engelleme işlemi oluşturma işlemi oluşturma [işlemiyle uyumlu değildir](attack-surface-reduction-rules-reference.md#block-process-creations-originating-from-psexec-and-wmi-commands). Bağlantı aracını çalıştırmak için bu kuralı geçici olarak devre dışı bırakmanız gerekir. Alternatif olarak, çözümleyiciyi çalıştırma sırasında [GEÇICI OLARAK ASR dışlamaları](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) eklersiniz.
>
> TelemetryProxyServer Kayıt Defteri'ne veya Grup ilkesi aracılığıyla ayarlandığı zaman, Uç Nokta için Defender geri dönecektir, tanımlı ara sunucuya erişemezse.

## <a name="related-articles"></a>İlgili makaleler

- [E grup ilkesi i yapılandırmak ve yönetmek için bu Microsoft Defender Virüsten Koruma](use-group-policy-microsoft-defender-antivirus.md)
- [Cihaz Windows ekleme](configure-endpoints.md)
- [Uç Nokta için Microsoft Defender ekleme sorunlarını giderme](troubleshoot-onboarding.md)
