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
description: Müşteri Anahtarı'nı ayarladıktan sonra, AKV anahtarlarını geri yükleyerek ve izinleri yöneterek ve veri şifreleme ilkeleri oluşturup atayarak anahtarı yönetmeyi öğrenin.
ms.openlocfilehash: 0ca6aa1e2cf725359d74477b486a4763a35ba681
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65465920"
---
# <a name="manage-customer-key"></a>Müşteri Anahtarını Yönet

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Müşteri Anahtarını ayarladıktan sonra bir veya daha fazla veri şifreleme ilkesi (DEP) oluşturup atamanız gerekir. DEP'lerinizi atadıktan sonra anahtarlarınızı bu makalede açıklandığı gibi yönetebilirsiniz. İlgili konularda Müşteri Anahtarı hakkında daha fazla bilgi edinin.

## <a name="create-a-dep-for-use-with-multiple-workloads-for-all-tenant-users"></a>Tüm kiracı kullanıcıları için birden çok iş yüküyle kullanmak üzere bir DEP oluşturma

Başlamadan önce Müşteri Anahtarını ayarlamak için gereken görevleri tamamladığınızdan emin olun. Bilgi için bkz. [Müşteri Anahtarını Ayarlama](customer-key-set-up.md). DEP'yi oluşturmak için kurulum sırasında aldığınız Key Vault URI'lere ihtiyacınız vardır. Bilgi için bkz. [Her Azure Key Vault anahtarı için URI'yi alma](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).

Çok iş yüküne sahip bir DEP oluşturmak için şu adımları izleyin:
  
1. Yerel bilgisayarınızda, kuruluşunuzda genel yönetici veya uyumluluk yöneticisi izinlerine sahip bir iş veya okul hesabı kullanarak [Windows PowerShell penceresinde Exchange Online PowerShell'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

2. DEP oluşturmak için New-M365DataAtRestEncryptionPolicy cmdlet'ini kullanın.

   ```powershell
   New-M365DataAtRestEncryptionPolicy -Name <PolicyName> -AzureKeyIDs <KeyVaultURI1, KeyVaultURI2> [-Description <String>]
   ```

   Konum:

   - *İlkeAdı* , ilke için kullanmak istediğiniz addır. Adlar boşluk içeremez. Örneğin, Contoso_Global.

   - *KeyVaultURI1* , ilkedeki ilk anahtarın URI'sini oluşturur. Örneğin, <https://contosoWestUSvault1.vault.azure.net/keys/Key_01>.

   - *KeyVaultURI2* , ilkedeki ikinci anahtarın URI'sini oluşturur. Örneğin, <https://contosoCentralUSvault1.vault.azure.net/keys/Key_02>. İki URI'yi virgül ve boşlukla ayırın.

   - *İlke Açıklaması* , ilkenin ne için olduğunu hatırlamanıza yardımcı olacak kullanıcı dostu bir açıklamadır. Açıklamaya boşluk ekleyebilirsiniz. Örneğin, "Kiracıdaki tüm kullanıcılar için birden çok iş yükü için kök ilke."

Örneğin:

```powershell
New-M365DataAtRestEncryptionPolicy -Name "Contoso_Global" -AzureKeyIDs "https://contosoWestUSvault1.vault.azure.net/keys/Key_01","https://contosoCentralUSvault1.vault.azure.net/keys/Key_02" -Description "Policy for multiple workloads for all users in the tenant."
```

### <a name="assign-multi-workload-policy"></a>Çok iş yükü ilkesi atama

Set-M365DataAtRestEncryptionPolicyAssignment cmdlet'ini kullanarak DEP'yi atayın. İlkeyi atadıktan sonra Microsoft 365 verileri DEP'te tanımlanan anahtarla şifreler.

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy <PolicyName or ID>
```

 Burada *policyName* , ilkenin adıdır. Örneğin, Contoso_Global.

Örneğin:

```powershell
Set-M365DataAtRestEncryptionPolicyAssignment -DataEncryptionPolicy "Contoso_Global"
```

## <a name="create-a-dep-for-use-with-exchange-online-mailboxes"></a>Exchange Online posta kutularıyla kullanmak için DEP oluşturma

Başlamadan önce Azure Key Vault ayarlamak için gereken görevleri tamamladığınızdan emin olun. Bilgi için bkz. [Müşteri Anahtarını Ayarlama](customer-key-set-up.md). Windows PowerShell ile Exchange Online uzaktan bağlanarak bu adımları tamamlayacaksınız.

DEP, Azure Key Vault'de depolanan bir dizi anahtarla ilişkilendirilir. Microsoft 365 bir posta kutusuna DEP atarsınız. Microsoft 365 daha sonra posta kutusunu şifrelemek için ilkede tanımlanan anahtarları kullanır. DEP'yi oluşturmak için kurulum sırasında aldığınız Key Vault URI'lere ihtiyacınız vardır. Bilgi için bkz. [Her Azure Key Vault anahtarı için URI'yi alma](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).

Hatırla! DEP oluşturduğunuzda iki farklı Azure Key Vault'ta iki anahtar belirtirsiniz. Coğrafi olarak yedeklilik sağlamak için bu anahtarları iki ayrı Azure bölgesinde oluşturun.

Posta kutusuyla kullanılacak bir DEP oluşturmak için şu adımları izleyin:
  
1. Yerel bilgisayarınızda, kuruluşunuzda genel yönetici veya Exchange Online yönetici izinlerine sahip bir iş veya okul hesabı kullanarak Windows PowerShell penceresinde [Exchange Online PowerShell'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

2. DEP oluşturmak için aşağıdaki komutu yazarak New-DataEncryptionPolicy cmdlet'ini kullanın.

   ```powershell
   New-DataEncryptionPolicy -Name <PolicyName> -Description "Policy Description" -AzureKeyIDs <KeyVaultURI1>, <KeyVaultURI2>
   ```

   Konum:

   - *İlkeAdı* , ilke için kullanmak istediğiniz addır. Adlar boşluk içeremez. Örneğin, USA_mailboxes.

   - *İlke Açıklaması* , ilkenin ne için olduğunu hatırlamanıza yardımcı olacak kullanıcı dostu bir açıklamadır. Açıklamaya boşluk ekleyebilirsiniz. Örneğin, "ABD'deki posta kutuları ve bölgeleri için kök anahtar".

   - *KeyVaultURI1* , ilkedeki ilk anahtarın URI'sini oluşturur. Örneğin, <https://contoso_EastUSvault01.vault.azure.net/keys/USA_key_01>.

   - *KeyVaultURI2* , ilkedeki ikinci anahtarın URI'sini oluşturur. Örneğin, <https://contoso_EastUS2vault01.vault.azure.net/keys/USA_Key_02>. İki URI'yi virgül ve boşlukla ayırın.

   Örneğin:
  
   ```powershell
   New-DataEncryptionPolicy -Name USA_mailboxes -Description "Root key for mailboxes in USA and its territories" -AzureKeyIDs https://contoso_EastUSvault02.vault.azure.net/keys/USA_key_01, https://contoso_CentralUSvault02.vault.azure.net/keys/USA_Key_02
   ```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-DataEncryptionPolicy](/powershell/module/exchange/new-data-encryptionpolicy).

### <a name="assign-a-dep-to-a-mailbox"></a>Posta kutusuna DEP atama

Set-Mailbox cmdlet'ini kullanarak DEP'yi bir posta kutusuna atayın. İlkeyi atadıktan sonra, Microsoft 365 posta kutusunu DEP'te tanımlanan anahtarla şifreleyebilir.
  
```powershell
Set-Mailbox -Identity <MailboxIdParameter> -DataEncryptionPolicy <PolicyName>
```

Burada *MailboxIdParameter* bir kullanıcı posta kutusu belirtir. Set-Mailbox cmdlet'i hakkında daha fazla bilgi için bkz. [Set-Mailbox](/powershell/module/exchange/set-mailbox).

Karma ortamlarda, Exchange Online kiracınızla eşitlenen şirket içi posta kutusu verilerine bir DEP atayabilirsiniz. Bu eşitlenmiş posta kutusu verilerine bir DEP atamak için Set-MailUser cmdlet'ini kullanacaksınız. Karma ortamdaki posta kutusu verileri hakkında daha fazla bilgi için bkz. karma [Modern Kimlik Doğrulaması ile iOS ve Android için Outlook kullanan şirket içi posta kutuları](/exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth).

```powershell
Set-MailUser -Identity <MailUserIdParameter> -DataEncryptionPolicy <PolicyName>
```

Burada *MailUserIdParameter* bir posta kullanıcı (posta etkin kullanıcı olarak da bilinir) belirtir. Set-MailUser cmdlet'i hakkında daha fazla bilgi için bkz [. Set-MailUser](/powershell/module/exchange/set-mailuser).

## <a name="create-a-dep-for-use-with-sharepoint-online-onedrive-for-business-and-teams-files"></a>SharePoint Online, OneDrive İş ve Teams dosyalarıyla kullanmak üzere bir DEP oluşturma

Başlamadan önce Azure Key Vault ayarlamak için gereken görevleri tamamladığınızdan emin olun. Bilgi için bkz. [Müşteri Anahtarını Ayarlama](customer-key-set-up.md).
  
SharePoint Online, OneDrive İş ve Teams dosyaları için Müşteri Anahtarını ayarlamak için Windows PowerShell ile SharePoint Online'a uzaktan bağlanarak bu adımları tamamlarsınız.
  
DeP'i Azure Key Vault'da depolanan bir dizi anahtarla ilişkilendirirsiniz. Tüm verilerinize coğrafi olarak da adlandırılan tek bir coğrafi konumda bir DEP uygularsınız. Office 365 çok coğrafi özelliğini kullanıyorsanız, coğrafi olarak farklı anahtarlar kullanma özelliğine sahip coğrafi bölge başına bir DEP oluşturabilirsiniz. Çok coğrafi bölge kullanmıyorsanız, kuruluşunuzda SharePoint Online, OneDrive İş ve Teams dosyalarıyla kullanmak üzere bir DEP oluşturabilirsiniz. Microsoft 365, bu coğrafi bölgede verilerinizi şifrelemek için DEP'de tanımlanan anahtarları kullanır. DEP'yi oluşturmak için kurulum sırasında aldığınız Key Vault URI'lere ihtiyacınız vardır. Bilgi için bkz. [Her Azure Key Vault anahtarı için URI'yi alma](customer-key-set-up.md#obtain-the-uri-for-each-azure-key-vault-key).
  
Hatırla! DEP oluşturduğunuzda iki farklı Azure Key Vault'ta iki anahtar belirtirsiniz. Coğrafi olarak yedeklilik sağlamak için bu anahtarları iki ayrı Azure bölgesinde oluşturun.
  
DEP oluşturmak için Windows PowerShell kullanarak SharePoint Online'a uzaktan bağlanmanız gerekir.
  
1. Yerel bilgisayarınızda, kuruluşunuzda genel yönetici izinlerine sahip bir iş veya okul hesabı kullanarak [Çevrimiçi PowerShell'i SharePoint Bağlan](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?preserve-view=true&view=sharepoint-ps).

2. Microsoft Office SharePoint Online Yönetim Kabuğu'nda Register-SPODataEncryptionPolicy cmdlet'ini aşağıdaki gibi çalıştırın:

   ```powershell
   Register-SPODataEncryptionPolicy -PrimaryKeyVaultName <PrimaryKeyVaultName> -PrimaryKeyName <PrimaryKeyName> -PrimaryKeyVersion <PrimaryKeyVersion> -SecondaryKeyVaultName <SecondaryKeyVaultName> -SecondaryKeyName <SecondaryKeyName> -SecondaryKeyVersion <SecondaryKeyVersion>
   ```

   Örneğin:
  
   ```powershell
   Register-SPODataEncryptionPolicy -PrimaryKeyVaultName 'stageRG3vault' -PrimaryKeyName 'SPKey3' -PrimaryKeyVersion 'f635a23bd4a44b9996ff6aadd88d42ba' -SecondaryKeyVaultName 'stageRG5vault' -SecondaryKeyName 'SPKey5' -SecondaryKeyVersion '2b3e8f1d754f438dacdec1f0945f251a'
   ```

   DEP'yi kaydettiğinizde şifreleme coğrafi verilerde başlar. Şifreleme biraz zaman alabilir. Bu parametreyi kullanma hakkında daha fazla bilgi için bkz [. Register-SPODataEncryptionPolicy](/powershell/module/sharepoint-online/register-spodataencryptionpolicy?preserve-view=true&view=sharepoint-ps).

### <a name="view-the-deps-youve-created-for-exchange-online-mailboxes"></a>Exchange Online posta kutuları için oluşturduğunuz DEP'leri görüntüleme

Posta kutuları için oluşturduğunuz tüm DEP'lerin listesini görüntülemek için Get-DataEncryptionPolicy PowerShell cmdlet'ini kullanın.

1. Kuruluşunuzda genel yönetici izinlerine sahip bir iş veya okul hesabı kullanarak [Exchange Online PowerShell'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kuruluşunuzdaki tüm DEP'leri döndürmek için Get-DataEncryptionPolicy cmdlet'ini parametre olmadan çalıştırın.

   ```powershell
   Get-DataEncryptionPolicy
   ```

   Get-DataEncryptionPolicy cmdlet'i hakkında daha fazla bilgi için bkz. [Get-DataEncryptionPolicy](/powershell/module/exchange/get-dataencryptionpolicy).

### <a name="assign-a-dep-before-you-migrate-a-mailbox-to-the-cloud"></a>Posta kutusunu buluta geçirmeden önce DEP atama

DEP'yi atadığınızda, Microsoft 365 geçiş sırasında atanan DEP'yi kullanarak posta kutusunun içeriğini şifreler. Bu işlem, posta kutusunu geçirmekten, DEP'yi atamaktan ve ardından şifrelemenin gerçekleşmesini beklemekten daha verimlidir ve bu işlem saatler veya muhtemelen günler sürebilir.

Office 365 geçirmeden önce posta kutusuna DEP atamak için Set-MailUser cmdlet'ini Exchange Online PowerShell'de çalıştırın:

1. Kuruluşunuzda genel yönetici izinlerine sahip bir iş veya okul hesabı kullanarak [Exchange Online PowerShell'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

2. Set-MailUser cmdlet'ini çalıştırın.

   ```powershell
   Set-MailUser -Identity <GeneralMailboxOrMailUserIdParameter> -DataEncryptionPolicy <DataEncryptionPolicyIdParameter>
   ```

   *Burada GeneralMailboxOrMailUserIdParameter* bir posta kutusu belirtir ve *DataEncryptionPolicyIdParameter* deP'nin kimliğidir. Set-MailUser cmdlet'i hakkında daha fazla bilgi için bkz [. Set-MailUser](/powershell/module/exchange/set-mailuser).

### <a name="determine-the-dep-assigned-to-a-mailbox"></a>Posta kutusuna atanan DEP'yi belirleme

Bir posta kutusuna atanan DEP'yi belirlemek için Get-MailboxStatistics cmdlet'ini kullanın. Cmdlet benzersiz bir tanımlayıcı (GUID) döndürür.
  
1. Kuruluşunuzda genel yönetici izinlerine sahip bir iş veya okul hesabı kullanarak [Exchange Online PowerShell'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

   ```powershell
   Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl DataEncryptionPolicyID
   ```

   *Burada GeneralMailboxOrMailUserIdParameter* bir posta kutusu belirtir ve DataEncryptionPolicyID de DEP'in GUID'sini döndürür. Get-MailboxStatistics cmdlet'i hakkında daha fazla bilgi için bkz. [Get-MailboxStatistics](/powershell/module/exchange/get-mailboxstatistics).
  
2. Posta kutusunun atandığı DEP'nin kolay adını bulmak için Get-DataEncryptionPolicy cmdlet'ini çalıştırın.
  
   ```powershell
   Get-DataEncryptionPolicy <GUID>
   ```

   Burada *GUID* , önceki adımda Get-MailboxStatistics cmdlet'i tarafından döndürülen GUID'dir.

## <a name="verify-that-customer-key-has-finished-encryption"></a>Müşteri Anahtarı'nın şifrelemeyi tamamlandığını doğrulayın

müşteri anahtarı aldıysanız, yeni bir DEP atadıysanız veya bir posta kutusunu geçirdiyseniz, şifrelemenin tamamlandığından emin olmak için bu bölümdeki adımları kullanın.

### <a name="verify-encryption-completes-for-exchange-online-mailboxes"></a>Exchange Online posta kutuları için şifrelemenin tamamlanmasını doğrulama

Posta kutusunun şifrelenmesi biraz zaman alabilir. İlk kez şifreleme için, hizmetin posta kutusunu şifreleyebilmesi için önce posta kutusunun bir veritabanından diğerine tamamen taşınması gerekir.
  
Posta kutusunun şifrelenip şifrelenmediğini belirlemek için Get-MailboxStatistics cmdlet'ini kullanın.
  
```powershell
Get-MailboxStatistics -Identity <GeneralMailboxOrMailUserIdParameter> | fl IsEncrypted
```

IsEncrypted özelliği, posta kutusu şifrelenmişse **true** değerini ve posta kutusu şifrelenmemişse **false** değerini döndürür. Posta kutusu taşımalarını tamamlama süresi, ilk kez DEP atadığınız posta kutularının sayısına ve posta kutularının boyutuna bağlıdır. DeP'i atadığınız zamandan itibaren bir hafta sonra posta kutuları şifrelenmemişse Microsoft'a başvurun.

New-MoveRequest cmdlet'i artık yerel posta kutusu taşımaları için kullanılamaz. Ek bilgi için [bu duyuruya](https://techcommunity.microsoft.com/t5/exchange-team-blog/disabling-new-moverequest-for-local-mailbox-moves/bc-p/1332141) bakın.

### <a name="verify-encryption-completes-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>SharePoint Online, OneDrive İş ve Teams dosyaları için şifrelemenin tamamlanıp tamamlanmadığını doğrulama

Get-SPODataEncryptionPolicy cmdlet'ini aşağıdaki gibi çalıştırarak şifreleme durumunu denetleyin:

```PowerShell
   Get-SPODataEncryptionPolicy <SPOAdminSiteUrl>
```

Bu cmdlet'ten elde edilen çıkış şunları içerir:
  
- Birincil anahtarın URI'sini.

- İkincil anahtarın URI'sini.

- Coğrafi bölge için şifreleme durumu. Olası durumlar şunlardır:

  - **Kayıtsız:** Müşteri Anahtarı şifrelemesi henüz uygulanmadı.

  - **Kaydediliyor:** Müşteri Anahtarı şifrelemesi uygulandı ve dosyalarınız şifreleniyor. Coğrafi konumun anahtarı kaydediliyorsa, şifreleme ilerleme durumunu izleyebilmenizi sağlayan coğrafi konumlardaki sitelerin yüzde kaçının tamamlandığını gösteren bilgiler de gösterilir.

  - **Kayıtlı:** Müşteri Anahtarı şifrelemesi uygulandı ve tüm sitelerdeki tüm dosyalar şifrelendi.

  - **Haddeleme:** Bir anahtar rulosu devam ediyor. Coğrafi konumun anahtarı sıralıysa ilerleme durumunu izleyebilebilmeniz için anahtar alma işlemini tamamlayan sitelerin yüzdesi hakkında da bilgi gösterilir.

- Ayrıca eklenen sitelerin yüzdesini de oluşturur.

## <a name="get-details-about-deps-you-use-with-multiple-workloads"></a>Birden çok iş yüküyle kullandığınız DEP'ler hakkında ayrıntılı bilgi edinin

Birden çok iş yüküyle kullanmak üzere oluşturduğunuz tüm DEP'ler hakkında ayrıntılı bilgi edinmek için şu adımları tamamlayın:

1. Yerel bilgisayarınızda, kuruluşunuzda genel yönetici veya uyumluluk yöneticisi izinlerine sahip bir iş veya okul hesabı kullanarak [Windows PowerShell penceresinde Exchange Online PowerShell'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

   - Kuruluştaki tüm çok iş yükü DEP'lerinin listesini döndürmek için bu komutu çalıştırın.

     ```powershell
        Get-M365DataAtRestEncryptionPolicy
     ```

   - Belirli bir DEP hakkındaki ayrıntıları döndürmek için bu komutu çalıştırın. Bu örnek, DEP için "Contoso_Global" adlı ayrıntılı bilgileri döndürür.

     ```powershell
        Get-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global"
     ```

## <a name="get-multi-workload-dep-assignment-information"></a>Çok iş yükü dep atama bilgilerini alma

Kiracınıza atanmış olan DEP'yi bulmak için aşağıdaki adımları izleyin. 

1. Yerel bilgisayarınızda, kuruluşunuzda genel yönetici veya uyumluluk yöneticisi izinlerine sahip bir iş veya okul hesabı kullanarak [Windows PowerShell penceresinde Exchange Online PowerShell'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

2. Bu komutu yazın.

   ```powershell
      Get-M365DataAtRestEncryptionPolicyAssignment
   ```

## <a name="disable-a-multi-workload-dep"></a>Çok iş yükülü DEP'yi devre dışı bırakma

Çok iş yüküne sahip bir DEP'yi devre dışı bırakmadan önce kiracınızdaki iş yüklerinden DEP'nin atamasını kaldırın. Birden çok iş yüküyle kullanılan bir DEP'yi devre dışı bırakmak için şu adımları tamamlayın:

1. Yerel bilgisayarınızda, kuruluşunuzda genel yönetici veya uyumluluk yöneticisi izinlerine sahip bir iş veya okul hesabı kullanarak [Windows PowerShell penceresinde Exchange Online PowerShell'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

2. Set-M365DataAtRestEncryptionPolicy cmdlet'ini çalıştırın.
  
   ```powershell
   Set-M365DataAtRestEncryptionPolicy -[Identity] "PolicyName" -Enabled $false
   ```

Burada *PolicyName* , ilkenin adı veya benzersiz kimliğidir. Örneğin, Contoso_Global.

Örneğin:

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global" -Enabled $false
```

## <a name="restore-azure-key-vault-keys"></a>Azure Key Vault anahtarlarını geri yükleme

Geri yükleme gerçekleştirmeden önce geçici silme tarafından sağlanan kurtarma özelliklerini kullanın. Müşteri Anahtarı ile kullanılan tüm anahtarların geçici silmenin etkinleştirilmesi gerekir. Geçici silme, geri dönüşüm kutusu gibi davranır ve geri yüklemeye gerek kalmadan 90 güne kadar kurtarma sağlar. Geri yükleme yalnızca anahtar veya anahtar kasasının kaybolması gibi aşırı veya olağan dışı durumlarda gerekli olmalıdır. Müşteri Anahtarı ile kullanmak üzere bir anahtarı geri yüklemeniz gerekiyorsa, Azure PowerShell Restore-AzureKeyVaultKey cmdlet'ini aşağıdaki gibi çalıştırın:
  
```powershell
Restore-AzKeyVaultKey -VaultName <vault name> -InputFile <filename>
```

Örneğin:
  
```powershell
Restore-AzKeyVaultKey -VaultName Contoso-O365EX-NA-VaultA1 -InputFile Contoso-O365EX-NA-VaultA1-Key001-Backup-20170802.backup
```

Anahtar kasası aynı ada sahip bir anahtar içeriyorsa geri yükleme işlemi başarısız olur. Restore-AzKeyVaultKey anahtar adı da dahil olmak üzere anahtar için tüm anahtar sürümlerini ve tüm meta verileri geri yükler.
  
## <a name="manage-key-vault-permissions"></a>Anahtar kasası izinlerini yönetme

Anahtar kasası izinlerini görüntülemenizi ve gerekirse kaldırmanızı sağlayan çeşitli cmdlet'ler mevcuttur. Örneğin, bir çalışan takımdan ayrıldığında izinleri kaldırmanız gerekebilir. Bu görevlerin her biri için Azure PowerShell kullanacaksınız. Azure PowerShell hakkında bilgi için bkz. [Azure PowerShell genel bakış](/powershell/azure/).

Anahtar kasası izinlerini görüntülemek için Get-AzKeyVault cmdlet'ini çalıştırın.

```powershell
Get-AzKeyVault -VaultName <vault name>
```

Örneğin:

```powershell
Get-AzKeyVault -VaultName Contoso-O365EX-NA-VaultA1
```

Yönetici izinlerini kaldırmak için Remove-AzKeyVaultAccessPolicy cmdlet'ini çalıştırın:
  
```powershell
Remove-AzKeyVaultAccessPolicy -VaultName <vault name> -UserPrincipalName <UPN of user>
```

Örneğin:

```powershell
Remove-AzKeyVaultAccessPolicy -VaultName Contoso-O365EX-NA-VaultA1 -UserPrincipalName alice@contoso.com
```

## <a name="roll-back-from-customer-key-to-microsoft-managed-keys"></a>Müşteri Anahtarı'ndan Microsoft tarafından yönetilen anahtarlara geri dönme

Microsoft tarafından yönetilen anahtarlara geri dönmeniz gerekiyorsa geri dönebilirsiniz. Kullanıma aldığınızda, verileriniz her bir iş yükü tarafından desteklenen varsayılan şifreleme kullanılarak yeniden şifrelenir. Örneğin, Exchange Online Microsoft tarafından yönetilen anahtarları kullanarak varsayılan şifrelemeyi destekler.

> [!IMPORTANT]
> Çıkarma, veri temizleme işlemiyle aynı değildir. Veri temizleme, kuruluşunuzun verilerini Microsoft 365'dan kalıcı olarak şifreler ve çıkarma işlemi yapmaz. Birden çok iş yükü ilkesi için veri temizleme işlemi gerçekleştiremezsiniz.

Çok iş yüküne sahip DEP'leri atamak için Müşteri Anahtarını artık kullanmamaya karar verirseniz, Müşteri Anahtarı'ndan "kullanıma alma" isteğiyle Microsoft desteğine ulaşmanız gerekir. Destek ekibinden Microsoft Purview Müşteri Anahtarı ekibine bir hizmet isteği göndermesini isteyin. Sorularınız varsa m365-ck@service.microsoft.com ulaşın.

Posta kutusu düzeyi DEP'leri kullanarak tek tek posta kutularını şifrelemek istemiyorsanız, posta kutusu düzeyi DEP'lerin atamasını tüm posta kutularınızdan kaldırabilirsiniz.

Posta kutusu DEP'lerinin atamasını silmek için Set-Mailbox PowerShell cmdlet'ini kullanın.

1. Kuruluşunuzda genel yönetici izinlerine sahip bir iş veya okul hesabı kullanarak [Exchange Online PowerShell'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

2. Set-Mailbox cmdlet'ini çalıştırın.

   ```powershell
   Set-Mailbox -Identity <mailbox> -DataEncryptionPolicy $NULL
   ```

Bu cmdlet'in çalıştırılması, şu anda atanmış olan DEP'nin atamasını kaldırın ve varsayılan Microsoft tarafından yönetilen anahtarlarla ilişkilendirilmiş DEP'yi kullanarak posta kutusunun şifresini yeniden şifreler. Microsoft tarafından yönetilen anahtarlar tarafından kullanılan DEP'nin atamasını kaldıramazsınız. Microsoft tarafından yönetilen anahtarları kullanmak istemiyorsanız, posta kutusuna başka bir Müşteri Anahtarı DEP'i atayabilirsiniz.

> [!IMPORTANT]
> SharePoint Online, OneDrive İş ve Teams dosyaları için Müşteri Anahtarı'ndan Microsoft tarafından yönetilen anahtarlara geri alma desteklenmez. 

## <a name="revoke-your-keys-and-start-the-data-purge-path-process"></a>Anahtarlarınızı iptal etme ve veri temizleme yolu işlemini başlatma

Kullanılabilirlik anahtarı da dahil olmak üzere tüm kök anahtarların iptalini siz denetlersiniz. Müşteri Anahtarı, sizin için mevzuat gereksinimlerinin çıkış planlama yönünün denetimini sağlar. Verilerinizi temizlemek ve hizmetten çıkmak için anahtarlarınızı iptal etmeye karar verirseniz, veri temizleme işlemi tamamlandıktan sonra hizmet kullanılabilirlik anahtarını siler. Bu, tek tek posta kutularına atanan Müşteri Anahtarı DEP'leri için desteklenir.

Microsoft 365, veri temizleme yolunu denetler ve doğrular. Daha fazla bilgi için [bkz. Hizmet Güveni Portalı'nda](https://servicetrust.microsoft.com/) bulunan SSAE 18 SOC 2 Raporu. Ayrıca, Microsoft aşağıdaki belgeleri önerir:

- [Microsoft Bulut'taki Finansal Kurumlar için Risk Değerlendirme ve Uyumluluk Kılavuzu](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=edee9b14-3661-4a16-ba83-c35caf672bd7&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

- [O365 Çıkış Planlama Konuları](https://servicetrust.microsoft.com/ViewPage/TrustDocuments?command=Download&downloadType=Document&downloadId=77ea7ebf-ce1b-4a5f-9972-d2d81a951d99&docTab=6d000410-c9e9-11e7-9a91-892aae8839ad_FAQ_and_White_Papers)

Müşteri Anahtarı için çok iş yükülü DEP'nin temizlenmesi desteklenmez. Çoklu iş yükü DEP, tüm kiracı kullanıcıları genelinde birden çok iş yükündeki verileri şifrelemek için kullanılır. Bu tür DEP'lerin temizlenmesi, birden çok iş yükünden gelen verilerin erişilemez hale gelmesine neden olur. Microsoft 365 hizmetlerden tamamen çıkmaya karar verirseniz, belgelenen işlem başına kiracı silme yolunu takip edebilirsiniz. [Azure Active Directory'da kiracıyı silme bölümüne](/azure/active-directory/enterprise-users/directory-delete-howto) bakın.

### <a name="revoke-your-customer-keys-and-the-availability-key-for-exchange-online-and-skype-for-business"></a>müşteri anahtarlarınızı ve Exchange Online ve Skype Kurumsal için kullanılabilirlik anahtarını iptal etme

Exchange Online ve Skype Kurumsal için veri temizleme yolunu başlattığınızda, DEP üzerinde kalıcı bir veri temizleme isteği ayarlarsınız. Bunu yaptığınızda, DEP'in atandığı posta kutularındaki şifrelenmiş veriler kalıcı olarak silinir.

PowerShell cmdlet'ini aynı anda yalnızca bir DEP'de çalıştırabildiğiniz için, veri temizleme yolunu başlatmadan önce tek bir DEP'yi tüm posta kutularınıza yeniden atamayı göz önünde bulundurun.

> [!WARNING]
> Posta kutularınızın bir alt kümesini silmek için veri temizleme yolunu kullanmayın. Bu işlem yalnızca hizmetten çıkan müşterilere yöneliktir.

Veri temizleme yolunu başlatmak için şu adımları tamamlayın:

1. Azure Key Vaults'tan "O365 Exchange Online" için sarmalama ve kaldırma izinlerini kaldırın.

2. Kuruluşunuzda genel yönetici ayrıcalıklarına sahip bir iş veya okul hesabı kullanarak [Exchange Online PowerShell'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

3. Silmek istediğiniz posta kutularını içeren her DEP için [Set-DataEncryptionPolicy](/powershell/module/exchange/set-dataencryptionpolicy) cmdlet'ini aşağıdaki gibi çalıştırın.

    ```powershell
    Set-DataEncryptionPolicy <Policy ID> -PermanentDataPurgeRequested -PermanentDataPurgeReason <Reason> -PermanentDataPurgeContact <ContactName>
    ```

   Komut başarısız olursa, bu görevin önceki bölümlerinde belirtildiği gibi Azure Key Vault'daki her iki anahtardan da Exchange Online izinlerini kaldırdığınızdan emin olun. Set-DataEncryptionPolicy cmdlet'ini kullanarak PermanentDataPurgeRequested anahtarını ayarladıktan sonra, bu DEP'yi artık posta kutularına atayamazsınız.

4. Microsoft desteğine başvurun ve Veri Temizleme eDocument'ını isteyin.

    İsteğiniz üzerine Microsoft, veri silme işlemini onaylamanız ve yetkilendirmeniz için size yasal bir belge gönderir. Kuruluşunuzda, ekleme sırasında FastTrack teklifinde onaylayan olarak kaydolan kişinin bu belgeyi imzalaması gerekir. Normalde bu, kuruluşunuz adına evrakları imzalamak için yasal olarak yetkili bir yönetici veya şirketinizde başka bir atanmış kişidir.

5. Temsilciniz yasal belgeyi imzaladıktan sonra Microsoft'a iade edin (genellikle bir eDoc imzası aracılığıyla).

    Microsoft yasal belgeyi aldıktan sonra, microsoft ilk olarak ilkeyi silen, posta kutularını kalıcı silme için işaretleyen ve ardından kullanılabilirlik anahtarını silen veri temizleme işlemini tetikleyen cmdlet'leri çalıştırır. Veri temizleme işlemi tamamlandıktan sonra veriler temizlenir, Exchange Online erişilemez ve kurtarılamaz.

### <a name="revoke-your-customer-keys-and-the-availability-key-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>SharePoint Online, OneDrive İş ve Teams dosyaları için Müşteri Anahtarlarınızı ve kullanılabilirlik anahtarınızı iptal etme

müşteri anahtarında SharePoint, iş veya okul için OneDrive ve Teams dosya DEP'lerinin temizlenmesi desteklenmez. Bu çoklu iş yükü DEP'leri, tüm kiracı kullanıcıları genelinde birden çok iş yükündeki verileri şifrelemek için kullanılır. Böyle bir DEP'nin temizlenmesi birden çok iş yükünden gelen verilerin erişilemez hale gelmesine neden olur. Microsoft 365 hizmetlerden tamamen çıkmaya karar verirseniz, belgelenen işlem başına kiracı silme yolunu takip edebilirsiniz. [Azure Active Directory'da kiracıyı silmeyi](/azure/active-directory/enterprise-users/directory-delete-howto) öğrenin.  

## <a name="related-articles"></a>İlgili makaleler

- [Microsoft Purview Müşteri Anahtarı ile hizmet şifreleme](customer-key-overview.md)

- [Kullanılabilirlik anahtarı hakkında bilgi edinin](customer-key-availability-key-understand.md)

- [Müşteri Anahtarını Ayarlama](customer-key-set-up.md)

- [Bir Müşteri Anahtarını veya uygunluk anahtarını toplama veya döndürme](customer-key-availability-key-roll.md)

- [Müşteri Kasası](customer-lockbox-requests.md)

- [Hizmet Şifrelemesi](office-365-service-encryption.md)
