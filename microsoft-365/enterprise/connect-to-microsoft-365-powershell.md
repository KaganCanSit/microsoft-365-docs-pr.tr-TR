---
title: Bağlan'Microsoft 365 PowerShell'i de
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- O365ITProTrain
- Ent_Office_Other
ms.assetid: 5ebc0e21-b72d-46d8-96fa-00643b18eaec
description: Bağlan satırdan Microsoft 365 yönetim merkezi görevlerini gerçekleştirmek için Microsoft 365 PowerShell kullanarak bu kiracınıza gidin.
ms.openlocfilehash: 67c3a596d1b0d7acec2925f39c2f6bd8025d7d4a
ms.sourcegitcommit: e3bff611439354e6339bb666a88682078f32ec13
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2022
ms.locfileid: "63014360"
---
# <a name="connect-to-microsoft-365-with-powershell"></a>Bağlan'Microsoft 365 PowerShell'i de

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Microsoft 365 için PowerShell, komut Microsoft 365 ayarlarınızı yönetmenize olanak sağlar. PowerShell'e bağlanmak için gerekli yazılımı yüklemeniz ve sonra bilgisayarınıza ve bilgisayarınıza Microsoft 365 gerekir.

Kullanıcı hesapları, gruplar ve lisansları yönetmek ve hesaba bağlanmak Microsoft 365 kullanabileceğiniz iki PowerShell modülü sürümü vardır:

- Azure Active Directory cmdlet'leri kendi adlarında *AzureAD* bulunan Graph için PowerShell'i içerir
- Microsoft Azure Active Directory içinde Msol bulunan Windows PowerShell için *Msol* Modülü

Şu anda Azure Active Directory, Graph için PowerShell modülü kullanıcı, grup ve lisans yönetimine Windows PowerShell için Microsoft Azure Active Directory Modülü işlevini tamamen değiştirmez. Bazı durumlarda her iki sürümü de kullanabiliyoruz. Aynı bilgisayara her iki sürümü de güvenle yükleyebilirsiniz.

>[!Note]
>Ayrıca, ilk buluttan [Azure Bulut Kabuğu'Microsoft 365 yönetim merkezi](#connect-with-the-azure-cloud-shell).
>


## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler


**İşletim sistemi**

Dosyanın 64 bit sürümünü Windows. Yeni Sürüm için Microsoft Azure Active Directory Modülü'ne 32 bit sürümü Windows PowerShell 2014'te sona erdi.

Aşağıdaki sürümleri kullanabilirsiniz Windows:
    
  - Windows 10, Windows 8.1, Windows 8 veya Windows 7 Service Pack 1 (SP1) 
    
  - Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 veya Windows Server 2008 R2 SP1

>[!Note]
>Windows 8.1, Windows 8, Windows 7 Service Pack 1 (SP1), Windows Server 2012 R2, Windows Server 2012 ve Windows Server 2008 R2 SP1 [için Windows Management Framework 5.1](https://www.microsoft.com/download/details.aspx?id=54616).

**PowerShell**

- Graph için PowerShell Azure Active Directory için, PowerShell sürüm 5.1'i kullan gerekir.

- Windows PowerShell için Microsoft Azure Active Directory Modülü'ne yönelik olarak, PowerShell sürüm 6'ya kadar PowerShell sürüm 5.1 veya sonraki bir sürümünü kullanabilirsiniz. PowerShell sürüm 7'ye sahip değil misiniz?
       
>[!Note]
>Bu yordamlar, bir yönetici rolüne üye Microsoft 365 yöneliktir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../admin/add-users/about-admin-roles.md).


## <a name="connect-with-the-azure-active-directory-powershell-for-graph-module"></a>Bağlan için Azure Active Directory PowerShell modülüyle Graph.

Azure Active Directory Graph için PowerShell modülünde yer alan komutların cmdlet adı altında *AzureAD* vardır. [Graph için PowerShell Azure Active Directory](/powershell/azure/active-directory/install-adv2) modülünü veya [Azure PowerShell.](/powershell/azure/install-az-ps)

Graph için Azure Active Directory PowerShell modülünde yeni cmdlet'leri gerektiren yordamlar için, modülü yüklemek ve Microsoft 365 aboneliğinize bağlanmak için bu adımları izleyin.

> [!Note]
> Farklı sürümlerin desteği hakkında bilgi için Windows bkz[. Azure Active Directory PowerShell for Graph.](/powershell/azure/active-directory/install-adv2)

### <a name="step-1-install-the-required-software"></a>1. Adım: Gerekli yazılımı yükleme

Bu adımlar bilgisayarınızda yalnızca bir kez gereklidir. Ancak, büyük olasılıkla yazılımı düzenli olarak güncelleştirmeniz gerekir.
  
1. Yükseltilmiş bir Komut Windows PowerShell penceresi açın (Windows PowerShell olarak çalıştırın).
    
2. Bu komutu çalıştırın:
    
    ```powershell
    Install-Module -Name AzureAD
    ```

  Varsayılan olarak, PowerShell Galerisi (PSGallery) PowerShellGet için güvenilir bir depo **olarak yapılandırılmaz**. PSGallery'yi ilk kez kullanıyorsanız, aşağıdaki iletiyi alırsınız:

```console
Untrusted repository

You are installing the modules from an untrusted repository. If you trust this repository, change its InstallationPolicy value by running the `Set-PSRepository` cmdlet.

Are you sure you want to install the modules from 'PSGallery'?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "N"):
```

**Yüklemeye** devam **etmek için Evet'e veya** Evet'e Yanıt Ver'i kullanın.

### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a>2. Adım: Bağlan aboneliğiniz için Azure AD Microsoft 365 e geçin

Microsoft 365 aboneliğinizin Azure Active Directory (Azure AD) hesabına hesap adı ve parolasıyla veya çok faktörlü kimlik doğrulamasıyla bağlanmak için, Windows PowerShell komut isteminden bu komutlardan birini çalıştırın. (Yükseltilmiş olması zorunda değil.)

| Office 365 bulut | Komut |
|:-------|:-----|
| Office 365 Dünya Çapında (+GCC) | `Connect-AzureAD` |
| Office 365 21 Vianet tarafından işletilen ağ | `Connect-AzureAD -AzureEnvironmentName AzureChinaCloud` |
| Office 365 Almanya | `Connect-AzureAD -AzureEnvironmentName AzureGermanyCloud` |
| Office 365. S. Government DoD ve Office 365 U.S. Government GCC High | `Connect-AzureAD -AzureEnvironmentName AzureUSGovernment` |
|||

Hesabınızla **oturum açın iletişim kutusuna** iş veya okul Microsoft 365 kullanıcı adı ve parolanızı yazın ve Tamam'ı **seçin**.

Çok faktörlü kimlik doğrulaması kullanıyorsanız, doğrulama kodu gibi ek kimlik doğrulama bilgilerini sağlamak için yönergeleri izleyin.

Bağlandıktan sonra, Azure Active Directory PowerShell için cmdlet'leri [Graph kullanabilirsiniz](/powershell/module/azuread).

## <a name="connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Bağlan için Microsoft Azure Active Directory Modülü ile Windows PowerShell

>[!Note]
>Microsoft Azure Active Directory için Microsoft Azure Active Directory Modülü'ne Windows PowerShell *Msol'un* adı vardır.

PowerShell sürüm 7 ve sonraki sürümler, Microsoft Azure Active Directory Modülü'Windows PowerShell *Msol ile Msol'i* desteklemez. PowerShell sürüm 7 ve sonraki sürümler için, Microsoft Graph PowerShell SDK'yı kullan gerekir.

PowerShell Core, adı *Msol* olan Microsoft Azure Active Directory Modülü Windows PowerShell cmdlet'leri desteklemez. Bu cmdlet'leri çalışma Windows PowerShell.
    
### <a name="step-1-install-the-required-software"></a>1. Adım: Gerekli yazılımı yükleme

Bu adımlar bilgisayarınızda yalnızca bir kez gereklidir. Ancak, büyük olasılıkla yazılımı düzenli olarak güncelleştirmeniz gerekir.
  
1.  Windows 10 çalışmıyorsanız, MICROSOFT Online Services Oturum Açma Yardımcısı: BT Uzmanları için [Microsoft Online Services](https://download.microsoft.com/download/7/1/E/71EF1D05-A42C-4A1F-8162-96494B5E615C/msoidcli_32bit.msi) Oturum Açma Yardımcısı RTW'nin 32 bit sürümünü yükleyin.
    
2. Windows PowerShell için Microsoft Azure Active Directory Modülü'ne yüklemek için şu Windows PowerShell:
    
   1. Yükseltilmiş bir komut Windows PowerShell istemi açın (Windows PowerShell olarak çalıştırın).
   1.  **Install-Module MSOnline komutunu** çalıştırın.
   1. Hizmet sağlayıcısını yüklemeniz istenirse, NuGet **Y** yazın ve Enter tuşuna basın.
   1. Modülü PSGallery'den yüklemeniz istenirse, **Y** yazın ve Enter tuşuna basın.
    
### <a name="step-2-connect-to-azure-ad-for-your-microsoft-365-subscription"></a>2. Adım: Bağlan aboneliğiniz için Azure AD Microsoft 365 e geçin

Microsoft 365 aboneliğinizin Azure AD'ye bir hesap adı ve parolasıyla veya çok faktörlü kimlik doğrulamasıyla bağlanmak için, Windows PowerShell isteminde bu komutlardan birini çalıştırın. (Yükseltilmiş olması zorunda değil.)

| Office 365 bulut | Komut |
|:-------|:-----|
| Office 365 Dünya Çapında (+GCC) | `Connect-MsolService` |
| Office 365 21 Vianet tarafından işletilen ağ | `Connect-MsolService -AzureEnvironment AzureChinaCloud` |
| Office 365 Almanya | `Connect-MsolService -AzureEnvironment AzureGermanyCloud` |
| Office 365. S. Government DoD ve Office 365 U.S. Government GCC High | `Connect-MsolService -AzureEnvironment USGovernment` |
|||

Hesabınızla **oturum açın iletişim kutusuna** iş veya okul Microsoft 365 kullanıcı adı ve parolanızı yazın ve Tamam'ı **seçin**.

Çok faktörlü kimlik doğrulaması kullanıyorsanız, doğrulama kodu gibi ek kimlik doğrulama bilgilerini sağlamak için yönergeleri izleyin.

### <a name="how-do-you-know-it-worked"></a>Çalıştığını nasıl biliyorsunuz?

Hata iletisi alasanız, başarılı bir şekilde bağlandınız. Hızlı test için, **Get-MsolUser** Microsoft 365 bir cmdlet'i çalıştırın ve sonuçlara bakın.
  
Hata iletisi alırsanız, aşağıdaki sorunları kontrol edin:
  
- **Sık karşılaşılan bir sorun, yanlış paroladır**. [2. Adımı](#step-2-connect-to-azure-ad-for-your-microsoft-365-subscription) yeniden çalıştırın ve girişte yer alan kullanıcı adı ve parolaya dikkat edin.
    
- **İş Microsoft Azure Active Directory modülünde Microsoft Windows PowerShell 3.5 .NET Framework gerekir.* x* bilgisayarınızda** etkindir. Büyük olasılıkla bilgisayarınızda daha yeni bir sürüm yüklüdür (örneğin, 4 veya 4,5).* x*). Ancak, yeni sürümün eski sürümleriyle geriye .NET Framework etkinleştirilebilir veya devre dışı bırakılabilir. Daha fazla bilgi için aşağıdaki makalelere bakın:
    
  - Daha Windows Server 2012 ve Windows Server 2012 R2 için bkz. Rol ve .NET Framework Ekleme Sihirbazı'nı kullanarak .NET Framework [3.5'i etkinleştirme](/previous-versions/windows/it-pro/windows-8.1-and-8/dn482071(v=win.10)).
    
  - 7 Windows 7 veya Windows Server 2008 R2 için bkz. Azure Active Directory [Modülü'ne Windows PowerShell](/troubleshoot/azure/active-directory/cant-open-aad-module-powershell).

  - Daha Windows 10, Windows 8.1 ve Windows 8 için bkz. Windows 10, Windows 8.1 ve diğer .NET Framework [3.5'i Windows 8](/dotnet/framework/install/dotnet-35-windows-10).

  
- **Örneğin, Microsoft Azure Active Directory Modülü Windows PowerShell eski olabilir.** Bunu kontrol etmek için, Microsoft 365 için PowerShell'de veya Microsoft Azure Active Directory Modülü'Windows PowerShell:
    
  ```powershell
  (Get-Item C:\Windows\System32\WindowsPowerShell\v1.0\Modules\MSOnline\Microsoft.Online.Administration.Automation.PSModule.dll).VersionInfo.FileVersion
  ```

    Döndürülen sürüm numarası *1.0.8070.2'den* düşükse, Microsoft Azure Active Directory için Microsoft Azure Active Directory Windows PowerShell Modülü'ünü kaldırın ve [yukarıdaki 1](#step-1-install-the-required-software). Adımdan yükleyin.

- **Bağlantı hata iletisi alırsanız**, ["Bağlan-MsolService: Exception of type was thrown" hatası'ne bakın](/office365/troubleshoot/active-directory/connect-msoservice-throw-exception).
    
- **"Get-Item: Find path" hata iletisini alırsanız**, şu komutu çalıştırın:


   ```powershell
     (dir "C:\Program Files\WindowsPowerShell\Modules\MSOnline").Name
   ```

## <a name="connect-with-the-azure-cloud-shell"></a>Bağlan Bulut Kabuğu ile depolama

Görev çubuğundan Azure Bulut Kabuğu'Microsoft 365 yönetim merkezi bağlanmak ve kullanmak için, görev çubuğunun sağ üst köşesinden PowerShell penceresi simgesini seçin. Azure Bulut **Kabuğu'ne Hoş Geldiniz bölmesinde** **PowerShell'i seçin**.

Yeni abonelik aboneliğinize bağlı olan, organizasyon için etkin bir Azure Microsoft 365 gerekir. Henüz bir tane yoksa, bir tane oluşturabilirsiniz. Azure aboneliğiniz olduktan sonra, PowerShell komutlarını ve betiklerini çalıştırabilirsiniz bir PowerShell penceresi açılır.

Daha fazla bilgi için bkz. [Azure Bulut Kabuğu](/azure/cloud-shell/overview).

## <a name="see-also"></a>Ayrıca bkz.

- [PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
- [Microsoft 365 için PowerShell'i Microsoft 365](getting-started-with-microsoft-365-powershell.md)
- [Bağlan tek Microsoft 365 pencerede tüm Windows PowerShell açma](connect-to-all-microsoft-365-services-in-a-single-windows-powershell-window.md)
