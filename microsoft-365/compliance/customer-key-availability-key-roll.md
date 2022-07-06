---
title: Bir Müşteri Anahtarını veya uygunluk anahtarını toplama veya döndürme
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
description: Müşteri Anahtarı ile birlikte kullanılan Azure Key Vault depolanan müşteri kök anahtarlarının nasıl alındığını öğrenin. Hizmetler Exchange Online, Skype Kurumsal, SharePoint Online, OneDrive İş ve Teams dosyalarını içerir.
ms.openlocfilehash: 474df9b4776df09b4a46ca002f506155606bdb52
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636501"
---
# <a name="roll-or-rotate-a-customer-key-or-an-availability-key"></a>Bir Müşteri Anahtarını veya uygunluk anahtarını toplama veya döndürme

> [!CAUTION]
> Yalnızca güvenlik veya uyumluluk gereksinimleriniz anahtarın alınması gerektiğini belirlediğinde Müşteri Anahtarı ile kullandığınız bir şifreleme anahtarını yuvarlayın. Ayrıca, ilkelerle ilişkilendirilmiş veya ilişkili anahtarları silmeyin. Anahtarlarınızı yuvarladığınızda, önceki anahtarlarla şifrelenmiş içerik olacaktır. Örneğin, etkin posta kutuları sık sık yeniden şifrelenirken, etkin olmayan, bağlantısı kesilmiş ve devre dışı bırakılmış posta kutuları önceki anahtarlarla yine de şifrelenebilir. SharePoint Online, geri yükleme ve kurtarma amacıyla içeriğin yedeğini gerçekleştirir, bu nedenle eski anahtarlar kullanılarak arşivlenmiş içerik olabilir.

## <a name="about-rolling-the-availability-key"></a>Kullanılabilirlik anahtarını döndürme hakkında

Microsoft, kullanılabilirlik anahtarının doğrudan denetimini müşterilere sunmaz. Örneğin, yalnızca Azure Key Vault sahip olduğunuz anahtarları yuvarlayabilir (döndürebilirsiniz). Microsoft 365, kullanılabilirlik anahtarlarını dahili olarak tanımlanmış bir zamanlamaya göre dağıtır. Bu anahtar dağıtımlar için müşteriye yönelik, hizmet düzeyi sözleşmesi (SLA) yoktur. Microsoft 365, microsoft 365 hizmet kodunu kullanarak kullanılabilirlik anahtarını otomatik ve el ile olmayan bir işlemle döndürür. Microsoft yöneticileri, roll işlemini başlatabilir. Anahtar, anahtar deposuna doğrudan erişim olmadan otomatik mekanizmalar kullanılarak alınır. Kullanılabilirlik anahtarı gizli deposuna erişim Microsoft yöneticilerine sağlanmaz. Kullanılabilirlik anahtarı yuvarlama, başlangıçta anahtarı oluşturmak için kullanılan mekanizmayı kullanır. Kullanılabilirlik anahtarı hakkında daha fazla bilgi için bkz. [Kullanılabilirlik anahtarını anlama](customer-key-availability-key-understand.md).

> [!IMPORTANT]
> Exchange Online ve Skype Kurumsal kullanılabilirlik anahtarları, oluşturduğunuz her DEP için benzersiz bir kullanılabilirlik anahtarı oluşturulduğundan yeni bir DEP oluşturan müşteriler tarafından etkili bir şekilde alınabilir. SharePoint Online, OneDrive İş ve Teams dosyalarının kullanılabilirlik anahtarları orman düzeyinde bulunur ve DEP'ler ve müşteriler arasında paylaşılır, yani sıra yalnızca Microsoft tarafından dahili olarak tanımlanmış bir zamanlamada gerçekleşir. Her yeni DEP oluşturulduğunda kullanılabilirlik anahtarını döndürmeme riskini azaltmak için SharePoint, OneDrive ve Teams, her yeni DEP oluşturulduğunda müşteri kök anahtarları ve kullanılabilirlik anahtarı tarafından sarmalanan anahtar olan kiracı ara anahtarını (TIK) alır.

## <a name="request-a-new-version-of-each-existing-root-key-you-want-to-roll"></a>Almak istediğiniz mevcut her kök anahtarın yeni bir sürümünü isteyin

Bir anahtarı yuvarladığınızda, mevcut anahtarın yeni bir sürümünü isteyebilirsiniz. Mevcut anahtarın yeni bir sürümünü istemek için, [add-AzKeyVaultKey](/powershell/module/az.keyvault/add-azkeyvaultkey) cmdlet'ini, anahtarı oluştururken kullandığınız söz dizimiyle birlikte kullanırsınız. Veri Şifreleme İlkesi (DEP) ile ilişkili herhangi bir anahtarı döndürmeyi tamamladıktan sonra, Müşteri Anahtarı'nın yeni anahtarı kullanmaya başladığından emin olmak için başka bir cmdlet çalıştırırsınız. Bu adımı her Azure Key Vault (AKV) içinde gerçekleştirin.

Örneğin:

1. Azure PowerShell ile Azure aboneliğinizde oturum açın. Yönergeler için bkz. [Azure PowerShell ile oturum açma](/powershell/azure/authenticate-azureps).

2. Aşağıdaki örnekte gösterildiği gibi Add-AzKeyVaultKey cmdlet'ini çalıştırın:

   ```powershell
   Add-AzKeyVaultKey -VaultName Contoso-CK-EX-NA-VaultA1 -Name Contoso-CK-EX-NA-VaultA1-Key001 -Destination HSM -KeyOps @('wrapKey','unwrapKey') -NotBefore (Get-Date -Date "12/27/2016 12:01 AM")
   ```

   Bu örnekte **Contoso-CK-EX-NA-VaultA1-Key001** adlı bir anahtar **Contoso-CK-EX-NA-VaultA1** kasasında bulunduğundan, cmdlet anahtarın yeni bir sürümünü oluşturur. Bu işlem, anahtarın sürüm geçmişinde önceki anahtar sürümlerini korur. Şifrelemeye devam eden verilerin şifresini çözmek için önceki anahtar sürümüne ihtiyacınız vardır. DEP ile ilişkili herhangi bir anahtarın sıralanmasını tamamladıktan sonra, Müşteri Anahtarının yeni anahtarı kullanmaya başladığından emin olmak için fazladan bir cmdlet çalıştırın. Aşağıdaki bölümlerde cmdlet'ler daha ayrıntılı olarak açıklanmaktadır.
  
## <a name="update-the-keys-for-multi-workload-deps"></a>Çoklu iş yükü DEP'leri için anahtarları güncelleştirme

Birden çok iş yüküyle kullanılan bir DEP ile ilişkili Azure Key Vault anahtarlarından birini yuvarladığınızda, DEP'yi yeni anahtara işaret eden şekilde güncelleştirmeniz gerekir. Bu işlem kullanılabilirlik anahtarını döndürmez.

Müşteri Anahtarı'na birden çok iş yükünü şifrelemek için yeni anahtarı kullanmasını bildirmek için şu adımları tamamlayın:

1. Yerel bilgisayarınızda, kuruluşunuzda genel yönetici veya uyumluluk yöneticisi izinlerine sahip bir iş veya okul hesabı kullanarak [Exchange Online PowerShell'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

2. Set-M365DataAtRestEncryptionPolicy cmdlet'ini çalıştırın.
  
   ```powershell
   Set-M365DataAtRestEncryptionPolicy -[Identity] "PolicyName" -Refresh
   ```

Burada *PolicyName* , ilkenin adı veya benzersiz kimliğidir. Örneğin, Contoso_Global.

Örneğin:

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global" -Refresh
```

## <a name="update-the-keys-for-exchange-online-deps"></a>Exchange Online DEP anahtarlarını güncelleştirme

Exchange Online ve Skype Kurumsal ile kullanılan bir DEP ile ilişkili Azure Key Vault anahtarlarından birini yuvarladığınızda, DEP'yi yeni anahtara işaret eden şekilde güncelleştirmeniz gerekir. Bu, kullanılabilirlik anahtarını döndürmez.

Müşteri Anahtarı'na posta kutularını şifrelemek için yeni anahtarı kullanmasını bildirmek için Set-DataEncryptionPolicy cmdlet'ini aşağıdaki gibi çalıştırın:

1. Set-DataEncryptionPolicy cmdlet'ini Azure PowerShell çalıştırın:
  
   ```powershell
   Set-DataEncryptionPolicy -Identity <DataEncryptionPolicyID> -Refresh
   ```

2. Posta kutusunun DataEncryptionPolicyID özelliğinin değerini denetlemek için, Posta [kutusuna atanan DEP'yi belirleme'deki](customer-key-manage.md#determine-the-dep-assigned-to-a-mailbox) adımları kullanın. Hizmet güncelleştirilmiş anahtarı uyguladığında bu özelliğin değeri değişir.
  
## <a name="update-the-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>SharePoint Online, OneDrive İş ve Teams dosyalarının anahtarlarını güncelleştirme

SharePoint Online, aynı anda yalnızca bir anahtar almanızı sağlar. Anahtar kasasında her iki anahtarı da yuvarlamak istiyorsanız, ilk işlemin tamamlanmasını bekleyin. Microsoft, bu sorundan kaçınmak için işlemlerinizi kademelendirmenizi önerir. SharePoint Online ve OneDrive İş ile kullanılan bir DEP ile ilişkili Azure Key Vault anahtarlarından birini yuvarladığınızda, DEP'yi yeni anahtara işaret eden şekilde güncelleştirmeniz gerekir. Bu, kullanılabilirlik anahtarını döndürmez.

1. Update-SPODataEncryptionPolicy cmdlet'ini aşağıdaki gibi çalıştırın:
  
   ```powershell
   Update-SPODataEncryptionPolicy  <SPOAdminSiteUrl> -KeyVaultName <ReplacementKeyVaultName> -KeyName <ReplacementKeyName> -KeyVersion <ReplacementKeyVersion> -KeyType <Primary | Secondary>
   ```

   Bu cmdlet, SharePoint Online ve OneDrive İş için anahtar alma işlemini başlatırken, eylem hemen tamamlanmaz.

2. Anahtar alma işleminin ilerleme durumunu görmek için Get-SPODataEncryptionPolicy cmdlet'ini aşağıdaki gibi çalıştırın:

   ```powershell
   Get-SPODataEncryptionPolicy <SPOAdminSiteUrl>
   ```

## <a name="related-articles"></a>İlgili makaleler

- [Müşteri Anahtarı ile hizmet şifrelemesi](customer-key-overview.md)

- [Müşteri Anahtarını Ayarlama](customer-key-set-up.md)

- [Müşteri Anahtarını Yönet](customer-key-manage.md)

- [Kullanılabilirlik anahtarı hakkında bilgi edinin](customer-key-availability-key-understand.md)
