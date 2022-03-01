---
title: Belirli işlemlerle açılan dosyalar için dışlamaları yapılandırma
description: Belirli bir işlemle açılmışsa, dosyaları taramaların dışında tutabilirsiniz.
keywords: Microsoft Defender Virüsten Koruma, süreç, dışlama, dosyalar, taramalar
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
ms.openlocfilehash: 034ad1312497652554c9a59d51ba18f6bddc9d83
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/29/2021
ms.locfileid: "62997043"
---
# <a name="configure-exclusions-for-files-opened-by-processes"></a>İşlemler tarafından açılan dosyalar için dışlamaları yapılandırma


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Belirli işlemler tarafından açılmış dosyaları taramaların dışında Microsoft Defender Virüsten Koruma. [Dışlama Öneriler tanımlamadan önce dışlamaları](configure-exclusions-microsoft-defender-antivirus.md#recommendations-for-defining-exclusions) tanımlama hakkında daha fazla bilgi için bkz.

Bu makalede dışlama listelerinin nasıl yapılandırıldığında açıklanmıştır.

## <a name="examples-of-exclusions"></a>Dışlama örnekleri

<br/><br/>

|Dışlama|Örnek|
|---|---|
|Makinede belirli bir dosya adına sahip herhangi bir işlem tarafından açılan herhangi bir dosya|Belirtmek, `test.exe` aşağıdakiler tarafından açılan dosyaları dışarıda tutabilirsiniz: <p>`c:\sample\test.exe` <p> `d:\internal\files\test.exe`|
|Makinede, belirli bir klasör altında herhangi bir işlem tarafından açılmış herhangi bir dosya|Belirtmek, `c:\test\sample\*` aşağıdakiler tarafından açılan dosyaları dışarıda tutabilirsiniz: <p> `c:\test\sample\test.exe` <p> `c:\test\sample\test2.exe` <p> `c:\test\sample\utility.exe`|
|Makinede, belirli bir klasörde belirli bir işlem tarafından açılmış herhangi bir dosya|Belirterek `c:\test\process.exe` yalnızca açılan dosyalar hariç tutulacak `c:\test\process.exe`|

İşlem dışlama listesine bir işlem eklerken, Microsoft Defender Virüsten Koruma nerede olursa olsun, bu işlem tarafından açılan dosyaları taramaz. Öte yandan, işlem, dosya dışlama listesine eklenmediği sürece [taranır](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

Dışlamalar yalnızca her zaman [gerçek zamanlı koruma ve izleme için geçerlidir](configure-real-time-protection-microsoft-defender-antivirus.md). Bunlar zamanlanmış veya isteğe bağlı taramalar için geçerli değildir.

Dışlama listelerinde Grup İlkesi ile yapılan **değişiklikler,** grup uygulamasındaki [Windows Güvenliği gösterir](microsoft-defender-security-center-antivirus.md). Bununla birlikte, Windows Güvenliği uygulamasında **yapılan değişiklikler Grup İlkesi** listelerinde göstermez.

Grup İlkesi, Microsoft Endpoint Configuration Manager, Microsoft Intune ve Windows Güvenliği uygulamasıyla dışlama listelerini ekleyebilir, kaldırabilir ve gözden geçirebilirsiniz. Listeleri daha da özelleştirmek için joker karakterleri kullanabilirsiniz.

Dışlama listelerini yapılandırmak ve listelerinizi gözden geçirmek de dahil olmak üzere dışlama listelerini yapılandırmak için PowerShell cmdlet'lerini ve WMI'yı da kullanabilirsiniz.

Varsayılan olarak, listelerde yapılan yerel değişiklikler (yönetici ayrıcalıklarına sahip kullanıcılar tarafından; PowerShell ve WMI ile yapılan değişiklikler), Grup İlkesi, Yapılandırma Yöneticisi veya Intune tarafından tanımlandığı (ve dağıtıldı) listelerle birleştirilir. Grup İlkesi listeleri, çakışmalar durumunda öncelikleri alır.

Yerel olarak [ve genel olarak tanımlanmış dışlama listelerinin nasıl birleştirileceklerini, yerel](configure-local-policy-overrides-microsoft-defender-antivirus.md#merge-lists) değişikliklerin yönetilen dağıtım ayarlarını geçersiz k olmasına izin verecek şekilde yapılandırabilirsiniz.

## <a name="configure-the-list-of-exclusions-for-files-opened-by-specified-processes"></a>Belirtilen işlemlerle açılan dosyalar için dışlamalar listesini yapılandırma

### <a name="use-microsoft-intune-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Belirtilen Microsoft Intune açtığı dosyaları taramalardan dışarıda tutmak için Microsoft Intune kullanma

Daha [fazla bilgi için Intune'da Microsoft Intune](/intune/device-restrictions-configure) Windows 10 ve cihaz Microsoft Defender Virüsten Koruma için cihaz kısıtlama ayarlarını [yapılandırma'ya](/intune/device-restrictions-windows-10#microsoft-defender-antivirus) bakın.

### <a name="use-microsoft-endpoint-manager-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Belirtilen Microsoft Endpoint Manager açtığı dosyaları taramalardan dışarıda tutmak için Microsoft Endpoint Manager kullanma

Bkz[. Kötü amaçlı yazılım önleme ilkeleri oluşturma ve dağıtma:](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings) Kimlik bilgilerini yapılandırmayla ilgili ayrıntılar için Microsoft Endpoint Manager ayarları.

### <a name="use-group-policy-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Belirtilen işlemler tarafından açılmış dosyaları taramalardan dışarıda tutmak için Grup İlkesi kullanma

1. Grup İlkesi yönetim bilgisayarınızda Grup İlkesi Yönetim [Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'ye **tıklayın**.

2. Grup İlkesi **Yönetim Düzenleyicisi'nde Bilgisayar** **yapılandırması'ne gidin ve** Yönetim **şablonları'ne tıklayın**.

3. Dışlamalar'da **bileşenleri Windows için \> Microsoft Defender Virüsten Koruma \> genişletin**.

4. İşlem **Dışlamaları'ne çift** tıklayın ve dışlamaları ekleyin:
    1. Seçeneği Etkin olarak **ayarlayın**.
    2. Seçenekler bölümünün **altında** Göster **... seçeneğine tıklayın**.
    3. Her işlemi, Değer adı sütununu altına kendi **satırına** girin. Farklı türlerde işlem dışlamaları için örnek tabloya bakın. Tüm **işlemler için** Değer **sütununa** 0 girin.

5. **Tamam**'a tıklayın.

### <a name="use-powershell-cmdlets-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Belirtilen işlemler tarafından açılmış dosyaları taramalardan dışarıda tutmak için PowerShell cmdlet'lerini kullanma

İşlemler tarafından açılan dosyalar için PowerShell'in dışlamaları eklemek veya kaldırmak için, parametreyle üç cmdlet'in birleşiminin kullanımı `-ExclusionProcess` gerekir. Cmdlet'lerin hepsi [Defender modülündedir](/powershell/module/defender/).

Cmdlet'lerin biçimi:

```PowerShell
<cmdlet> -ExclusionProcess "<item>"
```

Aşağıdakilere şu şekilde izin verilir \<cmdlet\>:

<br/><br/>

|Yapılandırma eylemi|PowerShell cmdlet'i|
|---|---|
|Listeyi oluşturma veya üzerine yazma|`Set-MpPreference`|
|Listeye ekleme|`Add-MpPreference`|
|Listeden öğeleri kaldırma|`Remove-MpPreference`|

> [!IMPORTANT]
> with veya ile bir liste oluşturduysanız `Set-MpPreference` `Add-MpPreference`, `Set-MpPreference` cmdlet'i yeniden kullanarak varolan listenin üzerine yazabilirsiniz.

Örneğin, aşağıdaki kod parçacığı Microsoft Defender AV'nin belirtilen işlem tarafından açılan tüm dosyaları dışarıda tutmak için taramalarına neden olabilir:

```PowerShell
Add-MpPreference -ExclusionProcess "c:\internal\test.exe"
```

PowerShell'i Microsoft Defender Virüsten Koruma [cmdlet'leriyle](/powershell/module/defender) birlikte kullanma hakkında daha fazla bilgi için bkz. PowerShell cmdlet'leriyle virüsten Microsoft Defender Virüsten Koruma yönetme.

### <a name="use-windows-management-instruction-wmi-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Belirtilen Windows tarafından açılmış dosyaları taramalardan dışarıda tutmak için Windows Yönetim Yönergesi'ne (WMI) sahip komutlar kullanma

Sınıf [**sınıfınıza** **göre** aşağıdaki **özellikler** için MSFT_MpPreference](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)), Ekle ve Kaldır yöntemlerini kullanın:

```WMI
ExclusionProcess
```

Ayarla, **Ekle ve** **Kaldır'ın** **kullanımı**, PowerShell'daki karşılığına benzer: `Set-MpPreference`, ve `Add-MpPreference``Remove-MpPreference`.

Daha fazla bilgi ve izin verilen parametreler için [WMIv2 API'Windows Defender bakın](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal).

### <a name="use-the-windows-security-app-to-exclude-files-that-have-been-opened-by-specified-processes-from-scans"></a>Belirtilen Windows Güvenliği tarafından açılmış dosyaları taramalardan dışarıda tutmak için Windows Güvenliği uygulamasını kullanma

Yönergeler [için bkz. Windows Güvenliği Dışlamalar](microsoft-defender-security-center-antivirus.md) ekleme.

## <a name="use-wildcards-in-the-process-exclusion-list"></a>İşlem dışlama listesinde joker karakter kullanma

İşlem dışlama listesinde joker karakterlerin kullanımı, diğer dışlama listelerinde yaptıkları kullanımdan farklıdır.

Özellikle soru işareti (`?`) joker karakteri kullanılamaz ve yıldız (`*`) joker karakteri yalnızca tam yolun sonunda kullanılabilir. Süreç dışlama listesinde öğeleri tanımlarken joker `%ALLUSERSPROFILE%`karakter olarak ortam değişkenlerini (örneğin) kullanmaya devam edersiniz.

Aşağıdaki tabloda, joker karakterlerin işlem dışlama listesinde nasıl kullanıla bir açıklaması vardır:

<br/><br/>

|Joker karakter|Örnek kullanım|Örnek eşleşmeler|
|---|---|---|
|`*` (yıldız işareti) <p> Herhangi bir sayıda karakteri değiştirir|`C:\MyData\*`|Açılan herhangi bir dosya `C:\MyData\file.exe`|
|Ortam değişkenleri <p> Dışlama değerlendirilirken tanımlı değişken yol olarak doldurulur|`%ALLUSERSPROFILE%\CustomLogFiles\file.exe`|Açılan herhangi bir dosya `C:\ProgramData\CustomLogFiles\file.exe`|

## <a name="review-the-list-of-exclusions"></a>Dışlama listesini gözden geçirme

Dışlama listesinde MpCmdRun, PowerShell, [Microsoft Endpoint Configuration Manager,](/configmgr/protect/deploy-use/endpoint-antimalware-policies#exclusion-settings) [Intune](/intune/device-restrictions-configure) veya Windows Güvenliği [kullanabilirsiniz](microsoft-defender-security-center-antivirus.md).

PowerShell kullanıyorsanız, listeyi iki şekilde geri aekleyebilirsiniz:

- Tüm kullanıcı tercihlerinin Microsoft Defender Virüsten Koruma alın. Listelerin her biri ayrı satırlarda görüntülenir, ancak liste içindeki öğeler aynı satırda bir araya gelecektir.
- Tüm tercihlerin durumunu bir değişkene yazın ve yalnızca ilgilendiğiniz listeyi aramak için bu değişkeni kullanın. Kullanım her `Add-MpPreference` yeni satıra yazılır.

### <a name="validate-the-exclusion-list-by-using-mpcmdrun"></a>MpCmdRun kullanarak dışlama listesini doğrulama

Özel kullanım çizgi aracıyla [dışlamaları mpcmdrun.exe](./command-line-arguments-microsoft-defender-antivirus.md?branch=v-anbic-wdav-new-mpcmdrun-options), aşağıdaki komutu kullanın:

```DOS
MpCmdRun.exe -CheckExclusion -path <path>
```

> [!NOTE]
> MpCmdRun ile dışlamaların denetlenması için Microsoft Defender Virüsten Koruma CAMP sürüm 4.18.1812.3 (Aralık 2018'de yayınlandı) ve sonraki sürümler gerekir.

### <a name="review-the-list-of-exclusions-alongside-all-other-microsoft-defender-antivirus-preferences-by-using-powershell"></a>PowerShell kullanarak diğer tüm dışlamalar ve diğer Microsoft Defender Virüsten Koruma dışlamalar listesini gözden geçirme

Aşağıdaki cmdlet'i kullanın:

```PowerShell
Get-MpPreference
```

PowerShell'i Microsoft Defender Virüsten Koruma ile kullanma hakkında daha fazla bilgi için Microsoft Defender Virüsten Koruma [ve Microsoft Defender Virüsten Koruma cmdlet'lerini](/powershell/module/defender) yapılandırmak ve çalıştırmak için PowerShell [cmdlet'lerini](use-powershell-cmdlets-microsoft-defender-antivirus.md) kullanma Microsoft Defender Virüsten Koruma.

### <a name="retrieve-a-specific-exclusions-list-by-using-powershell"></a>PowerShell kullanarak belirli bir dışlamalar listesini alma

Aşağıdaki kod parçacığını kullanın (her satırı ayrı bir komut olarak girin); **WDAVprefs yerine** değişkeni isim etmek istediğiniz etiketle değiştirin:

```PowerShell
$WDAVprefs = Get-MpPreference
$WDAVprefs.ExclusionProcess
```

PowerShell'i Microsoft Defender Virüsten Koruma ile kullanma hakkında daha fazla bilgi için Microsoft Defender Virüsten Koruma [ve Microsoft Defender Virüsten Koruma cmdlet'lerini](/powershell/module/defender) yapılandırmak ve çalıştırmak için PowerShell [cmdlet'lerini](use-powershell-cmdlets-microsoft-defender-antivirus.md) kullanma Microsoft Defender Virüsten Koruma.

## <a name="related-articles"></a>İlgili makaleler

- [Taramalarda dışlamaları yapılandırma Microsoft Defender Virüsten Koruma doğrulama](configure-exclusions-microsoft-defender-antivirus.md)
- [Dosya adı, uzantı ve klasör konumu temel alarak dışlamaları yapılandırma ve doğrulama](configure-extension-file-exclusions-microsoft-defender-antivirus.md)
- [Windows Server'da Microsoft Defender Virüsten Koruma dışlamaları yapılandırma](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Dışlamaları tanımlarken kaçınılması gereken yaygın hatalar](common-exclusion-mistakes-microsoft-defender-antivirus.md)
- [Bu taramaları ve düzeltmeleri sonucunda Microsoft Defender Virüsten Koruma, başlatma ve gözden geçirme](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
