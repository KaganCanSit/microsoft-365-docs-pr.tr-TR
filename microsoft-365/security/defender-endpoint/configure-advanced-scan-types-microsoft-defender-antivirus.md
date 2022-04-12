---
title: Microsoft Defender Virüsten Koruma için tarama seçeneklerini yapılandırma
description: Microsoft Defender AV'yi e-posta depolama dosyalarını, yedekleme veya yeniden ayrıştırma noktalarını, ağ dosyalarını ve arşivlenmiş dosyaları (.zip dosyaları gibi) tarayabilecek şekilde yapılandırabilirsiniz.
keywords: gelişmiş taramalar, tarama, e-posta, arşiv, zip, rar, arşiv, yeniden ayrıştırma taraması
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
ms.openlocfilehash: a2eaeb2de0a7caf502130bef788c17e515657d7a
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788974"
---
# <a name="configure-microsoft-defender-antivirus-scanning-options"></a>Microsoft Defender Virüsten Koruma tarama seçeneklerini yapılandırın

**Şunlar için geçerlidir:**
- [Pertahanan Microsoft untuk Titik Akhir Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows 

## <a name="use-microsoft-intune-to-configure-scanning-options"></a>Tarama seçeneklerini yapılandırmak için Microsoft Intune kullanma

Daha fazla bilgi için bkz[. Microsoft Intune cihaz kısıtlama ayarlarını yapılandırma](/intune/device-restrictions-configure) ve [Intune Windows 10 için cihaz kısıtlama ayarlarını Microsoft Defender Virüsten Koruma](/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

## <a name="use-microsoft-endpoint-manager-to-configure-scanning-options"></a>Tarama seçeneklerini yapılandırmak için Microsoft Endpoint Manager kullanma

Microsoft Endpoint Manager (geçerli dal) yapılandırmayla ilgili ayrıntılar için bkz. [Kötü amaçlı yazılımdan koruma ilkeleri oluşturma ve dağıtma: Tarama ayarları](/configmgr/protect/deploy-use/endpoint-antimalware-policies#scan-settings).

## <a name="use-group-policy-to-configure-scanning-options"></a>Tarama seçeneklerini yapılandırmak için grup ilkesi kullanma

> [!TIP]
> Windows için teslim edilen Yönetim şablonu dosyalarına dahil edilen bilgisayar ve kullanıcı yapılandırmaları için ilke ayarlarını listeleyen grup ilkesi Başvuru Elektronik Tablosu'nı indirin. grup ilkesi Nesneleri düzenlerken elektronik tabloya başvurmayı yapılandırabilirsiniz. <br/><br/> En son sürümler şunlardır:
> - [Windows 10 Mayıs 2020 Güncelleştirmesi (2004) için grup ilkesi Ayarlar Başvuru Elektronik Tablosu](https://www.microsoft.com/download/details.aspx?id=101451)
> - [Windows 11 Ekim 2021 Güncelleştirmesi (21H2) için grup ilkesi Ayarlar Başvuru Elektronik Tablosu](https://www.microsoft.com/download/details.aspx?id=103506)

1. grup ilkesi yönetim bilgisayarınızda [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın.

2. Yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **düzenle'yi** seçin.

3. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin ve **Yönetim şablonları'na** tıklayın.

4. Microsoft Defender Virüsten Koruma **bileşenleri** \> Windows için ağacı genişletin ve bir konum seçin (bu [makaledeki Ayarlar ve konumlara](#settings-and-locations) bakın).

5. İlke nesnesini düzenleyin.

6. **Tamam'a** tıklayın ve diğer ayarlar için yineleyin.

### <a name="settings-and-locations"></a>Ayarlar ve konumlar

|İlke öğesi ve konumu|Varsayılan ayar (yapılandırılmadıysa)|Sınıf için `MSFT_MpPreference` PowerShell `Set-MpPreference` parametresi veya WMI özelliği|
|---|---|---|
|E-posta taraması <p> **Tarama** \> **E-posta taramayı açma**<p>Bkz [. E-posta tarama sınırlamaları](#email-scanning-limitations) (bu makalede)|Devre dışı|`-DisableEmailScanning`|
| Betik tarama | Etkin  | Bu ilke ayarı betik taramasını yapılandırmanıza olanak tanır. Bu ayarı etkinleştirir veya yapılandırmazsanız, betik taraması etkinleştirilir. <p>Bkz. [Defender/AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender)  | 
|[Yeniden ayrıştırma noktalarını](/windows/win32/fileio/reparse-points) tarama <p> **Tarama** \> **Yeniden ayrıştırma noktası taramayı açma**|Devre dışı|Yok <p>Bkz [. Noktaları yeniden ayrıştırma](/windows/win32/fileio/reparse-points)|
|Eşlenen ağ sürücülerini tarama <p> **Tarama** \> **Eşlenen ağ sürücülerinde tam tarama çalıştırma**|Devre dışı|`-DisableScanningMappedNetworkDrivesForFullScan`|
|Arşiv dosyalarını tarayın (.zip veya .rar dosyaları gibi). <p> **Tarama** \> **Arşiv dosyalarını tarama**|Etkin|`-DisableArchiveScanning` <p>[Uzantılar dışlama listesi](configure-extension-file-exclusions-microsoft-defender-antivirus.md) bu ayardan önceliklidir.|
|Ağdaki dosyaları tarama <p> **Tarama** \> **Ağ dosyalarını tarama**|Devre dışı|`-DisableScanningNetworkFiles`|
|Paketlenmiş yürütülebilir dosyaları tarama <p> **Tarama** \> **Paketlenmiş yürütülebilir dosyaları tarama**|Etkin|Yok|
|Yalnızca tam taramalar sırasında çıkarılabilir sürücüleri tarama <p> **Tarama** \> **Çıkarılabilir sürücüleri tarama**|Devre dışı|`-DisableRemovableDriveScanning`|
|Taranacak arşiv klasöründeki alt klasörlerin düzeyini belirtme <p>**Tarama** \> **Arşiv dosyalarını taramak için maksimum derinliği belirtin**|0|Yok|
|Tarama sırasında en yüksek CPU yükünü (yüzde olarak) belirtin. <p> **Tarama** \> **Tarama sırasında en yüksek CPU kullanım yüzdesini belirtme**|50|`-ScanAvgCPULoadFactor` <p>**NOT**: Maksimum CPU yükü sabit bir sınır değildir, ancak tarama altyapısının ortalama en yüksek sınırı aşmaması için rehberliktir. Taramaları el ile çalıştırma bu ayarı yoksayar ve HERHANGI bir CPU sınırı olmadan çalışır.|
|Taranması gereken arşiv dosyalarının en büyük boyutunu (kilobayt cinsinden) belirtin. <p> **Tarama** \> **Taranacak arşiv dosyalarının en büyük boyutunu belirtin**|Sınır yok|Yok <p>0 varsayılan değeri sınır uygulamaz|
|Zamanlanmış taramalar için düşük CPU önceliğini yapılandırma <p> **Tarama** \> **Zamanlanmış taramalar için düşük CPU önceliğini yapılandırma**|Devre dışı|Yok|

> [!NOTE]
> Gerçek zamanlı koruma açıksa dosyalar erişilmeden ve yürütülmeden önce taranır. Tarama kapsamı, USB sürücüler gibi takılı çıkarılabilir medyadaki dosyalar da dahil olmak üzere tüm dosyaları içerir. Taramayı gerçekleştiren cihazda gerçek zamanlı koruma veya erişim üzerinde koruma açıksa, tarama ağ paylaşımlarını da içerir.

## <a name="use-powershell-to-configure-scanning-options"></a>Tarama seçeneklerini yapılandırmak için PowerShell kullanma

PowerShell'i Microsoft Defender Virüsten Koruma ile kullanma hakkında daha fazla bilgi için bkz.

- [PowerShell cmdlet'leriyle Microsoft Defender Virüsten Koruma yönetme](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma cmdlet'leri](/powershell/module/defender/)

## <a name="use-wmi-to-configure-scanning-options"></a>Tarama seçeneklerini yapılandırmak için WMI kullanma

Bkz. [Windows Defender WMIv2 API'leri](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

## <a name="email-scanning-limitations"></a>E-posta tarama sınırlamaları

E-posta taraması, Outlook ve diğer posta istemcileri tarafından isteğe bağlı ve zamanlanmış taramalar sırasında kullanılan e-posta dosyalarının taranmalarına olanak tanır. E-posta içindeki katıştırılmış nesneler (ekler ve arşivlenmiş dosyalar gibi) de taranır. Aşağıdaki dosya biçimi türleri taranabilir ve düzeltilebilir:

- DBX
- MBX
- MIME

Outlook 2003 veya daha eski (arşiv türünün unicode olmayan olarak ayarlandığı) tarafından kullanılan PST dosyaları da taranır, ancak Microsoft Defender Virüsten Koruma PST dosyalarının içinde algılanan tehditleri gideremez.

Microsoft Defender Virüsten Koruma bir e-posta iletisinde bir tehdit algılarsa, tehdidi el ile düzeltebilmeniz için güvenliği aşılmış e-postayı tanımlamanıza yardımcı olması için aşağıdaki bilgileri gösterir:

- E-posta konusu
- Ek adı

## <a name="scanning-mapped-network-drives"></a>Eşlenen ağ sürücülerini tarama

Herhangi bir işletim sisteminde, yalnızca sistem düzeyinde eşlenen ağ sürücüleri taranır. Kullanıcı düzeyinde eşlenmiş ağ sürücüleri taranmıyor. Kullanıcı düzeyinde eşlenen ağ sürücüleri, kullanıcının oturumlarında el ile ve kendi kimlik bilgilerini kullanarak eşledikleri sürücülerdir.

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [macOS'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender Virüsten Koruma macOS Virüsten Koruma ilkesi ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android'de Uç Nokta için Defender özelliklerini yapılandırma](android-configure.md)
> - [iOS özelliklerinde Pertahanan Microsoft untuk Titik Akhir yapılandırma](ios-configure-features.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Defender Virüsten Koruma taramalarının ve düzeltmelerinin sonuçlarını özelleştirme, başlatma ve gözden geçirme](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [İsteğe bağlı Microsoft Defender Virüsten Koruma taramalarını yapılandırın ve çalıştırın](run-scan-microsoft-defender-antivirus.md)
- [Zamanlanmış Microsoft Defender Virüsten Koruma taramalarını yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Windows 10'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
