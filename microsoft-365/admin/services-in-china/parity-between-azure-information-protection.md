---
title: 21Vianet tarafından Office 365 için Azure Information Protection desteği
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
description: 21Vianet tarafından işletilen müşteriler için Azure Information Protection (AIP) Office 365 ve Çin'deki müşteriler için yapılandırma hakkında daha fazla bilgi edinin.
monikerRange: o365-21vianet
ms.openlocfilehash: 44681286bce5e16a08f7400a2dbb083288a6f3b7
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "63010171"
---
# <a name="azure-information-protection-support-for-office-365-operated-by-21vianet"></a>21Vianet tarafından Office 365 için Azure Information Protection desteği

Bu makalede, 21Vianet tarafından çalıştırılan Office 365 için Azure Information Protection (AIP) desteği ile 21Vianet tarafından çalıştırılan ticari teklifler arasındaki farkların yanı sıra Çin'deki müşteriler için AIP'i&mdash; yapılandırmaya yönelik belirli yönergeler, AIP şirket içi tarayıcısını yükleme ve içerik tarama işlerini yönetme dahil olmak üzere bu makaledeki farklar açıklanmıştır.

## <a name="differences-between-aip-for-office-365-operated-by-21vianet-and-commercial-offerings"></a>21Vianet tarafından Office 365 için AIP ile ticari teklifler arasındaki farklar

21Vianet tarafından işletilen Office 365 için AIP teklifimiz ile tüm ticari özellikleri ve işlevleri Çin'deki müşterilere sunmakla birlikte, vurgulamak sunduğumuz bazı eksik işlevler bulunmaktadır.

Aşağıdaki liste, 21Vianet tarafından çalıştırılan Office 365 için AIP ile Ocak 2021'den itibaren yapılan ticari tekliflerimiz arasında var olan boşlukları içerir:

- Active Directory Rights Management Services (AD RMS) şifrelemesi yalnızca Kurumlar için Microsoft 365 Uygulamaları (derleme 11731.10000 veya sonraki derleme) içinde destekler. Office Professional Plus, AD RMS'yi desteklemez.

- AD RMS'den AIP'ye geçiş şu anda kullanılamıyor.
  
- Korumalı e-postaların ticari buluttaki kullanıcılarla paylaşımı da destekler.
  
- Ticari buluttaki kullanıcılarla belgelerin ve e-posta eklerinin paylaşımı şu anda kullanılamaz. Bu, Office 365 bulutta 21Vianet tarafından çalıştırılan, 21Vianet tarafından çalıştırılan Office 365 olmayan kullanıcılar ve Bireyler için RMS lisansına sahip kullanıcıları kapsar.
  
- IRM ve SharePoint (IRM korumalı siteler ve kitaplıklar) şu anda kullanılamıyor.
  
- AD RMS için Mobil Cihaz Uzantısı şu anda kullanılamıyor.

- Mobil [Görüntüleyici,](/azure/information-protection/rms-client/mobile-app-faq) Azure China 21Vianet tarafından desteklenmiyor.

- Azure portalında yer alan AIP alanı Çin'deki müşteriler tarafından kullanılamaz. Portalda içerik tarama işlerinizi yönetme ve çalıştırma gibi eylemleri gerçekleştirmek yerine [PowerShell](#step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs) komutlarını kullanın.

- 21Vianet tarafından Office 365 AIP uç noktaları, diğer bulut hizmetleri için gereken uç noktalardan farklıdır. İstemcilerden aşağıdaki uç noktalara ağ bağlantısı gereklidir:
    - Etiket ve etiket ilkelerini indirme: `*.protection.partner.outlook.cn`
    - Azure Hak Yönetimi hizmeti: `*.aadrm.cn`

## <a name="configure-aip-for-customers-in-china"></a>Çin'deki müşteriler için AIP'yi yapılandırma

Çin'deki müşteriler için AIP'yi yapılandırmak için:
1. [Kiracı için Hak Yönetimi'yi etkinleştirin](#step-1-enable-rights-management-for-the-tenant).

1. [Microsoft Bilgi Koruması Eşitleme Hizmeti sorumlusuna tıklayın](#step-2-add-the-microsoft-information-protection-sync-service-service-principal).

1. [DNS şifrelemeyi yapılandırma](#step-3-configure-dns-encryption).

1. [AIP birleşik etiketleme istemcisini yükleme ve yapılandırma](#step-4-install-and-configure-the-aip-unified-labeling-client).

1. [Diğer uygulamalarda AIP Windows](#step-5-configure-aip-apps-on-windows).

1. [AIP şirket içi tarayıcısını yükleyin ve içerik tarama işlerini yönetin](#step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs). 

### <a name="step-1-enable-rights-management-for-the-tenant"></a>1. Adım: Kiracı için Hak Yönetimini etkinleştirme

Şifrelemenin doğru çalışması için, kiracı için RMS'nin etkinleştirilmiş olması gerekir.

1. RMS'nin etkin olup değildir:

    1. PowerShell'i yönetici olarak açın.
    2. AIPService modülü yüklü değilse, çalıştırın `Install-Module AipService`.
    3. 'ı kullanarak modülü içeri aktarın `Import-Module AipService`.
    4. Bağlan 'ı kullanarak hizmete geri abilirsiniz`Connect-AipService -environmentname azurechinacloud`.
    5. Çalıştır `(Get-AipServiceConfiguration).FunctionalState` ve durumunun ne olduğunu kontrol edin `Enabled`.

2. İşlevsel durum ise `Disabled`, çalıştırın `Enable-AipService`.

### <a name="step-2-add-the-microsoft-information-protection-sync-service-service-principal"></a>2. Adım: Microsoft Bilgi Koruması Eşitleme Hizmeti sorumlusu ekleme

Eşitleme **Microsoft Bilgi Koruması hizmet** sorumlusu, Azure Çin kiracılarında varsayılan olarak kullanılamaz ve Azure Information Protection için gereklidir. Bu hizmet sorumlusunı Azure Az PowerShell modülü aracılığıyla el ile oluşturun.

1. Azure Az modülü yüklü değilse, bunu yükleyin veya Azure Az modülü, Azure Bulut Kabuğu gibi önceden yüklenmiş olarak geldiği [bir kaynağı kullanın](/azure/cloud-shell/overview). Daha fazla bilgi için bkz [. Azure Az PowerShell modülünü yükleme](/powershell/azure/install-az-ps).

1. [Bağlan-AzAccount cmdlet'ini](/powershell/module/az.accounts/Connect-AzAccount) `azurechinacloud` ve ortam adını kullanarak hizmete Bağlan:

    ```powershell
    Connect-azaccount -environmentname azurechinacloud
    ```

1. [New-AzADServicePrincipal](/powershell/module/az.resources/new-azadserviceprincipal) cmdlet'ini `870c4f2e-85b6-4d43-bdda-6ed9a579b725` ve Microsoft Bilgi Koruması Eşitleme Hizmeti'nin uygulama kimliğini kullanarak Microsoft Bilgi Koruması oluşturun:

    ```powershell 
    New-AzADServicePrincipal -ApplicationId 870c4f2e-85b6-4d43-bdda-6ed9a579b725
    ```

1. Hizmet sorumlusu ekledikten sonra, hizmete gereken ilgili izinleri ekleyin.

### <a name="step-3-configure-dns-encryption"></a>3. Adım: DNS şifrelemeyi yapılandırma

Şifrelemenin doğru çalışması için, Office uygulamalarının çin örneği olan hizmet ve önyükleme örneğine bağlanması gerekir. İstemci uygulamalarını doğru hizmet örneğine yönlendirmek için, kiracı yöneticisinin Azure RMS URL'si hakkında bilgileri olan bir DNS SRV kaydı yapılandırması gerekir. DNS SRV kaydı olmadan, istemci uygulaması varsayılan olarak genel bulut örneğine bağlanmayı dener ve başarısız olur.

Ayrıca, kullanıcıların kullanıcı adı (örneğin, ) değil, kiracıya ait etki alanı (örneğin, `joe@contoso.cn`) `onmschina` tabanlı bir kullanıcı adı ile oturum açacakları varsayımı iledir `joe@contoso.onmschina.cn`. Kullanıcı adının etki alanı adı, DNS yeniden yönlendirmesi için doğru hizmet örneğine kullanılır.

#### <a name="configure-dns-encryption---windows"></a>DNS şifrelemeyi yapılandırma - Windows

1. RMS Kimliğini alma:

    1. PowerShell'i yönetici olarak açın.
    2. AIPService modülü yüklü değilse, çalıştırın `Install-Module AipService`.
    3. Bağlan 'ı kullanarak hizmete geri abilirsiniz`Connect-AipService -environmentname azurechinacloud`.
    4. `(Get-AipServiceConfiguration).RightsManagementServiceId` RMS Kimliğini almak için çalıştırın.

2. DNS sağlayıcınızda oturum açma, etki alanının DNS ayarlarına gidin ve yeni bir SRV kaydı ekleyin.

    - Hizmet = `_rmsredir`
    - Protokol = `_http`
    - Ad = `_tcp`
    - Hedef = `[GUID].rms.aadrm.cn` (burada GUID, RMS Kimliği'dir)
    - Öncelik, Ağırlık, Saniye, TTL = varsayılan değerler

3. Özel etki alanını [Azure portalda](https://portal.azure.cn/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Domains) kiracıyla ilişkilendirme. Bu, DNS'e bir girdi ekler ve bu da DNS ayarlarına değeri girdikten sonra doğrulandıktan sonra birkaç dakika sürebilir.

4. Kullanıcı profilinde ilgili Microsoft 365 yönetim merkezi yönetici kimlik bilgileriyle oturum açma ve kullanıcı oluşturma için etki alanını (örneğin, `contoso.cn`) ekleme. Doğrulama sürecinde ek DNS değişiklikleri gerekebilir. Doğrulama yapıldıktan sonra kullanıcılar oluşturulabilir.

#### <a name="configure-dns-encryption---mac-ios-android"></a>DNS şifrelemesini yapılandırma - Mac, iOS, Android

DNS sağlayıcınızda oturum açma, etki alanının DNS ayarlarına gidin ve yeni bir SRV kaydı ekleyin.

- Hizmet = `_rmsdisco`
- Protokol = `_http`
- Ad = `_tcp`
- Hedef = `api.aadrm.cn`
- Bağlantı noktası = `80`
- Öncelik, Ağırlık, Saniye, TTL = varsayılan değerler


### <a name="step-4-install-and-configure-the-aip-unified-labeling-client"></a>4. Adım: AIP birleşik etiketleme istemcisini yükleme ve yapılandırma

Microsoft İndirme Merkezi'nden AIP birleşik etiketleme [istemcisini indirin ve yükleyin](https://www.microsoft.com/download/details.aspx?id=53018).

Daha fazla bilgi için bkz.:

- [AIP belgeleri](/azure/information-protection/)
- [AIP sürüm geçmişi ve destek ilkesi](/azure/information-protection/rms-client/unifiedlabelingclient-version-release-history)
- [AIP sistem gereksinimleri](/azure/information-protection/requirements)
- [AIP hızlı başlangıç: AIP istemcisini dağıtma](/azure/information-protection/quickstart-deploy-client)
- [AIP yönetici kılavuzu](/azure/information-protection/rms-client/clientv2-admin-guide)
- [AIP kullanıcı kılavuzu](/azure/information-protection/rms-client/clientv2-user-guide)
- [Duyarlılık etiketlerini Microsoft 365 hakkında bilgi](../../compliance/sensitivity-labels.md)

### <a name="step-5-configure-aip-apps-on-windows"></a>5. Adım: Diğer uygulamalarda AIP Windows

Aşağıdaki özelliklerde AIP Windows Azure Çin için doğru hakim buluta işaret etmek için aşağıdaki kayıt defteri anahtarı gerekir:

- Kayıt Defteri düğümü = `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIP`
- Ad = `CloudEnvType`
- Değer = `6` (varsayılan = 0)
- = yazın `REG_DWORD`

> [!IMPORTANT]
> Kaldırma sonrasında kayıt defteri anahtarını silmeyebilirsiniz. Anahtar boş, yanlış veya var olmayan bir anahtarsa, işlev varsayılan değer (ticari bulut için varsayılan değer = 0) olarak davranır. Anahtar boşsa veya yanlışsa, günlüğe yazdırma hatası da eklenir.

### <a name="step-6-install-the-aip-on-premises-scanner-and-manage-content-scan-jobs"></a>6. Adım: AIP şirket içi tarayıcısını yükleme ve içerik tarama işlerini yönetme

Hassas veriler için ağ ve içerik paylaşımlarınızı taramak için AIP şirket içi tarayıcıyı yükleyin ve kuruluş ilkesinde yapılandırılan sınıflandırma ve koruma etiketlerini kullanın.

İçerik tarama işlerinizi yapılandıracak ve yönetecekken, ticari teklifler tarafından kullanılan [Azure portal](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only) arabirimi yerine aşağıdaki yordamı kullanın.

Daha fazla bilgi için bkz [. Azure Information Protection](/azure/information-protection/deploy-aip-scanner) birleşik etiketleme tarayıcısı nedir? [ve Yalnızca PowerShell kullanarak içerik tarama işlerinizi yönetme](/azure/information-protection/deploy-aip-scanner-prereqs#use-powershell-with-a-disconnected-computer).

**Tarayıcınızı yüklemek ve yapılandırmak için**:

1. Tarayıcıyı çalıştıracak Windows Server bilgisayarda oturum açma. Yerel yönetici hakları olan ve ana veritabanına yazma izinleri olan SQL Server kullanın.

1. PowerShell kapalı olarak çalışmaya başlama. Daha önce AIP istemcisini ve tarayıcısını yüklemişsiniz, **AIPScanner hizmetinin durdurulurken** emin olun.

1. Yönetici Windows PowerShell ile **bir oturum açın**.

1. Azure Information Protection tarayıcı için bir veritabanı oluşturmak istediğiniz SQL Server örneğinizi ve tarayıcınızın kümesi için anlamlı bir ad belirterek [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner) cmdlet'ini çalıştırın.

    ```PowerShell
    Install-AIPScanner -SqlServerInstance <name> -Cluster <cluster name>
    ```

    > [!TIP]
    > Birden çok tarayıcı düğümünü aynı kümeyle ilişkilendirmek için [Install-AIPScanner](/powershell/module/azureinformationprotection/install-aipscanner) komutunda aynı küme adını kullanabilirsiniz. Birden çok tarayıcı düğümü için aynı kümeyi kullanmak, taramalarınızı gerçekleştirmek için birden çok tarayıcının birlikte çalışmasına olanak sağlar.
    > 

1. Yönetimsel **AraçlarServices** kullanılarak hizmetin artık **yüklü olduğunu** >  doğrulayın.

    Yüklü hizmet Azure **Information Protection Scanner olarak** adlandırılmıştır ve oluşturduğunuz tarayıcı hizmeti hesabı kullanılarak çalıştıracak şekilde yapılandırılmıştır.

1. Tarayıcınızla kullanmak üzere bir Azure belirteci alın. Azure AD belirteci tarayıcının Azure Information Protection hizmetinin kimliğini doğrulamasına olanak sağlayarak tarayıcının etkileşimli olmayan şekilde çalışmasına olanak sağlar. 

    1. Azure portalını açın ve kimlik doğrulamasına yönelik bir erişim belirteci belirtmek için bir Azure AD uygulaması oluşturun. Daha fazla bilgi için bkz [. Azure Information Protection için dosyaları etkileşimli olmayan şekilde etiketleme](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection).
    
        > [!TIP]
        > [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) komutu için Azure AD uygulamalarını oluştururken ve yapılandırken, API izinleri isteği bölmesi Microsoft **API'leri** sekmesi  yerine kuruluşumda kullandığı **API'leri** gösterir. Kuruluşumda **kullanmakta olduğu API'leri ve** ardından **Azure Rights Management Services'ı seçin**. 
        >

    1. Windows Server bilgisayarda, tarayıcınız hizmet hesabına yükleme için yerel olarak oturum açma hakkı verildiyse, bu  hesapla oturum açın ve Bir PowerShell oturumu başlatın. 
    
        Tarayıcı hizmet hesabınıza yükleme için yerel olarak oturum açma hakkı  verilenene kadar, [Azure Information Protection](/azure/information-protection/rms-client/clientv2-admin-guide-powershell#how-to-label-files-non-interactively-for-azure-information-protection) için dosyaları etkileşimli olmayan şekilde etiketleme konusunda açıklandığı gibi [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) ile *OnBehalfOf* parametresini kullanın.

    1. Azure AD [uygulamanıza kopyalanan değerleri belirterek Set-AIPAuthentication'i](/powershell/module/azureinformationprotection/set-aipauthentication) çalıştırın:

      ```PowerShell
      Set-AIPAuthentication -AppId <ID of the registered app> -AppSecret <client secret sting> -TenantId <your tenant ID> -DelegatedUser <Azure AD account>
      ```

      Örneğin:

      ```PowerShell
      $pscreds = Get-Credential CONTOSO\scanner
      Set-AIPAuthentication -AppId "77c3c1c3-abf9-404e-8b2b-4652836c8c66" -AppSecret "OAkk+rnuYc/u+]ah2kNxVbtrDGbS47L4" -DelegatedUser scanner@contoso.com -TenantId "9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a" -OnBehalfOf $pscreds
      Acquired application access token on behalf of CONTOSO\scanner.
      ```

    Tarayıcının artık Azure AD'de kimlik doğrulaması için bir belirteci vardır. Bu belirteç, Azure AD'de **Web App /API** istemci sırrı yapılandırmanıza bağlı olarak bir yıl, iki yıl veya hiçbir zaman geçerlidir. Belirteç sona erdiğinde, bu yordamı yinelemeniz gerekir.

1. Tarayıcıyı [çevrimdışı modda çalışması için ayarlamak için Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/set-aipscannerconfiguration) cmdlet'ini çalıştırın. Çalıştır:

    ```powershell
    Set-AIPScannerConfiguration -OnlineConfiguration Off
    ```

1. Varsayılan içerik [tarama işini oluşturmak için Set-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) cmdlet'ini çalıştırın.

    **Set-AIPScannerContentScanJob** cmdlet'inde gerekli olan tek parametre **Enforce parametresidir**. Bununla birlikte, şu anda içerik tarama işinin diğer ayarlarını tanımlamak istiyor da olabilir. Örneğin:

    ```powershell
    Set-AIPScannerContentScanJob -Schedule Manual -DiscoverInformationTypes PolicyOnly -Enforce Off -DefaultLabelType PolicyDefault -RelabelFiles Off -PreserveFileDetails On -IncludeFileTypes '' -ExcludeFileTypes '.msg,.tmp' -DefaultOwner <account running the scanner>
    ```

    Yapılandırmaya devam ederken yukarıdaki söz dizimi aşağıdaki ayarları yapılandırr:

    - Tarayıcının zamanlamayı el ile çalıştırmak için çalıştırmasını *sağlar*
    - Duyarlılık etiketleme ilkesine göre keşfed keşfedilacak bilgi türlerini ayarlar
    - *Duyarlılık etiketleme* ilkesi zorunlu değil
    - Duyarlılık etiketleme ilkesi için tanımlanan varsayılan etiketi kullanarak dosyaları içeriğe göre otomatik olarak etiketler
    - Dosyaları *yeniden* etiketleye izin vermez
    - Değiştirme tarihi, son değiştirme tarihi ve değerlere göre *değiştirme dahil olmak* üzere tarama ve otomatik *etiketleme* sırasında *dosya ayrıntılarını* korur
    - Tarayıcıyı, çalıştırma için .msg ve .tmp dosyalarını dışarıda bırakacak şekilde ayarlar
    - Tarayıcıyı çalıştırmaya devam etmek istediğiniz hesabın varsayılan sahibini ayarlar

1. İçerik tarama işlerinde taramak istediğiniz depoları tanımlamak için [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) cmdlet'ini kullanın. Örneğin, aşağıdakini çalıştırın:

    ```powershell
    Add-AIPScannerRepository -OverrideContentScanJob Off -Path 'c:\repoToScan'
    ```
    
    Eklemekte istediğiniz deponun türüne bağlı olarak, aşağıdaki söz dizimlerinden birini kullanın:

    - Ağ paylaşımı için kullanın `\\Server\Folder`.
    - Belge kitaplığı SharePoint için, kullanın`http://sharepoint.contoso.com/Shared%20Documents/Folder`.
    - Yerel yol için: `C:\Folder`
    - UNC yolu için: `\\Server\Folder`

    > [!NOTE]
    > Joker karakterler desteklenmiyor ve WebDav konumları desteklenmiyor.
    >
    > Depoyu daha sonra değiştirmek için bunun yerine [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) cmdlet'ini kullanın. 


Aşağıdaki adımlarla devam edin:

- [Tarayıcı için bir keşif döngüsü çalıştırma ve raporları görüntüleme](/azure/information-protection/deploy-aip-scanner-manage#run-a-discovery-cycle-and-view-reports-for-the-scanner)
- [Tarayıcıyı sınıflandırma ve koruma uygulamak üzere yapılandırmak için PowerShell kullanma](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only#use-powershell-to-configure-the-scanner-to-apply-classification-and-protection)
- [Tarayıcıyla DLP ilkesi yapılandırmak için PowerShell kullanma](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=azure-portal-only#use-powershell-to-configure-a-dlp-policy-with-the-scanner)

Aşağıdaki tabloda, tarayıcıyı yüklemek ve içerik tarama işlerinizi yönetmekle ilgili PowerShell cmdlet'leri listelemektedir:

| Cmdlet | Açıklama |
|--|--|
| [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) | İçerik tarama işinize yeni bir depo ekler. |
| [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/get-aipscannerconfiguration)|Kümeniz hakkında ayrıntıları döndürür. |
| [Get-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/get-aipscannercontentscanjob) | İçerik tarama işinin ayrıntılarını alır. |
| [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/get-aipscannerrepository) | İçerik tarama işi için tanımlanmış depolar hakkında ayrıntıları alır. |
| [Remove-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/remove-aipscannercontentscanjob) | İçerik tarama işini siler. |
| [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/remove-aipscannerrepository) | İçerik tarama iş yerlerinden bir depo kaldırır. |
| [Set-AIPScannerContentScanJob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) | İçerik tarama işinin ayarlarını tanımlar. |
| [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) | İçerik tarama işinizin var olan depo ayarlarını tanımlar. |
| | |

Daha fazla bilgi için bkz.:

- [Azure Information Protection birleşik etiketleme tarayıcısı nedir?](/azure/information-protection/deploy-aip-scanner)
- [Azure Information Protection(AIP) birleşik etiketleme tarayıcısını yapılandırma ve yükleme](/azure/information-protection/deploy-aip-scanner-configure-install?tabs=powershell-only)
- [Yalnızca PowerShell kullanarak içerik tarama işlerinizi yönetin](/azure/information-protection/deploy-aip-scanner-prereqs#use-powershell-with-a-disconnected-computer).
