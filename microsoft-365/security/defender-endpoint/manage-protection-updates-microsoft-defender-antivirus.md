---
title: Microsoft Defender Virüsten Koruma güncelleştirmeleri nasıl ve nereden alacağını yönetme
description: Microsoft Defender Virüsten Koruma koruma güncelleştirmelerini nasıl aldığına ilişkin geri dönüş sırasını yönetin.
keywords: güncelleştirmeler, güvenlik temelleri, koruma, geri dönüş sırası, ADL, MMPC, UNC, dosya yolu, paylaşım, wsus
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.reviewer: pahuijbr
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: 9af3694f530660ead6f10008e1642990a20cc0a6
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416628"
---
# <a name="manage-the-sources-for-microsoft-defender-antivirus-protection-updates"></a>Microsoft Defender Virüsten Koruma güncelleştirmeleri için kaynakları yönetin

> [!IMPORTANT]
> Mart 2022 Microsoft Defender altyapı güncelleştirmesini (**1.1.19100.5**) uygulayan müşteriler yüksek kaynak kullanımıyla (CPU ve/veya bellek) karşılaşmış olabilir. Microsoft, önceki sürümde sunulan hataları gideren bir güncelleştirme (**1.1.19200.5**) yayımladı. Müşterilerin Virüsten Koruma Altyapısı'nın bu yeni altyapı derlemesine (**1.1.19200.5**) güncelleştirmeleri önerilir. Performans sorunlarının tamamen düzeltildiğinden emin olmak için, güncelleştirme uygulandıktan sonra makinelerin yeniden başlatılması önerilir. Daha fazla bilgi için bkz. [Aylık platform ve altyapı sürümleri](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions).

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

<a id="protection-updates"></a>
<!-- this has been used as anchor in VDI content -->

Virüsten korumanızı güncel tutmak kritik öneme sahiptir. Microsoft Defender Virüsten Koruma için koruma güncelleştirmelerini yönetmek için iki bileşen vardır:

- Güncelleştirmelerin *nereden* indirildiği; Ve
- Güncelleştirmeler *indirildiğinde* ve uygulandığında.

Bu makalede güncelleştirmelerin nereden indirileceğinin nasıl belirtileceği açıklanır (bu, geri dönüş sırası olarak da bilinir). [Güncelleştirmelerin nasıl çalıştığına ve güncelleştirmelerin diğer yönlerini (güncelleştirmeleri](manage-updates-baselines-microsoft-defender-antivirus.md) zamanlama gibi) nasıl yapılandıracağınız hakkında genel bir bakış için güncelleştirmeleri Microsoft Defender Virüsten Koruma güncelleştirmeleri yönetme ve temelleri uygulama konusuna bakın.

> [!IMPORTANT]
> Microsoft Defender Virüsten Koruma Güvenlik bilgileri güncelleştirmeleri ve platform güncelleştirmeleri Windows Update üzerinden teslim edilir ve 21 Ekim 2019 Pazartesi gününden itibaren tüm güvenlik bilgileri güncelleştirmeleri sha-2 özel olarak imzalanır. Güvenlik zekanızı güncelleştirmek için cihazlarınız SHA-2'yi destekleyecek şekilde güncelleştirilmelidir. Daha fazla bilgi edinmek için bkz[. Windows ve WSUS için 2019 SHA-2 Kod İmzalama Desteği gereksinimi](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus).

<a id="fallback-order"></a>

## <a name="fallback-order"></a>Geri dönüş sırası

Genellikle uç noktaları birincil kaynaktan güncelleştirmeleri ve ardından diğer kaynakları öncelik sırasına göre ağ yapılandırmanıza göre tek tek indirecek şekilde yapılandırabilirsiniz. Güncelleştirmeler kaynaklardan belirttiğiniz sırayla alınır. Geçerli kaynaktan yapılan güncelleştirmeler güncel değilse, listedeki bir sonraki kaynak hemen kullanılır.

Güncelleştirmeler yayımlandığında, güncelleştirmenin boyutunu en aza indirmek için bazı mantık uygulanır. Çoğu durumda, cihazda yalnızca en son güncelleştirme ile yüklü olan güncelleştirme (delta olarak adlandırılır) arasındaki farklar indirilir ve uygulanır. Ancak, deltanın boyutu iki ana faktöre bağlıdır:

- Cihazdaki son güncelleştirmenin yaşı; Ve
- Güncelleştirmeleri indirmek ve uygulamak için kullanılan kaynak.

Bir uç noktadaki güncelleştirmeler ne kadar eskiyse indirme de o kadar büyük olur. Ancak indirme sıklığını da göz önünde bulundurmanız gerekir. Daha sık bir güncelleştirme zamanlaması daha fazla ağ kullanımına neden olabilirken, daha az sık yapılan bir zamanlama indirme başına daha büyük dosya boyutlarına neden olabilir.

Bir uç noktanın güncelleştirmeleri nereden edineceğini belirtebileceğiniz beş konum vardır:

- [Microsoft Update](https://support.microsoft.com/help/12373/windows-update-faq)
- [Windows Sunucu Güncelleştirme Hizmeti](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) <sup>[[1](#fn1)]<sup></sup>  
- [Microsoft Uç Noktası Yapılandırma Yöneticisi](/configmgr/core/servers/manage/updates)
- [Ağ dosya paylaşımı](#unc-share)
- [Microsoft Defender Virüsten Koruma ve diğer Microsoft kötü amaçlı yazılımdan](https://www.microsoft.com/wdsi/defenderupdates) <sup>koruma için güvenlik bilgileri güncelleştirmeleri [[2](#fn1)]<sup></sup>

(<a id="fn1">1</a>) İç Tanım Güncelleştirme Sunucusu'nu Intune - Microsoft Defender Virüsten Koruma tanım güncelleştirmelerini almak için SCCM/SUP kullanıyorsanız ve istemci cihazlarda engellenen cihazlarda Windows Update erişmeniz gerekiyorsa, ortak yönetime geçiş yapabilir ve uç nokta koruma iş yükünü Intune boşaltabilirsiniz. Intune'de yapılandırılan kötü amaçlı yazılımdan koruma ilkesinde, güncelleştirme kaynağı olarak şirket içi WSUS kullanacak şekilde yapılandırılabilir 'iç tanım güncelleştirme sunucusu' seçeneği vardır. Bu, resmi WU sunucusundan gelen hangi güncelleştirmelerin kuruluş için onaylanıp onaylanmayacaklarını denetlemenize ve ayrıca ağ trafiğinin resmi Windows UPdates ağına proxy ve kaydedilmesine yardımcı olur.

(<a id="fn1">2</a>) İlkeniz ve kayıt defterinizde bu, eski adıyla Microsoft Kötü Amaçlı Yazılımdan Koruma Merkezi (MMPC) güvenlik bilgileri olarak listelenmiş olabilir.

Microsoft Update, en iyi koruma düzeyini sağlamak için hızlı sürümlere izin verir ve bu da sık sık daha küçük indirmeler anlamına gelir. Windows Sunucu Güncelleştirme Hizmeti, Microsoft Endpoint Configuration Manager, Microsoft güvenlik bilgileri güncelleştirmeleri ve platform güncelleştirmeleri kaynakları daha az sıklıkta güncelleştirmeler sunar. Bu nedenle, delta daha büyük olabilir ve bu da daha büyük indirmelere neden olur.

> [!NOTE]
> Güvenlik bilgileri güncelleştirmeleri altyapı güncelleştirmelerini içerir ve aylık tempoda yayımlar.
Güvenlik bilgileri güncelleştirmeleri de günde birden çok kez teslim edilir, ancak bu paket bir altyapı içermez.


> [!IMPORTANT]
> [Microsoft Güvenlik bilgileri sayfası](https://www.microsoft.com/security/portal/definitions/adl.aspx) güncelleştirmelerini Windows Sunucu Güncelleştirme Hizmeti veya Microsoft Update'ten sonra bir geri dönüş kaynağı olarak ayarladıysanız, güncelleştirmeler yalnızca geçerli güncelleştirme güncel değil olarak kabul edildiğinde güvenlik bilgileri güncelleştirmelerinden ve platform güncelleştirmelerinden indirilir. (Varsayılan olarak, Windows Server Update Service veya Microsoft Update hizmetlerinden güncelleştirmeleri uygulayamamanın art arda yedi günüdür).
> Ancak [korumanın güncel olmayan olarak raporlanacağı gün sayısını ayarlayabilirsiniz](/windows/threat-protection/microsoft-defender-antivirus/manage-outdated-endpoints-microsoft-defender-antivirus#set-the-number-of-days-before-protection-is-reported-as-out-of-date).<p>
> 21 Ekim 2019 Pazartesi gününden itibaren güvenlik bilgileri güncelleştirmeleri ve platform güncelleştirmeleri sha-2 özel olarak imzalanacaktır. En son güvenlik bilgileri güncelleştirmelerini ve platform güncelleştirmelerini almak için cihazların SHA-2'yi destekleyecek şekilde güncelleştirilmesi gerekir. Daha fazla bilgi edinmek için bkz[. Windows ve WSUS için 2019 SHA-2 Kod İmzalama Desteği gereksinimi](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus).

Her kaynağın, aşağıdaki tabloda açıklandığı gibi güncelleştirmeleri yayımlama sıklıklarına ek olarak ağınızın nasıl yapılandırıldığına bağlı tipik senaryoları vardır:

<br/><br/>

|Konum|Örnek senaryo|
|---|---|
|Windows Sunucusu Güncelleştirme Hizmeti|Ağınıza yönelik güncelleştirmeleri yönetmek için Windows Sunucu Güncelleştirme Hizmeti kullanıyorsunuz.|
|Microsoft Update|Uç noktalarınızın doğrudan Microsoft Update'e bağlanmasını istiyorsunuz. Bu, kurumsal ağınıza düzensiz olarak bağlanan uç noktalar için veya güncelleştirmelerinizi yönetmek için Windows Sunucu Güncelleştirme Hizmeti'ni kullanmıyorsanız yararlı olabilir.|
|Dosya paylaşımı|İnternet'e bağlı olmayan cihazlarınız (VM'ler gibi) var. Güncelleştirmeleri vm'lerin edinebileceği bir ağ paylaşımına indirmek için İnternet'e bağlı VM ana bilgisayarınızı kullanabilirsiniz. Dosya paylaşımlarının sanal masaüstü altyapısı (VDI) ortamlarında nasıl kullanılabileceğini öğrenmek için VDI [dağıtım kılavuzuna](deployment-vdi-microsoft-defender-antivirus.md) bakın.|
|Microsoft Endpoint Manager|Uç noktalarınızı güncelleştirmek için Microsoft Endpoint Manager kullanıyorsunuz.|
|Microsoft Defender Virüsten Koruma ve diğer Microsoft kötü amaçlı yazılımdan koruma (eski adı MMPC) için güvenlik bilgileri güncelleştirmeleri ve platform güncelleştirmeleri|[Cihazlarınızın SHA-2'yi destekleyecek şekilde güncelleştirildiğinden emin olun](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus). Microsoft Defender Virüsten Koruma Güvenlik bilgileri ve platform güncelleştirmeleri Windows Update aracılığıyla sunulur ve 21 Ekim 2019 Pazartesi'den itibaren güvenlik bilgileri güncelleştirmeleri ve platform güncelleştirmeleri sha-2 özel olarak imzalanır. <br/>En son bulaşma nedeniyle veya [VDI dağıtımı](deployment-vdi-microsoft-defender-antivirus.md) için güçlü, temel bir görüntü sağlamaya yardımcı olmak için en son koruma güncelleştirmelerini indirin. Bu seçenek genellikle birincil kaynak olarak değil yalnızca son geri dönüş kaynağı olarak kullanılmalıdır. Yalnızca güncelleştirmeler [belirtilen sayıda gün](/microsoft-365/security/defender-endpoint/manage-outdated-endpoints-microsoft-defender-antivirus#set-the-number-of-days-before-protection-is-reported-as-out-of-date) boyunca Windows Sunucu Güncelleştirme Hizmeti'nden veya Microsoft Update'ten indirilemiyorsa kullanılır.|

Güncelleştirme kaynaklarının grup ilkesi, Microsoft Endpoint Configuration Manager, PowerShell cmdlet'leri ve WMI ile kullanılma sırasını yönetebilirsiniz.

> [!IMPORTANT]
> Windows Sunucu Güncelleştirme Hizmeti'ni indirme konumu olarak ayarlarsanız, konumu belirtmek için kullandığınız yönetim aracından bağımsız olarak güncelleştirmeleri onaylamanız gerekir. Windows Sunucu Güncelleştirme Hizmeti ile otomatik bir onay kuralı ayarlayabilirsiniz. Bu, güncelleştirmeler günde en az bir kez geldiğinde yararlı olabilir. Daha fazla bilgi için bkz. [Tek başına Windows Sunucu Güncelleştirme Hizmeti'nde uç nokta koruma güncelleştirmelerini eşitleme](/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus).

Bu makaledeki yordamlarda önce sıranın nasıl ayarlanacağı ve ardından etkinleştirdiyseniz **Dosya paylaşımı** seçeneğinin nasıl ayarlanacağı açıklanmaktadır.

## <a name="use-group-policy-to-manage-the-update-location"></a>Güncelleştirme konumunu yönetmek için grup ilkesi kullanma

1. grup ilkesi yönetim makinenizde [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **Düzenle'ye** tıklayın.

2. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin.

3. **İlkeler'e** ve ardından **Yönetim şablonları'nı** tıklatın.

4. **İmza güncelleştirmeleri** **Windows Defender bileşenleri** \> **Windows** \> için ağacı genişletin ve aşağıdaki ayarları yapılandırın:

   1. **Güvenlik bilgileri güncelleştirmelerini indirmek için kaynakların sırasını tanımla** ayarına çift tıklayın ve seçeneği **Etkin** olarak ayarlayın.

   2. Aşağıdaki ekran görüntüsünde gösterildiği gibi, kaynakların sırasını tek bir kanalla ayırarak girin. Örneğin: `InternalDefinitionUpdateServer|MicrosoftUpdateServer|MMPC`.

      :::image type="content" source="../../media/wdav-order-update-sources.png" alt-text="Kaynak sırasını listeleyen grup ilkesi ayarı" lightbox="../../media/wdav-order-update-sources.png":::

   3. **Tamam**'ı seçin. Bu, koruma güncelleştirme kaynaklarının sırasını ayarlar.

   4. **Güvenlik bilgileri güncelleştirmelerini indirmek için dosya paylaşımlarını tanımla** ayarına çift tıklayın ve seçeneği **Etkin** olarak ayarlayın.

   5. Dosya paylaşımı kaynağını belirtin. Birden çok kaynağınız varsa, her kaynağı tek bir kanalla ayrılmış olarak kullanılacak sırayla girin. Yolu ifade eden [standart UNC gösterimini](/openspecs/windows_protocols/ms-dtyp/62e862f4-2a51-452e-8eeb-dc4ff5ee33cc) kullanın, örneğin: `\\host-name1\share-name\object-name|\\host-name2\share-name\object-name`. Herhangi bir yol girmezseniz, VM güncelleştirmeleri indirdiğinde bu kaynak atlanır.

   6. **Tamam**'a tıklayın. Bu, **Kaynak sırasını tanımla...** grup ilkesi ayarında bu kaynağa başvurulduğunda dosya paylaşımlarının sırasını ayarlar.

> [!NOTE]
> Windows 10 İlke yolu, 1809'a kadar olan ve 1809'a kadar olan 1703 sürümleri için Windows **Bileşenler > Microsoft Defender Virüsten Koruma > İmza Güncelleştirmeleri** Windows 10, sürüm 1903 için ilke yolu bileşenler **Windows > güvenlik bilgileri güncelleştirmelerini Microsoft Defender Virüsten Koruma >**

## <a name="use-configuration-manager-to-manage-the-update-location"></a>Güncelleştirme konumunu yönetmek için Configuration Manager kullanma

Microsoft Endpoint Manager (geçerli dalı) yapılandırmayla ilgili ayrıntılar için bkz[. Endpoint Protection için Güvenlik bilgileri Güncelleştirmelerini](/configmgr/protect/deploy-use/endpoint-definition-updates) Yapılandırma.

## <a name="use-powershell-cmdlets-to-manage-the-update-location"></a>Güncelleştirme konumunu yönetmek için PowerShell cmdlet'lerini kullanma

Güncelleştirme sırasını ayarlamak için aşağıdaki PowerShell cmdlet'lerini kullanın.

```PowerShell
Set-MpPreference -SignatureFallbackOrder {LOCATION|LOCATION|LOCATION|LOCATION}
Set-MpPreference -SignatureDefinitionUpdateFileSharesSource {\\UNC SHARE PATH|\\UNC SHARE PATH}
```

Daha fazla bilgi için aşağıdaki makalelere bakın:

- [Set-MpPreference -SignatureFallbackOrder](/powershell/module/defender/set-mppreference)
- [Set-MpPreference -SignatureDefinitionUpdateFileSharesSource](/powershell/module/defender/set-mppreference#-signaturedefinitionupdatefilesharessources)
- [Microsoft Defender Virüsten Koruma yapılandırmak ve çalıştırmak için PowerShell cmdlet'lerini kullanma](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Defender Virüsten Koruma cmdlet'leri](/powershell/module/defender/index)

## <a name="use-windows-management-instruction-wmi-to-manage-the-update-location"></a>Güncelleştirme konumunu yönetmek için Windows Yönetim Yönergesi'ni (WMI) kullanma

Aşağıdaki özellikler için [**MSFT_MpPreference** sınıfının **Set** yöntemini](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) kullanın:

```WMI
SignatureFallbackOrder
SignatureDefinitionUpdateFileSharesSource
```

Daha fazla bilgi için aşağıdaki makalelere bakın:

- [WMIv2 API'lerini Windows Defender](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="use-mobile-device-management-mdm-to-manage-the-update-location"></a>Güncelleştirme konumunu yönetmek için Mobile Cihaz Yönetimi (MDM) kullanma

MDM'yi yapılandırmayla ilgili ayrıntılar için bkz. [İlke CSP - Defender/SignatureUpdateFallbackOrder](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdatefallbackorder) .

## <a name="what-if-were-using-a-third-party-vendor"></a>Üçüncü taraf satıcı kullanıyorsak ne olur?

Bu makalede, Microsoft Defender Virüsten Koruma güncelleştirmelerinin nasıl yapılandırıldığı ve yönetileceğini açıklanmaktadır. Ancak, bu görevleri gerçekleştirmek için üçüncü taraf satıcılar kullanılabilir.

Örneğin Contoso'nun Microsoft Defender Virüsten Koruma içeren güvenlik çözümünü yönetmek için Fabrikam'ı işe aldığını varsayalım. Fabrikam genellikle düzeltme eklerini ve güncelleştirmeleri dağıtmak için [Windows Yönetim Araçları](./use-wmi-microsoft-defender-antivirus.md), [PowerShell cmdlet'leri](./use-powershell-cmdlets-microsoft-defender-antivirus.md) veya [Windows komut satırı](./command-line-arguments-microsoft-defender-antivirus.md) kullanır.

> [!NOTE]
> Microsoft, Microsoft Defender Virüsten Koruma yönetmek için üçüncü taraf çözümleri test etmez.

<a id="unc-share"></a>

## <a name="create-a-unc-share-for-security-intelligence-and-platform-updates"></a>Güvenlik bilgileri ve platform güncelleştirmeleri için UNC paylaşımı oluşturma

Zamanlanmış bir görev kullanarak MMPC sitesinden güvenlik zekası ve platform güncelleştirmelerini indirmek için bir ağ dosya paylaşımı (UNC/eşlenmiş sürücü) ayarlayın.

1. Paylaşımı sağlamak ve güncelleştirmeleri indirmek istediğiniz sistemde, betiği kaydedebileceğiniz bir klasör oluşturun.

    ```console
    Start, CMD (Run as admin)
    MD C:\Tool\PS-Scripts\
    ```

2. İmza güncelleştirmelerini kaydedebileceğiniz klasörü oluşturun.

    ```console
    MD C:\Temp\TempSigs\x64
    MD C:\Temp\TempSigs\x86
    ```

3. [PowerShell](https://www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4) betiğini www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4'den indirin.

4. **El ile İndir'e** tıklayın.

5. **Ham nupkg dosyasını indir'e** tıklayın.

6. Dosyayı ayıklayın.

7. SignatureDownloadCustomTask.ps1 dosyasını daha önce oluşturduğunuz `C:\Tool\PS-Scripts\` klasöre kopyalayın.

8. Zamanlanmış görevi ayarlamak için komut satırını kullanın.

   > [!NOTE]
   > İki tür güncelleştirme vardır: tam ve delta.

   - x64 delta için:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x64 -isDelta $true -destDir C:\Temp\TempSigs\x64 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - x64 tam için:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x64 -isDelta $false -destDir C:\Temp\TempSigs\x64 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - x86 delta için:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x86 -isDelta $true -destDir C:\Temp\TempSigs\x86 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - x86 tam için:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x86 -isDelta $false -destDir C:\Temp\TempSigs\x86 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   > [!NOTE]
   > Zamanlanmış görevler oluşturulduğunda, bunları altındaki `Microsoft\Windows\Windows Defender`Görev Zamanlayıcı'da bulabilirsiniz.

9. Her görevi el ile çalıştırın ve aşağıdaki klasörlerde (`mpam-d.exe`, `mpam-fe.exe`ve `nis_full.exe`) veriniz olduğunu doğrulayın (farklı konumlar seçmiş olabilirsiniz):

   - `C:\Temp\TempSigs\x86`
   - `C:\Temp\TempSigs\x64`

   Zamanlanan görev başarısız olursa aşağıdaki komutları çalıştırın:

    ```console
    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x64 -isDelta $False -destDir C:\Temp\TempSigs\x64"

    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x64 -isDelta $True -destDir C:\Temp\TempSigs\x64"

    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x86 -isDelta $False -destDir C:\Temp\TempSigs\x86"

    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x86 -isDelta $True -destDir C:\Temp\TempSigs\x86"
    ```

    > [!NOTE]
    > Sorunlar yürütme ilkesinden de kaynaklanıyor olabilir.

10. öğesini işaret eden `C:\Temp\TempSigs` bir paylaşım oluşturun (örneğin, `\\server\updates`).

    > [!NOTE]
    > Kimliği doğrulanmış kullanıcıların en azından "Okuma" erişimi olmalıdır. Bu gereksinim etki alanı bilgisayarları, paylaşım ve NTFS (güvenlik) için de geçerlidir.

11. İlkedeki paylaşım konumunu paylaşım olarak ayarlayın.

    > [!NOTE]
    > Yola x64 (veya x86) klasörünü eklemeyin. mpcmdrun.exe işlemi otomatik olarak ekler.

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)

## <a name="related-articles"></a>İlgili makaleler

- [Microsoft Defender Virüsten Koruma dağıtma](deploy-manage-report-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma güncelleştirmelerini yönetme ve temelleri uygulama](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Güncel olmayan uç noktalar için güncelleştirmeleri yönetme](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Olay tabanlı zorunlu güncelleştirmeleri yönetin](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Mobil cihazlar ve VM'ler için güncelleştirmeleri yönetme](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Windows 10'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
