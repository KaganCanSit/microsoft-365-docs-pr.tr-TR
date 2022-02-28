---
title: Çok Exchange Online ortamda posta kutularını yönetme
ms.reviewer: adwood
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-mar2020
ms.localizationpriority: medium
description: PowerShell ile Exchange Online ortamınıza multi-geo ayarlarını Microsoft 365 yönetebilirsiniz.
ms.openlocfilehash: 2e4be2fd506f89579866c61bbf4a8a41aadc0d03
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985152"
---
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a>Çok Exchange Online ortamda posta kutularını yönetme

Exchange Online PowerShell, coğrafi ortamda çoklu coğrafi özellikleri görüntülemek ve yapılandırmak için Microsoft 365 gerekir. Exchange Online PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online e bağlama](/powershell/exchange/connect-to-exchange-online-powershell).

Kullanıcı nesnelerinde **PreferredDataLocation** Microsoft Azure Active Directory görmek için v1.x'te [Microsoft Azure Active Directory PowerShell](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) Modülü v1.1.166.0 veya daha sonraki bir adı gerekir. AAD Bağlan ile eşitlenen kullanıcı nesnelerinin AAD **PreferredDataLocation** değeri, AAD PowerShell aracılığıyla doğrudan değiştirilemez. Yalnızca bulut kullanıcı nesneleri PowerShell AAD değiştirilebilir. Azure AD PowerShell'e bağlanmak için bkz[. Bağlan PowerShell'e bağlanma](connect-to-microsoft-365-powershell.md).

Birden Exchange Online çok coğrafi ortamlarda, kiracınıza coğrafi olarak eklemek için el ile herhangi bir adım atılması gerek değildir. Birden çok coğrafi coğrafinin kullanıma hazır olduğunu söyleyen İleti Merkezi'Exchange Online, kullanılabilen tüm coğrafi coğrafiler hazır olur ve kullanımınız için yapılandırılır.

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a>Bağlan PowerShell kullanarak doğrudan bir Exchange Online konuma sürükleyin

Normalde, Exchange Online PowerShell merkezi coğrafi konuma bağlanacak. Ancak uydu coğrafi konumlarına doğrudan da bağlanabilirsiniz. Performans geliştirmeleri nedeniyle, sadece bu konumdaki kullanıcıları yönetirken uydunun coğrafi konumuyla doğrudan bağlanmayı öneririz.

EXO V2 modülünü yükleme ve kullanma gereksinimleri EXO V2 modülünü [yükleme ve koruma konusunda açıklanmıştır](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

PowerShell Exchange Online belirli bir coğrafi konuma bağlamak için *ConnectionUri* parametresi normal bağlantı yönergelerinden farklıdır. Komutların ve değerlerin geri kalanı aynıdır.

Özel olarak, değeri `?email=<emailaddress>` _ConnectionUri_ değerinin sonuna eklemeniz gerekir. `<emailaddress>` hedef coğrafi konumdaki **herhangi bir posta** kutusunun e-posta adresidir. Bu posta kutusu üzerinde izinlerinizi veya kimlik bilgilerinizle ilişkinizi bir faktör değildir; e-posta adresi yalnızca PowerShell Exchange Online e nereden bağlanılları olduğunu söyler.

Microsoft 365 veya Microsoft 365 GCC diğer müşterilerin normalde Exchange Online PowerShell'e bağlanmak için _ConnectionUri_ parametresini kullanmaları gerekli Exchange Online. Ancak, belirli bir coğrafi konuma bağlanmak için _ConnectionUri_ parametresini kullan çünkü bu parametreyi değerde `?email=<emailaddress>` kullanabilirsiniz.

### <a name="connect-to-a-geo-location-in-exchange-online-powershell"></a>Bağlan PowerShell'de coğrafi Exchange Online konuma sürükleyin

Aşağıdaki bağlantı yönergeleri Multi-Factor Authentication (MFA) için yapılandırılmış veya yapılandırılmamış hesaplarda çalışır.

1. Yeni Windows PowerShell, aşağıdaki komutu çalıştırarak EXO V2 modülünü yükleme:

   ```powershell
   Import-Module ExchangeOnlineManagement
   ```

2. Aşağıdaki örnekte, admin@contoso.onmicrosoft.com hesabı yönetici hesabıdır ve hedef coğrafi konum da posta kutusunun olga@contoso.onmicrosoft.com konumdur.

   ```powershell
   Connect-ExchangeOnline -UserPrincipalName admin@contoso.onmicrosoft.com -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com
   ```

3. Görüntülenen komut istemine admin@contoso.onmicrosoft.com parolayı girin. Hesap MFA için yapılandırılmışsa, güvenlik kodunu da girmeniz gerekir.

## <a name="view-the-available-geo-locations-that-are-configured-in-your-exchange-online-organization"></a>Exchange Online 2013'te yapılandırılmış mevcut coğrafi Exchange Online görüntüleme

Multi-Geo'da yapılandırılmış coğrafi konumların listesini Microsoft 365, Exchange Online PowerShell'de şu komutu çalıştırın:

```powershell
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

## <a name="view-the-central-geo-location-for-your-exchange-online-organization"></a>Kuruluş için merkezi coğrafi konumu Exchange Online görüntüleme

Kiracının merkezi coğrafi konumunu görüntülemek için, PowerShell'de aşağıdaki Exchange Online çalıştırın:

```powershell
Get-OrganizationConfig | Select DefaultMailboxRegion
```

## <a name="find-the-geo-location-of-a-mailbox"></a>Posta kutusunun coğrafi konumunu bulma

**PowerShell'de Get-Mailbox** cmdlet'i Exchange Online, posta kutularında aşağıdaki multi-geo ile ilgili özellikleri görüntüler:

- **Veritabanı**: Veritabanı adının ilk 3 harfi, posta kutusunun şu anda nerede olduğunu söyleyen coğrafi koda karşılık geldi. Çevrimiçi Arşiv Posta Kutuları için **ArchiveDatabase** özelliği kullanılmalıdır.

- **MailboxRegion**: Yönetici tarafından ayarlanmış olan coğrafi konum kodunu belirtir (Azure AD'de **PreferredDataLocation** bölümünden eşitlenir).

- **MailboxRegionLastUpdateTime**: MailboxRegion'in en son ne zaman güncelleştirildığını gösterir (otomatik olarak veya el ile).

Posta kutusunun bu özelliklerini görmek için aşağıdaki söz dizimi kullanın:

```powershell
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

Örneğin, posta kutusunun coğrafi konum bilgilerini görmek chris@contoso.onmicrosoft.com aşağıdaki komutu çalıştırın:

```powershell
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

Komutun çıkışı şöyle görünüyor:

```powershell
Database                    : EURPR03DG077-db007
MailboxRegion               : EUR
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM
```

> [!NOTE]
> Veritabanı adı'nın coğrafi konum kodu **MailboxRegion** değeriyle eş eşşilmezse, posta kutusu otomatik olarak yeniden yükleme sırasına taşınır ve **MailboxRegion** değeri tarafından belirtilen coğrafi konuma taşınır (Exchange Online bu özellik değerleri arasında bir eşleşme olup olmadığını aramaktadır).

## <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a>Var olan bir yalnızca bulut posta kutusunu belirli bir coğrafi konuma taşıma

Yalnızca bulut kullanıcı, kullanıcı eşitleme yoluyla kiracıyla eşitlen AAD Bağlan. Bu kullanıcı doğrudan Azure AD'de oluşturulmuş. Windows PowerShell için Azure AD Modülü'ne **Get-MsolUser** ve **Set-MsolUser** cmdlet'lerini kullanarak yalnızca bulut kullanıcı posta kutusunun depolandığı coğrafi konumu görüntüde veya belirtebilirsiniz.

Kullanıcının **PreferredDataLocation değerini** görüntülemek için, Azure AD PowerShell'de şu söz dizimi kullanın:

```powershell
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

Örneğin, kullanıcının Tercih **EdilenVeri Yerleşimi** değerini görmek michelle@contoso.onmicrosoft.com aşağıdaki komutu çalıştırın:

```powershell
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

Yalnızca bulut kullanan **bir kullanıcı nesnesi için PreferredDataLocation** değerini değiştirmek için, Azure AD PowerShell'de aşağıdaki söz dizimi kullanın:

```powershell
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoLocationCode>
```

Örneğin, kullanıcı konumu olarak **PreferredDataLocation** değerini Avrupa Birliği (EUR) coğrafi olarak michelle@contoso.onmicrosoft.com, aşağıdaki komutu çalıştırın:

```powershell
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

> [!NOTE]
>
> - Daha önce de belirtildiği gibi, şirket içi Active Directory'den eşitlenmiş kullanıcı nesneleri için bu yordamı kullanılamaz. Active Directory'de **PreferredDataLocation değerini** değiştirmeli ve Eşitlemek için Tercih Edilen AAD Bağlan. Daha fazla bilgi için bkz. [Azure Active Directory Bağlan eşitlemeyi yapılandırma: Bu kaynaklar için tercih Microsoft 365 yapılandırma](/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).
>
> - Posta kutusunu yeni bir coğrafi konuma ne kadar süreyle yeniden konumunu bulmanız birkaç etmene bağlıdır:
>
>   - Posta kutusunun boyutu ve türü.
>   - Taşınan posta kutularının sayısı.
>   - Taşıma kaynaklarının kullanılabilirliği.

### <a name="move-an-inactive-mailbox-to-a-specific-geo"></a>Etkin olmayan posta kutusunu belirli bir coğrafi bölgeye taşıma

PreferredDataLocation değerini değiştirerek, uyumluluk amacıyla korunan etkin olmayan posta kutularını (örneğin, Mahkeme Nedeniyle Tutma'daki posta kutuları) **hareket ettirebilirsiniz** . Etkin olmayan posta kutusunu farklı bir coğrafi bölgeye taşımak için aşağıdaki adımları izleyin:

1. Etkin olmayan posta kutusunu kurtarabilirsiniz. Yönergeler için bkz. [Etkin olmayan posta kutusunu kurtarma](../compliance/recover-an-inactive-mailbox.md).

2. Yönetilen Klasör Yardımcısı'nın\<MailboxIdentity\>, posta kutusunun adı, diğer adı, hesabı veya e-posta adresini değiştirerek ve PowerShell'de aşağıdaki komutu çalıştırarak kurtarılan [posta kutusunu işlemesini Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell):

    ```powershell
    Set-Mailbox <MailboxIdentity> -ElcProcessingDisabled $true
    ```

3. Kurtarılan **Exchange Online Posta Kutusu için Plan 2** lisansı attayabilirsiniz. Posta kutusunu yeniden Mahkeme Tutma'ya geri tutmak için bu adım gereklidir. Yönergeler için bkz [. Kullanıcılara lisans atama](../admin/manage/assign-licenses-to-users.md).

4. Posta kutusunda **PreferredDataLocation** değerini önceki bölümde açıklandığı gibi yapılandırın.

5. Posta kutusunun yeni coğrafi konuma taşındığını onay verdikten sonra, kurtarılan posta kutusunu yeniden Mahkeme Tutma'ya alın. Yönergeler için bkz [. Mahkeme Tutma'ya posta kutusu yükleme](../compliance/create-a-litigation-hold.md#place-a-mailbox-on-litigation-hold).

6. Mahkeme Tutma'nın var olduğunu doğruladikten sonra, Yönetilen Klasör Yardımcısı'nın posta kutusunun adı, diğer adı, \<MailboxIdentity\> hesabı veya e-posta adresiyle değiştirerek ve Exchange Online PowerShell'de şu komutu çalıştırarak posta kutusunu [yeniden işlemesine izin](/powershell/exchange/connect-to-exchange-online-powershell) Exchange Online:

    ```powershell
    Set-Mailbox <MailboxIdentity> -ElcProcessingDisabled $false
    ```

7. Posta kutusuyla ilişkilendirilmiş kullanıcı hesabını kaldırarak posta kutusunu yeniden devre dışı hale alın. Yönergeler için bkz [. Kuruluştan kullanıcı silme](../admin/add-users/delete-a-user.md). Bu adım, diğer kullanımlar Exchange Online Plan 2 lisansını da yayımlar.

**Not**: Etkin olmayan bir posta kutusunu farklı bir coğrafi konuma taşıyabilirsiniz, içerik arama sonuçlarını veya posta kutusunda eski coğrafi konumdan arama yapma olanağını etkileyebilirsiniz. Daha fazla bilgi için bkz [. Multi-Geo ortamlarında içerik arama ve dışarı aktarma](../compliance/set-up-compliance-boundaries.md#searching-and-exporting-content-in-multi-geo-environments).

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a>Belirli bir coğrafi konumda yeni bulut posta kutuları oluşturma

Belirli bir coğrafi konumda yeni posta kutusu oluşturmak için şu adımlardan birini uygulayın:

- Posta kutusunu **Yeni'de** oluşturmadan önce, Yalnızca buluttaki var olan bir posta kutusunu belirli bir coğrafi konuma taşıma bölümünde açıklandığı  gibi PreferredDataLocation Exchange Online.[](#move-an-existing-cloud-only-mailbox-to-a-specific-geo-location) Örneğin, lisans atamadan **önce kullanıcıda PreferredDataLocation** değerini yapılandırın.

- **PreferredDataLocation** değerini ayardığınız sırada lisans attayın.

Belirli bir coğrafi konumda yalnızca bulut lisanslı yeni bir kullanıcı (AAD Bağlan değil) oluşturmak için, Azure AD PowerShell'de aşağıdaki söz dizimi kullanın:

```powershell
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoLocationCode>
```

Bu örnekte, Elizabeth Brunner için aşağıdaki değerlerle yeni bir kullanıcı hesabı oluşturun:

- Kullanıcı asıl adı: ebrunner@contoso.onmicrosoft.com
- Ad: Elizabeth
- Soyadı: Brunner
- Görünen ad: Elizabeth Brunner
- Parola: Rastgele oluşturulur ve komutun sonuçlarında gösterilir ( *Password parametresi kullanmamız* gerekir)
- Lisans: `contoso:ENTERPRISEPREMIUM` (E5)
- Konum: Avustralya (AUS)

```powershell
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Azure AD PowerShell'de yeni kullanıcı hesapları oluşturma ve LisansAssignment değerlerini bulma hakkında daha fazla bilgi için bkz. [PowerShell](create-user-accounts-with-microsoft-365-powershell.md) ile kullanıcı hesapları oluşturma ve [PowerShell](view-licenses-and-services-with-microsoft-365-powershell.md) ile lisansları ve hizmetleri görüntüleme.

> [!NOTE]
> Bir posta kutusunu etkinleştirmek için Exchange Online PowerShell kullanıyorsanız ve posta kutusunun **doğrudan PreferredDataLocation'de** belirtilen coğrafi konumda oluşturulmuş olması gerekiyorsa, doğrudan bulut hizmetine karşı **Enable-Mailbox** veya **New-Mailbox** gibi bir Exchange Online cmdlet'i kullansanız gerekir. Şirket içi **PowerShell'de Enable-RemoteMailbox** cmdlet'ini Exchange, posta kutusu merkezi coğrafi konumda oluşturulur.

## <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo-location"></a>Mevcut şirket içi posta kutularını belirli bir coğrafi konuma ekleme

Standart ekleme araçlarını ve işlemlerini kullanarak posta kutusunu şirket içi Exchange kuruluşundan [EAC'daki Geçiş](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331) panosu ve Exchange Online PowerShell'de [New-MigrationBatch](/powershell/module/exchange/new-migrationbatch) cmdlet'i de dahil olmak üzere Exchange Online'e geçirebilirsiniz.

İlk adım, her posta kutusunun girilmiş olması için bir kullanıcı nesnesinin var olduğunu doğrulamak ve Azure AD'de doğru **PreferredDataLocation** değerinin yapılandırıldığından emin olmaktır. Ekleme araçları **PreferredDataLocation değerine uyar** ve posta kutularını doğrudan belirtilen coğrafi konuma geçirir.

Ya da, Exchange Online PowerShell'de [New-MoveRequest](/powershell/module/exchange/new-moverequest) cmdlet'ini kullanarak posta kutularını doğrudan belirli bir coğrafi konuma ekleme adımlarını kullanabilirsiniz.

1. Her posta kutusu için ekleme için kullanıcı nesnesinin var olduğunu ve **PreferredDataLocation'in** Azure AD'de istenen değere ayar olduğunu doğrulayın. **PreferredDataLocation değeri**, Exchange Online'te ilgili posta kullanıcısı nesnesinin **MailboxRegion** özniteliğiyle eşitlenir.

2. Bağlan daha önce verilen bağlantı yönergelerini kullanarak uydu coğrafi konumuyla doğrudan bağlantı kurun.

3. PowerShell Exchange Online de, posta kutusu geçişi gerçekleştirmek için kullanılan şirket içi yönetici kimlik bilgilerini değişkende depolamak için aşağıdaki komutu çalıştırabilirsiniz:

   ```powershell
   $RC = Get-Credential
   ```

4. PowerShell Exchange Online, aşağıdaki örnekteki gibi yeni bir **New-MoveRequest** oluşturun:

   ```powershell
   New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
   ```

5. Şirket içi posta kutusundan o anda bağlı olduğunuz uydu coğrafi konuma Exchange tüm posta kutuları için 4. adımı yinelayın.

6. Başka posta kutularını farklı uydu coğrafi konumlara geçirmeniz gerekirse, 2 ile 4 arasında olan adımları belirli konumlarda yinelayın.

## <a name="multi-geo-reporting"></a>Multi-geo reporting

**Birden Çok Coğrafi Kullanım Raporu** Microsoft 365 yönetim merkezi coğrafi konuma göre kullanıcı sayısını görüntüler. Rapor, geçerli ayın kullanıcı dağılımını görüntüler ve son 6 ayın geçmiş verilerini sağlar.

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell Microsoft 365'i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)