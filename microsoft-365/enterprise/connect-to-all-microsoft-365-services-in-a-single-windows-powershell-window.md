---
title: Bağlan PowerShell Microsoft 365 tek bir PowerShell penceresinde tüm diğer hizmetlere açık
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/23/2021
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- LIL_Placement
- Ent_Office_Other
- O365ITProTrain
- httpsfix
ms.assetid: 53d3eef6-4a16-4fb9-903c-816d5d98d7e8
description: 'Özet: Bağlan PowerShell Microsoft 365 tüm hizmetlerde kullanabilirsiniz.'
ms.openlocfilehash: 4df9a16aba22587adbe289bca2d74e78a64db4ba
ms.sourcegitcommit: b51bfed24a9e3b7adf82d4918b76462cd40dffaf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "63008085"
---
# <a name="connect-to-all-microsoft-365-services-in-a-single-powershell-window"></a>Bağlan PowerShell Microsoft 365 tek bir PowerShell penceresinde tüm diğer hizmetlere açık

PowerShell'i kullanarak Microsoft 365, aynı anda birden çok PowerShell oturumu açabilirsiniz. Kullanıcı hesaplarını yönetmek için SharePoint Online, Exchange Online, Skype Kurumsal Online&amp;, Microsoft Teams ve Güvenlik Uyumluluk Merkezi'nde farklı PowerShell pencereleriniz olabilir.
  
Bu senaryo, hizmet yönetimi Microsoft 365 için en uygun senaryo değildir, çünkü çapraz hizmet yönetimi için bu pencereler arasında veri alışverişinde bulunamaz. Bu makalede, Microsoft 365 Online, Skype Kurumsal Online, Exchange Online, SharePoint Online&amp;, Microsoft Teams ve Güvenlik Uyumluluk Merkezi'nde hesapları yönetmek için tek bir PowerShell örneğini nasıl kullanabileceğiniz açıklanmıştır.

>[!Note]
>Bu makale şu anda yalnızca Dünya Çapında (+GCC) buluta bağlanma komutlarını içerir. Notlar, diğer bulutlara bağlanmayla ilgili makalelerin Microsoft 365 sağlar.

## <a name="before-you-begin"></a>Başlamadan önce

Tüm bilgileri tek bir PowerShell Microsoft 365 bir örnekten yönetemeden önce, aşağıdaki önkoşulları göz önünde bulundurabilirsiniz:
  
- Kullanabileceğiniz Microsoft 365 veya okul hesabı, yönetici rolüne üye Microsoft 365 gerekir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../admin/add-users/about-admin-roles.md). Bu, Microsoft 365 için PowerShell için bir gereksinimdir, ancak diğer tüm Microsoft 365 olmayabilir.
    
- E-postanın aşağıdaki 64 bit sürümlerini Windows:
    
  - Windows 10
    
  - Windows 8.1 veya Windows 8
    
  - Windows Server 2019
    
  - Windows Server 2016
    
  - Windows Server 2012 R2 veya Windows Server 2012
    
  - Windows 7 Service Pack 1 (SP1)*
    
  - Windows Server 2008 R2 SP1*
    
    \*Microsoft .NET Framework 4.5'i yüklemeniz gerekir.*x'e* Windows Management Framework 3.0 veya 4.0'a basın. Daha fazla bilgi için bkz. [Windows Management Framework](/powershell/scripting/windows-powershell/wmf/overview).
    
    Skype Kurumsal Online modülüne ve Windows modüllerinden birinin gereksinimleri nedeniyle, Skype Kurumsal'un 64 bit sürümünü Microsoft 365 gerekir.
    
- Azure Active Directory, Exchange Online, SharePoint Online, Skype Kurumsal Online ve diğer Teams için gereken modülleri yüklemeniz gerekir:
    
  - [Azure Active Directory V2](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module)
  - [SharePoint Online Yönetim Kabuğu](https://go.microsoft.com/fwlink/p/?LinkId=255251)
  - [Skype Kurumsal Online, PowerShell Modülü](/microsoftteams/teams-powershell-overview)
  - [Exchange Online PowerShell V2](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exchange-online-powershell-v2-module)
  - [Teams PowerShell'e Genel Bakış](/microsoftteams/teams-powershell-overview)
    
-  PowerShell'in, Skype Kurumsal Online'da ve Güvenlik Uyumluluk Merkezi'nde imzalanmış betikleri çalıştıracak şekilde &amp; yapılandırılması gerekir. Yükseltilmiş bir PowerShell oturumunda (yönetici olarak çalıştırdınız bir PowerShell oturumu) **aşağıdaki komutu çalıştırın**.
    
   ```powershell
   Set-ExecutionPolicy RemoteSigned
   ```

## <a name="connection-steps-when-using-just-a-password"></a>Yalnızca parola kullanırken bağlantı adımları

Oturum açma için yalnızca parola kullanırken tek bir PowerShell penceresinde tüm hizmetlere bağlanmak için bu adımları izleyin.
  
1. Diğer Windows PowerShell.
    
2. Bu komutu çalıştırın ve iş Microsoft 365 okul hesabı kimlik bilgilerinizi girin.
    
   ```powershell
   $credential = Get-Credential
   ```

3. Graph için PowerShell modülünü kullanarak Azure AD'ye Azure Active Directory bu komutu çalıştırın.
    
   ```powershell
   Connect-AzureAD -Credential $credential
   ```
  
   Ya da modül için Microsoft Azure Active Directory Modülü'Windows PowerShell, bu komutu çalıştırın.
      
   ```powershell
   Connect-MsolService -Credential $credential
   ```

   > [!Note]
   > PowerShell Core, adı *Msol* olan Microsoft Azure Active Directory Modülü Windows PowerShell cmdlet'leri desteklemez. PowerShell'den bu cmdlet'leri çalıştırabilirsiniz.

4. SharePoint Online'a bağlanmak için bu komutları çalıştırın. Etki alanınız için kuruluş adını belirtin. Örneğin, "litwareinc\. onmicrosoft.com" için, kuruluş adı değeri "litwareinc" olur.
    
   ```powershell
   $orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
   Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
   Connect-SPOService -Url https://$orgName-admin.sharepoint.com -Credential $Credential
   ```

5. Exchange Online'a bağlanmak için bu komutları Exchange Online.
    
   ```powershell
   Import-Module ExchangeOnlineManagement
   Connect-ExchangeOnline -ShowProgress $true
   ```

   > [!Note]
   > Dünya Çapında dışında Exchange Online bulut Microsoft 365 bulutlara bağlanmak için bkz. [Bağlan PowerShell'Exchange Online bağlama](/powershell/exchange/connect-to-exchange-online-powershell).

6. Güvenlik Uyumluluk Merkezi'ne bağlanmak için bu &amp; komutları çalıştırın.
    
   ```powershell
   $acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
   Connect-IPPSSession -UserPrincipalName $acctName
   ```

   > [!Note]
   > Dünya Çapında dışında bulut bulutları &amp; Microsoft 365 Güvenlik Uyumluluk Merkezi'ne bağlanmak için bkz. [Bağlan ve Uyumluluk & PowerShell'e bağlanma](/powershell/exchange/connect-to-scc-powershell).

7. Teams PowerShell'e (ve Skype Kurumsal Online'a) bağlanmak için bu Skype Kurumsal çalıştırın.
    
   ```powershell
   Import-Module MicrosoftTeams
   $credential = Get-Credential
   Connect-MicrosoftTeams -Credential $credential
   ```
  
   > [!Note]
   > Skype Kurumsal Online Connector şu anda en son PowerShell modülünde Teams vardır. En son PowerShell Teams kullanıyorsanız, Skype Kurumsal Online Connector'ı yüklemenize gerek yok.
  
   > [!Note]
   > Dünya Çapında dışında Microsoft Teams bulutlara *bağlanmak için* bkz. [Bağlan-MicrosoftTeams](/powershell/module/teams/connect-microsoftteams).
  


### <a name="azure-active-directory-powershell-for-graph-module"></a>Azure Active Directory için PowerShell Graph modülü

Burada, Graph için PowerShell modülünde Azure Active Directory tüm hizmetlerin komutları ve tek Graph ve kullanımıdır. Etki alanı barındırma adınızı ve oturum açma için UPN'yi belirtin ve hepsini aynı anda çalıştırın.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$credential = Get-Credential -UserName $acctName -Message "Type the account's password."
#Azure Active Directory
Connect-AzureAD -Credential $credential
#SharePoint Online
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
#Exchange Online
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -ShowProgress $true
#Security & Compliance Center
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

### <a name="microsoft-azure-active-directory-module-for-windows-powershell-module"></a>Microsoft Azure Active Directory modülü için Windows PowerShell Modülü

Burada, kaynak modülü için Modül Için Microsoft Azure Active Directory'i kullanıyorken tek Windows PowerShell vardır. Etki alanı barındırma adınızı ve oturum açma için UPN'yi belirtin ve hepsini bir defada çalıştırın.
  
```powershell
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$credential = Get-Credential -UserName $acctName -Message "Type the account's password."
#Azure Active Directory
Connect-MsolService -Credential $credential
#SharePoint Online
Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
Connect-SPOService -Url https://$orgName-admin.sharepoint.com -credential $credential
#Exchange Online
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -ShowProgress $true
#Security & Compliance Center
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams -Credential $credential
```

## <a name="connection-steps-when-using-multi-factor-authentication"></a>Multi-factor authentication kullanırken bağlantı adımları

### <a name="azure-active-directory-powershell-for-graph-module"></a>Azure Active Directory için PowerShell Graph modülü

Graph için PowerShell modülüyle çok faktörlü kimlik doğrulaması kullanırsanız, tek bir blokta birden çok Azure Active Directory Microsoft 365 bağlanabilirsiniz.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-AzureAD
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Exchange Online
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Security & Compliance Center
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```
### <a name="microsoft-azure-active-directory-module-for-windows-powershell-module"></a>Microsoft Azure Active Directory modülü için Windows PowerShell Modülü

İşte, birden çok Microsoft 365 hizmetine bağlanmak için tek bir blokta yer alan tüm komutlar, Microsoft Azure Active Directory modülü için Windows PowerShell kullanır.

```powershell
$acctName="<UPN of the account, such as belindan@litwareinc.onmicrosoft.com>"
$orgName="<for example, litwareinc for litwareinc.onmicrosoft.com>"
#Azure Active Directory
Connect-MsolService
#SharePoint Online
Connect-SPOService -Url https://$orgName-admin.sharepoint.com
#Exchange Online
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName $acctName -ShowProgress $true
#Security & Compliance Center
Connect-IPPSSession -UserPrincipalName $acctName
#Teams and Skype for Business Online
Import-Module MicrosoftTeams
Connect-MicrosoftTeams
```

## <a name="close-the-powershell-window"></a>PowerShell penceresini kapatma

PowerShell penceresini kapatmak için, bu komutu çalıştırarak SharePoint Online'da etkin oturumları Teams:
  
```powershell
Disconnect-SPOService ; Disconnect-MicrosoftTeams 
```

## <a name="see-also"></a>Ayrıca bkz.

- [Bağlan'Microsoft 365 PowerShell'i de](connect-to-microsoft-365-powershell.md)
- [PowerShell SharePoint Online'da yönetme](manage-sharepoint-online-with-microsoft-365-powershell.md)
- [PowerShell Microsoft 365 hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)
