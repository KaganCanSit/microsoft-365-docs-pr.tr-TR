---
title: Ağ bağlantılarını yapılandırma Microsoft Defender Virüsten Koruma doğrulama
description: Microsoft Defender Virüsten Koruma bulut koruma hizmetiyle bağlantınızı yapılandırın ve test edin.
keywords: virüsten Microsoft Defender Virüsten Koruma, kötü amaçlı yazılımdan koruma, güvenlik, defender, bulut, saldırganlık, koruma düzeyi
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
ms.date: 02/03/2022
ms.reviewer: mkaminska; pahuijbr
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: f29cf5f77acd52a4ff3ccc8384f3c64861e48b64
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019473"
---
# <a name="configure-and-validate-microsoft-defender-antivirus-network-connections"></a>Ağ bağlantılarını yapılandırma Microsoft Defender Virüsten Koruma doğrulama

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Buluta Microsoft Defender Virüsten Koruma korumanın düzgün çalışması için, güvenlik ekibinin uç noktalarınız ve belirli Microsoft sunucuları arasında bağlantılara izin verecek şekilde anızı yapılandırması gerekir. Bu makalede, güvenlik duvarı kurallarını kullanmasına izin verilen bağlantılar listelemektedir. Ayrıca bağlantınızı doğrulama yönergeleri de sağlar. Korumanızı düzgün bir şekilde yapılandırmak, bulut teslimi koruma hizmetlerinden en iyi değeri alamanızı sağlar.

> [!IMPORTANT]
> Bu makale, yalnızca iş bağlantılarının ağ bağlantılarını yapılandırma Microsoft Defender Virüsten Koruma. Uç Nokta için Microsoft Defender kullanıyorsanız (uç nokta da Microsoft Defender Virüsten Koruma) bkz. Uç Nokta için Defender için cihaz ara sunucusunu ve [İnternet bağlantısı ayarlarını yapılandırma](configure-proxy-internet.md).


> [!NOTE]
> demo.wd.microsoft.com'daki Uç Nokta için Defender tanıtım sitesi kullanım dışıdır ve gelecekte kaldırılacaktır.

## <a name="allow-connections-to-the-microsoft-defender-antivirus-cloud-service"></a>Bulut hizmeti için Microsoft Defender Virüsten Koruma izin ver

Hızlı Microsoft Defender Virüsten Koruma hizmeti, uç noktalarınız için hızlı ve güçlü koruma sağlar. Bulut teslimi koruma hizmetini etkinleştirmek isteğe bağlıdır. Microsoft Defender Virüsten Koruma ve ağ üzerinde kötü amaçlı yazılımlara karşı önemli bir koruma sağladığı için bu bulut hizmetinin kullanılması önerilir. Daha fazla bilgi için bkz[](enable-cloud-protection-microsoft-defender-antivirus.md). Intune, Microsoft Endpoint Configuration Manager, Grup İlkesi, PowerShell cmdlet'leriyle veya Windows Güvenliği uygulamasındaki tek tek istemcilerle hizmeti etkinleştirmek için bulut teslimi korumasını etkinleştirme.

Hizmeti etkinleştirdikten sonra, ağ veya güvenlik duvarınızı ağ ile uç noktalarınız arasındaki bağlantılara izin verecek şekilde yapılandırmanız gerekir. Korumanız bir bulut hizmeti olduğundan, bilgisayarların İnternet erişimine sahip olması ve Microsoft bulut hizmetlerine erişmesi gerekir. URL'yi herhangi bir ağ `*.blob.core.windows.net` incelemesi dışında tutmakn.

> [!NOTE]
> Microsoft Defender Virüsten Koruma bulut hizmeti, ağ ve uç noktalarınız için güncelleştirilmiş koruma sağlar. Bulut hizmeti yalnızca bulutta depolanan dosyalarınız için koruma olarak kabul alınmamalıdır; bunun yerine bulut hizmeti, geleneksel Güvenlik zekası güncelleştirmelerine göre daha hızlı bir oranda uç noktalarınız için koruma sunmak için dağıtılmış kaynakları ve makine öğrenimini kullanır.

## <a name="services-and-urls"></a>Hizmetler ve URL'ler

Bu bölümdeki tabloda hizmetler ve onun ilişkili web sitesi adresleri (URL'ler) listelanmaktadır.

Bu URL'lere erişimi reddeden güvenlik duvarı veya ağ filtreleme kuralı yoktur. Aksi takdirde, bu URL'ler için özel olarak (URL hariç) bir izin kuralı oluşturmanız gerekir `*.blob.core.windows.net`. Aşağıdaki tabloda yer alan URL'lerde iletişim için bağlantı noktası 443'ü kullanır.

<br/><br/>

|Hizmet ve açıklama|URL|
|---|---|
|Microsoft Defender Virüsten Koruma teslim edilen koruma hizmeti, buluta teslim edilen Microsoft Etkin Koruma Hizmeti (HARITALAR) olarak adlandırılır.<p> Uygulama Microsoft Defender Virüsten Koruma bulut teslimi koruması sağlamak için HARITALAR hizmetini kullanır.|`*.wdcp.microsoft.com` <p> `*.wdcpalt.microsoft.com` <p> `*.wd.microsoft.com`|
|Microsoft Update Service (MU) Windows Update Service (WU) <p>Bu hizmetler, güvenlik zekası ve ürün güncelleştirmelerine olanak sağlar.|`*.update.microsoft.com` <p> `*.delivery.mp.microsoft.com`<p> `*.windowsupdate.com` <p> Daha fazla bilgi için bkz[. Güncelleştirme Güncelleştirme için Windows noktaları](/windows/privacy/manage-windows-1709-endpoints#windows-update)|
|Güvenlik zekası güncelleştirmeleri Alternatif İndirme Konumu (ADL)<p>Bu, yüklü Güvenlik zekası güncelleştirmeleri Microsoft Defender Virüsten Koruma, güvenlik zekası güncelleştirmeleri için alternatif bir konumdur (Yedi veya daha fazla gün geride).|`*.download.microsoft.com` <p> `*.download.windowsupdate.com`<p>  `go.microsoft.com`<p> `https://fe3cr.delivery.mp.microsoft.com/ClientWebService/client.asmx`|
|Kötü amaçlı yazılım gönderimi depolaması <p>Bu, Gönderim formu veya otomatik örnek gönderim aracılığıyla Microsoft'a gönderilen dosyalar için bir karşıya yükleme konumudır.|`ussus1eastprod.blob.core.windows.net` <p> `ussus2eastprod.blob.core.windows.net` <p> `ussus3eastprod.blob.core.windows.net` <p> `ussus4eastprod.blob.core.windows.net` <p> `wsus1eastprod.blob.core.windows.net` <p> `wsus2eastprod.blob.core.windows.net` <p> `ussus1westprod.blob.core.windows.net` <p> `ussus2westprod.blob.core.windows.net` <p> `ussus3westprod.blob.core.windows.net` <p> `ussus4westprod.blob.core.windows.net` <p> `wsus1westprod.blob.core.windows.net` <p> `wsus2westprod.blob.core.windows.net` <p> `usseu1northprod.blob.core.windows.net` <p> `wseu1northprod.blob.core.windows.net` <p> `usseu1westprod.blob.core.windows.net` <p> `wseu1westprod.blob.core.windows.net` <p> `ussuk1southprod.blob.core.windows.net` <p> `wsuk1southprod.blob.core.windows.net` <p> `ussuk1westprod.blob.core.windows.net` <p> `wsuk1westprod.blob.core.windows.net`|
|Sertifika İptal Listesi (CRL) <p> Windows CRL'yi güncelleştirmek için HARITALAR'a SSL bağlantısı oluştururken bu listeyi kullanabilirsiniz.|`http://www.microsoft.com/pkiops/crl/` <p> `http://www.microsoft.com/pkiops/certs` <p> `http://crl.microsoft.com/pki/crl/products` <p> `http://www.microsoft.com/pki/certs`|
|Symbol Store <p>Microsoft Defender Virüsten Koruma akışları sırasında bazı kritik dosyaları geri yüklemek için Simge Mağazası'nın kullanabilirsiniz.|`https://msdl.microsoft.com/download/symbols`|
|Evrensel GDPR İstemcisi <p> Windows tanılama verilerini göndermek için bu istemciyi kullanabilirsiniz. <p> Microsoft Defender Virüsten Koruma kalite ve izleme amacıyla Genel Veri Koruma Yönetmeliği'nin kullanımına yöneliktir.|Güncelleştirme, bildirimleri indirmek ve aşağıdaki DNS uç noktalarını kullanan tanılama verilerini Microsoft'a yüklemek için SSL (TCP Bağlantı Noktası 443) kullanır: <p> `vortex-win.data.microsoft.com` <p> `settings-win.data.microsoft.com`|


## <a name="validate-connections-between-your-network-and-the-cloud"></a>Ağınız ve bulut arasındaki bağlantıları doğrulama

Listelenen URL'lere izin verdikten sonra, bu bulut hizmetine bağlı Microsoft Defender Virüsten Koruma test edin. Tam korumalı olduğundan emin olmak için URL'lerin doğru rapor ve bilgi aldığını test edin.

### <a name="use-the-cmdline-tool-to-validate-cloud-delivered-protection"></a>Bulut teslimi korumasını doğrulamak için cmdline aracını kullanma

Ağ bulut hizmetiyle iletişim Microsoft Defender Virüsten Koruma doğrulamak için Microsoft Defender Virüsten Koruma komut satırı yardımcı programıyla (`mpcmdrun.exe`) aşağıdaki Microsoft Defender Virüsten Koruma kullanın:

```console
"%ProgramFiles%\Windows Defender\MpCmdRun.exe" -ValidateMapsConnection
```

> [!NOTE]
> Yönetici olarak Komut İstemi'ne açın. Başlat menüsünde öğeye sağ tıklayın **, Yönetici** olarak çalıştır'a **tıklayın ve** izin isteminde **Evet'e** tıklayın. Bu komut yalnızca 11. Windows 10, sürüm 1703 veya Windows üzerinde çalışır.

Daha fazla bilgi için bkz[. Microsoft Defender Virüsten Koruma komut mpcmdrun.exe yönetme](command-line-arguments-microsoft-defender-antivirus.md).

### <a name="attempt-to-download-a-fake-malware-file-from-microsoft"></a>Microsoft'tan sahte bir kötü amaçlı yazılım dosyası indirmeye çalışma

Buluta düzgün bir şekilde bağlı Microsoft Defender Virüsten Koruma algılayan ve engellenmiş olan örnek bir dosya indirebilirsiniz. Dosyayı [https://aka.ms/ioavtest](https://aka.ms/ioavtest) indirmek için ziyaret edin.

> [!NOTE]
> İndirilen dosya tam olarak kötü amaçlı yazılım değildir. Bu sahte bir dosya, buluta düzgün bir şekilde bağlanın mı olduğunu test etmek için tasarlanmıştır.

Bağlantı düzgünse, bağlantıda bir uyarı ve bildirim Microsoft Defender Virüsten Koruma.

E-posta Microsoft Edge, şu bildirim mesajlarını da alırsınız:

:::image type="content" source="../../media/wdav-bafs-edge.png" alt-text="Azure IoT Edge'de kötü amaçlı yazılım bulunduğu bildiriminin ekran görüntüsü.":::

Internet Explorer kullanıyorsanız da benzer bir ileti oluşur:

:::image type="content" source="../../media/wdav-bafs-ie.png" alt-text="Kötü amaçlı yazılım bulunduğuyla ilgili Microsoft Defender AV bildirimi.":::

#### <a name="view-the-fake-malware-detection-in-your-windows-security-app"></a>Windows Güvenliği uygulamanız içinde sahte kötü amaçlı yazılım algılamayı görüntüleme

1. Görev çubuğunuz üzerinde Kalkan simgesini seçin, **Kalkan Windows Güvenliği açın**. Veya Güvenlik için **Başlat'a** *bakarak da bunu arayabilirsiniz*.

2. Virüs **koruması'& ve ardından** Koruma **geçmişi'ne seçin**.

3. Karantinaya **alınmış tehditlerden korunma bölümünün** altında Tam geçmişi **gör'e seçerek** sahte kötü amaçlı yazılım algılandı.

   > [!NOTE]
   > Uygulamanın Windows 10 1703'den önceki sürümleri farklı bir kullanıcı arabirimine sahiptir. Uygulama [Microsoft Defender Virüsten Koruma daha fazla Windows Güvenliği bakın](microsoft-defender-security-center-antivirus.md).

   En Windows günlüğü istemci olay kimliği [1116'Windows Defender da gösterir](troubleshoot-microsoft-defender-antivirus.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Uç nokta için Microsoft Defender'da cihaz ara sunucusunu ve İnternet bağlantısı ayarlarını yapılandırma](configure-proxy-internet.md)
- [Grup İlkesi ayarlarını kullanarak grup ayarlarını yapılandırma ve Microsoft Defender Virüsten Koruma](use-group-policy-microsoft-defender-antivirus.md)
- [Microsoft Active Protection Services uç noktasına yapılan önemli değişiklikler](https://techcommunity.microsoft.com/t5/Configuration-Manager-Archive/Important-changes-to-Microsoft-Active-Protection-Service-MAPS/ba-p/274006) 