---
title: Dağıtım Uç Nokta için Microsoft Defender ayarlama
description: Uç Nokta için Microsoft Defender için dağıtımın nasıl ayar Uç Nokta için Microsoft Defender
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
ms.openlocfilehash: e1fbfdaa71cc57a7797a2b95c96a56abba4fcc40
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/29/2022
ms.locfileid: "64506999"
---
# <a name="set-up-microsoft-defender-for-endpoint-deployment"></a>Dağıtım Uç Nokta için Microsoft Defender ayarlama

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Uç Nokta için Defender'ın Dağıtımı üç aşamalı bir işlemdir:

|[![dağıtım aşaması - hazırlama.](images/phase-diagrams/prepare.png#lightbox)](prepare-deployment.md)<br>[Aşama 1: Hazırlama](prepare-deployment.md) | ![dağıtım aşaması - kurulum](images/phase-diagrams/setup.png#lightbox)<br>Aşama 2: Kurulum | [![dağıtım aşaması - ekleme](images/phase-diagrams/onboard.png#lightbox)](onboarding.md)<br>[Aşama 3: Ekleme](onboarding.md)|
|---|---|---|
||*Buradasınız!*||

Şu anda ayarlama aşamasındayız.

Bu dağıtım senaryosunda, aşağıdaki adımlarda size yol kılavuz olacak:

- Lisans doğrulama
- Kiracı yapılandırması
- Ağ yapılandırması

> [!NOTE]
> Bu senaryo, size tipik bir dağıtımda yol gösterme amacıyla, yalnızca genel dağıtım Microsoft Endpoint Configuration Manager. Uç Nokta için Defender diğer ekleme araçlarının kullanımını destekler, ancak dağıtım kılavuzunda bu senaryoları desteklemez. Daha fazla bilgi için bkz[. Cihaz ekleme Uç Nokta için Microsoft Defender](onboard-configure.md).

## <a name="check-license-state"></a>Lisans durumunu denetleme

Lisans durumunu denetleme ve uygun şekilde sağ isteyip almadıyseniz, yönetim merkezi aracılığıyla veya Microsoft Azure **yapılabilir**.

1. Lisanslarınızı görüntülemek için Lisanslar **portalına Microsoft Azure gidin** ve lisans Microsoft Azure [bölümüne gidin](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products).

   :::image type="content" source="images/atp-licensing-azure-portal.png" alt-text="Azure Lisans sayfası" lightbox="images/atp-licensing-azure-portal.png":::

1. Alternatif olarak, yönetim merkezinde Fatura Abonelikleri'ne **gidin**\>.

    Ekranda, sağlanan tüm lisansları ve onların geçerli durumunu **görürsünüz**.

    :::image type="content" source="images/atp-billing-subscriptions.png" alt-text="Fatura lisansları sayfası" lightbox="images/atp-billing-subscriptions.png":::

## <a name="cloud-service-provider-validation"></a>Bulut Hizmet Sağlayıcısı doğrulaması

Hangi lisansların şirketine sağlandıklarına erişmek ve lisansların durumunu kontrol etmek için yönetim merkezine gidin.

1. İş Ortağı **portalında**, Hizmetleri **yönet'i seçin ve > Office 365**.

2. İş ortağı **portalı bağlantısına** tıklamak adına **Yönetici seçeneğini açar** ve müşteri yönetim merkezine erişmenizi sağlar.

   :::image type="content" source="images/atp-O365-admin-portal-customer.png" alt-text="Office 365 yönetim portalı" lightbox="images/atp-O365-admin-portal-customer.png":::

## <a name="tenant-configuration"></a>Kiracı Yapılandırması

Uç Nokta için Microsoft Defender kolayca işe Uç Nokta için Microsoft Defender. Gezinti menüsünden, Uç Noktalar bölümünün altındaki herhangi bir öğeyi ya da ekleme Microsoft 365 Defender için Olay, Avlama, İşlem merkezi veya Tehdit Analizi gibi herhangi bir uygulama özelliğini seçin.

Web tarayıcısında, Site <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Portalı'Microsoft 365 Defender gidin</a>.

## <a name="data-center-location"></a>Veri merkezi konumu
Uç Nokta için Microsoft Defender verileri, kullanıcı tarafından kullanılan [konumda depolar ve Microsoft 365 Defender](/microsoft-365/security/defender/m365d-enable). Microsoft 365 Defender henüz açmamışsa Uç Nokta için Microsoft Defender'e ekleme Microsoft 365 Defender'i de açılır ve etkin verilerin konumu temel alarak yeni bir veri merkezi konumu Microsoft 365  güvenlik hizmetlerini sağlar. Seçili veri merkezi konumu ekranda gösterilir.

## <a name="network-configuration"></a>Ağ yapılandırması

Kuruluş, İnternet'e erişmek için proxy kullanmak üzere uç noktaların gerekli olmadığını fark etmese de bu bölümü atlayabilirsiniz.

En Uç Nokta için Microsoft Defender algılayıcısı, algılayıcı verilerini rapor etmek ve bu hizmetle iletişim kurmak için Microsoft Windows HTTP (WinHTTP Uç Nokta için Microsoft Defender gerektirir. Yerleşik Uç Nokta için Microsoft Defender algılayıcısı LocalSystem hesabını kullanarak sistem bağlamında çalışır. Algılayıcı, bulut hizmetiyle Windows sağlamak için Microsoft HTTP Hizmetleri (WinHTTP Uç Nokta için Microsoft Defender kullanır. WinHTTP yapılandırma ayarı, Windows Internet (WinINet) internet gözatma proxy ayarlarından bağımsızdır ve yalnızca aşağıdaki bulma yöntemlerini kullanarak bir proxy sunucusu keşfedebilirsiniz:

- **Otomatik Bulma yöntemleri**:
  - Saydam ara sunucu
  - Web Proxy Otomatik Bulma Protokolü (WPAD)

  Ağ topolojisinde Saydam ara sunucu veya WPAD uygulanmışsa, özel yapılandırma ayarlarına gerek yoktur. Proxy'Uç Nokta için Microsoft Defender URL dışlamaları hakkında daha fazla bilgi için, bu belgenin URL izin listesine yönelik Ara Sunucu Hizmeti [URL'leri](production-deployment.md#proxy-service-urls) bölümüne veya Cihaz ara sunucusu ve İnternet bağlantısı ayarlarını [yapılandırma'ya bakın](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server).

- **El ile statik ara sunucu yapılandırması**:
  - Kayıt defteri tabanlı yapılandırma
  - Netsh komutu kullanılarak yapılandırılan WinHTTP

    Kararlı bir topolojide yalnızca masaüstleri için uygundur (örneğin: aynı proxy arkasında şirket ağının bir masaüstü).

### <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>Kayıt defteri tabanlı statik proxy'yi kullanarak proxy sunucusunu el ile yapılandırma

Bilgisayarın Internet'e bağlanmasına izin verilmediğini varsa, yalnızca Uç Nokta için Microsoft Defender algılayıcısına tanılama verilerini bildirmesine ve Uç Nokta için Microsoft Defender hizmetleriyle iletişim kurmasına izin vermek için kayıt defteri tabanlı statik ara sunucu yapılandırabilirsiniz. Statik ara sunucu, Genel Grup ilkesi (GP) aracılığıyla yapılandırılabilir. Grup ilkesi şu altında bulunabilir:

- Yönetim Şablonları Windows \> Bileşenleri \> Veri Toplama ve Önizleme Derlemeleri \> Bağlı Kullanıcı Deneyimi ve Telemetri Hizmeti için Kimliği Doğrulanmış Ara Sunucu kullanımını yapılandırma
- Etkin olarak ayarlayın **ve Kimliği** Doğrulanmış Proxy **kullanımını devre dışı bırak'ı seçin**

1. Grup İlkesi Yönetim Konsolu'nu açın.
2. Kuruluş uygulamalarına göre bir ilke oluşturun veya var olan bir ilkeyi düzenleyin.
3. Bağlı grup ilkesi Deneyimi ve **Telemetri Hizmeti Windows \> \> Bileşenleri Veri Toplama ve Önizleme Derlemeleri için Kimliği Doğrulanmış Ara Sunucu kullanımını yapılandırmak için Yönetim Şablonları'nın ayarlarını düzenleyin.\>**

   :::image type="content" source="images/atp-gpo-proxy1.png" alt-text="Kullanım ilkesi yapılandırmasıyla ilgili seçenekler" lightbox="images/atp-gpo-proxy1.png":::

4. **Etkin'i seçin**.
5. Kimliği **Doğrulanmış Proxy kullanımını devre dışı bırak'ı seçin**.
6. Bileşenler Veri **Toplama ve Önizleme \> Windows Bağlı \> \> kullanıcı deneyimlerini ve telemetrisi yapılandırma yönetim şablonları bağlantısına gidin**.

   :::image type="content" source="images/atp-gpo-proxy2.png" alt-text="Bağlı kullanıcı deneyiminin ve telemetriye ilişkin yapılandırmayla ilgili seçenekler" lightbox="images/atp-gpo-proxy2.png":::

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

Url'lerde v20 içeren URL'lerin olması için, yalnızca Windows 10 sürüm 1803 veya Windows 11 gereklidir. Örneğin, `us-v20.events.data.microsoft.com` cihaz yalnızca 1803 veya Windows 10 üzerinde ise Windows 11.

Bir ara sunucu veya güvenlik duvarı anonim trafiği engelliyorsa, Uç Nokta için Microsoft Defender algılayıcının sistem bağlamından bağlanmasına izin verildiğinden, anonim trafiğin listelenen URL'lerde izin verildiğinden emin olun.

Aşağıdaki indirilebilir elektronik tablo, ağ bağlantı kurabilirsiniz ve bu hizmetlerle ilişkilendirilmiş URL'leri listeler. Bu URL'lere erişimi reddedecek güvenlik duvarı veya ağ filtreleme kuralları olmadığını onaylar veya özel olarak onlar için *bir izin verme* kuralı oluşturmanız gerekebilir.

<br>

****


|Etki alanı listesinin elektronik tablosu| Açıklama|
|---|---|
|Uç Nokta için Microsoft Defender müşteriler için bir URL listesi| Ticari müşteriler için hizmet konumları, coğrafi konumlar ve işletim sistemi için belirli DNS kayıtlarının elektronik tablosu. <p> [Elektronik tabloyu buradan indirin.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Uç Nokta için Microsoft Defender Gov/GCC/DoD için URL listesi | Gov/GCC/DoD müşterileri için hizmet konumları, coğrafi konumlar ve işletim sistemi için belirli DNS kayıtlarının elektronik tablosu. <p> [Elektronik tabloyu buradan indirin.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

## <a name="next-step"></a>Sonraki adım

[![**Aşama 3: Ekleme**.](images/onboard.png#lightbox)] <br> [Aşama 3: Ekleme](onboarding.md): Cihaz, cihaz servise Uç Nokta için Microsoft Defender bu cihazlardan algılayıcı verileri alsını sağlar.
