---
title: Müşteri Anahtarını Yönet
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Müşteri Anahtarını ayardikten sonra, AKV anahtarlarını geri yükleyerek ve izinleri yöneterek, veri şifreleme ilkeleri oluşturarak ve ataarak bunu yönetmeyi öğrenin.
ms.openlocfilehash: 9dd333064c9fa121f8f1c99ffcd048f6b977dbf2
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "62999052"
---
# <a name="manage-customer-key"></a>Müşteri Anahtarını Yönet

Müşteri Anahtarını Müşteri Anahtarı olarak Office 365 sonra, bir veya birden çok veri şifreleme ilkeleri (DEP) oluşturmanız ve atamaniz gerekir. DEP'lerinizi atadıktan sonra, anahtarlarınızı bu makalede açıklandığı gibi yönetabilirsiniz. Müşteri Anahtarı hakkında daha fazla bilgi edinmek için ilgili konulara bakın.

## <a name="create-a-dep-for-use-with-multiple-workloads-for-all-tenant-users"></a>Tüm kiracı kullanıcıları için birden çok iş yüküyle kullanmak üzere DEP oluşturma

Başlamadan önce Müşteri'nin ayarlaması için gereken görevleri tamamlamış olduğundan emin olmak. Bilgi için bkz [. Müşteri Anahtarını Ayarlama](customer-key-set-up.md). DEP'yi oluşturmak için, kurulum sırasında elde edilen Anahtar Kasa  URL'leri gerekir. Daha fazla bilgi için [bkz. Her bir Azure Anahtar Kasası anahtarı için URI alma](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).

Çok iş yüküne sahip bir DEP oluşturmak için şu adımları izleyin:
  
1. Yerel bilgisayarınızda, genel yönetici veya uyumluluk yöneticisi izinleri olan bir iş veya okul hesabı kullanarak, Windows PowerShell penceresinde [Exchange Online PowerShell'e](/powershell/exchange/connect-to-exchange-online-powershell) bağlanın.

2. DEP oluşturmak için, New-M365DataAtRestEncryptionPolicy kullanın.

   ```powershell
   New-M365DataAtRestEncryptionPolicy -Name <PolicyName> -AzureKeyIDs <KeyVaultURI1, KeyVaultURI2> [-Description <String>]
   ```

   Burada:

   - *PolicyName* , ilke için kullanmak istediğiniz addır. Adlar boşluk içeremez. Örneğin, Contoso_Global.

   - *KeyVaultURI1* , ilkenin ilk anahtarının URI'dir. Örneğin, <https://contosoWestUSvault1.vault.azure.net/keys/Key_01>.

   - *KeyVaultURI2* , ilkede ikinci anahtarın URI'dir. Örneğin, <https://contosoCentralUSvault1.vault.azure.net/keys/Key_02>. İki  URI'yı virgülle ve bir boşlukla birbirinden ayırma.

   - *İlke* Açıklaması, ilkenin ne için olduğunu anımsamanıza yardımcı olacak, ilkenin kullanıcı dostu bir açıklamasıdır. Açıklamaya boşluk  dahil edin. Örneğin, "Kiracıdaki tüm kullanıcılar için birden çok iş yükü için kök ilkesi."

Örneğin:

```powershell
New-M365DataAtRestEncryptionPolicy -Name "Contoso_Global" -AzureKeyIDs "https://contosoWestUSvault1.vault.azure.net/keys/Key_01","https://contosoCentralUSvault1.vault.azure.net/keys/Key_02" -Description "Policy for multiple workloads for all users in the tenant."
```

### <a name="assign-multi-workload-policy"></a>Çok iş yükü ilkesi atama

Set-M365DataAtRestEncryptionPolicyAssignment cmdlet'ini kullanarak DEP'yi attayin. İlkeyi atadığınız zaman, Microsoft 365 veriler DEP'de tanımlanan anahtarla şifrelenir.

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy <PolicyName or ID>
```

 Burada *PolicyName* , ilkenin adıdır. Örneğin, Contoso_Global.

Örneğin:

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy "Contoso_Global"
```

## <a name="create-a-dep-for-use-with-exchange-online-mailboxes"></a>Posta kutularıyla kullanmak üzere bir DEP Exchange Online oluşturma

Başlamadan önce, Azure Anahtar Kasasını ayarlamak için gereken görevleri tamamlamış olduğundan emin oluruz. Bilgi için bkz [. Müşteri Anahtarını Ayarlama](customer-key-set-up.md). Bu adımları, başka bir Exchange Online'a uzaktan bağlanarak Windows PowerShell.

DEP, Azure Anahtar Kasasında depolanan bir anahtar kümesiyle ilişkilendirildi. Microsoft 365'de bir posta kutusuna DEP Microsoft 365. Microsoft 365 posta kutusunu şifrelemek için ilkede tanımlanan anahtarları kullanır. DEP'yi oluşturmak için, kurulum sırasında elde edilen Anahtar Kasa  URL'leri gerekir. Daha fazla bilgi için [bkz. Her bir Azure Anahtar Kasası anahtarı için URI alma](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).

Unutmayın! DEP  oluşturmada, iki anahtarı iki farklı Azure Anahtar Kasasında belirtirsiniz. Coğrafi yedekli çalışma sağlamak için bu anahtarları iki ayrı Azure bölgesinde oluşturun.

Posta kutusuyla kullanmak üzere bir DEP oluşturmak için şu adımları izleyin:
  
1. Yerel bilgisayarınızda, genel yönetici ya da Exchange Online izinlerine sahip bir iş veya okul hesabı kullanarak, [Exchange Online PowerShell'e](/powershell/exchange/connect-to-exchange-online-powershell) Windows PowerShell bağlanın.

2. DEP oluşturmak için, New-DataEncryptionPolicy komutu yazarak cmdlet'i kullanın.

   ```powershell
   New-DataEncryptionPolicy -Name <PolicyName> -Description "Policy Description" -AzureKeyIDs <KeyVaultURI1>, <KeyVaultURI2>
   ```

   Burada:

   - *PolicyName* , ilke için kullanmak istediğiniz addır. Adlar boşluk içeremez. Örneğin, USA_mailboxes.

   - *İlke* Açıklaması, ilkenin ne için olduğunu anımsamanıza yardımcı olacak, ilkenin kullanıcı dostu bir açıklamasıdır. Açıklamaya boşluk  dahil edin. Örneğin, "ABD ve kendi sayfalarındaki posta kutuları için kök anahtar".

   - *KeyVaultURI1* , ilkenin ilk anahtarının URI'dir. Örneğin, <https://contoso_EastUSvault01.vault.azure.net/keys/USA_key_01>.

   - *KeyVaultURI2* , ilkede ikinci anahtarın URI'dir. Örneğin, <https://contoso_EastUS2vault01.vault.azure.net/keys/USA_Key_02>. İki  URI'yı virgülle ve bir boşlukla birbirinden ayırma.

   Örneğin:
  
   ```powershell
   New-DataEncryptionPolicy -Name USA_mailboxes -Description "Root key for mailboxes in USA and its territories" -AzureKeyIDs https://contoso_EastUSvault02.vault.azure.net/keys/USA_key_01, https://contoso_CentralUSvault02.vault.azure.net/keys/USA_Key_02
   ```

Ayrıntılı söz dizimi ve parametre bilgileri için [bkz. New-DataEncryptionPolicy](/powershell/module/exchange/new-data-encryptionpolicy).

### <a name="assign-a-dep-to-a-mailbox"></a>Posta kutusuna DEP atama

Set-Mailbox cmdlet'ini kullanarak DEP'i bir posta kutusuna attayabilirsiniz. İlkeyi atadığınız zaman, Microsoft 365 kutusunu DEP'de tanımlanan anahtarla şifreler.
  
```powershell
Set-Mailbox -Identity <MailboxIdParameter> -DataEncryptionPolicy <PolicyName>
```

*MailboxIdParameter bir* kullanıcı posta kutusunu belirtir. Bu cmdlet'i Set-Mailbox daha fazla bilgi için bkz. [Set-Mailbox](/powershell/module/exchange/set-mailbox).

Karma ortamlarda, kendi kiracınıza eşitlenen şirket içi posta kutusu verilerine DEP Exchange Online. Bu eşitlenmiş posta kutusu verilerine DEP atamak için, posta kutusu Set-MailUser kullanırsiniz. Karma ortamdaki posta kutusu verileri hakkında daha fazla bilgi için bkz. Karma Modern Kimlik Doğrulama ile [iOS ve Android için Outlook'i kullanan şirket içi posta kutuları](/exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth).

```powershell
Set-MailUser -Identity <MailUserIdParameter> -DataEncryptionPolicy <PolicyName>
```

Burada *MailUserIdParameter* bir posta kullanıcısı belirtir (posta etkin kullanıcı olarak da bilinir). Set-MailUser cmdlet'i hakkında daha fazla bilgi için bkz. [Set-MailUser](/powershell/module/exchange/set-mailuser).

## <a name="create-a-dep-for-use-with-sharepoint-online-onedrive-for-business-and-teams-files"></a>SharePoint Online, OneDrive İş ve Teams için DEP oluşturma

Başlamadan önce, Azure Anahtar Kasasını ayarlamak için gereken görevleri tamamlamış olduğundan emin oluruz. Bilgi için bkz [. Müşteri Anahtarını Ayarlama](customer-key-set-up.md).
  
SharePoint Online, OneDrive İş ve Teams dosyaları için Müşteri Anahtarını ayarlamak için, bu adımları SharePoint Online'a Windows PowerShell.
  
DEP'yi Azure Anahtar Kasasında depolanan bir dizi anahtarla ilişkilendirmeniz gerekir. Tek bir coğrafi konumdaki verilerinizin tamama (coğrafi olarak da denir) DEP'yi uygulayabilirsiniz. Office 365'ın multi-geo özelliğini kullanıyorsanız, her coğrafi bölge için farklı anahtarlar kullanma özelliğiyle geo başına bir DEP oluşturabilirsiniz. Multi-geo kullansanız bile, SharePoint Online, OneDrive İş ve Teams dosyalarıyla kullanmak için, Teams dep oluşturabilirsiniz. Microsoft 365 bu coğrafi bölgeye verilerinizi şifrelemek için DEP'de tanımlanan anahtarları kullanır. DEP'yi oluşturmak için, kurulum sırasında elde edilen Anahtar Kasa  URL'leri gerekir. Daha fazla bilgi için [bkz. Her bir Azure Anahtar Kasası anahtarı için URI alma](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).
  
Unutmayın! DEP  oluşturmada, iki anahtarı iki farklı Azure Anahtar Kasasında belirtirsiniz. Coğrafi yedekli çalışma sağlamak için bu anahtarları iki ayrı Azure bölgesinde oluşturun.
  
DEP oluşturmak için, SharePoint Online'ı kullanarak SharePoint Online'a uzaktan Windows PowerShell.
  
1. Yerel bilgisayarınızda, genel yönetici izinleri olan bir iş veya okul hesabı kullanarak Bağlan [Online PowerShell'SharePoint edin](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?preserve-view=true&view=sharepoint-ps).

2. Dış Microsoft Office SharePoint Online Kabuğu'Register-SPODataEncryptionPolicy aşağıdaki gibi bir cmdlet'i çalıştırın:

   ```powershell
   Register-SPODataEncryptionPolicy -PrimaryKeyVaultName <PrimaryKeyVaultName> -PrimaryKeyName <PrimaryKeyName> -PrimaryKeyVersion <PrimaryKeyVersion> -SecondaryKeyVaultName <SecondaryKeyVaultName> -SecondaryKeyName <SecondaryKeyName> -SecondaryKeyVersion <SecondaryKeyVersion>
   ```

   Örneğin:
  
   ```powershell
   Register-SPODataEncryptionPolicy -PrimaryKeyVaultName 'stageRG3vault' -PrimaryKeyName 'SPKey3' -PrimaryKeyVersion 'f635a23bd4a44b9996ff6aadd88d42ba' -SecondaryKeyVaultName 'stageRG5vault' -SecondaryKeyName 'SPKey5' -SecondaryKeyVersion '2b3e8f1d754f438dacdec1f0945f251a’
   ```

   DEP'yi kaydettir ilk olarak veriler coğrafi olarak şifrelenir. Şifreleme işlemi biraz zaman alabilirsiniz. Bu parametreyi kullanma hakkında daha fazla bilgi için bkz. [Register-SPODataEncryptionPolicy](/powershell/module/sharepoint-online/register-spodataencryptionpolicy?preserve-view=true&view=sharepoint-ps).

### <a name="view-the-deps-youve-created-for-exchange-online-mailboxes"></a>Posta kutuları için oluşturduğunuz DEP'leri Exchange Online görüntüleme

Posta kutuları için oluşturduğunuz tüm DEP'lerin listesini görüntülemek için, Get-DataEncryptionPolicy PowerShell cmdlet'ini kullanın.

1. Kuruluşta genel yönetici izinleri olan bir iş veya okul hesabı kullanarak, [Exchange Online PowerShell'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kuruluşta tüm DEP'leri geri dönmek için, Get-DataEncryptionPolicy parametresiz olarak cmdlet'i çalıştırın.

   ```powershell
   Get-DataEncryptionPolicy
   ```

   Bu cmdlet'i Get-DataEncryptionPolicy daha fazla bilgi için bkz. [Get-DataEncryptionPolicy](/powershell/module/exchange/get-dataencryptionpolicy).

### <a name="assign-a-dep-before-you-migrate-a-mailbox-to-the-cloud"></a>Posta kutusunu buluta geçirmeden önce DEP atama

DEP'yi atadığınız Microsoft 365, geçiş sırasında atanan DEP'yi kullanarak posta kutusunun içeriğini şifreler. Bu işlem, posta kutusunu hem de DEP'yi atamak ve şifrelemenin tamamlandır geceye kadar devam etmek için beklemesi saatler veya muhtemelen günler sürebilir, daha verimli bir işlemdir.

DEP'yi Office 365'a geçirmeden önce posta kutusuna atamak için, Exchange Online PowerShell'de Set-MailUser cmdlet'ini çalıştırın:

1. Kuruluşta genel yönetici izinleri olan bir iş veya okul hesabı kullanarak, [Exchange Online PowerShell'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

2. Set-MailUser cmdlet'ini çalıştırın.

   ```powershell
   Set-MailUser -Identity <GeneralMailboxOrMailUserIdParameter> -DataEncryptionPolicy <DataEncryptionPolicyIdParameter>
   ```

   Burada *GeneralMailboxOrMailUserIdParameter* bir posta kutusunu belirtir ve *DataEncryptionPolicyIdParameter* de DEP'nin kimliğidir. Set-MailUser cmdlet'i hakkında daha fazla bilgi için bkz. [Set-MailUser](/powershell/module/exchange/set-mailuser).

### <a name="determine-the-dep-assigned-to-a-mailbox"></a>Posta kutusuna atanan DEP'yi belirleme

Posta kutusuna atanmış DEP'yi belirlemek için, Get-MailboxStatistics kullanın. Cmdlet, benzersiz bir tanımlayıcı (GUID) döndürür.
  
1. Kuruluşta genel yönetici izinleri olan bir iş veya okul hesabı kullanarak, [Exchange Online PowerShell'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

   ```powershell
   Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl DataEncryptionPolicyID
   ```

   *GeneralMailboxOrMailUserIdParameter* bir posta kutusu belirtir ve DataEncryptionPolicyID de DEP'nin GUID'sine değer verir. [Get-MailboxStatistics Get-MailboxStatistics daha fazla bilgi için](/powershell/module/exchange/get-mailboxstatistics) bkz.
  
2. Posta Get-DataEncryptionPolicy da atanmış olan DEP'nin kolay adını bulmak için Get-DataEncryptionPolicy cmdlet'ini çalıştırın.
  
   ```powershell
   Get-DataEncryptionPolicy <GUID>
   ```

   Burada *GUID* , önceki adımda Get-MailboxStatistics tarafından döndürülen GUID'dir.

## <a name="verify-that-customer-key-has-finished-encryption"></a>Müşteri Anahtarının şifrelemeyi tamamla olduğunu doğrulama

Bir Müşteri Anahtarı yuvarlamış, yeni bir DEP atamış veya posta kutusunu geçirmış olun, şifrelemenin tamamlandıktan emin olmak için bu bölümdeki adımları kullanın.

### <a name="verify-encryption-completes-for-exchange-online-mailboxes"></a>Posta kutuları için şifreleme Exchange Online doğrulama

Posta kutusunun şifrelenmesi biraz zaman alır. İlk kez şifreleme için, hizmetin posta kutusunu şifreleyemediklerinden önce posta kutusunun bir veritabanından diğerine tamamen taşıması gerekir.
  
Posta kutusunun Get-MailboxStatistics şifrelenmediğini belirlemek için Get-MailboxStatistics cmdlet'ini kullanın.
  
```powershell
Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl IsEncrypted
```

IsEncrypted özelliği, posta kutusu şifrelenirse **true** değerini ve posta kutusu şifrelenmiş değilse **false** değerini döndürür. Posta kutusu hareketlerinin tamamlanması için gereken süre, ilk kez DEP atamanız gereken posta kutularının sayısına ve posta kutularının boyutuna bağlıdır. DEP'yi atamış olduğunuz zamandan bir hafta sonra posta kutuları şifrelenmezse, Microsoft'a ulaşın.

Yeni New-MoveRequest cmdlet'i artık yerel posta kutusu hareketlerinde kullanılamaz. Ek bilgi [için bu duyuruya](https://techcommunity.microsoft.com/t5/exchange-team-blog/disabling-new-moverequest-for-local-mailbox-moves/bc-p/1332141) bakın.

### <a name="verify-encryption-completes-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>SharePoint Online, OneDrive İş dosyalarınız için Teams doğrulama

Get-SPODataEncryptionPolicy cmdlet'ini çalıştırarak şifrelemenin durumunu kontrol edin:

```PowerShell
   Get-SPODataEncryptionPolicy <SPOAdminSiteUrl>
```

Bu cmdlet'in çıkışı şunları içerir:
  
- Birincil anahtarın URI'si.

- İkincil anahtarın URI'si.

- Coğrafi şifreleme durumu. Olası eyaletler şunlardır:

  - **Kaydı alındı:** Müşteri Anahtarı şifrelemesi henüz uygulanmamıştır.

  - **Kaydeden:** Müşteri Anahtarı şifrelemesi uygulandı ve dosyalarınız şifrelenme sürecinde. Coğrafi konumun anahtarı kaydediyorsa, şifreleme ilerleme durumunu izlemek için coğrafi coğrafi sitelerden yüzde kaçlarının tamamlanmıştır konusunda da bilgi gösterilir.

  - **Kayıtlı:** Müşteri Anahtarı şifrelemesi uygulanır ve tüm sitelerde yer alan tüm dosyalar şifrelenir.

  - **Yuvarlanıyor:** Bir temel alma ilerlemesi devam ediyor. Coğrafi konumun anahtarı geliyorsa, ilerleme durumunu izlemek için sitelerin yüzdesinde anahtar alma işlemi tamamlandıktan sonra size bilgi de gösterilir.

- Ayrıca, alınan sitelerin yüzdesini de çıkışı olur.

## <a name="get-details-about-deps-you-use-with-multiple-workloads"></a>Birden çok iş yüküyle birlikte kullanmakta olduğunuz DEP'ler hakkında ayrıntılı bilgi

Birden çok iş yüküyle kullanmak üzere oluşturduğunuz tüm DEP'ler hakkında ayrıntılı bilgi almak için şu adımları tamamlayın:

1. Yerel bilgisayarınızda, genel yönetici veya uyumluluk yöneticisi izinleri olan bir iş veya okul hesabı kullanarak, Windows PowerShell penceresinde [Exchange Online PowerShell'e](/powershell/exchange/connect-to-exchange-online-powershell) bağlanın.

   - Kuruluşta tüm çok iş yükü DEP'lerinin listesini geri dönmek için, bu komutu çalıştırın.

     ```powershell
        Get-M365DataAtRestEncryptionPolicy
     ```

   - Belirli bir DEP hakkında ayrıntılı bilgi dönmek için bu komutu çalıştırın. Bu örnekte, "Özel" adlı DEP için ayrıntılı Contoso_Global döndürür.

     ```powershell
        Get-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global"
     ```

## <a name="get-multi-workload-dep-assignment-information"></a>Çok iş yüküne sahip DEP atama bilgilerini al

Kiracınıza şu anda hangi DEP'nin atandığı hakkında daha fazla yardım için bu adımları izleyin. 

1. Yerel bilgisayarınızda, genel yönetici veya uyumluluk yöneticisi izinleri olan bir iş veya okul hesabı kullanarak, Windows PowerShell penceresinde [Exchange Online PowerShell'e](/powershell/exchange/connect-to-exchange-online-powershell) bağlanın.

2. Bu komutu yazın.

   ```powershell
      Get-M365DataAtRestEncryptionPolicyAssignment
   ```

## <a name="disable-a-multi-workload-dep"></a>Çok iş yüküne sahip DEP'yi devre dışı bırakma

Çok iş yüküne sahip bir DEP'yi devre dışı bırakmadan önce kiracıdaki iş yüklerinden DEP'in atamasını devre dışı bırakmanız gerekir. Birden çok iş yüküyle birlikte kullanılan bir DEP'yi devre dışı bırakmak için şu adımları tamamlayın:

1. Yerel bilgisayarınızda, genel yönetici veya uyumluluk yöneticisi izinleri olan bir iş veya okul hesabı kullanarak, Windows PowerShell penceresinde [Exchange Online PowerShell'e](/powershell/exchange/connect-to-exchange-online-powershell) bağlanın.

2. Set-M365DataAtRestEncryptionPolicy cmdlet'ini çalıştırın.
  
   ```powershell
   Set-M365DataAtRestEncryptionPolicy -[Identity] "PolicyName" -Enabled $false
   ```

Burada *PolicyName* , ilkenin adı veya benzersiz kimliğidir. Örneğin, Contoso_Global.

Örneğin:

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global" -Enabled $false
```

## <a name="restore-azure-key-vault-keys"></a>Azure Anahtar Kasası anahtarlarını geri yükleme

Bir geri yükleme gerçekleştirmeden önce, yazılım tarafından sağlanan kurtarma özelliklerini kullanın. Müşteri Anahtarı ile kullanılan tüm anahtarların, yumuşak silmenin etkinleştirilmesi gerekir. Yumuşak silme, geri dönüşüm kutusu gibi davranır ve geri yüklemek zorunda kalmadan 90 gün boyunca kurtarmayı sağlar. Geri yükleme, örneğin anahtar veya anahtar kasası kaybolursa yalnızca aşırı veya alışılmadık durumlarda gerekli olabilir. Müşteri Anahtarı ile kullanmak için anahtarı geri yüklemek Azure PowerShell, Azure PowerShell cmdlet'ini aşağıdaki Restore-AzureKeyVaultKey çalıştırın:
  
```powershell
Restore-AzKeyVaultKey -VaultName <vault name> -InputFile <filename>
```

Örneğin:
  
```powershell
Restore-AzKeyVaultKey -VaultName Contoso-O365EX-NA-VaultA1 -InputFile Contoso-O365EX-NA-VaultA1-Key001-Backup-20170802.backup
```

Anahtar kasası zaten aynı adı içeren bir anahtar içeriyorsa, geri yükleme işlemi başarısız olur. Restore-AzKeyVaultKey, anahtar adı da içinde olmak üzere anahtarın tüm önemli sürümlerini ve tüm meta verilerini geri yükleyebilir.
  
## <a name="manage-key-vault-permissions"></a>Anahtar kasası izinlerini yönetme

Bunları görüntülemeniz ve gerekirse anahtar kasası izinlerini kaldırmanız için çeşitli cmdlet'ler kullanılabilir. Örneğin, bir çalışan ekiptan ayrıldığında izinleri kaldırmanız gerekiyor olabilir. Bu görevlerin her biri için görev atama Azure PowerShell. Daha fazla bilgi Azure PowerShell bkz. Genel [bakış Azure PowerShell](/powershell/azure/).

Anahtar kasası izinlerini görüntülemek için, Get-AzKeyVault çalıştırın.

```powershell
Get-AzKeyVault -VaultName <vault name>
```

Örneğin:

```powershell
Get-AzKeyVault -VaultName Contoso-O365EX-NA-VaultA1
```

Yöneticinin izinlerini kaldırmak için, şu cmdletRemove-AzKeyVaultAccessPolicy çalıştırın:
  
```powershell
Remove-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user>
```

Örneğin:

```powershell
Remove-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 -UserPrincipalName alice@contoso.com
```

## <a name="roll-back-from-customer-key-to-microsoft-managed-keys"></a>Müşteri Anahtarı'dan Microsoft tarafından yönetilen Anahtarlara geri dönme

Microsoft tarafından yönetilen tuşlara geri dönmenizi gerekirse, bunu kullanabilirsiniz. Çıkarsanız, her bir iş yükünün desteklenen varsayılan şifrelemesi kullanılarak verileriniz yeniden şifrelenir. Örneğin, Exchange Online Microsoft tarafından yönetilen anahtarlar kullanılarak varsayılan şifrelemeyi destekler.

> [!IMPORTANT]
> Çıkararak çalışma, veri temizlemeyle aynı değildir. Veriler kalıcı olarak şifreleme ile silinir ve kuruluş verilerini kuruluştan Microsoft 365, çıkarama tarafından silinir. Birden çok iş yükü ilkesi için veri temizleme işlemi gerçekleştirebilirsiniz.

Artık çok iş yüküne sahip DEP'leri atamak için Müşteri Anahtarını kullanmama kararı aldıysanız, Müşteri Anahtarı'nın "çıkar" isteğiyle Microsoft desteğine ulaşman gerekir. Destek ekibiden, Müşteri Anahtarı ekibine karşı bir Microsoft 365 isteği sormalarını iste. Sorularınız varsa m365-ck@service.microsoft.com ulaşarak erişin.

Artık posta kutusu düzeyi DEP'leri kullanarak tek tek posta kutularını şifrelemek istemiyorsanız, tüm posta kutularınıza posta kutusu düzeyindeKIPP'lerin atamalarını geri sebilirsiniz.

Posta kutusu DEP'lerini atamalarını geri Set-Mailbox PowerShell cmdlet'ini kullanın.

1. Kuruluşta genel yönetici izinleri olan bir iş veya okul hesabı kullanarak, [Exchange Online PowerShell'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

2. Set-Mailbox cmdlet'ini çalıştırın.

   ```powershell
   Set-Mailbox -Identity <mailbox> -DataEncryptionPolicy $NULL
   ```

Bu cmdlet'i çalıştırarak, şu anda atanmış olan DEP atamalarını devre dışı bırakın ve varsayılan Microsoft tarafından yönetilen anahtarlarla ilişkilendirilmiş DEP'yi kullanarak posta kutusunu yeniden şifreler. Microsoft tarafından kullanılan DEP'nin atamasını alıyayaaz. Microsoft tarafından yönetilen anahtarlar kullanmak istemiyorsanız, posta kutusuna başka bir Müşteri Anahtarı DEP'i atabilirsiniz.

## <a name="revoke-your-keys-and-start-the-data-purge-path-process"></a>Anahtarlarınızı iptal etme ve veri temizleme yol işlemini başlatma

Kullanılabilirlik anahtarı da içinde olmak üzere tüm kök anahtarların iptali sizin denetimindedir. Müşteri Anahtarı, mevzuat gereksinimlerinin sizin için çıkış planlaması yönünün kontrolünü sağlar. Verilerinizi temizleme ve hizmetten çıkma anahtarlarınızı iptal etmek için karar verirsiniz, veri temizleme işlemi tamamlandıktan sonra hizmet kullanılabilirlik anahtarını siler. Bu, tek tek posta kutularına atanan Müşteri Anahtarı DEP'leri için de destekler.

Microsoft 365 denetlemelerini sağlar ve veri temizleme yolunu doğrular. Daha fazla bilgi için Hizmet Güveni Portalı'nde bulunan SSAE 18 SOC 2 [Raporu'ne bakın](https://servicetrust.microsoft.com/). Microsoft ayrıca aşağıdaki belgeleri de önermektedir:

- [Microsoft Bulut'ta Finansal Kurumlar için Risk Değerlendirmesi ve Uyumluluk Kılavuzu](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=edee9b14-3661-4a16-ba83-c35caf672bd7&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

- [O365 Çıkış Planlamada Dikkate Alınacak Noktalar](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=77ea7ebf-ce1b-4a5f-9972-d2d81a951d99&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

Çok iş yüküne sahip DEP'nin müşteri anahtarını temizlemek Microsoft 365 değildir. Çok iş yüküne sahip DEP, tüm kiracı kullanıcıları genelinde birden çok iş yükü genelinde verileri şifrelemek için kullanılır. Bu tür DEP'in temiz olması, birden çok iş yükünün karşıdan yüklerinden verinin erişilamamesine neden olabilir. Hizmetlerden tamamen çıkmak Microsoft 365 bu durumda belgelenmiş işlem başına kiracı silme yolunu takip etmek zorunda da olabilirsiniz. [Kiracıyı silmek için bkz. Azure Active Directory](/azure/active-directory/enterprise-users/directory-delete-howto).

### <a name="revoke-your-customer-keys-and-the-availability-key-for-exchange-online-and-skype-for-business"></a>Müşteri Anahtarlarınızı ve siparişler ve hizmetlerin kullanılabilirlik Exchange Online iptal Skype Kurumsal

VERI temizleme yolu ilk olarak SIZIN için Exchange Online Skype Kurumsal deP'de kalıcı bir veri temizleme isteği ayarlamaz. Bunu yapmak, bu DEP'nin atandığı posta kutuları içindeki şifrelenmiş verileri kalıcı olarak siler.

PowerShell cmdlet'ini aynı anda tek bir DEP'de çalıştırabilirsiniz, çünkü veri temizleme yolunu başlatmadan önce tek bir DEP'yi tüm posta kutularınıza yeniden atamanız iyi olabilir.

> [!WARNING]
> Posta kutularınızı bir alt kümesini silmek için veri temizleme yolunu kullanmayın. Bu işlem yalnızca hizmettan çıkış yapan müşterilere yöneliktir.

Veri temizleme yolunu başlatmak için şu adımları tamamlayın:

1. Azure Anahtar Kasalarından "O365 Exchange Online" kaydırma izinlerini kaldırın.

2. Genel yönetici ayrıcalıklarına sahip bir iş veya okul hesabını kullanarak, [Exchange Online PowerShell'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

3. Silmek istediğiniz posta kutularını içeren her DEP için [Set-DataEncryptionPolicy](/powershell/module/exchange/set-dataencryptionpolicy) cmdlet'ini aşağıdaki gibi çalıştırın.

    ```powershell
    Set-DataEncryptionPolicy <Policy ID> -PermanentDataPurgeRequested -PermanentDataPurgeReason <Reason> -PermanentDataPurgeContact <ContactName>
    ```

   Komut başarısız olursa, bu görevin başlarında belirtildiği gibi Azure Exchange Online Kasa'daki her iki tuştan da izin izinlerini kaldırmış olun.Set-DataEncryptionPolicy cmdlet'ini kullanarak PermanentDataPurgeRequested anahtarını ayarsanız, artık bu DEP'i posta kutularına atayamazsiniz.

4. Microsoft desteğine başvurun ve Veri Temizleme eDocument'ı talep et.

    İsteğiniz üzerine, Microsoft size veri silme işlemini onaylamanız ve yetkilendirmeniz için bir yasal belge gönderir. Ekleme sırasındaki teklifte yer alan ve sizin FastTrack için onaylayan kişinin bu belgeyi imzalaması gerekir. Normalde, bu şirketi şirketiniz içinde bulunan ve yasal olarak kuruluşun adına evrak işlerini imzalama yetkisi olan bir üst düzey yönetici veya başka bir kişidir.

5. Temsilciniz yasal belgeyi imzalarken, bunu Microsoft'a iade (genellikle eDoc imzası yoluyla).

    Microsoft yasal belgeyi aldığında, Microsoft önce ilkeyi silen, posta kutularını kalıcı olarak silme için işaretleyen ve ardından kullanılabilirlik anahtarını silen veri temizleme cmdlet'lerini çalıştırır. Veri temizleme işlemi tamamlandıktan sonra veriler temiz olur, bu veriler Exchange Online erişilebilir değildir ve kurtarılamaz.

### <a name="revoke-your-customer-keys-and-the-availability-key-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>SharePoint Online, OneDrive İş ve Teams dosyalarınız için Müşteri Anahtarları'Teams iptal etme

SharePoint Online, OneDrive İş ve Teams için veri temizleme yolunu başlatmak için şu adımları tamamlayın:

1. Azure Anahtar Kasası erişimini iptal edin. Tüm anahtar kasa yöneticilerinin erişimi iptal etmelerini kabul etmeleri gerekir.

   SharePoint Online için Azure Anahtar Kasasını silemezsiniz. Anahtar kasalar, birkaç SharePoint Online kiracısı ve DEP'leri arasında paylaşılıyor olabilir.

2. Kullanılabilirlik anahtarını silmek için Microsoft'a ulaşın.

    Uygunluk anahtarını silmek için Microsoft'a başvurarak size bir yasal belge göndeririz. Ekleme sırasındaki teklifte yer alan ve sizin FastTrack için onaylayan kişinin bu belgeyi imzalaması gerekir. Normalde, şirketiniz içinde bulunan ve yasal olarak evrak işlerini sizin organizasyonunuz adına imzalamak için yetkili olan bir yönetici veya başka bir kişidir.

3. Temsilciniz yasal belgeyi imzalarken, bunu Microsoft'a iade (genellikle eDoc imzası yoluyla).

   Microsoft yasal belgeyi aldığında, kiracı anahtarının, site anahtarının ve her belge için tek tek tüm anahtarların şifre ile silinmesini gerçekleştiren veri temizleme işlemini tetikleyen cmdlet'leri çalıştırarak anahtar hiyerarşisini geri alamaz şekilde kırılır. Veri temizleme cmdlet'leri tamamlandıktan sonra verileriniz temizlanır.

## <a name="related-articles"></a>İlgili makaleler

- [Müşteri Anahtarı ile Hizmet şifrelemesi](customer-key-overview.md)

- [Kullanılabilirlik anahtarı hakkında bilgi](customer-key-availability-key-understand.md)

- [Müşteri Anahtarını Ayarlama](customer-key-set-up.md)

- [Müşteri Anahtarını veya uygunluk anahtarını döndürme veya döndürme](customer-key-availability-key-roll.md)

- [Müşteri Kasası](customer-lockbox-requests.md)

- [Hizmet Şifrelemesi](office-365-service-encryption.md)
