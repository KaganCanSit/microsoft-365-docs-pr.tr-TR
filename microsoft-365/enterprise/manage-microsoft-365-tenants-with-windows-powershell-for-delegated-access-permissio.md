---
title: DAP iş ortakları için Windows PowerShell ile Microsoft 365 kiracılarını yönetme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: Bu makalede, müşteri eğilimlerinizi yönetmek üzere Microsoft 365 için PowerShell'i kullanmayı öğrenin.
ms.openlocfilehash: 11869157a5ed106d1aea0a4ce0e21716be1cc78f
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096798"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Temsilci Erişim İzinleri (DAP) iş ortakları için Windows PowerShell ile Microsoft 365 kiracılarını yönetme

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Windows PowerShell, Dağıtım ve Bulut Çözümü Sağlayıcısı (CSP) iş ortaklarının Microsoft 365 yönetim merkezi kullanılamayan müşteri kiracısı ayarlarını kolayca yönetmesine ve raporlamasına olanak tanır. İş ortağı yönetici hesabının müşteri kiracılarına bağlanması için Adına Yönet (AOBO) izinlerinin gerekli olduğunu unutmayın.

Temsilci Erişim İzni (DAP) iş ortakları, Dağıtım ve Bulut Çözümü Sağlayıcıları (CSP) İş Ortaklarıdır. Bunlar genellikle diğer şirketlerin ağ veya telekom sağlayıcılarıdır. Microsoft 365 aboneliklerini müşterilerine sunulan hizmet tekliflerine paketlemektedir. bir Microsoft 365 aboneliği sattıklarında, müşteri kiracılarını yönetebilmeleri ve raporlamaları için otomatik olarak müşteri kiracılarına Adına Yönetme (AOBO) izinleri verilir.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

Bu konudaki yordamlar[, PowerShell ile Microsoft 365 için Bağlan](connect-to-microsoft-365-powershell.md) bağlanmanızı gerektirir.

Ayrıca iş ortağı kiracı yöneticisi kimlik bilgilerinize de ihtiyacınız vardır.

## <a name="what-do-you-want-to-do"></a>Ne yapmak istiyorsunuz?

### <a name="list-all-tenant-ids"></a>Tüm kiracı kimliklerini listeleme

> [!NOTE]
> 500'den fazla kiracınız varsa, cmdlet söz diziminin kapsamını  _-All_ veya _-MaxResultsParameter_ ile belirleyin. Bu, **Get-MsolUser** gibi büyük bir çıkış verebilen diğer cmdlet'ler için geçerlidir.

Erişiminiz olan tüm müşteri kiracı kimliklerini listelemek için bu komutu çalıştırın.

```powershell
Get-MsolPartnerContract -All | Select-Object TenantId
```

Bu, **TenantId'ye** göre tüm müşteri kiracılarınızın listesini görüntüler.

>[!Note]
>PowerShell Core, Windows PowerShell modülü için Microsoft Azure Active Directory Modülünü ve adında **Msol** bulunan cmdlet'leri desteklemez. Bu cmdlet'leri kullanmaya devam etmek için bunları Windows PowerShell çalıştırmanız gerekir.
>

### <a name="get-a-tenant-id-by-using-the-domain-name"></a>Etki alanı adını kullanarak kiracı kimliği alma

Etki alanı adına göre belirli bir müşteri kiracısının **TenantId** değerini almak için bu komutu çalıştırın. _<domainname.onmicrosoft.com>_ yerine istediğiniz müşteri kiracısının gerçek etki alanı adını yazın.

```powershell
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>Kiracı için tüm etki alanlarını listeleme

Herhangi bir müşteri kiracısı için tüm etki alanlarını almak için bu komutu çalıştırın. değerini gerçek değerle değiştirin  _\<customer TenantId value>_ .

```powershell
Get-MsolDomain -TenantId <customer TenantId value>
```

Ek etki alanları kaydettiyseniz bu, customer **TenantId** ile ilişkili tüm etki alanlarını döndürür.

### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>Tüm kiracıların ve kayıtlı etki alanlarının eşlemesini alma

önceki Microsoft 365 komutları için PowerShell, kiracı kimliklerini veya etki alanlarını nasıl alabileceğinizi ancak ikisini aynı anda almayabileceğinizi ve bunların tümü arasında net bir eşleme olmadığını gösterdi. Bu komut, tüm müşteri kiracı kimliklerinizin ve etki alanlarının listesini oluşturur.

```powershell
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>Kiracı için tüm kullanıcıları alma

Bu, belirli bir kiracıdaki tüm kullanıcılar için **UserPrincipalName**, **DisplayName** ve **isLicensed** durumunu görüntüler. değerini gerçek değerle değiştirin _\<customer TenantId value>_ .

```powershell
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>Kullanıcı hakkındaki tüm ayrıntıları alma

Belirli bir kullanıcının tüm özelliklerini görmek istiyorsanız, bu komutu çalıştırın. ve _\<user principal name value>_ değerlerini gerçek değerlerle değiştirin _\<customer TenantId value>_.

```powershell
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>Kullanıcı ekleme, seçenekleri ayarlama ve lisans atama

Microsoft 365 kullanıcılarının toplu oluşturma, yapılandırma ve lisanslama işlemleri, Microsoft 365 için PowerShell kullanılarak özellikle verimlidir. Bu iki adımlı işlemde, önce virgülle ayrılmış değer (CSV) dosyasına eklemek istediğiniz tüm kullanıcılar için girdiler oluşturur ve ardından Microsoft 365 için PowerShell kullanarak bu dosyayı içeri aktarırsınız.

#### <a name="create-a-csv-file"></a>CSV dosyası oluşturma

Şu biçimi kullanarak bir CSV dosyası oluşturun:

`UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`

Nerede:

- **UsageLocation**: Bunun değeri, kullanıcının iki harfli ISO ülke/bölge kodudur. Ülke/bölge [kodları,ISO Online Gözatma Platformu'nda](https://go.microsoft.com/fwlink/p/?LinkId=532703) aranabilir. Örneğin, Birleşik Devletler kodu ABD, Brezilya kodu ise BR şeklindedir.

- **LicenseAssignment**: Bunun değeri şu biçimi kullanır: `syndication-account:<PROVISIONING_ID>`. Örneğin, müşteri kiracı kullanıcılarına lisansları O365_Business_Premium atıyorsanız **, LicenseAssignment** değeri şöyle görünür: **syndication-account:O365_Business_Premium**. dağıtım veya CSP iş ortağı olarak erişiminiz olan PROVISIONING_IDs Dağıtım İş Ortağı Portalı'nda bulabilirsiniz.

#### <a name="import-the-csv-file-and-create-the-users"></a>CSV dosyasını içeri aktarma ve kullanıcıları oluşturma

CSV dosyanızı oluşturduktan sonra, kullanıcının ilk oturum açmada değiştirmesi gereken ve belirttiğiniz lisansı atayan süresi dolmayan parolalara sahip kullanıcı hesapları oluşturmak için bu komutu çalıştırın. Doğru CSV dosya adını değiştirerek emin olun.

```powershell
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>Ayrıca bkz.

[İş ortakları için yardım](https://go.microsoft.com/fwlink/p/?LinkId=533477)
