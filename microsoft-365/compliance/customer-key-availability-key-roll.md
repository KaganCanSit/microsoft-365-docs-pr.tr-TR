---
title: Müşteri Anahtarını veya uygunluk anahtarını döndürme veya döndürme
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
description: Müşteri Anahtarı ile kullanılan Azure Anahtar Kasasında depolanan müşteri kök anahtarlarının nasıl yuvarlanacaklarını öğrenin. Hizmetler arasında Exchange Online, Skype Kurumsal, SharePoint Online, OneDrive İş ve Teams vardır.
ms.openlocfilehash: 5f2de108d493e4b6d4233f4a932a24f524e468bb
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "62999138"
---
# <a name="roll-or-rotate-a-customer-key-or-an-availability-key"></a>Müşteri Anahtarını veya uygunluk anahtarını döndürme veya döndürme

> [!CAUTION]
> Yalnızca, güvenlik veya uyumluluk gereksinimleriniz anahtarın sizin için önemli olduğu zaman Müşteri Anahtarı ile birlikte kullanılan bir şifreleme anahtarını geri alma. Ayrıca, ilkelerle ilişkili veya ilkelerle ilişkilendirilmiş hiçbir anahtarı silmeyin. Anahtarlarınızı yuvarlarken, önceki anahtarlarla şifrelenmiş içerik olur. Örneğin, etkin posta kutuları sık sık yeniden şifrelenirken, etkin olmayan, bağlantısı kesilmiş ve devre dışı bırakılmış posta kutuları yine önceki anahtarlarla şifrelenir. SharePoint Online, geri yükleme ve kurtarma amacıyla içeriğin yedeğini gerçekleştirir, bu nedenle hala eski anahtarlar kullanılarak arşivlenmiş içerikler olabilir.

## <a name="about-rolling-the-availability-key"></a>Kullanılabilirlik anahtarının yuvarlanma hakkında

Microsoft, kullanılabilirlik anahtarının doğrudan kontrollerini müşterilere açığa çıkarmaz. Örneğin, yalnızca Azure Anahtar Kasasında sahip olduğunuz anahtarları döndürebilir (döndürün). Microsoft 365, kullanılabilirlik anahtarlarını dahili olarak tanımlanan bir zamanlamada öteler. Bu önemli rulolar için müşteriye yönelik, hizmet düzeyinde sözleşme (SLA) yoktur. Microsoft 365, hizmet kodunu otomatik, Microsoft 365 olmayan bir işlemde kullanarak kullanılabilirlik anahtarını döndürebilir. Microsoft yöneticileri roll işlemini başlatıyor olabilir. Anahtar, anahtar deposuna doğrudan erişime gerek kalmadan otomatik mekanizmalar kullanılarak alınır. Microsoft yöneticilerine kullanılabilirlik anahtarı gizli deposuna erişim sağlanmaz. Kullanılabilirlik tuşu yuvarlama, ilk başta anahtarı oluşturmak için kullanılan mekanizmadan yararlanıyor. Kullanılabilirlik anahtarı hakkında daha fazla bilgi için bkz [. Kullanılabilirlik anahtarını anlama](customer-key-availability-key-understand.md).

> [!IMPORTANT]
> Exchange Online de Skype Kurumsal deP oluşturan müşteriler tarafından kullanılabilirlik anahtarları etkili bir şekilde top edilebilir, çünkü sizin Exchange Online her DEP için benzersiz bir kullanılabilirlik anahtarı oluşturulur. SharePoint Online, OneDrive İş ve Teams dosyalarının kullanılabilirlik anahtarları orman düzeyinde yer alan ve DEP'ler ile müşteriler arasında paylaşılır; başka bir ifadeyle, yuvarlama yalnızca Microsoft şirket içinde tanımlanmış bir zamanlamada gerçekleşir. Her yeni DEP oluşturulduğunda kullanılabilirlik anahtarının yuvarlanma riskini azaltmak için SharePoint, OneDrive ve Teams kiracı ara anahtarını (TIK) her yeni DEP oluşturulduğunda müşteri kök anahtarları ve kullanılabilirlik anahtarıyla sarılmış anahtarı alır.

## <a name="request-a-new-version-of-each-existing-root-key-you-want-to-roll"></a>Var olan her kök anahtarın yeni bir sürümünü alma isteğinde olun

Bir anahtarı yuvarlarken, var olan anahtarın yeni bir sürümünü talep edin. Var olan bir anahtarın yeni sürümünü talep etmek için, aynı cmdlet olan [Add-AzKeyVaultKey'i](/powershell/module/az.keyvault/add-azkeyvaultkey) kullanır ve ilk yerinde anahtarı oluşturmak için de aynı söz dizimi kullanılır. Veri Şifreleme İlkesi (DEP) ile ilişkilendirilmiş anahtarın yuvarlanması bittiğinde, Müşteri Anahtarının yeni anahtarı kullanmaya başladığından emin olmak için başka bir cmdlet çalıştırın. Bu adımı her Azure Anahtar Kasasında (AKV) kullanın.

Örneğin:

1. Azure PowerShell ile Azure aboneliğinde oturum Azure PowerShell. Yönergeler için bkz[. Posta ile Azure PowerShell](/powershell/azure/authenticate-azureps).

2. Aşağıdaki Add-AzKeyVaultKey gösterildiği gibi cmdlet'i çalıştırın:

   ```powershell
   Add-AzKeyVaultKey -VaultName Contoso-CK-EX-NA-VaultA1 -Name Contoso-CK-EX-NA-VaultA1-Key001 -Destination HSM -KeyOps @('wrapKey','unwrapKey') -NotBefore (Get-Date -Date "12/27/2016 12:01 AM")
   ```

   Bu örnekte, **Contoso-CK-EX-EX-NA-VaultA1-Key001** adlı bir anahtar **Contoso-CK-EX-NA-VaultA1** kasasında yer alır, cmdlet anahtarın yeni bir sürümünü oluşturur. Bu işlem, anahtarın sürüm geçmişinde önceki anahtar sürümlerini korur. Şifrelerini halen şifreleen verilerin şifresini çözmek için önceki anahtar sürümüne ihtiyacınız vardır. DEP ile ilişkili anahtarın yuvarlanması tamamlandıktan sonra, Müşteri Anahtarının yeni anahtarı kullanmaya başladığından emin olmak için fazladan bir cmdlet çalıştırın. Aşağıdaki bölümlerde cmdlet'ler daha ayrıntılı olarak açıklanmaktadır.
  
## <a name="update-the-keys-for-multi-workload-deps"></a>Çok iş yüküne sahip DEP'ler için anahtarları güncelleştirme

Birden çok iş yüküyle kullanılan bir DEP ile ilişkili Azure Anahtar Kasa anahtarlarının birini alırken DEP'i yeni anahtara işaretacak şekilde güncelleştirmeniz gerekir. Bu işlem uygunluk anahtarını döndürmez.

Müşteri Anahtarı'nın birden çok iş yükünü şifrelemek üzere yeni anahtarı kullanmalarını sağlamak için şu adımları tamamlayın:

1. Yerel bilgisayarınızda, genel yönetici veya uyumluluk yöneticisi izinleri olan bir iş veya okul hesabı kullanarak, Windows PowerShell penceresinde [Exchange Online PowerShell'e](/powershell/exchange/connect-to-exchange-online-powershell) bağlanın.

2. Set-M365DataAtRestEncryptionPolicy cmdlet'ini çalıştırın.
  
   ```powershell
   Set-M365DataAtRestEncryptionPolicy -[Identity] "PolicyName" -Refresh
   ```

Burada *PolicyName* , ilkenin adı veya benzersiz kimliğidir. Örneğin, Contoso_Global.

Örneğin:

```powershell
Set-M365DataAtRestEncryptionPolicy -Identity "Contoso_Global" -Refresh
```

## <a name="update-the-keys-for-exchange-online-deps"></a>DEP'ler için Exchange Online güncelleştirme

Exchange Online ve Skype Kurumsal ile kullanılan bir DEP ile ilişkili Azure Anahtar Kasa anahtarlarının birini alırken DEP'i yeni anahtara işaretacak şekilde güncelleştirmeniz gerekir. Bu, uygunluk anahtarını döndürmez.

Müşteri Anahtarı'nın posta kutularını şifrelemek için yeni anahtarı kullanmalarını sağlamak için, aşağıdaki Set-DataEncryptionPolicy cmdlet'ini çalıştırın:

1. Azure PowerShell'de Set-DataEncryptionPolicy cmdlet'ini Azure PowerShell:
  
   ```powershell
   Set-DataEncryptionPolicy -Identity <DataEncryptionPolicyID> -Refresh
   ```

2. Posta kutusunun DataEncryptionPolicyID özelliğinin değerini kontrol etmek için, Posta kutusuna [atanan DEP'yi belirleme'de yer alan adımları kullanın](customer-key-manage.md#determine-the-dep-assigned-to-a-mailbox). Hizmet güncelleştirilmiş anahtarı uygularken bu özelliğin değeri değişir.
  
## <a name="update-the-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>SharePoint Online, OneDrive İş ve dosya Teams güncelleştirme

SharePoint Online, bir defada yalnızca bir tuş amama izin verir. Her iki anahtarı da bir anahtar kasasında almak için ilk işlemi bekleyin. Microsoft, bu sorunu önlemek için işlemlerinizi basamaklamanızı öneririz. SharePoint Online ve OneDrive İş'da kullanılan bir DEP ile ilişkili Azure Anahtar Kasa anahtarlarının herhangi birini yuvarlarken DEP'i yeni anahtara işaretacak şekilde güncelleştirmeniz gerekir. Bu, uygunluk anahtarını döndürmez.

1. Update-SPODataEncryptionPolicy cmdlet'ini aşağıdaki gibi çalıştırın:
  
   ```powershell
   Update-SPODataEncryptionPolicy  <SPOAdminSiteUrl> -KeyVaultName <ReplacementKeyVaultName> -KeyName <ReplacementKeyName> -KeyVersion <ReplacementKeyVersion> -KeyType <Primary | Secondary>
   ```

   Bu cmdlet, SharePoint Online ve OneDrive İş için anahtar alma işlemini başlatırken, eylem hemen tamamlanmadı.

2. Anahtar rulosu işlemi ilerlemesini görmek için, aşağıdaki gibi Get-SPODataEncryptionPolicy cmdlet'i çalıştırın:

   ```powershell
   Get-SPODataEncryptionPolicy <SPOAdminSiteUrl>
   ```

## <a name="related-articles"></a>İlgili makaleler

- [Müşteri Hizmetleri için Müşteri Anahtarı ile hizmet Office 365](customer-key-overview.md)

- [Müşteri Için Müşteri Anahtarını Office 365](customer-key-set-up.md)

- [Müşteri Için Müşteri Anahtarını Office 365](customer-key-manage.md)

- [Kullanılabilirlik anahtarı hakkında bilgi](customer-key-availability-key-understand.md)
