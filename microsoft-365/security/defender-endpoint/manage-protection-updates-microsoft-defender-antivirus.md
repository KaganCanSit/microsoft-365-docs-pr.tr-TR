---
title: Güncelleştirmelerin nasıl ve nerede Microsoft Defender Virüsten Koruma yönet
description: Koruma güncelleştirmelerini nasıl aldığına göre Microsoft Defender Virüsten Koruma geri dönüş siparişlerini yönetin.
keywords: güncelleştirmeler, güvenlik taban çizgilerini, koruma, temel sıralama, ADL, MMPC, UNC, dosya yolu, paylaşım, wsus
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
ms.openlocfilehash: c2ebb60d3cd5514d003991d26c5070b05e89fb37
ms.sourcegitcommit: e3bff611439354e6339bb666a88682078f32ec13
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2022
ms.locfileid: "63014347"
---
# <a name="manage-the-sources-for-microsoft-defender-antivirus-protection-updates"></a>Koruma güncelleştirmeleri için kaynakları Microsoft Defender Virüsten Koruma yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

<a id="protection-updates"></a>
<!-- this has been used as anchor in VDI content -->

Virüsten korumanızın güncel korunması çok önemlidir. Güvenlik güncelleştirmelerini yönetmek için iki Microsoft Defender Virüsten Koruma:

- *Güncelleştirmelerin* indirilma yeri; ve
- *Güncelleştirmeler* indirilir ve uygulandığında.

Bu makalede güncelleştirmelerin nereden indirilmeleri gerektiği (geri dönüş sırası olarak da bilinir) açıklanmıştır. [Güncelleştirmelerin Microsoft Defender Virüsten Koruma ve güncelleştirmelerin](manage-updates-baselines-microsoft-defender-antivirus.md) diğer yönlerini (güncelleştirme zamanlama gibi) yapılandırma hakkında genel bir bilgi için bkz. Microsoft Defender Virüsten Koruma güncelleştirmelerini yönetme ve taban çizgilerini uygulama.

> [!IMPORTANT]
> Microsoft Defender Virüsten Koruma Güvenlik zekası güncelleştirmeleri Windows Güncelleştirmesi ile teslim edilir ve 21 Ekim 2019 Pazartesi'den itibaren tüm güvenlik zekası güncelleştirmeleri SHA-2'ye özel olarak imzalanacak. Güvenlik zekanızı güncelleştirmek için cihazlarınızı SHA-2'ye destek olacak şekilde güncelleştirilmiş olması gerekir. Daha fazla bilgi edinmek için bkz[. Windows WSUS için 2019 SHA-2 Kod İmzalama Desteği gereksinimi](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus).

<a id="fallback-order"></a>

## <a name="fallback-order"></a>Geri dönüş sırası

Normalde, ağ yapılandırmanıza bağlı olarak uç noktaları birincil kaynaktan bireysel olarak güncelleştirmeleri ve ardından öncelik sırasına göre diğer kaynakları indirmek için yapılandırmanız gerekir. Güncelleştirmeler, kaynaklardan sizin belirttiğiniz sırada elde edilir. Geçerli kaynaktan gelen güncelleştirmeler güncel değilse, listede bir sonraki kaynak hemen kullanılır.

Güncelleştirmeler yayım geldiğinde, güncelleştirmenin boyutunu en aza indirmek için bir mantık uygulanır. Çoğu durumda, yalnızca en son güncelleştirme ile şu anda yüklü olan güncelleştirme (delta olarak adlandırılır) arasındaki farklar cihaza indirilir ve uygulanır. Öte yandan, deltanın boyutu iki ana faktöre bağlıdır:

- Cihaza son güncelleştirmenin yaşı; ve
- Güncelleştirmeleri indirmek ve uygulamak için kullanılan kaynak.

Uç noktanın güncelleştirmeleri ne kadar eskise, indirme de o kadar büyük olur. Öte yandan, indirme sıklığını da göz önünde bulundurarak değerlendirmeniz gerekir. Daha sık yapılan bir güncelleştirme zamanlaması daha fazla ağ kullanımına neden olabilir, ancak daha sık yapılan bir zamanlama indirme başına daha büyük dosya boyutlarına neden olabilir.

Uç noktanın güncelleştirmeleri nereden alaları gerektiğini belirtebilirsiniz:

- [Microsoft Update](https://support.microsoft.com/help/12373/windows-update-faq)
- [Windows Sunucu Güncelleştirme Hizmeti](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) <sup>[[1](#fn1)]<sup></sup>  
- [Microsoft Uç Noktası Yapılandırma Yöneticisi](/configmgr/core/servers/manage/updates)
- [Ağ dosyası paylaşımı](#unc-share)
- [Microsoft kötü amaçlı yazılımdan Microsoft Defender Virüsten Koruma için güvenlik zekası güncelleştirmeleri](https://www.microsoft.com/wdsi/defenderupdates) <sup>[[2](#fn1)]<sup></sup>

(<a id="fn1">1</a>) Intune İç Tanım Güncelleştirme Sunucusu - Microsoft Defender Virüsten Koruma için tanım güncelleştirmelerini almak üzere SCCM/SUP kullanırsanız ve istemci cihazlarında engellenen Windows Update'e erişmeniz gerekirse, birlikte yönetime geçişebilir ve uç nokta koruma iş yükünü Intune'a atabilirsiniz. Intune'da yapılandırılan kötü amaçlı yazılımdan koruma ilkesinde, şirket içi WSUS'u güncelleştirme kaynağı olarak kullanmak üzere yapılandırılan bir 'iç tanım güncelleştirme sunucusu' seçeneği vardır. Bu, resmi WU sunucusundan kuruluş için onaylanan güncelleştirmeleri denetlemenizi ve ayrıca proxy'ye yardımcı olur ve ağ trafiğinin resmi Windows UPdates ağına kaydetmenizi sağlar.

(<a id="fn1">2</a>) İlkeniz ve kayıt defteriniz bunun eski adı olan Microsoft Kötü Amaçlı Yazılımdan Koruma Merkezi (MMPC) güvenlik zekası olarak listelenmiş olabilir.

En iyi koruma düzeyini sağlamak için Microsoft Update hızlı sürümlere izin verir; bu da, sık sık daha küçük indirmeler anlamına gelir. Windows Server Update Service, Microsoft Endpoint Configuration Manager ve Microsoft güvenlik zekası güncelleştirme kaynakları daha az sık güncelleştirmeler sağlar. Dolayısıyla, delta büyük olabilir ve büyük indirmeler meydana getirir.

> [!IMPORTANT]
> Windows Server Update Service veya Microsoft Update'den sonra [Microsoft Security Intelligence](https://www.microsoft.com/security/portal/definitions/adl.aspx) sayfa güncelleştirmelerini geri dönüş kaynağı olarak ayardıysanız, güncelleştirmeler yalnızca geçerli güncelleştirmenin güncel olduğu kabul edilirse güvenlik zekası güncelleştirmelerinden indirilir. (Varsayılan olarak, bu gün arka arkaya yedi gündür ve Windows Server Update Service veya Microsoft Update hizmetlerinden güncelleştirmeleri uygulayama).
> Bununla birlikte, [korumanın güncel olduğu bildirmeden önceki gün sayısını da ayarlayın](/windows/threat-protection/microsoft-defender-antivirus/manage-outdated-endpoints-microsoft-defender-antivirus#set-the-number-of-days-before-protection-is-reported-as-out-of-date).<p>
> 21 Ekim 2019 Pazartesi'den itibaren güvenlik zekası güncelleştirmeleri SHA-2'ye özel olarak imzalanacak. En son güvenlik zekası güncelleştirmelerini almak için cihazların SHA-2'ye destek olacak şekilde güncelleştirilmiş olması gerekir. Daha fazla bilgi edinmek için bkz[. Windows WSUS için 2019 SHA-2 Kod İmzalama Desteği gereksinimi](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus).

Her kaynağın, aşağıdaki tabloda açıklandığı gibi güncelleştirmeleri ne sıklıkta yayımlalarına ek olarak, ağ ın nasıl yapılandırıldığına bağlı tipik senaryoları vardır:

<br/><br/>

|Konum|Örnek senaryo|
|---|---|
|Windows Server Update Service|Ağ bağlantınız için Windows yönetmek için Windows Server Update Service kullanıyorsanız.|
|Microsoft Update|Uç noktalarınızı doğrudan Microsoft Update'e bağlamak istiyor olun. Bu, kurumsal ağınıza düzenli olarak bağlanan uç noktalar için veya güncelleştirmelerinizi yönetmek için Windows Server Update Service kullanamıyorsanız yararlı olabilir.|
|Dosya paylaşımı|İnternet'e bağlı olmayan cihazlarınız (VM'ler gibi) vardır. İnternet bağlantılı VM ana makinenizi kullanarak, güncelleştirmeleri ağ paylaşımına indirebilir ve sanal sanal makinenizin güncelleştirmeleri buradan edinebilirsiniz. Dosya [paylaşımlarının sanal masaüstü altyapısı](deployment-vdi-microsoft-defender-antivirus.md) (VDI) ortamlarında nasıl kullanılayları için VDI dağıtım kılavuzuna bakın.|
|Microsoft Endpoint Manager|Microsoft Endpoint Manager'i kullanarak uç noktalarınızı güncelleştirebilirsiniz.|
|Güvenlik zekası güncelleştirmeleri Microsoft Defender Virüsten Koruma Microsoft kötü amaçlı yazılımdan koruma (eski adı MMPC)|[Cihazlarınızı SHA-2'ye destek olacak şekilde güncelleştirilmiş olduğundan emin olun](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus). Microsoft Defender Virüsten Koruma Güvenlik zekası güncelleştirmeleri Windows Update aracılığıyla teslim edilir ve 21 Ekim 2019 Pazartesi günü başlayacak olan güvenlik zekası güncelleştirmeleri SHA-2'ye özel olarak imzalanacak. <br/>En son bulaşma nedeniyle veya VDI dağıtımı için güçlü, temel bir görüntü sağlanmasına yardımcı olmak için en son koruma [güncelleştirmelerini indirin](deployment-vdi-microsoft-defender-antivirus.md). Bu seçenek genellikle birincil kaynak olarak değil, yalnızca son geri dönüş kaynağı olarak kullanılmalıdır. Bu yalnızca, güncelleştirmeler Windows Server Update Hizmeti'nden veya Microsoft Update'den belirtilen [sayıda gün boyunca indirilene kadar kullanılmalıdır](/windows/threat-protection/microsoft-defender-antivirus/manage-outdated-endpoints-microsoft-defender-antivirus#set-the-number-of-days-before-protection-is-reported-as-out-of-date).|

Grup İlkesi, Veri Kaynağı, PowerShell cmdlet'leri ve WMI ile güncelleştirme kaynaklarının Microsoft Endpoint Configuration Manager yönetabilirsiniz.

> [!IMPORTANT]
> Windows Server Update Service'i indirme konumu olarak ayarlıyorsanız, konumu belirtmek için hangi yönetim aracını kullanırsanız kullanın, güncelleştirmeleri onaylamanız gerekir. Windows Server Update Service ile otomatik bir onay kuralı kurabilirsiniz ve bu kural, güncelleştirmelerin günde en az bir kez gelmesinde yararlı olabilir. Daha fazla bilgi için bkz. [Tek başına Windows Server Update Service'te uç nokta koruma güncelleştirmelerini eşitleme](/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus).

Bu makaledeki yordamlarda önce sıranın nasıl ayar bölümü ve ardından Etkinleştirdiyseniz Dosya **paylaşımı seçeneğinin** nasıl ayar olduğu açıklanmıştır.

## <a name="use-group-policy-to-manage-the-update-location"></a>Güncelleştirme konumunu yönetmek için Grup İlkesi kullanma

1. Grup İlkesi yönetim makinenizin Grup İlkesi Yönetim [Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine sağ tıklayın ve Düzenle'ye **tıklayın**.

2. Grup İlkesi **Yönetim Düzenleyicisi'nde Bilgisayar** **yapılandırması'ne gidin**.

3. **İlkeler'e** **ve ardından Yönetim şablonları'ne tıklayın**.

4. İmza güncelleştirmeleri yapmak **Windows bileşenleri Windows Defender** \>  \> **ağacı genişletin** ve aşağıdaki ayarları yapılandırabilirsiniz:

   1. Güvenlik zekası **güncelleştirmelerini indirmek için kaynakların sıralamalarını tanımla ayarını çift tıklatın** ve seçeneği Etkin olarak **ayarlayın**.

   2. Aşağıdaki ekran görüntüsünde gösterildiği gibi, kaynakları tek bir boruyla ayrılmış olarak girin. `InternalDefinitionUpdateServer|MicrosoftUpdateServer|MMPC`

      :::image type="content" source="../../media/wdav-order-update-sources.png" alt-text="kaynakların sıralarını listeleen grup ilkesi ayarı.":::

   3. **Tamam**'ı seçin. Bu, koruma güncelleştirme kaynaklarının sıralamasını ayarlatır.

   4. Güvenlik zekası **güncelleştirmelerini indirmek için dosya paylaşımlarını tanımla ayarını çift** tıklatın ve seçeneği Etkin olarak **ayarlayın**.

   5. Dosya paylaşım kaynağını belirtin. Birden çok kaynağınız varsa, her kaynağı kullanılmaları gereken sırayla girin ve tek bir boruyla birbirinden ayırarak girin. Yol [üzerinde açıklama vermek için standart UNC](/openspecs/windows_protocols/ms-dtyp/62e862f4-2a51-452e-8eeb-dc4ff5ee33cc) notasyonu kullanın, örneğin: `\\host-name1\share-name\object-name|\\host-name2\share-name\object-name`. Hiçbir yol gir girersiniz, VM güncelleştirmeleri indirirken bu kaynak atlanır.

   6. **Tamam**'a tıklayın. Bu, Kaynaklar için sıra tanımla... grup ilkesi ayarında kaynak **başvurul olduğunda dosya paylaşımlarının** sıralamalarını ayarlar.

> [!NOTE]
> 1809'a kadar 1703 ve 1809 sürümleri olan Windows 10 için, ilke yolu **Windows Bileşenleri > Microsoft Defender Virüsten Koruma >** Sürüm 1903 olan Windows 10 için, ilke yolu Bileşenler **Windows olur > Microsoft Defender Virüsten Koruma > Zekası Güncelleştirmeleri**

## <a name="use-configuration-manager-to-manage-the-update-location"></a>Güncelleştirme konumunu yönetmek için Yapılandırma Yöneticisi'ni kullanma

Güvenlik [Zekası Güncelleştirmelerini Yapılandırma (Endpoint Protection](/configmgr/protect/deploy-use/endpoint-definition-updates) dalı) yapılandırma Microsoft Endpoint Manager için bkz. Güvenlik Microsoft Endpoint Manager Güncelleştirmeleri.

## <a name="use-powershell-cmdlets-to-manage-the-update-location"></a>Güncelleştirme konumunu yönetmek için PowerShell cmdlet'lerini kullanma

Güncelleştirme siparişlerini ayarlamak için aşağıdaki PowerShell cmdlet'lerini kullanın.

```PowerShell
Set-MpPreference -SignatureFallbackOrder {LOCATION|LOCATION|LOCATION|LOCATION}
Set-MpPreference -SignatureDefinitionUpdateFileSharesSource {\\UNC SHARE PATH|\\UNC SHARE PATH}
```

Daha fazla bilgi için aşağıdaki makalelere bakın:

- [Set-MpPreference -SignatureFallbackOrder](/powershell/module/defender/set-mppreference)
- [Set-MpPreference -SignatureDefinitionUpdateFileSharesSource](/powershell/module/defender/set-mppreference#-signaturedefinitionupdatefilesharessources)
- [PowerShell cmdlet'lerini kullanarak bu cmdlet'leri yapılandırma ve Microsoft Defender Virüsten Koruma](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Defender Virüsten Koruma cmdlet'leri](/powershell/module/defender/index)

## <a name="use-windows-management-instruction-wmi-to-manage-the-update-location"></a>Güncelleştirme Windows yönetmek için YÖNETICI Yönergesi (WMI) kullanma

Aşağıdaki [**özellikler** için sınıf **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) Set yöntemini kullanın:

```WMI
SignatureFallbackOrder
SignatureDefinitionUpdateFileSharesSource
```

Daha fazla bilgi için aşağıdaki makalelere bakın:

- [Windows Defender WMIv2 API'leri](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="use-mobile-device-management-mdm-to-manage-the-update-location"></a>Güncelleştirme konumunu yönetmek için Mobil Cihaz Yönetimi'ne (MDM) sahip olun

[MDM'yi yapılandırmayla ilgili ayrıntılar için bkz. İLKe CSP - Defender/SignatureUpdateFallbackOrder](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdatefallbackorder).

## <a name="what-if-were-using-a-third-party-vendor"></a>Üçüncü taraf bir satıcı kullanıyoruzsa ne olur?

Bu makalede, her güncelleştirme için güncelleştirmelerin nasıl yapılandırıldığında ve Microsoft Defender Virüsten Koruma. Bununla birlikte, üçüncü taraf satıcılar bu görevleri gerçekleştirmek için kullanılabilir.

Örneğin, Contoso'un fabrikam'ı güvenlik çözümlerini yönetmesi için işe işe Microsoft Defender Virüsten Koruma. Fabrikam genellikle [yamaları ve güncelleştirmeleri](./use-wmi-microsoft-defender-antivirus.md) dağıtmak Windows Yönetim Aracı, [PowerShell cmdlet'leri](./use-powershell-cmdlets-microsoft-defender-antivirus.md) [veya Windows](./command-line-arguments-microsoft-defender-antivirus.md) komut satırı kullanır.

> [!NOTE]
> Microsoft, üçüncü taraf çözümlerini test Microsoft Defender Virüsten Koruma.

<a id="unc-share"></a>

## <a name="create-a-unc-share-for-security-intelligence-updates"></a>Güvenlik zekası güncelleştirmeleri için bir UNC paylaşımı oluşturma

Zamanlanmış bir görev kullanarak MMPC sitesinden güvenlik zekası güncelleştirmelerini indirmek için bir ağ dosya paylaşımı (UNC/eşlenmiş sürücü) ayarlayın.

1. Paylaşımı hazır yapmak ve güncelleştirmeleri indirmek istediğiniz sistemde, betiği kaydedecek bir klasör oluşturun.

    ```console
    Start, CMD (Run as admin)
    MD C:\Tool\PS-Scripts\
    ```

2. İmza güncelleştirmelerini kaydetmek istediğiniz klasörü oluşturun.

    ```console
    MD C:\Temp\TempSigs\x64
    MD C:\Temp\TempSigs\x86
    ```

3. Dosyadan PowerShell betiği [www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4](https://www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4).

4. El ile **İndir'e tıklayın**.

5. Ham **nupkg dosyasını indir'e tıklayın**.

6. Dosyayı ayıkla.

7. Dosya dosyasını SignatureDownloadCustomTask.ps1, önceden oluşturduğunuz klasöre kopyalayın `C:\Tool\PS-Scripts\` .

8. Zamanlanmış görevi ayarlamak için komut çizgilerini kullanın.

   > [!NOTE]
   > İki tür güncelleştirme vardır: tam ve delta.

   - x64 delta için:

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x64 -isDelta $true -destDir C:\Temp\TempSigs\x64 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - Tam x64 için:

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
   > Zamanlanmış görevler oluşturulduğunda, bunları altında Görev Zamanlayıcı'da bulabilirsiniz `Microsoft\Windows\Windows Defender`.

9. Her görevi el ile çalıştırın ve aşağıdaki klasörlerde (`mpam-d.exe`, `mpam-fe.exe`ve `nis_full.exe`) verileriniz olduğunu doğrulayın (farklı konumlar seçmiş olabilirsiniz):

   - `C:\Temp\TempSigs\x86`
   - `C:\Temp\TempSigs\x64`

   Zamanlanan görev başarısız olursa, aşağıdaki komutları çalıştırın:

    ```console
    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x64 -isDelta $False -destDir C:\Temp\TempSigs\x64"

    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x64 -isDelta $True -destDir C:\Temp\TempSigs\x64"

    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x86 -isDelta $False -destDir C:\Temp\TempSigs\x86"

    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x86 -isDelta $True -destDir C:\Temp\TempSigs\x86"
    ```

    > [!NOTE]
    > Sorunlar yürütme ilkesiden de olabilir.

10. Paylaşıma işaret edecek bir paylaşım `C:\Temp\TempSigs` oluşturma (örn. `\\server\updates`).

    > [!NOTE]
    > En azından, kimliği doğrulanmış kullanıcıların "Okuma" erişimi olması gerekir. Bu gereksinim etki alanı bilgisayarları, paylaşım ve NTFS (güvenlik) için de geçerlidir.

11. İlkede paylaşım konumunu paylaşım olarak ayarlayın.

    > [!NOTE]
    > Yola x64 (veya x86) klasörünü ekleme. Aşağıdaki mpcmdrun.exe bunu otomatik olarak ekler.

## <a name="related-articles"></a>İlgili makaleler

- [Dağıtım Microsoft Defender Virüsten Koruma](deploy-manage-report-microsoft-defender-antivirus.md)
- [Güncelleştirmeleri Microsoft Defender Virüsten Koruma ve taban çizgilerini uygulama](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Güncel olan uç nokta güncelleştirmelerini yönetme](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Olay tabanlı zorunlu güncelleştirmeleri yönetme](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Mobil cihazlar ve VM'ler için güncelleştirmeleri yönetme](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
