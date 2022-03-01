---
title: Seçenekler için tarama seçeneklerini Microsoft Defender Virüsten Koruma
description: E-posta depolama dosyalarını, noktaları, ağ dosyalarını ve arşivlenmiş dosyaları (örneğin, .zip) taramak için Microsoft Defender AV'yi yapılandırabilirsiniz.
keywords: gelişmiş taramalar, tarama, e-posta, arşiv, zip, rar, arşiv, yeniden tarama
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.date: 12/03/2021
ms.collection: M365-security-compliance
ms.topic: how-to
ms.openlocfilehash: 2527a558d474fecaab813963dc38a9e76aa89d5c
ms.sourcegitcommit: 2a4dddf7c655b44b17d4fd7f5e1e5d8a6e2b7aef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/06/2021
ms.locfileid: "62996605"
---
# <a name="configure-microsoft-defender-antivirus-scanning-options"></a>Tarama Microsoft Defender Virüsten Koruma yapılandırma

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="use-microsoft-intune-to-configure-scanning-options"></a>Tarama Microsoft Intune yapılandırmak için tarama seçeneklerini kullanma

Daha fazla bilgi için [bkz. Intune'daki](/intune/device-restrictions-windows-10#microsoft-defender-antivirus) Microsoft Intune kısıtlama Microsoft Defender Virüsten Koruma ayarları için Windows 10 yapılandırma.[](/intune/device-restrictions-configure)

## <a name="use-microsoft-endpoint-manager-to-configure-scanning-options"></a>Tarama Microsoft Endpoint Manager yapılandırmak için tarama seçeneklerini kullanma

Kimlik bilgilerini yapılandırma (geçerli Microsoft Endpoint Manager) hakkında ayrıntılı bilgi için bkz. Kötü amaçlı yazılım ilkeleri oluşturma ve [dağıtma: Tarama ayarları](/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings).

## <a name="use-group-policy-to-configure-scanning-options"></a>Tarama seçeneklerini yapılandırmak için Grup İlkesi kullanma

> [!TIP]
> Grup İlkesi Başvuru Elektronik Tablosu'nda, Yönetim şablonu dosyalarına dahil edilen bilgisayar ve kullanıcı yapılandırmalarının ilke ayarlarının listelerle birlikte teslim Windows. Grup İlkesi Nesnelerini düzenlerken elektronik tablo için başvuru yapılandırabilirsiniz. <br/><br/> En son sürümler:
> - [Mayıs 2020 Ayarlar Için Grup İlkesi Windows 10 Başvuru Elektronik Tablosu (2004)](https://www.microsoft.com/download/details.aspx?id=101451)
> - [11 Ayarlar 2021 Güncelleştirmesi Windows Grup İlkesi Başvuru Elektronik Tablosu (21H2)](https://www.microsoft.com/download/details.aspx?id=103506)

1. Grup İlkesi yönetim bilgisayarınızda Grup İlkesi [Yönetim Konsolu'nu açın](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Yapılandırmak istediğiniz Grup İlkesi Nesnesi'ne sağ tıklayın ve Düzenle'yi **seçin**.

3. Grup İlkesi **Yönetim Düzenleyicisi'nde Bilgisayar** **yapılandırması'ne gidin ve** Yönetim **şablonları'ne tıklayın**.

4. Ağacı, bileşenleri **Windows için** \> **Microsoft Defender Virüsten Koruma** ve bir konum seçin (bu makalede [Ayarlar konumlara](#settings-and-locations) ve konumlara bakın).

5. İlke nesnesini düzenleyin.

6. **Tamam'a** tıklayın ve diğer tüm ayarlar için işlemi yinelayın.

### <a name="settings-and-locations"></a>Ayarlar ve konumlar

|İlke öğesi ve konumu|Varsayılan ayar (yapılandırılmamışsa)|Sınıf için PowerShell `Set-MpPreference` parametresi veya `MSFT_MpPreference` WMI özelliği|
|---|---|---|
|E-posta tarama <p> **Tarama** \> **E-posta taramayı açma**<p>Bkz [. E-posta tarama sınırlamaları](#email-scanning-limitations) (bu makalede)|Devre dışı|`-DisableEmailScanning`|
| Komut dosyası tarama | Etkin  | Bu ilke ayarı betik taramayı yapılandırmaya olanak sağlar. Bu ayarı etkinleştirir veya yapılandırmazsanız, betik taraması etkinleştirilir. <p>Bkz [. Defender/AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender)  | 
|Yeniden [tarama noktaları](/windows/win32/fileio/reparse-points) <p> **Tarama** \> **Yeniden nokta taramayı açma**|Devre dışı|Yok <p>Noktaları [yenidenparsele'ye bakın](/windows/win32/fileio/reparse-points)|
|Eşlenmiş ağ sürücülerini tarama <p> **Tarama** \> **Eşlenmiş ağ sürücülerinde tam taramayı çalıştırma**|Devre dışı|`-DisableScanningMappedNetworkDrivesForFullScan`|
|Arşiv dosyalarını tara (örneğin, .zip veya .rar). <p> **Tarama** \> **Arşiv dosyalarını tarama**|Etkin|`-DisableArchiveScanning` <p>[Uzantılar dışlama listesi](configure-extension-file-exclusions-microsoft-defender-antivirus.md) bu ayardan önce gelecektir.|
|Ağ üzerinde dosyaları tarama <p> **Tarama** \> **Ağ dosyalarını tarama**|Devre dışı|`-DisableScanningNetworkFiles`|
|Paketlenmiş yürütülebilir dosyaları tarama <p> **Tarama** \> **Paketlenmiş yürütülebilir dosyaları tarama**|Etkin|Yok|
|Yalnızca tam tarama sırasında çıkarılabilir sürücüleri tarama <p> **Tarama** \> **Çıkarılabilir sürücüleri tarama**|Devre dışı|`-DisableRemovableDriveScanning`|
|Arşiv klasöründeki alt klasörlerin düzeyini taramak için belirtme <p>**Tarama** \> **Arşiv dosyalarını taramak için en fazla derinlik belirtme**|0|Yok|
|Tarama sırasında en yüksek CPU yükünü (yüzde olarak) belirtin. <p> **Tarama** \> **Tarama sırasında CPU kullanımının en yüksek yüzdesini belirtme**|50|`-ScanAvgCPULoadFactor` <p>**NOT**: En yüksek CPU yükü zor bir sınır değildir, ancak tarama altyapısının ortalama üst sınırı aşmama kılavuzudur. Taramaları el ile çalıştır bu ayarı yoksayar ve hiçbir CPU sınırı olmadan çalıştırın.|
|Taranacak arşiv dosyalarının boyutunu (kilobayt cinsinden) belirtin. <p> **Tarama** \> **Taranacak arşiv dosyalarının boyut üst boyutunu belirtme**|Sınır yok|Yok <p>0 varsayılan değeri hiçbir sınır uygulamaz|
|Zamanlanmış taramalar için düşük CPU önceliğini yapılandırma <p> **Tarama** \> **Zamanlanmış taramalar için düşük CPU önceliğini yapılandırma**|Devre dışı|Yok|

> [!NOTE]
> Gerçek zamanlı koruma açıksa, dosyalara erişilmeden ve yürütülmeden önce taranır. Tarama kapsamı, USB sürücüleri gibi çıkarılabilir medya dosyaları da dahil olmak üzere tüm dosyaları içerir. Taramayı gerçekleştiren cihazda gerçek zamanlı koruma veya erişim koruması açıksa, tarama işlemi ağ paylaşımlarını da içerir.

## <a name="use-powershell-to-configure-scanning-options"></a>Tarama seçeneklerini yapılandırmak için PowerShell kullanma

PowerShell'i diğerleriyle birlikte kullanma hakkında daha fazla Microsoft Defender Virüsten Koruma için bkz.

- [PowerShell cmdlet'leriyle Microsoft Defender Virüsten Koruma yönetme](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma cmdlet'leri](/powershell/module/defender/)

## <a name="use-wmi-to-configure-scanning-options"></a>Tarama seçeneklerini yapılandırmak için WMI kullanma

Bkz[. Windows Defender WMIv2 API'leri](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="email-scanning-limitations"></a>E-posta tarama sınırlamaları

E-posta tarama, isteğe bağlı ve zamanlanmış taramalar Outlook diğer posta istemcileri tarafından kullanılan e-posta dosyalarının taranmasını sağlar. E-postanın içindeki ekli nesneler (ekler ve arşivlenmiş dosyalar gibi) da taranır. Aşağıdaki dosya biçimi türleri taranarak düzeltebilirsiniz:

- DBX
- MBX
- MIME

Outlook 2003 veya daha eski (arşiv türü Unicode olmayan olarak ayarlanmıştır) tarafından kullanılan PST dosyaları da taranır, ancak Microsoft Defender Virüsten Koruma PST dosyaları içinde algılanan tehditleri düzeltmez.

E Microsoft Defender Virüsten Koruma bir e-posta iletisinin içinde bir tehdit algılarsa, güvenliği ihlal edilmiş e-postayı belirlemede size yardımcı olacak aşağıdaki bilgileri gösterir; böylelikle tehdide el ile müdahale edebilirsiniz:

- E-posta konusu
- Ek adı

## <a name="scanning-mapped-network-drives"></a>Eşlenmiş ağ sürücülerini tarama

Herhangi bir işletim sisteminde, yalnızca sistem düzeyinde eşlenen ağ sürücüleri taranır. Kullanıcı düzeyi eşlenmiş ağ sürücüleri taranmamış olabilir. Kullanıcı düzeyi eşlenmiş ağ sürücüleri, kullanıcının oturumlarında kendi kimlik bilgilerini el ile eşlenen ve kendi kimlik bilgilerini kullanan sürücülerdir.

## <a name="see-also"></a>Ayrıca bkz.

- [Bu taramaları ve düzeltmeleri sonucunda Microsoft Defender Virüsten Koruma, başlatma ve gözden geçirme](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Taramalarda isteğe bağlı olarak Microsoft Defender Virüsten Koruma çalıştırma](run-scan-microsoft-defender-antivirus.md)
- [Zamanlanmış taramaları Microsoft Defender Virüsten Koruma yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
