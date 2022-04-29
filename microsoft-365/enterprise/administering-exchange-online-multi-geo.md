---
title: Çok coğrafi bir ortamda Exchange Online posta kutularını yönetme
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
description: PowerShell ile Microsoft 365 ortamınızda çok coğrafi Exchange Online ayarlarını yönetmeyi öğrenin.
ms.openlocfilehash: 4b0b02fa9ea974784ec93efe83520faed5fd05bd
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130877"
---
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a>Çok coğrafi bir ortamda Exchange Online posta kutularını yönetme

Exchange Online PowerShell, Microsoft 365 ortamınızdaki çok coğrafi özellikleri görüntülemek ve yapılandırmak için gereklidir. Exchange Online PowerShell'e bağlanmak için bkz. [PowerShell'Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell).

Kullanıcı nesnelerinde **PreferredDataLocation** özelliğini görmek için v1.x'te [Microsoft Azure Active Directory PowerShell Modülü](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 veya üzeri gerekir. AAD Bağlan aracılığıyla AAD ile eşitlenen kullanıcı nesnelerinin **PreferredDataLocation** değerleri AAD PowerShell aracılığıyla doğrudan değiştirilemez. Yalnızca bulut kullanıcı nesneleri AAD PowerShell aracılığıyla değiştirilebilir. Azure AD PowerShell'e bağlanmak için bkz. [PowerShell'e Bağlan](connect-to-microsoft-365-powershell.md).

çok coğrafi Exchange Online ortamlarda, kiracınıza coğrafi bölge eklemek için el ile herhangi bir adım uygulamanız gerekmez. Çok coğrafi konumun Exchange Online için hazır olduğunu belirten İleti Merkezi gönderisini aldıktan sonra, kullanabileceğiniz tüm coğrafi bölgeler hazır ve yapılandırılır.

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a>Exchange Online PowerShell kullanarak doğrudan coğrafi konuma Bağlan

Genellikle, Exchange Online PowerShell merkezi coğrafi konuma bağlanır. Ancak doğrudan uydu coğrafi konumlarına da bağlanabilirsiniz. Performans geliştirmeleri nedeniyle, yalnızca bu konumdaki kullanıcıları yönetirken doğrudan uydu coğrafi konumuna bağlanmanızı öneririz.

EXO V2 modülünü yükleme ve kullanma gereksinimleri [, EXO V2 modülünü yükleme ve koruma](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module) başlığında açıklanmıştır.

Exchange Online PowerShell'i belirli bir coğrafi konuma bağlamak için *ConnectionUri* parametresi normal bağlantı yönergelerinden farklıdır. Komutların ve değerlerin geri kalanı aynıdır.

Özellikle, _ConnectionUri_ değerinin `?email=<emailaddress>` sonuna değeri eklemeniz gerekir. `<emailaddress>` hedef coğrafi konumdaki **herhangi bir** posta kutusunun e-posta adresidir. Bu posta kutusuna ilişkin izinleriniz veya kimlik bilgilerinizle olan ilişkinin bir faktörü yoktur; e-posta adresi Exchange Online PowerShell'e nereye bağlanacaklarını söyler.

Microsoft 365 veya Microsoft 365 GCC müşterilerin genellikle Exchange Online PowerShell'e bağlanmak için _ConnectionUri_ parametresini kullanmaları gerekmez. Ancak, belirli bir coğrafi konuma bağlanmak için _connectionUri_ parametresini kullanmanız gerekir, böylece değeri kullanabilirsiniz `?email=<emailaddress>` .

### <a name="connect-to-a-geo-location-in-exchange-online-powershell"></a>Exchange Online PowerShell'de coğrafi konuma Bağlan

Aşağıdaki bağlantı yönergeleri, çok faktörlü kimlik doğrulaması (MFA) için yapılandırılmış veya yapılandırılmamış hesaplarda çalışır.

1. Windows PowerShell bir pencerede aşağıdaki komutu çalıştırarak EXO V2 modülünü yükleyin:

   ```powershell
   Import-Module ExchangeOnlineManagement
   ```

2. Aşağıdaki örnekte, admin@contoso.onmicrosoft.com yönetici hesabıdır ve hedef coğrafi konum, posta kutusunun olga@contoso.onmicrosoft.com bulunduğu yerdir.

   ```powershell
   Connect-ExchangeOnline -UserPrincipalName admin@contoso.onmicrosoft.com -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com
   ```

3. Görüntülenen istemde admin@contoso.onmicrosoft.com parolasını girin. Hesap MFA için yapılandırılmışsa, güvenlik kodunu da girmeniz gerekir.

## <a name="view-the-available-geo-locations-that-are-configured-in-your-exchange-online-organization"></a>Exchange Online kuruluşunuzda yapılandırılan kullanılabilir coğrafi konumları görüntüleme

Microsoft 365 Multi-Geo'da yapılandırılmış coğrafi konumların listesini görmek için PowerShell Exchange Online de aşağıdaki komutu çalıştırın:

```powershell
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

## <a name="view-the-central-geo-location-for-your-exchange-online-organization"></a>Exchange Online kuruluşunuzun merkezi coğrafi konumunu görüntüleme

Kiracınızın merkezi coğrafi konumunu görüntülemek için Exchange Online PowerShell'de aşağıdaki komutu çalıştırın:

```powershell
Get-OrganizationConfig | Select DefaultMailboxRegion
```

## <a name="find-the-geo-location-of-a-mailbox"></a>Posta kutusunun coğrafi konumunu bulma

Exchange Online PowerShell'deki **Get-Mailbox** cmdlet'i posta kutularında aşağıdaki çok coğrafi ilişkili özellikleri görüntüler:

- **Veritabanı**: Veritabanı adının ilk 3 harfi, posta kutusunun şu anda nerede olduğunu bildiren coğrafi koda karşılık gelir. Çevrimiçi Arşiv Posta Kutuları için **ArchiveDatabase** özelliği kullanılmalıdır.

- **MailboxRegion**: Yönetici tarafından ayarlanan coğrafi konum kodunu belirtir (Azure AD **PreferredDataLocation** öğesinden eşitlenir).

- **MailboxRegionLastUpdateTime**: MailboxRegion'ın en son ne zaman güncelleştirildiğini gösterir (otomatik veya el ile).

Posta kutusunun bu özelliklerini görmek için aşağıdaki söz dizimini kullanın:

```powershell
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

Örneğin, posta kutusu chris@contoso.onmicrosoft.com coğrafi konum bilgilerini görmek için aşağıdaki komutu çalıştırın:

```powershell
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

Komutun çıkışı şöyle görünür:

```powershell
Database                    : EURPR03DG077-db007
MailboxRegion               : EUR
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM
```

> [!NOTE]
> Veritabanı adındaki coğrafi konum kodu **MailboxRegion** değeriyle eşleşmiyorsa, posta kutusu otomatik olarak yeniden konumlandırma kuyruğuna alınır ve **MailboxRegion** değeri tarafından belirtilen coğrafi konuma taşınır (Exchange Online bu özellik değerleri arasında uyuşmazlık arar).

## <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a>Mevcut yalnızca bulut posta kutusunu belirli bir coğrafi konuma taşıma

Yalnızca bulut kullanıcısı, AAD Bağlan aracılığıyla kiracıyla eşitlenmemiş bir kullanıcıdır. Bu kullanıcı doğrudan Azure AD oluşturuldu. Windows PowerShell için Azure AD Modülündeki **Get-MsolUser** ve **Set-MsolUser** cmdlet'lerini kullanarak yalnızca bulut kullanıcısının posta kutusunun depolanacağı coğrafi konumu görüntüleyin veya belirtin.

Kullanıcının **PreferredDataLocation** değerini görüntülemek için powershell Azure AD şu söz dizimini kullanın:

```powershell
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

Örneğin, kullanıcı michelle@contoso.onmicrosoft.com **PreferredDataLocation** değerini görmek için aşağıdaki komutu çalıştırın:

```powershell
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

Yalnızca bulutta bulunan bir kullanıcı nesnesinin **PreferredDataLocation** değerini değiştirmek için PowerShell Azure AD de aşağıdaki söz dizimini kullanın:

```powershell
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoLocationCode>
```

Örneğin, kullanıcı michelle@contoso.onmicrosoft.com **PreferredDataLocation** değerini Avrupa Birliği (EUR) coğrafi konumuna ayarlamak için aşağıdaki komutu çalıştırın:

```powershell
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

> [!NOTE]
>
> - Daha önce belirtildiği gibi, şirket içi Active Directory eşitlenmiş kullanıcı nesneleri için bu yordamı kullanamazsınız. Active Directory'de **PreferredDataLocation** değerini değiştirmeniz ve AAD Bağlan kullanarak eşitlemeniz gerekir. Daha fazla bilgi için bkz. [Azure Active Directory Bağlan eşitleme: Microsoft 365 kaynaklar için tercih edilen veri konumunu yapılandırma](/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).
>
> - Posta kutusunun yeni bir coğrafi konuma taşınma süresi çeşitli faktörlere bağlıdır:
>
>   - Posta kutusunun boyutu ve türü.
>   - Taşınan posta kutularının sayısı.
>   - Taşıma kaynaklarının kullanılabilirliği.

### <a name="move-an-inactive-mailbox-to-a-specific-geo"></a>Etkin olmayan posta kutusunu belirli bir coğrafi bölgeye taşıma

Uyumluluk amacıyla korunan etkin olmayan posta kutularını (örneğin, Dava Tutmadaki posta kutuları) **PreferredDataLocation** değerlerini değiştirerek taşıyamazsınız. Etkin olmayan posta kutusunu farklı bir coğrafi bölgeye taşımak için aşağıdaki adımları uygulayın:

1. Etkin olmayan posta kutusunu kurtarın. Yönergeler için bkz [. Etkin olmayan posta kutusunu kurtarma](../compliance/recover-an-inactive-mailbox.md).

2. Yönetilen Klasör Yardımcısı'nın kurtarılan posta kutusunu işlemesini önlemek için yerine posta kutusunun \<MailboxIdentity\> adını, diğer adını, hesabını veya e-posta adresini yazın ve [Exchange Online PowerShell'de](/powershell/exchange/connect-to-exchange-online-powershell) aşağıdaki komutu çalıştırın:

    ```powershell
    Set-Mailbox <MailboxIdentity> -ElcProcessingDisabled $true
    ```

3. Kurtarılan posta kutusuna **bir Exchange Online Plan 2** lisansı atayın. Bu adım, posta kutusunu Dava Tutma'ya geri yerleştirmek için gereklidir. Yönergeler için bkz. [Kullanıcılara lisans atama](../admin/manage/assign-licenses-to-users.md).

4. Önceki bölümde açıklandığı gibi posta kutusunda **PreferredDataLocation** değerini yapılandırın.

5. Posta kutusunun yeni coğrafi konuma taşındığını onayladıktan sonra, kurtarılan posta kutusunu Dava Tutma'ya geri yerleştirin. Yönergeler için bkz [. Dava Tutma'ya posta kutusu yerleştirme](../compliance/create-a-litigation-hold.md#place-a-mailbox-on-litigation-hold).

6. Dava Tutma'nın yerinde olduğunu doğruladıktan sonra, Yönetilen Klasör Yardımcısı'nın posta kutusunun adını, diğer adını, hesabını veya e-posta adresini değiştirip \<MailboxIdentity\> [Exchange Online PowerShell'de](/powershell/exchange/connect-to-exchange-online-powershell) aşağıdaki komutu çalıştırarak posta kutusunu yeniden işlemesine izin verin:

    ```powershell
    Set-Mailbox <MailboxIdentity> -ElcProcessingDisabled $false
    ```

7. Posta kutusuyla ilişkili kullanıcı hesabını kaldırarak posta kutusunu yeniden devre dışı bırak. Yönergeler için bkz. [Kuruluşunuzdan kullanıcı silme](../admin/add-users/delete-a-user.md). Bu adım, diğer kullanımlar için Exchange Online Plan 2 lisansını da yayınlar.

**Not**: Etkin olmayan bir posta kutusunu farklı bir coğrafi konuma taşıdığınızda, içerik arama sonuçlarını veya eski coğrafi konumdan posta kutusunda arama yapma özelliğini etkileyebilirsiniz. Daha fazla bilgi için bkz [. Multi-Geo ortamlarında içerik arama ve dışarı aktarma](../compliance/set-up-compliance-boundaries.md#searching-and-exporting-content-in-multi-geo-environments).

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a>Belirli bir coğrafi konumda yeni bulut posta kutuları oluşturma

Belirli bir coğrafi konumda yeni bir posta kutusu oluşturmak için şu adımlardan birini uygulamanız gerekir:

- Exchange Online'da posta kutusunu *oluşturmadan önce*, **preferredDataLocation** değerini önceki [Yalnızca bulut posta kutusunu belirli bir coğrafi konuma taşıma](#move-an-existing-cloud-only-mailbox-to-a-specific-geo-location) bölümünde açıklandığı gibi yapılandırın. Örneğin, lisans atamadan önce kullanıcıda **PreferredDataLocation** değerini yapılandırın.

- **PreferredDataLocation** değerini ayarladığınız anda bir lisans atayın.

Belirli bir coğrafi konumda yeni bir yalnızca bulut lisanslı kullanıcı (AAD Bağlan eşitlenmemiş) oluşturmak için powershell Azure AD de aşağıdaki söz dizimini kullanın:

```powershell
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoLocationCode>
```

Bu örnekte Elizabeth Brunner için aşağıdaki değerlerle yeni bir kullanıcı hesabı oluşturulur:

- Kullanıcı asıl adı: ebrunner@contoso.onmicrosoft.com
- Ad: Elizabeth
- Soyadı: Brunner
- Görünen ad: Elizabeth Brunner
- Parola: rastgele oluşturulur ve komutun sonuçlarında gösterilir ( *çünkü Password* parametresini kullanmıyoruz)
- Lisans: `contoso:ENTERPRISEPREMIUM` (E5)
- Konum: Avustralya (AUS)

```powershell
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Azure AD PowerShell'de yeni kullanıcı hesapları oluşturma ve LicenseAssignment değerlerini bulma hakkında daha fazla bilgi için bkz. [PowerShell ile kullanıcı hesapları oluşturma](create-user-accounts-with-microsoft-365-powershell.md) ve [PowerShell ile lisansları ve hizmetleri görüntüleme](view-licenses-and-services-with-microsoft-365-powershell.md).

> [!NOTE]
> Bir posta kutusunu etkinleştirmek için Exchange Online PowerShell kullanıyorsanız ve posta kutusunun doğrudan **PreferredDataLocation** içinde belirtilen coğrafi konumda oluşturulması gerekiyorsa, doğrudan bulut hizmetinde **Enable-Mailbox veya New-Mailbox** gibi bir Exchange Online cmdlet'i kullanmanız gerekir. Şirket içi Exchange PowerShell'de **Enable-RemoteMailbox** cmdlet'ini kullanırsanız, posta kutusu merkezi coğrafi konumda oluşturulur.

## <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo-location"></a>Mevcut şirket içi posta kutularını belirli bir coğrafi konuma ekleme

[EAC'deki Geçiş panosu](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331) ve Exchange Online PowerShell'deki [New-MigrationBatch](/powershell/module/exchange/new-migrationbatch) cmdlet'i de dahil olmak üzere bir posta kutusunu şirket içi Exchange kuruluştan Exchange Online geçirmek için standart ekleme araçlarını ve işlemlerini kullanabilirsiniz.

İlk adım, eklenecek her posta kutusu için bir kullanıcı nesnesi olduğunu ve Azure AD doğru **PreferredDataLocation** değerinin yapılandırıldığını doğrulamaktır. Ekleme araçları **PreferredDataLocation** değerine saygı gösterir ve posta kutularını doğrudan belirtilen coğrafi konuma geçirir.

Alternatif olarak, Exchange Online PowerShell'de [New-MoveRequest](/powershell/module/exchange/new-moverequest) cmdlet'ini kullanarak posta kutularını doğrudan belirli bir coğrafi konuma eklemek için aşağıdaki adımları kullanabilirsiniz.

1. Eklenecek her posta kutusu için kullanıcı nesnesinin mevcut olduğunu ve **PreferredDataLocation** öğesinin Azure AD istenen değere ayarlandığını doğrulayın. **PreferredDataLocation** değeri, Exchange Online karşılık gelen posta kullanıcı nesnesinin **MailboxRegion** özniteliğiyle eşitlenir.

2. Bu konunun önceki bölümlerinde yer alan bağlantı yönergelerini kullanarak doğrudan belirli bir uydu coğrafi konumuna Bağlan.

3. Exchange Online PowerShell'de, aşağıdaki komutu çalıştırarak bir değişkende posta kutusu geçişi gerçekleştirmek için kullanılan şirket içi yönetici kimlik bilgilerini depolayın:

   ```powershell
   $RC = Get-Credential
   ```

4. Exchange Online PowerShell'de aşağıdaki örneğe benzer yeni bir **New-MoveRequest** oluşturun:

   ```powershell
   New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
   ```

5. Şirket içi Exchange şu anda bağlı olduğunuz uydu coğrafi konumuna geçirmeniz gereken her posta kutusu için 4. adımı yineleyin.

6. Başka posta kutularını farklı uydu coğrafi konumlarına geçirmeniz gerekiyorsa, her bir konum için 2 ile 4 arasındaki adımları yineleyin.

## <a name="multi-geo-reporting"></a>Çok coğrafi raporlama

> [!NOTE]
> Çoklu coğrafi raporlama özelliği şu anda Önizleme aşamasındadır, tüm kuruluşlarda kullanılamaz ve değiştirilebilir.

Microsoft 365 yönetim merkezi Çok **Coğrafi Kullanım Raporları**, coğrafi konuma göre kullanıcı sayısını görüntüler. Rapor geçerli ayın kullanıcı dağıtımını görüntüler ve son 6 aya ilişkin geçmiş verileri sağlar.

## <a name="see-also"></a>Ayrıca bkz.

[PowerShell ile Microsoft 365’i yönetme](manage-microsoft-365-with-microsoft-365-powershell.md)
