---
title: Uç nokta dağıtımı için Microsoft Defender'ı ayarlama
description: Uç nokta için Microsoft Defender'da dağıtımı ayarlamayı öğrenin
keywords: dağıtma, kurulum, lisans doğrulama, kiracı yapılandırması, ağ yapılandırması
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
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-scenario
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c59e07e1d11be406c1f954a656cef7b32fa2851f
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63014412"
---
# <a name="set-up-microsoft-defender-for-endpoint-deployment"></a>Uç nokta dağıtımı için Microsoft Defender'ı ayarlama

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Uç Nokta için Defender'ın Dağıtımı üç aşamalı bir işlemdir:

|[![dağıtım aşaması - hazırlama.](images/phase-diagrams/prepare.png)](prepare-deployment.md)<br>[Aşama 1: Hazırlama](prepare-deployment.md) | ![dağıtım aşaması - kurulum](images/phase-diagrams/setup.png)<br>Aşama 2: Kurulum | [![dağıtım aşaması - ekleme](images/phase-diagrams/onboard.png)](onboarding.md)<br>[Aşama 3: Ekleme](onboarding.md)|
|---|---|---|
||*Buradasınız!*||

Şu anda ayarlama aşamasındayız.

Bu dağıtım senaryosunda, aşağıdaki adımlarda size yol kılavuz olacak:

- Lisans doğrulama
- Kiracı yapılandırması
- Ağ yapılandırması

> [!NOTE]
> Bu senaryo, size tipik bir dağıtımda yol gösterme amacıyla, yalnızca genel dağıtım Microsoft Endpoint Configuration Manager. Uç Nokta için Defender diğer ekleme araçlarının kullanımını destekler, ancak dağıtım kılavuzunda bu senaryoları desteklemez. Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender'a cihazları ekleme](onboard-configure.md).

## <a name="check-license-state"></a>Lisans durumunu denetleme

Lisans durumunu denetleme ve uygun şekilde sağ isteyip almadıyseniz, yönetim merkezi aracılığıyla veya Microsoft Azure **yapılabilir**.

1. Lisanslarınızı görüntülemek için Lisanslar **portalına Microsoft Azure gidin** ve lisans Microsoft Azure [bölümüne gidin](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products).

   ![Azure Lisanslama sayfasının resmi.](images/atp-licensing-azure-portal.png)

1. Alternatif olarak, yönetim merkezinde Fatura Abonelikleri'ne **gidin**\>.

    Ekranda, sağlanan tüm lisansları ve onların geçerli durumunu **görürsünüz**.

    ![Fatura lisanslarının resmi.](images/atp-billing-subscriptions.png)

## <a name="cloud-service-provider-validation"></a>Bulut Hizmet Sağlayıcısı doğrulaması

Hangi lisansların şirketine sağlandıklarına erişmek ve lisansların durumunu kontrol etmek için yönetim merkezine gidin.

1. İş Ortağı **portalında**, Hizmetleri **yönet'i seçin ve > Office 365**.

2. İş ortağı **portalı bağlantısına** tıklamak adına **Yönetici seçeneğini açar** ve müşteri yönetim merkezine erişmenizi sağlar.

   ![O365 yönetim portalı resmi.](images/atp-O365-admin-portal-customer.png)

## <a name="tenant-configuration"></a>Kiracı Yapılandırması

Uç Nokta için Microsoft Defender'a ekleme kolaydır. Gezinti menüsünden, Uç Noktalar bölümünün altındaki herhangi bir öğeyi ya da ekleme Microsoft 365 Defender için Olay, Avlama, İşlem merkezi veya Tehdit Analizi gibi herhangi bir uygulama özelliğini seçin.

Web tarayıcısında, Site <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Portalı'Microsoft 365 Defender gidin</a>.

## <a name="data-center-location"></a>Veri merkezi konumu
Uç Nokta için Microsoft Defender verileri, kullanıcı tarafından [kullanılan konumda depolar ve Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable). Microsoft 365 Defender henüz açmamışsa, Uç Nokta için Microsoft Defender'a ekleme Microsoft 365 Defender'i de açılır ve etkin veri merkezi güvenlik hizmetlerinin konumu temel alarak yeni bir veri merkezi Microsoft 365 seçilir. Seçili veri merkezi konumu ekranda gösterilir.

## <a name="network-configuration"></a>Ağ yapılandırması

Kuruluş, İnternet'e erişmek için proxy kullanmak üzere uç noktaların gerekli olmadığını fark etmese de bu bölümü atlayabilirsiniz.

Uç nokta algılayıcısı için Microsoft Defender, algılayıcı verilerini bildirmesi ve Uç nokta hizmeti için Microsoft Defender ile iletişim kurması için Microsoft Windows HTTP (WinHTTP) gerektirir. Yerleşik Uç Nokta algılayıcısı için Microsoft Defender LocalSystem hesabını kullanarak sistem bağlamında çalışır. Algılayıcı, Uç nokta bulut Windows Microsoft Defender ile iletişimi etkinleştirmek için Microsoft Windows HTTP Hizmetleri (WinHTTP) kullanır. WinHTTP yapılandırma ayarı, Windows Internet (WinINet) internet gözatma proxy ayarlarından bağımsızdır ve yalnızca aşağıdaki bulma yöntemlerini kullanarak bir proxy sunucusu keşfedebilirsiniz:

- **Otomatik Bulma yöntemleri**:
  - Saydam ara sunucu
  - Web Proxy Otomatik Bulma Protokolü (WPAD)

  Ağ topolojisinde Saydam ara sunucu veya WPAD uygulanmışsa, özel yapılandırma ayarlarına gerek yoktur. Proxy'de Uç Nokta URL dışlamaları için Microsoft Defender hakkında daha fazla bilgi için, bu belgenin URL izin listesine yönelik Ara Sunucu Hizmeti [URL'leri](production-deployment.md#proxy-service-urls) bölümüne veya Cihaz ara sunucusu ve İnternet bağlantısı ayarlarını [yapılandırma'ya bakın](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

- **El ile statik ara sunucu yapılandırması**:
  - Kayıt defteri tabanlı yapılandırma
  - Netsh komutu kullanılarak yapılandırılan WinHTTP

    Kararlı bir topolojide yalnızca masaüstleri için uygundur (örneğin: aynı proxy arkasında şirket ağının bir masaüstü).

### <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>Kayıt defteri tabanlı statik proxy'yi kullanarak proxy sunucusunu el ile yapılandırma

Bir bilgisayarın Internet'e bağlanmasına izin verilmediğini varsa, tanılama verilerini yalnızca Uç Nokta algılayıcısı için Microsoft Defender'ın rapor etmesine ve Uç nokta hizmetleri için Microsoft Defender ile iletişim kurmasına izin vermek için kayıt defteri tabanlı statik ara sunucu yapılandırın. Statik ara sunucu Grup İlkesi (GP) aracılığıyla yapılandırılabilir. Grup ilkesi şu altında bulunabilir:

- Yönetim Şablonları Windows \> Bileşenleri \> Veri Toplama ve Önizleme Derlemeleri \> Bağlı Kullanıcı Deneyimi ve Telemetri Hizmeti için Kimliği Doğrulanmış Ara Sunucu kullanımını yapılandırma
- Etkin olarak ayarlayın **ve Kimliği** Doğrulanmış Proxy **kullanımını devre dışı bırak'ı seçin**

1. Grup İlkesi Yönetim Konsolu'nu açın.
2. Kuruluş uygulamalarına göre bir ilke oluşturun veya var olan bir ilkeyi düzenleyin.
3. Grup İlkesi'yi düzenleyin ve Bağlı Kullanıcı Deneyimi **ve Telemetri Hizmeti Windows \> \> Bileşenleri Veri Toplama ve Önizleme Derlemeleri için Kimliği Doğrulanmış Ara Sunucu kullanımını yapılandırmak için Yönetim Şablonları'ne gidin.\>**

   ![Grup İlkesi yapılandırmasının resmi.](images/atp-gpo-proxy1.png)

4. **Etkin'i seçin**.
5. Kimliği **Doğrulanmış Proxy kullanımını devre dışı bırak'ı seçin**.
6. Bileşenler Veri **Toplama ve Önizleme \> Windows Bağlı \> \> kullanıcı deneyimlerini ve telemetrisi yapılandırma yönetim şablonları bağlantısına gidin**.

    ![Grup İlkesi yapılandırma ayarının resmi.](images/atp-gpo-proxy2.png)

7. **Etkin'i seçin**.
8. **Proxy Sunucu Adı'nın girin**.

İlke, kayıt defteri anahtarının `TelemetryProxyServer` REG_SZ olarak ve `DisableEnterpriseAuthProxy` REG_DWORD olarak iki kayıt defteri değeri ayarlar `HKLM\Software\Policies\Microsoft\Windows\DataCollection`.

Kayıt defteri değeri `TelemetryProxyServer` aşağıdaki dize biçimini alır:

```text
<server name or ip>:<port>
```

Örneğin: 10.0.0.6:8080

Kayıt defteri değeri `DisableEnterpriseAuthProxy` 1 olarak ayar gerekir.

### <a name="configure-the-proxy-server-manually-using-netsh-command"></a>Netsh komutunu kullanarak proxy sunucusunu el ile yapılandırma

Sistem çapında bir statik ara sunucu yapılandırmak için netsh kullanın.

> [!NOTE]
>
> - Bu da varsayılan ara sunucuyla WinHTTP Windows hizmetleri dahil olmak üzere tüm uygulamaları etkiler.
> - Topolojisi değişen dizüstü bilgisayarlar (örneğin: ofisten ev'e) netsh ile düzgün çalışmayan dizüstü bilgisayarlar. Kayıt defteri tabanlı statik ara sunucu yapılandırmasını kullanın.

1. Yükseltilmiş bir komut satırı açın:
    1. **Başlat'a gidin** ve **cmd yazın**.
    1. Komut istemi'ne **sağ tıklayın ve** Yönetici olarak **çalıştır'ı seçin**.

2. Aşağıdaki komutu girin ve Enter tuşuna **basın**:

   ```PowerShell
   netsh winhttp set proxy <proxy>:<port>
   ```

   Örneğin: netsh winhttp set proxy 10.0.0.6:8080

### <a name="proxy-configuration-for-down-level-devices"></a>Alt düzey cihazlar için Proxy Yapılandırması

Down-Level cihazları Windows 7 SP1 ve Windows 8.1 iş istasyonlarının yanı sıra Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 ve Windows Server 2016'in Windows'den önceki sürümlerini içerir  Sunucu CB 1803. Bu işletim sistemleri ara sunucu, uç noktadan Azure'a olan iletişimi işlemek için Microsoft Yönetim Aracısı'nın bir parçası olarak yapılandırılmış olur. Bir proxy'nin bu cihazlarda nasıl yapılandırıldıkları hakkında bilgi için Microsoft Yönetim Aracısı Hızlı Dağıtım Kılavuzu'ne bakın.

### <a name="proxy-service-urls"></a>Ara Sunucu Hizmeti URL'leri

Url'lerde v20 içeren URL'lerin olması için, Windows 10 1803 veya Windows 11 cihaz olması gerekir. Örneğin, `us-v20.events.data.microsoft.com` yalnızca cihaz 1803 veya Windows 10 11 üzerinde ise Windows gerekir.

Bir ara sunucu veya güvenlik duvarı anonim trafiği engelliyorsa, Uç nokta algılayıcısı için Microsoft Defender sistem bağlamından bağlanıyorsa, listelenen URL'lerde anonim trafiğin izin verildiğinden emin olun.

Aşağıdaki indirilebilir elektronik tablo, ağ bağlantı kurabilirsiniz ve bu hizmetlerle ilişkilendirilmiş URL'leri listeler. Bu URL'lere erişimi reddedecek güvenlik duvarı veya ağ filtreleme kuralları olmadığını onaylar veya özel olarak onlar için *bir izin verme* kuralı oluşturmanız gerekebilir.

<br>

****


|Etki alanı listesinin elektronik tablosu| Açıklama|
|---|---|
|Ticari müşteriler için Uç Nokta URL listesi için Microsoft Defender | Ticari müşteriler için hizmet konumları, coğrafi konumlar ve işletim sistemi için belirli DNS kayıtlarının elektronik tablosu. <p> [Elektronik tabloyu buradan indirin.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Gov/GCC/DoD müşterileri için Uç nokta URL listesi için Microsoft Defender| Gov/GCC/DoD müşterileri için hizmet konumları, coğrafi konumlar ve işletim sistemi için belirli DNS kayıtlarının elektronik tablosu. <p> [Elektronik tabloyu buradan indirin.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)
|

## <a name="next-step"></a>Sonraki adım

![**Aşama 3: Ekleme**.](images/onboard.png) <br> [Aşama 3: Ekleme](onboarding.md): Uç nokta hizmeti için Microsoft Defender'ın algılayıcı verilerini alsını için cihazları hizmete ekleme.
