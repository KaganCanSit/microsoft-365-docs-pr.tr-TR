---
title: Pertahanan Microsoft untuk Titik Akhir dağıtımı ayarlama
description: Pertahanan Microsoft untuk Titik Akhir için dağıtımı ayarlamayı öğrenin
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
ms.openlocfilehash: bae66223494d8de98737516cef1a2c407d7d1a6a
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783545"
---
# <a name="set-up-microsoft-defender-for-endpoint-deployment"></a>Pertahanan Microsoft untuk Titik Akhir dağıtımı ayarlama

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Pertahanan Microsoft untuk Titik Akhir mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Uç Nokta için Defender'ın dağıtılması üç aşamalı bir işlemdir:

|[![dağıtım aşaması - hazırlama.](images/phase-diagrams/prepare.png#lightbox)](prepare-deployment.md)<br>[Aşama 1: Hazırlık](prepare-deployment.md) | ![dağıtım aşaması - kurulum](images/phase-diagrams/setup.png#lightbox)<br>Aşama 2: Kurulum | [![dağıtım aşaması - ekleme](images/phase-diagrams/onboard.png#lightbox)](onboarding.md)<br>[Aşama 3: Katılım](onboarding.md)|
|---|---|---|
||*Buradasınız!*||

Şu anda kurulum aşamasındasınız.

Bu dağıtım senaryosunda aşağıdaki adımlarda size yol gösterilir:

- Lisans doğrulama
- Kiracı yapılandırması
- Ağ yapılandırması

> [!NOTE]
> Tipik bir dağıtımda size yol göstermek amacıyla, bu senaryo yalnızca Microsoft Endpoint Configuration Manager kullanımını kapsar. Uç Nokta için Defender diğer ekleme araçlarının kullanımını destekler ancak dağıtım kılavuzunda bu senaryoları kapsamaz. Daha fazla bilgi için bkz[. cihazları Pertahanan Microsoft untuk Titik Akhir ekleme](onboard-configure.md).

## <a name="check-license-state"></a>Lisans durumunu denetleme

Lisans durumunu ve doğru şekilde sağlanıp sağlanmadığını denetleme işlemi yönetim merkezi veya **Microsoft Azure portalı** üzerinden yapılabilir.

1. Lisanslarınızı görüntülemek için **Microsoft Azure portalına** gidin ve [Microsoft Azure portalı lisans bölümüne gidin](https://portal.azure.com/#blade/Microsoft_AAD_IAM/LicensesMenuBlade/Products).

   :::image type="content" source="images/atp-licensing-azure-portal.png" alt-text="Azure Lisanslama sayfası" lightbox="images/atp-licensing-azure-portal.png":::

1. Alternatif olarak, yönetim merkezinde **Faturalama** \> **Abonelikleri'ne** gidin.

    Ekranda sağlanan tüm lisansları ve geçerli **Durumlarını** görürsünüz.

    :::image type="content" source="images/atp-billing-subscriptions.png" alt-text="Faturalama lisansları sayfası" lightbox="images/atp-billing-subscriptions.png":::

## <a name="cloud-service-provider-validation"></a>Bulut Hizmeti Sağlayıcısı doğrulaması

Şirketinize sağlanan lisanslara erişmek ve lisansların durumunu denetlemek için yönetim merkezine gidin.

1. **İş ortağı portalından** **Hizmetleri > Office 365 yönet'i** seçin.

2. **İş ortağı portalı** bağlantısına tıklanması **, Yönetici adına** seçeneğini açar ve size müşteri yönetim merkezine erişim verir.

   :::image type="content" source="images/atp-O365-admin-portal-customer.png" alt-text="Office 365 yönetim portalı" lightbox="images/atp-O365-admin-portal-customer.png":::

## <a name="tenant-configuration"></a>Kiracı Yapılandırması

Pertahanan Microsoft untuk Titik Akhir eklemek kolaydır. Gezinti menüsünde Uç Noktalar bölümünden herhangi bir öğeyi veya ekleme işlemini başlatmak için Olaylar, Tehdit Avcılığı, İşlem merkezi veya Tehdit analizi gibi herhangi bir Microsoft 365 Defender özelliğini seçin.

Web tarayıcısından <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalına</a> gidin.

## <a name="data-center-location"></a>Veri merkezi konumu
Pertahanan Microsoft untuk Titik Akhir verileri [Microsoft 365 Defender tarafından kullanılan konumda](/microsoft-365/security/defender/m365d-enable) depolar ve işler. Microsoft 365 Defender henüz açılmadıysa, Pertahanan Microsoft untuk Titik Akhir'a ekleme işlemi de Microsoft 365 Defender açar ve etkin konumuna bağlı olarak yeni bir veri merkezi konumu otomatik olarak seçilir güvenlik hizmetlerini Microsoft 365. Seçili veri merkezi konumu ekranda gösterilir.

## <a name="network-configuration"></a>Ağ yapılandırması

Kuruluş, uç noktaların İnternet'e erişmek için Ara Sunucu kullanmasını gerektirmiyorsa bu bölümü atlayın.

Pertahanan Microsoft untuk Titik Akhir algılayıcısı, algılayıcı verilerini raporlamak ve Pertahanan Microsoft untuk Titik Akhir hizmetiyle iletişim kurmak için Microsoft Windows HTTP (WinHTTP) gerektirir. Ekli Pertahanan Microsoft untuk Titik Akhir algılayıcısı LocalSystem hesabını kullanarak sistem bağlamında çalışır. Algılayıcı, Pertahanan Microsoft untuk Titik Akhir bulut hizmetiyle iletişimi etkinleştirmek için Microsoft Windows HTTP Hizmetleri'ni (WinHTTP) kullanır. WinHTTP yapılandırma ayarı, Windows İnternet (WinINet) internet gözatma proxy ayarlarından bağımsızdır ve yalnızca aşağıdaki bulma yöntemlerini kullanarak bir ara sunucuyu bulabilir:

- **Otomatik bulma yöntemleri**:
  - Saydam ara sunucu
  - Web Proxy Otomatik Bulma Protokolü (WPAD)

  Ağ topolojisinde Saydam ara sunucu veya WPAD uygulanmışsa, özel yapılandırma ayarlarına gerek yoktur. Ara sunucudaki PERTAHANAN MICROSOFT UNTUK TITIK AKHIR URL dışlamaları hakkında daha fazla bilgi için, izin veren URL'ler listesi için bu belgedeki [Ara Sunucu Hizmeti URL'leri](production-deployment.md#proxy-service-urls) bölümüne veya [Cihaz ara sunucusu ve İnternet bağlantısı ayarlarını yapılandırma](configure-proxy-internet.md#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server) bölümüne bakın.

- **El ile statik proxy yapılandırması**:
  - Kayıt defteri tabanlı yapılandırma
  - netsh komutu kullanılarak yapılandırılan WinHTTP

    Yalnızca kararlı bir topolojideki masaüstleri için uygundur (örneğin: aynı proxy'nin arkasındaki şirket ağında bir masaüstü).

### <a name="configure-the-proxy-server-manually-using-a-registry-based-static-proxy"></a>Ara sunucuyu kayıt defteri tabanlı statik proxy kullanarak el ile yapılandırma

Bir bilgisayarın İnternet'e bağlanmasına izin verilmiyorsa, yalnızca Pertahanan Microsoft untuk Titik Akhir algılayıcısının tanılama verilerini raporlamasına ve Pertahanan Microsoft untuk Titik Akhir hizmetleriyle iletişim kurmasına izin verecek şekilde kayıt defteri tabanlı statik proxy yapılandırın. Statik proxy, grup ilkesi (GP) aracılığıyla yapılandırılabilir. Grup ilkesi aşağıdakiler altında bulunabilir:

- Yönetim Şablonları \> Windows Bileşenleri \> Veri Toplama ve Önizleme Derlemeleri \> Bağlı Kullanıcı Deneyimi ve Telemetri Hizmeti için Kimliği Doğrulanmış Proxy kullanımını yapılandırma
- **Etkin** olarak ayarlayın ve **Kimliği Doğrulanmış Proxy kullanımını devre dışı bırak'ı** seçin

1. Grup İlkesi Yönetim Konsolu'nu açın.
2. Kuruluş uygulamalarını temel alarak bir ilke oluşturun veya mevcut bir ilkeyi düzenleyin.
3. grup ilkesi düzenleyin ve **Yönetim Şablonları \> Windows Bileşenler \> Veri Toplama ve Önizleme Derlemeleri \> Bağlı Kullanıcı Deneyimi ve Telemetri Hizmeti için Kimliği Doğrulanmış Proxy kullanımını yapılandır'a** gidin.

   :::image type="content" source="images/atp-gpo-proxy1.png" alt-text="Kullanım ilkesinin yapılandırmasıyla ilgili seçenekler" lightbox="images/atp-gpo-proxy1.png":::

4. **Etkin'i** seçin.
5. **Kimliği Doğrulanmış Proxy kullanımını devre dışı bırak'ı** seçin.
6. **Yönetim Şablonları \> Windows Bileşenler \> Veri Toplama ve Önizleme Derlemeleri \> Bağlı kullanıcı deneyimlerini ve telemetrisini yapılandır'a** gidin.

   :::image type="content" source="images/atp-gpo-proxy2.png" alt-text="Bağlı kullanıcı deneyiminin ve telemetrinin yapılandırmasıyla ilgili seçenekler" lightbox="images/atp-gpo-proxy2.png":::

7. **Etkin'i** seçin.
8. **Ara Sunucu Adı'nı** girin.

İlke, iki kayıt defteri değerini `TelemetryProxyServer` REG_SZ ve `DisableEnterpriseAuthProxy` kayıt defteri anahtarı `HKLM\Software\Policies\Microsoft\Windows\DataCollection`altında REG_DWORD olarak ayarlar.

Kayıt defteri değeri `TelemetryProxyServer` aşağıdaki dize biçimini alır:

```text
<server name or ip>:<port>
```

Örneğin: 10.0.0.6:8080

Kayıt defteri değeri `DisableEnterpriseAuthProxy` 1 olarak ayarlanmalıdır.

### <a name="configure-the-proxy-server-manually-using-netsh-command"></a>Netsh komutunu kullanarak ara sunucuyu el ile yapılandırma

Sistem genelinde statik ara sunucuyu yapılandırmak için netsh kullanın.

> [!NOTE]
>
> - Bu, varsayılan proxy ile WinHTTP kullanan Windows hizmetleri de dahil olmak üzere tüm uygulamaları etkiler.
> - Topolojiyi değiştiren dizüstü bilgisayarlar (örneğin: ofisten eve) netsh ile arızalanır. Kayıt defteri tabanlı statik proxy yapılandırmasını kullanın.

1. Yükseltilmiş bir komut satırı açın:
    1. **Başlangıç'a** gidin ve **cmd** yazın.
    1. **Komut istemi'ne** sağ tıklayın ve **Yönetici olarak çalıştır'ı** seçin.

2. Aşağıdaki komutu girin ve **Enter tuşuna** basın:

   ```PowerShell
   netsh winhttp set proxy <proxy>:<port>
   ```

   Örneğin: netsh winhttp set proxy 10.0.0.6:8080

### <a name="proxy-configuration-for-down-level-devices"></a>Alt düzey cihazlar için Ara Sunucu Yapılandırması

Down-Level cihazlar Windows 7 SP1 ve Windows 8.1 iş istasyonlarının yanı sıra Windows Server 2008 R2 ve daha önce Microsoft Monitoring Agent kullanılarak eklenmiş olan diğer sunucu işletim sistemlerini içerir. Bu işletim sistemleri, uç noktadan Azure'a iletişimi işlemek için Microsoft Yönetim Aracısı'nın bir parçası olarak yapılandırılmış ara sunucuya sahip olacaktır. Bir proxy'nin bu cihazlarda nasıl yapılandırıldığı hakkında bilgi için Microsoft Yönetim Aracısı Hızlı Dağıtım Kılavuzu'na bakın.

### <a name="proxy-service-urls"></a>Proxy Hizmeti URL'leri

Bunlara v20 içeren URL'ler yalnızca Windows 10, sürüm 1803 veya Windows 11 cihazlarınız varsa gereklidir. Örneğin, `us-v20.events.data.microsoft.com` yalnızca cihaz Windows 10, sürüm 1803 veya Windows 11 ise gereklidir.

Pertahanan Microsoft untuk Titik Akhir algılayıcısı sistem bağlamından bağlandığından bir ara sunucu veya güvenlik duvarı anonim trafiği engelliyorsa, listelenen URL'lerde anonim trafiğe izin verildiğinden emin olun.

Aşağıdaki indirilebilir elektronik tablo, ağınızın bağlanabilmesi gereken hizmetleri ve bunların ilişkili URL'lerini listeler. Bu URL'lere erişimi reddedecek bir güvenlik duvarı veya ağ filtreleme kuralı olmadığından emin olun veya bunlar için özel olarak bir *izin verme* kuralı oluşturmanız gerekebilir.

<br>

****


|Etki alanları listesinin elektronik tablosu| Açıklama|
|---|---|
|Ticari müşteriler için Pertahanan Microsoft untuk Titik Akhir URL listesi| Ticari müşteriler için hizmet konumları, coğrafi konumlar ve işletim sistemi için belirli DNS kayıtlarının elektronik tablosu. <p> [Elektronik tabloyu buradan indirin.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Gov/GCC/DoD için Pertahanan Microsoft untuk Titik Akhir URL listesi | Gov/GCC/DoD müşterileri için hizmet konumları, coğrafi konumlar ve işletim sistemi için belirli DNS kayıtlarının elektronik tablosu. <p> [Elektronik tabloyu buradan indirin.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

## <a name="next-step"></a>Sonraki adım

[![**Aşama 3: Ekleme**.](images/onboard.png#lightbox)] <br> [3. Aşama: Ekleme](onboarding.md): Pertahanan Microsoft untuk Titik Akhir hizmetinin algılayıcı verilerini alabilmesi için cihazları hizmete ekleme.
