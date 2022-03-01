---
title: Bilgi Koruması için cihaz ara sunucusunu ve internet bağlantısı ayarlarını yapılandırma
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: Bilgi Koruması için cihaz ara sunucusunu ve internet bağlantısı ayarlarını yapılandırma
ms.openlocfilehash: 2d0bc6484636cffb479ccb96b3458fddf0697cd7
ms.sourcegitcommit: 726a72f135358603c2fde3f4067d834536e6deb2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2022
ms.locfileid: "63014319"
---
# <a name="configure-device-proxy-and-internet-connection-settings-for-information-protection"></a>Bilgi Koruması için cihaz ara sunucusunu ve internet bağlantısı ayarlarını yapılandırma

Microsoft Endpoint technologies, verileri rapor etmek Windows Microsoft uç nokta bulut hizmetiyle iletişim kurmak için HTTP (WinHTTP) Microsoft Web Sitesini kullanır. Ekli hizmet, LocalSystem hesabını kullanarak sistem bağlamında çalışır.

> [!TIP]
> İnternet'e bir ağ geçidi olarak iletme ara sunucularını kullanan kuruluşlarda, bir proxy'nin arkasında araştırma yapmak için ağ korumasını kullanabilirsiniz. Daha fazla bilgi için bkz [. İleri gelen sunucularda oluşan bağlantı olaylarını araştırma](/windows/security/threat-protection/microsoft-defender-atp/investigate-behind-proxy).

WinHTTP yapılandırma ayarı, Windows Internet (WinINet) Internet'e gözatma proxy ayarlarından bağımsızdır ve yalnızca aşağıdaki otomatik bulma yöntemlerini kullanarak bir proxy sunucusu keşfedebilirsiniz:

- Saydam ara sunucu
- Web Proxy Otomatik Bulma Protokolü (WPAD)

> [!NOTE]
> Ağ topolojinizde Saydam ara sunucu veya WPAD kullanıyorsanız, özel yapılandırma ayarlarına ihtiyacınız yok. Proxy'de Uç Nokta URL dışlamaları için Defender hakkında daha fazla bilgi için bkz. Proxy sunucusunda [Uç Nokta DLP bulut hizmeti URL'lerine erişimi etkinleştirme](#enable-access-to-endpoint-dlp-cloud-service-urls-in-the-proxy-server).

- El ile statik ara sunucu yapılandırması:
  - Kayıt defteri tabanlı yapılandırma
  - WinHTTP netsh komutu kullanılarak yapılandırıldı – Yalnızca kararlı bir topolojide masaüstleri için uygundur (örneğin: aynı ara sunucu arkasında şirket ağının bir masaüstü)

## <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>Kayıt defteri tabanlı statik proxy'yi kullanarak proxy sunucusunu el ile yapılandırma

İnternet'e bağlanmasına izin ver olmayan uç nokta cihazları için kayıt defteri tabanlı statik bir ara sunucu yapılandırmanız gerekir. Bunu, yalnızca Microsoft Endpoint DLP'nin tanılama verilerini bildirmesine ve Microsoft uç nokta bulut hizmetiyle iletişim kurmasına izin verecek şekilde yapılandırmanız gerekir.

Statik ara sunucu Grup İlkesi (GP) aracılığıyla yapılandırılabilir. Grup ilkesi şu altında bulunabilir:

1. Bağlı **Kullanıcı Deneyimi > Windows Telemetri >** Için Kimliği Doğrulanmış Ara Sunucu kullanımını yapılandırma > Için Veri Toplama ve Önizleme Derlemeleri için Yönetim Şablonları ve Bileşenleri

2. Etkin olarak ayarlayın **ve Kimliği** Doğrulanmış Proxy **kullanımını devre dışı bırak'ı seçin**:

   ![Grup ilkesi ayarları 1'in görüntüsü.](../media/atp-gpo-proxy1.png)

3. Bağlı **kullanıcı deneyimlerini > Windows telemetrisi > Veri Toplama ve Önizleme** Derlemeleri için Yönetim şablonları > Açın:

   Proxy'yi yapılandırma

   ![Grup ilkesi ayarları 2'nin resmi.](../media/atp-gpo-proxy2.png)

   İlke, kayıt defteri anahtarının `TelemetryProxyServer` REG_SZ olarak ve `DisableEnterpriseAuthProxy` REG_DWORD olarak iki kayıt defteri değeri ayarlar `HKLM\Software\Policies\Microsoft\Windows\DataCollection`.

   TelemetryProxyServer kayıt defteri değeri şu biçimdedir\<server name or ip\>\<port\>:. Örneğin: **10.0.0.6:8080**

   Kayıt defteri değeri `DisableEnterpriseAuthProxy` 1 olarak ayar gerekir.

## <a name="configure-the-proxy-server-manually-using-netsh-command"></a>"netsh" komutunu kullanarak proxy sunucusunu el ile yapılandırma

Sistem çapında bir statik ara sunucu yapılandırmak için netsh kullanın.

> [!NOTE]
> Bu da varsayılan ara sunucuyla WinHTTP Windows hizmetleri dahil olmak üzere tüm uygulamaları etkiler. - Topolojisi değişen dizüstü bilgisayarlar (örneğin: ofisten ev'e) netsh ile düzgün çalışmayan dizüstü bilgisayarlar. Kayıt defteri tabanlı statik ara sunucu yapılandırmasını kullanın.

1. Yükseltilmiş bir komut satırı açın:
    1. **Başlat'a gidin** ve **cmd yazın**
    2. Komut istemi'ne **sağ tıklayın ve** Yönetici olarak **çalıştır'ı seçin**.

2. Aşağıdaki komutu girin ve Enter tuşuna **basın**:

   `netsh winhttp set proxy <proxy>:<port>`

   Örneğin: **netsh winhttp set proxy 10.0.0.6:8080**

3. Winhttp proxy'lerini sıfırlamak için aşağıdaki komutu girin ve Enter tuşuna **basın**:

   `netsh winhttp reset proxy`

Daha [fazla bilgi edinmek için bkz. Netsh](/windows-server/networking/technologies/netsh/netsh-contexts) Komut Sözdizimi, Bağlam ve Biçimlendirme.

## <a name="enable-access-to-endpoint-dlp-cloud-service-urls-in-the-proxy-server"></a>Proxy sunucusunda Uç Nokta DLP bulut hizmeti URL'lerine erişimi etkinleştirme

Bir ara sunucu veya güvenlik duvarı varsayılan olarak tüm trafiği engelliyorsa ve yalnızca belirli etki alanları üzerinden izin veriliyorsa, indirilebilir sayfada listelenen etki alanlarını izin verilen etki alanları listesine ekleyin.

Bu [indirilebilir elektronik tablo](https://download.microsoft.com/download/8/a/5/8a51eee5-cd02-431c-9d78-a58b7f77c070/mde-urls.xlsx) , ağ bağlantı kur olması gereken hizmetleri ve bu hizmetlerle ilişkilendirilmiş URL'leri listeler. Bu URL'lere erişimi reddedecek güvenlik duvarı veya ağ filtreleme kuralları olmadığını veya bunlar için özel olarak bir izin kuralı oluşturmanız gerekebilir.

Ara sunucu veya güvenlik duvarı HTTPS tarama (SSL incelemesi) etkinse, yukarıdaki tabloda listelenen etki alanlarını HTTPS tarama dışında tutabilirsiniz.
Bir ara sunucu veya güvenlik duvarı anonim trafiği engelliyorsa, Uç Nokta DLP sistem bağlamından bağlanıyorsa, anonim trafiğin daha önce listelenen URL'lerde izin verildiğinden emin olun.

## <a name="verify-client-connectivity-to-microsoft-cloud-service-urls"></a>Microsoft bulut hizmeti URL'leri için istemci bağlantısını doğrulama

Proxy yapılandırmasının başarıyla tamamlandıktan sonra WinHTTP'nin ortamınız içinde ara sunucu üzerinden sunucuyu keşfederek ileteni ve proxy sunucusunun Uç nokta hizmeti URL'leri için Defender'a trafiğine izin vereni doğrulayın.

1. Uç Nokta [DLP'nin bulunduğu bilgisayara MDATP](https://aka.ms/mdatpanalyzer) İstemci Çözümleyicisi aracını indirin.
2. Cihaz üzerinde MDATPClientAnalyzer.zip içeriğini ayıkla.
3. Yükseltilmiş bir komut satırı açın:
    1. **Başlat'a gidin** ve **cmd yazın**.
    1. Komut istemi'ne **sağ tıklayın ve** Yönetici olarak **çalıştır'ı seçin**.
4. Aşağıdaki komutu girin ve Enter tuşuna **basın**:

   `HardDrivePath\MDATPClientAnalyzer.cmd`

   *Örneğin, SabitDrivePath'i* MDATPClientAnalyzer aracının indirilmiş olduğu yol ile değiştirin

   **C:\Work\tools\MDATPClientAnalyzer\MDATPClientAnalyzer.cmd**

5. MDATPClientAnalyzerResult.zip **içinde kullanılan** klasörde araç tarafından oluşturulan _HardDrivePath _ _HardDrivePath.

6. Sunucu **MDATPClientAnalyzerResult.txt** ve hizmet URL'lerine erişimi etkinleştirmek için sunucu bulma ve erişim için proxy yapılandırma adımlarını gerçekleştirin.  Araç, Uç Nokta istemcisi için Defender'ın etkileşimde bulunmak üzere yapılandırılan Uç nokta hizmeti URL'leri için Defender bağlantısını denetler. Ardından, uç nokta hizmetleri için **Defender'MDATPClientAnalyzerResult.txt** iletişim kurmak için kullanabilecek her URL için sonuçlarıMDATPClientAnalyzerResult.txtdosyasına yazdırır. Örneğin:

   ```DOS
   Testing URL: https://xxx.microsoft.com/xxx
   1 - Default proxy: Succeeded (200)
   2 - Proxy auto discovery (WPAD): Succeeded (200)
   3 - Proxy disabled: Succeeded (200)
   4 - Named proxy: Doesn't exist
   5 - Command-line proxy: Doesn't exist
   ```

Bağlantı seçenekleriden en az biri (200) durumu döndürürse, Uç Nokta için Defender istemcisi bu bağlantı yöntemini kullanarak test edilen URL'ye düzgün bir şekilde iletişim kurabilir.

Bununla birlikte, bağlantı denetimi sonucunda bir hata olduğu belirtleniyorsa HTTP hatası görüntülenir (bkz. HTTP Durum Kodları). Bundan sonra, Proxy sunucusunda Uç Nokta DLP bulut hizmeti URL'lerine erişimi etkinleştirme bağlantısında gösterilen tabloda yer alan [URL'leri kullanabilirsiniz](#enable-access-to-endpoint-dlp-cloud-service-urls-in-the-proxy-server). Kullanabileceğiniz URL'ler, ekleme yordamı sırasında seçilen bölgeye bağlıdır.

> [!NOTE]
>
> Bağlantı Çözümleyicisi aracı, PSExec ve WMI komutlarından kaynaklanan saldırı yüzeyi azaltma kuralı [Block process creations ile uyumlu değildir](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules-reference#block-process-creations-originating-from-psexec-and-wmi-commands). Bağlantı aracını çalıştırmak için bu kuralı geçici olarak devre dışı bırakmanız gerekir.
>
> TelemetryProxyServer ayarlandığı zaman, Kayıt Defteri'nda veya Grup İlkesi aracılığıyla Uç Nokta için Defender tanımlı proxy'ye erişeni kontrol etmede doğrudan kullanılabilir. İlgili konular:
>
> - Cihaz Windows 10 ekleme
> - Microsoft Endpoint DLP ekleme sorunlarını giderme

## <a name="see-also"></a>Ayrıca bkz.

- [Uç nokta veri kaybını önleme hakkında bilgi](endpoint-dlp-learn-about.md)
- [Uç nokta veri kaybını önlemeyi kullanma](endpoint-dlp-using.md)
- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)
- [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md)
- [Etkinlik gezgini ile çalışmaya başlama](data-classification-activity-explorer.md)
- [Uç Nokta için Microsoft Defender](/windows/security/threat-protection/)
- [Makine makineniz için ekleme araçları Windows 10 yöntemleri](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)
- [Microsoft 365 aboneliği](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure AD'ye katılan cihazlar](/azure/active-directory/devices/concept-azure-ad-join)
- [Temel Microsoft Edge yeni Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
