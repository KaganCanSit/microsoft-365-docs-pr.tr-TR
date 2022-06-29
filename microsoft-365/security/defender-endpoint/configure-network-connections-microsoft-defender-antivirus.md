---
title: Microsoft Defender Virüsten Koruma ağ bağlantılarını yapılandırın ve doğrulayın
description: Microsoft Defender Virüsten Koruma bulut koruma hizmetiyle bağlantınızı yapılandırın ve test edin.
keywords: virüsten koruma, Microsoft Defender Virüsten Koruma, kötü amaçlı yazılımdan koruma, güvenlik, defender, bulut, saldırganlık, koruma düzeyi
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.topic: article
ms.custom: nextgen
ms.date: 06/28/2022
ms.reviewer: mkaminska; pahuijbr
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: e06b2a37f45ccf0febc35e31d33ece55c03e3303
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66492070"
---
# <a name="configure-and-validate-microsoft-defender-antivirus-network-connections"></a>Microsoft Defender Virüsten Koruma ağ bağlantılarını yapılandırın ve doğrulayın

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Microsoft Defender Virüsten Koruma'nın bulut tabanlı korumasının düzgün çalıştığından emin olmak için güvenlik ekibinizin ağınızı uç noktalarınızla belirli Microsoft sunucuları arasında bağlantılara izin verecek şekilde yapılandırması gerekir. Bu makalede, güvenlik duvarı kurallarını kullanmak için izin verilmesi gereken bağlantılar listelenir. Ayrıca bağlantınızı doğrulamaya yönelik yönergeler de sağlar. Korumanızı doğru şekilde yapılandırmak, bulut tabanlı koruma hizmetlerinizden en iyi değeri almanızı sağlar.

> [!IMPORTANT]
> Bu makale, yalnızca Microsoft Defender Virüsten Koruma için ağ bağlantılarını yapılandırma hakkında bilgi içerir. Uç Nokta için Microsoft Defender kullanıyorsanız (Microsoft Defender Virüsten Koruma da dahil), bkz. [Uç Nokta için Defender için cihaz ara sunucusu ve İnternet bağlantısı ayarlarını yapılandırma](configure-proxy-internet.md).


> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

## <a name="allow-connections-to-the-microsoft-defender-antivirus-cloud-service"></a>Microsoft Defender Virüsten Koruma bulut hizmeti bağlantılarına izin ver

Microsoft Defender Virüsten Koruma bulut hizmeti uç noktalarınız için hızlı ve güçlü koruma sağlar. Bulut tabanlı koruma hizmetini etkinleştirmek isteğe bağlıdır. Uç noktalarınızdaki ve ağınızdaki kötü amaçlı yazılımlara karşı önemli koruma sağladığından Microsoft Defender Virüsten Koruma bulut hizmeti önerilir. Daha fazla bilgi için bkz. Windows Güvenliği uygulamasında hizmeti Intune, Microsoft Endpoint Configuration Manager, grup ilkesi, PowerShell cmdlet'leri veya tek tek istemcilerle etkinleştirmek için [bulut tabanlı korumayı etkinleştirme](enable-cloud-protection-microsoft-defender-antivirus.md).

Hizmeti etkinleştirdikten sonra ağınızı veya güvenlik duvarınızı ağ ile uç noktalarınız arasındaki bağlantılara izin verecek şekilde yapılandırmanız gerekir. Korumanız bir bulut hizmeti olduğundan bilgisayarların İnternet'e ve Microsoft bulut hizmetlerine erişmesi gerekir. URL'yi `*.blob.core.windows.net` herhangi bir ağ incelemesinin dışında tutmayın.

> [!NOTE]
> Microsoft Defender Virüsten Koruma bulut hizmeti, ağınıza ve uç noktalarınıza güncelleştirilmiş koruma sağlar. Bulut hizmeti yalnızca bulutta depolanan dosyalarınız için koruma olarak değerlendirilmemelidir; Bunun yerine bulut hizmeti, geleneksel Güvenlik bilgileri güncelleştirmelerinden daha hızlı bir hızda uç noktalarınıza koruma sağlamak için dağıtılmış kaynakları ve makine öğrenmesini kullanır.

## <a name="services-and-urls"></a>Hizmetler ve URL'ler

Bu bölümdeki tabloda hizmetler ve ilişkili web sitesi adresleri (URL'ler) listelenmektedir.

Bu URL'lere erişimi reddeden güvenlik duvarı veya ağ filtreleme kuralı olmadığından emin olun. Aksi takdirde, özellikle bu URL'ler için bir izin verme kuralı oluşturmanız gerekir (URL `*.blob.core.windows.net`hariç). Aşağıdaki tablodaki URL'ler iletişim için 443 numaralı bağlantı noktasını kullanır.

<br/><br/>

|Hizmet ve açıklama|URL|
|---|---|
|Microsoft Defender Virüsten Koruma bulut tabanlı koruma hizmeti, Microsoft Active Protection Service (MAPS) olarak adlandırılır.<p> Microsoft Defender Virüsten Koruma, bulut tabanlı koruma sağlamak için MAPS hizmetini kullanır.|`*.wdcp.microsoft.com` <p> `*.wdcpalt.microsoft.com` <p> `*.wd.microsoft.com`|
|Microsoft Update Hizmeti (MU) ve Windows Update Hizmeti (WU) <p>Bu hizmetler güvenlik bilgilerine ve ürün güncelleştirmelerine izin verir.|`*.update.microsoft.com` <p> `*.delivery.mp.microsoft.com`<p> `*.windowsupdate.com` <p> Daha fazla bilgi için bkz[. Windows Update için bağlantı uç noktaları](/windows/privacy/manage-windows-1709-endpoints#windows-update)|
|Güvenlik bilgileri güncelleştirmeleri Alternatif İndirme Konumu (ADL)<p>Bu, yüklü Güvenlik zekası güncel değilse (Yedi veya daha fazla gün geride) Microsoft Defender Virüsten Koruma Güvenlik bilgileri güncelleştirmeleri için alternatif bir konumdur.|`*.download.microsoft.com` <p> `*.download.windowsupdate.com`<p>  `go.microsoft.com`<p> `https://www.microsoft.com/security/encyclopedia/adlpackages.aspx` <p> `https://definitionupdates.microsoft.com/download/DefinitionUpdates/` <p> `https://fe3cr.delivery.mp.microsoft.com/ClientWebService/client.asmx`|
|Kötü amaçlı yazılım gönderme depolama alanı <p>Bu, Gönderme formu veya otomatik örnek gönderimi aracılığıyla Microsoft'a gönderilen dosyalar için bir karşıya yükleme konumudur.|`ussus1eastprod.blob.core.windows.net` <p> `ussus2eastprod.blob.core.windows.net` <p> `ussus3eastprod.blob.core.windows.net` <p> `ussus4eastprod.blob.core.windows.net` <p> `wsus1eastprod.blob.core.windows.net` <p> `wsus2eastprod.blob.core.windows.net` <p> `ussus1westprod.blob.core.windows.net` <p> `ussus2westprod.blob.core.windows.net` <p> `ussus3westprod.blob.core.windows.net` <p> `ussus4westprod.blob.core.windows.net` <p> `wsus1westprod.blob.core.windows.net` <p> `wsus2westprod.blob.core.windows.net` <p> `usseu1northprod.blob.core.windows.net` <p> `wseu1northprod.blob.core.windows.net` <p> `usseu1westprod.blob.core.windows.net` <p> `wseu1westprod.blob.core.windows.net` <p> `ussuk1southprod.blob.core.windows.net` <p> `wsuk1southprod.blob.core.windows.net` <p> `ussuk1westprod.blob.core.windows.net` <p> `wsuk1westprod.blob.core.windows.net`|
|Sertifika İptal Listesi (CRL) <p> Windows, CRL'yi güncelleştirmek için MAPS'e SSL bağlantısı oluştururken bu listeyi kullanır.|`http://www.microsoft.com/pkiops/crl/` <p> `http://www.microsoft.com/pkiops/certs` <p> `http://crl.microsoft.com/pki/crl/products` <p> `http://www.microsoft.com/pki/certs`|
|Sembol Deposu <p>Microsoft Defender Virüsten Koruma, düzeltme akışları sırasında bazı kritik dosyaları geri yüklemek için Sembol Deposu'nı kullanır.|`https://msdl.microsoft.com/download/symbols`|
|Evrensel GDPR İstemcisi <p> Windows, istemci tanılama verilerini göndermek için bu istemciyi kullanır. <p> Microsoft Defender Virüsten Koruma, ürün kalitesi ve izleme amacıyla Genel Veri Koruma Yönetmeliği'ne sahiptir.|Güncelleştirme, bildirimleri indirmek ve aşağıdaki DNS uç noktalarını kullanan tanılama verilerini Microsoft'a yüklemek için SSL (TCP Bağlantı Noktası 443) kullanır: <p> `vortex-win.data.microsoft.com` <p> `settings-win.data.microsoft.com`|


## <a name="validate-connections-between-your-network-and-the-cloud"></a>Ağınız ile bulut arasındaki bağlantıları doğrulama

Listelenen URL'lere izin verdikten sonra Microsoft Defender Virüsten Koruma bulut hizmetine bağlı olup olmadığınızı test edin. Tam olarak korunduğunuzdan emin olmak için URL'lerin doğru şekilde raporlanıp bilgi alınıp alınamediğini test edin.

### <a name="use-the-cmdline-tool-to-validate-cloud-delivered-protection"></a>Bulut tabanlı korumayı doğrulamak için cmdline aracını kullanma

Ağınızın Microsoft Defender Virüsten Koruma bulut hizmetiyle iletişim kurabildiğini doğrulamak için Microsoft Defender Virüsten Koruma komut satırı yardımcı programıyla (`mpcmdrun.exe`) aşağıdaki bağımsız değişkeni kullanın:

```console
"%ProgramFiles%\Windows Defender\MpCmdRun.exe" -ValidateMapsConnection
```

> [!NOTE]
> Yönetici olarak Komut İstemi'ni açın. **Başlat** menüsünde öğeye sağ tıklayın, **Yönetici olarak çalıştır'a** tıklayın ve izin isteminde **Evet'e** tıklayın. Bu komut yalnızca Windows 10, sürüm 1703 veya üzeri ya da Windows 11 üzerinde çalışır.

Daha fazla bilgi için bkz. [mpcmdrun.exe komut satırı aracıyla Microsoft Defender Virüsten Koruma'yı yönetme](command-line-arguments-microsoft-defender-antivirus.md).

### <a name="attempt-to-download-a-fake-malware-file-from-microsoft"></a>Microsoft'tan sahte kötü amaçlı yazılım dosyası indirme girişimi

Buluta düzgün bir şekilde bağlıysanız Microsoft Defender Virüsten Koruma'nın algılayıp engelleyecekleri örnek bir dosyayı indirebilirsiniz. Dosyayı indirmek için ziyaret edin [https://aka.ms/ioavtest1](https://aka.ms/ioavtest1) .

> [!NOTE]
> İndirilen dosya tam olarak kötü amaçlı yazılım değildir. Buluta düzgün bir şekilde bağlanıp bağlanmadığınızı test etmek için tasarlanmış sahte bir dosyadır.

Düzgün bir şekilde bağlandıysanız Microsoft Defender Virüsten Koruma bildirimini görürsünüz.

Microsoft Edge kullanıyorsanız bir bildirim iletisi de görürsünüz:

:::image type="content" source="../../media/wdav-bafs-edge.png" alt-text="Edge'de kötü amaçlı yazılım bulunduğuna ilişkin bildirim" lightbox="../../media/wdav-bafs-edge.png":::

Internet Explorer kullanıyorsanız benzer bir ileti oluşur:

:::image type="content" source="../../media/wdav-bafs-ie.png" alt-text="Kötü amaçlı yazılımların bulunduğuna ilişkin Microsoft Defender AV bildirimi" lightbox="../../media/wdav-bafs-ie.png":::

#### <a name="view-the-fake-malware-detection-in-your-windows-security-app"></a>Windows Güvenliği uygulamanızda sahte kötü amaçlı yazılım algılamasını görüntüleme

1. Görev çubuğunuzda Kalkan simgesini seçin, **Windows Güvenliği** uygulamasını açın. Veya *Güvenlik* için **Başlat'ı** arayın.

2. **Virüs & tehdit koruması**'& ve ardından **Koruma geçmişi'ne** tıklayın.

3. **Karantinaya alınan tehditler bölümünde, algılanan** sahte kötü amaçlı yazılımları görmek için **Tam geçmişe bakın'ı** seçin.

   > [!NOTE]
   > sürüm 1703'ün önceki Windows 10 sürümleri farklı bir kullanıcı arabirimine sahiptir. [Windows Güvenliği uygulamasında Microsoft Defender Virüsten Koruma'ya](microsoft-defender-security-center-antivirus.md) bakın.

   Windows olay günlüğünde Windows Defender [istemci olay kimliği 1116](troubleshoot-microsoft-defender-antivirus.md) da gösterilir.

    > [!TIP]
    > Diğer platformlar için Antivirüs ile ilgili bilgi arıyorsanız bkz:
    > - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
    > - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
    > - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
    > - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
    > - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
    > - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
    > - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)


## <a name="see-also"></a>Ayrıca bkz.

- [Uç Nokta için Microsoft Defender için cihaz ara sunucusu ve İnternet bağlantısı ayarlarını yapılandırma](configure-proxy-internet.md)
- [Microsoft Defender Virüsten Koruma'nın yapılandırılması ve yönetilmesi için grup ilkesi ayarlarını kullanma](use-group-policy-microsoft-defender-antivirus.md)
- [Microsoft Active Protection Services uç noktasında önemli değişiklikler](https://techcommunity.microsoft.com/t5/Configuration-Manager-Archive/Important-changes-to-Microsoft-Active-Protection-Service-MAPS/ba-p/274006) 
