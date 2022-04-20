---
title: 21Vianet tarafından sağlanan Office 365 için Azure Information Protection desteği
f1.keywords:
- NOCSH
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- GEU150
- GEA150
description: 21Vianet tarafından sağlanan Office 365 için Azure Information Protection (AIP) ve Çin'deki müşteriler için yapılandırma hakkında daha fazla bilgi edinin.
monikerRange: o365-21vianet
ms.openlocfilehash: 0f495139a807d4a0eeb3181626717c6d5061fc38
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64935225"
---
# <a name="azure-information-protection-support-for-office-365-operated-by-21vianet"></a>21Vianet tarafından sağlanan Office 365 için Azure Information Protection desteği

Bu makale, 21Vianet tarafından sağlanan Office 365 için Azure Information Protection (AIP) desteği ile ticari teklifler arasındaki farkların yanı sıra Çin'deki&mdash; müşteriler için AIP'yi yapılandırmaya yönelik özel yönergelerin yanı sıra AIP şirket içi tarayıcısını yükleme ve içerik tarama işlerini yönetme adımlarını kapsar.

## <a name="differences-between-aip-for-office-365-operated-by-21vianet-and-commercial-offerings"></a>21Vianet tarafından sağlanan Office 365 için AIP ile ticari teklifler arasındaki farklar

Hedefimiz, 21Vianet tarafından sağlanan Office 365 için AIP teklifimizle tüm ticari özellikleri ve işlevleri Çin'deki müşterilere sunmak olsa da, vurgulamak istediğimiz bazı eksik işlevler vardır.

Aşağıdaki liste, 21Vianet tarafından sağlanan Office 365 için AIP ile Ocak 2021 itibarıyla ticari tekliflerimiz arasındaki mevcut boşlukları içerir:

- Active Directory Rights Management Services (AD RMS) şifrelemesi yalnızca Kurumlar için Microsoft 365 Uygulamaları (derleme 11731.10000 veya üzeri) desteklenir. Office Professional Plus AD RMS'i desteklemez.

- AD RMS'den AIP'ye geçiş şu anda kullanılamıyor.
  
- Korumalı e-postaların ticari buluttaki kullanıcılarla paylaşılması desteklenir.
  
- Belgelerin ve e-posta eklerinin ticari buluttaki kullanıcılarla paylaşılması şu anda kullanılamıyor. Buna ticari buluttaki 21Vianet kullanıcısı tarafından sağlanan Office 365, ticari buluttaki 21Vianet kullanıcıları tarafından sağlanan Office 365 olmayan kullanıcılar ve Kişiler için RMS lisansına sahip kullanıcılar dahildir.
  
- SharePoint (IRM korumalı siteler ve kitaplıklar) bulunan IRM şu anda kullanılamıyor.
  
- AD RMS için Mobil Cihaz Uzantısı şu anda kullanılamıyor.

- [Mobil Görüntüleyici](/azure/information-protection/rms-client/mobile-app-faq), Azure China 21Vianet tarafından desteklenmez.

- Azure portal AIP alanı Çin'deki müşteriler tarafından kullanılamaz. İçerik tarama işlerinizi yönetme ve çalıştırma gibi eylemleri portalda gerçekleştirmek yerine [PowerShell komutlarını](#step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs) kullanın.

- 21Vianet tarafından sağlanan Office 365'deki AIP uç noktaları, diğer bulut hizmetleri için gereken uç noktalardan farklıdır. İstemcilerden aşağıdaki uç noktalara ağ bağlantısı gereklidir:
    - Etiket ve etiket ilkelerini indirin: `*.protection.partner.outlook.cn`
    - Azure Rights Management hizmeti: `*.aadrm.cn`

## <a name="configure-aip-for-customers-in-china"></a>Çin'deki müşteriler için AIP'yi yapılandırma

AIP'yi Çin'deki müşteriler için yapılandırmak için:
1. [Kiracı için Rights Management'i etkinleştirin](#step-1-enable-rights-management-for-the-tenant).

1. [Microsoft Purview Information Protection Eşitleme Hizmeti hizmet sorumlusunu ekleyin](#step-2-add-the-microsoft-purview-information-protection-sync-service-service-principal).

1. [DNS şifrelemeyi yapılandırma](#step-3-configure-dns-encryption).

1. [AIP birleşik etiketleme istemcisini yükleyin ve yapılandırın](#step-4-install-and-configure-the-aip-unified-labeling-client).

1. [Windows'da AIP uygulamalarını yapılandırın](#step-5-configure-aip-apps-on-windows).

1. [AIP şirket içi tarayıcısını yükleyin ve içerik tarama işlerini yönetin](#step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs). 

### <a name="step-1-enable-rights-management-for-the-tenant"></a>1. Adım: Kiracı için Rights Management'ı etkinleştirme

Şifrelemenin düzgün çalışması için kiracı için RMS'nin etkinleştirilmesi gerekir.

1. RMS'nin etkin olup olmadığını denetleyin:

    1. PowerShell'i yönetici olarak başlatın.
    2. AIPService modülü yüklü değilse komutunu çalıştırın `Install-Module AipService`.
    3. kullanarak `Import-Module AipService`modülü içeri aktarın.
    4. kullanarak `Connect-AipService -environmentname azurechinacloud`hizmete Bağlan.
    5. komutunu çalıştırın `(Get-AipServiceConfiguration).FunctionalState` ve durumunun olup `Enabled`olmadığını denetleyin.

2. İşlevsel durum ise `Disabled`komutunu çalıştırın `Enable-AipService`.

### <a name="step-2-add-the-microsoft-purview-information-protection-sync-service-service-principal"></a>2. Adım: Microsoft Purview Information Protection Eşitleme Hizmeti hizmet sorumlusunu ekleme

**Microsoft Purview Information Protection Eşitleme Hizmeti** hizmet sorumlusu varsayılan olarak Azure Çin kiracılarında kullanılamaz ve Azure Information Protection için gereklidir. Azure Az PowerShell modülü aracılığıyla bu hizmet sorumlusunu el ile oluşturun.

1. Azure Az modülü yüklü değilse bu modülü yükleyin veya Azure Az modülünün önceden yüklenmiş olarak geldiği [Azure Cloud Shell](/azure/cloud-shell/overview) gibi bir kaynak kullanın. Daha fazla bilgi için bkz. [Azure Az PowerShell modülünü yükleme](/powershell/azure/install-az-ps).

1. [Bağlan-AzAccount](/powershell/module/az.accounts/Connect-AzAccount) cmdlet'ini ve `azurechinacloud` ortam adını kullanarak hizmete Bağlan:

    ```powershell
    Connect-azaccount -environmentname azurechinacloud
    ```

1. [New-AzADServicePrincipal](/powershell/module/az.resources/new-azadserviceprincipal) cmdlet'ini ve `870c4f2e-85b6-4d43-bdda-6ed9a579b725` **Microsoft Purview Information Protection Eşitleme Hizmeti** için uygulama kimliğini kullanarak Microsoft Purview Information Protection Eşitleme Hizmeti hizmet sorumlusunu el ile oluşturun:

    ```powershell 
    New-AzADServicePrincipal -ApplicationId 870c4f2e-85b6-4d43-bdda-6ed9a579b725
    ```

1. Hizmet sorumlusunu ekledikten sonra, hizmete gereken ilgili izinleri ekleyin.

### <a name="step-3-configure-dns-encryption"></a>3. Adım: DNS şifrelemeyi yapılandırma

Şifrelemenin doğru çalışması için Office istemci uygulamalarının hizmetin Çin örneğine bağlanması ve oradan önyükleme yapması gerekir. İstemci uygulamalarını doğru hizmet örneğine yeniden yönlendirmek için kiracı yöneticisinin Azure RMS URL'si hakkında bilgi içeren bir DNS SRV kaydı yapılandırması gerekir. DNS SRV kaydı olmadan istemci uygulaması varsayılan olarak genel bulut örneğine bağlanmayı dener ve başarısız olur.

Ayrıca, kullanıcıların kullanıcı adı (örneğin, ) yerine `onmschina` kiracıya ait etki alanını (örneğin, `joe@contoso.cn`) temel alan bir kullanıcı adıyla `joe@contoso.onmschina.cn`oturum açacağı varsayımı da vardır. Dns'in doğru hizmet örneğine yeniden yönlendirmesi için kullanıcı adından etki alanı adı kullanılır.

#### <a name="configure-dns-encryption---windows"></a>DNS şifrelemeyi yapılandırma - Windows

1. RMS kimliğini alın:

    1. PowerShell'i yönetici olarak başlatın.
    2. AIPService modülü yüklü değilse komutunu çalıştırın `Install-Module AipService`.
    3. kullanarak `Connect-AipService -environmentname azurechinacloud`hizmete Bağlan.
    4. RMS kimliğini almak için komutunu çalıştırın `(Get-AipServiceConfiguration).RightsManagementServiceId` .

2. DNS sağlayıcınızda oturum açın, etki alanının DNS ayarlarına gidin ve yeni bir SRV kaydı ekleyin.

    - Hizmet = `_rmsredir`
    - Protokol = `_http`
    - Ad = `_tcp`
    - Hedef = `[GUID].rms.aadrm.cn` (BURADA GUID, RMS kimliğidir)
    - Öncelik, Ağırlık, Saniye, TTL = varsayılan değerler

3. Özel etki alanını [Azure portal](https://portal.azure.cn/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Domains) kiracıyla ilişkilendirin. Bu, DNS ayarlarına değeri ekledikten sonra doğrulanabilecek bir DNS girdisi ekler.

4. Microsoft 365 yönetim merkezi ilgili genel yönetici kimlik bilgileriyle oturum açın ve kullanıcı oluşturmak için etki alanını (örneğin, `contoso.cn`) ekleyin. Doğrulama işleminde ek DNS değişiklikleri gerekebilir. Doğrulama tamamlandıktan sonra kullanıcılar oluşturulabilir.

#### <a name="configure-dns-encryption---mac-ios-android"></a>DNS şifrelemeyi yapılandırma - Mac, iOS, Android

DNS sağlayıcınızda oturum açın, etki alanının DNS ayarlarına gidin ve yeni bir SRV kaydı ekleyin.

- Hizmet = `_rmsdisco`
- Protokol = `_http`
- Ad = `_tcp`
- Hedef = `api.aadrm.cn`
- Bağlantı noktası = `80`
- Öncelik, Ağırlık, Saniye, TTL = varsayılan değerler


### <a name="step-4-install-and-configure-the-aip-unified-labeling-client"></a>4. Adım: AIP birleşik etiketleme istemcisini yükleme ve yapılandırma

[Microsoft İndirme Merkezi'nden](https://www.microsoft.com/download/details.aspx?id=53018) AIP birleşik etiketleme istemcisini indirin ve yükleyin.

Daha fazla bilgi için bkz.:

- [AIP belgeleri](/azure/information-protection/)
- [AIP sürüm geçmişi ve destek ilkesi](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history)
- [AIP sistem gereksinimleri](/azure/information-protection/requirements)
- [AIP hızlı başlangıcı: AIP istemcisini dağıtma](/azure/information-protection/quickstart-deploy-client)
- [AIP yönetici kılavuzu](/azure/information-protection/rms-client/clientv2-admin-guide)
- [AIP kullanıcı kılavuzu](/azure/information-protection/rms-client/clientv2-user-guide)
- [Microsoft 365 duyarlılık etiketleri hakkında bilgi edinin](../../compliance/sensitivity-labels.md)

### <a name="step-5-configure-aip-apps-on-windows"></a>5. Adım: Windows'da AIP uygulamalarını yapılandırma

Windows üzerindeki AIP uygulamaları, Azure Çin için doğru bağımsız buluta işaret etmek için aşağıdaki kayıt defteri anahtarına ihtiyaç duyar:

- Kayıt defteri düğümü = `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIP`
- Ad = `CloudEnvType`
- Değer = `6` (varsayılan = 0)
- Tür = `REG_DWORD`

> [!IMPORTANT]
> Kaldırma sonrasında kayıt defteri anahtarını silmediğinizden emin olun. Anahtar boş, yanlış veya mevcut değilse, işlevsellik varsayılan değer olarak davranır (ticari bulut için varsayılan değer = 0). Anahtar boş veya yanlışsa, günlüğe bir yazdırma hatası da eklenir.

### <a name="step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs"></a>6. Adım: AIP şirket içi tarayıcısını yükleme ve içerik tarama işlerini yönetme

Ağınızı ve içerik paylaşımlarınızı hassas veriler için taramak ve kuruluşunuzun ilkesinde yapılandırılan sınıflandırma ve koruma etiketlerini uygulamak için AIP şirket içi tarayıcısını yükleyin.

İçerik tarama işlerinizi yapılandırırken ve yönetirken, ticari teklifler tarafından kullanılan [Azure portal arabirimi](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only) yerine aşağıdaki yordamı kullanın.

Daha fazla bilgi için bkz. [Azure Information Protection birleşik etiketleme tarayıcısı nedir?](/azure/information-protection/deploy-aip-scanner) ve [İçerik tarama işlerinizi yalnızca PowerShell kullanarak yönetme](/azure/information-protection/deploy-aip-scanner-prereqs#use-powershell-with-a-disconnected-computer).

**Tarayıcınızı yüklemek ve yapılandırmak için**:

1. Tarayıcıyı çalıştıracak Windows Sunucusu bilgisayarında oturum açın. Yerel yönetici haklarına sahip ve SQL Server ana veritabanına yazma izinleri olan bir hesap kullanın.

1. PowerShell kapalı olarak başlayın. AIP istemcisini ve tarayıcısını daha önce yüklediyseniz, **AIPScanner** hizmetinin durdurulduğunu doğrulayın.

1. **Yönetici olarak çalıştır** seçeneğiyle bir Windows PowerShell oturumu açın.

1. Azure Information Protection tarayıcısı için veritabanı oluşturulacak SQL Server örneğinizi ve tarayıcı kümeniz için anlamlı bir ad belirterek [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner) cmdlet'ini çalıştırın.

    ```PowerShell
    Install-AIPScanner -SqlServerInstance <name> -Cluster <cluster name>
    ```

    > [!TIP]
    > Birden çok tarayıcı düğümlerini aynı kümeyle ilişkilendirmek için [Install-AIPScanner](/powershell/module/azureinformationprotection/install-aipscanner) komutunda aynı küme adını kullanabilirsiniz. Birden çok tarayıcı düğümü için aynı kümeyi kullanmak, taramalarınızı gerçekleştirmek için birden çok tarayıcının birlikte çalışmasını sağlar.
    > 

1. **Yönetim** **AraçlarıHizmetleri'ni** >  kullanarak hizmetin yüklendiğini doğrulayın.

    Yüklü hizmet **Azure Information Protection Tarayıcısı** olarak adlandırılır ve oluşturduğunuz tarayıcı hizmet hesabı kullanılarak çalıştırılacak şekilde yapılandırılır.

1. Tarayıcınızla kullanmak için bir Azure belirteci alın. Azure AD belirteci, tarayıcının Azure Information Protection hizmetinde kimlik doğrulaması yapmasına olanak tanıyarak tarayıcının etkileşimli olmayan bir şekilde çalışmasını sağlar. 

    1. Azure portal açın ve kimlik doğrulaması için bir erişim belirteci belirtmek üzere bir Azure AD uygulaması oluşturun. Daha fazla bilgi için bkz. [Azure Information Protection için dosyaları etkileşimli olmayan şekilde etiketleme](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).
    
        > [!TIP]
        > [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) komutu için Azure AD uygulamaları oluştururken ve yapılandırırken, **API izinlerini isteme** bölmesi **Kuruluşumun kullandığı API'leri** **Microsoft API'leri** sekmesi yerine sekme olarak gösterir. **Kuruluşumun kullandığı API'leri** ve ardından **Azure Rights Management Services'ı** seçin. 
        >

    1. Windows Sunucusu bilgisayarından, tarayıcı hizmeti hesabınıza yükleme için **yerel olarak oturum açma** hakkı verildiyse, bu hesapla oturum açın ve bir PowerShell oturumu başlatın. 
    
        Tarayıcı hizmeti hesabınıza yükleme için **yerel olarak oturum açma** hakkı verilemiyorsa, [Dosyaları Azure Information Protection için etkileşimli olmayan şekilde etiketleme](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection) bölümünde açıklandığı gibi [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) ile *OnBehalfOf* parametresini kullanın.

    1. Azure AD uygulamanızdan kopyalanan değerleri belirterek [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) komutunu çalıştırın:

      ```PowerShell
      Set-AIPAuthentication -AppId <ID of the registered app> -AppSecret <client secret sting> -TenantId <your tenant ID> -DelegatedUser <Azure AD account>
      ```

      Örneğin:

      ```PowerShell
      $pscreds = Get-Credential CONTOSO\scanner
      Set-AIPAuthentication -AppId "77c3c1c3-abf9-404e-8b2b-4652836c8c66" -AppSecret "OAkk+rnuYc/u+]ah2kNxVbtrDGbS47L4" -DelegatedUser scanner@contoso.com -TenantId "9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a" -OnBehalfOf $pscreds
      Acquired application access token on behalf of CONTOSO\scanner.
      ```

    Tarayıcının artık Azure AD'de kimlik doğrulaması yapmak için bir belirteci vardır. Bu belirteç, Azure AD'de **Web uygulaması /API** istemci gizli dizisi yapılandırmanıza göre bir yıl, iki yıl veya hiçbir zaman geçerlidir. Belirtecin süresi dolduğunda bu yordamı yinelemeniz gerekir.

1. Tarayıcıyı çevrimdışı modda çalışacak şekilde ayarlamak için [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/set-aipscannerconfiguration) cmdlet'ini çalıştırın. Çalıştırmak:

    ```powershell
    Set-AIPScannerConfiguration -OnlineConfiguration Off
    ```

1. Varsayılan içerik tarama işini oluşturmak için [Set-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) cmdlet'ini çalıştırın.

    **Set-AIPScannerContentScanJob** cmdlet'inde gerekli olan tek parametre **Zorlama'dır**. Ancak, şu anda içerik tarama işiniz için diğer ayarları tanımlamak isteyebilirsiniz. Örneğin:

    ```powershell
    Set-AIPScannerContentScanJob -Schedule Manual -DiscoverInformationTypes PolicyOnly -Enforce Off -DefaultLabelType PolicyDefault -RelabelFiles Off -PreserveFileDetails On -IncludeFileTypes '' -ExcludeFileTypes '.msg,.tmp' -DefaultOwner <account running the scanner>
    ```

    Yukarıdaki söz dizimi, yapılandırmaya devam ederken aşağıdaki ayarları yapılandırıyor:

    - Tarayıcının çalışma zamanlamasını *el ile* çalışır halde tutar
    - Bulunabilecek bilgi türlerini duyarlılık etiketleme ilkesine göre ayarlar
    - Duyarlılık etiketleme ilkesini zorunlu *kılmaz*
    - Duyarlılık etiketleme ilkesi için tanımlanan varsayılan etiketi kullanarak dosyaları içeriğe göre otomatik olarak etiketler
    - Dosyaların yeniden etiketlenmesine izin *vermiyor*
    - Değerlere göre *değiştirme tarihi*, *son değiştirme* ve *değiştirme* dahil olmak üzere tarama ve otomatik etiketleme sırasında dosya ayrıntılarını korur
    - Çalışırken .msg ve .tmp dosyalarını dışlamak için tarayıcıyı ayarlar
    - Tarayıcıyı çalıştırırken kullanmak istediğiniz hesabın varsayılan sahibini ayarlar

1. İçerik tarama işinizde taramak istediğiniz depoları tanımlamak için [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) cmdlet'ini kullanın. Örneğin şunu çalıştırın:

    ```powershell
    Add-AIPScannerRepository -OverrideContentScanJob Off -Path 'c:\repoToScan'
    ```
    
    Eklediğiniz deponun türüne bağlı olarak aşağıdaki söz dizimlerinden birini kullanın:

    - Ağ paylaşımı için kullanın `\\Server\Folder`.
    - SharePoint kitaplığı için kullanın`http://sharepoint.contoso.com/Shared%20Documents/Folder`.
    - Yerel yol için: `C:\Folder`
    - UNC yolu için: `\\Server\Folder`

    > [!NOTE]
    > Joker karakterler desteklenmez ve WebDav konumları desteklenmez.
    >
    > Daha sonra depoyu değiştirmek için bunun yerine [Set-AIPScannerRepository cmdlet'ini](/powershell/module/azureinformationprotection/set-aipscannerrepository) kullanın. 


Gerekirse aşağıdaki adımlarla devam edin:

- [Bulma döngüsü çalıştırma ve tarayıcı için raporları görüntüleme](/azure/information-protection/deploy-aip-scanner-manage#run-a-discovery-cycle-and-view-reports-for-the-scanner)
- [Tarayıcıyı sınıflandırma ve koruma uygulayacak şekilde yapılandırmak için PowerShell kullanma](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only#use-powershell-to-configure-the-scanner-to-apply-classification-and-protection)
- [Tarayıcıyla DLP ilkesi yapılandırmak için PowerShell kullanma](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only#use-powershell-to-configure-a-dlp-policy-with-the-scanner)

Aşağıdaki tabloda, tarayıcıyı yüklemek ve içerik tarama işlerinizi yönetmek için uygun PowerShell cmdlet'leri listelenir:

| Cmdlet | Açıklama |
|--|--|
| [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) | İçerik tarama işinize yeni bir depo ekler. |
| [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/get-aipscannerconfiguration)|Kümenizle ilgili ayrıntıları döndürür. |
| [Get-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/get-aipscannercontentscanjob) | İçerik tarama işinizle ilgili ayrıntıları alır. |
| [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/get-aipscannerrepository) | İçerik tarama işiniz için tanımlanan depolarla ilgili ayrıntıları alır. |
| [Remove-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/remove-aipscannercontentscanjob) | İçerik tarama işinizi siler. |
| [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/remove-aipscannerrepository) | İçerik tarama işinizden bir depoyu kaldırır. |
| [Set-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) | İçerik tarama işinizin ayarlarını tanımlar. |
| [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) | İçerik tarama işinizde var olan bir deponun ayarlarını tanımlar. |
| | |

Daha fazla bilgi için bkz.:

- [Azure Information Protection birleşik etiketleme tarayıcısı nedir?](/azure/information-protection/deploy-aip-scanner)
- [Azure Information Protection (AIP) birleşik etiketleme tarayıcısını yapılandırma ve yükleme](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=powershell-only)
- [İçerik tarama işlerinizi yalnızca PowerShell kullanarak yönetin](/azure/information-protection/deploy-aip-scanner-prereqs#use-powershell-with-a-disconnected-computer).
