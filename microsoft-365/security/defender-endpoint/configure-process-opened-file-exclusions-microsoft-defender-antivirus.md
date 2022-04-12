---
title: Belirli işlemler tarafından açılan dosyalar için dışlamaları yapılandırma
description: Belirli bir işlem tarafından açılmış dosyaları taramaların dışında tutabilirsiniz.
keywords: Microsoft Defender Virüsten Koruma, işlem, dışlama, dosyalar, taramalar
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
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: e8cf075c0a35095f72d847a17f1fb48d590ad385
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788996"
---
# <a name="configure-exclusions-for-files-opened-by-processes"></a>İşlemler tarafından açılan dosyalar için dışlamaları yapılandırma


**Şunlar için geçerlidir:**

- [Pertahanan Microsoft untuk Titik Akhir Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows 

Belirli işlemler tarafından açılmış dosyaları Microsoft Defender Virüsten Koruma taramaların dışında tutabilirsiniz. [Dışlama listelerinizi tanımlamadan önce dışlamaları tanımlamak için](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions) bkz. Öneriler.

Bu makalede dışlama listelerinin nasıl yapılandırıldığı açıklanır.

## <a name="examples-of-exclusions"></a>Dışlama örnekleri

<br/><br/>

|Dışlama|Örnek|
|---|---|
|Makinedeki belirli bir dosya adına sahip herhangi bir işlem tarafından açılan herhangi bir dosya|Belirtilmesi `test.exe` , aşağıdakiler tarafından açılan dosyaları dışlar: <p>`c:\sample\test.exe` <p> `d:\internal\files\test.exe`|
|Makinedeki belirli bir klasör altındaki herhangi bir işlem tarafından açılan herhangi bir dosya|Belirtilmesi `c:\test\sample\*` , aşağıdakiler tarafından açılan dosyaları dışlar: <p> `c:\test\sample\test.exe` <p> `c:\test\sample\test2.exe` <p> `c:\test\sample\utility.exe`|
|Makinedeki belirli bir klasördeki belirli bir işlem tarafından açılan herhangi bir dosya|Belirtilmesi `c:\test\process.exe` yalnızca `c:\test\process.exe`|

İşlem dışlama listesine bir işlem eklediğinizde, Microsoft Defender Virüsten Koruma dosyaların nerede bulunduğu fark etmez, bu işlem tarafından açılan dosyaları taramaz. Ancak, [dosya dışlama listesine](configure-extension-file-exclusions-microsoft-defender-antivirus.md) de eklenmediği sürece işlemin kendisi taranır.

Dışlamalar yalnızca [her zaman açık gerçek zamanlı koruma ve izleme](configure-real-time-protection-microsoft-defender-antivirus.md) için geçerlidir. Zamanlanmış veya isteğe bağlı taramalar için geçerli değildir.

Dışlama listelerinde grup ilkesi yapılan değişiklikler [Windows Güvenliği uygulamasındaki](microsoft-defender-security-center-antivirus.md) listelerde **gösterilir**. Ancak, Windows Güvenliği uygulamasında yapılan değişiklikler grup ilkesi listelerinde **gösterilmez**.

grup ilkesi, Microsoft Endpoint Configuration Manager, Microsoft Intune ve Windows Güvenliği uygulamasıyla dışlamalar için listeleri ekleyebilir, kaldırabilir ve gözden geçirebilir ve listeleri daha fazla özelleştirmek için joker karakterler kullanabilirsiniz.

Dışlama listelerini yapılandırmak için listelerinizi gözden geçirmek de dahil olmak üzere PowerShell cmdlet'lerini ve WMI'yi de kullanabilirsiniz.

Varsayılan olarak, listelerde yapılan yerel değişiklikler (yönetici ayrıcalıklarına sahip kullanıcılar tarafından; PowerShell ve WMI ile yapılan değişiklikler), grup ilkesi, Configuration Manager veya Intune tarafından tanımlandığı (ve dağıtıldığı) listelerle birleştirilir. çakışma durumunda grup ilkesi listeleri önceliklidir.

Yerel değişikliklerin yönetilen dağıtım ayarlarını geçersiz kılmasını sağlamak için [yerel ve genel olarak tanımlanmış dışlama listelerinin nasıl birleştirildiğini yapılandırabilirsiniz](configure-local-policy-overrides-microsoft-defender-antivirus.md#merge-lists) .

## <a name="configure-the-list-of-exclusions-for-files-opened-by-specified-processes"></a>Belirtilen işlemler tarafından açılan dosyalar için dışlama listesini yapılandırma

### <a name="use-microsoft-intune-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Belirtilen işlemler tarafından açılmış dosyaları taramaların dışında tutmak için Microsoft Intune kullanın

Daha fazla bilgi için bkz. [Microsoft Intune cihaz kısıtlama ayarlarını yapılandırma](/intune/device-restrictions-configure) ve [Windows 10 için cihaz kısıtlama ayarlarını Microsoft Defender Virüsten Koruma Intune](/intune/device-restrictions-windows-10#microsoft-defender-antivirus).

### <a name="use-microsoft-endpoint-manager-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Belirtilen işlemler tarafından açılmış dosyaları taramaların dışında tutmak için Microsoft Endpoint Manager kullanın

Microsoft Endpoint Manager (geçerli dal) yapılandırma ayrıntıları için bkz[. Kötü amaçlı yazılımdan koruma ilkeleri oluşturma ve dağıtma: Dışlama ayarları](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings).

### <a name="use-group-policy-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Belirtilen işlemler tarafından açılmış dosyaları taramaların dışında tutmak için grup ilkesi kullanın

1. grup ilkesi yönetim bilgisayarınızda [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **Düzenle'ye** tıklayın.

2. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin ve **Yönetim şablonları'na** tıklayın.

3. **Dışlamalar Microsoft Defender Virüsten Koruma bileşenleri \> Windows \>** için ağacı genişletin.

4. **İşlem Dışlamaları'na** çift tıklayın ve dışlamaları ekleyin:
    1. Seçeneği **Etkin** olarak ayarlayın.
    2. **Seçenekler** bölümünün altında **Göster...** öğesine tıklayın.
    3. Her işlemi **Değer adı** sütununun altına kendi satırına girin. Farklı işlem dışlama türleri için örnek tabloya bakın. Tüm işlemler için **Değer** sütununa **0** girin.

5. **Tamam**'a tıklayın.

### <a name="use-powershell-cmdlets-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Belirtilen işlemler tarafından açılmış dosyaları taramaların dışında tutmak için PowerShell cmdlet'lerini kullanma

İşlemler tarafından açılmış dosyalar için dışlama eklemek veya kaldırmak için PowerShell kullanmak için parametresiyle `-ExclusionProcess` üç cmdlet'in birleşimini kullanmak gerekir. Cmdlet'lerin tümü [Defender modülündedir](/powershell/module/defender/).

Cmdlet'lerin biçimi:

```PowerShell
<cmdlet> -ExclusionProcess "<item>"
```

aşağıdakiler olarak \<cmdlet\>izin verilir:

<br/><br/>

|Yapılandırma eylemi|PowerShell cmdlet'i|
|---|---|
|Listeyi oluşturma veya üzerine yazma|`Set-MpPreference`|
|Listeye ekle|`Add-MpPreference`|
|Listeden öğeleri kaldırma|`Remove-MpPreference`|

> [!IMPORTANT]
> veya `Add-MpPreference`ile `Set-MpPreference` bir liste oluşturduysanız, cmdlet'ini `Set-MpPreference` yeniden kullanmak varolan listenin üzerine yazar.

Örneğin, aşağıdaki kod parçacığı Microsoft Defender AV taramalarının belirtilen işlem tarafından açılan tüm dosyaları dışlamasına neden olabilir:

```PowerShell
Add-MpPreference -ExclusionProcess "c:\internal\test.exe"
```

PowerShell'i Microsoft Defender Virüsten Koruma ile kullanma hakkında daha fazla bilgi için bkz. PowerShell cmdlet'leri ve [Microsoft Defender Virüsten Koruma cmdlet'leri ile virüsten](/powershell/module/defender) korumayı yönetme.

### <a name="use-windows-management-instruction-wmi-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Belirtilen işlemler tarafından açılmış dosyaları taramaların dışında tutmak için Windows Yönetim Yönergesi'ni (WMI) kullanın

Aşağıdaki özellikler için [**MSFT_MpPreference** sınıfının **Set**, **Add** ve **Remove** yöntemlerini](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) kullanın:

```WMI
ExclusionProcess
```

**Ayarla**, **Ekle** ve **Kaldır'ın** kullanımı, PowerShell'deki karşılıklarına benzer: `Set-MpPreference`, `Add-MpPreference`ve `Remove-MpPreference`.

Daha fazla bilgi ve izin verilen parametreler için bkz. [Windows Defender WMIv2 API'leri](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

### <a name="use-the-windows-security-app-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Belirtilen işlemler tarafından açılmış dosyaları taramaların dışında tutmak için Windows Güvenliği uygulamasını kullanın

Yönergeler için bkz. [Windows Güvenliği uygulamasında dışlama ekleme](microsoft-defender-security-center-antivirus.md).

## <a name="use-wildcards-in-the-process-exclusion-list"></a>İşlem dışlama listesinde joker karakter kullanma

İşlem dışlama listesindeki joker karakterlerin kullanımı, diğer dışlama listelerindeki kullanımlarından farklıdır.

Özellikle soru işaretini (`?`) joker karakter kullanamazsınız ve yıldız işareti (`*`) joker karakteri yalnızca tam bir yolun sonunda kullanılabilir. İşlem dışlama listesindeki öğeleri tanımlarken joker karakter olarak ortam değişkenlerini (örneğin `%ALLUSERSPROFILE%`) kullanmaya devam edebilirsiniz.

Aşağıdaki tabloda joker karakterlerin işlem dışlama listesinde nasıl kullanılabildiği açıklanmaktadır:

<br/><br/>

|Joker|Örnek kullanım|Örnek eşleşmeler|
|---|---|---|
|`*` (yıldız işareti) <p> Herhangi bir sayıda karakteri değiştirir|`C:\MyData\*`|Tarafından açılan herhangi bir dosya `C:\MyData\file.exe`|
|Ortam değişkenleri <p> Dışlama değerlendirildiğinde tanımlı değişken bir yol olarak doldurulur|`%ALLUSERSPROFILE%\CustomLogFiles\file.exe`|Tarafından açılan herhangi bir dosya `C:\ProgramData\CustomLogFiles\file.exe`|

## <a name="review-the-list-of-exclusions"></a>Dışlama listesini gözden geçirin

MpCmdRun, PowerShell, [Microsoft Endpoint Configuration Manager, Intune](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings) veya [Windows Güvenliği uygulamasıyla](microsoft-defender-security-center-antivirus.md) dışlama listesindeki öğeleri alabilirsiniz. [](/intune/device-restrictions-configure)

PowerShell kullanıyorsanız, listeyi iki yolla alabilirsiniz:

- Tüm Microsoft Defender Virüsten Koruma tercihlerinin durumunu alın. Listelerin her biri ayrı satırlarda görüntülenir, ancak her liste içindeki öğeler aynı satırda birleştirilir.
- Tüm tercihlerin durumunu bir değişkene yazın ve bu değişkeni yalnızca ilgilendiğiniz listeyi çağırmak için kullanın. her kullanımı `Add-MpPreference` yeni bir satıra yazılır.

### <a name="validate-the-exclusion-list-by-using-mpcmdrun"></a>MpCmdRun kullanarak dışlama listesini doğrulama

mpcmdrun.exeayrılmış [komut satırı aracıyla ](./command-line-arguments-microsoft-defender-antivirus.md?branch=v-anbic-wdav-new-mpcmdrun-options)dışlamaları denetlemek için aşağıdaki komutu kullanın:

```DOS
MpCmdRun.exe -CheckExclusion -path <path>
```

> [!NOTE]
> MpCmdRun ile dışlamaların denetlenmesi için MICROSOFT DEFENDER VIRÜSTEN KORUMA CAMP sürüm 4.18.1812.3 (Aralık 2018'de yayımlandı) veya üzeri gerekir.

### <a name="review-the-list-of-exclusions-alongside-all-other-microsoft-defender-antivirus-preferences-by-using-powershell"></a>PowerShell kullanarak diğer tüm Microsoft Defender Virüsten Koruma tercihlerinin yanı sıra dışlama listesini gözden geçirin

Aşağıdaki cmdlet'i kullanın:

```PowerShell
Get-MpPreference
```

[PowerShell'i Microsoft Defender Virüsten Koruma](use-powershell-cmdlets-microsoft-defender-antivirus.md) ile kullanma hakkında daha fazla bilgi için bkz. PowerShell [cmdlet'lerini Microsoft Defender Virüsten Koruma ve Microsoft Defender Virüsten Koruma cmdlet'lerini](/powershell/module/defender) yapılandırmak ve çalıştırmak için kullanma.

### <a name="retrieve-a-specific-exclusions-list-by-using-powershell"></a>PowerShell kullanarak belirli bir dışlama listesini alma

Aşağıdaki kod parçacığını kullanın (her satırı ayrı bir komut olarak girin); **WDAVprefs** değerini değişkeni adlandırmak istediğiniz etiketle değiştirin:

```PowerShell
$WDAVprefs = Get-MpPreference
$WDAVprefs.ExclusionProcess
```

[PowerShell'i Microsoft Defender Virüsten Koruma](use-powershell-cmdlets-microsoft-defender-antivirus.md) ile kullanma hakkında daha fazla bilgi için bkz. PowerShell [cmdlet'lerini Microsoft Defender Virüsten Koruma ve Microsoft Defender Virüsten Koruma cmdlet'lerini](/powershell/module/defender) yapılandırmak ve çalıştırmak için kullanma.

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [macOS'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender Virüsten Koruma macOS Virüsten Koruma ilkesi ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android'de Uç Nokta için Defender özelliklerini yapılandırma](android-configure.md)
> - [iOS özelliklerinde Pertahanan Microsoft untuk Titik Akhir yapılandırma](ios-configure-features.md)

## <a name="related-articles"></a>İlgili makaleler

- [Microsoft Defender Virüsten Koruma taramalarında dışlamaları yapılandırma ve doğrulama](configure-exclusions-microsoft-defender-antivirus.md)
- [Dosya adı, uzantı ve klasör konumuna göre dışlamaları yapılandırma ve doğrulama](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Windows Sunucusu'nda Microsoft Defender Virüsten Koruma dışlamalarını yapılandırma](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Dışlamaları tanımlarken kaçınılması gereken yaygın hatalar](common-exclusion-mistakes-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma taramalarının ve düzeltmelerinin sonuçlarını özelleştirme, başlatma ve gözden geçirme](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Windows 10'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
